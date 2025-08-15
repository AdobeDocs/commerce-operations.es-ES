---
title: 'Alertas administradas para Adobe Commerce: Alerta de disco crítico'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco crítica para Adobe Commerce en  [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 1378dcfd-cf7c-4234-82bb-6697e23d54ca
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Alertas administradas para Adobe Commerce: Alerta de disco crítico

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco crítica para Adobe Commerce en [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta crítica de disco](../../assets/managed-alerts/disk-critical-magento-managed.png){width="500"}

## Productos y versiones afectados

Infraestructura en la nube de Adobe Commerce en arquitectura de plan Pro

## Problema

Recibirá una alerta en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode). Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).

**¡No!**

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar una tensión adicional en el CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché.

Es posible que el sitio no responda (si aún no está experimentando una interrupción del sitio) si realiza alguna de las acciones &quot;No&quot; antes de haber investigado y resuelto la causa de la alerta.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa.

>[!WARNING]
>
>Como se trata de una alerta crítica, se recomienda completar el **Paso 1** antes de intentar solucionar el problema (Paso 2 en adelante).

1. Compruebe si existe un ticket de asistencia de Adobe Commerce. Para ver los pasos, consulte [Rastrear los vales de soporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) en la Base de conocimiento de soporte de Commerce. Es posible que el equipo de asistencia haya recibido una alerta de umbral [!DNL New Relic], haya creado un ticket y haya empezado a trabajar en el problema. Si no existe ningún ticket, cree uno. El ticket debe tener la siguiente información:
   * Motivo del contacto: seleccione **[!UICONTROL New Relic CRITICAL alert received]**.
   * Descripción de la alerta.
   * [[!DNL New Relic] Vínculo de incidente](https://docs.newrelic.com/docs/alerts/incident-management/view-event-details-incidents/). Esto se incluye en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. En [!DNL New Relic], revise los discos para el uso más alto. Para ver los pasos, consulte la ficha **[!UICONTROL Storage]** en la página [[!DNL New Relic] Hosts de supervisión de infraestructura: ficha [!UICONTROL Storage]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * Si en [!DNL New Relic] observa un aumento lento en el uso del disco, pruebe las siguientes opciones:
      * Optimización del espacio en disco mediante el ajuste de la asignación de espacio. Para ver los pasos, consulte [Administrar espacio en disco](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space.html) en la Guía de Commerce en la nube. También es posible que deba solicitar más espacio en disco (póngase en contacto con el equipo de cuenta de Adobe).
      * Borrar espacio en disco para MySQL. Consulte [El espacio en disco de MySQL es bajo](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) en la Base de conocimiento de soporte de Commerce para ver los pasos.
      * Si [!DNL New Relic] muestra un uso de disco que aumenta rápidamente, esto podría indicar que hay un problema que ha causado que un archivo aumente muy rápidamente en un directorio. Realice las siguientes comprobaciones:
         1. Compruebe el espacio en disco general para identificar el problema ejecutando el siguiente comando en CLI/Terminal: `df -h`
         1. Después de identificar un directorio con un uso de disco inesperadamente grande y creciente, debe comprobar el sistema de archivos afectado. El ejemplo siguiente muestra cómo comprobar el directorio de archivos `pub/media/`. Este es el directorio que utiliza Commerce para almacenar registros y archivos multimedia grandes. Sin embargo, debe ejecutar este comando para cualquier directorio que muestre un uso de disco inesperado: `du -sch ~/pub/media/*`

Si la salida del terminal muestra un archivo en uno de estos directorios aumentando rápidamente el uso del disco y sabe que el contenido del archivo no es necesario, considere la posibilidad de quitar el archivo. Si no se siente cómodo al realizar esta acción, [envíe un ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
