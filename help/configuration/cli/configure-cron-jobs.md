---
title: Configuración y ejecución de trabajos cron
description: Aprenda a administrar trabajos cron.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# Configurar trabajos cron

{{file-system-owner}}

Varias funciones de Commerce requieren al menos un trabajo cron, que programa las actividades para que se produzcan en el futuro. A continuación se muestra una lista parcial de estas actividades:

- Reglas de precios del catálogo
- Newsletters
- Generación de mapas del sitio de Google
- Alertas/notificaciones de clientes (cambio en el precio del producto, producto en existencias)
- Reindexación
- Ventas privadas (solo Adobe Commerce)
- Actualización automática de las tasas de cambio
- Todos los correos electrónicos de comercio (incluida la confirmación de pedido y transaccional)

>[!WARNING]
>
>Ya no se puede ejecutar `dev/tools/cron.sh` porque la secuencia de comandos se ha eliminado.

>[!INFO]
>
>El comercio depende de la configuración adecuada del trabajo cron para muchas funciones importantes del sistema, incluida la indexación. Si no se configura correctamente, Commerce no funcionará como se espera.

Los sistemas UNIX programan tareas para que las realicen usuarios particulares mediante un _crontab_, que es un archivo que contiene instrucciones al demonio cron que le indica al demonio en efecto &quot;ejecutar este comando en este momento en esta fecha&quot;. Cada usuario tiene su propio crontab, y los comandos de cualquier crontab dado se ejecutan como el usuario que lo posee.

Para ejecutar cron en un explorador web, consulte [Asegurar cron.php para que se ejecute en un navegador](../security/secure-cron-php.md).

## Crear o quitar la crontab de comercio

En esta sección se explica cómo crear o eliminar su crontab de comercio (es decir, la configuración de los trabajos de Commerce cron).

La variable _crontab_ es la configuración utilizada para ejecutar trabajos cron.

La aplicación Commerce utiliza tareas cron que pueden ejecutarse con diferentes configuraciones. La configuración de la línea de comandos de PHP controla el trabajo cron general que reindexa los indexadores, genera correos electrónicos, genera el mapa del sitio, etc.

>[!WARNING]
>
>- Para evitar problemas durante la instalación y actualización, recomendamos encarecidamente que aplique la misma configuración de PHP tanto a la configuración de la línea de comandos de PHP como a la configuración del complemento del servidor web de PHP. Para obtener más información, consulte [Configuración de PHP requerida](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
>- En un sistema de varios nodos, crontab sólo puede ejecutarse en un nodo. Esto solo se aplica si configura más de un nodo web por motivos relacionados con el rendimiento o la escalabilidad.


### Crear la crontab de comercio

A partir de la versión 2.2, Commerce crea un crontab por usted. Agregamos la crontab de comercio a cualquier crontab configurado para el propietario del sistema de archivos de comercio. En otras palabras, si ya ha configurado crontabs para otras extensiones o aplicaciones, le agregamos la crontab de comercio.

La crontab de comercio está dentro de `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en su crontab.

Para crear la crontab de comercio:

1. Inicie sesión como o cambie a la [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
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


Para ver la crontab, introduzca el siguiente comando como propietario del sistema de archivos:

```bash
crontab -l
```

A continuación se muestra una muestra:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>La variable `update/cron.php` se ha eliminado en Commerce 2.4.0, si este archivo existe en la instalación, se puede eliminar de forma segura.
>
>Cualquier referencia a `update/cron.php` y `bin/magento setup:cron:run` también debe eliminarse de crontab&#39;

### Quitar la crontab de comercio

Debe quitar Commerce crontab solo antes de desinstalar la aplicación Commerce.

Para eliminar Commerce crontab:

1. Inicie sesión como o cambie a la [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Este comando no tiene ningún efecto en los trabajos cron fuera de `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en su crontab.

## Ejecutar cron desde la línea de comandos

Opciones de comando:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

donde `--group` especifica el grupo cron que se va a ejecutar (omita esta opción para ejecutar cron para todos los grupos)

Para ejecutar el trabajo cron de indexación, introduzca:

```bash
bin/magento cron:run --group index
```

Para ejecutar el trabajo cron predeterminado, introduzca:

```bash
bin/magento cron:run --group default
```

Para configurar trabajos y grupos de cron personalizados, consulte [Configuración de trabajos cron personalizados y grupos cron](../cron/custom-cron.md).

>[!INFO]
>
>Debe ejecutar cron dos veces: la primera vez para descubrir tareas que se van a ejecutar y la segunda vez, para ejecutar las tareas por sí mismas. La segunda ejecución de cron debe ocurrir en o después de la `scheduled_at` tiempo para cada tarea.

## Registro

Todo `cron` la información del trabajo se ha movido de `system.log` en una `cron.log`.
De forma predeterminada, la información de cron se encuentra en `<install_directory>/var/log/cron.log`.
Todas las excepciones de trabajos cron se registran mediante `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Además de iniciar sesión `cron.log`:

- Error en los trabajos con `ERROR` y `MISSED` los estados se registran en la variable `<install_directory>/var/log/support_report.log`.

- Trabajos con un `ERROR` el estado siempre se registra como `CRITICAL` en `<install_directory>/var/log/exception.log`.

- Trabajos con un `MISSED` el estado se registra como `INFO` en el `<install_directory>/var/log/debug.log` (solo modo de desarrollador).

>[!INFO]
>
>Todos los datos de cron también se escriben en la variable `cron_schedule` en la base de datos de Commerce. La tabla proporciona un historial de trabajos cron, que incluye:
>
>- ID y código de trabajo
>- Estado
>- Fecha de creación
>- Fecha programada
>- Fecha de ejecución
>- Fecha de finalización
>
>Para ver los registros de la tabla, inicie sesión en la base de datos Commerce en la línea de comandos e introduzca `SELECT * from cron_schedule;`.
