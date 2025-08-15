---
title: Prácticas recomendadas para bloques de contenido privado
description: Conozca las prácticas recomendadas para configurar bloques de contenido privado a fin de optimizar el rendimiento de la tienda.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---

# Prácticas recomendadas para bloques de contenido privado

Cuando un bloque de contenido privado contiene la variable `_isScopePrivate`, el bloque no se puede almacenar en caché. Como el bloque privado no se almacena en caché, Adobe Commerce debe recuperar los mismos datos para cada solicitud de cliente, lo que aumenta la carga del servidor.

En lugar de usar la variable `_isScopePrivate` para contenido privado, cree un bloque y una plantilla para mostrar datos no relacionados con el usuario. Estos datos se sustituyen por datos específicos del usuario mediante el componente de interfaz de usuario de Adobe Commerce, que gestiona los datos de procesamiento previo de forma más eficaz. Para obtener instrucciones, consulte [Contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) en _[!DNL Commerce PHP Extensions Guide]_.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Impacto potencial en el rendimiento

Los sitios que tienen bloques de contenido privado que contienen las variables `_isScopePrivate` almacenan en déclencheur las solicitudes de AJAX para recuperar los mismos datos para cada solicitud de cliente. Esto aumenta el tiempo de respuesta y utiliza recursos adicionales que podrían utilizarse para gestionar operaciones de tienda más críticas para el negocio, como el registro de clientes, las actualizaciones del carro de compras, el envío de pedidos y las transacciones de pago.

## Más información

- [Contenido privado](../../../performance/configuration.md#client-side-optimization-settings)
- [Las solicitudes de AJAX de alto rendimiento causan bajo rendimiento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html?lang=es)
