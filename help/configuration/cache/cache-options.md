---
title: Opciones del servidor de caché y referencia de almacenamiento
description: Obtenga información acerca de las opciones de back-end de caché en Adobe Commerce, incluido el sistema de archivos, Redis, Valkey y el almacenamiento de bases de datos. Descubra enfoques heredados y modernos.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: d3c3e48c7627b932d1e46a7d2a99fa77b8b75b4c
workflow-type: tm+mt
source-wordcount: 331
ht-degree: 0%

---

# Opciones del servidor de caché y referencia de almacenamiento

{{cloud-cache-config}}

La aplicación de Commerce utiliza un front-end y un back-end de caché de bajo nivel para proporcionar acceso al almacenamiento en caché. Commerce admite varios back-ends y estrategias de almacenamiento en caché, cada uno adaptado a diferentes casos de uso. Esta página describe los backends disponibles y cómo difieren.

>[!NOTE]
>
>[Varnish](config-varnish.md) administra el almacenamiento en caché de página completa en el nivel HTTP y no utiliza el servidor de caché de nivel inferior.

## Opciones de caché back-end

La siguiente tabla resume las cachés backend disponibles:

| Servidor | Descripción | Guía de configuración |
| ------- | ----------- | ------------------- |
| Sistema de archivos | Predeterminado. Almacena datos de caché en archivos bajo `var/cache/`. No se requiere configuración. | N/D |
| [Redis](config-redis.md) | Almacén de datos en memoria para el almacenamiento en caché de alto rendimiento. | [Usar Redis para la caché predeterminada](redis-pg-cache.md) |
| [Valkey](config-valkey.md) | Alternativa de código abierto y compatible con Redis. | [Usar Valkey para la caché predeterminada](valkey-pg-cache.md) |
| [Base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Almacenamiento en caché respaldado por base de datos. | [Crear motores de caché personalizados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentación para desarrolladores de Adobe) |

>[!IMPORTANT]
>
>{{redis-cache-support}}

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
| Valkey | `valkey` |
| Sistema de archivos | `file` |

>[!NOTE]
>
>El nombre de tipo `redis` también se acepta, pero Redis no es un servicio de caché admitido oficialmente para Adobe Commerce 2.4.9 y versiones posteriores. Utilice `valkey` en su lugar.

**Ejemplo de configuración:**

```php?start_inline=1
'backend' => 'valkey',
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
