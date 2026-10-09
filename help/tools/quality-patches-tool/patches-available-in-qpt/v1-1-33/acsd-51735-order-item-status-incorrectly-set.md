---
title: 'ACSD-51735: el estado del elemento de pedido se estableció incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0'
description: Aplique el parche ACSD-51735 para corregir el problema de Adobe Commerce en el que el estado del elemento de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0.
feature: Orders, Products
role: Admin
exl-id: 56c8b58c-819f-46bd-8912-f543f56b66d6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%
---
# ACSD-51735: el estado del elemento de pedido se estableció incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0

El parche ACSD-51735 corrige el problema en el que el estado del elemento de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.33. El ID del parche es ACSD-50895. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del artículo de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock del producto es 0.

<u>Requisitos previos</u>:

* Los módulos de Adobe Commerce Inventory management (MSI) están instalados.
* Los pedidos no satisfechos están habilitados en **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** > **[!UICONTROL Backorders]**.

<u>Pasos a seguir</u>:

1. Cree un nuevo inventario de stock.
1. Cree una nueva fuente.
1. Asigne el sitio web predeterminado al nuevo inventario y asigne el nuevo origen.
1. Cree un nuevo producto.

   * Establezca la cantidad de origen predeterminada en 10 y la nueva cantidad de origen en 0.

1. Añadir el producto al carro de compras en la tienda.
1. Observe la advertencia de pedido pendiente al cerrar la compra, lo que indica que el producto proviene de una nueva fuente.
1. Realice el pedido.
1. Abra el pedido en Administración y compruebe el estado del pedido pendiente.

<u>Resultados esperados</u>:

El orden muestra que la cantidad 1 está en espera.

<u>Resultados reales</u>:

El orden muestra que la cantidad 1 está ordenada, no pendiente.

>[!MORELIKETHIS]
>
>[El estado del elemento de pedido se ha establecido incorrectamente en *[!UICONTROL Backordered]*](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51408-order-item-status-is-set-to-backordered.md)

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
