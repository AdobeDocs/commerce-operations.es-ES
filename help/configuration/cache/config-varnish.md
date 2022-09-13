---
title: Configuración y uso de Varnish
description: Comprenda cómo Varnish almacena archivos y mejora el tráfico HTTP.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# Configuración de barniz

[Caché de barniz] es un acelerador de aplicaciones web de código abierto (también denominado _Acelerador HTTP_ o _almacenamiento en caché del proxy inverso HTTP_). Varnish almacena (o almacena en caché) archivos o fragmentos de archivos en la memoria, lo que permite a Varnish reducir el tiempo de respuesta y el consumo de ancho de banda de la red en solicitudes futuras equivalentes. A diferencia de servidores web como Apache y nginx, Varnish fue diseñado para su uso exclusivo con el protocolo HTTP.

Commerce 2.4.2 se ha probado con Varnish 6.4. Commerce 2.4.x es compatible con Varnish 6.x

>[!WARNING]
>
>We _recomienda_ usted usa Varnish en producción. El almacenamiento en caché integrado de página completa, para el sistema de archivos o [base de datos]—es mucho más lento que Varnish y Varnish está diseñado para acelerar el tráfico HTTP.

Para obtener más información sobre Varnish, consulte:

- [El panorama general de barniz]
- [Variar opciones de inicio]
- [Rendimiento de barniz y sitio web]

## Diagrama de topología de barniz

La siguiente figura muestra una vista básica de Varnish en su topología de comercio.

![Diagrama de barniz básico](../../assets/configuration/varnish-basic.png)

En la figura anterior, las solicitudes HTTP de los usuarios a través de Internet dan como resultado numerosas solicitudes de CSS, HTML, JavaScript e imágenes (denominadas colectivamente como _activos_). Varnish se sitúa delante del servidor web y dirige estas solicitudes al servidor web.

A medida que el servidor web devuelve recursos, los recursos almacenables en caché se almacenan en Varnish. Cualquier solicitud posterior de esos recursos la cumple Varnish (es decir, las solicitudes no llegan al servidor web). Varnish devuelve el contenido almacenado en caché muy rápidamente. Los resultados son tiempos de respuesta más rápidos para devolver el contenido a los usuarios y un número reducido de solicitudes que Commerce debe satisfacer.

Los recursos almacenados en la caché de Varnish caducan a un intervalo configurable o se sustituyen por versiones más recientes de los mismos recursos. También puede borrar la caché manualmente mediante la función [Administrador](https://glossary.magento.com/magento-admin) o [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) comando.

## Información general del proceso

En este tema se explica cómo instalar inicialmente Varnish con un conjunto mínimo de parámetros y probar que funciona. A continuación, exporte una configuración de Varnish desde el administrador de comercio y vuelva a probarla.

El proceso puede resumirse de la siguiente manera:

1. Instale Varnish y pruébelo accediendo a cualquier página de comercio para ver si está obteniendo encabezados de respuesta HTTP que indiquen que Varnish está funcionando.
1. Instale el software Commerce y utilice el administrador para crear un archivo de configuración de Varnish.
1. Reemplace el archivo de configuración de Varnish existente por el generado por el administrador.
1. Pruebe todo de nuevo.

   Si no hay nada en su `<magento_root>/var/page_cache` directorio, ha configurado correctamente Varnish con Commerce!

>[!NOTE]
- Salvo donde se indique lo contrario, debe introducir todos los comandos mencionados en este tema como usuario con `root` privilegios.
- Este tema está escrito para Varnish en CentOS y Apache 2.4. Si está configurando Varnish en un entorno diferente, algunos comandos pueden ser diferentes. Consulte la documentación de Varnish para obtener más información.


## Problemas conocidos

Conocemos los siguientes problemas con Varniz:

- [Varnish no admite SSL]

   Como alternativa, utilice la terminación SSL o un proxy de terminación SSL.

- Si elimina manualmente el contenido del `<magento_root>/var/cache` , debe reiniciar Varnish.

- Posible error al instalar Commerce:

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   Si experimenta este error, edite `default.vcl` y agregue un tiempo de espera a la variable `backend` stanza como sigue:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Descripción general del almacenamiento en caché de Varniz

El almacenamiento en caché de barnices funciona con Commerce mediante:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) desde el repositorio de Magento 2 GitHub
- `.htaccess` archivo de configuración distribuido para Apache que se proporciona con Commerce
- `default.vcl` configuración para Varnish generada con [Administrador](../cache/config-varnish-magento.md)

