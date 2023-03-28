---
title: Referencia de rutas de configuración del catálogo
description: Consulte una lista de valores de configuración del catálogo.
source-git-commit: e4b7ea70b96143629b245409537459ad259393e0
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---


# Referencia de rutas de configuración del catálogo

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo**.

La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartido, `app/etc/config.php`, que debería estar en el control de código fuente. Para anular, opcionalmente, cualquier configuración o definir ajustes confidenciales, consulte [Usar variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables). Este tema sí _not_ list [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de catálogo

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Catálogo**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Máscara para SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara de meta título | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara de metapalabras clave | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para la meta descripción | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de lista | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en cuadrícula Valores permitidos | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en cuadrícula Valor predeterminado | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en lista de valores permitidos | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en lista Valor predeterminado | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lista de productos Ordenar por | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir todos los productos por página | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar categoría de catálogo plano | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar producto de catálogo plano | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Muestras por producto | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir que los invitados escriban revisiones | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir alertas cuando cambie el precio del producto | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de alertas de precio | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir alerta cuando el producto vuelva a estar en existencias | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de alerta de stock | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de alerta | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de inicio | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de error | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de error | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar para actual | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recuento predeterminado de productos vistos recientemente | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recuento predeterminado de productos comparados recientemente | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vídeo de base de inicio automático | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar vídeo relacionado | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reinicio automático de vídeo | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alcance del precio del catálogo | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precio de producto predeterminado | `catalog/price/default_product_price` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar recuento de productos | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo del paso de navegación por precios | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paso de navegación de precio predeterminado | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar el intervalo de precios como un precio | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de intervalos de precios | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Límite de división de intervalo | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidad máxima | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud mínima de la consulta | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud máxima de la consulta | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Motor de búsqueda | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera del servidor de Solr | `catalog/search/solr_server_timeout` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de indexación | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar sugerencias de búsqueda | `catalog/search/search_suggestion_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Recuento de sugerencias de búsqueda | `catalog/search/search_suggestion_count` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar recuento de resultados para cada sugerencia | `catalog/search/search_suggestion_count_results_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar Search Recommendations | `catalog/search/search_recommendations_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Buscar recuento de Recommendations | `catalog/search/search_recommendations_count` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar recuento de resultados para cada recomendación | `catalog/search/search_recommendations_count_results_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mínimo de términos para coincidir | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar reescrituras de URL de &quot;categoría/producto&quot; | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Términos de búsqueda populares | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de dirección URL del producto | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de dirección URL de categoría | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar ruta de categorías para direcciones URL de productos | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Crear redireccionamiento permanente para direcciones URL si se cambia la clave de URL | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separador de título de página | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Etiqueta Meta De Vínculo Canónico Para Categorías | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar Meta Etiqueta De Vínculo Canónico Para Productos | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar | `catalog/magento_catalogpermissions/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir navegación por categoría | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Página de aterrizaje | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar precios del producto | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir agregar al carro | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| No permitir la búsqueda en el catálogo por | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ordenar estado del elemento para activar las descargas | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo predeterminado de descargas | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartido | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de muestra predeterminado | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de vínculo predeterminado | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abrir vínculos en ventana nueva | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Disposición de Contenido | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Desactivar el cierre de compra de invitado si el carro contiene artículos descargables | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar calendario de JavaScript | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de campos de fecha | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de hora | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo de año | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la funcionalidad Eventos de catálogo | `catalog/magento_catalogevent/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Activar la utilidad Evento de catálogo en tienda | `catalog/magento_catalogevent/lister_output` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Número de eventos que se mostrarán en la utilidad del deslizador del evento | `catalog/magento_catalogevent/lister_widget_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Eventos que se desplazan por clic en la utilidad del deslizador del evento | `catalog/magento_catalogevent/lister_widget_scroll` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Número máximo de productos en la lista de productos relacionados | `catalog/magento_targetrule/related_position_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar productos relacionados | `catalog/magento_targetrule/related_position_behavior` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de rotación para productos en la lista de productos relacionados | `catalog/magento_targetrule/related_rotation_mode` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Número máximo de productos en la lista de productos de venta cruzada | `catalog/magento_targetrule/crosssell_position_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar productos de venta cruzada | `catalog/magento_targetrule/crosssell_position_behavior` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de rotación de los productos en la lista de productos de venta cruzada | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Número máximo de productos en la lista de productos de ventas superiores | `catalog/magento_targetrule/upsell_position_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar productos de ventas superiores | `catalog/magento_targetrule/upsell_position_behavior` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de rotación de los productos en la lista de productos de ventas superiores | `catalog/magento_targetrule/upsell_rotation_mode` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas de inventario

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Inventario**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Reducir stock cuando se realiza el pedido | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Definir el estado de los artículos para que esté en existencias cuando se cancele el pedido | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar productos fuera de existencias | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solo X Umbral izquierdo | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar la disponibilidad de los productos en existencias en la tienda | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sincronizar con catálogo | `cataloginventory/options/synchronize_with_catalog` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Administrar stock | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Respaldos | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar actualización de stock diferido | `cataloginventory/item_options/use_deferred_stock_update` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Cantidad máxima permitida en el carro de compras | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral fuera de existencias | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cantidad mínima permitida en el carro de compras | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificar para la cantidad inferior | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar incrementos de cantidad | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incrementos de cantidad | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devolver automáticamente el artículo de abono a stock | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ejecutar asincrónicamente | `cataloginventory/bulk_operations/async` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tamaño asíncrono del lote | `cataloginventory/bulk_operations/batch_size` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Proveedor | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de cómputo | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de comercialización visuales

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Comerciante visual**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Atributos visibles para reglas de categoría | `visualmerchandiser/options/smart_attributes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Umbral de stock mínimo | `visualmerchandiser/options/minimum_stock_threshold` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Código de atributo de color | `visualmerchandiser/options/color_attribute_code` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden del color | `visualmerchandiser/options/color_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas de mapa del sitio XML

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Mapa del sitio XML**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Frecuencia | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioridad | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioridad | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Agregar imágenes al mapa del sitio | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioridad | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de inicio | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de error | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de error | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de direcciones URL por archivo | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño máximo del archivo | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar envío a Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de fuentes RSS

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Fuentes RSS**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevos productos | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos especiales | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cupones/Descuentos | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoría superior | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificación de estado de pedido del cliente | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Enviar correo electrónico a rutas de amigos

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Enviar un correo electrónico a un amigo**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitado | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seleccionar plantilla de correo electrónico | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir a los clientes | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de destinatarios | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de productos enviados en 1 hora | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limitar envío por | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
