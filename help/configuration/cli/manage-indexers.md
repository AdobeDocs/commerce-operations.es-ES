---
title: Administrar los indexadores
description: Consulte ejemplos de cómo ver y administrar los indexadores de comercio.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: beee479caeb4145d759c105012ffc8b6b55a6e39
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Administrar los indexadores

{{file-system-owner}}

Para ver una lista de todos los indexadores:

```bash
bin/magento indexer:info
```

La lista se muestra de la siguiente manera:

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

>[!NOTE]
> Los comerciantes de Adobe Commerce que utilizan Live Search, Catalog Service o Product Recommendations tienen la opción de usar [Indexación de precios basada en SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-index/index.html).

## Ver estado del indexador

Utilice este comando para ver el estado de todos los indexadores o indexadores específicos. Por ejemplo, averigüe si es necesario reindexar un indizador.

Opciones de comando:

```bash
bin/magento indexer:status [indexer]
```

Donde `[indexer]` es una lista de indexadores separados por espacios. Omitir `[indexer]` para ver el estado de todos los indexadores.

Resultado de la muestra:

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Reindex

Utilice este comando para reindexar todos los indexadores o los seleccionados una sola vez.

>[!INFO]
>
>Este comando se reindexa una sola vez. Para mantener los indexadores actualizados, debe configurar un [trabajo cron](../cli/configure-cron-jobs.md).

Opciones de comando:

```bash
bin/magento indexer:reindex [indexer]
```

Donde `[indexer]` es una lista de indexadores separados por espacios. Omitir `[indexer]` para reindexar todos los indexadores.

Resultado de la muestra:

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>La reindexación de todos los indexadores puede llevar mucho tiempo para las tiendas con un gran número de productos, clientes, categorías y reglas promocionales.

### Reindexación en modo paralelo

Los indexadores tienen ámbitos y subprocesos múltiples para admitir la reindexación en modo paralelo. Se paraleliza por la dimensión del indizador y se ejecuta en varios subprocesos, lo que reduce el tiempo de procesamiento.

En este contexto, `dimension` es el ámbito de la reindexación, por ejemplo, un `website` o solo un `customer_group`.

La paralelización de índices solo afecta a los indexadores de ámbitos, lo que significa que Commerce divide los datos en varias tablas usando el indexador como su ámbito en lugar de mantener todos los datos en una tabla.

Puede ejecutar los siguientes índices en modo paralelo:

- `Catalog Search Fulltext` se puede comparar con las vistas de la tienda.
- `Category Product` se puede comparar con las vistas de la tienda.
- `Catalog Price` se puede comparar con grupos de clientes y sitios web.
- `Catalog Permissions` pueden ser paralelos a grupos de clientes.

>[!INFO]
>
>La paralelización para la búsqueda en catálogo El texto completo y el producto de categoría están habilitados de forma predeterminada.

Para utilizar la paralelización, establezca uno de los modos de dimensiones disponibles para el indizador de precios del producto:

- `none` (predeterminado)
- `website`
- `customer_group`
- `website_and_customer_group`

Por ejemplo, para configurar el modo por sitio web:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Para utilizar la paralelización para los permisos de Catálogo, establezca uno de los modos de dimensiones disponibles para el indexador Permisos de Catálogo:

- `none` (predeterminado)
- `customer_group`

O para comprobar el modo actual:

```bash
bin/magento indexer:show-dimensions-mode
```

Para reindexar en modo paralelo, ejecute el comando reindex utilizando la variable de entorno `MAGE_INDEXER_THREADS_COUNT`o agregar una variable de entorno al `env.php` archivo. Esta variable establece el número de subprocesos para el procesamiento del reíndice.

Por ejemplo, el siguiente comando ejecuta el `Catalog Search Fulltext` indexador en tres subprocesos:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Restablecer indexador

Utilice este comando para invalidar el estado de todos los indexadores o indexadores específicos.

Opciones de comando:

```bash
bin/magento indexer:reset [indexer]
```

Donde ```[indexer]``` es una lista de indexadores separados por espacios. Omitir `[indexer]` para invalidar todos los indexadores.

Resultado de la muestra:

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Configuración de indexadores

Utilice este comando para establecer las siguientes opciones de indexador:

- **Actualizar al guardar (`realtime`)**: Los datos indexados se actualizan cuando se realiza un cambio en Admin. (Por ejemplo, el índice de productos de la categoría se reindexa después de que los productos se agreguen a una categoría en el Administrador). Este es el valor predeterminado.
- **Actualizar por programación (`schedule`)**: Los datos se indexan según la programación establecida por su trabajo cron.

[Más información sobre la indexación](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Mostrar la configuración actual

Para ver la configuración del indexador actual:

```bash
bin/magento indexer:show-mode [indexer]
```

Donde `[indexer]` es una lista de indexadores separados por espacios. Omitir `[indexer]` para mostrar todos los modos de los indexadores. Por ejemplo, para mostrar el modo de todos los indexadores:

Resultado de la muestra:

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### Configuración de indexadores

>[!INFO]
>
>Antes de cambiar de modo de indexador, le recomendamos que coloque el sitio web en [mantenimiento](../../installation/tutorials/maintenance-mode.md) y [desactivar trabajos cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Esto garantiza que no sufra bloqueos de base de datos.

Para especificar la configuración del indizador:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Donde:

- `realtime`: permite configurar los indexadores seleccionados para que se actualicen al guardar.
- `schedule`: permite configurar los indexadores especificados para guardar según la programación cron.
- `indexer`: es una lista de indexadores separados por espacio. Omitir `indexer` para configurar todos los indexadores del mismo modo.

Por ejemplo, para cambiar solo los indexadores de categorías de productos y categorías de productos para actualizarlos según lo programado, introduzca:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Resultado de la muestra:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Los déclencheur de base de datos relacionados con los indexadores se agregan cuando el modo indexador se establece en `schedule` y se elimina cuando el modo indexador está configurado en `realtime`. Si faltan déclencheur en la base de datos mientras los indexadores están establecidos en `schedule`, cambie los indexadores a `realtime` y luego cambie a `schedule`. Esto restablece los déclencheur.
