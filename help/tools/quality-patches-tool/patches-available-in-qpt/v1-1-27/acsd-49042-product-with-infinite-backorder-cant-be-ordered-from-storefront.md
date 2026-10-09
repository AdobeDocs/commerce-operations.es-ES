---
title: 'ACSD-49042: El producto con un pedido pendiente infinito no se puede pedir desde la tienda'
description: Aplique el parche ACSD-49042 para corregir el problema de Adobe Commerce en el que un producto con un pedido pendiente infinito no se puede pedir desde la tienda.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%
---
# ACSD-49042: El producto con un pedido pendiente infinito no se puede pedir desde la tienda

El parche ACSD-49042 soluciona el problema de que un producto con un pedido pendiente infinito no se puede pedir desde la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27. El ID del parche es ACSD-49042. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error se produce cuando un producto con un pedido pendiente infinito no se puede pedir desde la tienda.

<u>Pasos a seguir</u>:

1. Establezca las siguientes opciones de configuración:
   * **[!UICONTROL Display Out of Stock Products]** se estableció en *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** se estableció en *[!UICONTROL Allow Qty Below 0]*.
1. Agregar **[!DNL custom stock]** y **[!DNL custom source]** nuevos.
1. Asigne un producto a **[!DNL custom source]** y asegúrese de que haya un número de inventario establecido para él (por ejemplo: *10*).
1. En la página de edición del producto, abra **[!UICONTROL Advanced Inventory]**. Establezca **[!UICONTROL minimum quantity]** en el carro de compras (por ejemplo: *160*). La cantidad debe estar por encima del inventario.
1. Vaya a la tienda y compre un producto para crear una reserva.
1. Cambiar **[!UICONTROL product quantity]** a *0*. El punto crítico es guardar el producto de **[!DNL Admin panel]** cuando hay una reserva.
1. Abra **[!UICONTROL product page]** en la tienda e intente agregar el producto al carro de compras.

<u>Resultados esperados</u>:

Es posible agregar el producto al carro de compras porque se permiten pedidos pendientes de una cantidad inferior a *0*.

<u>Resultados reales</u>:

Se muestra que el producto está agotado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
