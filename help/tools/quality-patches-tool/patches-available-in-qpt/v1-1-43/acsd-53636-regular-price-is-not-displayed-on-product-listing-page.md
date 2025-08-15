---
title: 'ACSD-53636: el precio normal no se muestra en la página [!UICONTROL Product Listing]'
description: Aplique el parche ACSD-53636 para corregir el problema de Adobe Commerce en el que el precio normal no se muestra en páginas *[!UICONTROL Product Listing]* para productos configurables que tienen productos secundarios con precios especiales.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636: el precio normal no se muestra en la página *[!UICONTROL Product Listing]*

El parche ACSD-53636 corrige el problema en el que el precio normal no se muestra en *[!UICONTROL Product Listing]* páginas para productos configurables que tienen productos secundarios con precios especiales. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. El ID del parche es ACSD-53636. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio normal no se muestra en *[!UICONTROL Product Listing]* páginas para productos configurables que tienen productos secundarios con precios especiales.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador, vaya a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** y cree o abra cualquier producto configurable.
2. Abra el producto secundario y agregue un precio especial a todos o a uno de los productos secundarios y guarde el producto.
3. Vaya a front-end y abra la página **[!UICONTROL Product Detail]** del producto configurable; en las muestras del producto secundario con precio especial, verá el *[!UICONTROL Regular price]* tachado (esperado).
4. Vaya a front-end y abra la página **[!UICONTROL Product Listing]** del producto configurable con precio especial; compruebe que los cambios de muestra del producto configurable no muestren el precio normal, a diferencia de *[!UICONTROL Product Detail Page]* y otros productos simples.

<u>Resultados esperados</u>:

En la página *[!UICONTROL Product Listing]*, el producto configurable muestra el precio normal de su producto secundario.

<u>Resultados reales</u>:

En la página *[!UICONTROL Product Listing]*, el producto configurable no muestra el precio normal para su producto secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
