---
title: Permisos de acceso de sistemas de archivos
description: Consulte cómo configurar el propietario o los propietarios del sistema de archivos de la aplicación Commerce para un sistema de desarrollo y producción.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# Permisos de acceso de sistemas de archivos

En esta sección se explica cómo configurar el propietario o los propietarios del sistema de archivos de comercio para un sistema de desarrollo y producción. Antes de continuar, revise los conceptos mencionados en [Información general sobre la propiedad y los permisos del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

Este tema se centra en el desarrollo del comercio y los sistemas de producción. Si va a instalar Commerce, consulte [Establezca la propiedad y los permisos previos a la instalación](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

En las secciones siguientes se analizan los requisitos para uno o dos propietarios de sistemas de archivos. Esto significa que:

- **Un usuario**—Normalmente es necesario en proveedores de alojamiento compartidos, que permiten acceder a un solo usuario en el servidor. Este usuario puede iniciar sesión, transferir archivos mediante FTP y también ejecutar el servidor web.

- **Dos usuarios**—Recomendamos dos usuarios si ejecuta su propio servidor de comercio: uno para transferir archivos y ejecutar utilidades de línea de comandos, y un usuario separado para el software del servidor web. Cuando es posible, esto es preferible porque es más seguro.

   En su lugar, tiene usuarios separados:

   - El usuario del servidor web, que ejecuta el Administrador y la tienda.

   - A _usuario de línea de comandos_, que es una cuenta de usuario local que puede utilizar para iniciar sesión en el servidor. Este usuario ejecuta trabajos de Commerce cron y utilidades de línea de comandos.

## Propiedad del sistema de archivos de producción para el alojamiento compartido (un usuario)

Para utilizar la configuración de un propietario, debe iniciar sesión en el servidor de comercio como el mismo usuario que ejecuta el servidor web. Esto es típico del alojamiento compartido.

Dado que tener un propietario de sistema de archivos es menos seguro, le recomendamos que implemente Commerce en producción en un servidor privado en lugar de en alojamiento compartido, si es posible.

### Configurar un propietario para el modo predeterminado o del desarrollador

En modo predeterminado o de desarrollador, el usuario debe poder escribir los siguientes directorios:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Cualquier otro recurso estático
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Puede configurar estos permisos utilizando la línea de comandos o una aplicación del administrador de archivos proporcionada por su proveedor de alojamiento compartido.

### Configurar un propietario para el modo de producción

Cuando esté listo para implementar su sitio en producción, debe eliminar el acceso de escritura de los archivos en los siguientes directorios para mejorar la seguridad:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Cualquier otro recurso estático
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Para actualizar componentes, instalar nuevos componentes o actualizar el software Commerce, todos los directorios anteriores deben ser de lectura y escritura.

#### Conversión de archivos de código y directorios en solo lectura

Para eliminar los permisos de escritura de archivos y directorios del grupo del usuario del servidor web:

1. Inicie sesión en su servidor de comercio.

1. Cambie al directorio de instalación de Commerce.

1. Cambie al modo de producción.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Elimine los permisos de escritura en los siguientes directorios.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Haga que la herramienta de línea de comandos sea ejecutable.

   ```bash
   chmod u+x bin/magento
   ```

#### Hacer que los archivos de código y los directorios sean grabables

Para hacer que los archivos y directorios sean grabables para que pueda actualizar los componentes y el software Commerce:

1. Inicie sesión en su servidor de comercio.
1. Cambie al directorio de instalación de Commerce.
1. Introduzca los siguientes comandos:

   ```bash
   chmod -R u+w .
   ```

### Configurado de forma opcional `magento_umask`

Consulte [Configuración opcional de una máscara](https://devdocs.magento.com/guides/v2.4/install-gde/install/post-install-umask.html) en el _Guía de instalación_.

## Propiedad del sistema de archivos de producción para alojamiento privado (dos usuarios)

Si utiliza su propio servidor (incluida la configuración del servidor privado de un proveedor de alojamiento), hay dos usuarios:

- La variable **usuario del servidor web**, que ejecuta el Administrador y la tienda.

   Los sistemas Linux normalmente no proporcionan un shell para este usuario; no puede iniciar sesión en el servidor de comercio como usuario del servidor web ni cambiarlo a.

- La variable **usuario de línea de comandos**, que inicia sesión en su servidor de Commerce como o cambia a .

   Commerce utiliza este usuario para ejecutar comandos CLI y cron.

   >[!INFO]
   >
   >El usuario de la línea de comandos también se denomina _propietario del sistema de archivos_.

Dado que estos usuarios necesitan acceder a los mismos archivos, le recomendamos que cree un [grupo compartido](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html#mage-owner-about-group) a los que ambos pertenecen. Los siguientes procedimientos suponen que ya ha hecho esto.

Consulte una de las siguientes secciones:

- Dos propietarios de sistemas de archivos en el modo de desarrollador o predeterminado
- Dos propietarios de sistemas de archivos en modo de producción

### Configuración de dos propietarios para el modo predeterminado o del desarrollador

Los archivos de los siguientes directorios deben ser grabables por ambos usuarios en el modo de desarrollador y por defecto:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Configure las variables [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) bit en los directorios para que los permisos siempre hereden del directorio principal.

>[!INFO]
>
>`setgid` se aplica solo a los directorios, _not_ a archivos.

Además, el grupo de servidores web debe poder escribir en los directorios. Dado que el contenido puede existir en estos directorios, agregue los permisos recursivamente.

#### Establezca permisos y `setgid`

Para configurar `setgid` y permisos para el modo de desarrollador:

1. Inicie sesión en el servidor de Commerce como propietario del sistema de archivos o cambie a .
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

### Dos propietarios de sistemas de archivos en modo de producción

Cuando esté listo para implementar su sitio en producción, debe eliminar el acceso de escritura de los archivos en los siguientes directorios para mejorar la seguridad:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Cualquier otro recurso estático
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Conversión de archivos de código y directorios en solo lectura

Para eliminar los permisos de escritura para archivos y directorios del grupo del usuario del servidor web:

1. Inicie sesión en su servidor de comercio.
1. Cambie al directorio de instalación de Commerce.
1. Como propietario del sistema de archivos, introduzca el siguiente comando para cambiar al modo de producción:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Introduzca el siguiente comando como usuario con `root` privilegios:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Hacer que los archivos de código y los directorios sean grabables

Para hacer que los archivos y directorios sean grabables para que pueda actualizar los componentes y el software Commerce:

1. Inicie sesión en su servidor de comercio.
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
