---
title: Habilitar registro
description: Obtenga información sobre cómo habilitar y deshabilitar tipos de registro.
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Habilitar registro

{{file-system-owner}}

## Registro de Debug

De forma predeterminada, Commerce escribe en el registro de depuración (`<install_directory>/var/log/debug.log`) cuando está en modo predeterminado o de desarrollo, pero no cuando está en modo de producción. Utilice el `bin/magento setup:config:set --enable-debug-logging` para cambiar el valor predeterminado.

>[!INFO]
>
>A partir de Commerce 2.3.1, ya no puede utilizar `bin/magento config:set dev/debug/debug_logging` para habilitar o deshabilitar el registro de depuración para el modo actual.

### Para habilitar el registro de depuración

1. Utilice el `setup:config:set` para habilitar el registro de depuración para el modo actual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

### Para deshabilitar el registro de depuración

1. Utilice el `setup:config:set` para deshabilitar el registro de depuración para el modo actual.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

## Registro de base de datos

De forma predeterminada, Commerce escribe los registros de actividad de la base de datos en `<install-dir>/var/debug/db.log` archivo.

### Para habilitar el registro en base de datos

1. Utilice el `dev:query-log` para habilitar o deshabilitar el registro de la base de datos.

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

Con el lanzamiento de la versión 2.3.1 de, Commerce ahora crea un `cron` registro. \
Commerce recientemente hizo que el registro de cron sea más detallado, lo que proporcionó más información pero prolongó la `system.log` considerablemente.
Móvil `cron` La información de un registro dedicado facilita la lectura de ambos registros.

De forma predeterminada, Commerce escribe `cron` información para el `<install-directory>/var/log/cron.log` archivo.

## Registro de Syslog

De forma predeterminada, Commerce escribe _syslog_ registra en el sistema operativo `syslog` archivo.
A partir de Commerce 2.3.1, debe utilizar el `magento` para habilitar o deshabilitar el registro del sistema.
Se ha eliminado la configuración del Administrador.

### Para habilitar el registro syslog

Iniciando sesión en `syslog` está desactivado de forma predeterminada.

1. Utilice el `setup:config:set` para cambiar el `dev/syslog/syslog_logging` valor de base de datos a `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```

### Para deshabilitar el registro de syslog

1. Utilice el `setup:config:set` para cambiar el `dev/syslog/syslog_logging` valor de base de datos a `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Vaciar la caché.

   ```bash
   bin/magento cache:flush
   ```
