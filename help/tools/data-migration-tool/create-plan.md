---
title: Creación de un plan de migración de datos
description: Obtenga información sobre cómo crear un plan de migración de datos para actualizar de Magento 1 a Magento 2. Planifique y pruebe la migración para evitar problemas.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Creación de un plan de migración de datos

Para migrar correctamente y evitar problemas, debe planificar a fondo y probar la migración.

## Antes de comenzar: considere una actualización

La migración es un buen momento para realizar cambios importantes y preparar su sitio para el siguiente nivel de crecimiento. Considere si su nuevo sitio debe diseñarse con hardware adicional o con una topología más avanzada con mejores niveles de almacenamiento en caché.

## Paso 1: Revisar las extensiones del sitio actual

* ¿Qué extensiones ha instalado?

* ¿Ha identificado si necesita todas estas extensiones en su nuevo sitio? Puede haber otros antiguos que pueda eliminar de forma segura.

* ¿Ha determinado si existen versiones de Magento 2 de sus extensiones? Visite [Commerce Marketplace](https://commercemarketplace.adobe.com/) para encontrar las versiones más recientes o póngase en contacto con su proveedor de extensiones.

* ¿Qué recursos de base de datos de sus extensiones desea migrar?

## Paso 2: crear y preparar su tienda para la migración

* Configure un sistema de hardware de Magento 2 con una topología y un diseño que coincidan al menos con su sistema Magento 1 existente

* Instale Magento 2 (con todos los módulos de esta versión) y [!DNL Data Migration Tool] en un sistema que cumpla [los requisitos del sistema](../../installation/system-requirements.md)

* Personalice el código [!DNL Data Migration Tool] para omitir determinados datos (como páginas de CMS o reglas de ventas) o convertir personalizaciones durante la migración. Lea las [!DNL Data Migration Tool]especificaciones técnicas[ de ](technical-specification.md) para obtener más información acerca de cómo funciona la migración

## Paso 3: Ejecución en seco

Antes de iniciar la migración en el entorno de producción, siga todos los pasos de migración en el entorno de prueba.

En estas pruebas de migración, siga estos pasos:

* Copiar la tienda de Magento 1 en un servidor de ensayo

* Migrar completamente la tienda replicada de Magento 1 a Magento 2

* Pruebe exhaustivamente su nueva tienda

## Paso 4: Inicio de la migración

1. Asegúrese de que [!DNL Data Migration Tool] tenga acceso de red para conectarse a las bases de datos de Magento 1 y Magento 2. Abra los puertos correspondientes en el cortafuegos.

1. Detenga todas las actividades en el Panel de administración de Magento 1 (excepto Order Management), como el envío, la creación de facturas y las notas de abono. La lista de actividades permitidas se puede ampliar ajustando la configuración del modo Delta en [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >No reanude estas actividades hasta que su tienda de Magento 2 se active.

1. Recomendamos detener todos los trabajos cron de Magento 1.

   Si algunos trabajos deben ejecutarse durante la migración, asegúrese de que no creen ni modifiquen entidades de base de datos de formas que el modo Delta no pueda procesar.

   Por ejemplo, el trabajo cron `enterprise_salesarchive_archive_orders` mueve pedidos antiguos al archivo. La ejecución de este trabajo durante la migración es segura porque el modo Delta reconoce este trabajo y procesa correctamente los pedidos archivados.

1. Use [!DNL Data Migration Tool] para migrar configuraciones y sitios web.

1. Copie los archivos multimedia de Magento 1 en Magento 2.

   Copie estos archivos manualmente del directorio `magento1-root/media` a `magento2-root/pub/media`.

1. Use [!DNL Data Migration Tool] para copiar masivamente los datos de la base de datos de Magento 1 en la base de datos de Magento 2.

   Si algunas de las extensiones tienen datos que desea migrar, es posible que tenga que instalar estas extensiones adaptadas para Magento 2. Si las extensiones tienen una estructura diferente en la base de datos de Magento 2, utilice los archivos de asignación proporcionados con [!DNL Data Migration Tool].

1. Reindexe todos los indexadores de Magento 2. Para obtener más información, consulte [Administrar indexadores](../../configuration/cli/manage-indexers.md) en la _Guía de configuración_.

## Paso 5: Realice cambios en los datos migrados (si es necesario)

A veces, es posible que desee tener su tienda Magento 2 con diferentes estructuras de catálogo, reglas de ventas y páginas de CMS después de la migración.

Es importante tener cuidado al trabajar con cambios manuales en los datos. Los errores crean errores en el paso de migración de datos incremental que sigue.

Por ejemplo, un producto eliminado de Magento 2: el que se ha comprado en su tienda Magento 1 activa y que ya no está disponible en su tienda Magento 2. La transferencia de datos acerca de dicha compra podría causar un error al ejecutar [!DNL Data Migration Tool] en modo Delta.

## Paso 6: Actualización de datos incrementales

Después de migrar los datos, utilice el modo Delta para capturar y transferir actualizaciones incrementales de Magento 1 (como nuevos pedidos, revisiones y cambios de perfil del cliente) a Magento 2.

* Inicie la migración incremental; las actualizaciones se ejecutan continuamente. Puede detener la transferencia de actualizaciones en cualquier momento pulsando `Ctrl+C`.

* Pruebe el sitio de Magento 2 durante este tiempo para detectar cualquier problema lo antes posible. Si tiene problemas, presione `Ctrl+C` para detener la migración incremental y reiniciarla después de resolver los problemas.

>[!NOTE]
>
>Pueden aparecer advertencias de comprobación de volumen en caso de que realice pruebas del sitio de Magento 2 y ejecute el proceso de migración al mismo tiempo. Esto sucede porque en Magento 2 se crean entidades que no existen en Magento 1.

## Paso 7: Publicación

Una vez que el sitio de Magento 2 se haya migrado completamente y funcione normalmente, complete el cambio:

1. Ponga su sistema Magento 1 en modo de mantenimiento (DOWNTIME STARTS).

1. Presione Control+C en la ventana de comandos de la herramienta de migración para detener las actualizaciones incrementales.

1. Inicie sus trabajos cron de Magento 2.

1. En el sistema Magento 2, vuelva a indexar el indexador de cotizaciones. Para obtener más información, consulte [Administrar indexadores](../../configuration/cli/manage-indexers.md) en la _Guía de configuración_.

1. Con una herramienta de su elección, visite las páginas de su sistema Magento 2 para almacenar en caché las páginas antes que los clientes que usen su tienda.

1. Realice cualquier verificación final del sitio de Magento 2.

1. Cambie el DNS, los equilibradores de carga, etc. para que apunten al nuevo hardware de producción (FIN DE TIEMPO DE INACTIVIDAD).

1. La tienda Magento 2 ya está lista para su uso. Usted y sus clientes pueden reanudar todas las actividades.
