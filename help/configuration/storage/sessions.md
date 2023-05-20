---
title: Ubicación de almacenamiento de sesión
description: Descubra dónde se almacenan los archivos de sesión.
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Ubicación de almacenamiento de sesión

En este tema se explica cómo buscar dónde se almacenan los archivos de sesión. El sistema utiliza la siguiente lógica para almacenar los archivos de sesión:

- Si configuró memcached, las sesiones se almacenan en RAM; consulte [Usar memcached para el almacenamiento de sesión](memcached.md).
- Si configuró Redis, las sesiones se almacenan en el servidor Redis; consulte [Usar Redis para el almacenamiento de sesión](../cache/redis-session.md).
- Si utiliza el almacenamiento predeterminado de sesiones basado en archivos, las sesiones se almacenan en las siguientes ubicaciones en el orden mostrado:

   1. Directorio definido en [`env.php`](#example-in-envphp)
   1. Directorio definido en [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directorio

## Ejemplo en `env.php`

Un fragmento de muestra de `<magento_root>/app/etc/env.php` sigue:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

El ejemplo anterior almacena los archivos de sesión en `/var/www/session`

## Ejemplo en `php.ini`

Como usuario con `root` privilegios, abra su `php.ini` y busque el valor de. `session.save_path`. Esto identifica dónde se almacenan las sesiones.

## Administrar tamaño de sesión

Consulte la [Administración de sesiones](https://docs.magento.com/user-guide/stores/security-session-management.html) en el _Guía del usuario_.

## Configuración de recolección de basura

Para limpiar sesiones caducadas, el sistema llama a `gc` (_recolección de basura_) de forma aleatoria de acuerdo con una probabilidad calculada por el `gc_probability / gc_divisor` Directiva. Por ejemplo, si establece estas directivas en `1/100` respectivamente, significa una probabilidad de `1%` (_probabilidad de una llamada de recolección de elementos no utilizados por cada 100 solicitudes_).

El controlador de recolección de elementos no utilizados utiliza `gc_maxlifetime` directiva: el número de segundos después de los cuales las sesiones se ven como _basura_ y potencialmente limpiado.

En algunos sistemas operativos (Debian/Ubuntu), la opción predeterminada `session.gc_probability` la directiva es `0`, que impide que se ejecute el controlador de recolección de elementos no utilizados.

Puede sobrescribir el `session.gc_` directivas del `php.ini` archivo en el `<magento_root>/app/etc/env.php` archivo:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configuración varía en función del tráfico y las necesidades específicas del sitio web del comerciante.
