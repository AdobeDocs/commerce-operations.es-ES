---
title: Instale el [!DNL Data Migration Tool]
description: Obtenga información sobre cómo instalar el [!DNL Data Migration Tool] para transferir datos entre el Magento 1 y el Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---


# Instale el [!DNL Data Migration Tool]

>[!INFO]
>
>Versiones del Magento y [!DNL Data Migration Tool] debe coincidir.


Asegúrese de que está utilizando *la misma versión publicada* del Magento 2 y del [!DNL Data Migration Tool]. Por ejemplo, para la versión 2.2.0 de Magento, también debe usar la variable [!DNL Data Migration Tool] versión 2.2.0.

## Comprobar su versión

Utilice uno de los siguientes métodos para comprobar su versión de Magento:

- [Compositor](#composer-metapackage)
- [Repositorio de GitHub](#github-repository)

### Paquete de metapástasis del Compositor

Si ha descargado el software del Magento mediante un metapaquete del Compositor, introduzca el siguiente comando:

```bash
php <magento_root>/bin/magento --version
```

### Repositorio de GitHub

Si ha clonado el repositorio de GitHub Magento 2, introduzca los siguientes comandos:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Si actualmente está en la `develop` ramificación, debe cambiar a [rama liberada](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) antes de continuar.

Si todavía no ha instalado el software Adobe Commerce o Magento Open Source, [instálela ahora](../../installation/prerequisites/commerce.md).
Si está clonando el repositorio de GitHub, asegúrese de extraer una etiqueta de lanzamiento como se describe en [(Colaborador) Clonar el repositorio de GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Buscar versiones publicadas de [!DNL Data Migration Tool]

Vaya a la [Versiones](https://github.com/magento/data-migration-tool/releases) de [!DNL Data Migration Tool] Repositorio de GitHub para encontrar versiones disponibles.

## Instale el [!DNL Data Migration Tool]

Puede instalar el [!DNL Data Migration Tool] de:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Antes de realizar la instalación, asegúrese de que:

- Se han completado todas las tareas mencionadas en la [Condiciones previas](prerequisites.md) sección
- [Se ha verificado la versión](install.md#check-your-version) del software Magento 2

### Instalar desde `repo.magento.com`

Para instalar el [!DNL Data Migration Tool], debe actualizar `composer.json` en el directorio de instalación raíz del Magento para proporcionar la ubicación de [!DNL Data Migration Tool] paquete.

1. Inicie sesión en el servidor de aplicaciones como, o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
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

1. Cuando se le solicite, introduzca su [claves de autenticación](../../installation/prerequisites/authentication-keys.md). Su clave pública es su nombre de usuario; la clave privada es su contraseña.

### Instalación desde GitHub

Si ha clonado el repositorio de GitHub, siga los pasos a continuación para instalar el [!DNL Data Migration Tool].

1. Inicie sesión en el servidor de aplicaciones como, o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
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

### Comprobar la versión de instalado [!DNL Data Migration Tool]

1. Cambie a su [!DNL Data Migration Tool] directorio: `<vendor>/magento/data-migration-tool`.

1. Apertura [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) en un editor de texto.

1. La variable `version` en ese archivo es la versión de la variable [!DNL Data Migration Tool].
