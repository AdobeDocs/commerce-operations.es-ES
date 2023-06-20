---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versión**: 3.0.3

Esta referencia contiene 9 comandos disponibles a través del `bin/uct` herramienta de línea de comandos.
La lista inicial se genera automáticamente utilizando `bin/uct list` en Adobe Commerce.

Obtenga más información acerca de la herramienta en [Información general](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Esta referencia se genera a partir del código base de la aplicación. Para cambiar el contenido, puede actualizar el código fuente para la implementación del comando correspondiente en la [código base](https://github.com/magento) y envíe los cambios para que se revisen. Otra forma es _Danos tu opinión_ (busque el vínculo en la parte superior derecha). Para ver las directrices de contribución, consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Comando interno para proporcionar sugerencias de finalización de shell

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

El tipo de shell (&quot;bash&quot;)

- Requiere un valor

### `--input`, `-i`

Una matriz de tokens de entrada (por ejemplo, COMP_WORDS o argv)

- Predeterminado: `[]`
- Requiere un valor

### `--current`, `-c`

Índice de la matriz de &quot;entrada&quot; en la que se encuentra el cursor (p. ej. COMP_CWORD)

- Requiere un valor

### `--symfony`, `-S`

La versión del script de finalización

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `completion`

Volcar el script de finalización de shell

```bash
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

El tipo de shell (p. ej. &quot;bash&quot;), el valor de la variable env &quot;$SHELL&quot; se usará si no se proporciona


### `--debug`

Seguimiento del registro de depuración de finalización

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `help`

Mostrar la ayuda de un comando

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

El nombre del comando

- Predeterminado: `help`


### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor

### `--raw`

Para generar la ayuda del comando raw

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `list`

Comandos de lista

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

El nombre del área de nombres


### `--raw`

Para generar la lista de comandos raw

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor

### `--short`

Para omitir la descripción de argumentos de comandos

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `refactor`

Resuelve los problemas que se pueden solucionar automáticamente. Se actualizará el código de la ruta proporcionada.

```bash
bin/uct refactor <path>
```


### `path`

Ruta para resolver problemas en.

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `core:code:changes`

La herramienta de compatibilidad de actualización es una herramienta de línea de comandos que compara una instancia de Adobe Commerce con una versión específica analizando todos los módulos que no son de Adobe Commerce instalados en ella. Devuelve una lista de errores y advertencias que debe corregir antes de actualizar a una nueva versión del código Adobe Commerce.

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

Directorio de instalación de Adobe Commerce.

- Requerido

### `vanilla-dir`

directorio de instalación de Adobe Commerce vanilla.


### `--output`, `-o`

Ruta del archivo donde se exportará la salida (formato Json)

- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dbschema:diff`

Permitir la lista de diferencias de esquema de Adobe Commerce DB entre dos versiones seleccionadas.
Versiones disponibles: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2.3.5-p1 | 2.3.5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.5-p2 | 2.4.6

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

versión actual (p. ej. 2.3.2).

- Requerido

### `target-version`

versión de target (p. ej. 2.4.5).

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `graphql:compare`

Verificación de la compatibilidad del esquema GraphQL

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

Dirección URL de extremo que señala al primer esquema de GraphQL.

- Requerido

### `schema2`

Dirección URL de extremo que señala al segundo esquema de GraphQL.

- Requerido

### `--output`, `-o`

Ruta del archivo donde se exportará la salida (formato JSON)

- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `upgrade:check`

La herramienta de compatibilidad de actualización es una herramienta de línea de comandos que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de errores y advertencias que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

Directorio de instalación de Adobe Commerce.

- Requerido

### `--current-version`, `-a`

Si se omite, se utilizará la versión actual de Adobe Commerce o la versión de la instalación de Adobe Commerce.

- Acepta un valor

### `--coming-version`, `-c`

Versión de Adobe Commerce de destino; si se omite, se utilizará la última versión de Adobe Commerce. Versiones disponibles de Adobe Commerce: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4 -p1 \| 2.4.5 \| 2.4.4-p2 \| 2.4.5-p1 \| 2.4.4-p3 \| 2.4.5-p2 \| 2.4.6

- Acepta un valor

### `--json-output-path`

Ruta del archivo donde se exportará la salida en formato json

- Acepta un valor

### `--html-output-path`

Ruta del archivo donde se exportará la salida en formato de HTML

- Acepta un valor

### `--min-issue-level`

Nivel mínimo de problema que desea ver en el informe (advertencia, error o crítico).

- Predeterminado: `warning`
- Acepta un valor

### `--ignore-current-version-compatibility-issues`, `-i`

Ignorar problemas comunes de la versión actual y futura

- Predeterminado: `false`
- No acepta un valor

### `--context`

Contexto de ejecución. Esta opción se utiliza con fines de integración y no afecta al resultado de la ejecución.

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para \&lt;info>lista\&lt;/info> mando

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor

