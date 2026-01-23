---
title: Funcionamiento de la migración de datos
description: Obtenga información acerca del proceso de migración de datos entre Magento 1 y Magento 2, incluida la terminología, los diagramas de flujo de trabajo y los pasos.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Funcionamiento de la migración de datos

Este tema proporciona información general de alto nivel sobre cómo se migran los datos de Magento 1 a Magento 2 mediante [!DNL Data Migration Tool].

[!DNL Data Migration Tool] es una herramienta de interfaz de línea de comandos (CLI) utilizada para transferir datos de Magento 1 a Magento 2. La herramienta comprueba la coherencia entre las estructuras de base de datos (tablas y campos) de Magento 1 y 2, rastrea el progreso de la transferencia de datos, crea registros y ejecuta pruebas de verificación de datos.

## Terminología

* **Modos**: un conjunto ordenado de operaciones para migrar datos de Magento 1.x a Magento 2.x.
* **Pasos**: las tareas de un modo que definen los tipos de datos que se migrarán.
* **Fases**: las tareas del paso que validan, transfieren y verifican los datos.
* **Archivos de mapa**: archivos XML que definen las reglas y conexiones entre las estructuras de datos de Magento 1.x y Magento 2.x para completar las fases.

## Modos

[!DNL Data Migration Tool] divide el proceso de migración en tres fases o *modos* para transferir y adaptar los datos de Magento 1.x a Magento 2.x. Los tres modos se enumeran aquí y deben ejecutarse en este orden:

1. **Modo de configuración**: migra la configuración del sistema y las opciones relacionadas con el sitio web.
1. **Modo de datos**: migra los recursos de la base de datos de forma masiva.
1. **Modo Delta**: migra cambios incrementales (cambios desde la última ejecución), como nuevos clientes y pedidos.

![Modos de migración](../../assets/data-migration/MigrationModes2.png)

## Pasos

[!DNL Data Migration Tool] usa una lista de *pasos* dentro de cada modo para migrar un tipo particular de datos. Por ejemplo, en el modo de Configuración, se siguen dos pasos para migrar todos los datos de configuración: el paso Tiendas y el paso Configuración. Encontrará detalles sobre los datos específicos que se migran en cada uno de estos pasos (y para los pasos de los demás modos) en la [[!DNL Data Migration Tool] especificación técnica](technical-specification.md).

![Información general de migración](../../assets/data-migration/MigrationOverview2.png)

## Fases

En cada paso hay tres *etapas* que siempre se ejecutan en este orden para garantizar que los datos se migren correctamente:

1. **Comprobación de integridad**: Compara los nombres de los campos de tabla, los tipos y otra información para comprobar la compatibilidad entre las estructuras de datos de Magento 1 y 2.
1. **Transferencia de datos**: transfiere la tabla de datos por tabla desde Magento 1 y 2.
1. **Comprobación de volumen**: Compara el número de registros entre tablas para comprobar que la transferencia se realizó correctamente.

![Fases de migración](../../assets/data-migration/MigrationSteps2.png)

## Asignar archivos

En el nivel inferior de los procesos de migración se encuentran los *archivos de asignación* XML. [!DNL Data Migration Tool] utiliza archivos de asignación en las fases de un paso para transformar distintas estructuras de datos entre las tablas Magento 1.x y 2.x.

Por ejemplo, cuando se transforman datos de una base de datos de Magento Open Source 1.8.0.0 a Magento Open Source 2.x.x, el archivo de asignación tiene en cuenta el hecho de que se ha cambiado el nombre de una tabla y cambia el nombre en consecuencia en la base de datos de destino. Si no hay diferencias en la estructura de datos o el formato de datos, [!DNL Data Migration Tool] lo transfiere tal cual, incluidos los datos de tablas creadas por extensiones, a la base de datos de Magento 2.

Cuando no se declaran diferencias en los archivos de asignación, [!DNL Data Migration Tool] muestra un error y no se inicia.

Los archivos de asignación se describen con más detalle en [[!DNL Data Migration Tool] Technical Specification].

## Diagrama de flujo de migración

![Flujo de migración](../../assets/data-migration/migration_flow.png)

[Especificación técnica de [!DNL Data Migration Tool]](technical-specification.md)

Nos complace que esté considerando pasar de la plataforma de comercio #1 del mundo, Magento 1.x, a la plataforma del futuro, Magento 2. Nos complace compartir los detalles sobre este proceso, al que nos referimos como migración.

## Componentes de migración

La migración a Magento 2 implica cuatro componentes: datos, extensiones y código personalizado, temáticas y personalizaciones.

### Datos

Hemos desarrollado **Magento 2[!DNL Data Migration Tool]** para ayudarle a mover con eficacia todos sus productos, clientes, datos de pedidos, configuraciones de tienda, promociones y mucho más a Magento 2. Esta guía proporciona información sobre la herramienta y las prácticas recomendadas para utilizarla con el fin de migrar los datos.

### Extensiones y código personalizado

Hemos estado trabajando duro con la comunidad de desarrollo para ayudarle a utilizar sus extensiones de Magento 1 en Magento 2. Ahora nos enorgullece presentar [Commerce Marketplace](https://commercemarketplace.adobe.com//), donde podrá descargar o adquirir las versiones más recientes de sus extensiones favoritas.

Encontrará más información sobre el desarrollo de extensiones para Magento 2 en [PHP Developer Guide](https://developer.adobe.com/commerce/php/development/).

### Temas y personalizaciones

Magento 2 utiliza nuevos enfoques y tecnologías que ofrecen a los comerciantes una capacidad inigualable para crear experiencias de compra innovadoras y escalarlas a nuevos niveles. Para aprovechar estos avances, los desarrolladores deben realizar cambios en sus temáticas y personalizaciones. La documentación está disponible en línea para crear [temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [diseños](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) y [personalizaciones](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/) de Magento 2.

## Esfuerzos de migración

Al igual que una actualización entre las versiones 1.x (por ejemplo, de la v1.12 a la v1.14), el nivel de esfuerzo para migrar de Magento 1 a Magento 2 depende de cómo haya creado el sitio y su nivel de personalización.
Sin embargo, estamos mejorando constantemente [!DNL Data Migration Tool] (vea el [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) para obtener más información); por lo que los esfuerzos de migración disminuyen continuamente.
