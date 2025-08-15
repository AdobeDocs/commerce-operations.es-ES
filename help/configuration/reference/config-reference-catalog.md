---
title: Referencia de rutas de configuración de catálogo
description: Consulte una lista de valores de configuración del catálogo.
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 47bda51cdcab964c37d9f652d467d69d795d8641
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 0%

---

# Referencia de rutas de configuración de catálogo

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Catálogo**.

El comando [`magento app:config:dump` ](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente. Para anular opcionalmente las opciones de configuración o establecer opciones confidenciales, vea [Usar variables de entorno para anular las opciones de configuración](override-config-settings.md#environment-variables). Este tema _no_ enumera [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de catálogo

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Catálogo**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Máscara para SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para metatítulo | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para palabras clave meta | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máscara para metadescripción | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de lista | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en valores permitidos de cuadrícula | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en valor predeterminado de cuadrícula | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en la lista de valores permitidos | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos por página en el valor predeterminado de la lista | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lista de productos Ordenar por | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir todos los productos por página | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar categoría de catálogo plano | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar producto de catálogo plano | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Muestras por producto | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir que los invitados escriban críticas | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir alerta cuando cambie el precio del producto | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de alerta de precio | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir la alerta cuando el producto vuelva a estar disponible | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de alerta de stock | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de alerta | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de inicio | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error de remitente de correo electrónico | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de error | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar para actual | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recuento predeterminado de productos vistos recientemente | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recuento predeterminado de productos comparados recientemente | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vídeo base de inicio automático | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar vídeo relacionado | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reinicio automático de vídeo | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precios de catálogo | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precio de producto predeterminado | `catalog/price/default_product_price` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar recuento de productos | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo de Paso de Navegación de Precio | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paso de navegación de precio predeterminado | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar intervalo de precio como un precio | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de intervalos de precio | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Límite de división de intervalo | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidad máxima | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud mínima de la consulta | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud máxima de la consulta | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Motor de búsqueda | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera del servidor Solr | `catalog/search/solr_server_timeout` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de indexación | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar sugerencias de búsqueda | `catalog/search/search_suggestion_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recuento de sugerencias de búsqueda | `catalog/search/search_suggestion_count` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar recuento de resultados de cada sugerencia | `catalog/search/search_suggestion_count_results_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Activar recomendaciones de búsqueda | `catalog/search/search_recommendations_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recuento de recomendaciones de búsqueda | `catalog/search/search_recommendations_count` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar recuento de resultados de cada recomendación | `catalog/search/search_recommendations_count_results_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Términos mínimos que deben cumplirse | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar reescrituras de URL de &quot;categoría/producto&quot; | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Términos de búsqueda populares | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de URL del producto | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de URL de categoría | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar ruta de categorías para URL de productos | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Crear redireccionamiento permanente para direcciones URL si se cambia la clave URL | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separador de título de página | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar Meta Etiqueta De Vínculo Canónico Para Las Categorías | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uso De La Meta Etiqueta De Vínculo Canónico Para Productos | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar | `catalog/magento_catalogpermissions/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir categoría de exploración | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Página de aterrizaje | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar precios de productos | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir la adición al carro | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupos de clientes | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| No permitir búsqueda en el catálogo por | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Estado del artículo del pedido para activar las descargas | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo predeterminado de descargas | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartible | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de muestra predeterminado | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de vínculo predeterminado | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abrir vínculos en una ventana nueva | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar Content-Disposition | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Deshabilitar la desprotección de invitados si el carro contiene elementos descargables | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar JavaScript Calendar | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de campos de fecha | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de tiempo | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo de años | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar funcionalidad de eventos de catálogo | `catalog/magento_catalogevent/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar el widget de evento de catálogo en tienda | `catalog/magento_catalogevent/lister_output` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Número de eventos que se mostrarán en el widget deslizador de eventos | `catalog/magento_catalogevent/lister_widget_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Eventos que se desplazarán por clic en el widget deslizador de eventos | `catalog/magento_catalogevent/lister_widget_scroll` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de productos en la lista de productos relacionados | `catalog/magento_targetrule/related_position_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar productos relacionados | `catalog/magento_targetrule/related_position_behavior` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de rotación para productos en la lista de productos relacionados | `catalog/magento_targetrule/related_rotation_mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de productos en la lista de productos de venta cruzada | `catalog/magento_targetrule/crosssell_position_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar productos de venta cruzada | `catalog/magento_targetrule/crosssell_position_behavior` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de rotación para productos en la lista de productos de venta cruzada | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de productos en la lista de productos ampliados | `catalog/magento_targetrule/upsell_position_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar productos de ampliación de venta | `catalog/magento_targetrule/upsell_position_behavior` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo de rotación de productos en la lista de productos ampliados | `catalog/magento_targetrule/upsell_rotation_mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas de inventario

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Inventario**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Disminuir stock al realizar el pedido | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Definir el estado de los artículos como En stock cuando se cancela el pedido | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar productos sin existencias | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solo el umbral izquierdo X | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar disponibilidad de productos en stock en tienda | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sincronizar con el catálogo | `cataloginventory/options/synchronize_with_catalog` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Administrar stock | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pedidos no satisfechos | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar actualización de Stock diferida | `cataloginventory/item_options/use_deferred_stock_update` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Cantidad máxima permitida en el carro de compras | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de falta de stock | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cantidad mínima permitida en el carro de compras | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificar para la cantidad siguiente | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar incrementos de cantidad | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incrementos de cantidad | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Devolver automáticamente el artículo de nota de abono a stock | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ejecutar asincrónicamente | `cataloginventory/bulk_operations/async` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tamaño de lote asincrónico | `cataloginventory/bulk_operations/batch_size` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Proveedor | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de cálculo | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de Visual Merchandiser

[!BADGE Solo PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Se aplica solo a proyectos de Adobe Commerce en la nube (infraestructura PaaS administrada por Adobe) y a proyectos locales."}

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Visual Merchandiser**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Atributos visibles para reglas de categoría | `visualmerchandiser/options/smart_attributes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Umbral de stock mínimo | `visualmerchandiser/options/minimum_stock_threshold` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Código de atributo de color | `visualmerchandiser/options/color_attribute_code` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Orden de color | `visualmerchandiser/options/color_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas del mapa XML

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Mapa del sitio XML**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
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
| Error de remitente de correo electrónico | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de error | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de URL por archivo | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño máximo de archivo | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar el envío a Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de fuentes RSS

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Fuentes RSS**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitar RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevos productos | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productos especiales | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cupones/Descuentos | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoría de nivel superior | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notificación del estado del pedido del cliente | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Correo electrónico a las rutas de un amigo

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Enviar correo electrónico a un amigo**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitado | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seleccionar plantilla de correo electrónico | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir a los invitados | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinatarios máximos | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de productos enviados en 1 hora | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limitar envío por | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
