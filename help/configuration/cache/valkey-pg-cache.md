---
title: Configuración de Valkey para la caché predeterminada y de página
description: Aprenda a configurar Valkey como el backend predeterminado y de la caché de página para Adobe Commerce. Descubra los comandos de CLI, la configuración de env.php y la verificación de la conexión.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 1315
ht-degree: 0%

---


# Configuración de Valkey para la caché predeterminada y de página

Commerce proporciona opciones de línea de comandos para configurar el valor predeterminado de Valkey y el almacenamiento en caché de páginas. Aunque puede configurar el almacenamiento en caché mediante la edición del archivo `<Commerce-install-dir>app/etc/env.php`, el método recomendado es utilizar la línea de comandos, especialmente para las configuraciones iniciales. La línea de comandos proporciona validación, lo que garantiza que la configuración sea sintácticamente correcta.

>[!IMPORTANT]
>
>Se requiere Valkey para la configuración de la caché de Adobe Commerce 2.4.9 y las versiones de parches posteriores a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 y 2.4.8-p4. Consulte [Requisitos del sistema](../../installation/system-requirements.md) para ver los servicios de caché admitidos por versión.

{{cloud-cache-config}}

**Requisito previo:**

[Instale Valkey](config-valkey.md#install-valkey) antes de continuar.

## Marcos admitidos

>[!BEGINTABS]

>[!TAB Caché Zend (2.4.8 y anteriores)]

- **Caché Zend (2.4.8 y anteriores)**: servidor Valkey heredado para Commerce 2.4.8 y anteriores:
   - **Servidor Valkey heredado** — Utiliza la ruta de clase completa (`Magento\Framework\Cache\Backend\Valkey`)
   - **Claves de precarga**: admite la precarga de claves de caché utilizadas frecuentemente
   - **Scripts de Lua**: Lua para la recolección de basura
   - **Compresión**: admite la compresión de datos

>[!TAB Caché Symfony (2.4.9+)]

- **Caché Symfony (2.4.9+)**: a partir de Commerce 2.4.9, la caché Symfony proporciona una implementación de caché moderna compatible con PSR-6 para Valkey con mejoras de rendimiento significativas:
   - **Canalización automática de Valkey**: agrupa varias operaciones en solicitudes únicas, lo que reduce la latencia
   - **PSR-6 TagAwareAdapter**: invalidación eficiente de caché basada en etiquetas con operaciones atómicas
   - **Serialización binaria Igbinary**: la serialización binaria reduce el tamaño de entrada de caché en un 45% y mejora la velocidad en un 5-10%
   - **Conexiones persistentes mejoradas**: agrupación de conexiones más estable con mejor manejo de los procesos bifurcados
   - **Scripts Lua optimizados**: ejecución del lado del servidor combinada con canalización para lograr la máxima eficiencia

>[!ENDTABS]

## Configurar el almacenamiento en caché predeterminado de Valkey

Ejecute el comando `setup:config:set` y especifique los parámetros para el almacenamiento en caché predeterminado de Valkey.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` habilita el almacenamiento en caché predeterminado de Valkey. Si esta función ya se ha habilitado, omita este parámetro.

- `--cache-backend-valkey-<parameter>=<value>` es una lista de pares de clave-valor que configuran el almacenamiento en caché predeterminado:

{{valkey-redis-cli-note}}

| Parámetro de línea de comandos | Valor | Significado | Valor predeterminado |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Nombre de host completo, dirección IP o ruta absoluta a un socket UNIX. El valor predeterminado de `127.0.0.1` indica que Valkey está instalado en el servidor de Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | puerto | Puerto de escucha del servidor Valkey | `6379` |
| `cache-backend-valkey-db` | database | Necesario si utiliza Valkey tanto para la caché predeterminada como para la caché de página completa. Especifique el número de base de datos de una de las cachés; la otra caché usa `0` de forma predeterminada.<br><br>**Importante**: Si usa Valkey para más de un tipo de almacenamiento en caché, los números de base de datos deben ser diferentes. Adobe recomienda que asigne el número de base de datos de almacenamiento en caché predeterminado a `0`, el número de base de datos de almacenamiento en caché de páginas a `1` y el número de base de datos de almacenamiento de sesión a `2`. | `0` |
| `cache-backend-valkey-password` | contraseña | La configuración de una contraseña de Valkey habilita una de sus características de seguridad integradas: el comando `auth`, que requiere que los clientes se autentiquen para acceder a la base de datos. La contraseña está configurada directamente en el archivo de configuración de Valkey: `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | Habilitar o deshabilitar LUA. <br><br>**LUA**: Lua nos permite ejecutar parte de la lógica de la aplicación dentro de Valkey, mejorando el rendimiento y asegurando la coherencia de los datos a través de su ejecución atómica. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | Habilite o deshabilite LUA para la recolección de elementos no utilizados. <br><br>**LUA**: Lua nos permite ejecutar parte de la lógica de la aplicación dentro de Valkey, mejorando el rendimiento y asegurando la coherencia de los datos a través de su ejecución atómica. | `1` |

## Comando de ejemplo (caché predeterminada)

El ejemplo siguiente habilita el almacenamiento en caché predeterminado de Valkey, establece el host en `127.0.0.1` y asigna el número de base de datos a `0`. Valkey utiliza los valores predeterminados de todos los demás parámetros.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Configurar el almacenamiento en caché de páginas Valkey

Para configurar el almacenamiento en caché de la página Valkey en Commerce, ejecute el comando `setup:config:set` con parámetros adicionales.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Con los siguientes parámetros:

- `--page-cache=valkey` habilita el almacenamiento en caché de páginas Valkey. Si esta función ya se ha habilitado, omita este parámetro.

- `--page-cache-valkey-<parameter>=<value>` es una lista de pares de clave y valor que configuran el almacenamiento en caché de la página:

| Parámetro de línea de comandos | Valor | Significado | Valor predeterminado |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Nombre de host completo, dirección IP o ruta absoluta a un socket UNIX. El valor predeterminado de `127.0.0.1` indica que Valkey está instalado en el servidor de Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | puerto | Puerto de escucha del servidor Valkey. | `6379` |
| `page-cache-valkey-db` | database | Necesario si utiliza Valkey tanto para la caché predeterminada como para la caché de página completa. Especifique el número de base de datos de una de las cachés; la otra caché usa `0` de forma predeterminada.<br/>**Importante**: Si usa Valkey para más de un tipo de almacenamiento en caché, los números de base de datos deben ser diferentes. Se recomienda asignar el número de base de datos de almacenamiento en caché predeterminado a `0`, el número de base de datos de almacenamiento en caché de páginas a `1` y el número de base de datos de almacenamiento de sesión a `2`. | `0` |
| `page-cache-valkey-password` | contraseña | La configuración de una contraseña de Valkey habilita una de sus características de seguridad integradas: el comando `auth`, que requiere que los clientes se autentiquen para acceder a la base de datos. Configure la contraseña en el archivo de configuración de Valkey: `/etc/valkey/valkey.conf` | |

### Ejemplo, comando (caché de página)

El ejemplo siguiente habilita el almacenamiento en caché de páginas de Valkey, establece el host en `127.0.0.1` y asigna el número de base de datos a `1`. El resto de parámetros se definen con el valor predeterminado.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Revisar la configuración del entorno de Commerce

Al ejecutar los comandos para configurar el almacenamiento en caché de Valkey, se actualiza la configuración del entorno de Commerce (`<Commerce-install-dir>app/etc/env.php`):

>[!BEGINTABS]

>[!TAB Caché Zend (2.4.8 y anteriores)]

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

>[!TAB Caché Symfony (2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>A partir de Commerce 2.4.9, utilice el tipo de backend simplificado `'backend' => 'valkey'` en lugar de la ruta de clase completa. Symfony Cache se utiliza automáticamente cuando se especifica el nombre simplificado.

>[!ENDTABS]

## Configurar opciones de almacenamiento en caché adicionales

### Función de precarga de Valkey

Dado que Commerce almacena los datos de configuración en la memoria caché de Valkey, puede cargar previamente los datos que se reutilizan entre páginas. Para buscar las claves que deben precargarse, analice los datos que se transfieren de Valkey a Commerce. Adobe sugiere precargar los datos que se cargan en todas las páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` y `DB_IS_UP_TO_DATE`.

Valkey usa `pipeline` para crear solicitudes de carga. Las claves deben incluir el prefijo de base de datos; por ejemplo, si el prefijo de base de datos es `061_`, la clave de precarga tiene el siguiente aspecto: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Caché Zend]

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

>[!TAB Caché Symfony]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
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

>[!ENDTABS]

Al utilizar la característica de precarga con una caché L2, debe agregar el sufijo `:hash` a las claves. La caché L2 transfiere únicamente el hash de los datos, no los datos reales.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Generación paralela

A partir de la versión Commerce 2.4.0, Adobe introdujo la opción `allow_parallel_generation` para los usuarios que desean eliminar la espera de bloqueos. Está desactivada de forma predeterminada y Adobe recomienda desactivarla hasta que tenga configuraciones o bloques excesivos.

**Para habilitar la generación paralela**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

Como es un indicador, no puede deshabilitarlo con un comando. Establezca manualmente el valor de configuración en `false`:

>[!BEGINTABS]

>[!TAB Caché Zend]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB Caché Symfony]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Optimización del rendimiento de Symfony Cache

Si utiliza Symfony Cache, puede optimizar aún más el rendimiento configurando el serializador Igbinary, instalando la extensión PHP igbinary y la extensión phpredis, y habilitando conexiones persistentes.

### Serializador igbinario

El serializador Igbinary proporciona mejoras significativas de rendimiento sobre la serialización predeterminada de PHP. Debe configurarse manualmente en `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### Instale la extensión PHP Igbinary

Para utilizar la serialización igbinary, debe instalar la extensión PHP Igbinary.

**Usando apt (recomendado para Debian/Ubuntu)**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**Usando pecl (método alternativo)**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### Extensiones de PHP Redis: phpredis vs Predis

Commerce 2.4.9+ incluye reserva automática entre phpredis (extensión nativa de C) y Predis (biblioteca PHP pura). Para obtener un rendimiento óptimo, instale phpredis:

**Usando apt (recomendado para Debian/Ubuntu)**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Usando pecl (método alternativo)**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Comparación de rendimiento**:

| Operación | Predis | fpredis | Mejora |
|-----------|--------|----------|-------------|
| GET de caché | 1-5 ms | 0,5-2 ms | De 2 a 3 veces más rápido |
| CONJUNTO DE caché | 2 a 6 ms | 0,8-2,5 ms | De 2 a 3 veces más rápido |
| Operaciones de etiqueta | 10-30 ms | 3 a 10 ms | De 3 a 4 veces más rápido |

### Conexiones persistentes

Las conexiones persistentes reutilizan las conexiones existentes de Valkey entre solicitudes, lo que proporciona operaciones de caché un 5-15 % más rápidas. Configurar en `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>Use un `persistent_id` único para cada tipo de caché a fin de evitar conflictos de conexión.

### Configuración optimizada completa

Esta es una configuración lista para la producción que combina todas las optimizaciones de rendimiento:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Verificar la conexión de Valkey

Para comprobar que Valkey y Commerce funcionan juntos correctamente:

1. Inicie sesión en el servidor que ejecuta Valkey y Commerce.
1. Abra un terminal.
1. Compruebe la conexión utilizando el comando `valkey-cli monitor` o el comando `valkey-cli ping`.

Si los comandos se ejecutan correctamente, Valkey se está ejecutando y puede comunicarse con la aplicación de Commerce. Si fallan, entonces hay un problema de conexión entre Valkey y Commerce que debe resolver.

### Comando Valkey monitor

```shell
valkey-cli monitor
```

Ejemplo de salida de almacenamiento en caché de páginas:

```text
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

```shell
valkey-cli ping
```

La respuesta esperada es: `PONG`

Si ambos comandos se ejecutan correctamente, Valkey se configura correctamente.

### Inspeccionar datos comprimidos

Para inspeccionar los datos de sesión comprimidos y la caché de página, use la herramienta [RESP.app](https://flathub.org/apps/app.resp.RESP). Admite la descompresión automática de los datos de caché de página y sesión de Commerce 2 y muestra los datos de sesión de PHP en un formato legible en lenguaje natural.

