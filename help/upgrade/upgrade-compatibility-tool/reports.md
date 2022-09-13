---
title: "[!DNL Upgrade Compatibility Tool] informes"
description: Siga estos pasos para ejecutar el [!DNL Upgrade Compatibility Tool] en su proyecto de Adobe Commerce.
source-git-commit: 147ecbc66eaf370e7ffaad0b6fce8b41f40b70df
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# Informes

{{commerce-only}}

Como resultado del análisis, la variable [!DNL Upgrade Compatibility Tool] puede exportar un informe que contenga una lista de problemas para cada archivo que especifique su gravedad, código de error y descripción del error. La variable [!DNL Upgrade Compatibility Tool] exporta el informe en dos formatos diferentes:

- A [Archivo JSON](reports.md#json-file).
- Un [informe del HTML](reports.md#html-report).

Consulte el siguiente ejemplo de interfaz de línea de comandos de un informe:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Marque la [Referencia de mensaje de error](../upgrade-compatibility-tool/error-messages.md) para obtener más información sobre los diferentes errores que puede producir este informe.

Este informe también incluye un resumen detallado que muestra:

- *Versión actual*: la versión instalada actualmente.
- *Versión de Target*: la versión a la que desee actualizar.
- *Tiempo de ejecución*: la cantidad de tiempo que tardó el análisis en crear el informe (mm:ss).
- *Módulos que requieren actualización*: el porcentaje de módulos que contienen problemas de compatibilidad y que requieren actualización.
- *Archivos que requieren actualización*: el porcentaje de archivos que contienen problemas de compatibilidad y que requieren actualización.
- *Errores críticos totales*: el número de errores críticos encontrados.
- *Errores totales*: el número de errores encontrados.
- *Advertencias totales*: el número de advertencias encontradas.
- *Uso máximo de memoria*: la cantidad máxima de memoria del [!DNL Upgrade Compatibility Tool] ha alcanzado durante la ejecución.

Consulte el siguiente ejemplo de interfaz de línea de comandos:

```terminal
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

Puede obtener la salida del archivo JSON al ejecutar el [!DNL Upgrade Compatibility Tool] en una interfaz de línea de comandos. La variable `JSON` contiene exactamente la misma información que se muestra en la variable [!DNL Upgrade Compatibility Tool] output:

- Una lista de problemas identificados.
- Resumen del análisis.

Para cada problema encontrado, el informe proporciona información detallada como la gravedad y descripción del problema.

Para exportar esto `JSON` en una carpeta de salida diferente:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Directorio de rutas para exportar `JSON` archivo de salida.

>[!NOTE]
>
> La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.json`.

## informe del HTML

Puede obtener el informe del HTML mientras ejecuta la herramienta en una interfaz de línea de comandos o a través del [!DNL Site-Wide Analysis Tool]. El informe del HTML también contiene:

- Una lista de problemas identificados.
- Resumen del análisis.

![Informe del HTML - Resumen](../../assets/upgrade-guide/uct-html-summary.png)

Puede navegar fácilmente por los problemas identificados durante el [!DNL Upgrade Compatibility Tool] análisis.

Puede filtrar los problemas que se muestran en el informe según el nivel de problema mínimo (el valor predeterminado es `WARNING`).

Hay un menú desplegable en la esquina superior derecha que le permite seleccionar un nivel diferente. La lista de problemas identificados se filtra en consecuencia.

![Informe del HTML: uso desplegable](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> Los problemas con un nivel de problema inferior se eliminan, pero se recibe una notificación para que siempre esté al tanto de los problemas identificados por módulo.

El informe del HTML también incluye cuatro gráficos diferentes:

- **Módulos por gravedad del problema**: Muestra la distribución de gravedad por módulos.
- **Archivos por gravedad del problema**: Muestra la distribución de gravedad por archivos.
- **Módulos ordenados por número total de problemas**: Muestra los 10 módulos más comprometidos teniendo en cuenta advertencias, errores y errores críticos.
- **Módulos con tamaños y problemas relativos**: Cuantos más archivos contenga un módulo, más grande será su círculo. Cuantos más problemas tenga un módulo, más rojo aparecerá su círculo.

Estos gráficos permiten identificar los módulos más comprometidos y aquellos que requieren más trabajo para realizar una actualización.

![Informe de HTML: diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Los diagramas de informes del HTML también se actualizan en consecuencia, con la única excepción del `Modules with relative sizes and issues`, que se genera con la variable `min-issue-level` que fue originalmente configurado.

Si desea ver resultados diferentes para la variable `Modules with relative sizes and issues` diagrama, debe volver a ejecutar el comando proporcionando otro valor para el `--min-issue-level` .

![Informe del HTML - Diagrama del gráfico de burbujas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar este informe de HTML a una carpeta de salida diferente:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=HTML-OUTPUT-PATH]`: Directorio de rutas para exportar `.html` archivo de salida.

>[!NOTE]
>
> La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.html`.
