---
title: Uso almacenado en la memoria caché para el almacenamiento de sesión
description: Obtenga más información sobre el uso de memcached para el almacenamiento de sesión de Commerce.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Uso almacenado en la memoria caché para el almacenamiento de sesión

La memoria en caché es un sistema de almacenamiento en caché distribuido de uso general. A menudo se utiliza para acelerar los sitios web dinámicos impulsados por bases de datos almacenando en caché los datos y objetos en RAM para reducir el número de veces que se debe leer una fuente de datos externa (como una base de datos o API).

En memoria caché proporciona una tabla hash grande que se puede distribuir entre varios equipos. Cuando la tabla está llena, las inserciones posteriores hacen que los datos más antiguos se purguen en el orden utilizado (LRU) menos recientemente. El tamaño de esta tabla hash a menudo es muy grande. (Fuente: [memcached.org](https://www.memcached.org/))

El comercio utiliza la memoria caché para el almacenamiento de sesión, pero no para el almacenamiento de páginas. Para el almacenamiento en caché de páginas, se recomienda [Redis](../cache/redis-pg-cache.md) o [Varniz](../cache/config-varnish.md).

**Para configurar Commerce para que use memcached**:

1. Apertura `<your install dir>/app/etc/env.php` en un editor de texto.
1. Busque lo siguiente:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Cambie de la siguiente manera:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached tiene parámetros de inicio opcionales que están fuera del alcance de esta guía. Puede encontrar más información sobre ellos en la sección [en caché](https://www.php.net/manual/en/memcached.sessions.php) documentación, código fuente y cambios.

1. Continúe con la siguiente sección.

**Para verificar que funciona con Commerce**:

1. Elimine el contenido de los siguientes directorios en el directorio de instalación de Commerce:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Vaya a cualquier página de la tienda.

1. Inicie sesión en el administrador y vaya a varias páginas.

   Si no se muestran errores, ¡felicitaciones! memcached está funcionando! Opcionalmente, puede ver el almacenamiento en caché como se describe en el paso siguiente.

   Si se muestran errores (como un HTTP 500 (error interno del servidor)), habilite el modo de desarrollador y diagnostique el problema. Asegúrese de que la memoria caché se esté ejecutando, configurada correctamente y que `env.php` no tiene errores de sintaxis.

1. (Opcional.) Utilice Telnet para ver el almacenamiento en caché.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Los resultados son similares a los siguientes:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
