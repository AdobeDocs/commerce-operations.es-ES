---
title: Auditar el rendimiento de front-end
description: Identificar y abordar los problemas que afectan negativamente al rendimiento del sitio mediante herramientas de rendimiento web para auditar las operaciones de tienda de Adobe Commerce.
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%
---
# Prácticas recomendadas para el rendimiento de front-end

Utilice las herramientas de rendimiento web para comprobar el rendimiento de front-end de sus tiendas Adobe Commerce.
Estas herramientas utilizan varias métricas para proporcionar información y recomendaciones útiles para mejorar el rendimiento de su tienda en línea.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Comprobar rendimiento de front-end

Para comprobar el rendimiento de front-end de la tienda del sitio web:

1. Auditar el rendimiento del front-end mediante herramientas de rendimiento web como:

   - **[Google Lighthouse](https://web.dev/measure/)**: Lighthouse tiene auditorías de rendimiento, accesibilidad, aplicaciones web progresivas, SEO y más. Para obtener más información sobre las distintas formas de ejecutar Lighthouse, consulte la [Descripción general del Lighthouse](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)**—PageSpeed Insights entrega rápidamente un informe detallado sobre las causas del rendimiento lento de la página web junto con recomendaciones sobre cómo solucionarlo.

1. Revise los informes de auditoría e implemente las recomendaciones proporcionadas para mejorar el rendimiento del almacén.

## Más información

- [Administración de índices para usuarios administradores](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Administración de índices mediante CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Información general de indización para desarrolladores](https://developer.adobe.com/commerce/php/development/components/indexing/)
