---
title: Requisitos previos de actualización de Adobe Commerce para MariaDB
description: Aprenda a preparar la base de datos de Adobe Commerce para actualizar MariaDB desde una versión anterior.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: 73663659dd1b3305bf8c9a167852b24dc1016e7d
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Actualizar los requisitos previos de MariaDB

Actualización del servicio MariaDB en la infraestructura de la nube de la versión 10.0 o 10.2 a la versión 10.3, 10.4 o 10.5. MariaDB versión 10.3 y posteriores requieren que la base de datos utilice el formato de fila de tabla dinámica y Adobe Commerce requiere el uso del motor de almacenamiento InnoDB para tablas. Este artículo explica cómo actualizar la base de datos para cumplir con estos requisitos de MariaDB.

Después de preparar la base de datos, envíe un ticket de asistencia de Adobe Commerce para actualizar la versión del servicio MariaDB en su infraestructura de nube antes de continuar con el proceso de actualización de Adobe Commerce.

## Producto y versiones afectados

Adobe Commerce en la infraestructura en la nube con MariaDB versión 10.3 o anterior.

## Preparar la base de datos para la actualización

Antes de que el equipo de asistencia de Adobe Commerce inicie el proceso de actualización, prepare la base de datos convirtiendo las tablas de la base de datos:

- Conversión del formato de fila de `COMPACT` hasta `DYNAMIC`
- Cambiar el motor de almacenamiento de `MyISAM` hasta `InnoDB`

Tenga en cuenta las siguientes consideraciones al planificar y programar la conversión:

- Convirtiendo desde `COMPACT` hasta `DYNAMIC` Las tablas pueden tardar varias horas con una base de datos de gran tamaño.

- Para evitar que se dañen los datos, no complete el trabajo de conversión en un sitio activo.

- Complete el trabajo de conversión durante un período de poco tráfico en el sitio.

- Cambie el sitio a [modo de mantenimiento](../../../installation/tutorials/maintenance-mode.md) antes de ejecutar los comandos para convertir tablas de base de datos.

### Convertir formato de fila de tabla de base de datos

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

### Convertir formato de almacenamiento de tabla de base de datos

Puede convertir tablas en un nodo del clúster. Los cambios se replican automáticamente en los demás nodos de servicio.

El proceso para convertir el formato de almacenamiento es diferente para los proyectos de Adobe Commerce Starter y Adobe Commerce Pro.

- Para la arquitectura de inicio, utilice MySQL `ALTER` para convertir el formato.
- En la arquitectura Pro, utilice el MySQL `CREATE` y `SELECT` comandos para crear una tabla de base de datos con `InnoDB` almacene y copie los datos de la tabla existente en la nueva tabla. Este método garantiza que los cambios se replican en todos los nodos del clúster.

**Convertir formato de almacenamiento de tabla para proyectos de Adobe Commerce Pro**

1. Identificar tablas que utilizan `MyISAM` almacenamiento.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir todas las tablas a `InnoDB` formato de almacenamiento de uno en uno.

   - Cambie el nombre de la tabla existente para evitar conflictos de nombres.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Cree una tabla que utilice `InnoDB` almacenamiento con los datos de la tabla existente.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Compruebe que la nueva tabla tiene todos los datos necesarios.

   - Elimine la tabla original cuyo nombre ha cambiado.


**Convertir formato de almacenamiento de tabla para proyectos de Adobe Commerce Starter**

1. Identificar tablas que utilizan `MyISAM` almacenamiento.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Convertir tablas que utilizan `MyISAM` almacenamiento en `InnoDB` almacenamiento.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### Comprobar la conversión de base de datos

El día anterior a la actualización programada a MariaDB versión 10.3, 10.4 o 10.6, compruebe que todas las tablas tengan el formato de fila y el motor de almacenamiento correctos. Es necesario realizar la comprobación porque las implementaciones de código realizadas después de completar la conversión pueden provocar que algunas tablas vuelvan a su configuración original.

1. Inicie sesión en la base de datos.

1. Compruebe si hay tablas que todavía tengan `COMPACT` formato de fila.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Compruebe si hay tablas que sigan utilizando `MyISAM` formato de almacenamiento

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Si se ha revertido alguna tabla, repita los pasos para cambiar el formato de fila de tabla y el motor de almacenamiento.

## Cambio del motor de almacenamiento

Consulte [Convertir tablas MyISAM a InnoDB](../planning/database-on-cloud.md).

## Información adicional

- [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](../planning/database-on-cloud.md)
- [Actualización de MariaDB de 10.0 a 12.0 para Adobe Commerce en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10.0-to-10.2-for-magento-commerce-cloud.html)
