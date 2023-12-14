---
title: Administrar los indexadores
description: Consulte ejemplos de cómo ver y administrar los indexadores de Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 41082413e24733dde34542a2c9cb3cabbfdd4a35
workflow-type: tm+mt
source-wordcount: '690'
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
> Los comerciantes de Adobe Commerce que utilizan Live Search, el servicio de catálogo o Product Recommendations tienen la opción de usar [Indexación de precios basada en SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Ver estado del indexador

Utilice este comando para ver el estado de todos los indexadores o de indexadores específicos. Por ejemplo, averigüe si es necesario reindexar un indexador.

Opciones de comando:

```bash
bin/magento indexer:status [indexer]
```

Donde `[indexer]` es una lista de indizadores separados por espacios. Omitir `[indexer]` para ver el estado de todos los indexadores.

Resultado de muestra:

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

## Reindexar

Utilice este comando para reindexar todos los indexadores o los seleccionados una sola vez.

>[!INFO]
>
>Este comando reindexa solo una vez. Para mantener los indexadores actualizados, debe configurar un [trabajo cron](../cli/configure-cron-jobs.md).

Opciones de comando:

```bash
bin/magento indexer:reindex [indexer]
```

Donde `[indexer]` es una lista de indizadores separados por espacios. Omitir `[indexer]` para reindexar todos los indexadores.

Resultado de muestra:

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
>La reindexación de todos los indexadores puede llevar mucho tiempo en tiendas con una gran cantidad de productos, clientes, categorías y reglas promocionales.

### Reindexación en modo paralelo

{{php-process-control}}

Los indizadores tienen ámbitos y subprocesos múltiples para admitir la reindexación en modo paralelo. Se paraleliza por la dimensión del indexador y se ejecuta en varios subprocesos, lo que reduce el tiempo de procesamiento.

En este contexto, `dimension` es el ámbito de la reindexación, por ejemplo, una `website` o solo un específico `customer_group`.

La paralelización de índices afecta únicamente a los indexadores con ámbito, lo que significa que Commerce divide los datos en varias tablas utilizando el indexador como ámbito en lugar de mantener todos los datos en una tabla.

Puede ejecutar los siguientes índices en modo paralelo:

- `Catalog Search Fulltext` puede ir paralelo a las vistas de tienda.
- `Category Product` puede ir paralelo a las vistas de tienda.
- `Catalog Price` puede ir paralelo a los grupos de sitios web y clientes.
- `Catalog Permissions` pueden ser paralelos a los grupos de clientes.

>[!INFO]
>
>La paralelización para la búsqueda en el catálogo de texto completo y categoría de producto está habilitada de forma predeterminada.

Para utilizar la paralelización, establezca uno de los modos de dimensión disponibles para el indexador de precios de producto:

- `none` (predeterminado)
- `website`
- `customer_group`
- `website_and_customer_group`

Por ejemplo, para establecer el modo por sitio web:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Para utilizar la paralelización para los permisos de Catálogo, establezca uno de los modos de dimensiones disponibles para el indexador Permisos de catálogo:

- `none` (predeterminado)
- `customer_group`

O para comprobar el modo actual:

```bash
bin/magento indexer:show-dimensions-mode
```

Para reindexar en modo paralelo, ejecute el comando reindex utilizando la variable de entorno `MAGE_INDEXER_THREADS_COUNT`o agregue una variable de entorno a `env.php` archivo. Esta variable establece el número de subprocesos para el procesamiento de reindexación.

Por ejemplo, el siguiente comando ejecuta el `Catalog Search Fulltext` indexador en tres hilos:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Restablecer indizador

Utilice este comando para invalidar el estado de todos los indexadores o de indexadores específicos.

Opciones de comando:

```bash
bin/magento indexer:reset [indexer]
```

Donde ```[indexer]``` es una lista de indizadores separados por espacios. Omitir `[indexer]` para invalidar todos los indexadores.

Resultado de muestra:

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

Utilice este comando para establecer las siguientes opciones del indizador:

- **Actualización al guardar (`realtime`)**: los datos indexados se actualizan cuando se realiza un cambio en el administrador. (Por ejemplo, el índice de productos de la categoría se reindexará después de agregar los productos a una categoría en el Administrador). Esta es la opción predeterminada.
- **Actualización según lo programado (`schedule`)**: Los datos se indexan según la programación establecida por el trabajo cron.

[Más información sobre la indexación](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Mostrar la configuración actual

Para ver la configuración actual del indizador:

```bash
bin/magento indexer:show-mode [indexer]
```

Donde `[indexer]` es una lista de indizadores separados por espacios. Omitir `[indexer]` para mostrar todos los modos de los indexadores. Por ejemplo, para mostrar el modo de todos los indexadores:

Resultado de muestra:

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

### Establecer el modo del indizador

>[!IMPORTANT]
>
>Asegúrese de configurar el [!DNL Customer Grid] con `realtime` en lugar de `schedule`. El [!DNL Customer Grid] solo se puede reindexar con la variable [!UICONTROL Update on Save] opción. Este índice no admite el `Update by Schedule` opción. Utilice la siguiente línea de comandos para configurar este indexador para que se actualice al guardar: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Consulte [Prácticas recomendadas para la configuración del indexador](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) en el _Guía de implementación_.

>[!INFO]
>
>Antes de cambiar a los modos del indizador, establezca el sitio web en [mantenimiento](../../installation/tutorials/maintenance-mode.md) modo y [deshabilitar trabajos de cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Esto garantiza que no sufra bloqueos de base de datos.

Para especificar la configuración del indexador:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Donde:

- `realtime`: permite definir los indexadores seleccionados para que se actualicen al guardar.
- `schedule`: permite definir los indexadores especificados para que se guarden según la programación de cron.
- `indexer`: es una lista de indexadores separados por espacios. Omitir `indexer` para configurar todos los indexadores del mismo modo.

Por ejemplo, para cambiar únicamente los indexadores de productos de categoría y categorías de productos para actualizar según lo programado, introduzca:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Resultado de muestra:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Los déclencheur de base de datos relacionados con los indexadores se agregan cuando el modo de indexador se establece en `schedule` y se quita cuando el modo del indexador está configurado en `realtime`. Si faltan los déclencheur en la base de datos mientras los indexadores están configurados en `schedule`, cambie los indexadores a `realtime` y, a continuación, vuelva a cambiarlos por `schedule`. Esto restablece los déclencheur.
