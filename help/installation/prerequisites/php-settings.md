---
title: Configuración de PHP
description: Siga estos pasos para instalar las extensiones de PHP requeridas y configurar los ajustes de PHP necesarios para las instalaciones locales de Adobe Commerce.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# Configuración de PHP

En este tema se explica cómo configurar las opciones de PHP requeridas.

>[!NOTE]
>
>La última versión de Adobe Commerce requiere un mínimo de PHP 8.1. Consulte [requisitos del sistema](../system-requirements.md) para todas las versiones compatibles de PHP.

Para obtener instrucciones de configuración de Cloud, consulte [Configuración de PHP](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=es) en la guía de _Commerce en infraestructura en la nube_.

## Control de procesos PHP

{{php-process-control}}

## Verificar que PHP esté instalado

PHP se instala por defecto en la mayoría de las distribuciones Linux. En este tema se da por hecho que ya ha instalado PHP. Para verificar si PHP está instalado, introduzca lo siguiente en la línea de comandos:

```bash
php -v
```

Si PHP está instalado, aparece un mensaje similar al siguiente:

```
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Si PHP no está instalado (o requiere una actualización), instálelo siguiendo las instrucciones para su distribución Linux.

## Verificar las extensiones instaladas

Adobe Commerce requiere ciertas extensiones PHP. Las siguientes listas especifican las extensiones necesarias para cada edición de Commerce. Las listas se generan automáticamente a partir de una implementación que ejecuta la última versión de cada edición.

{{$include /help/_includes/templated/php-extensions.md}}

Para comprobar las extensiones instaladas:

1. Enumerar los módulos instalados.

   ```bash
   php -m
   ```

1. Compruebe que todas las extensiones requeridas están instaladas.
1. Añada los módulos que falten utilizando el mismo flujo de trabajo utilizado para instalar PHP.

## Comprobar la configuración de PHP

>[!WARNING]
>
>Si usa PHP 7.4.20, establezca `pcre.jit=0` en el archivo `php.ini`. Esto evita un [error](https://bugs.php.net/bug.php?id=81101) de PHP que impide que CSS se cargue.

- Configure la zona horaria del sistema para PHP; de lo contrario, es posible que errores como la siguiente visualización durante la instalación y operaciones relacionadas con la hora como cron no funcionen:

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Establezca el límite de memoria PHP.

  El Adobe recomienda lo siguiente:

   - Compilando código o implementando recursos estáticos, `1G`
   - Depurando, `2G`
   - Probando, `~3-4G`

- Aumente los valores de PHP `realpath_cache_size` y `realpath_cache_ttl` a la configuración recomendada:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Estos ajustes permiten a los procesos de PHP almacenar en caché las rutas a los archivos en lugar de buscarlos durante la carga de la página. Consulte [Ajuste del rendimiento](https://www.php.net/manual/en/ini.core.php) en la documentación de PHP.

- Habilite [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), que es necesario para Adobe Commerce 2.1 y versiones posteriores.

  El Adobe recomienda habilitar [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) por motivos de rendimiento. OPcache está habilitado en muchas distribuciones PHP.

  Adobe Commerce 2.1 y versiones posteriores utilizan comentarios de código PHP para la generación de código.

>[!NOTE]
>
>Para evitar problemas durante la instalación y actualización, Adobe recomienda encarecidamente que aplique la misma configuración de PHP tanto a la configuración de la línea de comandos de PHP como a la configuración del complemento del servidor web de PHP. Para obtener más información, consulte la siguiente sección.

## Buscar archivos de configuración de PHP

En esta sección se explica cómo encontrar los archivos de configuración necesarios para actualizar la configuración necesaria.

### Buscar archivo de configuración de `php.ini`

Para encontrar la configuración del servidor web, ejecute un archivo [`phpinfo.php`](optional-software.md#create-phpinfophp) en el explorador web y busque `Loaded Configuration File` de la siguiente manera:

![Página de información de PHP](../../assets/installation/config_phpini-webserver.png)

Para localizar la configuración de la línea de comandos de PHP, introduzca

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Si solo tiene un archivo de `php.ini`, cámbielo. Si tiene dos archivos de `php.ini`, cambie *ambos* archivos. Si no se hace esto, el rendimiento puede ser impredecible.

### Buscar opciones de configuración de OPcache

La configuración de OPcache de PHP se encuentra generalmente en `php.ini` o `opcache.ini`. La ubicación puede depender de su sistema operativo y versión de PHP. El archivo de configuración de OPcache puede tener una sección `opcache` o valores como `opcache.enable`.

Siga estas directrices para encontrarlo:

- Servidor web Apache:

  Para Ubuntu con Apache, la configuración de OPcache generalmente se encuentra en el archivo `php.ini`.

  Para CentOS con Apache o nginx, la configuración de OPcache generalmente se encuentra en `/etc/php.d/opcache.ini`

  Si no es así, utilice el siguiente comando para localizarlo:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- Servidor web nginx con PHP-FPM: `/etc/php/8.1/fpm/php.ini`

Si tiene más de un(a) `opcache.ini`, modifíquelos(as) todos(as).

## Cómo configurar las opciones de PHP

Para configurar las opciones de PHP:

1. Abra un(a) `php.ini` en un editor de texto.
1. Busque la zona horaria del servidor en la [configuración de zona horaria disponible](https://www.php.net/manual/en/timezones.php)
1. Busque la siguiente configuración y quite los comentarios si es necesario:

   ```conf
   date.timezone =
   ```

1. Añada la configuración de zona horaria que encontró en el paso 2.

1. Cambie el valor de `memory_limit` por uno de los valores recomendados al principio de esta sección.

   Por ejemplo,

   ```conf
   memory_limit=2G
   ```

1. Agregue o actualice la configuración de `realpath_cache` para que coincida con los siguientes valores:

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

1. Abra los otros `php.ini` (si son diferentes) y realice los mismos cambios en ellos.

## Definir opciones de OPcache

Para establecer las opciones de `opcache.ini`:

1. Abra el archivo de configuración de OPcache en un editor de texto:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (servidor web nginx (CentOS o Ubuntu))

1. Busque `opcache.save_comments` y quite los comentarios si es necesario.
1. Asegúrese de que su valor esté establecido en `1`.
1. Guarde los cambios y salga del editor de texto.
1. Reinicie el servidor web:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu y CentOS: `service nginx restart`

## Resolución de problemas

Consulte los siguientes artículos de soporte de Adobe Commerce para obtener ayuda con la resolución de problemas de PHP:

- [Error de versión de PHP o error 404 al acceder a Adobe Commerce en un explorador](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Errores de configuración de PHP](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [La extensión mcrypt de PHP no se instaló correctamente](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemas de comprobación de preparación de la versión de PHP](https://support.magento.com/hc/en-us/articles/360033546411)
- [Errores y soluciones comunes de PHP](https://support.magento.com/hc/en-us/articles/360030568432)
