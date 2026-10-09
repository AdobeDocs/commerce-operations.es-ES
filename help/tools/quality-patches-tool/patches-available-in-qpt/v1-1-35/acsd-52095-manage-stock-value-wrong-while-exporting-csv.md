---
title: 'ACSD-52095: La administración del valor de stock es incorrecta al exportar el CSV'
description: Aplique el parche ACSD-52095 para corregir el problema de Adobe Commerce en el que el valor de stock de administración de productos es incorrecto al exportar CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-52095: el valor [!UICONTROL Manage Stock] no es correcto al exportar el CSV

El parche ACSD-52095 corrige el problema en el que el valor del producto `manage_stock` es incorrecto al exportar CSV. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52095. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El valor `manage_stock` se establece incorrectamente en 0 en el archivo CSV después de la exportación del producto.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** y establezca **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Cree un nuevo producto y guárdelo.
1. Ir a **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Seleccione *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* y exporte los productos.
1. Compruebe el archivo CSV generado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. De nuevo, vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** y establezca **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Vaya a **Sistema** > **Exportar**.
Seleccionar *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Compruebe el archivo CSV generado: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Abra el producto en el Administrador, vaya a **[!UICONTROL Advanced Inventory]** y compruebe el valor **[!UICONTROL Manage Stock]**.

<u>Resultados esperados</u>

El valor **[!UICONTROL Manage Stock]** es *1* cuando está habilitado para los productos.

<u>Resultados reales</u>

El valor **[!UICONTROL Manage Stock]** es *0* cuando está habilitado para los productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
