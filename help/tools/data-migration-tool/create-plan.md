---
title: Crear un plan de migración de datos
description: Siga estos pasos para crear un plan de migración de datos que garantice una actualización correcta del Magento 1 al Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---


# Crear un plan de migración de datos

Para migrar correctamente y evitar problemas, debe planificar y probar la migración a fondo.

## Antes de comenzar: Tenga en cuenta la actualización

La migración es el momento perfecto para realizar cambios serios y preparar su sitio para el próximo nivel de crecimiento. Considere si su nuevo sitio necesita ser diseñado con más hardware o con una topología más avanzada con mejores niveles de almacenamiento en caché.

## Paso 1: Revisar extensiones de su sitio actual

* ¿Qué extensiones ha instalado?

* ¿Ha identificado si necesita todas estas extensiones en el nuevo sitio? Puede haber antiguos que puede eliminar con seguridad.

* ¿Ha determinado si existen versiones de Magento 2 de las extensiones? Visita [Commerce Marketplace] para buscar las versiones más recientes o póngase en contacto con el proveedor de extensiones.

* ¿Qué activos de base de datos de sus extensiones desea migrar?

## Paso 2: Cree y prepare su tienda para la migración

* Configure un sistema de hardware Magento 2 utilizando topología y diseño que al menos coincida con su sistema Magento 1 existente

* Instale el Magento 2.x (con todos los módulos de esta versión) y el [!DNL Data Migration Tool] en un sistema que cumpla la función [requisitos del sistema del Magento]

* Realice los ajustes personalizados en la variable [!DNL Data Migration Tool] en caso de que no necesite migrar algunos datos (como páginas de CMS o reglas de ventas) o desee convertir la personalización de su Magento durante la migración. Lea el [!DNL Data Migration Tool]&#39;s [Especificación técnica](technical-specification.md) para comprender mejor cómo funciona la migración desde adentro

## Paso 3: Sequía

Antes de iniciar la migración en el entorno de producción, sería mejor seguir todos los pasos de migración en el entorno de prueba.

En estas pruebas de migración, siga estos pasos:

* Copiar el almacén de Magento 1 en un servidor de ensayo

* Migración completa del almacén de Magento 1 replicado al Magento 2

* Pruebe exhaustivamente la nueva tienda

## Paso 4: Inicie la migración

1. Asegúrese de que la variable [!DNL Data Migration Tool] tiene acceso a la red para conectarse a las bases de datos de Magento 1 y Magento 2. Abra los puertos correspondientes en el cortafuegos.

1. Detenga todas las actividades en el Panel de administración de Magento 1.x (excepto la administración de pedidos), como el envío, la creación de facturas y notas de crédito. La lista de actividades permitidas se puede ampliar ajustando la configuración del modo Delta en el [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >No debe reanudar estas actividades hasta que la tienda de Magento 2 entre en funcionamiento.

1. Se recomienda detener todos los trabajos cron de Magento 1.x.

   Sin embargo, si es necesario que algunos trabajos se ejecuten durante la migración, asegúrese de que no creen nuevas entidades de base de datos ni cambien las existentes de la forma en que el modo Delta no puede procesar dichas entidades.

   Por ejemplo, la variable `enterprise_salesarchive_archive_orders` el trabajo cron mueve los pedidos antiguos al archivo. La ejecución de este trabajo durante la migración es segura porque el modo Delta reconoce este trabajo y procesa correctamente los pedidos archivados.

1. Utilice la variable [!DNL Data Migration Tool] para migrar la configuración y los sitios web.

1. Copie los archivos multimedia de Magento 1.x en Magento 2.x.

   Debe copiar estos archivos manualmente desde el `magento1-root/media` de `magento2-root/pub/media`.

1. Utilice la variable [!DNL Data Migration Tool] para copiar de forma masiva los datos de la base de datos de Magento 1 a la base de datos de Magento 2.

   Si algunas de las extensiones tienen datos que desea migrar, es posible que tenga que instalar estas extensiones adaptadas para el Magento 2. Si las extensiones tienen una estructura diferente en la base de datos de Magento 2, utilice los archivos de asignación proporcionados con la variable [!DNL Data Migration Tool].

1. Reindexe todos los indexadores Magento 2.x. Para obtener más información, consulte la [Guía de configuración].

## Paso 5: Realizar cambios en los datos migrados (si es necesario)

A veces, es posible que desee que su tienda Magento 2 tenga una estructura de catálogo, reglas de ventas y páginas CMS diferentes después de la migración.

Es importante tener cuidado al trabajar mediante cambios manuales en los datos. Los errores crean errores en el paso de migración de datos incremental que sigue.

Por ejemplo, un producto eliminado del Magento 2: el que se ha comprado en su tienda Magento 1 en directo y que ya no está disponible en su tienda Magento 2. La transferencia de datos sobre dicha compra podría causar un error al ejecutar el [!DNL Data Migration Tool] en modo Delta.

## Paso 6: Actualización de datos incrementales

Después de migrar los datos, debe capturar de forma incremental las actualizaciones de datos que se han agregado en el almacén de Magento 1 (como nuevos pedidos, revisiones y cambios en los perfiles de los clientes) y transferir estas actualizaciones al almacén de Magento 2 mediante el modo Delta.

* Inicie la migración incremental; las actualizaciones se ejecutan de forma continua. Puede detener la transferencia de actualizaciones en cualquier momento presionando `Ctrl+C`.

* Pruebe el sitio de Magento 2 durante este tiempo para detectar cualquier problema lo antes posible. Si tiene problemas, presione `Ctrl+C` para detener la migración incremental y volver a iniciarla después de resolver los problemas.

>[!NOTE]
>
>Pueden aparecer advertencias de comprobación de volumen en caso de que realice pruebas del sitio de Magento 2 y ejecute el proceso de migración al mismo tiempo. Esto sucede porque en el Magento 2 se crean entidades que no existen en la instancia del Magento 1.

## Paso 7: Go live

Ahora que su sitio de Magento 2 está actualizado con el Magento 1 y funciona normalmente, haga lo siguiente para cortar en el nuevo sitio:

1. Ponga su sistema Magento 1 en modo de mantenimiento (INICIO DE DOWNTIME).

1. Pulse Control+C en la ventana de comandos de la herramienta de migración para detener las actualizaciones incrementales.

1. Inicie sus trabajos cron de Magento 2.

1. En su sistema Magento 2, reindexe el indizador de existencias. Para obtener más información, consulte la [Guía de configuración].

1. Con la herramienta que elija, visite las páginas del sistema de Magento 2 para almacenar en caché las páginas antes que los clientes que usen la tienda.

1. Realice cualquier verificación final del sitio del Magento 2.

1. Cambie DNS, equilibradores de carga, etc. para que apunten al nuevo hardware de producción (DOWNTIME ENDS).

1. La tienda de Magento 2 ya está lista para su uso. Usted y sus clientes pueden reanudar todas las actividades.

<!-- LINK ADDRESSES -->
[requisitos del sistema del Magento]: ../../installation/system-requirements.md
[Commerce Marketplace]: https://marketplace.magento.com
[Guía de configuración]: ../../configuration/cli/manage-indexers.md
