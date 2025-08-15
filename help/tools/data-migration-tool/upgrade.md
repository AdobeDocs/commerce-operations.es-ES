---
title: Actualizar  [!DNL Data Migration Tool]
description: Aprenda a actualizar  [!DNL Data Migration Tool] para transferir datos entre Magento 1 y Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Actualizar [!DNL Data Migration Tool]

Para asegurarse de que las versiones de la instalación actual de Magento 2 y de [!DNL Data Migration Tool] coinciden exactamente, es posible que tenga que actualizar la herramienta.

## Requisitos previos

Antes de actualizar [!DNL Data Migration Tool], debe:

* Actualice el software de Magento para obtener la versión más reciente

* Hacer una copia de seguridad del directorio `vendor/magento/data-migration-tool`

* Asegúrese de que la versión de [!DNL Data Migration Tool] coincida con la versión de la aplicación de Magento

### Actualización del software de Magento

Si aún no lo ha hecho, [actualice el software de Magento](../../upgrade/overview.md).

### Hacer una copia de seguridad del directorio `vendor/magento/data-migration-tool`

Antes de actualizar [!DNL Data Migration Tool], haga una copia de seguridad del directorio `vendor/magento/data-migration-tool` como mínimo. Durante la actualización, se podía eliminar y reemplazar por el código actualizado.

También puede realizar una copia de seguridad de toda la base de código y la base de datos de Magento mediante el siguiente comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>El directorio `vendor/magento/data-migration-tool` contiene su código personalizado. Si no realiza una copia de seguridad, puede perder las personalizaciones durante la actualización.


### Comprobar que las versiones coinciden

Las versiones de [!DNL Data Migration Tool] y del software de Magento deben coincidir exactamente. Por ejemplo, Magento 2.1.2 requiere la versión 2.1.2 de [!DNL Data Migration Tool].

Consulte el tema [Instalar [!DNL Data Migration Tool]](install.md) para saber cómo:

* [Comprueba](install.md#check-your-version) tu versión de Magento 2

* [Buscar](install.md#find-released-versions-of-data-migration-tool) versiones publicadas de [!DNL Data Migration Tool]

* [Comprobar](install.md#check-version-of-installed-data-migration-tool) la versión de [!DNL Data Migration Tool]

## Actualizar [!DNL Data Migration Tool]

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.
1. Cambie al directorio raíz de la aplicación.
1. Introduzca el siguiente comando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   donde `<version>` debe coincidir con la versión del código base de Magento 2.

   Por ejemplo, para la versión 2.1.2, introduzca:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Espere mientras se completa el comando.
