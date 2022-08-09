---
title: Tipos de caché
description: Asocie frontends de caché con tipos de caché.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Tipos de caché

Los siguientes pasos explican cómo asociar el front-end de caché con un tipo de caché.

## Paso 1: Definición de un front-end de caché

La aplicación Commerce tiene un `default` front-end de caché que puede usar para cualquier [tipo de caché](../cli/manage-cache.md#clean-and-flush-cache-types). En esta sección se explica cómo definir opcionalmente un front-end de caché con un nombre diferente, lo cual es preferible si se espera personalizar el front-end.

>[!INFO]
>
>Para usar la variable `default` tipo de caché, no es necesario modificar `env.php` en absoluto; modifica la variable global de Commerce `di.xml`. Consulte [Opciones de caché de bajo nivel](cache-options.md).

Debe especificar un front-end de caché personalizado: `app/etc/env.php` o la `app/etc/di.xml`.

El siguiente ejemplo muestra cómo definirlo en la variable `env.php` que anula la función `di.xml` archivo:

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

Donde `<unique frontend id>` es un nombre único para identificar su front-end y `<cache options>` se tratan las opciones en los temas específicos de cada tipo de almacenamiento en caché (base de datos, Redis, etc.).

## Paso 2: Configuración de la caché

Puede especificar las opciones de configuración de la caché de front-end y de backend en `env.php` o `di.xml`. Esta tarea es opcional.

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

- `<frontend_option>`, `<frontend_option_value>` son el nombre y el valor de las opciones que el marco de comercio pasa como matriz asociativa a la caché de front-end al crearse.
- `<backend_type>` es el tipo de caché back-end de bajo nivel. Especifique el nombre de una clase compatible con `Zend_Cache_Backend` y que implementen `Zend_Cache_Backend_Interface`.
- `<backend_option>` y `<backend_option_value>` son el nombre y el valor de las opciones que el marco de comercio pasa como una matriz asociativa a la caché back-end al crearse.

Consulte la [Documentación de Laminas](https://docs.laminas.dev/) para obtener la información más reciente sobre Zend.
