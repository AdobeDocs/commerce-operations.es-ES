---
title: 'ACSD-54018: problema de rendimiento con la lista de productos del widget de catálogo'
description: Aplique el parche ACSD-54018 para corregir el problema de Adobe Commerce en el que la página se carga lentamente al añadir una lista de productos de widget de catálogo con condición y tipo de atributo booleano.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-54018: problema de rendimiento con la lista de productos del widget de catálogo

El parche ACSD-54018 corrige el problema en el que la página se carga lentamente al añadir una lista de productos de widget de catálogo con condición y tipo de atributo booleano. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38. El ID del parche es ACSD-54018. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página se carga lentamente al añadir una lista de productos de widget de catálogo con condición y tipo de atributo booleano.

<u>Pasos a seguir</u>:

1. Genere 100k productos.
1. Cree un atributo bool con el ámbito establecido en [!UICONTROL Store View].
1. Asignar atributo a todos los conjuntos de atributos.
   * Asigne el valor de atributo *Yes* a todos los productos.
1. Ahora vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y seleccione los 100.000 productos.
   * Elija **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Establezca el atributo bool en *Yes* y guárdelo.
   * Si cerró la sesión en este paso, compruebe *Notas*.
1. Vaya a CLI y ejecute `php bin/magento queue:con:start product_action_attribute.update`.
   * Asegúrese de que se actualizan los atributos de todos los productos.
1. Ahora vaya a **[!UICONTROL Content]** > **[!UICONTROL Pages]** y cree una nueva página.
1. Abra **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Elija *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Establezca la condición *[!UICONTROL Created attribute]* en *[!UICONTROL Yes]* y guárdela.
1. Vaya al front-end y abra la página creada.
1. Deshabilite la memoria caché de la página completa y bloquee la memoria caché html.
1. Compruebe la velocidad de carga de la página.
1. Vuelva a cargar la página unas cuantas veces y calcule el tiempo medio de carga.

<u>Resultados esperados</u>:

La página se carga rápido.

<u>Resultados reales</u>:

La página tarda de 5 a 10 segundos en cargarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
