---
title: Práctica recomendada para el tamaño de memoria de OPcache
description: Describe cómo evitar la degradación del rendimiento mediante la configuración específica del consumo de memoria OPcache en proyectos de Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---

# Práctica recomendada para el tamaño de memoria de OPcache en Adobe Commerce

Para la arquitectura de plan Pro 2.3.x de Adobe Commerce en la infraestructura en la nube, se recomienda establecer `opcache.memory_consumption` en al menos 2 GB para evitar la degradación del rendimiento.

## Productos y versiones afectados

* Arquitectura de plan de Adobe Commerce en la nube Pro 2.3.x
* PHP 7.0 y posterior

## Configuración de memoria

Asigne al menos **2 GB** de memoria para el [módulo PHP de OPcache](https://www.php.net/manual/en/book.opcache.php). El módulo OPcache está configurado en el archivo `php.ini`. Para asignar 2048 MB de memoria, establezca `opcache.memory_consumption = 2048`.

## Más información

* [Prácticas recomendadas de rendimiento - Configuración de PHP](../../../performance/software.md#php-settings)
* [Configurar opciones de PHP](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)
* [Problemas más comunes de las bases de datos en Adobe Commerce sobre la infraestructura en la nube](../maintenance/resolve-database-performance-issues.md)
* [Indexadores &quot;Actualización según lo programado&quot; optimiza el rendimiento de Adobe Commerce](../maintenance/indexer-configuration.md)
