---
title: Tipos de caché
description: Asociar frontend de caché con tipos de caché.
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Tipos de caché

Los siguientes pasos describen cómo asociar el front-end de caché con un tipo de caché.

## Paso 1: Definir un front-end de caché

La aplicación Commerce tiene un `default` front-end de caché que puede utilizar para cualquier [tipo de caché](../cli/manage-cache.md#clean-and-flush-cache-types). En esta sección se explica cómo definir de forma opcional un front-end de caché con un nombre diferente, lo que es preferible si espera personalizar el front-end.

>[!INFO]
>
>Para usar la variable `default` tipo de caché, no es necesario modificarlo `env.php` en absoluto; se modifica la configuración global de `di.xml`. Consulte [Opciones de caché de nivel bajo](cache-options.md).

Debe especificar un front-end de caché personalizado `app/etc/env.php` o la versión global de Commerce `app/etc/di.xml`.

El siguiente ejemplo muestra cómo definirlo en la variable `env.php` , que anula el `di.xml` archivo:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Donde `<unique frontend id>` es un nombre único para identificar el front-end y `<cache options>` Hay opciones que se tratan en los temas específicos de cada tipo de almacenamiento en caché (base de datos, Redis, etc.).

## Paso 2: Configuración de la caché

Puede especificar las opciones de configuración de caché de front-end y back-end en `env.php` o `di.xml`. Esta tarea es opcional.

`env.php` ejemplo:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

donde

- `<frontend_type>` es el tipo de caché de front-end de bajo nivel. Especifique el nombre de una clase compatible con `Zend\Cache\Core`.
Si omite `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) se utiliza.

- `<frontend_option>`, `<frontend_option_value>` son el nombre y el valor de las opciones que el marco de comercio pasa como una matriz asociativa a la caché de front-end tras su creación.
- `<backend_type>` es el tipo de caché back-end de bajo nivel. Especifique el nombre de una clase compatible con `Zend_Cache_Backend` y que implementa `Zend_Cache_Backend_Interface`.
- `<backend_option>` y `<backend_option_value>` son el nombre y el valor de las opciones que el marco de Commerce pasa como una matriz asociativa a la caché back-end en el momento de su creación.

Consulte la [Documentación de Laminas](https://docs.laminas.dev/) para obtener la información más reciente de Zend.
