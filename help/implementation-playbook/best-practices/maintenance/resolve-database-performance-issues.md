---
title: Prácticas recomendadas para resolver problemas de rendimiento de la base de datos
description: Aprenda a solucionar problemas de bases de datos que ralentizan el rendimiento en los sitios de Adobe Systems Commerce implementados en infraestructura en la nube.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Prácticas recomendadas para resolver problemas de rendimiento de la base de datos

Este artículo explica cómo solucionar problemas de base de datos que afectan negativamente al rendimiento de la base de datos en Adobe Systems Commerce en sitios de infraestructura en la nube.

## Versiones relacionadas

Adobe Commerce en la infraestructura en la nube

## Identificar y resolver consultas de larga duración

Determine si tiene alguna consulta MySQL de ejecución lenta. Según el plan de infraestructura en la nube de Adobe Commerce y, por lo tanto, la disponibilidad de las herramientas, puede hacer lo siguiente.

### Analizar consultas de base de datos con MySQL

Puede utilizar MySQL para identificar y resolver consultas de larga ejecución en cualquier proyecto de infraestructura en la nube de Adobe Commerce.

1. Ejecute la [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) instrucción.
1. Si ve consultas de larga duración, ejecute [MySQL `EXPLAIN` y `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) para cada una de ellas, para averiguar qué hace que el consulta funcione durante mucho tiempo.
1. En función de los problemas encontrados, tome medidas para solucionar el consulta de modo que se ejecute más rápidamente.

### Análisis de consultas con Percona Toolkit (solo para arquitectura Pro)

Si su proyecto Adobe Systems Commerce está implementado en la arquitectura Pro, puede usar Percona Toolkit para analizar consultas.

1. Ejecute el `pt-query-digest --type=slowlog` comando contra MySQL slow consulta logs.
   * Para encontrar la ubicación de los registros de consultas lentas, consulte **[!UICONTROL Log locations > Service Logs]**(https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs) en nuestra documentación para desarrolladores.
   * Consulte la documentación de [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest).
1. En función de los problemas encontrados, realice pasos para corregir la consulta de modo que se ejecute más rápidamente.

## Comprobar que todas las tablas tienen una clave principal

La definición de claves principales es un requisito para el buen diseño de bases de datos y tablas. Las claves principales proporcionan una forma de identificar una sola fila en cualquier tabla de forma exclusiva.

Si tiene tablas sin una clave principal, el motor de base de datos predeterminado para Adobe Systems Commerce (InnoDB) utiliza la primera clave única, no nula, como clave principal. Si no hay ninguna clave única disponible, InnoDB crea una clave principal oculta (6 bytes). El problema con una clave principal definida implícitamente es que usted no tiene control sobre ella. Además, el valor implícito se asigna globalmente a todas las tablas sin claves principales. Esta configuración puede causar problemas de contención si realiza escrituras simultáneas en estas tablas. Esto puede posible cliente a problemas de rendimiento, ya que las tablas también comparten el incremento del índice de clave principal oculta global.

Para evitar estos problemas, defina una clave principal para las tablas que no tengan una.

### Identificar y actualizar tablas sin una clave principal

1. Identifique tablas sin una clave principal mediante la siguiente consulta SQL:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Para cualquier tabla que no tenga una clave principal, agregue una clave principal actualizando `db_schema.xml` (el esquema declarativo) con un nodo similar al siguiente:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Cuando agregue el nodo, reemplace las variables `referenceID` y `column name` por sus valores personalizados.

Para obtener más información, consulte [Configurar esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) en nuestra documentación para desarrolladores.

## Identificación y eliminación de índices duplicados

Identifique los índices duplicado de la base de datos y elimínelos.

### Comprobar duplicado índices

Para comprobar si hay índices duplicado en la arquitectura Pro o Starter nube, ejecute el siguiente consulta SQL.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

La consulta devuelve los nombres de las columnas y los nombres de los índices duplicado.

Los comerciantes de arquitectura profesional también pueden ejecutar la comprobación utilizando el comando Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` .

### Quitar duplicado índices

Utilice la instrucción SQL [DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) para quitar los índices duplicados.

```SQL
DROP INDEX
```

## Más información

[Prácticas recomendadas de configuración de bases de datos para implementaciones en la nube](../planning/database-on-cloud.md)
