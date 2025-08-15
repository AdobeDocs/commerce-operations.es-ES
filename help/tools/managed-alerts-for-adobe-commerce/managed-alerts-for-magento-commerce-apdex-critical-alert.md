---
title: 'Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta crítica'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta crítica  [!DNL Apdex] para Adobe Commerce en [!DNL New Relic]. The [!DNL Apdex] score que mide la satisfacción de los usuarios con el tiempo de respuesta de las aplicaciones y los servicios web. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 00e29611-fd4b-45c8-a1e0-56fc3cbe90e0
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta crítica

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta crítica de [!DNL Apdex] para Adobe Commerce en [!DNL New Relic]. La puntuación [!DNL Apdex] mide la satisfacción de los usuarios con el tiempo de respuesta de las aplicaciones y los servicios web. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta crítica de apdex](../../assets/managed-alerts/apdex-critical-magento-managed.png){width="500"}

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
* Realice cualquier tarea administrativa importante (es decir, el administrador de Commerce o las importaciones/exportaciones de datos).
* Borre la caché.

Si hace lo anterior cuando ha recibido una alerta crítica, antes de haber solucionado la causa de la alerta, puede provocar que su sitio deje de responder si aún no está experimentando una interrupción del sitio.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

>[!WARNING]
>
>Como se trata de una alerta crítica, se recomienda completar el **Paso 1** antes de intentar solucionar el problema (Paso 2 en adelante).

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulte [Rastrear los vales de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) en la Base de conocimiento de soporte de Commerce. Es posible que el equipo de asistencia haya recibido una alerta de umbral [!DNL New Relic], haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
   * Motivo del contacto: seleccione **[!UICONTROL New Relic CRITICAL alert received]**.
   * Descripción de la alerta.
   * [[!DNL New Relic] Vínculo de incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Esto se incluye en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Para identificar el origen del problema, use la [[!DNL New Relic] página de transacciones de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar las transacciones con problemas de rendimiento:
   * Ordene las transacciones en [!DNL Apdex] puntuaciones en orden ascendente. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una puntuación baja de [!DNL Apdex] puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos, [!DNL Redis], o PHP. Para ver los pasos, consulte [[!DNL New Relic] Ver transacciones con mayor insatisfacción con Apdex](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#dissatisfaction).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte [[!DNL New Relic] Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Si sigue teniendo problemas para identificar el problema, use la [[!DNL New Relic] página de infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Use la [[!DNL New Relic] página de infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar procesos que requieren muchos recursos. Para ver los pasos, consulte la [[!DNL New Relic] página Hosts de supervisión de infraestructura: [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si servicios como [!DNL Redis] o MySQL son la fuente principal de consumo de memoria, intente lo siguiente:
   * Compruebe que está en la versión más reciente. Las versiones más recientes a veces pueden corregir las fugas de memoria. Si no dispone de la versión más reciente, considere la posibilidad de actualizar. Para ver los pasos, consulte [Cambiar servicios](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) en la Guía de Commerce en la nube.
   * Compruebe problemas de MySQL como consultas de larga ejecución, claves principales no definidas e índices duplicados. Para ver los pasos, consulte [Problemas más comunes de la base de datos en Adobe Commerce sobre la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) en el Manual de implementación de Commerce.
   * Compruebe si hay problemas con PHP. Revise los procesos en ejecución ejecutando `ps aufx` en CLI/Terminal. En la salida de terminal verá trabajos y procesos cron que se están ejecutando actualmente. Compruebe el resultado para el tiempo de ejecución de los procesos. Si hay un cron con un tiempo de ejecución largo, el cron puede estar colgando. Para ver los pasos de solución de problemas, consulte [Rendimiento lento, crons lentos y de larga ejecución](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) y [Trabajo de Cron atascado en estado de &quot;ejecución&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) en la Base de conocimiento de soporte de Commerce.

1. Una vez identificada la fuente, SSH en el entorno para investigar más a fondo. Para ver los pasos, consulte [SSH en su entorno](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) en la Guía de Commerce en la nube.
1. Si sigue teniendo problemas para identificar el origen, revise las tendencias recientes para identificar problemas con implementaciones de código o cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
1. Si no puede encontrar una solución en un plazo razonable, solicite un aumento o coloque un sitio en modo de mantenimiento si aún no lo ha hecho. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) en nuestra Base de conocimiento de asistencia de Commerce y [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce.
1. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Consulte [Pruebas de carga y esfuerzo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en la Guía de Commerce en la nube.
