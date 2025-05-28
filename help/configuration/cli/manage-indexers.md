---
title: Administrar los indexadores
description: Consulte ejemplos de cómo ver y administrar los indexadores de Commerce.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Administrar los indexadores

{{file-system-owner}}

Para ver una lista de todos los indexadores:

```bash
bin/magento indexer:info
```

La lista se muestra de la siguiente manera:

```
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
>
> Los comerciantes de Adobe Commerce que usan Live Search, Servicio de catálogo o Product Recommendations tienen la opción de usar la [indexación de precios basada en SaaS](https://experienceleague.adobe.com/es/docs/commerce/price-indexer/price-indexing).

## Ver estado del indexador

Utilice este comando para ver el estado de todos los indexadores o de indexadores específicos. Por ejemplo, averigüe si es necesario reindexar un indexador.

Opciones de comando:

```bash
bin/magento indexer:status [indexer]
```

Donde `[indexer]` es una lista de indizadores separados por espacios. Omita `[indexer]` para ver el estado de todos los indizadores.

Resultado de muestra:

```
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
>Este comando reindexa solo una vez. Para mantener los indizadores actualizados, debe configurar un [trabajo cron](../cli/configure-cron-jobs.md).

Opciones de comando:

```bash
bin/magento indexer:reindex [indexer]
```

Donde `[indexer]` es una lista de indizadores separados por espacios. Omita `[indexer]` para reindexar todos los indexadores.

Resultado de muestra:

```
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

En este contexto, `dimension` es el ámbito de la reindexación, por ejemplo `website` o simplemente un `customer_group` específico.

La paralelización de índices afecta únicamente a los indexadores con ámbito, lo que significa que Commerce divide los datos en varias tablas utilizando el indexador como ámbito en lugar de mantener todos los datos en una tabla.

Puede ejecutar los siguientes índices en modo paralelo:

- `Catalog Search Fulltext` se puede comparar con las vistas de tiendas.
- `Category Product` se puede comparar con las vistas de tiendas.
- `Catalog Price` puede estar en paralelo con los grupos de sitios web y clientes.
- `Catalog Permissions` puede estar en paralelo en los grupos de clientes.

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

Para reindexar en modo paralelo, ejecute el comando reindex usando la variable de entorno `MAGE_INDEXER_THREADS_COUNT` o agregue una variable de entorno al archivo `env.php`. Esta variable establece el número de subprocesos para el procesamiento de reindexación.

Por ejemplo, el comando siguiente ejecuta el indizador `Catalog Search Fulltext` en tres subprocesos:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Restablecer indizador

Utilice este comando para invalidar el estado de todos los indexadores o de indexadores específicos.

Opciones de comando:

```bash
bin/magento indexer:reset [indexer]
```

Donde ```[indexer]``` es una lista de indizadores separados por espacios. Omita `[indexer]` para invalidar todos los indizadores.

Resultado de muestra:

```
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

- **Actualización al guardar (`realtime`)**: los datos indizados se actualizan cuando se realiza un cambio en el administrador. (Por ejemplo, el índice de productos de la categoría se reindexará después de agregar los productos a una categoría en el Administrador).
- **Actualización por programación (`schedule`)**: los datos se indizan según la programación establecida por el trabajo cron.

[Más información sobre la indexación](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Mostrar la configuración actual

Para ver la configuración actual del indizador:

```bash
bin/magento indexer:show-mode [indexer]
```

Donde `[indexer]` es una lista de indizadores separados por espacios. Omita `[indexer]` para mostrar todos los modos de los indizadores. Por ejemplo, para mostrar el modo de todos los indexadores:

Resultado de muestra:

```
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
>Asegúrese de establecer [!DNL Customer Grid] con `realtime` en lugar de `schedule`. [!DNL Customer Grid] solo se puede reindexar usando la opción [!UICONTROL Update on Save]. Este índice no admite la opción `Update by Schedule`. Utilice la siguiente línea de comandos para establecer este indizador para que se actualice al guardar: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Consulte las [Prácticas recomendadas para la configuración del indizador](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html?lang=es) en el _Manual de implementación_.

>[!INFO]
>
>Antes de cambiar los modos del indizador, establezca su sitio web en el modo [mantenimiento](../../installation/tutorials/maintenance-mode.md) y [deshabilite los trabajos cron](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=es#disable-cron-jobs). Esto garantiza que no sufra bloqueos de base de datos.

Para especificar la configuración del indexador:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Donde:

- `realtime`: define los indexadores seleccionados para que se actualicen al guardar.
- `schedule`: establece los indizadores especificados para que se guarden según la programación de cron.
- `indexer`: es una lista de indizadores separados por espacios. Omita `indexer` para configurar todos los indizadores de la misma manera.

Por ejemplo, para cambiar únicamente los indexadores de productos de categoría y categorías de productos para actualizar según lo programado, introduzca:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Resultado de muestra:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

Los déclencheur de base de datos relacionados con los indizadores se agregan cuando el modo de indizador se establece en `schedule` y se quitan cuando el modo de indizador se establece en `realtime`. Si faltan los déclencheur en la base de datos mientras los indizadores están establecidos en `schedule`, cambie los indizadores a `realtime` y vuelva a cambiarlos a `schedule`. Esto restablece los déclencheur.

### Establecer estado del indizador

El comando `bin/magento indexer:set-status` se introdujo en Adobe Commerce 2.4.7. Permite a los administradores modificar el estado operativo de uno o más indexadores, optimizando el rendimiento del sistema durante operaciones extensas como importaciones de datos, actualizaciones o mantenimiento.

Sintaxis del comando:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Donde:

- `invalid`: marca los indizadores como desactualizados y solicita la reindexación en la siguiente ejecución de cron a menos que se suspendan.
- `suspended`: detiene temporalmente las actualizaciones automáticas activadas por cron para los indexadores. Este estado se aplica tanto a los modos de tiempo real como a los de programación, lo que garantiza que las actualizaciones automáticas se detengan durante las operaciones intensivas.
- `valid`: indica que los datos del indizador están actualizados y no es necesario volver a indexarlos.
- `indexer`: es una lista de indizadores separados por espacios. Omita `indexer` para configurar todos los indizadores de la misma manera.

Por ejemplo, para suspender indexadores específicos, introduzca:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Resultado de muestra:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Administración del estado del indexador suspendido

Cuando un indizador se establece en un estado `suspended`, afecta principalmente a la reindexación automática y a las actualizaciones de la vista materializada. A continuación se muestra una breve descripción general:

**Se ha omitido la reindexación**: la reindexación automática se ha omitido para los indexadores `suspended` y cualquier indexador que comparta el mismo `shared_index`. Esto garantiza que los recursos del sistema se conserven al no reindexar los datos relacionados con los procesos suspendidos.

**Actualizaciones de vista materializada omitidas**: de forma similar a la reindexación, las actualizaciones de vistas materializadas relacionadas con indexadores `suspended` o sus índices compartidos también se pausan. Esta acción reduce aún más la carga del sistema durante los períodos de suspensión.

>[!INFO]
>
>El comando `indexer:reindex` vuelve a indexar todos los indexadores, incluidos los marcados como `suspended`, lo que hace que sea útil para las actualizaciones manuales cuando se pausan las automáticas.

>[!IMPORTANT]
>
>Cambiar el estado de un indizador a `valid` de `suspended` o `invalid` requiere precaución. Esta acción puede provocar una degradación del rendimiento si se acumulan datos sin indexar.
>
>Es crucial asegurarse de que todos los datos estén indexados con precisión antes de actualizar manualmente el estado a `valid` para mantener el rendimiento del sistema y la integridad de los datos.
