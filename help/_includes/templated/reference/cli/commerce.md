---
source-git-commit: 27e7a262fd1d8092045f5ebe2f88caaec37a6b0d
workflow-type: tm+mt
source-wordcount: '29783'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce en infraestructura en la nube)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versión**: 1.42.0

Esta referencia contiene 134 comandos disponibles a través del `magento-cloud` herramienta de línea de comandos.
La lista inicial se genera automáticamente utilizando `magento-cloud list` en la edición.

>[!NOTE]
>
>Esta referencia se genera a partir del código base de la aplicación. Para cambiar el contenido, puede actualizar el código fuente para la implementación del comando correspondiente en la [código base](https://github.com/magento) y envíe los cambios para que se revisen. Otra forma es _Danos tu opinión_ (busque el vínculo en la parte superior derecha). Para ver las directrices de contribución, consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

Gancho de terminación BASH.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

### `--generate-hook`, `-g`

Genere el código BASH que configure la finalización para esta aplicación.

- Predeterminado: `false`
- No acepta un valor

### `--program`, `-p`

Nombre de programa que debe alcanzar el déclencheur de finalización &lt;comment>(toma como valor predeterminado la ruta absoluta de la aplicación)&lt;/comment>.

- Requiere un valor

### `--multiple`, `-m`

El vínculo generado se puede utilizar para varias aplicaciones.

- Predeterminado: `false`
- No acepta un valor

### `--shell-type`

Establezca el tipo de shell (zsh o bash). De lo contrario, esto se determina automáticamente.

- Acepta un valor


## `bot`

El bot de Magento Cloud

```bash
magento-cloud bot [--party] [--parrot]
```

### `--party`



- Predeterminado: `false`
- No acepta un valor

### `--parrot`



- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `clear-cache`

Borre la caché de CLI

```bash
magento-cloud clear-cache
```


```bash
clearcache
```


```bash
cc
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `decode`

Descodificar una cadena codificada como MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

Valor de la variable que se va a descodificar

- Requerido

### `--property`, `-P`

La propiedad que se verá en la variable

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `docs`

Abra la documentación en línea

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

Término(s) de búsqueda

- Predeterminado: `[]`

- Matriz

### `--browser`

Explorador que se utiliza para abrir la dirección URL. Establezca 0 para ninguno.

- Requiere un valor

### `--pipe`

Envíe la URL a stdout.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `help`

Muestra la Ayuda de un comando

```bash
magento-cloud help [--format FORMAT] [--raw] [--] [<command_name>]
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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `legacy-migrate`

Migrar desde la estructura de archivos heredada

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

No cree una copia de seguridad del proyecto.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `list`

Comandos de listas

```bash
magento-cloud list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `command`

El comando que se va a ejecutar

- Requerido

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

### `--all`

Mostrar todos los comandos, incluidos los ocultos

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `multi`

Ejecutar un comando en varios proyectos

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd> (<cmd>)...
```


### `cmd`

El comando que se va a ejecutar

- Predeterminado: `[]`

- Requerido
- Matriz

### `--projects`, `-p`

Una lista de ID de proyecto, separados por comas o espacios en blanco

- Requiere un valor

### `--continue`

Continuar ejecutando comandos incluso si se encuentra una excepción

- Predeterminado: `false`
- No acepta un valor

### `--sort`

Propiedad por la que se ordena la lista de opciones del proyecto

- Predeterminado: `title`
- Requiere un valor

### `--reverse`

Invertir el orden de las opciones del proyecto

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `web`

Abrir la interfaz de usuario web

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--browser`

Explorador que se utiliza para abrir la dirección URL. Establezca 0 para ninguno.

- Requiere un valor

### `--pipe`

Envíe la URL a stdout.

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `welcome`

Bienvenido a Magento Cloud

```bash
magento-cloud welcome
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `activity:cancel`

Cancelar una actividad

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

El ID de actividad. El valor predeterminado es la actividad cancelable más reciente.


### `--type`

Filtre por tipo (al seleccionar una actividad predeterminada). Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede usar como comodín para el tipo, p. ej. &#39;%var%&#39; para seleccionar actividades relacionadas con variables.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-type`

Excluir por tipo (al seleccionar una actividad predeterminada). Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede utilizar como comodín para excluir tipos.

- Predeterminado: `[]`
- Requiere un valor

### `--all`, `-a`

Compruebe las actividades recientes en todos los entornos (al seleccionar una actividad predeterminada)

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `activity:get`

Ver información detallada sobre una sola actividad

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

El ID de actividad. El valor predeterminado es la actividad más reciente.


### `--property`, `-P`

La propiedad que se va a ver

- Requiere un valor

### `--type`

Filtre por tipo (al seleccionar una actividad predeterminada). Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede usar como comodín para el tipo, p. ej. &#39;%var%&#39; para seleccionar actividades relacionadas con variables.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-type`

Excluir por tipo (al seleccionar una actividad predeterminada). Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede utilizar como comodín para excluir tipos.

- Predeterminado: `[]`
- Requiere un valor

### `--state`

Filtrar por estado (al seleccionar una actividad predeterminada): en curso, pendiente, completo o cancelado. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--result`

Filtrar por resultado (al seleccionar una actividad predeterminada): éxito o error

- Requiere un valor

### `--incomplete`, `-i`

Incluya solo las actividades incompletas (al seleccionar una actividad predeterminada). Este es un atajo para &lt;info>—state=en_curso,pendiente&lt;/info>

- Predeterminado: `false`
- No acepta un valor

### `--all`, `-a`

Compruebe las actividades recientes en todos los entornos (al seleccionar una actividad predeterminada)

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `activity:list`

Obtener una lista de actividades de un entorno o proyecto

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

Filtrar actividades por tipo Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se dividirá por comas o espacios en blanco. El carácter % se puede usar como comodín para el tipo, p. ej. &#39;%var%&#39; para seleccionar actividades relacionadas con variables.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-type`, `-x`

Excluir actividades por tipo. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede utilizar como comodín para excluir tipos.

- Predeterminado: `[]`
- Requiere un valor

### `--limit`

Limitar el número de resultados mostrados

- Predeterminado: `10`
- Requiere un valor

### `--start`

Solo se enumerarán las actividades creadas antes de esta fecha

- Requiere un valor

### `--state`

Filtrar actividades por estado: en curso, pendiente, completo o cancelado. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--result`

Filtrado de actividades por resultado: éxito o fracaso

- Requiere un valor

### `--incomplete`, `-i`

Enumerar solo las actividades incompletas

- Predeterminado: `false`
- No acepta un valor

### `--all`, `-a`

Enumerar actividades en todos los entornos

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: id*, created*, description*, progress*, state*, result*, completed, environment, type (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `activity:log`

Mostrar el registro de una actividad

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

El ID de actividad. El valor predeterminado es la actividad más reciente.


### `--refresh`

Intervalo de actualización de la actividad (segundos). Establezca el valor en 0 para deshabilitar la actualización.

- Predeterminado: `3`
- Requiere un valor

### `--timestamps`, `-t`

Mostrar una marca de tiempo junto a cada mensaje

- Predeterminado: `false`
- No acepta un valor

### `--type`

Filtre por tipo (al seleccionar una actividad predeterminada). Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede usar como comodín para el tipo, p. ej. &#39;%var%&#39; para seleccionar actividades relacionadas con variables.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-type`

Excluir por tipo (al seleccionar una actividad predeterminada). Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede utilizar como comodín para excluir tipos.

- Predeterminado: `[]`
- Requiere un valor

### `--state`

Filtrar por estado (al seleccionar una actividad predeterminada): en curso, pendiente, completo o cancelado. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--result`

Filtrar por resultado (al seleccionar una actividad predeterminada): éxito o error

- Requiere un valor

### `--incomplete`, `-i`

Incluya solo las actividades incompletas (al seleccionar una actividad predeterminada). Este es un atajo para &lt;info>—state=en_curso,pendiente&lt;/info>

- Predeterminado: `false`
- No acepta un valor

### `--all`, `-a`

Compruebe las actividades recientes en todos los entornos (al seleccionar una actividad predeterminada)

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `api:curl`

Ejecute una solicitud de cURL autenticada en la API de Magento Cloud

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

La ruta de API


### `--request`, `-X`

El método de solicitud que se va a utilizar

- Requiere un valor

### `--data`, `-d`

Datos para enviar

- Requiere un valor

### `--json`

Datos JSON para enviar

- Requiere un valor

### `--include`, `-i`

Incluir encabezados en la salida

- Predeterminado: `false`
- No acepta un valor

### `--head`, `-I`

Recuperar solo encabezados

- Predeterminado: `false`
- No acepta un valor

### `--disable-compression`

No utilice el indicador curl —compressed

- Predeterminado: `false`
- No acepta un valor

### `--enable-glob`

Habilitar globbing curl (eliminar el indicador —globoff)

- Predeterminado: `false`
- No acepta un valor

### `--fail`, `-f`

Error sin salida en respuesta a error

- Predeterminado: `false`
- No acepta un valor

### `--header`, `-H`

Encabezado(s) adicional(es)

- Predeterminado: `[]`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `app:config-get`

Ver la configuración de una aplicación

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--property`, `-P`

La propiedad de configuración que se va a ver

- Requiere un valor

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--identity-file`, `-i`

[Opción obsoleta, ya no se utiliza]

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `app:list`

Enumerar aplicaciones en el proyecto

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
apps
```

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: nombre*, tipo*, disco, ruta, tamaño (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `auth:api-token-login`

Inicie sesión en Magento Cloud mediante un token de API

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `auth:browser-login`

Inicie sesión en Magento Cloud mediante un explorador

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

### `--force`, `-f`

Inicie sesión de nuevo, incluso si ya ha iniciado sesión

- Predeterminado: `false`
- No acepta un valor

### `--browser`

Explorador que se utiliza para abrir la dirección URL. Establezca 0 para ninguno.

- Requiere un valor

### `--pipe`

Envíe la URL a stdout.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `auth:info`

Mostrar la información de la cuenta

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

Propiedad de la cuenta que se va a ver


### `--no-auto-login`

Omite el inicio de sesión automático. No se generará nada si no se inicia sesión, y el código de salida será 0, suponiendo que no haya otros errores.

- Predeterminado: `false`
- No acepta un valor

### `--property`, `-P`

La propiedad de cuenta que se va a ver (sintaxis alternativa)

- Requiere un valor

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `auth:logout`

Cerrar sesión en Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

### `--all`, `-a`

Cerrar sesión en todas las sesiones locales

- Predeterminado: `false`
- No acepta un valor

### `--other`

Cerrar sesión en otras sesiones locales

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Inicie sesión en Magento Cloud con un nombre de usuario y una contraseña

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `auth:token`

Obtenga un token de acceso de OAuth 2 para solicitudes a las API de Magento Cloud

```bash
magento-cloud auth:token [-H|--header] [-W|--no-warn]
```

### `--header`, `-H`

Agregue al token el prefijo &quot;Autorización: Portador&quot; para crear un encabezado RFC 6750

- Predeterminado: `false`
- No acepta un valor

### `--no-warn`, `-W`

Suprima la advertencia que se imprime de forma predeterminada en stderr. Esta opción es preferible a redirigir stderr, ya que esto ocultaría otros mensajes potencialmente útiles.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `blackfire:setup`

Configure la integración de Blackfire.io para el proyecto

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--server_id`

El ID del servidor

- Requiere un valor

### `--server_token`

El token del servidor

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `blue-green:conclude`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Finalizar una implementación azul/verde

```bash
magento-cloud blue-green:conclude [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `blue-green:deploy`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Realizar una implementación azul/verde

```bash
magento-cloud blue-green:deploy [--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`

Establecer el porcentaje de enrutamiento de la última versión

- Predeterminado: `100`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `blue-green:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Habilitar implementaciones azules/verdes

```bash
magento-cloud blue-green:enable [-%|--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`, `-%`

Establecer el porcentaje de enrutamiento de la última versión

- Predeterminado: `100`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `certificate:add`

Añadir un certificado SSL al proyecto

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--cert`

La ruta al archivo de certificado

- Requiere un valor

### `--key`

Ruta al archivo de clave privada del certificado

- Requiere un valor

### `--chain`

La ruta al archivo de cadena de certificados

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `certificate:delete`

Eliminar un certificado del proyecto

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

El ID del certificado (o el inicio)

- Requerido

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `certificate:get`

Ver un certificado

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] <id>
```


### `id`

El ID del certificado (o el inicio)

- Requerido

### `--property`, `-P`

La propiedad de certificado que se va a ver

- Requiere un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `certificate:list`

Enumerar certificados de proyecto

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
certificates
```


```bash
certs
```

### `--domain`

Filtrar por nombre de dominio (búsqueda sin distinción de mayúsculas y minúsculas)

- Requiere un valor

### `--exclude-domain`

Excluir certificados, coincidencia por nombre de dominio (búsqueda sin distinción de mayúsculas y minúsculas)

- Requiere un valor

### `--issuer`

Filtrar por emisor

- Requiere un valor

### `--only-auto`

Mostrar solo los certificados aprovisionados automáticamente

- Predeterminado: `false`
- No acepta un valor

### `--no-auto`

Mostrar solo los certificados añadidos manualmente

- Predeterminado: `false`
- No acepta un valor

### `--ignore-expiry`

Mostrar certificados caducados y no caducados

- Predeterminado: `false`
- No acepta un valor

### `--only-expired`

Mostrar solo los certificados caducados

- Predeterminado: `false`
- No acepta un valor

### `--no-expired`

Mostrar solo los certificados no caducados (predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--pipe-domains`

Devolver solo una lista de nombres de dominio cubiertos por los certificados

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: creado, dominios, caduca, id, emisor. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `commit:get`

Mostrar detalles de confirmación

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

El SHA de compromiso. Esto también puede aceptar sufijos de &quot;HEAD&quot; y acento circunflejo (^) o tilde (~) para confirmaciones principales.

- Predeterminado: `HEAD`


### `--property`, `-P`

La propiedad commit que se va a mostrar.

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--format`

OBSOLETO

- Requiere un valor

### `--columns`

OBSOLETO

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

OBSOLETO

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `commit:list`

Enumerar confirmaciones

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

El SHA de confirmación de Git de inicio. Esto también puede aceptar sufijos de &quot;HEAD&quot; y acento circunflejo (^) o tilde (~) para confirmaciones principales.


### `--limit`

Número de confirmaciones que se van a mostrar.

- Predeterminado: `10`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: autor, fecha, sha, resumen. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `db:dump`

Crear un volcado local de la base de datos remota

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

### `--schema`

Esquema que se va a volcar. Omita utilizar el esquema predeterminado (normalmente &quot;main&quot;).

- Requiere un valor

### `--file`, `-f`

Un nombre de archivo personalizado para el volcado

- Requiere un valor

### `--directory`, `-d`

Un directorio personalizado para el volcado

- Requiere un valor

### `--gzip`, `-z`

Comprimir el volcado utilizando gzip

- Predeterminado: `false`
- No acepta un valor

### `--timestamp`, `-t`

Añadir una marca de tiempo al nombre del archivo de volcado

- Predeterminado: `false`
- No acepta un valor

### `--stdout`, `-o`

Salida a STDOUT en lugar de a un archivo

- Predeterminado: `false`
- No acepta un valor

### `--table`

Tabla(s) que incluir

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-table`

Tabla(s) que excluir

- Predeterminado: `[]`
- Requiere un valor

### `--schema-only`

Volcar solo esquemas, sin datos

- Predeterminado: `false`
- No acepta un valor

### `--charset`

La codificación del conjunto de caracteres del volcado

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `db:size`

Calcular el uso de disco de una base de datos

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

### `--bytes`, `-B`

Mostrar tamaños en bytes.

- Predeterminado: `false`
- No acepta un valor

### `--cleanup`, `-C`

Comprobar si las tablas se pueden limpiar y mostrar recomendaciones (solo InnoDb).

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: max, percent_used, used. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `db:sql`

Ejecutar SQL en la base de datos remota

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


```bash
sql
```


```bash
environment:sql
```


### `query`

Instrucción SQL para ejecutar


### `--raw`

Producir salida sin procesar y no tabular

- Predeterminado: `false`
- No acepta un valor

### `--schema`

Esquema que se va a utilizar. Omita utilizar el esquema predeterminado (normalmente &quot;main&quot;). Pase una cadena vacía para no utilizar ningún esquema.

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `domain:add`

Añadir un nuevo dominio al proyecto

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

El nombre de dominio

- Requerido

### `--cert`

Ruta de acceso al archivo de certificado para este dominio

- Requiere un valor

### `--key`

Ruta de acceso al archivo de clave privada del certificado proporcionado.

- Requiere un valor

### `--chain`

Ruta de acceso al archivo o archivos de cadena de certificados para el certificado proporcionado

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `domain:delete`

Eliminar un dominio del proyecto

```bash
magento-cloud domain:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

El nombre de dominio

- Requerido

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `domain:get`

Mostrar información detallada de un dominio

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] [<name>]
```


### `name`

El nombre de dominio


### `--property`, `-P`

Propiedad de dominio que se va a ver

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `domain:list`

Obtener una lista de todos los dominios

```bash
magento-cloud domains [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
domains
```

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: name*, ssl*, created_at*, updated_at (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `domain:update`

Actualización de un dominio

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

El nombre de dominio

- Requerido

### `--cert`

Ruta de acceso al archivo de certificado para este dominio

- Requiere un valor

### `--key`

Ruta de acceso al archivo de clave privada del certificado proporcionado.

- Requiere un valor

### `--chain`

Ruta de acceso al archivo o archivos de cadena de certificados para el certificado proporcionado

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:activate`

Activar un entorno

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

Los entornos que se van a activar

- Predeterminado: `[]`

- Matriz

### `--parent`

Establezca un nuevo entorno principal antes de activar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:branch`

Rama de un entorno

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

El ID (nombre de rama) del nuevo entorno


### `parent`

El elemento principal del nuevo entorno


### `--title`

El título del nuevo entorno

- Requiere un valor

### `--type`

El tipo de entorno nuevo

- Requiere un valor

### `--force`

Cree el nuevo entorno aunque la rama no se pueda desproteger localmente

- Predeterminado: `false`
- No acepta un valor

### `--no-clone-parent`

No clonar los datos de la rama principal

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:checkout`

Desproteger un entorno

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

El ID del entorno que se va a desproteger. Por ejemplo: &quot;sprint2&quot;


### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:curl`

Ejecutar una solicitud cURL autenticada en la API de un entorno

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

La ruta de API


### `--request`, `-X`

El método de solicitud que se va a utilizar

- Requiere un valor

### `--data`, `-d`

Datos para enviar

- Requiere un valor

### `--json`

Datos JSON para enviar

- Requiere un valor

### `--include`, `-i`

Incluir encabezados en la salida

- Predeterminado: `false`
- No acepta un valor

### `--head`, `-I`

Recuperar solo encabezados

- Predeterminado: `false`
- No acepta un valor

### `--disable-compression`

No utilice el indicador curl —compressed

- Predeterminado: `false`
- No acepta un valor

### `--enable-glob`

Habilitar globbing curl (eliminar el indicador —globoff)

- Predeterminado: `false`
- No acepta un valor

### `--fail`, `-f`

Error sin salida en respuesta a error

- Predeterminado: `false`
- No acepta un valor

### `--header`, `-H`

Encabezado(s) adicional(es)

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:delete`

Eliminar uno o más entornos

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--type TYPE] [-t|--only-type ONLY-TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [--inactive] [--merged] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

Los entornos que se van a eliminar. El carácter % puede utilizarse como comodín. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`

- Matriz

### `--delete-branch`

Eliminar ramas de Git (entornos inactivos)

- Predeterminado: `false`
- No acepta un valor

### `--no-delete-branch`

No elimine las ramas Git (entornos inactivos)

- Predeterminado: `false`
- No acepta un valor

### `--type`

Eliminar todos los entornos de un tipo (añadiendo a otros seleccionados) Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se dividirá por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--only-type`, `-t`

Eliminar solo los entornos de un tipo específico Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se dividirá por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude`

Entornos que no se van a eliminar. El carácter % puede utilizarse como comodín. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-type`

Tipos de entorno que no se deben eliminar Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se dividirá por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--inactive`

Eliminar todos los entornos inactivos (añadir a otros seleccionados)

- Predeterminado: `false`
- No acepta un valor

### `--merged`

Eliminar todos los entornos combinados (añadir a cualquier otro seleccionado)

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:http-access`

Actualizar la configuración de acceso HTTP de un entorno

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

### `--access`

Restricción de acceso con el formato &quot;permission:address&quot;. Utilice 0 para borrar todas las direcciones.

- Predeterminado: `[]`
- Requiere un valor

### `--auth`

Credenciales de autenticación HTTP Basic en el formato &quot;nombre de usuario:contraseña&quot;. Utilice 0 para borrar todas las credenciales.

- Predeterminado: `[]`
- Requiere un valor

### `--enabled`

Si el control de acceso debe habilitarse: 1 para habilitar, 0 para deshabilitar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:info`

Leer o establecer propiedades para un entorno

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
environment:metadata
```


### `property`

El nombre de la propiedad


### `value`

Establezca un nuevo valor para la propiedad


### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:init`

Inicializar un entorno desde un repositorio Git público

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

Una URL a un repositorio Git

- Requerido

### `--profile`

El nombre del perfil

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:list`

Obtener una lista de entornos

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
environments
```


```bash
env
```

### `--no-inactive`, `-I`

No mostrar entornos inactivos

- Predeterminado: `false`
- No acepta un valor

### `--pipe`

Envíe una lista sencilla de ID de entorno.

- Predeterminado: `false`
- No acepta un valor

### `--refresh`

Si se actualiza la lista.

- Predeterminado: `1`
- Requiere un valor

### `--sort`

Una propiedad por la que ordenar

- Predeterminado: `title`
- Requiere un valor

### `--reverse`

Ordenar en orden inverso (descendente)

- Predeterminado: `false`
- No acepta un valor

### `--type`

Filtre la lista por tipo(s) de entorno. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: id*, title*, status*, type*, created, machine_name, updated (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:logs`

Leer los registros de un entorno

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

El tipo de registro, p. ej. &quot;acceso&quot; o &quot;error&quot;


### `--lines`

Número de líneas que se van a mostrar

- Predeterminado: `100`
- Requiere un valor

### `--tail`

Seguir continuamente el registro

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:merge`

Combinar un entorno

```bash
magento-cloud merge [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
merge
```


### `environment`

El entorno para combinar


### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:push`

Insertar código en un entorno

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

La referencia de origen: un nombre de rama o hash de confirmación

- Predeterminado: `HEAD`


### `--target`

El nombre de la rama de destino

- Requiere un valor

### `--force`, `-f`

Permitir actualizaciones que no sean de avance rápido

- Predeterminado: `false`
- No acepta un valor

### `--force-with-lease`

Permitir actualizaciones que no sean de avance rápido, si la rama de seguimiento remoto está actualizada

- Predeterminado: `false`
- No acepta un valor

### `--set-upstream`, `-u`

Establezca el entorno de destino como flujo ascendente para la rama de origen

- Predeterminado: `false`
- No acepta un valor

### `--activate`

Activar el entorno antes de insertar

- Predeterminado: `false`
- No acepta un valor

### `--branch`

DEPRECATED: alias de —activate

- Predeterminado: `false`
- No acepta un valor

### `--parent`

Establecer el nuevo entorno principal (solo se usa con —activate)

- Requiere un valor

### `--type`

Defina el tipo de entorno (solo se usa con —activate )

- Requiere un valor

### `--no-clone-parent`

No clonar los datos de la rama principal (solo se usa con —activate)

- Predeterminado: `false`
- No acepta un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:redeploy`

Volver a implementar un entorno

```bash
magento-cloud redeploy [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:relationships`

Mostrar las relaciones de un entorno

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

El entorno


### `--property`, `-P`

La propiedad de relación que se va a ver

- Requiere un valor

### `--refresh`

Si se actualizan las relaciones

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:scp`

Copiar archivos desde y hacia el entorno actual mediante scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

Archivos para copiar. Utilice el prefijo remote: para definir ubicaciones remotas.

- Predeterminado: `[]`

- Matriz

### `--recursive`, `-r`

Copiar directorios completos de forma recursiva

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:set-remote`

Configurar el entorno remoto para que se asigne a una rama

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

El nombre de la máquina del entorno. Establezca el valor en 0 para eliminar la asignación de una rama

- Requerido

### `branch`

La rama Git que se va a asignar (el valor predeterminado es la rama actual)


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:ssh`

SSH al entorno actual

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

Un comando para ejecutar en el entorno.

- Predeterminado: `[]`

- Matriz

### `--pipe`

Envíe solo la dirección URL SSH.

- Predeterminado: `false`
- No acepta un valor

### `--all`

Mostrar todas las URL SSH (de cada aplicación).

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:synchronize`

Sincronizar el código o los datos de un entorno desde su elemento principal

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

Qué sincronizar: &quot;código&quot;, &quot;datos&quot; o ambos

- Predeterminado: `[]`

- Matriz

### `--rebase`

Sincronizar el código cambiando el nombre en lugar de combinarlo

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:url`

Obtener las direcciones URL públicas de un entorno

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
url
```

### `--primary`, `-1`

Devolver solo la dirección URL de la ruta principal

- Predeterminado: `false`
- No acepta un valor

### `--browser`

Explorador que se utiliza para abrir la dirección URL. Establezca 0 para ninguno.

- Requiere un valor

### `--pipe`

Envíe la URL a stdout.

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `environment:xdebug`

Abrir un túnel a Xdebug en el entorno

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```


```bash
xdebug
```

### `--port`

El puerto local

- Predeterminado: `9000`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:activity:get`

Ver información detallada sobre una sola actividad de integración

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

Un ID de integración. Déjelo en blanco para elegir de una lista.


### `activity`

El ID de actividad. El valor predeterminado es la actividad de integración más reciente.


### `--property`, `-P`

La propiedad que se va a ver

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

[Opción obsoleta, no utilizada]

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:activity:list`

Obtener una lista de actividades para una integración

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


```bash
i:act
```


```bash
integration:activities
```


### `id`

Un ID de integración. Déjelo en blanco para elegir de una lista.


### `--type`

Filtrar actividades por tipo. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--exclude-type`, `-x`

Excluir actividades por tipo. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco. El carácter % se puede utilizar como comodín para excluir tipos.

- Predeterminado: `[]`
- Requiere un valor

### `--limit`

Limitar el número de resultados mostrados

- Predeterminado: `10`
- Requiere un valor

### `--start`

Solo se enumerarán las actividades creadas antes de esta fecha

- Requiere un valor

### `--state`

Filtrar actividades por estado. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--result`

Filtrado de actividades por resultado

- Requiere un valor

### `--incomplete`, `-i`

Enumerar solo las actividades incompletas

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: id*, created*, description*, type*, state*, result*, completed (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

[Opción obsoleta, no utilizada]

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:activity:log`

Mostrar el registro de una actividad de integración

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

Un ID de integración. Déjelo en blanco para elegir de una lista.


### `activity`

El ID de actividad. El valor predeterminado es la actividad de integración más reciente.


### `--timestamps`, `-t`

Mostrar una marca de tiempo junto a cada mensaje

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

[Opción obsoleta, no utilizada]

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:add`

Añadir una integración al proyecto

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--type`

El tipo de integración (&quot;bitbucket&quot;, &quot;bitbucket_server&quot;, &quot;github&quot;, &quot;gitlab&quot;, &quot;webhook&quot;, &quot;health.email&quot;, &quot;health.pagerduty&quot;, &quot;health.slack&quot;, &quot;health.webhook&quot;, &quot;script&quot;, &quot;newrelic&quot;, &quot;splunk&quot;, &quot;sumologic&quot;, &quot;syslog&quot;)

- Requiere un valor

### `--base-url`

La URL base de la instalación del servidor

- Requiere un valor

### `--username`

Nombre de usuario del servidor Bitbucket

- Requiere un valor

### `--token`

Un token de autenticación o acceso para la integración

- Requiere un valor

### `--key`

Una clave de consumidor de OAuth de Bitbucket

- Requiere un valor

### `--secret`

Un secreto de consumidor de OAuth de Bitbucket

- Requiere un valor

### `--license-key`

Clave de licencia de registros de New Relic

- Requiere un valor

### `--server-project`

El proyecto (por ejemplo, &quot;área de nombres/repositorio&quot;)

- Requiere un valor

### `--repository`

El repositorio que se va a rastrear (p. ej. &quot;propietario/repositorio&quot;)

- Requiere un valor

### `--build-merge-requests`

GitLab: crear solicitudes de combinación como entornos

- Predeterminado: `true`
- Requiere un valor

### `--build-pull-requests`

Generar cada solicitud de extracción como un entorno

- Predeterminado: `true`
- Requiere un valor

### `--build-draft-pull-requests`

Generar solicitudes de extracción de borrador

- Predeterminado: `true`
- Requiere un valor

### `--build-pull-requests-post-merge`

Generar solicitudes de extracción en función de su estado posterior a la combinación

- Predeterminado: `false`
- Requiere un valor

### `--build-wip-merge-requests`

GitLab: crear solicitudes de combinación de WIP

- Predeterminado: `true`
- Requiere un valor

### `--merge-requests-clone-parent-data`

GitLab: clonar datos para solicitudes de combinación

- Predeterminado: `true`
- Requiere un valor

### `--pull-requests-clone-parent-data`

Clonar los datos del entorno principal para solicitudes de extracción

- Predeterminado: `true`
- Requiere un valor

### `--resync-pull-requests`

Volver a sincronizar los datos del entorno de solicitud de extracción en cada compilación

- Predeterminado: `false`
- Requiere un valor

### `--fetch-branches`

Recupere todas las ramas del remoto (como entornos inactivos)

- Predeterminado: `true`
- Requiere un valor

### `--prune-branches`

Eliminar ramas que no existen en el remoto

- Predeterminado: `true`
- Requiere un valor

### `--url`

Extremo de URL o API para la integración

- Requiere un valor

### `--shared-key`

Webhook: la clave secreta compartida de JWS

- Requiere un valor

### `--file`

Nombre de un archivo local que contiene el script que se va a cargar

- Requiere un valor

### `--events`

Una lista de eventos en los que actuar, p. ej. environment.push

- Predeterminado: `*`
- Requiere un valor

### `--states`

Una lista de estados en los que actuar, por ejemplo, pendiente, en curso, completo

- Predeterminado: `complete`
- Requiere un valor

### `--environments`

Los ID de entorno que se incluirán

- Predeterminado: `*`
- Requiere un valor

### `--excluded-environments`

Los ID de entorno que se excluirán

- Predeterminado: `[]`
- Requiere un valor

### `--from-address`

[Opcional] Dirección remitente personalizada para correos electrónicos de alerta

- Requiere un valor

### `--recipients`

Las direcciones de correo electrónico de los destinatarios

- Predeterminado: `[]`
- Requiere un valor

### `--channel`

El canal del Slack

- Requiere un valor

### `--routing-key`

La clave de enrutamiento PagerDuty

- Requiere un valor

### `--category`

La categoría Lógica de sumo, utilizada para filtrar

- Requiere un valor

### `--index`

El índice de Splunk

- Requiere un valor

### `--sourcetype`

El tipo de origen del evento Splunk

- Requiere un valor

### `--protocol`

Protocolo de transporte Syslog (&#39;tcp&#39;, &#39;udp&#39;, &#39;tls&#39;)

- Predeterminado: `tls`
- Requiere un valor

### `--syslog-host`

Host de recolector/relé Syslog

- Requiere un valor

### `--syslog-port`

Puerto de recolector/relé Syslog

- Requiere un valor

### `--facility`

Instalación de Syslog

- Predeterminado: `1`
- Requiere un valor

### `--message-format`

Formato de mensaje Syslog (&#39;rfc3164&#39; o &#39;rfc5424&#39;)

- Predeterminado: `rfc5424`
- Requiere un valor

### `--auth-mode`

Modo de autenticación (&quot;prefix&quot; o &quot;structured_data&quot;)

- Predeterminado: `prefix`
- Requiere un valor

### `--auth-token`

Token de autenticación

- Requiere un valor

### `--verify-tls`

Si la verificación de certificados HTTPS debe habilitarse (recomendado)

- Predeterminado: `true`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:delete`

Eliminación de una integración de un proyecto

```bash
magento-cloud integration:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

El ID de integración. Déjelo en blanco para elegir de una lista.


### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:get`

Visualización de detalles de una integración

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<id>]
```


### `id`

Un ID de integración. Déjelo en blanco para elegir de una lista.


### `--property`, `-P`

La propiedad de integración que se va a ver

- Acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:list`

Ver una lista de las integraciones del proyecto

```bash
magento-cloud integrations [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
integrations
```

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: ID, resumen, tipo. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:update`

Actualización de una integración

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

El ID de la integración que se va a actualizar


### `--type`

El tipo de integración (&quot;bitbucket&quot;, &quot;bitbucket_server&quot;, &quot;github&quot;, &quot;gitlab&quot;, &quot;webhook&quot;, &quot;health.email&quot;, &quot;health.pagerduty&quot;, &quot;health.slack&quot;, &quot;health.webhook&quot;, &quot;script&quot;, &quot;newrelic&quot;, &quot;splunk&quot;, &quot;sumologic&quot;, &quot;syslog&quot;)

- Requiere un valor

### `--base-url`

La URL base de la instalación del servidor

- Requiere un valor

### `--username`

Nombre de usuario del servidor Bitbucket

- Requiere un valor

### `--token`

Un token de autenticación o acceso para la integración

- Requiere un valor

### `--key`

Una clave de consumidor de OAuth de Bitbucket

- Requiere un valor

### `--secret`

Un secreto de consumidor de OAuth de Bitbucket

- Requiere un valor

### `--license-key`

Clave de licencia de registros de New Relic

- Requiere un valor

### `--server-project`

El proyecto (por ejemplo, &quot;área de nombres/repositorio&quot;)

- Requiere un valor

### `--repository`

El repositorio que se va a rastrear (p. ej. &quot;propietario/repositorio&quot;)

- Requiere un valor

### `--build-merge-requests`

GitLab: crear solicitudes de combinación como entornos

- Predeterminado: `true`
- Requiere un valor

### `--build-pull-requests`

Generar cada solicitud de extracción como un entorno

- Predeterminado: `true`
- Requiere un valor

### `--build-draft-pull-requests`

Generar solicitudes de extracción de borrador

- Predeterminado: `true`
- Requiere un valor

### `--build-pull-requests-post-merge`

Generar solicitudes de extracción en función de su estado posterior a la combinación

- Predeterminado: `false`
- Requiere un valor

### `--build-wip-merge-requests`

GitLab: crear solicitudes de combinación de WIP

- Predeterminado: `true`
- Requiere un valor

### `--merge-requests-clone-parent-data`

GitLab: clonar datos para solicitudes de combinación

- Predeterminado: `true`
- Requiere un valor

### `--pull-requests-clone-parent-data`

Clonar los datos del entorno principal para solicitudes de extracción

- Predeterminado: `true`
- Requiere un valor

### `--resync-pull-requests`

Volver a sincronizar los datos del entorno de solicitud de extracción en cada compilación

- Predeterminado: `false`
- Requiere un valor

### `--fetch-branches`

Recupere todas las ramas del remoto (como entornos inactivos)

- Predeterminado: `true`
- Requiere un valor

### `--prune-branches`

Eliminar ramas que no existen en el remoto

- Predeterminado: `true`
- Requiere un valor

### `--url`

Extremo de URL o API para la integración

- Requiere un valor

### `--shared-key`

Webhook: la clave secreta compartida de JWS

- Requiere un valor

### `--file`

Nombre de un archivo local que contiene el script que se va a cargar

- Requiere un valor

### `--events`

Una lista de eventos en los que actuar, p. ej. environment.push

- Predeterminado: `*`
- Requiere un valor

### `--states`

Una lista de estados en los que actuar, por ejemplo, pendiente, en curso, completo

- Predeterminado: `complete`
- Requiere un valor

### `--environments`

Los ID de entorno que se incluirán

- Predeterminado: `*`
- Requiere un valor

### `--excluded-environments`

Los ID de entorno que se excluirán

- Predeterminado: `[]`
- Requiere un valor

### `--from-address`

[Opcional] Dirección remitente personalizada para correos electrónicos de alerta

- Requiere un valor

### `--recipients`

Las direcciones de correo electrónico de los destinatarios

- Predeterminado: `[]`
- Requiere un valor

### `--channel`

El canal del Slack

- Requiere un valor

### `--routing-key`

La clave de enrutamiento PagerDuty

- Requiere un valor

### `--category`

La categoría Lógica de sumo, utilizada para filtrar

- Requiere un valor

### `--index`

El índice de Splunk

- Requiere un valor

### `--sourcetype`

El tipo de origen del evento Splunk

- Requiere un valor

### `--protocol`

Protocolo de transporte Syslog (&#39;tcp&#39;, &#39;udp&#39;, &#39;tls&#39;)

- Predeterminado: `tls`
- Requiere un valor

### `--syslog-host`

Host de recolector/relé Syslog

- Requiere un valor

### `--syslog-port`

Puerto de recolector/relé Syslog

- Requiere un valor

### `--facility`

Instalación de Syslog

- Predeterminado: `1`
- Requiere un valor

### `--message-format`

Formato de mensaje Syslog (&#39;rfc3164&#39; o &#39;rfc5424&#39;)

- Predeterminado: `rfc5424`
- Requiere un valor

### `--auth-mode`

Modo de autenticación (&quot;prefix&quot; o &quot;structured_data&quot;)

- Predeterminado: `prefix`
- Requiere un valor

### `--auth-token`

Token de autenticación

- Requiere un valor

### `--verify-tls`

Si la verificación de certificados HTTPS debe habilitarse (recomendado)

- Predeterminado: `true`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `integration:validate`

Validación de una integración existente

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--] [<id>]
```


### `id`

Un ID de integración. Déjelo en blanco para elegir de una lista.


### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `local:build`

Generar el proyecto actual localmente

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


```bash
build
```


### `app`

Especificar las aplicaciones que se van a generar

- Predeterminado: `[]`

- Matriz

### `--abslinks`, `-a`

Uso de vínculos absolutos

- Predeterminado: `false`
- No acepta un valor

### `--source`, `-s`

El directorio de origen. El valor predeterminado es la raíz del proyecto actual.

- Requiere un valor

### `--destination`, `-d`

El destino al que se enlazará simbólicamente la raíz web de cada aplicación. Valor predeterminado: _www

- Requiere un valor

### `--copy`, `-c`

Copie en un directorio de compilación, en lugar de realizar enlaces simbólicos desde el origen

- Predeterminado: `false`
- No acepta un valor

### `--clone`

Utilice Git para clonar el HEAD actual en el directorio de compilación

- Predeterminado: `false`
- No acepta un valor

### `--run-deploy-hooks`

Ejecutar vínculos de implementación o post_deploy

- Predeterminado: `false`
- No acepta un valor

### `--no-clean`

No eliminar las compilaciones antiguas

- Predeterminado: `false`
- No acepta un valor

### `--no-archive`

No cree ni utilice un archivo de compilación

- Predeterminado: `false`
- No acepta un valor

### `--no-backup`

No realizar copia de seguridad de la versión anterior

- Predeterminado: `false`
- No acepta un valor

### `--no-cache`

Deshabilitar almacenamiento en caché

- Predeterminado: `false`
- No acepta un valor

### `--no-build-hooks`

No ejecutar vínculos posteriores a la compilación

- Predeterminado: `false`
- No acepta un valor

### `--no-deps`

No instale las dependencias de compilación localmente

- Predeterminado: `false`
- No acepta un valor

### `--working-copy`

Borrado: utilice Git para clonar un repositorio de cada módulo de Drupal en lugar de simplemente descargar una versión

- Predeterminado: `false`
- No acepta un valor

### `--concurrency`

Borrado: define el número de proyectos simultáneos que se procesarán al mismo tiempo

- Predeterminado: `4`
- Requiere un valor

### `--lock`

Borrado: crear o actualizar un archivo de bloqueo (solo disponible con la versión 7 o posterior de Borrado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `local:clean`

Eliminar compilaciones de proyecto antiguas

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```


```bash
clean
```

### `--keep`

Número máximo de compilaciones que se deben mantener

- Predeterminado: `5`
- Requiere un valor

### `--max-age`

La antigüedad máxima de las compilaciones, en segundos. Se ignora si no se establece.

- Requiere un valor

### `--include-active`

Eliminar las compilaciones activas también

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `local:dir`

Buscar la raíz del proyecto local

```bash
magento-cloud dir [<subdir>]
```


```bash
dir
```


### `subdir`

El subdirectorio que se busca (&quot;local&quot;, &quot;web&quot; o &quot;compartido&quot;)


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `metrics:disk-usage`

Mostrar el uso del disco en un servicio

```bash
magento-cloud disk [-s|--service SERVICE] [--type TYPE] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-B|--bytes] [-1|--latest] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
disk
```

### `--service`, `-s`

El nombre del servicio

- Requiere un valor

### `--type`

El tipo de servicio (si no se proporciona el nombre del servicio), por ejemplo, mysql, pgsql, mongodb, etc. No se requiere la versión del tipo.

- Requiere un valor

### `--range`, `-r`

El intervalo de tiempo. Las métricas se cargarán durante esta duración hasta la hora de finalización (—to). Puede especificar unidades: horas (h), minutos (m) o segundos (s). Mínimo &lt;comment>5 m&lt;/comment>, máximo &lt;comment>8 h&lt;/comment> o más (según el proyecto), predeterminado &lt;comment>10 m&lt;/comment>.

- Requiere un valor

### `--interval`, `-i`

El intervalo de tiempo. El valor predeterminado es una división del intervalo. Puede especificar unidades: horas (h), minutos (m) o segundos (s). Mínimo &lt;comment>1 m&lt;/comment>, máximo &lt;comment>1 h&lt;/comment>.

- Requiere un valor

### `--to`

La hora final. El valor predeterminado es ahora.

- Requiere un valor

### `--bytes`, `-B`

Mostrar tamaños en bytes

- Predeterminado: `false`
- No acepta un valor

### `--latest`, `-1`

Mostrar solo el último punto de datos individual

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: timestamp*, used*, limit*, percent*, ipercent*, limit, interval, iused (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `mount:download`

Descargar archivos desde un montaje mediante rsync

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--all`, `-a`

Descargar desde todos los montajes

- Predeterminado: `false`
- No acepta un valor

### `--mount`, `-m`

El montaje (como ruta relativa a la aplicación)

- Requiere un valor

### `--target`

El directorio en el que se descargarán los archivos. Si se utiliza —all, se anexará la ruta de montaje

- Requiere un valor

### `--source-path`

Utilice la ruta de origen del montaje (en lugar de la ruta de montaje) como subdirectorio del destino, cuando se utiliza —all

- Predeterminado: `false`
- No acepta un valor

### `--delete`

Si se eliminarán archivos prescindibles en el directorio de destino

- Predeterminado: `false`
- No acepta un valor

### `--exclude`

Archivos que se excluirán de la descarga (patrón)

- Predeterminado: `[]`
- Requiere un valor

### `--include`

Archivos para incluir en la descarga (patrón)

- Predeterminado: `[]`
- Requiere un valor

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `mount:list`

Obtener una lista de montajes

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```


```bash
mounts
```

### `--paths`

Salida de las rutas de montaje solamente (una por línea)

- Predeterminado: `false`
- No acepta un valor

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: definición, ruta. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `mount:size`

Compruebe el uso de los soportes en el disco

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--bytes`, `-B`

Mostrar tamaños en bytes

- Predeterminado: `false`
- No acepta un valor

### `--refresh`

Actualizar la caché

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: available, max, mounts, percent_used, tamaños, used. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `mount:upload`

Cargar archivos a un montaje mediante rsync

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--source`

Directorio que contiene los archivos que se van a cargar

- Requiere un valor

### `--mount`, `-m`

El montaje (como ruta relativa a la aplicación)

- Requiere un valor

### `--delete`

Si se eliminarán archivos superfluos en el montaje

- Predeterminado: `false`
- No acepta un valor

### `--exclude`

Archivos que se excluirán de la carga (patrón)

- Predeterminado: `[]`
- Requiere un valor

### `--include`

Archivos para incluir en la carga (patrón)

- Predeterminado: `[]`
- Requiere un valor

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--worker`

Un nombre de trabajador

- Requiere un valor

### `--instance`, `-I`

Un ID de instancia

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:clear-build-cache`

Borrar la memoria caché de la versión de un proyecto

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT]
```

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:curl`

Ejecutar una solicitud cURL autenticada en la API de un proyecto

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--] [<path>]
```


### `path`

La ruta de API


### `--request`, `-X`

El método de solicitud que se va a utilizar

- Requiere un valor

### `--data`, `-d`

Datos para enviar

- Requiere un valor

### `--json`

Datos JSON para enviar

- Requiere un valor

### `--include`, `-i`

Incluir encabezados en la salida

- Predeterminado: `false`
- No acepta un valor

### `--head`, `-I`

Recuperar solo encabezados

- Predeterminado: `false`
- No acepta un valor

### `--disable-compression`

No utilice el indicador curl —compressed

- Predeterminado: `false`
- No acepta un valor

### `--enable-glob`

Habilitar globbing curl (eliminar el indicador —globoff)

- Predeterminado: `false`
- No acepta un valor

### `--fail`, `-f`

Error sin salida en respuesta a error

- Predeterminado: `false`
- No acepta un valor

### `--header`, `-H`

Encabezado(s) adicional(es)

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:get`

Clonar un proyecto localmente

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

El ID del proyecto


### `directory`

El directorio en el que clonar. Valores predeterminados del título del proyecto


### `--environment`, `-e`

El ID de entorno que se va a clonar. Valores predeterminados del proyecto o el primer entorno disponible

- Requiere un valor

### `--depth`

Crear un clon superficial: limitar el número de confirmaciones en el historial

- Requiere un valor

### `--build`

Cree el proyecto después de la clonación

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:info`

Leer o establecer las propiedades de un proyecto

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
project:metadata
```


### `property`

El nombre de la propiedad


### `value`

Establezca un nuevo valor para la propiedad


### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:list`

Obtener una lista de todos los proyectos activos

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

Presente una lista sencilla de ID de proyecto. Deshabilita la paginación.

- Predeterminado: `false`
- No acepta un valor

### `--host`

Filtrar por nombre de host de región (coincidencia exacta)

- Requiere un valor

### `--title`

Filtrar por título (búsqueda sin distinción de mayúsculas y minúsculas)

- Requiere un valor

### `--my`

Mostrar solo los proyectos de su propiedad

- Predeterminado: `false`
- No acepta un valor

### `--refresh`

Si se actualiza la lista

- Predeterminado: `1`
- Requiere un valor

### `--sort`

Una propiedad por la que ordenar

- Predeterminado: `title`
- Requiere un valor

### `--reverse`

Ordenar en orden inverso (descendente)

- Predeterminado: `false`
- No acepta un valor

### `--page`

Número de página. Esto habilita la paginación, a pesar de la configuración de o —count. Se ignora si se especifica —pipe.

- Requiere un valor

### `--count`, `-c`

El número de proyectos que se mostrarán por página. Utilice 0 para desactivar la paginación. Se ignora si se especifica —page.

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`

Columnas para mostrar. Columnas disponibles: id*, title*, region*, created_at, endpoint, organization_id, organization_label, organization_name, region_label, status, ui_url (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:set-remote`

Establecer el proyecto remoto para el repositorio Git actual

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

El ID del proyecto


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Eliminar una variable de un proyecto

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

El nombre de la variable

- Requerido

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Ver las variables de un proyecto

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<name>]
```


```bash
project-variables
```


```bash
pvget
```


```bash
project:variable:list
```


### `name`

Nombre de la variable


### `--pipe`

Mostrar solo el valor completo de la variable (se debe especificar un &quot;nombre&quot;)

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Establecer una variable para un proyecto

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

El nombre de la variable

- Requerido

### `value`

El valor de variable

- Requerido

### `--json`

Marcar el valor como JSON

- Predeterminado: `false`
- No acepta un valor

### `--no-visible-build`

No exponer esta variable en el momento de la compilación

- Predeterminado: `false`
- No acepta un valor

### `--no-visible-runtime`

No exponer esta variable durante la ejecución

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `repo:cat`

Leer un archivo en el repositorio del proyecto

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

La ruta al archivo

- Requerido

### `--commit`, `-c`

El SHA de compromiso. Esto también puede aceptar sufijos de &quot;HEAD&quot; y acento circunflejo (^) o tilde (~) para confirmaciones principales.

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `repo:ls`

Enumerar archivos en el repositorio del proyecto

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

La ruta a un subdirectorio


### `--directories`, `-d`

Mostrar solo directorios

- Predeterminado: `false`
- No acepta un valor

### `--files`, `-f`

Mostrar solo archivos

- Predeterminado: `false`
- No acepta un valor

### `--git-style`

Salida de estilo similar a &quot;git ls-tree&quot;

- Predeterminado: `false`
- No acepta un valor

### `--commit`, `-c`

El SHA de compromiso. Esto también puede aceptar sufijos de &quot;HEAD&quot; y acento circunflejo (^) o tilde (~) para confirmaciones principales.

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `repo:read`

Leer un directorio o archivo en el repositorio del proyecto

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

La ruta al directorio o archivo


### `--commit`, `-c`

El SHA de compromiso. Esto también puede aceptar sufijos de &quot;HEAD&quot; y acento circunflejo (^) o tilde (~) para confirmaciones principales.

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `route:get`

Ver información detallada sobre una ruta

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

La URL original de la ruta


### `--id`

ID de ruta que se va a seleccionar

- Requiere un valor

### `--primary`, `-1`

Seleccionar la ruta principal

- Predeterminado: `false`
- No acepta un valor

### `--property`, `-P`

La propiedad que se va a mostrar

- Requiere un valor

### `--refresh`

Omitir la caché de rutas

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

[Opción obsoleta, ya no se utiliza]

- Requiere un valor

### `--identity-file`, `-i`

[Opción obsoleta, ya no se utiliza]

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `route:list`

Enumerar todas las rutas de un entorno

```bash
magento-cloud routes [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

El ID de entorno


### `--refresh`

Omitir la caché de rutas

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: route*, type*, to*, url (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `self:install`

Instalar o actualizar archivos de configuración de CLI

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```


```bash
local:install
```

### `--shell-type`

El tipo de shell para el autocompletado (bash o zsh)

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `self:stats`

Ver estadísticas de descargas de paquetes de GitHub

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

Número de página

- Predeterminado: `1`
- Requiere un valor

### `--count`, `-c`

Resultados por página (máximo: 100)

- Predeterminado: `20`
- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`

Columnas para mostrar. Columnas disponibles: recurso, fecha, descargas, versión. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `self:update`

Actualice la CLI a la versión más reciente

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```


```bash
self-update
```


```bash
update
```

### `--no-major`

Actualizar solo entre versiones secundarias o de parche

- Predeterminado: `false`
- No acepta un valor

### `--unstable`

Actualizar a una nueva versión inestable, si está disponible

- Predeterminado: `false`
- No acepta un valor

### `--manifest`

Omitir la ubicación del archivo de manifiesto

- Requiere un valor

### `--current-version`

Anular la versión actual

- Requiere un valor

### `--timeout`

Tiempo de espera para la comprobación de versión

- Predeterminado: `30`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `service:list`

Enumerar servicios en el proyecto

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
services
```

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: disco, nombre, tamaño, tipo. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `service:mongo:dump`

Crear un volcado de archivo binario de datos de MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

### `--collection`, `-c`

Colección que se va a volcar

- Requiere un valor

### `--gzip`, `-z`

Comprimir el volcado utilizando gzip

- Predeterminado: `false`
- No acepta un valor

### `--stdout`, `-o`

Salida a STDOUT en lugar de a un archivo

- Predeterminado: `false`
- No acepta un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `service:mongo:export`

Exportación de datos de MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

### `--collection`, `-c`

Colección que se va a exportar

- Requiere un valor

### `--jsonArray`

Exportar datos como una sola matriz JSON

- Predeterminado: `false`
- No acepta un valor

### `--type`

El tipo de exportación, p. ej. &quot;csv&quot;

- Requiere un valor

### `--fields`, `-f`

Los campos que se van a exportar

- Predeterminado: `[]`
- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `service:mongo:restore`

Restaurar un archivo binario volcado de datos en MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

### `--collection`, `-c`

Colección que se va a restaurar

- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `service:mongo:shell`

Usar el shell de MongoDB

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

### `--eval`

Pase un fragmento de JavaScript al shell

- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `service:redis-cli`

Acceso a la CLI de Redis

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


```bash
redis
```


### `args`

Argumentos para agregar al comando Redis


### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Cambio entre sesiones

```bash
magento-cloud session:switch [<id>]
```


### `id`

El nuevo ID de sesión


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `snapshot:create`

Crear una instantánea de un entorno

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
backup
```


```bash
backup:create
```


```bash
environment:backup
```


### `environment`

El entorno


### `--live`

Copia de seguridad en vivo: no detenga el entorno. Si se establece, el entorno se mantendrá en ejecución y abierto a las conexiones durante la copia de seguridad. Esto reduce el tiempo de inactividad, con el riesgo de realizar copias de seguridad de los datos en un estado incoherente.

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--unsafe`

Opción obsoleta: usar —live en su lugar

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `snapshot:list`

Enumerar las instantáneas disponibles de un entorno

```bash
magento-cloud snapshots [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
snapshots
```


```bash
backups
```


```bash
backup:list
```

### `--limit`

[Obsoleto] - esta opción no se utiliza

- Requiere un valor

### `--start`

[Obsoleto] - esta opción no se utiliza

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `snapshot:restore`

Restaurar una instantánea de entorno

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

Nombre de la instantánea. Valores predeterminados del más reciente


### `--target`

El entorno en el que restaurar. Valores predeterminados del entorno actual de la instantánea

- Requiere un valor

### `--branch-from`

Si —target aún no existe, especifica el elemento principal del nuevo entorno

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Ejecutar una operación de origen

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

El nombre de la operación

- Requerido

### `--variable`

Variable que se va a establecer durante la operación con el formato &lt;info>type:nombre=valor&lt;/info>

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `ssh-cert:info`

Mostrar información sobre el certificado SSH actual

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

### `--no-refresh`

No actualice el certificado si no es válido

- Predeterminado: `false`
- No acepta un valor

### `--property`, `-P`

Propiedad del certificado que se va a mostrar

- Requiere un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `ssh-cert:load`

Generación de un certificado SSH

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

### `--refresh-only`

Actualice el certificado solo si es necesario (no escriba la configuración SSH)

- Predeterminado: `false`
- No acepta un valor

### `--new`

Forzar la actualización del certificado

- Predeterminado: `false`
- No acepta un valor

### `--new-key`

[Obsoleto] Utilice —new en su lugar

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `ssh-key:add`

Añadir una nueva clave SSH

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

La ruta a una clave pública SSH existente


### `--name`

Un nombre para identificar la clave

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `ssh-key:delete`

Eliminación de una clave SSH

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

El ID de la clave SSH que se va a eliminar


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `ssh-key:list`

Obtenga una lista de claves SSH en su cuenta

```bash
magento-cloud ssh-keys [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: id*, title*, path*, huella digital (* = columnas predeterminadas). El carácter &quot;+&quot; se puede utilizar como marcador de posición para las columnas predeterminadas. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `subscription:info`

Leer o modificar propiedades de suscripción

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<property>] [<value>]
```


### `property`

El nombre de la propiedad


### `value`

Establezca un nuevo valor para la propiedad


### `--id`, `-s`

ID de suscripción

- Requiere un valor

### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)

- Predeterminado: `c`
- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `tunnel:close`

Cierre de túneles SSH

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

Cerrar todos los túneles

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `tunnel:info`

Ver información de relación para túneles SSH

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

### `--property`, `-P`

La propiedad de relación que se va a ver

- Requiere un valor

### `--encode`, `-c`

Salida como JSON con codificación base64

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `tunnel:list`

Enumeración de túneles SSH

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
tunnels
```

### `--all`, `-a`

Ver todos los túneles

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `tunnel:open`

Apertura de túneles SSH para las relaciones de una aplicación

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

Permitir que los hosts remotos se conecten a los puertos reenviados locales

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `tunnel:single`

Apertura de un solo túnel SSH para una relación de aplicación

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

### `--port`

El puerto local

- Requiere un valor

### `--gateway-ports`, `-g`

Permitir que los hosts remotos se conecten a los puertos reenviados locales

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--app`, `-A`

El nombre de la aplicación remota

- Requiere un valor

### `--relationship`, `-r`

La relación de servicio que se va a utilizar

- Requiere un valor

### `--identity-file`, `-i`

Una identidad SSH (clave privada) que utilizar

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `user:add`

Agregar un usuario al proyecto

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

La dirección de correo electrónico del usuario


### `--role`, `-r`

La función de proyecto del usuario (&quot;administrador&quot; o &quot;visualizador&quot;) o la función de tipo de entorno (por ejemplo, &quot;ensayo:colaborador&quot; o &quot;producción:visualizador&quot;). Para quitar un usuario de un tipo de entorno, establezca la función como &quot;ninguno&quot;. El carácter % se puede usar como comodín para el tipo de entorno, p. ej. &#39;%:viewer&#39; para dar al usuario la función &#39;viewer&#39; en todos los tipos. La función puede abreviarse, por ejemplo, &quot;producción:v&quot;.

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `user:delete`

Eliminar un usuario del proyecto

```bash
magento-cloud user:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

La dirección de correo electrónico del usuario

- Requerido

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `user:get`

Ver las funciones de un usuario

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

La dirección de correo electrónico del usuario


### `--level`, `-l`

El nivel de función (&quot;proyecto&quot; o &quot;entorno&quot;)

- Requiere un valor

### `--pipe`

Enviar la función a stdout (después de realizar cualquier cambio)

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--role`, `-r`

[Obsoleto: usar user:update para cambiar las funciones de un usuario]

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `user:list`

Enumerar usuarios de proyecto

```bash
magento-cloud users [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
users
```

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: correo electrónico, ID, nombre, función. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `user:update`

Actualización de las funciones del usuario en un proyecto

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

La dirección de correo electrónico del usuario


### `--role`, `-r`

La función de proyecto del usuario (&quot;administrador&quot; o &quot;visualizador&quot;) o la función de tipo de entorno (por ejemplo, &quot;ensayo:colaborador&quot; o &quot;producción:visualizador&quot;). Para quitar un usuario de un tipo de entorno, establezca la función como &quot;ninguno&quot;. El carácter % se puede usar como comodín para el tipo de entorno, p. ej. &#39;%:viewer&#39; para dar al usuario la función &#39;viewer&#39; en todos los tipos. La función puede abreviarse, por ejemplo, &quot;producción:v&quot;.

- Predeterminado: `[]`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:create`

Crear una variable

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

El nombre de la variable


### `--level`, `-l`

Nivel en el que se va a establecer la variable (&quot;proyecto&quot; o &quot;entorno&quot;)

- Requiere un valor

### `--name`

El nombre de la variable

- Requiere un valor

### `--value`

El valor de la variable

- Requiere un valor

### `--json`

Si la variable tiene formato JSON

- Predeterminado: `false`
- Requiere un valor

### `--sensitive`

Si la variable es confidencial

- Predeterminado: `false`
- Requiere un valor

### `--prefix`

Prefijo del nombre de la variable (por ejemplo, &quot;none&quot; o &quot;env:&quot;)

- Predeterminado: `none`
- Requiere un valor

### `--enabled`

Si la variable debe habilitarse

- Predeterminado: `true`
- Requiere un valor

### `--inheritable`

Si los entornos secundarios heredan la variable

- Predeterminado: `true`
- Requiere un valor

### `--visible-build`

Si la variable debe ser visible en el momento de la compilación

- Requiere un valor

### `--visible-runtime`

Si la variable debe ser visible durante la ejecución

- Predeterminado: `true`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:delete`

Eliminar una variable

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

El nombre de la variable

- Requerido

### `--level`, `-l`

El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)

- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Deshabilitar una variable de nivel de entorno habilitada

```bash
magento-cloud variable:disable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nombre de la variable

- Requerido

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Habilitar una variable de entorno deshabilitada

```bash
magento-cloud variable:enable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nombre de la variable

- Requerido

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:get`

Ver una variable

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


```bash
vget
```


### `name`

Nombre de la variable


### `--property`, `-P`

Ver una sola propiedad de variable

- Requiere un valor

### `--level`, `-l`

El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--pipe`

[Opción obsoleta] Mostrar solo el valor de la variable

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:list`

Variables de lista

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: is_enabled, level, name, value. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Establecer una variable para un entorno

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

El nombre de la variable

- Requerido

### `value`

El valor de variable

- Requerido

### `--json`

Marcar el valor como JSON

- Predeterminado: `false`
- No acepta un valor

### `--disabled`

Marcar la variable como deshabilitada

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `variable:update`

Actualización de una variable

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

El nombre de la variable

- Requerido

### `--level`, `-l`

El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)

- Requiere un valor

### `--value`

El valor de la variable

- Requiere un valor

### `--json`

Si la variable tiene formato JSON

- Predeterminado: `false`
- Requiere un valor

### `--sensitive`

Si la variable es confidencial

- Predeterminado: `false`
- Requiere un valor

### `--enabled`

Si la variable debe habilitarse

- Predeterminado: `true`
- Requiere un valor

### `--inheritable`

Si los entornos secundarios heredan la variable

- Predeterminado: `true`
- Requiere un valor

### `--visible-build`

Si la variable debe ser visible en el momento de la compilación

- Requiere un valor

### `--visible-runtime`

Si la variable debe ser visible durante la ejecución

- Predeterminado: `true`
- Requiere un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--no-wait`, `-W`

No espere a que se complete la operación

- Predeterminado: `false`
- No acepta un valor

### `--wait`

Espere a que se complete la operación (valor predeterminado)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `version:list`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Enumerar versiones de entornos

```bash
magento-cloud versions [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
versions
```

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor


## `worker:list`

Obtener una lista de todos los trabajadores implementados

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
workers
```

### `--refresh`

Si se actualiza la caché

- Predeterminado: `false`
- No acepta un valor

### `--project`, `-p`

El ID o la URL del proyecto

- Requiere un valor

### `--host`

Opción obsoleta, ya no se utiliza

- Requiere un valor

### `--environment`, `-e`

El ID de entorno

- Requiere un valor

### `--format`

El formato de salida: tabla, csv, tsv o sin formato

- Predeterminado: `table`
- Requiere un valor

### `--columns`, `-c`

Columnas para mostrar. Columnas disponibles: comandos, nombre, tipo. Si una lista se proporciona como un valor único (por ejemplo, &quot;a,b,c&quot;), se divide por comas o espacios en blanco.

- Predeterminado: `[]`
- Requiere un valor

### `--no-header`

No generar el encabezado de tabla

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumentar el detalle de los mensajes

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

- Predeterminado: `false`
- No acepta un valor

### `--yes`, `-y`

Responder &quot;sí&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--no-interaction`

No haga ninguna pregunta interactiva; acepte los valores predeterminados. Equivale a usar la variable de entorno: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predeterminado: `false`
- No acepta un valor

### `--ansi`

Forzar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no-ansi`

Deshabilitar salida ANSI

- Predeterminado: `false`
- No acepta un valor

### `--no`, `-n`

Responder &quot;no&quot; a las preguntas de confirmación; aceptar el valor predeterminado para otras preguntas; deshabilitar la interacción

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor
