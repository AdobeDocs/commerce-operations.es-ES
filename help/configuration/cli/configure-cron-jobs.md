---
title: Configurar y ejecutar trabajos cron
description: Aprenda a administrar los trabajos de cron.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '748'
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
- Todos los correos electrónicos de Commerce (incluida la confirmación del pedido y los mensajes transaccionales)

>[!WARNING]
>
>Ya no puede ejecutar `dev/tools/cron.sh` porque se ha quitado el script.

>[!INFO]
>
>Commerce depende de la configuración adecuada del trabajo cron para muchas funciones importantes del sistema, incluida la indexación. Si no se configura correctamente, Commerce no funcionará como se espera.

Los sistemas UNIX programan tareas que deben realizar determinados usuarios mediante _crontab_, que es un archivo que contiene instrucciones para el daemon cron que indican al daemon en vigor que &quot;ejecute este comando en este momento en esta fecha&quot;. Cada usuario tiene su propio crontab, y los comandos de cualquier crontab dado se ejecutan como el usuario propietario.

Para ejecutar cron en un navegador web, consulta [Secure cron.php para ejecutar en un navegador](../security/secure-cron-php.md).

## Crear o quitar el crontab de Commerce

En esta sección se explica cómo crear o quitar el crontab de Commerce (es decir, la configuración de los trabajos cron de Commerce).

_crontab_ es la configuración usada para ejecutar trabajos cron.

La aplicación de Commerce utiliza tareas cron que se pueden ejecutar con diferentes configuraciones. La configuración de línea de comandos de PHP controla el trabajo cron general que reindexa los indexadores, genera correos electrónicos, genera el mapa del sitio, etc.

>[!WARNING]
>
>- Para evitar problemas durante la instalación y actualización, recomendamos encarecidamente que aplique la misma configuración de PHP tanto a la configuración de la línea de comandos de PHP como a la configuración del complemento del servidor web de PHP. Para obtener más información, consulte [Configuración de PHP requerida](../../installation/prerequisites/php-settings.md).
>- En un sistema de varios nodos, crontab puede ejecutarse en un solo nodo. Esto solo se aplica si configura más de un nodo web por motivos relacionados con el rendimiento o la escalabilidad.

### Creación del crontab de Commerce

A partir de la versión 2.2, Commerce crea un crontab para usted. Agregamos el crontab de Commerce a cualquier crontab configurado para el propietario del sistema de archivos de Commerce. En otras palabras, si ya ha configurado crontab para otras extensiones o aplicaciones, se le agrega el crontab de Commerce.

El crontab de Commerce está dentro de `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en el crontab.

Para crear el crontab de Commerce:

1. Inicie sesión como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   bin/magento cron:install [--force]
   ```

Use `--force` para reescribir un crontab existente.

>[!INFO]
>
>- `magento cron:install` no vuelve a escribir un crontab existente dentro de `#~ MAGENTO START` y `#~ MAGENTO END` comentarios en su crontab.
>- `magento cron:install --force` no tiene efecto en ningún trabajo cron fuera de los comentarios de Commerce.

Para ver el crontab, introduzca el siguiente comando como propietario del sistema de archivos:

```bash
crontab -l
```

A continuación se muestra un ejemplo:

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>El archivo `update/cron.php` se ha quitado en Commerce 2.4.0; si existe en la instalación, se puede quitar de forma segura.
>
>Cualquier referencia a `update/cron.php` y `bin/magento setup:cron:run` también debe eliminarse de &quot;crontab&quot;

### Eliminar el crontab de Commerce

Solo debe quitar el crontab de Commerce antes de desinstalar la aplicación de Commerce.

Para eliminar el crontab de Commerce:

1. Inicie sesión como o cambie al [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Cambie al directorio de instalación de Commerce.
1. Introduzca el siguiente comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Este comando no tiene efecto en los trabajos cron fuera de los comentarios `#~ MAGENTO START` y `#~ MAGENTO END` de su crontab.

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
>Debe ejecutar cron dos veces: la primera vez para descubrir las tareas que se van a ejecutar y la segunda vez, para ejecutar las tareas por sí mismas. La segunda ejecución de cron debe ocurrir en o después de la hora `scheduled_at` para cada tarea.

## Registro

Toda la información del trabajo `cron` se ha movido de `system.log` a un(a) `cron.log` diferente.
De forma predeterminada, la información de cron se encuentra en `<install_directory>/var/log/cron.log`.
`\Magento\Cron\Observer\ProcessCronQueueObserver::execute` ha registrado todas las excepciones de los trabajos de cron.

Además de iniciar sesión en `cron.log`:

- Los trabajos con errores con `ERROR` y `MISSED` estados se registran en `<install_directory>/var/log/support_report.log`.

- Los trabajos con un estado `ERROR` siempre se registran como `CRITICAL` en `<install_directory>/var/log/exception.log`.

- Los trabajos con un estado `MISSED` se registran como `INFO` en el directorio `<install_directory>/var/log/debug.log` (solo modo de desarrollador).

>[!INFO]
>
>Todos los datos cron también se escriben en la tabla `cron_schedule` de la base de datos de Commerce. La tabla proporciona un historial de los trabajos cron, incluidos los siguientes:
>
>- Código e ID de trabajo
>- Estado
>- Fecha de creación
>- Fecha programada
>- Fecha de ejecución
>- Fecha de finalización
>
>Para ver los registros de la tabla, inicie sesión en la base de datos de Commerce en la línea de comandos y escriba `SELECT * from cron_schedule;`.
