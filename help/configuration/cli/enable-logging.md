---
title: Habilitar el registro
description: Obtenga información sobre cómo habilitar y deshabilitar tipos de registro.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Habilitar el registro

{{file-system-owner}}

## Registro de Debug

De forma predeterminada, Commerce escribe en el registro de depuración (`<install_directory>/var/log/debug.log`) cuando está en modo predeterminado o de desarrollo, pero no cuando está en modo de producción. Utilice la variable `bin/magento setup:config:set --enable-debug-logging` para cambiar el valor predeterminado.

>[!INFO]
>
>A partir de Commerce 2.3.1, ya no puede usar la variable `bin/magento config:set dev/debug/debug_logging` para habilitar o deshabilitar el registro de depuración para el modo actual.

### Para habilitar el registro de depuración

1. Utilice la variable `setup:config:set` para habilitar el registro de depuración para el modo actual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

### Para desactivar el registro de depuración

1. Utilice la variable `setup:config:set` para desactivar el registro de depuración para el modo actual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

## Registro de bases de datos

De forma predeterminada, Commerce escribe los registros de actividad de la base de datos en la variable `<install-dir>/var/debug/db.log` archivo.

### Para habilitar el registro de base de datos

1. Utilice la variable `dev:query-log` para habilitar o deshabilitar el registro de base de datos.

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

## Registro de crones

Con el lanzamiento de la versión 2.3.1, Commerce ahora crea una `cron` log. \
El comercio ha hecho recientemente que el registro de crones sea más detallado, lo que ha proporcionado más información pero alargado el `system.log` considerablemente.
Mover `cron` información a un registro dedicado facilita la lectura de ambos registros.

De forma predeterminada, Commerce escribe `cron` información de `<install-directory>/var/log/cron.log` archivo.

## Registro de Syslog

De forma predeterminada, Commerce escribe _syslog_ inicia sesión en el sistema operativo `syslog` archivo.
A partir de Commerce 2.3.1, debe usar la variable `magento` para habilitar o deshabilitar el syslog.
Se ha eliminado la configuración de Administración.

### Para habilitar el registro de syslog

Iniciando sesión en `syslog` está desactivado de forma predeterminada.

1. Utilice la variable `setup:config:set` para cambiar el `dev/syslog/syslog_logging` valor de base de datos en `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

### Para desactivar el registro de syslog

1. Utilice la variable `setup:config:set` para cambiar el `dev/syslog/syslog_logging` valor de base de datos en `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```
