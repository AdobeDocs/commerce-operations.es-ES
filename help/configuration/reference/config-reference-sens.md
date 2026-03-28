---
title: Rutas confidenciales y específicas del sistema
description: Obtenga información acerca de las rutas de configuración confidenciales y específicas del sistema para Adobe Commerce. Descubra la configuración segura y la administración de variables de entorno.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# Configuración confidencial y específica del sistema

En este tema se enumeran las rutas de configuración para la configuración específica del sistema y confidencial:

- El comando [`magento app:config:dump`](../cli/export-configuration.md) escribe la configuración específica del sistema en el archivo de configuración específico del sistema, `app/etc/env.php`, que debería _no_ estar en el control de código fuente. También escribe la configuración compartida para todas las instancias de Commerce en `app/etc/config.php`; este archivo _debería_ estar en el control de código fuente.
- El comando [`magento config:sensitive:set` ](../cli/set-configuration-values.md) escribe la configuración confidencial en `app/etc/env.php`.

  También puede establecer valores confidenciales usando variables de configuración como se describe en [Usar variables de entorno para invalidar las opciones de configuración](../reference/override-config-settings.md#environment-variables).

Para obtener una lista de otras rutas de configuración, consulte:

- [Todas las rutas de configuración excepto pagos](../reference/config-reference-general.md)
- [Rutas de configuración de pago](../reference/config-reference-payment.md).

>[!INFO]
>
>Todas las rutas de configuración enumeradas en este tema son confidenciales. La columna `System-specific?` muestra qué valores también son específicos del sistema.

## Rutas generales sensibles a categorías y específicas del sistema

En esta sección se enumeran los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **General**.

### Rutas web confidenciales y rutas específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Web**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL básica | `web/unsecure/base_url` |  | | Específico del sistema | |
| URL de vínculo base | `web/unsecure/base_link_url` |  | | Específico del sistema | |
| URL base para archivos de vista estática | `web/unsecure/base_static_url` |  | | Específico del sistema | |
| URL básica para archivos de medios de usuario | `web/unsecure/base_media_url` |  | | Específico del sistema | |
| URL base segura | `web/secure/base_url` |  | | Específico del sistema | |
| URL de vínculo base seguro | `web/secure/base_link_url` |  | | Específico del sistema | |
| URL base segura para archivos de vista estática | `web/secure/base_static_url` |  | | Específico del sistema | |
| URL básica segura para archivos de medios de usuario | `web/secure/base_media_url` |  | | Específico del sistema | |
| URL web predeterminada | `web/default/front` |  | | Específico del sistema | |
| URL predeterminada sin ruta | `web/default/no_route` |  | | Específico del sistema | |
| Ruta de cookie | `web/cookie/cookie_path` |  | | Específico del sistema | |
| Dominio de cookie | `web/cookie/cookie_domain` |  | | Específico del sistema | |
| Duración de cookie | `web/cookie/cookie_lifetime` |  | | Específico del sistema | |
| Usar solo HTTP | `web/cookie/cookie_httponly` |  | | Específico del sistema | |
| Modo de restricción de cookies | `web/cookie/cookie_restriction` |  | | Específico del sistema | |

{style="table-layout:auto"}

### Rutas sensibles a la configuración de moneda y específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Configuración de moneda**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
| --- | --- | --- | --- | --- | --- |
| Error de destinatario de correo electrónico | `currency/import/error_email` |  | | | Sensible |

{style="table-layout:auto"}

### Almacenar rutas confidenciales y específicas del sistema de direcciones de correo electrónico

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración de correo electrónico** > **General** > **Almacenar direcciones de correo electrónico**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nombre del remitente | `trans_email/ident_general/name` | | | | Sensible |
| Correo electrónico del remitente | `trans_email/ident_general/email` |  | | | Sensible |
| Nombre del remitente | `trans_email/ident_sales/name` |  | | | Sensible |
| Correo electrónico del remitente | `trans_email/ident_sales/email` |  | | | Sensible |
| Nombre del remitente | `trans_email/ident_support/name` |  | | | Sensible |
| Correo electrónico del remitente | `trans_email/ident_support/email` |  | | | Sensible |
| Nombre del remitente | `trans_email/ident_custom1/name` |  | | | Sensible |
| Correo electrónico del remitente | `trans_email/ident_custom1/email` |  | | | Sensible |
| Nombre del remitente | `trans_email/ident_custom2/name` |  | | | Sensible |
| Correo electrónico del remitente | `trans_email/ident_custom2/email` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas de contacto confidenciales y específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **General** > **Contactos**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Envío de correos electrónicos a | `contact/email/recipient_email` |  | | | Sensible |
| Remitente de correo electrónico | `contact/email/sender_email_identity` |  | | | Sensible |
| Plantilla de correo electrónico | `contact/email/email_template` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas de informes confidenciales y específicas del sistema de New Relic

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **General** > **Informes de New Relic**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID de cuenta de New Relic | `newrelicreporting/general/account_id` |  | | | Sensible |
| ID de aplicación de New Relic | `newrelicreporting/general/app_id` |  | | | Sensible |
| Clave de API de New Relic | `newrelicreporting/general/api` |  | Cifrado | | Sensible |
| Clave API de Insights | `newrelicreporting/general/insights_insert_key` |  | Cifrado | | Sensible |
| URL de API de New Relic | `newrelicreporting/general/api_url` |  | | Específico del sistema | Sensible |
| URL de API de perspectivas | `newrelicreporting/general/insights_api_url` |  | | Específico del sistema | Sensible |

{style="table-layout:auto"}

## Rutas sensibles a categorías de clientes y específicas del sistema

En esta sección se enumeran los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Clientes**.

### Rutas sensibles a la configuración del cliente y específicas del sistema

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Clientes** > **Configuración del cliente**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Dominio de correo electrónico predeterminado | `customer/create_account/email_domain` |  | | Específico del sistema | |

{style="table-layout:auto"}

## Categoría de catálogo

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Catálogo**.

### Rutas sensibles al catálogo y específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Catálogo**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error de destinatario de correo electrónico | `catalog/productalert_cron/error_email` |  | | | Sensible |
| Clave de API de YouTube | `catalog/product_video/youtube_api_key` |  | | | Sensible |
| Nombre de host del servidor Solr | `catalog/search/solr_server_hostname` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Puerto del servidor Solr | `catalog/search/solr_server_port` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Nombre de usuario del servidor Solr | `catalog/search/solr_server_username` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña del servidor Solr | `catalog/search/solr_server_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Ruta del servidor Solr | `catalog/search/solr_server_path` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Nombre de host del servidor Elasticsearch | `catalog/search/elasticsearch_server_hostname` |  | | Específico del sistema | Sensible |
| Puerto del servidor de Elasticsearch | `catalog/search/elasticsearch_server_port` |  | | Específico del sistema | Sensible |
| Prefijo de índice de Elasticsearch | `catalog/search/elasticsearch_index_prefix` |  | | Específico del sistema | Sensible |
| Habilitar autenticación HTTP de Elasticsearch | `catalog/search/elasticsearch_enable_auth` |  | | Específico del sistema | |
| Nombre de usuario HTTP de Elasticsearch | `catalog/search/elasticsearch_username` |  | | Específico del sistema | |
| Contraseña HTTP de Elasticsearch | `catalog/search/elasticsearch_password` |  | | Específico del sistema | |
| Tiempo de espera del servidor Elasticsearch | `catalog/search/elasticsearch_server_timeout` |  | | Específico del sistema | |
| Nombre de usuario HTTP de Elasticsearch | `catalog/search/elasticsearch_username` | | | Específico del sistema | |
| Contraseña HTTP de Elasticsearch | `catalog/search/elasticsearch_password` | | | Específico del sistema | |
| Tiempo de espera del servidor Elasticsearch | `catalog/search/elasticsearch_server_timeout` | | | Específico del sistema | |
| Nombre del servidor OpenSearch | `catalog/search/opensearch_server_hostname` | | | Específico del sistema | Sensible |
| Puerto de servidor OpenSearch | `catalog/search/opensearch_server_port` | | | Específico del sistema | Sensible |
| Prefijo de índice de OpenSearch | `catalog/search/opensearch_index_prefix` | | | Específico del sistema | Sensible |
| Habilitar autenticación HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | | | Específico del sistema | |
| Nombre de usuario HTTP OpenSearch | `catalog/search/opensearch_username` | | | Específico del sistema | |
| Contraseña HTTP de OpenSearch | `catalog/search/opensearch_password` | | | Específico del sistema | |
| Tiempo de espera de OpenSearch Server | `catalog/search/opensearch_server_timeout` | | | Específico del sistema | |

{style="table-layout:auto"}

>[!NOTE]
>
>La configuración de OpenSearch se introdujo en Adobe Commerce 2.4.6.

### Rutas sensibles al inventario y específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Inventario**.

| Nombre | Ruta de configuración | Compatibilidad con la versión de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? | |
--------------|--------------|--------------|--------------|--------------|--------------|
| Clave de API de Google | `cataloginventory/source_selection_distance_based_google/api_key` | | Cifrado | | | Sensible |

### Rutas específicas del sistema y confidenciales del mapa del sitio XML

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Mapa del sitio XML**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error de destinatario de correo electrónico | `sitemap/generate/error_email` |  | | | Sensible |

{style="table-layout:auto"}

## Categoría de ventas

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas**.

### Rutas sensibles y específicas del sistema de la configuración de envío

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Configuración de envío**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| País | `shipping/origin/country_id` |  | | | Sensible |
| Región o estado | `shipping/origin/region_id` |  | | | Sensible |
| Código postal | `shipping/origin/postcode` |  | | | Sensible |
| Ciudad | `shipping/origin/city` |  | | | Sensible |
| Dirección física | `shipping/origin/street_line1` |  | | | Sensible |
| Dirección de la calle Línea 2 | `shipping/origin/street_line2` |  | | | Sensible |
| Cuenta activa | `carriers/ups/is_account_live` |  | | Específico del sistema | |

{style="table-layout:auto"}

### Rutas de correo electrónico de ventas confidenciales y específicas del sistema

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Correos electrónicos de ventas**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar copia de pedido por correo electrónico a | `sales_email/order/copy_to` |  | | | Sensible |
| Enviar Comentario De Pedido Por Correo Electrónico A | `sales_email/order_comment/copy_to` |  | | | Sensible |
| Enviar copia de correo electrónico de factura a | `sales_email/invoice/copy_to` |  | | | Sensible |
| Enviar copia de correo electrónico de comentario de factura a | `sales_email/invoice_comment/copy_to` |  | | | Sensible |
| Enviar correo electrónico de envío a | `sales_email/shipment/copy_to` |  | | | Sensible |
| Enviar Comentario De Envío Por Correo Electrónico A | `sales_email/shipment_comment/copy_to` |  | | | Sensible |
| Enviar copia de abono por correo electrónico a | `sales_email/creditmemo/copy_to` |  | | | Sensible |
| Enviar copia de comentario de abono por correo electrónico a | `sales_email/creditmemo_comment/copy_to` |  | | | Sensible |
| Enviar copia de correo electrónico lista para recoger a | `sales_email/temando_pickup/copy_to` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas confidenciales y específicas del sistema de extracción

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **Cierre de compra**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar correo electrónico con error de pago a | `checkout/payment_failed/copy_to` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas específicas del sistema y confidenciales de la API de Google

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **API de Google**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID de contenedor | `google/analytics/container_id` | Solo Commerce Enterprise | | | Sensible |

{style="table-layout:auto"}

### Métodos de envío: rutas confidenciales y específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **Métodos de envío**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de puerta | `carriers/usps/gateway_url` |  | | | Sensible |
| URL de Secure Gateway | `carriers/usps/gateway_secure_url` |  | | | Sensible |
| Título | `carriers/usps/title` |  | | | |
| ID de usuario | `carriers/usps/userid` |  | Cifrado | | Sensible |
| Contraseña | `carriers/usps/password` |  | Cifrado | | Sensible |
| ID de usuario | `carriers/ups/username` |  | Cifrado | | Sensible |
| Contraseña | `carriers/ups/password` |  | Cifrado | | Sensible |
| Número de licencia de acceso | `carriers/ups/access_license_number` |  | Cifrado | | Sensible |
| URL XML de seguimiento | `carriers/ups/tracking_xml_url` |  | | | Sensible |
| URL XML de puerta | `carriers/ups/gateway_xml_url` |  | | | Sensible |
| Número de transportista | `carriers/ups/shipper_number` |  | | | Sensible |
| Depurar | `carriers/ups/debug` |  | | | Sensible |
| ID de cuenta | `carriers/fedex/account` |  | Cifrado | | Sensible |
| Clave | `carriers/fedex/key` |  | Cifrado | | Sensible |
| Número de medidor | `carriers/fedex/meter_number` |  | Cifrado | | Sensible |
| Contraseña | `carriers/fedex/password` |  | Cifrado | | Sensible |
| Access ID | `carriers/dhl/id` |  | Cifrado | | Sensible |
| Contraseña | `carriers/dhl/password` |  | Cifrado | | Sensible |
| Depurar | `carriers/dhl/debug` |  | | | |
| Número de cuenta | `carriers/dhl/account` |  | | | Sensible |
| URL de puerta | `carriers/dhl/gateway_url` |  | | | Sensible |
| Modo de zona protegida | `carriers/fedex/sandbox_mode` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas sensibles a las ventas y específicas del sistema

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Ventas**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nombre de contacto | `sales/magento_rma/store_name` | Solo Commerce Enterprise | | | Sensible |
| Dirección física | `sales/magento_rma/address` | Solo Commerce Enterprise | | | Sensible |
| Dirección física | `sales/magento_rma/address1` |  | | | Sensible |
| Ciudad | `sales/magento_rma/city` | Solo Commerce Enterprise | | | Sensible |
| Estado/Provincia | `sales/magento_rma/region_id` | Solo Commerce Enterprise | | | Sensible |
| Código postal | `sales/magento_rma/zip` | Solo Commerce Enterprise | | | Sensible |
| País | `sales/magento_rma/country_id` | Solo Commerce Enterprise | | | Sensible |
| Enviar copia de correo electrónico de RMA a | `sales_email/magento_rma/copy_to` | Solo Commerce Enterprise | | | Sensible |
| Enviar correo electrónico de autorización de RMA a | `sales_email/magento_rma_auth/copy_to` | Solo Commerce Enterprise | | | Sensible |
| Enviar copia de comentario de RMA por correo electrónico a | `sales_email/magento_rma_comment/copy_to` | Solo Commerce Enterprise | | | Sensible |
| Enviar copia de comentario de RMA por correo electrónico a | `sales_email/magento_rma_customer_comment/copy_to` | Solo Commerce Enterprise | | | Sensible |

{style="table-layout:auto"}

### Rutas de API de Google

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Ventas** > **API de Google**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Número de cuenta | `google/analytics/account` |  | | | Sensible |

{style="table-layout:auto"}

## Categoría avanzada

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Avanzadas**.

### Rutas confidenciales y específicas del sistema para el administrador

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Avanzado** > **Administrador**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL de administración personalizada | `admin/url/custom` |  | | | Sensible |
| Ruta de administración personalizada | `admin/url/custom_path` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas sensibles al sistema y específicas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Avanzado** > **Sistema**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Error de destinatario de correo electrónico | `system/magento_scheduled_import_export_log/error_email` |  | | | Sensible |
| Lista de acceso | `system/full_page_cache/varnish/access_list` |  |  | | Sensible |
| Error de remitente de correo electrónico | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | Sensible |

{style="table-layout:auto"}

### Rutas confidenciales y específicas del sistema para desarrolladores

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Avanzado** > **Desarrollador**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IP permitidas (separadas por comas) | `dev/restrict/allow_ips` |  | | Específico del sistema | Sensible |

{style="table-layout:auto"}

## Categoría avanzada

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Avanzadas**.

### Rutas del sistema

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Avanzado** > **Sistema**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` |  | | Específico del sistema | Sensible |
| Puerto (25) | `system/smtp/port` |  | | Específico del sistema | Sensible |
| Host back-end | `system/full_page_cache/varnish/backend_host` |  | | Específico del sistema | Sensible |
| Puerto back-end | `system/full_page_cache/varnish/backend_port` |  | | Específico del sistema | Sensible |

{style="table-layout:auto"}

### Rutas para desarrolladores

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Avanzado** > **Desarrollador**.

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registrar errores de JS en la clave de almacenamiento de sesión | `dev/js/session_storage_key` | ![No es solo para Commerce](/help/assets/configuration/red-x.png) | | Específico del sistema | |

{style="table-layout:auto"}

## Rutas sensibles al pago y específicas del sistema

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Ventas** > **Pago**.

### Variable general

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? |
|--------------|--------------|--------------|--------------|
| País Comerciante | `paypal/general/merchant_country` |  | Sensible |

{style="table-layout:auto"}

>[!INFO]
>
>La elección de esta variable determina las [rutas internacionales](#international-paths) que puede usar.

### Rutas sensibles y específicas del sistema de PayPal

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Correo electrónico asociado a la cuenta de comerciante de PayPal (opcional) | `paypal/general/business_account` |  | | | Sensible |
| ID de cuenta de comerciante | `payment/paypal_express/merchant_id` |  | | | Sensible |
| Identificador de publicador | `payment/paypal_express_bml/publisher_id` |  | | | Sensible |
| Contraseña | `paypal/fetch_reports/ftp_password` |  | Cifrado | | Sensible |
| Iniciar sesión | `paypal/fetch_reports/ftp_login` |  | Cifrado | | Sensible |
| Nombre de host o dirección IP de extremo personalizado | `paypal/fetch_reports/ftp_ip` |  | | Específico del sistema | Sensible |
| Modo de zona protegida | `paypal/fetch_reports/ftp_sandbox` |  | | Específico del sistema | |
| Modo de depuración | `payment/paypal_express/debug` |  | | Específico del sistema | |
| Modo de depuración | `payment/paypal_billing_agreement/debug` |  | | Específico del sistema | |
| Credenciales de SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### PayPal Payflow Pro rutas sensibles y específicas del sistema

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuario | `payment/payflow_advanced/user` |  | Cifrado | | Sensible |
| Contraseña | `payment/payflow_advanced/pwd` |  | Cifrado | | Sensible |
| Ruta personalizada | `paypal/fetch_reports/ftp_path` |  | | Específico del sistema | Sensible |
| Usuario | `payment/payflowpro/user` |  | Cifrado | | Sensible |
| Contraseña | `payment/payflowpro/pwd` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment/payflowpro/sandbox_flag` |  | | Específico del sistema | |
| Socio | `payment/payflowpro/partner` |  | | | Sensible |
| Host de proxy | `payment/payflowpro/proxy_host` |  | | Específico del sistema | Sensible |
| Puerto de proxy | `payment/payflowpro/proxy_port` |  | | Específico del sistema | Sensible |
| Modo de depuración | `payment/payflowpro/debug` |  | | Específico del sistema | |
| Credenciales de SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | Específico del sistema | |
| Configuración de tarjeta de crédito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | Sensible |

{style="table-layout:auto"}

### PayPal Payflow Rutas sensibles al vínculo y específicas del sistema

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Usuario | `payment/payflow_link/user` |  | Cifrado | | Sensible |
| Contraseña | `payment/payflow_link/pwd` |  | Cifrado | | Sensible |
| Modo de prueba | `payment/payflow_link/sandbox_flag` |  | | Específico del sistema | |
| Usar proxy | `payment/payflow_link/use_proxy` |  | | Específico del sistema | |
| Host de proxy | `payment/payflow_link/proxy_host` |  | | Específico del sistema | |
| Puerto de proxy | `payment/payflow_link/proxy_port` |  |  | Específico del sistema | |
| Modo de depuración | `payment/payflow_link/debug` |  | | Específico del sistema | |
| Método de URL para Cancelar URL y Devolver URL | `payment/payflow_link/url_method` |  | | Específico del sistema | |
| Modo de depuración | `payment/payflow_express/debug` |  | | Específico del sistema | |
| Credenciales de SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### PayPal Payments Pro rutas sensibles y específicas del sistema

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nombre de usuario API | `paypal/wpp/api_username` |  | Cifrado | | Sensible |
| Contraseña de API | `paypal/wpp/api_password` |  | Cifrado | | Sensible |
| Firma de API | `paypal/wpp/api_signature` |  | Cifrado | | Sensible |
| Certificado de API | `paypal/wpp/api_cert` |  | | | Sensible |
| Host de proxy | `paypal/wpp/proxy_host` |  | | Específico del sistema | Sensible |
| Puerto de proxy | `paypal/wpp/proxy_port` |  | | Específico del sistema | Sensible |
| Modo de zona protegida | `paypal/wpp/sandbox_flag` |  | | Específico del sistema | |
| Credenciales de SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### PayPal Payments Pro Rutas sensibles y específicas del sistema alojadas

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modo de depuración | `payment/hosted_pro/debug` |  | | Específico del sistema | |
| Credenciales de SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas sensibles y específicas del sistema de Braintree

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID de comerciante | `payment/braintree/merchant_id` |  | | | Sensible |
| Clave pública | `payment/braintree/public_key` |  | Cifrado | | Sensible |
| Clave privada | `payment/braintree/private_key` |  | Cifrado | | Sensible |
| ID de cuenta de comerciante | `payment/braintree/merchant_account_id` |  | | | Sensible |
| ID de comerciante de Kount | `payment/braintree/kount_id` |  | | | Sensible |
| Omitir nombre de comerciante | `payment/braintree_paypal/merchant_name_override` |  | | | Sensible |
| Teléfono | `payment/braintree/descriptor_phone` |  | | | Sensible |
| URL | `payment/braintree/descriptor_url` |  | | Específico del sistema | |

{style="table-layout:auto"}

### Rutas de cheque / giro postal

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Enviar cheque a | `payment/checkmo/mailing_address` |  | | | Sensible |
| Enviar cheque a | `payment_us/checkmo/mailing_address` |  | | | Sensible |

{style="table-layout:auto"}

### Rutas internacionales

| Nombre | Ruta de configuración | Compatibilidad con versiones de Commerce | ¿Cifrado? | ¿Específico del sistema? | ¿Sensible? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Clave de transacción | `payment_au/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_au/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_au/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_au/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_au/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_au/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_au/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_au/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_au/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_au/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de zona protegida | `payment_au/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_au/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_au/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_au/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_au/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_au/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_au/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_es/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_es/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_es/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_es/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_es/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_es/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_es/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_es/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_es/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_es/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Secreto MD5 para transacciones | `payment_es/worldpay/md5_secret` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Depurar | `payment_es/worldpay/debug` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_es/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_es/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_es/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_es/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_es/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_es/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_es/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_nz/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_nz/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_nz/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Modo de prueba | `payment_nz/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de prueba | `payment_nz/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_nz/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_nz/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_nz/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_nz/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_nz/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Contraseña de API de zona protegida | `payment_nz/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_nz/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment/payflow_advanced/sandbox_flag` |  | | Específico del sistema | |
| Host de proxy | `payment/payflow_advanced/proxy_host` |  | | Específico del sistema | Sensible |
| Puerto de proxy | `payment/payflow_advanced/proxy_port` |  | | Específico del sistema | |
| Modo de depuración | `payment/payflow_advanced/debug` |  | | Específico del sistema | |
| Método de URL para Cancelar URL y Devolver URL | `payment/payflow_advanced/url_method` |  | | Específico del sistema | |
| Modo de prueba | `payment_us/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_us/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_us/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de acceso | `payment_us/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_us/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_us/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de prueba | `payment_us/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_us/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_us/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_us/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_us/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_us/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_us/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_us/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | |
| Modo de prueba | `payment_gb/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de prueba | `payment_gb/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_gb/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Modo de prueba | `payment_gb/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_gb/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_gb/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_gb/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_gb/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_gb/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_gb/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_gb/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_de/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_de/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_de/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_de/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave de transacción | `payment_de/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_de/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_de/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_de/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Contraseña de respuesta de pago | `payment_de/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_de/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Depurar | `payment_de/worldpay/debug` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_de/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_de/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_de/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_de/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_de/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_de/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_de/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_other/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_other/authorizenet_directpost/test` |  | | Específico del sistema | Sensible |
| URL de puerta | `payment_other/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_other/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | |
| Clave de transacción | `payment_other/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_other/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_other/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Estado de nuevo pedido | `payment_other/cybersource/order_status` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de prueba | `payment_other/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_other/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_other/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de prueba | `payment_other/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_other/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_other/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_other/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_other/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_other/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_other/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_other/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_ca/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_ca/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_ca/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_ca/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_ca/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_ca/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Estado de nuevo pedido | `payment_ca/cybersource/order_status` | Solo Commerce Enterprise | | | |
| Modo de prueba | `payment_ca/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_ca/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de autorización de administración remota | `payment_ca/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de prueba | `payment_ca/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_ca/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_ca/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_ca/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_ca/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_ca/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Contraseña de API de zona protegida | `payment_ca/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_ca/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_hk/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_hk/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_hk/authorizenet_directpost/cgi_url` |  | | | Sensible |
| URL de detalles de transacción | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_hk/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_hk/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_hk/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_hk/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de respuesta de pago | `payment_hk/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_hk/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de prueba | `payment_hk/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Clave API activa | `payment_hk/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Contraseña de API activa | `payment_hk/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_hk/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_hk/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_hk/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_hk/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_jp/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_jp/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_jp/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_jp/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_jp/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_jp/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Estado de nuevo pedido | `payment_jp/cybersource/order_status` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de prueba | `payment_jp/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_jp/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_jp/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de prueba | `payment_jp/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_jp/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_jp/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_jp/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_jp/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_jp/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_jp/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_jp/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_fr/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_fr/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_fr/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_fr/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_fr/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_fr/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_fr/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_fr/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_fr/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de prueba | `payment_fr/worldpay/sandbox_flag` | Solo Commerce Enterprise |  | Específico del sistema | |
| Modo de zona protegida | `payment_fr/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_fr/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_fr/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_fr/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_fr/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_fr/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_fr/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de transacción | `payment_it/authorizenet_directpost/trans_key` |  | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_it/authorizenet_directpost/test` |  | | Específico del sistema | |
| URL de puerta | `payment_it/authorizenet_directpost/cgi_url` |  | | Específico del sistema | Sensible |
| URL de detalles de transacción | `payment_it/authorizenet_directpost/cgi_url_td` |  | | Específico del sistema | Sensible |
| Clave de transacción | `payment_it/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de acceso | `payment_it/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave secreta | `payment_it/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Modo de prueba | `payment_it/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Contraseña de respuesta de pago | `payment_it/worldpay/response_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Contraseña de autorización de administración remota | `payment_it/worldpay/auth_password` | Solo Commerce Enterprise | | Específico del sistema | Sensible |
| Modo de prueba | `payment_it/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Modo de zona protegida | `payment_it/eway/sandbox_flag` | Solo Commerce Enterprise | | Específico del sistema | |
| Clave API activa | `payment_it/eway/live_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API activa | `payment_it/eway/live_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado activa del lado del cliente | `payment_it/eway/live_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API de zona protegida | `payment_it/eway/sandbox_api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Contraseña de API de zona protegida | `payment_it/eway/sandbox_api_password` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de cifrado del lado del cliente de zona protegida | `payment_it/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| Clave de API | `fraud_protection/signifyd/api_key` | Solo Commerce Enterprise | Cifrado | Específico del sistema | Sensible |
| URL de API | `fraud_protection/signifyd/api_url` | Solo Commerce Enterprise |  | Específico del sistema | Sensible |
| Credenciales de SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| ID de inicio de sesión API | `payment_au/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_au/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_au/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_au/authorizenet_directpost/merchant_email` |  | | | Sensible |
| Identificador de instalación de administración remota | `payment_au/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_au/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Enviar cheque a | `payment_es/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_es/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_es/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_es/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_es/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_es/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_es/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Identificador de instalación de administración remota | `payment_es/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | | | | | |
| Credenciales de SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| ID de inicio de sesión API | `payment_nz/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_nz/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_nz/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_nz/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_nz/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave de transacción | `payment_nz/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_nz/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave de acceso | `payment_nz/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave secreta | `payment_nz/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_nz/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Contraseña de respuesta de pago | `payment_nz/worldpay/response_password` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_nz/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Contraseña de autorización de administración remota | `payment_nz/worldpay/auth_password` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_nz/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensible |
| ID de inicio de sesión API | `payment_us/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| Clave de transacción | `payment_us/authorizenet_directpost/trans_key` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_us/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_us/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_us/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_us/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave de transacción | `payment_us/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_us/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_us/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Contraseña de respuesta de pago | `payment_us/worldpay/response_password` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_us/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Contraseña de autorización de administración remota | `payment_us/worldpay/auth_password` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_us/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensible |
| Credenciales de SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Enviar cheque a | `payment_gb/checkmo/mailing_address` |  | | | Sensible |
| ID de comerciante | `payment_gb/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave de transacción | `payment_gb/cybersource/transaction_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_gb/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave de acceso | `payment_gb/cybersource/access_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| Clave secreta | `payment_gb/cybersource/secret_key` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de inicio de sesión API | `payment_gb/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| Clave de transacción | `payment_gb/authorizenet_directpost/trans_key` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_gb/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_gb/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | Sensible |
| ID de instalación | `payment_gb/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Contraseña de respuesta de pago | `payment_gb/worldpay/response_password` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_gb/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Contraseña de autorización de administración remota | `payment_gb/worldpay/auth_password` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_de/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_de/checkmo/mailing_address` |  | | | Sensible |
| ID de comerciante | `payment_de/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_de/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de inicio de sesión API | `payment_de/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_de/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_de/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_de/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de instalación | `payment_de/worldpay/installation_id` | Solo Commerce Enterprise | | | |
| Identificador de instalación de administración remota | `payment_de/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_de/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensible |
| Credenciales de SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_other/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_other/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_other/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_other/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Estado de nuevo pedido | `payment_other/authorizenet_directpost/order_status` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_other/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_other/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_other/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_other/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_other/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_other/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_ca/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_ca/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_ca/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_ca/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Estado de nuevo pedido | `payment_ca/authorizenet_directpost/order_status` |  | | | Sensible |
| Cliente de correo electrónico | `payment_ca/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_ca/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_ca/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_ca/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_ca/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_ca/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_ca/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | Sensible |
| Credenciales de SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_hk/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_hk/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_hk/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_hk/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_hk/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_hk/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_hk/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_hk/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_hk/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_hk/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_hk/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Campos de firma | `payment_hk/worldpay/signature_fields` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_jp/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_jp/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_jp/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_jp/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_jp/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_jp/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_jp/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_jp/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_jp/worldpay/installation_id` | Solo Commerce Enterprise | | | |
| Identificador de instalación de administración remota | `payment_jp/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_jp/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Campos de firma | `payment_jp/worldpay/signature_fields` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_fr/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_fr/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_fr/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_fr/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_fr/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_fr/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_fr/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_fr/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_fr/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_fr/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_fr/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |
| Campos de firma | `payment_fr/worldpay/signature_fields` | Solo Commerce Enterprise | | | Sensible |
| Credenciales de SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensible |
| Credenciales de SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensible |
| Hacer cheque a pagar a | `payment_it/checkmo/payable_to` |  | | | Sensible |
| Enviar cheque a | `payment_it/checkmo/mailing_address` |  | | | Sensible |
| ID de inicio de sesión API | `payment_it/authorizenet_directpost/login` |  | Cifrado | | Sensible |
| MD5 de Merchant | `payment_it/authorizenet_directpost/trans_md5` |  | Cifrado | | Sensible |
| Cliente de correo electrónico | `payment_it/authorizenet_directpost/email_customer` |  | | | Sensible |
| Correo electrónico del comerciante | `payment_it/authorizenet_directpost/merchant_email` |  | | | Sensible |
| ID de comerciante | `payment_it/cybersource/merchant_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de perfil | `payment_it/cybersource/profile_id` | Solo Commerce Enterprise | Cifrado | | Sensible |
| ID de instalación | `payment_it/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensible |
| Identificador de instalación de administración remota | `payment_it/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensible |
| Secreto MD5 para transacciones | `payment_it/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensible |

{style="table-layout:auto"}
