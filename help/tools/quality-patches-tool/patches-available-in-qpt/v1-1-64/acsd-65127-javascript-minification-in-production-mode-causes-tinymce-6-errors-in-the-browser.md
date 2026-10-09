---
title: 'ACSD-65127: la minificación de JavaScript en el modo de producción provoca [!DNL TinyMCE] 6 errores en el explorador'
description: Aplique el parche ACSD-65127 para solucionar el problema de Adobe Commerce donde al habilitar la minificación de JavaScript en el modo de producción [!DNL TinyMCE] 6 se generaron errores en la consola del explorador que afectaron a la funcionalidad y la experiencia del usuario.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
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
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-65127: la minificación de JavaScript en el modo de producción provoca [!DNL TinyMCE] 6 errores en el explorador

La revisión ACSD-65127 corrige el problema que causaba que, al habilitar la minificación de JavaScript en el modo de producción, [!DNL TinyMCE] 6 generara errores en la consola del explorador, lo que afectaba a la funcionalidad y a la experiencia del usuario. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-65127. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al habilitar la minificación de JavaScript en el modo de producción, [!DNL TinyMCE] 6 generó errores en la consola del explorador, lo que afectó a la funcionalidad y la experiencia del usuario.

<u>Pasos a seguir</u>:

1. Establezca la configuración ejecutando los siguientes comandos:

   ```shell
   bin/magento config:set --lock-config dev/js/minify_files 1
   bin/magento config:set --lock-config dev/js/enable_js_bundling 1
   bin/magento config:set --lock-config dev/js/merge_files 1
   ```

   >[!NOTE]
   >
   >Adobe no recomienda habilitar **[!UICONTROL Merge JavaScript Files]**. Ver [Combinar archivos JS (no recomendado)](/help/implementation-playbook/best-practices/development/optimize-css-js-files.md#merge-js-files).

1. Habilitar modo de producción.

```shell
bin/magento deploy:mode:set production
```

1. En la barra lateral de Administración, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Haga clic en **[!UICONTROL Edit]** en cualquier producto de la lista, desplácese hacia abajo hasta **[!UICONTROL Content]** y seleccione **[!UICONTROL Show Editor]**.

<u>Resultados esperados</u>:

No hay errores de JS en la consola del explorador.

<u>Resultados reales</u>:

*404* errores en la consola del explorador para js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
