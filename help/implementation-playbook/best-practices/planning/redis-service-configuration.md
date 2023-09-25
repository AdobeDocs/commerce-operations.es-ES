---
title: Prácticas recomendadas para la configuración del servicio Redis
description: Obtenga información sobre cómo mejorar el rendimiento del almacenamiento en caché mediante la implementación de caché de Redis extendida para Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 156e6412b9f94b74bad040b698f466808b0360e3
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración del servicio Redis

- Configurar la caché de Redis L2
- Activar conexión esclava de Redis
- Claves de precarga
- Habilitar caché obsoleta
- Separe la caché de Redis de la sesión de Redis
- Comprima la caché de Redis y utilice `gzip` para una mayor compresión

## Configurar la caché de Redis L2

Configure la caché de Redis L2 configurando el `REDIS_BACKEND` variable de implementación en `.magento.env.yaml` archivo de configuración.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para ver la configuración del entorno en la infraestructura de Cloud, consulte la [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) en el _Guía de Commerce en la infraestructura de Cloud_.

Para instalaciones locales, consulte [Configurar el almacenamiento en caché de páginas Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) en el _Guía de configuración_.

>[!NOTE]
>
>Compruebe que está utilizando la versión más reciente de `ece-tools` paquete. Si no es así, [actualizar a la versión más reciente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Puede comprobar la versión instalada en el entorno local mediante el complemento `composer show magento/ece-tools` Comando CLI.

## Activar conexión esclava de Redis

Habilite una conexión esclava de Redis en `.magento.env.yaml` archivo de configuración para permitir que solo un nodo gestione el tráfico de lectura-escritura, mientras que los demás nodos gestionan el tráfico de solo lectura.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Consulte [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) en el _Guía de Commerce en la infraestructura de Cloud_.

Para las instalaciones locales de Adobe Commerce, configure la nueva implementación de caché de Redis con el `bin/magento:setup` comandos. Consulte [Usar Redis para la caché predeterminada](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) en el _Guía de configuración_.

>[!WARNING]
>
>Hacer _no_ configurar una conexión esclava de Redis para proyectos de infraestructura en la nube con una [arquitectura escalada/dividida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Esto provoca errores de conexión de Redis. Consulte [Guía de configuración de Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) en el _Commerce en infraestructura en la nube_ guía.

## Claves de precarga

Para reutilizar datos entre páginas, enumere las claves de la precarga en la `.magento.env.yaml` archivo de configuración.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Para instalaciones locales, consulte [Función de precarga Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) en el _Guía de configuración_.

## Habilitar caché obsoleta

Reduzca los tiempos de espera de bloqueo y mejore el rendimiento, especialmente cuando se trata de numerosos bloques y claves de caché, mediante el uso de una caché obsoleta y la generación de una nueva caché en paralelo. Habilite la caché anticuada y defina los tipos de caché en la `.magento.env.yaml` archivo de configuración:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

Para configurar instalaciones locales, consulte [Opciones de caché antiguas](../../../configuration/cache/level-two-cache.md#stale-cache-options) en el _Guía de configuración_.

## Instancias de sesión y caché de Redis independientes

Separar la caché de Redis de la sesión de Redis le permite administrar la caché y las sesiones de forma independiente. Evita que los problemas de caché afecten a las sesiones, lo que podría afectar a los ingresos. Cada instancia de Redis se ejecuta en su propio núcleo, lo que mejora el rendimiento.

1. Actualice el `.magento/services.yaml` archivo de configuración.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. Actualice el `.magento.app.yaml` archivo de configuración.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Enviar un [ticket de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para solicitar el aprovisionamiento de una nueva instancia de Redis dedicada a sesiones en entornos de Producción y Ensayo. Incluir el actualizado `.magento/services.yaml` y `.magento.app.yaml` archivos de configuración. Esto no provocará ningún tiempo de inactividad, pero requiere una implementación para activar el nuevo servicio.

1. Compruebe que la nueva instancia se esté ejecutando y anote el número de puerto.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Agregue el número de puerto al `.magento.env.yaml` archivo de configuración.

   >[!NOTE]
   >`disable_locking` se debe establecer en `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Eliminación de sesiones de [base de datos predeterminada](../../../configuration/cache/redis-pg-cache.md) (`db 0`) en la instancia de caché de Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante la implementación, debería ver las siguientes líneas en la [registro de generación e implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Compresión de caché

Si utiliza más de 6 GB de Redis `maxmemory`Además, puede utilizar la compresión de caché para reducir el espacio consumido por las claves. Tenga en cuenta que existe un equilibrio entre el rendimiento del lado del cliente y el de Si tiene CPU de reserva, actívela. Consulte [Usar Redis para el almacenamiento de sesión](../../../configuration/cache/redis-session.md) en el _Guía de configuración_.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Información adicional

- [Caché de página de Redis](../../../configuration/cache/redis-pg-cache.md)
- [Usar Redis para el almacenamiento de sesión](../../../configuration/cache/redis-session.md)
