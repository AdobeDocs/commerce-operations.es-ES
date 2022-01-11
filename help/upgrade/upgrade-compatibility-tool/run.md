---
title: Ejecutar la herramienta de compatibilidad de actualización
description: Siga estos pasos para ejecutar la herramienta de compatibilidad de actualización en su proyecto de Adobe Commerce.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---


# Ejecutar la herramienta de compatibilidad de actualización

La herramienta de compatibilidad de actualización es una herramienta de línea de comandos que comprueba una instancia personalizada de Adobe Commerce en relación con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce.

La herramienta de compatibilidad de actualización identifica posibles problemas que deben solucionarse en el código antes de intentar actualizar a una versión más reciente de Adobe Commerce.

## Utilice la variable `upgrade:check` command

La variable `upgrade:check` es el comando principal para ejecutar la herramienta:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>La variable `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

La variable `upgrade:check` ejecuta la herramienta de compatibilidad de actualización y comprueba una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de problemas, errores y advertencias críticos que deben solucionarse antes de actualizar a la versión más reciente de Adobe Commerce.

>[!WARNING]
>
>Ejecutar solo cuando se proporcione el directorio raíz (o principal) del proyecto.

Este comando comprueba los cambios en el código principal de esa instancia de Adobe Commerce específica y todos los cambios en el código personalizado instalados en ella.

Puede ejecutar el `core:code:changes` para analizar solo los cambios en el código principal de esa instancia de Adobe Commerce específica. Consulte [Cambios en el código principal](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) para obtener más información.

Mientras que puede usar la variable `graphql:compare` para comparar dos esquemas de GraphQL y comprobar si hay cambios entre ellos. Consulte [Verificación de la compatibilidad del esquema de GraphQL](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) para obtener más información.

### Recommendations para usar la variable `upgrade:check` command

- La herramienta de compatibilidad de actualización requiere al menos 2 GB de RAM para ejecutarse. Se recomienda esta configuración para evitar problemas debido a una limitación de memoria baja. La herramienta de compatibilidad de actualización muestra una pregunta si ejecuta la `upgrade:check` comando con un valor bajo `memory_limit` configuración.
- Especifique la variable `-m` para ejecutar la herramienta en un módulo específico:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=MODULE-PATH]`: Directorio de rutas del módulo específico.

### Utilice la variable `--help` option

Para ver las opciones generales y la ayuda del comando Actualizar herramienta de compatibilidad, ejecute:

```bash
bin/uct --help
```

Sin embargo, es posible ejecutar `--help` como opción al ejecutar un comando específico, como `bin/uct upgrade:check`. Esto devuelve un valor específico `--help` opciones para ese comando:

```bash
bin/uct upgrade:check --help
```

Disponible `--help` para las `upgrade:check` comando:

- `-m, --module-path[=MODULE-PATH]`: Ruta de los módulos que se van a analizar
- `-a, --current-version[=CURRENT-VERSION]`: Versión actual de Adobe Commerce, se utilizará la versión de la instalación de Adobe Commerce si se omite.
- `-c, --coming-version[=COMING-VERSION]`: Versión de Adobe Commerce de Target, se utilizará la versión de la instalación de Adobe Commerce si se omite.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Ruta del archivo donde se exporta la salida en formato json.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Ruta del archivo donde se exportará el resultado en formato de HTML.
- `--min-issue-level`: Nivel mínimo del problema que se mostrará en el informe. El valor predeterminado es [ADVERTENCIA].
- `--ignore-current-version-compatibility-issues`: Utilice esta opción cuando no desee incluir problemas críticos conocidos, errores y advertencias en el informe de la herramienta de compatibilidad de actualización.
- `--context=CONTEXT`: Contexto de ejecución. Esta opción se utiliza con fines de integración y no afecta al resultado de la ejecución.
- `-h, --help`: Mostrar ayuda para ese comando específico. Si no se proporciona ningún comando, `list` es el resultado predeterminado.
- `-q, --quiet`: No envíe ningún mensaje mientras ejecuta el comando.
- `-v, --version`: Mostrar versión de la aplicación.
- `--ansi, --no-ansi`: Habilite la salida ANSI.
- `-n, --no-interaction`: No haga ninguna pregunta interactiva mientras ejecuta el comando.
- `-v, --vv, --vvv, --verbose`: Aumente la diversidad de las comunicaciones de salida. 1 para la salida normal, 2 para la salida verbosa y 3 para la salida DEBUG.

