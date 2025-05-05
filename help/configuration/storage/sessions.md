---
title: Ubicación de almacenamiento de sesión
description: Descubra dónde se almacenan los archivos de sesión.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Ubicación de almacenamiento de sesión

En este tema se explica cómo buscar dónde se almacenan los archivos de sesión. El sistema utiliza la siguiente lógica para almacenar los archivos de sesión:

- Si configuró memcached, las sesiones se almacenan en RAM; consulte [Usar memcached para almacenar sesiones](memcached.md).
- Si configuró Redis, las sesiones se almacenan en el servidor Redis; consulte [Usar Redis para el almacenamiento de sesiones](../cache/redis-session.md).
- Si utiliza el almacenamiento predeterminado de sesiones basado en archivos, las sesiones se almacenan en las siguientes ubicaciones en el orden mostrado:

   1. Directorio definido en [`env.php`](#example-in-envphp)
   1. Directorio definido en [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directorio

## Ejemplo en `env.php`

A continuación se muestra un fragmento de ejemplo de `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

El ejemplo anterior almacena los archivos de sesión en `/var/www/session`

## Ejemplo en `php.ini`

Como usuario con privilegios de `root`, abra el archivo `php.ini` y busque el valor de `session.save_path`. Esto identifica dónde se almacenan las sesiones.

## Administrar tamaño de sesión

Consulte [Administración de sesión](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/security-session-management) en la _Guía del usuario_.

## Configuración de recolección de basura

Para limpiar sesiones caducadas, el sistema llama al controlador `gc` (_recolección de elementos no utilizados_) de forma aleatoria según una probabilidad calculada por la directiva `gc_probability / gc_divisor`. Por ejemplo, si establece estas directivas en `1/100` respectivamente, significa una probabilidad de `1%` (_probabilidad de una llamada de recolección de basura por cada 100 solicitudes_).

El controlador de recolección de elementos no utilizados usa la directiva `gc_maxlifetime`, es decir, el número de segundos después de los cuales las sesiones se ven como _elementos no utilizados_ y se pueden limpiar.

En algunos sistemas operativos (Debian/Ubuntu), la directiva predeterminada `session.gc_probability` es `0`, lo que impide que se ejecute el controlador de recolección de elementos no utilizados.

Puede sobrescribir las directivas `session.gc_` del archivo `php.ini` en el archivo `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configuración varía en función del tráfico y las necesidades específicas del sitio web del comerciante.
