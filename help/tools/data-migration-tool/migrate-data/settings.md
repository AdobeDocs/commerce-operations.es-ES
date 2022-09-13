---
title: Configuración de migración de datos
description: Obtenga información sobre cómo empezar a migrar la configuración de Magento 1 a Magento 2 con la variable [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


# Configuración de migración de datos

La variable `Settings` migra tiendas, sitios web y configuración del sistema como los ajustes de envío, pago e impuestos. Según nuestra migración de datos [pedido](overview.md#migration-order), primero debe migrar la configuración.

Antes de empezar, siga los siguientes pasos para prepararse:

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

1. Cambie a la función `/bin` o asegúrese de que se agrega al sistema `PATH`.

>[!NOTE]
>
>Asegúrese de que el Magento 2 esté implementado en `default` en el menú contextual. El modo de desarrollador puede provocar errores de validación en la herramienta de migración.


Consulte la [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecutar el comando de migración de configuración

Para iniciar la migración de la configuración, ejecute:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración

* `[-a|--auto]` es un argumento opcional que evita que la migración se detenga cuando encuentra errores de comprobación de integridad.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a la herramienta de migración [`config.xml`](../configure.md#configure-migration-in-vendor-folder) archivo; este argumento es obligatorio.

>[!NOTE]
>
>Este comando no migra todos los ajustes de configuración. Verificar todas las configuraciones en el Magento 2 [Administrador](https://glossary.magento.com/admin) antes de continuar.


La variable `Migration completed` se muestra una vez transferida correctamente la configuración.

## Configuración de reglas de migración personalizadas

Puede ignorar, cambiar el nombre o cambiar las configuraciones del sistema al migrar la configuración. Para ello, especifique las reglas personalizadas en la `settings.xml` archivo.

1. Inicie sesión en el servidor de aplicaciones como o cambie a la [propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).

1. Cambie al siguiente directorio:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Por ejemplo, si la aplicación está instalada en `/var/www/html`, el `settings.xml.dist` está en uno de los siguientes directorios:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Para crear un `settings.xml` del ejemplo proporcionado, ejecute:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Realice los cambios en `settings.xml`.

1. Para especificar el nuevo nombre del archivo de configuración para la asignación, cambie la variable `<settings_map_file>` en el `path/to/config.xml` archivo.

Para obtener más información, consulte la [Modo de migración de configuración](../technical-specification.md#settings-migration-mode) de la sección [especificación](../technical-specification.md).

## Siguiente paso de migración

* [Migración de datos](data.md)
