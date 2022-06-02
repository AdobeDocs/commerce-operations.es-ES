---
title: '"[!DNL Upgrade Compatibility Tool] informes"'
description: Siga estos pasos para ejecutar el [!DNL Upgrade Compatibility Tool] en su proyecto de Adobe Commerce.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Informes

{{commerce-only}}

Como resultado del análisis, la variable [!DNL Upgrade Compatibility Tool] exporta un informe que contiene una lista de problemas para cada archivo que especifica su gravedad, código de error y descripción del error.

Consulte el ejemplo siguiente:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Marque la [Referencia de mensaje de error](../upgrade-compatibility-tool/error-messages.md) para obtener más información.

El informe también incluye un resumen detallado que muestra:

- *Versión actual*: la versión instalada actualmente.
- *Versión de Target*: la versión a la que desee actualizar.
- *Tiempo de ejecución*: la cantidad de tiempo que tardó el análisis en crear el informe (mm:ss).
- *Módulos que requieren actualización*: el porcentaje de módulos que contienen problemas de compatibilidad y que requieren actualización.
- *Archivos que requieren actualización*: el porcentaje de archivos que contienen problemas de compatibilidad y que requieren actualización.
- *Errores críticos totales*: el número de errores críticos encontrados.
- *Errores totales*: el número de errores encontrados.
- *Advertencias totales*: el número de advertencias encontradas.

Consulte el ejemplo siguiente:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>De forma predeterminada, la variable [!DNL Upgrade Compatibility Tool] exporta el informe en dos formatos diferentes: `json` y `html`.

## Archivo JSON

El archivo JSON contiene exactamente la misma información que se muestra en la salida:

- Lista de los problemas identificados.
- Resumen del análisis.

Para cada problema encontrado, el informe proporciona información detallada como la gravedad y descripción del problema.

Para exportar este informe a una carpeta de salida diferente, ejecute:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Directorio de rutas para exportar `.json` archivo de salida.

>[!NOTE]
>
>La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.json`.

## informe del HTML

El archivo del HTML también contiene el resumen del análisis y la lista de problemas identificados. Puede obtener el informe del HTML mientras ejecuta la herramienta en una interfaz de línea de comandos o a través del [!DNL Site-Wide Analysis Tool].

![Informe del HTML - Resumen](../../assets/upgrade-guide/uct-html-summary.png)

Puede navegar fácilmente por los problemas identificados durante el [!DNL Upgrade Compatibility Tool] análisis:

![Informe del HTML: detalles](../../assets/upgrade-guide/uct-html-details.png)

El informe del HTML también incluye cuatro gráficos diferentes:

- **Módulos por gravedad del problema**: Muestra la distribución de gravedad por módulos.
- **Archivos por gravedad del problema**: Muestra la distribución de gravedad por archivos.
- **Módulos ordenados por número total de problemas**: Muestra los 10 módulos más comprometidos teniendo en cuenta advertencias, errores y errores críticos.
- **Módulos con tamaños y problemas relativos**: Cuantos más archivos contenga un módulo, más grande será su círculo. Cuantos más problemas tenga un módulo, más rojo aparecerá su círculo.

Estos gráficos permiten identificar (de un vistazo) las partes más comprometidas y las que requieren más trabajo para realizar una actualización.

![Informe de HTML: diagramas](../../assets/upgrade-guide/uct-html-diagrams.png)

Puede filtrar los problemas que se muestran en el informe según el nivel de problema mínimo. El valor predeterminado es `WARNING`.

Hay un menú desplegable en la esquina superior derecha que le permite seleccionar uno diferente según sus necesidades. La lista de problemas identificados se filtrará en consecuencia.

![Informe del HTML: uso desplegable](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

Tenga en cuenta que los problemas con menor nivel de problema se eliminan, pero recibe una notificación para que siempre esté al tanto de los problemas identificados por módulo.

Los diagramas también se actualizan en consecuencia, con la única excepción del `Modules with relative sizes and issues`, que se genera con la variable `min-issue-level` originalmente configurado.

Si desea ver resultados diferentes, tendrá que volver a ejecutar el comando proporcionando otro valor para la variable `--min-issue-level` .

![Informe del HTML - Diagrama del gráfico de burbujas](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Para exportar este informe a una carpeta de salida diferente, ejecute:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: Directorio de instalación de {{site.data.var.ee}}.
- `[=HTML-OUTPUT-PATH]`: Directorio de rutas para exportar `.html` archivo de salida.

>[!NOTE]
>
> La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.html`.
