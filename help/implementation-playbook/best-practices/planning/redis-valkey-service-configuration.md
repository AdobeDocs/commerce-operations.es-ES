---
title: Prácticas recomendadas para la configuración de los servicios Valkey y Redis
description: Obtenga información sobre cómo configurar el almacenamiento en caché de Redis y Valkey para Adobe Commerce en la nube, incluidas las conexiones de réplica, la caché L2, la caché antigua y el almacenamiento de sesión.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce en la nube" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos de Adobe Commerce en la nube."
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
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
source-git-commit: 55f36b56b5d719ace064eccf42675cd8f9b7683b
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Prácticas recomendadas para la configuración del servicio Valkey y Redis

Utilice estas recomendaciones cuando configure Redis o Valkey para la caché de aplicaciones de Adobe Commerce, el almacenamiento de sesión y la caché L2 para implementaciones de Adobe Commerce en la nube.

Para la configuración de caché local de Adobe Commerce, consulte [Configuración de caché L2 para la optimización del rendimiento](/help/configuration/cache/level-two-cache.md).

>[!NOTE]
>
>Este tema cubre la caché de la aplicación Commerce y los back-ends de sesión. El almacenamiento en caché de página completa de HTTP, como Fastly o Varnish, es una capa de almacenamiento en caché independiente y se configura de forma independiente. Los cambios en el back-end de la caché de la aplicación no reemplazan ni configuran la caché de página completa HTTP.

Estas recomendaciones abarcan lo siguiente:

- Seleccione un servicio de caché admitido
- Habilitar conexión de réplica
- Instancias de caché y sesión independientes
- Configuración de compresión de caché
- Habilitar la liberación asincrónica
- Habilitar E/S multiproceso
- Aumentar los tiempos de espera y reintentos del cliente
- Configurar la caché L2, incluidas las claves de precarga, la caché obsoleta y la caché L2 [!DNL Symfony]
- Revisar ejemplos de configuración

## Seleccione un servicio de caché admitido

| Versión de Adobe Commerce | Servicio de caché recomendado | Implementación de caché L2 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8 y anteriores, cuando son compatibles con la versión exacta de | Redis o Valkey | RemoteSynchronizedCache |
| 2.4.9 y posterior | Valkey | symfony_l2 |

Redis no es compatible con la configuración de caché en Adobe Commerce 2.4.9 y en las versiones de parches, donde los requisitos del sistema especifican Valkey en su lugar. Compruebe siempre la versión exacta de Commerce, el nivel de parche y la versión del servicio en las [opciones de servidor de caché y referencia de almacenamiento](/help/configuration/cache/cache-options.md) y en los [requisitos del sistema](/help/installation/system-requirements.md).

>[!NOTE]
>
>Compruebe que está utilizando la última versión del paquete `ece-tools`. Si no es así, [actualice a la versión más reciente](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Puede comprobar la versión instalada en su entorno local mediante el comando CLI `composer show magento/ece-tools`.

## Habilitar conexión de réplica

Habilite la conexión de réplica en el archivo `.magento.env.yaml`. Este cambio permite a Adobe Commerce utilizar una conexión de caché adicional para las lecturas mientras sigue utilizando el extremo principal para las escrituras. Esta configuración puede reducir la carga de lectura en el servicio de caché principal y distribuir el tráfico de lectura de forma más eficaz.

>[!NOTE]
>
>La disponibilidad de una conexión de réplica depende de la topología del proyecto (por ejemplo, de un solo nodo frente a una arquitectura dividida o HA) y de la versión `ece-tools`. Antes de confiar en esta configuración, confirme que existe una relación de réplica para su servicio ejecutando `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp` y comprobando si hay una entrada `USE_SLAVE_CONNECTION`. Para confirmar si la topología aprovisiona un extremo de réplica, actualice `ece-tools` y vuelva a implementar, o póngase en contacto con el soporte técnico de Adobe Commerce si no hay ninguna entrada `USE_SLAVE_CONNECTION`.
>
>Para `symfony_l2`, la compatibilidad con la conexión de réplica se entrega a través de una actualización de `ece-tools` y Cloud Patches. No se requiere ninguna configuración de caché adicional más allá de cambiar `VALKEY_USE_SLAVE_CONNECTION: true`. Actualice a la última versión de `ece-tools` para recibir la corrección.

>[!BEGINTABS]

>[!TAB Configuración de Valkey]

Para Valkey, utilice:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Para obtener detalles de configuración de la variable de entorno, consulte [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) en la _Guía de infraestructura de Commerce en la nube_.

>[!TAB Configuración de Redis]

Para Redis, utilice:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Para obtener detalles sobre la configuración de la variable de entorno, consulte [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) en la _Guía de infraestructura de Commerce en la nube_.

>[!ENDTABS]

## Instancias de caché y sesión independientes

La configuración de caché y sesión es independiente. `SESSION_CONFIGURATION` no afecta al comportamiento de la caché, independientemente del backend de la caché o de la implementación de caché L2 que utilice. La separación de la caché de las sesiones permite administrarlas de forma independiente. Reduce la contención entre la caché y el tráfico de sesión, evita que la presión relacionada con la caché afecte a las sesiones y permite que cada instancia de Redis o Valkey tenga un tamaño y un ajuste para su propia carga de trabajo.

>[!IMPORTANT]
>
>El aprovisionamiento de una instancia de sesión dedicada en Producción y ensayo no es autoservicio. Se requiere enviar un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) con los archivos `.magento/services.yaml` y `.magento.app.yaml` actualizados, tal como se describe en el paso 3 a continuación.

