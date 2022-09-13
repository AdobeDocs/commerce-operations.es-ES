---
title: Clonar datos de ejemplo en repositorios Git
description: Siga estos pasos para instalar Adobe Commerce y los datos de ejemplo del Magento Open Source mediante la clonación de repositorios Git.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# Clonar datos de ejemplo en repositorios Git

En este tema se explica cómo clonar y añadir datos de ejemplo si ha clonado el repositorio de GitHub Magento Open Source. Este método solo está diseñado para desarrolladores que contribuyan (es decir, desarrolladores que planeen contribuir al código base del Magento Open Source).

Si no es un desarrollador colaborador, elija una de las otras opciones mostradas en la tabla de contenido en la parte izquierda de la página.

Los desarrolladores colaboradores pueden utilizar este método para instalar datos de ejemplo *only* si el siguiente es true:

* Utiliza el Magento Open Source
* You [clonó el repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Puede utilizar datos de ejemplo con `develop` rama (más actual) o una rama liberada (como `2.4` (más estable). Le recomendamos que utilice una rama liberada porque es más estable. Si va a contribuir con código al repositorio y necesita el código más reciente, use el `develop` rama. Independientemente de la rama que elija, debe [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) la rama correspondiente del repositorio de GitHub Magento Open Source. Por ejemplo, datos de ejemplo para la variable `develop` se puede usar la rama *only* con el Magento Open Source `develop` rama.

## Clonar el repositorio de datos de ejemplo

En esta sección se explica cómo instalar datos de ejemplo clonando el repositorio de datos de ejemplo. Puede clonar el repositorio de datos de ejemplo de cualquiera de estas formas:

* Clonar con la variable [Protocolo SSH](#clone-with-ssh)
* Clonar con la variable [Protocolo HTTPS](#clone-with-https)

### Clonar con SSH

Para clonar el repositorio de GitHub de datos de muestra mediante el protocolo SSH:

1. En un explorador web, vaya a la [repositorio de datos de ejemplo](https://github.com/magento/magento2-sample-data).
1. Junto al nombre de la rama, haga clic en **SSH** de la lista.
1. Haga clic en **Copiar al portapapeles**

   La siguiente figura muestra un ejemplo.

   ![Clonar el repositorio de GitHub mediante SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Cambie al directorio docroot del servidor web.

   Normalmente, para Ubuntu, es `/var/www` y para CentOS es `/var/www/html`.

1. Entrar `git clone` y pegue el valor que ha obtenido anteriormente.

   A continuación se muestra un ejemplo:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Espere a que el repositorio clone en el servidor.

   >[!NOTE]
   >
   >Si aparece el siguiente error, asegúrese de que [compartió su clave SSH](https://docs.github.com/articles/generating-ssh-keys/) con GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Asegúrese de extraer la rama del repositorio de datos de ejemplo que corresponde a la rama utilizada desde la rama principal `magento2` repositorio.

   Por ejemplo:

   Si ha utilizado la variable `2.4-develop` rama del repositorio Magento Open Source de GitHub, la rama de datos de ejemplo debe ser `2.4-develop`.

   Si ha utilizado la variable `2.4.3` rama del repositorio Magento Open Source de GitHub, la rama de datos de ejemplo debe ser `2.4.3`.

   Para extraer la rama correcta, ejecute el siguiente comando desde el directorio raíz del repositorio de datos de ejemplo (suponiendo que necesite el `2.4.3` rama):

   ```bash
   git checkout 2.4.3
   ```

1. Cambiar a `<app_root>`.
1. Introduzca el siguiente comando para crear vínculos simbólicos entre los archivos que ha clonado para que los datos de ejemplo funcionen correctamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Espere a que se complete el comando.

1. Consulte [Definir permisos y propiedad del sistema de archivos](#set-file-system-ownership-and-permissions).

1. Ejecute el siguiente comando:

   ```bash
   bin/magento setup:upgrade
   ```

### Clone con HTTPS

Para clonar el repositorio de GitHub de datos de ejemplo mediante el protocolo HTTPS:

1. En un explorador web, vaya a la [repositorio de datos de ejemplo](https://github.com/magento/magento2-sample-data).
1. En el lado derecho de la página, debajo de la sección **clonar URL** , haga clic en **HTTPS**.
1. Haga clic en **Copiar al portapapeles**.

   La siguiente figura muestra un ejemplo.

   ![Clonar el repositorio de GitHub mediante HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Cambie al directorio docroot del servidor web.

   Normalmente, para Ubuntu, es `/var/www` y para CentOS es `/var/www/html`.

1. Entrar `git clone` y pegue el valor que ha obtenido anteriormente.

   A continuación se muestra un ejemplo:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Espere a que el repositorio clone en el servidor.
1. Asegúrese de extraer la rama del repositorio de datos de ejemplo que corresponde a la rama utilizada desde la rama principal `magento2` repositorio.

   Por ejemplo:

   Si ha utilizado la variable `2.4-develop` rama del repositorio Magento Open Source de GitHub, la rama de datos de ejemplo debe ser `2.4-develop`.

   Si ha utilizado la variable `2.4.3` rama del repositorio Magento Open Source de GitHub, la rama de datos de ejemplo debe ser `2.4.3`.

   Para extraer la rama correcta, ejecute el siguiente comando desde el directorio raíz del repositorio de datos de ejemplo (suponiendo que necesite el `2.4.3` rama):

   ```bash
   git checkout 2.4.3
   ```

1. Cambiar a `<magento_root>`.
1. Introduzca el siguiente comando para crear vínculos simbólicos entre los archivos que ha clonado para que los datos de ejemplo funcionen correctamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Por ejemplo,

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Espere a que se complete el comando.
1. Consulte la siguiente sección.

>[!WARNING]
>
>Si va a instalar datos de ejemplo *after* al instalar Adobe Commerce o Magento Open Source, también debe ejecutar el siguiente comando para actualizar la base de datos y el esquema:
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## Establezca la propiedad y los permisos del sistema de archivos

Porque la variable `php build-sample-data.php` crea enlaces simbólicos entre el repositorio de datos de ejemplo y el repositorio de Magento Open Source, debe establecer los permisos y la propiedad del sistema de archivos en el repositorio de datos de ejemplo. Si no lo hace, se producen errores al acceder a la tienda.

Para establecer los permisos y la propiedad del sistema de archivos en el repositorio de datos de ejemplo:

1. Cambie al directorio de clonación de datos de ejemplo.
1. Establezca la propiedad:

   ```bash
   chown -R :<your web server group name> .
   ```

   Ejemplos habituales:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Definir permisos:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Borrar archivos estáticos:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Completar la instalación de datos de ejemplo

{{$include /help/_includes/sample-data-complete.md}}
