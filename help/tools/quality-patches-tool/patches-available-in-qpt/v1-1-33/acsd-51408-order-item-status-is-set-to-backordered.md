---
title: "ACSD-51408: el estado del elemento de pedido no se ha establecido correctamente en [!UICONTROL backordered]"
description: Aplique el parche ACSD-51408 para corregir el problema de Adobe Commerce en el que el estado del elemento de pedido está establecido incorrectamente en [!UICONTROL backordered].
feature: B2B, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# ACSD-51408: el estado del elemento de pedido se ha establecido incorrectamente en *[!UICONTROL backordered]*

El parche ACSD-51408 corrige el problema en el que el estado del elemento de pedido se establece incorrectamente en [!UICONTROL backordered]. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51408. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del elemento de pedido se ha establecido incorrectamente en *[!UICONTROL backordered]*.

<u>Requisitos previos</u>:

Los módulos Adobe Commerce B2B y Inventory management (MSI) están instalados.

<u>Pasos a seguir</u>:

1. Crear un nuevo sitio web, tienda y vista de tienda.
1. Cree una nueva fuente.
1. Cree un nuevo inventario vinculado al nuevo sitio web creado en el paso 1 y asigne el origen creado en el paso 2.
1. Cree una empresa y asígnela al nuevo sitio web creado en el paso 1.
1. Cree un nuevo cliente y asígnelo a la compañía creada en el paso 4.
1. Cree un producto, asígnelo al nuevo sitio web y establezca **[!UICONTROL default stock]** = *0*, y **[!UICONTROL new stock]** en mayor que *0*.
1. Habilitar **[!UICONTROL backorders]**.
1. Habilite el método de pago **[!UICONTROL Check/Money Order]** para el nuevo ámbito del sitio web.
1. Habilite **[!UICONTROL Flat Rate shipping method]** para el nuevo ámbito del sitio web.
1. Cree un nuevo pedido a partir de **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Seleccione el nuevo cliente creado en el paso 5.
1. Seleccione el nuevo almacén creado en el paso 1.
1. Elija el producto creado en el paso 6.
1. Rellene la información del pedido, incluidos los métodos de pago y envío.
1. Envíe el pedido.
1. Comprueba el *estado del elemento*.

<u>Resultados esperados</u>

El artículo está disponible para su envío desde el inventario. El estado del elemento es *[!UICONTROL ordered]*.

<u>Resultados reales</u>

El estado del elemento es *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[El estado del artículo de pedido se ha establecido incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0.](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