Para aprovisionar una instancia dedicada para las sesiones, siga los pasos a continuación:

>[!BEGINTABS]

>[!TAB Valkey]

1. Actualice el archivo de configuración `.magento/services.yaml` y reemplace `<version>` por las versiones de servicio que está usando. Consulte [Requisitos del sistema](/help/installation/system-requirements.md) para ver las versiones de servicio compatibles por versión.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Enviar un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Incluir los archivos de configuración actualizados de `.magento/services.yaml` y `.magento.app.yaml`.

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

1. Elimine sesiones de la [base de datos predeterminada](/help/configuration/cache/redis-pg-cache.md) (`db 0`) en la instancia de caché de Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis]

1. Actualice el archivo de configuración `.magento/services.yaml` y reemplace `<version>` por las versiones de servicio que está usando.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Enviar un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Incluir los archivos de configuración actualizados de `.magento/services.yaml` y `.magento.app.yaml`.

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

1. Quitar sesiones de la [base de datos predeterminada](/help/configuration/cache/redis-pg-cache.md) (`db 0`) en la instancia de caché de Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compresión de caché

Si usa más de 6 GB de Redis o Valkey `maxmemory`, puede habilitar la compresión de caché para reducir el espacio consumido por las claves. Tenga en cuenta que esta configuración cambia el rendimiento del lado del cliente por ahorros de memoria. Si tiene capacidad de CPU disponible, considere la posibilidad de habilitarla. Consulte [Usar Redis para almacenamiento de sesión](/help/configuration/cache/redis-session.md) o [Usar Valkey para almacenamiento de sesión](/help/configuration/cache/valkey-session.md) en la _Guía de configuración_.

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

Para habilitar `lazyfree` en la infraestructura de nube de Adobe Commerce, envíe un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) en el que se solicite que se aplique la siguiente configuración de Redis o Valkey a sus entornos:

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

Para habilitar el subprocesamiento de E/S de Redis en la infraestructura de nube de Adobe Commerce, envíe un [ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) solicitando la configuración de subprocesamiento de E/S a continuación. Esta configuración puede mejorar el rendimiento descargando lecturas de socket, escrituras y análisis de comandos desde el hilo principal, a costa de un mayor uso de CPU. Valide en y supervise sus hosts.

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

## Configuración de la caché L2

Configure la caché L2 estableciendo la variable de implementación `VALKEY_BACKEND` o `REDIS_BACKEND` en el archivo de configuración `.magento.env.yaml`.

Hay dos implementaciones de caché L2 disponibles para Adobe Commerce en la infraestructura en la nube.

- La implementación heredada usa `RemoteSynchronizedCache` con `Cm_Cache_Backend_File` para el almacenamiento local
- La implementación moderna usa `symfony_l2` con compatibilidad con PSR-6 y rendimiento mejorado. La implementación moderna solo admite Valkey.

