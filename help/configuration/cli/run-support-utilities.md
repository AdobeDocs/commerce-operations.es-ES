---
title: Ejecute las utilidades de soporte
description: Solucionar problemas del proyecto de Commerce con la utilidad de soporte integrada.
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Ejecute las utilidades de soporte

{{ee-only}}

{{file-system-owner}}

Las utilidades de soporte de Adobe Commerce (también denominadas [Recopilador de datos](https://docs.magento.com/user-guide/system/support-data-collector.html): permite a los usuarios recopilar información sobre la resolución de problemas de su sistema que nuestro equipo de asistencia puede utilizar.

Adobe Commerce utiliza estas copias de seguridad, también denominadas _volcados_, para analizar los problemas que requieren acceso a su código. A continuación se muestra un escenario típico:

1. Tiene algún problema con su tienda de comercio y se pone en contacto con el servicio de asistencia técnica de Adobe Commerce.
1. El servicio de asistencia determina que deben ver el código o la base de datos para reproducir el problema.
1. Haga una copia de seguridad del código en un `.tar.gz` archivo.

   Esta copia de seguridad _excluye los archivos multimedia para acelerar el proceso y dar como resultado un archivo mucho más pequeño.

1. La base de datos se copia de seguridad en un `.tar.gz` archivo.

   De forma predeterminada, los datos confidenciales tienen un cifrado hash al realizar la copia de seguridad.

1. Las copias de seguridad se cargan en un servicio de uso compartido de archivos.
1. La asistencia analiza los problemas sin afectar al entorno de desarrollo o producción.

Las utilidades pueden tardar varios minutos en completarse.

## Crear una copia de seguridad de código

Este comando hace una copia de seguridad del código y lo comprime en `tar.gz` formato.

{{tip-backup-command}}

Opciones de comando:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Donde:

- **`--name`** especifica el nombre del archivo de volcado (opcional). Si omite este parámetro, el archivo de volcado tiene una marca de fecha y hora.
- **`-o|--output=<path>`** es la ruta absoluta del sistema de archivos para almacenar la copia de seguridad (requerido).
- **`-l|--logs`** incluye archivos de registro (opcional).

Por ejemplo, para crear una copia de seguridad de código denominada `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Una vez finalizado el comando, proporcione la copia de seguridad del código al Soporte técnico de Adobe Commerce.

## Crear una copia de seguridad de base de datos

Este comando realiza una copia de seguridad de la base de datos de Commerce y la comprime en `tar.gz` formato.

{{tip-backup-command}}

Opciones de comando:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Donde:

- **`--name`** especifica el nombre del archivo de volcado (opcional). Si omite este parámetro, el archivo de volcado tiene una marca de fecha y hora.
- **`-o|--output=<path>` es la ruta absoluta del sistema de archivos para almacenar la copia de seguridad (requerido).
- **`-l|--logs`** incluye archivos de registro (opcional).
- **`-i|--ignore-sanitize`** significa que se conservan los datos; omita el indicador para hash datos confidenciales almacenados en la base de datos al crear la copia de seguridad (opcional).

Los datos confidenciales incluyen información de clientes de las siguientes tablas de base de datos:

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

Una vez finalizado el comando, proporcione la copia de seguridad de la base de datos al Soporte técnico de Adobe Commerce.

## Solución de problemas: mostrar utilidades y rutas

Proporcionamos comandos que muestran las rutas a las utilidades requeridas por el Recopilador de datos y la línea de comandos. Puede utilizar estos comandos, por ejemplo, si se muestran errores como los siguientes en la pantalla Administrador o en la línea de comandos:

```terminal
Utility lsof not found
```

Ejecute los siguientes comandos en el orden mostrado para mostrar las rutas a las aplicaciones utilizadas por las utilidades de soporte y el Recopilador de datos:

1. Cambie al directorio de instalación de Commerce.

   Por ejemplo, `cd /var/www/magento2`

   >[!INFO]
   >
   >Los comandos se ejecutan correctamente _only_ del directorio de instalación.

1. `bin/magento support:utility:paths` crea `<magento_root>/var/support/Paths.php`, que enumera las rutas a todas las aplicaciones utilizadas por la utilidad.
1. `bin/magento support:utility:check` muestra las rutas del sistema de archivos.

A continuación se muestra una muestra:

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

Para resolver los problemas con la ejecución de las herramientas, asegúrese de que estas aplicaciones están instaladas y se encuentran en el `$PATH` variable de entorno.
