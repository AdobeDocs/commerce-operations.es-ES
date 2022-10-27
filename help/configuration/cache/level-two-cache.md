---
title: Configuración de caché L2
description: Aprenda a configurar la caché L2.
source-git-commit: 2ef8b48fab84221c8e6423f41126bbee37706809
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configuración de caché L2

El almacenamiento en caché permite reducir el tráfico de red entre el almacenamiento en caché remoto y la aplicación Commerce. Una instancia de comercio estándar transfiere alrededor de 300 kb por solicitud, y el tráfico puede crecer rápidamente a más de ~1000 solicitudes en algunas situaciones.

Para reducir el ancho de banda de la red a Redis, almacene datos de caché localmente en cada nodo web y utilice la caché remota para dos propósitos:

- Compruebe la versión de los datos de caché y asegúrese de que la caché más reciente se almacena localmente
- Transferir la caché más reciente del equipo remoto al equipo local

Commerce almacena la versión de datos con hash en Redis, con el sufijo &#39;:hash&#39; anexado a la clave regular. Si hay una caché local obsoleta, los datos se transfieren al equipo local con un adaptador de caché.

>[!INFO]
>
>Para Adobe Commerce en infraestructura de nube, puede usar [implementar variables](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) para la configuración de caché L2.

## Ejemplo de configuración

Utilice el siguiente ejemplo para modificar o reemplazar la sección de caché existente en la `app/etc/env.php` archivo.

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
                ],
                'use_stale_cache' => false,
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

- `backend` es la implementación de la caché L2.
- `backend_options` es la configuración de caché L2.
   - `remote_backend` es la implementación de caché remota: Redis o MySQL.
   - `remote_backend_options` es la configuración de caché remota.
   - `local_backend` es la implementación de caché local: `Cm_Cache_Backend_File`
   - `local_backend_options` es la configuración de caché local.
      - `cache_dir` es una opción específica de caché de archivos para el directorio donde se almacena la caché local.
   - `use_stale_cache` es un indicador que habilita o deshabilita el uso de la caché obsoleta.

Adobe recomienda utilizar Redis para el almacenamiento en caché remoto (`\Magento\Framework\Cache\Backend\Redis`) y `Cm_Cache_Backend_File` para el almacenamiento en caché local de datos en la memoria compartida, utilizando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

El Adobe recomienda el uso de la variable [`cache preload`](redis-pg-cache.md#redis-preload-feature) , ya que disminuye drásticamente la presión sobre Redis. No olvide agregar el sufijo &#39;:hash&#39; para claves de precarga.

## Opciones de caché obsoletas

Primeros pasos con [!DNL Commerce] 2.4. `use_stale_cache` puede mejorar el rendimiento en algunos casos específicos.

Por lo general, la compensación con la espera de bloqueo es aceptable desde el punto de vista del rendimiento, pero cuanto mayor sea el número de bloques o caché que tenga el comerciante, más tiempo se pasa esperando los bloqueos. En algunos casos, puede esperar un **números de claves** \* **tiempo de espera de búsqueda** cantidad de tiempo para el proceso. En algunos casos excepcionales, el comerciante puede tener cientos de claves en la variable `Block/Config` caché, por lo que incluso el tiempo de espera de búsqueda pequeño para bloqueo puede costar segundos.

La caché obsoleta solo funciona con una caché L2. Con una caché obsoleta, podría enviar una caché obsoleta, mientras que una nueva se está generando en un proceso paralelo. Para habilitar la caché obsoleta, agregue `'use_stale_cache' => true` a la configuración superior de la caché L2.

Adobe recomienda habilitar la variable `use_stale_cache` solo para los tipos de caché que más se benefician de ella, incluidos:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
                ],
                'use_stale_cache' => false,
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
