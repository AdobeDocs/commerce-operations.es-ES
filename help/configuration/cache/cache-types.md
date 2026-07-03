---
title: Configurar tipos y frontend de caché
description: Obtenga información sobre cómo definir front-end de caché y asociarlos a tipos de caché en Adobe Commerce. Descubra la sintaxis de configuración para env.php y di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2:
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 507
ht-degree: 1%

---

# Configurar tipos y front-end de caché

Un front-end de caché es una interfaz entre los tipos de caché de Commerce y el back-end de almacenamiento de caché. Puede definir varios front-end, cada uno con una configuración de back-end diferente, y luego asignar [tipos de caché](../cli/manage-cache.md#clean-and-flush-cache-types) específicos a cada front-end.

Utilice esta relación para decidir dónde almacena datos cada tipo de caché:

`cache type` -> `cache frontend` -> `cache backend`

Esto resulta útil cuando desea utilizar diferentes backends o configuraciones de caché para diferentes tipos de datos en caché. Por ejemplo, podría asignar el tipo de caché `full_page` a un front-end `page_cache` que use una base de datos de Valkey dedicada, mientras que otros tipos de caché usan el front-end `default`.

{{cloud-cache-config}}

## Usar el front-end predeterminado

Commerce proporciona un front-end de caché `default` que funciona para todos los tipos de caché. Amplía [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) al implementar la caché de front-end [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

En la mayoría de los casos, no es necesario personalizar el front-end. Solo es necesario configurar el servidor. Consulte [Opciones de servidor de caché](cache-options.md).

## Definir un front-end de caché personalizado

A continuación se describen los pasos para asociar un front-end de caché con un tipo de caché.

### Paso 1: Definir un front-end de caché y asignar tipos de caché

Para definir un front-end de caché personalizado, agregue la configuración a `app/etc/env.php` (que invalida `di.xml`):

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
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Donde:

- `<unique frontend id>`: un nombre único para identificar el front-end (por ejemplo, `default`, `page_cache`, `stale_cache_enabled`)
- `<cache options>`: tipo de servidor y opciones para este front-end (consulte [Opciones de caché](cache-options.md))
- `<cache type>`: un tipo de caché de Commerce para asignar a este front-end (por ejemplo, `config`, `layout`, `block_html`, `full_page`)

>[!TIP]
>
>Adobe Commerce 2.4.9 y versiones posteriores utilizan nombres de tipo de back-end simplificados, como `valkey` o `file`, con la implementación de Symfony Cache. Consulte [Opciones de back-end de caché](cache-options.md) para ver ejemplos de back-end e instrucciones específicas de la versión.


### Paso 2: Configurar las opciones de front-end y back-end

Puede especificar opciones de configuración de caché de front-end y back-end en `env.php` o `di.xml`. Esta tarea es opcional. Si no especifica opciones, Commerce utiliza la configuración predeterminada de front-end y back-end.

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

Donde:

- `<frontend_type>`: el tipo de caché de nivel inferior de front-end. Especifique un nombre de clase compatible con `Zend\Cache\Core`.Si se omite, se usa [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

- `<frontend_option>`, `<frontend_option_value>`: el nombre y valor de las opciones que el marco de trabajo de Commerce pasa como una matriz asociativa a la caché de front-end en el momento de la creación.

- `<backend_type>`: el tipo de caché de servidor de nivel bajo. Puede especificar:
   - **Caché Symfony moderna (2.4.9+, recomendada)**: Nombres simplificados como `redis`, `valkey` o `file`
   - **Heredado (basado en Zend)**: Nombre de clase completo compatible con `Zend_Cache_Backend` que implementa `Zend_Cache_Backend_Interface`

- `<backend_option>`, `<backend_option_value>`: nombre y valor de las opciones que el marco de trabajo de Commerce pasa como una matriz asociativa a la caché back-end al crearla.

>[!NOTE]
>
>**Implementación heredada frente a moderna:**
>
>- **Heredado (basado en Zend)**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **Moderno (Symfony Cache)**: `'backend' => 'valkey'` para las versiones de Commerce 2.4.9+ y las revisiones actuales para las líneas de versión 2.4.5 - 2.4.8 donde Valkey es el servidor de caché compatible.
>
>La implementación moderna de Symfony Cache proporciona un mejor rendimiento a través del cumplimiento de PSR-6, serialización Igbinary, compresión gzip, scripts Lua y conexiones persistentes.

Consulte la [documentación de Laminas](https://docs.laminas.dev/) para ver las opciones basadas en Zend. Para obtener información sobre la configuración de la caché de Symfony, consulte los artículos [Redis](redis-pg-cache.md) y [Valkey](valkey-pg-cache.md) de esta documentación.
