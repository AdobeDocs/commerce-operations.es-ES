---
title: Copia de seguridad y reversión del sistema de archivos, medios y base de datos
description: Siga estos pasos para realizar copias de seguridad y restaurar la aplicación de Adobe Commerce o Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# Copia de seguridad y reversión del sistema de archivos, medios y base de datos

Este comando permite realizar una copia de seguridad:

* El sistema de archivos (excepto `var` y `pub/static` directorios)
* La variable `pub/media` directory
* La base de datos

Las copias de seguridad se almacenan en la variable `var/backups` y se puede restaurar en cualquier momento mediante la función [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

Después de realizar la copia de seguridad, puede [rollback](#rollback) más tarde.

>[!TIP]
>
>Para Adobe Commerce en proyectos de infraestructura en la nube, consulte [Administración de copias instantáneas y copias de seguridad](https://devdocs.magento.com/cloud/project/project-webint-snap.html) en el _Guía de Cloud_.

## Habilitar copias de seguridad

La función de copia de seguridad está deshabilitada de forma predeterminada. Para habilitar, introduzca el siguiente comando CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Aviso de fin de compatibilidad:**
>La funcionalidad de copia de seguridad está obsoleta a partir de 2.1.16, 2.2.7 y 2.3.0. Se recomienda investigar tecnologías de copia de seguridad adicionales y herramientas de copia de seguridad binaria (como Percona XtraBackup).

## Establecer el límite de archivos abiertos

La reversión a una copia de seguridad anterior puede fallar silenciosamente, lo que da como resultado que los datos incompletos se escriban en el sistema de archivos o en la base de datos utilizando la variable [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

A veces, una cadena de consulta larga hace que el espacio de memoria asignado del usuario se quede sin memoria debido a demasiadas llamadas recursivas.

## Cómo configurar archivos abiertos `ulimit`

Se recomienda configurar los archivos abiertos [`ulimit`](https://ss64.com/bash/ulimit.html) para el usuario del sistema de archivos a un valor de `65536` o más.

Puede hacerlo en la línea de comandos o puede convertirlo en una configuración permanente para el usuario editando su script shell.

Antes de continuar, si aún no lo ha hecho, cambie a la [propietario del sistema de archivos](../prerequisites/file-system/overview.md).

Comando:

```bash
ulimit -s 65536
```

Puede cambiar esto a un valor mayor si es necesario.

>[!NOTE]
>
>La sintaxis de los archivos abiertos `ulimit` depende del shell de UNIX que utilice. La configuración anterior debería funcionar con CentOS y Ubuntu con el shell de Bash. Sin embargo, para macOS, la configuración correcta es `ulimit -S 65532`. Consulte una página de comando man o referencia del sistema operativo para obtener más información.

Para establecer opcionalmente el valor en el shell Bash del usuario:

1. Si aún no lo ha hecho, cambie a la [propietario del sistema de archivos](../prerequisites/file-system/overview.md).
1. Apertura `/home/<username>/.bashrc` en un editor de texto.
1. Añada la siguiente línea:

   ```bash
   ulimit -s 65536
   ```

1. Guarde los cambios en `.bashrc` y salga del editor de texto.

>[!WARNING]
>
>Le recomendamos que evite establecer un valor para [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) en el `php.ini` porque puede provocar devoluciones incompletas sin aviso de error.

## Copia de seguridad

Uso de comandos:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

El comando realiza las siguientes tareas:

1. Coloca la tienda en modo de mantenimiento.
1. Ejecuta una de las siguientes opciones de comando.

   | Opción | Significado | Nombre y ubicación del archivo de copia de seguridad |
   |--- |--- |--- |
   | `--code` | Realiza una copia de seguridad del sistema de archivos (excepto los directorios var y pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Haga una copia de seguridad del directorio de medios/pub. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Haga una copia de seguridad de la base de datos. | `var/backups/<timestamp>/_db.sql` |

1. Quita el almacén del modo de mantenimiento.

Por ejemplo, para realizar una copia de seguridad del sistema de archivos y la base de datos,

```bash
bin/magento setup:backup --code --db
```

Se muestran mensajes similares a los siguientes:

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Reversión

En esta sección se explica cómo restaurar una copia de seguridad que realizó anteriormente. Debe conocer el nombre de archivo del archivo de copia de seguridad para restaurar.

Para encontrar el nombre de las copias de seguridad, escriba:

```bash
bin/magento info:backups:list
```

La primera cadena del nombre del archivo de copia de seguridad es la marca de tiempo.

Para volver a una copia de seguridad anterior, introduzca:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Por ejemplo, para restaurar una copia de seguridad multimedia denominada `1440611839_filesystem_media.tgz`, introduzca

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Se muestran mensajes similares a los siguientes:

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
