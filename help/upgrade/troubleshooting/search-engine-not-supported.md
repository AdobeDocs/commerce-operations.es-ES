---
title: Motor de búsqueda actual no admitido
description: Solucione el problema de la actualización de Adobe Commerce después de encontrar un error sobre un motor de búsqueda no compatible.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Motor de búsqueda actual no admitido

El siguiente mensaje de error indica que la versión de Adobe Commerce desde la que está actualizando está configurada para utilizar un motor de búsqueda en el catálogo que no es compatible con la versión a la que está actualizando:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Este error significa que una de las siguientes condiciones es verdadera en la versión de nivel inferior de Adobe Commerce:

- El motor de búsqueda se establece en MySQL.
- El motor de búsqueda está configurado con una versión de Elasticsearch que ya no es compatible.

Utilice el siguiente comando para comprobar el motor de búsqueda actual:

```bash
bin/magento config:show catalog/search/engine
```

El error se produce si el valor devuelto es `mysql`, `elasticsearch` o `elasticsearch6`.

>[!WARNING]
>
>Si ha recibido este error, la instalación está en un estado incoherente y no puede acceder al administrador. Le recomendamos que vuelva a su versión anterior mientras resuelve este error. Para ello, ejecute uno de los siguientes comandos:
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Donde `<version>` es la versión del Magento que ejecutaba **antes** de la actualización. Por ejemplo, `2.3.5`.

Siga las directrices descritas en las secciones siguientes para recuperarse de un estado incoherente.

## Si el motor de búsqueda es `mysql`

Antes de 2.4, MySQL era el motor de búsqueda por catálogo predeterminado, pero MySQL ya no es compatible con esta capacidad. Ahora debe instalar y configurar Elasticsearch o OpenSearch como motor de búsqueda antes de actualizar a 2.4.

Utilice los siguientes recursos para guiarle a través de este proceso:

- [Instalación y configuración del motor de búsqueda](../../configuration/search/overview-search.md)
- [Configuración del motor de búsqueda](../../configuration/search/configure-search-engine.md)

Después de configurar el motor de búsqueda y reindexar, está listo para actualizar a 2.4.

## Si el motor de búsqueda es `elasticsearch`

Ya no se admite el Elasticsearch 6 y versiones anteriores de.

El valor `elasticsearch` indica que su versión de nivel inferior de Adobe Commerce está configurada para utilizar el Elasticsearch 2.x. Esta versión de Elasticsearch ya no es compatible.

Debe realizar las siguientes tareas antes de actualizar a la versión 2.4:

1. Actualice a una versión de Elasticsearch compatible con Commerce. Consulte [Actualización del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre cómo realizar copias de seguridad de los datos, detectar posibles problemas de migración y probar las actualizaciones antes de implementarlas en producción. Según la versión actual del Elasticsearch, puede que sea necesario o no reiniciar el clúster por completo.

   >[!NOTE]
   >
   >Elasticsearch requiere JDK 1.8 o superior. Consulte [Instalar el Kit de desarrollo de software de Java (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) para comprobar qué versión de JDK está instalada.

1. [Configurar el Elasticsearch](../../configuration/search/configure-search-engine.md) y reindexar.

Después de configurar el motor de búsqueda y reindexar, está listo para actualizar a 2.4.
