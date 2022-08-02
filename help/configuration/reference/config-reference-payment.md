---
title: Referencia de rutas de configuración de pago
description: Consulte una lista de valores de métodos de pago configurables.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '4133'
ht-degree: 0%

---


# Referencia de rutas de configuración de pago

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Métodos de pago**.

La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartido, `app/etc/config.php`, que debería estar en el control de código fuente. Para anular, opcionalmente, cualquier configuración o definir ajustes confidenciales, consulte [Usar variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables). Este tema sí _not_ list [valores confidenciales y específicos del sistema](config-reference-sens.md).

La configuración se organiza aún más por método de pago.

## Rutas PayPal

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitar esta solución | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la experiencia de cierre de compra en contexto | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar crédito de PayPal | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar crédito de PayPal | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posición | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posición | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posición | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posición | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tamaño | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar en la página Detalles del producto | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar en carro de compras | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir artículos de línea del carro de compras | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Omitir paso de revisión de pedido | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir artículos de línea del carro de compras | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir opciones de envío | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Flavor de botones de acceso directo | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar el cierre de compra de invitado de PayPal | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Requerir dirección de facturación del cliente | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suscripción al contrato de facturación | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transferir artículos de línea del carro de compras | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir en Asistente de Acuerdo de Facturación | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la captura automática | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Programación | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora del día | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logotipo de producto PayPal | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de página | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dirección URL de imagen de encabezado | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Color de fondo de encabezado | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Color del borde del encabezado | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Color de fondo de página | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar esta solución | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordenar crédito PayPal | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar en la página Detalles del producto | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de honor de la autorización (días) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período válido de pedido (días) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de autorizaciones secundarias | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar en carro de compras | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## PayPal Payments Pro

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Métodos de autenticación de API | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La API utiliza el proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Solución alojada en Payments Pro (Reino Unido)

