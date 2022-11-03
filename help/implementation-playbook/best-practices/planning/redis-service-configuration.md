---
title: Prácticas recomendadas para la configuración del servicio Redis
description: Aprenda a mejorar el rendimiento del almacenamiento en caché mediante la implementación de caché de Redis ampliada para Adobe Commerce 2.3.5.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración del servicio Redis

- Para Adobe Commerce 2.3.3 y versiones posteriores implementadas en la infraestructura de nube, actualice a Redis versión 5.0.
- Para Adobe Commerce versión 2.3.5 o superior, utilice la implementación de caché de Redis extendida. Esta implementación incluye las siguientes optimizaciones para minimizar el número de consultas de Redis que se realizan en cada solicitud de Adobe Commerce:
   - Reduzca el tamaño de las transferencias de datos de red entre Redis y Adobe Commerce
   - Reduzca el consumo de Redis de los ciclos de CPU al mejorar la capacidad del adaptador para determinar automáticamente lo que debe cargarse
   - Reducir las condiciones de carrera en las operaciones de escritura Redis

## Productos y versiones afectados

Adobe Commerce en infraestructura de nube con versión 2.3.3 o posterior.
Adobe Commerce (todos los métodos de implementación), versión 2.3.5 y posterior

## Actualización de la versión de Redis para implementaciones en la nube

Para implementaciones de Adobe Commerce en infraestructura de nube con Adobe Commerce 2.3.3 o posterior, actualice el servicio Redis a la versión 5.0 de Redis. Para obtener instrucciones, consulte los temas siguientes en la documentación de Adobe Commerce sobre infraestructura de nube:

- [Configuración del servicio Redis](https://devdocs.magento.com/cloud/project/services-redis.html)
- [Cambiar la versión del servicio](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## Configurar la implementación de caché de Redis extendida

Para Adobe Commerce 2.3.5 y versiones posteriores, actualice la configuración para que utilice la implementación de caché de Redis extendida `\Magento\Framework\Cache\Backend\Redis`.

### Configuración para implementaciones en la nube

con `ece-tools` 2002.1.1 o superior, configure la caché mejorada de Redis estableciendo la variable `REDIS_BACKEND` variable de implementación en el archivo de configuración de entorno, `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Para obtener más información, consulte [Implementar variables > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) en la documentación de Adobe Commerce sobre infraestructura de nube.

>[!NOTE]
>
> Compruebe la versión de las herramientas de ece instalada en el entorno local de Cloud desde la línea de comandos utilizando la variable `composer show magento/ece-tools` comando. Si es necesario, [actualizar la versión de las herramientas de ece](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

### Configuración de implementaciones locales

Para implementaciones locales de Adobe Commerce, configure la nueva implementación de caché de Redis mediante el `bin/magento:setup` comandos. Para obtener instrucciones, consulte [Usar Redis para la caché predeterminada](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Información adicional

- [Versión 2.3.5 de Adobe Commerce: mejoras de rendimiento](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis Page Cache](../../../configuration/cache/redis-pg-cache.md)


