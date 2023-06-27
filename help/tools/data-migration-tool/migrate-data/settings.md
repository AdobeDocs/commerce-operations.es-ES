---
title: Configuración de migración de datos
description: Obtenga información sobre cómo empezar a migrar configuraciones del Magento 1 al Magento 2 con [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Configuración de migración de datos

El `Settings` Este modo migra tiendas, sitios web y la configuración del sistema, como los ajustes de envío, pago e impuestos. Según nuestra migración de datos [pedido](overview.md#migration-order), primero debe migrar la configuración.

Antes de empezar, siga estos pasos para prepararse:

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

1. Cambie a la `/bin` o asegúrese de que se añade al sistema `PATH`.

>[!NOTE]
>
>Asegúrese de que el Magento 2 se implementa en `default` modo. El modo de desarrollador puede provocar errores de validación en la herramienta de migración.


Consulte la [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecute el comando de migración de configuración

Para empezar a migrar la configuración, ejecute:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración

* `[-a|--auto]` es un argumento opcional que evita que la migración se detenga cuando encuentre errores de comprobación de integridad.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a la [`config.xml`](../configure.md#configure-migration-in-vendor-folder) file; este argumento es obligatorio.

>[!NOTE]
>
>Este comando no migra todas las opciones de configuración. Compruebe todas las configuraciones en el administrador de Magento 2 antes de continuar.


El `Migration completed` El mensaje se muestra después de que la configuración se transfiera correctamente.

## Configuración de reglas de migración personalizadas

Puede ignorar, cambiar el nombre o cambiar las configuraciones del sistema al migrar configuraciones. Para ello, especifique las reglas personalizadas en la variable `settings.xml` archivo.

1. Inicie sesión en el servidor de aplicaciones como, o cambie a, [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

1. Cambie al siguiente directorio:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Por ejemplo, si la aplicación está instalada en `/var/www/html`, el `settings.xml.dist` está en uno de los siguientes directorios:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Para crear un `settings.xml` en el ejemplo proporcionado, ejecute:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Realice los cambios en `settings.xml`.

1. Para especificar el nuevo nombre del archivo de configuración para la asignación, cambie el `<settings_map_file>` etiqueta en el `path/to/config.xml` archivo.

Para obtener más información, consulte la [Modo de migración de configuración](../technical-specification.md#settings-migration-mode) de la sección de la herramienta [especificación](../technical-specification.md).

## Siguiente paso de migración

* [Migración de datos](data.md)
