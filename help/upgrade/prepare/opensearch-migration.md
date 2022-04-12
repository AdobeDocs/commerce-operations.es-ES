---
title: Migración de Elasticsearch a OpenSearch
description: Obtenga información sobre cómo reemplazar el motor de búsqueda utilizado para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Migración a OpenSearch

OpenSearch es una ramificación de código abierto de Elasticsearch 7.10.2 que se creó tras el cambio de licencia del Elasticsearch.

A partir de 2.4.4, 2.4.3-p2 y 2.3.7-p3, Adobe Commerce y el Magento Open Source admiten OpenSearch. Las instalaciones locales siguen siendo compatibles con el Elasticsearch, aunque Adobe Commerce ya no es compatible con la infraestructura en la nube.

## Ruta de migración

Los pasos para migrar a OpenSearch son sencillos y en gran medida siguen los pasos para la configuración del Elasticsearch. Estos pasos suponen que Adobe Commerce es la única aplicación que utiliza el motor de búsqueda. En casos en los que varias aplicaciones utilizan el motor de búsqueda, siga la guía oficial de migración [Cambio del Elasticsearch de código abierto a OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Asegúrese de que la instalación cumpla los requisitos de [requisitos previos del motor de búsqueda](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. Coloque el sitio en [Modo de mantenimiento](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. Desinstale el Elasticsearch de forma opcional.

1. [Instalar OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configuración del motor de búsqueda](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) y realizar tareas relacionadas, como vaciar la caché y reindexar el índice de búsqueda del catálogo.

No es necesario realizar más cambios en los valores de configuración.
