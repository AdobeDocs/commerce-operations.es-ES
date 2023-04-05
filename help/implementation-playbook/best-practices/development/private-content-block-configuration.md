---
title: Prácticas recomendadas para bloques de contenido privado
description: Conozca las prácticas recomendadas para configurar bloques de contenido privado con el fin de optimizar el rendimiento de la tienda.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Prácticas recomendadas para bloques de contenido privado

Cuando un bloque de contenido privado contiene la variable `_isScopePrivate` , el bloque no se puede almacenar en caché. Dado que el bloque privado no se almacena en caché, Adobe Commerce debe recuperar los mismos datos para cada solicitud del cliente, lo que aumenta la carga del servidor.

En lugar de usar la variable `_isScopePrivate` para contenido privado, cree un bloque y una plantilla para mostrar los datos no deseados por el usuario. Estos datos se reemplazan con datos específicos del usuario mediante el componente de interfaz de usuario de Adobe Commerce, que gestiona los datos de procesamiento previo de forma más eficaz. Para obtener instrucciones, consulte [Contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) en el _[!DNL Commerce PHP Extensions Guide]_.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Posible impacto en el rendimiento

Sitios que tienen bloques de contenido privado que contienen la variable `_isScopePrivate` déclencheur de variables AJAX solicitudes para recuperar los mismos datos para cada solicitud del cliente. Esto aumenta el tiempo de respuesta y utiliza recursos adicionales que podrían utilizarse para gestionar operaciones de tienda más críticas para el negocio, como el registro de clientes, las actualizaciones del carro de compras, el envío de pedidos y las transacciones de pago.

## Información adicional

- [Contenido privado](../../../performance/configuration.md#client-side-optimization-settings)
- [Las solicitudes de AJAX de alto rendimiento causan un rendimiento deficiente](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)


