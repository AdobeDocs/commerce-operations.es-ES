---
title: Resumen de migración
description: Obtenga información sobre cómo empezar a migrar datos de Magento 1 a Magento 2 con [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '315'
ht-degree: 0%
---
# Resumen de migración

Antes de iniciar la migración, detenga todos los trabajos cron de Magento 1.

Durante el proceso de migración, siga estas reglas generales para que la migración se realice correctamente:

1. **No** realice cambios en el administrador de Magento 1, excepto en la administración de pedidos (envío, creación de facturas y abonos)
1. **No** modificar ningún código
1. **No** realice cambios en el administrador y tienda de Magento 2

>[!TIP]
>
>Se permiten todas las operaciones en la tienda de Magento 1.

## Ejecutar [!DNL Data Migration Tool]

Esta sección muestra cómo ejecutar [!DNL Data Migration Tool] para migrar la configuración, los datos o los cambios incrementales.

### Primeros pasos

1. Inicie sesión en el servidor de aplicaciones como un usuario con permisos para escribir en el sistema de archivos o cambie a. Vea [cambiar al propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

   Si utiliza el shell de bash, puede utilizar la siguiente sintaxis para cambiar al propietario del sistema de archivos e introducir el comando al mismo tiempo:

   ```shell
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si el propietario del sistema de archivos no permite inicios de sesión, puede hacer lo siguiente:

   ```shell
   sudo -u <file system owner>  <command>
   ```

1. Para ejecutar comandos de Magento desde cualquier directorio, agregue `<magento_root>/bin` a su sistema `PATH`.

   Como los shells tienen sintaxis diferente, consulte una referencia como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Ejemplo de shell de bash para CentOS:

   ```shell
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Opcionalmente, puede ejecutar los comandos de las siguientes maneras:

   - `cd <magento_root>/bin` y ejecutarlos como `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` es un subdirectorio del servidor web docroot.

### Sintaxis de comandos

A continuación se muestra un ejemplo de comando típico:

```shell
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

- `<mode>` puede ser: [`settings`](settings.md), [`data`](data.md) o [`delta`](delta.md)
- `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración.
- `[-a|--auto]` es un argumento opcional que impide que se detenga la migración cuando encuentra errores de comprobación de integridad.
- `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a `config.xml`; este argumento es obligatorio.

>[!NOTE]
>
>Los registros se escriben en el directorio `<magento_root>/var/`.


## Orden de migración

Cuando se creó [!DNL Data Migration Tool], se asumió la siguiente secuencia de transferencia de datos:

1. [Configuración](settings.md)
1. [Datos](data.md)
1. [Cambios](delta.md)

Se recomienda migrar los datos en el mismo orden.
