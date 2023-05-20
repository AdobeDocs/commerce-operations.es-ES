---
title: Prácticas recomendadas del carro de productos
description: Aprenda a optimizar el rendimiento de Adobe Commerce limitando el número de productos en un carro de compras.
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Prácticas recomendadas para la administración del carro de productos

Para obtener el mejor rendimiento, utilice las siguientes directrices para administrar los límites del carro de compras para Adobe Commerce y Magento Open Source:

- Para las versiones 2.3.x - 2.4.2, permita un máximo de 100 productos en un carro de compras.
- En las versiones 2.4.3 y posteriores, la mejora de las funciones de las reglas de ventas aumentó el carrito hasta 750.


Para las versiones 2.3.x - 2.4.2, el rendimiento esperado basado en los límites de elementos del carro de compras es:

- Hasta **100** productos en un carro de compras: el producto funciona y cumple los objetivos de rendimiento en cuanto al tiempo de respuesta.
- Hasta **300** productos en un carro de compras: el producto funciona, pero el tiempo de respuesta aumenta por encima de los objetivos.
- Arriba **500** productos en un carro de compras: no se garantiza que funcionen los flujos del carro de compras y del cierre de compra

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Reducir el número de elementos del carro de compras

Utilice las siguientes estrategias para administrar el número de elementos del carro de compras

- Divida los pedidos en varios pedidos más pequeños con un número menor de filas utilizando [!UICONTROL Add Item by SKU] función.
- Agregue únicamente la lógica personalizada y la personalización del carro de compras necesarias para cargar una lista de elementos.

## Impactos potenciales en el rendimiento

Tener más del número máximo recomendado de productos en el carro de compras puede afectar el rendimiento del sitio de las siguientes maneras:

- Mayor tiempo de respuesta para operaciones de recuperación de datos, validación de artículos del carro de compras, comprobaciones para aplicar reglas de precios y cálculos de impuestos y totales.
- Mayor tiempo de respuesta para el procesamiento de minicarros, incluido el procesamiento de vistas del carro de compras, el flujo de cierre de compra y la ejecución.
- Se ha aumentado el tiempo de carga de todas las páginas del sitio donde hay una minicart.

## Información adicional

- [Configurar opciones del producto](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Administración de un carro de compras](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
