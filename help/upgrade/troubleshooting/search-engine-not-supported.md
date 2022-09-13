---
title: Motor de búsqueda actual no compatible
description: Solucione los problemas de la actualización de Adobe Commerce o Magento Open Source después de encontrar un error sobre un motor de búsqueda no admitido.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Motor de búsqueda actual no admitido

El siguiente mensaje de error indica que la versión de Adobe Commerce o Magento Open Source desde la que está actualizando está configurada para utilizar un motor de búsqueda de catálogo no compatible con la versión a la que está actualizando:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Este error significa que una de las siguientes condiciones es verdadera en la versión de nivel inferior de Adobe Commerce o Magento Open Source:

- El motor de búsqueda está establecido en MySQL.
- El motor de búsqueda se establece en una versión de Elasticsearch que ya no es compatible.

Utilice el siguiente comando para comprobar el motor de búsqueda actual:

```bash
bin/magento config:show catalog/search/engine
```

El error se produce si el valor devuelto es `mysql` o `elasticsearch`.

>[!WARNING]
>
>Si ha recibido este error, la instalación se encuentra en un estado incoherente y no puede acceder al administrador. Le recomendamos que vuelva a su versión anterior mientras resuelve este error. Para ello, ejecute uno de los siguientes comandos:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Donde `<version>` es la versión de Magento que estaba ejecutando **before** la actualización. Por ejemplo, `2.3.5`.

Siga las directrices descritas en las secciones siguientes para recuperarse de un estado incoherente.

## Si el motor de búsqueda es `mysql`

Antes de la versión 2.4, MySQL era el motor de búsqueda predeterminado del catálogo, pero MySQL ya no es compatible con esta capacidad. Ahora, debe instalar y configurar Elasticsearch o OpenSearch como motor de búsqueda antes de actualizar a 2.4.

Utilice los siguientes recursos para ayudarle a guiar a través de este proceso:

- [Instalación y configuración del Elasticsearch](../../configuration/search/overview-search.md)
- [Instalación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configuración del Elasticsearch para trabajar con [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) o [Apache](../../installation/prerequisites/search-engine/configure-apache.md)
- [Configuración del Elasticsearch](../../configuration/search/configure-search-engine.md)

Después de configurar el motor de búsqueda y reindexar, está listo para actualizar a 2.4.

## Si el motor de búsqueda es `elasticsearch`

Un valor de `elasticsearch` indica que la versión de nivel inferior de Adobe Commerce o Magento Open Source está configurada para utilizar Elasticsearch 2.x. Esta versión de Elasticsearch ya no es compatible.

Debe realizar las siguientes tareas antes de actualizar a la versión 2.4:

1. Actualice a una versión de Elasticsearch compatible con Commerce. Consulte [Actualización del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre cómo realizar copias de seguridad de los datos, detectar posibles problemas de migración y probar actualizaciones antes de implementarlas en producción. Según la versión actual del Elasticsearch, puede que sea necesario o no reiniciar el clúster completo.

   >[!NOTE]
   >
   >Elasticsearch requiere JDK 1.8 o superior. Consulte [Instalación del Kit de desarrollo de software de Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para comprobar qué versión de JDK está instalada.

1. [Configuración del Elasticsearch](../../configuration/search/configure-search-engine.md) y reindexar.

Después de configurar el motor de búsqueda y reindexar, está listo para actualizar a 2.4.
