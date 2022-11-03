---
title: Prácticas recomendadas para configurar promociones
description: Conozca las prácticas recomendadas para configurar las reglas de ventas y los códigos de cupones con el fin de optimizar el rendimiento del Commerce store.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Prácticas recomendadas para configurar promociones

Para obtener el mejor rendimiento, siga estas prácticas recomendadas para configurar las ventas y promociones de los artículos de un carro de compras:

- **Reglas de ventas (reglas de precios del carro de compras)**-Configure no más de 1000 reglas de precios del carro de compras para todos los sitios web
   - Administrar y eliminar reglas no utilizadas.
   - Agregue condiciones de regla estrictas (como atributo o filtro de categoría) para la coincidencia más eficiente.
- **Cupones**—
   - Compruebe que el número total de cupones en la base de datos sea inferior a 250.000.
   - Elimine los cupones no utilizados y caducados.
   - Genere solo el número de cupones necesarios para cumplir los requisitos de la campaña.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Impacto potencial en el rendimiento

Tener más de la cantidad máxima recomendada de cupones o reglas de precios del carro de compras puede afectar el rendimiento del sitio de las siguientes maneras:

- Se ha aumentado el tiempo de respuesta cuando los productos se añaden al carro de compras.
- Se ha aumentado el tiempo para cargar y procesar el minicart.
- Se ha aumentado el tiempo para procesar la página del carro de compras.
- Se ha aumentado el tiempo para procesar la variable **Totales** en la página Cierre de compra.
- La aplicación de cupones puede tardar más de 2 segundos.

## Información adicional

- [Explicación de las campañas y promociones de marketing](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#campaigns)
- [Reglas de precios del carro de compras](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart.html)
- [Tutorial: Crear una regla de precio del carro de compras](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/cart-price-rules.html)
- [Códigos de cupón](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html)
- [Adobe Commerce en infraestructura de nube: Prácticas recomendadas para la configuración de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
