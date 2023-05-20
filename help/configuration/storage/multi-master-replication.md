---
title: Replicación de base de datos
description: Consulte las ventajas de configurar la replicación de bases de datos.
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Replicación de base de datos

{{ee-only}}

{{deprecate-split-db}}

La configuración de la replicación de bases de datos ofrece las siguientes ventajas:

- Proporciona backup de datos
- Habilita el análisis de datos sin afectar a la base de datos maestra
- Escalabilidad

Las bases de datos MySQL se replican de forma asíncrona, lo que significa que los esclavos no necesitan estar conectados permanentemente para recibir actualizaciones del maestro.

## Configurar replicación de base de datos

En esta guía no se aborda en profundidad la replicación de bases de datos. Para configurarlo, puede consultar un recurso como:

- [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Cómo configurar la replicación de esclavos maestros en MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce proporciona configuraciones MySQL de muestra para sus bases de datos esclavas. Se proporciona una configuración sencilla con el `ResourceConnections` clase `README.md`.

Lo siguiente es más avanzado y se proporciona solo para su información:

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Mejora del rendimiento

Para mejorar el rendimiento de la replicación maestro-esclavo, puede filtrar algunas tablas en instancias esclavas. Se recomienda filtrar todas las tablas temporales con el patrón de nombre `search\_tmp\_%` que se utilizan para la búsqueda en el catálogo.

Para ello, añada la línea siguiente a su `my.cnf` en las instancias de esclavos:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
