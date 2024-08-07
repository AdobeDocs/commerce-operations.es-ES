---
title: Configurar la propiedad y los permisos del archivo
description: Siga estos pasos para configurar permisos del sistema de archivos para instalaciones locales de Adobe Commerce.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Configurar la propiedad y los permisos del archivo

En este tema se explica cómo establecer permisos de lectura y escritura para el grupo de servidores web antes de instalar Adobe Commerce. Esto es necesario para que la línea de comandos pueda escribir archivos en el sistema de archivos.

El procedimiento que utilice es diferente, dependiendo de si usa [alojamiento compartido](#set-permissions-for-one-user-on-shared-hosting) y tiene un usuario o si usa un [servidor privado](#set-ownership-and-permissions-for-two-users) y tiene dos usuarios.

## Definir permisos para un usuario en un alojamiento compartido

En esta sección se explica cómo establecer permisos previos a la instalación si inicia sesión en el servidor de aplicaciones con el mismo usuario que también ejecuta el servidor web. Este tipo de configuración es común en entornos de alojamiento compartido.

Para establecer permisos antes de instalar la aplicación:

1. Inicie sesión en el servidor de aplicaciones.
1. Utilice una aplicación de administrador de archivos proporcionada por el proveedor de alojamiento compartido para comprobar que los permisos de escritura están establecidos en los siguientes directorios:

   * `vendor` (instalación del compositor o del archivo comprimido)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Cualquier otro recurso estático

1. Si tiene acceso desde la línea de comandos, introduzca los siguientes comandos en el orden mostrado:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Para especificar opcionalmente todos los comandos en una línea, escriba lo siguiente suponiendo que la aplicación esté instalada en `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Si aún no lo ha hecho, obtenga la aplicación de una de las siguientes maneras:

   * [Metapaquete del Compositor](../../composer.md)
   * [Clonar el repositorio (solo desarrolladores colaboradores)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Después de establecer la propiedad y los permisos del sistema de archivos, [instale la aplicación](../../advanced.md)

>[!NOTE]
>
>Para restringir aún más los permisos después de instalar la aplicación, puede [configurar una máscara de usuario](../../next-steps/set-umask.md).

## Establecer la propiedad y los permisos para dos usuarios

En esta sección se explica cómo establecer la propiedad y los permisos para su propio servidor o para una configuración de alojamiento privada. En este tipo de configuración, normalmente *no puede* iniciar sesión como usuario del servidor web o cambiar a él. Normalmente, se inicia sesión como un usuario y se ejecuta el servidor web como un usuario diferente.

Para establecer la propiedad y los permisos para un sistema de dos usuarios:

Complete las siguientes tareas en el orden mostrado:

* [Acerca del grupo compartido](#about-the-shared-group)
* [Cree el propietario del sistema de archivos y proporcione al usuario una contraseña segura](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Busque el grupo del usuario del servidor web](#find-the-web-server-user-group)
* [Coloque el propietario del sistema de archivos en el grupo de servidores web](#put-the-file-system-owner-in-the-web-server-group)
* [Obtener el software](#get-the-software)
* [Establecer la propiedad y los permisos para el grupo compartido](#set-ownership-and-permissions-for-the-shared-group)

### Acerca del grupo compartido

Para permitir que el servidor web escriba archivos y directorios en el sistema de archivos, pero también para mantener la *propiedad* del propietario del sistema de archivos, ambos usuarios deben estar en el mismo grupo. Esto es necesario para que ambos usuarios puedan compartir el acceso a los archivos (incluidos los archivos creados con el administrador u otras utilidades basadas en la web).

En esta sección se explica cómo crear un propietario del sistema de archivos y colocar a ese usuario en el grupo del servidor web. Si lo desea, puede utilizar una cuenta de usuario existente; por motivos de seguridad, le recomendamos que disponga de una contraseña segura.

>[!NOTE]
>
>Pase a [Buscar el grupo de usuarios del servidor web](#find-the-web-server-user-group) si planea usar una cuenta de usuario existente.

### Cree el propietario del sistema de archivos y proporcione al usuario una contraseña segura

En esta sección se explica cómo crear el propietario del sistema de archivos. (el propietario del sistema de archivos es otro término para *usuario de línea de comandos*.)

Para crear un usuario en CentOS o Ubuntu, introduzca el siguiente comando como usuario con privilegios de `root`:

```bash
adduser <username>
```

Para dar al usuario una contraseña, escriba el siguiente comando como usuario con privilegios de `root`:

```bash
passwd <username>
```

Siga las indicaciones de la pantalla para crear una contraseña de usuario.

>[!WARNING]
>
>Si no tiene privilegios de `root` en el servidor de aplicaciones, puede utilizar otra cuenta de usuario local. Asegúrese de que el usuario tenga una contraseña segura y continúe con [Coloque al propietario del sistema de archivos en el grupo de servidores web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Por ejemplo, para crear un usuario denominado `magento_user` y darle una contraseña, escriba:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Dado que el objetivo de crear este usuario es proporcionar seguridad adicional, asegúrese de crear una [contraseña segura](https://en.wikipedia.org/wiki/Password_strength).

### Búsqueda del grupo de usuarios del servidor web

Para buscar el grupo del usuario del servidor web:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  o

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

Normalmente, el nombre de usuario y el nombre de grupo son `apache`.

* Ubuntu: `ps aux | grep apache` para encontrar el usuario Apache y `groups <apache user>` para encontrar el grupo.

Normalmente, el nombre de usuario y el nombre de grupo son `www-data`.

### Coloque el propietario del sistema de archivos en el grupo de servidores web

Para colocar al propietario del sistema de archivos en el grupo principal del servidor web (suponiendo el nombre de grupo Apache típico para CentOS y Ubuntu), introduzca el siguiente comando como usuario con privilegios `root`:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>Las opciones de `-a -G` son importantes porque agregan `apache` o `www-data` como un grupo *secundario* a la cuenta de usuario, lo que conserva el grupo *principal* del usuario. Añadir un grupo secundario a una cuenta de usuario ayuda a [restringir la propiedad y los permisos de los archivos](#set-ownership-and-permissions-for-two-users) para garantizar que los miembros de un grupo compartido solo tengan acceso a ciertos archivos.

Por ejemplo, para agregar el usuario `magento_user` al grupo principal `apache` en CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Para confirmar que el usuario es miembro del grupo de servidores web, introduzca el siguiente comando:

```bash
groups magento_user
```

El siguiente resultado de ejemplo muestra los grupos principal (`magento`) y secundario (`apache`) del usuario.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Normalmente, el nombre de usuario y el nombre del grupo principal son el mismo.

Para completar la tarea, reinicie el servidor web:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Obtener el software

Si aún no lo ha hecho, obtenga el software de una de las siguientes maneras:

* [Metapaquete del Compositor](../../composer.md)
* [Clonar el repositorio (solo desarrolladores colaboradores)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Establecer la propiedad y los permisos para el grupo compartido

Para establecer la propiedad y los permisos antes de instalar la aplicación:

1. Inicie sesión en el servidor de aplicaciones como propietario del sistema de archivos o cambie a.
1. Introduzca los siguientes comandos en el orden mostrado:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Para especificar opcionalmente todos los comandos en una línea, escriba lo siguiente suponiendo que la aplicación esté instalada en `/var/www/html/magento2` y que el nombre del grupo de servidores web sea `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

En el sistema de archivos de evento, los permisos se establecen incorrectamente y el propietario del sistema de archivos no puede cambiarlos. Puede escribir el comando como usuario con privilegios de `root`:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Cambiar al propietario del sistema de archivos

Después de haber realizado las demás tareas de este tema, escriba uno de los siguientes comandos para cambiar a ese usuario:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Por ejemplo,

```bash
su magento_user
```
