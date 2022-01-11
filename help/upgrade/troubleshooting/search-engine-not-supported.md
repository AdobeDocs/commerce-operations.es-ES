---
title: Motor de búsqueda actual no compatible
description: Solucione los problemas de la actualización de Adobe Commerce o Magento Open Source después de encontrar un error sobre un motor de búsqueda no admitido.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# Motor de búsqueda actual no admitido

El siguiente mensaje de error indica que la versión de Magento desde la que está actualizando está configurada para utilizar un motor de búsqueda de catálogo no compatible con la versión de Magento a la que está actualizando:

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
>Si ha recibido este error, el Magento se encuentra en un estado incoherente y no puede acceder al administrador. Le recomendamos que vuelva a su versión anterior mientras resuelve este error. Para ello, ejecute uno de los siguientes comandos:
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

Antes de la versión 2.4, MySQL era el motor de búsqueda predeterminado del catálogo, pero MySQL ya no es compatible con esta capacidad. Ahora, debe instalar y configurar Elasticsearch como motor de búsqueda antes de actualizar a la versión 2.4.

Utilice los siguientes recursos para ayudarle a guiar a través de este proceso:

- [Instalación y configuración del Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [Instalación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configuración del Elasticsearch para trabajar con [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) o [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [Configuración del Magento para utilizar el Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

Después de configurar el Elasticsearch y reindexar, está listo para actualizar a 2.4.

## Si el motor de búsqueda es `elasticsearch`

Un valor de `elasticsearch` indica que la versión de nivel inferior de Adobe Commerce o Magento Open Source está configurada para utilizar Elasticsearch 2.x. Esta versión de Elasticsearch ya no es compatible.

Debe realizar las siguientes tareas antes de actualizar a la versión 2.4:

1. Actualizar Elasticsearch. Se recomienda actualizar al Elasticsearch 7.x. Consulte [Actualización del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre cómo realizar copias de seguridad de los datos, detectar posibles problemas de migración y probar actualizaciones antes de implementarlas en producción. Según la versión actual del Elasticsearch, puede que sea necesario o no reiniciar el clúster completo.

   >[!NOTE]
   >
   >Elasticsearch requiere JDK 1.8 o superior. Consulte [Instalación del Kit de desarrollo de software de Java (JDK)](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) para comprobar qué versión de JDK está instalada.

1. [Configuración del Magento para utilizar el Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) y reindexar.

Después de configurar el Elasticsearch y reindexar, está listo para actualizar a 2.4.
