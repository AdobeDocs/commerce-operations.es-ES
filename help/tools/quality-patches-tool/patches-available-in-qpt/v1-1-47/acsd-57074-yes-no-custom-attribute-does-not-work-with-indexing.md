---
title: 'ACSD-57074: *Sí/No* el atributo personalizado con el prefijo "price_*" en el atributo "attribute_code" no funciona con la indexación'
description: Aplique el parche ACSD-57074 para solucionar el problema de Adobe Commerce donde el atributo personalizado *Yes/No* con el prefijo "price_* en el atributo "attribute_code" no funciona con la indexación.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-57074: *Sí/No* el atributo personalizado con prefijo `price_*` en el atributo `attribute_code` no funciona con la indexación

El parche ACSD-57074 corrige el problema en el que el atributo personalizado *Yes/No* con el prefijo `price_*` en el atributo `attribute_code` no funciona con la indexación. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.47. El ID del parche es ACSD-57074. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El atributo personalizado *Yes/No* con el prefijo `price_*` en el atributo `attribute_code` no funciona con la indización.

<u>Pasos a seguir</u>:

1. Cree un atributo de producto personalizado con las siguientes opciones:
   * *[!UICONTROL Catalog Input Type]*: *Sí/No*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Sí*
1. Asigne el atributo al conjunto de atributos predeterminado.
1. Cree un producto con el atributo que hemos creado.
1. Asigne el producto que hemos creado a una categoría.
1. Ejecutar reindexación completa.

<u>Resultados esperados</u>:

El producto se muestra en la categoría asignada.

<u>Resultados reales</u>:

El producto no aparece en la página de categoría principal.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