### Salida

Como resultado del análisis realizado, la herramienta de compatibilidad de actualización exporta un informe que contiene una lista de problemas para cada archivo que especifica su gravedad, código de error y descripción del error.

Consulte el ejemplo siguiente:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Marque la [Referencia de mensaje de error](error-messages.md) para obtener más información.

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
>De forma predeterminada, la herramienta de compatibilidad de actualización exporta el informe en dos formatos diferentes: `json` y `html`.

#### JSON

El archivo JSON contiene exactamente la misma información que se muestra en la salida:

- Lista de los problemas identificados.
- Resumen del análisis.

Para cada problema encontrado, el informe proporciona información detallada como la gravedad y descripción del problema.

>[!NOTE]
>
>La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.json`.

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

#### HTML

El archivo del HTML también contiene la lista de problemas identificados y el resumen del análisis. También incluye cuatro gráficos diferentes:

- **Módulos por gravedad del problema**: Muestra la distribución de gravedad por módulos.
- **Archivos por gravedad del problema**: Muestra la distribución de gravedad por archivos.
- **Módulos ordenados por número total de problemas**: Muestra los 10 módulos más comprometidos teniendo en cuenta advertencias, errores y errores críticos.
- **Módulos con tamaños y problemas relativos**: Cuantos más archivos contenga un módulo, más grande será su círculo. Cuantos más problemas tenga un módulo, más rojo aparecerá su círculo.

Estos gráficos permiten identificar (de un vistazo) las partes más comprometidas y las que requieren más trabajo para realizar una actualización.

![Informe del HTML - Resumen](../../assets/upgrade-guide/uct-html-summary.png)

![Informe del HTML: detalles](../../assets/upgrade-guide/uct-html-details.png)

Para exportar este informe a una carpeta de salida diferente, ejecute:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: Directorio de instalación de {{site.data.var.ee}}.
- `[=HTML-OUTPUT-PATH]`: Directorio de rutas para exportar `.html` archivo de salida.

>[!NOTE]
>
>La ruta predeterminada para la carpeta de salida es `var/output/[TIME]-results.html`.

### Utilice la variable `--ignore-current-version-compatibility-issues` option

La herramienta de compatibilidad de actualización le permite ejecutar el `upgrade:check` con un `--ignore-current-version-compatibility-issues` , por lo que solo muestra problemas críticos, errores y advertencias nuevos o desconocidos. Utilice esta opción cuando no desee incluir problemas críticos conocidos, errores y advertencias en el informe de la herramienta de compatibilidad de actualización.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Esto solo se aplica a las validaciones de la API PHP.

### Instalación de vainilla

A _vainilla_ la instalación es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

La variable `bin/uct core:code:changes` comprueba si hay una instancia de vainilla en el sistema. Si es la primera vez que se utiliza una instalación de vainilla, una pregunta interactiva de la línea de comandos le pedirá que descargue el proyecto de vainilla desde el [Repositorio de Adobe Commerce](https://repo.magento.com/).

Puede ejecutar un comando de la herramienta de compatibilidad de actualización con el `--vanilla-dir` para especificar el directorio de instalación de Adobe Commerce vainilla.

Consulte la [Implementar instancia de vanilla](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obtener más información.

## Utilice la variable `list` command

Para devolver una lista de los comandos disponibles de la herramienta de compatibilidad de actualización, ejecute:

```bash
bin/uct list
```

La variable `list` devuelve lo siguiente:

- `-h, --help`: Mostrar ayuda para ese comando específico. Si no se proporciona ningún comando, `list` es el resultado predeterminado.
- `-q, --quiet`: No envíe ningún mensaje mientras ejecuta el comando.
- `-v, --version`: Mostrar versión de la aplicación.
- `--ansi, --no-ansi`: Habilite la salida ANSI.
- `-n, --no-interaction`: No haga ninguna pregunta interactiva mientras ejecuta el comando.
- `-v, --vv, --vvv, --verbose`: Aumente la diversidad de las comunicaciones de salida. 1 para la salida normal, 2 para la salida verbosa y 3 para la salida DEBUG.

## Utilice la variable `core:code:changes` command

Puede comparar su instalación actual de Adobe Commerce con una instalación de vainilla limpia para ver si el código principal tiene modificaciones realizadas para implementar una nueva función o personalización. Esta validación ayuda a calcular el esfuerzo que requiere la actualización en función de esos cambios.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `<vanilla dir>`: Directorio de instalación de vainilla de Adobe Commerce.

Existen algunas limitaciones al ejecutar este comando:

- Ejecutar solo cuando se proporcione el directorio raíz (o principal) del proyecto.
- Muestra únicamente una lista de modificaciones principales.

### Utilice la variable `core:code:changes` con la variable `--help` option

Disponible `--help` para las `core:code:changes` comando:

- `-h, --help`: Mostrar ayuda para ese comando específico. Si no se proporciona ningún comando, `list` es el resultado predeterminado.
- `-q, --quiet`: No envíe ningún mensaje mientras ejecuta el comando.
- `-v, --version`: Mostrar versión de la aplicación.
- `--ansi, --no-ansi`: Habilite la salida ANSI.
- `-n, --no-interaction`: No haga ninguna pregunta interactiva mientras ejecuta el comando.
- `-v, --vv, --vvv, --verbose`: Aumente la diversidad de las comunicaciones de salida. 1 para la salida normal, 2 para la salida verbosa y 3 para la salida DEBUG.

## Versión

Puede comparar su instalación actual de Adobe Commerce con las versiones de Adobe Commerce `>=2.3`.

Debe proporcionar la versión como parámetro al ejecutar el comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Donde:

- `-c, --coming-version[=COMING-VERSION]`: La versión de destino de Adobe Commerce.

Existen algunas limitaciones al ejecutar el comando anterior:

- Este parámetro hace referencia a cualquier etiqueta que identifique una versión específica de Adobe Commerce.
- Es un requisito que se proporcione explícitamente; proporcionar solo el valor de no funciona.
- Proporcione la versión de la etiqueta sin comillas (ni simple ni doble): ~~&quot;2.4.1-desarrollar&quot;~~.
- NO debe proporcionar versiones anteriores a la que tiene instalada actualmente, ni anteriores a la 2.3, que es la más antigua compatible en este momento.

## Verificación de la compatibilidad del esquema de GraphQL

La herramienta de compatibilidad de actualización también proporciona la opción de inspeccionar dos extremos de GraphQL y comparar sus esquemas buscando cambios y cambios peligrosos entre ellos:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Donde los argumentos son los siguientes:

- `<schema1>`: Dirección URL del extremo para la instalación existente.
- `<schema2>`: Dirección URL de extremo para la instalación de vainilla.

Debe estar en ejecución `instance before` y `instance after` la actualización.

### Comparación de GraphQL, comando `--help` opciones

Disponible `--help` para las `graphql:compare` comando:

- `-h, --help`: Mostrar ayuda para ese comando específico. Si no se proporciona ningún comando, `list` es el resultado predeterminado.
- `-q, --quiet`: No envíe ningún mensaje mientras ejecuta el comando.
- `-v, --version`: Mostrar versión de la aplicación.
- `--ansi, --no-ansi`: Habilite la salida ANSI.
- `-n, --no-interaction`: No haga ninguna pregunta interactiva mientras ejecuta el comando.
- `-v, --vv, --vvv, --verbose`: Aumente la diversidad de las comunicaciones de salida. 1 para la salida normal, 2 para la salida verbosa y 3 para la salida DEBUG.

### Ejemplo con una lista de problemas críticos, errores y advertencias para GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

Consulte [Información para desarrolladores](../upgrade-compatibility-tool/developer.md) para obtener más información.

Puede ejecutar la herramienta de compatibilidad de actualización con una configuración de ejecución a través del complemento PhpStorm. Consulte la [Configuración de ejecución de la herramienta de compatibilidad de actualización](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) para obtener más información.

## Resolución de problemas

### Salida vacía

>[!NOTE]
>
>La variable `M2_VERSION` es la versión de Adobe Commerce de destino que desea comparar con la instancia de Adobe Commerce.

Si después de ejecutar este comando:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

El único resultado es `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

La causa probable es una limitación de memoria PHP.
Anule la limitación de memoria estableciendo `memory_limit` a `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
