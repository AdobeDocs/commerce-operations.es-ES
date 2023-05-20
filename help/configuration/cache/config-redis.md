---
title: Configurar Redis
description: Obtenga información general sobre las funciones de Redis e inicie la configuración de Redis.
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Configurar Redis

Las funciones de Redis incluyen:

- Almacenamiento de sesión PHP
- Limpieza de caché basada en etiquetas sin `foreach` bucles
- Guardados en disco y replicación maestra/esclava

## Instalar Redis

La instalación y configuración del software de Redis excede el ámbito de esta guía. Consulte recursos como:

- [Descargar página de Redis](https://redis.io/download)
- [Inicio rápido de Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Página de documentación de Redis](https://redis.io/docs)

## Configurar Redis

Según la instalación, la configuración de Redis suele encontrarse en uno de los siguientes archivos: `/etc/redis/redis.conf` o `/etc/redis/<port>.conf`

Para optimizar la instancia de Redis según sus necesidades, obtenga los mejores resultados utilizando una instancia dedicada para cada sesión, caché de Commerce y FPC.

Para las sesiones, Adobe recomienda habilitar la persistencia para copiar datos de Redis en el disco mediante cualquiera de las siguientes opciones de persistencia: instantáneas de Redis Database Backup (RDB) normales o registros de persistencia de Anexar solo archivo (AOF).

- **Copia de Seguridad Redis Database** Las instantáneas de (RDB) almacenan la base de datos completa en un archivo de volcado después de un tiempo determinado, cuando un número mínimo de claves ha cambiado desde la última vez que se guardó. Utilice el `save` configuración dentro de `redis.conf` para configurar esta opción.

- **Anexar solo archivo** (AOF) almacena cada operación de escritura enviada a Redis en un archivo de diario. Redis solo lee este archivo al reiniciar y lo utiliza para restaurar el conjunto de datos original.

También puede activar las opciones RDB y AOF al mismo tiempo. Para obtener más información, incluidas las ventajas y desventajas de las opciones de persistencia, consulte la [Documentación de Persistencia de Redis](https://redis.io/topics/persistence).

Para la instancia de caché de, configure la instancia de modo que sea lo suficientemente grande como para almacenar toda la caché de Commerce. Los requisitos de tamaño dependen de diferentes factores, como el número de productos y las vistas de la tienda. Como punto de partida, puede utilizar el tamaño de la carpeta de caché en el sistema de archivos. Por ejemplo, si la variable `var/cache` en su sistema de archivos es de 5 GB, configure su instancia de Redis con al menos 5 GB para iniciar. No se requiere persistencia para la instancia de caché porque se puede restaurar la caché de Commerce. Consulte [Guía de caché de Redis](https://redis.io/docs/manual/eviction/).

Para ajustar el rendimiento, puede habilitar la siguiente configuración para la eliminación asincrónica. Esta configuración no cambia el comportamiento de Redis.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

En Redis 6.x y versiones posteriores, también puede agregar el siguiente valor:

```ini
lazyfree-lazy-user-del yes
```
