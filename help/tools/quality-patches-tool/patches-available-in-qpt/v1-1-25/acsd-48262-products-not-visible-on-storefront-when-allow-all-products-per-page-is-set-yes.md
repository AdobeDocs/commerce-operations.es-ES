---
title: "ACSD-48262: productos no visibles en la tienda cuando [!UICONTROL Allow All Products Per Page] está establecido [!UICONTROL Yes]"
description: Aplique la revisión ACSD-48262 para corregir el problema de Adobe Commerce en el que los productos no son visibles en la tienda cuando la configuración de [!UICONTROL Allow All Products Per Page] está establecida en [!UICONTROL Yes].
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48262: productos no visibles en la tienda cuando [!UICONTROL Allow All Products Per Page] está establecido *[!UICONTROL Yes]*

La revisión ACSD-48262 corrige el problema en el que los productos no son visibles en la tienda cuando la configuración de [!UICONTROL Allow All Products Per Page] está establecida en *[!UICONTROL Yes]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-48262. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La revisión ACSD-48262 corrige el problema en el que los productos no son visibles en la tienda cuando la configuración de [!UICONTROL Allow All Products Per Page] está establecida en *[!UICONTROL Yes]*.

<u>Pasos a seguir</u>:

1. Cree una categoría de prueba.
1. Cree un producto de prueba en la categoría de prueba.
1. Examine el producto para probar la página de categoría en la tienda y asegurarse de que el producto sea visible.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** y establezca la configuración de [!UICONTROL Allow All Products Per Page] en *[!UICONTROL Yes]*.
1. Borrar caché.
1. Comprueba la página de categoría en la tienda.

<u>Resultados esperados</u>:

El producto está visible.

<u>Resultados reales</u>:

El producto no es visible.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
