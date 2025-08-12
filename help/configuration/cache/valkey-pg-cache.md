---
title: Usar Valkey para la caché predeterminada
description: Aprenda a configurar Valkey como la memoria caché predeterminada para Adobe Commerce.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: bc0274074c0254f649af2f9e2b288017ac82ce9b
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 0%

---


# Usar Valkey para la caché predeterminada

Commerce proporciona opciones de línea de comandos para configurar la página de Valkey y el almacenamiento en caché predeterminado. Aunque puede configurar el almacenamiento en caché mediante la edición del archivo `<Commerce-install-dir>app/etc/env.php`, el método recomendado es utilizar la línea de comandos, especialmente para las configuraciones iniciales. La línea de comandos proporciona validación, lo que garantiza que la configuración sea sintácticamente correcta.

Debe [instalar Valkey](config-redis.md#install-redis) antes de continuar.

## Configurar el almacenamiento en caché predeterminado de Valkey

Ejecute el comando `setup:config:set` y especifique los parámetros para el almacenamiento en caché predeterminado de Valkey.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` habilita el almacenamiento en caché predeterminado de valkey. Si esta función ya se ha habilitado, omita este parámetro.

- `--cache-backend-valkey-<parameter>=<value>` es una lista de pares de clave-valor que configuran el almacenamiento en caché predeterminado:

| Parámetro de línea de comandos | Valor | Significado | Valor predeterminado |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Nombre de host completo, dirección IP o ruta absoluta a un socket UNIX. El valor predeterminado de `127.0.0.1` indica que Valkey está instalado en el servidor de Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | puerto | Puerto de escucha del servidor Valkey | `6379` |
| `cache-backend-valkey-db` | database | Necesario si utiliza Valkey tanto para la caché predeterminada como para la caché de página completa. Debe especificar el número de base de datos de una de las cachés; la otra caché utiliza `0` de forma predeterminada.<br><br>**Importante**: Si usa Valkey para más de un tipo de almacenamiento en caché, los números de la base de datos deben ser diferentes. Adobe recomienda que asigne el número de base de datos de almacenamiento en caché predeterminado a `0`, el número de base de datos de almacenamiento en caché de páginas a `1` y el número de base de datos de almacenamiento de sesión a `2`. | `0` |
| `cache-backend-valkey-password` | contraseña | La configuración de una contraseña de Valkey habilita una de sus características de seguridad integradas: el comando `auth`, que requiere que los clientes se autentiquen para acceder a la base de datos. La contraseña está configurada directamente en el archivo de configuración de Valkey: `/etc/valkey/valkey.conf` | |

### Ejemplo, comando

El ejemplo siguiente habilita el almacenamiento en caché predeterminado de Valkey, establece el host en `127.0.0.1` y asigna el número de base de datos a `0`. Valkey utiliza los valores predeterminados de todos los demás parámetros.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

## Configurar almacenamiento en caché de página

Para configurar el almacenamiento en caché de la página Valkey en Commerce, ejecute el comando `setup:config:set` con parámetros adicionales.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Con los siguientes parámetros:

- `--page-cache=valkey` habilita el almacenamiento en caché de páginas Valkey. Si esta función ya se ha habilitado, omita este parámetro.

- `--page-cache-valkey-<parameter>=<value>` es una lista de pares de clave y valor que configuran el almacenamiento en caché de la página:

| Parámetro de línea de comandos | Valor | Significado | Valor predeterminado |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Nombre de host completo, dirección IP o ruta absoluta a un socket UNIX. El valor predeterminado de `127.0.0.1` indica que Valkey está instalado en el servidor de Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | puerto | Puerto de escucha del servidor Valkey. | `6379` |
| `page-cache-valkey-db` | database | Necesario si utiliza Valkey tanto para la caché predeterminada como para la caché de página completa. Debe especificar el número de base de datos de una de las cachés; la otra caché utiliza `0` de forma predeterminada.<br/>**Importante**: Si usa Valkey para más de un tipo de almacenamiento en caché, los números de la base de datos deben ser diferentes. Se recomienda asignar el número de base de datos de almacenamiento en caché predeterminado a `0`, el número de base de datos de almacenamiento en caché de páginas a `1` y el número de base de datos de almacenamiento de sesión a `2`. | `0` |
| `page-cache-valkey-password` | contraseña | La configuración de una contraseña de Valkey habilita una de sus características de seguridad integradas: el comando `auth`, que requiere que los clientes se autentiquen para acceder a la base de datos. Configure la contraseña en el archivo de configuración de Valkey: `/etc/valkey/valkey.conf` | |

### Ejemplo, comando

El ejemplo siguiente habilita el almacenamiento en caché de páginas de Valkey, establece el host en `127.0.0.1` y asigna el número de base de datos a `1`. El resto de parámetros se definen con el valor predeterminado.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

## Resultados

Como resultado de los dos comandos de ejemplo, Commerce agrega líneas similares a las siguientes a `<Commerce-install-dir>app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Nueva implementación de caché de Valkey

[!BADGE 2.4.9-alpha]{type=Negative tooltip="Disponible solo en 2.4.9-alpha."}

A partir de Adobe Commerce 2.4.9, Adobe recomienda utilizar la implementación de caché de Valkey: `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Función de precarga de Valkey

Dado que Commerce almacena los datos de configuración en la memoria caché de Valkey, puede cargar previamente los datos que se reutilizan entre páginas. Para buscar las claves que deben precargarse, analice los datos que se transfieren de Valkey a Commerce. Adobe sugiere precargar los datos que se cargan en todas las páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` y `DB_IS_UP_TO_DATE`.

Valkey usa `pipeline` para crear solicitudes de carga. Las claves deben incluir el prefijo de base de datos; por ejemplo, si el prefijo de base de datos es `061_`, la clave de precarga tiene el siguiente aspecto: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Al utilizar la característica de precarga con una caché L2, debe agregar el sufijo `:hash` a las claves. La caché L2 transfiere únicamente el hash de los datos, no los datos reales.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Generación paralela

A partir de la versión Commerce 2.4.0, Adobe introdujo la opción `allow_parallel_generation` para los usuarios que desean eliminar las esperas de bloqueos.
Está desactivada de forma predeterminada y Adobe recomienda desactivarla hasta que tenga configuraciones o bloques excesivos.

**Para habilitar la generación paralela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Como es un indicador, no puede deshabilitarlo con un comando. Debe establecer manualmente el valor de configuración en `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Verificar la conexión de Valkey

Para comprobar que Valkey y Commerce funcionan juntos correctamente, inicie sesión en el servidor que ejecuta Valkey, abra un terminal y use el comando `valkey-cli monitor` o el comando `redis-cli ping`.

### Comando Valkey monitor

```bash
valkey-cli monitor
```

Ejemplo de salida de almacenamiento en caché de páginas:

```
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Valkey ping, comando

```bash
redis-cli ping
```

La respuesta esperada es: `PONG`

Si ambos comandos se ejecutan correctamente, Valkey se configura correctamente.

### Inspección de datos comprimidos

Para inspeccionar los datos de sesión comprimidos y la memoria caché de la página, [RESP.app](https://flathub.org/apps/app.resp.RESP) admite la descompresión automática de la memoria caché de página y sesión de Commerce 2 y muestra los datos de sesión PHP en un formato legible en lenguaje natural.
