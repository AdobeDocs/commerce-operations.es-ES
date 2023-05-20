---
title: Desinstalación de paquetes de idioma
description: Siga estos pasos para desinstalar un paquete de idioma de Adobe Commerce o de Magento Open Source.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Desinstalación de paquetes de idioma

En esta sección se explica cómo desinstalar uno o más paquetes de idioma, incluyendo opcionalmente el código de los paquetes de idioma del sistema de archivos. Primero puede crear copias de seguridad para poder restaurar los datos más adelante.

Este comando desinstala *solamente* paquetes de idioma especificados en `composer.json`; en otras palabras, paquetes de idiomas que se proporcionan como paquetes de Compositor. Si el paquete de idioma no es un paquete de Compositor, debe desinstalarlo manualmente eliminando el código del paquete de idioma del sistema de archivos.

Puede restaurar las copias de seguridad en cualquier momento mediante el [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

Uso de comandos:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

El comando de desinstalación del paquete de idioma realiza las siguientes tareas:

1. Comprueba las dependencias; si es así, el comando finaliza.

   Para solucionarlo, puede desinstalar todos los paquetes de idiomas dependientes al mismo tiempo o puede desinstalar primero los paquetes de idiomas dependientes.

1. If `--backup code` se especifica, realizar una copia de seguridad del sistema de archivos (excluyendo `var` y `pub/static` directorios) a `var/backups/<timestamp>_filesystem.tgz`
1. Elimina los archivos de paquetes de idioma de la base de código mediante `composer remove`.
1. Limpia la caché.

Por ejemplo, si intenta desinstalar un paquete de idioma del que depende otro paquete de idioma, se muestra el siguiente mensaje:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Una alternativa es desinstalar ambos paquetes de idioma después de realizar una copia de seguridad de la base de código:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Se muestran mensajes similares a los siguientes:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
