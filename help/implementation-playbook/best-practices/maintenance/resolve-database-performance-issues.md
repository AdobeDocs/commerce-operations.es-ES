---
title: Prácticas recomendadas para resolver problemas de rendimiento de la base de datos
description: Obtenga información sobre cómo solucionar problemas de bases de datos que ralentizan el rendimiento en sitios de Adobe Commerce implementados en la infraestructura de nube.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---


<!--Consider moving this topic to the Maintenance section-->

# Prácticas recomendadas para resolver problemas de rendimiento de la base de datos

Este artículo explica cómo solucionar problemas de base de datos que afectan negativamente al rendimiento de la base de datos en Adobe Commerce en sitios de infraestructura de nube.

## Versiones afectadas

Adobe Commerce en infraestructura en la nube

## Identificar y resolver consultas de larga duración

Determine si tiene consultas MySQL de ejecución lenta. Según el plan de infraestructura de nube de Adobe Commerce y, por lo tanto, la disponibilidad de herramientas, puede hacer lo siguiente.

### Analizar consultas de base de datos con MySQL

Puede usar MySQL para identificar y resolver consultas de larga duración en cualquier proyecto de infraestructura en la nube de Adobe Commerce.

1. Ejecute el [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) instrucción.
1. Si ve consultas de larga duración, ejecute [MySQL `EXPLAIN` y `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) para cada uno de ellos, para averiguar qué hace que la consulta se ejecute durante mucho tiempo.
1. En función de los problemas encontrados, tome medidas para corregir la consulta de modo que se ejecute más rápidamente.

### Analizar consultas utilizando Percona Toolkit (solo para la arquitectura Pro)

Si el proyecto de Adobe Commerce está implementado en la arquitectura Pro, puede utilizar Percona Toolkit para analizar consultas.

1. Ejecute el `pt-query-digest --type=slowlog` con registros de consulta lentos MySQL.
   * Para encontrar la ubicación de los registros de consulta lentos, consulte **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) en nuestra documentación para desarrolladores.
   * Consulte la [Kit de herramientas Percona > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) documentación.
1. En función de los problemas encontrados, tome medidas para corregir la consulta de modo que se ejecute más rápidamente.

## Verificar que todas las tablas tengan una clave principal

La definición de claves principales es un requisito para un buen diseño de bases de datos y tablas. Las claves principales permiten identificar de forma exclusiva una sola fila en cualquier tabla.

Si tiene tablas sin clave principal, el motor de base de datos predeterminado para Adobe Commerce (InnoDB) utiliza la primera clave única no nula como clave principal. Si no hay ninguna clave única disponible, InnoDB crea una clave principal oculta (6 bytes). El problema con una clave principal definida implícitamente es que no tiene control sobre ella. Además, el valor implícito se asigna globalmente para todas las tablas sin claves principales. Esta configuración puede causar problemas de contención si realiza escrituras simultáneas en estas tablas. Esto puede provocar problemas de rendimiento, ya que las tablas también comparten el incremento global del índice de clave principal oculta.

Evite estos problemas definiendo una clave principal para cualquier tabla que no tenga una.

### Identificar y actualizar tablas sin clave principal

1. Identifique tablas sin clave principal mediante la siguiente consulta SQL:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Para cualquier tabla que no tenga una clave principal, agregue una clave principal actualizando la variable `db_schema.xml` (el esquema declarativo) con un nodo similar al siguiente:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Cuando agregue el nodo , reemplace la variable `referenceID` y `column name` con sus valores personalizados.

Para obtener más información, consulte [Configurar esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) en nuestra documentación para desarrolladores.

## Identificar y eliminar índices duplicados

Identifique cualquier índice duplicado en la base de datos y elimínelo.

### Comprobar índices duplicados

Para comprobar si hay índices duplicados en la arquitectura de nube Pro o Starter, ejecute la siguiente consulta SQL.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

La consulta devuelve los nombres de columna y los nombres de cualquier índice duplicado.

Los comerciantes de arquitectura Pro también pueden ejecutar la comprobación utilizando Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` comando.

### Eliminar índices duplicados

Usar el SQL [Instrucción DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) para eliminar índices duplicados.

```SQL
DROP INDEX
```

## Información adicional

[Prácticas recomendadas para la configuración de bases de datos en implementaciones de nube](../planning/database-on-cloud.md)

