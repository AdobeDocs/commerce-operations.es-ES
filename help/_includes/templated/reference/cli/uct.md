---
source-git-commit: a8f4df78dfec2a1e94d650cac03c7fba21f398e8
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**Versión**: 3.0.19

Esta referencia contiene 9 comandos disponibles mediante la herramienta de línea de comandos `bin/uct`.
La lista inicial se genera automáticamente usando el comando `bin/uct list` en Adobe Commerce.

## General

Obtenga más información acerca de la herramienta en [Información general](/help/upgrade/upgrade-compatibility-tool/overview.md).

Esta documentación de referencia se genera a partir del código fuente de la aplicación. Para cambiar la documentación, debe abrir una solicitud de extracción para el comando correspondiente en el repositorio [codebase](https://github.com/magento) correspondiente. Consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) para obtener más información.

### Opciones globales

#### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

- Predeterminado: `false`
- No acepta un valor

#### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

#### `--verbose`, `-v|-vv|-vvv`

Aumente el nivel de detalle de los mensajes: 1 para un resultado normal, 2 para un resultado más detallado y 3 para una depuración

- Predeterminado: `false`
- No acepta un valor

#### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

#### `--ansi`

Forzar (o deshabilitar —sin ansi) la salida ANSI

- No acepta un valor

#### `--no-ansi`

Anule la opción &quot;—ansi&quot;

- Predeterminado: `false`
- No acepta un valor

#### `--no-interaction`, `-n`

No haga ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

Comando interno para proporcionar sugerencias de finalización de shell

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--shell`, `-s`

El tipo de shell (&quot;bash&quot;)

- Requiere un valor

#### `--input`, `-i`

Una matriz de tokens de entrada (por ejemplo, COMP_WORDS o argv)

- Predeterminado: `[]`
- Requiere un valor

#### `--current`, `-c`

Índice de la matriz de &quot;entrada&quot; en la que se encuentra el cursor (p. ej. COMP_CWORD)

- Requiere un valor

#### `--symfony`, `-S`

La versión del script de finalización

- Requiere un valor


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Volcar el script de finalización de shell

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently only bash completion is supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion bash | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion bash > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion bash)"
```

### Argumentos

#### `shell`

El tipo de shell (p. ej. &quot;bash&quot;), el valor de la variable env &quot;$SHELL&quot; se usará si no se proporciona

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--debug`

Seguimiento del registro de depuración de finalización

- Predeterminado: `false`
- No acepta un valor


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Mostrar la ayuda de un comando

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumentos

#### `command_name`

El nombre del comando

- Predeterminado: `help`

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor

#### `--raw`

Para generar la ayuda del comando raw

- Predeterminado: `false`
- No acepta un valor


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Comandos de lista

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### Argumentos

#### `namespace`

El nombre del área de nombres

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--raw`

Para generar la lista de comandos raw

- Predeterminado: `false`
- No acepta un valor

#### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor

#### `--short`

Para omitir la descripción de argumentos de comandos

- Predeterminado: `false`
- No acepta un valor


## `refactor`

```bash
bin/uct refactor <path>
```

Resuelve los problemas que se pueden solucionar automáticamente. Se actualizará el código de la ruta proporcionada.

### Argumentos

#### `path`

Ruta para resolver problemas en.

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

La herramienta de compatibilidad de actualización es una herramienta de línea de comandos que compara una instancia de Adobe Commerce con una versión específica analizando todos los módulos que no son de Adobe Commerce instalados en ella. Devuelve una lista de errores y advertencias que debe corregir antes de actualizar a una nueva versión del código Adobe Commerce.

### Argumentos

#### `dir`

Directorio de instalación de Adobe Commerce.

- Requerido


#### `vanilla-dir`

directorio de instalación de Adobe Commerce vanilla.

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--output`, `-o`

Ruta del archivo donde se exportará la salida (formato Json)

- Acepta un valor


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Permitir la lista de diferencias de esquema de Adobe Commerce DB entre dos versiones seleccionadas. Versiones disponibles: 2.3.0 | 2.3.1. | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2,3,5-p1 | 2,3,5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2,3,7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2.4.0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2,4,5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2,4,5-p2 | 2,4,5-p3 | 2.4.5-p4 | 2.4.6 | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2,4,5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-beta3 | 2.4.7 | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2,4,5-p8 | 2.4.6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2,4,5-p9 | 2.4.6-p7 | 2,4,7-p2 | 2.4.4-p11 | 2,4,5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-beta1

### Argumentos

#### `current-version`

versión actual (p. ej. 2.3.2).

- Requerido


#### `target-version`

versión de target (p. ej. 2.4.5).

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Verificación de la compatibilidad del esquema GraphQL

### Argumentos

#### `schema1`

Dirección URL de extremo que señala al primer esquema de GraphQL.

- Requerido


#### `schema2`

Dirección URL de extremo que señala al segundo esquema de GraphQL.

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--output`, `-o`

Ruta del archivo donde se exportará la salida (formato JSON)

- Acepta un valor


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

La herramienta de compatibilidad de actualización es una herramienta de línea de comandos que compara una instancia personalizada de Adobe Commerce con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de errores y advertencias que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.

### Argumentos

#### `dir`

Directorio de instalación de Adobe Commerce.

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--current-version`, `-a`

Si se omite, se utilizará la versión actual de Adobe Commerce o la versión de la instalación de Adobe Commerce.

- Acepta un valor

#### `--coming-version`, `-c`

Versión de Adobe Commerce de destino. Si se omite, se utilizará la última versión estable lanzada de Adobe Commerce. Versiones de Adobe Commerce disponibles: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4.8-beta1

- Acepta un valor

#### `--json-output-path`

Ruta del archivo donde se exportará la salida en formato json

- Acepta un valor

#### `--html-output-path`

Ruta del archivo donde se exportará la salida en formato de HTML

- Acepta un valor

#### `--min-issue-level`

Nivel mínimo de problema que desea ver en el informe (advertencia, error o crítico).

- Predeterminado: `warning`
- Acepta un valor

#### `--ignore-current-version-compatibility-issues`, `-i`

Ignorar problemas comunes de la versión actual y futura

- Predeterminado: `false`
- No acepta un valor

#### `--context`

Contexto de ejecución. Esta opción se utiliza con fines de integración y no afecta al resultado de la ejecución.

- Requiere un valor

