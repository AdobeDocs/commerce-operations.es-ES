---
title: Configurar una conexión de base de datos MySQL remota
description: Siga estos pasos para configurar una conexión de base de datos remota para instalaciones locales de Adobe Commerce y Magento Open Source.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Configurar una conexión de base de datos MySQL remota

A veces puede que desee alojar la base de datos en un servidor independiente en lugar de ejecutar el servidor de base de datos y el servidor web en el mismo equipo.

El Adobe ha proporcionado una forma de conectarse a un servidor MySQL en un equipo diferente. A partir de Adobe Commerce y Magento Open Source 2.4.3, también puede configurar la aplicación para que utilice una base de datos de Amazon Web Service (AWS) Aurora sin cambios de código.

Aurora es un servidor MySQL totalmente compatible y de alto rendimiento alojado en AWS.

## Conexión a una base de datos de AWS Aurora

Usar Aurora como base de datos es tan fácil como especificar la base de datos en la configuración de configuración normal de Adobe Commerce y Magento Open Source, utilizando el conector de base de datos predeterminado.

Al ejecutar `bin/magento setup:install`, use la información de Aurora en el `db-` campos:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

El `db-host` El valor es la URL de Aurora con el `https://` y final `:portnumber`  eliminado.

## Configurar una conexión de base de datos remota

>[!NOTE]
>
>Se trata de un tema avanzado que sólo debe utilizar un administrador de red o de base de datos experimentado. Debe tener `root` tener acceso al sistema de archivos y debe poder iniciar sesión en MySQL como `root`.

### Requisitos previos

Antes de empezar, debe:

* [Instalar el servidor MySQL](mysql.md) en el servidor de base de datos.
* [Crear una instancia de base de datos](mysql.md#configuring-the-database-instance) en el servidor de base de datos.
* Instale el cliente MySQL en su nodo web Adobe Commerce o Magento Open Source. Consulte la documentación de MySQL para obtener más detalles.

### Alta disponibilidad

Siga estas directrices para configurar conexiones a bases de datos remotas si el servidor web o de base de datos está en clúster:

* Debe configurar una conexión para cada nodo de servidor web.
* Normalmente, se configura una conexión de base de datos con el equilibrador de carga de base de datos; sin embargo, la agrupación en clúster de base de datos puede ser compleja y su configuración depende de usted. El Adobe no realiza recomendaciones específicas para la agrupación en clúster de bases de datos.

   Para obtener más información, consulte [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Solución de problemas de conexión

Si tiene problemas para conectarse a cualquiera de los hosts, primero haga ping al otro host para asegurarse de que esté accesible. Es posible que deba permitir conexiones de un host a otro modificando las reglas de cortafuegos y SELinux (si utiliza SELinux).

## Crear la conexión remota

Para crear una conexión remota:

1. En el servidor de la base de datos, como usuario con `root` privilegios, abra su archivo de configuración MySQL.

   Para localizarlo, introduzca el siguiente comando:

   ```bash
   mysql --help
   ```

   La ubicación se muestra de forma similar a la siguiente:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >En Ubuntu 16, la ruta es generalmente `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Buscar en el archivo de configuración `bind-address`.

   Si existe, cambie el valor de la siguiente manera.

   Si no existe, agréguela al `[mysqld]` sección.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Consulte [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), especialmente si tiene un servidor web en clúster.

1. Guarde los cambios en el archivo de configuración y salga del editor de texto.
1. Reinicie el servicio MySQL:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Si MySQL no se inicia, busque en syslog el origen del problema. Resuelva el problema utilizando [Documentación de MySQL](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) u otra fuente autorizada.

## Conceder acceso a un usuario de base de datos

Para permitir que el nodo web se conecte al servidor de base de datos, debe conceder a un usuario de base de datos de nodo web acceso a la base de datos en el servidor remoto.

En este ejemplo se concede la `root` acceso completo del usuario de la base de datos a la base de datos en el host remoto.

Para conceder acceso a un usuario de base de datos:

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
   >Si el servidor web está agrupado, escriba el mismo comando en todos los servidores web. Debe utilizar el mismo nombre de usuario para cada servidor web.

## Verificar acceso a base de datos

En el host del nodo web, introduzca el siguiente comando para comprobar que la conexión funciona:

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

* La dirección URL base (también denominada *dirección del almacén*) especifica el nombre de host o la dirección IP del *nodo web*
* El host de base de datos es *servidor de base de datos remoto* Dirección IP (o equilibrador de carga si el servidor de la base de datos está agrupado)
* El nombre de usuario es *nodo web local* usuario de base de datos al que ha dado acceso
* Contraseña de base de datos es la contraseña del usuario del nodo web local
* Nombre de base de datos es el nombre de la base de datos en el servidor remoto
