---
title: Configurar y ejecutar trabajos cron
description: Aprenda a administrar los trabajos de cron.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# Configuración de trabajos cron

{{file-system-owner}}

Varias funciones de Commerce requieren al menos un trabajo cron, que programa actividades para que se produzcan en el futuro. A continuación se ofrece una lista parcial de estas actividades:

- Reglas de precios de catálogo
- Newsletters
- Generando mapas del sitio de Google
- Alertas/notificaciones para clientes (cambio de precio del producto, producto disponible en stock)
- Reindexación
- Ventas privadas (solo Adobe Commerce)
- Actualización automática de tipos de cambio
- Todos los correos electrónicos comerciales (incluida la confirmación de pedido y los transaccionales)

>[!WARNING]
>
>Ya no puede ejecutar `dev/tools/cron.sh` porque se ha eliminado la secuencia de comandos.

>[!INFO]
>
>Commerce depende de la configuración adecuada del trabajo de cron para muchas funciones importantes del sistema, incluida la indexación. Si no se configura correctamente, Commerce no funcionará como se espera.

Los sistemas UNIX programan tareas que deben realizar determinados usuarios mediante una _crontab_, que es un archivo que contiene instrucciones al daemon cron que le dicen al daemon en efecto que &quot;ejecute este comando en este momento en esta fecha&quot;. Cada usuario tiene su propio crontab, y los comandos de cualquier crontab dado se ejecutan como el usuario propietario.

Para ejecutar cron en un explorador web, consulte [Asegure cron.php para ejecutar en un navegador](../security/secure-cron-php.md).

## Cree o elimine el crontab de Commerce

En esta sección se explica cómo crear o quitar su crontab de Commerce (es decir, la configuración de los trabajos de Commerce cron).

El _crontab_ es la configuración utilizada para ejecutar trabajos cron.

La aplicación Commerce utiliza tareas cron que se pueden ejecutar con diferentes configuraciones. La configuración de línea de comandos de PHP controla el trabajo cron general que reindexa los indexadores, genera correos electrónicos, genera el mapa del sitio, etc.

>[!WARNING]
>
>- Para evitar problemas durante la instalación y actualización, recomendamos encarecidamente que aplique la misma configuración de PHP tanto a la configuración de la línea de comandos de PHP como a la configuración del complemento del servidor web de PHP. Para obtener más información, consulte [Configuración de PHP requerida](../../installation/prerequisites/php-settings.md).
>- En un sistema de varios nodos, crontab puede ejecutarse en un solo nodo. Esto solo se aplica si configura más de un nodo web por motivos relacionados con el rendimiento o la escalabilidad.


### Creación del crontab de Commerce

A partir de la versión 2.2, Commerce crea un crontab para usted. Añadimos el crontab de Commerce a cualquier crontab configurado para el propietario del sistema de archivos de Commerce. En otras palabras, si ya configura crontab para otras extensiones o aplicaciones, le agregamos el crontab de Commerce.

El crontab de Commerce está dentro `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en su crontab.

Para crear el crontab de Commerce:

1. Inicie sesión como, o cambie a, la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   bin/magento cron:install [--force]
   ```

Uso `--force` para reescribir un crontab existente.

>[!INFO]
>
>- `magento cron:install` no reescribe un crontab existente dentro de `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en su crontab.
>- `magento cron:install --force` no tiene ningún efecto en ningún trabajo cron fuera de los comentarios de Commerce.


Para ver el crontab, introduzca el siguiente comando como propietario del sistema de archivos:

```bash
crontab -l
```

A continuación se muestra un ejemplo:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>El `update/cron.php` El archivo de se ha eliminado en Commerce 2.4.0. Si este archivo existe en la instalación, se puede eliminar de forma segura.
>
>Cualquier referencia a `update/cron.php` y `bin/magento setup:cron:run` también debe eliminarse de &quot;crontab&quot;

### Eliminar el crontab de Commerce

Solo debe quitar el crontab de Commerce antes de desinstalar la aplicación Commerce.

Para eliminar el crontab de Commerce:

1. Inicie sesión como o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Este comando no afecta a los trabajos cron fuera de `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en su crontab.

## Ejecute cron desde la línea de comandos

Opciones de comando:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

donde `--group` especifica el grupo cron que se ejecutará (omita esta opción para ejecutar cron para todos los grupos)

Para ejecutar el trabajo cron de indexación, introduzca:

```bash
bin/magento cron:run --group index
```

Para ejecutar el trabajo cron predeterminado, introduzca:

```bash
bin/magento cron:run --group default
```

Para configurar trabajos y grupos cron personalizados, consulte [Configurar trabajos cron personalizados y grupos cron](../cron/custom-cron.md).

>[!INFO]
>
>Debe ejecutar cron dos veces: la primera vez para descubrir las tareas que se van a ejecutar y la segunda vez, para ejecutar las tareas por sí mismas. La segunda ejecución de cron debe ocurrir en o después de la `scheduled_at` hora de cada tarea.

## Registro

Todo `cron` la información de trabajo se ha movido de `system.log` en un `cron.log`.
De forma predeterminada, la información de cron se encuentra en `<install_directory>/var/log/cron.log`.
Todas las excepciones de los trabajos de cron las registra `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Además de iniciar sesión `cron.log`:

- Trabajos con errores con `ERROR` y `MISSED` los estados se registran en `<install_directory>/var/log/support_report.log`.

- Trabajos con un `ERROR` los estados siempre se registran como `CRITICAL` in `<install_directory>/var/log/exception.log`.

- Trabajos con un `MISSED` los estados se registran como `INFO` en el `<install_directory>/var/log/debug.log` (solo modo de desarrollador).

>[!INFO]
>
>Todos los datos de cron también se escriben en `cron_schedule` en la base de datos de Commerce. La tabla proporciona un historial de los trabajos cron, incluidos los siguientes:
>
>- Código e ID de trabajo
>- Estado
>- Fecha de creación
>- Fecha programada
>- Fecha de ejecución
>- Fecha de finalización
>
>Para ver los registros de la tabla, inicie sesión en la base de datos de Commerce en la línea de comandos e introduzca `SELECT * from cron_schedule;`.
