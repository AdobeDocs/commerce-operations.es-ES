---
title: '[!DNL Upgrade Compatibility Tool] informes'
description: Siga estos pasos para ejecutar  [!DNL Upgrade Compatibility Tool]  en su proyecto de Adobe Commerce.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Informes

{{commerce-only}}

Como resultado del análisis, [!DNL Upgrade Compatibility Tool] puede exportar un informe que contiene una lista de problemas para cada archivo especificando su gravedad, código de error y descripción del error. [!DNL Upgrade Compatibility Tool] exporta el informe en dos formatos diferentes:

- Un [archivo JSON](reports.md#json-file).
- Un [informe de HTML](reports.md#html-report).

Consulte el siguiente ejemplo de interfaz de línea de comandos de un informe:

```
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Consulte el tema [Referencia de mensaje de error](../upgrade-compatibility-tool/error-messages.md) para obtener más información sobre los diferentes errores que puede producir este informe.

Este informe también incluye un resumen detallado que muestra lo siguiente:

- *Versión actual*: la versión instalada actualmente.
- *Versión de destino*: la versión a la que desea actualizar.
- *Tiempo de ejecución*: cantidad de tiempo que tardó el análisis en generar el informe (mm:ss).
- *Módulos que requieren actualización*: el porcentaje de módulos que contienen problemas de compatibilidad y requieren actualización.
- *Archivos que requieren actualización*: el porcentaje de archivos que contienen problemas de compatibilidad y que requieren actualización.
- *Errores críticos totales*: número de errores críticos encontrados.
- *Errores totales*: el número de errores encontrados.
- *Advertencias totales*: el número de advertencias encontradas.
- *Uso máximo de memoria*: la cantidad máxima de memoria que ha alcanzado [!DNL Upgrade Compatibility Tool] durante la ejecución.

Consulte el siguiente ejemplo de interfaz de línea de comandos:

```
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## Archivo JSON

Puede obtener la salida del archivo JSON mientras ejecuta [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos. El archivo `JSON` contiene exactamente la misma información mostrada en la salida [!DNL Upgrade Compatibility Tool]:

- Una lista de problemas identificados.
- Un resumen del análisis.

Para cada problema encontrado, el informe proporciona información detallada, como la gravedad y la descripción del problema.

Para exportar este archivo de `JSON` a una carpeta de salida diferente:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: directorio de ruta para exportar el archivo de salida `JSON`.

>[!NOTE]
>
> La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.json`.

## informe del HTML

Puede obtener el informe de HTML mientras ejecuta la herramienta en una interfaz de línea de comandos o a través de [!DNL Site-Wide Analysis Tool]. El informe de HTML también contiene:

- Una lista de problemas identificados.
- Un resumen del análisis.

![Informe del HTML - Resumen](../../assets/upgrade-guide/uct-html-summary.png)

Puede navegar fácilmente por los problemas identificados durante el análisis [!DNL Upgrade Compatibility Tool].

Puede filtrar los problemas que se muestran en el informe según el nivel mínimo de problemas (el valor predeterminado es `WARNING`).

Hay un menú desplegable en la esquina superior derecha que le permite seleccionar un nivel diferente. La lista de problemas identificados se filtra en consecuencia.

![informe del HTML - Uso desplegable](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Los problemas con un nivel de problema menor se eliminan, pero se obtiene una notificación para que siempre tenga en cuenta los problemas identificados por módulo.

El informe del HTML también incluye cuatro diagramas diferentes:

- **Módulos por gravedad del problema**: Muestra la distribución de la gravedad por módulos.
- **Archivos por gravedad del problema**: Muestra la distribución de la gravedad por archivos.
- **Módulos ordenados por número total de problemas**: muestra los 10 módulos más comprometidos teniendo en cuenta advertencias, errores y errores críticos.
- **Módulos con problemas y tamaños relativos**: cuantos más archivos contenga un módulo, mayor será su círculo. Cuantos más problemas tenga un módulo, más rojo aparecerá su círculo.

Estos gráficos le permiten identificar los módulos más comprometidos y los que requieren más trabajo para realizar una actualización.

![informe del HTML - Diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Los diagramas del informe del HTML también se actualizan en consecuencia, con la única excepción de `Modules with relative sizes and issues`, que se genera con `min-issue-level` que se configuró originalmente.

Si desea ver resultados diferentes para el diagrama `Modules with relative sizes and issues`, debe volver a ejecutar el comando proporcionando otro valor para la opción `--min-issue-level`.

![Informe del HTML - Diagrama del gráfico de burbujas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar este informe de HTML a una carpeta de salida diferente:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=HTML-OUTPUT-PATH]`: directorio de ruta para exportar el archivo de salida `.html`.

>[!NOTE]
>
> La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.html`.
