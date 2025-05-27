---
title: Prácticas recomendadas para la configuración del servicio Valkey
description: Aprenda a mejorar el rendimiento del almacenamiento en caché mediante la implementación de caché de Valkey ampliada para Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
source-git-commit: 107b5bb19c3375be64c216bd89feb8410e2fc2bd
workflow-type: tm+mt
source-wordcount: '682'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración del servicio Valkey

Adobe recomienda las siguientes prácticas recomendadas al configurar el servicio Valkey:

## Configuración de la caché de Valkey L2

Configure la caché de Valkey L2 estableciendo la variable de implementación `VALKEY_BACKEND` en el archivo de configuración `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Para obtener información sobre la configuración del entorno en la infraestructura en la nube, consulte [`VALKEY_BACKEND`](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) en la _Guía de Commerce en la infraestructura en la nube_.

Para instalaciones locales, consulte [Configurar el almacenamiento en caché de la página Valkey](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) en la _Guía de configuración_.

>[!NOTE]
>
>Compruebe que está utilizando la última versión del paquete `ece-tools`. Si no es así, [actualice a la versión más reciente](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). Puede comprobar la versión instalada en su entorno local mediante el comando CLI `composer show magento/ece-tools`.

### Tamaño de la memoria caché L2 (Adobe Commerce Cloud)

La caché L2 usa un [sistema de archivos temporal](https://en.wikipedia.org/wiki/Tmpfs) como mecanismo de almacenamiento. En comparación con los sistemas de base de datos de clave-valor especializados, un sistema de archivos temporal no tiene una política de expulsión de claves para controlar el uso de la memoria.

La falta de control de uso de memoria puede hacer que el uso de memoria caché L2 crezca con el tiempo al acumular la caché antigua.

Para evitar el agotamiento de la memoria de las implementaciones de caché L2, Adobe Commerce borra el almacenamiento cuando se alcanza un determinado umbral. El valor de umbral predeterminado es 95 %.

Es importante ajustar el uso máximo de memoria caché L2 en función de los requisitos del proyecto para el almacenamiento en caché. Utilice uno de los siguientes métodos para configurar el tamaño de la caché de memoria:

- Cree un vale de soporte técnico para solicitar cambios de tamaño del montaje `/dev/shm`.
- Ajuste la propiedad `cleanup_percentage` en el nivel de aplicación para limitar el porcentaje de relleno máximo del almacenamiento. La memoria libre restante puede ser utilizada por otros servicios.
Puede ajustar la configuración en la configuración de implementación en el grupo de configuración de caché `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>La opción de configuración `cleanup_percentage` se introdujo en Adobe Commerce 2.4.4.

El siguiente ejemplo muestra un(a) `CACHE_CONFIGURATION` en el archivo `.magento.env.yaml`:

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

Los requisitos de caché pueden variar en función de la configuración del proyecto y el código de terceros personalizado. El ámbito del tamaño de la memoria caché L2 permite que la caché L2 funcione sin visitas de umbral innecesarias.
Lo ideal es que el uso de memoria caché L2 se estabilice en un determinado nivel por debajo del umbral para evitar la limpieza frecuente del almacenamiento.

Puede comprobar el uso de la memoria de almacenamiento en caché L2 en cada nodo del clúster mediante el siguiente comando CLI y, a continuación, buscar la línea `/dev/shm`.
El uso puede variar entre distintos nodos, pero debe converger al mismo valor.

```bash
df -h
```

## Habilitar la conexión esclava de Valkey

Habilite una conexión esclava de Valkey en el archivo de configuración `.magento.env.yaml` para permitir que solo un nodo gestione el tráfico de lectura-escritura mientras que los demás nodos gestionan el tráfico de solo lectura.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Para obtener más información, consulte [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) en la _Guía de infraestructura de Commerce en la nube_.

Para las instalaciones locales de Adobe Commerce, configure la nueva implementación de caché de Valkey con los comandos `bin/magento:setup`. Para obtener más información, consulte [Usar Valkey para la caché predeterminada](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) en la _Guía de configuración_.

>[!WARNING]
>
>No configure _not_ una conexión esclava de Valkey para proyectos de infraestructura en la nube con una [arquitectura escalada/dividida](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Esto provoca errores de conexión de Redis. Para obtener más información, consulte las [Directrices de configuración de Redis](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) en la guía de _Commerce en infraestructura en la nube_.

## Claves de precarga

Para reutilizar datos entre páginas, enumere las claves para la carga previa en el archivo de configuración `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

Para instalaciones locales, consulte [Función de precarga de Valkey](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) en la _Guía de configuración_.

## Habilitar caché obsoleta

Reduzca los tiempos de espera de bloqueo y mejore el rendimiento, especialmente cuando se trata de numerosos bloques y claves de caché, mediante el uso de una caché obsoleta y la generación de una nueva caché en paralelo. Habilite la caché obsoleta y defina los tipos de caché en el archivo de configuración `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

>[!NOTE]
>
>En el ejemplo anterior, la caché de `full_page` no es relevante para Adobe Commerce en proyectos de infraestructura en la nube, ya que utilizan [Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly).

Para configurar instalaciones locales, consulte [Opciones de caché antiguas](../../../configuration/cache/level-two-cache.md#stale-cache-options) en la _Guía de configuración_.

Durante la implementación, debería ver las líneas siguientes en el [registro de compilación e implementación](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Compresión de caché

Si usa más de 6 GB de Valkey `maxmemory`, puede utilizar la compresión de caché para reducir el espacio consumido por las claves. Tenga en cuenta que existe un equilibrio entre el rendimiento del lado del cliente y el de Si tiene CPU de reserva, Adobe recomienda habilitarlas. Consulte [Usar Redis para el almacenamiento de sesión](../../../configuration/cache/redis-session.md) en la _Guía de configuración_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```

## Más información

- [Caché de página de Redis](../../../configuration/cache/redis-pg-cache.md)
- [Usar Redis para el almacenamiento de sesión](../../../configuration/cache/redis-session.md)
