---
title: Realizar una copia de seguridad y una reversión del sistema de archivos, medios y base de datos
description: Siga estos pasos para realizar una copia de seguridad y restaurar la aplicación de Adobe Commerce.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Realizar una copia de seguridad y una reversión del sistema de archivos, medios y base de datos

Este comando le permite realizar una copia de seguridad:

* El sistema de archivos (excluyendo `var` y `pub/static` directorios)
* El directorio `pub/media`
* La base de datos

Las copias de seguridad se almacenan en el directorio `var/backups` y se pueden restaurar en cualquier momento mediante el comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Después de hacer la copia de seguridad, puedes [revertir](#rollback) más tarde.

>[!TIP]
>
>Para Adobe Commerce sobre proyectos de infraestructura en la nube, consulte [Administración de instantáneas y copias de seguridad](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) en la _Guía de la nube_.

## Habilitar copias de seguridad

La función de copia de seguridad está desactivada de forma predeterminada. Para habilitarlo, introduzca el siguiente comando de CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Aviso de obsolescencia:**
>&#x200B;>La funcionalidad de copia de seguridad quedará obsoleta a partir de las versiones 2.1.16, 2.2.7 y 2.3.0. Recomendamos investigar tecnologías de copia de seguridad adicionales y herramientas de copia de seguridad binaria (como Percona XtraBackup).

## Establecer el límite de archivos abiertos

Si se vuelve a una copia de seguridad anterior, se pueden producir errores de forma silenciosa, lo que hace que se escriban datos incompletos en el sistema de archivos o en la base de datos con el comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

A veces, una cadena de consulta larga hace que el espacio de memoria asignado al usuario se quede sin memoria debido a demasiadas llamadas recursivas.

## Cómo establecer los archivos abiertos `ulimit`

Se recomienda establecer los archivos abiertos [`ulimit`](https://ss64.com/bash/ulimit.html) para el usuario del sistema de archivos en un valor de `65536` o más.

Puede hacerlo en la línea de comandos o puede convertirlo en un ajuste permanente para el usuario editando su script shell.

Antes de continuar, si aún no lo ha hecho, cambie al [propietario del sistema de archivos](../prerequisites/file-system/overview.md).

Comando:

```bash
ulimit -s 65536
```

Puede cambiarlo a un valor mayor si es necesario.

>[!NOTE]
>
>La sintaxis de los archivos abiertos `ulimit` depende del shell de UNIX que utilice. La configuración anterior debería funcionar con CentOS y Ubuntu con el shell de Bash. Sin embargo, para macOS, la configuración correcta es `ulimit -S 65532`. Consulte una página de comando man o una referencia del sistema operativo para obtener más información.

Para establecer de forma opcional el valor en el shell de Bash del usuario:

1. Si aún no lo ha hecho, cambie al [propietario del sistema de archivos](../prerequisites/file-system/overview.md).
1. Abra `/home/<username>/.bashrc` en un editor de texto.
1. Añada la línea siguiente:

   ```bash
   ulimit -s 65536
   ```

1. Guarde los cambios en `.bashrc` y salga del editor de texto.

>[!WARNING]
>
>Le recomendamos que evite establecer un valor para [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) en el archivo `php.ini`, ya que puede provocar reversiones incompletas sin previo aviso de error.

## Copia de seguridad

Uso de comandos:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

El comando realiza las siguientes tareas:

1. Pone el almacén en modo de mantenimiento.
1. Ejecuta una de las siguientes opciones de comando.

   | Opción | Significado | Nombre y ubicación del archivo de copia de seguridad |
   |--- |--- |--- |
   | `--code` | Realiza una copia de seguridad del sistema de archivos (excepto de los directorios var y pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Haga una copia de seguridad del directorio pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Haga una copia de seguridad de la base de datos. | `var/backups/<timestamp>/_db.sql` |

1. Elimina el almacén del modo de mantenimiento.

Por ejemplo, para realizar una copia de seguridad del sistema de archivos y la base de datos,

```bash
bin/magento setup:backup --code --db
```

Se muestran mensajes similares a los siguientes:

```
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

En esta sección se explica cómo revertir a una copia de seguridad realizada anteriormente. Debe conocer el nombre de archivo del archivo de copia de seguridad que desea restaurar.

Para buscar el nombre de las copias de seguridad, introduzca:

```bash
bin/magento info:backups:list
```

La primera cadena del nombre del archivo de copia de seguridad es la marca de tiempo.

Para revertir a una copia de seguridad anterior, introduzca:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Por ejemplo, para restaurar una copia de seguridad de medios denominada `1440611839_filesystem_media.tgz`, escriba

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Se muestran mensajes similares a los siguientes:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
