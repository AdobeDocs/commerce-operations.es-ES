---
title: Configuración de una conexión de base de datos MySQL remota
description: Siga estos pasos para configurar una conexión de base de datos remota para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# Configuración de una conexión de base de datos MySQL remota

A veces, es posible que desee alojar la base de datos en un servidor independiente en lugar de ejecutar el servidor de base de datos y el servidor web en el mismo equipo.

Adobe ha proporcionado una forma de conectarse a un servidor MySQL en un equipo diferente. Desde Adobe Commerce y Magento Open Source 2.4.3, también puede configurar la aplicación para que utilice una base de datos de Amazon Web Service (AWS) Aurora sin cambios de código.

Aurora es un servidor MySQL de alto rendimiento y totalmente compatible alojado en AWS.

## Conexión a una base de datos de AWS Aurora

El uso de Aurora como base de datos es tan fácil como especificar la base de datos en la configuración normal de Adobe Commerce y Magento Open Source, utilizando el conector predeterminado de la base de datos.

Al ejecutarse `bin/magento setup:install`, utilice la información de Aurora en la `db-` campos:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

La variable `db-host` es la dirección URL de Aurora con la variable `https://` y final `:portnumber`  eliminado.

## Configuración de una conexión de base de datos remota

>[!NOTE]
>
>Se trata de un tema avanzado que debe ser utilizado únicamente por un administrador de red o de base de datos experimentado. Debe tener `root` acceso al sistema de archivos y debe poder iniciar sesión en MySQL como `root`.

### Requisitos previos

Antes de comenzar, debe:

* [Instalación del servidor MySQL](mysql.md) en el servidor de base de datos.
* [Crear una instancia de base de datos](mysql.md#configuring-the-database-instance) en el servidor de base de datos.
* Instale el cliente MySQL en su nodo web Adobe Commerce o Magento Open Source. Consulte la documentación de MySQL para obtener más información.

### Alta disponibilidad

Utilice las siguientes directrices para configurar las conexiones de base de datos remotas si el servidor web o el servidor de base de datos están agrupados:

* Debe configurar una conexión para cada nodo de servidor web.
* Normalmente, se configura una conexión de base de datos con el equilibrador de carga de la base de datos; sin embargo, la agrupación de bases de datos puede ser compleja y la configuración depende de usted. Adobe no realiza recomendaciones específicas para la agrupación en clústeres de bases de datos.

   Para obtener más información, consulte [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Solución de problemas de conexión

Si tiene problemas para conectarse a cualquiera de los hosts, haga ping primero en el otro host para asegurarse de que esté disponible. Es posible que deba permitir conexiones de un host a otro modificando el firewall y las reglas SELinux (si utiliza SELinux).

## Crear la conexión remota

Para crear una conexión remota:

1. En el servidor de la base de datos, como usuario con `root` privilegios, abra el archivo de configuración MySQL.

   Para localizarlo, introduzca el siguiente comando:

   ```bash
   mysql --help
   ```

   La ubicación es similar a la siguiente:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >En Ubuntu 16, la ruta de acceso suele ser `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Busque en el archivo de configuración `bind-address`.

   Si existe, cambie el valor como se indica a continuación.

   Si no existe, agréguelo a la variable `[mysqld]` para obtener más información.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Consulte [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), especialmente si tiene un servidor web agrupado.

1. Guarde los cambios en el archivo de configuración y salga del editor de texto.
1. Reinicie el servicio MySQL:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Si MySQL no se inicia, busque en syslog el origen del problema. Resuelva el problema utilizando [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) u otra fuente autorizada.

## Conceder acceso a un usuario de una base de datos

Para permitir que el nodo web se conecte al servidor de base de datos, debe conceder a un usuario de base de datos de nodo web acceso a la base de datos en el servidor remoto.

Este ejemplo concede a la variable `root` acceso completo del usuario de la base de datos a la base de datos en el host remoto.

Para conceder acceso a un usuario de una base de datos:

1. Inicie sesión en el servidor de la base de datos.
1. Conéctese a la base de datos MySQL como `root` usuario.
1. Introduzca el siguiente comando:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Por ejemplo,

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Si el servidor web está agrupado, introduzca el mismo comando en cada servidor web. Debe utilizar el mismo nombre de usuario para cada servidor web.

## Comprobar el acceso a la base de datos

En el host del nodo web, introduzca el siguiente comando para verificar que la conexión funciona:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Si el monitor MySQL se muestra de la siguiente manera, la base de datos está lista para Adobe Commerce o Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Si el servidor web está agrupado, introduzca el comando en cada host de servidor web.

## Instalación de Adobe Commerce o Magento Open Source

Al instalar Adobe Commerce o Magento Open Source, debe especificar lo siguiente:

* La URL base (también denominada *dirección de tienda*) especifica el nombre de host o la dirección IP del *nodo web*
* El host de base de datos es *servidor de bases de datos remotas* Dirección IP (o equilibrador de carga si el servidor de base de datos está agrupado)
* El nombre de usuario de la base de datos es *nodo web local* usuario de la base de datos al que ha dado acceso
* La contraseña de la base de datos es la contraseña del usuario del nodo web local
* Nombre de base de datos es el nombre de la base de datos en el servidor remoto
