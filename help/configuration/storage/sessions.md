---
title: Ubicación de almacenamiento de sesión
description: Obtenga información acerca de las ubicaciones de almacenamiento de sesión y la administración de archivos en Adobe Commerce. Descubra la lógica de almacenamiento y las opciones de configuración.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '279'
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

Consulte [Administración de sesión](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) en la _Guía del usuario_.

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
