---
title: Información general sobre migración
description: Obtenga información sobre cómo empezar a migrar datos del Magento 1 al Magento 2 con la variable [!DNL Data Migration Tool].
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Información general sobre migración

Antes de iniciar la migración, detenga todos los trabajos cron de Magento 1.

Durante el proceso de migración, siga estas reglas generales para una migración correcta:

1. **No** realice cambios en el administrador de Magento 1, excepto en la gestión de pedidos (envío, creación de facturas y notas de abono)
1. **No** modificar cualquier código
1. **No** realizar cambios en el administrador y la tienda de Magento 2

>[!TIP]
>
>Se permiten todas las operaciones en la tienda Magento 1.

## Ejecute el [!DNL Data Migration Tool]

Esta sección muestra cómo ejecutar el [!DNL Data Migration Tool] para migrar la configuración, los datos o los cambios incrementales.

### Primeros pasos

1. Inicie sesión en el servidor de aplicaciones como usuario con permisos para escribir en el sistema de archivos o cambie a. Consulte [cambie al propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

   Si utiliza el shell de bash, puede utilizar la siguiente sintaxis para cambiar al propietario del sistema de archivos e introducir el comando al mismo tiempo:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si el propietario del sistema de archivos no permite inicios de sesión, puede hacer lo siguiente:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Para ejecutar comandos de Magento desde cualquier directorio, agregue `<magento_root>/bin` al sistema `PATH`.

   Dado que los contenedores tienen una sintaxis diferente, consulte una referencia como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Ejemplo de shell bash para CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   De forma opcional, puede ejecutar los comandos de las siguientes maneras:

   - `cd <magento_root>/bin` y ejecútelos como `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` es un subdirectorio de su servidor web docroot.

### Sintaxis del comando

A continuación se muestra un ejemplo de comando típico:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

- `<mode>` puede ser: [`settings`](settings.md), [`data`](data.md)o [`delta`](delta.md)
- `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración.
- `[-a|--auto]` es un argumento opcional que evita que la migración se detenga cuando encuentra errores de comprobación de integridad.
- `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a `config.xml`; este argumento es obligatorio.

>[!NOTE]
>
>Los registros se escriben en la variable `<magento_root>/var/` directorio.


## Orden de migración

Cuando creamos el [!DNL Data Migration Tool], asumimos la siguiente secuencia de transferencia de datos:

1. [Configuración](settings.md)
1. [Datos](data.md)
1. [Cambios](delta.md)

Se recomienda migrar datos en el mismo orden.
