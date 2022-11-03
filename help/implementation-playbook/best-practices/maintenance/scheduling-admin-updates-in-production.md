---
title: Programación de actualizaciones de administración en sitios de producción
description: Conozca las prácticas recomendadas para programar actualizaciones críticas para Adobe Commerce para evitar interrupciones y un rendimiento lento.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# Prácticas recomendadas para programar actualizaciones de administración en sitios de producción

Programe actualizaciones y operaciones críticas en sus sitios de Adobe Commerce durante las horas de menor actividad para evitar interrupciones y un rendimiento lento en los sitios de producción.

Ejemplos de acciones críticas:

- Cambios en la configuración de administración, por ejemplo, actualizar un atributo de producto o mover una subcategoría de producto a otra categoría
- Operaciones de importación o exportación de datos

Las acciones críticas llevan a operaciones de invalidación y reindexación de caché que aumentan significativamente el tiempo de respuesta y pueden causar interrupciones en el sitio.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Información adicional

- [Prácticas recomendadas para el almacenamiento en caché](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Contenido privado: Invalidar contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Recomendaciones de hardware: Cachés](../../../performance/hardware.md#caches)
- [Configuración avanzada: Configuración de Redis](../../../performance/advanced-setup.md#set-up-redis)

