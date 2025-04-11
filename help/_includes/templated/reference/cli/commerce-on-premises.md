---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '8253'
ht-degree: 1%

---
# bin/magento (Adobe Systems Commerce local)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Versión**: 2.4.8

Esta referencia contiene 145 comandos disponibles a través del `bin/magento` herramienta de línea de comandos.
El lista inicial se genera automáticamente mediante el `bin/magento list` comando de Adobe Systems Commerce.

## General

Utilice el [guía &quot;añadir comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) para agregar un comando CLI personalizado.

Puede llamar a `bin/magento` comandos CLI utilizando accesos directos en lugar del nombre completo del comando. Por ejemplo, puede llamar `bin/magento setup:upgrade` mediante `bin/magento s:up`, `bin/magento s:upg`. Consulte [la sintaxis](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) de acceso directo para comprender cómo usar los accesos directos con cualquier comando de CLI.

Esta documentación de referencia se genera a partir del código fuente aplicación. Para cambiar la documentación, debe abrir una solicitud de recibir para el comando correspondiente en el repositorio de la base](https://github.com/magento) de código correspondiente[. Consulte [Code contribuciones](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) para obtener más información.

### Opciones globales

#### `--help`, `-h`

Mostrar ayuda para el comando dado. Cuando no se proporciona ningún comando, mostrar ayuda para el comando lista

- Predeterminado: `false`
- No acepta un valor

#### `--quiet`, `-q`

No generar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

#### `--verbose`, `-v|-vv|-vvv`

Aumente la palabrería de los mensajes: 1 para el resultado normal, 2 para los resultados más detallados y 3 para los depurar

- Predeterminado: `false`
- No acepta un valor

#### `--version`, `-V`

Mostrar esta versión aplicación

- Predeterminado: `false`
- No acepta un valor

#### `--ansi`

Forzar (o deshabilitar --no-ansi) salida ANSI

- No acepta un valor

#### `--no-ansi`

Anular la opción &quot;--ansi&quot;

- Predeterminado: `false`
- No acepta un valor

#### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Comando interno para proporcionar sugerencias de finalización de shell

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--shell`, `-s`

El tipo de concha (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Requiere un valor

#### `--input`, `-i`

Una matriz de tokens de entrada (por ejemplo, COMP_WORDS o argv)

- Predeterminado: `[]`
- Requiere un valor

#### `--current`, `-c`

Índice de la matriz de &quot;entrada&quot; en la que se encuentra el cursor (p. ej. COMP_CWORD)

- Requiere un valor

#### `--api-version`, `-a`

La versión de API del script de finalización

- Requiere un valor

#### `--symfony`, `-S`

obsolescente

- Requiere un valor


## `completion`

```bash
bin/magento completion [--debug] [--] [<shell>]
```

Volcar el script de finalización del shell

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
```

### Argumentos

#### `shell`

El tipo de shell (por ejemplo, &quot;bash&quot;), el valor del &quot;$SHELL&quot; env var se usará si no se da esto

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--debug`

Seguir el registro de finalización depurar

- Predeterminado: `false`
- No acepta un valor


## `help`

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Mostrar la ayuda de un comando

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumentos

#### `command_name`

El nombre del comando

- Predeterminado: `help`

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor

#### `--raw`

Para generar ayuda de comando sin procesar

- Predeterminado: `false`
- No acepta un valor


## `list`

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Lista de comandos

```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
```

### Argumentos

#### `namespace`

El nombre del espacio de nombres

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--raw`

Para generar la lista de comandos raw

- Predeterminado: `false`
- No acepta un valor

#### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor

#### `--short`

Omitir la descripción de los argumentos de los comandos

- Predeterminado: `false`
- No acepta un valor


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Desactivación Adobe Systems módulo IMS

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Habilite Adobe Systems módulo IMS.

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--organization-id`, `-o`

Establezca el identificador de organización para Adobe Systems configuración de IMS. Se requiere al habilitar el módulo

- Acepta un valor

#### `--client-id`, `-c`

Establezca el ID de cliente para Adobe Systems configuración de IMS. Se requiere al habilitar el módulo

- Acepta un valor

#### `--client-secret`, `-s`

Establezca el secreto de cliente para Adobe Systems configuración de IMS. Se requiere al habilitar el módulo

- Acepta un valor

#### `--2fa`, `-t`

Compruebe si 2FA está habilitado para Organización en Adobe Admin Console. Se requiere al habilitar el módulo

- Acepta un valor


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Información de Adobe Systems configuración del módulo IMS

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Estado de Adobe Systems módulo IMS

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crea un administrador

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--admin-user`

(Requerido) usuario de administración

- Requiere un valor

#### `--admin-password`

(Requerido) Administrador contraseña

- Requiere un valor

#### `--admin-email`

(Requerido) Administrador correo electrónico

- Requiere un valor

#### `--admin-firstname`

(Requerido) Nombre del administrador

- Requiere un valor

#### `--admin-lastname`

(Requerido) Apellido del administrador

- Requiere un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Desbloquear cuenta de administrador

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### Argumentos

#### `username`

El nombre de usuario de administrador que se desbloqueará

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Crear vertedero de aplicación

### Argumentos

#### `config-types`

Lista separada por espacios de los tipos de configuración u omitir para volcar todos los [ámbitos, temas, sistema, i18n]

- Predeterminado: `[]`
- Matriz

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Importación de datos de archivos de configuración compartidos al almacenamiento de datos adecuado

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `app:config:status`

```bash
bin/magento app:config:status
```

Comprueba si la propagación de la configuración requiere actualización

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migrar tarjetas almacenadas desde una base de datos de Magento 1

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--host`

Nombre de host/IP. El puerto es opcional

- Requiere un valor

#### `--dbname`

Nombre de la base de datos

- Requiere un valor

#### `--username`

Nombre de usuario de la base de datos. Debe tener acceso de lectura

- Requiere un valor

#### `--password`

Contraseña

- Requiere un valor


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Limpia los tipos de caché

### Argumentos

#### `types`

Los lista separados por espacios de los tipos de caché u omitidos se aplican a todos los tipos de caché.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--bootstrap`

Agregar o anular parámetros de Bootstrap

- Requiere un valor


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Servicios de pago limpios Caché de ámbitos comerciales

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Desactiva los tipos de caché

### Argumentos

#### `types`

Los lista separados por espacios de los tipos de caché u omitidos se aplican a todos los tipos de caché.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--bootstrap`

Agregar o anular parámetros de Bootstrap

- Requiere un valor


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Habilita los tipos de caché

### Argumentos

#### `types`

Los lista separados por espacios de los tipos de caché u omitidos se aplican a todos los tipos de caché.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--bootstrap`

Agregar o anular parámetros de Bootstrap

- Requiere un valor


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Vacía la caché almacenamiento utilizada por los tipos de caché

### Argumentos

#### `types`

Los lista separados por espacios de los tipos de caché u omitidos se aplican a todos los tipos de caché.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--bootstrap`

Agregar o anular parámetros de Bootstrap

- Requiere un valor


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Comprueba el estado de la caché

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--bootstrap`

Agregar o anular parámetros de Bootstrap

- Requiere un valor


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Crea imágenes de producto redimensionadas

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--async`, `-a`

Cambiar el tamaño de la imagen en modo asíncrono

- Predeterminado: `false`
- No acepta un valor

#### `--skip_hidden_images`

No procesar imágenes marcadas como oculta desde página de producto

- Predeterminado: `false`
- No acepta un valor


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Elimina los atributos del producto no utilizados.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Establezca si desea aplicar usuario validación de contenido HTML o mostrar una advertencia en su lugar

### Argumentos

#### `restrict`

Y\n

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Establecer valores de configuración sensibles

### Argumentos

#### `path`

Ruta de configuración, por ejemplo: grupo/section/field_name


#### `value`

Valor de configuración

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--interactive`, `-i`

Habilite el modo interactivo para establecer todas las variables confidenciales

- Predeterminado: `false`
- No acepta un valor

#### `--scope`

Margen de configuración; si no está establecido, use &quot;predeterminado&quot;

- Predeterminado: `default`
- Acepta un valor

#### `--scope-code`

Código de ámbito para la configuración, cadena vacía de forma predeterminada

- Valor predeterminado: &#39;&#39;
- Acepta un valor


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Cambiar la configuración del sistema

### Argumentos

#### `path`

Ruta de configuración en formato sección/grupo/field_name

- Obligatorio


#### `value`

Valor de configuración

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--scope`

ámbito de configuración (predeterminada, sitio web o tienda)

- Predeterminado: `default`
- Requiere un valor

#### `--scope-code`

Código de ámbito (necesario solo si ámbito no es predeterminado)

- Requiere un valor

#### `--lock-env`, `-e`

Valor de bloqueo que evita la modificación en el Administrador (se guardará en la aplicación / etc / env.php)

- Predeterminado: `false`
- No acepta un valor

#### `--lock-config`, `-c`

Bloquear y compartir el valor con otras instalaciones, evita la modificación en el Administrador (se guardará en la aplicación / etc / config.php)

- Predeterminado: `false`
- No acepta un valor

#### `--lock`, `-l`

En desuso, use la opción --lock-env en su lugar.

- Predeterminado: `false`
- No acepta un valor


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Muestra el valor de configuración para una ruta determinada. Si no se especifica la ruta, se mostrarán todos los valores guardados

### Argumentos

#### `path`

Ruta de configuración, por ejemplo section_id/group_id/field_id

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--scope`

Si no se especifica el margen de configuración, se utilizará la ámbito predeterminada

- Predeterminado: `default`
- Acepta un valor

#### `--scope-code`

Código de ámbito (necesario solo si ámbito no `default`lo es)

- Valor predeterminado: &#39;&#39;
- Acepta un valor


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Genera e instala crontab para el usuario actual

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--force`, `-f`

Forzar tareas de instalación

- Predeterminado: `false`
- No acepta un valor

#### `--non-optional`, `-d`

Instale solo las tareas no opcionales (predeterminadas)

- Predeterminado: `false`
- No acepta un valor


## `cron:remove`

```bash
bin/magento cron:remove
```

Quita tareas de crontab

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Ejecuta trabajos por programación

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--group`

Ejecute trabajos únicamente desde grupo especificados

- Requiere un valor

#### `--exclude-group`

Excluir trabajos del grupo especificado

- Predeterminado: `[]`
- Acepta varios valores

#### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Actualice los hash del cliente según el algoritmo más reciente

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Establezca aplicación modo.

### Argumentos

#### `mode`

El modo de aplicación que se va a establecer. Las opciones disponibles son &quot;desarrollador&quot; o &quot;producción&quot;

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--skip-compilation`, `-s`

Omite la limpieza y regeneración de contenido estáticos (código generado, CSS preprocesado y activos en pub/static/)

- Predeterminado: `false`
- No acepta un valor


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Muestra el modo de aplicación actual.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

Proporciona información sobre la configuración de la inyección de dependencias para el Comando.

### Argumentos

#### `class`

Nombre de la clase

- Obligatorio


#### `area`

Área Code

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Analiza las plantillas de la newsletter en busca de posibles problemas de compatibilidad con el uso del variable

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Análisis correo electrónico anulaciones de plantilla para detectar posibles problemas de compatibilidad de uso variable

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Deshabilite el generador de perfiles.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Habilite el generador de perfiles.

### Argumentos

#### `type`

Tipo de perfilador

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Deshabilitar DB consulta registro

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Habilitar la consulta de base de datos registro

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--include-all-queries`

Registre todas las consultas. [true\|false]

- Predeterminado: `true`
- Acepta un valor

#### `--query-time-threshold`

Umbrales de tiempo de consulta.

- Predeterminado: `0.001`
- Acepta un valor

#### `--include-call-stack`

Incluir pila de llamadas. [true\|false]

- Predeterminado: `true`
- Acepta un valor


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Recopila y publica archivos de origen para el tema.

### Argumentos

#### `file`

Archivos al preproceso (el archivo debe especificarse sin extensión)

- Predeterminado: `css/styles-mcss/styles-l`

- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--type`

Tipo de archivos de origen: [menos]

- Predeterminado: `less`
- Requiere un valor

#### `--locale`

Configuración regional: [en_US]

- Predeterminado: `en_US`
- Requiere un valor

#### `--area`

Área: [frontend\|adminhtml]

- Predeterminado: `frontend`
- Requiere un valor

#### `--theme`

Tema: [Proveedor/tema]

- Predeterminado: `Magento/luma`
- Requiere un valor


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Deshabilite las sugerencias de plantilla front-end. Puede que se requiera un vaciado de caché.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Habilite las sugerencias de plantilla front-end. Puede que se requiera un vaciado de caché.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Mostrar front-end plantilla sugiere el estado.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Ejecuta pruebas

### Argumentos

#### `type`

Tipo de prueba que se ejecutará. Tipos disponibles: todo, unidad, integración, integración-todo, estático, estático-todo, integridad, heredado, predeterminado

- Predeterminado: `default`

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--arguments`, `-c`

Argumentos adicionales para PHPUnit. Ejemplo: &quot;-c&#39;--filter=MyTest&#39;&quot; (sin espacios)

- Valor predeterminado: &#39;&#39;
- Requiere un valor


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Genera el catálogo de asignaciones de URN a *.xsd para que el IDE resalte xml.

### Argumentos

#### `path`

Ruta al archivo para generar el catálogo. Para PhpStorm use .idea/misc.xml

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--ide`

Formato en el que se generará el catálogo. Soportado: [phpstorm, vscode]

- Predeterminado: `phpstorm`
- Requiere un valor


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Convierte archivos XML mediante hojas de estilo XSL

### Argumentos

#### `xml-file`

Ruta al archivo XML que se va a transformar

- Obligatorio


#### `processor`

Ruta de acceso a la hoja de estilo XSL que se va a aplicar al archivo XML

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--overwrite`, `-o`

Sobrescribir archivo XML

- Predeterminado: `false`
- No acepta un valor


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

añadir dominios a la lista blanca de dominios descargables

### Argumentos

#### `domains`

Nombre de dominios

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Quitar dominios de la lista blanca de dominios descargables

### Argumentos

#### `domains`

Nombres de dominio

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Mostrar lista blanca de dominios descargables

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

Muestra una lista de recifrado de datos disponibles.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

Vuelve a cifrar los datos cifrados con la clave de cifrado actual.

### Argumentos

#### `encryptors`

lista separadas por espacios de los reencriptadores a utilizar.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

Cambie la clave de cifrado dentro del archivo env.php.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--key`, `-k`

La clave debe ser una cadena de 32 caracteres. Si no se proporciona, se generará una clave aleatoria.

- Acepta un valor


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Vuelve a cifrar los datos cifrados de tarjeta de crédito con el cifrado más reciente.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Crear proveedor de Evento personalizado en Adobe Systems eventos de E/S para este instancia. Si no especifica las opciones de etiqueta y descripción, deben definirse en el archivo app/etc/evento-types.json del sistema.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--label`

Una etiqueta para definir su proveedor personalizado.

- Acepta un valor

#### `--description`

Una descripción de su proveedor.

- Acepta un valor


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Generar módulo basados en plugins lista

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Devuelve la carga útil del evento especificado.

### Argumentos

#### `event-code`

Código de evento

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--depth`

El número de niveles de la carga útil evento que se devolverán

- Predeterminado: `2`
- Acepta un valor


## `events:list`

```bash
bin/magento events:list
```

Muestra lista de eventos suscritos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Devuelve un lista de eventos suscritos definidos en el módulo especificado

### Argumentos

#### `module_name`

Nombre del módulo

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Crea metadatos en E/S Adobe Systems desde el lista de configuración (configuraciones XML y aplicación)

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Devuelve detalles sobre el proveedor de evento configurado

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Enumera evento registros en el proyecto aplicación Builder

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

Se suscribe al evento

### Argumentos

#### `event-code`

Código de evento

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--force`, `-f`

Fuerza la suscripción del evento especificado, igualado si no se ha definido localmente.

- Predeterminado: `false`
- No acepta un valor

#### `--fields`

La lista de campos de la carga útil datos de evento.

- Predeterminado: `[]`
- Requiere un valor

#### `--parent`

El elemento principal evento código para una suscripción evento con reglas o como alias.

- Requiere un valor

#### `--rules`

La lista de reglas para la suscripción de evento, donde cada regla tiene el formato &quot;campo\|operador\|valor&quot;. Para utilizar esta opción, también debe especificar la opción &quot;parent&quot;.

- Predeterminado: `[]`
- Requiere un valor

#### `--priority`, `-p`

Acelera la transmisión de este evento. Especifique esta opción para los eventos que deben entregarse inmediatamente. De forma predeterminada, cron envía eventos una vez por minuto.

- Predeterminado: `false`
- No acepta un valor

#### `--destination`, `-d`

El destino de esta evento. Especifique esta opción para los eventos que deben entregarse en el destino personalizado.

- Predeterminado: `default`
- Requiere un valor

#### `--hipaaAuditRequired`

Indica que el evento contiene datos sujetos a auditoría HIPAA.

- Predeterminado: `false`
- No acepta un valor


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Sincronizar metadatos de evento para esta instancia

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--delete`, `-d`

Ya no es necesario eliminar metadatos de eventos

- Predeterminado: `false`
- No acepta un valor


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Quita la suscripción al evento proporcionado

### Argumentos

#### `event-code`

Código de evento desde el que cancelar la suscripción

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Descubre frases en la base de código

### Argumentos

#### `directory`

Ruta de directorio para analizar. No es necesario si está configurado el indicador --magento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--output`, `-o`

Ruta (incluido el nombre del archivo) a un archivo de salida. Sin especificar ningún archivo, el valor predeterminado es stdout.

- Requiere un valor

#### `--magento`, `-m`

Utilice el parámetro —magento para analizar la base de código de Magento actual. Omita el parámetro si se especifica un directorio.

- Predeterminado: `false`
- No acepta un valor


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Guarda el paquete de idioma

### Argumentos

#### `source`

Ruta al archivo de diccionario de origen con traducciones

- Obligatorio


#### `locale`

Target configuración regional del diccionario, por ejemplo, &quot;de_DE&quot;

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--mode`, `-m`

Guardar modo para el diccionario - &quot;reemplazar&quot; - reemplazar el paquete de idioma por uno nuevo - &quot;fusionar&quot; - combinar paquetes de idioma, por defecto &quot;reemplazar&quot;

- Predeterminado: `replace`
- Requiere un valor

#### `--allow-duplicates`, `-d`

Utilice el parámetro --allow-duplicates para poder guardar duplicados de traducción. De lo contrario, omita el parámetro.

- Predeterminado: `false`
- No acepta un valor


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Desinstala paquetes de idioma

### Argumentos

#### `package`

Nombre del paquete de idioma

- Predeterminado: `[]`
- Requerido

- Matriz

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--backup-code`, `-b`

Llevar los archivos de código y configuración copia de seguridad (excluyendo archivos temporales)

- Predeterminado: `false`
- No acepta un valor


## `indexer:info`

```bash
bin/magento indexer:info
```

Muestra los indexadores permitidos

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Reindexe datos

### Argumentos

#### `index`

Los lista separados por espacios de los tipos de índices u omitidos se aplican a todos los índices.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Restablece el estado del indexador a no válido

### Argumentos

#### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Establecer modo de dimensiones del indizador

### Argumentos

#### `indexer`

Nombre [del indizador catalog_product_price|catalogpermissions_categoría]


#### `mode`

Modos de dimensión de indexador catalog_product_price none,website,customer_grupo,website_and_customer_grupo catalogpermissions_categoría none,customer_grupo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Define el tipo de modo de índice

### Argumentos

#### `mode`

Tipo de modo de indexador realtime [|schedule]


#### `index`

Los lista separados por espacios de los tipos de índices u omitidos se aplican a todos los índices.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Establece el estado del indexador especificado

### Argumentos

#### `status`

Tipo de [estado de indexador no válido|suspendido|válido]

- Obligatorio


#### `index`

Los lista separados por espacios de los tipos de índices u omitidos se aplican a todos los índices.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Muestra el modo de Dimension de indexador

### Argumentos

#### `indexer`

lista separados por espacios de tipos de índice u omisión para aplicar a todos los índices (catalog_product_price,catalogpermissions_categoría)

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Muestra el modo Index

### Argumentos

#### `index`

Los lista separados por espacios de los tipos de índices u omitidos se aplican a todos los índices.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Muestra el estado del indizador

### Argumentos

#### `index`

Los lista separados por espacios de los tipos de índices u omitidos se aplican a todos los índices.

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Muestra el URI de administración de Magento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Imprime lista de los archivos de copia de seguridad disponibles

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Muestra la lista de monedas disponibles

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Muestra el número de dependencias de Magento marco de trabajo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--output`, `-o`

Nombre de archivo de informe

- Predeterminado: `framework-dependencies.csv`
- Requiere un valor


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Muestra el número de dependencias entre módulos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--output`, `-o`

Nombre de archivo de informe

- Predeterminado: `modules-dependencies.csv`
- Requiere un valor


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Muestra el número de dependencias circulares entre módulos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--output`, `-o`

Nombre de archivo de informe

- Predeterminado: `modules-circular-dependencies.csv`
- Requiere un valor


## `info:language:list`

```bash
bin/magento info:language:list
```

Muestra la lista de las configuraciones regionales de idioma disponibles

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Muestra la lista de las zonas horarias disponibles

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Crear reservas mediante argumentos de indemnización proporcionados

### Argumentos

#### `compensations`

Lista de argumentos de compensación en formato &quot;:::&quot;

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--raw`, `-r`

Resultado sin procesar

- Predeterminado: `false`
- No acepta un valor


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Mostrar todos los pedidos y productos con inconsistencias cantidad vendibles

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--complete-orders`, `-c`

Mostrar solo inconsistencias para pedidos completos

- Predeterminado: `false`
- No acepta un valor

#### `--incomplete-orders`, `-i`

Mostrar solo inconsistencias para pedidos incompletos

- Predeterminado: `false`
- No acepta un valor

#### `--bunch-size`, `-b`

Define cuántos pedidos se cargarán a la vez

- Predeterminado: `50`
- Acepta un valor

#### `--raw`, `-r`

Salida en bruto

- Predeterminado: `false`
- No acepta un valor


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Descargar e importar nombres geográficos para el algoritmo de selección de origen

### Argumentos

#### `countries`

Lista de códigos de país para importar

- Predeterminado: `[]`
- Obligatorio

- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Establece IP exentas del modo de mantenimiento

### Argumentos

#### `ip`

Direcciones IP permitidas

- Predeterminado: `[]`
- Matriz

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--none`

Borrar las direcciones IP permitidas

- Predeterminado: `false`
- No acepta un valor

#### `--add`

añadir la dirección IP a los lista existentes

- Predeterminado: `false`
- No acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Deshabilita el modo de mantenimiento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--ip`

Direcciones IP permitidas (utilice &quot;ninguno&quot; para borrar las lista IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Activa el modo de mantenimiento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--ip`

Direcciones IP permitidas (utilice &quot;ninguno&quot; para borrar las lista IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Muestra el estado del modo de mantenimiento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Sincronizar contenido con activos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Sincronizar medios almacenamiento y medios activos de la base de datos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `module:config:status`

```bash
bin/magento module:config:status
```

Comprueba la configuración de los módulos en el archivo &#39;app/etc/config.php&#39; e informa si están actualizados o no

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Deshabilita los módulos especificados

### Argumentos

#### `module`

Nombre del módulo

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--force`, `-f`

Omitir comprobación de dependencias

- Predeterminado: `false`
- No acepta un valor

#### `--all`

Deshabilitar todos los módulos

- Predeterminado: `false`
- No acepta un valor

#### `--clear-static-content`, `-c`

Borre los archivos de vista estáticos generados. Necesario si los módulo tienen archivos de vista estáticos

- Predeterminado: `false`
- No acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Habilita módulos especificados

### Argumentos

#### `module`

Nombre del módulo

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--force`, `-f`

Omitir comprobación de dependencias

- Predeterminado: `false`
- No acepta un valor

#### `--all`

Habilitar todos los módulos

- Predeterminado: `false`
- No acepta un valor

#### `--clear-static-content`, `-c`

Borre los archivos de vista estáticos generados. Necesario si los módulo tienen archivos de vista estáticos

- Predeterminado: `false`
- No acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Muestra el estado de los módulos

### Argumentos

#### `module-names`

Nombre de módulo opcional

- Predeterminado: `[]`
- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--enabled`

Impresión solo módulos habilitados

- Predeterminado: `false`
- No acepta un valor

#### `--disabled`

Impresión solo módulos deshabilitados

- Predeterminado: `false`
- No acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Desinstala módulos instalados por composer

### Argumentos

#### `module`

Nombre del módulo

- Predeterminado: `[]`
- Obligatorio

- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--remove-data`, `-r`

Quitar datos instalados por los módulo

- Predeterminado: `false`
- No acepta un valor

#### `--backup-code`

Llevar los archivos de código y configuración copia de seguridad (excluyendo archivos temporales)

- Predeterminado: `false`
- No acepta un valor

#### `--backup-media`

Toma medios copia de seguridad

- Predeterminado: `false`
- No acepta un valor

#### `--backup-db`

Tome el copia de seguridad completo de la base de datos

- Predeterminado: `false`
- No acepta un valor

#### `--non-composer`

Todos los módulos que pasarán aquí no estarán basados en el compositor

- Predeterminado: `false`
- No acepta un valor

#### `--clear-static-content`, `-c`

Borre los archivos de vista estáticos generados. Necesario si los módulo tienen archivos de vista estáticos

- Predeterminado: `false`
- No acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Verifique el cola de implementar para las entradas y cree un marcador de implementar apropiado.

### Argumentos

#### `message`

¿Implementar Enviar mensaje?

- Obligatorio


#### `change_log`

¿Cambiar registro?

- Obligatorio


#### `user`

Usuario de implementación


#### `revision`

Revisión

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Lista de consumidores de MessageQueue

```
This command shows list of MessageQueue consumers.
```

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Reiniciar consumidores de MessageQueue

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

Inicio Consumidor de MessageQueue

```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```

### Argumentos

#### `consumer`

Nombre del consumidor que se va a iniciar.

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--max-messages`

El número de mensajes que debe procesar el consumidor antes de la finalización del proceso. Si no se especifica, finalice después de procesar todos los mensajes en cola.

- Requiere un valor

#### `--batch-size`

Número de mensajes por lote. Aplicable sólo al consumidor del lote.

- Requiere un valor

#### `--area-code`

El área predeterminada de preferencia (global, adminhtml, etc...) es global.

- Requiere un valor

#### `--single-thread`

Esta opción evita ejecutar varias copias de un consumidor simultáneamente.

- Predeterminado: `false`
- No acepta un valor

#### `--multi-process`

El número de procesos por consumidor.

- Acepta un valor

#### `--pid-file-path`

La ruta del archivo para guardar el PID (Esta opción está obsoleta, utilice --single-thread en su lugar)

- Requiere un valor


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Sincronice medios archivos con Remote almacenamiento.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

Vuelve a sincronizar fuente datos con el servicio SaaS.

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--feed`

Nombre de la fuente para volver a sincronizar completamente al servicio SaaS. Fuentes disponibles: Producción de pedidos de servicios de pago, Sandbox de pedidos de servicios de pago, Producción de pedidos Estado de servicios de pago, Sandbox de Estado de pedidos de servicios de pago, Producción de la tienda de servicios de pago, Sandbox de la tienda de servicios de pago

- Requiere un valor

#### `--no-reindex`

Ejecute el reenvío de datos de fuente solo al servicio SaaS. No vuelve a indexar. (Esta opción no se aplica a productos, anulaciones de productos, fuentes de precios)

- Predeterminado: `false`
- No acepta un valor

#### `--cleanup-feed`

Forzar la limpieza de fuente tabla del indizador antes sincronizar.

- Predeterminado: `false`
- No acepta un valor

#### `--dry-run`

Pista en seco. Los datos no se exportarán. Para guardar la carga útil en archivo de registro var/log/saas-export.log ejecute env variable EXPORTER_EXTENDED_LOG=1.

- Predeterminado: `false`
- No acepta un valor

#### `--thread-count`

Configure el recuento de subprocesos de sincronización.

- Requiere un valor

#### `--batch-size`

Configurar el tamaño del lote de sincronización

- Requiere un valor

#### `--continue-resync`

Continuar resincronizar desde la última posición almacenada (esta opción es aplicable a productos, anulaciones de productos, fuentes de precios)

- Predeterminado: `false`
- No acepta un valor

#### `--by-ids`

Se vuelve a sincronizar parcialmente según lista de los identificadores proporcionados. (Esta opción se aplica a los productos, sobrescrituras de productos y fuentes de precios)

- Requiere un valor

#### `--id-type`

Tipo de identificadores para la resincronización parcial (por ejemplo, sku, productId, etc.)

- Requiere un valor


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Implementar módulos de datos de ejemplo para instalaciones de Magento basadas en compositor

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

- Predeterminado: `false`
- No acepta un valor


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Quitar todos los paquetes de datos de ejemplo de composer.json

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

- Predeterminado: `false`
- No acepta un valor


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Restablecer todos los módulos de datos de ejemplo para su reinstalación

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Deshabilite reCAPTCHA para el administrador usuario olvidó contraseña formulario

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Deshabilitar reCAPTCHA para administradores usuario inicio de sesión formulario

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Establezca el secreto utilizado para la generación de Google OTP.

### Argumentos

#### `user`

Nombre de usuario

- Requerido


#### `secret`

Secreto

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Enumerar todos los proveedores disponibles

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Restablecer la configuración de un usuario

### Argumentos

#### `user`

Nombre de usuario

- Requerido


#### `provider`

Código de proveedor

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Ejecutar aplicación servidor

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--port`, `-p`

puerto en el que servir

- Predeterminado: `9501`
- Acepta un valor

#### `--background`, `-b`

Modo de fondo indicador

- Predeterminado: `0`
- Acepta un valor

#### `--workerNum`, `-wn`

Número de procesos de trabajo a inicio

- Predeterminado: `4`
- Acepta un valor

#### `--dispatchMode`, `-dm`

modo de envío de conexiones a los procesos de trabajo

- Predeterminado: `3`
- Acepta un valor

#### `--maxRequests`, `-mr`

Solicitudes máximas antes de que se reinicie el proceso de trabajo

- Predeterminado: `10000`
- Acepta un valor

#### `--area`, `-a`

área del servidor de aplicaciones

- Predeterminado: `graphql`
- Acepta un valor

#### `--magento-init-params`, `-mip`

parámetros init de bootstrap de magento

- Predeterminado: &quot;
- Acepta un valor

#### `--maxWaitTime`, `-mwt`

cuánto tiempo esperar para los trabajadores después de recargar (p. ej. cambio de configuración) antes de matarlos

- Predeterminado: `3600`
- Acepta un valor

#### `--state-monitor`

Habilite la supervisión de estado. Utilice este parámetro solo para depurar problemas de estado.

- Predeterminado: `false`
- No acepta un valor


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Resultado agregado del monitor de estado de ApplicationServer

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Toma copia de seguridad de Magento base de código, medios y base de datos de Application

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--code`

Llevar los archivos de código y configuración copia de seguridad (excluyendo archivos temporales)

- Predeterminado: `false`
- No acepta un valor

#### `--media`

Toma medios copia de seguridad

- Predeterminado: `false`
- No acepta un valor

#### `--db`

Tome el copia de seguridad completo de la base de datos

- Predeterminado: `false`
- No acepta un valor

#### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización de Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crea o modifica la configuración implementación

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--remote-storage-driver`

Controlador de almacenamiento remoto

- Requiere un valor

#### `--remote-storage-prefix`

Prefijo de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

#### `--remote-storage-endpoint`

Punto final de almacenamiento remoto

- Requiere un valor

#### `--remote-storage-bucket`

Bloque de almacenamiento remoto

- Requiere un valor

#### `--remote-storage-region`

Región de almacenamiento remoto

- Requiere un valor

#### `--remote-storage-key`

Clave de acceso al almacenamiento remoto

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--remote-storage-secret`

Clave secreta almacenamiento remota

- Predeterminado: &quot;
- Requiere un valor

#### `--remote-storage-path-style`

Estilo de ruta de almacenamiento remota

- Predeterminado: `0`
- Requiere un valor

#### `--backend-frontname`

Nombre principal del backend (se generará automáticamente si falta)

- Requiere un valor

#### `--enable-debug-logging`

Habilitar depurar registro

- Requiere un valor

#### `--enable-syslog-logging`

Habilitar el registro syslog

- Requiere un valor

#### `--id_salt`

Sal GraphQl

- Requiere un valor

#### `--checkout-async`

¿Habilitar el procesamiento asíncrono de pedidos? 1 - Sí, 0 - No

- Requiere un valor

#### `--config-async`

¿Habilitar la configuración de administración asíncrona Guardar? 1 - Sí, 0 - No

- Requiere un valor

#### `--amqp-host`

host del servidor Amqp

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--amqp-port`

puerto del servidor Amqp

- Predeterminado: `5672`
- Requiere un valor

#### `--amqp-user`

Nombre de usuario del servidor Amqp

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--amqp-password`

contraseña del servidor Amqp

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--amqp-virtualhost`

Amqp virtualhost

- Predeterminado: `/`
- Requiere un valor

#### `--amqp-ssl`

Amqp SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--amqp-ssl-options`

AMQP SSL Opciones (JSON)

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--consumers-wait-for-messages`

¿Deben los consumidores esperar un mensaje del cola? 1 - Sí, 0 - No

- Requiere un valor

#### `--queue-default-connection`

Enviar mensaje la conexión predeterminada de cola. Puede ser &#39;db&#39;, &#39;amqp&#39; o un sistema cola personalizado. El sistema cola debe estar instalado y configurado, de lo contrario los mensajes no se procesarán correctamente.

- Requiere un valor

#### `--deferred-total-calculating`

¿Habilitar el cálculo total diferido? 1 - Sí, 0 - No

- Requiere un valor

#### `--key`

Clave de cifrado

- Requiere un valor

#### `--db-host`

Servidor de base de datos host

- Requiere un valor

#### `--db-name`

Nombre de la base de datos

- Requiere un valor

#### `--db-user`

Nombre de usuario del servidor de base de datos

- Requiere un valor

#### `--db-engine`

Motor del servidor de base de datos

- Requiere un valor

#### `--db-password`

Servidor de base de datos contraseña

- Requiere un valor

#### `--db-prefix`

Prefijo de tabla de base de datos

- Requiere un valor

#### `--db-model`

Tipo de base de datos

- Requiere un valor

#### `--db-init-statements`

Conjunto inicial de comandos de la base de datos

- Requiere un valor

#### `--skip-db-validation`, `-s`

Si se especifica, se omitirá la validación de conexión db

- Predeterminado: `false`
- No acepta un valor

#### `--http-cache-hosts`

Hosts de caché http

- Requiere un valor

#### `--db-ssl-key`

Ruta completa del archivo de clave de cliente para establecer la conexión db a través de SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--db-ssl-cert`

Ruta completa del archivo de certificado de cliente para establecer una conexión db a través de SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--db-ssl-ca`

Ruta completa del archivo de certificado del servidor para establecer la conexión db a través de SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--db-ssl-verify`

Verificar la certificación del servidor

- Predeterminado: `false`
- No acepta un valor

#### `--session-save`

Controlador de guardado de sesión

- Requiere un valor

#### `--session-save-redis-host`

Nombre de host completo, dirección IP o ruta de acceso absoluta si se utilizan sockets UNIX

- Requiere un valor

#### `--session-save-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--session-save-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--session-save-redis-timeout`

Tiempo de espera de la conexión, en segundos

- Requiere un valor

#### `--session-save-redis-retries`

reintentos de conexión Redis.

- Requiere un valor

#### `--session-save-redis-persistent-id`

Cadena única para habilitar las conexiones persistentes

- Requiere un valor

#### `--session-save-redis-db`

Número de base de datos de Redis

- Requiere un valor

#### `--session-save-redis-compression-threshold`

umbral de compresión Redis

- Requiere un valor

#### `--session-save-redis-compression-lib`

Compresión Redis biblioteca. Valores: gzip (predeterminado), lzf, lz4, snappy

- Requiere un valor

#### `--session-save-redis-log-level`

Nivel de registro de Redis. Valores: 0 (menos detallado) a 7 (más detallado)

- Requiere un valor

#### `--session-save-redis-max-concurrency`

Número máximo de procesos que pueden esperar un bloqueo en una sesión

- Requiere un valor

#### `--session-save-redis-break-after-frontend`

Número de segundos que esperar antes de intentar romper un bloqueo para una sesión front-end

- Requiere un valor

#### `--session-save-redis-break-after-adminhtml`

Número de segundos que esperar antes de intentar romper un bloqueo para la sesión de administrador

- Requiere un valor

#### `--session-save-redis-first-lifetime`

Duración en segundos de la sesión para los no bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

#### `--session-save-redis-bot-first-lifetime`

Duración en segundos de la sesión de los bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

#### `--session-save-redis-bot-lifetime`

Duración de la sesión para bots en escrituras posteriores (use 0 para deshabilitar)

- Requiere un valor

#### `--session-save-redis-disable-locking`

Redis deshabilita el bloqueo. Valores: false (predeterminado), true

- Requiere un valor

#### `--session-save-redis-min-lifetime`

Sesión mínima de Redis vida útil, en segundos

- Requiere un valor

#### `--session-save-redis-max-lifetime`

Sesión máxima de Redis vida útil, en segundos

- Requiere un valor

#### `--session-save-redis-sentinel-master`

Maestro Centinela de Redis

- Requiere un valor

#### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por comas

- Requiere un valor

#### `--session-save-redis-sentinel-verify-master`

Maestro de verificación Redis Sentinel. Valores: false (predeterminado), true

- Requiere un valor

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conecta reintentos.

- Requiere un valor

#### `--cache-backend`

Gestor de caché predeterminado

- Requiere un valor

#### `--cache-backend-redis-server`

Servidor Redis

- Requiere un valor

#### `--cache-backend-redis-db`

Número de base de datos de la caché

- Requiere un valor

#### `--cache-backend-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--cache-backend-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--cache-backend-redis-compress-data`

Configúrelo en 0 para desactivar la compresión (el valor predeterminado es 1, habilitado)

- Requiere un valor

#### `--cache-backend-redis-compression-lib`

Compresión lib para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

#### `--cache-backend-redis-use-lua`

Establezca el valor en 1 para habilitar lua (el valor predeterminado es 0, deshabilitado)

- Requiere un valor

#### `--cache-backend-redis-use-lua-on-gc`

Establezca el valor en 0 para deshabilitar lua en la recolección de elementos no utilizados (el valor predeterminado es 1, habilitado)

- Requiere un valor

#### `--cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

#### `--allow-parallel-generation`

Permitir generar caché de forma no bloqueante

- Predeterminado: `false`
- No acepta un valor

#### `--page-cache`

Gestor de caché predeterminado

- Requiere un valor

#### `--page-cache-redis-server`

Servidor Redis

- Requiere un valor

#### `--page-cache-redis-db`

Número de base de datos de la caché

- Requiere un valor

#### `--page-cache-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

#### `--page-cache-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--page-cache-redis-compress-data`

Establezca este valor en 1 para comprimir la caché completa del Página (use 0 para deshabilitar)

- Requiere un valor

#### `--page-cache-redis-compression-lib`

Biblioteca de compresión para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

#### `--page-cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

#### `--lock-provider`

Bloquear nombre de proveedor

- Requiere un valor

#### `--lock-db-prefix`

Prefijo de bloqueo específico de la instalación para evitar conflictos de bloqueo

- Requiere un valor

#### `--lock-zookeeper-host`

Aloje y puerto conectarse al clúster de Zookeeper. Por ejemplo: 127.0.0.1:2181

- Requiere un valor

#### `--lock-zookeeper-path`

La ruta donde Zookeeper guardará los bloqueos. La ruta predeterminada es: /magento/locks

- Requiere un valor

#### `--lock-file-path`

La ruta donde se guardarán los bloqueos de archivos.

- Requiere un valor

#### `--document-root-is-pub`

El indicador que se mostrará es Pub está en la raíz, puede ser verdadero o falso solamente

- Requiere un valor

#### `--backpressure-logger`

Manipulador del registrador de contrapresión

- Requiere un valor

#### `--backpressure-logger-redis-server`

Servidor Redis

- Requiere un valor

#### `--backpressure-logger-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--backpressure-logger-redis-timeout`

Tiempo de espera del servidor Redis

- Requiere un valor

#### `--backpressure-logger-redis-persistent`

Redis persistente

- Requiere un valor

#### `--backpressure-logger-redis-db`

Número de base de datos en Redis

- Requiere un valor

#### `--backpressure-logger-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--backpressure-logger-redis-user`

usuario del servidor Redis

- Requiere un valor

#### `--backpressure-logger-id-prefix`

Prefijo de ID para las claves

- Requiere un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala y actualiza datos en la base de datos

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización de Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Genere el parche y colóquelo en una carpeta específica.

### Argumentos

#### `module`

Nombre de módulo

- Requerido


#### `patch`

Nombre del parche

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--revertable`

Compruebe si parche es revertible o no.

- Predeterminado: `false`
- Acepta un valor

#### `--type`

Averigüe qué tipo de parche se debe generar. Valores disponibles: `data`, `schema`.

- Predeterminado: `data`
- Acepta un valor


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Generar una lista blanca de tablas y columnas que el instalador de declaraciones puede editar

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--module-name`

Nombre de la módulo en la que se generará la lista blanca

- Predeterminado: `all`
- Acepta un valor


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mueva las tablas relacionadas con las cotizaciones de compra a un servidor de base de datos independiente

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--host`

host de servidor de base de datos esclavo

- Predeterminado: `localhost`
- Requiere un valor

#### `--dbname`

Nombre de la base de datos esclava

- Requiere un valor

#### `--username`

Nombre de usuario de base de datos esclava

- Predeterminado: `root`
- Requiere un valor

#### `--password`

contraseña de usuario de base de datos esclava

- Acepta un valor

#### `--connection`

Nombre de la conexión esclava

- Predeterminado: `default`
- Acepta un valor

#### `--resource`

Nombre del recurso esclavo

- Predeterminado: `default`
- Acepta un valor

#### `--maxAllowedLag`

Retraso máximo permitido Conexión esclava (en segundos)

- Valor predeterminado: &#39;&#39;
- Acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mueva las tablas relacionadas con las cotizaciones de compra a un servidor de base de datos independiente. En desuso desde la versión 2.4.2 y se eliminará

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--host`

Cierre de la host del servidor de base de datos

- Requiere un valor

#### `--dbname`

Nombre de la base de datos de cierre de compra

- Requiere un valor

#### `--username`

Nombre del usuario de la base de datos de verificación

- Requiere un valor

#### `--password`

Checkout DB usuario contraseña

- Acepta un valor

#### `--connection`

Nombre de la conexión de cierre de compra

- Predeterminado: `checkout`
- Acepta un valor

#### `--resource`

Nombre del recurso de cierre de compra

- Predeterminado: `checkout`
- Acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Mover las tablas relacionadas con las ventas a un servidor de base de datos independiente. En desuso desde la versión 2.4.2 y se eliminará

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--host`

Servidor de base de datos de ventas host

- Requiere un valor

#### `--dbname`

Nombre de la base de datos de ventas

- Requiere un valor

#### `--username`

Nombre del usuario de la base de datos de ventas

- Requiere un valor

#### `--password`

Base de datos de ventas usuario passowrd

- Acepta un valor

#### `--connection`

Nombre de conexión de ventas

- Predeterminado: `sales`
- Acepta un valor

#### `--resource`

Nombre del recurso de ventas

- Predeterminado: `sales`
- Acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala y actualiza la base de datos esquema

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) a db_esquema.xml formato

- Predeterminado: `false`
- Acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Comprueba si los datos o esquema de la base de datos requieren actualización

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Genera la configuración de DI y todas las clases que faltan que se pueden generar automáticamente

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala el aplicación de Magento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--remote-storage-driver`

Controlador de almacenamiento remoto

- Requiere un valor

#### `--remote-storage-prefix`

Prefijo almacenamiento remoto

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--remote-storage-endpoint`

Punto final de almacenamiento remoto

- Requiere un valor

#### `--remote-storage-bucket`

Depósito almacenamiento remoto

- Requiere un valor

#### `--remote-storage-region`

área geográfica almacenamiento remoto

- Requiere un valor

#### `--remote-storage-key`

Clave de acceso al almacenamiento remoto

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--remote-storage-secret`

Clave secreta almacenamiento remota

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--remote-storage-path-style`

Estilo de ruta de almacenamiento remota

- Predeterminado: `0`
- Requiere un valor

#### `--backend-frontname`

Nombre del front-end (se generará automáticamente si falta)

- Requiere un valor

#### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

#### `--enable-syslog-logging`

Habilitar registro syslog

- Requiere un valor

#### `--id_salt`

Sal GraphQl

- Requiere un valor

#### `--checkout-async`

¿Habilitar el procesamiento asíncrono de pedidos? 1 - Sí, 0 - No

- Requiere un valor

#### `--config-async`

¿Habilitar Guardar configuración de administración asincrónica? 1 - Sí, 0 - No

- Requiere un valor

#### `--amqp-host`

Host del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

#### `--amqp-port`

puerto del servidor Amqp

- Predeterminado: `5672`
- Requiere un valor

#### `--amqp-user`

Nombre de usuario del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

#### `--amqp-password`

Contraseña del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

#### `--amqp-virtualhost`

Amqp virtualhost

- Predeterminado: `/`
- Requiere un valor

#### `--amqp-ssl`

Amqp SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--amqp-ssl-options`

AMQP SSL Opciones (JSON)

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--consumers-wait-for-messages`

¿Deben los consumidores esperar un mensaje del cola? 1 - Sí, 0 - No

- Requiere un valor

#### `--queue-default-connection`

Enviar mensaje la conexión predeterminada de cola. Puede ser &#39;db&#39;, &#39;amqp&#39; o un sistema cola personalizado. El sistema cola debe estar instalado y configurado, de lo contrario los mensajes no se procesarán correctamente.

- Requiere un valor

#### `--deferred-total-calculating`

¿Habilitar el cálculo total diferido? 1 - Sí, 0 - No

- Requiere un valor

#### `--key`

Clave de cifrado

- Requiere un valor

#### `--db-host`

Host del servidor de base de datos

- Requiere un valor

#### `--db-name`

Nombre de la base de datos

- Requiere un valor

#### `--db-user`

Nombre de usuario del servidor

- Requiere un valor

#### `--db-engine`

Motor del servidor de base de datos

- Requiere un valor

#### `--db-password`

Servidor de base de datos contraseña

- Requiere un valor

#### `--db-prefix`

Prefijo de tabla de base de datos

- Requiere un valor

#### `--db-model`

Tipo de base de datos

- Requiere un valor

#### `--db-init-statements`

Conjunto inicial de comandos de la base de datos

- Requiere un valor

#### `--skip-db-validation`, `-s`

Si se especifica, se omitirá la validación de conexión db

- Predeterminado: `false`
- No acepta un valor

#### `--http-cache-hosts`

Hosts de caché http

- Requiere un valor

#### `--db-ssl-key`

Ruta completa del archivo de clave de cliente para establecer la conexión db a través de SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--db-ssl-cert`

Ruta completa del archivo de certificado de cliente para establecer una conexión db a través de SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--db-ssl-ca`

Ruta completa del archivo de certificado del servidor para establecer la conexión db a través de SSL

- Valor predeterminado: &#39;&#39;
- Requiere un valor

#### `--db-ssl-verify`

Verificar la certificación del servidor

- Predeterminado: `false`
- No acepta un valor

#### `--session-save`

Controlador de guardado de sesión

- Requiere un valor

#### `--session-save-redis-host`

Nombre de host completo, dirección IP o ruta de acceso absoluta si se utilizan sockets UNIX

- Requiere un valor

#### `--session-save-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--session-save-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--session-save-redis-timeout`

Tiempo de espera de la conexión, en segundos

- Requiere un valor

#### `--session-save-redis-retries`

reintentos de conexión Redis.

- Requiere un valor

#### `--session-save-redis-persistent-id`

Cadena única para habilitar las conexiones persistentes

- Requiere un valor

#### `--session-save-redis-db`

Número de base de datos de Redis

- Requiere un valor

#### `--session-save-redis-compression-threshold`

umbral de compresión Redis

- Requiere un valor

#### `--session-save-redis-compression-lib`

Compresión Redis biblioteca. Valores: gzip (predeterminado), lzf, lz4, snappy

- Requiere un valor

#### `--session-save-redis-log-level`

Nivel de registro de Redis. Valores: 0 (menos detallado) a 7 (más detallado)

- Requiere un valor

#### `--session-save-redis-max-concurrency`

Número máximo de procesos que pueden esperar un bloqueo en una sesión

- Requiere un valor

#### `--session-save-redis-break-after-frontend`

Número de segundos que esperar antes de intentar romper un bloqueo para una sesión front-end

- Requiere un valor

#### `--session-save-redis-break-after-adminhtml`

Número de segundos que esperar antes de intentar romper un bloqueo para la sesión de administrador

- Requiere un valor

#### `--session-save-redis-first-lifetime`

Duración en segundos de la sesión para los no bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

#### `--session-save-redis-bot-first-lifetime`

Duración en segundos de la sesión de los bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

#### `--session-save-redis-bot-lifetime`

Duración de la sesión para bots en escrituras posteriores (use 0 para deshabilitar)

- Requiere un valor

#### `--session-save-redis-disable-locking`

Redis deshabilita el bloqueo. Valores: false (predeterminado), true

- Requiere un valor

#### `--session-save-redis-min-lifetime`

Sesión mínima de Redis vida útil, en segundos

- Requiere un valor

#### `--session-save-redis-max-lifetime`

Sesión máxima de Redis vida útil, en segundos

- Requiere un valor

#### `--session-save-redis-sentinel-master`

Maestro Centinela de Redis

- Requiere un valor

#### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por comas

- Requiere un valor

#### `--session-save-redis-sentinel-verify-master`

Maestro de verificación Redis Sentinel. Valores: false (predeterminado), true

- Requiere un valor

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conecta reintentos.

- Requiere un valor

#### `--cache-backend`

Gestor de caché predeterminado

- Requiere un valor

#### `--cache-backend-redis-server`

Servidor Redis

- Requiere un valor

#### `--cache-backend-redis-db`

Número de base de datos de la caché

- Requiere un valor

#### `--cache-backend-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--cache-backend-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--cache-backend-redis-compress-data`

Configúrelo en 0 para desactivar la compresión (el valor predeterminado es 1, habilitado)

- Requiere un valor

#### `--cache-backend-redis-compression-lib`

Compresión lib para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

#### `--cache-backend-redis-use-lua`

Establezca este valor en 1 para habilitar lua (el valor predeterminado es 0, deshabilitado)

- Requiere un valor

#### `--cache-backend-redis-use-lua-on-gc`

Configúrelo en 0 para deshabilitar lua en el colección basura (el valor predeterminado es 1, habilitado)

- Requiere un valor

#### `--cache-id-prefix`

Prefijo de ID para las claves de caché

- Requiere un valor

#### `--allow-parallel-generation`

Permitir generar caché de forma no bloqueante

- Predeterminado: `false`
- No acepta un valor

#### `--page-cache`

Gestor de caché predeterminado

- Requiere un valor

#### `--page-cache-redis-server`

Servidor Redis

- Requiere un valor

#### `--page-cache-redis-db`

Número de base de datos de la caché

- Requiere un valor

#### `--page-cache-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--page-cache-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--page-cache-redis-compress-data`

Establezca este valor en 1 para comprimir la caché completa del Página (use 0 para deshabilitar)

- Requiere un valor

#### `--page-cache-redis-compression-lib`

Compresión biblioteca usar [Snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

#### `--page-cache-id-prefix`

Prefijo de ID para las claves de caché

- Requiere un valor

#### `--lock-provider`

Bloquear nombre de proveedor

- Requiere un valor

#### `--lock-db-prefix`

Prefijo de bloqueo específico de la instalación para evitar conflictos de bloqueo

- Requiere un valor

#### `--lock-zookeeper-host`

Aloje y puerto conectarse al clúster de Zookeeper. Por ejemplo: 127.0.0.1:2181

- Requiere un valor

#### `--lock-zookeeper-path`

La ruta donde Zookeeper guardará los bloqueos. La ruta predeterminada es: /magento/locks

- Requiere un valor

#### `--lock-file-path`

La ruta donde se guardarán los bloqueos de archivos.

- Requiere un valor

#### `--document-root-is-pub`

El indicador que se mostrará es Pub está en la raíz, puede ser verdadero o falso solamente

- Requiere un valor

#### `--backpressure-logger`

Manipulador del registrador de contrapresión

- Requiere un valor

#### `--backpressure-logger-redis-server`

Servidor Redis

- Requiere un valor

#### `--backpressure-logger-redis-port`

Servidor Redis escuchar puerto

- Requiere un valor

#### `--backpressure-logger-redis-timeout`

Tiempo de espera del servidor Redis

- Requiere un valor

#### `--backpressure-logger-redis-persistent`

Redis persistente

- Requiere un valor

#### `--backpressure-logger-redis-db`

Número de base de datos en Redis

- Requiere un valor

#### `--backpressure-logger-redis-password`

contraseña del servidor Redis

- Requiere un valor

#### `--backpressure-logger-redis-user`

usuario del servidor Redis

- Requiere un valor

#### `--backpressure-logger-id-prefix`

Prefijo de ID para las claves

- Requiere un valor

#### `--base-url`

URL se supone que el tienda está disponible en. Deprecated, use config:set con la ruta web/unsecure/base_url

- Requiere un valor

#### `--language`

Código de idioma predeterminado. En desuso, utilice config:set con ruta general/locale/code

- Requiere un valor

#### `--timezone`

Código de zona horaria predeterminado. En desuso, utilice config:set con ruta general/locale/timezone

- Requiere un valor

#### `--currency`

Código de moneda predeterminado. En desuso, utilice config:set con ruta currency/options/base, currency/options/default y currency/options/allow

- Requiere un valor

#### `--use-rewrites`

Usar reescrituras. En desuso, use config:set con ruta web/seo/use_rewrites

- Requiere un valor

#### `--use-secure`

Utilice direcciones URL seguras. Active esta opción sólo si SSL está disponible. En desuso, utilice config:set con ruta web/secure/use_in_frontend

- Requiere un valor

#### `--base-url-secure`

URL base para la conexión SSL. Deprecated, use config:set con la ruta web/secure/base_url

- Requiere un valor

#### `--use-secure-admin`

Ejecute la interfaz de administración con SSL. En desuso, use config:set con ruta web/secure/use_in_adminhtml

- Requiere un valor

#### `--admin-use-security-key`

Si se debe utilizar una función de &quot;clave de seguridad&quot; en Magento URL y formularios de administración. En desuso, use config:set con ruta admin/security/use_form_key

- Requiere un valor

#### `--admin-user`

usuario de administración

- Acepta un valor

#### `--admin-password`

Administrador contraseña

- Acepta un valor

#### `--admin-email`

Administrador correo electrónico

- Acepta un valor

#### `--admin-firstname`

Nombre del administrador

- Acepta un valor

#### `--admin-lastname`

Apellido del administrador

- Acepta un valor

#### `--search-engine`

Motor de búsqueda. Valores: elasticsearch8, opensearch

- Requiere un valor

#### `--elasticsearch-host`

Elasticsearch servidor host.

- Requiere un valor

#### `--elasticsearch-port`

Elasticsearch servidor puerto.

- Requiere un valor

#### `--elasticsearch-enable-auth`

Se establece en 1 para habilitar la autenticación. (el valor predeterminado es 0, deshabilitado)

- Requiere un valor

#### `--elasticsearch-username`

Nombre de usuario de Elasticsearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

#### `--elasticsearch-password`

Contraseña de Elasticsearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

#### `--elasticsearch-index-prefix`

Elasticsearch prefijo de índice.

- Requiere un valor

#### `--elasticsearch-timeout`

Elasticsearch tiempo de espera del servidor.

- Requiere un valor

#### `--opensearch-host`

host del servidor OpenSearch.

- Requiere un valor

#### `--opensearch-port`

puerto del servidor OpenSearch.

- Requiere un valor

#### `--opensearch-enable-auth`

Establezca el valor en 1 para habilitar la autenticación. (el valor predeterminado es 0, desactivado)

- Requiere un valor

#### `--opensearch-username`

Nombre de usuario de OpenSearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

#### `--opensearch-password`

OpenSearch contraseña. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

#### `--opensearch-index-prefix`

Prefijo de índice de OpenSearch.

- Requiere un valor

#### `--opensearch-timeout`

Tiempo de espera del servidor OpenSearch.

- Requiere un valor

#### `--cleanup-database`

Limpie la base de datos antes de la instalación

- Predeterminado: `false`
- No acepta un valor

#### `--sales-order-increment-prefix`

Prefijo del número de pedido de ventas

- Requiere un valor

#### `--use-sample-data`

Uso de datos de ejemplo

- Predeterminado: `false`
- No acepta un valor

#### `--enable-modules`

Lista de nombres de módulo separados por comas. Eso debe incluirse durante la instalación. Parámetro mágico disponible &quot;todo&quot;.

- Acepta un valor

#### `--disable-modules`

Lista de nombres de módulos separados por comas. Debe evitarse durante la instalación. Parámetro mágico disponible &quot;todo&quot;.

- Acepta un valor

#### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) al formato db_schema.xml.

- Predeterminado: `false`
- Acepta un valor

#### `--interactive`, `-i`

interactivo instalación Magento

- Predeterminado: `false`
- No acepta un valor

#### `--safe-mode`

Instalación segura de Magento con volcados en operaciones destructivas, gustar eliminación de columnas

- Acepta un valor

#### `--data-restore`

Restaurar los datos eliminados de los volcados

- Acepta un valor

#### `--dry-run`

Magento La instalación se ejecutará en modo de funcionamiento en seco

- Predeterminado: `false`
- Acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Genera luminarias

### Argumentos

#### `profile`

Ruta al archivo de configuración de perfil

- Requerido

### Opciones

Para ver las opciones globales, consulte [Opciones globales](#global-options).

#### `--skip-reindex`, `-s`

Omitir reindexación

- Predeterminado: `false`
- No acepta un valor


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Revierte el código base, los medios y la base de datos de la aplicación Magento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--code-file`, `-c`

Nombre base del archivo de copia de seguridad de código en var/backups

- Requiere un valor

#### `--media-file`, `-m`

Nombre base del archivo de copia de seguridad de medios en var/backups

- Requiere un valor

#### `--db-file`, `-d`

Nombre base del archivo de copia de seguridad de base de datos en var/backups

- Requiere un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Implementa archivos de vista estática

### Argumentos

#### `languages`

Lista separada por espacios de códigos de idioma ISO-639 para los que se van a generar archivos de vista estática.

- Predeterminado: `[]`
- Matriz

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--force`, `-f`

Implemente archivos en cualquier modo.

- Predeterminado: `false`
- No acepta un valor

#### `--strategy`, `-s`

Implemente archivos mediante la estrategia especificada.

- Predeterminado: `quick`
- Acepta un valor

#### `--area`, `-a`

Genere archivos solo para las áreas especificadas.

- Predeterminado: `all`
- Acepta varios valores

#### `--exclude-area`

No genere archivos para las áreas especificadas.

- Predeterminado: `none`
- Acepta varios valores

#### `--theme`, `-t`

Genere archivos de vista estáticos solo para el temáticas especificado.

- Predeterminado: `all`
- Acepta varios valores

#### `--exclude-theme`

No genere archivos para el temáticas especificado.

- Predeterminado: `none`
- Acepta varios valores

#### `--language`, `-l`

Generar archivos solo para los idiomas especificados.

- Predeterminado: `all`
- Acepta varios valores

#### `--exclude-language`

No genere archivos para los idiomas especificados.

- Predeterminado: `none`
- Acepta varios valores

#### `--jobs`, `-j`

Habilite el procesamiento paralelo utilizando el número especificado de trabajos.

- Predeterminado: `0`
- Acepta un valor

#### `--max-execution-time`

Tiempo de ejecución máximo previsto de implementación proceso estático (en segundos).

- Predeterminado: `900`
- Acepta un valor

#### `--symlink-locale`

Crear los enlaces simbólicos para los archivos de esas configuraciones regionales, que se pasan por implementación, pero no tienen personalizaciones.

- Predeterminado: `false`
- No acepta un valor

#### `--content-version`

Se puede utilizar una versión personalizada de contenido estática si se ejecuta implementación en varios nodos para garantizar que la versión de contenido estática sea idéntica y almacenamiento en caché funcione correctamente.

- Requiere un valor

#### `--refresh-content-version-only`

La actualización de la versión de contenido estática solo se puede utilizar para actualizar las contenido estáticas en la caché de Caché del explorador y CDN.

- Predeterminado: `false`
- No acepta un valor

#### `--no-javascript`

No implementar JavaScript archivos.

- Predeterminado: `false`
- No acepta un valor

#### `--no-js-bundle`

No implementar JavaScript paquete archivos.

- Predeterminado: `false`
- No acepta un valor

#### `--no-css`

No implementar archivos CSS.

- Predeterminado: `false`
- No acepta un valor

#### `--no-less`

No implementar archivos LESS.

- Predeterminado: `false`
- No acepta un valor

#### `--no-images`

No implementar imágenes.

- Predeterminado: `false`
- No acepta un valor

#### `--no-fonts`

No implementar fuente archivos.

- Predeterminado: `false`
- No acepta un valor

#### `--no-html`

No implementar archivos HTML.

- Predeterminado: `false`
- No acepta un valor

#### `--no-misc`

No implementar archivos de otros tipos (.md, .jbf, .csv, etc.).

- Predeterminado: `false`
- No acepta un valor

#### `--no-html-minify`

No minimice los archivos HTML.

- Predeterminado: `false`
- No acepta un valor

#### `--no-parent`

No compile temáticas principales. Compatible solo con estrategias rápidas y estándar.

- Predeterminado: `false`
- No acepta un valor


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala la configuración tienda. En desuso desde 2.2.0. Utilice config:set en su lugar

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--base-url`

URL se supone que el tienda está disponible en. Deprecated, use config:set con la ruta web/unsecure/base_url

- Requiere un valor

#### `--language`

Código de idioma predeterminado. En desuso, utilice config:set con ruta general/locale/code

- Requiere un valor

#### `--timezone`

Código de zona horaria predeterminado. En desuso, utilice config:set con ruta general/locale/timezone

- Requiere un valor

#### `--currency`

Código de moneda predeterminado. En desuso, utilice config:set con ruta currency/options/base, currency/options/default y currency/options/allow

- Requiere un valor

#### `--use-rewrites`

Usar reescrituras. En desuso, use config:set con ruta web/seo/use_rewrites

- Requiere un valor

#### `--use-secure`

Utilice direcciones URL seguras. Active esta opción sólo si SSL está disponible. En desuso, utilice config:set con ruta web/secure/use_in_frontend

- Requiere un valor

#### `--base-url-secure`

URL base para la conexión SSL. Deprecated, use config:set con la ruta web/secure/base_url

- Requiere un valor

#### `--use-secure-admin`

Ejecute la interfaz de administración con SSL. En desuso, use config:set con ruta web/secure/use_in_adminhtml

- Requiere un valor

#### `--admin-use-security-key`

Si se debe utilizar una función de &quot;clave de seguridad&quot; en Magento URL y formularios de administración. En desuso, use config:set con ruta admin/security/use_form_key

- Requiere un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Desinstala el aplicación de Magento

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Actualiza el aplicación de Magento, los datos de la base de datos y esquema

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--keep-generated`

Evita que se eliminen los archivos generados. Se desaconseja utilizar esta opción, excepto cuando se implemente en producción. Consulte con su integrador o administrador de sistemas para obtener más información.

- Predeterminado: `false`
- No acepta un valor

#### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) a db_esquema.xml formato

- Predeterminado: `false`
- Acepta un valor

#### `--safe-mode`

Instalación segura de Magento con volcados en operaciones destructivas, gustar eliminación de columnas

- Acepta un valor

#### `--data-restore`

Restauración de datos eliminados de volcados

- Acepta un valor

#### `--dry-run`

La instalación de Magento se ejecutará en modo de ejecución en seco

- Predeterminado: `false`
- Acepta un valor

#### `--magento-init-params`

añadir a cualquier comando para personalizar Magento parámetros de inicialización. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

- Requiere un valor


## `store:list`

```bash
bin/magento store:list
```

Muestra el lista de los almacenes

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `store:website:list`

```bash
bin/magento store:website:list
```

Muestra la lista de los sitios web

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Crear Code copia de seguridad

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--name`

Nombre de volcado

- Acepta un valor

#### `--output`, `-o`

Output ruta

- Acepta un valor

#### `--logs`, `-l`

Incluir registros

- Predeterminado: `false`
- No acepta un valor


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

Crear DB copia de seguridad

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--name`

Nombre de volcado

- Acepta un valor

#### `--output`, `-o`

Output ruta

- Acepta un valor

#### `--logs`, `-l`

Incluir registros

- Predeterminado: `false`
- No acepta un valor

#### `--ignore-sanitize`, `-i`

Ignorar sanear

- Predeterminado: `false`
- No acepta un valor


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Compruebe las utilidades de copia de seguridad necesarias

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--hide-paths`

Compruebe solo las utilidades de consola requeridas

- Predeterminado: `false`
- No acepta un valor


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Crear rutas de utilidades lista

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--force`, `-f`

Fuerza

- Predeterminado: `false`
- No acepta un valor


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Desinstala tema

### Argumentos

#### `theme`

Ruta del tema. La ruta del tema debe especificarse como ruta completa, que es área/proveedor/nombre. Por ejemplo, frontend/Magento/blank

- Predeterminado: `[]`
- Obligatorio

- Arreglo

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--backup-code`

Tome el código copia de seguridad (excluyendo archivos temporales)

- Predeterminado: `false`
- No acepta un valor

#### `--clear-static-content`, `-c`

Borre los archivos de vista estáticos generados.

- Predeterminado: `false`
- No acepta un valor


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Genera Varnish VCL y lo hace eco en la línea de comandos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--access-list`

Las IP acceden a lista que pueden purgar el barniz

- Predeterminado: `localhost`
- Requiere un valor

#### `--backend-host`

Host del backend web

- Predeterminado: `localhost`
- Requiere un valor

#### `--backend-port`

Puerto del backend web

- Predeterminado: `8080`
- Requiere un valor

#### `--export-version`

La versión del archivo Varnish

- Predeterminado: `6`
- Requiere un valor

#### `--grace-period`

Período de gracia en segundos

- Predeterminado: `300`
- Requiere un valor

#### `--input-file`

Archivo de entrada a partir del cual generar vcl

- Requiere un valor

#### `--output-file`

Ruta al archivo a escribir vcl

- Requiere un valor


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Ejecuta un webhook registrado con fines de desarrollo.

### Argumentos

#### `name`

Nombre del webhook

- Obligatorio


#### `payload`

La carga útil del webhook en JSON formato

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Generar plugins basados en registros de webhook

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Devuelve la carga útil del webhook especificado.

### Argumentos

#### `webhook-name`

Nombre del método Webhook

- Obligatorio


#### `webhook-type`

Tipo de Webhook (antes, después)

- Predeterminado: `before`

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.

#### `--depth`

El número de niveles de la carga útil del webhook que se devolverán

- Predeterminado: `3`
- Acepta un valor


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Muestra lista de webhooks suscritos

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Devuelve una lista de nombres de métodos de webhook admitidos para el módulo especificado

### Argumentos

#### `module_name`

Nombre del módulo

- Obligatorio

### Opciones

Para ver las opciones globales, consulte [Opciones](#global-options) globales.
