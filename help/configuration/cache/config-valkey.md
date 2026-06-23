---
title: Instalar y configurar Valkey
description: Aprenda a instalar y configurar Valkey para el almacenamiento en caché y el almacenamiento de sesión con Adobe Commerce. Descubra las opciones de optimización y ajuste del rendimiento.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
TQID: 'https://experienceleague.adobe.com/Ef4WREy0eq0ChsrI5-0FtrjMZWNjwr7l71Pm-RHD1GI'
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
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 414
ht-degree: 0%

---

# Instalación y configuración de Valkey

Valkey es un almacén de datos en memoria de código abierto y compatible con Redis que se puede utilizar como back-end de caché y para almacenamiento de sesión. Las funciones principales incluyen:

- Almacenamiento de sesión PHP
- Limpieza de caché basada en etiquetas sin bucles `foreach`
- Guardados en disco y replicación maestra/esclava

{{cloud-cache-config}}

## Instalar Valkey

Para instalar y configurar el software de Valkey, consulte los siguientes recursos:

- [Descargar página de Valkey](https://valkey.io/download/){target="_blank"}
- [Inicio rápido Valkey](https://valkey.io/topics/quickstart/){target="_blank"}
- [Página de documentación de Valkey](https://valkey.io/docs){target="_blank"}

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
