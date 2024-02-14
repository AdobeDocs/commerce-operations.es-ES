---
source-git-commit: d7926b9150137813b1161581bb1d7884a6fe11e9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# Ajustes de configuración de MariaDB

La reindexación en MariaDB 10.4 y 10.6 tarda más tiempo en comparación con versiones anteriores de MariaDB o MySQL. Para acelerar la reindexación, se recomienda configurar estos parámetros de configuración de MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Si experimenta una degradación del rendimiento no relacionada con la indexación después de actualizar a MariaDB 10.6, considere la posibilidad de habilitar el [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) configuración. Por ejemplo, `--query-cache-type=ON`.

Antes de actualizar Adobe Commerce en proyectos de infraestructura en la nube, es posible que también deba actualizar MariaDB ([consulte Prácticas recomendadas de actualización de MariaDB](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md)).

Por ejemplo:

* Adobe Commerce 2.4.6 con MariaDB versión 10.5.1 o superior
* Adobe Commerce 2.3.5 con MariaDB versión 10.3 o anterior

Además de estas recomendaciones, debe consultar al administrador de la base de datos sobre la configuración de los siguientes parámetros:

>[!NOTE]
>
>Esta configuración solo está disponible para implementaciones locales. Los clientes de Adobe Commerce en la infraestructura en la nube no tienen acceso a esta configuración.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
