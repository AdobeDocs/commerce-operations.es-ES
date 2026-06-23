---
title: Configurar Redis para caché de páginas y predeterminados
description: Aprenda a configurar Redis como el backend predeterminado y de la caché de página para Adobe Commerce. Descubra los comandos de CLI, la configuración de env.php y la verificación de la conexión.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
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
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 1485
ht-degree: 0%

---

# Configurar Redis para caché predeterminada y de página

{{cloud-cache-config}}

Commerce proporciona opciones de línea de comandos para configurar la página Redis y el almacenamiento en caché predeterminado. Aunque puede configurar el almacenamiento en caché mediante la edición del archivo `<Commerce-install-dir>app/etc/env.php`, el método recomendado es utilizar la línea de comandos, especialmente para las configuraciones iniciales. La línea de comandos proporciona validación, lo que garantiza que la configuración sea sintácticamente correcta.

**Requisito previo:**

[Instale Redis](config-redis.md#install-redis) antes de continuar.

>[!NOTE]
>
>Para las instancias de Commerce alojadas en EC2, puede utilizar AWS ElastiCache en lugar de una instancia local de Redis. Consulte [Configurar Elasticache para instancias de EC2](redis-elasticache-for-ec2.md).

## Marcos admitidos

>[!BEGINTABS]

>[!TAB Caché Zend (2.4.8 y anteriores)]

- **Caché Zend (2.4.8 y anteriores)**: back-end heredado de Redis para Commerce 2.4.8 y anteriores:
   - **Servidor Redis heredado** — Utiliza la ruta de clase completa (`Magento\Framework\Cache\Backend\Redis`)
   - **Claves de precarga**: admite la precarga de claves de caché utilizadas frecuentemente
   - **Scripts de Lua**: Lua para la recolección de basura
   - **Compresión**: admite la compresión de datos

>[!TAB Caché Symfony (2.4.9+)]

- **Caché Symfony (2.4.9+)**: a partir de Commerce 2.4.9, la caché Symfony proporciona una implementación de caché moderna compatible con PSR-6 para Redis con mejoras de rendimiento significativas:
   - **Canalización automática de Redis**: agrupa varias operaciones en solicitudes únicas, lo que reduce la latencia
   - **PSR-6 TagAwareAdapter**: invalidación eficiente de caché basada en etiquetas con operaciones atómicas
   - **Serialización binaria Igbinary**: la serialización binaria reduce el tamaño de entrada de caché en un 45% y mejora la velocidad en un 5-10%
   - **Conexiones persistentes mejoradas**: agrupación de conexiones más estable con mejor manejo de los procesos bifurcados
   - **Scripts Lua optimizados**: ejecución del lado del servidor combinada con canalización para lograr la máxima eficiencia

>[!ENDTABS]


## Configurar el almacenamiento en caché predeterminado de Redis

Ejecute el comando `setup:config:set` y especifique los parámetros específicos de Redis para el almacenamiento en caché predeterminado.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Con los siguientes parámetros:

- `--cache-backend=redis` habilita el almacenamiento en caché predeterminado de Redis. Si esta función ya se ha habilitado, omita este parámetro.

- `--cache-backend-redis-<parameter>=<value>` es una lista de pares de clave y valor que configuran el almacenamiento en caché predeterminado:

| Parámetro de línea de comandos | Valor | Significado | Valor predeterminado |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Nombre de host completo, dirección IP o ruta absoluta a un socket UNIX. El valor predeterminado de 127.0.0.1 indica que Redis está instalado en el servidor de Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | puerto | Puerto de escucha del servidor Redis | `6379` |
| `cache-backend-redis-db` | database | Necesario si utiliza Redis tanto para la caché predeterminada como para la caché de página completa. Especifique el número de base de datos de una de las cachés; la otra caché utiliza 0 de forma predeterminada.<br><br>**Importante**: Si utiliza Redis para más de un tipo de almacenamiento en caché, los números de base de datos deben ser diferentes. Se recomienda asignar el número de base de datos de almacenamiento en caché predeterminado a 0, el número de base de datos de almacenamiento en caché de páginas a 1 y el número de base de datos de almacenamiento de sesión a 2. | `0` |
| `cache-backend-redis-password` | contraseña | La configuración de una contraseña de Redis habilita una de sus características de seguridad integradas: el comando `auth`, que requiere que los clientes se autentiquen para tener acceso a la base de datos. La contraseña está configurada directamente en el archivo de configuración de Redis: `/etc/redis/redis.conf` | |
| `cache-backend-redis-use-lua` | use_lua | Habilite o deshabilite los scripts de Lua para todas las operaciones de redis. <br><br>**Valor predeterminado: mantener en `0`.** El modo Lua está deshabilitado de forma predeterminada para evitar regresiones de rendimiento conocidas y problemas de pérdida de caché de GraphQL introducidos por la biblioteca Redis integrada (1.17.x) cuando Lua estaba habilitado. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Habilite o deshabilite los scripts de Lua para la recolección de elementos no utilizados (el trabajo cron de `backend_clean_cache`). <br><br>**Valor predeterminado: mantener en `1`.** Habilitado de forma intencionada para garantizar la limpieza del conjunto de etiquetas atómicas durante la CG. Sin ella, puede producirse una condición de carrera cuando el cron `backend_clean_cache` se ejecuta al mismo tiempo que una operación de guardado de caché, lo que deja las entradas de caché sin un registro correspondiente en el índice de etiquetas de caché. Esto provoca que la invalidación basada en etiquetas falle de forma silenciosa; por ejemplo, actualizar un precio de producto puede no invalidar la caché del producto y, en su lugar, requerir un vaciado de caché completo. | `1` |

### Modo Lua

Cuando se habilita, el modo Lua agrupa varias operaciones de Redis (escrituras en caché, actualizaciones de etiquetas, recolección de elementos no utilizados) en un solo script atómico ejecutado en el lado del servidor mediante `EVALSHA`. Esto evita la intercalación de solicitudes simultáneas como, por ejemplo, garantizar que una entrada de caché y su pertenencia a una etiqueta se escriban juntas.

>[!WARNING]
>
>No cambie los valores predeterminados de `use_lua` y `use_lua_on_gc` sin comprender las implicaciones para su versión de Adobe Commerce:
>
>- **`use_lua`**: si se habilita esto en Adobe Commerce 2.4.7 o 2.4.8 (biblioteca `colinmollenhour/cache-backend-redis` 1.17.1), pueden dañarse las cachés y producirse problemas de pérdida de caché en GraphQL.
>- **`use_lua_on_gc`**: al deshabilitar esto en Adobe Commerce 2.4.8, se elimina la protección atómica durante la recolección de elementos no utilizados y puede provocar que la invalidación de la caché basada en etiquetas falle de forma silenciosa, lo que requiere un vaciado de caché completo para recuperarse.

## Comando de ejemplo (caché predeterminada)

En el siguiente ejemplo se habilita el almacenamiento en caché predeterminado de Redis, se establece el host en `127.0.0.1` y se asigna el número de base de datos a 0. Redis utiliza valores predeterminados para el resto de parámetros.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurar el almacenamiento en caché de páginas Redis

Para configurar el almacenamiento en caché de la página Redis en Commerce, ejecute el comando `setup:config:set` con parámetros adicionales.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Con los siguientes parámetros:

- `--page-cache=redis` habilita el almacenamiento en caché de páginas Redis. Si esta función ya se ha habilitado, omita este parámetro.

- `--page-cache-redis-<parameter>=<value>` es una lista de pares de clave y valor que configuran el almacenamiento en caché de la página:

| Parámetro de línea de comandos | Valor | Significado | Valor predeterminado |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Nombre de host completo, dirección IP o ruta absoluta a un socket UNIX. El valor predeterminado de 127.0.0.1 indica que Redis está instalado en el servidor de Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | puerto | Puerto de escucha del servidor Redis | `6379` |
| `page-cache-redis-db` | database | Necesario si utiliza Redis tanto para la caché predeterminada como para la caché de página completa. Especifique el número de base de datos de una de las cachés; la otra caché utiliza 0 de forma predeterminada.<br/>**Importante**: Si utiliza Redis para más de un tipo de almacenamiento en caché, los números de base de datos deben ser diferentes. Se recomienda asignar el número de base de datos de almacenamiento en caché predeterminado a 0, el número de base de datos de almacenamiento en caché de páginas a 1 y el número de base de datos de almacenamiento de sesión a 2. | `0` |
| `page-cache-redis-password` | contraseña | La configuración de una contraseña de Redis habilita una de sus características de seguridad integradas: el comando `auth`, que requiere que los clientes se autentiquen para tener acceso a la base de datos. Configure la contraseña en el archivo de configuración de Redis: `/etc/redis/redis.conf` | |

El ejemplo siguiente habilita el almacenamiento en caché de páginas de Redis, establece el host en `127.0.0.1` y asigna el número de base de datos a `1`. El resto de parámetros se definen con el valor predeterminado.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Revisar la configuración del entorno de Commerce

Al ejecutar los comandos para configurar el almacenamiento en caché de Redis, se actualiza la configuración del entorno de Commerce (`<Commerce-install-dir>app/etc/env.php`):

>[!BEGINTABS]

>[!TAB Caché Zend (2.4.8 y anteriores)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'redis',
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
>A partir de Commerce 2.4.9, utilice el tipo de backend simplificado `'backend' => 'redis'` en lugar de la ruta de clase completa. Symfony Cache se utiliza automáticamente cuando se especifica el nombre simplificado.

>[!ENDTABS]

## Configurar opciones de almacenamiento en caché adicionales

### Función de precarga Redis

Dado que Commerce almacena datos de configuración en la caché de Redis, puede cargar previamente datos que se reutilizan entre páginas. Para buscar las claves que deben cargarse previamente, analice los datos que se transfieren de Redis a Commerce. Adobe sugiere precargar los datos que se cargan en todas las páginas, como `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` y `DB_IS_UP_TO_DATE`.

Redis usa `pipeline` para componer solicitudes de carga. Las claves deben incluir el prefijo de base de datos; por ejemplo, si el prefijo de base de datos es `061_`, la clave de precarga tiene el siguiente aspecto: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Caché Zend]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
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

>[!TAB Caché Symfony]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'redis',
                'backend_options' => [
                    'server' => 'redis',
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
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
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

Las conexiones persistentes reutilizan las conexiones de Redis existentes entre solicitudes, lo que proporciona operaciones de caché un 5-15 % más rápidas. Configurar en `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
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
                'server' => 'redis',
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

Esta es una configuración de Symfony lista para la producción que combina todas las optimizaciones de rendimiento:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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

## Compruebe la conexión de Redis

Para comprobar que Redis y Commerce funcionan juntos correctamente:

1. Inicie sesión en el servidor que ejecuta Redis y Commerce.
1. Abra un terminal.
1. Compruebe la conexión utilizando el comando `redis-cli monitor` o el comando `redis-cli ping`.

Si los comandos se ejecutan correctamente, Redis se está ejecutando y puede comunicarse con la aplicación de Commerce. Si se producen errores, existe un problema de conexión entre Redis y Commerce que debe resolver.

### Redis monitor, comando

```shell
redis-cli monitor
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
...
```

Si ambos comandos se ejecutan correctamente, Redis se configura correctamente.

### Inspeccionar datos comprimidos

Para inspeccionar los datos de sesión comprimidos y la caché de página, use la herramienta [RESP.app](https://flathub.org/apps/details/app.resp.RESP). Admite la descompresión automática de los datos de caché de página y sesión de Commerce 2 y muestra los datos de sesión de PHP en un formato legible en lenguaje natural.
