---
title: Directrices de MySQL
description: Siga estos pasos para instalar y configurar MySQL y MariaDB para instalaciones locales de Adobe Commerce.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Directrices generales de MySQL

Consulte [Requisitos del sistema](../../system-requirements.md) para ver las versiones compatibles de MySQL.

El Adobe _strong_ recomienda que cumpla el estándar siguiente al configurar la base de datos:

* Adobe Commerce usa [déclencheur de base de datos MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) para mejorar el acceso a la base de datos durante la reindexación. Estas se crean cuando el modo de indizador se establece en [schedule](../../../configuration/cli/manage-indexers.md#configure-indexers). La aplicación no admite ningún déclencheur personalizado en la base de datos porque los déclencheur personalizados pueden producir incompatibilidades con versiones futuras de Adobe Commerce.
* Familiarícese con [estas posibles limitaciones de déclencheur de MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) antes de continuar.
* Para mejorar la postura de seguridad de la base de datos, habilite el modo SQL [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) para evitar almacenar valores de datos no válidos, lo que podría provocar interacciones de base de datos no deseadas.
* Adobe Commerce _no_ admite la replicación basada en instrucciones MySQL. Asegúrese de usar _solo_ [replicación basada en filas](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce actualmente usa instrucciones `CREATE TEMPORARY TABLE` dentro de transacciones, que son [incompatibles](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) con implementaciones de base de datos que usan replicación basada en GTID, como [instancias de segunda generación de SQL de Google Cloud](https://cloud.google.com/sql/docs/features#differences). Considere MySQL para Cloud SQL 8.0 como alternativa.

>[!NOTE]
>
>Si el servidor web y el servidor de base de datos están en hosts diferentes, realice las tareas descritas en este tema en el host del servidor de base de datos y, a continuación, vea [Configurar una conexión de base de datos MySQL remota](mysql-remote.md).

## Instalación de MySQL en Ubuntu

Adobe Commerce 2.4 requiere una instalación limpia de MySQL 8.0. Siga los enlaces a continuación para obtener instrucciones sobre la instalación de MySQL en su máquina.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Si espera importar una gran cantidad de productos, puede aumentar el valor de [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) que sea mayor que el valor predeterminado de 16 MB.

>[!NOTE]
>
>El valor predeterminado se aplica a Adobe Commerce en la infraestructura en la nube _y_ proyectos locales. Los clientes de Adobe Commerce en la infraestructura en la nube Pro deben abrir un ticket de asistencia para aumentar el valor de `max_allowed_packet`. Los clientes de Adobe Commerce on cloud Infrastructure Starter pueden aumentar el valor al actualizar la configuración en el archivo `/etc/mysql/mysql.cnf`.

Para aumentar el valor, abra el archivo `/etc/mysql/mysql.cnf` en un editor de texto y busque el valor de `max_allowed_packet`. Guarde los cambios en el archivo `mysql.cnf`, cierre el editor de texto y reinicie MySQL (`service mysql restart`).

Para comprobar de forma opcional el valor que ha establecido, escriba el siguiente comando en el símbolo del sistema `mysql>`:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

A continuación, [configure la instancia de base de datos](#configuring-the-database-instance).

## Cambios de MySQL 8

Para Adobe Commerce 2.4, hemos agregado compatibilidad con MySQL 8.
En esta sección se describen los cambios más importantes en MySQL 8 que los desarrolladores deben tener en cuenta.

### Se ha eliminado la anchura para los tipos de enteros (relleno)

La especificación de anchura de visualización para tipos de datos enteros (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) ha quedado obsoleta en MySQL 8.0.17. Las instrucciones que incluyen definiciones de tipo de datos en su salida ya no muestran el ancho de visualización para tipos enteros, excepto TINYINT(1). Los conectores MySQL suponen que las columnas TINYINT(1) se originaron como columnas BOOLEANAS. Esta excepción les permite seguir haciendo esa suposición.

#### Ejemplo

Describir admin_user en mysql 8.19

| Campo | Tipo | Nulo | Clave | Predeterminado | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NO | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | SÍ | | `NULL` | |
| `lastname` | `varchar(32`) | SÍ | | `NULL` | |
| `email` | `varchar(128)` | SÍ | | `NULL` | |
| `username` | `varchar(40)` | SÍ | UNI | `NULL` | |
| `password` | `varchar(255)` | NO | | `NULL` | |
| `created` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` en la actualización `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | SÍ | | `NULL` | |
| `lognum` | `smallint unsigned` | NO | | `0` | |

Excepto _TINYINT(1)_, todo el relleno entero (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) debe quitarse del archivo `db_schema.xml`.

Para obtener más información, consulte [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportamiento ORDER BY predeterminado

Antes de la versión 8.0, las entradas se ordenaban por clave externa. El orden predeterminado depende del motor que se utilice.
Especifique siempre un criterio de ordenación si el código depende de un criterio de ordenación específico.

### Calificadores ASC y DESC obsoletos para GROUP BY

A partir de MySQL 8.0.13, se han eliminado los calificadores obsoletos `ASC` o `DESC` para las cláusulas `GROUP BY`. Las consultas que anteriormente dependían de la ordenación `GROUP BY` pueden producir resultados diferentes de las versiones anteriores de MySQL. Para generar un criterio de ordenación determinado, proporcione una cláusula `ORDER BY`.

## Commerce y MySQL 8

Se han realizado algunos cambios en Adobe Commerce para admitir correctamente MySQL 8.

### Comportamiento de consulta e inserción

Adobe Commerce deshabilitó el comportamiento de validación normal al establecer SET SQL_MODE=&#39;&#39; en `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Con la validación deshabilitada, es posible que MySQL trunque los datos. En MySQL, el comportamiento de la consulta ha cambiado: `Select * on my_table where IP='127.0.0.1'` ya no devuelve resultados porque la dirección IP ahora se ve correctamente como una cadena, en lugar de como un número entero.

## Actualización de MySQL 5.7 a MySQL 8

Para actualizar correctamente MySQL de la versión 5.7 a la versión 8, debe seguir estos pasos en orden:

1. Actualice Adobe Commerce a 2.4.0.
Pruebe todo y asegúrese de que el sistema funciona según lo esperado.
1. Activar modo de mantenimiento:

   ```bash
   bin/magento maintenance:enable
   ```

1. Hacer una copia de seguridad de base de datos:

   ```bash
   bin/magento setup:backup --db
   ```

1. Actualice MySQL a la versión 8.
1. Importe los datos de copia de seguridad en MySQL.
1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Desactivar el modo de mantenimiento:

   ```bash
   bin/magento maintenance:disable
   ```

## Configuración de la instancia de base de datos

En esta sección se explica cómo crear una instancia de base de datos para Adobe Commerce. Aunque se recomienda una nueva instancia de base de datos, puede instalar Adobe Commerce con una instancia de base de datos existente.

Para configurar una instancia de base de datos MySQL:

1. Inicie sesión en el servidor de la base de datos como cualquier usuario.
1. Vaya al símbolo del sistema de MySQL:

   ```bash
   mysql -u root -p
   ```

1. Escriba la contraseña del usuario MySQL `root` cuando se le solicite.
1. Introduzca los siguientes comandos en el orden mostrado para crear una instancia de base de datos denominada `magento` con el nombre de usuario `magento`:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Escriba `exit` para salir del símbolo del sistema.

1. Compruebe la base de datos:

   ```bash
   mysql -u magento -p
   ```

   Si se muestra el monitor MySQL, ha creado correctamente la base de datos. Si aparece un error, repita los comandos anteriores.

1. Si el servidor web y el servidor de base de datos están en hosts diferentes, realice las tareas descritas en este tema en el host del servidor de base de datos y, a continuación, vea [Configurar una conexión de base de datos MySQL remota](mysql-remote.md).

   Le recomendamos que configure la instancia de la base de datos según corresponda para su negocio. Al configurar la base de datos, tenga en cuenta lo siguiente:

   * Los indizadores requieren valores superiores de `tmp_table_size` y `max_heap_table_size` (por ejemplo, 64 M). Si configura el parámetro `batch_size`, puede ajustar ese valor junto con la configuración del tamaño de la tabla para mejorar el rendimiento del indizador. Consulte la [Guía de optimización](../../../performance/configuration.md) para obtener más información.

   * Para obtener un rendimiento óptimo, asegúrese de que todas las tablas de índice MySQL y Adobe Commerce se puedan conservar en memoria (por ejemplo, configure `innodb_buffer_pool_size`).

   * La reindexación en MariaDB 10.4 tarda más tiempo en comparación con otras versiones de MariaDB o MySQL. Consulte [Prácticas recomendadas de configuración](../../../performance/configuration.md#indexers).

1. Para que los campos MySQL `TIMESTAMP` sigan las preferencias y la composición esperadas por la arquitectura de esquema declarativo de la aplicación, la variable del sistema `explicit_defaults_for_timestamp` debe establecerse en `on`.

   Referencias:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Si esta configuración no está habilitada, `bin/magento setup:db:status` siempre informa que `Declarative Schema is not up to date`.

>[!NOTE]
>
>La configuración `explicit_defaults_for_timestamp` está obsoleta. Esta opción controla los comportamientos de TIMESTAMP obsoletos que se eliminarán en una versión futura de MySQL. Cuando se eliminan esos comportamientos, también se elimina la configuración `explicit_defaults_for_timestamp`.

>[!WARNING]
>
>Para Adobe Commerce en proyectos de infraestructura en la nube, la configuración de `explicit_defaults_for_timestamp` para MySQL (MariaDB) tiene el valor predeterminado _OFF_.

{{$include /help/_includes/maria-db-config.md}}
