---
title: Prácticas recomendadas para la paginación de listas de productos
description: Aprenda a optimizar el rendimiento de Adobe Commerce administrando la cantidad de productos que se muestran en cada página del catálogo de tiendas.
role: User, Admin
feature: Best Practices, Catalogs
exl-id: 473f23a9-53fb-41a6-9b3a-af7bd1208be0
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Prácticas recomendadas para la paginación de listas de productos

Para obtener el mejor rendimiento, muestre un máximo de 48 productos por página.

Puede configurar Adobe Commerce para que los compradores puedan ver todos los productos de la categoría en una sola página. Si el número de productos de categoría supera significativamente los 48 productos, actualice la configuración del catálogo para controles de paginación de tienda.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Actualizar la configuración de la lista de productos

Si tienes más de 48 productos en cualquier categoría, actualiza la configuración del catálogo de tiendas para desactivar la opción **Permitir todos los productos por página**.

Después de deshabilitar esta opción, Adobe Commerce usa los controles de paginación de tienda de listas de productos para administrar el número de productos que se muestran en los componentes de tienda. Para obtener instrucciones, consulte [Configuración de controles de paginación](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Información adicional

- [Configurar listados de productos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html)
