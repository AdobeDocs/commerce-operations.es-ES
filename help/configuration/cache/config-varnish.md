---
title: Configuración y uso de Barniz
description: Entender cómo Varnish almacena archivos y mejora el tráfico HTTP.
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Configurar barniz

[Caché de barniz] es un acelerador de aplicaciones web de código abierto (también denominado _acelerador HTTP_ o _almacenamiento en caché del proxy inverso HTTP_). Varnish almacena (o almacena en caché) archivos o fragmentos de archivos en la memoria, lo que permite a Varnish reducir el tiempo de respuesta y el consumo de ancho de banda de la red en solicitudes futuras y equivalentes. A diferencia de los servidores web como Apache y nginx, Varnish fue diseñado para usarse exclusivamente con el protocolo HTTP.

Commerce 2.4.2 se prueba con Varnish 6.4. Commerce 2.4.x es compatible con Varnish 6.x

>[!WARNING]
>
>Nosotros _recomendar_ Se utiliza Barnish en la producción. El almacenamiento en caché de página completa integrado: para el sistema de archivos o [database]: es mucho más lento que Varnish, y Varnish está diseñado para acelerar el tráfico HTTP.

Para obtener más información sobre Barniz, consulte:

- [El cuadro de barniz grande]
- [Opciones de inicio de barniz]
- [Barniz y rendimiento del sitio web]

## Diagrama de topología de barniz

La siguiente figura muestra una vista básica de Barniz en su topología de comercio.

![Diagrama de barniz básico](../../assets/configuration/varnish-basic.png)

En la figura anterior, las solicitudes HTTP de los usuarios a través de Internet resultan en numerosas solicitudes de CSS, HTML, JavaScript e imágenes (denominadas colectivamente _activos_). Varnish se encuentra delante del servidor web y envía estas solicitudes al servidor web.

A medida que el servidor web devuelve recursos, los recursos almacenables en caché se almacenan en Barnish. Todas las solicitudes posteriores de esos recursos las cumple Varnish (es decir, las solicitudes no llegan al servidor web). El barniz devuelve el contenido almacenado en caché muy rápidamente. Los resultados son tiempos de respuesta más rápidos para devolver el contenido a los usuarios y un número reducido de solicitudes que Commerce debe satisfacer.

Los recursos almacenados en caché por Varnish caducan a un intervalo configurable o se reemplazan con versiones más recientes de los mismos recursos. También puede borrar la caché manualmente utilizando el administrador o el [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) comando.

## Resumen del proceso

En este tema se explica cómo instalar inicialmente Varnish con un conjunto mínimo de parámetros y probar que funciona. A continuación, exporte una configuración de Barniz del administrador de Commerce y pruébela de nuevo.

El proceso puede resumirse de la siguiente manera:

1. Instale Varnish y pruébelo accediendo a cualquier página de Commerce para ver si obtiene encabezados de respuesta HTTP que indiquen que Varnish funciona.
1. Instale el software Commerce y utilice el Admin para crear un archivo de configuración de Barnish.
1. Reemplace el archivo de configuración de Barniz existente por el generado por el administrador.
1. Pruebe todo de nuevo.

   Si no hay nada en su `<magento_root>/var/page_cache` , ha configurado correctamente Varnish con Commerce.

>[!NOTE]
- Salvo que se indique lo contrario, debe introducir todos los comandos mencionados en este tema como usuario con `root` privilegios.
- Este tema está escrito para Varnish en CentOS y Apache 2.4. Si está configurando Barniz en un entorno diferente, algunos comandos pueden ser diferentes. Consulte la documentación de Barniz para obtener más información.


## Problemas conocidos

Sabemos de los siguientes problemas con Varnish:

- [El barniz no admite SSL]

   Como alternativa, utilice la terminación SSL o un proxy de terminación SSL.

- Si elimina manualmente el contenido del `<magento_root>/var/cache` , debe reiniciar Varnish.

- Posible error al instalar Commerce:

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   Si experimenta este error, edite `default.vcl` y añada un tiempo de espera a `backend` estrofa como sigue:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Descripción general del almacenamiento en caché de Varnish

