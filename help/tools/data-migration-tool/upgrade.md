---
title: Actualice el [!DNL Data Migration Tool]
description: Obtenga información sobre cómo actualizar el [!DNL Data Migration Tool] para transferir datos entre Magento 1 y Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Actualice el [!DNL Data Migration Tool]

Para asegurarse de que las versiones de la instalación actual de Magento 2 y [!DNL Data Migration Tool] coincida exactamente con, es posible que tenga que actualizar la herramienta.

## Requisitos previos

Antes de actualizar el [!DNL Data Migration Tool], debe:

* Actualice el software de Magento para obtener la versión más reciente

* Haga una copia de seguridad del `vendor/magento/data-migration-tool` directorio

* Asegúrese de que la variable [!DNL Data Migration Tool] La versión coincide con la versión de la aplicación Magento

### Actualización del software de Magento

Si aún no lo ha hecho, [actualizar el software del Magento](../../upgrade/overview.md).

### Haga una copia de seguridad del `vendor/magento/data-migration-tool` directorio

Antes de actualizar el [!DNL Data Migration Tool], haga una copia de seguridad al menos del `vendor/magento/data-migration-tool` directorio. Durante la actualización, se podía eliminar y reemplazar por el código actualizado.

También puede realizar una copia de seguridad de todo el código base del Magento y de la base de datos mediante el siguiente comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>El `vendor/magento/data-migration-tool` contiene su código personalizado. Si no realiza una copia de seguridad, puede perder las personalizaciones durante la actualización.


### Comprobar que las versiones coinciden

Las versiones de la [!DNL Data Migration Tool] y el software del Magento debe coincidir exactamente. Por ejemplo, el Magento 2.1.2 requiere la versión 2.1.2 del [!DNL Data Migration Tool].

Consulte la [Instalar [!DNL Data Migration Tool]](install.md) tema para saber cómo:

* [Marque](install.md#check-your-version) su versión de Magento 2

* [Buscar](install.md#find-released-versions-of-data-migration-tool) versiones publicadas de [!DNL Data Migration Tool]

* [Marque](install.md#check-version-of-installed-data-migration-tool) el [!DNL Data Migration Tool] version

## Actualice el [!DNL Data Migration Tool]

1. Inicie sesión en el servidor de aplicaciones como o cambie a, [el propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Cambie al directorio raíz de la aplicación.
1. Introduzca el siguiente comando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   donde `<version>` debe coincidir con la versión del código de base de Magento 2.

   Por ejemplo, para la versión 2.1.2, introduzca:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Espere mientras se completa el comando.
