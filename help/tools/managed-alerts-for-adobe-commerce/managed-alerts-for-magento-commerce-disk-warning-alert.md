---
title: 'Alertas gestionadas para Adobe Commerce: Alerta de advertencia de disco'
description: Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco de advertencia para Adobe Commerce en  [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 3ad22e3a113b52da6d6095103376fee6e36dc804
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Alertas gestionadas para Adobe Commerce: Alerta de advertencia de disco

Este artículo proporciona pasos para solucionar problemas cuando recibe una alerta de disco de advertencia para Adobe Commerce en [!DNL New Relic]. Se requiere una acción inmediata para solucionar el problema. La alerta tendrá el siguiente aspecto, según el canal de notificación de alerta que haya seleccionado.

![alerta de advertencia de disco](../../assets/managed-alerts/disk-warning-magento-managed.png){width="500"}

## Productos y versiones afectados

* Adobe Commerce en la infraestructura en la nube, arquitectura de plan Pro.

## Problema

Recibirá una alerta en [!DNL New Relic] si se ha registrado en [Alertas administradas para Adobe Commerce](managed-alerts-for-magento-commerce.md) y se han sobrepasado uno o más de los umbrales de alerta. Estas alertas fueron desarrolladas por Adobe para ofrecer a los clientes un conjunto estándar con información de Soporte e Ingeniería.

<u> **Hacer!** </u>

* Anule cualquier implementación programada hasta que se borre esta alerta.
* Ponga su sitio en modo de mantenimiento inmediatamente si su sitio no responde o se vuelve completamente insensible. Para ver los pasos, consulte [Habilitar o deshabilitar el modo de mantenimiento](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) en la Guía de instalación de Commerce. Asegúrese de añadir su IP a la lista de direcciones IP exentas para asegurarse de que aún puede acceder al sitio para solucionar problemas. Para ver los pasos, consulte [Mantener la lista de direcciones IP exentas](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) en la Guía de instalación de Commerce.

<u> **¡No!** </u>

* Inicie campañas de marketing adicionales que puedan llevar vistas de página adicionales al sitio.
* Ejecute indexadores o crons adicionales que puedan causar una tensión adicional en el CPU o el disco.
* Realice las principales tareas administrativas (por ejemplo, administración de Commerce, importación/exportación de datos).
* Borre la caché. Es posible que el sitio no responda (si aún no está experimentando una interrupción del sitio) si realiza alguna de las acciones &quot;No&quot; antes de haber investigado y resuelto la causa de la alerta.

## Solución

Siga estos pasos para identificar y solucionar los problemas de la causa:

1. En [!DNL New Relic], revise los discos para el uso más alto. Para ver los pasos, consulte la ficha **[!UICONTROL Storage]** en la página [[!DNL New Relic] Hosts de supervisión de infraestructura: ficha [!UICONTROL Storage]](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/#storage):
   * Si en [!DNL New Relic] observa un aumento lento en el uso del disco, pruebe las siguientes opciones:
      * Optimización del espacio en disco mediante el ajuste de la asignación de espacio. Para ver los pasos, consulte [Administrar espacio en disco](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) en la Guía de Commerce en la nube. También es posible que deba solicitar más espacio en disco (póngase en contacto con el equipo de cuenta de Adobe).
      * Borrar espacio en disco para MySQL. Consulte [El espacio en disco de MySQL es bajo](http://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-disk-space-is-low-on-magento-commerce-cloud) para ver los pasos.
      * Si [!DNL New Relic] muestra un uso de disco que aumenta rápidamente, esto podría indicar que hay un problema que ha causado que un archivo aumente muy rápidamente en un directorio. Realice las siguientes comprobaciones:
         1. Compruebe el espacio en disco general para identificar el problema ejecutando el siguiente comando en CLI/Terminal: `df -h`
         1. Después de identificar un directorio con un uso de disco inesperadamente grande y creciente, debe comprobar el sistema de archivos afectado. El ejemplo siguiente muestra cómo comprobar el directorio de archivos `pub/media/`. Este es el directorio que utiliza Adobe Commerce para almacenar registros y archivos multimedia grandes. Sin embargo, debe ejecutar este comando para cualquier directorio que muestre un uso de disco inesperado: `du -sch ~/pub/media/*`.

Si la salida del terminal muestra un archivo en uno de estos directorios aumentando rápidamente el uso del disco y sabe que el contenido del archivo no es necesario, considere la posibilidad de quitar el archivo. Si no se siente cómodo al realizar esta acción, [envíe un ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
