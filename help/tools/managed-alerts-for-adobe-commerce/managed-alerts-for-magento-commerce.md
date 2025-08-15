---
title: Alertas administradas para Adobe Commerce
description: Si es cliente de Adobe Commerce en una infraestructura en la nube, puede utilizar alertas administradas para comprender el estado del sitio. Si es cliente del plan de arquitectura del plan inicial de Adobe Commerce en la infraestructura en la nube, solo recibirá alertas por las condiciones de  [!DNL Apdex]  y tasa de error.
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce


Hemos configurado paneles y alertas clave para ayudarle a comprender cuándo su sitio alcanza niveles de almacenamiento críticos y [!DNL Apdex] (satisfacción de los usuarios con las aplicaciones y el tiempo de respuesta de los servicios). Esto puede ayudarle a tomar medidas antes de que note tiempos de respuesta lentos o una interrupción del servicio. Podrá solucionar los problemas de las alertas con los artículos que se enumeran a continuación. Antes de poder utilizar las alertas, primero configure los canales de notificación. Consulte [[!DNL New Relic] Configuración de canales de notificación](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) en la Guía de Commerce en la nube.

>[!NOTE]
>
>Si las alertas administradas para la directiva de alertas de Adobe Commerce no están disponibles, podría deberse a que esta cuenta se ha creado recientemente o a que [!DNL New Relic] se ha configurado recientemente. Todos los martes se ejecuta un proceso para agregar la directiva de alerta a esas cuentas. La directiva de alertas debe estar disponible el día siguiente a la ejecución del siguiente proceso. Si la directiva aún no se encuentra, [envíe una solicitud de soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) e incluya su ID de proyecto.

Consulte a continuación en la tabla los vínculos a los artículos de la BC que proporcionan pasos para la resolución de problemas de estas alertas:

* Alertas administradas para Adobe Commerce: alerta de advertencia de CPU
* Alertas administradas para Adobe Commerce: Alerta crítica de CPU
* Alertas administradas para Adobe Commerce: alerta de advertencia de memoria
* Alertas administradas para Adobe Commerce: alerta crítica de memoria
* Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta de advertencia
* Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta crítica
* Alertas administradas para Adobe Commerce: alerta de advertencia de disco
* Alertas administradas para Adobe Commerce: alerta de disco crítico
* Alertas administradas en Adobe Commerce: alertas de MariaDB
* Alertas administradas en Adobe Commerce: [!DNL Redis] alerta de advertencia de memoria
* Alertas administradas en Adobe Commerce: [!DNL Redis] alerta crítica de memoria

>[!NOTE]
>
>Los umbrales establecidos para las alertas de advertencia y las alertas críticas se basan en la investigación que estamos realizando utilizando datos de rendimiento históricos en nuestra base de clientes y representan las últimas perspectivas de los equipos de ingeniería y soporte de Adobe Commerce. Tenga en cuenta que estos umbrales están sujetos a cambios según el análisis más reciente y en curso. El flujo de alertas típico es recibir alertas de menor a mayor en términos de gravedad. Por lo tanto, es probable que reciba una alerta de advertencia antes de recibir una alerta crítica. Consulte los vínculos a artículos para ver los pasos de solución de problemas.

| Gravedad | CPU | Memoria | Disco | [!DNL Apdex] | MariaDB | Memoria [!DNL Redis] | Artículo de resolución de problemas |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Advertencia | ✅ |        |      |       |         |              | [Alertas administradas para Adobe Commerce: alerta de advertencia de CPU](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Crítico | ✅ |        |      |       |         |              | [Alertas administradas para Adobe Commerce: alerta crítica de CPU](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Advertencia |     | ✅ |      |       |         |              | [Alertas administradas para Adobe Commerce: alerta de advertencia de memoria](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Crítico |     | ✅ |      |       |         |              | [Alertas administradas para Adobe Commerce: alerta crítica de memoria](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Advertencia |     |        |      | ✅ |         |              | [Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta de advertencia](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Crítico |     |        |      | ✅ |         |              | [Alertas administradas para Adobe Commerce: [!DNL Apdex] alerta crítica](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Advertencia |     |        | ✅ |       |         |              | [Alertas administradas para Adobe Commerce: alerta de advertencia de disco](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Crítico |     |        | ✅ |       |         |              | [Alertas administradas para Adobe Commerce: alerta crítica de disco](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Advertencia y elementos críticos |     |        |      |       | ✅ |              | [Alertas administradas en Adobe Commerce: alertas de MariaDB](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Advertencia |     |        |      |       |         | ✅ | [Alertas administradas en Adobe Commerce: [!DNL Redis] alerta de advertencia de memoria](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Crítico |     |        |      |       |         | ✅ | [Alertas administradas en Adobe Commerce: [!DNL Redis] Alerta crítica de memoria](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |
