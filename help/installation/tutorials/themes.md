---
title: Desinstalar temas
description: Siga estos pasos para desinstalar una temática de Adobe Commerce.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Desinstalar temas

Antes de utilizar este comando, debe conocer la ruta relativa a la temática. Los temas se encuentran en un subdirectorio de `<magento_root>/app/design/<area name>`. Debe especificar la ruta de acceso al tema que comienza con el área, que es `frontend` (para temas de tienda) o `adminhtml` (para temas de administración).

Por ejemplo, la ruta al tema de Luma proporcionado con Adobe Commerce es `frontend/Magento/luma`.

Para obtener más información acerca de las temáticas, vea [estructura de temáticas](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Información general sobre la desinstalación de temáticas

En esta sección se explica cómo desinstalar una o más temáticas, incluyendo de forma opcional el código de las temáticas del sistema de archivos. Primero puede crear copias de seguridad para poder restaurar los datos más adelante.

Este comando desinstala *solamente* temas especificados en `composer.json`; en otras palabras, temas que se proporcionan como paquetes de composición. Si la temática no es un paquete de Compositor, debe desinstalarlo manualmente:

* Actualizando la información del nodo `parent` en `theme.xml` para quitar las referencias al tema.
* Quitando el código de tema del sistema de archivos.

  [Más información acerca de la herencia de temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Desinstalar temas

Uso de comandos:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Donde

* `{theme path}` es la ruta relativa al tema, empezando por el nombre del área. Por ejemplo, la ruta de acceso al tema en blanco proporcionado con Adobe Commerce es `frontend/Magento/blank`.
* `--backup-code` realiza una copia de seguridad del código base como se describe en los párrafos siguientes.
* `--clear-static-content` limpia [archivos de vista estática](../../configuration/cli/static-view-file-deployment.md) generados, lo cual es necesario para que los archivos de vista estática se muestren correctamente.

El comando realiza las siguientes tareas:

1. Comprueba que existen las rutas de acceso de temas especificadas; de lo contrario, el comando finaliza.
1. Comprueba que la temática es un paquete de Compositor; si no es así, el comando finaliza.
1. Comprueba las dependencias y finaliza el comando si hay dependencias que no se cumplen.

   Para solucionarlo, puede desinstalar todas las temáticas al mismo tiempo o puede desinstalar primero la temática en función de la temática.

1. Comprueba que el tema no se está utilizando; si se está utilizando, el comando finaliza.
1. Comprueba que el tema no es la base del tema virtual; si es la base de un tema virtual, el comando finaliza.
1. Pone el almacén en modo de mantenimiento.
1. Si se especifica `--backup-code`, haga una copia de seguridad del código base, excluyendo los directorios `pub/static`, `pub/media` y `var`.

   El nombre del archivo de copia de seguridad es `var/backups/<timestamp>_filesystem.tgz`

   Puede restaurar copias de seguridad en cualquier momento mediante el comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

1. Quita los temas de la tabla de base de datos `theme`.
1. Quitar temas de la base de código usando `composer remove`.
1. Limpia la caché.
1. Limpia las clases generadas
1. Si se especifica `--clear-static-content`, limpia [los archivos de vista estática generados](../../configuration/cli/static-view-file-deployment.md).

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
>Para desinstalar un tema de administración, también debe quitarlo de la configuración de inyección de dependencias del componente, `<component root directory>/etc/di.xml`.
