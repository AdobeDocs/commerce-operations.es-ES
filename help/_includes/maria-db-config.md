---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%

---
# Ajustes de configuración de MariaDB

La reindexación en MariaDB 10.4 y 10.6 tarda más tiempo en comparación con versiones anteriores de MariaDB o MySQL. Para acelerar la reindexación, se recomienda configurar estos parámetros de configuración de MariaDB:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Si experimenta una degradación del rendimiento no relacionada con la indexación después de actualizar a MariaDB 10.6, considere la posibilidad de habilitar el [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) configuración. Por ejemplo, `--query-cache-type=ON`.

Además de estas recomendaciones, debe consultar al administrador de la base de datos sobre la configuración de los siguientes parámetros:

>[!NOTE]
>
>Esta configuración solo está disponible para implementaciones locales. Los clientes de Adobe Commerce en la infraestructura en la nube no tienen acceso a esta configuración.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
