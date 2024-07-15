---
title: Requisitos previos de actualización de Adobe Commerce para MariaDB
description: Aprenda a preparar la base de datos de Adobe Commerce para actualizar MariaDB desde una versión anterior.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Actualizar los requisitos previos de MariaDB

Antes de actualizar Adobe Commerce en una infraestructura en la nube, es posible que también tenga que actualizar el software de la base de datos si utiliza MariaDB. Por ejemplo:

- Adobe Commerce 2.4.6 con MariaDB versión 10.5.1 o superior
- Adobe Commerce 2.3.5 con MariaDB versión 10.3 o anterior

## Adobe Commerce 2.4.6

A partir de MariaDB 10.5.1, las columnas con formatos temporales antiguos se marcan con un comentario `/* mariadb-5.3 */` en la salida de las instrucciones `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE`, así como en la columna `COLUMN_TYPE` de la tabla `INFORMATION_SCHEMA.COLUMNS`. [Consulte la documentación de MariaDB](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce no puede asignar las columnas de fecha a un tipo de datos adecuado debido al comentario de MariaDB, lo que puede provocar un comportamiento inesperado en el código personalizado.

Para evitar comportamientos inesperados al actualizar MariaDB de versiones anteriores a la 10.6, Adobe recomienda migrar las columnas al nuevo formato interno.

### Configuración predeterminada

En MariaDB 10.1.2, se introdujo un nuevo formato temporal desde MySQL 5.6. La variable de sistema `mysql56_temporal_format` permite que la base de datos convierta automáticamente el antiguo formato de fecha al nuevo cuando se ejecuta una tabla alternativa o se importa la base de datos. La configuración predeterminada de `mysql56_temporal_format` siempre está habilitada en Adobe Commerce en la infraestructura en la nube.

### Migración de columnas de fecha

La siguiente consulta muestra la tabla y las columnas afectadas que deben migrarse después de actualizar MariaDB a 10.5.1 o posterior:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

La migración de las columnas al nuevo formato de fecha interno requiere volver a importar la base de datos o ejecutarse posteriormente en la columna identificada con la misma definición de columna. La siguiente consulta genera las consultas ALTER necesarias:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Es importante migrar las columnas al nuevo formato de fecha interno _antes de_ implementar el nuevo código para evitar comportamientos inesperados.

## Adobe Commerce 2.3.5

Actualización del servicio MariaDB en la infraestructura de la nube de la versión 10.0 o 10.2 a la versión 10.3, 10.4 o 10.5. MariaDB versión 10.3 y posteriores requieren que la base de datos utilice el formato de fila de tabla dinámica y Adobe Commerce requiere el uso del motor de almacenamiento InnoDB para tablas. Este artículo explica cómo actualizar la base de datos para cumplir con estos requisitos de MariaDB.

Después de preparar la base de datos, envíe un ticket de asistencia de Adobe Commerce para actualizar la versión del servicio MariaDB en su infraestructura de nube antes de continuar con el proceso de actualización de Adobe Commerce.

### Preparar la base de datos para la actualización

Antes de que el equipo de asistencia de Adobe Commerce inicie el proceso de actualización, prepare la base de datos convirtiendo las tablas de la base de datos:

- Convertir el formato de fila de `COMPACT` a `DYNAMIC`
- Cambiar el motor de almacenamiento de `MyISAM` a `InnoDB`

Tenga en cuenta las siguientes consideraciones al planificar y programar la conversión:

- La conversión de tablas de `COMPACT` a `DYNAMIC` puede tardar varias horas con una base de datos grande.

- Para evitar que se dañen los datos, no complete el trabajo de conversión en un sitio activo.

- Complete el trabajo de conversión durante un período de poco tráfico en el sitio.

- Cambie el sitio al [modo de mantenimiento](../../../installation/tutorials/maintenance-mode.md) antes de ejecutar los comandos para convertir las tablas de la base de datos.

#### Convertir formato de fila de tabla de base de datos

Puede convertir tablas en un nodo del clúster. Los cambios se replican automáticamente en los demás nodos de servicio.

1. Desde su Adobe Commerce en el entorno de la infraestructura de la nube, utilice SSH para conectarse al nodo 1.

1. Inicie sesión en MariaDB.

1. Identifique las tablas que se van a convertir de formato compacto a dinámico.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Determine los tamaños de la tabla para poder programar el trabajo de conversión.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Las tablas más grandes tardan más en convertirse. Revise las tablas y agrupe el trabajo de conversión por prioridad y tamaño de tabla para ayudar a planificar las ventanas de mantenimiento necesarias.

1. Convierta todas las tablas a formato dinámico de una en una.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Convertir formato de almacenamiento de tabla de base de datos

Puede convertir tablas en un nodo del clúster. Los cambios se replican automáticamente en los demás nodos de servicio.

El proceso para convertir el formato de almacenamiento es diferente para los proyectos de Adobe Commerce Starter y Adobe Commerce Pro.

- Para la arquitectura inicial, utilice el comando MySQL `ALTER` para convertir el formato.
- En la arquitectura Pro, utilice los comandos MySQL `CREATE` y `SELECT` para crear una tabla de base de datos con almacenamiento `InnoDB` y copie los datos de la tabla existente en la nueva tabla. Este método garantiza que los cambios se replican en todos los nodos del clúster.

**Convertir formato de almacenamiento de tabla para proyectos de Adobe Commerce Pro**

1. Identificar tablas que usan el almacenamiento `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir todas las tablas al formato de almacenamiento `InnoDB` de una en una.

   - Cambie el nombre de la tabla existente para evitar conflictos de nombres.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Cree una tabla que use el almacenamiento `InnoDB` con los datos de la tabla existente.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Compruebe que la nueva tabla tiene todos los datos necesarios.

   - Elimine la tabla original cuyo nombre ha cambiado.


**Convertir formato de almacenamiento de tabla para proyectos de Adobe Commerce Starter**

1. Identificar tablas que usan el almacenamiento `MyISAM`.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir las tablas que usan el almacenamiento `MyISAM` al almacenamiento `InnoDB`.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### Comprobar la conversión de base de datos

El día anterior a la actualización programada a MariaDB versión 10.3, 10.4 o 10.6, compruebe que todas las tablas tengan el formato de fila y el motor de almacenamiento correctos. Es necesario realizar la comprobación porque las implementaciones de código realizadas después de completar la conversión pueden provocar que algunas tablas vuelvan a su configuración original.

1. Inicie sesión en la base de datos.

1. Compruebe si hay tablas que sigan teniendo el formato de fila `COMPACT`.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Buscar tablas que sigan utilizando el formato de almacenamiento `MyISAM`

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Si se ha revertido alguna tabla, repita los pasos para cambiar el formato de fila de tabla y el motor de almacenamiento.

### Cambio del motor de almacenamiento

Vea [Convertir tablas MyISAM a InnoDB](../planning/database-on-cloud.md).
