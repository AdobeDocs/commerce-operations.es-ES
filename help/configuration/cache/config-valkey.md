---
title: Configuración de Valkey
description: Obtenga información general sobre las funciones de Valkey e inicie la configuración de Valkey.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: b2cf71bfda3e5db8e27eb28d764cf99216454e33
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Configuración de Valkey

Las características de Valkey incluyen:

- Almacenamiento de sesión PHP
- Limpieza de caché basada en etiquetas sin bucles `foreach`
- Guardados en disco y replicación maestra/esclava

## Instalar Valkey

Para instalar y configurar el software de Valkey, consulte los siguientes recursos:

- [Descargar página de Valkey](https://valkey.io/download/)
- [Inicio rápido de Valkey](https://valkey.io/topics/quickstart/)
- [Página de documentación de Valkey](https://valkey.io/docs)

## Configurar Valkey

Según la instalación, normalmente puede encontrar la configuración de Valkey en el archivo `/etc/valkey/valkey.conf` o en el archivo `/etc/valkey/<port>.conf`.

Para optimizar la instancia de Valkey según sus necesidades, puede obtener los mejores resultados utilizando una instancia específica para cada sesión, caché de Commerce y FPC.

Adobe recomienda habilitar la persistencia para que las sesiones copien datos de Valkey en el disco. Puede utilizar instantáneas de la copia de seguridad de la base de datos de Valkey (RDB) o registros de persistencia del archivo de sólo anexar (AOF).

- Las instantáneas **RDB** (Base de datos de Valkey) almacenan la base de datos completa en un archivo de volcado después de un tiempo determinado, cuando un número mínimo de claves ha cambiado desde la última vez que se guardó. Use la configuración `save` dentro del archivo `valkey.conf` para configurar esta configuración.

- **Anexar solo archivo** (AOF) almacena cada operación de escritura enviada a Valkey en un archivo de diario. Valkey lee este archivo solo al reiniciar y lo utiliza para restaurar el conjunto de datos original.

También puede activar las opciones RDB y AOF al mismo tiempo. Para obtener más información, incluidas las ventajas y desventajas de las opciones de persistencia, consulte la [documentación sobre la persistencia de Valkey](https://valkey.io/topics/persistence/).

Para la instancia de caché, configúrela de modo que sea lo suficientemente grande como para almacenar toda la caché de Commerce. Los requisitos de tamaño dependen de diferentes factores, como el número de productos y las vistas de la tienda. Como punto de partida, puede utilizar el tamaño de la carpeta de caché en el sistema de archivos. Por ejemplo, si la carpeta `var/cache` del sistema de archivos tiene 5 GB, configure la instancia de Valkey con al menos 5 GB para el inicio. No se requiere persistencia para la instancia de caché porque se puede restaurar la caché de Commerce.

Para ajustar el rendimiento, puede habilitar la siguiente configuración para la eliminación asincrónica. Esta configuración no cambia el comportamiento de Valkey.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
