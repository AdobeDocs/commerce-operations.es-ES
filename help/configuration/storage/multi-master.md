---
title: Solución de rendimiento de base de datos dividida
description: Obtenga información sobre la solución de base de datos dividida para Adobe Commerce y Magento Open Source.
exl-id: 922a9af7-2c46-4bf3-b1ad-d966f5564ec0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Información general sobre la solución de base de datos dividida

{{ee-only}}

{{deprecate-split-db}}

Adobe Commerce ofrece varias ventajas de escalabilidad, incluida la capacidad de utilizar tres bases de datos maestras independientes para diferentes áreas funcionales de la aplicación Commerce.

Los datos de cierres de compra, pedidos y productos pueden utilizar una base de datos maestra independiente que puede replicar de forma opcional. Esta separación puede escalar de forma independiente la carga de las cierres de compra de sitios web, las actividades de administración de pedidos, la navegación por sitios web y las actividades de comercialización, según sus necesidades. Estos cambios proporcionan una flexibilidad considerable en la forma de escalar el nivel de la base de datos.

>[!INFO]
>
>Adobe Commerce en la infraestructura en la nube sí _no_ admite esta función.

El `ResourceConnections` proporciona la conexión de base de datos MySQL unificada a la aplicación Commerce. Para las consultas a las bases de datos maestras, implementamos el patrón de base de datos Command Query Responsibility Segregation (CQRS). Este patrón administra la lógica para enrutar las consultas de lectura y escritura a las bases de datos adecuadas. Los desarrolladores no necesitan saber qué configuración se está utilizando y no hay conexiones de base de datos de lectura y escritura independientes.

Si configura la replicación opcional de bases de datos, obtendrá las siguientes ventajas:

- Backup de datos
- Análisis de datos sin afectar a la base de datos maestra
- Escalabilidad

Las bases de datos MySQL se replican de forma asíncrona, lo que significa que los esclavos no necesitan estar conectados permanentemente para recibir actualizaciones del maestro.

La siguiente figura muestra cómo funciona esta función.

![Adobe Commerce utiliza diferentes bases de datos para almacenar tablas](../../assets/configuration/split-db-diagram-ee.png)

En Magento Open Source, sólo se utiliza una base de datos maestra.

Adobe Commerce utiliza tres bases de datos maestras y un número configurable de bases de datos esclavas para la replicación. Adobe Commerce tiene una sola interfaz para conexiones de bases de datos, lo que da como resultado un rendimiento más rápido y una mejor escalabilidad.

## Opciones de configuración

Debido al diseño de la solución de rendimiento de la base de datos dividida, el código personalizado y los componentes instalados _no puede_ realice una de las acciones siguientes:

- Escribir directamente en la base de datos (en su lugar, debe utilizar la interfaz de base de datos de Adobe Commerce)
- Utilice combinaciones que afecten a las bases de datos de ofertas o ventas
- Utilice claves externas para guardar tablas en las bases de datos de pago, ventas o principales

>[!WARNING]
>
>Póngase en contacto con los desarrolladores de componentes para comprobar si sus componentes cumplen alguna de las acciones anteriores. Si es así, debe elegir solo una de las siguientes opciones:
>
>- Pida a los desarrolladores de componentes que actualicen sus componentes.
>- Usar los componentes tal cual _sin_ la solución split database.
>- Quite los componentes para poder utilizar la solución de base de datos dividida.


Esto también significa que puede:

- Configuración de la solución de base de datos dividida _antes_ poner Commerce en producción.

   Adobe recomienda configurar las bases de datos divididas lo antes posible después de instalar el software Commerce.

- [Configurar manualmente](multi-master-manual.md) la solución split database.

   Debe realizar esta tarea si ya ha instalado componentes o si Commerce ya está en producción. (_No hacer_ actualizar un sistema de producción; realizar las actualizaciones en un sistema de desarrollo y sincronizar los cambios después de probarlos.)

   >[!WARNING]
   >
   >Debe realizar una copia de seguridad de las dos instancias de base de datos adicionales manualmente. Commerce realiza una copia de seguridad solo de la instancia de base de datos principal. El [`magento setup:backup --db`](../../installation/tutorials/backup.md) Las opciones de comando y administración no hacen una copia de seguridad de las tablas adicionales.

## Requisitos previos

La base de datos dividida requiere que configure tres bases de datos maestras MySQL en cualquier host (las tres en el servidor de Commerce, cada base de datos en un servidor independiente, etc.). Estas son las _principal_ y se utilizan de la siguiente manera:

- Una base de datos maestra para tablas de cierre
- Una base de datos maestra para tablas de ventas (también denominada _Sistema de Order Management_, o _OMS_, tablas)
- Una base de datos maestra para el resto de las tablas de la aplicación Commerce 2

Además, si lo desea, puede configurar cualquier número de _esclavo_ que sirven como equilibradores de carga y copias de seguridad.

En esta guía se explica cómo configurar sólo las bases de datos maestras. Proporcionamos configuraciones y referencias de ejemplo para que pueda configurar bases de datos esclavas si lo desea.

En esta guía, las tres bases de datos maestras reciben el nombre:

- `magento_quote`
- `magento_sales`
- `magento`

(Puede asignar a las bases de datos cualquier nombre que desee.)
