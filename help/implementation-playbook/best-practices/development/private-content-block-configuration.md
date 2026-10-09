---
title: Prácticas recomendadas para bloques de contenido privado
description: Conozca las prácticas recomendadas para configurar bloques de contenido privado a fin de optimizar el rendimiento de la tienda.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%
---
# Prácticas recomendadas para bloques de contenido privado

Cuando un bloque de contenido privado contiene la variable `_isScopePrivate`, el bloque no se puede almacenar en caché. Como el bloque privado no se almacena en caché, Adobe Commerce debe recuperar los mismos datos para cada solicitud de cliente, lo que aumenta la carga del servidor.

En lugar de usar la variable `_isScopePrivate` para contenido privado, cree un bloque y una plantilla para mostrar datos no relacionados con el usuario. Estos datos se sustituyen por datos específicos del usuario mediante el componente de interfaz de usuario de Adobe Commerce, que gestiona los datos de procesamiento previo de forma más eficaz. Para obtener instrucciones, consulte [Contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content) en _[!DNL Commerce PHP Extensions Guide]_.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Impacto potencial en el rendimiento

Los sitios que tienen bloques de contenido privado que contienen las variables `_isScopePrivate` almacenan en déclencheur las solicitudes de AJAX para recuperar los mismos datos para cada solicitud de cliente. Esto aumenta el tiempo de respuesta y utiliza recursos adicionales que podrían utilizarse para gestionar operaciones de tienda más críticas para el negocio, como el registro de clientes, las actualizaciones del carro de compras, el envío de pedidos y las transacciones de pago.

## Más información

- [Contenido privado](../../../performance/configuration.md#client-side-optimization-settings)
- [Bloques privados y almacenables en caché](https://developer.adobe.com/commerce/php/development/cache/page/private-content#cacheable-and-private-blocks) en _[!DNL Commerce PHP Extensions Guide]_
