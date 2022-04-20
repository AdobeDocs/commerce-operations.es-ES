---
title: Configuración avanzada
description: Revise las prácticas recomendadas y recomendaciones para los sistemas empresariales grandes diseñados para procesar grandes volúmenes de datos.
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 0%

---


# Configuración avanzada

[!DNL Commerce] es un producto altamente flexible y escalable que contiene soluciones para comerciantes de todos los tamaños. Esta sección trata las prácticas recomendadas y recomendaciones sobre la configuración [!DNL Commerce] para trabajar con grandes cantidades de datos, cargas extremas y otros casos empresariales.

## Calibrar el rendimiento del índice

Cuando se trata de grandes cantidades de datos, la reindexación puede convertirse en un problema. La variable [!DNL Commerce] El equipo seleccionó los índices más cargados y habilitó la indexación por lotes, lo que le permite establecer una parte de los datos que se procesarán en cada iteración. De este modo, el usuario puede ajustar el tamaño de los lotes en función del tipo y el tamaño de los datos de la base de datos.

Para administrar esta configuración, edite la `batchRowsCount` en el `di.xml` del módulo correspondiente. Los siguientes índices admiten esta función:

* Índice de productos de categoría (módulo de catálogo)
* Índice de precios (Módulo de catálogo)
* Índice EAV (módulo catálogo)
* Índice de stock (Módulo CatalogInventory)

Puede ajustar el rendimiento del indizador ajustando las variables de tamaño del agrupamiento de índices. Esto controla cuántas entidades procesa el indizador a la vez. En algunas situaciones, hemos visto disminuciones significativas en el tiempo de indexación.

Por ejemplo, si está ejecutando un perfil similar a B2B Medium, puede anular el valor de configuración `batchRowsCount` en `app/code/Magento/catalog/etc/di.xml` y anulan el valor predeterminado de `5000` a `1000`. Esto reduce el tiempo de indexación completo de 4 horas a 2 horas con un valor predeterminado [!DNL MySQL] configuración.

>[!NOTE]
>
>No se ha habilitado el agrupamiento para el indexador de reglas de catálogo. Los comerciantes con un gran número de reglas de catálogo deben ajustar su [!DNL MySQL] para optimizar el tiempo de indexación. En este caso, la edición de [!DNL MySQL] y la asignación de más memoria a los valores de configuración TMP_TABLE_SIZE y MAX_HEAP_TABLE_SIZE (el valor predeterminado es 16M para ambos) mejorará el rendimiento de este indexador, pero dará como resultado [!DNL MySQL] consume más RAM.

### Limitar grupos de clientes y catálogos compartidos por sitios web

Un gran número de SKU de producto, sitios web, grupos de clientes o catálogos compartidos afectará al tiempo de ejecución de los indexadores de precios de producto y reglas de catálogo. Esto se debe a que, de forma predeterminada, todos los sitios web se asignan a todos los grupos de clientes (catálogos compartidos).

