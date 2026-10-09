---
title: 'Alertas administradas en Adobe Commerce: alertas de MariaDB'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe alertas MariaDB para Adobe Commerce en [!DNL New Relic]. Las alertas de MariaDB supervisan la carga de consultas alta, así como las consultas de lenguaje de manipulación de datos (DML) excesivas. Ambos pueden llevar a una experiencia del usuario degradada o incluso a un tiempo de inactividad. Puede recibir dos tipos de alertas.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%
---
# Alertas administradas en Adobe Commerce: alertas de MariaDB

Este artículo proporciona pasos para solucionar problemas cuando recibe alertas MariaDB para Adobe Commerce en [!DNL New Relic]. Las alertas de MariaDB supervisan la carga de consultas alta, así como las consultas de lenguaje de manipulación de datos (DML) excesivas. Ambos pueden llevar a una experiencia del usuario degradada o incluso a un tiempo de inactividad. Puede recibir dos tipos de alertas:

* Advertencia de consultas DML
* Consultas DML Críticas

## Productos y versiones afectados

Arquitectura del plan Pro de Adobe Commerce en la infraestructura en la nube

## Problema

Recibirá una alerta administrada en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

**Hacer!**

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](/help/installation/tutorials/maintenance-mode.md) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](/help/installation/tutorials/maintenance-mode.md#maintain-the-list-of-exempt-ip-addresses).
* Finalice los scripts, como las importaciones, que puedan ser la causa de la alerta si el rendimiento del sitio se ve afectado.

**¡No!**

* Ejecute indexadores o crones adicionales que puedan causar un estrés adicional en MariaDB.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

**Consultas DML (consultas que modifican la base de datos mediante UPDATE, INSERT y DELETE)**

Si recibe una alerta de consultas críticas de DML, comience en el paso uno. Si recibe una alerta de advertencia de consultas DML, comience en el paso dos.

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulte nuestra base de conocimiento [Seguimiento de los tickets de asistencia](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#track-support-case). Es posible que el equipo de asistencia haya recibido una alerta de umbral [!DNL New Relic], haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
   * Motivo del contacto: seleccione **[!UICONTROL New Relic MariaDB alert received]**.
   * Descripción de la alerta.
   * [[!DNL New Relic] Vínculo de incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Esto se incluye en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Para identificar el origen del problema, intente identificar las consultas DML:
   1. Revise las operaciones de la base de datos mediante los pasos de la página [Bases de datos de New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time).
   1. Ordenar por **[!UICONTROL CALL COUNT]** y después **[!UICONTROL OPERATION]**. Revisar las operaciones de `INSERT`, `DELETE` y `UPDATE`.
   1. Busque una media alta.
   1. Haga clic para buscar llamadores de operaciones de base de datos. Esto identificará las transacciones que utilizan esa consulta por tiempo.
   1. Busque optimizaciones de código u optimizaciones operativas:
      * Optimizaciones de código: busque optimizar las consultas con inserciones/actualizaciones masivas, minimizando el uso del índice o restringiendo el código.
      * Optimizaciones operativas: descargue las modificaciones de datos que requieren muchos recursos para reducir los tiempos de tráfico.
      * Optimizaciones adicionales: Asegúrese de que está en la última versión de ECE-Tools. Para ver los pasos, consulte [Actualizar ece-tools version](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) en la Guía de Commerce en la nube.
