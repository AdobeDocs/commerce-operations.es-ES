---
title: Prácticas recomendadas para la configuración de los servicios Redis y Valkey
description: Aprenda a configurar los servicios de Redis y Valkey para Adobe Commerce. Mejore el rendimiento del almacenamiento en caché con caché L2, conexiones esclavas, caché obsoleta y separación de sesiones.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '2071'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración de servicios de Redis y Valkey

Utilice estas recomendaciones para configurar Redis o Valkey para el almacenamiento en caché y las sesiones de Adobe Commerce.

- Configuración de la caché L2
- Habilitar conexión esclava
- Precargar claves
- Habilitar caché obsoleta
- Separar caché y sesión
- Comprimir la caché
- Ejemplos de configuración

>[!NOTE]
>
>Para Commerce en entornos de infraestructura en la nube, compruebe que está usando la última versión del paquete `ece-tools`. Si no es así, [actualice a la versión más reciente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Puede comprobar la versión instalada en su entorno local mediante el comando CLI `composer show magento/ece-tools`.

## Configuración de la caché L2

Configure la caché L2 estableciendo la variable de implementación `REDIS_BACKEND` o `VALKEY_BACKEND` en el archivo de configuración `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Configuración de Redis]

Para Redis, utilice:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obtener información sobre la configuración del entorno en la infraestructura en la nube, consulte la referencia de configuración [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) en la _Guía de Commerce en la infraestructura en la nube_.

Para instalaciones locales, consulte [Configurar el almacenamiento en caché de la página Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) en la _Guía de configuración_.

>[!TAB Configuración de Valkey]

Para Valkey, utilice:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obtener información sobre la configuración del entorno en la infraestructura en la nube, consulte la referencia de configuración [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) en la _Guía de Commerce en la infraestructura en la nube_.

Para instalaciones locales, consulte [Configurar Valkey](../../../configuration/cache/config-valkey.md) en la _Guía de configuración_.

>[!ENDTABS]


### Tamaño de la memoria caché L2 para Adobe Commerce Cloud

La caché L2 usa un [sistema de archivos temporal](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) como mecanismo de almacenamiento. A diferencia de los almacenes de valor clave especializados, los tmpfs no tienen una política de desalojo de claves, por lo que el uso de la memoria puede crecer sin límites. Para evitar el agotamiento, Adobe Commerce borra automáticamente el almacenamiento L2 cuando el uso alcanza un umbral configurable (95 % de forma predeterminada). Puede controlar el consumo de memoria solicitando un montaje de `/dev/shm` mayor o reduciendo el umbral de limpieza.

Ajuste el uso máximo de memoria caché L2 en función de los requisitos del proyecto. Utilice uno de los siguientes métodos:

- Cree un vale de soporte técnico para ajustar el tamaño de montaje de `/dev/shm`. En este caso, Adobe recomienda establecer el tamaño de montaje de `/dev/shm` en 15 GB.
- Ajuste la propiedad `cleanup_percentage` en el nivel de aplicación para limitar el uso del almacenamiento y la memoria libre disponible para otros servicios.
Puede ajustar la configuración en la configuración de implementación en el grupo de configuración de caché `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>La opción configurable `cleanup_percentage` se introdujo en Adobe Commerce 2.4.4.

Los siguientes ejemplos muestran el código de configuración en el archivo `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Configuración de Redis]

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Configuración de Valkey]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

Los requisitos de caché varían en función de la configuración del proyecto y del código de terceros personalizado. Tamaño de la memoria caché L2 para que la caché pueda funcionar sin visitas de umbral frecuentes.

Lo ideal es que el uso de la memoria caché L2 se estabilice por debajo del umbral para evitar la limpieza frecuente del almacenamiento.

Puede comprobar el uso de la memoria de almacenamiento en caché L2 en cada nodo del clúster ejecutando el siguiente comando CLI y revisando la línea `/dev/shm`.

```shell
df -h /dev/shm
```

El uso puede variar entre nodos, pero debe converger a un valor similar.

## Habilitar conexión esclava

Habilite la conexión esclava en el archivo `.magento.env.yaml` para permitir que Adobe Commerce utilice una conexión de caché de solo lectura adicional para las lecturas mientras sigue utilizando el extremo principal para las escrituras. Esta configuración puede reducir la carga de lectura en el servicio de caché principal y distribuir el tráfico de lectura de forma más eficaz.

>[!BEGINTABS]

>[!TAB Configuración de Redis]

Para Redis, utilice:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Para obtener información sobre la configuración del entorno en la infraestructura de Commerce Cloud, consulte [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) en la _Guía de infraestructura de Commerce en la nube_.

Para las instalaciones locales de Adobe Commerce, configure la nueva implementación de caché de Redis con los comandos `bin/magento setup`. Consulte [Usar Redis para la caché predeterminada](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) en la _Guía de configuración_.

>[!TAB Configuración de Valkey]

Para Valkey, utilice:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Para obtener información sobre la configuración del entorno en la infraestructura de Commerce Cloud, consulte [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) en la _Guía de infraestructura de Commerce en la nube_.

Para las instalaciones locales de Adobe Commerce, configure la nueva implementación de caché de Valkey con los comandos `bin/magento setup`. Consulte [Configurar Valkey](../../../configuration/cache/config-valkey.md) en la _Guía de configuración_.

>[!ENDTABS]

## Precargar claves

Magento generalmente carga las entradas de caché de Redis o Valkey de una en una. La función de precarga permite proporcionar una lista de las claves utilizadas frecuentemente que Magento recupera en una sola canalización en el primer acceso durante una solicitud. A continuación, Magento mantiene los valores recuperados en la memoria PHP durante el resto de esa solicitud, lo que reduce los viajes de ida y vuelta repetidos a Redis o Valkey y puede mejorar el rendimiento de arranque de la solicitud para esas claves.

Puede identificar las claves utilizadas con frecuencia controlando los comandos activos en Redis o Valkey:

>[!BEGINTABS]

>[!TAB Configuración de clave de precarga de Redis]

Las claves de precarga están configuradas en el archivo de configuración `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Para enumerar las claves, ejecute el siguiente comando:

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Después de 10 segundos, presione **[!UICONTROL Ctrl+C]**. A continuación, ejecute el siguiente comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Este registro enumera las claves que puede cargar previamente. Para ver el contenido de una clave, ejecute el siguiente comando:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

Para instalaciones locales, consulte [Función de precarga de Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) en la _Guía de configuración_.

>[!TAB Configuración de clave de precarga de Valkey]

Las claves de precarga están configuradas en el archivo de configuración `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Para enumerar las claves, ejecute el siguiente comando:

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Después de 10 segundos, presione **[!UICONTROL Ctrl+C]**. A continuación, ejecute el siguiente comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Este registro enumera las claves que puede cargar previamente. Para ver el contenido de una clave, ejecute el siguiente comando:

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

Para instalaciones locales, consulte [Función de precarga de Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) en la _Guía de configuración_.

>[!ENDTABS]

## Habilitar caché obsoleta

La caché obsoleta es una característica de caché L2 de `RemoteSynchronizedCache`. Cuando está habilitada, Adobe Commerce puede servir un valor de caché local existente de `/dev/shm` mientras otra solicitud ya está regenerando la misma entrada, en lugar de hacer que cada solicitud simultánea espere. Esto reduce las estampidas de caché y la contención de bloqueos durante la regeneración de entradas de caché costosas.

### Cómo funciona

Con `RemoteSynchronizedCache`, Magento mantiene dos copias de cada entrada de caché: una copia local en `/dev/shm` y una copia remota en Redis o Valkey. Cuando la copia remota no está disponible y ya existe un bloqueo de regeneración para esa clave, las solicitudes simultáneas pueden recibir el valor local anterior en lugar de esperar hasta que se escriba el nuevo valor.

Para habilitar la caché obsoleta, configúrela en el archivo `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Configurar caché obsoleta para Redis]

