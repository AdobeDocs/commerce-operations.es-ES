---
title: Desinstalación de módulos
description: Siga estos pasos para desinstalar un módulo de Adobe Commerce.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Desinstalación de módulos

En esta sección se explica cómo desinstalar uno o más módulos. Durante la desinstalación, puede eliminar de forma opcional el código de los módulos, el esquema de la base de datos y los datos de la base de datos. Primero puede crear copias de seguridad para poder recuperar los datos más adelante.

Solo debe desinstalar un módulo si está seguro de que no lo utilizará. En lugar de desinstalar un módulo, puede deshabilitarlo como se describe en [Habilitar o deshabilitar módulos](manage-modules.md).

>[!NOTE]
>
>Este comando comprueba que solo las dependencias declaradas en la variable `composer.json` archivo. Si desinstala un módulo que es _no_ definida en la variable `composer.json` , este comando desinstala el módulo sin comprobar las dependencias. Este comando hace lo siguiente _no_, sin embargo, elimine el código del módulo del sistema de archivos. Debe utilizar las herramientas del sistema de archivos para quitar el código del módulo (por ejemplo, `rm -rf <path to module>`). Como alternativa, puede hacer lo siguiente [disable](manage-modules.md) módulos que no son de Compositor.

Uso de comandos:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Donde `{ModuleName}` especifica el nombre del módulo en `<VendorName>_<ModuleName>` formato. Por ejemplo, el nombre del módulo Cliente es `Magento_Customer`. Para obtener una lista de nombres de módulos, escriba `magento module:status`

El comando de desinstalación del módulo realiza las siguientes tareas:

1. Comprueba que los módulos especificados existen en la base de código y que son paquetes instalados por Composer.

   Este comando funciona _solamente_ con módulos definidos como paquetes de Compositor.

1. Comprueba las dependencias con otros módulos y finaliza el comando si hay dependencias que no se cumplen.

   Para solucionarlo, puede desinstalar todos los módulos al mismo tiempo o puede desinstalar primero los módulos dependientes.

1. Solicita confirmación para continuar.
1. Pone el almacén en modo de mantenimiento.
1. Procesa las siguientes opciones de comando.

   | Opción | Significado | Nombre y ubicación del archivo de copia de seguridad |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Realiza una copia de seguridad del sistema de archivos (excluyendo `var` y `pub/static` directorios). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Realiza una copia de seguridad del directorio pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Copia de seguridad de la base de datos. | `var/backups/<timestamp>_db.gz` |

1. If `--remove-data` se especifica, quite el esquema de la base de datos y los datos definidos en el `Uninstall` clases.

   Para que se desinstale cada módulo especificado, invoca el `uninstall` método en su `Uninstall` clase. Esta clase debe heredar de [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Quita los módulos especificados del `setup_module` tabla de base de datos.
1. Quita los módulos especificados de la lista de módulos de [configuración de implementación](../../configuration/reference/deployment-files.md).
1. Quita el código de la base de código mediante `composer remove`.

   >[!NOTE]
   >
   >Desinstalación de un módulo _siempre_ ejecuciones `composer remove`. El `--remove-data` elimina los datos de la base de datos y el esquema definidos por el módulo `Uninstall` clase.

1. Limpia la caché.
1. Actualiza las clases generadas.
1. If `--clear-static-content` se ha especificado, limpia [archivos de vista estática generados](../../configuration/cli/static-view-file-deployment.md).
1. Elimina el almacén del modo de mantenimiento.

Por ejemplo, si intenta desinstalar un módulo del que depende otro módulo, aparecerá el siguiente mensaje:

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Una alternativa es desinstalar ambos módulos después de realizar una copia de seguridad del sistema de archivos del módulo, `pub/media` archivos y tablas de base de datos pero _no_ eliminando el esquema o los datos de la base de datos del módulo:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Se muestran mensajes similares a los siguientes:

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Se muestran errores si intenta desinstalar un módulo con una dependencia de otro módulo. En ese caso, no puede desinstalar un módulo; debe desinstalar ambos.

## Revertir los archivos de sistema de archivos, base de datos o medios

Para restaurar el código base al estado en el que realizó la copia de seguridad, utilice el siguiente comando:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Donde `<filename>` es el nombre del archivo de copia de seguridad en `<app_root>/var/backups` directorio. Para mostrar una lista de archivos de copia de seguridad, escriba `magento info:backups:list`

>[!WARNING]
>
>Este comando elimina los archivos especificados o la base de datos antes de restaurarlos. Por ejemplo, la variable `--media-file` elimina los recursos de medios en la opción `pub/media` antes de restaurar desde el archivo de reversión especificado. Asegúrese de no haber cambiado el sistema de archivos o la base de datos que desea conservar antes de utilizar este comando.

>[!NOTE]
>
>Para mostrar una lista de los archivos de copia de seguridad disponibles, escriba `magento info:backups:list`

Este comando realiza las tareas siguientes:

1. Pone el almacén en modo de mantenimiento.
1. Comprueba el nombre del archivo de copia de seguridad.
1. Si especifica un archivo de reversión de código:

   a. Comprueba que las ubicaciones de destino de reversión pueden escribirse (tenga en cuenta que la variable `pub/static` y `var` carpetas se ignoran).

   b. Elimina todos los archivos y directorios del directorio de instalación de la aplicación.

   c. Extrae el archivo de almacenamiento a las ubicaciones de destino.

1. Si especifica un archivo de reversión de base de datos:

   a. Borra toda la base de datos.

   b. Restaura la base de datos mediante la copia de seguridad de la base de datos.

1. Si especifica un archivo de reversión de medios:

   a. Comprueba que se puede escribir en las ubicaciones de destino de reversión.

   b. Elimina todos los archivos y directorios de `pub/media`

   c. Extrae el archivo de almacenamiento a las ubicaciones de destino.

1. Elimina el almacén del modo de mantenimiento.

Por ejemplo, para restaurar una copia de seguridad de un código (es decir, un sistema de archivos), introduzca los siguientes comandos en el orden mostrado:

* Mostrar una lista de copias de seguridad:

  ```bash
  magento info:backups:list
  ```

* Restaurar una copia de seguridad de archivos denominada `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Se muestran mensajes similares a los siguientes:

  ```terminal
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Para ejecutar el `magento` vuelva a ejecutar el comando sin cambiar los directorios, es posible que tenga que introducir `cd pwd`.
