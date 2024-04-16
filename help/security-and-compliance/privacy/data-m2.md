---
title: Referencia de información personal del cliente (versión 2.x)
description: Obtenga información sobre los diagramas de flujo de datos y las asignaciones de entidades de base de datos para la información personal del cliente en Adobe Commerce 2.x.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Referencia de información personal del cliente (versión 2.x)

>[!NOTE]
>
>Este es uno de una serie de temas para ayudar a los comerciantes y desarrolladores de Adobe Commerce a prepararse para el cumplimiento de las normas de privacidad. Consulte con su asesor legal para determinar si su empresa debe cumplir con alguna obligación legal y cómo debe hacerlo.

Utilice los siguientes diagramas de flujo de datos y asignaciones de entidades de base de datos como referencia al desarrollar programas de cumplimiento de regulaciones de privacidad como:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagramas de flujo de datos

Los diagramas de flujo de datos muestran los tipos de datos que los clientes y administradores pueden introducir y recuperar de la tienda y del administrador.

### Puntos de entrada de datos de front-end

Un usuario puede introducir información sobre el cliente, la dirección y el pago al registrarse en una cuenta, durante el cierre de compra y eventos similares.

![Puntos de entrada de datos de front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Puntos de acceso a datos de front-end

Adobe Commerce carga la información del cliente cuando este inicia sesión y ve varias páginas diferentes o realiza la retirada.

![Puntos de acceso a datos de front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Puntos de entrada de datos back-end

Un comerciante puede introducir información del cliente, datos de dirección y datos de pago al crear un cliente o pedido desde el administrador.

![Puntos de entrada de datos back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Puntos de acceso a datos back-end

Adobe Commerce carga la información del cliente cuando un comerciante ve varios tipos de cuadrículas, hace clic en una cuadrícula para ver información detallada y realiza otras tareas.

![Puntos de acceso a datos back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entidades de base de datos

Adobe Commerce almacena principalmente información específica del cliente en las tablas de clientes, direcciones, pedidos, presupuestos y pagos. Otras tablas contienen referencias al ID de cliente.

### Datos del cliente

Adobe Commerce se puede configurar para almacenar los siguientes atributos del cliente:

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
>De acuerdo con las prácticas recomendadas actuales de seguridad y privacidad, asegúrese de estar al tanto de cualquier posible riesgo legal y de seguridad asociado con el almacenamiento de la fecha de nacimiento completa de los clientes (mes, día, año) junto con otros identificadores personales, como el nombre completo, antes de recopilar o procesar dichos datos.

#### `customer_entity` y referencias de &#39;customer_entity&#39;

Las siguientes columnas de la variable `customer_entity` La tabla contiene información del cliente:

| Columna | Tipo de datos |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | fecha |
| `gender` | smallint(5) |

Estas tablas hacen referencia a `customer_entity` y pueden contener atributos de cliente personalizados:

| Tabla | Columna | Tipo de datos |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | texto |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` tabla

Las siguientes columnas de la variable `customer_grid_flat` La tabla contiene información del cliente:

| Columna | Tipo de datos |
| -------------------- | ------------ |
| `name` | texto |
| `email` | varchar(255) |
| `dob` | fecha |
| `gender` | int(11) |
| `shipping_full` | texto |
| `billing_full` | texto |
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

### Datos de direcciones

Adobe Commerce almacena los siguientes atributos de cliente:

- Ciudad
- Compañía
- País
- Fax
- Nombre
- Apellidos
- Segundo nombre/inicial
- Prefijo de nombre
- Sufijo de nombre
- Número de teléfono
- Estado/Provincia
- ID de estado/provincia
- Dirección física
- Número de IVA
- Código postal

#### `customer_address_entity` y `customer_address_entity` referencias

Las siguientes columnas de la variable `customer_address_entity` La tabla contiene información del cliente:

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
| `street` | texto |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Estas tablas hacen referencia a `customer_address_entity` y pueden contener atributos de cliente personalizados:

| Tabla | Columna | Tipo de datos |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | texto |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Datos del pedido

El `sales_order` y las tablas relacionadas contienen el nombre del cliente, las direcciones de facturación y envío y los datos relacionados.

#### `sales_order` tabla

Las siguientes columnas de la variable `sales_order` La tabla contiene información del cliente:

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

El `sales_order_address` contiene la dirección del cliente.

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

Las siguientes columnas de la variable `sales_order_grid` La tabla contiene información del cliente:

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

### Datos de presupuesto

Las ofertas contienen el nombre, el correo electrónico, la dirección y la información relacionada de un cliente.

#### `quote` tabla

Las siguientes columnas de la variable `quote` La tabla contiene información del cliente:

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

Las siguientes columnas de la variable `quote_address` La tabla contiene información del cliente:

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

El `sales_order_payment` La tabla incluye información de tarjetas de crédito y otra información transaccional.

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
| `additional_information` | texto |

### Datos de invitación

Adobe Commerce se puede configurar para que los clientes puedan enviar invitaciones a eventos y ventas privados.

#### `magento_invitation` tabla

El `magento_invitation` La tabla contiene el ID de cliente, el correo electrónico y el ID de referencia.

| Columna | Tipo de datos |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` tabla

El `magento_invitation_track` La tabla también contiene información del cliente.

| Columna | Tipo de datos |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Varias tablas que hacen referencia a clientes

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
