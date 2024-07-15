---
title: Prácticas recomendadas de administración de catálogos
description: Conozca las recomendaciones para configurar los límites del carro de compras y los atributos del producto, enumerar la paginación, las opciones, las promociones y las variaciones.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# Prácticas recomendadas de administración de catálogos

Las prácticas recomendadas de administración del catálogo que se describen aquí abarcan una serie de problemas, entre los que se incluyen, entre otros:

- Límites del carro
- Límites de categoría
- Atributos del producto
- Paginación del listado de productos
- Opciones de producto
- Variaciones de productos
- Promociones

## Límites del carro

Para obtener el mejor rendimiento, utilice las siguientes directrices para administrar los límites del carro de compras para Adobe Commerce.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Reducir el número de elementos del carro de compras

Utilice las siguientes estrategias para administrar el número de elementos del carro de compras

- Divida los pedidos en varios pedidos más pequeños con un número menor de filas mediante la característica [!UICONTROL Add Item by SKU].
- Agregue únicamente la lógica personalizada y la personalización del carro de compras necesarias para cargar una lista de elementos.

## Límites de categoría

La configuración de un gran número de categorías puede afectar al rendimiento.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Reducción del número de productos

Utilice las siguientes estrategias para reducir el número de categorías:

- Administración de funciones de producto únicas mediante atributos y opciones personalizadas
- Eliminar categorías inactivas
- Optimizar la profundidad del catálogo en la navegación

## Atributos del producto

La configuración de demasiados atributos de producto u opciones de atributos de producto puede afectar al rendimiento.

>[!NOTE]
>
>Los atributos del producto especifican funciones que se aplican globalmente a todos los productos. Las opciones de atributos de producto son personalizaciones para especificar funciones que se aplican a productos específicos.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Reducción del número de atributos

Para obtener el mejor rendimiento al administrar productos desde el administrador y al recuperar datos de productos en la tienda:

- Utilice diferentes plantillas de producto (conjuntos de atributos) para diferentes productos.
- Aproveche opciones personalizadas y productos complejos para la administración de variaciones
- Minimice el número de atributos en los que se puede buscar.
- Elimine las propiedades del producto que no utilice.
- Almacene y administre atributos no relacionados con el comercio en sistemas de administración de productos externos (PMS).

### Reducción del número de opciones de atributos

Para obtener el mejor rendimiento al administrar productos desde el administrador y al recuperar datos de productos en la tienda:

- Utilice diferentes mecanismos de variación para crear productos: productos complejos y opciones personalizadas como fuente de variaciones de productos.
- Cree plantillas de producto específicas con atributos de segmentación y opciones para evitar plantillas de producto generalizadas y contenedores de opciones.
- Mantenga una lista de opciones de atributos reales.
- Administre la información del producto mediante un sistema de administración de productos (PMS) externo.

### Reducción del número de conjuntos de atributos

Elimine los conjuntos de atributos de productos no utilizados mediante MySQL.

#### Revisar configuración de conjunto de atributos

