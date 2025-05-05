---
title: 'ACSD-48234: resultado de la búsqueda en el catálogo recuento incorrecto de elementos de categoría cuando [!UICONTROL Display Out of Stock Products] está habilitado'
description: Aplique el parche ACSD-48234 para solucionar el problema de Adobe Commerce donde el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción [!UICONTROL Display Out of Stock Products] está habilitada.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
exl-id: c177f12d-2db5-48e2-8f88-ff589cea4dd4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234: el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría **[!UICONTROL Display Out of Stock Products]** habilitados

El parche ACSD-48234 resuelve el problema en el que el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción **[!UICONTROL Display Out of Stock Products]** está habilitada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-48234. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.


## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción **[!UICONTROL Display Out of Stock Products]** está habilitada.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y abra el atributo **[!UICONTROL color]**.
1. Añada dos opciones, por ejemplo, naranja y verde. Guarde el atributo.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** y agregue el atributo **[!UICONTROL color]** al conjunto de atributos **[!UICONTROL Default]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** y establezca **[!UICONTROL Display Out of Stock Products]** en _Sí_.
1. Crear categoría &quot;cat1&quot;.
1. Cree dos productos:
   1. Nombre: prod1, Color: orange, Categorías: cat1.
   1. Nombre: prod2, Color: green, Categorías: cat1.
1. Abra la categoría cat1 en la tienda.
1. Seleccione el color naranja en la navegación por capas.

<u>Resultados esperados</u>:

Solo se muestra el producto prod1.

<u>Resultados reales</u>:

Se muestran los productos prod1 y prod2.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
