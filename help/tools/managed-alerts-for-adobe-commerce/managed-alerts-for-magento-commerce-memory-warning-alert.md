---
title: 'Alertas administradas para Adobe Commerce: Alerta de advertencia de memoria'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de advertencia de memoria para Adobe Commerce en  [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 54cb28acd9e930cc915f2ab1bf04cfc61d08663c
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: Alerta de advertencia de memoria

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de advertencia de memoria para Adobe Commerce en [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![advertencia de memoria](../../assets/managed-alerts/memory-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe Commerce para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

<u>**Hacer!**</u>:

* Se recomienda cancelar cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) en la Guía de instalación de Commerce.

<u>**¡No!**</u>:

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales, lo que puede causar una tensión adicional en el CPU o el disco.
* Realice cualquier tarea administrativa importante (es decir, el administrador, las importaciones/exportaciones de datos).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Utilice la [[!DNL New Relic] página Infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar los procesos con mayor consumo de memoria. Para ver los pasos, consulte [[!DNL New Relic] [Página de hosts de supervisión de infraestructura: ficha [!UICONTROL Processes]]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes). Si servicios como [!DNL Redis] o MySQL son la fuente principal de consumo de memoria, intente lo siguiente:

   * Compruebe que está en la versión más reciente. Las versiones más recientes a veces pueden corregir las fugas de memoria. Si no dispone de la versión más reciente, considere la posibilidad de actualizar. Para ver los pasos, consulte [Cambiar servicios](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) en la Guía de Commerce en la nube.
   * Si sigue sin poder identificar el origen del aumento del consumo de memoria, compruebe problemas de MySQL como consultas de larga ejecución, claves principales no definidas e índices duplicados. Para ver los pasos, consulte [Problemas más comunes de la base de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=es) en el Manual de implementación de Commerce.
   * Si no hay problemas con MySQL, compruebe si hay problemas con PHP. Revise los procesos en ejecución ejecutando `ps aufx` en CLI/Terminal. En la salida del terminal, verá los trabajos y procesos cron que se están ejecutando actualmente. Compruebe el resultado para el tiempo de ejecución de los procesos. Si hay un cron con un tiempo de ejecución largo, el cron puede estar colgando. Consulte [Rendimiento lento, crones lentos y de larga ejecución](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) y [Trabajo de cron atascado en estado de &quot;ejecución&quot;](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) en la Base de conocimiento de soporte de Commerce para ver los pasos de solución de problemas.

1. Si sigue teniendo problemas para identificar el origen del problema, use la [[!DNL New Relic] página de transacciones de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:

   * Ordene las transacciones en [!DNL Apdex] puntuaciones en orden ascendente. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una [puntuación [!DNL Apdex] baja](managed-alerts-for-magento-commerce-apdex-warning-alert.md) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos [!DNL Redis] o PHP. Para ver los pasos, consulte [Ver transacciones con mayor insatisfacción [!DNL Apdex] 2&rbrace; de New Relic.](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte [[!DNL New Relic] Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si sigue teniendo problemas para identificar el problema, use la [[!DNL New Relic] página de infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).

1. Si no puede identificar la causa del aumento del consumo de memoria, revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.

1. Si los métodos anteriores no le ayudan a encontrar la causa y/o la solución en un tiempo razonable, solicite un aumento o coloque el sitio en modo de mantenimiento si aún no lo ha hecho. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) en la Base de conocimiento de asistencia de Commerce y [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce.

1. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Consulte [Pruebas de carga y esfuerzo](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en la Guía de Commerce en la nube.
