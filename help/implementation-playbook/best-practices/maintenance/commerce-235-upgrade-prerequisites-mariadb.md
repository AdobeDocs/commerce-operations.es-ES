---
title: Requisitos previos de actualización de Adobe Commerce 2.3.5 para MariaDB
description: Obtenga información sobre cómo preparar la base de datos de Adobe Commerce para la actualización desde Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Requisitos previos de la actualización a Adobe Commerce 2.3.5

Este artículo explica cómo preparar la base de datos al actualizar a Adobe Commerce 2.3.5 desde la versión 2.3.4 o anterior.

Esta actualización requiere que el equipo de asistencia actualice MariaDB a la infraestructura de nube de MariaDB 10.0 a 10.2 para satisfacer los requisitos de Adobe Commerce . Adobe Commerce versión 2.3.5 y posteriores.

## Producto y versiones afectados

Adobe Commerce en infraestructura de nube con Adobe Commerce versión 2.3.4 o anterior y MariaDB versión 10.0 o anterior.

## Preparar la base de datos para la actualización

Antes de que el equipo de asistencia de Adobe Commerce inicie el proceso de actualización, debe preparar la base de datos convirtiendo el formato de todas las tablas de `COMPACT` a `DYNAMIC`. También debe convertir el tipo de motor de almacenamiento de `MyISAM` a `InnoDB`.

Tenga en cuenta las siguientes directrices al crear el plan y la programación para convertir la base de datos.

- Conversión de `COMPACT` a `DYNAMIC` las tablas pueden tardar varias horas con una base de datos grande.

- Para evitar la corrupción de datos, no realice la conversión cuando el sitio esté activo.

- Complete el trabajo de conversión durante un período de poco tráfico en el sitio.

- Cambie el sitio a [modo de mantenimiento](../../../installation/tutorials/maintenance-mode.md) antes de ejecutar el `ALTER` comandos.

### Convertir tablas de base de datos

Puede convertir tablas en un nodo del clúster. Los cambios se replicarán en los demás nodos principales del clúster.

1. Desde Adobe Commerce en el entorno de infraestructura de nube, utilice SSH para conectarse al nodo 1.

1. Inicie sesión en MariaDB.

1. Convierta el formato de tabla.

   - Identifique las tablas que se van a convertir de formato compacto a dinámico.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Determine los tamaños de tabla para poder programar el trabajo de conversión.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      Las tablas más grandes tardan más en convertirse. Debe planificar en consecuencia al llevar su sitio dentro y fuera del modo de mantenimiento qué lotes de tablas convertir en qué orden, para así planificar los tiempos de las ventanas de mantenimiento necesarios

   - Convierta todas las tablas en formato dinámico de una en una.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Actualice el motor de almacenamiento de tablas.

   - Identifique las tablas que utilizan `MyISAM` almacenamiento.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Convertir tablas que utilizan `MyISAM` almacenamiento en `InnoDB` almacenamiento.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Compruebe la conversión.

   Este paso es necesario porque las implementaciones de código realizadas después de completar la conversión pueden hacer que algunas tablas se reviertan a su configuración original.

   - El día antes de la actualización programada a la versión 10.2 de MariaDB, inicie sesión en la base de datos y ejecute las consultas para comprobar el formato y el motor de almacenamiento.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Si se ha revertido alguna tabla, repita los pasos para cambiar el formato de tabla y el motor de almacenamiento.

## Información adicional

[Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](../planning/database-on-cloud.md)
