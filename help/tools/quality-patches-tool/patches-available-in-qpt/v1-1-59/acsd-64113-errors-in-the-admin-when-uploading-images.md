---
title: 'ACSD-64113: error del administrador al cargar una imagen con una anchura menor que la altura mediante [!DNL Media Gallery]'
description: Aplique el parche ACSD-64113 para corregir el problema de Adobe Commerce en el que el administrador produce errores al cargar imágenes con una anchura relativamente pequeña en comparación con su altura (o viceversa) a través de [!DNL Media Gallery].
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '378'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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

   ```yaml
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   o

   ```yaml
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
