---
title: Tamaño de caché de RealPath
description: Aprenda a optimizar el rendimiento de Adobe Commerce actualizando la configuración de caché de readlpath de PHP para utilizar la configuración recomendada.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Prácticas recomendadas de configuración de caché Realpath

La caché Realpath almacena en caché las rutas reales del sistema de archivos de los nombres de archivo a los que se hace referencia en lugar de buscarlos cada vez. Cada vez que se realizan varias funciones de archivo o se requiere un archivo y se utiliza una ruta relativa, PHP tiene que buscar donde realmente existe ese archivo.

Para mejorar el rendimiento de Commerce, utilice la siguiente configuración recomendada para configurar el `realpath_cache` configuración en la `php.ini` archivo:

- Establezca el tamaño de la caché en 10 MB (`realpath cache_size=10M`)
- Establezca el tiempo de vida (ttl) en 7200 segundos (`realpath_cache_ttl=7200`)

Para obtener instrucciones de configuración, consulte [Cómo configurar las opciones de PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Productos y versiones afectados

- Adobe Commerce local, todas las versiones 2.3.x y superiores
- Adobe Commerce en infraestructura en la nube, todas las versiones 2.3.x y superiores

## Impacto potencial en el rendimiento

Si los valores de configuración de caché de Realpath son demasiado bajos o demasiado altos, añade una sobrecarga adicional durante la generación de caché, lo que ralentiza el rendimiento.

## Información adicional

- [On-premise: Configuración de PHP](../../../performance/software.md#php-settings)
- En la infraestructura en la nube:
   - [Prácticas recomendadas de base de datos](database-on-cloud.md)
   - [Problemas más comunes de la base de datos en Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Indexadores &quot;Actualización según lo programado&quot; optimiza el rendimiento del Magento](../maintenance/indexer-configuration.md)
