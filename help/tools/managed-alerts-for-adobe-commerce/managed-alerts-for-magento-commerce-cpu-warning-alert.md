---
title: 'Alertas administradas para Adobe Commerce: alerta de advertencia de CPU'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de advertencia de CPU para Adobe Commerce en  [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 09b5331df0b7504b1a3a792d4203f0eaaab842cc
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---


# Alertas administradas para Adobe Commerce: alerta de advertencia de CPU

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de advertencia de CPU para Adobe Commerce en [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![Alerta de advertencia de CPU](../../assets/managed-alerts/cpu-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde completamente. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) en la Guía de instalación de Commerce.

<u>**¡No!**</u>

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar una tensión adicional en el CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

1. Use la [[!DNL New Relic] página de transacciones de APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) para identificar transacciones con problemas de rendimiento:
   * Ordene las transacciones en [!DNL Apdex] puntuaciones en orden ascendente. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) hace referencia a la satisfacción del usuario con el tiempo de respuesta de sus aplicaciones y servicios web. [Una puntuación [!DNL Apdex] baja](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce) puede indicar un cuello de botella (una transacción con un tiempo de respuesta más alto). Normalmente es la base de datos, [!DNL Redis], o PHP. Para ver los pasos, consulte [!DNL New Relic] [Ver transacciones con mayor [!DNL Apdex] insatisfacción](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#apdex-dissat).
   * Ordene las transacciones por el mayor rendimiento, el tiempo de respuesta medio más lento, el tiempo más lento y otros umbrales. Para ver los pasos, consulte [[!DNL New Relic] Buscar problemas de rendimiento específicos](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Si sigue teniendo problemas para identificar el origen, use la [[!DNL New Relic] página Infraestructura de APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/) para identificar los servicios con recursos pesados. Para ver los pasos, consulte [!DNL New Relic] [Página de hosts de supervisión de infraestructura: [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Si identifica la fuente, SSH en el entorno para investigar más a fondo. Para ver los pasos, consulte [SSH en su entorno](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) en la Guía de Commerce en la nube.
1. Si sigue teniendo problemas para identificar la fuente:
   * Revise las tendencias recientes para identificar los problemas con las implementaciones de código o los cambios de configuración recientes (por ejemplo, nuevos grupos de clientes y grandes cambios en el catálogo). Se recomienda revisar los últimos siete días de actividad para cualquier correlación en implementaciones o cambios de código.
   * Considere la posibilidad de buscar y deshabilitar catálogos planos. Para ver los pasos, consulte [Funcionamiento lento, crons lentos y de larga duración](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) en la Base de conocimiento de asistencia de Commerce.
   * Si sospecha que está experimentando un ataque DDoS, intente bloquear el tráfico de bots. Para ver los pasos, consulte [Cómo bloquear el tráfico malintencionado para Adobe Commerce en el nivel Fastly](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) en la Base de conocimiento de asistencia de Commerce.
1. Si el problema parece temporal, realice pasos de mitigación como un aumento de tamaño o ponga el sitio en modo de mantenimiento. Para ver los pasos, consulte [Cómo solicitar el cambio de tamaño temporal](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) en la Base de conocimiento de soporte técnico de Commerce y [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Si el cambio de tamaño devuelve el sitio a las operaciones normales, considere la posibilidad de solicitar un cambio de tamaño permanente (póngase en contacto con el equipo de cuenta de Adobe) o intente reproducir el problema en el ensayo dedicado ejecutando una prueba de carga y optimizando las consultas, o código que reduzca la presión sobre los servicios. Para ver los pasos, consulte [Pruebas de carga y estrés](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) en la Guía de Commerce en la nube.
