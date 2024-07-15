---
title: Alineación de infraestructura de Adobe Commerce y Adobe Experience Manager
description: Alinee su infraestructura de Adobe Commerce y Adobe Experience Manager para establecer límites aceptables de tiempo de espera y conexión.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Alineaciones de infraestructura (tiempos de espera y límites de conexión)

AEM Existen configuraciones con la infraestructura de Adobe Commerce y la de los entornos, como equilibradores de carga, que necesitan alineación; estas se relacionan con los límites de conexión y la configuración de tiempo de espera.

AEM Una falta de alineación entre estos límites significaría que las conexiones podrían terminar siendo restringidas de lado, mientras que Adobe Commerce es capaz de gestionar más conexiones. AEM Del mismo modo, para la configuración de tiempo de espera, una desalineación podría significar que se producen errores de tiempo de espera en el lado de la, mientras Adobe Commerce sigue procesando una solicitud.

Para la configuración de tiempo de espera, la configuración debe revisarse y alinearse para evitar que aparezcan errores de tiempo de espera 503 al cargar. Hay varias configuraciones de infraestructura y tiempo de espera de la aplicación que se deben revisar:

AEM ![Diagrama numerado que describe los tiempos de espera y los límites de conexión para la conexión de la red de área de trabajo](../assets/commerce-at-scale/timeout-settings.svg)

## AEM balanceador de carga de

Suponiendo que haya un equilibrador de carga de aplicación de AWS en la infraestructura y varios distribuidores/editores, se debe tener en cuenta la siguiente configuración para el equilibrador de carga:

1. Las comprobaciones de estado del publicador deben revisarse para evitar que los distribuidores abandonen el servicio de forma innecesaria antes de los aumentos repentinos de carga. La configuración de tiempo de espera de la comprobación de estado del equilibrador de carga debe estar alineada con la configuración de tiempo de espera del editor.

   AEM ![Captura de pantalla que muestra las comprobaciones de estado del equilibrador de carga de la](../assets/commerce-at-scale/health-checks.png)

1. Se puede deshabilitar la permanencia del grupo de destino de Dispatcher y se puede utilizar el algoritmo de equilibrio de carga Round Robin. AEM AEM Esto supone que no se utiliza ninguna funcionalidad específica de la o que se utilizan sesiones de usuario que requieran que se establezca la permanencia de la sesión. Supone que el inicio de sesión y la administración de sesiones de los usuarios solo se realizan en Adobe Commerce a través de GraphQL.

   AEM ![Captura de pantalla que muestra atributos de permanencia de sesión de la sesión de la](../assets/commerce-at-scale/session-stickiness.png)

1. Tenga en cuenta que si habilita la permanencia de la sesión, esto puede hacer que las solicitudes de Fastly no se almacenen en caché, ya que de forma predeterminada, Fastly no almacena en caché las páginas con el encabezado Set-Cookies. Adobe Commerce establece cookies incluso en páginas almacenables en caché (TTL > 0), pero el VCL predeterminado de Fastly elimina esas cookies en páginas almacenables en caché para que funcione el almacenamiento en caché de Fastly. Si las páginas no están en caché, compruebe cualquier cookie personalizada que pueda estar utilizando y también cargue el VCL de Fastly y vuelva a comprobar el sitio.

## Configuración de tiempo de espera de Dispatcher

AEM La opción /timeout en &quot;renders&quot; de Dispatcher especifica el tiempo de espera de conexión que accede a la instancia de publicación de la en milisegundos. Esto debe revisarse y se debe utilizar la configuración predeterminada de &quot;0&quot; (tiempo de espera indefinido) si hay un equilibrador de carga independiente presente para gestionar la configuración de tiempo de espera.

Si no hay ningún equilibrador de carga en la infraestructura, la configuración de tiempo de espera debe especificarse en la configuración de /timeout de Dispatcher, con un valor que coincida con la configuración de tiempo de espera de GraphQL en el editor.

## Editores

Límites y tiempos de espera de la conexión de Publisher GraphQL: Inicialmente, la configuración OSGI de fábrica de configuración del cliente de Adobe Commerce CIF GraphQL HTTP debe establecerse en el límite predeterminado de conexiones máximas de Fastly, que actualmente está establecido en 200. AEM Incluso si hay varios editores en el conjunto de servidores de la, el límite debe establecerse del mismo modo en cada editor, coincidiendo con la configuración de Fastly. El motivo es que, en algunos casos, un editor podría estar administrando más tráfico que los otros editores si, por ejemplo, se saca a un distribuidor asociado de la granja. Esto significaría que todo el tráfico se enrutaría a través del único Dispatcher y los editores restantes, en este caso el único editor puede necesitar todas las conexiones HTTP.

El &quot;método HTTP predeterminado&quot; debe establecerse de POST a GET. Solo las solicitudes de GET se almacenan en caché en Adobe Commerce GraphQL y, por lo tanto, el método predeterminado siempre debe establecerse en GET.

El tiempo de espera de la conexión http y el tiempo de espera del socket http deben establecerse en un valor que coincida con el tiempo de espera de Fastly.

La siguiente imagen muestra el Magento CIF de la fábrica de configuración del cliente de GraphQL. La configuración que se muestra aquí son solo ejemplos y debe ajustarse caso por caso:

![Captura de pantalla de las opciones de configuración del Commerce integration framework](../assets/commerce-at-scale/cif-config.png)

Las siguientes imágenes muestran las configuraciones del servidor de Fastly. La configuración que se muestra aquí son solo ejemplos y debe ajustarse caso por caso:

![Captura de pantalla de las opciones de configuración de administración de Commerce para Fastly](../assets/commerce-at-scale/cif-config-advanced.png)
