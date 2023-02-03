---
title: Funcionamiento de la migración de datos
description: Obtenga información sobre el proceso de migración de datos entre el Magento 1 y el Magento 2, incluida la terminología, los diagramas de flujo de trabajo y los pasos.
source-git-commit: be2f924728853236bba786e7611b2a368c9f3054
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---


# Funcionamiento de la migración de datos

En este tema se ofrece una descripción general de alto nivel sobre cómo se migran los datos del Magento 1 al Magento 2 mediante la [!DNL Data Migration Tool].

La variable [!DNL Data Migration Tool] es una herramienta de interfaz de línea de comandos (CLI) que se utiliza para transferir datos del Magento 1 al Magento 2. La herramienta verifica la coherencia entre las estructuras de base de datos del Magento 1 y 2 (tablas y campos), rastrea el progreso de la transferencia de datos, crea registros y ejecuta pruebas de verificación de datos.

## Terminología

* **Modos** - un conjunto ordenado de operaciones para migrar datos del Magento 1.x al Magento 2.x.
* **Pasos** : las tareas en un modo que definen los tipos de datos que se van a migrar.
* **Etapas** : las tareas en el paso que validan, transfieren y verifican los datos.
* **Asignar archivos** : archivos XML que definen las reglas y conexiones entre las estructuras de datos de Magento 1.x y Magento 2.x para completar las fases.

## Modos

La variable [!DNL Data Migration Tool] divide el proceso de migración en tres fases o *modos* para transferir y adaptar los datos del Magento 1.x al Magento 2.x. Los tres modos se enumeran aquí y deben ejecutarse en este orden:

1. **Modo de configuración**: migra la configuración del sistema y los ajustes relacionados con el sitio web.
1. **Modo de datos**: migra recursos de base de datos de forma masiva.
1. **Modo Delta**: migra los cambios incrementales (cambios desde la última ejecución), como nuevos clientes y pedidos.

![Modos de migración](../../assets/data-migration/MigrationModes2.png)

## Pasos

La variable [!DNL Data Migration Tool] utiliza una lista de *pasos* en cada modo para migrar un tipo concreto de datos. Por ejemplo, en el modo Configuración , se siguen dos pasos para migrar todos los datos de configuración: el paso Almacenes y el paso Configuración . Los detalles sobre los datos específicos que se migran en cada uno de estos pasos (y para ver los pasos de los demás modos) se encuentran en la [[!DNL Data Migration Tool] Especificación técnica](technical-specification.md).

![Información general sobre migración](../../assets/data-migration/MigrationOverview2.png)

## Etapas

Dentro de cada paso hay tres *fases* que siempre se ejecutan para garantizar que los datos se migran correctamente:

1. **Comprobación de integridad**: Compara los nombres de los campos de la tabla, los tipos y otra información para comprobar la compatibilidad entre las estructuras de datos del Magento 1 y 2.
1. **Transferencia de datos**: Transfiere la tabla de datos por tabla de los Magento 1 y 2.
1. **Comprobación de volumen**: Compara el número de registros entre tablas para verificar que la transferencia se haya realizado correctamente.

![Etapas de migración](../../assets/data-migration/MigrationSteps2.png)

## Asignar archivos

En el nivel inferior de los procesos de migración se encuentra el XML *asignar archivos*. La variable [!DNL Data Migration Tool] utiliza archivos de asignación en las fases de un paso para transformar diferentes estructuras de datos entre las tablas Magento 1.x y 2.x.

Por ejemplo, cuando se transforman los datos de una base de datos Magento Open Source 1.8.0.0 a Magento Open Source 2.x.x, el archivo de asignación tiene en cuenta el hecho de que se ha cambiado el nombre de una tabla y cambia el nombre correspondiente en la base de datos de destino. Si no hay diferencias en la estructura de datos o el formato de datos, la variable [!DNL Data Migration Tool] la transfiere tal cual, incluidos los datos de tablas creadas por extensiones, a la base de datos de Magento 2.

Cuando las diferencias no se declaran en los archivos de asignación, la variable [!DNL Data Migration Tool] muestra un error y no se inicia.

Los archivos de asignación se tratan con más detalle en [[!DNL Data Migration Tool] Especificación técnica].

## Diagrama de flujo de migración

![Flujo de migración](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Especificación técnica](technical-specification.md)

Nos complace que esté considerando pasar de la primera plataforma comercial del mundo — Magento 1.x — a la plataforma del futuro, Magento 2. Estamos encantados de compartir los detalles sobre este proceso, al que nos referimos como migración.

## Componentes de migración

La migración al Magento 2 consta de cuatro componentes: datos, extensiones y código personalizado, temas y personalizaciones.

### Datos

Hemos desarrollado el **Magento 2[!DNL Data Migration Tool]** para ayudarle a mover de forma eficaz todos sus productos, clientes y datos de pedidos, almacene configuraciones, promociones y mucho más al Magento 2. Esta guía proporciona información sobre la herramienta y prácticas recomendadas para utilizarla para migrar los datos.

### Extensiones y código personalizado

Hemos estado trabajando duro con la comunidad de desarrollo para ayudarle a utilizar sus extensiones de Magento 1 en el Magento 2. Ahora estamos orgullosos de presentar el [Commerce Marketplace](https://marketplace.magento.com/), donde puede descargar o adquirir las últimas versiones de sus extensiones favoritas.

Encontrará más información sobre el desarrollo de extensiones para el Magento 2 en la [Guía para desarrolladores de PHP](https://developer.adobe.com/commerce/php/development/).

### Temas y personalizaciones

El Magento 2 utiliza nuevos enfoques y tecnologías que brindan a los comerciantes una capacidad incomparable para crear experiencias de compra innovadoras y escalar a nuevos niveles. Para aprovechar estos avances, los desarrolladores deben realizar cambios en sus temas y personalizaciones. La documentación está disponible en línea para crear el Magento 2 [temáticas](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [diseños](https://developer.adobe.com/commerce/frontend-core/guide/layouts/)y [personalizaciones](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Esfuerzos de migración

Al igual que una actualización entre versiones 1.x (por ejemplo, de v1.12 a v1.14), el nivel de esfuerzo para migrar del Magento 1 al Magento 2 depende de cómo haya creado su sitio y su nivel de personalización.
Sin embargo, estamos mejorando constantemente el [!DNL Data Migration Tool] (consulte la [Cambio](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) para más detalles); por lo tanto, los esfuerzos de migración están disminuyendo continuamente.
