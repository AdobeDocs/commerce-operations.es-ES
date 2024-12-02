---
title: 'ACSD-51857: El trabajo cron lento de "aggregate_sales_report_bestsellers_data" afecta al rendimiento'
description: Aplique el parche ACSD-51857 para corregir el problema de Adobe Commerce en el que el trabajo cron lento `aggregate_sales_report_bestsellers_data` afecta a grandes tablas de base de datos "sales_order" y "sales_order_item".
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857: el trabajo cron lento de `aggregate_sales_report_bestsellers_data` afecta al rendimiento

El parche ACSD-51857 corrige el problema en el que el trabajo cron lento `aggregate_sales_report_bestsellers_data` afecta a tablas de base de datos grandes `sales_order` y `sales_order_item`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34. El ID del parche es ACSD-51857. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento del trabajo cron de `aggregate_sales_report_bestsellers_data` es lento en `sales_order` y `sales_order_item` tablas de base de datos.

Para resolver esto, se ha vuelto a escribir la consulta de datos principal que captura los datos del informe en un formulario más eficiente. Ahora se utiliza una subconsulta para determinar el subconjunto de datos.

Para que la subconsulta funcionara lo más rápido posible, se agregó un nuevo índice para la tabla de base de datos `sales_order`: `SALES_ORDER_STORE_STATE_CREATED` basado en las columnas `store_id`, `state` y `created_at`.

<u>Requisitos previos</u>

Asegúrese de un gran número de pedidos diarios.

<u>Pasos a seguir</u>

1. Ejecutar el trabajo cron `aggregate_sales_report_bestsellers_data`.
1. Compruebe los datos que se mostrarán en el tablero de administración, en la ficha **[!UICONTROL Bestsellers]**.

<u>Resultados esperados</u>:

*[!UICONTROL Quantity per source]* en la ficha **[!UICONTROL Configuration]** no debería estar vacío.

<u>Resultados reales</u>:

*[!UICONTROL Quantity per source]* en la ficha **[!UICONTROL Configuration]** está vacío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
