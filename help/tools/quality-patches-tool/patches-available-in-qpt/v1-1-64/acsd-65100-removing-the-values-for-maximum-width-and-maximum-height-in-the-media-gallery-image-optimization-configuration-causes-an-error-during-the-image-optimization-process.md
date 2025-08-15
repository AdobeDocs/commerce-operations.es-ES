---
title: 'ACSD-65100: La eliminación de los valores [!UICONTROL Maximum Width] y [!UICONTROL Maximum Height] en la configuración [!UICONTROL Media Gallery Image Optimization] provoca un error'
description: Aplique el parche ACSD-65100 para corregir el problema de Adobe Commerce en el que al eliminar los valores [!UICONTROL Maximum Width] y [!UICONTROL Maximum Height] en la configuración [!UICONTROL Media Gallery Image Optimization] se produce un error durante el proceso de optimización de imágenes.
feature: Media
role: Admin, Developer
exl-id: 86197602-19a1-41c2-b129-1f695f303ce5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-65100: La eliminación de los valores [!UICONTROL Maximum Width] y [!UICONTROL Maximum Height] en la configuración [!UICONTROL Media Gallery Image Optimization] provoca un error

La revisión ACSD-65100 corrige el problema en el cual al eliminar los valores **[!UICONTROL Maximum Width]** y **[!UICONTROL Maximum Height]** en la configuración **[!UICONTROL Media Gallery Image Optimization]** se produce un error durante el proceso de optimización de imágenes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-65100. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error durante el proceso de optimización de imágenes cuando los valores de **[!UICONTROL Maximum Width]** y **[!UICONTROL Maximum Height]** se quitan en la configuración de **[!UICONTROL Media Gallery Image Optimization]**.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**.
1. Quite los valores de **[!UICONTROL Maximum Width]** y **[!UICONTROL Maximum Height]**.
1. Limpie la caché de configuración.
1. Vaya a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Abra cualquier página para editarla.
1. En el área de contenido:
   1. Seleccione **[!UICONTROL Add Layout]** > **[!UICONTROL Row]**.
   1. Seleccione **[!UICONTROL Add Elements]** > **[!UICONTROL Text]**.
   1. En el editor de WYSIWYG, haga clic en **[!UICONTROL Add Image]**.
   1. Cargue una imagen y seleccione **[!UICONTROL Add Selected]**.
1. Compruebe el archivo `var/log/exception.log`.

<u>Resultados esperados</u>:

Sin errores.

<u>Resultados reales</u>:

Se registra un error similar al siguiente:

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
