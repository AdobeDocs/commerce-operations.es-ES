---
title: Configurar tipos y frontend de caché
description: Obtenga información sobre cómo definir front-end de caché y asociarlos a tipos de caché en Adobe Commerce. Descubre la sintaxis de configuración para env.php.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
product_v2: id: cdf0c6dd-1717-4e20-9530-a24eee57088bid: eadea719-cf89-469b-a6fd-a236a7138047id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2: id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 3652976a8db3d0bb19ff9cd06adb3a7736c89539
workflow-type: tm+mt
source-wordcount: 398
ht-degree: 0%

---

# Configurar tipos y front-end de caché

Un front-end de caché conecta los tipos de caché de Commerce con el almacenamiento de caché. Puede definir varios front-end y asignar tipos de caché específicos a cada front-end.

>[!BEGINSHADEBOX]

Utilice la siguiente relación para determinar dónde almacena sus datos un tipo de caché:

tipo de caché → caché front-end → back-end de caché

>[!ENDSHADEBOX]

Para obtener una descripción general de la arquitectura de almacenamiento en caché de Commerce, consulte [Información general de almacenamiento en caché y opciones de configuración](caching-overview.md).

>[!NOTE]
>
>Para Adobe Commerce en la infraestructura en la nube, use la [configuración de implementación en la nube](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/configure-env-yaml) que se describe en la guía de Cloud. No edite `app/etc/env.php` directamente. Las herramientas de implementación generan este archivo y pueden sobrescribir los cambios manuales.

## Usar el front-end predeterminado

Commerce proporciona un front-end predeterminado que pueden utilizar todos los tipos de caché.

En la mayoría de los casos, no es necesario definir un front-end personalizado. Si todos los tipos de caché pueden utilizar las mismas opciones de back-end y back-end, utilice el front-end predeterminado y configure su back-end. Consulte [Opciones de servidor de caché](cache-options.md) para obtener la configuración específica de servidor.

Para las versiones de Adobe Commerce anteriores a la 2.4.9, el front-end predeterminado utiliza la implementación de caché basada en Zend heredada. El front-end `Magento\Framework\Cache\Core` extiende `Zend_Cache_Core`. Adobe Commerce 2.4.9 y versiones posteriores utilizan la implementación moderna de Symfony. Consulte [Opciones de servidor de caché](cache-options.md) para obtener instrucciones específicas de la versión.

## Definir un front-end personalizado

Utilice un front-end de caché personalizado cuando uno o más tipos de caché necesiten configuraciones de back-end que difieran de las del front-end predeterminado.

Para implementaciones locales, defina el front-end en `app/etc/env.php`. A continuación, asígnele uno o varios tipos de caché:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<frontend-id>' => [
            'backend' => '<backend-type>',
            'backend_options' => [
                // Backend-specific options
            ],
        ],
    ],
    'type' => [
        '<cache-type-id>' => [
            'frontend' => '<frontend-id>',
        ],
    ],
],
```

Donde:

- `<frontend-id>` es el identificador único del front-end, como `default` o `page_cache`.
- `<backend-type>` identifica el servidor usado por el front-end. El valor admitido depende de la versión de Adobe Commerce y del back-end seleccionado.
- `backend_options` contiene opciones para el backend seleccionado.
- `<cache-type-id>` es un tipo de caché de Commerce, como `config`, `layout`, `block_html` o `full_page`.


Para ver los tipos de servidor, las opciones compatibles y los ejemplos de configuración específicos de la versión, consulte [Opciones de servidor de caché](cache-options.md).

## Asignar un tipo de caché a un front-end

La configuración de `type` asigna un tipo de caché a un front-end:

```php?start_inline=1
'type' => [
    'full_page' => [
        'frontend' => 'page_cache',
    ],
],
```

En este ejemplo, Commerce asigna el tipo de caché `full_page` al front-end `page_cache`. El front-end determina qué configuración back-end almacena ese tipo de caché.

>[!NOTE]
>
>La clave `full_page` representa un tipo de caché de aplicación de Commerce. El almacenamiento en caché de página completa HTTP a través de Varnish o Fastly es una capa de almacenamiento en caché independiente. Consulte [Información general de almacenamiento en caché y opciones de configuración](caching-overview.md).

>[!MORELIKETHIS]
>
>- [Configuración de caché L2 para la optimización del rendimiento](level-two-cache.md)
>- [Administrar la caché](../cli/manage-cache.md)
