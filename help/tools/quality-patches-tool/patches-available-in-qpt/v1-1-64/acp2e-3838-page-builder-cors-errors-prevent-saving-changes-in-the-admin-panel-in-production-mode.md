---
title: 'ACP2E-3838: [!DNL Page Builder] Los errores CORS impiden guardar los cambios en el panel de administración en el modo de producción'
description: Aplique el parche ACP2E-3838 para corregir el problema de Adobe Commerce donde  [!DNL Page Builder] los errores CORS impiden guardar cambios en el panel de administración en el modo de producción.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838: [!DNL Page Builder] errores CORS impiden guardar cambios en el panel de administración en modo de producción

El parche ACP2E-3838 corrige el problema en el que los errores CORS de [!DNL Page Builder] impiden guardar cambios en el panel de administración en el modo de producción. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACP2E-3838. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL Page Builder] errores CORS impiden guardar cambios en el panel de administración en el modo de producción.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Ir a **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Haga clic en **[!UICONTROL Add New Page]** o seleccione una página de CMS existente y haga clic en **[!UICONTROL Edit]**.
1. Haga clic en **[!UICONTROL Edit with Page Builder]** para agregar un bloque de contenido nuevo o editar uno existente.
1. Realice cualquier cambio en el contenido, como agregar texto, imágenes u otros elementos.
1. Haga clic en el botón **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

El contenido de la página se debe guardar correctamente sin errores.

<u>Resultados reales</u>:

1. No se pudieron guardar los cambios [!DNL Page Builder].
1. La consola del explorador registra los errores relacionados con CORS.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
