---
title: Configuración de migración de datos
description: Obtenga información sobre cómo empezar a migrar la configuración del Magento 1 al Magento 2 con  [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Configuración de migración de datos

El modo `Settings` migra tiendas, sitios web y la configuración del sistema, como la configuración de envío, pago e impuestos. Según nuestro pedido [order](overview.md#migration-order) de migración de datos, primero debe migrar la configuración.

Antes de empezar, siga estos pasos para prepararse:

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

1. Cambie al directorio `/bin` o asegúrese de que se agrega a su sistema `PATH`.

>[!NOTE]
>
>Asegúrese de que el Magento 2 se implementa en el modo `default`. El modo de desarrollador puede provocar errores de validación en la herramienta de migración.


Consulte la sección [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecute el comando de migración de configuración

Para empezar a migrar la configuración, ejecute:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración

* `[-a|--auto]` es un argumento opcional que impide que se detenga la migración cuando encuentra errores de comprobación de integridad.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos al archivo [`config.xml`](../configure.md#configure-migration-in-vendor-folder) de la herramienta de migración; este argumento es obligatorio.

>[!NOTE]
>
>Este comando no migra todas las opciones de configuración. Compruebe todas las configuraciones en el administrador de Magento 2 antes de continuar.


El mensaje `Migration completed` se muestra después de que la configuración se transfiera correctamente.

## Configuración de reglas de migración personalizadas

Puede ignorar, cambiar el nombre o cambiar las configuraciones del sistema al migrar configuraciones. Para ello, especifique las reglas personalizadas en el archivo `settings.xml`.

1. Inicie sesión en el servidor de aplicaciones como, o cambie a, [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

1. Cambie al siguiente directorio:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Por ejemplo, si la aplicación está instalada en `/var/www/html`, el archivo `settings.xml.dist` se encuentra en uno de los siguientes directorios:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Para crear un archivo de `settings.xml` a partir del ejemplo proporcionado, ejecute:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Realice los cambios en `settings.xml`.

1. Para especificar el nuevo nombre del archivo de configuración para la asignación, cambie la etiqueta `<settings_map_file>` en el archivo `path/to/config.xml`.

Para obtener más información, consulte la sección [Modo de migración de configuración](../technical-specification.md#settings-migration-mode) de la [especificación](../technical-specification.md) de la herramienta.

## Siguiente paso de migración

* [Migración de datos](data.md)
