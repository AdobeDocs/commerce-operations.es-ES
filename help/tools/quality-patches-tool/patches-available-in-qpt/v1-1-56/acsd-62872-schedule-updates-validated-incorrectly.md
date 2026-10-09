---
title: 'ACSD-62872: programar actualizaciones validadas incorrectamente'
description: Aplique el parche ACSD-62872 para corregir el problema de Adobe Commerce con validación de atributos únicos en el que las actualizaciones programadas se validan incorrectamente.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '354'
ht-degree: 0%
---
# ACSD-62872: programar actualizaciones validadas incorrectamente

El parche ACSD-62872 corrige el problema de validación de atributos únicos en el que las actualizaciones programadas se validan incorrectamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62872. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche está marcado como obsoleto para las versiones 2.4.4 - 2.4.6-p8 en la versión 1.1.58 QPT.

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La actualización programada para un atributo personalizado se ha validado incorrectamente.

<u>Pasos a seguir</u>:

1. Cree un atributo personalizado para las categorías.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Cree una nueva categoría.
1. En la misma categoría, vaya a la sección **[!UICONTROL Scheduled Updates]**.
1. Configure una nueva actualización para esta categoría en cualquier momento futuro.
1. Antes de iniciar la actualización programada, intente editar la actualización de programación creada para la categoría.

<u>Resultados esperados</u>:

Debe poder actualizar la actualización programada.

<u>Resultados reales</u>:

Se genera un error: *El valor del atributo &quot;Atributo personalizado&quot; no es único. Establezca un valor único e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en infraestructura de nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en infraestructura de nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
