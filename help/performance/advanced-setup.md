---
title: Configuración avanzada
description: Revise las prácticas recomendadas y las recomendaciones para sistemas de grandes empresas diseñados para procesar grandes volúmenes de datos.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# Configuración avanzada

[!DNL Commerce] es un producto altamente flexible y escalable que contiene soluciones para comerciantes de todos los tamaños. Esta sección trata sobre las prácticas recomendadas y las recomendaciones para la configuración de [!DNL Commerce] para trabajar con grandes cantidades de datos, cargas extremas y otros casos empresariales.

## Calibrar el rendimiento del índice

Cuando se trata de grandes cantidades de datos, la reindexación puede convertirse en un problema. El [!DNL Commerce] El equipo seleccionó los índices más cargados y habilitó la indexación por lotes, que le permite establecer una parte de los datos que se procesará en cada iteración. De este modo, el usuario puede ajustar el tamaño de los lotes en función del tipo y el tamaño de los datos de la base de datos.

Para administrar esta configuración, edite el `batchRowsCount` en el campo `di.xml` del módulo correspondiente. Los siguientes índices admiten esta función:

* Índice de productos de categorías (módulo de catálogo)
* Índice de precios (módulo de catálogo)
* Índice EAV (módulo de catálogo)
* Índice de Existencias (Módulo CatalogInventory)

Puede ajustar el rendimiento del indizador ajustando las variables de tamaño de agrupamiento de índices. Controla cuántas entidades procesa a la vez el indexador. En algunas situaciones, hemos visto disminuciones significativas en el tiempo de indexación.

Por ejemplo, si está ejecutando un perfil similar al medio B2B, puede anular el valor de configuración `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` y reemplace el valor predeterminado de `5000` hasta `1000`. Esto reduce el tiempo de indexación completo de 4 horas a 2 horas con un valor predeterminado [!DNL MySQL] configuración.

>[!NOTE]
>
>No se ha habilitado el agrupamiento para el indexador de reglas de catálogo. Los comerciantes con un gran número de reglas de catálogo deben ajustar su [!DNL MySQL] para optimizar el tiempo de indexación. En este caso, edite su [!DNL MySQL] El archivo de configuración y la asignación de más memoria a los valores de configuración TMP_TABLE_SIZE y MAX_HEAP_TABLE_SIZE (el valor predeterminado es 16 M para ambos) mejorarán el rendimiento de este indexador, pero resultarán en [!DNL MySQL] consumiendo más RAM.

### Limitar los grupos de clientes y los catálogos compartidos por sitios web

Un gran número de SKU de producto, sitios web, grupos de clientes o catálogos compartidos afectará al tiempo de ejecución de los indexadores de Precio de producto y Regla de catálogo. Esto se debe a que, de forma predeterminada, todos los sitios web se asignan a todos los grupos de clientes (catálogos compartidos).

Para reducir el tiempo de indexación, puede hacer lo siguiente [excluir ciertos sitios web de los grupos de clientes (catálogos compartidos)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Configuración de Redis

A veces, una instancia de Redis no es suficiente para servir solicitudes entrantes. Hay varias soluciones que podemos recomendar para hacer frente a esta situación.

Primero, [!DNL Commerce] permite configurar el almacenamiento en caché independiente para cada tipo de caché. Esto le permite instalar tantas instancias de Redis independientes como el número de tipos de caché registrados en Magento. En términos realistas, es posible que desee crear instancias de Redis para las cachés más utilizadas, como configuración, diseño y bloques.

Otra solución puede ser colocar la caché de configuración en el sistema de archivos y mover las otras cachés al servidor Redis. Con esta solución, necesita una herramienta independiente para invalidar de forma centralizada la caché de configuración en todos los nodos web.

También puede utilizar un clúster de Redis que realice operaciones de lectura y escritura paralelas con un número de nodos que aumenta automáticamente. [!DNL Commerce] no proporciona configuración para este caso, pero se puede iniciar con personalizaciones menores.

## Configuración de [!DNL RabbitMQ]

Adobe Commerce admite colas de mensajes implementadas mediante [!DNL RabbitMQ]. [!DNL Commerce] utiliza este servicio para ejecutar numerosas operaciones asincrónicas, incluidas las operaciones de catálogo B2B y las actualizaciones asincrónicas de existencias. Todas las interfaces para agregar más trabajos al servidor de trabajos se distribuyen con el producto y están disponibles para la implementación de lógica asincrónica personalizada en el ámbito de las extensiones de terceros. Al igual que con cualquier otra integración, [!DNL Commerce] proporciona un archivo de configuración de ejemplo para [!DNL RabbitMQ] que contiene todas las configuraciones recomendadas y está totalmente listo para el uso en producción.

## Dividir la base de datos

>[!WARNING]
>
>La función de base de datos dividida era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) en la versión 2.4.2 de Adobe Commerce. Consulte [Revertir de una base de datos dividida a una única base de datos](../configuration/storage/revert-split-database.md).

