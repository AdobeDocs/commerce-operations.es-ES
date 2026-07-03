---
title: Configuración de caché L2 para la optimización del rendimiento
description: Aprenda a configurar la caché L2 en Adobe Commerce para reducir el tráfico de red y mejorar el rendimiento. Descubra las opciones de implementación heredadas y de Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: dac87252-6066-4d6e-a9d2-f6d84c323de7id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: efeccc00d057a7e7115f1b156c3d9202ab476ded
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 0%

---

# Configuración de caché L2 para la optimización del rendimiento

El almacenamiento en caché L2 (de dos niveles) reduce el tráfico de red entre el almacenamiento de caché remoto (Redis o Valkey) y la aplicación de Commerce al agregar una capa de caché local en cada nodo web. Una instancia estándar de Commerce transfiere unos 300 KB por solicitud y el tráfico puede aumentar rápidamente a más de 1000 solicitudes en algunas situaciones.

Con el almacenamiento en caché L2, cada nodo web almacena localmente los datos a los que se accede con frecuencia y utiliza la caché remota para dos fines:

- Comprobación de la versión de los datos de la caché para asegurarse de que la caché más reciente se almacena localmente
- Transferir datos de caché actualizados del almacén remoto al equipo local

Commerce almacena la versión de los datos con hash en la caché remota, con el sufijo `:hash` anexado a la clave normal. Cuando la caché local está obsoleta, los datos se recuperan del equipo remoto a través de un adaptador de caché.

Hay dos implementaciones de caché L2 disponibles:

| Implementación | Versión | Descripción |
| -------------- | ------- | ----------- |
| [Heredado (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | 2.4.x | Caché de dos niveles basada en Zend con `Cm_Cache_Backend_File` para almacenamiento local |
| [Moderno (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | L2 basado en caché Symfony con compatibilidad con PSR-6 y rendimiento mejorado |

>[!NOTE]
>
>Para Adobe Commerce en la nube, configure la caché L2 estableciendo la variable de implementación [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) o [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) en `.magento.env.yaml`. Consulte [Configurar la caché L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache) para ver ejemplos de configuración.

## Configuración de caché L2 heredada (RemoteSynchronizedCache)

Utilice el siguiente ejemplo para modificar o reemplazar la sección de caché existente en el archivo `app/etc/env.php`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

Donde:

- `backend` es la implementación de caché L2.
- `backend_options` es la configuración de caché L2.
   - `remote_backend` es la implementación de caché remota: Redis o MySQL.
   - `remote_backend_options` es la configuración de caché remota.
   - `local_backend` es la implementación de caché local: `Cm_Cache_Backend_File`
   - `local_backend_options` es la configuración de caché local.
   - `cache_dir` es una opción específica de la caché de archivos para el directorio donde se almacena la caché local.

Adobe recomienda usar Redis para el almacenamiento remoto en caché (`\Magento\Framework\Cache\Backend\Redis`) y `Cm_Cache_Backend_File` para el almacenamiento local en caché de datos en la memoria compartida, con: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe recomienda el uso de la característica [`cache preload`](redis-pg-cache.md#redis-preload-feature), ya que reduce drásticamente la presión sobre Redis. No olvide agregar el sufijo &#39;:hash&#39; para las claves de precarga.

## Opciones de caché antiguas

A partir de Commerce 2.4, la opción `use_stale_cache` puede mejorar el rendimiento en casos específicos al ofrecer datos almacenados en caché anteriormente mientras se generan nuevos datos de caché en un proceso paralelo.

Por lo general, el equilibrio con la espera de bloqueo es aceptable desde el punto de vista del rendimiento. Sin embargo, a medida que aumenta el número de bloques o entradas de caché, las esperas de bloqueo tardan más. En algunos casos, la espera puede ser de hasta **el número de claves** x **tiempo de espera de búsqueda** para el proceso. En casos excepcionales, un comerciante puede tener cientos de claves en la caché de `Block/Config`, por lo que incluso un pequeño tiempo de espera de búsqueda para un bloqueo puede costar segundos.

>[!IMPORTANT]
>
>La caché antigua solo funciona con la caché L2. Para habilitarlo, agregue `'use_stale_cache' => true` a la configuración de nivel superior del front-end de caché L2.

Adobe recomienda habilitar la opción `use_stale_cache` solo para los tipos de caché que más se benefician de ella, incluidos:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe no recomienda habilitar la opción `use_stale_cache` para el tipo de caché `default`.

El siguiente código muestra un ejemplo de configuración:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Implementación moderna de la caché Symfony L2

A partir de Commerce 2.4.9, puede utilizar la implementación de caché L2 basada en Symfony Cache (`symfony_l2` backend) que proporciona una implementación de almacenamiento en caché moderna compatible con PSR-6 con mejoras significativas de rendimiento con respecto a la implementación tradicional de `RemoteSynchronizedCache`.

>[!NOTE]
>
>Actualmente, esta funcionalidad solo está disponible para clientes de Adobe Commerce local 2.4.9. Se habilitará para Adobe Commerce en la nube más adelante en julio de 2026.

### Ventajas de la caché Symfony L2

- **Arquitectura moderna**: creada en los componentes de la caché Symfony (compatible con PSR-6)
- **Mejor rendimiento**: Compatibilidad nativa con serialización Igbinary, compresión gzip y scripts Lua
- **Conexiones persistentes**: reduce la sobrecarga de conexión de Redis o Valkey con la agrupación de conexiones
- **Claves de precarga**: admite la precarga de claves de caché para datos críticos
- **Compatibilidad con caché obsoleta**: Compatibilidad total con la opción `use_stale_cache`
- **Configuración simplificada**: nombres de tipo de servidor más limpios (`redis`, `valkey`, `file`)

### Ejemplo de configuración con caché Symfony L2

Usar el tipo de servidor `symfony_l2` simplificado para la caché L2:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Redis with Symfony Cache
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Caché Symfony L2 con caché obsoleta

Configure front-end independientes para admitir caché obsoleta:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Opciones de servidor para la caché de Symfony L2

| Opción | Tipo | Predeterminado | Descripción |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | cadena | `'redis'` | Tipo de servidor remoto: `redis`, `valkey` o `file` |
| `remote_backend_options` | matriz | `[]` | Configuración del servidor remoto (consulte la documentación de Redis/Valkey) |
| `local_backend` | cadena | `'file'` | Tipo de servidor local: `file` o `apcu` |
| `local_backend_options` | matriz | `[]` | Configuración del servidor local |
| `cleanup_percentage` | entero | `90` | Umbral de limpieza de caché L1 (1-100) |
| `use_stale_cache` | booleano | `false` | Habilitar caché anticuada para alta disponibilidad |

### Asistencia de Valkey

El servidor `symfony_l2` también admite Valkey como servidor remoto:

```php
'backend_options' => [
    'remote_backend' => 'valkey',  // Use Valkey instead of Redis
    'remote_backend_options' => [
        'server' => 'localhost',
        'database' => '0',
        'port' => '6379',
        'serializer' => 'igbinary',
        'compression_lib' => 'gzip',
    ],
    // ... rest of configuration
]
```

Para ver las opciones de configuración detalladas, consulte:
- [Configuración de caché de Redis con caché de Symfony](redis-pg-cache.md)
- [Configuración de la caché de Valkey con Symfony Cache](valkey-pg-cache.md)