>[!INFO]
Este tema cubre únicamente las opciones predeterminadas de la lista anterior. Existen muchas otras formas de configurar el almacenamiento en caché en escenarios complejos (por ejemplo, utilizando una red de entrega de contenido); esos métodos quedan fuera del ámbito de esta guía.

En la primera solicitud del explorador, los recursos almacenables en caché se entregan al explorador del cliente desde Varnish y se almacenan en la caché del explorador.

Además, Varnish utiliza un [Entidad](https://glossary.magento.com/entity) Etiqueta (ETag) para recursos estáticos. La etiqueta ETag permite determinar cuándo [archivos estáticos](https://glossary.magento.com/static-files) cambie en el servidor. Como resultado, los recursos estáticos se envían al cliente cuando cambian en el servidor, ya sea en una nueva solicitud de un explorador o cuando el cliente actualiza la caché del explorador, normalmente presionando F5 o Control+F5.

En las secciones siguientes se proporcionan más detalles.

## Almacenamiento en caché por solicitud del explorador

En esta sección se utiliza un inspector del explorador para mostrar cómo se entregan los recursos al explorador en la primera solicitud y después de cargarse desde la caché del explorador local.

### Primera solicitud del explorador

`nginx.conf.sample` y `.htaccess` proporciona opciones para el almacenamiento en caché del cliente. Cuando la primera solicitud se realiza desde un explorador para un objeto almacenable en caché, Varnish la envía al cliente.

La siguiente figura muestra un ejemplo con un inspector de navegador:

![La primera vez que se realiza una solicitud para un objeto almacenable en caché, Varnish la envía al explorador](../../assets/configuration/varnish-apache-first-visit.png)

El ejemplo anterior muestra una solicitud para la página principal de la tienda (`m2_ce_my`). Los recursos CSS y JavaScript se almacenan en caché en el explorador del cliente.

>[!NOTE]
La mayoría de los recursos estáticos tienen un código de estado HTTP 200 (OK), que indica que el recurso se recuperó del servidor.

### Segunda solicitud del explorador

Si el mismo explorador solicita la misma página de nuevo, estos recursos se envían desde la caché del explorador local, como se muestra en la siguiente figura.

![La próxima vez que se solicite el mismo objeto, los recursos se cargan desde la caché del explorador local](../../assets/configuration/varnish-apache-second-visit.png)

Observe la diferencia en el tiempo de respuesta entre la primera y la segunda solicitud. De nuevo, los recursos estáticos tienen un código de respuesta de 200 (OK) porque se entregan desde la caché local por primera vez.

## Cómo utiliza Commerce Etag

En el siguiente ejemplo se muestran los encabezados de respuesta de un recurso estático concreto.

![La etiqueta ETag facilita la determinación de si un recurso estático ha cambiado o no](../../assets/configuration/varnish-etag.png)

`calendar.css` tiene un encabezado de respuesta ETag, lo que significa que el archivo CSS en el navegador del cliente se puede comparar con el del servidor.

Además, los recursos estáticos se devuelven con un código de estado HTTP 304 (no modificado), como se muestra en la siguiente figura.

![El código de respuesta HTTP 304 (no modificado) indica que el recurso estático en la caché local es el mismo que en el servidor](../../assets/configuration/varnish-304.png)

El código de estado 304 se produce porque el usuario invalidó su caché local y el contenido del servidor no cambió. Debido al código de estado 304, el recurso estático _contenido_ no se transfiera; solo se descargan encabezados HTTP en el explorador.

Si el contenido cambia en el servidor, el cliente descarga el recurso estático con un código de estado HTTP 200 (OK) y una nueva etiqueta ETag.

<!-- Link Definitions -->

[base de datos]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[El panorama general de barniz]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Caché de barniz]: https://varnish-cache.org
[Variar opciones de inicio]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Rendimiento de barniz y sitio web]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Varnish no admite SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
