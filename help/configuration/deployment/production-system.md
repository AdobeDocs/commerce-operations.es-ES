---
title: Configuración del sistema de producción
description: Aprenda a configurar un sistema de producción para la aplicación Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Configuración del sistema de producción

Puede tener un sistema de producción. Todo lo siguiente debe ser verdadero:

- Todo el código de comercio está en el control de código fuente en el mismo repositorio que los sistemas de desarrollo y compilación
- Asegúrese de que todos los elementos siguientes sean: _included_ en control de código fuente:

   - `app/etc/config.php`
   - `generated` directorio (y subdirectorios)
   - `pub/media` directory
   - `pub/media/wysiwyg` directorio (y subdirectorios)
   - `pub/static` directorio (y subdirectorios)

- Commerce 2.2 o posterior debe estar instalado y configurado para [modo de producción](../bootstrap/application-modes.md#production-mode)
- Tiene establecidos permisos y propiedad del sistema de archivos como se describe en [Requisito previo para los sistemas de desarrollo, construcción y producción](../deployment/prerequisites.md).

## Configuración de un equipo de producción

Para configurar un equipo de producción:

1. Después de instalar Commerce o de extraerlo del control de código fuente, inicie sesión en el servidor de producción como o cambie a la [propietario del sistema de archivos](https://glossary.magento.com/magento-file-system-owner).
1. Crear `~/.ssh/.composer/auth.json` si aún no lo ha hecho.

   Cree el directorio:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Crear `auth.json` en ese directorio.

   `auth.json` debe contener [claves de autenticación](../../installation/prerequisites/authentication-keys.md).

   A continuación se muestra una muestra:

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Guarde los cambios en `auth.json`.
1. Copiar `<Commerce root dir>/app/etc/env.php` desde su sistema de desarrollo hasta su sistema de producción.
1. Apertura `env.php` en un editor de texto y cambie los valores necesarios (por ejemplo, la información de conexión a la base de datos).
1. Ejecute el [`magento config:set`](../cli/set-configuration-values.md) o [`magento config:set-sensitive`](../cli/set-configuration-values.md) para definir los valores de cualquier valor de configuración sensible o específico del sistema, respectivamente.

   La siguiente sección muestra un ejemplo.

## Establezca los valores de configuración en el sistema de producción

En esta sección se explica cómo configurar valores confidenciales en el sistema de producción utilizando la variable `magento config:sensitive:set` comando.

Para establecer valores confidenciales:

1. Busque un valor para configurar usando la variable [referencia de valor sensible](../reference/config-reference-sens.md).
1. Tenga en cuenta la ruta de configuración de la configuración.
1. Inicie sesión en el sistema de producción como propietario del sistema de archivos o cambie a él.
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Por ejemplo, para establecer el valor de la clave de API de YouTube en `1234`, introduzca

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   También puede definir uno o varios valores de forma interactiva de la siguiente manera:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Cuando se le pida, introduzca un valor para cada configuración confidencial o pulse Intro para omitir un valor y pasar al siguiente.

1. Para comprobar que el valor se ha establecido, inicie sesión en el administrador.
1. Busque la configuración en Administración.

   Por ejemplo, la configuración de la clave de API de YouTube se encuentra en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Catálogo** > **Vídeo del producto**.

   La configuración se muestra en Administración y no se puede editar. La siguiente figura muestra un ejemplo.

   ![Configuración confidencial en la administración](../../assets/configuration/sensitive-set.png)
