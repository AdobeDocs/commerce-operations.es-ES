---
title: Información general del motor de búsqueda
description: Descripción general de las opciones del motor de búsqueda para Adobe Commerce y Magento Open Source.
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Información general del motor de búsqueda

A partir de la versión 2.4.4, Adobe Commerce y Magento Open Source requieren cualquiera de las opciones siguientes: [Elasticsearch] o [OpenSearch] para que sea el motor de búsqueda del catálogo. Se requiere el Elasticsearch de las versiones anteriores de 2.4.x. Consulte los siguientes temas para obtener más información sobre la instalación de un motor de búsqueda y la configuración inicial:

- [Requisitos previos del motor de búsqueda]
- [Configure nginx en su motor de búsqueda]
- [Configurar Apache para su motor de búsqueda]
- [Instalación del software Commerce] (interfaz de línea de comandos)

Después de instalar e integrar el motor de búsqueda con Adobe Commerce, debe realizar un mantenimiento adicional:

- [Configurar palabras clave de búsqueda](search-stopwords.md)
- [Configuración del motor de búsqueda](configure-search-engine.md)

<!-- Link Definitions -->

[Requisitos previos del motor de búsqueda]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[Configure nginx en su motor de búsqueda]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[Configurar Apache para su motor de búsqueda]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Instalación del software Commerce]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
