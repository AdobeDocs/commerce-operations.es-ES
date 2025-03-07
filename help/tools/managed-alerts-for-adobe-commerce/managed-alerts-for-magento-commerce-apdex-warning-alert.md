---
title: 'Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta de advertencia'
description: Este artículo proporciona pasos de solución de problemas para cuando reciba una alerta de advertencia  [!DNL Apdex] para Adobe Commerce en [!DNL New Relic]. The [!DNL Apdex] score mide la satisfacción de los usuarios con el tiempo de respuesta de las aplicaciones y servicios web. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 0e1e0e001cfe07d7404b4dd9f53c1608df1e0c25
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---


# Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta de advertencia

Este artículo proporciona pasos de solución de problemas para cuando reciba una alerta de advertencia [!DNL Apdex] para Adobe Commerce en [!DNL New Relic]. La puntuación [!DNL Apdex] mide la satisfacción de los usuarios con el tiempo de respuesta de las aplicaciones y los servicios web. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta de advertencia de apdex](../../assets/managed-alerts/apdex-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

* Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube
* Adobe Commerce en infraestructura en la nube Arquitectura del plan inicial

## Problema

Recibirá una alerta administrada en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe para ofrecer a los comerciantes un conjunto estándar con información de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) en la Guía de instalación de Commerce.

<u>**¡No!**</u>

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar una tensión adicional en el CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Para identificar el origen del problema, use [[!DNL New Relic APM's] Página de transacciones](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:
   * Ordenar transacciones en orden ascendente [!DNL Apdex scores]. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una [puntuación [!DNL Apdex] baja](managed-alerts-for-magento-commerce-apdex-warning-alert.md) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos, [!DNL Redis], o PHP. Para ver los pasos, consulte [[!DNL New Relic] Ver transacciones con mayor [!DNL Apdex] insatisfacción](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte [[!DNL New Relic] Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Use la [[!DNL New Relic] página de infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar procesos que requieren muchos recursos. Para ver los pasos, consulte la [[!DNL New Relic] página Hosts de supervisión de infraestructura: [!UICONTROL Processes] pestaña](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si servicios como [!DNL Redis] o MySQL son la fuente principal de consumo de memoria, intente lo siguiente:
   * Compruebe que está en la versión más reciente. Las versiones más recientes a veces pueden corregir las fugas de memoria. Si no dispone de la versión más reciente, considere la posibilidad de actualizar. Para ver los pasos, consulte [Cambiar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) en la Guía de Commerce en la nube.
1. Si el problema no se debe a las versiones del servicio:
   * Compruebe otros problemas de MySQL, como consultas de larga ejecución, claves principales no definidas e índices duplicados. Para ver los pasos, consulte [Problemas más comunes de la base de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) en el Manual de implementación de Commerce.
   * Compruebe si hay otros problemas con PHP. Revise los procesos en ejecución ejecutando `ps aufx` en CLI/Terminal. En la salida de terminal verá trabajos y procesos cron que se están ejecutando actualmente. Compruebe el resultado para el tiempo de ejecución de los procesos. Si hay un cron con un tiempo de ejecución largo, el cron puede estar colgando. Para ver los pasos de solución de problemas, consulte [Rendimiento lento, crons lentos y de larga ejecución](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) y [Trabajo de Cron atascado en estado de &quot;ejecución&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) en la Base de conocimiento de soporte de Commerce.
1. Una vez identificada una fuente potencial del problema, SSH en el entorno para investigar más a fondo. Para ver los pasos, consulte [SSH en su entorno](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) en la Guía de Commerce en la nube.
1. Si sigue teniendo problemas para identificar el origen, revise las tendencias recientes para identificar problemas con implementaciones de código o cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
1. Si no puede encontrar una solución en un plazo razonable, solicite un aumento o coloque un sitio en modo de mantenimiento si aún no lo ha hecho. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) en la Base de conocimiento de soporte técnico de Commerce y [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce.
1. Si [upsize](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) devuelve el sitio a operaciones normales, considere la posibilidad de solicitar un upsize permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el entorno de ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Consulte [Pruebas de carga y esfuerzo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en la Guía de Commerce en la nube.
