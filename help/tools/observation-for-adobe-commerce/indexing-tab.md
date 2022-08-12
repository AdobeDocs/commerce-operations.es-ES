---
title: '"El [!UICONTROL Indexing] tab"'
description: Obtenga información sobre [!UICONTROL Indexing] pestaña [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# La variable [!UICONTROL Indexing] ficha

La variable **[!UICONTROL Indexing]** intenta explicar los problemas con la indexación e identificar posibles causas.

## [!UICONTROL Core index invalidated]

![Índice principal no válido](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

La variable **[!UICONTROL Core index invalidated]** frame busca la invalidación de indexación en un intervalo de tiempo seleccionado. Si la indexación está ocurriendo al mismo tiempo que otros crons con muchos recursos, supondrá una carga pesada en los recursos del sitio.

* &#39;%El indexador de reglas de producto del catálogo se ha invalidado%&#39;) como &#39;catalog_product_rule_idx_reset&#39;
* &#39;%El indexador de producto de regla de catálogo se ha invalidado%&#39;) como &#39;catalog_rule_product_idx_reset&#39;
* &#39;%El indizador de búsqueda del catálogo se ha invalidado%&#39;) como &#39;catalog_search_idx_reset&#39;
* &#39;%El indizador de productos de categoría se ha invalidado%&#39;) como &#39;category_products_idx_reset&#39;
* &#39;%El indizador de cuadrícula de cliente se ha invalidado%&#39;) como &#39;customer_grid_idx_reset&#39;
* &#39;%El indizador de cuadrícula de configuración de diseño se ha invalidado%&#39;) como &#39;design_config_grid_idx_
* &#39;%El indizador de categorías de producto se ha invalidado%&#39;) como &#39;product_categories_idx_reset&#39;
* &#39;%El indexador EAV del producto se ha invalidado%&#39;) como &#39;product_eav_idx_reset&#39;
* &#39;%El indexador de precios de producto se ha invalidado%&#39;) como &#39;product_price_idx_reset&#39;
* &#39;%El indizador de Stock se ha invalidado%&#39;) como &#39;stock_idx_reset&#39;
* &#39;%El indizador de inventario se ha invalidado%&#39;) como &#39;inventory_idx_reset&#39;
* &#39;%El indizador de inventario se ha invalidado%&#39;) como &#39;inventory_idx_reset&#39;
* &#39;%El indexador de reglas de ventas se invalidó%&#39;) como &#39;sales_rule_idx_reset&#39;

## [!UICONTROL Core index rebuilds]

![Reconversión del índice principal](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

La variable **[!UICONTROL Core index rebuilds]** frame busca las recompilaciones del índice principal en un intervalo de tiempo seleccionado. Estas son las cadenas que se analizan desde los registros para indicar que se ha completado la reconstrucción del índice.

* &#39;%El índice de reglas de producto del catálogo se ha vuelto a generar%&#39;) como &#39;catalog_product_rule_idx&#39;
* &#39;%El índice del producto de la regla del catálogo se ha vuelto a generar%&#39;) como &#39;catalog_rule_product_idx&#39;
* &#39;%El índice de búsqueda del catálogo se ha vuelto a generar%&#39;) como &#39;catalog_search_idx&#39;
* &#39;%Category Products index se ha reconstruido correctamente%&#39;) como &#39;category_products_idx&#39;
* &#39;%El índice de cuadrícula de cliente se ha vuelto a generar%&#39;) como &#39;customer_grid_idx&#39;
* &#39;%Design Config Grid index se ha reconstruido%&#39;) como &#39;design_config_grid_idx&#39;
* &#39;%El índice de categorías de productos se ha vuelto a generar%&#39;) como &#39;product_categories_idx&#39;
* &#39;%El índice EAV del producto se ha vuelto a generar%&#39;) como &#39;product_eav_idx&#39;
* &#39;%El índice de precios de producto se ha vuelto a generar%&#39;) como &#39;product_price_idx&#39;
* &#39;%Stock index se ha vuelto a generar%&#39;) como &#39;stock_idx&#39;
* &#39;%El índice de inventario se ha vuelto a generar correctamente%&#39;) como &#39;inventory_idx&#39;
* %El índice de reglas de producto/objetivo se ha vuelto a generar correctamente%) como &quot;prod_target_rule_idx&quot;
* &#39;%El índice de reglas de ventas se ha vuelto a generar correctamente%&#39;) como &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![tablas de índice catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

La variable **[!UICONTROL catalogsearch index table(s)]** frame observa las tablas de índice de búsqueda de catálogos en un intervalo de tiempo seleccionado. Esta consulta examina la duración de cualquier operación del almacén de datos con tablas con ‘%catalogsearch%’ en el nombre de tabla.

## [!UICONTROL product index table(s)]

![tablas de índice de productos](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

La variable **[!UICONTROL product index table(s)]** frame observa las tablas de índice del producto en un intervalo de tiempo seleccionado. Esta consulta examina la duración de cualquier operación del almacén de datos con tablas con ‘%product%’ en el nombre de tabla.
