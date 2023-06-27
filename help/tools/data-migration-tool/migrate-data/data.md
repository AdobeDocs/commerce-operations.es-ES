---
title: Migración de datos
description: Obtenga información sobre cómo empezar a migrar datos del Magento 1 al Magento 2 con la [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Migración de datos

Antes de empezar, siga estos pasos para prepararse:

1. Inicie sesión en el servidor de aplicaciones como [el propietario del sistema de archivos](../../../installation/prerequisites/file-system/overview.md).
1. Cambie al directorio de instalación de la aplicación o asegúrese de que se agrega al sistema `PATH`.

Consulte la [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecute el comando de migración de datos

Para empezar a migrar datos, ejecute:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-a|--auto]` es un argumento opcional que evita que la migración se detenga cuando encuentre errores de comprobación de integridad.

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a `config.xml`; este argumento es obligatorio

En este paso, la variable [!DNL Data Migration Tool] crea tablas y déclencheur adicionales para las tablas de migración en la base de datos de Magento 1. Se utilizan en el [incremental/delta](delta.md) paso de migración. Las tablas adicionales contienen información sobre los registros modificados después de la ejecución final de la migración. Los déclencheur de base de datos se utilizan para rellenar estas tablas adicionales, por lo que si se está realizando una nueva operación en la tabla concreta (se agrega, modifica o elimina un registro), estos déclencheur de base de datos guardan información sobre esta operación en la tabla adicional. Cuando ejecutamos un proceso de migración delta, la variable [!DNL Data Migration Tool] comprueba si hay registros sin procesar en estas tablas y migra el contenido necesario a la base de datos de Magento 2.

Cada nueva tabla contiene:

* `m2_cl` prefijo
* `INSERT`, `UPDATE`, `DELETE` déclencheur de eventos.

Por ejemplo, para `sales_flat_order` el [!DNL Data Migration Tool] crea:

* `m2_cl_sales_flat_order` tabla:

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` déclencheur:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>El [!DNL Data Migration Tool] guarda su progreso actual mientras se ejecuta. Si hay errores o una intervención del usuario impide que se ejecute, la herramienta reanuda el progreso en el último estado correcto conocido. Para forzar la [!DNL Data Migration Tool] para ejecutar desde el principio, utilice el `--reset` argumento. En ese caso, le recomendamos que restaure el volcado de la base de datos de Magento 2 para evitar la duplicación de datos migrados anteriormente.


## Posibles errores de coherencia

Mientras se ejecuta, la variable [!DNL Data Migration Tool] puede notificar incoherencias entre las bases de datos del Magento 1 y del Magento 2 y mostrar mensajes como los siguientes:

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Consulte la [Solución de problemas](https://support.magento.com/hc/en-us/articles/360033020451) de esta guía para obtener más información y recomendaciones.

## Siguiente paso de migración

[Migrar cambios](delta.md)
