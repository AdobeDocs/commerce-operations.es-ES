---
title: Software opcional
description: Obtenga más información acerca del software opcional que puede instalar para admitir instalaciones locales de Adobe Commerce.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Software opcional

Le recomendamos encarecidamente que instale NTP para garantizar que las tareas relacionadas con cron se realicen correctamente. (Las fechas del servidor pueden ser pasadas o futuras, por ejemplo).

Las otras utilidades opcionales que se tratan en este tema pueden ayudarle con la instalación; sin embargo, no son necesarias para instalar o utilizar Adobe Commerce.

## Instalación y configuración del Protocolo de tiempo de red (NTP)

[NTP](https://www.ntp.org/) permite que los servidores sincronicen sus relojes del sistema usando [servidores de grupo disponibles globalmente](https://www.ntppool.org/en/). Le recomendamos que utilice servidores NTP en los que confíe, ya sean soluciones de hardware dedicadas para su red interna o servidores públicos externos.

Si implementa Adobe Commerce en varios hosts, NTP es una forma sencilla de garantizar que todos sus relojes estén sincronizados, independientemente del huso horario en el que se encuentren los servidores. Además, las tareas relacionadas con cron (como la indexación y los correos electrónicos transaccionales) dependen de que el reloj del servidor sea preciso.

### Instalar y configurar NTP en Ubuntu

Introduzca el siguiente comando para instalar NTP:

```bash
apt-get install ntp
```

Continuar con [Usar servidores de grupo NTP](#use-ntp-pool-servers).

### Instalación y configuración de NTP en CentOS

Para instalar y configurar NTP:

1. Introduzca el siguiente comando para buscar el software NTP adecuado:

   ```bash
   yum search ntp
   ```

1. Seleccione un paquete para instalar. Por ejemplo, `ntp.x86_64`.

1. Instale el paquete.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Introduzca el siguiente comando para que NTP se inicie cuando se inicie el servidor.

   ```bash
   chkconfig ntpd on
   ```

1. Continúe con la siguiente sección.

### Usar servidores de grupo NTP

La selección de los servidores de grupo depende de usted. Si usa servidores de grupo NTP, ntp.org recomienda usar [servidores de grupo](https://www.ntppool.org/en/) que estén cerca de la zona horaria de los servidores, tal como se describe en la [página del proyecto de grupo NTP](https://www.ntppool.org/en/use.html). Si tiene un servidor NTP privado disponible para todos los hosts de la implementación, puede utilizar ese servidor en su lugar.

1. Abra `/etc/ntp.conf` en un editor de texto.

1. Busque líneas similares a las siguientes:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Reemplace esas líneas o agregue líneas adicionales que especifiquen el servidor de grupo NTP u otros servidores NTP. Es aconsejable especificar más de uno.

1. A continuación se muestra un ejemplo del uso de tres servidores NTP basados en Estados Unidos:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Guarde los cambios en `/etc/ntp.conf` y salga del editor de texto.

1. Reinicie el servicio.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Escriba `date` para comprobar la fecha del servidor.

   Si la fecha es incorrecta, asegúrese de que el puerto cliente NTP (normalmente UDP 123) esté abierto en el cortafuegos.

   Pruebe el comando `ntpdate _[pool server hostname]_`. Si falla, busque el error que devuelve.

   Si todo lo demás falla, intente reiniciar el servidor.

## Crear phpinfo.php

El archivo [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) muestra una gran cantidad de información acerca de PHP y sus extensiones.

>[!NOTE]
>
>Usar `phpinfo.php` en un sistema de desarrollo _solamente_. Puede ser un problema de seguridad en producción.

Agregue el siguiente código en cualquier parte del docroot del servidor web:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Para obtener más información, consulte la [página del manual phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Para ver los resultados, introduzca la siguiente URL en el campo de ubicación o dirección del explorador:

```http
http://<web server host or IP>/phpinfo.php
```

Si aparece un error 404 (no encontrado), compruebe lo siguiente:

* Inicie el servidor web si es necesario.
* Asegúrese de que el cortafuegos permite el tráfico en el puerto 80.

  [Ayuda para Ubuntu](https://help.ubuntu.com/community/UFW)

  [Ayuda para CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

La aplicación phpMyAdmin es una utilidad de administración de bases de datos gratuita y fácil de usar. Puede utilizarla para comprobar y manipular el contenido de la base de datos. Debe iniciar sesión en phpMyAdmin como usuario administrativo de la base de datos MySQL.

Para obtener más información sobre phpMyAdmin, consulte la [página principal de phpMyAdmin](https://www.phpmyadmin.net/).

Para obtener información más detallada sobre la instalación, consulte la [documentación de instalación de phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Use phpMyAdmin en un sistema de desarrollo _solamente_. Puede ser un problema de seguridad en producción.

1. Para usar phpMyAdmin, introduzca el siguiente comando en el campo de dirección o ubicación de su navegador:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Cuando se le solicite, inicie sesión usando su base de datos MySQL `root` o el nombre de usuario y contraseña del usuario administrativo.
