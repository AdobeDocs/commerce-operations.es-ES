---
title: Ejecutar las utilidades de soporte
description: Solucione los problemas del proyecto de Commerce mediante la utilidad de soporte integrada.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Ejecutar las utilidades de soporte

{{ee-only}}

{{file-system-owner}}

Las utilidades de soporte de Adobe Commerce, también denominadas [Recopilador de datos](https://docs.magento.com/user-guide/system/support-data-collector.html), permiten a los usuarios recopilar información de solución de problemas acerca del sistema que puede usar nuestro equipo de soporte.

Adobe Commerce usa estas copias de seguridad, también denominadas _volcados_, para analizar los problemas que requieren acceso al código. A continuación se muestra un escenario típico:

1. Tiene un problema con su tienda de Commerce y se pone en contacto con el servicio de asistencia de Adobe Commerce.
1. La asistencia determina que necesitan ver el código o la base de datos para reproducir el problema.
1. Hace una copia de seguridad del código en un archivo de `.tar.gz`.

   Esta copia de seguridad _excluye los archivos multimedia para acelerar el proceso y dar como resultado un archivo mucho más pequeño.

1. Hace una copia de seguridad de la base de datos en un archivo de `.tar.gz`.

   De forma predeterminada, los datos confidenciales se colocan en un hash al realizar la copia de seguridad.

1. Las copias de seguridad se cargan en un servicio para compartir archivos.
1. La asistencia de analiza los problemas sin afectar al entorno de desarrollo o producción.

Las utilidades pueden tardar varios minutos en completarse.

## Crear una copia de seguridad de código

Este comando realiza una copia de seguridad del código y lo comprime en formato `tar.gz`.

{{tip-backup-command}}

Opciones de comando:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Donde:

- **`--name`** especifica el nombre del archivo de volcado (opcional). Si omite este parámetro, el archivo de volcado se marcará con la hora y la fecha.
- **`-o|--output=<path>`** es la ruta absoluta del sistema de archivos para almacenar la copia de seguridad (obligatorio).
- **`-l|--logs`** incluye archivos de registro (opcional).

Por ejemplo, para crear una copia de seguridad de código con el nombre `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Una vez completado el comando, proporcione la copia de seguridad de código al Soporte técnico de Adobe Commerce.

## Crear una copia de seguridad

Este comando realiza una copia de seguridad de la base de datos de Commerce y la comprime en formato `tar.gz`.

{{tip-backup-command}}

Opciones de comando:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Donde:

- **`--name`** especifica el nombre del archivo de volcado (opcional). Si omite este parámetro, el archivo de volcado se marcará con la hora y la fecha.
- **`-o|--output=<path>` es la ruta absoluta del sistema de archivos para almacenar la copia de seguridad (obligatorio).
- **`-l|--logs`** incluye archivos de registro (opcional).
- **`-i|--ignore-sanitize`** significa que los datos se conservan; omita el indicador para hash los datos confidenciales almacenados en la base de datos al crear la copia de seguridad (opcional).

Los datos confidenciales incluyen información del cliente de las siguientes tablas de base de datos:

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

## Solución de problemas: utilidades de visualización y rutas

Proporcionamos comandos que muestran las rutas a las utilidades requeridas por el Recopilador de datos y la línea de comandos. Puede utilizar estos comandos, por ejemplo, si se muestran errores como los siguientes en Admin o en la línea de comandos:

```terminal
Utility lsof not found
```

Ejecute los siguientes comandos en el orden mostrado para mostrar las rutas a las aplicaciones utilizadas por las utilidades de soporte y el Recopilador de datos:

1. Cambie al directorio de instalación de Commerce.

   Por ejemplo, `cd /var/www/magento2`

   >[!INFO]
   >
   >Los comandos se ejecutan correctamente _solamente_ desde el directorio de instalación.

1. `bin/magento support:utility:paths` crea `<magento_root>/var/support/Paths.php`, que enumera las rutas de acceso a todas las aplicaciones utilizadas por la utilidad.
1. `bin/magento support:utility:check` muestra las rutas de acceso al sistema de archivos.

A continuación se muestra un ejemplo:

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

Para resolver los problemas relacionados con la ejecución de las herramientas, asegúrese de que estas aplicaciones estén instaladas y se encuentren en la variable de entorno `$PATH` del usuario del servidor web.
