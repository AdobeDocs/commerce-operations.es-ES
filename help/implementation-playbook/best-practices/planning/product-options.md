---
title: Prácticas recomendadas de configuración de opciones de productos
description: Optimice el rendimiento de Adobe Commerce limitando el número de opciones de producto.
role: Admin
feature: Best Practices, Catalog Management
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Prácticas recomendadas sobre opciones de productos

Para obtener el mejor rendimiento, configure un máximo de 100 opciones de producto por producto.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Reducción de opciones de productos

Para obtener el mejor rendimiento del sitio, utilice las siguientes estrategias para reducir el número de opciones de producto:

- Configure productos complejos y opciones personalizadas como fuente de variaciones de productos.
- En lugar de crear plantillas de producto globales y contenedores de opciones que se apliquen a todos los productos, utilice conjuntos de atributos para crear plantillas de producto específicas con atributos y opciones de destino.
- Administre la información del producto mediante un sistema de administración de productos (PMS) externo.

## Impacto potencial en el rendimiento

La configuración de muchas opciones de producto aumenta la cantidad de datos recuperados para cada producto en todas las operaciones de lectura y escritura, lo que da como resultado:

- Mayor tráfico de consultas SQL y más `JOIN` las operaciones aumentan el rendimiento de la base de datos.
- Tamaño aumentado para los índices de Adobe Commerce y el índice de búsqueda de texto completo.

Los incrementos enumerados anteriormente pueden afectar al rendimiento del sitio de las siguientes maneras:

- Tiempo de respuesta más largo para la mayoría de los escenarios de tienda relacionados con productos que contienen muchas opciones en atributos.
- Aumento significativo del tiempo necesario para completar las operaciones de administración de productos en Admin que puede provocar tiempos de espera, especialmente para escenarios relacionados con la lista de atributos y la recuperación del árbol, incluida la administración de reglas de promoción.
- Puede bloquear las acciones masivas que completan operaciones masivas asincrónicas como la importación y exportación y la asignación de precios personalizados a varios productos en un catálogo compartido.

## Información adicional

- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Prácticas recomendadas para la configuración de atributos del producto](product-attributes-and-options.md)
- [Registro de acciones masivas](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API de acciones masivas de inventario](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Formación: Administrar catálogos y productos con Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
