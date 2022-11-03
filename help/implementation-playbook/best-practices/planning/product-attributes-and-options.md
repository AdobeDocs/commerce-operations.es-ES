---
title: Prácticas recomendadas para la configuración de atributos de producto
description: Obtenga información sobre cómo optimizar el rendimiento de Adobe Commerce mediante la limitación del número de atributos de producto, opciones de atributos y conjuntos de atributos
role: User, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Prácticas recomendadas para la configuración de atributos del producto

- Para obtener el mejor rendimiento, no configure más del número máximo recomendado de atributos de producto u opciones de atributos de producto.

- **Atributos del producto**—
   - Para Adobe Commerce versión 2.3.x y 2.4.0 a 2.4.1-p1, configure no más de 500 atributos
   - Para Adobe Commerce versión 2.4.2 y posteriores, configure hasta 1500 atributos de producto
- **Opciones de atributos del producto**-Configure hasta 100 opciones de atributos para cada atributo
- **Conjuntos de atributos del producto**-Configure un máximo de 1000 conjuntos de atributos _

>[!NOTE]
>
>Los atributos de producto especifican características que se aplican globalmente a todos los productos. Las opciones de atributos del producto son personalizaciones para especificar características que se aplican a productos específicos.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Reducir el número de atributos de producto

Para obtener el mejor rendimiento al administrar productos desde el administrador y recuperar datos de productos en la tienda:

- Utilice diferentes plantillas de producto (conjuntos de atributos) para diferentes productos.
- Aproveche las opciones personalizadas y los productos complejos para la administración de variaciones
- Minimice el número de atributos en los que se pueden buscar.
- Elimine las propiedades del producto que no se utilicen.
- Almacene y administre atributos no relacionados con el comercio en sistemas de administración de productos externos (PMS).

## Reducir las opciones de atributos de producto de número

Para obtener el mejor rendimiento al administrar productos desde el administrador y recuperar datos de productos en la tienda:

- Utilice diferentes mecanismos de variación para crear productos: productos complejos, opciones personalizadas como fuente de variaciones de productos.
- Cree plantillas de producto específicas con atributos y opciones de objetivo para evitar plantillas de producto generalizadas y contenedores de opciones.
- Mantener una lista de opciones de atributos reales.
- Administre la información del producto a través de un sistema de administración de productos (PMS) externo.

## Reducir el número de conjuntos de atributos del producto

Elimine los conjuntos de atributos de producto no utilizados mediante MySQL.

### Revisión de la configuración del conjunto de atributos

1. [Conectarse a la base de datos del sitio](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Buscar el número de conjuntos de atributos usando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Elimine los conjuntos de atributos no utilizados.

## Impacto potencial en el rendimiento

Configurar muchas **atributos del producto** aumenta el tamaño de la plantilla de producto de cada producto (estructura EAV) y la cantidad de datos que deben recuperarse. Este aumento afecta a las operaciones de las siguientes maneras:

- Aumento del tráfico de consultas SQL relacionado con la recuperación de datos EAV y la cantidad de datos procesados, lo que resulta en una disminución del rendimiento de la base de datos
- Aumento significativo del tamaño de los índices de Adobe Commerce y del índice de búsqueda de texto completo
- Alcanzar límites duros de MySQL al crear un índice FLAT para plantillas de producto de gran tamaño y la incapacidad de usarlo

Los aumentos en los datos de productos y los tamaños de índice pueden afectar al rendimiento del sitio de las siguientes maneras:

- Se ha aumentado el tiempo de respuesta para la mayoría de los escenarios de tienda relacionados con la exploración del catálogo, la búsqueda (rápida y avanzada) y la navegación en capas.
- Las operaciones de administración de productos en el administrador se ralentizan significativamente, lo que puede llevar a tiempos de espera.
- La funcionalidad Acciones masivas del producto se puede bloquear.
- El tiempo de regeneración de índices para catálogos de tamaño medio y grande no se puede realizar diariamente debido a los largos tiempos de ejecución.

Configurar muchas **opciones de atributo** puede afectar al rendimiento del sitio de las siguientes maneras:

- Tiempos de solicitud y procesamiento largos en el detalle del producto (PDP) y en las páginas de categoría que contienen productos complejos.
- El tiempo de respuesta de las operaciones de guardado de productos de administración aumenta por encima de los objetivos de rendimiento óptimos.
- Aumento del tiempo de procesamiento del formulario de edición de producto.
- Cierre de compra lento.

## Información adicional

- [Información general sobre Atributos de producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Conjuntos de atributos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutoriales de personalización > Personalizar formulario de creación de productos](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)

