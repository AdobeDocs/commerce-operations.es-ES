---
title: Solución de rendimiento de la base de datos dividida
description: Obtenga más información sobre la solución de división de bases de datos para Adobe Commerce y Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Descripción general de la solución de base de datos dividida

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce ofrece varias ventajas de escalabilidad, incluida la capacidad de utilizar tres bases de datos maestras independientes para diferentes áreas funcionales de la aplicación Commerce.

Los datos de cierre de compra, pedidos y productos pueden utilizar una base de datos maestra independiente que se puede duplicar opcionalmente. Esta separación escala de forma independiente la carga desde los cierres de compra del sitio web, las actividades de administración de pedidos, la navegación por sitios web y las actividades de comercialización, según sus necesidades. Estos cambios proporcionan una flexibilidad considerable en la forma de escalar el nivel de la base de datos.

>[!INFO]
>
>Adobe Commerce en la infraestructura de nube sí _not_ admiten esta función.

La variable `ResourceConnections` proporciona la conexión unificada de la base de datos MySQL a la aplicación Commerce. Para las consultas a las bases de datos maestras, implementamos el patrón de base de datos de Segmentación de Responsabilidad de Consulta de Comandos (CQRS). Este patrón gestiona la lógica para enrutar las consultas de lectura y escritura a las bases de datos adecuadas. Los desarrolladores no necesitan saber qué configuración se está utilizando y no hay conexiones de base de datos de lectura y escritura independientes.

Si configura la replicación opcional de la base de datos, obtendrá las siguientes ventajas:

- Copia de seguridad de datos
- Análisis de datos sin afectar a la base de datos maestra
- Escalabilidad

Las bases de datos MySQL se replican asincrónicamente, lo que significa que los esclavos no necesitan estar conectados permanentemente para recibir actualizaciones del maestro.

La siguiente figura muestra cómo funciona esta función.

![Adobe Commerce utiliza diferentes bases de datos para almacenar tablas](../../assets/configuration/split-db-diagram-ee.png)

En Magento Open Source, solo se utiliza una base de datos maestra.

Adobe Commerce utiliza tres bases de datos maestras y un número configurable de bases de datos esclavas para la replicación. Adobe Commerce tiene una interfaz única para conexiones a bases de datos, lo que da como resultado un rendimiento más rápido y una mejor escalabilidad.

## Opciones de configuración

Debido al modo en que se diseña la solución de rendimiento de la base de datos dividida, su código personalizado y los componentes instalados _cannot_ realice una de las acciones siguientes:

- Escribir directamente en la base de datos (en su lugar, debe utilizar la interfaz de la base de datos de Adobe Commerce)
- Utilice JOIN que afecten a las ventas o [comillas](https://glossary.magento.com/quote) bases de datos
- Utilice claves externas para tablas en las bases de datos principales, ventas o cierre de compra

>[!WARNING]
>
>Póngase en contacto con los desarrolladores de componentes para comprobar si sus componentes realizan alguna de las acciones anteriores. Si es así, debe elegir solo una de las siguientes opciones:
>
>- Pida a los desarrolladores de componentes que actualicen sus componentes.
>- Utilice los componentes tal cual _without_ la solución de base de datos dividida.
>- Elimine los componentes para poder utilizar la solución de base de datos dividida.


Esto también significa que puede:

- Configuración de la solución de base de datos dividida _before_ poner Comercio en producción.

   Adobe recomienda configurar bases de datos divididas lo antes posible después de instalar el software Commerce.

- [Configuración manual](multi-master-manual.md) la solución de base de datos dividida.

   Debe realizar esta tarea si ya tiene componentes instalados o si Commerce ya está en producción. (_No_ actualizar un sistema de producción; realice las actualizaciones en un sistema de desarrollo y sincronice los cambios después de probarlos).

   >[!WARNING]
   >
   >Debe realizar una copia de seguridad de las dos instancias de base de datos adicionales manualmente. Commerce realiza una copia de seguridad solo de la instancia de base de datos principal. La variable [`magento setup:backup --db`](../../installation/tutorials/backup.md) las opciones de comando y administración no hacen una copia de seguridad de las tablas adicionales.

## Requisitos previos

La base de datos dividida requiere que configure tres bases de datos maestras de MySQL en cualquier host (las tres en el servidor de comercio, cada base de datos en un servidor separado, etc.). Estos son los _maestro_ y se utilizan de la siguiente manera:

- Una base de datos maestra para [cierre de compra](https://glossary.magento.com/checkout) tablas
- Una base de datos maestra para tablas de ventas (también denominada _Sistema de gestión de pedidos_ o _OMS_, tablas)
- Una base de datos maestra para el resto de las tablas de la aplicación Commerce 2

Además, puede configurar cualquier número de _esclavo_ bases de datos que sirven como equilibradores de carga y backups.

Esta guía explica cómo configurar las bases de datos maestras únicamente. Proporcionamos configuraciones de muestra y referencias para que usted configure bases de datos esclavas si lo desea.

En esta guía, se nombra a las tres bases de datos maestras:

- `magento_quote`
- `magento_sales`
- `magento`

(Puede nombrar sus bases de datos como desee).
