---
title: Configuración manual de bases de datos maestras
description: Consulte las instrucciones sobre la configuración manual de la solución de base de datos dividida.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1379'
ht-degree: 0%

---


# Configuración manual de bases de datos maestras

{{ee-only}}

{{deprecate-split-db}}

Si la aplicación Commerce ya está en producción o si ya ha instalado código o componentes personalizados, es posible que tenga que configurar bases de datos divididas manualmente. Antes de continuar, póngase en contacto con el servicio de asistencia de Adobe Commerce para ver si es necesario en su caso.

La división manual de bases de datos implica:

- Creación de las bases de datos del sistema de gestión de pedidos (OMS) y cierre de compra
- Ejecute una serie de secuencias de comandos SQL que:

   - Borrar claves externas
   - Hacer una copia de seguridad de las tablas de base de datos de presupuestos y ventas
   - Mover tablas de la base de datos principal a las bases de datos de ventas y presupuestos

>[!WARNING]
>
>Si algún código personalizado utiliza JOIN con tablas en las bases de datos de ventas y presupuestos, usted _cannot_ utilice bases de datos divididas. Si tiene alguna duda, póngase en contacto con los autores de cualquier código personalizado o extensión para asegurarse de que su código no utiliza JOIN.

En este tema se utilizan las siguientes convenciones de nomenclatura:

- El nombre de la base de datos principal es `magento` y su nombre de usuario y contraseña son ambos `magento`
- El nombre de la base de datos de presupuesto es `magento_quote` y su nombre de usuario y contraseña son ambos `magento_quote`

   La base de datos de presupuesto también se denomina _cierre de compra_ base de datos.

- El nombre de la base de datos de ventas es `magento_sales` y su nombre de usuario y contraseña son ambos `magento_sales`

   La base de datos de ventas también se denomina base de datos OMS.

>[!INFO]
>
>Esta guía asume que las tres bases de datos están en el mismo host que la aplicación Commerce. Sin embargo, usted puede elegir dónde ubicar las bases de datos y cómo se denominan. Esperamos que nuestros ejemplos hagan que las instrucciones sean más fáciles de seguir.

## Haga una copia de seguridad del sistema de comercio

Adobe recomienda encarecidamente que realice una copia de seguridad de la base de datos y el sistema de archivos actuales para que pueda restaurarla si experimenta problemas durante el proceso.

**Para realizar una copia de seguridad del sistema**:

1. Inicie sesión en el servidor de Commerce como, o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Introduzca los siguientes comandos:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Continúe con la siguiente sección.

## Configuración de bases de datos maestras adicionales

En esta sección se explica cómo crear instancias de base de datos para tablas de venta y presupuesto.

**Para crear bases de datos de presupuestos de ventas y OMS**:

1. Inicie sesión en el servidor de la base de datos como cualquier usuario.
1. Introduzca el siguiente comando para llegar al símbolo del sistema MySQL:

   ```bash
   mysql -u root -p
   ```

1. Introduzca el MySQL `root` contraseña del usuario cuando se le pida.
1. Introduzca los siguientes comandos en el orden mostrado para crear instancias de base de datos con el nombre `magento_quote` y `magento_sales` con los mismos nombres de usuario y contraseñas:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Entrar `exit` para salir del símbolo del sistema.

1. Compruebe las bases de datos de una en una:

   base de datos de presupuesto:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Si aparece el monitor MySQL, ha creado la base de datos correctamente. Si aparece un error, repita los comandos anteriores.

1. Continúe con la siguiente sección.

## Configurar la base de datos de ventas

En esta sección se explica cómo crear y ejecutar secuencias de comandos SQL que alteren tablas de base de datos de comillas y realizar copias de seguridad de los datos de dichas tablas.

Los nombres de tabla de la base de datos de ventas empiezan por:

- `salesrule_`
- `sales_`
- `magento_sales_`
- La variable `magento_customercustomattributes_sales_flat_order` también se ve afectada