| Versión de Commerce | RemoteSynchronizedCache con Valkey | Configuración recomendada |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8 y anteriores<br>(si se admite Valkey) | Ruta L2 heredada admitida | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9 y posterior | No compatible | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>La caché de Redis no es compatible con Adobe Commerce 2.4.9 ni con versiones de parches posteriores a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 y 2.4.8-p4. Utilice Valkey para la configuración de caché donde no se admita Redis. Consulte [Requisitos del sistema](/help/installation/system-requirements.md) para ver los servicios de caché admitidos por versión.

>[!BEGINTABS]

>[!TAB Configuración de Valkey]

En Commerce 2.4.8 y versiones anteriores compatibles con Valkey, utilice esta configuración:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

En Commerce 2.4.9 y versiones posteriores, utilice la siguiente configuración con la implementación de L2 [!DNL Symfony]:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Configuración de Redis]

En la versión 2.4.8 y versiones anteriores de Commerce compatibles con Redis, utilice:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obtener detalles de configuración del entorno, consulte [`REDIS_BACKEND`](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) en la _Guía de infraestructura de Commerce en la nube_.

>[!ENDTABS]

### Migrar a Valkey con caché L2 de [!DNL Symfony]

Si está migrando un proyecto existente de Adobe Commerce en la nube de `RemoteSynchronizedCache` (Redis o Valkey) a `symfony_l2`, revise lo siguiente antes de actualizar `.magento.env.yaml`.

