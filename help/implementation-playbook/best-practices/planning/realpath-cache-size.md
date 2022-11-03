---
title: Tamaño de caché de la ruta de acceso real
description: Aprenda a optimizar el rendimiento de Adobe Commerce actualizando la configuración de caché de readlpath de PHP para utilizar los ajustes recomendados.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración de caché de Realpath

La caché de Realpath almacena en caché las rutas reales del sistema de archivos de los nombres de archivo a los que se hace referencia en lugar de buscarlos cada vez. Cada vez que se realizan varias funciones de archivo o requieren un archivo y utilizan una ruta relativa, PHP debe buscar dónde existe realmente ese archivo.

Para mejorar el rendimiento de Commerce, utilice las siguientes opciones recomendadas para configurar la variable `realpath_cache` en la `php.ini` archivo:

- Establezca el tamaño de la caché en 10 MB (`realpath cache_size=10M`)
- Establezca el tiempo de vida (ttl) en 7200 segundos (`realpath_cache_ttl=7200`)

Para obtener instrucciones de configuración, consulte [Cómo configurar las opciones de PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Productos y versiones afectados

- Adobe Commerce local, todas las versiones 2.3.x y posteriores
- Adobe Commerce en infraestructura en la nube, todas las versiones 2.3.x y posteriores

## Posible impacto en el rendimiento

Si los valores de configuración de la caché de Realpath son demasiado bajos o demasiado altos, se añade sobrecarga adicional durante la generación de la caché, lo que ralentiza el rendimiento.

## Información adicional

- [Local: Configuración de PHP](../../../performance/software.md#php-settings)
- En la infraestructura de nube:
   - [Prácticas recomendadas de la base de datos](database-on-cloud.md)
   - [Problemas más comunes de la base de datos en el Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Los indexadores &quot;Actualizar según lo programado&quot; optimizan el rendimiento del Magento](../maintenance/indexer-configuration.md)

