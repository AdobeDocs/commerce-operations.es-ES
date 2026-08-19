---
title: Configuración de caché L2 para la optimización del rendimiento
description: Aprenda a configurar la caché L2 en Adobe Commerce para reducir el tráfico de red y mejorar el rendimiento. Descubra las opciones de implementación heredadas y de Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# Configuración de caché L2 para la optimización del rendimiento

El almacenamiento en caché L2 (de dos niveles) reduce el tráfico de red entre el almacenamiento de caché remoto (Redis o Valkey) y la aplicación de Commerce al agregar una capa de caché local en cada nodo web. Una instancia estándar de Commerce transfiere unos 300 KB por solicitud y el tráfico puede aumentar rápidamente a más de 1000 solicitudes en algunas situaciones.

Con el almacenamiento en caché L2, cada nodo web almacena localmente los datos a los que se accede con frecuencia y utiliza la caché remota para dos fines:

- Comprobación de la versión de los datos de la caché para asegurarse de que la caché más reciente se almacena localmente
- Transferir datos de caché actualizados del almacén remoto al equipo local

Commerce almacena la versión de los datos con hash en la caché remota, con el sufijo `:hash` anexado a la clave normal. Cuando la caché local está obsoleta, los datos se recuperan del equipo remoto a través de un adaptador de caché.

Hay dos implementaciones de caché L2 disponibles en Adobe Commerce:

