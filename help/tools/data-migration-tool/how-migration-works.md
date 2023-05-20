---
title: Funcionamiento de la migración de datos
description: Obtenga información acerca del proceso de migración de datos entre el Magento 1 y el Magento 2, incluida la terminología, los diagramas de flujo de trabajo y los pasos.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Funcionamiento de la migración de datos

En este tema se proporciona información general de alto nivel sobre cómo se migran los datos del Magento 1 al Magento 2 utilizando [!DNL Data Migration Tool].

El [!DNL Data Migration Tool] es una herramienta de interfaz de línea de comandos (CLI) utilizada para transferir datos del Magento 1 al Magento 2. La herramienta comprueba la coherencia entre las estructuras de base de datos del Magento 1 y 2 (tablas y campos), rastrea el progreso de la transferencia de datos, crea registros y ejecuta pruebas de verificación de datos.

## Terminología

* **Modos** : un conjunto ordenado de operaciones para migrar datos de Magento 1.x a Magento 2.x.
* **Pasos** : las tareas de un modo que definen los tipos de datos que se van a migrar.
* **Fases** : las tareas del paso que validan, transfieren y verifican los datos.
* **Asignar archivos** : archivos XML que definen las reglas y conexiones entre las estructuras de datos de Magento 1.x y Magento 2.x para completar las fases.

## Modos

El [!DNL Data Migration Tool] divide el proceso de migración en tres fases o *modos* para transferir y adaptar datos de Magento 1.x a Magento 2.x. Los tres modos se enumeran aquí y deben ejecutarse en este orden:

1. **Modo de configuración**: migra la configuración del sistema y la configuración relacionada con el sitio web.
1. **Modo de datos**: migra los recursos de la base de datos de forma masiva.
1. **Modo Delta**: migra cambios incrementales (cambios desde la última ejecución), como nuevos clientes y pedidos.

![Modos de migración](../../assets/data-migration/MigrationModes2.png)

## Pasos

El [!DNL Data Migration Tool] utiliza una lista de *pasos* dentro de cada modo para migrar un tipo concreto de datos. Por ejemplo, en el modo de Configuración, se siguen dos pasos para migrar todos los datos de configuración: el paso Tiendas y el paso Configuración. Encontrará detalles sobre los datos específicos que se migran en cada uno de estos pasos (y para los pasos en los demás modos) en la [[!DNL Data Migration Tool] Especificaciones técnicas](technical-specification.md).

![Resumen de migración](../../assets/data-migration/MigrationOverview2.png)

## Fases

Dentro de cada paso hay tres *etapas* que siempre se ejecutan con este fin para garantizar que los datos se migran correctamente:

1. **Comprobación de integridad**: compara los nombres de campo de tabla, los tipos y otra información para comprobar la compatibilidad entre las estructuras de datos del Magento 1 y 2.
1. **Transferencia de datos**: transfiere la tabla de datos por tabla desde el Magento 1 y 2.
1. **Comprobación del volumen**: Compara el número de registros entre tablas para comprobar que la transferencia se realizó correctamente.

![Fases de migración](../../assets/data-migration/MigrationSteps2.png)

## Asignar archivos

En el nivel más bajo de los procesos de migración se encuentra XML *asignar archivos*. El [!DNL Data Migration Tool] utiliza archivos de mapa dentro de las fases de un paso para transformar diferentes estructuras de datos entre las tablas de Magento 1.x y 2.x.

Por ejemplo, cuando se transforman datos de una base de datos de Magento Open Source 1.8.0.0 a Magento Open Source 2.x.x, el archivo de asignación tiene en cuenta el hecho de que se ha cambiado el nombre de una tabla y, en consecuencia, se cambia el nombre en la base de datos de destino. Si no hay diferencias en la estructura o el formato de datos, la variable [!DNL Data Migration Tool] lo transfiere tal cual, incluidos los datos de tablas creadas por extensiones, a la base de datos de Magento 2.

Cuando no se declaran diferencias en los archivos de mapa, la variable [!DNL Data Migration Tool] muestra un error y no se inicia.

Los archivos de asignación se analizan con más detalle en [[!DNL Data Migration Tool] Especificaciones técnicas].

## Diagrama de flujo de migración

![Flujo de migración](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Especificaciones técnicas](technical-specification.md)

Nos complace que esté considerando pasar de la plataforma de comercio #1 del mundo, Magento 1.x, a la plataforma del futuro, Magento 2. Nos complace compartir los detalles sobre este proceso, al que nos referimos como migración.

## Componentes de migración

La migración a Magento 2 implica cuatro componentes: datos, extensiones y código personalizado, temáticas y personalizaciones.

### Datos

Hemos desarrollado el **MAGENTO 2[!DNL Data Migration Tool]** para ayudarle a trasladar de forma eficaz todos sus productos, clientes y datos de pedidos, configuraciones de tienda, promociones y mucho más a Magento 2. Esta guía proporciona información sobre la herramienta y las prácticas recomendadas para utilizarla con el fin de migrar los datos.

### Extensiones y código personalizado

Hemos trabajado duro con la comunidad de desarrollo para ayudarle a utilizar las extensiones de Magento 1 en Magento 2. Ahora estamos orgullosos de presentar el [Commerce Marketplace](https://marketplace.magento.com/), donde puede descargar o adquirir las versiones más recientes de sus extensiones favoritas.

Encontrará más información sobre el desarrollo de extensiones para Magento 2 en la [Guía para desarrolladores de PHP](https://developer.adobe.com/commerce/php/development/).

### Temas y personalizaciones

Magento 2 utiliza nuevos enfoques y tecnologías que ofrecen a los comerciantes una capacidad inigualable para crear experiencias de compra innovadoras y escalarlas a nuevos niveles. Para aprovechar estos avances, los desarrolladores deben realizar cambios en sus temáticas y personalizaciones. La documentación está disponible en línea para crear Magento 2 [temas](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [diseños](https://developer.adobe.com/commerce/frontend-core/guide/layouts/), y [personalizaciones](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Esfuerzos de migración

Al igual que una actualización entre las versiones 1.x (por ejemplo, de la v1.12 a la v1.14), el nivel de esfuerzo para migrar del Magento 1 al Magento 2 depende de cómo haya creado el sitio y de su nivel de personalización.
Sin embargo, estamos mejorando constantemente la [!DNL Data Migration Tool] (consulte la [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) para obtener más información); por lo tanto, los esfuerzos de migración disminuyen continuamente.
