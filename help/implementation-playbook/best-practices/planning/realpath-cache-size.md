---
title: Tamaño de caché de RealPath
description: Aprenda a optimizar el rendimiento de Adobe Commerce actualizando la configuración de caché de readlpath de PHP para utilizar la configuración recomendada.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Prácticas recomendadas de configuración de caché Realpath

La caché Realpath almacena en caché las rutas reales del sistema de archivos de los nombres de archivo a los que se hace referencia en lugar de buscarlos cada vez. Cada vez que se realizan varias funciones de archivo o se requiere un archivo y se utiliza una ruta relativa, PHP tiene que buscar donde realmente existe ese archivo.

Para mejorar el rendimiento de Commerce, use la siguiente configuración recomendada para establecer la configuración de `realpath_cache` en el archivo `php.ini`:

- Establecer el tamaño de la caché en 10 MB (`realpath_cache_size=10M`)
- Establezca el tiempo de vida (ttl) en 7200 segundos (`realpath_cache_ttl=7200`)

Para obtener instrucciones de configuración, consulte [Cómo establecer las opciones de PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Productos y versiones afectados

- Adobe Commerce local, todas las versiones 2.3.x y superiores
- Adobe Commerce en infraestructura en la nube, todas las versiones 2.3.x y superiores

## Impacto potencial en el rendimiento

Si los valores de configuración de caché de Realpath son demasiado bajos o demasiado altos, añade una sobrecarga adicional durante la generación de caché, lo que ralentiza el rendimiento.

## Más información

- [On-premise: Configuración de PHP](../../../performance/software.md#php-settings)
- En la infraestructura en la nube:
  - [Prácticas recomendadas de base de datos](database-on-cloud.md)
  - [Problemas más comunes de las bases de datos en Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Indexadores &quot;Update On Schedule&quot; optimiza el rendimiento de Magento](../maintenance/indexer-configuration.md)
