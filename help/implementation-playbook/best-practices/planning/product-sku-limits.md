---
title: Prácticas recomendadas sobre los límites del producto
description: Conozca las prácticas recomendadas para configurar las unidades de mantenimiento (SKU) de existencias de productos a fin de maximizar el rendimiento del sitio.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración de SKU de producto

Para maximizar el rendimiento, el máximo recomendado para unidades de mantenimiento de almacenamiento (SKU) efectivas del producto es de 10 millones. Este máximo de producto efectivo se calcula como:

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

Tener más de la cantidad máxima de SKU efectivos ralentiza la recuperación de datos de productos y aumenta el tiempo para completar las operaciones de administración.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Reducir el número de productos

Utilice las siguientes estrategias para reducir el número de productos (SKU):

- Minimizar multiplicadores—
   - Mover tiendas o sitios web reduce el multiplicador. Si tiene 50 000 SKU, diez sitios web y diez grupos de clientes, el número efectivo de SKU es de 5 millones. Si se eliminan cinco grupos de clientes, los SKU efectivos se reducirán a 2,5 millones.
   - Utilice funciones de producto alternativas para los precios personalizados con el fin de reemplazar los multiplicadores de catálogo compartido y de grupos de clientes.
- Reestructurar el catálogo—
   - Reduzca el número de productos asignados a categorías.
   - Reduzca el número de SKU disminuyendo el número de tiendas, sitios web, grupos de clientes o cantidad de productos.
- Proporcione más variaciones de producto mediante el uso de opciones personalizadas en lugar de crear productos independientes.
- Desactivar o quitar componentes del sistema no utilizados, como módulos. (Consulte  [Desinstalar módulos](../../../installation/tutorials/uninstall-modules.md).)
- Administre productos en un sistema de administración de plataformas (PMS) externo.

## Información adicional

- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Asignaciones de productos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- Infraestructura de nube: [Configuración de varios sitios web y tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Local: [Múltiples sitios web o tiendas](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce en infraestructura de nube: Prácticas recomendadas para la configuración de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
