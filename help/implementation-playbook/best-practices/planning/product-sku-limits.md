---
title: Prácticas recomendadas sobre límites de productos
description: Conozca las prácticas recomendadas para configurar las unidades de mantenimiento de stock (SKU) de los productos para maximizar el rendimiento del sitio.
role: Admin
feature: Best Practices, Catalogs
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración del SKU del producto

Para maximizar el rendimiento, el máximo recomendado de unidades de almacenamiento (SKU) de producto efectivas es de 242 millones. Este SKU efectivo del producto se calcula del siguiente modo:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Donde:

- N es el número de elementos de esa categoría
- Los grupos de clientes incluyen catálogos compartidos, ya que crean un grupo de clientes adicional.

Tener más SKU efectivas que la cantidad máxima ralentiza la recuperación de datos del producto y aumenta el tiempo para completar las operaciones o indexaciones del Panel de administración.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Reducción del número de productos

Utilice las siguientes estrategias para reducir el número de productos (SKU):

- Minimizar multiplicadores—
   - La consolidación de sitios web reduce el multiplicador. Si tiene 50 000 SKU, diez sitios web y diez grupos de clientes, el número efectivo de SKU es de 5 millones. La eliminación de cinco grupos de clientes reduce los SKU efectivos a 2,5 millones.
   - Utilice funciones de producto alternativas para personalizar los precios y reemplazar los multiplicadores de catálogo compartido y de grupos de clientes.
   - Tanto los grupos de clientes como el catálogo compartido funcionan como multiplicadores del número de SKU efectivas en una tienda.
- Reestructurar el catálogo—
   - Reduzca el número de productos asignados a categorías.
   - Reduzca el número de SKU al reducir el número de sitios web, grupos de clientes, catálogos compartidos, número de productos o número de opciones de productos configurables
- Proporcione más variaciones de productos utilizando opciones personalizadas en lugar de crear productos separados.
- Teniendo en cuenta que un SKU efectivo podría incluir una serie de posibles permutaciones de precios, ya que los precios se pueden especificar de forma diferente para cada tienda o grupo de clientes.
- Desactive o elimine componentes del sistema no utilizados como módulos. (Consulte  [Desinstalación de módulos](../../../installation/tutorials/uninstall-modules.md).)
- Administre productos en un sistema de administración de plataformas (PMS) externo.

## Información adicional

- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Asignaciones de productos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Uso de catálogos compartidos](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Infraestructura en la nube: [Configuración de varios sitios web y tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- En línea: [Varios sitios web o tiendas](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce en la infraestructura de la nube: Prácticas recomendadas para la configuración de tiendas](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
