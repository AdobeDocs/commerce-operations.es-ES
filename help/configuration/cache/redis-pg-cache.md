---
title: Usar Redis para la caché predeterminada
description: Aprenda a configurar Redis como la caché predeterminada para Adobe Commerce y Magento Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# Usar Redis para la caché predeterminada

Commerce proporciona opciones de línea de comandos para configurar la página Redis y el almacenamiento en caché predeterminado. Aunque puede configurar el almacenamiento en caché editando el `<Commerce install dir>app/etc/env.php` , el uso de la línea de comandos es el método recomendado, especialmente para las configuraciones iniciales. La línea de comandos proporciona validación, lo que garantiza que la configuración sea sintácticamente correcta.

Debe [instalar Redis](config-redis.md#install-redis) antes de continuar.

## Configurar el almacenamiento en caché predeterminado de Redis

Ejecute el `setup:config:set` y especifique los parámetros específicos del almacenamiento en caché predeterminado de Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter_name>=<parameter_value>...
```

donde

`--cache-backend=redis` habilita el almacenamiento en caché predeterminado de Redis. Si esta función ya se ha habilitado, omita este parámetro.

`--cache-backend-redis-<parameter_name>=<parameter_value>` es una lista de pares de clave-y-valor que configuran el almacenamiento en caché predeterminado:

| Parámetro de línea de comandos | Parámetro | Significado | Valor predeterminado |
|--- |--- |--- |--- |
| cache-backend-redis-server | server | Nombre de host completo, dirección IP o una ruta absoluta a un socket UNIX. El valor predeterminado de 127.0.0.1 indica que Redis está instalado en el servidor de comercio. | 127.0.0.1 |
| cache-backend-redis-port | puerto | Puerto de escucha del servidor de Redis | 6379 |
| cache-backend-redis-db | base de datos | Necesario si utiliza Redis tanto para la caché predeterminada como para la de página completa. Debe especificar el número de la base de datos de una de las cachés; la otra caché utiliza 0 de forma predeterminada.<br><br>Importante: Si utiliza Redis para más de un tipo de almacenamiento en caché, los números de la base de datos deben ser diferentes. Se recomienda asignar el número predeterminado de base de datos de almacenamiento en caché a 0, el número de base de datos de almacenamiento en caché de páginas a 1 y el número de base de datos de almacenamiento de sesión a 2. | 0 |
| cache-backend-redis-password | password | La configuración de una contraseña de Redis habilita una de sus funciones de seguridad integradas: el `auth` , que requiere que los clientes se autentiquen para acceder a la base de datos. La contraseña se configura directamente en el archivo de configuración de Redis, `/etc/redis/redis.conf`. |  |

### Ejemplo, comando

El ejemplo siguiente habilita el almacenamiento en caché predeterminado de Redis, establece el host en `127.0.0.1` y asigna el número de la base de datos a 0. Redis utiliza valores predeterminados para todos los demás parámetros.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurar el almacenamiento en caché de páginas de Redis

Para configurar el almacenamiento en caché de la página de Redis en Commerce, ejecute el `setup:config:set` con parámetros adicionales.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter_name>=<parameter_value>...
```

donde

`--page-cache=redis` habilita el almacenamiento en caché de páginas de Redis. Si esta función ya se ha habilitado, omita este parámetro.

`--page-cache-redis-<parameter_name>=<parameter_value>` es una lista de pares de parámetros/valores que configuran el almacenamiento en caché de la página:

| Parámetro de línea de comandos | Parámetro | Significado | Valor predeterminado |
|--- |--- |--- |--- |
| page-cache-redis-server | server | Nombre de host completo, dirección IP o una ruta absoluta a un socket UNIX. El valor predeterminado de 127.0.0.1 indica que Redis está instalado en el servidor de comercio. | 127.0.0.1 |
| page-cache-redis-port | puerto | Puerto de escucha del servidor de Redis | 6379 |
| page-cache-redis-db | base de datos | Necesario si utiliza Redis para la caché de página predeterminada y completa. Debe especificar el número de la base de datos de una de las cachés; la otra caché utiliza 0 de forma predeterminada.<br/>Importante: Si utiliza Redis para más de un tipo de almacenamiento en caché, los números de la base de datos deben ser diferentes. Se recomienda asignar el número predeterminado de base de datos de almacenamiento en caché a 0, el número de base de datos de almacenamiento en caché de páginas a 1 y el número de base de datos de almacenamiento de sesión a 2. | 0 |
| page-cache-redis-password | password | La configuración de una contraseña de Redis habilita una de sus funciones de seguridad integradas: el `auth` , que requiere que los clientes se autentiquen para acceder a la base de datos. Configure la contraseña en el archivo de configuración de Redis, /etc/redis/redis.conf. |  |

### Ejemplo, comando

El ejemplo siguiente habilita el almacenamiento en caché de páginas de Redis y establece el host en `127.0.0.1` y asigna el número de la base de datos a 1. Todos los demás parámetros se establecen en el valor predeterminado.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Resultados

Como resultado de los dos comandos de ejemplo, Commerce agrega líneas similares a las siguientes a `<Commerce install dir>app/etc/env.php`:

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

## Uso de AWS ElastiCache con la instancia EC2

A partir de Commerce 2.4.3, las instancias alojadas en Amazon EC2 pueden utilizar un AWS ElastiCache en lugar de una instancia local de Redis.

>[!WARNING]
>
>Esta sección solo funciona para instancias de comercio que se ejecutan en VPC Amazon EC2. No funciona para instalaciones locales.

### Configuración de un clúster de Redis

Después [configuración de un clúster de Redis en AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), configure la instancia EC2 para utilizar ElastiCache.

1. [Crear un clúster de ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) en la misma región y VPC de la instancia EC2.
1. Compruebe la conexión.

   - Abra una conexión SSH con la instancia EC2
   - En la instancia EC2, instale el cliente Redis:

      ```bash
      sudo apt-get install redis
      ```

   - Agregue una regla de entrada al grupo de seguridad EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Agregue una regla de entrada al grupo de seguridad del clúster ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Conéctese a la CLI de Redis:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### Configuración de Commerce para utilizar el clúster

El comercio admite varios tipos de configuraciones de almacenamiento en caché. Por lo general, las configuraciones de almacenamiento en caché se dividen entre front-end y backend. El almacenamiento en caché del front-end se clasifica como &#39;predeterminado&#39;, se utiliza para cualquier tipo de caché. Puede personalizar o dividir en cachés de nivel inferior para lograr un mejor rendimiento. Una configuración común de Redis está separando la caché predeterminada y la caché de página en su propia base de datos de Redis (RDB).

Ejecutar `setup` para especificar los extremos de Redis.

Configuración de Commerce for Redis como almacenamiento en caché predeterminado:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Configurar el almacenamiento en caché de páginas de Commerce for Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Configure Commerce para utilizar Redis para el almacenamiento de sesión:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Verifique la conectividad

Para verificar que Commerce está hablando con ElasiCache:

1. Abra una conexión SSH a la instancia Commerce EC2.
1. Inicie el monitor Redis.

   ```bash
   redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port> monitor
   ```

1. Abra una página en la interfaz de usuario de Commerce.
1. Compruebe el [salida de caché](#verify-redis-connection) en su terminal.

## Nueva implementación de caché de Redis

A partir de Commerce 2.3.5, se recomienda utilizar la implementación de caché de Redis ampliada: `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Función de precarga de redis

Dado que Commerce almacena muchos datos de configuración en la caché de Redis, podemos cargar previamente datos que se reutilizan entre páginas.
Para encontrar claves que se deben precargar, debe analizar los datos que se transfieren de Redis a Commerce. Se recomienda cargar previamente los datos que se cargan en todas las páginas; por ejemplo, `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.
Redis usa el `pipeline` para combinar solicitudes de carga.
Tenga en cuenta que las claves deben incluir el prefijo de la base de datos, por ejemplo, si el prefijo de la base de datos es `061_`, la clave de precarga tiene el aspecto siguiente `061_SYSTEM_DEFAULT`.

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

Si está utilizando la función de precarga con la caché L2, no olvide agregar el sufijo &#39;:hash&#39; a sus claves, ya que la caché L2 solo transfiere el hash de los datos, no los datos en sí:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Generación paralela

A partir de la versión 2.4.0, presentamos el `allow_parallel_generation` para los usuarios que desean eliminar las espera de los bloqueos.
Se deshabilita de forma predeterminada y se recomienda desactivarla hasta que tenga configuraciones y/o bloques excesivos.

**Para habilitar la generación paralela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Como es un indicador, no puede desactivarlo con un comando. Debe establecer manualmente el valor de configuración en `false`:

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

## Comprobar conexión Redis

Para verificar que Redis y Commerce están trabajando juntos, inicie sesión en el servidor que ejecuta Redis, abra un terminal y utilice el comando Redis monitor o el comando ping.

### Redis monitor, comando

```bash
redis-cli monitor
```

Ejemplo de salida de almacenamiento en caché de páginas:

```terminal
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

### Redis ping, comando

```bash
redis-cli ping
```

`PONG` debe ser la respuesta.

Si ambos comandos se ejecutaron correctamente, Redis está configurado correctamente.

### Inspección de datos comprimidos

Para inspeccionar los datos de sesión comprimidos y la caché de página, la variable [RESP.app](https://flathub.org/apps/details/app.resp.RESP) admite la descompresión automática de la caché de páginas y sesiones de Commerce 2 y muestra los datos de sesión de PHP de forma legible.