El almacenamiento en caché de barniz funciona con Commerce mediante:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) desde el repositorio de GitHub de Magento 2
- `.htaccess` archivo de configuración distribuido para Apache proporcionado con Commerce
- `default.vcl` configuración de barniz generada mediante el [Administrador](../cache/configure-varnish-commerce.md)

>[!INFO]
En este tema se tratan únicamente las opciones predeterminadas de la lista anterior. Existen muchas otras formas de configurar el almacenamiento en caché en escenarios complejos (por ejemplo, mediante una red de distribución de contenido); estos métodos están fuera del ámbito de esta guía.

En la primera solicitud del explorador, los recursos almacenables en caché se entregan al explorador del cliente desde Varnish y se almacenan en la caché del explorador.

Además, Varnish utiliza una etiqueta de entidad (ETag) para los recursos estáticos. ETag permite determinar cuándo cambian los archivos estáticos en el servidor. Como resultado, los recursos estáticos se envían al cliente cuando cambian en el servidor, ya sea en una nueva solicitud desde un explorador o cuando el cliente actualiza la caché del explorador, normalmente presionando F5 o Control+F5.

En las secciones siguientes se ofrecen más detalles.

## Almacenamiento en caché por solicitud del explorador

En esta sección se utiliza un inspector del explorador para mostrar cómo se entregan los recursos al explorador en la primera solicitud y después se cargan desde la caché del explorador local.

### Primera solicitud del explorador

`nginx.conf.sample` y `.htaccess` proporciona opciones para el almacenamiento en caché del cliente. Cuando se realiza la primera solicitud desde un explorador para un objeto almacenable en caché, Varnish la envía al cliente.

En la siguiente figura se muestra un ejemplo utilizando un inspector del explorador:

![La primera vez que se solicita un objeto almacenable en caché, Varnish lo envía al explorador](../../assets/configuration/varnish-apache-first-visit.png)

El ejemplo anterior muestra una solicitud para la página principal de la tienda (`m2_ce_my`). Los recursos CSS y JavaScript se almacenan en la caché del explorador del cliente.

>[!NOTE]
La mayoría de los recursos estáticos tienen un código de estado HTTP 200 (OK), que indica que el recurso se recuperó del servidor.

### Segunda solicitud de explorador

Si el mismo explorador vuelve a solicitar la misma página, estos recursos se entregan desde la caché del explorador local, como se muestra en la siguiente ilustración.

![La próxima vez que se solicite el mismo objeto, los recursos se cargarán desde la caché del explorador local](../../assets/configuration/varnish-apache-second-visit.png)

Tenga en cuenta la diferencia en el tiempo de respuesta entre la primera y la segunda solicitud. De nuevo, los recursos estáticos tienen un código de respuesta 200 (OK) porque se envían desde la caché local por primera vez.

## Cómo utiliza Commerce Etag

El siguiente ejemplo muestra los encabezados de respuesta de un recurso estático concreto.

![ETag facilita la determinación de si un recurso estático ha cambiado o no](../../assets/configuration/varnish-etag.png)

`calendar.css` tiene un encabezado de respuesta ETag, lo que significa que el archivo CSS del explorador del cliente se puede comparar con el del servidor.

Además, los recursos estáticos se devuelven con un código de estado HTTP 304 (sin modificar), como se muestra en la siguiente ilustración.

![El código de respuesta HTTP 304 (sin modificar) indica que el recurso estático de la caché local es el mismo que el del servidor](../../assets/configuration/varnish-304.png)

El código de estado 304 se produce porque el usuario invalidó su caché local y el contenido del servidor no cambió. Debido al código de estado 304, el recurso estático _content_ no se transfiere; solo los encabezados HTTP se descargan en el explorador.

Si el contenido cambia en el servidor, el cliente descarga el recurso estático con un código de estado HTTP 200 (OK) y una nueva ETag.

<!-- Link Definitions -->

[database]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[El cuadro de barniz grande]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Caché de barniz]: https://varnish-cache.org
[Opciones de inicio de barniz]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Barniz y rendimiento del sitio web]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[El barniz no admite SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
