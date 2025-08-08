---
title: 'ACSD-66082: No se puede actualizar la imagen de muestra de un producto mediante la importación de productos'
description: Aplique el parche ACSD-66082 para corregir el problema de Adobe Commerce en el que la carga de un archivo CSV con el campo swatch_image establecido en EMPTY_VALUE para anular la configuración de imágenes de muestra provoca que el proceso de importación falle con un error.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: bdd15514c6b6ece6c7f33a41267357b4a24261f1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-66082: No se puede actualizar la imagen de muestra de un producto mediante la importación de productos

El parche ACSD-66082 corrige el problema en el que no era posible actualizar la imagen de muestra de un producto mediante la importación de productos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66082. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si se carga un archivo CSV con el campo `swatch_image` establecido en `EMPTY_VALUE` para anular la configuración de las imágenes de muestra, el proceso de importación fallará y producirá un error.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Haga clic en la flecha hacia abajo situada junto al botón **[!UICONTROL Add Product]** y seleccione **[!UICONTROL Simple Product]**. Establezca su **[!UICONTROL SKU]** en *ABC*.
1. Cargue una imagen PNG llamada *testing.png* a `var/import/images/`.
1. Cree un archivo CSV con el siguiente contenido:

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Import]** para importar el archivo ajustando la siguiente configuración:
   * **[!UICONTROL Entity type]**: *Productos*
   * **[!UICONTROL Import Behavior]**: *Agregar/Actualizar*
   * Haga clic en **[!UICONTROL Choose File]** para seleccionar el archivo CSV creado en el paso anterior para importar. La importación se realiza correctamente y se añade la muestra.
1. Actualice el CSV con el siguiente contenido:

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Repita el proceso de importación.

<u>Resultados esperados</u>:

La imagen de muestra no está configurada.

<u>Resultados reales</u>:

El proceso de importación genera un error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
