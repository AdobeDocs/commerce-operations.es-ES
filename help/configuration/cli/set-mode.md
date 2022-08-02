---
title: Definir el modo de operación
description: Obtenga más información sobre la configuración de los modos de operación de Adobe Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# Definir el modo de operación

{{file-system-owner}}

Para mejorar la seguridad y la facilidad de uso, hemos agregado un comando que cambia [modos de aplicación](../bootstrap/application-modes.md) de desarrollador a producción y viceversa.

El modo de producción tiene un mejor rendimiento porque los archivos de vista estáticos se rellenan en la variable `pub/static` y debido a la compilación del código.

>[!INFO]
>
>En la versión 2.0.6 y posteriores, Commerce no establece explícitamente permisos de archivos o directorios cuando cambia entre los modos predeterminado, de desarrollo y de producción. A diferencia de otros modos, los modos de desarrollo y producción se establecen en la variable `env.php` archivo. Adobe Commerce en la infraestructura de nube solo admite modos de producción y mantenimiento.
>
>Consulte [Propiedad y permisos comerciales en desarrollo y producción](../deployment/file-system-permissions.md).

Al cambiar al modo de desarrollo o producción, se borra el contenido de los siguientes directorios:

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
>De forma predeterminada, Commerce usa la variable `var` directorios para almacenar la caché, los registros y el código compilado. Puede personalizar este directorio, pero en esta guía, se supone que es `var`.

## Mostrar el modo actual

La forma más sencilla de hacerlo es ejecutar este comando como el [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html). Si ha compartido un alojamiento, este es el usuario que su proveedor le da para iniciar sesión en el servidor. Si tiene un servidor privado, suele ser una cuenta de usuario local en el servidor de comercio.

Uso de comandos:

```bash
bin/magento deploy:mode:show
```

Se muestra un mensaje similar al siguiente:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

donde:

- **`{mode}`** puede `default`, `developer`o `production`

## Cambiar modos

Uso de comandos:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

donde:

- **`{mode}`** es obligatorio; puede ser `developer` o `production`

- **`--skip-compilation`** es un parámetro opcional que puede utilizar para omitir [compilación de código](../cli/code-compiler.md) al cambiar al modo de producción.

A continuación se muestran ejemplos.

### Cambio al modo de producción

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
Successfully processed LESS and/or [Sass](https://glossary.magento.com/sass) files
[CSS](https://glossary.magento.com/css) deployment complete
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

### Cambio al modo de desarrollador

Al cambiar del modo de producción al de desarrollador, se deben borrar las clases generadas y las entidades del Administrador de objetos como los proxies para evitar errores inesperados. Después de hacerlo, puede cambiar los modos. Siga estos pasos:

1. Si va a cambiar del modo de producción al modo de desarrollador, elimine el contenido del `generated/code` y `generated/metadata` directorios:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Establezca el modo:

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

Si no ha añadido `<Commerce-install-directory>/bin` al sistema `PATH`, puede esperarse un error al ejecutar el comando por sí solo.
