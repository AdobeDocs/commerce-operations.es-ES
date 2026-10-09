---
title: 'ACSD-66082: No se puede actualizar la imagen de muestra de un producto mediante la importación de productos'
description: Aplique el parche ACSD-66082 para corregir el problema de Adobe Commerce en el que la carga de un archivo CSV con el campo swatch_image establecido en EMPTY_VALUE para anular la configuración de imágenes de muestra provoca que el proceso de importación falle con un error.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
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
source-wordcount: '405'
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

   ```text
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Import]** para importar el archivo ajustando la siguiente configuración:
   * **[!UICONTROL Entity type]**: *Productos*
   * **[!UICONTROL Import Behavior]**: *Agregar/Actualizar*
   * Haga clic en **[!UICONTROL Choose File]** para seleccionar el archivo CSV creado en el paso anterior para importar. La importación se realiza correctamente y se añade la muestra.
1. Actualice el CSV con el siguiente contenido:

   ```text
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
