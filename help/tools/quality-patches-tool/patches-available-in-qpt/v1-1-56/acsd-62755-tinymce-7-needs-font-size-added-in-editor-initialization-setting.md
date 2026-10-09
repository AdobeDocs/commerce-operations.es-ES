---
title: 'ACSD-62755: [!DNL TinyMCE] 7 necesita que se agreguen el tamaño y la fuente a la configuración de inicialización del editor'
description: Aplique el parche ACSD-62755 para corregir el problema de Adobe Commerce donde [!DNL TinyMCE] 7 requiere que *tamaño de fuente* y *familia de fuentes* se agreguen específicamente dentro de la configuración de inicialización del editor.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
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
source-wordcount: '328'
ht-degree: 0%
---
# ACSD-62755: [!DNL TinyMCE] 7 necesita que se agreguen el tamaño y la fuente a la configuración de inicialización del editor

El parche ACSD-62755 corrige el problema en el que [!DNL TinyMCE] 7 requiere que se agreguen específicamente selectores de *tamaño de fuente* y *familia de fuentes* dentro de la configuración de inicialización del editor. Este parche está disponible con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 instalado. El ID del parche es ACSD-62755. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p10

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL TinyMCE] 7 requiere que los selectores *tamaño de fuente* y *familia de fuentes* se agreguen específicamente en la configuración de inicialización del editor.

<u>Pasos a seguir</u>:

Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** y seleccione *[!UICONTROL Show Editor]*.

<u>Resultados esperados</u>:

Los selectores *Tamaño de fuente* y *familia de fuentes* están visibles en el editor de WYSIWYG.

<u>Resultados reales</u>:

Falta el selector *Tamaño de fuente* en el editor de WYSIWYG.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
