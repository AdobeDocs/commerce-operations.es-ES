---
title: 'ACSD-62056: la carga de imágenes para el producto configurable falla si MSI está instalado'
description: Aplique el parche ACSD-62056 para corregir el problema de Adobe Commerce en el que las imágenes de los productos configurables no se agregan si MSI está instalado.
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: la carga de imágenes para el producto configurable falla si MSI está instalado

El parche ACSD-62056 corrige el problema de que no se agregan imágenes para productos configurables si MSI está instalado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-62056. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al editar un producto configurable con [!UICONTROL Inventory Management/MSI] habilitado, las opciones para agregar imágenes no funcionan. Esto afecta a las opciones [!UICONTROL Apply a single set of images to all SKUs] y [!UICONTROL Apply unique images by attribute to each SKU].

<u>Requisitos previos</u>:

Los módulos [!UICONTROL Inventory Management/MSI] están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Cree una nueva fuente.
1. Cree un nuevo inventario de stock y asigne el nuevo origen.
1. Editar un producto configurable.
1. Haga clic en **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Seleccione cualquiera de las siguientes opciones y añada una imagen.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Resultados esperados</u>:

Se añaden las imágenes.

<u>Resultados reales</u>:

Las imágenes no se agregan.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
