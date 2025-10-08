---
title: Configuración de caché L2
description: Obtenga información sobre cómo configurar la caché L2 para la optimización del rendimiento de Adobe Commerce. Descubra los pasos de configuración y las técnicas de reducción del tráfico de red.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Configuración de caché L2

El almacenamiento en caché permite reducir el tráfico de red entre el almacenamiento de caché remoto y la aplicación de Commerce. Una instancia estándar de Commerce transfiere unos 300 kb por solicitud y el tráfico puede aumentar rápidamente a más de ~1000 solicitudes en algunas situaciones.

Para reducir el ancho de banda de red a Redis, almacene los datos de la caché localmente en cada nodo web y utilice la caché remota para dos fines:

- Compruebe la versión de los datos de la caché y asegúrese de que la caché más reciente se almacena localmente
- Transfiera la última caché del equipo remoto al equipo local

Commerce almacena la versión de datos con hash en Redis, con el sufijo &#39;:hash&#39; anexado a la clave normal. Si hay una caché local obsoleta, los datos se transfieren al equipo local con un adaptador de caché.

>[!INFO]
>
>Para Adobe Commerce en la infraestructura en la nube, puede usar [implementar variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es#redis_backend) para la configuración de la caché L2.

## Ejemplo de configuración

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

A partir de [!DNL Commerce] 2.4, la opción `use_stale_cache` puede mejorar el rendimiento en algunos casos específicos.

Por lo general, la compensación con la espera de bloqueo es aceptable desde el lado del rendimiento, pero cuanto mayor sea el número de bloques o caché que tiene el comerciante, más tiempo se pasa esperando bloqueos. En algunos casos, puede esperar **números de claves** \* **tiempo de espera de búsqueda** durante el proceso. En algunos casos excepcionales, el comerciante puede tener cientos de claves en la caché de `Block/Config`, por lo que incluso un pequeño tiempo de espera de búsqueda para el bloqueo puede costar segundos.

La caché antigua solo funciona con una caché L2. Con una caché obsoleta, puede enviar una caché obsoleta, mientras que una nueva se genera en un proceso paralelo. Para habilitar la caché obsoleta, agregue `'use_stale_cache' => true` a la configuración superior de la caché L2.

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