Para Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Configurar caché obsoleta para Valkey]

Para Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>El tipo de caché `full_page` no es relevante para los proyectos de Adobe Commerce en la nube porque usan [Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly).

Para instalaciones locales, consulte [Opciones de caché antiguas](../../../configuration/cache/level-two-cache.md#stale-cache-options) en la _Guía de configuración_.

>[!WARNING]
>
>La configuración anterior habilita la caché obsoleta en el front-end de caché de `default`, que aplica el comportamiento de caché obsoleta a todas las entradas de caché que utilizan ese front-end. Los tipos de caché principales de Magento suelen funcionar según lo esperado con esta configuración. Sin embargo, si el proyecto incluye código personalizado o extensiones que escriben en la caché a través de la API genérica `\Magento\Framework\App\Cache` (por ejemplo `$this->cache->save()`) sin un front-end de caché dedicado, esas entradas también pueden proporcionar valores antiguos durante la regeneración.
>
>
>Si esto resulta en un comportamiento inesperado en las personalizaciones, deje deshabilitada la caché obsoleta en el front-end `default` y actívela solo para los tipos de caché seleccionados, como comúnmente se [hace de forma local](../../../configuration/cache/level-two-cache.md#stale-cache-options).

### Habilitar la caché obsoleta por tipo de caché individualmente

Puede habilitar la caché obsoleta solamente para los tipos de caché seleccionados definiendo un front-end de caché dedicado en `.magento.env.yaml` y asignando los tipos de caché seleccionados a él.

Para funcionar correctamente, el front-end personalizado debe definirse como un front-end completo en `CACHE_CONFIGURATION.frontend`. No basta con definir solo `use_stale_cache: true` para un nuevo nombre de front-end.

**Configuraciones de ejemplo**

>[!BEGINTABS]

>[!TAB Configurar caché obsoleta para Redis]

Para Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Configurar caché obsoleta para Valkey]

Para Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>Si el front-end de origen está configurado con opciones de back-end adicionales como compresión, reintentos, teclas de precarga u otros valores de ajuste, copie esas opciones en `stale_cache_enabled` para que el nuevo front-end mantenga el mismo comportamiento.


## Instancias de caché y sesión independientes

La separación de la caché de las sesiones permite administrarlas de forma independiente. Reduce la contención entre la caché y el tráfico de sesión, evita que la presión relacionada con la caché afecte a las sesiones y permite que cada instancia de Redis o Valkey tenga un tamaño y un ajuste para su propia carga de trabajo.

Siga los pasos a continuación para aprovisionar una instancia dedicada para las sesiones:

>[!BEGINTABS]

>[!TAB Redis]

1. Actualizar el archivo de configuración `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
     type: redis:6.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. Actualizar el archivo de configuración `.magento.app.yaml`.

   ```yaml
      relationships:
        database: "mysql:mysql"
        redis: "redis:redis"
        redis-session: "redis-session:redis"   # Relationship of the new Redis instance
        search: "search:elasticsearch"
        rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Solicite una nueva instancia de Redis dedicada a sesiones en entornos de producción y ensayo.

   Enviar un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Incluir los archivos de configuración actualizados de `.magento/services.yaml` y `.magento.app.yaml`.

   Esta actualización no provoca ningún tiempo de inactividad, pero requiere una implementación para activar el nuevo servicio.

1. Compruebe que la nueva instancia se esté ejecutando y anote el número de puerto.

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Agregue el número de puerto al archivo de configuración `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configure el puerto de sesión de Redis solo si `ece-tools` no puede detectarlo automáticamente a partir de la definición del servicio de sesión de `MAGENTO_CLOUD_RELATIONSHIPS` Redis.

   >[!NOTE]
   >
   >Establezca `disable_locking` en `1` para obtener el mejor rendimiento. En casos excepcionales en los que se producen condiciones de carrera debido a una alta actividad de sesión simultánea, establézcala en `0` para habilitar el bloqueo.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Quitar sesiones de la [base de datos predeterminada](../../../configuration/cache/redis-pg-cache.md) (`db 0`) en la instancia de caché de Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Valkey]

1. Actualizar el archivo de configuración `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. Actualizar el archivo de configuración `.magento.app.yaml`.

   ```yaml
   relationships:
     database: "mysql:mysql"
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Solicite una nueva instancia de Valkey dedicada a sesiones en entornos de producción y ensayo.

   Enviar un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Incluir los archivos de configuración actualizados de `.magento/services.yaml` y `.magento.app.yaml`.

   Esta actualización no provoca ningún tiempo de inactividad, pero requiere una implementación para activar el nuevo servicio.

1. Compruebe que la nueva instancia se esté ejecutando y anote el número de puerto.

   ```shell
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Agregue el número de puerto al archivo de configuración `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configure el puerto de sesión de Valkey solo si `ece-tools` no puede detectarlo automáticamente desde la definición del servicio de sesión de Valkey `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Establezca `disable_locking` en `1` para obtener el mejor rendimiento. En casos excepcionales en los que se producen condiciones de carrera debido a una alta actividad de sesión simultánea, establézcala en `0` para habilitar el bloqueo.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Elimine sesiones de la [base de datos predeterminada](../../../configuration/cache/redis-pg-cache.md) (`db 0`) en la instancia de caché de Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compresión de caché

Si usa más de 6 GB de Redis o Valkey `maxmemory`, puede habilitar la compresión de caché para reducir el espacio consumido por las claves. Tenga en cuenta que esta configuración cambia el rendimiento del lado del cliente por ahorros de memoria. Si tiene capacidad de CPU disponible, considere la posibilidad de habilitarla. Consulte [Usar Redis para almacenamiento de sesión](../../../configuration/cache/redis-session.md) o [Usar Valkey para almacenamiento de sesión](../../../configuration/cache/valkey-session.md) en la _Guía de configuración_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Habilitar la liberación asincrónica

Para habilitar `lazyfree` en Adobe Commerce en la infraestructura en la nube, envíe un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) en el que se solicite que se aplique la siguiente configuración de Redis o Valkey a sus entornos:

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Cuando `lazyfree` está habilitado, Redis o Valkey descargan la reclamación de memoria a subprocesos en segundo plano para expulsiones, caducidades, eliminaciones iniciadas por el servidor, eliminaciones de usuarios y vaciados del conjunto de datos de réplica. Esto reduce el bloqueo de subprocesos principales y puede reducir la latencia de las solicitudes.

