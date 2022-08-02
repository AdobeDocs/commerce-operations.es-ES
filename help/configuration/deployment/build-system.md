---
title: Configuración del sistema de compilación
description: Aprenda a implementar Commerce en un sistema de compilación.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Configuración del sistema de compilación

Puede tener un sistema de compilación que cumpla los siguientes requisitos:

- Todo el código de comercio está bajo control de código fuente en el mismo repositorio que los sistemas de desarrollo y producción
- Asegúrese de que todos los elementos siguientes sean: _included_ en control de código fuente:

   - `app/etc/config.php`
   - `generated` directorio (y subdirectorios)
   - `pub/media` directory
   - `pub/media/wysiwyg` directorio (y subdirectorios)
   - `pub/static` directorio (y subdirectorios)

- Debe tener instalada una versión PHP compatible
- Debe tener instalado el Compositor
- Tiene establecidos permisos y propiedad del sistema de archivos como se describe en [Requisito previo para los sistemas de desarrollo, construcción y producción](../deployment/technical-details.md).
- El sistema de compilación no necesita instalar Commerce, pero el código debe estar disponible para él.

>[!WARNING]
>
>La conexión de base de datos no es necesaria si ya está contenida en `config.php`; see [Exportar la configuración](../cli/export-configuration.md). De lo contrario, se requiere la conexión a la base de datos.

>[!INFO]
>
>El equipo de compilación puede estar en su propio host o en el mismo host que un sistema de comercio instalado.

## Configuración del equipo de compilación

En las secciones siguientes se explica cómo configurar el equipo de compilación.

### Instalar Compositor

Primero, compruebe si el Compositor ya está instalado:

En un símbolo del sistema, introduzca cualquiera de los siguientes comandos:

- `composer --help`
- `composer list --help`

Si se muestra la ayuda del comando, el Compositor ya está instalado.

Si se muestra un error, siga los siguientes pasos para instalar Composer.

Para instalar Composer:

1. Cambie a o cree un directorio vacío en el servidor de comercio.

1. Introduzca los siguientes comandos:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Para obtener más opciones de instalación, consulte la [Documentación de instalación del compositor][composer].

### Instalar PHP

Instalar PHP en [CentOS] o [Ubuntu].

### Configuración del sistema de compilación

Para configurar el sistema de compilación:

1. Inicie sesión en el sistema de compilación como propietario del sistema de archivos o cambie a él.
1. Recupere el código de comercio del control de código fuente.

   Si utiliza Git, utilice el siguiente comando:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Cambie al directorio raíz del comercio e introduzca:

   ```bash
   composer install
   ```

1. Espere a que se actualicen las dependencias.
1. Establezca la propiedad:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Por ejemplo,

   ```bash
   chown -R commerce-username:apache .
   ```

1. Si utiliza Git, abra `.gitignore` en un editor de texto.
1. Inicie cada una de las líneas siguientes con un `#` para comentarlos:

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

1. El sistema de compilación debe utilizar [modo predeterminado](../bootstrap/application-modes.md#default-mode) o [modo de desarrollador](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` es obligatorio. Puede ser `default` o `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
