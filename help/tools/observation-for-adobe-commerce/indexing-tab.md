---
title: La ficha [!UICONTROL Indexing]
description: Obtenga información acerca de la ficha [!UICONTROL Indexing] de  [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# La ficha [!UICONTROL Indexing]

La pestaña **[!UICONTROL Indexing]** intenta explicar los problemas con la indexación e identificar las posibles causas.

## [!UICONTROL Core index invalidated]

![Índice principal invalidado](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

El fotograma **[!UICONTROL Core index invalidated]** busca la invalidación de la indexación en un periodo de tiempo seleccionado. Si la indización se realiza al mismo tiempo que otros [!DNL crons] que requieren muchos recursos, supondrá una carga pesada en los recursos del sitio.

* `%Catalog Product Rule indexer has been invalidated%`) como `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) como `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) como `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) como `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) como `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) como `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) como `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) como `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) como `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) como `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) como `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) como `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) como `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Recompilaciones del índice principal](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

El fotograma **[!UICONTROL Core index rebuilds]** observa las recompilaciones de índice principal en un periodo de tiempo seleccionado. Estas son las cadenas que se analizan desde los registros para indicar la finalización de la regeneración del índice.

* `%Catalog Product Rule index has been rebuilt%`) como `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) como `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) como `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) como `category_products_idx`
* `%Customer Grid index has been rebuilt%`) como `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) como `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) como `product_categories_idx`
* `%Product EAV index has been rebuilt%`) como `product_eav_idx`
* `%Product Price index has been rebuilt%`) como `product_price_idx`
* `%Stock index has been rebuilt%`) como `stock_idx`
* `%Inventory index has been rebuilt successfully%`) como `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) como `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) como `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![tabla(s) de índice de catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

El fotograma **[!UICONTROL catalogsearch index table(s)]** busca las tablas de índice de catalogsearch en un periodo de tiempo seleccionado. Esta consulta está buscando la duración de cualquier operación de almacén de datos contra tablas con `%catalogsearch%` en el nombre de tabla.

## [!UICONTROL product index table(s)]

![tabla(s) de índice de producto](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

El marco **[!UICONTROL product index table(s)]** consulta las tablas de índice de productos en un intervalo de tiempo seleccionado. Esta consulta está buscando la duración de cualquier operación de almacén de datos contra tablas con `%product%` en el nombre de tabla.
