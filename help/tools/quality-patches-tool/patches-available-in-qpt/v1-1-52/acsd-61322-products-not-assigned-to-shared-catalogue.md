---
title: 'ACSD-61322: los productos no asignados a [!UICONTROL Shared Catalogue] se incluyen en el mapa del sitio XML'
description: Aplique el parche ACSD-61322 para solucionar el problema de Adobe Commerce en el que los productos o las categorías que no están asignados al [!UICONTROL Shared Catalog] para el grupo Predeterminado (General) siguen incluyéndose en el mapa del sitio XML.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 48c59cc5-3c2e-5df1-8756-f5c139a28932
    internal-label: Site Navigation
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '469'
ht-degree: 0%
---
# ACSD-61322: los productos no asignados a [!UICONTROL Shared Catalogue] se incluyen en el mapa del sitio XML

La revisión ACSD-61322 corrige el problema en el que los productos/categorías no asignados al [!UICONTROL Shared Catalog] para el grupo Predeterminado (General) siguen incluidos en el mapa del sitio XML. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52. El ID del parche es ACSD-61322. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos o las categorías que no se hayan asignado a [!UICONTROL Shared Catalog] para el grupo Predeterminado (General) se seguirán incluyendo en el mapa del sitio XML.

<u>Pasos a seguir</u>:

1. Cree algunas categorías y añada productos (por ejemplo, Categoría 1 con Categoría 2).
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** y habilite *[!UICONTROL Company and Shared Catalog]*.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** y modifique el catálogo predeterminado.
1. En el menú desplegable **[!UICONTROL Select]**, seleccione **[!UICONTROL Set Pricing and Structure]** y haga clic en **[!UICONTROL Configure]**.
1. En la categoría *Categoría 1 > Categoría 2*, anule la selección de algunos productos que no deberían estar en [!UICONTROL Shared Catalog].
1. Haga clic en **[!UICONTROL Next]** y genere el catálogo.
1. En la Tienda, cree una cuenta de cliente.
1. Vaya a la categoría *Categoría 1 > Categoría 2*. Muestra únicamente los productos que se asignaron a [!UICONTROL Shared Catalog].
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** y genere un nuevo mapa del sitio.
1. Abra `sitemap.xml` en la Tienda.
1. Busque los productos que no incluyó en el [!UICONTROL Shared Catalog].

<u>Resultados esperados</u>:

El mapa del sitio no contiene vínculos a productos y categorías que no están asignados a [!UICONTROL Shared Catalog].

<u>Resultados reales</u>:

El mapa del sitio contiene vínculos a productos y categorías que no están asignados a [!UICONTROL Shared Catalog].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
