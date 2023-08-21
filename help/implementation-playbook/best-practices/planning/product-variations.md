---
title: Prácticas recomendadas de configuración de variaciones de productos
description: Aprenda a optimizar el rendimiento de Adobe Commerce limitando el número de variaciones de productos configuradas.
role: Admin
feature: Best Practices, Catalog Management
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Prácticas recomendadas para configurar variaciones de productos

Para obtener el mejor rendimiento, configure un máximo de 50 variaciones por producto.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Reducción del número de variaciones de productos

Para obtener el mejor rendimiento del sitio, utilice las siguientes estrategias para reducir el número de variaciones de productos:

- Reestructurar el catálogo distribuyendo el número de variaciones entre diferentes productos.
- Elimine las opciones de atributos configurables que no estén disponibles.
- Administre variaciones mediante funciones alternativas como opciones personalizadas, categorías, productos relacionados, agrupados y agrupados.

## Impacto potencial en el rendimiento

Exceder el número recomendado de variaciones de productos puede afectar al rendimiento del sitio de las siguientes maneras:

- Tiempos de solicitud y procesamiento largos en las páginas de detalles y categorías de productos que contienen productos complejos.
- Se ha aumentado el tiempo de respuesta para completar las operaciones de guardado en el administrador.
- Se ha aumentado el tiempo para procesar el formulario de edición de productos.
- Cierre de compra lento.

## Información adicional

- [Crear productos configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Formación—[Administración de catálogos y productos mediante Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
