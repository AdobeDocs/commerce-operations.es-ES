---
title: Instalación y configuración de Redis
description: Obtenga información sobre cómo instalar y configurar Redis para almacenar en caché y almacenar sesiones con Adobe Commerce. Descubra las opciones de optimización y ajuste del rendimiento.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T20:26:29.348Z'
TQID: 'https://experienceleague.adobe.com/N61AAy4ihSIlhEjdvpji2XVOdZuHWhytp9zgoAU41K4'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 456
ht-degree: 0%

---

# Instalación y configuración de Redis

Redis es un almacén de datos en memoria que se puede utilizar como back-end de caché y para almacenamiento de sesión. Las funciones principales incluyen:

- Almacenamiento de sesión PHP
- Limpieza de caché basada en etiquetas sin bucles `foreach`
- Guardados en disco y replicación maestra/esclava

{{cloud-cache-config}}

## Instalar Redis

La instalación y configuración del software de Redis excede el ámbito de esta guía. Consulte recursos como:

- [Descargar página de Redis](https://redis.io/download)
- [Inicio rápido de Redis](https://redis.io/docs/latest/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Página de documentación de Redis](https://redis.io/docs)

## Configurar Redis

Según la instalación, normalmente puede encontrar la configuración de Redis en uno de los siguientes archivos: `/etc/redis/redis.conf` o `/etc/redis/<port>.conf`

Para optimizar la instancia de Redis según sus necesidades, obtenga los mejores resultados utilizando una instancia específica para cada sesión, caché de Commerce y FPC.

Para las sesiones, Adobe recomienda habilitar la persistencia para copiar datos de Redis en el disco mediante cualquiera de las siguientes opciones de persistencia: instantáneas de Redis Database Backup (RDB) normales o registros de persistencia de Anexar solo archivo (AOF).

- Las instantáneas **Redis Database Backup** (RDB) almacenan la base de datos completa en un archivo de volcado después de un tiempo determinado, cuando un número mínimo de claves ha cambiado desde la última vez que se guardó. Use la configuración `save` dentro del archivo `redis.conf` para configurar esta configuración.

- **Anexar solo archivo** (AOF) almacena cada operación de escritura enviada a Redis en un archivo de diario. Redis solo lee este archivo al reiniciar y lo utiliza para restaurar el conjunto de datos original.

También puede activar las opciones RDB y AOF al mismo tiempo. Para obtener más información, incluidas las ventajas y desventajas de las opciones de persistencia, consulte la [documentación de Redis Persistence](https://redis.io/topics/persistence).

Para la instancia de caché, configúrela de modo que sea lo suficientemente grande como para almacenar toda la caché de Commerce. Los requisitos de tamaño dependen de diferentes factores, como el número de productos y las vistas de la tienda. Como punto de partida, puede utilizar el tamaño de la carpeta de caché en el sistema de archivos. Por ejemplo, si la carpeta `var/cache` del sistema de archivos tiene 5 GB, configure la instancia de Redis con al menos 5 GB para que se inicie. No se requiere persistencia para la instancia de caché porque se puede restaurar la caché de Commerce. Consulte [Guía de caché de Redis](https://redis.io/docs/latest/develop/use/).

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