>[!INFO]
>
>Esta sección contiene secuencias de comandos con nombres de tabla de base de datos específicos. Si ha realizado personalizaciones o si desea ver una lista completa de las tablas antes de realizar acciones en ellas, consulte [Scripts de referencia](#reference-scripts).

Para obtener más información, consulte:

- [Crear scripts SQL de base de datos de ventas](#create-sales-database-sql-scripts)
- [Realizar copias de seguridad de los datos de ventas](#back-up-sales-data)

### Crear scripts SQL de base de datos de ventas

Cree las siguientes secuencias de comandos SQL en una ubicación a la que el usuario pueda acceder cuando inicie sesión en el servidor de Commerce. Por ejemplo, si inicia sesión o ejecuta comandos como `root`, puede crear las secuencias de comandos en el `/root/sql-scripts` directorio.

#### Eliminar claves externas

Esta secuencia de comandos elimina las claves externas que hacen referencia a tablas que no son de ventas de la base de datos de ventas.

Cree la siguiente secuencia de comandos y asígnele un nombre como `1_foreign-sales.sql`. Reemplazar `<your main DB name>` con el nombre de la base de datos.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### Configurar la base de datos de ventas

Ejecute la secuencia de comandos anterior:

1. Inicie sesión en la base de datos MySQL como `root` o usuario administrativo:

   ```bash
   mysql -u root -p
   ```

1. En el `mysql>` ejecute el script de la siguiente manera:

   ```shell
   source <path>/<script>.sql
   ```

   Por ejemplo,

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Después de ejecutar la secuencia de comandos, escriba `exit`.

### Realizar copias de seguridad de los datos de ventas

En esta sección se explica cómo realizar una copia de seguridad de las tablas de ventas de la base de datos principal de Commerce para que pueda restaurarlas en la base de datos de ventas independiente.

Si actualmente se encuentra en la `mysql>` solicitud, introduzca `exit` para volver al shell de comandos.

Ejecute lo siguiente `mysqldump` comandos, uno a la vez, desde el shell de comandos. En cada uno de ellos, sustitúyase lo siguiente:

- `<your database root username>` con el nombre del usuario raíz de la base de datos
- `<your database root user password>` con la contraseña del usuario
- `<your main Commerce DB name>` con el nombre de la base de datos de Commerce
- `<path>` con una ruta del sistema de archivos grabable

#### Script 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Script 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Script 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Script 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Restaurar datos de ventas

Esta secuencia de comandos restaura los datos de ventas de la base de datos de presupuestos.

#### Requisito de NDB

Si está utilizando un [Base de datos de red (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Convertir tablas de InnoDb a tipo NDB en archivos de volcado:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Elimine las filas con una clave FULLTEXT de los volcados porque las tablas NDB no admiten FULLTEXT.

#### Restaurar los datos

Ejecute los siguientes comandos:

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Donde

- `<your sales DB name>` con el nombre de la base de datos de ventas.

   En este tema, el nombre de base de datos de ejemplo es `magento_sales`.

- `<root username>` con su nombre de usuario raíz MySQL
- `<root user password>` con la contraseña del usuario
- Compruebe la ubicación de los archivos de copia de seguridad creados anteriormente (por ejemplo, `/var/sales.sql`)

## Configuración de la base de datos de presupuesto

En esta sección se tratan las tareas necesarias para soltar claves externas de las tablas de la base de datos de ventas y mover tablas a la base de datos de ventas.

>[!INFO]
>
>Esta sección contiene secuencias de comandos con nombres de tabla de base de datos específicos. Si ha realizado personalizaciones o si desea ver una lista completa de las tablas antes de realizar acciones en ellas, consulte [Scripts de referencia](#reference-scripts).

Los nombres de tabla de la base de datos de ofertas comienzan con `quote`. La variable `magento_customercustomattributes_sales_flat_quote` y `magento_customercustomattributes_sales_flat_quote_address` las tablas también se ven afectadas

### Quitar claves externas de las tablas de comillas

Esta secuencia de comandos elimina las claves externas que hacen referencia a tablas que no son de comillas de las tablas de comillas. Reemplazar `<your main Commerce DB name>` con el nombre de la base de datos de Commerce.

Cree la siguiente secuencia de comandos y asígnele un nombre como `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Ejecute el script de la siguiente manera:

1. Inicie sesión en la base de datos MySQL como usuario raíz o administrativo:

   ```bash
   mysql -u root -p
   ```

1. En el `mysql >` ejecute el script de la siguiente manera:
   `source <path>/<script>.sql`

   Por ejemplo,

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Una vez ejecutada la secuencia de comandos, escriba `exit`.

### Copia de seguridad de tablas de cotización

En esta sección se explica cómo realizar una copia de seguridad de las tablas de comillas desde la base de datos principal y restaurarlas en la base de datos de ofertas.

Ejecute el siguiente comando desde un símbolo del sistema:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### Requisito de NDB

Si está utilizando un [Base de datos de red (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Convertir tablas de InnoDb a tipo NDB en archivos de volcado:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Elimine las filas con una clave FULLTEXT de los volcados porque las tablas NDB no admiten FULLTEXT.

### Restaurar tablas a la base de datos de presupuesto

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Borrar tablas de ventas y presupuestos de la base de datos

Esta secuencia de comandos vende y cita tablas de la base de datos de Commerce. Reemplazar `<your main DB name>` con el nombre de la base de datos de Commerce.

Cree la siguiente secuencia de comandos y asígnele un nombre como `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Ejecute el script de la siguiente manera:

1. Inicie sesión en la base de datos MySQL como usuario raíz o administrativo:

   ```bash
   mysql -u root -p
   ```

1. En el `mysql>` ejecute el script de la siguiente manera:

   ```shell
   source <path>/<script>.sql
   ```

   Por ejemplo,

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Una vez ejecutada la secuencia de comandos, escriba `exit`.

## Actualizar la configuración de implementación

El último paso para dividir manualmente las bases de datos es agregar la información de conexión y recursos a la configuración de implementación de Commerce. `env.php`.

Para actualizar la configuración de implementación:

1. Inicie sesión en el servidor de Commerce como, o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Haga una copia de seguridad de la configuración de implementación:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Apertura `<magento_root>/app/etc/env.php` en un editor de texto y actualícelo siguiendo las directrices descritas en las secciones siguientes.

### Actualizar conexiones de base de datos

Busque el bloque que comienza con `'default'` (en `'connection'`) y añada `'checkout'` y `'sales'` secciones. Reemplace los valores de muestra por valores apropiados para su sitio.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Actualizar recursos

Busque el bloque que comienza con `'resource'` y agregue `'checkout'` y `'sales'` de la siguiente manera:

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Scripts de referencia

Esta sección proporciona secuencias de comandos que pueden ejecutarse para imprimir una lista completa de las tablas afectadas sin realizar ninguna acción en ellas. Puede utilizarlas para ver qué tablas se ven afectadas antes de dividir manualmente las bases de datos, lo que puede resultar útil si utiliza extensiones que personalizan el esquema de la base de datos.

Para utilizar estas secuencias de comandos:

1. Cree una secuencia de comandos SQL con el contenido de cada secuencia de comandos en esta sección.
1. En cada script, reemplace `<your main DB name>` con el nombre de la base de datos de Commerce.

   En este tema, el nombre de base de datos de ejemplo es `magento`.

1. Ejecute cada script desde la `mysql>` solicite como `source <script name>`
1. Examine la salida.
1. Copie el resultado de cada secuencia de comandos en otra secuencia de comandos SQL, eliminando los caracteres de barra vertical (`|`).
1. Ejecute cada script desde la `mysql>` solicite como `source <script name>`.

   La ejecución de esta segunda secuencia de comandos realiza las acciones en la base de datos principal de Commerce.

### Eliminar claves externas (tablas de ventas)

Esta secuencia de comandos elimina las claves externas que hacen referencia a tablas que no son de ventas de la base de datos de ventas.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Eliminar claves externas (tablas de comillas)

Esta secuencia de comandos elimina las claves externas que hacen referencia a tablas que no son de comillas de las tablas de comillas.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Soltar tablas de ventas

Esta secuencia de comandos elimina las tablas de ventas de la base de datos de Commerce.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Soltar tablas de comillas

Suelte todas las tablas que empiecen por `quote_`.
