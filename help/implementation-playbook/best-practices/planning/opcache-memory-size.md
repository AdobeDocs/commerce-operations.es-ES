---
title: Práctica recomendada para el tamaño de memoria de OPcache
description: Describe cómo evitar la degradación del rendimiento mediante la configuración específica del consumo de memoria OPcache en proyectos de Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
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
* [Configurar las opciones de PHP](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)
* [Problemas más comunes de las bases de datos en Adobe Commerce sobre la infraestructura en la nube](../maintenance/resolve-database-performance-issues.md)
* [Indexadores &quot;Actualización según lo programado&quot; optimiza el rendimiento de Adobe Commerce](../maintenance/indexer-configuration.md)
