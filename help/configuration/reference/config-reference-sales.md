---
title: Referencia de rutas de configuración de ventas
description: Consulte una lista de valores de configuración de ventas.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# Referencia de rutas de configuración de ventas

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas**.

El comando [`magento app:config:dump` ](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente. Para anular opcionalmente las opciones de configuración o establecer opciones confidenciales, vea [Usar variables de entorno para anular las opciones de configuración](override-config-settings.md#environment-variables). Este tema _no_ enumera [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de ventas

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Ventas**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Ocultar IP del cliente | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotal | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Descuento | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envío | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impuestos | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impuesto de producto fijo | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total general | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarjetas de regalo | `sales/totals_sort/giftcardaccount` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Crédito de tienda | `sales/totals_sort/customerbalance` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir reordenar | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo para copias impresas PDF (200 x 50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo para la vista de impresión de HTML | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dirección | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cantidad mínima | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir impuesto al importe | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de descripción | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error al mostrar en el carro de compras | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar cada dirección por separado en el cierre de compra de varias direcciones | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de descripción de varias direcciones | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error de varias direcciones para mostrar en el carro de compras | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uso de datos agregados | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de la orden de pago pendiente (minutos) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensajes de regalo en el nivel de pedido | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensajes de regalo para artículos de pedido | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir ajuste de regalo en el nivel de pedido | `sales/gift_options/wrapping_allow_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir ajuste de regalo para artículos de pedido | `sales/gift_options/wrapping_allow_items` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir recibo de regalo | `sales/gift_options/allow_gift_receipt` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir tarjeta impresa | `sales/gift_options/allow_printed_card` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Precio predeterminado para la tarjeta impresa | `sales/gift_options/printed_card_price` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precio real | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de texto emergente predeterminado | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de texto predeterminado &quot;Qué es esto&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar pedido por SKU en Mi cuenta en Tienda | `sales/product_sku/my_account_enable` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto del botón | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupos de clientes | `sales/product_sku/allowed_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar archivado | `sales/magento_salesarchive/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Archivar pedidos adquiridos | `sales/magento_salesarchive/age` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Estados de pedidos que se archivarán | `sales/magento_salesarchive/order_statuses` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar RMA en tienda | `sales/magento_rma/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar RMA en el nivel de producto | `sales/magento_rma/enabled_on_product` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Usar dirección de la tienda | `sales/magento_rma/use_store_address` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas de correos electrónicos de ventas

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Correos electrónicos de ventas**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Envío asincrónico | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo remitente de correo electrónico de confirmación de pedido | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nueva plantilla de confirmación de pedido | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nueva plantilla de confirmación de pedido para invitado | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Enviar copia de correo electrónico del pedido | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar correo electrónico de comentario de pedido | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de pedido | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de pedido para invitado | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios de pedidos por correo electrónico Método de copia | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de factura | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de factura | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de factura para invitado | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Enviar copia de correo electrónico de factura | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de comentario de factura | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de factura | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de factura para invitado | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios de factura por correo electrónico Método de copia | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de envío | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de envío | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de envío para invitado | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Enviar copia de correo electrónico de envío | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de comentario de envío | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de envío | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de envío para invitado | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios de envío Correo electrónico Método de copia | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de abono | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de abono | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de nota de abono para invitado | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar copia de correo electrónico de nota de abono | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de comentario de abono | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de abono | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de comentario de nota de abono para invitado | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comentarios de nota de abono Método de copia de correo electrónico | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `sales_email/magento_rma/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico RMA | `sales_email/magento_rma/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de RMA | `sales_email/magento_rma/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de RMA para invitado | `sales_email/magento_rma/guest_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Método Enviar copia de correo electrónico RMA | `sales_email/magento_rma/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales_email/magento_rma_auth/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de autorización RMA | `sales_email/magento_rma_auth/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de autorización RMA | `sales_email/magento_rma_auth/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de autorización de RMA para invitado | `sales_email/magento_rma_auth/guest_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Método Enviar copia de correo electrónico de autorización RMA | `sales_email/magento_rma_auth/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales_email/magento_rma_comment/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de comentario RMA | `sales_email/magento_rma_comment/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de comentario RMA | `sales_email/magento_rma_comment/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de comentario de RMA para invitado | `sales_email/magento_rma_comment/guest_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Método Enviar copia de correo electrónico RMA | `sales_email/magento_rma_comment/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `sales_email/magento_rma_customer_comment/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de comentario RMA | `sales_email/magento_rma_customer_comment/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Destinatario de correo electrónico de comentario RMA | `sales_email/magento_rma_customer_comment/recipient` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de comentario RMA | `sales_email/magento_rma_customer_comment/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Método Enviar copia de correo electrónico RMA | `sales_email/magento_rma_customer_comment/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar ID de pedido en el encabezado | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar ID de pedido en el encabezado | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar ID de pedido en el encabezado | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas fiscales

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Impuestos**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Clase de Impuesto para Envío | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Clase de Impuesto para Opciones de Regalo | `tax/classes/wrapping_tax_class` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Clase de impuesto predeterminada para el producto | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Clase de Impuesto por Defecto para Cliente | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de cálculo de impuestos basado en | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo De Impuestos Basado En | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precios de catálogo | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precios de envío | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar impuesto al cliente | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar Descuento En Precios | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar impuesto a | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar el comercio transfronterizo | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| País predeterminado | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estado predeterminado | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Código postal predeterminado | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de productos en el catálogo | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de envío | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar importe de envío | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de envoltorio para regalos | `tax/cart_display/gift_wrapping` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar precios de tarjetas impresas | `tax/cart_display/printed_card` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Incluir impuestos en el total del pedido | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar resumen completo de impuestos | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal de impuestos cero | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar importe de envío | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios de envoltorio para regalos | `tax/sales_display/gift_wrapping` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar precios de tarjetas impresas | `tax/sales_display/printed_card` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Incluir impuestos en el total del pedido | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar resumen completo de impuestos | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar subtotal de impuestos cero | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Precios En Listas De Productos | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios en la página de vista del producto | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar Precios En Módulos De Ventas | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar precios en correos electrónicos | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicar impuesto a FTP | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir FPT en el subtotal | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de cierre

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **Cierre de compra**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitar cierre de compra de una página | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir cierre de compra de invitado | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar dirección de facturación en | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar Términos y condiciones | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de la cotización (días) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Después de agregar una redirección de producto al carro de compras | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imagen de producto agrupada | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imagen de producto configurable | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Previsualizar duración de la cotización (minutos) | `checkout/cart/preview_quota_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar resumen del carro | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar barra lateral del carro de compras | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar máximo de elementos añadidos recientemente | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico con error de pago | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Receptor de correo electrónico con error de pago | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de pago fallido | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método Enviar copia de correo electrónico con error de pago | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de configuración de envío

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Configuración de envío**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Aplicar política de envío personalizada | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Política de envío | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de configuración de multienvío

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Configuración de envío múltiple**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Permitir el envío a varias direcciones | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cantidad máxima permitida para el envío a varias direcciones | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de métodos de envío

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **Métodos de envío**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitado | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre del método | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Precio | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de manejo | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de manipulación | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre del método | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cantidad mínima del pedido | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre del método | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condición | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incluir productos virtuales en el cálculo de precios | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exportar | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importar | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de manejo | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de manipulación | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para cierre de compra | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para RMA | `carriers/ups/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo de UPS | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Origen del envío | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de puerta | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar tarifas negociadas | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de solicitud de paquetes | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contenedor | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidad de peso | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de destino | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo del paquete (consulte con su transportista para conocer el peso máximo de envío admitido) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método de recogida | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso mínimo del paquete (consulte con su transportista para obtener el peso mínimo de envío admitido) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de manejo | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de manipulación | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar umbral de envío gratuito | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para cierre de compra | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para RMA | `carriers/usps/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modo | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de solicitud de paquetes | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contenedor | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ancho | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altura | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Girth | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Procesable | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo del paquete (consulte con su transportista para conocer el peso máximo de envío admitido) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de manejo | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de manipulación | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar umbral de envío gratuito | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para cierre de compra | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para RMA | `carriers/fedex/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Título | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de servicios web (producción) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL de servicios web (zona protegida) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de solicitud de paquetes | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Empaquetando | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Caída | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidad de peso | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso máximo del paquete (consulte con su transportista para conocer el peso máximo de envío admitido) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de manejo | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de manipulación | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Entrega residencial | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de concentrador | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar umbral de envío gratuito | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depurar | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para cierre de compra | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activado para RMA | `carriers/dhl/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Título | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de contenido | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcular tarifa de manejo | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestión aplicada | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tarifa de manipulación | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dividir peso del pedido | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unidad de peso | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altura | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profundidad | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ancho | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Métodos permitidos | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de preparación | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensaje de error mostrado | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Método libre | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar umbral de envío gratuito | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de importe de envío gratuito | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a los países aplicables | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar a países específicos | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar método si no es aplicable | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden de clasificación | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de API de Google

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **API de Google**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Activar | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de cuenta | `google/analytics/type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar experimentos de contenido | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Propiedad de lista para la página del catálogo | `google/analytics/catalog_page_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Propiedad de lista para el bloque de venta cruzada | `google/analytics/crosssell_block_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Propiedad de lista para el bloque de ampliación de venta | `google/analytics/upsell_block_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Propiedad de lista para el bloque de productos relacionado | `google/analytics/related_block_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Propiedad List para la página de resultados de la búsqueda | `google/analytics/search_page_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| &quot;Promociones internas&quot; para el campo de promociones &quot;Etiqueta&quot;. | `google/analytics/promotions_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Activar | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de conversión | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Idioma de conversión | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de conversión | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Color de conversión | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Etiqueta de conversión | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de valor de conversión | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor de conversión | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de tarjetas regalo

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Tarjetas de regalo**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Remitente de correo electrónico de notificación de tarjeta regalo | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de notificación de tarjeta regalo | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Canjeable | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración (días) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir mensaje de regalo | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud máxima del mensaje de regalo | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar cuenta de tarjeta regalo cuando el artículo de pedido esté | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de tarjeta regalo | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de tarjeta regalo | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud de código | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de código | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefijo de código | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de código | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Guión cada X caracteres | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo tamaño de grupo | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral de grupo de código bajo | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
