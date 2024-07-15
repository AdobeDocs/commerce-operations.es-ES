---
title: Configurar sistema de compilación
description: Obtenga información sobre cómo implementar Commerce en un sistema de compilación.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Configuración del sistema de compilación

Puede tener un sistema de compilación que cumpla los siguientes requisitos:

- Todo el código Commerce está bajo control de código fuente en el mismo repositorio que los sistemas de desarrollo y producción
- Asegúrese de que todos los elementos siguientes estén _incluidos_ en el control de código fuente:

   - `app/etc/config.php`
   - Directorio `generated` (y subdirectorios)
   - `pub/media` directorio
   - Directorio `pub/media/wysiwyg` (y subdirectorios)
   - Directorio `pub/static` (y subdirectorios)

- Debe tener instalada una versión compatible de PHP
- Debe tener Composer instalado
- Tiene la propiedad del sistema de archivos y los permisos establecidos como se describe en [Requisito previo para los sistemas de desarrollo, compilación y producción](../deployment/technical-details.md).
- El sistema de compilación no necesita que Commerce esté instalado, pero el código debe estar disponible para él.

>[!WARNING]
>
>No se requiere la conexión a la base de datos si ya se encuentra en `config.php`; consulte [Exportar la configuración](../cli/export-configuration.md). De lo contrario, se requiere la conexión a base de datos.

>[!INFO]
>
>El equipo de generación puede estar en su propio host o en el mismo host que un sistema Commerce instalado.

## Configurar el equipo de generación

En las siguientes secciones se explica cómo configurar el equipo de generación.

### Instalar Compositor

En primer lugar, compruebe si Composer ya está instalado:

En un símbolo del sistema, introduzca cualquiera de los siguientes comandos:

- `composer --help`
- `composer list --help`

Si se muestra la ayuda de comandos, Composer ya está instalado.

Si se muestra un error, siga los siguientes pasos para instalar Composer.

Para instalar Composer:

1. Cambie a o cree un directorio vacío en el servidor de Commerce.

1. Introduzca los siguientes comandos:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Para obtener más opciones de instalación, consulte la [documentación de instalación del Compositor][composer].

### Instalar PHP

Instala PHP en [CentOS] o [Ubuntu].

### Configurar el sistema de compilación

Para configurar el sistema de compilación:

1. Inicie sesión en el sistema de generación como propietario del sistema de archivos o cambie a él.
1. Recupere el código Commerce del control de código fuente.

   Si utiliza Git, utilice el siguiente comando:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Cambie al directorio raíz de Commerce e introduzca:

   ```bash
   composer install
   ```

1. Espere a que se actualicen las dependencias.
1. Establecer propiedad:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Por ejemplo,

   ```bash
   chown -R commerce-username:apache .
   ```

1. Si usa Git, abra `.gitignore` en un editor de texto.
1. Comience cada una de las siguientes líneas con un carácter `#` para comentarlas:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Guarde los cambios en `.gitignore` y salga del editor de texto.
1. Si utiliza Git, utilice los siguientes comandos para confirmar el cambio:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Consulte la [`.gitignore` referencia](../reference/config-reference-gitignore.md) para obtener más información.

1. El sistema de compilación debe usar [modo predeterminado](../bootstrap/application-modes.md#default-mode) o [modo de desarrollador](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   Se requiere `<mode>`. Puede ser `default` o `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