1. [Conectarse a la base de datos del sitio](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Buscar el número de conjuntos de atributos usando MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Elimine los conjuntos de atributos que no utilice.

### Impacto potencial en el rendimiento

Al configurar muchos **atributos de producto**, aumenta el tamaño de la plantilla de producto para cada producto (estructura EAV) y la cantidad de datos que se deben recuperar. Este aumento afecta a las operaciones de las siguientes maneras:

- Aumento del tráfico de consultas SQL relacionado con la recuperación de datos EAV y la cantidad de datos procesados, lo que resulta en un menor rendimiento de la base de datos
- Aumento significativo del tamaño de los índices Adobe Commerce y del índice de búsqueda de texto completo
- Alcanzar límites duros de MySQL al crear un índice FLAT para plantillas de productos de gran tamaño e incapacidad para usarlo

El aumento de los datos de productos y de los tamaños de los índices puede afectar al rendimiento del sitio de las siguientes maneras:

- Mayor tiempo de respuesta para la mayoría de los escenarios de tienda relacionados con la navegación por catálogo, la búsqueda (rápida y avanzada) y la navegación por capas.
- Las operaciones de administración de productos en el administrador se ralentizan significativamente, lo que puede provocar tiempos de espera.
- La funcionalidad Acciones masivas de productos se puede bloquear.
- El tiempo de reconstrucción de índices para catálogos de tamaño medio y grande no se puede realizar diariamente debido a los largos tiempos de ejecución.

Configurar muchas **opciones de atributos** puede afectar el rendimiento del sitio de las siguientes maneras:

- Tiempos de solicitud y procesamiento largos en las páginas de detalles del producto (PDP) y de categorías que contienen productos complejos.
- El tiempo de respuesta de las operaciones de guardado del producto del administrador aumenta por encima de los objetivos de rendimiento óptimos.
- Aumento en el tiempo de procesamiento del formulario de edición de productos.
- Cierre de compra lento.

## Opciones de producto

La configuración de demasiadas opciones de producto por producto puede afectar al rendimiento.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Reducción del número de opciones

Utilice las siguientes estrategias para reducir el número de opciones de producto por producto:

- Configure productos complejos y opciones personalizadas como fuente de variaciones de productos.
- En lugar de crear plantillas de producto globales y contenedores de opciones que se apliquen a todos los productos, utilice conjuntos de atributos para crear plantillas de producto específicas con atributos y opciones de destino.
- Administre la información del producto mediante un sistema de administración de productos (PMS) externo.

### Impacto potencial en el rendimiento

La configuración de muchas opciones de producto aumenta la cantidad de datos recuperados para cada producto en todas las operaciones de lectura y escritura, lo que da como resultado:

- El mayor tráfico de consultas SQL y las operaciones de `JOIN` más pesadas aumentan el rendimiento de la base de datos.
- Tamaño aumentado para los índices de Adobe Commerce y el índice de búsqueda de texto completo.

Los incrementos enumerados anteriormente pueden afectar al rendimiento del sitio de las siguientes maneras:

- Tiempo de respuesta más largo para la mayoría de los escenarios de tienda relacionados con productos que contienen muchas opciones en atributos.
- Aumento significativo del tiempo necesario para completar las operaciones de administración de productos en Admin que puede provocar tiempos de espera, especialmente para escenarios relacionados con la lista de atributos y la recuperación del árbol, incluida la administración de reglas de promoción.
- Puede bloquear las acciones masivas que completan operaciones masivas asincrónicas como la importación y exportación y la asignación de precios personalizados a varios productos en un catálogo compartido.

## Paginación del listado de productos

La visualización de demasiados productos por página puede afectar al rendimiento.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Actualizar la configuración de la lista de productos

Si tiene demasiados productos en una categoría, actualice la configuración del catálogo de tiendas para deshabilitar la opción a **Permitir todos los productos por página**.

Después de deshabilitar esta opción, Adobe Commerce usa los controles de paginación de tienda de listas de productos para administrar el número de productos que se muestran en los componentes de tienda. Para obtener instrucciones, consulte [Configurar controles de paginación](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## Límites de SKU de productos

La configuración de demasiados SKU de producto puede afectar al rendimiento al ralentizar la recuperación de datos del producto y aumentar el tiempo para completar las operaciones de administración o las indexaciones.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Reducción del número de productos

Utilice las siguientes estrategias para reducir el número de productos (SKU):

- Minimizar multiplicadores—
   - La consolidación de sitios web reduce el multiplicador.
   - Utilice funciones de producto alternativas para personalizar los precios y reemplazar los multiplicadores de catálogo compartido y de grupos de clientes.
   - Tanto los grupos de clientes como el catálogo compartido funcionan como multiplicadores del número de SKU efectivas en una tienda.
- Reestructurar el catálogo—
   - Reduzca el número de productos asignados a categorías.
   - Reduzca el número de SKU al reducir el número de sitios web, grupos de clientes, catálogos compartidos, número de productos o número de opciones de productos configurables
- Proporcione más variaciones de productos utilizando opciones personalizadas en lugar de crear productos separados.
- Teniendo en cuenta que un SKU efectivo podría incluir una serie de posibles permutaciones de precios, ya que los precios se pueden especificar de forma diferente para cada tienda o grupo de clientes.
- Desactive o elimine componentes del sistema no utilizados como módulos. Consulte [Desinstalar módulos](../../../installation/tutorials/uninstall-modules.md).
- Administre productos en un sistema de administración de plataformas (PMS) externo.

## Variaciones de productos

La configuración de demasiadas variaciones por producto puede afectar al rendimiento.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Reducción del número de variaciones

Para obtener el mejor rendimiento del sitio, utilice las siguientes estrategias para reducir el número de variaciones de productos:

- Reestructurar el catálogo distribuyendo el número de variaciones entre diferentes productos.
- Elimine las opciones de atributos configurables que no estén disponibles.
- Administre variaciones mediante funciones alternativas como opciones personalizadas, categorías, productos relacionados, agrupados y agrupados.

### Impacto potencial en el rendimiento

Exceder el número recomendado de variaciones de productos puede afectar al rendimiento del sitio de las siguientes maneras:

- Tiempos de solicitud y procesamiento largos en las páginas de detalles y categorías de productos que contienen productos complejos.
- Se ha aumentado el tiempo de respuesta para completar las operaciones de guardado en el administrador.
- Se ha aumentado el tiempo para procesar el formulario de edición de productos.
- Cierre de compra lento.

## Promociones

Siga estas prácticas recomendadas para configurar ventas y promociones de artículos en un carro de compras:

- **Reglas de ventas (reglas de precios del carro de compras)**
   - Administrar y eliminar reglas no utilizadas.
   - Añada condiciones de regla estrictas (como atributo o filtro de categoría) para lograr la coincidencia más eficaz.
- **Cupones**
   - Eliminar cupones no utilizados y caducados.
   - Genere solamente el número de cupones necesarios para cumplir los requisitos de la campaña.

### Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

### Impacto potencial en el rendimiento

Tener más del número máximo recomendado de reglas de precios de carro de compras o cupones puede afectar el rendimiento del sitio de las siguientes maneras:

- Se ha aumentado el tiempo de respuesta cuando se añaden productos al carro de compras.
- Se ha aumentado el tiempo para cargar y procesar la minicart.
- Tiempo aumentado para procesar la página del carro de compras.
- Se ha aumentado el tiempo para procesar el bloque **Totales** en la página Cierre de compra.
