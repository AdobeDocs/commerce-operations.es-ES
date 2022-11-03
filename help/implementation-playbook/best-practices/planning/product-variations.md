---
title: Prácticas recomendadas para la configuración de variaciones de producto
description: Aprenda a optimizar el rendimiento de Adobe Commerce limitando el número de variaciones de producto configuradas.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---


# Prácticas recomendadas para configurar variaciones de productos

Para obtener el mejor rendimiento, configure un máximo de 50 variaciones por producto.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Reducir el número de variaciones de productos

Para obtener el mejor rendimiento del sitio, utilice las siguientes estrategias para reducir el número de variaciones de productos:

- Reestructurar el catálogo distribuyendo el número de variaciones entre diferentes productos.
- Elimine las opciones de atributo configurables que no estén en existencias.
- Administre variaciones mediante funciones alternativas como opciones personalizadas, categorías, productos relacionados, agrupados y agrupados.

## Posible impacto en el rendimiento

Si se supera el número recomendado de variaciones de productos, el rendimiento del sitio puede verse afectado de las siguientes maneras:

- Tiempos de solicitud y procesamiento largos en los detalles del producto y las páginas de categoría que contienen productos complejos.
- Se ha aumentado el tiempo de respuesta para completar las operaciones de Guardar en Admin.
- Se ha aumentado el tiempo para procesar el formulario de edición de producto.
- Cierre de compra lento.

## Información adicional

- [Crear productos configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Formación—[Administrar catálogos y productos con Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
