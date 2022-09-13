---
title: Software opcional
description: Obtenga más información sobre el software opcional que puede instalar para admitir las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 0%

---


# Software opcional

Le recomendamos encarecidamente que instale NTP para asegurarse de que las tareas relacionadas con cron funcionan correctamente. (Las fechas del servidor podrían ser, por ejemplo, pasadas o futuras).

Las otras utilidades opcionales que se tratan en este tema pueden ayudarle con la instalación; sin embargo, no es necesario que instalen o utilicen Adobe Commerce o Magento Open Source.

## Instalación y configuración del Protocolo de tiempo de red (NTP)

[NTP](https://www.ntp.org/) permite a los servidores sincronizar sus relojes del sistema mediante [servidores de grupos disponibles globalmente](https://www.ntppool.org/en/). Le recomendamos que utilice servidores NTP en los que confía, ya sean soluciones de hardware dedicadas para su red interna o servidores públicos externos.

Si está implementando Adobe Commerce o Magento Open Source en varios hosts, NTP es una forma sencilla de garantizar que todos los relojes se sincronicen, independientemente de la zona horaria en la que se encuentren los servidores. Además, las tareas relacionadas con cron (como la indexación y los correos electrónicos transaccionales) dependen de que el reloj del servidor sea preciso.

### Instalar y configurar NTP en Ubuntu

Introduzca el siguiente comando para instalar NTP:

```bash
apt-get install ntp
```

Continuar con [Usar servidores de pool NTP](#use-ntp-pool-servers).

### Instalación y configuración de NTP en CentOS

Para instalar y configurar NTP:

1. Introduzca el siguiente comando para encontrar el software NTP adecuado:

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

### Usar servidores de pool NTP

La selección de los servidores del grupo depende de usted. Si utiliza servidores de grupos NTP, ntp.org recomienda usar [servidores de grupos](https://www.ntppool.org/en/) que están cerca de la zona horaria de sus servidores, tal como se describe en la sección [Página de proyecto del pool NTP](https://www.ntppool.org/en/use.html). Si tiene un servidor NTP privado disponible para todos los hosts de la implementación, puede usar ese servidor en su lugar.

1. Apertura `/etc/ntp.conf` en un editor de texto.

1. Busque líneas similares a las siguientes:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Reemplace esas líneas o agregue líneas adicionales que especifiquen su servidor de pool NTP u otros servidores NTP. Es una buena idea especificar más de uno.

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

1. Entrar `date` para comprobar la fecha del servidor.

   Si la fecha es incorrecta, asegúrese de que el puerto cliente NTP (normalmente, UDP 123) esté abierto en el cortafuegos.

   Pruebe la `ntpdate _[pool server hostname]_` comando. Si falla, busque el error que devuelve.

   Si todo lo demás falla, intente reiniciar el servidor.

## Crear phpinfo.php

La variable [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) muestra una gran cantidad de información acerca de [PHP](https://glossary.magento.com/php) y sus extensiones.

>[!NOTE]
>
>Uso `phpinfo.php` en un sistema de desarrollo _only_. Puede tratarse de un problema de seguridad en la producción.

Agregue el siguiente código en cualquier lugar del docroot de su servidor web:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Para obtener más información, consulte la [página manual de phpinfo](https://www.php.net/manual/en/function.phpinfo.php).

Para ver los resultados, escriba lo siguiente [URL](https://glossary.magento.com/url) en el campo de ubicación o dirección del explorador:

```http
http://<web server host or IP>/phpinfo.php
```

Si aparece un error 404 (No encontrado), compruebe lo siguiente:

* Inicie el servidor web si es necesario.
* Asegúrese de que el cortafuegos permita el tráfico en el puerto 80.

   [Ayuda para Ubuntu](https://help.ubuntu.com/community/UFW)

   [Ayuda para CentOS](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

La aplicación phpMyAdmin es una utilidad de administración de bases de datos gratuita y fácil de usar. Puede utilizarla para comprobar y manipular el contenido de la base de datos. Debe iniciar sesión en phpMyAdmin como usuario administrativo de la base de datos MySQL.

Para obtener más información sobre phpMyAdmin, consulte la [página de inicio de phpMyAdmin](https://www.phpmyadmin.net/).

Para obtener información más detallada sobre la instalación, consulte la [documentación de instalación de phpMyAdmin](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Utilizar phpMyAdmin en un sistema de desarrollo _only_. Puede tratarse de un problema de seguridad en la producción.

1. Para usar phpMyAdmin, introduzca el siguiente comando en el campo de dirección o ubicación de su navegador:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Cuando se le solicite, inicie sesión con su base de datos MySQL `root` o nombre de usuario y contraseña del usuario administrativo.
