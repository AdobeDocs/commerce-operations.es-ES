---
title: Alineación de la infraestructura de Adobe Commerce y Adobe Experience Manager
description: Alinee su infraestructura de Adobe Commerce y Adobe Experience Manager para establecer tiempos de espera aceptables y límites de conexión.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Alineaciones de la infraestructura (tiempos de espera y límites de conexión)

Hay configuraciones con AEM y Adobe Commerce e infraestructura circundante, como equilibradores de carga que necesitan alineación, que están relacionadas con los límites de conexión y la configuración de tiempo de espera.

Un desajuste entre estos límites significaría que las conexiones podrían terminar siendo restringidas en AEM lado, mientras que Adobe Commerce es capaz de manejar más conexiones. Del mismo modo, para la configuración de tiempo de espera, un desajuste podría significar que se producen errores de tiempo de espera en AEM lado, mientras Adobe Commerce sigue procesando una solicitud.

Para la configuración de tiempo de espera, la configuración debe revisarse y alinearse para evitar que aparezcan errores de tiempo de espera 503 al estar en carga. Hay varias opciones de configuración de tiempo de espera de la aplicación y la infraestructura que se deben revisar:

![Diagrama numerado que describe tiempos de espera y límites de conexión para AEM](../assets/commerce-at-scale/timeout-settings.svg)

## equilibrador de carga AEM

Suponiendo que haya un equilibrador de carga de aplicación de AWS en la infraestructura y varios distribuidores/editores, se debe tener en cuenta la siguiente configuración para el equilibrador de carga:

1. Se deben revisar las comprobaciones de estado del editor para evitar que los despachantes abandonen el servicio innecesariamente antes de que se produzcan sobrecargas de carga. La configuración de tiempo de espera de la comprobación de estado del equilibrador de carga debe alinearse con la configuración de tiempo de espera del editor.

   ![Captura de pantalla que muestra AEM controles de estado del equilibrador de carga](../assets/commerce-at-scale/health-checks.png)

1. La adherencia del grupo de destino de Dispatcher se puede deshabilitar y se puede utilizar el algoritmo de equilibrio de carga de Round Robin. Esto supone que no hay AEM funcionalidad específica o AEM sesiones de usuario utilizadas que requerirían que se estableciera la permanencia de la sesión. Se supone que el inicio de sesión del usuario y la administración de sesiones solo están en Adobe Commerce a través de GraphQL.

   ![Captura de pantalla que muestra AEM atributos de adherencia a la sesión](../assets/commerce-at-scale/session-stickiness.png)

1. Tenga en cuenta que si habilita la permanencia en la sesión, esto puede hacer que las solicitudes no se almacenen en caché, ya que de forma predeterminada Finfinito no almacena en caché las páginas con el encabezado Set-Cookies. Adobe Commerce establece cookies incluso en páginas almacenables en caché (TTL > 0), pero la VCL predeterminada de Flash elimina esas cookies en páginas almacenables en caché para que funcione el almacenamiento en caché de forma rápida. Si las páginas no están almacenando en caché, compruebe las cookies personalizadas que pueda estar utilizando, y también cargue la LV de moda y vuelva a comprobar el sitio.

## Configuración de tiempo de espera de Dispatcher

El /timeout en las opciones &quot;renders&quot; de Dispatcher especifica el tiempo de espera de conexión que accede a la instancia de publicación de AEM en milisegundos. Esto debe revisarse y se debe utilizar la configuración predeterminada de &quot;0&quot; (tiempo de espera indefinido) si hay un equilibrador de carga independiente para gestionar la configuración de tiempo de espera.

Si no hay ningún equilibrador de carga en la infraestructura, la configuración de tiempo de espera debe especificarse en la configuración de Dispatcher/timeout, con un valor que coincida con la configuración de tiempo de espera de GraphQL del publicador.

## Editores

Límites y tiempos de espera de conexión de Publisher GraphQL: Inicialmente, las conexiones HTTP máximas en la configuración OSGI de la fábrica de configuración del cliente de Adobe Commerce CIF GraphQL deben establecerse en el límite máximo de conexiones predeterminado, que actualmente está establecido en 200. Incluso si hay varios editores en la granja de AEM, el límite debe establecerse igual en cada publicador, coincidiendo con la configuración de Inicio. El motivo de esto es que, en algunos casos, un editor podría estar gestionando más tráfico que los otros editores, si se saca a un despachante asociado de la granja, por ejemplo. Esto significaría que todo el tráfico se enrutaría a través del Dispatcher y los editores restantes, en este caso el editor único puede necesitar todas las conexiones HTTP.

El &quot;método HTTP predeterminado&quot; debe configurarse de POST en GET. Solo las solicitudes de GET se almacenan en caché en la caché de Adobe Commerce GraphQL y, por lo tanto, el método predeterminado siempre debe configurarse como GET.

El tiempo de espera de la conexión http y el tiempo de espera del socket http deben establecerse en un valor que coincida con el tiempo de espera Finfinito.

La siguiente imagen muestra la Fábrica de Configuración del Cliente CIF GraphQL de Magento. La configuración que se muestra a continuación son solo ejemplos y debe ajustarse en función de cada caso:

![Captura de pantalla de la configuración del marco de integración de comercio](../assets/commerce-at-scale/cif-config.png)

Las siguientes imágenes muestran las configuraciones del backend de Ffinity. La configuración que se muestra a continuación son solo ejemplos y debe ajustarse en función de cada caso:

![Captura de pantalla de los ajustes de configuración de Administración de comercio para Ffinity](../assets/commerce-at-scale/cif-config-advanced.png)
