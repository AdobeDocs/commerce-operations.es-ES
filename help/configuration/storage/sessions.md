---
title: Ubicación de almacenamiento de sesión
description: Descubra dónde se almacenan los archivos de sesión.
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Ubicación de almacenamiento de sesión

En este tema se explica cómo localizar dónde se almacenan los archivos de sesión. El sistema utiliza la siguiente lógica para almacenar archivos de sesión:

- Si ha configurado las sesiones en caché, las sesiones se almacenan en RAM; see [Uso almacenado en la memoria caché para el almacenamiento de sesión](memcached.md).
- Si ha configurado Redis, las sesiones se almacenan en el servidor de Redis; see [Usar Redis para almacenamiento de sesión](../cache/redis-session.md).
- Si utiliza el almacenamiento de sesión predeterminado basado en archivos, almacenamos las sesiones en las siguientes ubicaciones en el orden que se muestra:

   1. Directorio definido en [`env.php`](#example-in-envphp)
   1. Directorio definido en [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Ejemplo en `env.php`

Un fragmento de ejemplo de `<magento_root>/app/etc/env.php` a continuación:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

El ejemplo anterior almacena archivos de sesión en `/var/www/session`

## Ejemplo en `php.ini`

Como usuario con `root` privilegios, abra su `php.ini` y busque el valor de `session.save_path`. Esto identifica dónde se almacenan las sesiones.

## Administrar tamaño de sesión

Consulte la [Administración de sesiones](https://docs.magento.com/user-guide/stores/security-session-management.html) en el _Guía del usuario_.

## Configuración de colección de residuos

Para limpiar sesiones caducadas, el sistema llama a la función `gc` (_colección de residuos_) de forma aleatoria según una probabilidad calculada por la variable `gc_probability / gc_divisor` directiva. Por ejemplo, si establece estas directivas en `1/100` respectivamente, significa una probabilidad de `1%` (_probabilidad de una llamada de colección de residuos por cada 100 solicitudes_).

El controlador de la colección de residuos utiliza la variable `gc_maxlifetime` directiva: el número de segundos después de los cuales se ven las sesiones como _basura_ y posiblemente limpiado.

En algunos sistemas operativos (Debian/Ubuntu), el valor predeterminado `session.gc_probability` directiva es `0`, que evita que se ejecute el controlador de colección de residuos.

Puede sobrescribir la variable `session.gc_` directivas de `php.ini` en el `<magento_root>/app/etc/env.php` archivo:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configuración varía según el tráfico y las necesidades específicas del sitio web del comerciante.
