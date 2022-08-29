---
title: Actualice el [!DNL Data Migration Tool]
description: Obtenga información sobre cómo actualizar el [!DNL Data Migration Tool] para transferir datos entre el Magento 1 y el Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---


# Actualice el [!DNL Data Migration Tool]

Para asegurarse de que las versiones de la instalación actual del Magento 2 y la [!DNL Data Migration Tool] coincida exactamente, es posible que tenga que actualizar la herramienta.

## Requisitos previos

Antes de actualizar la variable [!DNL Data Migration Tool], debe:

* Actualice el software del Magento para obtener la versión más reciente

* Haga una copia de seguridad de `vendor/magento/data-migration-tool` directory

* Asegúrese de que la variable [!DNL Data Migration Tool] la versión coincide con la versión de la aplicación Magento

### Actualice el software del Magento

Si aún no lo ha hecho, [actualizar el software del Magento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html).

### Haga una copia de seguridad de `vendor/magento/data-migration-tool` directory

Antes de actualizar la variable [!DNL Data Migration Tool], haga una copia de seguridad de al menos `vendor/magento/data-migration-tool` directorio. Durante la actualización, se puede eliminar y reemplazar con el código actualizado.

También puede realizar una copia de seguridad de toda la base de datos del Magento mediante el siguiente comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>La variable `vendor/magento/data-migration-tool` contiene el código personalizado. Si no realiza la copia de seguridad, puede perder las personalizaciones durante la actualización.


### Asegúrese de que las versiones coincidan

Las versiones de [!DNL Data Migration Tool] y su software Magento debe coincidir exactamente. Por ejemplo, el Magento 2.1.2 requiere la versión 2.1.2 del [!DNL Data Migration Tool].

Consulte la [Instalar [!DNL Data Migration Tool]](install.md) tema para saber cómo:

* [Marque](install.md#check-your-version) su versión de Magento 2

* [Buscar](install.md#find-released-versions-of-data-migration-tool) versiones publicadas de [!DNL Data Migration Tool]

* [Marque](install.md#check-version-of-installed-data-migration-tool) el [!DNL Data Migration Tool] version

## Actualice el [!DNL Data Migration Tool]

1. Inicie sesión en el servidor Magento como o cambie a [el propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Cambie al directorio raíz del Magento 2.
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
