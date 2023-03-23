---
title: Prácticas recomendadas para la configuración del servicio Redis
description: Aprenda a mejorar el rendimiento del almacenamiento en caché mediante la implementación de caché de Redis ampliada para Adobe Commerce.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 92faa85b51a1fd5314a5906e8650b03723118ce1
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración del servicio Redis

- Utilice la implementación de caché de Redis extendida, que incluye las siguientes optimizaciones para minimizar el número de consultas de Redis que se realizan en cada solicitud de Adobe Commerce:
   - Reduce el tamaño de las transferencias de datos de red entre Redis y Adobe Commerce
   - Reduce el consumo de Redis de los ciclos de CPU al mejorar la capacidad del adaptador para determinar automáticamente lo que debe cargarse
   - Reduce las condiciones de carrera en las operaciones de escritura de Redis
- Separe la caché de Redis de la sesión de Redis
- Comprima la caché de Redis y utilice `gzip` para mejorar el rendimiento

## Implementación de caché de Redis extendida

Actualice la configuración para utilizar la implementación de caché de Redis extendida `\Magento\Framework\Cache\Backend\Redis`.

### Configuración de implementaciones en la nube

Configure la caché mejorada de Redis estableciendo la variable `REDIS_BACKEND` variable de implementación en la variable `.magento.env.yaml` archivo de configuración.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Para obtener más información, consulte la [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) descripción de la variable _Guía de Commerce on Cloud Infrastructure_.

>[!NOTE]
>
> Marque la `ece-tools` versión instalada en el entorno local desde la línea de comandos utilizando la variable `composer show magento/ece-tools` comando. Si es necesario, [actualizar a la versión más reciente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Do _not_ configurar una conexión esclava de Redis para proyectos de infraestructura en la nube con un [arquitectura escalada](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Esto provoca errores de conexión de Redis. Consulte [las directrices de configuración de Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) en el _Comercio en infraestructura de nube_ guía.

### Configuración de implementaciones locales

Para implementaciones locales de Adobe Commerce, configure la nueva implementación de caché de Redis mediante el `bin/magento:setup` comandos. Para obtener instrucciones, consulte [Usar Redis para la caché predeterminada](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Separar la caché y las instancias de sesión

La separación de la caché de Redis de la sesión de Redis le permite administrar la caché y las sesiones de forma independiente para evitar que los problemas de la caché afecten a las sesiones.

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

1. Envíe un [ticket de asistencia de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para cambiar la configuración del servicio Redis en los entornos de producción y ensayo Pro. Incluir la `.magento/services.yaml` y `.magento.app.yaml` archivos de configuración.

1. Compruebe que la nueva instancia se esté ejecutando y anote el número de puerto.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Agregue el número de puerto al `.magento.env.yaml` archivo de configuración.

   >[!NOTE]
   >`disable_locking` debe estar configurado como `1`.

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

1. Elimine sesiones de la función [base de datos predeterminada](../../../configuration/cache/redis-pg-cache.md) (`db 0`) en la instancia de caché de Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante la implementación, debería ver las siguientes líneas en la sección [registro de compilación e implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

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

Utilice la compresión de caché, pero tenga en cuenta que existe un equilibrio con el rendimiento del lado del cliente. Si tiene CPUs de reserva, actívelo. Consulte [Usar Redis para almacenamiento de sesión](../../../configuration/cache/redis-session.md).

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

- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)
- [Usar Redis para almacenamiento de sesión](../../../configuration/cache/redis-session.md)
