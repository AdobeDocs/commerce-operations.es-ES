---
title: Requisitos previos de instalación local
description: Obtenga más información acerca de las dependencias de software necesarias para las instalaciones locales de Adobe Commerce.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: db2256f5327897a4376a0d038ce697e8f93235af
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# Requisitos previos de instalación local

Antes de instalar Adobe Commerce, debe hacer lo siguiente:

* Configure uno o más hosts que cumplan los [requisitos del sistema](../system-requirements.md) indicados en la ficha *Commerce local*.
* Si está configurando más de un nodo web con equilibrio de carga, configure y pruebe esa parte del sistema _antes_ de instalar la aplicación.
* Asegúrese de que puede realizar copias de seguridad de todo el sistema en distintos puntos durante la instalación para poder revertirlo si hay problemas.

>[!NOTE]
>
>Suponemos que está instalando Adobe Commerce en un **entorno de desarrollo**, que tiene acceso de usuario raíz a la máquina, **y** que la máquina no necesita ser altamente segura. Si va a configurar un equipo más seguro, le recomendamos encarecidamente que consulte con un administrador de red para obtener ayuda adicional.

Le recomendamos encarecidamente que actualice y actualice el software de su sistema operativo. Estas actualizaciones pueden proporcionar correcciones de seguridad y software que podrían evitar problemas futuros. ¿No sabes lo que significa todo esto? Consulte nuestra [página de información general sobre la instalación](../overview.md).

Escriba los siguientes comandos como usuario con privilegios de `root`:

* Ubuntu

  ```bash
  apt-get update
  ```

  ```bash
  apt-get upgrade
  ```

* CentOS

  ```bash
  yum -y update
  ```

  ```bash
  yum -y upgrade
  ```

## Comprobación de requisitos previos

Para comprobar los requisitos previos del sistema, introduzca los siguientes comandos:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

Adobe Commerce es compatible con la versión 2.4 de Apache, como indica el siguiente resultado:

```
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Para instalar o actualizar Apache, consulte [Apache](web-server/apache.md).

### PHP

Consulte la ficha *Commerce local* en [requisitos del sistema](../system-requirements.md) para ver las versiones compatibles de PHP y [PHP](../system-requirements.md#php-settings) para los requisitos de PHP.

### MySQL

Compruebe que tiene una versión compatible de MySQL para la versión de Adobe Commerce que está instalando. Consulte la pestaña *Commerce local* en [Requisitos del sistema](../system-requirements.md) para ver las versiones compatibles.

```bash
mysql -u <database root user or database owner name> -p
```

Por ejemplo:

```bash
mysql -u magento -p
```

El siguiente resultado indica la versión que está ejecutando.

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Escriba `help` o `\h` para obtener ayuda. Escriba `\c` para borrar la instrucción de entrada actual.

Escriba `exit` en el símbolo del sistema `mysql>` para salir.

Para instalar o actualizar MySQL, consulte [MySQL](database/mysql.md).

### Motor de búsqueda

Para comprobar la instalación de OpenSearch:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Para comprobar la instalación de Elasticsearch:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Por ejemplo:

```bash
curl -XGET 'localhost:9200'
```

```
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
