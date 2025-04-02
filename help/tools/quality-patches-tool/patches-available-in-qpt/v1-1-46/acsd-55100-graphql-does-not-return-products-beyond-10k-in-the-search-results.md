---
title: 'ACSD-55100: [!DNL GraphQL] no devuelve productos superiores a 10.000 en los resultados de búsqueda'
description: Aplique el parche ACSD-55100 para corregir el problema de Adobe Commerce en el que GraphQL no devuelve productos superiores a *10k* en los resultados de búsqueda.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
source-git-commit: b8c2c28f126360fe15bd1a49c37560b7d220f4f2
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# ACSD-55100: [!DNL GraphQL] no devuelve productos superiores a 10 000 en los resultados de búsqueda

>[!NOTE]
>
>Se ha lanzado un parche actualizado ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) para resolver el mismo problema en las versiones 2.4.6 - 2.4.6-p8. Para obtener más información, consulte [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

La revisión ACSD-55100 corrige el problema en el cual [!DNL GraphQL] no devuelve productos que superen los *10k* en los resultados de búsqueda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46. El ID del parche es ACSD-55100. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL GraphQL] no devuelve productos superiores a *10k* en los resultados de búsqueda.

<u>Requisitos previos</u>:

En el caso de **[!DNL OpenSearch]**, asegúrese de que está usando la versión más reciente disponible.

Para resolver el problema del que se ha informado, se ha introducido la funcionalidad de momento, que está disponible después de **[!DNL OpenSearch]** 2.5.0 y requiere la versión 2.2 del paquete `opensearch-project/opensearch-php`.

Sin embargo, hay un conflicto con `magento/magento-cloud-metapackage`, que especifica una dependencia en el paquete `opensearch-project/opensearch-php` que debe ser menor que la versión 2.0.1.


Esta dependencia impide actualizar el paquete [opensearch-project/opensearch-php] a la última versión 2.2.

Como resultado, el sistema encuentra el siguiente error y devuelve resultados nulos para los productos que superan los *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dependencia existente hace difícil agregar directamente una versión al archivo `composer.json` y actualizar el paquete `opensearch-project/opensearch-php` a la versión 2.2.

Para resolver el problema, incluya la línea siguiente en el archivo principal `composer.json` en el bloque requerido. Después, vuelva a implementar para actualizar el paquete problemático a la versión más reciente.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Pasos a seguir</u>:

1. Genere el catálogo con *15k* productos.
1. Enviar [!DNL GraphQL]:

```
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Resultados esperados</u>:

Total_count = *15k*
Debería poder mostrar todos los productos.

<u>Resultados reales</u>:

Total_count = *10k*
No puedes conseguir más productos para mostrar después del lote de *10.000*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
