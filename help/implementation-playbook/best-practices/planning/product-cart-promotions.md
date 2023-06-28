---
title: Prácticas recomendadas para configurar promociones
description: Conozca las prácticas recomendadas para configurar reglas de ventas y códigos de cupones para optimizar el rendimiento de la tienda de Commerce.
role: User
feature: Best Practices, Price Rules, Shopping Cart
exl-id: 6e177836-b8da-4e55-842c-e12ff54ffaf5
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Prácticas recomendadas para configurar promociones

Para obtener el mejor rendimiento, siga estas prácticas recomendadas para configurar las ventas y promociones de los artículos de un carro de compras:

- **Reglas de ventas (reglas de precios del carro de compras)**-Configurar no más de 1000 reglas de precios de carrito para todos los sitios web
   - Administrar y eliminar reglas no utilizadas.
   - Añada condiciones de regla estrictas (como atributo o filtro de categoría) para lograr la coincidencia más eficaz.
- **Cupones**—
   - Compruebe que el número total de cupones de la base de datos sea inferior a 250 000.
   - Eliminar cupones no utilizados y caducados.
   - Genere solamente el número de cupones necesarios para cumplir los requisitos de la campaña.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Impactos potenciales en el rendimiento

Tener más del número máximo recomendado de reglas de precios de carro de compras o cupones puede afectar el rendimiento del sitio de las siguientes maneras:

- Se ha aumentado el tiempo de respuesta cuando se añaden productos al carro de compras.
- Se ha aumentado el tiempo para cargar y procesar la minicart.
- Tiempo aumentado para procesar la página del carro de compras.
- Mayor tiempo para procesar **Totales** en la página Cierre de compra.
- La aplicación de cupones puede tardar más de 2 segundos.

## Información adicional

- [Campañas y promociones de marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Reglas de precio de carrito](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutorial: Crear una regla de precios de carro de compras](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Códigos de cupón](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce en la infraestructura de la nube: Prácticas recomendadas para la configuración de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