- **Cambiar la variable de implementación es suficiente para habilitar `symfony_l2`.** Al establecer `VALKEY_BACKEND: symfony_l2` solo, se genera automáticamente la configuración de caché L2 completa. No necesita volver a crear manualmente la estructura de `backend_options` que utilizó la configuración anterior de `RemoteSynchronizedCache`. Consulte [Configurar [!DNL Symfony] caché L2](#configure-symfony-l2-cache).

- **Quitar `preload_keys` de la configuración existente.** Si la configuración de `RemoteSynchronizedCache` incluye `preload_keys` en `CACHE_CONFIGURATION`, elimínelo como parte de la migración. Consulte [Claves de precarga](#preload-keys) para obtener más información.

- **El comportamiento de la caché obsoleta cambia automáticamente.** En `symfony_l2`, `ece-tools` habilita automáticamente la caché obsoleta para los tipos de caché comunes (como `layout`, `block_html`, `full_page` y `translate`) sin requerir la configuración de front-end manual que `RemoteSynchronizedCache` necesitaba. Si anteriormente configuró manualmente la caché obsoleta y desea conservar el comportamiento anterior exacto, revise [Habilitar la caché obsoleta](#enable-stale-cache) antes de migrar.

- **La compresión requiere un indicador explícito.** Si personaliza la compresión de `symfony_l2` mediante `CACHE_CONFIGURATION`, la configuración de `compression_lib` por sí sola no habilita la compresión: `compress_data` también debe estar establecida. Consulte [Compresión de caché](#cache-compression).

- **Redis no es un servidor remoto compatible para `symfony_l2`.** Migre a Valkey como parte de este cambio. Consulte [Configurar el servicio Valkey](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/valkey).

- La configuración de **sesión no se ve afectada por esta migración.** `SESSION_CONFIGURATION` es independiente del servidor de caché y no necesita cambiarse al pasar a `symfony_l2`. Consulte [Separar caché e instancias de sesión](#separate-cache-and-session-instances).

>[!IMPORTANT]
>
>No configure `symfony_l2` manualmente en `app/etc/env.php`. Configúrelo a través de `.magento.env.yaml`, de modo que `ece-tools` aplique y mantenga la configuración durante la implementación. Consulte [Configurar [!DNL Symfony] caché L2](#configure-symfony-l2-cache).

### Precargar claves

Las claves de precarga se pueden aplicar a una configuración de `symfony_l2` si usa la ubicación correcta (en `backend_options` o `remote_backend_options`). Sin embargo, Adobe no recomienda utilizar claves de precarga con `symfony_l2`. La implementación de precarga de `symfony_l2` recupera las claves de una en una, de modo que no reduce los viajes de ida y vuelta como lo hace para `RemoteSynchronizedCache` y puede aumentar la carga en Valkey sin una ventaja de rendimiento.

La función de precarga permite proporcionar una lista de las claves utilizadas frecuentemente que Magento recupera en una sola canalización en el primer acceso durante una solicitud. A continuación, Magento mantiene los valores recuperados en la memoria PHP durante el resto de esa solicitud, lo que reduce los viajes de ida y vuelta repetidos a Redis o Valkey y puede mejorar el rendimiento de arranque de la solicitud para esas claves.

Puede identificar las claves utilizadas con frecuencia controlando los comandos activos en Redis o Valkey:

Las claves de precarga están configuradas en el archivo de configuración `.magento.env.yaml`. Este ejemplo muestra la configuración de Adobe Commerce 2.4.8 y versiones anteriores compatibles con `RemoteSynchronizedCache`.

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

Después de 10 segundos, presione **Ctrl+C**. A continuación, ejecute el siguiente comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

Este registro enumera las claves que puede cargar previamente. Para ver el contenido de una clave, ejecute el siguiente comando:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### Habilitar caché obsoleta

La caché obsoleta es una característica de caché L2 que permite a Adobe Commerce servir un valor de caché local existente de `/dev/shm` mientras otra solicitud ya está regenerando la misma entrada. Esto evita que las solicitudes simultáneas esperen. Esto reduce las estampidas de caché y la contención de bloqueos durante la regeneración de entradas de caché costosas.

Para Adobe Commerce 2.4.9 y versiones posteriores, establezca `VALKEY_BACKEND: symfony_l2` en el archivo `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools` genera automáticamente un front-end `default` y `stale_cache_enabled`, y asigna los siguientes tipos de caché al front-end habilitado para obsoleto: `layout`, `block_html`, `reflection`, `config_integration`, `config_integration_api`, `full_page` y `translate`. No se requiere ninguna configuración manual de `use_stale_cache` o de front-end para estos tipos. Esta asignación automática es en sí misma un ejemplo de habilitación selectiva de caché obsoleta. Solo los tipos de caché específicos utilizan el front-end habilitado para obsoletos, no todos ellos. Para personalizar qué tipos se asignan a `stale_cache_enabled` o para agregar tipos más allá de los valores predeterminados, vea [Personalizar la [!DNL Symfony] configuración de la caché L2](#customize-the-symfony-l2-cache-configuration).

>[!NOTE]
>
>El tipo de caché `full_page` no es relevante para Adobe Commerce en proyectos de infraestructura en la nube porque utiliza Fastly para el almacenamiento en caché de página completa. Los ejemplos de configuración manual de esta sección omiten `full_page` por ese motivo, aunque `ece-tools` lo incluya en la asignación predeterminada `symfony_l2`.

La siguiente configuración heredada se aplica a Adobe Commerce 2.4.8 y versiones anteriores, que utilizan `RemoteSynchronizedCache` y requieren una caché anticuada manual y una configuración de front-end. La misma recomendación selectiva sobre global se aplica aquí.

#### Cómo funciona el servidor remotoSynchronizedCache heredado

Con `RemoteSynchronizedCache`, Magento mantiene dos copias de cada entrada de caché: una copia local en `/dev/shm` y una copia remota en Redis o Valkey. Cuando la copia remota no está disponible y ya existe un bloqueo de regeneración para esa clave, las solicitudes simultáneas pueden recibir el valor local anterior en lugar de esperar hasta que se escriba el nuevo valor.

Para habilitar la caché obsoleta para 2.4.8 y versiones anteriores, configúrela en el archivo `.magento.env.yaml`.

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

>[!WARNING]
>
>La configuración anterior habilita la caché obsoleta en el front-end de caché de `default`, que aplica el comportamiento de caché obsoleta a todas las entradas de caché que utilizan ese front-end. Los tipos de caché principal de Magento funcionan según lo esperado con esta configuración. Sin embargo, si el proyecto incluye código personalizado o extensiones que escriben en la caché a través de la API genérica `\Magento\Framework\App\Cache` (por ejemplo `$this->cache->save()`) sin un front-end de caché dedicado, esas entradas también pueden proporcionar valores antiguos durante la regeneración.
>
>
>Si esto resulta en un comportamiento inesperado en las personalizaciones, deje deshabilitada la caché obsoleta en el front-end `default` y actívela solo para los tipos de caché seleccionados, como se muestra a continuación.

#### Habilitar la caché obsoleta por tipo de caché individualmente (heredado)

Puede habilitar la caché obsoleta solamente para los tipos de caché seleccionados definiendo un front-end de caché dedicado en `.magento.env.yaml` y asignando los tipos de caché seleccionados a él. Este método manual se aplica al back-end `RemoteSynchronizedCache` heredado; `symfony_l2` realiza esta asignación automáticamente, tal como se ha descrito anteriormente.

Para funcionar correctamente, el front-end personalizado debe definirse como un front-end completo en `CACHE_CONFIGURATION.frontend`. No basta con definir solo `use_stale_cache: true` para un nuevo nombre de front-end.

**Configuraciones de ejemplo**

En el caso de Redis en las versiones 2.4.8 y anteriores, la siguiente configuración habilita la caché obsoleta para los tipos de caché `layout`, `reflection`, `config_integration`, `config_integration_api` y `translate`, mientras que deja otros tipos de caché con el front-end predeterminado deshabilitado:

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

>[!NOTE]
>
>Si el front-end de origen está configurado con opciones de back-end adicionales, copie esas opciones en `stale_cache_enabled` para que el nuevo front-end mantenga el mismo comportamiento.

### Configurar la caché L2 de [!DNL Symfony]

Adobe Commerce 2.4.9 y versiones posteriores admiten el back-end de caché `symfony_l2`. El servidor `symfony_l2` es la implementación de caché que Adobe Commerce usa para administrar el comportamiento de la caché L1 y L2. **No reemplaza a Redis ni a Valkey como servicio de caché remota.**

>[!IMPORTANT]
>
>Configure `symfony_l2` mediante la variable de implementación `.magento.env.yaml`, de modo que `ece-tools` aplique y mantenga la configuración durante la implementación. No configure `symfony_l2` manualmente en `app/etc/env.php`, ya que la implementación puede sobrescribir los cambios manuales de `env.php`. Si `ece-tools` no aplica `symfony_l2`, Commerce puede volver a la caché basada en archivos, lo que puede aumentar la E/S del disco, agregar sobrecarga de replicación del sistema de archivos en entornos de varios nodos y degradar el rendimiento.

Para usar la caché de `symfony_l2` en Adobe Commerce 2.4.9, complete estos pasos:

- Asegúrese de que el proyecto de nube esté usando el paquete v2002.2.12[&#128279;](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) de `ece-tools` o posterior.

- Establezca la variable de implementación en el archivo `.magento.env.yaml`: `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

Al establecer la variable de implementación `VALKEY_BACKEND` en `symfony_l2`, se genera automáticamente la configuración de caché L2 completa a partir de los detalles de conexión del servicio Valkey, incluidos los front-end `default` y `stale_cache_enabled`, con los tipos de caché comunes ya asignados. La definición de `CACHE_CONFIGURATION` es opcional y necesaria solamente si desea personalizar opciones específicas del servidor.

>[!NOTE]
>
>El parche ACP2E-5132 para Adobe Commerce 2.4.9 mejora el rendimiento y la fiabilidad de la caché de nivel 2 de [!DNL Symfony] al optimizar el almacenamiento de etiquetas, agregar un bloqueo de regeneración de caché obsoleto y solucionar problemas con pertenencias de etiquetas obsoletas, escrituras remotas redundantes y desalojo basado en el tamaño L1 (`cleanup_percentage`). Esto reduce la E/S del disco y la carga back-end al tiempo que mejora la coherencia de la caché. Consulte [Rendimiento y fiabilidad mejorados de la caché Symfony L2](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability) en la _Guía de configuración de Adobe Commerce_.
>
>El parche se incluye en [Parches de nube para el paquete de Commerce](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches) (una dependencia de `ece-tools`) y se aplica automáticamente durante la implementación al actualizar a la última versión de `ece-tools`. Actualice a la última versión de `ece-tools` para recibir el parche.

#### Personalizar la configuración de caché L2 de [!DNL Symfony]

`ece-tools` deriva automáticamente los detalles de conexión de Valkey (`server`, `port`, `database`, `serializer`, `compression_lib`, `persistent_id`) para los front-end `default` y `stale_cache_enabled`. Para personalizar otras opciones de servidor, como el directorio de caché local, defina `CACHE_CONFIGURATION` con `_merge: true` junto con `VALKEY_BACKEND: symfony_l2`. Los valores que defina aquí anulan los valores predeterminados generados automáticamente; cualquier opción que omita seguirá utilizando los valores que `ece-tools` deriva automáticamente.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>Al definir `CACHE_CONFIGURATION` para `symfony_l2`, solo invalide `server` o `port` si señala intencionalmente a un extremo de caché que no sea el servicio Valkey del proyecto. El paquete `ece-tools` deriva estos valores automáticamente de su relación de servicio de Valkey.
>
>Si reemplaza `server`, su valor debe ser `localhost` al conectarse al servicio Valkey del proyecto. Si se proporciona un valor `server` o `port` incorrecto, la implementación fallará y se producirá un error de conexión de caché.

### Tamaño de la memoria caché L2 para Adobe Commerce Cloud

La caché L2 usa un [sistema de archivos temporal](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) como mecanismo de almacenamiento. A diferencia de los almacenes de valor clave especializados, los tmpfs no tienen una política de desalojo de claves, por lo que el uso de la memoria puede crecer sin límites. Para evitar el agotamiento, Adobe Commerce borra automáticamente el almacenamiento L2 cuando el uso alcanza un umbral configurable (95 % de forma predeterminada). Puede controlar el consumo de memoria solicitando un montaje de `/dev/shm` mayor o reduciendo el umbral de limpieza.

Ajuste el uso máximo de memoria caché L2 en función de los requisitos del proyecto. Utilice uno de los siguientes métodos:

- Para ajustar el tamaño de montaje de `/dev/shm`, cree un vale de soporte. En este caso, Adobe recomienda establecer el tamaño de montaje de `/dev/shm` en 15 GB.
- Ajuste la propiedad `cleanup_percentage` en el nivel de aplicación para limitar el uso del almacenamiento y la memoria libre disponible para otros servicios.
Puede ajustar la configuración en la configuración de implementación en el grupo de configuración de caché `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>La opción configurable `cleanup_percentage` se introdujo en Adobe Commerce 2.4.4.

Los siguientes ejemplos muestran el código de configuración en el archivo `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Configuración de Valkey]

Para Commerce 2.4.9 y versiones posteriores, utilice la siguiente configuración para establecer el umbral de limpieza en 90 %:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Configuración de Redis]

Para Commerce 2.4.8 y versiones anteriores, utilice la siguiente configuración para establecer el umbral de limpieza en 90 %:

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

>[!ENDTABS]

Los requisitos de caché varían en función de la configuración del proyecto y del código de terceros personalizado. Tamaño de la memoria caché L2 para que la caché pueda funcionar sin visitas de umbral frecuentes.

Lo ideal es que el uso de la memoria caché L2 se estabilice por debajo del umbral para evitar la limpieza frecuente del almacenamiento.

Puede comprobar el uso de la memoria de almacenamiento en caché L2 en cada nodo del clúster ejecutando el siguiente comando CLI y revisando la línea `/dev/shm`.

```shell
df -h /dev/shm
```

El uso varía según los nodos, pero converge a un valor similar.

## Ejemplos de configuración

Utilice los siguientes ejemplos como punto de partida para las configuraciones del servicio Redis o Valkey.


### Aplicar todas las recomendaciones de prácticas recomendadas

>[!BEGINTABS]

>[!TAB Ejemplo de configuración de Valkey]

Para `VALKEY_BACKEND: symfony_l2`, permita que `ece-tools` genere los front-end `default` y `stale_cache_enabled` y sus asignaciones de tipo de caché. No configure `use_stale_cache` en el front-end `default` amplio. El bloque `CACHE_CONFIGURATION` a continuación contiene solamente invalidaciones explícitas de opciones de backend.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
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

>[!TAB Ejemplo de configuración de Redis]

Utilice la siguiente configuración para Redis en Adobe Commerce 2.4.8 y versiones anteriores:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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

>[!ENDTABS]

### Separar caché obsoleta por tipo de caché

>[!BEGINTABS]

>[!TAB Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
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
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
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

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
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

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [Configurar el servicio Valkey](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [Configurar el servicio Redis](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [Implementar variables](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