| Implementación | Versión | Descripción |
| -------------- | ------- | ----------- |
| [Heredado (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Caché de dos niveles basada en Zend con `Cm_Cache_Backend_File` para almacenamiento local |
| [Moderno (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | L2 basado en caché Symfony con compatibilidad con PSR-6 y rendimiento mejorado. Apoya a Valkey. |

La caché de Symfony L2 es la implementación recomendada para Adobe Commerce 2.4.9 y versiones posteriores. Proporciona una implementación de almacenamiento en caché moderna y compatible con PSR-6 con mejoras de rendimiento significativas con respecto a la implementación tradicional de `RemoteSynchronizedCache`.

## Configuración de caché L2 heredada (RemoteSynchronizedCache)

Las instrucciones de configuración de caché L2 heredada se aplican a versiones anteriores de Adobe Commerce. Si utiliza la versión 2.4.9 o posterior de Adobe Commerce, use Valkey con la [implementación de caché de nivel 2 de Modern Symfony](#modern-symfony-l2-cache-implementation).

>[!NOTE]
>
>Esta página cubre únicamente la configuración local. Para Adobe Commerce en la nube, consulte [Configuración de la caché L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Para las versiones locales de Adobe Commerce compatibles con Redis, utilice el siguiente ejemplo para modificar o reemplazar la sección de caché existente en el archivo `app/etc/env.php`.

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
]
```

Donde:

- `backend` es la implementación de caché L2.
- `backend_options` es la configuración de caché L2.
  - `remote_backend` es la implementación de caché remota: Redis o MySQL.
  - `remote_backend_options` es la configuración de caché remota.
  - `local_backend` es la implementación de caché local: `Cm_Cache_Backend_File`.
  - `local_backend_options` es la configuración de caché local.
  - `cache_dir` es una opción específica de la caché de archivos para el directorio donde se almacena la caché local.

Para las versiones de Adobe Commerce anteriores a la 2.4.9 que admiten Redis, Adobe recomienda usar Redis para el almacenamiento remoto en caché (`\Magento\Framework\Cache\Backend\Redis`) y `Cm_Cache_Backend_File` para el almacenamiento local en caché de datos en la memoria compartida, con: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`.

Adobe recomienda el uso de la característica [`cache preload`](redis-pg-cache.md#redis-preload-feature), ya que reduce drásticamente la presión sobre Redis. No olvide agregar el sufijo `:hash` para las claves de precarga.

## Opciones de caché antiguas

A partir de Commerce 2.4, la opción `use_stale_cache` puede mejorar el rendimiento en casos específicos al ofrecer datos almacenados en caché anteriormente mientras se generan nuevos datos de caché en un proceso paralelo. Los tipos de caché recomendados y las compensaciones descritas en esta sección se aplican a las implementaciones heredadas de `RemoteSynchronizedCache` y `symfony_l2`. Para ver un ejemplo de configuración de `symfony_l2`, consulte [Caché de Symfony L2 con caché obsoleta](#symfony-l2-cache-with-stale-cache).

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

El siguiente código muestra un ejemplo de configuración para el backend `RemoteSynchronizedCache` heredado. Para ver un ejemplo de `symfony_l2`, vea [Caché de Symfony L2 con caché obsoleta](#symfony-l2-cache-with-stale-cache).

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

En las versiones de Commerce 2.4.9 o posterior, utilice la implementación de caché L2 basada en caché de Symfony (`symfony_l2` backend) en lugar de la caché L2 heredada. La caché Symfony L2 proporciona una implementación de almacenamiento en caché moderna compatible con PSR-6 con mejoras de rendimiento significativas con respecto a la versión tradicional de `RemoteSynchronizedCache`.

>[!IMPORTANT]
>
>Redis no se admite como servidor de caché remoto que comience por:
>
>- Adobe Commerce 2.4.9 y posterior
>- Parches 2.4.8-p4 y posteriores
>- 2.4.7-p9 y parches posteriores
>- Parches 2.4.6-p14 y posteriores
>- Parches 2.4.5-p16 y posteriores
>
>Si va a actualizar más allá de estas versiones, configure Valkey y actualice la configuración de la caché para que use `symfony_l2`. Consulte [configurar Valkey](config-valkey.md) y [Requisitos del sistema](../../installation/system-requirements.md).

### Ventajas de la caché Symfony L2

- **Arquitectura moderna:** creada en los componentes de caché de Symfony (compatible con PSR-6)
- **Mejor rendimiento:** compatibilidad nativa con serialización Igbinary, compresión gzip y scripts Lua
- **Conexiones persistentes:** reduce la sobrecarga de la conexión de Valkey con la agrupación de conexiones
- **Claves de precarga:** admite la precarga de claves de caché para datos críticos
- **Compatibilidad con caché obsoleta:** compatibilidad total con la opción `use_stale_cache`
- **Configuración simplificada:** nombres de tipo de servidor más limpio (`valkey`, `file`)

### Migración de RemoteSynchronizedCache a Symfony L2

Si está actualizando una instalación local desde el servidor heredado `RemoteSynchronizedCache` a `symfony_l2`, revise lo siguiente antes de actualizar `app/etc/env.php`. No basta con cambiar únicamente el valor `backend`. La estructura de configuración, los nombres clave y algunos comportamientos predeterminados son diferentes.

- **La estructura de configuración cambia.** `remote_backend`, `remote_backend_options` y `local_backend` utilizan valores diferentes en `symfony_l2`. Por ejemplo, `remote_backend` se convierte en `'valkey'` en lugar de un nombre de clase completo. Use el [ejemplo de configuración](#configuration-example-with-symfony-l2-cache) a continuación como punto de partida en lugar de editar la configuración heredada existente.

- No se recomienda **`preload_keys`con `symfony_l2`.** Si la configuración heredada incluye `preload_keys`, elimínela como parte de la migración. La precarga de claves no mejora el rendimiento en `symfony_l2` y puede aumentar la carga en Valkey al activar búsquedas de claves adicionales e innecesarias.

- **La compresión requiere un indicador explícito.** La configuración de `compression_lib` por sí sola no habilita la compresión en `symfony_l2`. Consulte [Opciones de servidor para la caché de Symfony L2](#backend-options-for-symfony-l2-cache) para ver la configuración `compress_data` requerida.

- **La caché obsoleta no está habilitada de forma predeterminada para implementaciones locales configuradas manualmente.** `use_stale_cache` toma como valor predeterminado `false` en `symfony_l2` (consulte la [tabla de opciones del servidor](#backend-options-for-symfony-l2-cache)). Si la configuración heredada utilizó el front-end `stale_cache_enabled`, debe volver a crearlo explícitamente usando el patrón de la caché de [Symfony L2 con caché obsoleta](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>Adobe Commerce en entornos de nube que establecen la variable de implementación `VALKEY_BACKEND: symfony_l2` tiene su configuración L2 completa, incluido el front-end `stale_cache_enabled`, generado automáticamente por `ece-tools`. Consulte [Configurar la caché de Symfony L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) para obtener información sobre el comportamiento específico de la nube.

- **Redis no es un servidor remoto compatible para `symfony_l2`.** Migre a Valkey como parte de este cambio. Consulte [configurar Valkey](config-valkey.md).

### Ejemplo de configuración con caché Symfony L2

>[!NOTE]
>
>Este ejemplo es para la configuración local de `app/etc/env.php`. Para Adobe Commerce en la nube, `ece-tools` administra automáticamente la configuración de la caché. En lugar de editar `env.php` directamente, consulte [Configurar la caché de Symfony L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

En el archivo `app/etc/env.php`, use el tipo de servidor `symfony_l2` simplificado para la caché L2. Este ejemplo no incluye la configuración `preload_keys`, que no se recomienda con `symfony_l2`. Para obtener más información, consulte [Migración de RemoteSynchronizedCache a Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
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

Consulte [Opciones de caché obsoletas](#stale-cache-options) para ver qué tipos de caché se benefician de la caché obsoleta y por qué.

Utilice el siguiente ejemplo para configurar front-end independientes para la compatibilidad con caché obsoleta de `symfony_l2`:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
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
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | cadena | `'valkey'` | Tipo de servidor remoto: `valkey` o `file`. Usar `valkey` para la caché L2. |
| `remote_backend_options` | matriz | `[]` | Configuración remota del servidor (consulte la documentación de Valkey) |
| `local_backend` | cadena | `'file'` | Tipo de servidor local: `file` o `apcu` |
| `local_backend_options` | matriz | `[]` | Configuración del servidor local |
| `cleanup_percentage` | entero | `95` | Umbral de limpieza de caché L1 (1-100) |
| `use_stale_cache` | booleano | `false` | Habilitar caché anticuada para alta disponibilidad |
| `compress_data` | booleano | `false` | Habilita la compresión cuando se combina con `compression_lib`. La configuración de `compression_lib` por sí sola no habilita la compresión. |
| `persistent` | booleano | `true` | Controla las conexiones persistentes al servidor remoto. Se establece en `false` (`'0'`) para que coincida con el comportamiento de la caché heredada de Zend, que toma como valor predeterminado conexiones no persistentes. |


>[!NOTE]
>
>- La opción `remote_backend` también acepta un valor de `redis`, pero Redis no se admite oficialmente (consulte la nota anterior en [Implementación moderna de caché de Symfony L2](#modern-symfony-l2-cache-implementation)).
>
>- `frontend_options.write_control`, utilizado en la configuración heredada `RemoteSynchronizedCache`, no se aplica a `symfony_l2`.

### Rendimiento y fiabilidad mejorados de la caché Symfony L2

>[!NOTE]
>
>Estas mejoras se aplican a las implementaciones de Adobe Commerce 2.4.9 que utilizan `symfony_l2` y están disponibles en el parche ACP2E-5132. Para Adobe Commerce local, aplique este parche con la herramienta Parches de calidad (QPT). Para Adobe Commerce en la nube, este parche se entrega automáticamente mediante [Parches de nube para Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest).

Las actualizaciones más recientes mejoran la escalabilidad de la caché de Symfony L2, reducen la E/S innecesaria del sistema de archivos y mejoran la consistencia y fiabilidad de la caché.

#### Almacenamiento de etiquetas de caché de Symfony L2 optimizado

Se ha optimizado el comportamiento de la caché de Symfony L2 para implementaciones respaldadas por Valkey al eliminar escrituras redundantes de índices de etiquetas de sistemas de archivos. Las etiquetas de caché ahora se almacenan exclusivamente en Valkey, alineando el comportamiento de la caché de Symfony L2 con la implementación de la caché heredada. Esto reduce la E/S de disco innecesaria, mejora el rendimiento de escritura en caché y evita el crecimiento del directorio `var/cache/symfony/tags/`.

#### Comportamiento de caché basado en archivos mejorado

Para implementaciones que utilizan la caché basada en archivos (sin Valkey), el índice de etiquetas local se sigue manteniendo para admitir la invalidación de la caché. El índice de etiquetas ahora se escribe en la ubicación `cache_dir` configurada en lugar de en la ubicación `var/cache` codificada anteriormente, lo que garantiza un uso coherente del directorio de caché y una compatibilidad mejorada con las configuraciones de caché personalizadas.

#### Corrección de pertenencia a etiqueta obsoleta después de reetiquetar

Si se reetiqueta una entrada de caché, podría dejarla asociada a etiquetas a las que ya no pertenecía. Las suscripciones a etiquetas antiguas ahora se borran al volver a etiquetar, por lo que las entradas de la caché solo se invalidan con las etiquetas asignadas actualmente a ellas.

#### Corrección de escritura remota redundante para guardar sin modificar

Al guardar una entrada de caché con contenido no modificado, se sigue activando una escritura en el backend remoto (Valkey). Las operaciones de guardado ahora se omiten cuando el contenido no se modifica, lo que reduce las escrituras remotas innecesarias.

#### Corrección de desalojos basada en el tamaño L1 (cleanup_percentage)

El umbral `cleanup_percentage` utilizado para la expulsión basada en el tamaño L1 no almacenaba en déclencheur la limpieza de forma coherente. La expulsión de caché de L1 ahora respeta correctamente la configuración de `cleanup_percentage`.

#### Bloqueo de regeneración para caché obsoleta

Cuando `use_stale_cache` está habilitado y la copia remota de una entrada no está disponible temporalmente, solo un proceso adquiere ahora un bloqueo de corta duración para regenerar esa entrada. Otras solicitudes simultáneas para la misma entrada siguen sirviendo al valor local existente en lugar de regenerarlo ellas mismas, reduciendo las estampidas de regeneración y la carga redundante del servidor.

#### Impacto

- Elimina las escrituras redundantes del índice de etiquetas del sistema de archivos para las implementaciones de caché Symfony L2 respaldadas por Valkey, lo que reduce la E/S del disco y evita el crecimiento innecesario del directorio `var/cache/symfony/tags/`.
- Garantiza que las implementaciones de caché basadas en archivos utilicen de forma coherente el `cache_dir` configurado para el índice de etiqueta local y, al mismo tiempo, conserva el comportamiento de invalidación de la caché.
- Evita la invalidación de caché incorrecta causada por pertenencias de etiquetas obsoletas dejadas atrás después del reetiquetado.
- Reduce las escrituras remotas innecesarias para guardar la caché sin modificar, lo que reduce la carga de red y back-end.
- Garantiza que los déclencheur de desalojo de caché L1 se ajusten de forma fiable al umbral `cleanup_percentage` configurado.
- Reduce las estampidas de regeneración de las entradas de `use_stale_cache` al seleccionar un solo regenerador por clave en lugar de volver a crearla en cada solicitud simultánea.

Para ver las opciones de configuración detalladas, consulte:

- [Configuración de la caché de Valkey con Symfony Cache](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [Información general de almacenamiento en caché y opciones de configuración](caching-overview.md)
>- [Opciones de servidor de caché y referencia de almacenamiento](cache-options.md)
>- [Configurar tipos y front-end de caché](cache-types.md)
>- [Configurar Redis para caché predeterminada y de página](redis-pg-cache.md)
