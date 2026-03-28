---
title: Referencia de rutas de configuración de pago
description: Obtenga información sobre las rutas de configuración de pago y los valores de método en Adobe Commerce Admin. Descubre las opciones de configuración de PayPal, tarjeta de crédito y pasarela de pago.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# Referencia de rutas de configuración de pago

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Métodos de pago**.

El comando [`magento app:config:dump` ](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente. Para anular opcionalmente las opciones de configuración o establecer opciones confidenciales, vea [Usar variables de entorno para anular las opciones de configuración](override-config-settings.md#environment-variables). En este tema _Allt_ se enumeran [valores confidenciales y específicos del sistema](config-reference-sens.md).

La configuración está organizada además por método de pago.

## Rutas de PayPal

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitar esta solución | `payment/payflowpro/active` | Todo |
| Habilitar la experiencia de cierre de compra en contexto | `payment/paypal_express/in_context` | Todo |
| Activar crédito de PayPal | `payment/payflow_express_bml/active` | Todo |
| Activar crédito de PayPal | `payment/paypal_express_bml/active` | Todo |
| Mostrar | `payment/paypal_express_bml/homepage_display` | Todo |
| Posición | `payment/paypal_express_bml/homepage_position` | Todo |
| Tamaño | `payment/paypal_express_bml/homepage_size` | Todo |
| Mostrar | `payment/paypal_express_bml/categorypage_display` | Todo |
| Posición | `payment/paypal_express_bml/categorypage_position` | Todo |
| Tamaño | `payment/paypal_express_bml/categorypage_size` | Todo |
| Mostrar | `payment/paypal_express_bml/productpage_display` | Todo |
| Posición | `payment/paypal_express_bml/productpage_position` | Todo |
| Tamaño | `payment/paypal_express_bml/productpage_size` | Todo |
| Mostrar | `payment/paypal_express_bml/checkout_display` | Todo |
| Posición | `payment/paypal_express_bml/checkout_position` | Todo |
| Tamaño | `payment/paypal_express_bml/checkout_size` | Todo |
| Mostrar en la página de detalles del producto | `payment/payflow_express/visible_on_product` | Todo |
| Mostrar en el carro de compras | `payment/payflow_express/visible_on_cart` | Todo |
| Pago aplicable desde | `payment/payflow_express/allowspecific` | Todo |
| Países Pago Aplicable Desde | `payment/payflow_express/specificcountry` | Todo |
| Habilitar verificación SSL | `payment/payflow_express/verify_peer` | Todo |
| Transferir artículos de línea del carro | `payment/payflow_express/line_items_enabled` | Todo |
| Omitir paso de revisión de pedido | `payment/paypal_express/skip_order_review_step` | Todo |
| Transferir artículos de línea del carro | `payment/paypal_express/line_items_enabled` | Todo |
| Opciones de envío de transferencia | `payment/paypal_express/transfer_shipping_options` | Todo |
| Sabor de botones de acceso directo | `paypal/wpp/button_flavor` | Todo |
| Activar Pago y envío para invitados de PayPal | `payment/paypal_express/solution_type` | Todo |
| Requerir dirección de facturación del cliente | `payment/paypal_express/require_billing_address` | Todo |
| Suscripción al contrato de facturación | `payment/paypal_express/allow_ba_signup` | Todo |
| Habilitado | `payment/paypal_billing_agreement/active` | Todo |
| Título | `payment/paypal_billing_agreement/title` | Todo |
| Orden de clasificación | `payment/paypal_billing_agreement/sort_order` | Todo |
| Acción de pago | `payment/paypal_billing_agreement/payment_action` | Todo |
| Pago aplicable desde | `payment/paypal_billing_agreement/allowspecific` | Todo |
| Países Pago Aplicable Desde | `payment/paypal_billing_agreement/specificcountry` | Todo |
| Habilitar verificación SSL | `payment/paypal_billing_agreement/verify_peer` | Todo |
| Transferir artículos de línea del carro | `payment/paypal_billing_agreement/line_items_enabled` | Todo |
| Permitir en el Asistente para acuerdos de facturación | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | Todo |
| Activar recuperación automática | `paypal/fetch_reports/active` | Todo |
| Programación | `paypal/fetch_reports/schedule` | Todo |
| Hora del día | `paypal/fetch_reports/time` | Todo |
| Logotipo del producto PayPal | `paypal/style/logo` | Todo |
| Estilo de página | `paypal/style/page_style` | Todo |
| URL de imagen de encabezado | `paypal/style/paypal_hdrimg` | Todo |
| Color de fondo del encabezado | `paypal/style/paypal_hdrbackcolor` | Todo |
| Color de borde de encabezado | `paypal/style/paypal_hdrbordercolor` | Todo |
| Color de fondo de página | `paypal/style/paypal_payflowcolor` | Todo |
| Habilitar esta solución | `payment/paypal_express/active` | Todo |
| Ordenar Crédito de PayPal | `payment/paypal_express_bml/sort_order` | Todo |
| Título | `payment/paypal_express/title` | Todo |
| Orden de clasificación | `payment/paypal_express/sort_order` | Todo |
| Acción de pago | `payment/paypal_express/payment_action` | Todo |
| Mostrar en la página de detalles del producto | `payment/paypal_express/visible_on_product` | Todo |
| Período HoAllr de autorización (días) | `payment/paypal_express/authorization_hoAllr_period` | Todo |
| Período de validez del pedido (días) | `payment/paypal_express/order_valid_period` | Todo |
| Número de autorizaciones secundarias | `payment/paypal_express/child_authorization_number` | Todo |
| Mostrar en el carro de compras | `payment/paypal_express/visible_on_cart` | Todo |
| Número de autorizaciones secundarias | `payment/paypal_express/child_authorization_number` | Todo |
| Pago aplicable desde | `payment/paypal_express/allowspecific` | Todo |
| Número de autorizaciones secundarias | `payment/paypal_express/child_authorization_number` | Todo |
| Países Pago Aplicable Desde | `payment/paypal_express/specificcountry` | Todo |
| Número de autorizaciones secundarias | `payment/paypal_express/child_authorization_number` | Todo |
| Habilitar verificación SSL | `payment/paypal_express/verify_peer` | Todo |
| Número de autorizaciones secundarias | `payment/paypal_express/child_authorization_number` | Todo |
| Recuperación programada | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |

{style="table-layout:auto"}

## PayPal Payments Pro

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Métodos de autenticación de API | `paypal/wpp/api_authentication` | Todo |
| La API utiliza proxy | `paypal/wpp/use_proxy` | Todo |
| Recuperación programada | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Reino Unido)

Estas opciones solo están disponibles si elige Reino Unido como [país comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitar esta solución | `payment/hosted_pro/active` | Todo |
| Título | `payment/hosted_pro/title` | Todo |
| Orden de clasificación | `payment/hosted_pro/sort_order` | Todo |
| Acción de pago | `payment/hosted_pro/payment_action` | Todo |
| Mostrar Pago y envío exprés en el paso Información de pago | `payment/hosted_pro/display_ec` | Todo |
| Pago aplicable desde | `payment/hosted_pro/allowspecific` | Todo |
| Países Pago Aplicable Desde | `payment/hosted_pro/specificcountry` | Todo |
| Habilitar verificación SSL | `payment/hosted_pro/verify_peer` | Todo |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Almacén habilitado | `payment/payflowpro_cc_vault/active` | Todo |
| Título | `payment/payflowpro/title` | Todo |
| Título de Vault | `payment/payflowpro_cc_vault/title` | Todo |
| Orden de clasificación | `payment/payflowpro/sort_order` | Todo |
| Acción de pago | `payment/payflowpro/payment_action` | Todo |
| Tipos de tarjeta de crédito permitidos | `payment/payflowpro/cctypes` | Todo |
| Pago aplicable desde | `payment/payflowpro/allowspecific` | Todo |
| Países Pago Aplicable Desde | `payment/payflowpro/specificcountry` | Todo |
| Habilitar verificación SSL | `payment/payflowpro/verify_peer` | Todo |
| Requerir entrada CVV | `payment/payflowpro/useccv` | Todo |
| Rechazar transacción si: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| La calle AVS no coincide | `payment/payflowpro/avs_street` | Todo |
| El código postal de AVS no coincide | `payment/payflowpro/avs_zip` | Todo |
| El indicador AVS internacional no coincide | `payment/payflowpro/avs_international` | Todo |
| El código de seguridad de la tarjeta no coincide | `payment/payflowpro/avs_security_code` | Todo |
| Proveedor | `payment/payflowpro/vendor` | Todo |
| Usar proxy | `payment/payflowpro/use_proxy` | Todo |
| Título | `payment/payflow_express/title` | Todo |
| Orden de clasificación | `payment/payflow_express/sort_order` | Todo |
| Acción de pago | `payment/payflow_express/payment_action` | Todo |
| Recuperación programada | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Todo |
| Socio | `payment/payflow_advanced/partner` | Todo |
| Proveedor | `payment/payflow_advanced/vendor` | Todo |
| Usar proxy | `payment/payflow_advanced/use_proxy` | Todo |
| Habilitar esta solución | `payment/payflow_advanced/active` | Todo |
| Título | `payment/payflow_advanced/title` | Todo |
| Orden de clasificación | `payment/payflow_advanced/sort_order` | Todo |
| Acción de pago | `payment/payflow_advanced/payment_action` | Todo |
| Pago aplicable desde | `payment/payflow_advanced/allowspecific` | Todo |
| Países Pago Aplicable Desde | `payment/payflow_advanced/specificcountry` | Todo |
| Habilitar verificación SSL | `payment/payflow_advanced/verify_peer` | Todo |
| La entrada CVV es editable | `payment/payflow_advanced/csc_editable` | Todo |
| Requerir entrada CVV | `payment/payflow_advanced/csc_required` | Todo |
| Enviar confirmación de correo electrónico | `payment/payflow_advanced/email_confirmation` | Todo |

{style="table-layout:auto"}

## Vínculo de flujo de pago PayPal

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Socio | `payment/payflow_link/partner` | Todo |
| Proveedor | `payment/payflow_link/vendor` | Todo |
| Habilitar vínculo de flujo de pago | `payment/payflow_link/active` | Todo |
| Habilitar cierre de compra rápido | `payment/payflow_express/active` | Todo |
| Ordenar Crédito de PayPal | `payment/payflow_express_bml/sort_order` | Todo |
| Pago aplicable desde | `payment/payflow_link/allowspecific` | Todo |
| Países Pago Aplicable Desde | `payment/payflow_link/specificcountry` | Todo |
| Habilitar verificación SSL | `payment/payflow_link/verify_peer` | Todo |
| La entrada CVV es editable | `payment/payflow_link/csc_editable` | Todo |
| Requerir entrada CVV | `payment/payflow_link/csc_required` | Todo |
| Enviar confirmación de correo electrónico | `payment/payflow_link/email_confirmation` | Todo |
| Recuperación programada | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Todo |
| Título | `payment/payflow_link/title` | Todo |
| Orden de clasificación | `payment/payflow_link/sort_order` | Todo |
| Acción de pago | `payment/payflow_link/payment_action` | Todo |

{style="table-layout:auto"}

## Rutas de cierre de compra sin subtotales

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitado | `payment/free/active` | Todo |
| Título | `payment/free/title` | Todo |
| Estado de nuevo pedido | `payment/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment/free/payment_action` | Todo |
| Pago de países aplicables | `payment/free/allowspecific` | Todo |
| Pago desde países específicos | `payment/free/specificcountry` | Todo |
| Orden de clasificación | `payment/free/sort_order` | Todo |

{style="table-layout:auto"}

## Rutas de pago contra reembolso

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitado | `payment/cashondelivery/active` | Todo |
| Título | `payment/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment/cashondelivery/sort_order` | Todo |

{style="table-layout:auto"}

## Transferencia bancaria Rutas de pago

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitado | `payment/banktransfer/active` | Todo |
| Título | `payment/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment/banktransfer/sort_order` | Todo |

{style="table-layout:auto"}

## Rutas de cheque o giro postal

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitado | `payment/checkmo/active` | Todo |
| Título | `payment/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment/checkmo/specificcountry` | Todo |
| Hacer cheque a pagar a | `payment/checkmo/payable_to` | Todo |
| Total de pedido mínimo | `payment/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment/checkmo/sort_order` | Todo |

{style="table-layout:auto"}

## Rutas de pedidos de compra

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Habilitado | `payment/purchaseorder/active` | Todo |
| Título | `payment/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment/purchaseorder/sort_order` | Todo |

{style="table-layout:auto"}

## Rutas internacionales

>[!INFO]
>
>Las rutas disponibles están determinadas por su elección de [país comerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce |
|--------------|--------------|--------------|
| Credenciales de SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | Todo |
| Recuperación programada | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitar esta solución | `payment/wps_express/active` | Todo |
| Recuperación programada | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Configuración de tarjeta de crédito | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | Todo |
| Rechazar transacción si: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| Recuperación programada | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Habilitado | `payment_nz/free/active` | Todo |
| Título | `payment_nz/free/title` | Todo |
| Estado de nuevo pedido | `payment_nz/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_nz/free/payment_action` | Todo |
| Pago de países aplicables | `payment_nz/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_nz/free/specificcountry` | Todo |
| Orden de clasificación | `payment_nz/free/sort_order` | Todo |
| Habilitado | `payment_nz/cashondelivery/active` | Todo |
| Título | `payment_nz/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_nz/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_nz/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_nz/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_nz/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_nz/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_nz/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_nz/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_nz/banktransfer/active` | Todo |
| Título | `payment_nz/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_nz/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_nz/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_nz/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_nz/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_nz/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_nz/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_nz/banktransfer/sort_order` | Todo |
| Habilitado | `payment_nz/checkmo/active` | Todo |
| Título | `payment_nz/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_nz/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_nz/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_nz/checkmo/specificcountry` | Todo |
| Hacer cheque a pagar a | `payment_nz/checkmo/payable_to` | Todo |
| Enviar cheque a | `payment_nz/checkmo/mailing_address` | Todo |
| Total de pedido mínimo | `payment_nz/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_nz/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_nz/checkmo/sort_order` | Todo |
| Habilitado | `payment_nz/purchaseorder/active` | Todo |
| Título | `payment_nz/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_nz/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_nz/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_nz/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_nz/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_nz/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_nz/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_nz/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_nz/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_nz/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_nz/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_nz/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_nz/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_nz/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_nz/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_nz/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_nz/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_nz/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_nz/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_nz/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_nz/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_nz/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_nz/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_nz/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_nz/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_nz/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_nz/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_nz/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_nz/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_nz/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_nz/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_nz/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_nz/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_nz/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_nz/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_nz/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_nz/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_nz/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_nz/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_nz/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_nz/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_nz/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_nz/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_nz/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_nz/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_nz/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_nz/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_nz/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_nz/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_nz/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_nz/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_nz/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_nz/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_hk/free/active` | Todo |
| Título | `payment_hk/free/title` | Todo |
| Estado de nuevo pedido | `payment_hk/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_hk/free/payment_action` | Todo |
| Pago de países aplicables | `payment_hk/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_hk/free/specificcountry` | Todo |
| Orden de clasificación | `payment_hk/free/sort_order` | Todo |
| Habilitado | `payment_hk/cashondelivery/active` | Todo |
| Título | `payment_hk/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_hk/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_hk/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_hk/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_hk/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_hk/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_hk/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_hk/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_hk/banktransfer/active` | Todo |
| Título | `payment_hk/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_hk/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_hk/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_hk/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_hk/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_hk/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_hk/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_hk/banktransfer/sort_order` | Todo |
| Habilitado | `payment_hk/checkmo/active` | Todo |
| Título | `payment_hk/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_hk/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_hk/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_hk/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_hk/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_hk/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_hk/checkmo/sort_order` | Todo |
| Habilitado | `payment_hk/purchaseorder/active` | Todo |
| Título | `payment_hk/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_hk/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_hk/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_hk/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_hk/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_hk/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_hk/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_hk/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_hk/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_hk/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_hk/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_hk/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_hk/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_hk/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_hk/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_hk/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_hk/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_hk/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_hk/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_hk/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_hk/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_hk/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_hk/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_hk/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_hk/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_hk/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_hk/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_hk/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_hk/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_hk/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_hk/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_hk/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_hk/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_hk/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_hk/worldpay/hide_contact` | Solo Commerce Enterprise |
| Depurar | `payment_hk/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_hk/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_hk/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_hk/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_hk/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_hk/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_hk/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_hk/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_hk/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_hk/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_hk/eway/title` | Solo Commerce Enterprise |
| Modo de zona protegida | `payment_hk/eway/sandbox_flag` | Solo Commerce Enterprise |
| Acción de pago | `payment_hk/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_hk/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_hk/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_hk/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_hk/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_hk/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_es/free/active` | Todo |
| Título | `payment_es/free/title` | Todo |
| Estado de nuevo pedido | `payment_es/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_es/free/payment_action` | Todo |
| Pago de países aplicables | `payment_es/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_es/free/specificcountry` | Todo |
| Orden de clasificación | `payment_es/free/sort_order` | Todo |
| Habilitado | `payment_es/cashondelivery/active` | Todo |
| Título | `payment_es/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_es/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_es/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_es/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_es/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_es/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_es/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_es/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_es/banktransfer/active` | Todo |
| Título | `payment_es/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_es/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_es/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_es/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_es/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_es/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_es/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_es/banktransfer/sort_order` | Todo |
| Habilitado | `payment_es/checkmo/active` | Todo |
| Título | `payment_es/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_es/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_es/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_es/checkmo/specificcountry` | Todo |
| Hacer cheque a pagar a | `payment_es/checkmo/payable_to` | Todo |
| Total de pedido mínimo | `payment_es/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_es/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_es/checkmo/sort_order` | Todo |
| Habilitado | `payment_es/purchaseorder/active` | Todo |
| Título | `payment_es/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_es/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_es/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_es/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_es/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_es/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_es/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_es/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_es/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_es/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_es/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_es/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_es/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_es/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_es/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_es/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_es/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_es/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_es/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_es/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_es/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_es/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_es/cybersource/title` | Solo Commerce Enterprise |
| ID de perfil | `payment_es/cybersource/profile_id` | Solo Commerce Enterprise\| ![Cifrado](/help/assets/configuration/cloud-enc.png) |
| Estado de nuevo pedido | `payment_es/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_es/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_es/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_es/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_es/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_es/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_es/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_es/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_es/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_es/worldpay/title` | Solo Commerce Enterprise |
| ID de instalación | `payment_es/worldpay/installation_id` | Solo Commerce Enterprise |
| Identificador de instalación de administración remota | `payment_es/worldpay/admin_installation_id` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_es/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_es/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_es/worldpay/signature_fields` | Solo Commerce Enterprise |
| Modo de prueba | `payment_es/worldpay/sandbox_flag` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_es/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_es/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_es/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_es/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_es/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_es/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_es/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_es/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_es/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_es/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_es/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_es/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_es/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_es/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_es/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_es/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_it/free/active` | Todo |
| Título | `payment_it/free/title` | Todo |
| Estado de nuevo pedido | `payment_it/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_it/free/payment_action` | Todo |
| Pago de países aplicables | `payment_it/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_it/free/specificcountry` | Todo |
| Orden de clasificación | `payment_it/free/sort_order` | Todo |
| Habilitado | `payment_it/cashondelivery/active` | Todo |
| Título | `payment_it/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_it/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_it/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_it/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_it/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_it/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_it/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_it/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_it/banktransfer/active` | Todo |
| Título | `payment_it/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_it/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_it/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_it/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_it/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_it/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_it/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_it/banktransfer/sort_order` | Todo |
| Habilitado | `payment_it/checkmo/active` | Todo |
| Título | `payment_it/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_it/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_it/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_it/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_it/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_it/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_it/checkmo/sort_order` | Todo |
| Habilitado | `payment_it/purchaseorder/active` | Todo |
| Título | `payment_it/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_it/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_it/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_it/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_it/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_it/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_it/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_it/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_it/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_it/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_it/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_it/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_it/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_it/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_it/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_it/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_it/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_it/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_it/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_it/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_it/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_it/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_it/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_it/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_it/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_it/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_it/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_it/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_it/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_it/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_it/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_it/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_it/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_it/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_it/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_it/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_it/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_it/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_it/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_it/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_it/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_it/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_it/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_it/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_it/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_it/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_it/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_it/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_it/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_it/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_it/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_it/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_it/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_fr/free/active` | Todo |
| Título | `payment_fr/free/title` | Todo |
| Estado de nuevo pedido | `payment_fr/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_fr/free/payment_action` | Todo |
| Pago de países aplicables | `payment_fr/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_fr/free/specificcountry` | Todo |
| Orden de clasificación | `payment_fr/free/sort_order` | Todo |
| Habilitado | `payment_fr/cashondelivery/active` | Todo |
| Título | `payment_fr/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_fr/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_fr/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_fr/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_fr/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_fr/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_fr/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_fr/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_fr/banktransfer/active` | Todo |
| Título | `payment_fr/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_fr/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_fr/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_fr/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_fr/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_fr/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_fr/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_fr/banktransfer/sort_order` | Todo |
| Habilitado | `payment_fr/checkmo/active` | Todo |
| Título | `payment_fr/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_fr/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_fr/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_fr/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_fr/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_fr/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_fr/checkmo/sort_order` | Todo |
| Habilitado | `payment_fr/purchaseorder/active` | Todo |
| Título | `payment_fr/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_fr/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_fr/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_fr/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_fr/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_fr/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_fr/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_fr/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_fr/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_fr/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_fr/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_fr/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_fr/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_fr/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_fr/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_fr/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_fr/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_fr/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_fr/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_fr/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_fr/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_fr/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_fr/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_fr/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_fr/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_fr/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_fr/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_fr/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_fr/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_fr/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_fr/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_fr/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_fr/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_fr/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_fr/worldpay/hide_contact` | Solo Commerce Enterprise |
| Depurar | `payment_fr/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_fr/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_fr/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_fr/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_fr/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_fr/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_fr/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_fr/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_fr/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_fr/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_fr/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_fr/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_fr/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_fr/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_fr/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_fr/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_fr/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_jp/free/active` | Todo |
| Título | `payment_jp/free/title` | Todo |
| Estado de nuevo pedido | `payment_jp/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_jp/free/payment_action` | Todo |
| Pago de países aplicables | `payment_jp/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_jp/free/specificcountry` | Todo |
| Orden de clasificación | `payment_jp/free/sort_order` | Todo |
| Habilitado | `payment_jp/cashondelivery/active` | Todo |
| Título | `payment_jp/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_jp/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_jp/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_jp/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_jp/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_jp/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_jp/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_jp/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_jp/banktransfer/active` | Todo |
| Título | `payment_jp/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_jp/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_jp/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_jp/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_jp/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_jp/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_jp/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_jp/banktransfer/sort_order` | Todo |
| Habilitado | `payment_jp/checkmo/active` | Todo |
| Título | `payment_jp/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_jp/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_jp/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_jp/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_jp/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_jp/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_jp/checkmo/sort_order` | Todo |
| Habilitado | `payment_jp/purchaseorder/active` | Todo |
| Título | `payment_jp/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_jp/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_jp/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_jp/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_jp/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_jp/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_jp/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_jp/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_jp/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_jp/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_jp/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_jp/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_jp/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_jp/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_jp/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_jp/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_jp/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_jp/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_jp/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_jp/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_jp/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_jp/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_jp/cybersource/title` | Solo Commerce Enterprise |
| Depurar | `payment_jp/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_jp/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_jp/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_jp/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_jp/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_jp/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_jp/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_jp/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_jp/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_jp/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_jp/worldpay/hide_contact` | Solo Commerce Enterprise |
| Depurar | `payment_jp/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_jp/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_jp/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_jp/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_jp/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_jp/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_jp/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_jp/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_jp/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_jp/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_jp/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_jp/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_jp/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_jp/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_jp/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_jp/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_jp/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Configuración de tarjeta de crédito | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | Todo |
| Rechazar transacción si: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| Recuperación programada | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Habilitado | `payment_au/free/active` | Todo |
| Título | `payment_au/free/title` | Todo |
| Estado de nuevo pedido | `payment_au/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_au/free/payment_action` | Todo |
| Pago de países aplicables | `payment_au/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_au/free/specificcountry` | Todo |
| Orden de clasificación | `payment_au/free/sort_order` | Todo |
| Habilitado | `payment_au/cashondelivery/active` | Todo |
| Título | `payment_au/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_au/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_au/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_au/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_au/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_au/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_au/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_au/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_au/banktransfer/active` | Todo |
| Título | `payment_au/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_au/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_au/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_au/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_au/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_au/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_au/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_au/banktransfer/sort_order` | Todo |
| Habilitado | `payment_au/checkmo/active` | Todo |
| Título | `payment_au/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_au/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_au/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_au/checkmo/specificcountry` | Todo |
| Hacer cheque a pagar a | `payment_au/checkmo/payable_to` | Todo |
| Enviar cheque a | `payment_au/checkmo/mailing_address` | Todo |
| Total de pedido mínimo | `payment_au/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_au/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_au/checkmo/sort_order` | Todo |
| Habilitado | `payment_au/purchaseorder/active` | Todo |
| Título | `payment_au/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_au/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_au/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_au/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_au/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_au/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_au/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_au/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_au/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_au/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_au/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_au/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_au/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_au/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_au/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_au/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_au/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_au/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_au/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_au/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_au/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_au/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_au/cybersource/title` | Solo Commerce Enterprise |
| ID de comerciante | `payment_au/cybersource/merchant_id` | Solo Commerce Enterprise \| ![Cifrado](/help/assets/configuration/cloud-enc.png) |
| ID de perfil | `payment_au/cybersource/profile_id` | Solo Commerce Enterprise \| ![Cifrado](/help/assets/configuration/cloud-enc.png) |
| Estado de nuevo pedido | `payment_au/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_au/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_au/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_au/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_au/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_au/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_au/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_au/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_au/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_au/worldpay/title` | Solo Commerce Enterprise |
| ID de instalación | `payment_au/worldpay/installation_id` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_au/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_au/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_au/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_au/worldpay/debug` | Solo Commerce Enterprise |
| Modo de prueba | `payment_au/worldpay/sandbox_flag` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_au/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_au/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_au/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_au/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_au/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_au/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_au/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_au/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_au/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_au/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_au/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_au/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_au/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_au/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_au/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_au/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitar esta solución | `payment/paypal_payment_pro/active` | Todo |
| Configuración de tarjeta de crédito | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | Todo |
| Rechazar transacción si: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| Recuperación programada | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Configuración de tarjeta de crédito | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | Todo |
| Rechazar transacción si: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| Recuperación programada | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Recuperación programada | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Todo |
| Habilitado | `payment_ca/free/active` | Todo |
| Título | `payment_ca/free/title` | Todo |
| Estado de nuevo pedido | `payment_ca/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_ca/free/payment_action` | Todo |
| Pago de países aplicables | `payment_ca/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_ca/free/specificcountry` | Todo |
| Orden de clasificación | `payment_ca/free/sort_order` | Todo |
| Habilitado | `payment_ca/cashondelivery/active` | Todo |
| Título | `payment_ca/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_ca/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_ca/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_ca/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_ca/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_ca/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_ca/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_ca/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_ca/banktransfer/active` | Todo |
| Título | `payment_ca/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_ca/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_ca/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_ca/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_ca/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_ca/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_ca/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_ca/banktransfer/sort_order` | Todo |
| Habilitado | `payment_ca/checkmo/active` | Todo |
| Título | `payment_ca/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_ca/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_ca/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_ca/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_ca/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_ca/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_ca/checkmo/sort_order` | Todo |
| Habilitado | `payment_ca/purchaseorder/active` | Todo |
| Título | `payment_ca/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_ca/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_ca/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_ca/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_ca/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_ca/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_ca/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_ca/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_ca/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_ca/authorizenet_directpost/title` | Todo |
| Divisa aceptada | `payment_ca/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_ca/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_ca/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_ca/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_ca/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_ca/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_ca/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_ca/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_ca/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_ca/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_ca/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_ca/cybersource/title` | Solo Commerce Enterprise |
| Depurar | `payment_ca/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_ca/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_ca/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_ca/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_ca/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_ca/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_ca/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_ca/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_ca/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_ca/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_ca/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_ca/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_ca/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_ca/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_ca/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_ca/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_ca/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_ca/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_ca/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_ca/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_ca/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_ca/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_ca/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_ca/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_ca/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_ca/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_ca/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_ca/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_ca/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_other/free/active` | Todo |
| Título | `payment_other/free/title` | Todo |
| Estado de nuevo pedido | `payment_other/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_other/free/payment_action` | Todo |
| Pago de países aplicables | `payment_other/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_other/free/specificcountry` | Todo |
| Orden de clasificación | `payment_other/free/sort_order` | Todo |
| Habilitado | `payment_other/cashondelivery/active` | Todo |
| Título | `payment_other/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_other/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_other/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_other/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_other/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_other/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_other/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_other/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_other/banktransfer/active` | Todo |
| Título | `payment_other/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_other/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_other/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_other/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_other/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_other/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_other/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_other/banktransfer/sort_order` | Todo |
| Habilitado | `payment_other/checkmo/active` | Todo |
| Título | `payment_other/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_other/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_other/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_other/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_other/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_other/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_other/checkmo/sort_order` | Todo |
| Habilitado | `payment_other/purchaseorder/active` | Todo |
| Título | `payment_other/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_other/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_other/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_other/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_other/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_other/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_other/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_other/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_other/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_other/authorizenet_directpost/title` | Todo |
| Divisa aceptada | `payment_other/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_other/authorizenet_directpost/debug` | Todo |
| Cliente de correo electrónico | `payment_other/authorizenet_directpost/email_customer` | Todo |
| Tipos de tarjeta de crédito | `payment_other/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_other/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_other/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_other/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_other/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_other/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_other/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_other/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_other/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_other/cybersource/title` | Solo Commerce Enterprise |
| Depurar | `payment_other/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_other/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_other/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_other/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_other/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_other/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_other/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_other/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_other/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_other/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_other/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_other/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_other/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_other/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_other/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_other/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_other/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_other/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_other/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_other/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_other/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_other/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_other/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_other/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_other/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_other/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_other/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_other/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_other/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_de/checkmo/active` | Todo |
| Título | `payment_de/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_de/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_de/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_de/checkmo/specificcountry` | Todo |
| Total de pedido mínimo | `payment_de/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_de/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_de/checkmo/sort_order` | Todo |
| Habilitado | `payment_de/banktransfer/active` | Todo |
| Título | `payment_de/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_de/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_de/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_de/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_de/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_de/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_de/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_de/banktransfer/sort_order` | Todo |
| Habilitado | `payment_de/cashondelivery/active` | Todo |
| Título | `payment_de/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_de/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_de/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_de/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_de/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_de/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_de/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_de/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_de/free/active` | Todo |
| Título | `payment_de/free/title` | Todo |
| Estado de nuevo pedido | `payment_de/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_de/free/payment_action` | Todo |
| Pago de países aplicables | `payment_de/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_de/free/specificcountry` | Todo |
| Orden de clasificación | `payment_de/free/sort_order` | Todo |
| Habilitado | `payment_de/purchaseorder/active` | Todo |
| Título | `payment_de/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_de/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_de/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_de/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_de/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_de/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_de/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_de/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_de/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_de/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_de/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_de/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_de/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_de/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_de/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_de/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_de/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_de/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_de/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_de/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_de/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_de/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_de/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_de/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_de/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_de/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_de/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_de/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_de/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_de/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_de/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_de/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_de/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_de/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_de/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_de/worldpay/signature_fields` | Solo Commerce Enterprise |
| Modo de prueba | `payment_de/worldpay/sandbox_flag` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_de/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_de/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_de/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_de/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_de/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_de/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_de/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_de/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_de/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_de/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_de/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_de/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_de/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_de/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_de/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_de/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Habilitado | `payment_gb/checkmo/active` | Todo |
| Título | `payment_gb/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_gb/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_gb/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_gb/checkmo/specificcountry` | Todo |
| Hacer cheque a pagar a | `payment_gb/checkmo/payable_to` | Todo |
| Total de pedido mínimo | `payment_gb/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_gb/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_gb/checkmo/sort_order` | Todo |
| Habilitado | `payment_gb/banktransfer/active` | Todo |
| Título | `payment_gb/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_gb/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_gb/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_gb/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_gb/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_gb/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_gb/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_gb/banktransfer/sort_order` | Todo |
| Habilitado | `payment_gb/cashondelivery/active` | Todo |
| Título | `payment_gb/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_gb/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_gb/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_gb/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_gb/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_gb/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_gb/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_gb/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_gb/free/active` | Todo |
| Título | `payment_gb/free/title` | Todo |
| Estado de nuevo pedido | `payment_gb/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_gb/free/payment_action` | Todo |
| Pago de países aplicables | `payment_gb/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_gb/free/specificcountry` | Todo |
| Orden de clasificación | `payment_gb/free/sort_order` | Todo |
| Habilitado | `payment_gb/purchaseorder/active` | Todo |
| Título | `payment_gb/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_gb/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_gb/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_gb/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_gb/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_gb/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_gb/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_gb/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_gb/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_gb/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_gb/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_gb/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_gb/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_gb/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_gb/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_gb/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_gb/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_gb/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_gb/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_gb/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_gb/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_gb/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_gb/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_gb/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_gb/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_gb/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_gb/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_gb/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_gb/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_gb/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_gb/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_gb/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_gb/worldpay/title` | Solo Commerce Enterprise |
| Secreto MD5 para transacciones | `payment_gb/worldpay/md5_secret` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_gb/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_gb/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_gb/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_gb/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_gb/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_gb/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_gb/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_gb/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_gb/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_gb/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_gb/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_gb/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_gb/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_gb/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_gb/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_gb/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_gb/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_gb/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_gb/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_gb/eway/sort_order` | Solo Commerce Enterprise |
| Recuperación programada | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | Todo |
| Configuración de tarjeta de crédito | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | Todo |
| Rechazar transacción si: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| Recuperación programada | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Todo |
| Activar crédito de PayPal | `payment/wps_express_bml/active` | Todo |
| Recuperación programada | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Todo |
| Configuración de tarjeta de crédito | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | Todo |
| Rechazar transacción si: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Todo |
| Recuperación programada | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Todo |
| Recuperación programada | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Todo |
| Estilo de páginas de comerciante de PayPal | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Todo |
| Habilitado | `payment_us/free/active` | Todo |
| Título | `payment_us/free/title` | Todo |
| Estado de nuevo pedido | `payment_us/free/order_status` | Todo |
| Facturar automáticamente todos los artículos | `payment_us/free/payment_action` | Todo |
| Pago de países aplicables | `payment_us/free/allowspecific` | Todo |
| Pago desde países específicos | `payment_us/free/specificcountry` | Todo |
| Orden de clasificación | `payment_us/free/sort_order` | Todo |
| Habilitado | `payment_us/cashondelivery/active` | Todo |
| Título | `payment_us/cashondelivery/title` | Todo |
| Estado de nuevo pedido | `payment_us/cashondelivery/order_status` | Todo |
| Pago de países aplicables | `payment_us/cashondelivery/allowspecific` | Todo |
| Pago desde países específicos | `payment_us/cashondelivery/specificcountry` | Todo |
| Instrucciones | `payment_us/cashondelivery/instructions` | Todo |
| Total de pedido mínimo | `payment_us/cashondelivery/min_order_total` | Todo |
| Total de pedido máximo | `payment_us/cashondelivery/max_order_total` | Todo |
| Orden de clasificación | `payment_us/cashondelivery/sort_order` | Todo |
| Habilitado | `payment_us/banktransfer/active` | Todo |
| Título | `payment_us/banktransfer/title` | Todo |
| Estado de nuevo pedido | `payment_us/banktransfer/order_status` | Todo |
| Pago de países aplicables | `payment_us/banktransfer/allowspecific` | Todo |
| Pago desde países específicos | `payment_us/banktransfer/specificcountry` | Todo |
| Instrucciones | `payment_us/banktransfer/instructions` | Todo |
| Total de pedido mínimo | `payment_us/banktransfer/min_order_total` | Todo |
| Total de pedido máximo | `payment_us/banktransfer/max_order_total` | Todo |
| Orden de clasificación | `payment_us/banktransfer/sort_order` | Todo |
| Habilitado | `payment_us/checkmo/active` | Todo |
| Título | `payment_us/checkmo/title` | Todo |
| Estado de nuevo pedido | `payment_us/checkmo/order_status` | Todo |
| Pago de países aplicables | `payment_us/checkmo/allowspecific` | Todo |
| Pago desde países específicos | `payment_us/checkmo/specificcountry` | Todo |
| Hacer cheque a pagar a | `payment_us/checkmo/payable_to` | Todo |
| Total de pedido mínimo | `payment_us/checkmo/min_order_total` | Todo |
| Total de pedido máximo | `payment_us/checkmo/max_order_total` | Todo |
| Orden de clasificación | `payment_us/checkmo/sort_order` | Todo |
| Habilitado | `payment_us/purchaseorder/active` | Todo |
| Título | `payment_us/purchaseorder/title` | Todo |
| Estado de nuevo pedido | `payment_us/purchaseorder/order_status` | Todo |
| Pago de países aplicables | `payment_us/purchaseorder/allowspecific` | Todo |
| Pago desde países específicos | `payment_us/purchaseorder/specificcountry` | Todo |
| Total de pedido mínimo | `payment_us/purchaseorder/min_order_total` | Todo |
| Total de pedido máximo | `payment_us/purchaseorder/max_order_total` | Todo |
| Orden de clasificación | `payment_us/purchaseorder/sort_order` | Todo |
| Habilitado | `payment_us/authorizenet_directpost/active` | Todo |
| Acción de pago | `payment_us/authorizenet_directpost/payment_action` | Todo |
| Título | `payment_us/authorizenet_directpost/title` | Todo |
| Estado de nuevo pedido | `payment_us/authorizenet_directpost/order_status` | Todo |
| Divisa aceptada | `payment_us/authorizenet_directpost/currency` | Todo |
| Depurar | `payment_us/authorizenet_directpost/debug` | Todo |
| Tipos de tarjeta de crédito | `payment_us/authorizenet_directpost/cctypes` | Todo |
| Verificación de tarjeta de crédito | `payment_us/authorizenet_directpost/useccv` | Todo |
| Pago de países aplicables | `payment_us/authorizenet_directpost/allowspecific` | Todo |
| Pago desde países específicos | `payment_us/authorizenet_directpost/specificcountry` | Todo |
| Total de pedido mínimo | `payment_us/authorizenet_directpost/min_order_total` | Todo |
| Total de pedido máximo | `payment_us/authorizenet_directpost/max_order_total` | Todo |
| Orden de clasificación | `payment_us/authorizenet_directpost/sort_order` | Todo |
| Habilitado | `payment_us/cybersource/active` | Solo Commerce Enterprise |
| Acción de pago | `payment_us/cybersource/payment_action` | Solo Commerce Enterprise |
| Título | `payment_us/cybersource/title` | Solo Commerce Enterprise |
| Estado de nuevo pedido | `payment_us/cybersource/order_status` | Solo Commerce Enterprise |
| Depurar | `payment_us/cybersource/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_us/cybersource/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_us/cybersource/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_us/cybersource/specificcountry` | Solo Commerce Enterprise |
| Total de pedido mínimo | `payment_us/cybersource/min_order_total` | Solo Commerce Enterprise |
| Total de pedido máximo | `payment_us/cybersource/max_order_total` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_us/cybersource/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_us/worldpay/active` | Solo Commerce Enterprise |
| Título | `payment_us/worldpay/title` | Solo Commerce Enterprise |
| Permitir Editar La Información De Contacto | `payment_us/worldpay/fix_contact` | Solo Commerce Enterprise |
| Ocultar información de contacto | `payment_us/worldpay/hide_contact` | Solo Commerce Enterprise |
| Campos de firma | `payment_us/worldpay/signature_fields` | Solo Commerce Enterprise |
| Depurar | `payment_us/worldpay/debug` | Solo Commerce Enterprise |
| Acción de pago para prueba | `payment_us/worldpay/test_action` | Solo Commerce Enterprise |
| Acción de pago | `payment_us/worldpay/payment_action` | Solo Commerce Enterprise |
| Pago Desde Países Aplicables | `payment_us/worldpay/allowspecific` | Solo Commerce Enterprise |
| Pago De Países Específicos | `payment_us/worldpay/specificcountry` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para CVV | `payment_us/worldpay/cvv_fraud_case` | Solo Commerce Enterprise |
| Definir el estado del pedido como Sospechoso de fraude para el código postal AVS | `payment_us/worldpay/avs_fraud_case` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_us/worldpay/sort_order` | Solo Commerce Enterprise |
| Habilitado | `payment_us/eway/active` | Solo Commerce Enterprise |
| Tipo de conexión | `payment_us/eway/connection_type` | Solo Commerce Enterprise |
| Título | `payment_us/eway/title` | Solo Commerce Enterprise |
| Acción de pago | `payment_us/eway/payment_action` | Solo Commerce Enterprise |
| Depurar | `payment_us/eway/debug` | Solo Commerce Enterprise |
| Tipos de tarjeta de crédito | `payment_us/eway/cctypes` | Solo Commerce Enterprise |
| Pago de países aplicables | `payment_us/eway/allowspecific` | Solo Commerce Enterprise |
| Pago desde países específicos | `payment_us/eway/specificcountry` | Solo Commerce Enterprise |
| Orden de clasificación | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
