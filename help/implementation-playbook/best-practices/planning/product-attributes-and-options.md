---
title: Prácticas recomendadas de configuración de atributos de producto
description: Obtenga información sobre cómo optimizar el rendimiento de Adobe Commerce limitando el número de atributos de producto, opciones de atributos y conjuntos de atributos
role: User, Admin
feature: Best Practices
feature-set: Commerce
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Prácticas recomendadas para la configuración de atributos del producto

- Para obtener el mejor rendimiento, no configure más del número máximo recomendado de atributos de producto u opciones de atributos de producto.

- **Atributos del producto**—
   - Para las versiones de Adobe Commerce 2.3.x y 2.4.0 a 2.4.1-p1, configure no más de 500 atributos
   - Para la versión 2.4.2 y posteriores de Adobe Commerce, configure hasta 1500 atributos de producto
- **Opciones de atributos del producto**-Configurar hasta 100 opciones de atributos para cada atributo
- **Conjuntos de atributos del producto**-Configurar un máximo de 1000 conjuntos de atributos _

>[!NOTE]
>
>Los atributos del producto especifican funciones que se aplican globalmente a todos los productos. Las opciones de atributos de producto son personalizaciones para especificar funciones que se aplican a productos específicos.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Reducción del número de atributos del producto

Para obtener el mejor rendimiento al administrar productos desde el administrador y al recuperar datos de productos en la tienda:

- Utilice diferentes plantillas de producto (conjuntos de atributos) para diferentes productos.
- Aproveche opciones personalizadas y productos complejos para la administración de variaciones
- Minimice el número de atributos en los que se puede buscar.
- Elimine las propiedades del producto que no utilice.
- Almacene y administre atributos no relacionados con el comercio en sistemas de administración de productos externos (PMS).

## Reducción del número de opciones de atributos de producto

Para obtener el mejor rendimiento al administrar productos desde el administrador y al recuperar datos de productos en la tienda:

- Utilice diferentes mecanismos de variación para crear productos: productos complejos y opciones personalizadas como fuente de variaciones de productos.
- Cree plantillas de producto específicas con atributos de segmentación y opciones para evitar plantillas de producto generalizadas y contenedores de opciones.
- Mantenga una lista de opciones de atributos reales.
- Administre la información del producto mediante un sistema de administración de productos (PMS) externo.

## Reducción del número de conjuntos de atributos del producto

Elimine los conjuntos de atributos de productos no utilizados mediante MySQL.

### Revisar configuración de conjunto de atributos

1. [Conexión a la base de datos del sitio](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Buscar el número de conjuntos de atributos usando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Elimine los conjuntos de atributos que no utilice.

## Impactos potenciales en el rendimiento

Configuración de varios **atributos del producto** aumenta el tamaño de la plantilla de producto para cada producto (estructura EAV) y la cantidad de datos que deben recuperarse. Este aumento afecta a las operaciones de las siguientes maneras:

- Aumento del tráfico de consultas SQL relacionado con la recuperación de datos EAV y la cantidad de datos procesados, lo que resulta en un menor rendimiento de la base de datos
- Aumento significativo del tamaño de los índices Adobe Commerce y del índice de búsqueda de texto completo
- Alcanzar límites duros de MySQL al crear un índice FLAT para plantillas de productos de gran tamaño e incapacidad para usarlo

El aumento de los datos de productos y de los tamaños de los índices puede afectar al rendimiento del sitio de las siguientes maneras:

- Mayor tiempo de respuesta para la mayoría de los escenarios de tienda relacionados con la navegación por catálogo, la búsqueda (rápida y avanzada) y la navegación por capas.
- Las operaciones de administración de productos en el administrador se ralentizan significativamente, lo que puede provocar tiempos de espera.
- La funcionalidad Acciones masivas de productos se puede bloquear.
- El tiempo de reconstrucción de índices para catálogos de tamaño medio y grande no se puede realizar diariamente debido a los largos tiempos de ejecución.

Configuración de varios **opciones de atributo** puede afectar al rendimiento del sitio de las siguientes maneras:

- Tiempos de solicitud y procesamiento largos en las páginas de detalles del producto (PDP) y de categorías que contienen productos complejos.
- El tiempo de respuesta de las operaciones de guardado del producto del administrador aumenta por encima de los objetivos de rendimiento óptimos.
- Aumento en el tiempo de procesamiento del formulario de edición de productos.
- Cierre de compra lento.

## Información adicional

- [Información general sobre atributos del producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Conjuntos de atributos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Crear un producto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Tutoriales de personalización > Personalizar formulario de creación de productos](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
