---
title: 'Alertas administradas en Adobe Commerce: alertas de MariaDB'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe alertas MariaDB para Adobe Commerce en  [!DNL New Relic]. Las alertas de MariaDB supervisan la carga de consultas alta, así como las consultas de lenguaje de manipulación de datos (DML) excesivas. Ambos pueden llevar a una experiencia del usuario degradada o incluso a un tiempo de inactividad. Puede recibir dos tipos de alertas.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '518'
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
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Finalice los scripts, como las importaciones, que puedan ser la causa de la alerta si el rendimiento del sitio se ve afectado.

**¡No!**

* Ejecute indexadores o crones adicionales que puedan causar un estrés adicional en MariaDB.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

## Solución

**Consultas DML (consultas que modifican la base de datos mediante UPDATE, INSERT y DELETE)**

Si recibe una alerta de consultas críticas de DML, comience en el paso uno. Si recibe una alerta de advertencia de consultas DML, comience en el paso dos.

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulte nuestra base de conocimiento [Seguimiento de los tickets de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). Es posible que el equipo de asistencia haya recibido una alerta de umbral [!DNL New Relic], haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
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
