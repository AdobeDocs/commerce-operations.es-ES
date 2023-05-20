---
title: Definición del modo de funcionamiento
description: Obtenga información sobre cómo configurar los modos de funcionamiento de Adobe Commerce.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Definición del modo de funcionamiento

{{file-system-owner}}

Para mejorar la seguridad y la facilidad de uso, hemos añadido un comando que cambia [modos de aplicación](../bootstrap/application-modes.md) del desarrollador a la producción y viceversa.

El modo de producción tiene un mejor rendimiento porque los archivos de vista estática se rellenan en la variable `pub/static` y debido a la compilación del código.

>[!INFO]
>
>En la versión 2.0.6 y posteriores, Commerce no establece explícitamente permisos de archivos o directorios al cambiar entre los modos de producción, desarrollo y predeterminado. A diferencia de otros modos, los modos de desarrollador y producción se establecen en la variable `env.php` archivo. Adobe Commerce en la infraestructura en la nube solo admite modos de producción y mantenimiento.
>
>Consulte [Propiedad comercial y permisos en desarrollo y producción](../deployment/file-system-permissions.md).

Cuando cambie al modo de desarrollo o producción, borraremos el contenido de los siguientes directorios:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Excepciones:

- `.htaccess` los archivos no se eliminan
- `pub/static` contiene un archivo que especifica la versión del contenido estático; este archivo no se elimina

>[!INFO]
>
>De forma predeterminada, Commerce utiliza la variable `var` para almacenar la caché, los registros y el código compilado. Puede personalizar este directorio, pero en esta guía se supone que es `var`.

## Mostrar el modo actual

La forma más sencilla de hacerlo es ejecutar este comando como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md). Si tiene un alojamiento compartido, este es el usuario que su proveedor le proporciona para iniciar sesión en el servidor. Si tiene un servidor privado, suele ser una cuenta de usuario local en el servidor de Commerce.

Uso de comandos:

```bash
bin/magento deploy:mode:show
```

Aparece un mensaje similar al siguiente:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

donde:

- **`{mode}`** puede ser `default`, `developer`, o `production`

## Cambiar modos

Uso de comandos:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

donde:

- **`{mode}`** es obligatorio; puede ser lo siguiente `developer` o `production`

- **`--skip-compilation`** es un parámetro opcional que puede utilizar para omitir [compilación de código](../cli/code-compiler.md) cuando cambie al modo de producción.

A continuación se muestran ejemplos.

### Cambiar a modo de producción

```bash
bin/magento deploy:mode:set production
```

Se muestran mensajes similares a los siguientes:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Cambiar a modo de desarrollador

Cuando cambie del modo de producción al modo de desarrollador, debe borrar las clases generadas y las entidades del Administrador de objetos como los proxies para evitar errores inesperados. Después de hacerlo, puede cambiar de modo. Siga estos pasos:

1. Si está cambiando del modo de producción al modo de desarrollador, elimine el contenido del `generated/code` y `generated/metadata` directorios:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Configure el modo:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Se muestra el siguiente mensaje:

   ```terminal
   Enabled developer mode.
   ```

### Cambiar al modo predeterminado

```bash
bin/magento deploy:mode:set default
```

Se muestra el siguiente mensaje:

```terminal
Enabled default mode.
```

### Ejecute comandos CLI desde cualquier lugar

[Ejecute comandos CLI desde cualquier lugar](../cli/config-cli.md#config-install-cli-first).

Si no ha añadido `<Commerce-install-directory>/bin` a su sistema `PATH`, entonces puede esperar un error al ejecutar el comando por sí solo.
