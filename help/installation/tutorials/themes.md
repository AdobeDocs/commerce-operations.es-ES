---
title: Desinstalar temas
description: Siga estos pasos para desinstalar una temática de Adobe Commerce o de Magento Open Source.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Desinstalar temas

Antes de utilizar este comando, debe conocer la ruta relativa a la temática. Los temas se encuentran en un subdirectorio de `<magento_root>/app/design/<area name>`. Debe especificar la ruta al tema que comienza con el área, que puede ser `frontend` (para temas de tienda) o `adminhtml` (para temas de administración).

Por ejemplo, la ruta al tema de Luma que se proporciona con Adobe Commerce es `frontend/Magento/luma`.

Para obtener más información sobre las temáticas, consulte [estructura del tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Información general sobre la desinstalación de temáticas

En esta sección se explica cómo desinstalar una o más temáticas, incluyendo de forma opcional el código de las temáticas del sistema de archivos. Primero puede crear copias de seguridad para poder restaurar los datos más adelante.

Este comando desinstala *solamente* temas especificados en `composer.json`; es decir, las temáticas que se proporcionan como paquetes de Compositor. Si la temática no es un paquete de Compositor, debe desinstalarlo manualmente:

* Actualización del `parent` información del nodo en `theme.xml` para quitar referencias a la temática.
* Quitando el código de tema del sistema de archivos.

  [Más información sobre la herencia de temáticas](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Desinstalar temas

Uso de comandos:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Donde

* `{theme path}` es la ruta relativa a la temática, empezando por el nombre del área. Por ejemplo, la ruta a la temática en blanco proporcionada con Adobe Commerce es `frontend/Magento/blank`.
* `--backup-code` realiza una copia de seguridad del código base tal como se describe en los párrafos siguientes.
* `--clear-static-content` limpiezas generadas [archivos de vista estática](../../configuration/cli/static-view-file-deployment.md), que es necesario para que los archivos de vista estática se muestren correctamente.

El comando realiza las siguientes tareas:

1. Comprueba que existen las rutas de acceso de temas especificadas; de lo contrario, el comando finaliza.
1. Comprueba que la temática es un paquete de Compositor; si no es así, el comando finaliza.
1. Comprueba las dependencias y finaliza el comando si hay dependencias que no se cumplen.

   Para solucionarlo, puede desinstalar todas las temáticas al mismo tiempo o puede desinstalar primero la temática en función de la temática.

1. Comprueba que el tema no se está utilizando; si se está utilizando, el comando finaliza.
1. Comprueba que el tema no es la base del tema virtual; si es la base de un tema virtual, el comando finaliza.
1. Pone el almacén en modo de mantenimiento.
1. If `--backup-code` se especifica, haga una copia de seguridad del código base, excluyendo el `pub/static`, `pub/media`, y `var` directorios.

   El nombre del archivo de copia de seguridad es `var/backups/<timestamp>_filesystem.tgz`

   Puede restaurar las copias de seguridad en cualquier momento mediante el [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

1. Quita los temas del `theme` tabla de base de datos.
1. Quitar temáticas de la base de código mediante `composer remove`.
1. Limpia la caché.
1. Limpia las clases generadas
1. If `--clear-static-content` se ha especificado, limpia [archivos de vista estática generados](../../configuration/cli/static-view-file-deployment.md).

Por ejemplo, si intenta desinstalar una temática de la que depende otra, se muestra el siguiente mensaje:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Una alternativa es desinstalar ambos temas al mismo tiempo como se indica a continuación, haciendo una copia de seguridad de la base de código:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Se muestran mensajes similares a los siguientes:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Para desinstalar un tema de administración, también debe eliminarlo de la configuración de inyección de dependencias del componente. `<component root directory>/etc/di.xml`.
