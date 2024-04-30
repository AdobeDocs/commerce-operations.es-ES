---
source-git-commit: 19d19ef385cf4aaee3a255930af8e6d3b81de23a
workflow-type: tm+mt
source-wordcount: '17795'
ht-degree: 0%

---
# bin/magento (Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versión**: 2.4.7

Esta referencia contiene 116 comandos disponibles a través del `bin/magento` herramienta de línea de comandos.
La lista inicial se genera automáticamente utilizando `bin/magento list` comando en el Magento Open Source.
Utilice el [&quot;Agregar comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) para agregar un comando de CLI personalizado.

>[!NOTE]
>
>Puede llamar a `bin/magento` Comandos CLI que utilizan métodos abreviados en lugar del nombre de comando completo. Por ejemplo, puede llamar a `bin/magento setup:upgrade` usando `bin/magento s:up`, `bin/magento s:upg`. Consulte [sintaxis de acceso directo](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) para comprender cómo utilizar accesos directos con cualquier comando CLI.

>[!NOTE]
>
>Esta referencia se genera a partir del código base de la aplicación. Para cambiar el contenido, puede actualizar el código fuente para la implementación del comando correspondiente en la [código base](https://github.com/magento) y envíe los cambios para que se revisen. Otra forma es _Danos tu opinión_ (busque el vínculo en la parte superior derecha). Para ver las directrices de contribución, consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Comando interno para proporcionar sugerencias de finalización de shell


### `--shell`, `-s`

El tipo de contenedor (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Requiere un valor

### `--input`, `-i`

Una matriz de tokens de entrada (por ejemplo, COMP_WORDS o argv)

- Predeterminado: `[]`
- Requiere un valor

### `--current`, `-c`

Índice de la matriz de &quot;entrada&quot; en la que se encuentra el cursor (p. ej. COMP_CWORD)

- Requiere un valor

### `--api-version`, `-a`

Versión de API del script de finalización

- Requiere un valor

### `--symfony`, `-S`

obsoleto

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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

```bash
bin/magento completion [--debug] [--] [<shell>]
```

Volcar el script de finalización de shell


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


### `shell`

El tipo de shell (p. ej. &quot;bash&quot;), el valor de la variable env &quot;$SHELL&quot; se usará si no se proporciona


### `--debug`

Seguimiento del registro de depuración de finalización

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Comandos de lista


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Deshabilitar el módulo Adobe IMS


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Habilite el módulo Adobe IMS.


### `--organization-id`, `-o`

Establezca el ID de organización para la configuración de Adobe IMS. Necesario al habilitar el módulo

- Acepta un valor

### `--client-id`, `-c`

Establezca el ID de cliente para la configuración de Adobe IMS. Necesario al habilitar el módulo

- Acepta un valor

### `--client-secret`, `-s`

Establezca el Secreto del cliente para la configuración de Adobe IMS. Necesario al habilitar el módulo

- Acepta un valor

### `--2fa`, `-t`

Compruebe si 2FA está habilitado para la organización en Adobe Admin Console. Necesario al habilitar el módulo

- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Información sobre la configuración del módulo Adobe IMS


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Estado del módulo Adobe IMS


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crea un administrador


### `--admin-user`

(Obligatorio) Usuario administrador

- Requiere un valor

### `--admin-password`

(Obligatorio) Contraseña de administrador

- Requiere un valor

### `--admin-email`

(Obligatorio) Correo electrónico del administrador

- Requiere un valor

### `--admin-firstname`

(Obligatorio) Nombre del administrador

- Requiere un valor

### `--admin-lastname`

(Obligatorio) Apellido del administrador

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


### `username`

El nombre de usuario del administrador que desbloquear

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Crear volcado de aplicación



### `config-types`

Lista separada por espacios de los tipos de configuración u omitir para volcar todo [ámbitos, sistema, temas, i18n]

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `app:config:import`

```bash
bin/magento app:config:import
```

Importación de datos de archivos de configuración compartidos al almacenamiento de datos adecuado


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `app:config:status`

```bash
bin/magento app:config:status
```

Comprueba si la propagación de la configuración requiere actualización


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Migración de tarjetas almacenadas desde una base de datos de Magento 1


### `--host`

Nombre de host/IP. El puerto es opcional

- Requiere un valor

### `--dbname`

Nombre de base

- Requiere un valor

### `--username`

Nombre de usuario de base de datos Debe tener acceso de lectura

- Requiere un valor

### `--password`

Contraseña

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Limpia los tipos de caché



### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Deshabilita los tipos de caché



### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Habilita los tipos de caché



### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Vacía el almacenamiento de caché utilizado por los tipos de caché



### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Comprueba el estado de caché


### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Crea imágenes de productos redimensionadas


### `--async`, `-a`

Cambiar el tamaño de la imagen en modo asincrónico

- Predeterminado: `false`
- No acepta un valor

### `--skip_hidden_images`

No procesar imágenes marcadas como ocultas en la página del producto

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Elimina los atributos del producto no utilizados.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Establezca si desea aplicar la validación de contenido del HTML de usuario o mostrar una advertencia en su lugar



### `restrict`

y\n

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Establecer valores de configuración confidenciales



### `path`

Ruta de configuración, por ejemplo, group/section/field_name


### `value`

Valor de configuración


### `--interactive`, `-i`

Habilite el modo interactivo para establecer todas las variables confidenciales

- Predeterminado: `false`
- No acepta un valor

### `--scope`

Ámbito para la configuración; si no se establece, utilice &#39;predeterminado&#39;

- Predeterminado: `default`
- Acepta un valor

### `--scope-code`

Código de ámbito de la configuración, cadena vacía de forma predeterminada

- Predeterminado: &quot;
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Cambiar configuración del sistema



### `path`

Ruta de configuración en formato sección/grupo/nombre_campo

- Requerido

### `value`

Valor de configuración

- Requerido

### `--scope`

Ámbito de configuración (predeterminado, sitio web o tienda)

- Predeterminado: `default`
- Requiere un valor

### `--scope-code`

Código de ámbito (requerido solo si el ámbito no es &quot;predeterminado&quot;)

- Requiere un valor

### `--lock-env`, `-e`

Valor de bloqueo que impide la modificación en el administrador (se guardará en app/etc/env.php)

- Predeterminado: `false`
- No acepta un valor

### `--lock-config`, `-c`

Bloquear y compartir valor con otras instalaciones, evita la modificación en el Administrador (se guardará en app/etc/config.php)

- Predeterminado: `false`
- No acepta un valor

### `--lock`, `-l`

En desuso, utilice la opción —lock-env en su lugar.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Muestra el valor de configuración de una ruta determinada. Si no se especifica la ruta, se mostrarán todos los valores guardados



### `path`

Ruta de configuración, por ejemplo section_id/group_id/field_id


### `--scope`

Ámbito para la configuración; si no se especifica, se utilizará el ámbito predeterminado

- Predeterminado: `default`
- Acepta un valor

### `--scope-code`

Código de ámbito (requerido solo si el ámbito no es `default`)

- Predeterminado: &quot;
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Genera e instala crontab para el usuario actual


### `--force`, `-f`

Forzar tareas de instalación

- Predeterminado: `false`
- No acepta un valor

### `--non-optional`, `-d`

Instalar solo las tareas no opcionales (predeterminadas)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cron:remove`

```bash
bin/magento cron:remove
```

Quita tareas de crontab


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Ejecuta trabajos por programación


### `--group`

Ejecutar trabajos solo desde el grupo especificado

- Requiere un valor

### `--exclude-group`

Excluir trabajos del grupo especificado

- Predeterminado: `[]`
- Acepta varios valores

### `--bootstrap`

Agregar o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

Actualizar el hash del cliente según el algoritmo más reciente


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Establezca el modo de aplicación.



### `mode`

El modo de aplicación que se va a establecer. Las opciones disponibles son &quot;desarrollador&quot; o &quot;producción&quot;

- Requerido

### `--skip-compilation`, `-s`

Omite la eliminación y regeneración del contenido estático (código generado, CSS preprocesado y recursos en pub/static/s)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Muestra el modo de aplicación actual.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:di:info`

```bash
bin/magento dev:di:info <class>
```

Proporciona información sobre la configuración de la inyección de dependencias para el comando.



### `class`

Nombre de clase

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Analiza las plantillas de newsletter por posibles problemas de compatibilidad de uso de variables


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Analiza las anulaciones de plantillas de correo electrónico para detectar posibles problemas de compatibilidad de uso de variables


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Deshabilite el generador de perfiles.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

Habilite el generador de perfiles.



### `type`

Tipo de generador de perfiles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Deshabilitar registro de consultas DB


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Habilitar registro de consultas DB


### `--include-all-queries`

Registra todas las consultas. [true\|false]

- Predeterminado: `true`
- Acepta un valor

### `--query-time-threshold`

Umbrales de tiempo de consulta.

- Predeterminado: `0.001`
- Acepta un valor

### `--include-call-stack`

Incluir pila de llamadas. [true\|false]

- Predeterminado: `true`
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Recopila y publica archivos de origen para temas.



### `file`

Archivos para preprocesar (el archivo debe especificarse sin extensión)

- Predeterminado: `css/styles-mcss/styles-l`

- Matriz

### `--type`

Tipo de archivos de origen: [menos]

- Predeterminado: `less`
- Requiere un valor

### `--locale`

Configuración regional: [en_US]

- Predeterminado: `en_US`
- Requiere un valor

### `--area`

Área: [frontend\|adminhtml]

- Predeterminado: `frontend`
- Requiere un valor

### `--theme`

Tema: [Proveedor/tema]

- Predeterminado: `Magento/luma`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Deshabilite las sugerencias de plantilla de front-end. Puede ser necesario vaciar la caché.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Habilitar sugerencias de plantilla de front-end. Puede ser necesario vaciar la caché.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Mostrar estado de sugerencias de plantilla de front-end.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Ejecuta pruebas



### `type`

Tipo de prueba que se va a ejecutar. Tipos disponibles: todos, unidad, integración, integration-all, estático, static-all, integridad, heredado, predeterminado

- Predeterminado: `default`


### `--arguments`, `-c`

Argumentos adicionales para PHPUnit. Ejemplo: &quot;-c&#39;—filter=MyTest&#39;&quot; (sin espacios)

- Predeterminado: &quot;
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Genera el catálogo de URN a asignaciones *.xsd para que el IDE resalte el xml.



### `path`

Ruta al archivo para generar el catálogo. Para PhpStorm utilice .idea/misc.xml

- Requerido

### `--ide`

Formato en el que se generará el catálogo. Admitido: [phpstorm, vscode]

- Predeterminado: `phpstorm`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Convierte el archivo XML utilizando hojas de estilos XSL



### `xml-file`

Ruta al archivo XML que se va a transformar

- Requerido

### `processor`

Ruta a la hoja de estilos XSL que se aplicará al archivo XML

- Requerido

### `--overwrite`, `-o`

Sobrescribir archivo XML

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Añadir dominios a la lista blanca de dominios descargables



### `domains`

Nombre de dominios

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Eliminar dominios de la lista blanca de dominios descargables



### `domains`

Nombres de dominio

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Mostrar la lista blanca de dominios descargables


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Vuelve a cifrar los datos cifrados de la tarjeta de crédito con el último cifrado.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Descubre frases en la base de código



### `directory`

Ruta de directorio para analizar. No es necesario si —magento está establecido


### `--output`, `-o`

Ruta (incluido el nombre del archivo) a un archivo de salida. Sin especificar ningún archivo, el valor predeterminado es stdout.

- Requiere un valor

### `--magento`, `-m`

Utilice el parámetro —magento para analizar el código base del Magento actual. Omita el parámetro si se especifica un directorio.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Guarda el paquete de idioma



### `source`

Ruta al archivo del diccionario de origen con traducciones

- Requerido

### `locale`

Configuración regional de destino para el diccionario, por ejemplo &quot;de_DE&quot;

- Requerido

### `--mode`, `-m`

Modo de guardado para el diccionario - &quot;replace&quot; - reemplazar paquete de idioma por uno nuevo - &quot;merge&quot; - fusionar paquetes de idioma, de forma predeterminada &quot;replace&quot;

- Predeterminado: `replace`
- Requiere un valor

### `--allow-duplicates`, `-d`

Utilice el parámetro —allow-duplicates para permitir el guardado de duplicados de la traducción. De lo contrario, omita el parámetro.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Desinstala paquetes de idioma



### `package`

Nombre del paquete de idioma

- Predeterminado: `[]`

- Requerido
- Matriz

### `--backup-code`, `-b`

Realizar copia de seguridad de archivos de código y configuración (excepto archivos temporales)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:info`

```bash
bin/magento indexer:info
```

Muestra indizadores permitidos


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Reindexe datos



### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Restablece el estado del indexador a no válido



### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Establecer modo de Dimension de indizador



### `indexer`

Nombre del indexador [catalog_product_price]


### `mode`

Modos de dimensión de indizador catalog_product_price none,sitio web,customer_group,sitio_web_and_customer_group


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Establece el tipo de modo de índice



### `mode`

Tipo de modo de indizador [tiempo real|programación]


### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Establece el estado del indizador especificado



### `status`

Tipo de estado del indexador [no válido|suspendido|válido]

- Requerido

### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Muestra el modo de Dimension del indizador



### `indexer`

Lista separada por espacios de los tipos de índice u omitir para aplicar a todos los índices (catalog_product_price)

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Muestra el modo de índice



### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Muestra el estado del indizador



### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Muestra el URI de administración del Magento


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Imprime una lista de los archivos de copia de seguridad disponibles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Muestra la lista de divisas disponibles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Muestra el número de dependencias del marco de trabajo del Magento


### `--output`, `-o`

Nombre del informe

- Predeterminado: `framework-dependencies.csv`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Muestra el número de dependencias entre módulos


### `--output`, `-o`

Nombre del informe

- Predeterminado: `modules-dependencies.csv`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Muestra el número de dependencias circulares entre módulos


### `--output`, `-o`

Nombre del informe

- Predeterminado: `modules-circular-dependencies.csv`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:language:list`

```bash
bin/magento info:language:list
```

Muestra la lista de configuraciones regionales de idioma disponibles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Muestra la lista de husos horarios disponibles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Crear reservas con argumentos de compensación proporcionados



### `compensations`

Lista de argumentos de compensación en formato &quot;:::&quot;

- Predeterminado: `[]`

- Matriz

### `--raw`, `-r`

Salida en bruto

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Mostrar todos los pedidos y productos con incoherencias de cantidad vendible


### `--complete-orders`, `-c`

Mostrar sólo incoherencias para pedidos completos

- Predeterminado: `false`
- No acepta un valor

### `--incomplete-orders`, `-i`

Mostrar sólo incoherencias para pedidos incompletos

- Predeterminado: `false`
- No acepta un valor

### `--bunch-size`, `-b`

Define cuántos pedidos se cargarán a la vez

- Predeterminado: `50`
- Acepta un valor

### `--raw`, `-r`

Salida en bruto

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Descargar e importar nombres geográficos para el algoritmo de selección de origen



### `countries`

Lista de códigos de país para importar

- Predeterminado: `[]`

- Requerido
- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Establece IP exentas del modo de mantenimiento



### `ip`

Direcciones IP permitidas

- Predeterminado: `[]`

- Matriz

### `--none`

Borrar direcciones IP permitidas

- Predeterminado: `false`
- No acepta un valor

### `--add`

Añadir la dirección IP a la lista existente

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Desactiva el modo de mantenimiento


### `--ip`

Direcciones IP permitidas (utilice &quot;ninguno&quot; para borrar la lista de direcciones IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Activa el modo de mantenimiento


### `--ip`

Direcciones IP permitidas (utilice &quot;ninguno&quot; para borrar la lista de direcciones IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Muestra el estado del modo de mantenimiento


### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Sincronización de contenido con recursos


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Sincronizar el almacenamiento y los recursos de medios en la base de datos


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `module:config:status`

```bash
bin/magento module:config:status
```

Comprueba la configuración de módulos en el archivo &#39;app/etc/config.php&#39; e informa si están actualizados o no


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Deshabilita los módulos especificados



### `module`

Nombre del módulo

- Predeterminado: `[]`

- Matriz

### `--force`, `-f`

Omitir comprobación de dependencias

- Predeterminado: `false`
- No acepta un valor

### `--all`

Deshabilitar todos los módulos

- Predeterminado: `false`
- No acepta un valor

### `--clear-static-content`, `-c`

Borrar archivos de vista estática generados. Necesario, si los módulos tienen archivos de vista estática

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Habilita módulos especificados



### `module`

Nombre del módulo

- Predeterminado: `[]`

- Matriz

### `--force`, `-f`

Omitir comprobación de dependencias

- Predeterminado: `false`
- No acepta un valor

### `--all`

Habilitar todos los módulos

- Predeterminado: `false`
- No acepta un valor

### `--clear-static-content`, `-c`

Borrar archivos de vista estática generados. Necesario, si los módulos tienen archivos de vista estática

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Muestra el estado de los módulos



### `module-names`

Nombre de módulo opcional

- Predeterminado: `[]`

- Matriz

### `--enabled`

Imprimir solo los módulos habilitados

- Predeterminado: `false`
- No acepta un valor

### `--disabled`

Imprimir solo los módulos desactivados

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Desinstala los módulos instalados por composer



### `module`

Nombre del módulo

- Predeterminado: `[]`

- Requerido
- Matriz

### `--remove-data`, `-r`

Eliminar datos instalados por los módulos

- Predeterminado: `false`
- No acepta un valor

### `--backup-code`

Realizar copia de seguridad de archivos de código y configuración (excepto archivos temporales)

- Predeterminado: `false`
- No acepta un valor

### `--backup-media`

Realizar copia de seguridad de medios

- Predeterminado: `false`
- No acepta un valor

### `--backup-db`

Realizar copia de seguridad completa de base de datos

- Predeterminado: `false`
- No acepta un valor

### `--non-composer`

Todos los módulos que pasarán aquí no estarán basados en compositores

- Predeterminado: `false`
- No acepta un valor

### `--clear-static-content`, `-c`

Borrar archivos de vista estática generados. Necesario, si los módulos tienen archivos de vista estática

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Compruebe las entradas de la cola de implementación y cree un marcador de implementación adecuado.



### `message`

¿Implementar mensaje?

- Requerido

### `change_log`

¿Cambiar registro?

- Requerido

### `user`

Usuario de implementación


### `revision`

Revisión


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Lista de consumidores de MessageQueue


```
This command shows list of MessageQueue consumers.
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Reiniciar consumidores de MessageQueue


```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

Iniciar consumidor de MessageQueue


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


### `consumer`

Nombre del consumidor que se va a iniciar.

- Requerido

### `--max-messages`

El número de mensajes que debe procesar el consumidor antes de la finalización del proceso. Si no se especifica, finalice después de procesar todos los mensajes en cola.

- Requiere un valor

### `--batch-size`

Número de mensajes por lote. Aplicable únicamente para el consumidor de lotes.

- Requiere un valor

### `--area-code`

El área preferida (global, adminhtml, etc.) por defecto es global.

- Requiere un valor

### `--single-thread`

Esta opción evita la ejecución simultánea de varias copias de un consumidor.

- Predeterminado: `false`
- No acepta un valor

### `--multi-process`

Número de procesos por consumidor.

- Acepta un valor

### `--pid-file-path`

Ruta de archivo para guardar el PID (esta opción está obsoleta; utilice —single-thread en su lugar)

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Sincronizar archivos multimedia con almacenamiento remoto.


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync]
```

Vuelve a sincronizar los datos de fuente con el servicio SaaS.


### `--feed`

Nombre de la fuente para volver a sincronizar completamente con el servicio SaaS. Fuentes disponibles: Producción de pedidos de servicios de pago, Zona protegida de pedidos de servicios de pago, Producción de estado de pedidos de servicios de pago, Zona protegida de estado de pedidos de servicios de pago, Producción de tiendas de servicios de pago, Zona protegida de tiendas de servicios de pago

- Requiere un valor

### `--no-reindex`

Ejecute la nueva presentación de los datos de la fuente solo al servicio SaaS. No vuelve a indexar. (Esta opción no es aplicable a los productos, anulaciones de productos, precios y fuentes)

- Predeterminado: `false`
- No acepta un valor

### `--cleanup-feed`

Forzar la limpieza de la tabla del indexador de fuentes antes de sincronizar.

- Predeterminado: `false`
- No acepta un valor

### `--dry-run`

Corre en seco. Los datos no se exportarán. Para guardar la carga en el archivo de registro var/log/saas-export.log ejecute con la variable env EXPORTER_EXTENDED_LOG=1.

- Predeterminado: `false`
- No acepta un valor

### `--thread-count`

Establezca el recuento de subprocesos de sincronización.

- Requiere un valor

### `--batch-size`

Establecer tamaño del lote de sincronización

- Requiere un valor

### `--continue-resync`

Continuar la sincronización desde la última posición almacenada (esta opción es aplicable a los productos, anulaciones de productos y fuentes de precios)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Implementación de módulos de datos de ejemplo para instalaciones de Magento basadas en compositor


### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Elimine todos los paquetes de datos de ejemplo de composer.json


### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Restablecer todos los módulos de datos de ejemplo para la reinstalación


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

Deshabilitar reCAPTCHA para el usuario administrador olvidó el formulario de contraseña


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

Deshabilitar reCAPTCHA para el formulario de inicio de sesión del usuario administrador


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Establezca el secreto utilizado para la generación OTP de Google.



### `user`

Nombre de usuario

- Requerido

### `secret`

Secreto

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Enumerar todos los proveedores disponibles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Restablecer la configuración de un usuario



### `user`

Nombre de usuario

- Requerido

### `provider`

Código de proveedor

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Realiza una copia de seguridad de la base de código, medios y base de datos de la aplicación Magento


### `--code`

Realizar copia de seguridad de archivos de código y configuración (excepto archivos temporales)

- Predeterminado: `false`
- No acepta un valor

### `--media`

Realizar copia de seguridad de medios

- Predeterminado: `false`
- No acepta un valor

### `--db`

Realizar copia de seguridad completa de base de datos

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:config:set`

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Crea o modifica la configuración de implementación


### `--backend-frontname`

Nombre del front-end (se generará automáticamente si falta)

- Requiere un valor

### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

### `--enable-syslog-logging`

Habilitar registro syslog

- Requiere un valor

### `--remote-storage-driver`

Controlador de almacenamiento remoto

- Requiere un valor

### `--remote-storage-prefix`

Prefijo de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-endpoint`

Extremo de almacenamiento remoto

- Requiere un valor

### `--remote-storage-bucket`

Bloque de almacenamiento remoto

- Requiere un valor

### `--remote-storage-region`

Región de almacenamiento remoto

- Requiere un valor

### `--remote-storage-key`

Clave de acceso de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-secret`

Clave secreta de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-path-style`

Estilo de ruta de almacenamiento remoto

- Predeterminado: `0`
- Requiere un valor

### `--id_salt`

Sal de GraphQl

- Requiere un valor

### `--config-async`

¿Habilitar Guardar configuración de administración asincrónica? 1 - Sí, 0 - No

- Requiere un valor

### `--amqp-host`

Host del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-port`

Puerto del servidor Amqp

- Predeterminado: `5672`
- Requiere un valor

### `--amqp-user`

Nombre de usuario del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-password`

Contraseña del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-virtualhost`

Amqp virtualhost

- Predeterminado: `/`
- Requiere un valor

### `--amqp-ssl`

Amqp SSL

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-ssl-options`

Opciones SSL de Amqp (JSON)

- Predeterminado: &quot;
- Requiere un valor

### `--consumers-wait-for-messages`

¿Deben los consumidores esperar un mensaje de la cola? 1 - Sí, 0 - No

- Requiere un valor

### `--queue-default-connection`

Conexión predeterminada de colas de mensajes. Puede ser &quot;db&quot;, &quot;amqp&quot; o un sistema de colas personalizado. El sistema de colas debe estar instalado y configurado; de lo contrario, los mensajes no se procesarán correctamente.

- Requiere un valor

### `--key`

Clave de cifrado

- Requiere un valor

### `--db-host`

Host del servidor de base de datos

- Requiere un valor

### `--db-name`

Nombre de base

- Requiere un valor

### `--db-user`

Nombre de usuario del servidor

- Requiere un valor

### `--db-engine`

Motor de servidor de base de datos

- Requiere un valor

### `--db-password`

Contraseña del servidor de base de datos

- Requiere un valor

### `--db-prefix`

Prefijo de tabla de base

- Requiere un valor

### `--db-model`

Tipo de base de datos

- Requiere un valor

### `--db-init-statements`

Conjunto inicial de comandos de la base de datos

- Requiere un valor

### `--skip-db-validation`, `-s`

Si se especifica, se omitirá la validación de la conexión de base de datos

- Predeterminado: `false`
- No acepta un valor

### `--http-cache-hosts`

hosts de caché http

- Requiere un valor

### `--db-ssl-key`

Ruta de acceso completa del archivo de clave de cliente para establecer una conexión de base de datos mediante SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-cert`

Ruta de acceso completa del archivo de certificado de cliente para establecer una conexión de base de datos mediante SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-ca`

Ruta de acceso completa del archivo de certificado del servidor para establecer una conexión de base de datos mediante SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-verify`

Verificar certificación del servidor

- Predeterminado: `false`
- No acepta un valor

### `--session-save`

Controlador de guardado de sesión

- Requiere un valor

### `--session-save-redis-host`

Nombre de host completo, dirección IP o ruta absoluta si se utilizan sockets UNIX

- Requiere un valor

### `--session-save-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--session-save-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--session-save-redis-timeout`

Tiempo de espera de conexión, en segundos

- Requiere un valor

### `--session-save-redis-persistent-id`

Cadena única para habilitar conexiones persistentes

- Requiere un valor

### `--session-save-redis-db`

Número de base de datos Redis

- Requiere un valor

### `--session-save-redis-compression-threshold`

Umbral de compresión de Redis

- Requiere un valor

### `--session-save-redis-compression-lib`

Biblioteca de compresión de Redis. Valores: gzip (predeterminado), lzf, lz4, snappy

- Requiere un valor

### `--session-save-redis-log-level`

Nivel de registro de Redis. Valores: 0 (menos detallado) a 7 (más detallado)

- Requiere un valor

### `--session-save-redis-max-concurrency`

Número máximo de procesos que pueden esperar un bloqueo en una sesión

- Requiere un valor

### `--session-save-redis-break-after-frontend`

Número de segundos de espera antes de intentar romper un bloqueo para la sesión de front-end

- Requiere un valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos de espera antes de intentar romper un bloqueo para la sesión de administrador

- Requiere un valor

### `--session-save-redis-first-lifetime`

Duración, en segundos, de la sesión para los no bots en la primera escritura (utilice 0 para desactivar)

- Requiere un valor

### `--session-save-redis-bot-first-lifetime`

Duración, en segundos, de la sesión para bots en la primera escritura (utilice 0 para desactivar)

- Requiere un valor

### `--session-save-redis-bot-lifetime`

Duración de la sesión para bots en escrituras posteriores (utilice 0 para deshabilitarla)

- Requiere un valor

### `--session-save-redis-disable-locking`

Redis desactiva el bloqueo. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-min-lifetime`

Duración mínima de la sesión de Redis, en segundos

- Requiere un valor

### `--session-save-redis-max-lifetime`

Duración máxima de la sesión de Redis, en segundos

- Requiere un valor

### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Requiere un valor

### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por comas

- Requiere un valor

### `--session-save-redis-sentinel-verify-master`

Redis Centinela verificar maestro. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conecta reintentos.

- Requiere un valor

### `--cache-backend`

Controlador de caché predeterminado

- Requiere un valor

### `--cache-backend-redis-server`

Servidor Redis

- Requiere un valor

### `--cache-backend-redis-db`

Número de base de datos de la caché

- Requiere un valor

### `--cache-backend-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--cache-backend-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--cache-backend-redis-compress-data`

Establezca el valor en 0 para deshabilitar la compresión (el valor predeterminado es 1, habilitado)

- Requiere un valor

### `--cache-backend-redis-compression-lib`

Libreta de compresión para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

### `--cache-backend-redis-use-lua`

Establezca el valor en 1 para habilitar lua (el valor predeterminado es 0, deshabilitado)

- Requiere un valor

### `--cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--allow-parallel-generation`

Permitir generar caché de forma no bloqueante

- Predeterminado: `false`
- No acepta un valor

### `--page-cache`

Controlador de caché predeterminado

- Requiere un valor

### `--page-cache-redis-server`

Servidor Redis

- Requiere un valor

### `--page-cache-redis-db`

Número de base de datos de la caché

- Requiere un valor

### `--page-cache-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--page-cache-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--page-cache-redis-compress-data`

Establezca el valor en 1 para comprimir la memoria caché de toda la página (utilice 0 para desactivarla)

- Requiere un valor

### `--page-cache-redis-compression-lib`

Biblioteca de compresión para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

### `--page-cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--lock-provider`

Bloquear nombre de proveedor

- Requiere un valor

### `--lock-db-prefix`

Prefijo de bloqueo específico de la instalación para evitar conflictos de bloqueo

- Requiere un valor

### `--lock-zookeeper-host`

Host y puerto para conectarse al clúster de Zookeeper. Por ejemplo: 127.0.0.1:2181

- Requiere un valor

### `--lock-zookeeper-path`

El camino donde Zookeeper guardará las cerraduras. La ruta predeterminada es: /magento/locks.

- Requiere un valor

### `--lock-file-path`

La ruta en la que se guardarán los bloqueos de archivo.

- Requiere un valor

### `--document-root-is-pub`

El indicador que se mostrará es Pub está en la raíz, solo puede ser verdadero o falso

- Requiere un valor

### `--backpressure-logger`

Controlador de registrador de contrapresión

- Requiere un valor

### `--backpressure-logger-redis-server`

Servidor Redis

- Requiere un valor

### `--backpressure-logger-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--backpressure-logger-redis-timeout`

Tiempo de espera del servidor Redis

- Requiere un valor

### `--backpressure-logger-redis-persistent`

Redis persistente

- Requiere un valor

### `--backpressure-logger-redis-db`

Número de base de datos Redis

- Requiere un valor

### `--backpressure-logger-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--backpressure-logger-redis-user`

Usuario del servidor Redis

- Requiere un valor

### `--backpressure-logger-id-prefix`

Prefijo de ID para claves

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala y actualiza datos en la base de datos


### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Genere el parche y colóquelo en una carpeta específica.



### `module`

Nombre de módulo

- Requerido

### `patch`

Nombre del parche

- Requerido

### `--revertable`

Compruebe si el parche es reversible o no.

- Predeterminado: `false`
- Acepta un valor

### `--type`

Averigüe qué tipo de parche se debe generar. Valores disponibles: `data`, `schema`.

- Predeterminado: `data`
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Genere una lista blanca de tablas y columnas que el instalador de declaraciones pueda editar


### `--module-name`

Nombre del módulo donde se generará la lista de admitidos

- Predeterminado: `all`
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala y actualiza el esquema de la base de datos


### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) al formato db_schema.xml.

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Comprueba si los datos o el esquema de la base de datos requieren actualización


### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Genera la configuración de ID y todas las clases que faltan que pueden generarse automáticamente


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:install`

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala la aplicación Magento


### `--backend-frontname`

Nombre del front-end (se generará automáticamente si falta)

- Requiere un valor

### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

### `--enable-syslog-logging`

Habilitar registro syslog

- Requiere un valor

### `--remote-storage-driver`

Controlador de almacenamiento remoto

- Requiere un valor

### `--remote-storage-prefix`

Prefijo de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-endpoint`

Extremo de almacenamiento remoto

- Requiere un valor

### `--remote-storage-bucket`

Bloque de almacenamiento remoto

- Requiere un valor

### `--remote-storage-region`

Región de almacenamiento remoto

- Requiere un valor

### `--remote-storage-key`

Clave de acceso de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-secret`

Clave secreta de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-path-style`

Estilo de ruta de almacenamiento remoto

- Predeterminado: `0`
- Requiere un valor

### `--id_salt`

Sal de GraphQl

- Requiere un valor

### `--config-async`

¿Habilitar Guardar configuración de administración asincrónica? 1 - Sí, 0 - No

- Requiere un valor

### `--amqp-host`

Host del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-port`

Puerto del servidor Amqp

- Predeterminado: `5672`
- Requiere un valor

### `--amqp-user`

Nombre de usuario del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-password`

Contraseña del servidor Amqp

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-virtualhost`

Amqp virtualhost

- Predeterminado: `/`
- Requiere un valor

### `--amqp-ssl`

Amqp SSL

- Predeterminado: &quot;
- Requiere un valor

### `--amqp-ssl-options`

Opciones SSL de Amqp (JSON)

- Predeterminado: &quot;
- Requiere un valor

### `--consumers-wait-for-messages`

¿Deben los consumidores esperar un mensaje de la cola? 1 - Sí, 0 - No

- Requiere un valor

### `--queue-default-connection`

Conexión predeterminada de colas de mensajes. Puede ser &quot;db&quot;, &quot;amqp&quot; o un sistema de colas personalizado. El sistema de colas debe estar instalado y configurado; de lo contrario, los mensajes no se procesarán correctamente.

- Requiere un valor

### `--key`

Clave de cifrado

- Requiere un valor

### `--db-host`

Host del servidor de base de datos

- Requiere un valor

### `--db-name`

Nombre de base

- Requiere un valor

### `--db-user`

Nombre de usuario del servidor

- Requiere un valor

### `--db-engine`

Motor de servidor de base de datos

- Requiere un valor

### `--db-password`

Contraseña del servidor de base de datos

- Requiere un valor

### `--db-prefix`

Prefijo de tabla de base

- Requiere un valor

### `--db-model`

Tipo de base de datos

- Requiere un valor

### `--db-init-statements`

Conjunto inicial de comandos de la base de datos

- Requiere un valor

### `--skip-db-validation`, `-s`

Si se especifica, se omitirá la validación de la conexión de base de datos

- Predeterminado: `false`
- No acepta un valor

### `--http-cache-hosts`

hosts de caché http

- Requiere un valor

### `--db-ssl-key`

Ruta de acceso completa del archivo de clave de cliente para establecer una conexión de base de datos mediante SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-cert`

Ruta de acceso completa del archivo de certificado de cliente para establecer una conexión de base de datos mediante SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-ca`

Ruta de acceso completa del archivo de certificado del servidor para establecer una conexión de base de datos mediante SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-verify`

Verificar certificación del servidor

- Predeterminado: `false`
- No acepta un valor

### `--session-save`

Controlador de guardado de sesión

- Requiere un valor

### `--session-save-redis-host`

Nombre de host completo, dirección IP o ruta absoluta si se utilizan sockets UNIX

- Requiere un valor

### `--session-save-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--session-save-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--session-save-redis-timeout`

Tiempo de espera de conexión, en segundos

- Requiere un valor

### `--session-save-redis-persistent-id`

Cadena única para habilitar conexiones persistentes

- Requiere un valor

### `--session-save-redis-db`

Número de base de datos Redis

- Requiere un valor

### `--session-save-redis-compression-threshold`

Umbral de compresión de Redis

- Requiere un valor

### `--session-save-redis-compression-lib`

Biblioteca de compresión de Redis. Valores: gzip (predeterminado), lzf, lz4, snappy

- Requiere un valor

### `--session-save-redis-log-level`

Nivel de registro de Redis. Valores: 0 (menos detallado) a 7 (más detallado)

- Requiere un valor

### `--session-save-redis-max-concurrency`

Número máximo de procesos que pueden esperar un bloqueo en una sesión

- Requiere un valor

### `--session-save-redis-break-after-frontend`

Número de segundos de espera antes de intentar romper un bloqueo para la sesión de front-end

- Requiere un valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos de espera antes de intentar romper un bloqueo para la sesión de administrador

- Requiere un valor

### `--session-save-redis-first-lifetime`

Duración, en segundos, de la sesión para los no bots en la primera escritura (utilice 0 para desactivar)

- Requiere un valor

### `--session-save-redis-bot-first-lifetime`

Duración, en segundos, de la sesión para bots en la primera escritura (utilice 0 para desactivar)

- Requiere un valor

### `--session-save-redis-bot-lifetime`

Duración de la sesión para bots en escrituras posteriores (utilice 0 para deshabilitarla)

- Requiere un valor

### `--session-save-redis-disable-locking`

Redis desactiva el bloqueo. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-min-lifetime`

Duración mínima de la sesión de Redis, en segundos

- Requiere un valor

### `--session-save-redis-max-lifetime`

Duración máxima de la sesión de Redis, en segundos

- Requiere un valor

### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Requiere un valor

### `--session-save-redis-sentinel-servers`

Servidores Redis Sentinel, separados por comas

- Requiere un valor

### `--session-save-redis-sentinel-verify-master`

Redis Centinela verificar maestro. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conecta reintentos.

- Requiere un valor

### `--cache-backend`

Controlador de caché predeterminado

- Requiere un valor

### `--cache-backend-redis-server`

Servidor Redis

- Requiere un valor

### `--cache-backend-redis-db`

Número de base de datos de la caché

- Requiere un valor

### `--cache-backend-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--cache-backend-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--cache-backend-redis-compress-data`

Establezca el valor en 0 para deshabilitar la compresión (el valor predeterminado es 1, habilitado)

- Requiere un valor

### `--cache-backend-redis-compression-lib`

Libreta de compresión para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

### `--cache-backend-redis-use-lua`

Establezca el valor en 1 para habilitar lua (el valor predeterminado es 0, deshabilitado)

- Requiere un valor

### `--cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--allow-parallel-generation`

Permitir generar caché de forma no bloqueante

- Predeterminado: `false`
- No acepta un valor

### `--page-cache`

Controlador de caché predeterminado

- Requiere un valor

### `--page-cache-redis-server`

Servidor Redis

- Requiere un valor

### `--page-cache-redis-db`

Número de base de datos de la caché

- Requiere un valor

### `--page-cache-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--page-cache-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--page-cache-redis-compress-data`

Establezca el valor en 1 para comprimir la memoria caché de toda la página (utilice 0 para desactivarla)

- Requiere un valor

### `--page-cache-redis-compression-lib`

Biblioteca de compresión para usar [snappy,lzf,l4z,zstd,gzip] (dejar en blanco para determinar automáticamente)

- Requiere un valor

### `--page-cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--lock-provider`

Bloquear nombre de proveedor

- Requiere un valor

### `--lock-db-prefix`

Prefijo de bloqueo específico de la instalación para evitar conflictos de bloqueo

- Requiere un valor

### `--lock-zookeeper-host`

Host y puerto para conectarse al clúster de Zookeeper. Por ejemplo: 127.0.0.1:2181

- Requiere un valor

### `--lock-zookeeper-path`

El camino donde Zookeeper guardará las cerraduras. La ruta predeterminada es: /magento/locks.

- Requiere un valor

### `--lock-file-path`

La ruta en la que se guardarán los bloqueos de archivo.

- Requiere un valor

### `--document-root-is-pub`

El indicador que se mostrará es Pub está en la raíz, solo puede ser verdadero o falso

- Requiere un valor

### `--backpressure-logger`

Controlador de registrador de contrapresión

- Requiere un valor

### `--backpressure-logger-redis-server`

Servidor Redis

- Requiere un valor

### `--backpressure-logger-redis-port`

Puerto de escucha del servidor Redis

- Requiere un valor

### `--backpressure-logger-redis-timeout`

Tiempo de espera del servidor Redis

- Requiere un valor

### `--backpressure-logger-redis-persistent`

Redis persistente

- Requiere un valor

### `--backpressure-logger-redis-db`

Número de base de datos Redis

- Requiere un valor

### `--backpressure-logger-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--backpressure-logger-redis-user`

Usuario del servidor Redis

- Requiere un valor

### `--backpressure-logger-id-prefix`

Prefijo de ID para claves

- Requiere un valor

### `--base-url`

La URL de la tienda debería estar disponible en. Obsoleto, usar config:set con ruta web/unsecure/base_url

- Requiere un valor

### `--language`

Código de idioma predeterminado. Obsoleto, use config:set con path general/locale/code

- Requiere un valor

### `--timezone`

Código de zona horaria predeterminado. Obsoleto, usar config:set con path general/locale/timezone

- Requiere un valor

### `--currency`

Código de moneda predeterminado. Obsoleto, usar config:set con la ruta currency/options/base, currency/options/default y currency/options/allow

- Requiere un valor

### `--use-rewrites`

Utilice las reescrituras. Obsoleto, use config:set con la ruta web/seo/use_rewrites

- Requiere un valor

### `--use-secure`

Utilice direcciones URL seguras. Active esta opción solo si SSL está disponible. Obsoleto, usar config:set con ruta web/secure/use_in_frontend

- Requiere un valor

### `--base-url-secure`

Dirección URL base para la conexión SSL. Obsoleto, usar config:set con ruta web/secure/base_url

- Requiere un valor

### `--use-secure-admin`

Ejecute la interfaz de administración con SSL. Obsoleto, usar config:set con ruta web/secure/use_in_adminhtml

- Requiere un valor

### `--admin-use-security-key`

Si se utiliza la función &quot;clave de seguridad&quot; en los formularios y las URL de administración de Magento. Obsoleto, usar config:set con path admin/security/use_form_key

- Requiere un valor

### `--admin-user`

Usuario administrador

- Acepta un valor

### `--admin-password`

Contraseña de administrador

- Acepta un valor

### `--admin-email`

Correo electrónico del administrador

- Acepta un valor

### `--admin-firstname`

Nombre del administrador

- Acepta un valor

### `--admin-lastname`

Apellidos del administrador

- Acepta un valor

### `--search-engine`

Motor de búsqueda. Valores: elasticsearch7, elasticsearch8, opensearch

- Requiere un valor

### `--elasticsearch-host`

Host del servidor del Elasticsearch.

- Requiere un valor

### `--elasticsearch-port`

Puerto del servidor del Elasticsearch.

- Requiere un valor

### `--elasticsearch-enable-auth`

Establezca el valor en 1 para habilitar la autenticación. (el valor predeterminado es 0, desactivado)

- Requiere un valor

### `--elasticsearch-username`

Nombre de usuario del Elasticsearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

### `--elasticsearch-password`

Contraseña del Elasticsearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

### `--elasticsearch-index-prefix`

Prefijo de índice del Elasticsearch.

- Requiere un valor

### `--elasticsearch-timeout`

Tiempo de espera del servidor Elasticsearch.

- Requiere un valor

### `--opensearch-host`

Host del servidor de OpenSearch.

- Requiere un valor

### `--opensearch-port`

Puerto del servidor OpenSearch.

- Requiere un valor

### `--opensearch-enable-auth`

Establezca el valor en 1 para habilitar la autenticación. (el valor predeterminado es 0, desactivado)

- Requiere un valor

### `--opensearch-username`

Usuario de OpenSearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

### `--opensearch-password`

Contraseña de OpenSearch. Solo se aplica si la autenticación HTTP está habilitada

- Requiere un valor

### `--opensearch-index-prefix`

Prefijo de índice de OpenSearch.

- Requiere un valor

### `--opensearch-timeout`

Tiempo de espera del servidor OpenSearch.

- Requiere un valor

### `--cleanup-database`

Limpieza de la base de datos antes de la instalación

- Predeterminado: `false`
- No acepta un valor

### `--sales-order-increment-prefix`

Prefijo de número de pedido de ventas

- Requiere un valor

### `--use-sample-data`

Usar datos de ejemplo

- Predeterminado: `false`
- No acepta un valor

### `--enable-modules`

Lista de nombres de módulos separados por comas. Esto debe incluirse durante la instalación. Parámetro mágico disponible &quot;todo&quot;.

- Acepta un valor

### `--disable-modules`

Lista de nombres de módulos separados por comas. Debe evitarse durante la instalación. Parámetro mágico disponible &quot;todo&quot;.

- Acepta un valor

### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) al formato db_schema.xml.

- Predeterminado: `false`
- Acepta un valor

### `--interactive`, `-i`

Instalación interactiva del Magento

- Predeterminado: `false`
- No acepta un valor

### `--safe-mode`

Instalación segura del Magento con volcados en operaciones destructivas, como la eliminación de columnas

- Acepta un valor

### `--data-restore`

Restauración de datos eliminados de volcados

- Acepta un valor

### `--dry-run`

La instalación del Magento se ejecutará en modo de ejecución en seco

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Genera sujeciones



### `profile`

Ruta al archivo de configuración de perfil

- Requerido

### `--skip-reindex`, `-s`

Omitir reindexación

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Revierte el código base de la aplicación de Magento, los medios y la base de datos


### `--code-file`, `-c`

Nombre base del archivo de copia de seguridad de código en var/backups

- Requiere un valor

### `--media-file`, `-m`

Nombre base del archivo de copia de seguridad de medios en var/backups

- Requiere un valor

### `--db-file`, `-d`

Nombre base del archivo de copia de seguridad de la base de datos en var/backups

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Implementa archivos de vista estática



### `languages`

Lista separada por espacios de códigos de idioma ISO-639 para los que se van a generar archivos de vista estática.

- Predeterminado: `[]`

- Matriz

### `--force`, `-f`

Implemente archivos en cualquier modo.

- Predeterminado: `false`
- No acepta un valor

### `--strategy`, `-s`

Implemente archivos con la estrategia especificada.

- Predeterminado: `quick`
- Acepta un valor

### `--area`, `-a`

Genere archivos solo para las áreas especificadas.

- Predeterminado: `all`
- Acepta varios valores

### `--exclude-area`

No genere archivos para las áreas especificadas.

- Predeterminado: `none`
- Acepta varios valores

### `--theme`, `-t`

Generar archivos de vista estática solo para las temáticas especificadas.

- Predeterminado: `all`
- Acepta varios valores

### `--exclude-theme`

No genere archivos para las temáticas especificadas.

- Predeterminado: `none`
- Acepta varios valores

### `--language`, `-l`

Genere archivos solo para los idiomas especificados.

- Predeterminado: `all`
- Acepta varios valores

### `--exclude-language`

No genere archivos para los idiomas especificados.

- Predeterminado: `none`
- Acepta varios valores

### `--jobs`, `-j`

Habilite el procesamiento en paralelo con el número de trabajos especificado.

- Predeterminado: `0`
- Acepta un valor

### `--max-execution-time`

Tiempo máximo de ejecución esperado del proceso estático de implementación (en segundos).

- Predeterminado: `900`
- Acepta un valor

### `--symlink-locale`

Cree enlaces simbólicos para los archivos de esas configuraciones regionales, que se pasan para su implementación, pero no tienen personalizaciones.

- Predeterminado: `false`
- No acepta un valor

### `--content-version`

Se puede utilizar una versión personalizada del contenido estático si se ejecuta la implementación en varios nodos para garantizar que la versión del contenido estático sea idéntica y que el almacenamiento en caché funcione correctamente.

- Requiere un valor

### `--refresh-content-version-only`

Actualizar la versión del contenido estático solo se puede utilizar para actualizar el contenido estático en la caché del explorador y la caché de CDN.

- Predeterminado: `false`
- No acepta un valor

### `--no-javascript`

No implemente archivos JavaScript.

- Predeterminado: `false`
- No acepta un valor

### `--no-js-bundle`

No implemente archivos de paquete JavaScript.

- Predeterminado: `false`
- No acepta un valor

### `--no-css`

No implemente archivos CSS.

- Predeterminado: `false`
- No acepta un valor

### `--no-less`

No implemente archivos LESS.

- Predeterminado: `false`
- No acepta un valor

### `--no-images`

No implemente imágenes.

- Predeterminado: `false`
- No acepta un valor

### `--no-fonts`

No implemente archivos de fuentes.

- Predeterminado: `false`
- No acepta un valor

### `--no-html`

No implemente archivos de HTML.

- Predeterminado: `false`
- No acepta un valor

### `--no-misc`

No implemente archivos de otros tipos (.md, .jbf, .csv, etc.).

- Predeterminado: `false`
- No acepta un valor

### `--no-html-minify`

No minifique los archivos de HTML.

- Predeterminado: `false`
- No acepta un valor

### `--no-parent`

No compilar temáticas principales. Compatible solo con estrategias rápidas y estándar.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Instala la configuración de la tienda. Obsoleto desde 2.2.0. Utilice config:set en su lugar


### `--base-url`

La URL de la tienda debería estar disponible en. Obsoleto, usar config:set con ruta web/unsecure/base_url

- Requiere un valor

### `--language`

Código de idioma predeterminado. Obsoleto, use config:set con path general/locale/code

- Requiere un valor

### `--timezone`

Código de zona horaria predeterminado. Obsoleto, usar config:set con path general/locale/timezone

- Requiere un valor

### `--currency`

Código de moneda predeterminado. Obsoleto, usar config:set con la ruta currency/options/base, currency/options/default y currency/options/allow

- Requiere un valor

### `--use-rewrites`

Utilice las reescrituras. Obsoleto, use config:set con la ruta web/seo/use_rewrites

- Requiere un valor

### `--use-secure`

Utilice direcciones URL seguras. Active esta opción solo si SSL está disponible. Obsoleto, usar config:set con ruta web/secure/use_in_frontend

- Requiere un valor

### `--base-url-secure`

Dirección URL base para la conexión SSL. Obsoleto, usar config:set con ruta web/secure/base_url

- Requiere un valor

### `--use-secure-admin`

Ejecute la interfaz de administración con SSL. Obsoleto, usar config:set con ruta web/secure/use_in_adminhtml

- Requiere un valor

### `--admin-use-security-key`

Si se utiliza la función &quot;clave de seguridad&quot; en los formularios y las URL de administración de Magento. Obsoleto, usar config:set con path admin/security/use_form_key

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

Desinstala la aplicación Magento


### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Actualiza la aplicación de Magento, los datos de la base de datos y el esquema


### `--keep-generated`

Evita que se eliminen los archivos generados. No se recomienda utilizar esta opción excepto al implementarla en producción. Consulte al integrador de sistemas o al administrador para obtener más información.

- Predeterminado: `false`
- No acepta un valor

### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) al formato db_schema.xml.

- Predeterminado: `false`
- Acepta un valor

### `--safe-mode`

Instalación segura del Magento con volcados en operaciones destructivas, como la eliminación de columnas

- Acepta un valor

### `--data-restore`

Restauración de datos eliminados de volcados

- Acepta un valor

### `--dry-run`

La instalación del Magento se ejecutará en modo de ejecución en seco

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `store:list`

```bash
bin/magento store:list
```

Muestra la lista de tiendas


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `store:website:list`

```bash
bin/magento store:website:list
```

Muestra la lista de sitios web


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Desinstala el tema



### `theme`

Ruta del tema. La ruta del tema debe especificarse como ruta completa que es área/proveedor/nombre. Por ejemplo, frontend/Magento/blank

- Predeterminado: `[]`

- Requerido
- Matriz

### `--backup-code`

Realizar copia de seguridad del código (excepto archivos temporales)

- Predeterminado: `false`
- No acepta un valor

### `--clear-static-content`, `-c`

Borrar archivos de vista estática generados.

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Genera VCL de barniz y lo hace eco de la línea de comandos


### `--access-list`

Lista de IP de acceso que pueden purgar Barniz

- Predeterminado: `localhost`
- Requiere un valor

### `--backend-host`

Host del servidor web

- Predeterminado: `localhost`
- Requiere un valor

### `--backend-port`

Puerto del servidor web

- Predeterminado: `8080`
- Requiere un valor

### `--export-version`

La versión del archivo Varnish

- Predeterminado: `6`
- Requiere un valor

### `--grace-period`

Período de gracia en segundos

- Predeterminado: `300`
- Requiere un valor

### `--input-file`

Archivo de entrada desde el que generar VCL

- Requiere un valor

### `--output-file`

Ruta al archivo para escribir vcl

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el comando de lista

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
