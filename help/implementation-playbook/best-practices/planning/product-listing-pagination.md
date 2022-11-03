---
title: Prácticas recomendadas para la paginación de listas de productos
description: Aprenda a optimizar el rendimiento de Adobe Commerce al administrar la cantidad de productos que se muestran en cada página del catálogo de tiendas.
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Prácticas recomendadas para la paginación de listas de productos

Para obtener el mejor rendimiento, muestre un máximo de 48 productos por página.

Puede configurar Adobe Commerce para que los compradores puedan ver todos los productos de la categoría en una sola página. Si el número de productos de categoría supera significativamente los 48 productos, actualice la configuración del catálogo para los controles de paginación de tienda.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Actualizar la configuración de la lista de productos

Si tiene más de 48 productos en cualquier categoría, actualice la configuración del catálogo de tiendas para deshabilitar la opción para **Permitir todos los productos por página**.

Después de desactivar esta opción, Adobe Commerce utiliza los controles de paginación de tienda de la lista de productos para administrar el número de productos que se muestran en los componentes de tienda. Para obtener instrucciones, consulte [Configurar controles de paginación](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Información adicional

- [Configurar listas de productos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
