---
title: Programación de actualizaciones de administración en sitios de producción
description: Conozca las prácticas recomendadas para programar actualizaciones críticas en Adobe Commerce a fin de evitar interrupciones y un rendimiento lento.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%
---
# Prácticas recomendadas para programar actualizaciones de administración en sitios de producción

Programe actualizaciones y operaciones críticas en los sitios de Adobe Commerce durante las horas de menor actividad para evitar interrupciones y rendimiento lentos en los sitios de producción.

Ejemplos de acciones críticas:

- Cambios en la configuración de administración, como actualizar un atributo de producto o mover una subcategoría de producto a otra categoría
- Operaciones de importación o exportación de datos

Las acciones críticas producen operaciones de invalidación y reindexación de la caché que aumentan significativamente el tiempo de respuesta, lo que puede provocar interrupciones en el sitio.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Más información

- [Prácticas recomendadas para el almacenamiento en caché](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Contenido privado: invalidar contenido privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [Recomendaciones de hardware: cachés](../../../performance/hardware.md#caches)
- [Configuración avanzada: Configurar Redis](../../../performance/advanced-setup.md#set-up-redis)
