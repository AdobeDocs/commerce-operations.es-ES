---
title: 'MDVA-38346: Los filtros de fecha no funcionan cuando la zona horaria de Adobe Commerce es diferente de la local'
description: El parche MDVA-38346 resuelve el problema de los filtros de fecha que no funcionan correctamente cuando la zona horaria de Adobe Commerce es diferente de la del entorno local. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-38346. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Configuration
role: Admin
exl-id: 6ed909be-81da-4e06-97c7-4eab8be2ddd2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38346: Los filtros de fecha no funcionan cuando la zona horaria de Adobe Commerce es diferente de la local

El parche MDVA-38346 resuelve el problema de los filtros de fecha que no funcionan correctamente cuando la zona horaria de Adobe Commerce es diferente de la del entorno local. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-38346. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1, 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los filtros de fecha no funcionan correctamente cuando la zona horaria de Adobe Commerce es diferente de la del entorno local.

<u>Pasos a seguir</u>:

1. Cambie la zona horaria a Australia/Sídney.
1. Realizar algunos pedidos.
1. Cree facturas para ellos.
1. Vaya a **Ventas** > **Facturas** y filtre por Fecha de factura (fecha actual - fecha actual).
1. Compruebe las fechas.

<u>Resultados esperados</u>:

La fecha de factura mostrada y la coincidencia de filtro real.

<u>Resultados reales</u>:

La fecha de factura mostrada es anterior en un día al filtro real (fecha actual + 1 día).

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
