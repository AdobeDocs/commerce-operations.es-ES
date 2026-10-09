---
title: 'ACSD-64813: la desasignación de categorías en el catálogo compartido de [!DNL B2B] a través de la API REST es lenta'
description: Aplique el parche ACSD-64813 para solucionar el problema de Adobe Commerce donde la anulación de la asignación de categorías en un catálogo compartido de [!DNL B2B] a través de la API REST es lenta.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
# ACSD-64813: la desasignación de categorías en el catálogo compartido de [!DNL B2B] a través de la API REST es lenta

El parche ACSD-64813 corrige el problema que causa que la anulación de la asignación de categorías en un catálogo compartido de [!DNL B2B] a través de la API REST sea lenta. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-64813. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La desasignación de categorías en un catálogo compartido de [!DNL B2B] mediante la API de REST es lenta.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL B2B]**, **[!UICONTROL Company]** y **[!UICONTROL Shared Catalog]**.
1. Genere 30.000 productos activos en stock.
1. Cree un [catálogo compartido personalizado](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) y asígnele todos los productos.
1. Cree una nueva categoría en la categoría raíz predeterminada y asígnele algunos productos.
1. Use el token de administración para llamar al extremo de la API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` con el nuevo ID de categoría.

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. Confirme que la respuesta es *true*.
1. Ejecute `bin/magento cron:run` dos veces o realice una reindexación.
1. Use el token de administración para llamar al extremo de la API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` con el nuevo ID de categoría.

   ```json
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

<u>Resultados esperados</u>:

La operación debe completarse en un tiempo razonable (en un par de minutos).

<u>Resultados reales</u>:

La ejecución tarda unos 30 minutos o provoca un error de tiempo de espera.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
