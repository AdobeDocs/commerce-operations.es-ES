---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce en infraestructura de nube)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versión**: 1,38,1 <!-- app.version -->

Esta referencia contiene 127 comandos disponibles a través del `magento-cloud` herramienta de línea de comandos.
La lista inicial se genera automáticamente usando la variable `magento-cloud list` en la edición.

>[!NOTE]
>
>Esta referencia se genera a partir de la base de código de la aplicación. Para cambiar el contenido, puede actualizar el código fuente para la implementación de comandos correspondiente en la [código](https://github.com/magento) y envíe los cambios para su revisión. Otra forma es _Envíenos sus comentarios_ (busque el vínculo en la parte superior derecha). Para ver las directrices de contribución, consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

gancho de finalización de BASH.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



Genere código BASH que configure la finalización para esta aplicación.
- Predeterminado: `false`
- No acepta un valor



### `--program`, `-p`



Nombre del programa que debe completarse el déclencheur &lt;comment>(el valor predeterminado es la ruta absoluta de la aplicación)&lt;/comment>.
- Requiere un valor



### `--multiple`, `-m`



El gancho generado se puede usar para varias aplicaciones.
- Predeterminado: `false`
- No acepta un valor


### `--shell-type`

Establezca el tipo de shell (zsh o bash). De lo contrario, esto se determina automáticamente.
- Acepta un valor <!-- options --> <!-- options.size -->

## `bot`

El bot de la nube Magento

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `clear-cache`

Borre la caché de CLI

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `decode`

Decode una cadena codificada como MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

El valor de la variable que se va a descodificar
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad que se va a ver en la variable
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `docs`

Abra la documentación en línea

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

Términos de búsqueda

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

El explorador que se utilizará para abrir la dirección URL. Establezca 0 para ninguno.
- Requiere un valor


### `--pipe`

Incluya la dirección URL para stdout.
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `help`

Muestra ayuda para un comando

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

El nombre del comando
- Predeterminado: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `legacy-migrate`

Migración desde la estructura de archivos heredada

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

No cree una copia de seguridad del proyecto.
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `list`

Listas, comandos

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

El nombre del área de nombres
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Para generar la lista de comandos sin procesar
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (txt, xml, json o md)
- Predeterminado: `txt`
- Requiere un valor <!-- options --> <!-- options.size -->

## `multi`

Ejecutar un comando en varios proyectos

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

El comando que se va a ejecutar
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



Una lista de ID de proyecto separados por comas o espacios en blanco
- Requiere un valor


### `--continue`

Continuar ejecutando comandos incluso si se encuentra una excepción
- Predeterminado: `false`
- No acepta un valor


### `--sort`

Una propiedad mediante la cual ordenar la lista de opciones de proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `web`

Abrir la interfaz de usuario web

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

El explorador que se utilizará para abrir la dirección URL. Establezca 0 para ninguno.
- Requiere un valor


### `--pipe`

Incluya la dirección URL para stdout.
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `welcome`

Bienvenido a Magento Cloud

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `activity:cancel`

Cancelar una actividad

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de actividad. El valor predeterminado es la actividad cancelable más reciente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtrar por tipo (al seleccionar una actividad predeterminada)
- Requiere un valor



### `--all`, `-a`



Comprobar actividades recientes en todos los entornos (al seleccionar una actividad predeterminada)
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `activity:get`

Ver información detallada sobre una sola actividad

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de actividad. El valor predeterminado es la actividad más reciente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad que se va a ver
- Requiere un valor


### `--type`

Filtrar por tipo (al seleccionar una actividad predeterminada)
- Requiere un valor


### `--state`

Filtrar por estado (al seleccionar una actividad predeterminada): in_progress, pendiente, completado o cancelado
- Predeterminado: `[]`
- Requiere un valor


### `--result`

Filtrar por resultado (al seleccionar una actividad predeterminada): éxito o fracaso
- Requiere un valor



### `--incomplete`, `-i`



Incluir solo actividades incompletas (al seleccionar una actividad predeterminada). Esto es una abreviatura para &lt;info>—state=in_progress,pendiente&lt;/info>
- Predeterminado: `false`
- No acepta un valor



### `--all`, `-a`



Comprobar actividades recientes en todos los entornos (al seleccionar una actividad predeterminada)
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `activity:list`

Obtener una lista de actividades para un entorno o proyecto

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Filtrar actividades por tipo
- Requiere un valor


### `--limit`

Limitar el número de resultados mostrados
- Predeterminado: `10`
- Requiere un valor


### `--start`

Solo se enumerarán las actividades creadas antes de esta fecha
- Requiere un valor


### `--state`

Filtrar actividades por estado: in_progress, pendiente, completado o cancelado
- Predeterminado: `[]`
- Requiere un valor


### `--result`

Filtrar actividades por resultado: éxito o fracaso
- Requiere un valor



### `--incomplete`, `-i`



Enumerar solo actividades incompletas
- Predeterminado: `false`
- No acepta un valor



### `--all`, `-a`



Enumerar actividades en todos los entornos
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `activity:log`

Mostrar el registro de una actividad

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de actividad. El valor predeterminado es la actividad más reciente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Intervalo de actualización de la actividad (segundos). Establézcalo en 0 para desactivar la actualización.
- Predeterminado: `3`
- Requiere un valor



### `--timestamps`, `-t`



Mostrar una marca de tiempo junto a cada mensaje
- Predeterminado: `false`
- No acepta un valor


### `--type`

Filtrar por tipo (al seleccionar una actividad predeterminada)
- Requiere un valor


### `--state`

Filtrar por estado (al seleccionar una actividad predeterminada): in_progress, pendiente, completado o cancelado
- Predeterminado: `[]`
- Requiere un valor


### `--result`

Filtrar por resultado (al seleccionar una actividad predeterminada): éxito o fracaso
- Requiere un valor



### `--incomplete`, `-i`



Incluir solo actividades incompletas (al seleccionar una actividad predeterminada). Esto es una abreviatura para &lt;info>—state=in_progress,pendiente&lt;/info>
- Predeterminado: `false`
- No acepta un valor



### `--all`, `-a`



Comprobar actividades recientes en todos los entornos (al seleccionar una actividad predeterminada)
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `api:curl`

Ejecute una solicitud de cURL autenticada en la API de Magento Cloud

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

La ruta de API
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



El método de solicitud para utilizar
- Requiere un valor



### `--data`, `-d`



Datos que enviar
- Requiere un valor



### `--include`, `-i`



Incluir encabezados en la salida
- Predeterminado: `false`
- No acepta un valor



### `--head`, `-I`



Buscar solo encabezados
- Predeterminado: `false`
- No acepta un valor


### `--disable-compression`

No utilice el indicador curl —comprimido
- Predeterminado: `false`
- No acepta un valor


### `--enable-glob`

Habilitar el globalización de curvas (elimine el indicador —globoff )
- Predeterminado: `false`
- No acepta un valor



### `--header`, `-H`



Encabezados adicionales
- Predeterminado: `[]`
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `app:config-get`

Ver la configuración de una aplicación

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad de configuración a ver
- Requiere un valor


### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `app:list`

Enumerar aplicaciones en el proyecto

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `auth:api-token-login`

Inicie sesión en Magento Cloud mediante un token de API

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `auth:browser-login`

Inicie sesión en Magento Cloud a través de un explorador

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Inicie sesión de nuevo, aunque ya haya iniciado sesión
- Predeterminado: `false`
- No acepta un valor


### `--browser`

El explorador que se utilizará para abrir la dirección URL. Establezca 0 para ninguno.
- Requiere un valor


### `--pipe`

Incluya la dirección URL para stdout.
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `auth:info`

Mostrar la información de la cuenta

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

La propiedad de la cuenta que se va a ver
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad account que se va a ver (sintaxis alternativa)
- Requiere un valor


### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `auth:logout`

Cierre la sesión de Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Cierre la sesión de todas las sesiones locales
- Predeterminado: `false`
- No acepta un valor


### `--other`

Cierre la sesión de otras sesiones locales
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Inicie sesión en Magento Cloud con un nombre de usuario y una contraseña

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `auth:token`

Obtenga un token de acceso de OAuth 2 para solicitudes a las API de Magento Cloud

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `blackfire:setup`

Configuración de la integración de Blackfire.io para el proyecto

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

ID del servidor
- Requiere un valor


### `--server_token`

El token del servidor
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `certificate:add`

Agregar un certificado SSL al proyecto

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

Ruta al archivo de certificado
- Requiere un valor


### `--key`

Ruta al archivo de clave privada del certificado
- Requiere un valor


### `--chain`

Ruta al archivo de cadena de certificados
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `certificate:delete`

Eliminar un certificado del proyecto

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de certificado (o el inicio del mismo)
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `certificate:get`

Ver un certificado

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de certificado (o el inicio del mismo)
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad certificate que se va a ver
- Requiere un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `certificate:list`

Enumerar certificados de proyecto

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

Filtrar por nombre de dominio (búsqueda que no distingue entre mayúsculas y minúsculas)
- Requiere un valor


### `--exclude-domain`

Excluir certificados, buscar por nombre de dominio (búsqueda que no distingue entre mayúsculas y minúsculas)
- Requiere un valor


### `--issuer`

Filtrar por emisor
- Requiere un valor


### `--only-auto`

Mostrar solo certificados aprovisionados automáticamente
- Predeterminado: `false`
- No acepta un valor


### `--no-auto`

Mostrar solo los certificados agregados manualmente
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

Mostrar solo certificados no caducados (predeterminado)
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

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `commit:get`

Mostrar detalles de confirmación

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

La comisión SHA. Esto también puede aceptar los sufijos &quot;HEAD&quot; y acento circunflejo (^) o virgulilla (~) para las confirmaciones principales.
- Predeterminado: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad commit que se va a mostrar.
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `commit:list`

Listar confirmaciones

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

El SHA de confirmación de Git de inicio. Esto también puede aceptar los sufijos &quot;HEAD&quot; y acento circunflejo (^) o virgulilla (~) para las confirmaciones principales.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

Número de confirmaciones que se van a mostrar.
- Predeterminado: `10`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `db:dump`

Crear un volcado local de la base de datos remota

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

El esquema que se va a volcar. Omite utilizar el esquema predeterminado (normalmente &quot;main&quot;).
- Requiere un valor



### `--file`, `-f`



Un nombre de archivo personalizado para el volcado
- Requiere un valor



### `--directory`, `-d`



Un directorio personalizado para el volcado
- Requiere un valor



### `--gzip`, `-z`



Comprima el volcado utilizando gzip
- Predeterminado: `false`
- No acepta un valor



### `--timestamp`, `-t`



Agregar una marca de tiempo al nombre del archivo volcado
- Predeterminado: `false`
- No acepta un valor



### `--stdout`, `-o`



Enviar a STDOUT en lugar de un archivo
- Predeterminado: `false`
- No acepta un valor


### `--table`

Tabla(s) que se debe incluir
- Predeterminado: `[]`
- Requiere un valor


### `--exclude-table`

Tabla(s) que se excluirán
- Predeterminado: `[]`
- Requiere un valor


### `--schema-only`

Volcar solo esquemas, sin datos
- Predeterminado: `false`
- No acepta un valor


### `--charset`

La codificación del conjunto de caracteres para el volcado
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `db:size`

Calcular el uso de disco de una base de datos

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Mostrar tamaños en bytes.
- Predeterminado: `false`
- No acepta un valor



### `--cleanup`, `-C`



Compruebe si las tablas se pueden limpiar y muéstreme recomendaciones (solo InnoDb).
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `db:sql`

Ejecutar SQL en la base de datos remota

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

Una instrucción SQL que se va a ejecutar
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Producción de resultados sin procesar y sin tabular
- Predeterminado: `false`
- No acepta un valor


### `--schema`

El esquema que se va a utilizar. Omite utilizar el esquema predeterminado (normalmente &quot;main&quot;). Pasa una cadena vacía para no utilizar ningún esquema.
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `domain:add`

Agregar un nuevo dominio al proyecto

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de dominio
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Ruta al archivo de certificado para este dominio
- Requiere un valor


### `--key`

Ruta al archivo de clave privada del certificado proporcionado.
- Requiere un valor


### `--chain`

La ruta al archivo de cadena de certificados o a los archivos del certificado proporcionado
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `domain:delete`

Eliminar un dominio del proyecto

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de dominio
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `domain:get`

Mostrar información detallada de un dominio

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de dominio
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad de dominio que se va a ver
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `domain:list`

Obtener una lista de todos los dominios

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `domain:update`

Actualizar un dominio

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de dominio
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Ruta al archivo de certificado para este dominio
- Requiere un valor


### `--key`

Ruta al archivo de clave privada del certificado proporcionado.
- Requiere un valor


### `--chain`

La ruta al archivo de cadena de certificados o a los archivos del certificado proporcionado
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:activate`

Activar un entorno

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Los entornos para activar

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

Establecer un nuevo entorno principal antes de activar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:branch`

Ramificar un entorno

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID (nombre de rama) del nuevo entorno
<!-- argument -->

### `parent`

El elemento principal del nuevo entorno
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

Título del nuevo entorno
- Requiere un valor


### `--force`

Cree el nuevo entorno aunque la rama no se pueda desproteger localmente
- Predeterminado: `false`
- No acepta un valor


### `--no-clone-parent`

No clona los datos de la rama principal
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:checkout`

Consulte un entorno

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID del entorno que se va a extraer. Por ejemplo: &quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:delete`

Eliminar un entorno

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Los entornos que se van a eliminar

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

Elimine también las ramas de Git remotas
- Predeterminado: `false`
- No acepta un valor


### `--no-delete-branch`

No elimine las ramas de Git remotas
- Predeterminado: `false`
- No acepta un valor


### `--inactive`

Eliminar todos los entornos inactivos
- Predeterminado: `false`
- No acepta un valor


### `--merged`

Eliminar todos los entornos combinados
- Predeterminado: `false`
- No acepta un valor


### `--exclude`

Entornos que no se van a eliminar
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:http-access`

Actualizar la configuración de acceso HTTP para un entorno

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

Restricción de acceso con el formato &quot;permission:address&quot;. Utilice 0 para borrar todas las direcciones.
- Predeterminado: `[]`
- Requiere un valor


### `--auth`

Credenciales de autenticación básica HTTP con el formato &quot;username:password&quot;. Utilice 0 para borrar todas las credenciales.
- Predeterminado: `[]`
- Requiere un valor


### `--enabled`

Si el control de acceso debe estar habilitado: 1 para habilitar, 0 para deshabilitar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:info`

Leer o establecer propiedades para un entorno

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

Nombre de la propiedad
<!-- argument -->

### `value`

Definir un nuevo valor para la propiedad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:init`

Inicialización de un entorno desde un repositorio público de Git

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Una URL a un repositorio de Git
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

Nombre del perfil
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:list`

Obtener una lista de entornos

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



No mostrar entornos inactivos
- Predeterminado: `false`
- No acepta un valor


### `--pipe`

Incluya una lista sencilla de ID de entorno.
- Predeterminado: `false`
- No acepta un valor


### `--refresh`

Si desea actualizar la lista.
- Predeterminado: `1`
- Requiere un valor


### `--sort`

Una propiedad para ordenar por
- Predeterminado: `title`
- Requiere un valor


### `--reverse`

Ordenar en orden inverso (descendente)
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:logs`

Leer los registros de un entorno

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

El tipo de registro, por ejemplo: &quot;access&quot; o &quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

Número de líneas que se van a mostrar
- Predeterminado: `100`
- Requiere un valor


### `--tail`

Seguir rastreando el registro
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:merge`

Combinar un entorno

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

El entorno para combinar
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:push`

Inserción de código en un entorno

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

La fuente ref: un nombre de rama o confirmar hash
- Predeterminado: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

El nombre de la rama de destino
- Requiere un valor



### `--force`, `-f`



Permitir actualizaciones no rápidas
- Predeterminado: `false`
- No acepta un valor


### `--force-with-lease`

Permitir actualizaciones no rápidas si la rama de seguimiento remoto está actualizada
- Predeterminado: `false`
- No acepta un valor



### `--set-upstream`, `-u`



Establezca el entorno de destino como flujo ascendente para la rama de origen
- Predeterminado: `false`
- No acepta un valor


### `--activate`

Activar el entorno antes de pulsar
- Predeterminado: `false`
- No acepta un valor


### `--branch`

OBSOLETO: alias de —activate
- Predeterminado: `false`
- No acepta un valor


### `--parent`

Establecer un nuevo entorno principal (solo se usa con —activate o —branch)
- Requiere un valor



### `--no-wait`, `-W`



No espere a que se complete la operación
- Predeterminado: `false`
- No acepta un valor


### `--wait`

Espere a que se complete la operación (valor predeterminado)
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:redeploy`

Reimplementar un entorno

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:relationships`

Mostrar las relaciones de un entorno

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

El entorno
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad de relación que se va a ver
- Requiere un valor


### `--refresh`

Si desea actualizar las relaciones
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:scp`

Copiar archivos a y desde el entorno actual mediante scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

Archivos para copiar. Utilice el control remoto: para definir ubicaciones remotas.

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



Copiar directorios completos de forma recursiva
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:set-remote`

Establecer el entorno remoto para asignarlo a una rama

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Nombre del equipo de entorno. Establecer en 0 para eliminar la asignación de una rama
- Requerido

   <!-- argument -->

### `branch`

La rama Git que se va a asignar (el valor predeterminado es la rama actual)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:ssh`

SSH al entorno actual

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Un comando para ejecutarse en el entorno.

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Incluya únicamente la URL SSH.
- Predeterminado: `false`
- No acepta un valor


### `--all`

Incluya todas las URL SSH (para cada aplicación).
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:synchronize`

Sincronizar el código o los datos de un entorno de su elemento principal

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

Qué sincronizar: &quot;code&quot;, &quot;data&quot; o ambos

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

Sincronizar código cambiando el valor en lugar de combinarlo
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:url`

Obtener las direcciones URL públicas de un entorno

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



Devolver solo la dirección URL de la ruta principal
- Predeterminado: `false`
- No acepta un valor


### `--browser`

El explorador que se utilizará para abrir la dirección URL. Establezca 0 para ninguno.
- Requiere un valor


### `--pipe`

Incluya la dirección URL para stdout.
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `environment:xdebug`

Abra un túnel para Xdebug en el entorno

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

El puerto local
- Predeterminado: `9000`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:activity:get`

Ver información detallada sobre una sola actividad de integración

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Un ID de integración. Deje en blanco para elegir de una lista.
<!-- argument -->

### `activity`

El ID de actividad. El valor predeterminado es la actividad de integración más reciente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad que se va a ver
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



[Opción obsoleta, no se utiliza]
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:activity:list`

Obtener una lista de actividades para una integración

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

Un ID de integración. Deje en blanco para elegir de una lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filtrar actividades por tipo
- Requiere un valor


### `--limit`

Limitar el número de resultados mostrados
- Predeterminado: `10`
- Requiere un valor


### `--start`

Solo se enumerarán las actividades creadas antes de esta fecha
- Requiere un valor


### `--state`

Filtrar actividades por estado
- Predeterminado: `[]`
- Requiere un valor


### `--result`

Filtrar actividades por resultado
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



[Opción obsoleta, no se utiliza]
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:activity:log`

Mostrar el registro de una actividad de integración

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Un ID de integración. Deje en blanco para elegir de una lista.
<!-- argument -->

### `activity`

El ID de actividad. El valor predeterminado es la actividad de integración más reciente.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



Mostrar una marca de tiempo junto a cada mensaje
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



[Opción obsoleta, no se utiliza]
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:add`

Agregar una integración al proyecto

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

El tipo de integración (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;weblock&#39;, &#39;health.email&#39;, &#39;health.pagerty&#39;, &#39;health.slack&#39;, &#39;health.weblock&#39;, &#39;script&#39;)
- Requiere un valor


### `--base-url`

La URL base de la instalación del servidor
- Requiere un valor


### `--username`

El nombre de usuario de Bitbucket Server
- Requiere un valor


### `--token`

Un token de acceso para la integración
- Requiere un valor


### `--key`

Una clave de consumidor de Bitbucket OAuth
- Requiere un valor


### `--secret`

Secreto de consumidor de Bitbucket OAuth
- Requiere un valor


### `--server-project`

El proyecto (p. ej. &#39;namespace/repo&#39;)
- Requiere un valor


### `--repository`

El repositorio que se va a rastrear (p. ej. &#39;owner/repository&#39;)
- Requiere un valor


### `--build-merge-requests`

GitLab: crear solicitudes de combinación como entornos
- Predeterminado: `true`
- Requiere un valor


### `--build-pull-requests`

Generar cada solicitud de extracción como entorno
- Predeterminado: `true`
- Requiere un valor


### `--build-draft-pull-requests`

Generar solicitudes de extracción borrador
- Predeterminado: `true`
- Requiere un valor


### `--build-pull-requests-post-merge`

Generar solicitudes de extracción basadas en su estado posterior a la fusión
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

Vuelva a sincronizar los datos del entorno de solicitud de extracción en cada compilación
- Predeterminado: `false`
- Requiere un valor


### `--fetch-branches`

Recuperar todas las ramas del remoto (como entornos inactivos)
- Predeterminado: `true`
- Requiere un valor


### `--prune-branches`

Eliminar ramas que no existen en el remoto
- Predeterminado: `true`
- Requiere un valor


### `--room`

ID de la sala HipChat
- Requiere un valor


### `--url`

Weblock: una URL para recibir datos JSON
- Requiere un valor


### `--shared-key`

Weblock: la clave secreta compartida de JWS
- Requiere un valor


### `--file`

El nombre de un archivo local que contiene la secuencia de comandos que se va a cargar
- Requiere un valor


### `--events`

Una lista de eventos en los que actuar, por ejemplo environment.push
- Predeterminado: `*`
- Requiere un valor


### `--states`

Una lista de estados en los que actuar, por ejemplo pendiente, en_curso, completo
- Predeterminado: `complete`
- Requiere un valor


### `--environments`

Los ID de entorno que se van a incluir
- Predeterminado: `*`
- Requiere un valor


### `--excluded-environments`

Los ID de entorno que se van a excluir
- Predeterminado: `[]`
- Requiere un valor


### `--from-address`

[Opcional] Dirección de formulario personalizada para correos electrónicos de alerta
- Requiere un valor


### `--recipients`

Las direcciones de correo electrónico del destinatario
- Predeterminado: `[]`
- Requiere un valor


### `--channel`

El canal Slack
- Requiere un valor


### `--routing-key`

La clave de enrutamiento PagerDuty
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:delete`

Eliminar una integración de un proyecto

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de integración. Deje en blanco para elegir de una lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:get`

Ver detalles de una integración

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Un ID de integración. Deje en blanco para elegir de una lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad de integración que desea ver
- Acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:list`

Ver una lista de integración de proyectos

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:update`

Actualización de una integración

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de la integración que se va a actualizar
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

El tipo de integración (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;weblock&#39;, &#39;health.email&#39;, &#39;health.pagerty&#39;, &#39;health.slack&#39;, &#39;health.weblock&#39;, &#39;script&#39;)
- Requiere un valor


### `--base-url`

La URL base de la instalación del servidor
- Requiere un valor


### `--username`

El nombre de usuario de Bitbucket Server
- Requiere un valor


### `--token`

Un token de acceso para la integración
- Requiere un valor


### `--key`

Una clave de consumidor de Bitbucket OAuth
- Requiere un valor


### `--secret`

Secreto de consumidor de Bitbucket OAuth
- Requiere un valor


### `--server-project`

El proyecto (p. ej. &#39;namespace/repo&#39;)
- Requiere un valor


### `--repository`

El repositorio que se va a rastrear (p. ej. &#39;owner/repository&#39;)
- Requiere un valor


### `--build-merge-requests`

GitLab: crear solicitudes de combinación como entornos
- Predeterminado: `true`
- Requiere un valor


### `--build-pull-requests`

Generar cada solicitud de extracción como entorno
- Predeterminado: `true`
- Requiere un valor


### `--build-draft-pull-requests`

Generar solicitudes de extracción borrador
- Predeterminado: `true`
- Requiere un valor


### `--build-pull-requests-post-merge`

Generar solicitudes de extracción basadas en su estado posterior a la fusión
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

Vuelva a sincronizar los datos del entorno de solicitud de extracción en cada compilación
- Predeterminado: `false`
- Requiere un valor


### `--fetch-branches`

Recuperar todas las ramas del remoto (como entornos inactivos)
- Predeterminado: `true`
- Requiere un valor


### `--prune-branches`

Eliminar ramas que no existen en el remoto
- Predeterminado: `true`
- Requiere un valor


### `--room`

ID de la sala HipChat
- Requiere un valor


### `--url`

Weblock: una URL para recibir datos JSON
- Requiere un valor


### `--shared-key`

Weblock: la clave secreta compartida de JWS
- Requiere un valor


### `--file`

El nombre de un archivo local que contiene la secuencia de comandos que se va a cargar
- Requiere un valor


### `--events`

Una lista de eventos en los que actuar, por ejemplo environment.push
- Predeterminado: `*`
- Requiere un valor


### `--states`

Una lista de estados en los que actuar, por ejemplo pendiente, en_curso, completo
- Predeterminado: `complete`
- Requiere un valor


### `--environments`

Los ID de entorno que se van a incluir
- Predeterminado: `*`
- Requiere un valor


### `--excluded-environments`

Los ID de entorno que se van a excluir
- Predeterminado: `[]`
- Requiere un valor


### `--from-address`

[Opcional] Dirección de formulario personalizada para correos electrónicos de alerta
- Requiere un valor


### `--recipients`

Las direcciones de correo electrónico del destinatario
- Predeterminado: `[]`
- Requiere un valor


### `--channel`

El canal Slack
- Requiere un valor


### `--routing-key`

La clave de enrutamiento PagerDuty
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `integration:validate`

Validación de una integración existente

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Un ID de integración. Deje en blanco para elegir de una lista.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `local:build`

Crear el proyecto actual localmente

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

Especificar aplicaciones para generar

- Predeterminado: `[]`

- Matriz <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



Usar vínculos absolutos
- Predeterminado: `false`
- No acepta un valor



### `--source`, `-s`



El directorio de origen. El valor predeterminado es la raíz del proyecto actual.
- Requiere un valor



### `--destination`, `-d`



Destino al que se vinculará la raíz web de cada aplicación. Predeterminado: _www
- Requiere un valor



### `--copy`, `-c`



Copiar a un directorio de compilación, en lugar de enlaces simbólicos desde el origen
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

No eliminar compilaciones antiguas
- Predeterminado: `false`
- No acepta un valor


### `--no-archive`

No crear ni utilizar un archivo de compilación
- Predeterminado: `false`
- No acepta un valor


### `--no-backup`

No realice una copia de seguridad de la versión anterior
- Predeterminado: `false`
- No acepta un valor


### `--no-cache`

Deshabilitar el almacenamiento en caché
- Predeterminado: `false`
- No acepta un valor


### `--no-build-hooks`

No ejecutar enlaces posteriores a la compilación
- Predeterminado: `false`
- No acepta un valor


### `--no-deps`

No instale dependencias de compilación localmente
- Predeterminado: `false`
- No acepta un valor


### `--working-copy`

Arrastrar: utilice git para clonar un repositorio de cada módulo de Drupal en lugar de descargar simplemente una versión
- Predeterminado: `false`
- No acepta un valor


### `--concurrency`

Arrastrar: establecer el número de proyectos simultáneos que se procesarán al mismo tiempo
- Predeterminado: `4`
- Requiere un valor


### `--lock`

Arrastrar: crear o actualizar un archivo de bloqueo (solo disponible con Drush versión 7+)
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `local:clean`

Eliminar compilaciones de proyecto antiguas

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

El número máximo de compilaciones que se deben mantener
- Predeterminado: `5`
- Requiere un valor


### `--max-age`

La edad máxima de las compilaciones, en segundos. Se omite si no se configura.
- Requiere un valor


### `--include-active`

Eliminar también compilaciones activas
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `local:dir`

Buscar la raíz del proyecto local

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

El subdirectorio que se va a buscar (&quot;local&quot;, &quot;web&quot; o &quot;compartido&quot;)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `mount:download`

Descargar archivos de un montaje utilizando rsync

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Descargar desde todos los montículos
- Predeterminado: `false`
- No acepta un valor



### `--mount`, `-m`



El montaje (como una ruta relativa a la aplicación)
- Requiere un valor


### `--target`

El directorio en el que se descargarán los archivos. Si se utiliza —all, se añadirá la ruta de montaje
- Requiere un valor


### `--source-path`

Utilice la ruta de origen del montaje (en lugar de la ruta de montaje) como subdirectorio del destino, cuando se utilice —all
- Predeterminado: `false`
- No acepta un valor


### `--delete`

Si se eliminan archivos superfluos en el directorio de destino
- Predeterminado: `false`
- No acepta un valor


### `--exclude`

Archivos que se van a excluir de la descarga (patrón)
- Predeterminado: `[]`
- Requiere un valor


### `--include`

Archivos que se van a incluir en la descarga (patrón)
- Predeterminado: `[]`
- Requiere un valor


### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `mount:list`

Obtener una lista de montículos

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

Salida de las rutas de montaje únicamente (una por línea)
- Predeterminado: `false`
- No acepta un valor


### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `mount:size`

Compruebe el uso de discos de los montajes

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Mostrar tamaños en bytes
- Predeterminado: `false`
- No acepta un valor


### `--refresh`

Actualizar la caché
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `mount:upload`

Cargar archivos a un montaje mediante rsync

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

Un directorio que contiene los archivos que se van a cargar
- Requiere un valor



### `--mount`, `-m`



El montaje (como una ruta relativa a la aplicación)
- Requiere un valor


### `--delete`

Si se eliminan archivos prescindibles en el montaje
- Predeterminado: `false`
- No acepta un valor


### `--exclude`

Archivos que se van a excluir de la carga (patrón)
- Predeterminado: `[]`
- Requiere un valor


### `--include`

Archivos que se van a incluir en la carga (patrón)
- Predeterminado: `[]`
- Requiere un valor


### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--worker`

Un nombre de trabajador
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

Borrar la caché de compilación de un proyecto

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:curl`

Ejecute una solicitud cURL autenticada en la API de un proyecto

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

La ruta de API
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



El método de solicitud para utilizar
- Requiere un valor



### `--data`, `-d`



Datos que enviar
- Requiere un valor



### `--include`, `-i`



Incluir encabezados en la salida
- Predeterminado: `false`
- No acepta un valor



### `--head`, `-I`



Buscar solo encabezados
- Predeterminado: `false`
- No acepta un valor


### `--disable-compression`

No utilice el indicador curl —comprimido
- Predeterminado: `false`
- No acepta un valor


### `--enable-glob`

Habilitar el globalización de curvas (elimine el indicador —globoff )
- Predeterminado: `false`
- No acepta un valor



### `--header`, `-H`



Encabezados adicionales
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:get`

Clonar un proyecto localmente

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

El ID del proyecto
<!-- argument -->

### `directory`

El directorio al que se va a clonar. El valor predeterminado es el título del proyecto
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



El ID de entorno que se va a clonar. El valor predeterminado es el proyecto predeterminado o el primer entorno disponible
- Requiere un valor


### `--depth`

Cree un clon superficial: limitar el número de confirmaciones en el historial
- Requiere un valor


### `--build`

Creación del proyecto después de la clonación
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:info`

Leer o establecer propiedades para un proyecto

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

Nombre de la propiedad
<!-- argument -->

### `value`

Definir un nuevo valor para la propiedad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:list`

Obtener una lista de todos los proyectos activos

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

Inclusión de una lista sencilla de ID de proyecto
- Predeterminado: `false`
- No acepta un valor


### `--host`

Filtrar por nombre de host de región (coincidencia exacta)
- Requiere un valor


### `--title`

Filtrar por título (búsqueda que no distingue entre mayúsculas y minúsculas)
- Requiere un valor


### `--my`

Mostrar solo los proyectos que posee
- Predeterminado: `false`
- No acepta un valor


### `--refresh`

Si desea actualizar la lista
- Predeterminado: `1`
- Requiere un valor


### `--sort`

Una propiedad para ordenar por
- Predeterminado: `title`
- Requiere un valor


### `--reverse`

Ordenar en orden inverso (descendente)
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:set-remote`

Establecer el proyecto remoto para el repositorio Git actual

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

El ID del proyecto
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Eliminar una variable de un proyecto

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Ver variables de un proyecto

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

Nombre de la variable
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Incluya solo el valor de la variable completa (se debe especificar un &quot;nombre&quot;)
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Establecer una variable para un proyecto

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de la variable
- Requerido

   <!-- argument -->

### `value`

El valor de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Marcar el valor como JSON
- Predeterminado: `false`
- No acepta un valor


### `--no-visible-build`

No exponer esta variable en el momento de la compilación
- Predeterminado: `false`
- No acepta un valor


### `--no-visible-runtime`

No exponer esta variable en tiempo de ejecución
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `repo:cat`

Leer un archivo en el repositorio del proyecto

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Ruta al archivo
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



La comisión SHA. Esto también puede aceptar los sufijos &quot;HEAD&quot; y acento circunflejo (^) o virgulilla (~) para las confirmaciones principales.
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `repo:ls`

Enumerar archivos en el repositorio del proyecto

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

La ruta a un subdirectorio
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



Mostrar solo directorios
- Predeterminado: `false`
- No acepta un valor



### `--files`, `-f`



Mostrar sólo archivos
- Predeterminado: `false`
- No acepta un valor


### `--git-style`

Salida de estilo similar a &quot;git ls-tree&quot;
- Predeterminado: `false`
- No acepta un valor



### `--commit`, `-c`



La comisión SHA. Esto también puede aceptar los sufijos &quot;HEAD&quot; y acento circunflejo (^) o virgulilla (~) para las confirmaciones principales.
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `route:get`

Ver información detallada sobre una ruta

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

La dirección URL original de la ruta
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

Un ID de ruta para seleccionar
- Requiere un valor



### `--primary`, `-1`



Seleccione la ruta principal
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



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `route:list`

Enumerar todas las rutas para un entorno

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

ID del entorno
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Omitir la caché de rutas
- Predeterminado: `false`
- No acepta un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `self:install`

Instalación o actualización de archivos de configuración de CLI

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

El tipo de shell para el autocompletado (bash o zsh)
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `self:stats`

Ver estadísticas de las descargas de paquetes de GitHub

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



Número de página
- Predeterminado: `1`
- Requiere un valor



### `--count`, `-c`



Resultados por página (máximo: 100)
- Predeterminado: `20`
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `self:update`

Actualice la CLI a la versión más reciente

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

Actualizar solamente entre versiones menores o de parches
- Predeterminado: `false`
- No acepta un valor


### `--unstable`

Actualización a una nueva versión inestable, si está disponible
- Predeterminado: `false`
- No acepta un valor


### `--manifest`

Anular la ubicación del archivo de manifiesto
- Requiere un valor


### `--current-version`

Anular la versión actual
- Requiere un valor


### `--timeout`

Un tiempo de espera para la comprobación de versiones
- Predeterminado: `30`
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `service:list`

Enumerar servicios en el proyecto

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `service:mongo:dump`

Crear un archivo binario de volcado de datos de MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



La colección que se va a volcar
- Requiere un valor



### `--gzip`, `-z`



Comprima el volcado utilizando gzip
- Predeterminado: `false`
- No acepta un valor



### `--stdout`, `-o`



Enviar a STDOUT en lugar de un archivo
- Predeterminado: `false`
- No acepta un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `service:mongo:export`

Exportar datos de MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



La colección que se va a exportar
- Requiere un valor


### `--jsonArray`

Exportar datos como una única matriz JSON
- Predeterminado: `false`
- No acepta un valor


### `--type`

El tipo de exportación, por ejemplo &quot;csv&quot;
- Requiere un valor



### `--fields`, `-f`



Los campos que desea exportar
- Predeterminado: `[]`
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `service:mongo:restore`

Restaurar un volcado de datos de archivo binario en MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



La colección que se va a restaurar
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `service:mongo:shell`

Usar el shell de MongoDB

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

Pasar un fragmento de JavaScript al shell
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `service:redis-cli`

Acceso a la CLI de Redis

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Argumentos para agregar al comando Redis
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Cambiar entre sesiones

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El nuevo ID de sesión
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `snapshot:create`

Crear una instantánea de un entorno

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

El entorno
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

Copia de seguridad activa: no detenga el entorno. Si se configura, esto deja el entorno en ejecución y abierto a las conexiones durante la copia de seguridad. Esto reduce el tiempo de inactividad, con el riesgo de realizar backup de datos en un estado inconsistente.
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `snapshot:list`

Lista de instantáneas disponibles de un entorno

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

Limitar el número de instantáneas a la lista
- Predeterminado: `10`
- Requiere un valor


### `--start`

Solo se enumerarán las instantáneas creadas antes de esta fecha
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `snapshot:restore`

Restaurar una instantánea de entorno

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

Nombre de la instantánea. El valor predeterminado es el más reciente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

Entorno al que restaurar. Valores predeterminados del entorno actual de la instantánea
- Requiere un valor


### `--branch-from`

Si el —target aún no existe, especifica el elemento principal del nuevo entorno
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Ejecutar una operación de origen

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

El nombre de la operación
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

Variable que se debe configurar durante la operación, en formato &lt;info>type:name=value&lt;/info>
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `ssh-cert:info`

Mostrar información sobre el certificado SSH actual

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

No actualice el certificado si no es válido
- Predeterminado: `false`
- No acepta un valor



### `--property`, `-P`



La propiedad certificate que se va a mostrar
- Requiere un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `ssh-cert:load`

Generar un certificado SSH

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

Actualizar solo el certificado si es necesario (no escribir la configuración SSH)
- Predeterminado: `false`
- No acepta un valor


### `--new`

Forzar la actualización del certificado
- Predeterminado: `false`
- No acepta un valor


### `--new-key`

[Obsoleto] Utilice —nuevo en su lugar
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `ssh-key:add`

Añadir una nueva clave SSH

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Ruta a una clave pública SSH existente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

Un nombre para identificar la clave
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `ssh-key:delete`

Eliminar una clave SSH

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

El ID de la clave SSH que se va a eliminar
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `ssh-key:list`

Obtener una lista de claves SSH en la cuenta

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `subscription:info`

Leer o modificar las propiedades de suscripción

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

Nombre de la propiedad
<!-- argument -->

### `value`

Definir un nuevo valor para la propiedad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



El ID de suscripción
- Requiere un valor


### `--date-fmt`

El formato de fecha (como una cadena de formato de fecha PHP)
- Predeterminado: `c`
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `tunnel:close`

Cierre de túneles SSH

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Cierre todos los túneles
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `tunnel:info`

Ver información de relación para túneles SSH

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



La propiedad de relación que se va a ver
- Requiere un valor



### `--encode`, `-c`



Salida como JSON codificado para base64
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `tunnel:list`

Enumerar túneles SSH

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Ver todos los túneles
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `tunnel:open`

Apertura de túneles SSH en las relaciones de una aplicación

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



Permitir que los hosts remotos se conecten a puertos reenviados locales
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `tunnel:single`

Abrir un solo túnel SSH en una relación de aplicación

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

El puerto local
- Requiere un valor



### `--gateway-ports`, `-g`



Permitir que los hosts remotos se conecten a puertos reenviados locales
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--app`, `-A`



El nombre de la aplicación remota
- Requiere un valor



### `--relationship`, `-r`



La relación de servicio que se va a usar
- Requiere un valor



### `--identity-file`, `-i`



Una identidad SSH (clave privada) para usar
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `user:add`

Agregar un usuario al proyecto

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

La dirección de correo electrónico del usuario
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



La función de proyecto del usuario (&quot;administrador&quot; o &quot;visor&quot;) o la función específica del entorno (p. ej. &#39;master:contributor&#39; o &#39;stage:viewer&#39;). El carácter % puede utilizarse como comodín en el ID de entorno, por ejemplo &#39;%:visor&#39;. La función se puede abreviar, por ejemplo &#39;master:c&#39;.
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `user:delete`

Eliminar un usuario del proyecto

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

La dirección de correo electrónico del usuario
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `user:get`

Ver las funciones de un usuario

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

La dirección de correo electrónico del usuario
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Nivel de función (&quot;proyecto&quot; o &quot;entorno&quot;)
- Requiere un valor


### `--pipe`

Incluya la función en stdout (después de realizar cualquier cambio)
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `user:list`

Lista de usuarios de proyectos

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `user:update`

Actualizar las funciones de usuario en un proyecto

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

La dirección de correo electrónico del usuario
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



La función de proyecto del usuario (&quot;administrador&quot; o &quot;visor&quot;) o la función específica del entorno (p. ej. &#39;master:contributor&#39; o &#39;stage:viewer&#39;). El carácter % puede utilizarse como comodín en el ID de entorno, por ejemplo &#39;%:visor&#39;. La función se puede abreviar, por ejemplo &#39;master:c&#39;.
- Predeterminado: `[]`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:create`

Crear una variable

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de la variable
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Nivel en el que se debe configurar la variable (&quot;proyecto&quot; o &quot;entorno&quot;)
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

Si la variable es sensible
- Predeterminado: `false`
- Requiere un valor


### `--prefix`

El prefijo del nombre de la variable (p. ej. &#39;none&#39; o &#39;env:&#39;)
- Predeterminado: `none`
- Requiere un valor


### `--enabled`

Si la variable debe estar habilitada
- Predeterminado: `true`
- Requiere un valor


### `--inheritable`

Si la variable es heredable por entornos secundarios
- Predeterminado: `true`
- Requiere un valor


### `--visible-build`

Si la variable debe ser visible en el momento de la compilación
- Predeterminado: `true`
- Requiere un valor


### `--visible-runtime`

Indica si la variable debe ser visible durante la ejecución
- Predeterminado: `true`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:delete`

Eliminar una variable

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Deshabilitar una variable habilitada a nivel de entorno

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Nombre de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Habilitar una variable deshabilitada a nivel de entorno

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

Nombre de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:get`

Ver una variable

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

Nombre de la variable
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Ver una sola propiedad de variable
- Requiere un valor



### `--level`, `-l`



El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor


### `--pipe`

[Opción obsoleta] Incluya únicamente el valor de la variable
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:list`

Variables de lista

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



El nivel de variable (&quot;proyecto&quot;, &quot;entorno&quot;, &quot;p&quot; o &quot;e&quot;)
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Establecer una variable para un entorno

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de la variable
- Requerido

   <!-- argument -->

### `value`

El valor de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

Marcar el valor como JSON
- Predeterminado: `false`
- No acepta un valor


### `--disabled`

Marque la variable como deshabilitada
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `variable:update`

Actualizar una variable

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

El nombre de la variable
- Requerido

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




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

Si la variable es sensible
- Predeterminado: `false`
- Requiere un valor


### `--enabled`

Si la variable debe estar habilitada
- Predeterminado: `true`
- Requiere un valor


### `--inheritable`

Si la variable es heredable por entornos secundarios
- Predeterminado: `true`
- Requiere un valor


### `--visible-build`

Si la variable debe ser visible en el momento de la compilación
- Predeterminado: `true`
- Requiere un valor


### `--visible-runtime`

Indica si la variable debe ser visible durante la ejecución
- Predeterminado: `true`
- Requiere un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
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



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size -->

## `worker:list`

Obtener una lista de todos los trabajadores implementados

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Si actualizar la caché
- Predeterminado: `false`
- No acepta un valor



### `--project`, `-p`



ID o URL del proyecto
- Requiere un valor


### `--host`

El nombre de host de la API del proyecto
- Requiere un valor



### `--environment`, `-e`



ID del entorno
- Requiere un valor


### `--format`

El formato de salida (&quot;tabla&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;sin formato&quot;)
- Predeterminado: `table`
- Requiere un valor


### `--columns`

Columnas que se van a mostrar (lista separada por comas o valores múltiples)
- Predeterminado: `[]`
- Requiere un valor


### `--no-header`

No mostrar el encabezado de tabla
- Predeterminado: `false`
- No acepta un valor



### `--help`, `-h`



Mostrar este mensaje de ayuda
- Predeterminado: `false`
- No acepta un valor



### `--quiet`, `-q`



No mostrar ningún mensaje
- Predeterminado: `false`
- No acepta un valor



### `--verbose`, `-v|-vv|-vvv`



Aumentar la diversidad de los mensajes
- Predeterminado: `false`
- No acepta un valor



### `--version`, `-V`



Mostrar esta versión de la aplicación
- Predeterminado: `false`
- No acepta un valor



### `--yes`, `-y`



Responda &quot;sí&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor



### `--no`, `-n`



Responda &quot;no&quot; a cualquier pregunta de sí/no. desactivar interacción
- Predeterminado: `false`
- No acepta un valor <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->