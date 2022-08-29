---
title: Migración de datos
description: Obtenga información sobre cómo empezar a migrar datos del Magento 1 al Magento 2 con la variable [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Migración de datos

Antes de empezar, siga los siguientes pasos para prepararse:

1. Inicie sesión en el servidor de aplicaciones como [el propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Cambie al directorio de instalación de la aplicación o asegúrese de que se agrega al sistema `PATH`.

Consulte la [primeros pasos](overview.md#first-steps) para obtener más información.

## Ejecutar el comando de migración de datos

Para empezar a migrar datos, ejecute:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Donde:

* `[-a|--auto]` es un argumento opcional que evita que la migración se detenga cuando encuentra errores de comprobación de integridad.

* `[-r|--reset]` es un argumento opcional que inicia la migración desde el principio. Puede utilizar este argumento para probar la migración.

* `{<path to config.xml>}` es la ruta absoluta del sistema de archivos a `config.xml`; este argumento es obligatorio

Dentro de este paso, la variable [!DNL Data Migration Tool] crea tablas y déclencheur adicionales para las tablas de migración en la base de datos de Magento 1. Se utilizan en la variable [incremental/delta](delta.md) paso de migración. Las tablas adicionales contienen información sobre los registros modificados después de la ejecución de la migración final. Los déclencheur de base de datos se utilizan para rellenar estas tablas adicionales, por lo que si se está realizando una nueva operación en la tabla en particular (se agrega/modifica/elimina un registro), el déclencheur de la base de datos guarda la información sobre esta operación en la tabla adicional. Cuando se ejecuta un proceso de migración delta, la variable [!DNL Data Migration Tool] comprueba estas tablas para los registros no procesados y migra el contenido necesario a la base de datos de Magento 2.

Cada nueva tabla contiene:

* `m2_cl` prefix
* `INSERT`, `UPDATE`, `DELETE` déclencheur de eventos.

Por ejemplo, para la variable `sales_flat_order` el [!DNL Data Migration Tool] crea:

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
>La variable [!DNL Data Migration Tool] guarda el progreso actual mientras se ejecuta. Si los errores o una intervención del usuario impiden que se ejecute, la herramienta reanuda el progreso en el último estado correcto conocido. Para forzar la [!DNL Data Migration Tool] para ejecutar desde el principio, utilice el `--reset` argumento. En ese caso, le recomendamos que restaure el volcado de la base de datos de Magento 2 para evitar la duplicación de los datos migrados anteriormente.


## Posibles errores de coherencia

Mientras se ejecuta, la variable [!DNL Data Migration Tool] pueden informar de incoherencias entre las bases de datos de Magento 1 y Magento 2, y mostrar mensajes como los siguientes:

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

Consulte la [Resolución de problemas](https://support.magento.com/hc/en-us/articles/360033020451) para obtener más información y recomendaciones.

## Siguiente paso de migración

[Migración de cambios](delta.md)
