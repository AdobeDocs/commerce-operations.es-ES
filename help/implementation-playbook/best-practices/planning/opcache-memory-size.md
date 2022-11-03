---
title: Práctica recomendada para el tamaño de memoria OPcache
description: Describe cómo evitar la degradación del rendimiento por configuraciones específicas del consumo de memoria OPcache en proyectos de Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Práctica recomendada para el tamaño de memoria OPcache en Adobe Commerce

Para Adobe Commerce en la arquitectura 2.3.x de planificación de la infraestructura en la nube, se recomienda configurar `opcache.memory_consumption` hasta al menos 2 GB, para evitar la degradación del rendimiento.

## Productos y versiones afectados

* Adobe Commerce en infraestructura en la nube Arquitectura de plan Pro 2.3.x
* PHP 7.0 y posterior

## Configurar memoria

Asignar al menos **2 GB** de memoria para el [Módulo PHP OPcache](https://www.php.net/manual/en/book.opcache.php). El módulo OPcache está configurado en el `php.ini` archivo. Para asignar 2048 MB de memoria, establezca `opcache.memory_consumption = 2048`.

## Información adicional

* [Prácticas recomendadas de rendimiento: configuración de PHP](../../../performance/software.md#php-settings)
* [Configurar las opciones de PHP](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)
* [Los problemas más comunes de las bases de datos en Adobe Commerce en la infraestructura de la nube](../maintenance/resolve-database-performance-issues.md)
* [Los indexadores &quot;Actualizar según lo programado&quot; optimizan el rendimiento de Adobe Commerce](../maintenance/indexer-configuration.md)