Estas opciones solo están disponibles si elige el Reino Unido como el [país comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitar esta solución | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar el cierre de compra exprés en el paso Información de pago | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## PayPal Payflow Pro

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Vault habilitado | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título de la caja fuerte | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito permitidos | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Requerir entrada de CVV | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La calle AVS no coincide | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| El Zip de AVS no coincide | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| El indicador internacional AVS no coincide | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| El código de seguridad de la tarjeta no coincide | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proveedor | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar proxy | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Socio | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proveedor | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar proxy | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar esta solución | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La entrada de CVV es editable | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Requerir entrada de CVV | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar confirmación de correo electrónico | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Vínculo de flujo de trabajo de PayPal

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Socio | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proveedor | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar vínculo de flujo de navegación | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar el cierre de compra exprés | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordenar crédito PayPal | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago Aplicable Desde | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Países Pagos Aplicables Desde | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar verificación SSL | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| La entrada de CVV es editable | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Requerir entrada de CVV | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar confirmación de correo electrónico | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Cero rutas de cierre de compra de subtotal

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitado | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de pago de efectivo al enviar

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitado | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de pago de transferencia bancaria

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitado | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de cheque o de pedido de dinero

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitado | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hacer que la comprobación sea pagable a | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de orden de compra

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Habilitado | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas internacionales

>[!INFO]
>
>Las rutas disponibles están determinadas por su elección de [País comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| Credenciales SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar esta solución | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de la tarjeta de crédito | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hacer que la comprobación sea pagable a | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comprobación a | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_nz/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_nz/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_nz/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_nz/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_nz/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_nz/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_nz/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_nz/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_nz/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_nz/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_nz/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_nz/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_nz/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_nz/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_nz/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_nz/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_nz/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_nz/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_nz/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_nz/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_nz/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_nz/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_nz/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_nz/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_nz/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_nz/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_nz/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_nz/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_nz/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_nz/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_nz/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_nz/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_nz/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_hk/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_hk/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_hk/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_hk/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_hk/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_hk/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_hk/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_hk/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_hk/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_hk/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_hk/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_hk/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_hk/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_hk/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_hk/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_hk/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_hk/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_hk/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_hk/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_hk/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_hk/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_hk/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_hk/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_hk/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_hk/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_hk/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de espacio aislado | `payment_hk/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_hk/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_hk/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_hk/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_hk/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_hk/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_hk/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hacer que la comprobación sea pagable a | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_es/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_es/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_es/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID de perfil | `payment_es/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |
| Nuevo estado de pedido | `payment_es/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_es/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_es/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_es/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_es/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_es/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_es/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_es/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_es/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_es/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID de instalación | `payment_es/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID de instalación de administración remota | `payment_es/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_es/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_es/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_es/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de prueba | `payment_es/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_es/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_es/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_es/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_es/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_es/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_es/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_es/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_es/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_es/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_es/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_es/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_es/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_es/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_es/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_es/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_es/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_it/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_it/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_it/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_it/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_it/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_it/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_it/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_it/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_it/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_it/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_it/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_it/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_it/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_it/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_it/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_it/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_it/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_it/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_it/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_it/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_it/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_it/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_it/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_it/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_it/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_it/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_it/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_it/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_it/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_it/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_it/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_it/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_it/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_fr/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_fr/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_fr/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_fr/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_fr/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_fr/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_fr/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_fr/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_fr/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_fr/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_fr/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_fr/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_fr/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_fr/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_fr/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_fr/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_fr/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_fr/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_fr/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_fr/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_fr/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_fr/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_fr/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_fr/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_fr/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_fr/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_fr/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_fr/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_fr/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_fr/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_fr/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_fr/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_jp/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_jp/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_jp/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_jp/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_jp/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_jp/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_jp/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_jp/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_jp/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_jp/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_jp/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_jp/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_jp/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_jp/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_jp/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_jp/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_jp/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_jp/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_jp/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_jp/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_jp/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_jp/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_jp/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_jp/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_jp/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_jp/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_jp/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_jp/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_jp/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_jp/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_jp/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de la tarjeta de crédito | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hacer que la comprobación sea pagable a | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enviar comprobación a | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_au/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_au/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_au/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID del comerciante | `payment_au/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |
| ID de perfil | `payment_au/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |
| Nuevo estado de pedido | `payment_au/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_au/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_au/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_au/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_au/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_au/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_au/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_au/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_au/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_au/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID de instalación | `payment_au/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_au/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_au/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_au/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_au/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de prueba | `payment_au/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_au/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_au/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_au/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_au/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_au/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_au/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_au/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_au/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_au/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_au/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_au/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_au/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_au/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_au/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_au/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_au/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar esta solución | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de la tarjeta de crédito | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de la tarjeta de crédito | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_ca/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_ca/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_ca/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_ca/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_ca/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_ca/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_ca/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_ca/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_ca/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_ca/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_ca/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_ca/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_ca/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_ca/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_ca/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_ca/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_ca/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_ca/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_ca/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_ca/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_ca/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_ca/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_ca/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_ca/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_ca/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_ca/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_ca/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_ca/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_ca/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_ca/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_ca/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_ca/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cliente de correo electrónico | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_other/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_other/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_other/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_other/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_other/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_other/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_other/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_other/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_other/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_other/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_other/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_other/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_other/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_other/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_other/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_other/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_other/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_other/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_other/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_other/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_other/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_other/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_other/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_other/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_other/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_other/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_other/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_other/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_other/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_other/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_other/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_other/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_de/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_de/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_de/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_de/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_de/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_de/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_de/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_de/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_de/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_de/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_de/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_de/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_de/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_de/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_de/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de prueba | `payment_de/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_de/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_de/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_de/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_de/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_de/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_de/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_de/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_de/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_de/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_de/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_de/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_de/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_de/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_de/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_de/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_de/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hacer que la comprobación sea pagable a | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_gb/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_gb/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_gb/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_gb/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_gb/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_gb/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_gb/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_gb/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_gb/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_gb/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_gb/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_gb/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Secreto MD5 para transacciones | `payment_gb/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_gb/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_gb/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_gb/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_gb/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_gb/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_gb/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_gb/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_gb/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_gb/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_gb/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_gb/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_gb/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_gb/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_gb/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_gb/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_gb/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_gb/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_gb/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_gb/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_gb/eway/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Captura programada | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de la tarjeta de crédito | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar crédito de PayPal | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de la tarjeta de crédito | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rechazar transacción si: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Captura programada | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estilo de páginas comerciales de PayPal | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Facturar automáticamente todos los artículos | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instrucciones | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hacer que la comprobación sea pagable a | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acción de pago | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Título | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuevo estado de pedido | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moneda aceptada | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Depuración | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipos de tarjetas de crédito | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificación de la tarjeta de crédito | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de los países aplicables | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pago de países específicos | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido mínimo | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Total de pedido máximo | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Orden | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `payment_us/cybersource/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_us/cybersource/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_us/cybersource/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Nuevo estado de pedido | `payment_us/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_us/cybersource/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_us/cybersource/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_us/cybersource/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_us/cybersource/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido mínimo | `payment_us/cybersource/min_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Total de pedido máximo | `payment_us/cybersource/max_order_total` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_us/cybersource/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_us/worldpay/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_us/worldpay/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir Editar Información De Contacto | `payment_us/worldpay/fix_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Ocultar información de contacto | `payment_us/worldpay/hide_contact` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Campos de firma | `payment_us/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_us/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago para pruebas | `payment_us/worldpay/test_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_us/worldpay/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Los Países Aplicables | `payment_us/worldpay/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago De Países Específicos | `payment_us/worldpay/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Configurar el estado del pedido a Fraude sospechoso para CVV | `payment_us/worldpay/cvv_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Definir el estado del pedido como posible fraude para el AVS de código postal | `payment_us/worldpay/avs_fraud_case` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_us/worldpay/sort_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitado | `payment_us/eway/active` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipo de conexión | `payment_us/eway/connection_type` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Título | `payment_us/eway/title` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Acción de pago | `payment_us/eway/payment_action` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Depuración | `payment_us/eway/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Tipos de tarjetas de crédito | `payment_us/eway/cctypes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de los países aplicables | `payment_us/eway/allowspecific` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Pago de países específicos | `payment_us/eway/specificcountry` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Orden | `payment_us/eway/sort_order` |  |

{style=&quot;table-layout:auto&quot;}
