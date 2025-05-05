---
title: 'Alertas administradas en Adobe Commerce: Alerta crítica de CPU'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta crítica de CPU para Adobe Commerce en  [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: b30266b8f39989103ca70fa3e57ade8cea9b0dcc
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Alertas administradas en Adobe Commerce: Alerta crítica de CPU

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta crítica de CPU para Adobe Commerce en [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta crítica de disco](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## Productos y versiones afectados

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta administrada en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe Commerce para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

<u>**Hacer!**</u>:

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) en la Guía de instalación de Commerce.

<u>**¡No!**</u>:

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales, lo que puede causar una tensión adicional en el CPU o disco.
* Realice cualquier tarea administrativa importante (es decir, el administrador de Commerce o las importaciones/exportaciones de datos).
* Borre la caché.

Es posible que el sitio no responda (si aún no está experimentando una interrupción del sitio) si realiza alguna de las acciones &quot;No&quot; antes de haber investigado y resuelto la causa de la alerta.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

>[!WARNING]
>
>Como se trata de una alerta crítica, se recomienda completar el **Paso 1** antes de intentar solucionar el problema (Paso 2 en adelante).

Compruebe si existe el vale de soporte de Adobe Commerce. Para ver los pasos, consulte [Rastrear los vales de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) en la Base de conocimiento de soporte de Commerce. Es posible que la asistencia técnica haya recibido una alerta de umbral [!DNL New Relic], haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:

1. Motivo del contacto: seleccione **[!UICONTROL New Relic CRITICAL alert received]**.
1. Descripción de la alerta.
1. [[!DNL New Relic] Vínculo de incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Esto se incluye en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Use la [[!DNL New Relic] página de transacciones de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:
   * Ordene las transacciones según las puntuaciones de Apdex ascendentes. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. Una [puntuación [!DNL Apdex] baja](managed-alerts-for-magento-commerce-apdex-warning-alert.md) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente, está relacionado con la base de datos [!DNL Redis] o PHP. Para ver los pasos, consulte [Ver transacciones con mayor insatisfacción [!DNL Apdex] 2&rbrace; de New Relic.](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat)
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte [!DNL New Relic] [Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si sigue teniendo problemas para identificar el origen, use la [[!DNL New Relic] página Infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) para identificar los servicios con recursos pesados. Para ver los pasos, consulte [!DNL New Relic] [Página de hosts de supervisión de infraestructura: ficha Procesos](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si identifica la fuente, SSH en el entorno para investigar más a fondo. Para ver los pasos, consulte [SSH en su entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) en la Guía de Commerce en la nube.
1. Si sigue teniendo problemas para identificar la fuente:
   * Revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
   * Considere la posibilidad de buscar y deshabilitar catálogos planos. Para ver los pasos, consulte [Funcionamiento lento, crons lentos y de larga duración](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) en la Base de conocimiento de asistencia de Commerce.
   * Si sospecha que está experimentando un ataque DDoS, intente bloquear el tráfico de bots. Para ver los pasos, consulte [Cómo bloquear el tráfico malintencionado para Adobe Commerce en la infraestructura en la nube en el nivel Fastly](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) en la Base de conocimiento de asistencia de Commerce.
1. Si el problema parece temporal, realice pasos de mitigación como un aumento de tamaño o ponga el sitio en modo de mantenimiento. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) en la Base de conocimiento de asistencia de Commerce y [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas o el código que reduce la presión sobre los servicios. Para ver los pasos, consulte [Pruebas de carga y esfuerzo](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en la Guía de Commerce en la nube.
