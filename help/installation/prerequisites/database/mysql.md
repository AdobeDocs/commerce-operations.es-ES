---
title: Directrices MySQL
description: Siga estos pasos para instalar y configurar MySQL y MariaDB para instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 0%

---


# Directrices generales de MySQL

Consulte [Requisitos del sistema](../../system-requirements.md) para versiones compatibles de MySQL.

Adobe _strong_ recomienda que observe el estándar siguiente al configurar la base de datos:

* Uso de Adobe Commerce y Magento Open Source [Déclencheur de base de datos MySQL](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) para mejorar el acceso a la base de datos durante la reindexación. Estos se crean cuando el modo de indexador está configurado en [programación](../../../configuration/cli/manage-indexers.md#configure-indexers). La aplicación no admite déclencheur personalizados en la base de datos porque los déclencheur personalizados pueden provocar incompatibilidades con versiones futuras de Adobe Commerce y Magento Open Source.
* Familiarícese con [estas posibles limitaciones de déclencheur MySQL](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) antes de continuar.
* Para mejorar la postura de seguridad de la base de datos, active la variable [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) El modo SQL para evitar almacenar valores de datos no válidos, lo que podría provocar interacciones de base de datos no deseadas.
* Adobe Commerce y el Magento Open Source sí _not_ admiten replicación basada en instrucciones MySQL. Asegúrese de utilizar _only_ [replicación basada en filas](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce y Magento Open Source utilizan actualmente `CREATE TEMPORARY TABLE` instrucciones dentro de transacciones, que son [incompatible](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) con implementaciones de base de datos, utilice replicación basada en GTID, como [Instancias de segunda generación de Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Considere MySQL para Cloud SQL 8.0 como alternativa.

>[!NOTE]
>
>Si el servidor web y el servidor de base de datos están en hosts diferentes, realice las tareas que se tratan en este tema en el host del servidor de base de datos y, a continuación, consulte [Configuración de una conexión de base de datos MySQL remota](mysql-remote.md).

## Instalación de MySQL en Ubuntu

Adobe Commerce y Magento Open Source 2.4 requieren una instalación limpia de MySQL 8.0. Siga los enlaces siguientes para obtener instrucciones sobre la instalación de MySQL en su equipo.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Si espera importar grandes cantidades de productos, puede aumentar el valor de [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) que es mayor que el valor predeterminado, 16 MB.

>[!NOTE]
>
>El valor predeterminado se aplica a Adobe Commerce en la infraestructura de la nube _y_ proyectos locales. Los clientes de Adobe Commerce en la infraestructura de nube Pro deben abrir un ticket de asistencia para aumentar el `max_allowed_packet` valor. Adobe Commerce en la infraestructura de nube Los clientes iniciales pueden aumentar el valor actualizando la configuración en la variable `/etc/mysql/mysql.cnf` archivo.

Para aumentar el valor, abra el `/etc/mysql/mysql.cnf` en un editor de texto y busque el valor de `max_allowed_packet`. Guarde los cambios en la `mysql.cnf` , cierre el editor de texto y reinicie MySQL (`service mysql restart`).

Para verificar opcionalmente el valor que ha establecido, introduzca el siguiente comando en una `mysql>` Solicitud de confirmación:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

A continuación, [Configuración de la instancia de base de datos](#configuring-the-database-instance).

## Cambios en MySQL 8

Para Adobe Commerce y Magento Open Source 2.4, hemos agregado compatibilidad con MySQL 8.
En esta sección se describen los principales cambios realizados en MySQL 8 que los desarrolladores deben tener en cuenta.

### Se ha eliminado la anchura para tipos enteros (relleno)

La especificación de anchura de visualización para tipos de datos enteros (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) ha quedado obsoleta en MySQL 8.0.17. Las instrucciones que incluyen definiciones de tipo de datos en su salida ya no muestran el ancho de visualización para tipos enteros, excepto para TINYINT(1). Los conectores MySQL suponen que las columnas TINYINT(1) se originaron como columnas BOOLEAN. Esta excepción les permite seguir asumiendo esa suposición.

#### Ejemplo

Describir admin_user en mysql 8.19

| Campo | Tipo | Null | Clave | Predeterminado | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NO | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | SÍ |  | `NULL` |  |
| `lastname` | `varchar(32`) | SÍ |  | `NULL` |  |
| `email` | `varchar(128)` | SÍ |  | `NULL` |  |
| `username` | `varchar(40)` | SÍ | UNI | `NULL` |  |
| `password` | `varchar(255)` | NO |  | `NULL` |  |
| `created` | `timestamp` | NO |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NO |  | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` al actualizar `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | SÍ |  | `NULL` |  |
| `lognum` | `smallint unsigned` | NO |  | `0` |  |

Excepto para _TINYINT(1)_, todo el relleno entero (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) debe eliminarse del `db_schema.xml` archivo.

Para obtener más información, consulte [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Comportamiento predeterminado ORDER BY

Antes de la versión 8.0, las entradas se ordenaban por clave externa. El orden de clasificación predeterminado depende del motor utilizado.
Especifique siempre un orden si el código depende de un orden específico.

### Cualificadores ASC y DESC obsoletos para GROUP BY

A partir de MySQL 8.0.13, el `ASC` o `DESC` calificadores para `GROUP BY` se han eliminado. Consultas en las que se dependía anteriormente `GROUP BY` la clasificación puede producir resultados que difieren de versiones anteriores de MySQL. Para generar un orden determinado, proporcione un `ORDER BY` cláusula.

## Commerce y MySQL 8

Se han realizado algunos cambios en Adobe Commerce y Magento Open Source para admitir correctamente MySQL 8.

### Comportamiento de consulta e inserción

Adobe Commerce y el Magento Open Source deshabilitaron el comportamiento de validación normal al establecer SET SQL_MODE=&#39;&#39; en `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Con la validación deshabilitada, es posible que MySQL trunca los datos. En MySQL, el comportamiento Query ha cambiado: `Select * on my_table where IP='127.0.0.1'` ya no devuelve resultados porque la dirección IP ahora se ve correctamente como una cadena, en lugar de como un número entero.

## Actualización de MySQL 5.7 a MySQL 8

Para actualizar correctamente MySQL de la versión 5.7 a la versión 8, debe seguir estos pasos en orden:

1. Actualice Adobe Commerce o Magento Open Source a 2.4.0. Pruebe todo y asegúrese de que el sistema funciona según lo esperado.
1. Habilitar modo de mantenimiento:

   ```bash
   bin/magento maintenance:enable
   ```

1. Hacer una copia de seguridad de la base de datos:

   ```bash
   bin/magento setup:backup --db
   ```

1. Actualice MySQL a la versión 8.
1. Importe los datos de copia de seguridad en MySQL.
1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```

1. Desactivar modo de mantenimiento:

   ```bash
   bin/magento maintenance:disable
   ```

## Configuración de la instancia de base de datos

En esta sección se explica cómo crear una instancia de base de datos para Adobe Commerce o Magento Open Source. Aunque se recomienda una nueva instancia de base de datos, también se puede instalar Adobe Commerce o Magento Open Source con una instancia de base de datos existente.

Para configurar una instancia de base de datos MySQL:

1. Inicie sesión en el servidor de la base de datos como cualquier usuario.
1. Acceda al símbolo del sistema MySQL:

   ```bash
   mysql -u root -p
   ```

1. Introduzca el MySQL `root` contraseña del usuario cuando se le pida.
1. Introduzca los siguientes comandos en el orden mostrado para crear una instancia de base de datos denominada `magento` con nombre de usuario `magento`:

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

1. Entrar `exit` para salir del símbolo del sistema.

1. Compruebe la base de datos:

   ```bash
   mysql -u magento -p
   ```

   Si aparece el monitor MySQL, ha creado la base de datos correctamente. Si aparece un error, repita los comandos anteriores.

1. Si el servidor web y el servidor de base de datos están en hosts diferentes, realice las tareas que se tratan en este tema en el host del servidor de base de datos y, a continuación, consulte [Configuración de una conexión de base de datos MySQL remota](mysql-remote.md).

   Le recomendamos que configure la instancia de base de datos según corresponda para su negocio. Al configurar la base de datos, tenga en cuenta lo siguiente:

   * Los indexadores requieren `tmp_table_size` y `max_heap_table_size` (por ejemplo, 64 M). Si configura la variable `batch_size` , puede ajustar ese valor junto con la configuración de tamaño de tabla para mejorar el rendimiento del indexador. Consulte la [Guía de optimización](../../../performance/configuration.md) para obtener más información.

   * Para obtener un rendimiento óptimo, asegúrese de que todas las tablas de índice MySQL y Adobe Commerce o Magento Open Source puedan guardarse en la memoria (por ejemplo, configure `innodb_buffer_pool_size`).

   * La reindexación en MariaDB 10.4 toma más tiempo que otras versiones de MariaDB o MySQL. Consulte [Prácticas recomendadas de configuración](../../../performance/configuration.md#indexers).

1. Para MySQL `TIMESTAMP` para seguir las preferencias y la composición esperadas por la arquitectura de esquema declarativo de la aplicación, la variable del sistema `explicit_defaults_for_timestamp` debe estar configurado como `on`.

   Referencias:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Si esta configuración no está habilitada, `bin/magento setup:db:status` siempre indica que la variable `Declarative Schema is not up to date`.

>[!NOTE]
>
>La variable `explicit_defaults_for_timestamp` está en desuso. Esta configuración controla los comportamientos TIMESTAMP obsoletos que se eliminarán en una futura versión de MySQL. Cuando se eliminan esos comportamientos, la variable `explicit_defaults_for_timestamp` también se elimina.

>[!WARNING]
>
>Para Adobe Commerce en proyectos de infraestructura en la nube, la variable `explicit_defaults_for_timestamp` configuración de MySQL (MariaDB) predeterminada es _OFF_.

La reindexación en MariaDB 10.4 toma más tiempo que otras versiones de MariaDB o MySQL. Para acelerar la reindexación, se recomienda configurar estos parámetros de configuración de MariaDB:

* optimizer_switch=&#39;rowid_filter=off&#39;
* optimizer_use_condition_selectivity = 1