Adobe Commerce le permite configurar el almacenamiento escalable de la base de datos para satisfacer las necesidades de una empresa en crecimiento. Puede configurar tres bases de datos maestras independientes que sirven a dominios específicos:

* Base de datos principal (catálogo)
* Base de datos de extracción
* Base de Datos del Sistema Order Management (OMS)

Para configurar bases de datos adicionales, debe crear una base de datos vacía y ejecutar uno de los siguientes comandos:

Para la base de datos maestra de extracción

```bash
bin/magento setup:db-schema:split-quote
```

Para base de datos maestra de OMS

```bash
bin/magento setup:db-schema:split-sales
```

Estos comandos migran tablas de dominio específicas de la base de datos principal a una base de datos de dominio. También cambian el [!DNL Commerce] para permitir la conectividad correspondiente y restringir el procesamiento.

Al disponer de bases de datos independientes para el cierre de compra y Order Management, puede distribuir la carga entre los servidores de base de datos. Puede entregar más cierres de compra y procesar más pedidos por segundo sin afectar la disponibilidad del catálogo y otras operaciones. Recomendamos dividir las bases de datos por períodos de ventas flash o activas, o usarlas permanentemente para proyectos de alta carga natural. La migración de los datos actuales entre bases de datos debe ejecutarse bajo la supervisión del administrador del sistema.  No divida las bases de datos mientras esté en el modo de producción.

Además de las bases de datos maestras, [!DNL Commerce] permite configurar varias bases de datos esclavas (una para cada recurso de datos declarado en el sistema). Una base de datos esclava sirve como réplica completa de la base de datos principal o de una base de datos maestra de dominio. Se emite para operaciones de lectura en un recurso específico.

Puede agregar una base de datos esclava ejecutando el siguiente comando:

```bash
bin/magento setup:db-schema:add-slave
```

Este comando realiza cambios de configuración, pero no configura la replicación en sí. Esto debe hacerse manualmente.

Después de dividir la base de datos maestra y establecer las bases de datos esclavas, [!DNL Commerce] regula automáticamente las conexiones a una base de datos específica y toma decisiones basadas en el tipo de solicitud (POST, PUT, GET, etc.) y recurso de datos. If [!DNL Commerce] Para que sus extensiones realicen operaciones de escritura en una solicitud de GET, el sistema cambia automáticamente la conexión de base de datos esclava a maestra. Funciona del mismo modo con las bases de datos maestras: tan pronto como se trabaja con una tabla relacionada con la retirada, el sistema redirige todas las consultas a una base de datos específica. Mientras tanto, todas las consultas relacionadas con el catálogo irán a la base de datos principal.

Para obtener más información sobre la configuración y las ventajas de la configuración maestra/esclava múltiple, consulte
[Solución de rendimiento de base de datos dividida](../configuration/storage/multi-master.md).

## Proporcionar contenido multimedia

Magento no proporciona ninguna integración específica para ofrecer y entregar contenido multimedia. Todos los enfoques comunes se pueden utilizar juntos en Magento.

La forma más sencilla de ofrecer contenido multimedia es enviarlo y almacenarlo en caché en un [!DNL Varnish] servidor. Este método supone un sistema de archivos compartido para almacenar contenido multimedia o un servidor dedicado que señala a [!DNL Varnish].

Para entornos de carga media y alta, recomendamos utilizar servicios de red de distribución de contenido (CDN) como Fastly, Akamai y otros. Al trabajar con estos servicios, [!DNL Commerce] utiliza el método de extracción clásico para las actualizaciones de contenido. Debe configurar [!DNL Commerce] URL para trabajar con el servicio CDN correspondiente. Al mover contenido multimedia a una CDN, reducirá considerablemente la carga de las instancias.

## Configuración del almacenamiento de registros

El almacenamiento de registros y su influencia en otras operaciones de disco afectan a la disponibilidad de los nodos web, especialmente en situaciones de carga alta. Le recomendamos que minimice el registro si no lo necesita. También puede configurar el registro para que escriba en un sistema de almacenamiento independiente que tenga altas velocidades de acceso. Tenga en cuenta que cualquier cuello de botella en el acceso al almacenamiento del registro puede afectar directamente al procesamiento de las solicitudes entrantes que registran operaciones de escritura o lectura como parte de su flujo.
