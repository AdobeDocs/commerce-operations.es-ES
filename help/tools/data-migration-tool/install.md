---
title: Instalar  [!DNL Data Migration Tool]
description: Aprenda a instalar  [!DNL Data Migration Tool]  para transferir datos entre Magento 1 y Magento 2.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Instalar [!DNL Data Migration Tool]

>[!INFO]
>
>Las versiones de Magento y [!DNL Data Migration Tool] deben coincidir.


Asegúrese de que está usando *la misma versión lanzada* de Magento 2 y [!DNL Data Migration Tool]. Por ejemplo, para la versión 2.2.0 de Magento, también debe utilizar la versión 2.2.0 de [!DNL Data Migration Tool].

## Compruebe su versión

Utilice uno de los siguientes métodos para comprobar su versión de Magento:

- [Compositor](#composer-metapackage)
- [Repositorio de GitHub](#github-repository)

### Metapaquete del Compositor

Si ha descargado el software de Magento mediante un metapaquete de Composer, introduzca el siguiente comando:

```bash
php <magento_root>/bin/magento --version
```

### Repositorio de GitHub

Si ha clonado el repositorio de GitHub de Magento 2, introduzca los siguientes comandos:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Si actualmente se encuentra en la rama `develop`, debe cambiar a una [rama liberada](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) antes de continuar.

Si aún no ha instalado el software de Adobe Commerce, [instálelo ahora](../../installation/prerequisites/commerce.md).
Si está clonando el repositorio de GitHub, asegúrese de retirar una etiqueta de versión como se describe en [(Colaborador) Clone el repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Buscar versiones publicadas de [!DNL Data Migration Tool]

Vaya a la página [Versiones](https://github.com/magento/data-migration-tool/releases) del repositorio de GitHub [!DNL Data Migration Tool] para ver las versiones disponibles.

## Instalar [!DNL Data Migration Tool]

Puede instalar [!DNL Data Migration Tool] desde:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Antes de instalar, asegúrese de que dispone de lo siguiente:

- Se han completado todas las tareas mencionadas en la sección [Condiciones previas](prerequisites.md)
- [Comprobó la versión](install.md#check-your-version) del software Magento 2

### Instalar desde `repo.magento.com`

Para instalar [!DNL Data Migration Tool], debe actualizar `composer.json` en el directorio de instalación raíz de Magento para proporcionar la ubicación del paquete [!DNL Data Migration Tool].

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.
1. Cambie al directorio raíz de la aplicación.
1. Introduzca los siguientes comandos:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Donde `<version>` debe coincidir con la versión del código base de Magento 2.

   Por ejemplo, para la versión 2.2.0, introduzca:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Cuando se le solicite, escriba sus [claves de autenticación](../../installation/prerequisites/authentication-keys.md). Su clave pública es su nombre de usuario; su clave privada es su contraseña.

### Instalar desde GitHub

Si ha clonado el repositorio de GitHub, siga los pasos a continuación para instalar [!DNL Data Migration Tool].

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.
1. Cambie al directorio raíz de la aplicación.
1. Introduzca los siguientes comandos:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   donde `<version>` debe coincidir con la versión del código base de Magento 2.

   Por ejemplo, para la versión 2.2.0, introduzca:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Comprobar versión de [!DNL Data Migration Tool] instalado

1. Cambie a su directorio [!DNL Data Migration Tool]: `<vendor>/magento/data-migration-tool`.

1. Abra [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) en un editor de texto.

1. La entrada `version` de ese archivo es la versión de [!DNL Data Migration Tool].
