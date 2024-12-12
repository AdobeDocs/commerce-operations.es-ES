---
title: 'ACSD-52095: La administración del valor de stock es incorrecta al exportar el CSV'
description: Aplique el parche ACSD-52095 para corregir el problema de Adobe Commerce en el que el valor de stock de administración de productos es incorrecto al exportar CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '366'
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en la guía [!DNL Quality Patches Tool].
