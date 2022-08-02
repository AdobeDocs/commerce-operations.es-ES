---
title: Rutas confidenciales y específicas del sistema
description: Consulte una lista de valores de configuración sensibles y específicos del sistema.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '3711'
ht-degree: 0%

---


# Ajustes confidenciales y específicos del sistema

En este tema se enumeran las rutas de configuración para las configuraciones específicas y confidenciales del sistema:

- La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe las configuraciones específicas del sistema en el archivo de configuración específico del sistema, `app/etc/env.php`, que debería _not_ estar en control de código fuente. También escribe la configuración compartida para todas las instancias de Commerce en `app/etc/config.php`, este archivo _should_ estar en control de código fuente.
- La variable [`magento config:sensitive:set` command](../cli/set-configuration-values.md) escribe configuraciones sensibles a `app/etc/env.php`.

   También puede establecer valores confidenciales utilizando variables de configuración como se explica en [Usar variables de entorno para anular los ajustes de configuración](../reference/override-config-settings.md#environment-variables).

Para obtener una lista de otras rutas de configuración, consulte:

- [Todas las rutas de configuración excepto pagos](../reference/config-reference-general.md)
- [Rutas de configuración de pago](../reference/config-reference-payment.md).

>[!INFO]
>
>Todas las rutas de configuración enumeradas en este tema son confidenciales. La variable `System-specific?` muestra qué valores son también específicos del sistema.

## Rutas generales sensibles a categorías y específicas del sistema

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **General**.

### Rutas web confidenciales y rutas específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **General** > **Web**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Dirección URL base | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL del vínculo base | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Dirección URL base para archivos de vista estáticos | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL base para archivos multimedia de usuario | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de base segura | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL del vínculo base seguro | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL base segura para archivos de vista estática | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de base segura para archivos multimedia del usuario | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL web predeterminada | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Dirección URL predeterminada sin ruta | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Ruta de la cookie | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Dominio de la cookie | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Duración de la cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Usar solo HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de restricción de cookies | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles a la configuración de divisas y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **General** > **Configuración de moneda**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario de correo electrónico de error | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Almacenar rutas de correo electrónico confidenciales y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración de correo electrónico** > **General** > **Almacenar direcciones de correo electrónico**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nombre del remitente | `trans_email/ident_general/name` |  |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del remitente | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nombre del remitente | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del remitente | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nombre del remitente | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del remitente | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nombre del remitente | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del remitente | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nombre del remitente | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del remitente | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas confidenciales de contactos y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **General** > **Contactos**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar correos electrónicos a | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Remitente de correo electrónico | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Plantilla de correo electrónico | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Nuevas rutas sensibles y específicas del sistema para la creación de informes de reliquia

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **General** > **Nuevos informes de reliquia**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nuevo ID de cuenta de relic | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nuevo ID de aplicación relic | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nueva clave de API relic | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de perspectivas | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nueva URL de API de relicio | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL de la API de perspectivas | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Los clientes pueden utilizar rutas sensibles a categorías y específicas del sistema

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Clientes**.

### Rutas sensibles a la configuración del cliente y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Clientes** > **Configuración del cliente**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## Categoría del catálogo

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo**.

### Rutas confidenciales del catálogo y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Catálogo**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario de correo electrónico de error | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de YouTube | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Solr Server Hostname | `catalog/search/solr_server_hostname` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto del servidor Solr | `catalog/search/solr_server_port` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Solr Server Username | `catalog/search/solr_server_username` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña del servidor Solr | `catalog/search/solr_server_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Ruta del servidor Solr | `catalog/search/solr_server_path` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nombre de host del servidor Elasticsearch | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto del servidor Elasticsearch | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Prefijo de índice del Elasticsearch | `catalog/search/elasticsearch_index_prefix` | !<!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Habilitar autenticación HTTP del Elasticsearch | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Nombre de usuario HTTP del Elasticsearch | `catalog/search/elasticsearch_username` | !<!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña HTTP del Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Tiempo de espera del servidor Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas confidenciales de inventario y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Inventario**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Clave de API de Google | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas específicas del sistema y confidenciales del mapa del sitio XML

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Mapa del sitio XML**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario de correo electrónico de error | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Categoría de ventas

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Ventas**.

### Rutas sensibles a la configuración de envío y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Configuración de envío**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| País | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Región/Estado | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Código postal | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Ciudad | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Línea de dirección 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cuenta en directo | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Correos electrónicos de ventas sensibles y rutas específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Correos electrónicos de ventas**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar copia de correo electrónico del pedido a | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico del comentario del pedido a | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de factura a | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de comentario de factura a | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de envío a | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de comentario de envío a | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de nota de crédito a | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de comentario de nota de crédito a | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico lista para la recogida a | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas confidenciales y específicas del sistema de cierre de compra

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Cierre de compra**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar copia de correo electrónico con error de pago a | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles a la API de Google y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **API de Google**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Id De Contenedor | `google/analytics/container_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Métodos de envío confidenciales y rutas específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Métodos de envío**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de puerta de enlace | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL de Secure Gateway | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Título | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID de usuario | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de usuario | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Número de licencia de acceso | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL XML de seguimiento | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL XML de puerta de enlace | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Número de remitente | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Depuración | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de cuenta | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Número de métrica | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de acceso | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Depuración | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Número de cuenta | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL de puerta de enlace | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de espacio aislado | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles a las ventas y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Ventas**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nombre de contacto | `sales/magento_rma/store_name` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección | `sales/magento_rma/address` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Ciudad | `sales/magento_rma/city` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Estado/provincia | `sales/magento_rma/region_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Código postal | `sales/magento_rma/zip` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| País | `sales/magento_rma/country_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de RMA a | `sales_email/magento_rma/copy_to` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de autorización de RMA a | `sales_email/magento_rma_auth/copy_to` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de comentario RMA a | `sales_email/magento_rma_comment/copy_to` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar copia de correo electrónico de comentario RMA a | `sales_email/magento_rma_customer_comment/copy_to` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas de API de Google

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **API de Google**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Número de cuenta | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Categoría avanzada

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas**.

### Rutas confidenciales para administradores y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas** > **Administrador**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Dirección URL de administración personalizada | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Ruta de administración personalizada | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles al sistema y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas** > **Sistema**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario de correo electrónico de error | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Lista de acceso | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Remitente de correo electrónico de error | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles al desarrollador y específicas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas** > **Desarrollador**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IP permitidas (separadas por coma) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

## Categoría avanzada

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas**.

### Rutas del sistema

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas** > **Sistema**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Host back-end | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto back-end | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas de desarrollador

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Avanzadas** > **Desarrollador**.

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registrar los errores de JS en la clave de almacenamiento de sesión | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

## Rutas sensibles a los pagos y específicas del sistema

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Ventas** > **Pago**.

### Variable general

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| País comerciante | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

>[!INFO]
>
>La elección de esta variable determina cuál [Rutas internacionales](#international-paths) puede usar .

### Rutas sensibles a PayPal y específicas del sistema

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Correo electrónico asociado con la cuenta de comercialización de PayPal (opcional) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de cuenta de comerciante | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del editor | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Inicio de sesión | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nombre de host o dirección IP de extremo personalizado | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de espacio aislado | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuración | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuración | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Credenciales SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Carreteras sensibles y específicas del sistema de PayPal Payflow Pro

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuario | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Ruta personalizada | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Usuario | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Socio | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Host de proxy | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto proxy | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de depuración | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Credenciales SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Configuración de la tarjeta de crédito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles y específicas del sistema de los vínculos de flujo de trabajo de PayPal

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuario | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Usar proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Host de proxy | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Puerto proxy | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuración | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Método de URL para Cancelar URL y Devolver URL | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuración | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Credenciales SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payments Rutas sensibles y específicas del sistema

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nombre de usuario de API | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de API | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Firma de API | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Certificado de API | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Host de proxy | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto proxy | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de espacio aislado | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Credenciales SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### PayPal Payments Pro Hosted rutas sensibles y específicas del sistema

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modo de depuración | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Credenciales SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas sensibles al Braintree y específicas del sistema

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID del comerciante | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave pública | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave privada | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de cuenta de comerciante | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de Kount Merchant | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Sustituir nombre de comerciante | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Teléfono | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas de cheques/pedidos de dinero

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar comprobación a | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}

### Rutas internacionales

| Nombre | Ruta de configuración | ¿Sólo comercio? | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Clave de transacción | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_au/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_au/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_au/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_au/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_au/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_au/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de espacio aislado | `payment_au/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_au/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_au/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_au/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_au/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_au/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_au/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_es/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_es/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_es/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_es/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_es/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_es/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_es/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Depuración | `payment_es/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_es/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_es/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_es/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_es/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_es/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_es/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_es/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_nz/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_nz/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_nz/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_nz/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_nz/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_nz/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_nz/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_nz/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_nz/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Host de proxy | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Puerto proxy | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de depuración | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Método de URL para Cancelar URL y Devolver URL | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_us/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_us/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_us/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_us/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_us/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_us/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_us/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_us/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_us/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_us/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_us/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_gb/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_gb/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_gb/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_gb/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_gb/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_gb/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_gb/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_gb/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_gb/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_de/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_de/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_de/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_de/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de transacción | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de respuesta de pago | `payment_de/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_de/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Depuración | `payment_de/worldpay/debug` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_de/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_de/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_de/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_de/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_de/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_de/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_de/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL de puerta de enlace | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de transacción | `payment_other/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_other/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_other/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nuevo estado de pedido | `payment_other/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_other/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_other/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_other/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_other/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_other/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_other/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_other/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_other/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_other/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_other/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_other/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_ca/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_ca/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_ca/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nuevo estado de pedido | `payment_ca/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| Modo de prueba | `payment_ca/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_ca/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de autorización de administración remota | `payment_ca/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_ca/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_ca/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_ca/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_ca/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_ca/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_ca/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_ca/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_ca/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_hk/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_hk/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_hk/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_hk/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de respuesta de pago | `payment_hk/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_hk/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_hk/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API en directo | `payment_hk/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_hk/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_hk/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_hk/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_hk/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_hk/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_jp/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_jp/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_jp/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nuevo estado de pedido | `payment_jp/cybersource/order_status` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de prueba | `payment_jp/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_jp/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_jp/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_jp/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_jp/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_jp/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_jp/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_jp/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_jp/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_jp/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_jp/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_fr/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_fr/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_fr/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_fr/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_fr/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_fr/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_fr/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_fr/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_fr/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_fr/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_fr/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_fr/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_fr/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_fr/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| URL de puerta de enlace | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Dirección URL de detalles de transacción | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_it/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_it/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_it/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_it/cybersource/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Contraseña de respuesta de pago | `payment_it/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_it/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Modo de prueba | `payment_it/worldpay/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Modo de espacio aislado | `payment_it/eway/sandbox_flag` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) |
| Clave de API en directo | `payment_it/eway/live_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API Live | `payment_it/eway/live_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente activo | `payment_it/eway/live_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API de Sandbox | `payment_it/eway/sandbox_api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de la API de Sandbox | `payment_it/eway/sandbox_api_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de cifrado del lado del cliente de Sandbox | `payment_it/eway/sandbox_encryption_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de API | `fraud_protection/signifyd/api_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| URL de API | `fraud_protection/signifyd/api_url` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  | ![Específico del sistema](/help/assets/configuration/cloud-env.png) | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_au/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_au/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_es/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_es/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_es/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP |
| Credenciales SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | !![Commerce-only]([enc] |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_nz/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_nz/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_nz/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_nz/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_nz/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_nz/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de respuesta de pago | `payment_nz/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_nz/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_nz/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_nz/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_us/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_us/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_us/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_us/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de respuesta de pago | `payment_us/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_us/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_us/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_us/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_gb/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_gb/cybersource/transaction_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_gb/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de acceso | `payment_gb/cybersource/access_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave secreta | `payment_gb/cybersource/secret_key` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Clave de transacción | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_gb/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de respuesta de pago | `payment_gb/worldpay/response_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_gb/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Contraseña de autorización de administración remota | `payment_gb/worldpay/auth_password` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_de/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_de/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_de/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID de instalación de administración remota | `payment_de/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_de/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nuevo estado de pedido | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_other/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_other/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_other/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_other/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_other/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Nuevo estado de pedido | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_ca/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_ca/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_ca/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_ca/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_ca/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_hk/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_hk/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_hk/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_hk/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_hk/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Campos de firma | `payment_hk/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_jp/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_jp/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_jp/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |
| ID de instalación de administración remota | `payment_jp/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_jp/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Campos de firma | `payment_jp/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_fr/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_fr/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_fr/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_fr/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_fr/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Campos de firma | `payment_fr/worldpay/signature_fields` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Credenciales SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Hacer que la comprobación sea pagable a | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Enviar comprobación a | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de inicio de sesión de API | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Comerciante MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Cliente de correo electrónico | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Correo electrónico del comerciante | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID del comerciante | `payment_it/cybersource/merchant_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de perfil | `payment_it/cybersource/profile_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) | ![Cifrado](/help/assets/configuration/cloud-enc.png) |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación | `payment_it/worldpay/installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| ID de instalación de administración remota | `payment_it/worldpay/admin_installation_id` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |
| Secreto MD5 para transacciones | `payment_it/worldpay/md5_secret` | ![Solo comercio](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensible](/help/assets/configuration/cloud-sens.png) |

{style=&quot;table-layout:auto&quot;}
