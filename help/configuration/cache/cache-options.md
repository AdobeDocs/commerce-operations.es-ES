---
title: Opciones del servidor de caché y referencia de almacenamiento
description: Obtenga información acerca de las opciones de back-end de caché en Adobe Commerce, incluido el sistema de archivos, Redis, Valkey y el almacenamiento de bases de datos. Descubra enfoques heredados y modernos.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Opciones del servidor de caché y referencia de almacenamiento

La aplicación de Commerce utiliza un front-end y un back-end de caché de bajo nivel para proporcionar acceso al almacenamiento en caché. Commerce admite varios back-ends y estrategias de almacenamiento en caché, cada uno adaptado a diferentes casos de uso. Esta página describe los backends disponibles y cómo difieren.

>[!NOTE]
>
>Para obtener más información sobre la configuración de la caché de front-end, consulte [Configurar front-end de caché](cache-types.md).

## Opciones de caché back-end

La siguiente tabla resume las cachés backend disponibles:

| Servidor | Descripción | Guía de configuración |
| ------- | ----------- | ------------------- |
| Sistema de archivos | Predeterminado. Almacena datos de caché en archivos bajo `var/cache/`. No se requiere configuración. | N/D |
| [Redis](config-redis.md) | Almacén de datos en memoria para el almacenamiento en caché de alto rendimiento. | [Usar Redis para la caché predeterminada](redis-pg-cache.md) |
| [Valkey](config-valkey.md) | Alternativa de código abierto y compatible con Redis. | [Usar Valkey para la caché predeterminada](valkey-pg-cache.md) |
| [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Almacenamiento en caché respaldado por base de datos. | [Crear motores de caché personalizados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentación para desarrolladores de Adobe) |

>[!NOTE]
>
>[Varnish](config-varnish.md) administra el almacenamiento en caché de página completa en el nivel HTTP y no utiliza el servidor de caché de nivel inferior.

## Enfoques de implementación

Commerce admite dos enfoques de implementación back-end. El método que elija dependerá de la versión de Commerce:

>[!BEGINTABS]

>[!TAB Caché heredada basada en Zend (2.4.8 y versiones anteriores)]

Utiliza nombres de clase completos para la configuración del servidor:

| Servidor | Nombre de clase |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

Son compatibles con la interfaz `Zend_Cache_Backend`.

**Ejemplo de configuración:**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB Caché Symfony moderna (2.4.9 y posterior, recomendada)]

>[!TIP]
>
>La implementación moderna de Symfony Cache proporciona un mejor rendimiento a través del cumplimiento de PSR-6, serialización Igbinary, compresión gzip, scripts Lua y conexiones persistentes.

Utiliza nombres de tipo de servidor simplificado:

| Servidor | Escriba el nombre |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| Sistema de archivos | `file` |

**Ejemplo de configuración:**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

Para ver las opciones de configuración completas, consulte:

- [Usar Redis para la caché predeterminada](redis-pg-cache.md)
- [Usar Valkey para la caché predeterminada](valkey-pg-cache.md)
- [Configuración de caché L2](level-two-cache.md)

Consulte la [documentación de Laminas](https://docs.laminas.dev/) para ver las opciones heredadas basadas en Zend.
