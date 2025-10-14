---
title: 'ACSD-64113: error del administrador al cargar una imagen con una anchura menor que la altura mediante  [!DNL Media Gallery]'
description: Aplique el parche ACSD-64113 para corregir el problema de Adobe Commerce en el que el administrador produce errores al cargar imágenes con una anchura relativamente pequeña en comparación con su altura (o viceversa) a través de  [!DNL Media Gallery].
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: error del administrador al cargar una imagen con una anchura menor que la altura mediante [!DNL Media Gallery]

El parche ACSD-64113 corrige el problema en el que se producen errores en el administrador al cargar imágenes con una anchura relativamente pequeña en comparación con su altura (o viceversa) a través de [!DNL Media Gallery]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-64113. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se producen errores en el administrador al cargar imágenes con una anchura relativamente pequeña en comparación con su altura (o viceversa) mediante [!DNL Media Gallery].

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** y seleccione el directorio **[!UICONTROL wysiwyg]**.
1. Cargue la imagen con una anchura relativamente pequeña en comparación con su altura (o viceversa).

<u>Resultados esperados</u>:

La imagen se carga sin errores.

<u>Resultados reales</u>:

1. Se genera el siguiente mensaje de error:

   *Un problema técnico con el servidor creó un error. Intenta de nuevo continuar lo que estabas haciendo. Si el problema persiste, inténtelo de nuevo más tarde.*
1. `var/log/exception.log` contiene:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   o

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
