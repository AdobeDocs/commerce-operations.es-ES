---
title: Configuración del sistema de producción
description: Obtenga información sobre cómo configurar un sistema de producción para la aplicación Commerce.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Configuración del sistema de producción

Puede tener un sistema de producción. Todo lo siguiente debe ser verdadero:

- Todo el código Commerce se encuentra en control de código fuente en el mismo repositorio que los sistemas de desarrollo y compilación
- Asegúrese de que todas las opciones siguientes son _incluido_ en el control de código fuente:

   - `app/etc/config.php`
   - `generated` directorio (y subdirectorios)
   - `pub/media` directorio
   - `pub/media/wysiwyg` directorio (y subdirectorios)
   - `pub/static` directorio (y subdirectorios)

- Commerce 2.2 o posterior debe estar instalado y configurado para [modo de producción](../bootstrap/application-modes.md#production-mode)
- Tiene la propiedad del sistema de archivos y los permisos establecidos, tal como se describe en [Requisito previo para los sistemas de desarrollo, compilación y producción](../deployment/prerequisites.md).

## Configurar una máquina de producción

Para configurar una máquina de producción:

1. Después de instalar Commerce o extraerlo del control de código fuente, inicie sesión en el servidor de producción como propietario del sistema de archivos o cambie a.
1. Crear `~/.ssh/.composer/auth.json` si aún no lo ha hecho.

   Cree el directorio:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Crear `auth.json` en ese directorio.

   `auth.json` debe contener su [claves de autenticación](../../installation/prerequisites/authentication-keys.md).

   A continuación se muestra un ejemplo:

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

1. Guardar los cambios en `auth.json`.
1. Copiar `<Commerce root dir>/app/etc/env.php` de su sistema de desarrollo a su sistema de producción.
1. Abrir `env.php` en un editor de texto y cambie los valores necesarios (por ejemplo, la información de conexión a base de datos).
1. Ejecute el [`magento config:set`](../cli/set-configuration-values.md) o [`magento config:set-sensitive`](../cli/set-configuration-values.md) para establecer los valores de cualquier valor de configuración sensible o específico del sistema, respectivamente.

   La siguiente sección muestra un ejemplo.

## Establezca los valores de configuración en el sistema de producción

En esta sección se explica cómo configurar valores confidenciales en el sistema de producción mediante `magento config:sensitive:set` comando.

Para establecer valores confidenciales:

1. Busque un valor que establecer con la variable [referencia de valor confidencial](../reference/config-reference-sens.md).
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

   También puede establecer uno o más valores de forma interactiva de la siguiente manera:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Cuando se le solicite, introduzca un valor para cada configuración confidencial o pulse Entrar para omitir un valor y pasar al siguiente.

1. Para comprobar que el valor se ha establecido, inicie sesión en el administrador.
1. Busque la configuración en el Administrador.

   Por ejemplo, la configuración de clave de API de YouTube se encuentra en **Tiendas** > Configuración > **Configuración** > **Catálogo** > **Catálogo** > **Vídeo del producto**.

   La configuración se muestra en el Administrador y no se puede editar. La siguiente figura muestra un ejemplo.

   ![Configuración confidencial en el administrador](../../assets/configuration/sensitive-set.png)
