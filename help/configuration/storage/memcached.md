---
title: Usar memcached para el almacenamiento de sesión
description: Aprenda a configurar Adobe Commerce para que utilice memcached para el almacenamiento de sesiones en env.php y cuándo preferir Redis o Varnish para otras capas de almacenamiento en caché.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%
---
# Usar memcached para el almacenamiento de sesión

Memcached es un sistema de almacenamiento en caché de memoria distribuida de uso general. A menudo se utiliza para acelerar los sitios web dinámicos impulsados por bases de datos almacenando en caché datos y objetos en la RAM para reducir el número de veces que se debe leer una fuente de datos externa (como una base de datos o una API).

Memcached proporciona una tabla hash de gran tamaño que se puede distribuir entre varios equipos. Cuando la tabla está llena, las inserciones posteriores hacen que los datos más antiguos se purguen en el orden de uso menos reciente (LRU). El tamaño de esta tabla hash suele ser muy grande. (Source: [memcached.org](https://www.memcached.org/))

Commerce utiliza memcached para el almacenamiento de sesión, pero no para el almacenamiento de páginas en caché. Para el almacenamiento en caché de páginas, recomendamos [Redis](../cache/redis-pg-cache.md) o [Varnish](../cache/config-varnish.md).

**Para configurar Commerce para que use memcached**:

1. Abra `<your install dir>/app/etc/env.php` en un editor de texto.
1. Busque lo siguiente:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Cámbielo como se indica a continuación:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached tiene parámetros de inicio opcionales que están fuera del alcance de esta guía. Puede encontrar más información sobre ellos en la documentación de [memcached](https://www.php.net/manual/en/memcached.sessions.php), el código fuente y los registros de cambios.

1. Continúe con la siguiente sección.

**Para comprobar que memcached funciona con Commerce**:

1. Elimine el contenido de los siguientes directorios del directorio de instalación de Commerce:

   ```shell
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Vaya a cualquier página de la tienda.

1. Inicie sesión en Admin y navegue a varias páginas.

   Si no se muestran errores, ¡enhorabuena! memcached está funcionando. Opcionalmente, puede consultar el almacenamiento en caché de memes como se describe en el siguiente paso.

   Si se muestran errores (como un HTTP 500 (Error interno del servidor)), habilite el modo de desarrollador y diagnostique el problema. Asegúrese de que memcached se esté ejecutando, que esté configurada correctamente y que `env.php` no tenga errores de sintaxis.

1. (Opcional.) Utilice Telnet para ver el almacenamiento en memoria caché.

   ```shell
   telnet <memcached host or ip> <memcached port>
   ```

   ```shell
   stats items
   ```

   Los resultados son similares a los siguientes:

   ```text
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
