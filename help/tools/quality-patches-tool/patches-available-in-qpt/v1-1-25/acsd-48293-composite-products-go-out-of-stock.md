---
title: 'ACSD-48293: productos compuestos agotados al agotarse los productos infantiles repuestos'
description: Aplique el parche ACSD-48293 para corregir el problema de Adobe Commerce en el que los productos compuestos no están en existencias cuando los productos secundarios agotados vuelven a estar en existencias.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '461'
ht-degree: 0%
---
# ACSD-48293: productos compuestos agotados al agotarse los productos infantiles repuestos

El parche ACSD-48293 soluciona el problema de que los productos compuestos se agotan cuando los productos secundarios agotados vuelven a estar en existencias. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25. El ID del parche es ACSD-48293. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos compuestos se agotan cuando los productos secundarios que se agotaron vuelven a estar en existencias.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda secundarios.
1. Cree dos orígenes y existencias y asígnelos a cada sitio web.
1. Habilite la opción mostrar productos sin existencias en **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Cree un producto configurable con un producto asociado utilizando la fuente de stock del sitio web principal (cantidad establecida = 1).
1. Realice un pedido del producto configurable.
1. Corre el cron.
1. Abra el producto configurable de la tienda y confirme que está agotado.
1. Abra el producto configurable de [!UICONTROL Admin] y establezca **[!UICONTROL Manage Stock Option]** en *[!UICONTROL No]*.
1. Corre el cron.
1. Envíe el pedido y añada la cantidad al producto simple para que esté disponible.
1. Corre el cron.
1. Compruebe la disponibilidad del producto en la tienda.

<u>Resultados esperados</u>:

El producto configurable está en stock.

<u>Resultados reales</u>:

El producto configurable está agotado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
