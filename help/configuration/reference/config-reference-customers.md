---
title: Referencia de rutas de configuración de clientes
description: Consulte una lista de valores de configuración de clientes.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Referencia de rutas de configuración de clientes

En esta sección se enumeran los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Clientes**.

El comando [`magento app:config:dump` ](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente. Para anular opcionalmente las opciones de configuración o establecer opciones confidenciales, vea [Usar variables de entorno para anular las opciones de configuración](override-config-settings.md#environment-variables). Este tema _no_ enumera [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de newsletter

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Clientes** > **Boletín**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Permitir suscripción de invitado | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Necesita confirmar | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de confirmación | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de confirmación | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico correcto | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de éxito | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de baja | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de baja | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de configuración del cliente

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Clientes** > **Configuración del cliente**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Intervalo de minutos en línea | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartir cuentas de cliente | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la asignación automática al grupo de clientes | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo De Impuestos Basado En | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo predeterminado | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo por ID de IVA válido - Nacional | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA válido - Dentro de la Unión | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Agrupar por ID de IVA no válido | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo de errores de validación | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar en cada transacción | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor predeterminado para Deshabilitar cambios automáticos de grupo según el identificador de IVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar número de IVA en tienda | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de bienvenida predeterminado | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de bienvenida predeterminado sin contraseña | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Requerir confirmación de correos electrónicos | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de vínculo de confirmación | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de bienvenida | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar ID de cliente descriptivo para humanos | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de protección de restablecimiento de contraseña | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de solicitudes de restablecimiento de contraseña | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo Mínimo Entre Solicitudes De Restablecimiento De Contraseña | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico olvidado | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recordar plantilla de correo electrónico | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla para restablecer contraseña | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de plantilla de contraseña | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad del vínculo de recuperación (horas) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar autocompletar en formularios de inicio de sesión/contraseña olvidada | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de clases de caracteres requeridas | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de errores de inicio de sesión en la cuenta bloqueada | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud mínima de contraseña | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de bloqueo (minutos) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de líneas de una dirección | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar prefijo | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opciones desplegables de prefijo | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar segundo nombre (inicial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar sufijo | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opciones desplegables de sufijo | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar fecha de nacimiento | `customer/address/dob_show`<br>De acuerdo con las prácticas recomendadas actuales de seguridad y privacidad, antes de recopilar o procesar dichos datos, asegúrese de estar al tanto de los posibles riesgos legales y de seguridad asociados con el almacenamiento de la fecha de nacimiento completa de los clientes (mes, día, año) junto con otros identificadores personales, como el nombre completo. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar número de IVA/impuesto | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar género | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar la funcionalidad de crédito de tienda | `customer/magento_customerbalance/is_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostrar historial de crédito de la tienda a los clientes | `customer/magento_customerbalance/show_history` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Reembolso de crédito de tienda automáticamente | `customer/magento_customerbalance/refund_automatically` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Enviar correo electrónico de actualización de crédito de tienda | `customer/magento_customerbalance/email_identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de actualización de crédito de tienda | `customer/magento_customerbalance/email_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Redirigir al cliente al tablero de cuentas después de iniciar sesión | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto Una Línea | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la funcionalidad de segmentos del cliente | `customer/magento_customersegment/is_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar CAPTCHA en tienda | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fuente | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de visualización | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de intentos de inicio de sesión erróneos | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de CAPTCHA (minutos) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de símbolos | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Símbolos utilizados en CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Distinción entre mayúsculas y minúsculas | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de lista de deseos

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Clientes** > **Lista de deseos**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitado | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar varias listas de deseos | `wishlist/general/multiple_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Número de listas de deseos múltiples | `wishlist/general/multiple_wishlist_number` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de correos electrónicos permitidos para enviar | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Límite de longitud de texto de correo electrónico | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar resumen de listas de deseos | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de invitaciones

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Clientes** > **Invitaciones**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitar funcionalidad de invitaciones | `magento_invitation/general/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar invitaciones en tienda | `magento_invitation/general/enabled_on_front` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Grupo de clientes referidos | `magento_invitation/general/registration_use_inviter_group` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Registro de nuevas cuentas | `magento_invitation/general/registration_required_invitation` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Permitir que los clientes agreguen un mensaje personalizado al correo electrónico de invitación | `magento_invitation/general/allow_customer_message` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Número máximo de invitaciones que se pueden enviar a la vez | `magento_invitation/general/max_invitation_amount_per_send` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de invitación de cliente | `magento_invitation/email/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de invitación de cliente | `magento_invitation/email/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas de puntos de recompensa

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Clientes** > **Puntos de recompensa**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitar la funcionalidad de puntos de recompensa | `magento_reward/general/is_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Habilitar la funcionalidad de puntos de recompensa en Storefront | `magento_reward/general/is_enabled_on_front` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Los Clientes Pueden Ver El Historial De Puntos De Recompensa | `magento_reward/general/publish_history` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Puntos de recompensa Umbral de canje de saldo | `magento_reward/general/min_points_balance` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Saldo de puntos de recompensa de límite en | `magento_reward/general/max_points_balance` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Los puntos de recompensa caducan en (días) | `magento_reward/general/expiration_days` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Cálculo de caducidad de puntos de recompensa | `magento_reward/general/expiry_calculation` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Reembolso automático de puntos de recompensa | `magento_reward/general/refund_automatically` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Deducir puntos de recompensa del importe de reembolso automáticamente | `magento_reward/general/deduct_automatically` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Página de aterrizaje | `magento_reward/general/landing_page` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Comprar | `magento_reward/points/order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Registro | `magento_reward/points/register` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Suscripción a newsletter | `magento_reward/points/newsletter` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Convertir invitación en cliente | `magento_reward/points/invitation_customer` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Límite de cantidad de invitaciones a conversiones de clientes | `magento_reward/points/invitation_customer_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Convirtiendo invitación en pedido | `magento_reward/points/invitation_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Límite de cantidad de invitaciones a conversiones de pedidos | `magento_reward/points/invitation_order_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Conversión de invitación a recompensa por pedido | `magento_reward/points/invitation_order_frequency` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Revisar envío | `magento_reward/points/review` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Límite de cantidad de envío de críticas recompensadas | `magento_reward/points/review_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico | `magento_reward/notification/email_sender` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Suscribir clientes de forma predeterminada | `magento_reward/notification/subscribe_by_default` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Correo electrónico de actualización de saldo | `magento_reward/notification/balance_update_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mensaje de advertencia de caducidad de puntos de recompensa | `magento_reward/notification/expiry_warning_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Advertencia de caducidad antes (días) | `magento_reward/notification/expiry_day_before` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Rutas de promociones

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Clientes** > **Promociones**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Activar correos electrónicos de recordatorio | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuto de la hora | `promo/magento_reminder/minutes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Hora de inicio | `promo/magento_reminder/time` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Máximo de correos electrónicos por ejecución | `promo/magento_reminder/limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Umbral de error de envío de correo electrónico | `promo/magento_reminder/threshold` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de recordatorio | `promo/magento_reminder/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Longitud de código | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de código | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefijo de código | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de código | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Guión cada X caracteres | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas del registro de regalos

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Clientes** > **Registro de regalos**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Activar Registro de regalos | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de inscritos | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral máximo de correos electrónicos enviados | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de carro de compras persistentes

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Clientes** > **Carro de compras persistente**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Habilitar persistencia | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de la persistencia (segundos) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar &quot;Recordar mis datos&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor predeterminado &quot;Recordarme&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Borrar persistencia al cerrar la sesión | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Continuar carro de compras | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar lista de deseos | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar artículos pedidos recientemente | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar productos comparados actualmente | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar historial de comparación | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar productos vistos recientemente | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar la pertenencia y segmentación a grupos de clientes | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
