---
title: "El [!UICONTROL Indexing] tab"
description: Obtenga información sobre [!UICONTROL Indexing] pestaña [!DNL Observation for Adobe Commerce].
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# La variable [!UICONTROL Indexing] ficha

La variable **[!UICONTROL Indexing]** intenta explicar los problemas con la indexación e identificar posibles causas.

## [!UICONTROL Core index invalidated]

![Índice principal no válido](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

La variable **[!UICONTROL Core index invalidated]** frame busca la invalidación de indexación en un intervalo de tiempo seleccionado. Si la indexación está ocurriendo al mismo tiempo que otros recursos intensivos [!DNL crons], colocará una carga pesada en los recursos del sitio.

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

![Reconversión del índice principal](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

La variable **[!UICONTROL Core index rebuilds]** frame busca las recompilaciones del índice principal en un intervalo de tiempo seleccionado. Estas son las cadenas que se analizan desde los registros para indicar que se ha completado la reconstrucción del índice.

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

![tablas de índice catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

La variable **[!UICONTROL catalogsearch index table(s)]** frame observa las tablas de índice de búsqueda de catálogos en un intervalo de tiempo seleccionado. Esta consulta examina la duración de cualquier operación del almacén de datos con tablas con `%catalogsearch%` en el nombre de tabla.

## [!UICONTROL product index table(s)]

![tablas de índice de productos](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

La variable **[!UICONTROL product index table(s)]** frame observa las tablas de índice del producto en un intervalo de tiempo seleccionado. Esta consulta examina la duración de cualquier operación del almacén de datos con tablas con `%product%` en el nombre de tabla.
