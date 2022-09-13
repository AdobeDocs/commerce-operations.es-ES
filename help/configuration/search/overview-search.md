---
title: Información general del motor de búsqueda
description: Descripción general de las opciones del motor de búsqueda para Adobe Commerce y Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '132'
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

[Requisitos previos del motor de búsqueda]: ../../installation/prerequisites/search-engine/overview.md
[Configure nginx en su motor de búsqueda]: ../../installation/prerequisites/search-engine/configure-nginx.md
[Configurar Apache para su motor de búsqueda]: ../../installation/prerequisites/search-engine/configure-apache.md
[Elasticsearch]: https://www.elastic.co
[Instalación del software Commerce]: ../../installation/composer.md
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
