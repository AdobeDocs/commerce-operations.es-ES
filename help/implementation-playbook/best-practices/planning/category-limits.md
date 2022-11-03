---
title: Prácticas recomendadas para la configuración de categorías
description: Conozca las prácticas recomendadas para maximizar el rendimiento del sitio mediante la limitación del número de categorías en el catálogo.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración de categorías

Para obtener el mejor rendimiento, no configure más del número máximo recomendado de categorías para sitios de Adobe Commerce.

- Para la versión 2.4.2 y posteriores de Adobe Commerce, configure un máximo de 6000 categorías
- Para las versiones 2.3.x y 2.4.0 a 2.4.1-p1 de Adobe Commerce, configure un máximo de 3000 categorías

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Reducir el número de productos

Utilice las siguientes estrategias para reducir el número de categorías:

- Administrar características de producto únicas mediante atributos y opciones personalizadas
- Eliminar categorías inactivas
- Optimizar la profundidad del catálogo en la navegación

## Impacto potencial en el rendimiento

Tener más de la cantidad máxima recomendada de categorías puede afectar el rendimiento del sitio de las siguientes maneras:

- Aumento tangible en el tiempo de respuesta para páginas de catálogo no almacenadas en caché
- Ejecución y tiempos de espera largos al administrar categorías desde Administración
- Aumento del tamaño de las tablas de base de datos correspondientes
- Las tablas de índice más grandes aumentan el tiempo necesario para completar las operaciones de indexación para la variable `[category/product relation index\]`
- Se ha aumentado el tiempo de procesamiento para completar las operaciones de administración de reglas de categoría, recuperación de menús y creación de árboles de categorías.

## Información adicional

- [Resumen de las categorías](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Información general sobre navegación](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Asignaciones de productos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce en infraestructura de nube: Prácticas recomendadas para la configuración de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
