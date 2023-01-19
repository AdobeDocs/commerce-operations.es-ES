---
title: Requisitos previos de actualización de Adobe Commerce 2.3.5 para MariaDB
description: Obtenga información sobre cómo preparar la base de datos de Adobe Commerce para la actualización desde Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 35efea20181b112e97bfae803c8d0168cfc88dfc
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# Requisitos previos de la actualización a Adobe Commerce 2.3.5

Este artículo explica cómo preparar la base de datos al actualizar a Adobe Commerce 2.3.5 desde la versión 2.3.4 o anterior.

Esta actualización requiere que el equipo de asistencia actualice MariaDB en la infraestructura de nube de MariaDB 10.0 a 10.2 para satisfacer los requisitos de la versión 2.3.5 y posteriores de Adobe Commerce.

## Producto y versiones afectados

Adobe Commerce en infraestructura de nube con Adobe Commerce versión 2.3.4 o anterior y MariaDB versión 10.0 o anterior.

## Preparar la base de datos para la actualización

Antes de que el equipo de asistencia de Adobe Commerce comience el proceso de actualización, prepare la base de datos convirtiendo las tablas de la base de datos:

- Convertir el formato de fila de `COMPACT` a `DYNAMIC`
- Convertir el motor de almacenamiento de `MyISAM` a `InnoDB`

Tenga en cuenta las siguientes consideraciones cuando planifique y programe la conversión:

- Conversión de `COMPACT` a `DYNAMIC` las tablas pueden tardar varias horas con una base de datos grande.

- Para evitar que se dañen los datos, no complete el trabajo de conversión en un sitio activo.

- Complete el trabajo de conversión durante un período de poco tráfico en el sitio.

- Cambie el sitio a [modo de mantenimiento](../../../installation/tutorials/maintenance-mode.md) antes de ejecutar los comandos para convertir tablas de base de datos.

### Convertir el formato de fila de la tabla de la base de datos

Puede convertir tablas en un nodo del clúster. Los cambios se replican automáticamente en los demás nodos de servicio.

1. Desde Adobe Commerce en el entorno de infraestructura de nube, utilice SSH para conectarse al nodo 1.

1. Inicie sesión en MariaDB.

1. Identifique las tablas que se van a convertir de formato compacto a dinámico.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Determine los tamaños de tabla para poder programar el trabajo de conversión.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Las tablas más grandes tardan más en convertirse. Revise las tablas y agrupe el trabajo de conversión por prioridad y tamaño de tabla para ayudar a planificar las ventanas de mantenimiento necesarias.

1. Convierta todas las tablas en formato dinámico de una en una.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

### Convertir el formato de almacenamiento de la tabla de la base de datos

Puede convertir tablas en un nodo del clúster. Los cambios se replican automáticamente en los demás nodos de servicio.

El proceso para convertir el formato de almacenamiento es diferente para los proyectos de Adobe Commerce Starter y Adobe Commerce Pro.

- Para la arquitectura de inicio, utilice MySQL `ALTER` para convertir el formato.
- En la arquitectura Pro, utilice MySQL `CREATE` y `SELECT` comandos para crear una tabla de base de datos con `InnoDB` almacene y copie los datos de la tabla existente en la nueva tabla. Este método garantiza que los cambios se replicen en todos los nodos del clúster.

**Convertir el formato de almacenamiento de tablas para proyectos de Adobe Commerce Pro**

1. Identifique las tablas que utilizan `MyISAM` almacenamiento.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir todas las tablas a `InnoDB` formato de almacenamiento de información de uno en uno.

   - Cambie el nombre de la tabla existente para evitar conflictos de nombres.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Cree una tabla que utilice `InnoDB` almacenamiento utilizando los datos de la tabla existente.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Compruebe que la nueva tabla tiene todos los datos necesarios.

   - Elimine la tabla original a la que ha cambiado el nombre.


**Convertir el formato de almacenamiento de tablas para proyectos de Adobe Commerce Starter**

1. Identifique las tablas que utilizan `MyISAM` almacenamiento.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir tablas que utilizan `MyISAM` almacenamiento en `InnoDB` almacenamiento.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### Verificar la conversión de la base de datos

El día antes de la actualización programada a la versión 10.2 de MariaDB, compruebe que todas las tablas tengan el formato de fila y el motor de almacenamiento correctos. La verificación es necesaria porque las implementaciones de código realizadas después de completar la conversión pueden hacer que algunas tablas se reviertan a su configuración original.

1. Inicie sesión en la base de datos.

1. Compruebe si hay tablas que aún tengan la variable `COMPACT` formato de fila.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Compruebe si hay tablas que aún utilicen la variable `MyISAM` formato de almacenamiento

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Si se ha revertido alguna tabla, repita los pasos para cambiar el formato de fila de tabla y el motor de almacenamiento.

## Información adicional

[Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](../planning/database-on-cloud.md)
