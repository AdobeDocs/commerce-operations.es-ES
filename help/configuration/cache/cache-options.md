---
title: Opciones del servidor de caché y referencia de almacenamiento
description: Obtenga información acerca de las opciones de back-end de caché en Adobe Commerce, incluido el sistema de archivos, Redis, Valkey y el almacenamiento de bases de datos. Descubra las opciones basadas en Zend (RemoteSynchronizedCache) y Symfony Cache.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# Opciones del servidor de caché y referencia de almacenamiento

>[!NOTE]
>
>Esta página documenta la configuración de `app/etc/env.php` local.
>
>Para [!DNL Adobe Commerce on Cloud] proyectos, el paquete `ece-tools` genera la configuración `app/etc/env.php` resultante durante la implementación en función de la configuración de la variable de implementación en `.magento.env.yaml`. No edita el archivo `env.php`.  Vea las [Prácticas recomendadas para la configuración de los servicios Valkey y Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) y [Implementar variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy).

La aplicación de Commerce utiliza un front-end y un back-end de caché de bajo nivel para proporcionar acceso al almacenamiento en caché. Commerce admite varios back-ends y estrategias de almacenamiento en caché, cada uno adaptado a diferentes casos de uso. Esta página describe los backends disponibles y cómo difieren.

>[!NOTE]
>
>[Varnish](config-varnish-install.md) administra el almacenamiento en caché de página completa en el nivel HTTP para implementaciones locales. El [servicio Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) lo administra para implementaciones de nube. Ninguna de las dos soluciones utiliza el backend de caché de nivel bajo.

## Opciones de caché back-end

La siguiente tabla resume las cachés backend disponibles:

| Servidor | Descripción | Guía de configuración |
| ------- | ----------- | ------------------- |
| Sistema de archivos | Predeterminado. Almacena datos de caché en archivos bajo `var/cache/`. No se requiere configuración. | N/D |
| Redis | Almacén de datos en memoria para el almacenamiento en caché de alto rendimiento. | [Usar Redis para la caché predeterminada](redis-pg-cache.md) |
| Valkey | Alternativa de código abierto y compatible con Redis. | [Usar Valkey para la caché predeterminada](valkey-pg-cache.md) |
| Base de datos | Motor de caché personalizado respaldado por una base de datos | [Crear motores de caché personalizados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} (documentación de Adobe Developer) |

>[!IMPORTANT]
>
>La caché de Redis no es compatible con Adobe Commerce 2.4.9 o con versiones de parches posteriores a las 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 y 2.4.8-p4. Si va a actualizar a una de estas versiones, configure Valkey y actualice la configuración de la caché para utilizarlo. Para [!DNL Adobe Commerce on-premises], consulte [configurar Valkey](config-valkey.md).

## Implementaciones back-end de caché y L2 {#implementation-approaches}

Commerce admite back-ends de caché directo y almacenamiento en caché L2. Un servidor directo selecciona el almacenamiento en caché. El almacenamiento en caché L2 agrega una capa de caché local delante del almacenamiento remoto.

### Backends de caché directo

La siguiente tabla resume los valores de configuración del servidor de caché para `<Commerce-install-dir>/app/etc/env.php`. No habilita el almacenamiento en caché L2.

| Versión de Commerce | Servidor | Valor de configuración |
| ---------------- | ------- | -------------------- |
| 2.4.8 y versiones anteriores, si son compatibles | archivo | Predeterminado. No se requiere configuración |
| 2.4.8 y versiones anteriores, si son compatibles | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 y versiones anteriores, si son compatibles | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 y versiones posteriores, además de puertos posteriores compatibles | archivo | `file` |
| 2.4.9 y versiones posteriores, además de puertos posteriores compatibles | Valkey | `valkey` |

Para obtener una compatibilidad exacta a nivel de parche, consulte [Requisitos del sistema](../../installation/system-requirements.md).

>[!TAB Caché basada en Zend (2.4.8 y anteriores)]

#### Ejemplos de back-end

En implementaciones locales, los siguientes ejemplos configuran los backends de caché directo en `<Commerce-install-dir>/app/etc/env.php`. No habilitan el almacenamiento en caché L2. No utilice estos ejemplos para implementaciones de [!DNL Adobe Commerce on Cloud], que utilizan el paquete `ece-tools` para generar la configuración de `app/etc/env.php` resultante durante la implementación.

>[!BEGINTABS]

>[!TAB Redis]

Utilice el nombre de clase completo de Redis solo en versiones donde se admita Redis:

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Valkey]

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

## Almacenamiento en caché L2

El almacenamiento en caché L2 (de dos niveles) agrega una capa de caché local en cada nodo web delante del almacenamiento de caché remoto compartido, lo que reduce el tráfico de red entre Commerce y la caché remota. Para obtener opciones de implementación, compatibilidad con versiones y pasos de configuración, consulte [Configuración de caché L2](level-two-cache.md).

Para proyectos en la nube, configure el almacenamiento en caché L2 mediante las variables de implementación descritas en [Implementar variables](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}.

- [Usar Redis para la caché predeterminada](redis-pg-cache.md)
- [Usar Valkey para la caché predeterminada](valkey-pg-cache.md)
- [Configuración de caché L2](level-two-cache.md)
