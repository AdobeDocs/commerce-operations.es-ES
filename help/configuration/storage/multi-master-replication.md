---
title: Duplicación de base de datos
description: Consulte los beneficios de configurar la replicación de bases de datos.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Duplicación de base de datos

{#ee-only}

{{deprecate-split-db}}

La configuración de la replicación de bases de datos ofrece las siguientes ventajas:

- Proporciona copia de seguridad de datos
- Permite el análisis de datos sin afectar a la base de datos maestra
- Escalabilidad

Las bases de datos MySQL se replican asincrónicamente, lo que significa que los esclavos no necesitan estar conectados permanentemente para recibir actualizaciones del maestro.

## Configurar la replicación de la base de datos

Un análisis en profundidad de la replicación de bases de datos está fuera del alcance de esta guía. Para configurarlo, puede consultar un recurso como:

- [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Cómo configurar la replicación maestra del esclavo en MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce proporciona configuraciones MySQL de muestra para sus bases de datos esclavas. Se proporciona una configuración sencilla con la variable `ResourceConnections` class `README.md`.

Lo siguiente es más avanzado y solo se proporciona para su información:

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

Para mejorar el rendimiento de la replicación maestro-esclavo, puede filtrar algunas tablas en instancias esclavas. Se recomienda filtrar todas las tablas temporales con un patrón de nombres `search\_tmp\_%` que se usan para [catálogo](https://glossary.magento.com/catalog) buscar.

Para ello, agregue la línea siguiente al `my.cnf` en las instancias esclavas:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
