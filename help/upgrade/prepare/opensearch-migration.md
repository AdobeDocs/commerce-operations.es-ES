---
title: Migrar de Elasticsearch a OpenSearch
description: Obtenga información acerca de cómo reemplazar el motor de búsqueda utilizado para las instalaciones locales de Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%
---
# Migración a OpenSearch

OpenSearch es una ramificación de código abierto de Elasticsearch 7.10.2 que se creó después del cambio de licencia de Elasticsearch.

Desde las versiones 2.4.4, 2.4.3-p2 y 2.3.7-p3, Adobe Commerce admite OpenSearch. Las instalaciones locales siguen siendo compatibles con Elasticsearch, aunque ya no lo es con Adobe Commerce en la infraestructura en la nube. A partir de la versión 2.4.6, OpenSearch tiene su propio módulo y campos en los ajustes de configuración de la administración.

## Ruta de migración

Los pasos para migrar a OpenSearch son sencillos y siguen en gran medida los pasos de la configuración de Elasticsearch. En estos pasos se da por hecho que Adobe Commerce es la única aplicación que utiliza el motor de búsqueda. En los casos en que varias aplicaciones usen el motor de búsqueda, siga la guía de migración oficial [Cambio de Elasticsearch de código abierto a OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Asegúrese de que la instalación cumpla los [requisitos previos del motor de búsqueda](../../installation/prerequisites/search-engine/overview.md).

1. Coloque el sitio en [Modo de mantenimiento](../../installation/tutorials/maintenance-mode.md).

1. Si lo desea, desinstale Elasticsearch.

1. [Instalar OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configure el motor de búsqueda](../../configuration/search/configure-search-engine.md) y realice tareas relacionadas, como vaciar la caché y reindexar el índice de búsqueda del catálogo.

No es necesario realizar más cambios en el valor de configuración.
