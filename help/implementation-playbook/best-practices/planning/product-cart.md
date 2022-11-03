---
title: Prácticas recomendadas del carro de productos
description: Obtenga información sobre cómo optimizar el rendimiento de Adobe Commerce mediante la limitación del número de productos en un carro de compras.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Prácticas recomendadas para la administración del carro de productos

Para obtener el mejor rendimiento, utilice las siguientes directrices para administrar los límites del carro de compras para Adobe Commerce y Magento Open Source:

- Para las versiones 2.3.x - 2.4.2, permita un máximo de 100 productos en un carro de compras.
- Para las versiones 2.4.3 y posteriores, la mejora de las capacidades de las reglas de ventas aumentó el máximo del carro de compras a 750.


Para las versiones 2.3.x - 2.4.2, el rendimiento esperado en función de los límites de artículos del carro de compras es:

- Hasta **100** productos en un carro de compras: el producto funciona y cumple los objetivos de rendimiento para el tiempo de respuesta.
- Hasta **300** productos en un carro de compras: el producto funciona, pero el tiempo de respuesta aumenta por encima de los objetivos.
- Superior **500** productos en un carro de compras: no se garantiza que funcionen los flujos de carro y cierre de compra

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Reducir el número de artículos del carro de compras

Utilice las siguientes estrategias para administrar la cantidad de artículos del carro de compras

- Dividir pedidos en varios pedidos más pequeños con un número menor de filas usando la variable [!UICONTROL Add Item by SKU] función.
- Agregue solo la lógica personalizada y la personalización del carro de compras necesarias para cargar una lista de elementos.

## Impacto potencial en el rendimiento

Tener más del número máximo recomendado de productos en el carro de compras puede afectar al rendimiento del sitio de las siguientes maneras:

- Se ha aumentado el tiempo de respuesta para operaciones de recuperación de datos, validación de artículos del carro de compras, comprobaciones para la aplicación de reglas de precios y cálculos de impuestos y totales.
- Se ha aumentado el tiempo de respuesta para la renderización minicart, que incluye la renderización de vistas del carro de compras, el flujo de cierre de compra y la ejecución.
- Se ha aumentado el tiempo de carga de todas las páginas del sitio donde está presente el minicart.

## Información adicional

- [Configurar opciones de producto](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Administrar un carro de compras](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
