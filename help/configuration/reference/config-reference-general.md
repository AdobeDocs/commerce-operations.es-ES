---
title: Referencia de rutas de configuración generales
description: Consulte una lista de valores de configuración generales y avanzados.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 0%

---

# Referencia de rutas de configuración generales y avanzadas

En este tema se enumeran las rutas de configuración generales y avanzadas y _no_ [valores confidenciales y específicos del sistema](config-reference-sens.md). El [`magento app:config:dump` mando](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente.

Para anular cualquier configuración de configuración o definir configuraciones confidenciales, consulte [Utilice variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables).

## Categoría general

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de la sección Administración de **Tiendas** > Configuración > **Configuración** > **General**.

### Rutas generales

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > General > **General**.

| Nombre | Ruta de configuración | ¿Solo comercio? | ¿Sensible? |
|--------------|--------------|--------------|--------------|
| País predeterminado | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Permitir países | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Código postal opcional para | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Países de la Unión Europea | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Principales destinos | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| El estado es obligatorio para | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir la selección del estado si es opcional para el país | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Timezone | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Configuración regional | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Unidad de peso | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Primer día de la semana | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Días del fin de semana | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Restricción de acceso | `general/restriction/is_active` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |  |
| Modo de restricción | `general/restriction/mode` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |  |
| Página de inicio | `general/restriction/http_redirect` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |  |
| Página de aterrizaje | `general/restriction/cms_page` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |  |
| Respuesta HTTP | `general/restriction/http_status` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |  |
| Nombre del almacén | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Número de teléfono de tienda | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Almacenar horas de funcionamiento | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| País | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Región o estado | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Código postal | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Ciudad | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Dirección física | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Dirección de la calle Línea 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Número de IVA | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Habilitar modo de tienda única | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |

{style="table-layout:auto"}

### Rutas web

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Web**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Añadir código de tienda a las direcciones URL | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redireccionamiento automático a URL base | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar reescrituras de servidor web | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar URL seguras en tienda | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar direcciones URL seguras en el administrador | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Actualizar solicitudes no seguras | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Encabezado de descarga | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página de inicio de CMS | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página Sin ruta de CMS | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página Sin Cookies de CMS | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar rutas para páginas de CMS | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar solo HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de restricción de cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar REMOTE_ADDR | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Validar HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar SID en tienda | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Redirigir a la página de CMS si las cookies están desactivadas | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar aviso si JavaScript está deshabilitado | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostrar aviso si el almacenamiento local está deshabilitado | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas de configuración de moneda

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Configuración de moneda**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Moneda base | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Divisa para mostrar predeterminada | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Divisas permitidas | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` |  |
| Fixer.io | `TBD` |  |
| Webservicex | `TBD` |  |
| Tiempo de espera de conexión en segundos | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de conexión en segundos | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de conexión en segundos | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Servicio | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de inicio | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error de destinatario de correo electrónico | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Error de remitente de correo electrónico | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de error | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas de contactos

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Contactos**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Activar Contáctenos | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Envío de correos electrónicos a | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Remitente de correo electrónico | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas de informes

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Informes**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| El Año Hasta La Fecha Comienza | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| El mes actual comienza | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas de administración de contenido

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Gestión de contenido**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Habilitar el editor WYSIWYG | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar direcciones URL estáticas para el contenido de medios en WYSIWYG para el catálogo | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar funcionalidad de jerarquía | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar metadatos de jerarquía | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diseño predeterminado para el menú Jerarquía | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas de informes de New Relic

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Informes de New Relic**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Habilitar la integración con New Relic | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nombre de aplicación New Relic | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar Cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Categoría avanzada

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Admin en **Tiendas** > Configuración > **Configuración** > **Avanzadas**.

### Rutas de administrador

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Avanzadas** > **Administrador**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Plantilla de correo electrónico de contraseña olvidada | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Olvidé y restablezca el remitente del correo electrónico | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de notificación de usuario | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Página de inicio | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usar URL de administración personalizada | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar ruta de administración personalizada | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uso compartido de cuentas de administrador | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de protección de restablecimiento de contraseña | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad del vínculo de recuperación (horas) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número máximo de solicitudes de restablecimiento de contraseña | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo Mínimo Entre Solicitudes De Restablecimiento De Contraseña | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Añadir clave secreta a las direcciones URL | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| El inicio de sesión distingue mayúsculas de minúsculas | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de la sesión de administrador (segundos) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Máximo de errores de inicio de sesión en la cuenta bloqueada | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de bloqueo (minutos) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de la contraseña (días) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cambio de contraseña | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Activar gráficos | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar CAPTCHA en el administrador | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fuente | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de visualización | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de intentos de inicio de sesión erróneos | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de CAPTCHA (minutos) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Número de símbolos | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Símbolos utilizados en CAPTCHA | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Distinción entre mayúsculas y minúsculas | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Acciones habilitadas | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Avanzadas** > **Sistema**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Duración de mensajes correctos | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mensajes De Reintento En Curso Después De | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de mensajes fallidos | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de mensajes nuevos | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar horarios cada | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Programar con anticipación para | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Se pasa por alto si no se ejecuta en | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limpieza de historial cada | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del historial de éxito | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del historial de errores | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar proceso independiente | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar horarios cada | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Programar con anticipación para | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Se pasa por alto si no se ejecuta en | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limpieza de historial cada | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del historial de éxito | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del historial de errores | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Generar horarios cada | `system/cron/staging/schedule_generate_every` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Programar con anticipación para | `system/cron/staging/schedule_ahead_for` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Se pasa por alto si no se ejecuta en | `system/cron/staging/schedule_lifetime` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Limpieza de historial cada | `system/cron/staging/history_cleanup_every` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Duración del historial de éxito | `system/cron/staging/history_success_lifetime` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Duración del historial de errores | `system/cron/staging/history_failure_lifetime` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Utilizar proceso independiente | `system/cron/staging/use_separate_process` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Generar horarios cada | `system/cron/catalog/event/schedule_generate_every` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Programar con anticipación para | `system/cron/catalog/event/schedule_ahead_for` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Se pasa por alto si no se ejecuta en | `system/cron/catalog/event/schedule_lifetime` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Limpieza de historial cada | `system/cron/catalog/event/history_cleanup_every` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Duración del historial de éxito | `system/cron/catalog/event/history_success_lifetime` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Duración del historial de errores | `system/cron/catalog/event/history_failure_lifetime` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Utilizar proceso independiente | `system/cron/catalog/event/use_separate_process` | ![Solo de comercio](/help/assets/configuration/cloud-ee.png) |
| Utilizar proceso independiente | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Desactivar comunicaciones por correo electrónico | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Establecer ruta de retorno | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Correo electrónico de ruta de retorno | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Divisas instaladas | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizar HTTPS para obtener fuente | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia de actualización | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Última actualización | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar copia de seguridad programada | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo de copia | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de inicio | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modo de mantenimiento | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración de entrada de registro, días | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia de archivado de registros | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aplicación de almacenamiento en caché | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL para contenido público | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de gracia | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuración de exportación | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Días guardados en el registro | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Almacenamiento de medios | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seleccionar base de datos de medios | `system/media_storage_configuration/media_database` (obsoleto en Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de actualización del entorno | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Guardar archivos, días | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar limpieza programada del historial de archivos | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hora de inicio | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frecuencia | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plantilla de correo electrónico de error | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Rutas para desarrolladores

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Avanzadas** > **Desarrollador**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Tipo de flujo de trabajo | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir enlaces simbólicos | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimizar Html | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar sugerencias de ruta de plantilla para tienda | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar sugerencias de ruta de plantilla para el administrador | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Agregar nombres de bloque a sugerencias | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registrar en archivo | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Iniciar sesión en syslog | `dev/syslog/syslog_logging` |  |
| Habilitado para tienda | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitado para administradores | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Combinar archivos JavaScript | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Habilitar agrupación de JavaScript | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimizar archivos JavaScript | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Estrategia de traducción | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registrar errores de JS en almacenamiento de sesión | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Combinar archivos CSS | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimizar archivos CSS | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adaptador de imagen | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Firmar archivos estáticos | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indexación asincrónica | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Atributos definidos por el usuario de caché | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
