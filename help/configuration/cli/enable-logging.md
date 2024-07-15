---
title: Habilitar registro
description: Obtenga información sobre cómo habilitar y deshabilitar tipos de registro.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Habilitar registro

{{file-system-owner}}

## Registro de Debug

De manera predeterminada, Commerce escribe en el registro de depuración (`<install_directory>/var/log/debug.log`) cuando está en modo predeterminado o de desarrollo, pero no cuando está en modo de producción. Utilice el comando `bin/magento setup:config:set --enable-debug-logging` para cambiar el valor predeterminado.

>[!INFO]
>
>A partir de Commerce 2.3.1, ya no puede utilizar el comando `bin/magento config:set dev/debug/debug_logging` para habilitar o deshabilitar el registro de depuración para el modo actual.

### Para habilitar el registro de depuración

1. Utilice el comando `setup:config:set` para habilitar el registro de depuración para el modo actual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

### Para deshabilitar el registro de depuración

1. Utilice el comando `setup:config:set` para deshabilitar el registro de depuración para el modo actual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

## Registro de base de datos

De manera predeterminada, Commerce escribe los registros de actividad de la base de datos en el archivo `<install-dir>/var/debug/db.log`.

### Para habilitar el registro en base de datos

1. Utilice el comando `dev:query-log` para habilitar o deshabilitar el registro en la base de datos.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

## Registro de Cron

Con la versión 2.3.1 de, Commerce ahora crea un registro `cron` independiente. \
Commerce recientemente hizo que el registro de cron fuera más detallado, lo que proporcionó más información pero prolongó considerablemente el `system.log`.
Mover la información de `cron` a un registro dedicado facilita la lectura de ambos registros.

De manera predeterminada, Commerce escribe información de `cron` en el archivo `<install-directory>/var/log/cron.log`.

## Registro de Syslog

De manera predeterminada, Commerce escribe registros de _syslog_ en el archivo del sistema operativo `syslog`.
A partir de Commerce 2.3.1, debe utilizar el comando `magento` para habilitar o deshabilitar el registro del sistema.
Se ha eliminado la configuración del Administrador.

### Para habilitar el registro syslog

El registro en `syslog` está deshabilitado de manera predeterminada.

1. Use el comando `setup:config:set` para cambiar el valor de la base de datos `dev/syslog/syslog_logging` a `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

### Para deshabilitar el registro de syslog

1. Use el comando `setup:config:set` para cambiar el valor de la base de datos `dev/syslog/syslog_logging` a `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```
