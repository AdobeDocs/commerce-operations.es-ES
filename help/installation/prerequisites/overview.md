---
title: Requisitos previos de instalación local
description: Obtenga más información sobre las dependencias de software necesarias para las instalaciones locales de Adobe Commerce y Magento Open Source.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Requisitos previos de instalación local

Antes de instalar Adobe Commerce o Magento Open Source, debe hacer lo siguiente:

* Configure uno o varios hosts que cumplan los requisitos [requisitos del sistema](../system-requirements.md).
* Si está configurando más de un nodo web con equilibrio de carga, configure y pruebe esa parte del sistema _antes_ la aplicación se instala.
* Asegúrese de que puede realizar copias de seguridad de todo el sistema en distintos puntos durante la instalación para poder revertirlo si hay problemas.

>[!NOTE]
>
>Suponemos que va a instalar el Adobe Commerce o el Magento Open Source en un **entorno de desarrollo**, que tiene acceso de usuario raíz al equipo, **y** que la máquina no necesita ser altamente segura. Si va a configurar un equipo más seguro, le recomendamos encarecidamente que consulte con un administrador de red para obtener ayuda adicional.

Le recomendamos encarecidamente que actualice y actualice el software de su sistema operativo. Estas actualizaciones pueden proporcionar correcciones de seguridad y software que podrían evitar problemas futuros. ¿No sabes lo que significa todo esto? Consulte nuestra [página de información general de instalación](../overview.md).

Introduzca los siguientes comandos como usuario con `root` privilegios:

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

Adobe Commerce y Magento Open Source admiten la versión 2.4 de Apache como indica el siguiente resultado:

```terminal
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Para instalar o actualizar Apache, consulte [Apache](web-server/apache.md).

### PHP

Consulte [requisitos del sistema](../system-requirements.md) para versiones compatibles de PHP y [PHP] para requisitos de PHP.

### MySQL

```bash
mysql -u <database root user or database owner name> -p
```

Por ejemplo:

```bash
mysql -u magento -p
```

Compruebe que tiene la versión correcta de MySQL para la versión de Adobe Commerce o del Magento Open Source que está instalando ([consulte aquí las versiones compatibles](../system-requirements.md). El siguiente resultado indica la versión que está ejecutando.)

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: 5.7.9 MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Tipo `help` o `\h` para obtener ayuda. Tipo `\c` para borrar la instrucción de entrada actual.

Entrar `exit` en el `mysql>` Mensaje para salir.

Para instalar o actualizar MySQL, consulte [MySQL](database/mysql.md).

### Motor de búsqueda

Para comprobar la instalación de OpenSearch:

```bash
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

Para comprobar la instalación del Elasticsearch:

```bash
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Por ejemplo:

```bash
curl -XGET 'localhost:9200'
```

```terminal
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
