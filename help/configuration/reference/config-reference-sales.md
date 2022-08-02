---
title: Referencia de rutas de configuración de ventas
description: Consulte una lista de valores de configuración de ventas.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '1500'
ht-degree: 0%

---


# Referencia de rutas de configuración de ventas

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Ventas**.

La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartido, `app/etc/config.php`, que debería estar en el control de código fuente. Para anular, opcionalmente, cualquier configuración o definir ajustes confidenciales, consulte [Usar variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables). Este tema sí _not_ list [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de venta

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Ventas**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Ocultar IP del cliente | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotal | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Descuento | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envío | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impuesto | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impuesto fijo del producto | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total general | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarjetas de regalo | `sales/totals_sort/giftcardaccount` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Crédito de la tienda | `sales/totals_sort/customerbalance` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir reordenación | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo para impresiones de PDF (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo para vista de impresión del HTML | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dirección | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importe mínimo | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir impuesto a importe | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de descripción | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error al mostrar en el carro de compras | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar cada dirección por separado en el cierre de compra multidirección | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de descripción de varias direcciones | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error de varias direcciones para mostrar en el carro de compras | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar datos agregados | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de pedido de pago pendiente (minutos) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensajes de regalo en el nivel de pedido | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensajes de regalo para artículos de pedido | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir ajuste de regalo en el nivel de pedido | `sales/gift_options/wrapping_allow_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir ajuste de regalo para artículos de pedido | `sales/gift_options/wrapping_allow_items` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir recibo de regalo | `sales/gift_options/allow_gift_receipt` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir tarjeta impresa | `sales/gift_options/allow_printed_card` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Precio predeterminado para tarjeta impresa | `sales/gift_options/printed_card_price` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precio real | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de texto emergente predeterminado | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de texto predeterminado &quot;Qué es esto&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Pedido por SKU en mi cuenta en tienda | `sales/product_sku/my_account_enable` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto de botón | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupos de clientes | `sales/product_sku/allowed_groups` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar archivado | `sales/magento_salesarchive/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Archivar pedidos comprados | `sales/magento_salesarchive/age` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Estados de pedidos que se van a archivar | `sales/magento_salesarchive/order_statuses` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar RMA en tienda | `sales/magento_rma/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar RMA a nivel de producto | `sales/magento_rma/enabled_on_product` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Usar dirección de tienda | `sales/magento_rma/use_store_address` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Rutas de correo electrónico de ventas

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Correos electrónicos de ventas**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Envío asincrónico | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo remitente de correo electrónico de confirmación de pedido | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nueva plantilla de confirmación de pedido | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nueva plantilla de confirmación de pedido para invitado | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de copia de correo electrónico del pedido de envío | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solicitar remitente de correo electrónico de comentario | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordenar plantilla de correo electrónico de comentario | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solicitar plantilla de correo electrónico de comentario para invitado | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios del pedido: método de copia de correo electrónico | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de factura | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de factura | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de factura para invitado | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Método de Copia de Correo Electrónico de Factura | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de comentario de factura | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de factura | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de factura para invitado | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar Comentarios de Facturas Método de Copia de Correo Electrónico | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de envío | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de envío | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de envío para invitado | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar método de copia de correo electrónico | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de comentario de envío | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de envío | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de envío para invitado | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios de envío Método de copia de correo electrónico | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de nota de crédito | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de nota de crédito | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de nota de crédito para invitado | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar nota de crédito: método de copia de correo electrónico | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de comentario de nota de crédito | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de nota de crédito | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nota de crédito Plantilla de correo electrónico de comentario para invitado | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios de nota de crédito Método de copia de correo electrónico | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/magento_rma/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico RMA | `sales_email/magento_rma/identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico RMA | `sales_email/magento_rma/template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico RMA para invitado | `sales_email/magento_rma/guest_template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de copia de correo electrónico RMA | `sales_email/magento_rma/copy_method` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales_email/magento_rma_auth/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de autorización de RMA | `sales_email/magento_rma_auth/identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de autorización de RMA | `sales_email/magento_rma_auth/template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de autorización de RMA para invitado | `sales_email/magento_rma_auth/guest_template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de copia de correo electrónico de autorización de RMA | `sales_email/magento_rma_auth/copy_method` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales_email/magento_rma_comment/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de comentarios de RMA | `sales_email/magento_rma_comment/identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de comentario de RMA | `sales_email/magento_rma_comment/template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de comentario de RMA para invitado | `sales_email/magento_rma_comment/guest_template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de copia de correo electrónico RMA | `sales_email/magento_rma_comment/copy_method` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales_email/magento_rma_customer_comment/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de comentarios de RMA | `sales_email/magento_rma_customer_comment/identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Destinatario de correo electrónico de comentario de RMA | `sales_email/magento_rma_customer_comment/recipient` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de comentario de RMA | `sales_email/magento_rma_customer_comment/template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Enviar método de copia de correo electrónico RMA | `sales_email/magento_rma_customer_comment/copy_method` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar ID de pedido en el encabezado | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar ID de pedido en el encabezado | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar ID de pedido en el encabezado | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas fiscales

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Impuesto**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Clase de Impuestos para Envío | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Clase fiscal para opciones de regalo | `tax/classes/wrapping_tax_class` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Clase de Impuesto Predeterminada para el Producto | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Clase de Impuesto Predeterminada para el Cliente | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de cálculo de impuestos basado en | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo de impuestos basado en | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precios del catálogo | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precios de envío | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar impuesto al cliente | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar descuento en precios | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar impuesto en | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar el comercio transfronterizo | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| País predeterminado | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estado predeterminado | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Código de anuncio predeterminado | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar los precios del producto en el catálogo | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de envío | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar importe de envío | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de ajuste de regalo | `tax/cart_display/gift_wrapping` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar precios de tarjeta impresos | `tax/cart_display/printed_card` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Incluir total de impuestos en pedido | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar resumen de impuestos completos | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal de impuestos cero | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar importe de envío | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de ajuste de regalo | `tax/sales_display/gift_wrapping` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar precios de tarjeta impresos | `tax/sales_display/printed_card` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Incluir total de impuestos en pedido | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar resumen de impuestos completos | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal de impuestos cero | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Precios En Listas De Productos | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios en la página Vista del producto | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Precios En Módulos De Ventas | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Los Precios En Los Correos Electrónicos | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar impuesto a FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir FPT en subtotal | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de cierre de compra

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Cierre de compra**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar el cierre de compra de una página | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir cierre de compra de invitado | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar dirección de facturación activada | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar términos y condiciones | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de la cotización (días) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Después de agregar una redirección de producto al carro de compras | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imagen de producto agrupada | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imagen de producto configurable | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vista previa de la duración del presupuesto (minutos) | `checkout/cart/preview_quota_lifetime` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar resumen del carro de compras | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar barra lateral del carro de compras | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar máximo los elementos agregados recientemente | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico con error de pago | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Receptor de correo electrónico con error de pago | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla con error de pago | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envío de pago fallido por correo electrónico Método de copia | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de configuración de envío

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Configuración de envío**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Aplicar directiva de envío personalizada | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Política de envío | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de configuración de envío múltiple

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Configuración de envío múltiple**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Permitir envío a varias direcciones | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cantidad máxima permitida para el envío a varias direcciones | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de métodos de entrega

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Métodos de envío**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitado | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre del método | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precio | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de administración | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de gestión | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre del método | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importe mínimo de pedido | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre del método | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condición | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir productos virtuales en el cálculo de precios | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exportar | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importar | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de administración | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de gestión | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para cierre de compra | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para RMA | `carriers/ups/active_rma` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de UPS | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Origen del envío | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de puerta de enlace | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar tasas negociadas | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de solicitud de paquetes | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contenedor | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidad de peso | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de destino | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo del paquete (consulte con el transportista para obtener el peso máximo admitido para el envío) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de recolección | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso mínimo del paquete (consulte con el transportista para obtener el peso mínimo admitido de envío) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de administración | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de gestión | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar Umbral de Envío Gratuito | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para cierre de compra | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para RMA | `carriers/usps/active_rma` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de solicitud de paquetes | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contenedor | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Length | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anchura | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altura | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Giro | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máquina | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo del paquete (consulte con el transportista para obtener el peso máximo admitido para el envío) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de administración | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de gestión | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar Umbral de Envío Gratuito | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para cierre de compra | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para RMA | `carriers/fedex/active_rma` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de servicios web (producción) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de servicios web (Simulador para pruebas) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de solicitud de paquetes | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envase | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropoff | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidad de peso | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo del paquete (consulte con el transportista para obtener el peso máximo admitido para el envío) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de administración | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de gestión | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrega residencial | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de concentrador | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar Umbral de Envío Gratuito | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para cierre de compra | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para RMA | `carriers/dhl/active_rma` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de contenido | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de administración | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de gestión | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dividir peso del pedido | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidad de peso | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altura | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidad | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anchura | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo listo | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar Umbral de Envío Gratuito | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países aplicables | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de API de Google

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **API de Google**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de cuenta | `google/analytics/type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar experimentos de contenido | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Propiedad List de la página de catálogo | `google/analytics/catalog_page_list_value` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Propiedad List para el bloque de venta cruzada | `google/analytics/crosssell_block_list_value` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Propiedad List para el bloque de ventas superiores | `google/analytics/upsell_block_list_value` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Propiedad List para el bloque de productos relacionados | `google/analytics/related_block_list_value` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Propiedad List para la página de resultados de búsqueda | `google/analytics/search_page_list_value` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ’Promociones internas’ para el campo de promociones &quot;Etiqueta&quot;. | `google/analytics/promotions_list_value` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de conversión | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Idioma de conversión | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de conversión | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Color de conversión | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Etiqueta de conversión | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de valor de conversión | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor de conversión | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de tarjetas de regalo

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Tarjetas de regalo**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Remitente de correo electrónico de notificación de tarjeta de regalo | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de notificación de tarjeta de regalo | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Disponibles | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración (días) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensaje de regalo | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud máxima del mensaje de regalo | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar cuenta de tarjeta de regalo cuando el artículo del pedido está | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de tarjeta de regalo | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de tarjeta de regalo | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud del código | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de código | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefijo de código | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de código | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Guiar cada carácter X | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo tamaño del grupo | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de grupo de código bajo | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
