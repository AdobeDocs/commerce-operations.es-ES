---
title: 'ACSD-64813: desasignar categorías en el catálogo compartido  [!DNL B2B] a través de la API REST es lento'
description: Aplique el parche ACSD-64813 para solucionar el problema de Adobe Commerce donde la anulación de la asignación de categorías en un catálogo compartido de  [!DNL B2B] a través de la API de REST es lenta.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
exl-id: e6fd89c2-d3c0-462f-b328-7a80b456d96d
source-git-commit: 239a9efcc2ae231b337f654e4e36e6119e6eff7e
workflow-type: tm+mt
source-wordcount: '368'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La desasignación de categorías en un catálogo compartido de [!DNL B2B] mediante la API de REST es lenta.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL B2B]**, **[!UICONTROL Company]** y **[!UICONTROL Shared Catalog]**.
1. Genere 30.000 productos activos en stock.
1. Cree un [catálogo compartido personalizado](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) y asígnele todos los productos.
1. Cree una nueva categoría en la categoría raíz predeterminada y asígnele algunos productos.
1. Use el token de administración para llamar al extremo de la API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` con el nuevo ID de categoría.

   ```
   {
     "categories": [
       { "id": <new category id> }
     ]
   }
   ```

1. Confirme que la respuesta es *true*.
1. Ejecute `bin/magento cron:run` dos veces o realice una reindexación.
1. Use el token de administración para llamar al extremo de la API REST `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` con el nuevo ID de categoría.

   ```
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
