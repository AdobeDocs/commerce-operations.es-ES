---
title: Referencia de información personal del cliente (versión 2.x)
description: Obtenga información sobre los diagramas de flujo de datos y las asignaciones de entidades de base de datos para la información personal del cliente en Adobe Commerce y Magento Open Source 2.x.
source-git-commit: 2120e5bb912a89c58611ef9e23661a54e40a14f1
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---


# Referencia de información personal del cliente (versión 2.x)

>[!NOTE]
>
>Este es uno de los temas de una serie para ayudar a los comerciantes y desarrolladores de Adobe Commerce y Magento Open Source a prepararse para el cumplimiento de las normas de privacidad. Consulte con su asesor legal para determinar si su empresa debe cumplir con alguna obligación legal y cómo debe hacerlo.

Utilice los siguientes diagramas de flujo de datos y asignaciones de entidades de base de datos como referencia al desarrollar programas de cumplimiento de normas para regulaciones de privacidad como:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagramas de flujo de datos

Los diagramas de flujo de datos muestran los tipos de datos que los clientes y administradores pueden introducir y recuperar desde la tienda y el administrador.

### Puntos de entrada de datos del front-end

Un usuario puede introducir la información de cliente, dirección y pago al registrarse en una cuenta, durante el cierre de compra y eventos similares.

![Puntos de entrada de datos del front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Puntos de acceso a los datos del front-end

Adobe Commerce y el Magento Open Source cargan la información del cliente cuando el cliente inicia sesión y visualiza varias páginas diferentes o cierra la sesión.

![Puntos de acceso a los datos del front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Puntos de entrada de datos del back-end

Un comerciante puede introducir información de clientes, datos de direcciones y datos de pagos al crear un cliente o pedido desde el administrador.

![Puntos de entrada de datos del back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Puntos de acceso de datos back-end

Adobe Commerce y el Magento Open Source cargan la información del cliente cuando un comerciante ve varios tipos de cuadrículas, hace clic en una cuadrícula para ver información detallada y realiza otras tareas.

![Puntos de acceso de datos back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entidades de base de datos

Adobe Commerce y el Magento Open Source almacenan principalmente información específica del cliente en tablas de cliente, dirección, pedido, presupuesto y pago. Otras tablas contienen referencias al ID de cliente.

### Datos del cliente

Adobe Commerce y Magento Open Source se pueden configurar para almacenar los siguientes atributos del cliente:

- Fecha de nacimiento
- Correo electrónico
- Nombre
- Sexo
- Apellidos
- Segundo nombre/inicial
- Prefijo de nombre
- Sufijo de nombre

>[!NOTE]
>
>De acuerdo con las prácticas recomendadas actuales de seguridad y privacidad, asegúrese de conocer cualquier riesgo legal y de seguridad potencial asociado con el almacenamiento de la fecha de nacimiento completa de los clientes (mes, día, año) junto con otros identificadores personales, como el nombre completo, antes de recopilar o procesar dichos datos.

#### `customer_entity` y referencias de &quot;customer_entity&quot;

Las columnas siguientes de la sección `customer_entity` contiene información del cliente:

| Columna | Tipo de datos |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | date |
| `gender` | smallint(5) |

Estas tablas hacen referencia a `customer_entity` y pueden contener atributos de cliente personalizados:

| Tabla | Columna | Tipo de datos |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` tabla

Las columnas siguientes de la sección `customer_grid_flat` contiene información del cliente:

| Columna | Tipo de datos |
| -------------------- | ------------ |
| `name` | text |
| `email` | varchar(255) |
| `dob` | date |
| `gender` | int(11) |
| `shipping_full` | text |
| `billing_full` | text |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### Datos de dirección

Adobe Commerce y Magento Open Source almacenan los siguientes atributos del cliente:

- Ciudad
- Empresa
- País
- Fax
- Nombre
- Apellidos
- Segundo nombre/inicial
- Prefijo de nombre
- Sufijo de nombre
- Número de teléfono
- Estado/provincia
- Estado/ID de provincia
- Dirección
- Número de IVA
- Código postal

#### `customer_address_entity` y `customer_address_entity` referencias

Las columnas siguientes de la sección `customer_address_entity` contiene información del cliente:

| Columna | Tipo de datos |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | text |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Estas tablas hacen referencia a `customer_address_entity` y pueden contener atributos de cliente personalizados:

| Tabla | Columna | Tipo de datos |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Ordenar datos

La variable `sales_order` y las tablas relacionadas contienen el nombre del cliente, las direcciones de facturación y envío y los datos relacionados.

#### `sales_order` tabla

Las columnas siguientes de la sección `sales_order` contiene información del cliente:

| Columna | Tipo de datos |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` tabla

La variable `sales_order_address` contiene la dirección del cliente.

| Columna | Tipo de datos |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` tabla

Las columnas siguientes de la sección `sales_order_grid` contiene información del cliente:

| Columna | Tipo de datos |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Datos de cotización

Las cotizaciones contienen el nombre del cliente, el correo electrónico, la dirección y la información relacionada.

#### `quote` tabla

Las columnas siguientes de la sección `quote` contiene información del cliente:

| Columna | Tipo de datos |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` tabla

Las columnas siguientes de la sección `quote_address` contiene información del cliente:

| Columna | Tipo de datos |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### Datos de pago

La variable `sales_order_payment` incluye información de tarjetas de crédito y otra información transaccional.

| Columna | Tipo de datos |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | text |

### Datos de invitación

Adobe Commerce y Magento Open Source se pueden configurar para que los clientes puedan enviar invitaciones a eventos y ventas privados.

#### `magento_invitation` tabla

La variable `magento_invitation` contiene el ID de cliente, el correo electrónico y el ID de referente.

| Columna | Tipo de datos |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` tabla

La variable `magento_invitation_track` también contiene información del cliente.

| Columna | Tipo de datos |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Tablas diversas que hacen referencia al cliente

Las tablas siguientes contienen un `customer_id` columna:

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
