---
title: "ACSD-51238: El origen de inventario se elimina al actualizar un producto configurable y editar el precio"
description: Aplique el parche ACSD-51238 para solucionar el problema de Adobe Commerce en el que se elimina el origen de inventario al actualizar un producto configurable y editar el precio.
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51238: el origen de inventario se elimina al actualizar un producto configurable y editar el precio

El parche ACSD-51238 corrige el problema en el que se elimina el origen de inventario al actualizar un producto configurable y editar el precio. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.32. El ID del parche es ACSD-51238. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El origen de inventario se elimina al actualizar un producto configurable y editar el precio.

<u>Pasos a seguir</u>:

1. Instalar **[!DNL Adobe Commerce]** con **[!DNL Inventory module]**
1. Vaya a **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** y cree *dos orígenes* y *dos existencias*.
1. Crear un(a) **[!UICONTROL configurable product]** y asignarlo a **[!UICONTROL default sources]** o **[!UICONTROL newly created sources]**.
1. Haga clic en **[!UICONTROL next button]** y *guarde* el producto.
1. Ahora edite el mismo(a) **[!UICONTROL Configurable Product]** y haga clic en **[!UICONTROL Edit Configuration]** dentro de **[!UICONTROL Configuration tab]**.
1. En `Step 3: Bulk Images,Price and Quantity`, cambie `price` y deje `Quantity` y `Images` a `Skip quantity at this time` y `Skip image uploading at this time` respectivamente.
1. Haga clic en **[!UICONTROL next button]** y genere el producto.

<u>Resultados esperados</u>

La cantidad por origen dentro de **[!UICONTROL Configuration tab]** no debe estar vacía.

<u>Resultados reales</u>

La cantidad por origen dentro de **[!UICONTROL Configuration tab]** está vacía.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](</help/tools/quality-patches-tool/usage.md>) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) en la guía [!DNL Quality Patches Tool].
