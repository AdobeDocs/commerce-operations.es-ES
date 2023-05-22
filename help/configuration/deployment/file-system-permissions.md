---
title: Permisos de acceso a sistemas de archivos
description: Consulte cómo configurar el propietario o los propietarios del sistema de archivos de la aplicación Commerce para un sistema de desarrollo y producción.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# Permisos de acceso a sistemas de archivos

En esta sección se explica cómo configurar el propietario o los propietarios del sistema de archivos Commerce para un sistema de desarrollo y producción. Antes de continuar, revise los conceptos mencionados en [Información general sobre la propiedad y los permisos del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

Este tema se centra en los sistemas de desarrollo y producción de Commerce. Si va a instalar Commerce, consulte [Establecer propiedad y permisos previos a la instalación](../../installation/prerequisites/file-system/configure-permissions.md).

En las secciones siguientes se describen los requisitos de uno o dos propietarios de sistemas de archivos. Esto significa que:

- **Un usuario**: normalmente, es necesario en los proveedores de alojamiento compartido, que permiten acceder a un solo usuario en el servidor. Este usuario puede iniciar sesión, transferir archivos mediante FTP y también ejecuta el servidor web.

- **Dos usuarios**: recomendamos dos usuarios si ejecuta su propio servidor de Commerce: uno para transferir archivos y ejecutar utilidades de línea de comandos y otro para el software del servidor web. Cuando sea posible, es preferible porque es más seguro.

   En su lugar, tiene usuarios independientes:

   - El usuario del servidor web, que ejecuta el administrador y la tienda.

   - A _usuario de línea de comandos_, que es una cuenta de usuario local que puede utilizar para iniciar sesión en el servidor. Este usuario ejecuta trabajos cron de Commerce y utilidades de la línea de comandos.

## Propiedad del sistema de archivos de producción para el alojamiento compartido (un usuario)

Para utilizar la configuración de un solo propietario, debe iniciar sesión en el servidor de Commerce con el mismo usuario que ejecuta el servidor web. Esto suele ocurrir en el alojamiento compartido.

Dado que tener un propietario del sistema de archivos es menos seguro, le recomendamos que implemente Commerce en producción en un servidor privado en lugar de en un alojamiento compartido, si es posible.

### Configurar un propietario para el modo predeterminado o de desarrollador

En modo predeterminado o de desarrollador, el usuario debe poder escribir en los siguientes directorios:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Cualquier otro recurso estático
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Puede establecer estos permisos mediante la línea de comandos o una aplicación de administrador de archivos proporcionada por su proveedor de alojamiento compartido.

### Configuración de un propietario para el modo de producción

Cuando esté listo para implementar el sitio en producción, debe quitar el acceso de escritura de los archivos en los siguientes directorios para mejorar la seguridad:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Cualquier otro recurso estático
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Para actualizar componentes, instalar componentes nuevos o actualizar el software de Commerce, todos los directorios anteriores deben ser de lectura y escritura.

#### Hacer que los archivos y directorios de código sean de sólo lectura

Para quitar permisos de escritura a archivos y directorios del grupo del usuario del servidor web:

1. Inicie sesión en su servidor de Commerce.

1. Cambie al directorio de instalación de Commerce.

1. Cambie al modo de producción.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Quite los permisos de escritura en los siguientes directorios.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Hacer ejecutable la herramienta de línea de comandos.

   ```bash
   chmod u+x bin/magento
   ```

#### Hacer que los archivos y directorios de código puedan escribirse

Para hacer que los archivos y directorios se puedan escribir para poder actualizar los componentes y actualizar el software de Commerce:

1. Inicie sesión en su servidor de Commerce.
1. Cambie al directorio de instalación de Commerce.
1. Introduzca los siguientes comandos:

   ```bash
   chmod -R u+w .
   ```

### Establecido opcionalmente `magento_umask`

Consulte [Si lo desea, puede configurar umask](../../installation/next-steps/set-umask.md) en el _Guía de instalación_.

## Propiedad del sistema de archivos de producción para el alojamiento privado (dos usuarios)

Si utiliza su propio servidor (incluida la configuración del servidor privado de un proveedor de alojamiento), hay dos usuarios:

- El **usuario de servidor web**, que ejecuta el administrador y la tienda.

   Los sistemas Linux no suelen proporcionar un shell para este usuario; no puede iniciar sesión en el servidor de Commerce como usuario del servidor web ni cambiar a él.

- El **usuario de línea de comandos**, con el que inicia sesión en su servidor de Commerce o cambia a.

   Commerce utiliza este usuario para ejecutar comandos de CLI y cron.

   >[!INFO]
   >
   >El usuario de la línea de comandos también se denomina _propietario del sistema de archivos_.

Dado que estos usuarios requieren acceso a los mismos archivos, le recomendamos que cree un [grupo compartido](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) a la que ambos pertenecen. Los siguientes procedimientos suponen que ya lo ha hecho.

Consulte una de las siguientes secciones:

- Dos propietarios del sistema de archivos en modo de desarrollador o predeterminado
- Dos propietarios del sistema de archivos en modo de producción

### Configurar dos propietarios para el modo predeterminado o de desarrollador

Los usuarios deben poder escribir en los archivos de los siguientes directorios en modo de desarrollador y predeterminado:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Configure las variables [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) bits en directorios, por lo que los permisos siempre heredan del directorio principal.

>[!INFO]
>
>`setgid` solo se aplica a los directorios, _no_ a archivos.

Además, el grupo de servidores web debe poder escribir en los directorios. Dado que el contenido puede existir en estos directorios, agregue los permisos de forma recursiva.

#### Definición de permisos y `setgid`

Para establecer `setgid` y permisos para el modo de desarrollador:

1. Inicie sesión en el servidor de Commerce como propietario del sistema de archivos o cambie a.
1. Introduzca los siguientes comandos en el orden mostrado:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Dos propietarios del sistema de archivos en modo de producción

Cuando esté listo para implementar el sitio en producción, debe quitar el acceso de escritura de los archivos en los siguientes directorios para mejorar la seguridad:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Cualquier otro recurso estático
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Hacer que los archivos y directorios de código sean de sólo lectura

Para quitar los permisos de escritura en archivos y directorios del grupo del usuario del servidor web:

1. Inicie sesión en su servidor de Commerce.
1. Cambie al directorio de instalación de Commerce.
1. Como propietario del sistema de archivos, introduzca el siguiente comando para cambiar al modo de producción:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Introduzca el siguiente comando como usuario con `root` privilegios:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Hacer que los archivos y directorios de código puedan escribirse

Para hacer que los archivos y directorios se puedan escribir para poder actualizar los componentes y actualizar el software de Commerce:

1. Inicie sesión en su servidor de Commerce.
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
