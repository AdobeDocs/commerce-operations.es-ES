---
title: Prácticas recomendadas de configuración de categorías
description: Conozca las prácticas recomendadas para maximizar el rendimiento del sitio limitando el número de categorías en el catálogo.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración de categorías

Para obtener el mejor rendimiento, no configure más del número máximo recomendado de categorías para sitios de Adobe Commerce.

- Para la versión 2.4.2 y posteriores de Adobe Commerce, configure un máximo de 6000 categorías
- Para las versiones de Adobe Commerce 2.3.x y 2.4.0 a 2.4.1-p1, configure un máximo de 3000 categorías

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Reducción del número de productos

Utilice las siguientes estrategias para reducir el número de categorías:

- Administración de funciones de producto únicas mediante atributos y opciones personalizadas
- Eliminar categorías inactivas
- Optimizar la profundidad del catálogo en la navegación

## Impactos potenciales en el rendimiento

Tener un número de categorías superior al máximo recomendado puede afectar al rendimiento del sitio de las siguientes maneras:

- Aumento tangible en el tiempo de respuesta para páginas de catálogo no almacenadas en caché
- Ejecución y tiempos de espera largos al administrar categorías desde el administrador
- Aumento del tamaño de las tablas de base de datos correspondientes
- Las tablas de índice más grandes aumentan el tiempo necesario para completar las operaciones de indexación del `[category/product relation index\]`
- Mayor tiempo de procesamiento para completar las operaciones de creación de árbol de categorías, recuperación de menús y administración de reglas de categorías

## Información adicional

- [Resumen de categorías](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Información general de navegación](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Asignaciones de productos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce en la infraestructura de la nube: Prácticas recomendadas para la configuración de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
