---
title: Referencia de rutas de configuración de clientes
description: Consulte una lista de valores de configuración de clientes.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# Referencia de rutas de configuración de clientes

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Clientes**.

La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartido, `app/etc/config.php`, que debería estar en el control de código fuente. Para anular, opcionalmente, cualquier configuración o definir ajustes confidenciales, consulte [Usar variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables). Este tema sí _not_ list [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de newsletter

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Newsletter**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Permitir suscripción de invitado | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Necesidad de confirmar | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de confirmación | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de confirmación | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de éxito | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de éxito | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cancelación de suscripción del remitente de correo electrónico | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Baja de la plantilla de correo electrónico | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de configuración del cliente

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Configuración del cliente**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Intervalo de minutos en línea | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Compartir cuentas de cliente | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la asignación automática para el grupo de clientes | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cálculo de impuestos basado en | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo predeterminado | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA válido - Nacional | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA válido - Intra-Unión | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo para ID de IVA no válido | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grupo de errores de validación | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar en cada transacción | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor predeterminado para desactivar los cambios automáticos de grupo basados en el ID de IVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar número de IVA en tienda | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de bienvenida predeterminado | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de bienvenida predeterminado sin contraseña | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Requerir confirmación de correo electrónico | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico del vínculo de confirmación | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de bienvenida | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar ID de cliente reconocible | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de protección de restablecimiento de contraseña | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de solicitudes de restablecimiento de contraseña | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo mínimo entre solicitudes de restablecimiento de contraseña | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico olvidada | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recordar plantilla de correo electrónico | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Restaurar plantilla de contraseña | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico de plantilla de contraseña | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad del vínculo de recuperación (horas) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Autocompletar en formularios de inicio de sesión/contraseña olvidada | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de clases de caracteres requeridas | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de errores de inicio de sesión en la cuenta de bloqueo | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Longitud mínima de la contraseña | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de bloqueo (minutos) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de líneas de una dirección de calle | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar prefijo | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opciones desplegables de prefijo | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar nombre medio (inicial) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar sufijo | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opciones desplegables de sufijo | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar fecha de nacimiento | `customer/address/dob_show`<br>De acuerdo con las prácticas recomendadas actuales de seguridad y privacidad, asegúrese de conocer cualquier riesgo legal y de seguridad potencial asociado con el almacenamiento de la fecha de nacimiento completa de los clientes (mes, día, año) junto con otros identificadores personales, como el nombre completo, antes de recopilar o procesar dichos datos. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar número de IVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar género | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar funcionalidad de crédito de tienda | `customer/magento_customerbalance/is_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Mostrar el historial de crédito de la tienda a los clientes | `customer/magento_customerbalance/show_history` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Reembolsar crédito de almacén | `customer/magento_customerbalance/refund_automatically` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Store Credit Update Email Sender | `customer/magento_customerbalance/email_identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de actualización de crédito del almacén | `customer/magento_customerbalance/email_template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Redirigir al cliente al panel de cuentas después de iniciar sesión | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Texto de una línea | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar la funcionalidad de segmentos del cliente | `customer/magento_customersegment/is_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar CAPTCHA en tienda | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fuente | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de visualización | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de intentos fallidos de inicio de sesión | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de CAPTCHA (minutos) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de símbolos | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Símbolos utilizados en CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Distinción entre mayúsculas y minúsculas | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de lista de deseos

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Lista de deseos**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitado | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar varias listas de deseos | `wishlist/general/multiple_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Número de listas de deseos múltiples | `wishlist/general/multiple_wishlist_number` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de correos electrónicos permitidos | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Límite de longitud de texto del correo electrónico | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar resumen de listas de deseos | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de invitación

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Invitaciones**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar funcionalidad de invitaciones | `magento_invitation/general/enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar invitaciones en tienda | `magento_invitation/general/enabled_on_front` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Grupo de clientes referido | `magento_invitation/general/registration_use_inviter_group` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Registro de nuevas cuentas | `magento_invitation/general/registration_required_invitation` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Permitir que los clientes añadan mensajes personalizados al correo electrónico de invitación | `magento_invitation/general/allow_customer_message` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Máximo de invitaciones permitidas para enviarse a la vez | `magento_invitation/general/max_invitation_amount_per_send` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico de invitación del cliente | `magento_invitation/email/identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Plantilla de correo electrónico de invitación del cliente | `magento_invitation/email/template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Rutas de puntos de recompensa

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Puntos de rebote**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar la funcionalidad de puntos de devolución | `magento_reward/general/is_enabled` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Habilitar la funcionalidad de puntos de recompensa en tienda | `magento_reward/general/is_enabled_on_front` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Los Clientes Pueden Ver El Historial De Puntos De Recompensa | `magento_reward/general/publish_history` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Umbral de reembolso de saldo de puntos de recompensa | `magento_reward/general/min_points_balance` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Balance de los puntos de devolución del límite | `magento_reward/general/max_points_balance` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Los puntos de devolución caducan en (días) | `magento_reward/general/expiration_days` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Cálculo de caducidad de puntos de recompensa | `magento_reward/general/expiry_calculation` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Devolver puntos de devolución automáticamente | `magento_reward/general/refund_automatically` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Devolución de Puntos de Devolución de Importe de Reembolso Automáticamente | `magento_reward/general/deduct_automatically` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Página de aterrizaje | `magento_reward/general/landing_page` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Compra | `magento_reward/points/order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Registro | `magento_reward/points/register` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Suscripción al boletín | `magento_reward/points/newsletter` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Conversión de la invitación al cliente | `magento_reward/points/invitation_customer` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Límite de cantidad de invitaciones a conversiones de clientes | `magento_reward/points/invitation_customer_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Conversión de invitación a pedido | `magento_reward/points/invitation_order` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Invitación al Límite de Cantidad de Conversiones de Pedidos | `magento_reward/points/invitation_order_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Conversión de invitación a devolución de pedido | `magento_reward/points/invitation_order_frequency` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Revisión de envío | `magento_reward/points/review` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Límite de cantidad de envío de revisiones recompensadas | `magento_reward/points/review_limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Remitente de correo electrónico | `magento_reward/notification/email_sender` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Suscribir clientes de forma predeterminada | `magento_reward/notification/subscribe_by_default` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Correo electrónico de actualización de saldo | `magento_reward/notification/balance_update_template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Correo electrónico de advertencia de caducidad de los puntos de devolución | `magento_reward/notification/expiry_warning_template` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Advertencia de caducidad antes de (días) | `magento_reward/notification/expiry_day_before` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Rutas de promociones

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Promociones**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar los correos electrónicos de recordatorio | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervalo | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuto de la hora | `promo/magento_reminder/minutes` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Hora de inicio | `promo/magento_reminder/time` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Máximo de correos electrónicos por ejecución | `promo/magento_reminder/limit` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Umbral de error de envío de correo electrónico | `promo/magento_reminder/threshold` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Reminder correo electrónico recordatorio | `promo/magento_reminder/identity` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Longitud del código | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato de código | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefijo de código | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sufijo de código | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Guiar cada carácter X | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas de registro de regalo

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Registro de regalos**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Activar el Registro de regalos | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registradores máximos | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Umbral máximo de correos electrónicos enviados | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas persistentes del carro de compras

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Carro de compras persistente**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Habilitar persistencia | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de persistencia (segundos) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar &quot;Recordarme&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valor predeterminado &quot;Recordarme&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Borrar persistencia al cerrar sesión | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar carro de compras | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persist Wish List | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistir elementos pedidos recientemente | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar productos comparados actualmente | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Historial de comparación persistente | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conservar productos vistos recientemente | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistir la pertenencia y segmentación al grupo de clientes | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
