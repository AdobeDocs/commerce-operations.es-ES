---
title: Migrar de Elasticsearch a OpenSearch
description: Obtenga información sobre cómo reemplazar el motor de búsqueda utilizado para las instalaciones locales de Adobe Commerce y Magento Open Source.
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Migración a OpenSearch

OpenSearch es una ramificación de código abierto de Elasticsearch 7.10.2 que se creó después del cambio de licencia de Elasticsearch.

A partir de las versiones 2.4.4, 2.4.3-p2 y 2.3.7-p3, Adobe Commerce y Magento Open Source admiten OpenSearch. Las instalaciones locales siguen siendo compatibles con Elasticsearch, aunque ya no lo es con Adobe Commerce en la infraestructura en la nube. A partir de la versión 2.4.6, OpenSearch tiene su propio módulo y campos en los ajustes de configuración de la administración.

## Ruta de migración

Los pasos para migrar a OpenSearch son sencillos y siguen en gran medida los pasos para la configuración del Elasticsearch. En estos pasos se da por hecho que Adobe Commerce es la única aplicación que utiliza el motor de búsqueda. En los casos en los que varias aplicaciones utilicen el motor de búsqueda, siga la guía oficial de migración [Cambio del Elasticsearch de código abierto a OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Asegúrese de que la instalación cumple los [requisitos previos del motor de búsqueda](../../installation/prerequisites/search-engine/overview.md).

1. Coloque el sitio en [Modo de mantenimiento](../../installation/tutorials/maintenance-mode.md).

1. Elasticsearch de desinstalación opcional.

1. [Instalar OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configuración del motor de búsqueda](../../configuration/search/configure-search-engine.md) y realizar tareas relacionadas, como vaciar la caché y reindexar el índice de búsqueda del catálogo.

No es necesario realizar más cambios en el valor de configuración.
