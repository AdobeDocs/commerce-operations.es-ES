---
title: 'ACSD-65127: la minificación de JavaScript en el modo de producción provoca  [!DNL TinyMCE] 6 errores en el explorador'
description: Aplique el parche ACSD-65127 para solucionar el problema de Adobe Commerce donde al habilitar la minificación de JavaScript en el modo de producción  [!DNL TinyMCE] 6 generó errores en la consola del explorador, afectando la funcionalidad y la experiencia del usuario.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: c878d5a4-8059-4bfc-93a8-0a9606e866fc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '333'
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

```
bin/magento config:set --lock-config dev/js/minify_files 1
bin/magento config:set --lock-config dev/js/enable_js_bundling 1
bin/magento config:set --lock-config dev/js/merge_files 1
```

1. Habilitar modo de producción.

```
bin/magento deploy:mode:set production
```

1. En la barra lateral de Administración, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Haga clic en **[!UICONTROL Edit]** en cualquier producto de la lista, desplácese hacia abajo hasta **[!UICONTROL Content]** y seleccione **[!UICONTROL Show Editor]**.

<u>Resultados esperados</u>:

No hay errores de JS en la consola del explorador.

<u>Resultados reales</u>:

*404* errores en la consola del explorador para js `tiny_mce_6/plugins/help/js/i18n/keynav/en.js`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
