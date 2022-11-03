---
title: Prácticas recomendadas para configurar sitios, tiendas y vistas de tiendas
description: Conozca las prácticas recomendadas para configurar sitios, tiendas y vistas de tiendas a fin de maximizar el rendimiento del sitio.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---


# Práctica recomendada para configurar sitios, tiendas y vistas de tiendas

Para obtener el mejor rendimiento del sitio, configure un máximo de 50 sitios, 50 tiendas y 50 vistas de tiendas para Adobe Commerce en proyectos de infraestructura en la nube.

>[!NOTE]
>
>Para Adobe Commerce en infraestructura de nube, las prácticas recomendadas se aplican específicamente al entorno de producción (y posiblemente a la arquitectura de ensayo en Pro, sujeta a limitaciones de recursos), que tendría más recursos que los entornos de integración y desarrollo. Para los entornos de integración (Pro y Starter) y de ensayo (Starter), reduzca el número de vistas de tienda a menos de 5 o 10 (sujetas a revisión técnica).

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Estrategias para mejorar el rendimiento

Si el proyecto requiere muchos sitios, tiendas o vistas de tiendas, puede utilizar las siguientes estrategias para mejorar el rendimiento:

- Reestructurar el catálogo cambiando la lógica a categorías
- Separe las listas de precios de los datos del catálogo utilizando un precio externo y un sistema de gestión de precios (PMS).
- Usar un almacenamiento de datos alternativo sin SQL como Elasticsearch

## Impacto potencial en el rendimiento

Los sitios web y las tiendas son multiplicadores de los datos del catálogo, por lo que tener muchos sitios web y tiendas puede afectar negativamente al rendimiento del sitio de las siguientes maneras:

- Las tablas de índice más grandes aumentan el tiempo necesario para completar las operaciones de indexación [Índice de precios].
- El tiempo aumentado para recuperar la configuración de la aplicación degrada el tiempo de respuesta de la tienda en las páginas de catálogo que no están en caché.
- Aumento significativo del tiempo necesario para completar las operaciones de guardado en el administrador, ya que los datos se guardan por separado para cada sitio web.


## Información adicional

- [Información sobre sitios web, tiendas y vistas de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Configuración de varios sitios web o tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