>[!NOTE]
>
>La opción `lazyfree-lazy-user-del yes` hace que el comando `DEL` se comporte como `UNLINK`, lo que desvincula las claves inmediatamente y libera su memoria de forma asincrónica.

>[!WARNING]
>
>Dado que la liberación se produce en segundo plano, la memoria utilizada por las claves eliminadas, caducadas o desalojadas permanece asignada hasta que los subprocesos en segundo plano completan el trabajo. Si su instancia de Redis o Valkey ya está bajo una presión de memoria estricta, realice una prueba con precaución y considere primero reducir la presión de memoria. Por ejemplo, deshabilite Bloquear caché para casos específicos e instancias de Redis de caché y sesión independientes como se ha descrito anteriormente.

## Habilitar E/S multiproceso

Para habilitar el subprocesamiento de E/S de Redis en Adobe Commerce en la infraestructura en la nube, envíe un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando la configuración de subprocesamiento de E/S a continuación. Esta configuración puede mejorar el rendimiento descargando lecturas y escrituras de socket y analizando comandos desde el hilo principal, a costa de un mayor uso de CPU. Valide en y supervise sus hosts.

>[!BEGINTABS]

>[!TAB Configurar subprocesos de E/S para Redis]

Para Redis:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Configurar subprocesos de E/S para Valkey]

