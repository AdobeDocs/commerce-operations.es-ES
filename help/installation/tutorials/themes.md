---
title: Desinstalación de temas
description: Siga estos pasos para desinstalar un tema de Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Desinstalación de temas

Antes de utilizar este comando, debe conocer la ruta relativa a su tema. Los temas se encuentran en un subdirectorio de `<magento_root>/app/design/<area name>`. Debe especificar la ruta al tema empezando por el área, que puede ser `frontend` (para temas de tienda) o `adminhtml` (para [Administrador](https://glossary.magento.com/magento-admin) temas).

Por ejemplo, la ruta a la Luma [tema](https://glossary.magento.com/theme) se proporciona con Adobe Commerce y Magento Open Source es `frontend/Magento/luma`.

Para obtener más información sobre los temas, consulte [estructura del tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Información general sobre la desinstalación de temas

En esta sección se explica cómo desinstalar uno o más temas, incluyendo opcionalmente el código de los temas del sistema de archivos. Primero puede crear copias de seguridad para poder restaurar los datos más adelante.

Este comando desinstala *only* temas especificados en `composer.json`; en otras palabras, los temas que se proporcionan como [Compositor](https://glossary.magento.com/composer) paquetes. Si el tema no es un paquete Composer, debe desinstalarlo manualmente:

* Actualización del `parent` información de nodo en `theme.xml` para eliminar referencias al tema.
* Eliminación del código de tema del sistema de archivos.

   [Más información sobre la herencia de temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Desinstalación de temas

Uso de comandos:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Donde

* `{theme path}` es la ruta relativa al tema, empezando por el nombre del área. Por ejemplo, la ruta al tema en blanco suministrada con Adobe Commerce y el Magento Open Source es `frontend/Magento/blank`.
* `--backup-code` haga una copia de seguridad del código de base tal como se indica en los párrafos siguientes.
* `--clear-static-content` limpiadores generados [archivos de vista estáticos](../../configuration/cli/static-view-file-deployment.md), que es necesario para que los archivos de vista estáticos se muestren correctamente.

El comando realiza las siguientes tareas:

1. Comprueba que existen las rutas de tema especificadas; si no es así, el comando finaliza.
1. Verifica que el tema sea un paquete Composer; si no es así, el comando finaliza.
1. Comprueba las dependencias y finaliza el comando si hay dependencias no cumplidas.

   Para solucionarlo, puede desinstalar todos los temas al mismo tiempo o puede desinstalar primero según el tema.

1. Comprueba que el tema no se esté utilizando; si se está utilizando, el comando finaliza.
1. Verifica que el tema no sea la base del tema virtual; si es la base de un tema virtual, el comando finaliza.
1. Coloca la tienda en modo de mantenimiento.
1. If `--backup-code` se especifica, haga una copia de seguridad de la base de código, excluyendo la variable `pub/static`, `pub/media`y `var` directorios.

   El nombre del archivo de copia de seguridad es `var/backups/<timestamp>_filesystem.tgz`

   Puede restaurar las copias de seguridad en cualquier momento utilizando la variable [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

1. Elimina los temas del `theme` tabla de base de datos.
1. Eliminación de temas de la base de código mediante `composer remove`.
1. Limpia el [cache](https://glossary.magento.com/cache).
1. Limpia las clases generadas
1. If `--clear-static-content` se especifica, limpia [archivos de vista estáticos generados](../../configuration/cli/static-view-file-deployment.md).

Por ejemplo, si intenta desinstalar un tema del que dependa otro tema, aparece el siguiente mensaje:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Una alternativa es desinstalar ambos temas al mismo tiempo que se realiza la copia de seguridad del código base:

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
>Para desinstalar [Administrador](https://glossary.magento.com/admin) tema, también debe eliminarlo del [inyección de dependencia](https://glossary.magento.com/dependency-injection) configuración, `<component root directory>/etc/di.xml`.
