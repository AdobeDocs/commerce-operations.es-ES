---
title: Configurar Redis
description: Obtenga información general sobre las funciones de Redis e inicie su configuración de Redis.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Configurar Redis

Las funciones de revisión incluyen:

- Almacenamiento de sesión PHP
- Limpieza de caché basada en etiquetas sin `foreach` bucles
- Almacenamiento en disco y replicación maestra/esclava

## Instalar Redis

La instalación y configuración del software de Redis está fuera del alcance de esta guía. Consulte recursos como:

- [Descargar página de Redis](https://redis.io/download)
- [Inicio rápido de Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Página de documentación de Redis](https://redis.io/docs)

## Configuración de Redis

Según la instalación, normalmente puede encontrar la configuración de Redis en uno de los siguientes archivos: `/etc/redis/redis.conf` o `/etc/redis/<port>.conf`

Para optimizar la instancia de Redis para sus necesidades, obtendrá mejores resultados mediante el uso de una instancia dedicada para cada sesión, caché de comercio y FPC.

Para las sesiones, Adobe recomienda habilitar la persistencia para copiar los datos de Redis en el disco mediante cualquiera de las siguientes opciones de persistencia: instantáneas de copia de seguridad de bases de datos de Redis (RDB) regulares o registros de persistencia de archivos de solo anexar (AOF).

- **Copia de seguridad de la base de datos de Redis** Las instantáneas (RDB) almacenan la base de datos completa en un archivo de volcado después de un tiempo determinado, cuando un número mínimo de claves ha cambiado desde la última vez que se guardó. Utilice la variable `save` dentro de la variable `redis.conf` para configurar esta configuración.

- **Anexar solo archivo** (AOF) almacena cada operación de escritura enviada a Redis en un archivo de diario. Redis lee este archivo solo al reiniciar y lo utiliza para restaurar el conjunto de datos original.

También puede activar las opciones RDB y AOF al mismo tiempo. Para obtener más información, incluidas las ventajas y desventajas de las opciones de persistencia, consulte la [Documentación de Persistencia de Redis](https://redis.io/topics/persistence).

Para la instancia de caché, configure la instancia para que sea lo suficientemente grande como para almacenar toda la caché de comercio. Los requisitos de tamaño dependen de diferentes factores, como la cantidad de productos y las vistas de la tienda. Como punto de partida, puede utilizar el tamaño de la carpeta de caché en su sistema de archivos. Por ejemplo, si la variable `var/cache` en su sistema de archivos es de 5 GB, configure su instancia de Redis con al menos 5 GB para que se inicie. No se requiere persistencia para la instancia de caché porque se puede restaurar la caché de comercio. Consulte [Guía de caché de Redis](https://redis.io/docs/manual/eviction/).

Para el ajuste del rendimiento, puede habilitar las siguientes configuraciones para la eliminación asincrónica. Estos ajustes no cambian el comportamiento de Redis.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

En Redis 6.x y posteriores, también puede agregar el siguiente valor:

```ini
lazyfree-lazy-user-del yes
```
