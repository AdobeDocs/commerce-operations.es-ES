---
title: Prácticas recomendadas para la configuración de opciones de producto
description: Optimice el rendimiento de Adobe Commerce limitando el número de opciones de producto.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---


# Prácticas recomendadas de opciones de producto

Para obtener el mejor rendimiento, configure un máximo de 100 opciones de producto por producto.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Reducir las opciones de los productos

Para obtener el mejor rendimiento del sitio, utilice las siguientes estrategias para reducir el número de opciones de producto:

- Configure productos complejos y opciones personalizadas como fuente de variaciones de productos.
- En lugar de crear plantillas de producto globales y contenedores de opciones que se aplican a todos los productos, utilice conjuntos de atributos para crear plantillas de producto específicas con atributos y opciones de destino.
- Administre la información del producto a través de un sistema de administración de productos (PMS) externo.

## Posible impacto en el rendimiento

La configuración de muchas opciones de producto aumenta la cantidad de datos recuperados para cada producto en todas las operaciones de lectura y escritura, lo que da como resultado:

- Se ha aumentado el tráfico de consultas SQL y el mayor `JOIN` las operaciones aumentan el rendimiento de la base de datos.
- Se ha aumentado el tamaño de los índices de Adobe Commerce y el índice de búsqueda de texto completo.

Los aumentos enumerados anteriormente pueden afectar al rendimiento del sitio de las siguientes maneras:

- Tiempo de respuesta más largo para la mayoría de los escenarios de tienda relacionados con productos que contienen muchas opciones en atributos.
- Aumento significativo del tiempo necesario para completar las operaciones de administración de productos en Administración que puede llevar a tiempos de espera, especialmente para escenarios relacionados con la lista de atributos y la recuperación de árboles, incluida la administración de reglas de promoción.
- Puede bloquear acciones masivas que completan operaciones masivas asincrónicas como importar y exportar y asignar precios personalizados a varios productos en un catálogo compartido.

## Información adicional

- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Prácticas recomendadas para la configuración de atributos del producto](product-attributes-and-options.md)
- [Registro de acciones masivas](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API de acciones masivas de inventario](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Formación: Administrar catálogos y productos con Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

