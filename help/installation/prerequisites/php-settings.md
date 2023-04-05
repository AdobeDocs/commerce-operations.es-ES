---
title: Configuración de PHP
description: Siga estos pasos para instalar las extensiones de PHP requeridas y configurar los ajustes de PHP necesarios para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---


# Configuración de PHP

En este tema se explica cómo configurar las opciones de PHP requeridas.

>[!NOTE]
>
>Consulte [requisitos del sistema](../system-requirements.md) para versiones compatibles de PHP.

## Verifique que PHP esté instalado

La mayoría de los sabores de Linux tienen PHP instalado de forma predeterminada. En este tema se supone que ya ha instalado PHP. Para verificar si PHP ya está instalado, en la línea de comandos, escriba:

```bash
php -v
```

Si está instalado PHP, aparece un mensaje similar al siguiente:

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce y Magento Open Source 2.4 son compatibles con PHP 7.3, pero probamos con PHP 7.4 y recomendamos usarlos.

Si PHP no está instalado, o se necesita una actualización de versión, instálelo siguiendo las instrucciones para su sabor particular de Linux.
En CentOS, [pueden ser necesarios pasos adicionales](https://wiki.centos.org/HowTos/php7).

## Verificar las extensiones instaladas

Adobe Commerce y Magento Open Source requieren que se instale un conjunto de extensiones.

{{$include /help/_includes/templated/php-extensions.md}}

Para verificar las extensiones instaladas:

1. Enumerar módulos instalados.

   ```bash
   php -m
   ```

1. Compruebe que están instaladas todas las extensiones necesarias.
1. Añada los módulos que faltan utilizando el mismo flujo de trabajo utilizado para instalar PHP. Por ejemplo, si utiliza `yum` para instalar PHP, los módulos PHP 7.4 pueden agregarse con:

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## Comprobar la configuración de PHP

>[!WARNING]
>
>Si está utilizando PHP 7.4.20, establezca `pcre.jit=0` en su `php.ini` archivo. Esto da la vuelta a un PHP [error](https://bugs.php.net/bug.php?id=81101) que impide que CSS se cargue.

- Establezca la zona horaria del sistema para PHP; de lo contrario, es posible que los errores como los siguientes se muestren durante la instalación y las operaciones relacionadas con el tiempo como cron no funcionen:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Establezca el límite de memoria PHP.

   Nuestras recomendaciones detalladas son:

   - Compilación de código o implementación de recursos estáticos, `1G`
   - Depuración, `2G`
   - Pruebas, `~3-4G`

- Aumente los valores para el PHP `realpath_cache_size` y `realpath_cache_ttl` a la configuración recomendada:

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   Estos ajustes permiten que los procesos PHP almacenen en caché las rutas a los archivos en lugar de buscarlas cada vez que se carga una página. Consulte [Ajuste del rendimiento](https://www.php.net/manual/en/ini.core.php) en la documentación de PHP.

- Habilitar [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), que es necesario para Adobe Commerce y Magento Open Source 2.1 y posteriores.

   Le recomendamos que habilite la variable [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) por motivos de rendimiento. El OPcache está habilitado en muchas distribuciones PHP.

   Adobe Commerce y Magento Open Source 2.1 y posteriores utilizan comentarios de código PHP para la generación de código.

>[!NOTE]
>
>Para evitar problemas durante la instalación y actualización, recomendamos encarecidamente que aplique la misma configuración de PHP tanto a la configuración de la línea de comandos de PHP como a la configuración del complemento del servidor web de PHP. Para obtener más información, consulte la siguiente sección.

## Buscar archivos de configuración PHP

En esta sección se explica cómo encontrar los archivos de configuración necesarios para actualizar los ajustes necesarios.

### Buscar `php.ini` archivo de configuración

Para buscar la configuración del servidor web, ejecute un [`phpinfo.php` file](optional-software.md#create-phpinfophp) en el explorador web y busque la variable `Loaded Configuration File` de la siguiente manera:

![Página de información de PHP](../../assets/installation/config_phpini-webserver.png)

Para localizar la configuración de la línea de comandos PHP, introduzca

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Si solo tiene uno `php.ini` , realice los cambios en ese archivo. Si tiene dos `php.ini` archivos, realice los cambios en *all* archivos. Si no lo hace, puede que el rendimiento sea impredecible.

### Buscar los ajustes de configuración de OPcache

La configuración de PHP OPcache generalmente se encuentra en `php.ini` o `opcache.ini`. La ubicación puede depender del sistema operativo y de la versión PHP. El archivo de configuración OPcache puede tener un `opcache` sección o configuración como `opcache.enable`.

Siga las siguientes directrices para encontrarlo:

- Servidor web Apache:

   Para Ubuntu con Apache, la configuración de OPcache generalmente se encuentra en la `php.ini` archivo.

   Para CentOS con Apache o nginx, la configuración de OPcache generalmente se encuentra en `/etc/php.d/opcache.ini`

   Si no es así, utilice el siguiente comando para localizarlo:

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- servidor web nginx con PHP-FPM: `/etc/php/7.2/fpm/php.ini`

Si tiene más de uno `opcache.ini`, modifique todos.

## Cómo configurar las opciones de PHP

Para configurar las opciones de PHP:

1. Abra un `php.ini` en un editor de texto.
1. Localice la zona horaria del servidor en la [configuración de zona horaria](https://www.php.net/manual/en/timezones.php)
1. Busque la siguiente configuración y quite la marca de comentario si es necesario:

   ```conf
   date.timezone =
   ```

1. Agregue la configuración de zona horaria que encontró en el paso 2.

1. Cambiar el valor de `memory_limit` a uno de los valores recomendados al principio de esta sección.

   Por ejemplo,

   ```conf
   memory_limit=2G
   ```

1. Agregue o actualice la variable `realpath_cache` para que coincida con los siguientes valores:

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Guarde los cambios y salga del editor de texto.

1. Abra el otro `php.ini` (si son diferentes) y realice los mismos cambios en él.

## Establecer las opciones de OPcache

Para configurar `opcache.ini` opciones:

1. Abra el archivo de configuración OPcache en un editor de texto:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/7.2/fpm/php.ini` (servidor web nginx (CentOS o Ubuntu))

1. Localizar `opcache.save_comments` y quite la marca de comentario si es necesario.
1. Asegúrese de que su valor esté establecido en `1`.
1. Guarde los cambios y salga del editor de texto.
1. Reinicie el servidor web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu y CentOS: `service nginx restart`

## Resolución de problemas

Consulte los siguientes artículos de soporte de Adobe Commerce para obtener ayuda con la resolución de problemas de PHP:

- [Error de versión PHP o error 404 al acceder a Adobe Commerce en el navegador](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Errores de configuración de PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [La extensión mcrypt de PHP no está instalada correctamente](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemas de comprobación de preparación para versiones PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Errores mortales comunes de PHP y soluciones](https://support.magento.com/hc/en-us/articles/360030568432)
