---
title: Prácticas recomendadas de configuración de bases de datos para implementaciones en la nube
description: Obtenga información sobre cómo configurar la base de datos y la configuración de la aplicación para mejorar el rendimiento al implementar Adobe Commerce en la infraestructura en la nube.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración de bases de datos

Conozca las prácticas recomendadas para mejorar el rendimiento de la base de datos y trabajar de forma eficaz con la base de datos al implementar Adobe Commerce en la infraestructura en la nube.

## Productos afectados

Adobe Commerce en la infraestructura en la nube

## Convertir todas las tablas MyISAM a InnoDB

Adobe recomienda utilizar el motor de base de datos InnoDB. En una instalación predeterminada de Adobe Commerce, todas las tablas de la base de datos se almacenan mediante el motor InnoDB. Sin embargo, algunos módulos de terceros (extensiones) pueden introducir tablas en formato MyISAM. Después de instalar un módulo de terceros, compruebe la base de datos para identificar cualquier tabla en `myisam` formatearlos y convertirlos en `innodb` formato.

### Determinar si un módulo incluye tablas MyISAM

Puede analizar el código del módulo de terceros antes de instalarlo para determinar si utiliza tablas MyISAM.

Si ya ha instalado una extensión, ejecute la siguiente consulta para determinar si la base de datos tiene tablas MyISAM:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Cambie el motor de almacenamiento a InnoDB

En el `db_schema.xml` archivo que declara la tabla, establezca el `engine` valor de atributo para el correspondiente `table` nodo a `innodb`. Para ver una referencia, consulte [Configure el esquema declarativo > nodo de tabla](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) en nuestra documentación para desarrolladores.

El esquema declarativo se introdujo en Adobe Commerce en la versión 2.3 de la infraestructura en la nube.

## Configurar el motor de búsqueda recomendado para la búsqueda nativa de MySQL

Adobe recomienda configurar siempre Elasticsearch u OpenSearch para su proyecto de infraestructura en la nube de Adobe Commerce, incluso si planea configurar una herramienta de búsqueda de terceros para su aplicación de Adobe Commerce. Esta configuración proporciona una opción de reserva en caso de que falle la herramienta de búsqueda de terceros.

El motor de búsqueda que utilice depende de la versión de Adobe Commerce en la nube instalada:

- Para Adobe Commerce 2.4.4 y versiones posteriores, utilice el servicio OpenSearch para la búsqueda nativa de MySQL.

- Para versiones anteriores de Adobe Commerce, utilice Elasticsearch.

Para determinar qué motor de búsqueda está actualmente en uso, ejecute el siguiente comando:

```bash
./bin/magento config:show catalog/search/engine
```

Para obtener instrucciones de configuración, consulte la Guía del desarrollador de Adobe Commerce en la nube:

- [Configurar el servicio OpenSearch](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Configuración del servicio de Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Evitar déclencheur personalizados

Evite utilizar déclencheur personalizados, si es posible.

Los déclencheur se utilizan para registrar cambios en tablas de auditoría. Adobe recomienda configurar la aplicación para que escriba directamente en las tablas de auditoría en lugar de utilizar la funcionalidad de déclencheur por estos motivos:

- Los déclencheur se interpretan como código y MySQL no los precompila. Al conectarse al espacio de transacción de la consulta, agregan la sobrecarga a un analizador e intérprete para cada consulta realizada con la tabla.
- Los déclencheur comparten el mismo espacio de transacciones que las consultas originales y, mientras que estas consultas compiten por bloqueos en la tabla, los déclencheur compiten de forma independiente en bloqueos en otra tabla.

Para obtener más información sobre alternativas al uso de déclencheur personalizados, consulte [Déclencheur MySQL](mysql-configuration.md#triggers).

## Actualizar [!DNL ECE-Tools] a la versión 2002.0.21 o superior {#ece-tools-version}

Para evitar posibles problemas con los interbloqueos de cron, actualice ECE-Tools a la versión 2002.0.21 o superior. Para obtener instrucciones, consulte [Actualizar `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) en nuestra documentación para desarrolladores.

## Cambiar el modo del indexador con seguridad

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Cambiar indexadores genera [!DNL data definition language] Instrucciones (DDL) para crear déclencheur que puedan bloquear la base de datos. Puede evitar este problema poniendo su sitio web en modo de mantenimiento y deshabilitando los trabajos cron antes de cambiar la configuración.
Para obtener instrucciones, consulte [Configuración de indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) en el *Guía de configuración de Adobe Commerce*.

## No ejecutar instrucciones DDL en producción

Evite ejecutar instrucciones DDL en el entorno de producción para evitar conflictos (como modificaciones y creaciones de tablas). El `setup:upgrade` El proceso de es una excepción.

Si necesita ejecutar una instrucción DDL, ponga el sitio web en modo de mantenimiento y deshabilite cron (consulte las instrucciones para cambiar los índices de forma segura en la sección anterior).

## Activar archivado de pedidos

Active el archivado de pedidos desde el administrador para reducir el espacio necesario para las tablas de ventas a medida que aumentan los datos de pedidos. El archivado ahorra espacio en disco de MySQL y mejora el rendimiento de cierre de compra.

Consulte [Habilitar archivado](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) en la documentación de Adobe Commerce Merchant.

## Información adicional

- [Motores de almacenamiento MySQL](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Requisitos previos de actualización de Adobe Commerce 2.3.5 para MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Prácticas recomendadas para resolver problemas de rendimiento de la base de datos](../maintenance/resolve-database-performance-issues.md)