Para reducir el tiempo de indexación, puede [excluir determinados sitios web de grupos de clientes (catálogos compartidos)](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexer-optimization.html#customer-group-limitations-by-websites).

## Configuración de Redis

A veces, una instancia de Redis no es suficiente para servir solicitudes entrantes. Hay varias soluciones que podemos recomendar para abordar esta situación.

Primero, [!DNL Commerce] permite configurar almacenamiento de caché independiente para cada tipo de caché. Esto le permite instalar tantas instancias de Redis independientes como el número de tipos de caché registrados en el Magento. En términos realistas, es posible que desee instancias de Redis para las cachés más utilizadas, como la configuración, el diseño y los bloques.

Otra solución puede ser colocar la caché de configuración en el sistema de archivos y mover las otras cachés al servidor de Redis. Con esta solución, necesita una herramienta independiente para la invalidación centralizada de la caché de configuración en todos los nodos web.

También puede utilizar un clúster de Redis que realice operaciones paralelas de lectura y escritura con un número de nodos que aumente automáticamente. [!DNL Commerce] no proporciona configuración para este caso, pero se puede iniciar con personalizaciones menores.

## Configuración [!DNL RabbitMQ]

Magento Open Source y Adobe [!DNL Commerce] cola de mensajes de asistencia implementada a través de [!DNL RabbitMQ]. [!DNL Commerce] utiliza este servicio para ejecutar numerosas operaciones asincrónicas, incluidas las operaciones del catálogo B2B y las actualizaciones de existencias asincrónicas. Todas las interfaces para agregar más trabajos al servidor de trabajos se distribuyen con el producto y están disponibles para la implementación de lógica asíncrona personalizada en el ámbito de extensiones de terceros. Como con cualquier otra integración, [!DNL Commerce] proporciona un archivo de configuración de ejemplo para [!DNL RabbitMQ] que contiene todos los ajustes recomendados y está totalmente listo para el uso de producción.

## Dividir la base de datos

>[!WARNING]
>
>La función de base de datos dividida era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) en la versión 2.4.2 de Adobe Commerce. Consulte [Revertir de una base de datos dividida a una única base de datos](https://devdocs.magento.com/guides/v2.4/config-guide/revert-split-database.html).

Adobe Commerce le permite configurar el almacenamiento de base de datos escalable para satisfacer las necesidades de un negocio en crecimiento. Puede configurar tres bases de datos maestras independientes que sirven a dominios específicos:

* Base de datos principal (catálogo)
* Base de datos de cierre de compra
* Base de Datos del Sistema de Gestión de Pedidos (OMS)

Para configurar bases de datos adicionales, debe crear una base de datos vacía y ejecutar uno de los siguientes comandos:

Para la base de datos maestra de cierre de compra

```bash
bin/magento setup:db-schema:split-quote
```

Para OMS Master DB

```bash
bin/magento setup:db-schema:split-sales
```

Estos comandos migran las tablas de dominio específicas de la base de datos principal a una base de datos de dominio. También cambian el [!DNL Commerce] para permitir la conectividad correspondiente y el procesamiento de restricciones.

Al tener bases de datos separadas para cierre de compra y Gestión de pedidos, puede distribuir la carga entre los servidores de bases de datos. Puede servir más cierres de compra y procesar más pedidos por segundo sin afectar a la disponibilidad del catálogo y otras operaciones. Se recomienda dividir las bases de datos para periodos de ventas activas o flash, o usarlas de forma permanente para proyectos de carga alta de forma natural. La migración de los datos actuales entre bases de datos debe ejecutarse bajo la supervisión del administrador del sistema.  No divida las bases de datos mientras se encuentra en el modo Producción.

Además de las bases de datos maestras, [!DNL Commerce] permite configurar una serie de bases de datos esclavas (una para cada recurso de datos declarado en el sistema). Una base de datos esclava sirve como réplica completa de la base de datos principal o de una de las bases de datos maestras de dominios. Se publica para operaciones de lectura en un recurso específico.

Puede agregar una base de datos esclava ejecutando el siguiente comando:

```bash
bin/magento setup:db-schema:add-slave
```

Este comando realiza cambios de configuración, pero no configura la replicación en sí. Eso debe hacerse manualmente.

Después de dividir la base de datos maestra y establecer bases de datos esclavas, [!DNL Commerce] regula automáticamente las conexiones a una base de datos específica, tomando decisiones según el tipo de solicitud (POST, PUT, GET, etc.) y el recurso de datos. If [!DNL Commerce] o sus extensiones realizan operaciones de escritura en una solicitud de GET, el sistema cambia automáticamente la conexión de esclavo a base de datos maestra. Funciona del mismo modo con las bases de datos maestras: tan pronto como se trabaja con una tabla relacionada con el cierre de compra, el sistema redirige todas las consultas a una base de datos específica. Mientras tanto, todas las consultas relacionadas con el catálogo irán a la base de datos principal.

Para obtener más información sobre la configuración y las ventajas de la configuración maestra/esclava múltiple, consulte
[Solución de rendimiento de la base de datos dividida](https://devdocs.magento.com/guides/v2.4/config-guide/multi-master/multi-master.html).

## Servir contenido multimedia

Magento no proporciona ninguna integración específica para ofrecer y entregar contenido multimedia. Todos los enfoques comunes se pueden utilizar juntos en el Magento.

La forma más sencilla de servir contenido multimedia es entregarlo y almacenarlo en caché en un [!DNL Varnish] servidor. Este enfoque supone un sistema de archivos compartidos para almacenar contenido multimedia o un servidor dedicado que señala a [!DNL Varnish].

Para entornos de carga media y alta, recomendamos utilizar los servicios de Red de entrega de contenido (CDN) como FIENE, Akamai y otros. Al trabajar con estos servicios, [!DNL Commerce] utiliza el método de extracción clásico para las actualizaciones de contenido. Debe configurar [!DNL Commerce] URL para trabajar con el servicio CDN correspondiente. Al mover contenido multimedia a una CDN, se reducirá significativamente la carga en las instancias.

## Configurar el almacenamiento de registros

El almacenamiento de registros y su influencia en otras operaciones de disco afectan a la disponibilidad de los nodos web, especialmente en situaciones de alta carga. Se recomienda minimizar el registro si no lo necesita. También puede configurar el registro para que escriba en un sistema de almacenamiento independiente que tenga velocidades de acceso altas. Tenga en cuenta que cualquier cuello de botella en el acceso al almacenamiento de registros puede afectar directamente al procesamiento de las solicitudes entrantes que registran operaciones de escritura o lectura como parte de su flujo.
