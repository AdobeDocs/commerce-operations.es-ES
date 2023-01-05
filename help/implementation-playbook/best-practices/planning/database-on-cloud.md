---
title: Prácticas recomendadas para la configuración de bases de datos en implementaciones de nube
description: Obtenga información sobre cómo configurar la base de datos y la aplicación para mejorar el rendimiento al implementar Adobe Commerce en la infraestructura de nube.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '687'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración de bases de datos

Obtenga información sobre las prácticas recomendadas para mejorar el rendimiento de la base de datos y trabajar de forma eficiente con la base de datos al implementar Adobe Commerce en la infraestructura de la nube.

## Productos afectados

Adobe Commerce en infraestructura en la nube

## Convertir todas las tablas MyISAM a InnoDB

Adobe recomienda utilizar el motor de base de datos InnoDB. En una instalación predeterminada de Adobe Commerce, todas las tablas de la base de datos se almacenan con el motor InnoDB. Sin embargo, algunos módulos de terceros (extensiones) pueden introducir tablas en el formato MyISAM. Después de instalar un módulo de terceros, compruebe la base de datos para identificar cualquier tabla en `myisam` formatearlos y convertirlos en `innodb` formato.

### Determinar si un módulo incluye tablas MyISAM

Puede analizar el código de módulo de terceros antes de instalarlo, para determinar si utiliza tablas MyISAM.

Si ya ha instalado una extensión, ejecute la siguiente consulta para determinar si la base de datos tiene tablas MyISAM:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Cambiar el motor de almacenamiento a InnoDB

En el `db_schema.xml` que declara la tabla, establezca la variable `engine` valor de atributo para el `table` nodo a `innodb`. Para obtener más información, consulte [Configurar esquema declarativo > nodo de tabla](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) en nuestra documentación para desarrolladores.

El esquema declarativo se introdujo en Adobe Commerce en la versión 2.3 de la infraestructura en la nube.

## Configurar el motor de búsqueda recomendado para la búsqueda nativa de MySQL

Adobe recomienda configurar siempre Elasticsearch o OpenSearch para su proyecto de infraestructura de nube de Adobe Commerce aunque tenga pensado configurar una herramienta de búsqueda de terceros para su aplicación de Adobe Commerce. Esta configuración proporciona una opción de reserva en caso de que falle la herramienta de búsqueda de terceros.

El motor de búsqueda que utilice depende de la versión de nube de Adobe Commerce instalada:

- Para Adobe Commerce 2.4.4 y posteriores, use el servicio OpenSearch para la búsqueda nativa de MySQL.

- Para versiones anteriores de Adobe Commerce, utilice Elasticsearch.

Para determinar qué motor de búsqueda está actualmente en uso, ejecute el siguiente comando:

```bash
./bin/magento config:show catalog/search/engine
```

Para obtener instrucciones de configuración, consulte la guía para desarrolladores de Adobe Commerce en la nube:

- [Configuración del servicio OpenSearch](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Configuración del servicio de Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Evitar déclencheur personalizados

Evite utilizar déclencheur personalizados si es posible.

Los déclencheur se utilizan para registrar los cambios en las tablas de auditoría. Adobe recomienda configurar la aplicación para que escriba directamente en las tablas de auditoría en lugar de utilizar la funcionalidad de déclencheur por estos motivos:

- Los déclencheur se interpretan como código y MySQL no los precompila. Al unirse al espacio de transacciones de la consulta, añaden la sobrecarga a un analizador e intérprete para cada consulta realizada con la tabla.
- Los déclencheur comparten el mismo espacio de transacción que las consultas originales y, mientras que esas consultas compiten por los bloqueos de la tabla, los déclencheur compiten de forma independiente en los bloqueos de otra tabla.

Para obtener más información sobre las alternativas al uso de déclencheur personalizados, consulte [Usar déclencheur MySQL de forma eficaz](mysql-triggers-usage.md) en nuestra base de conocimientos de soporte.

## Actualización [!DNL ECE-Tools] a la versión 2002.0.21 o superior {#ece-tools-version}

Para evitar posibles problemas con los bloqueos cron, actualice ECE-Tools a la versión 2002.0.21 o superior. Para obtener instrucciones, consulte [Actualizar `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) en nuestra documentación para desarrolladores.

## Cambiar el modo de indexación de forma segura

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

El cambio de indexadores genera [!DNL data definition language] (DDL) para crear déclencheur que puedan causar bloqueos de base de datos. Para evitar este problema, ponga el sitio web en modo de mantenimiento y deshabilite los trabajos cron antes de cambiar la configuración.
Para obtener instrucciones, consulte [Configuración de indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) en el *Guía de configuración de Adobe Commerce*.

## No ejecutar instrucciones DDL en producción

Evite ejecutar instrucciones DDL en el entorno de producción para evitar conflictos (como modificaciones y creaciones de tablas). La variable `setup:upgrade` es una excepción.

Si necesita ejecutar una instrucción DDL, ponga el sitio web en modo de mantenimiento y deshabilite cron (consulte las instrucciones para cambiar índices de forma segura en la sección anterior).

## Habilitar el archivado de pedidos

Habilite el archivado de pedidos del administrador para reducir el espacio necesario para las tablas de ventas a medida que crezcan los datos de pedidos. El archivado ahorra espacio en disco de MySQL y mejora el rendimiento del cierre de compra.

Consulte [Habilitar archivado](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) en la documentación de Adobe Commerce Merchant.

## Información adicional

- [Motores de almacenamiento MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Requisitos previos de actualización de Adobe Commerce 2.3.5 para MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Prácticas recomendadas para resolver problemas de rendimiento de la base de datos](../maintenance/resolve-database-performance-issues.md)