Para Valkey:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>Los subprocesos de E/S paralelizan solo la E/S del cliente y el análisis. La ejecución de comandos de Redis sigue siendo de un solo subproceso.

>[!WARNING]
>
>La activación de los subprocesos de E/S puede aumentar el uso de CPU y no beneficia a todas las cargas de trabajo. Comience con un valor y una referencia conservadores. Si la latencia aumenta o CPU se satura, reduzca `io-threads` o deshabilite las lecturas en los subprocesos de E/S.


## Aumentar los tiempos de espera y reintentos del cliente

Aumente la tolerancia del cliente de caché de Redis o Valkey a periodos de saturación cortos ajustando las opciones del servidor en `.magento.env.yaml`.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Esta configuración puede reducir los errores intermitentes de conexión y tiempo de espera de lectura durante picos cortos al reintentar la configuración de la conexión y permitir más tiempo para las respuestas de Redis o Valkey.

>[!NOTE]
>
>Esta configuración puede ayudar con una congestión breve, pero no corrige la sobrecarga persistente.

## Ejemplos de configuración

Utilice los siguientes ejemplos como punto de partida para las configuraciones del servicio Redis o Valkey.


### Aplicar todas las recomendaciones de prácticas recomendadas

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Ejemplo de configuración de Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Aplicar todas las recomendaciones de prácticas recomendadas y separar la caché obsoleta por tipo de caché

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Más información

Consulte los siguientes temas relacionados:

- [Caché de página de Redis](../../../configuration/cache/redis-pg-cache.md)
- [Usar Redis para el almacenamiento de sesión](../../../configuration/cache/redis-session.md)
- [Usar Valkey para la caché predeterminada](../../../configuration/cache/valkey-pg-cache.md)
- [Uso de Valkey para el almacenamiento de sesión](../../../configuration/cache/valkey-session.md)
