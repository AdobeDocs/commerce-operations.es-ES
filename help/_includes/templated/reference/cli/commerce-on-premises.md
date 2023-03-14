---
source-git-commit: 177f301802e1ab1d0560ee98594b8128440efa7c
workflow-type: tm+mt
source-wordcount: '19444'
ht-degree: 0%

---
# bin/magento (Adobe Commerce local)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Versión**: 2.4.6-beta2

Esta referencia contiene 130 comandos disponibles a través del `bin/magento` herramienta de línea de comandos.
La lista inicial se genera automáticamente utilizando `bin/magento list` en la edición.
Utilice el [&quot;Agregar comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) para agregar un comando de CLI personalizado.

>[!NOTE]
>
>Puede llamar a `bin/magento` Comandos CLI que utilizan métodos abreviados en lugar del nombre de comando completo. Por ejemplo, puede llamar a `bin/magento setup:upgrade` usando `bin/magento s:up`, `bin/magento s:upg`. Consulte [sintaxis de acceso directo](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) para comprender cómo utilizar accesos directos con cualquier comando CLI.

>[!NOTE]
>
>Esta referencia se genera a partir del código base de la aplicación. Para cambiar el contenido, puede actualizar el código fuente para la implementación del comando correspondiente en la [código base](https://github.com/magento) y envíe los cambios para que se revisen. Otra forma es _Danos tu opinión_ (busque el vínculo en la parte superior derecha). Para ver las directrices de contribución, consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Comando interno para proporcionar sugerencias de finalización de shell

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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
bin/magento completion [--debug] [--] [<shell>]
```


### `shell`

El tipo de shell (p. ej. &quot;bash&quot;), el valor de la variable env &quot;$SHELL&quot; se usará si no se proporciona


### `--debug`

Seguimiento del registro de depuración de finalización

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilitar el módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Habilite el módulo Adobe IMS.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Información sobre la configuración del módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Estado del módulo Adobe IMS

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Crea un administrador

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Desbloquear cuenta de administrador

```bash
bin/magento admin:user:unlock <username>
```


### `username`

El nombre de usuario del administrador que desbloquear

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Crear volcado de aplicación

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Lista separada por espacios de los tipos de configuración u omitir para volcar todo [ámbitos, sistema, temas, i18n]

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Importación de datos de archivos de configuración compartidos al almacenamiento de datos adecuado

```bash
bin/magento app:config:import
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Comprueba si la propagación de la configuración requiere actualización

```bash
bin/magento app:config:status
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Migración de tarjetas almacenadas desde una base de datos de Magento 1

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Limpia los tipos de caché

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilita los tipos de caché

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Habilita los tipos de caché

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Vacía el almacenamiento de caché utilizado por los tipos de caché

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista separada por espacios de los tipos de caché u omita aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Comprueba el estado de caché

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

añadir o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Crea imágenes de productos redimensionadas

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Cambiar el tamaño de la imagen en modo asincrónico

- Predeterminado: `false`
- No acepta un valor

### `--skip_hidden_images`

No procesar imágenes marcadas como ocultas en la página del producto

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Elimina los atributos del producto no utilizados.

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establezca si desea aplicar la validación de contenido del HTML de usuario o mostrar una advertencia en su lugar

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establecer valores de configuración confidenciales

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Cambiar configuración del sistema

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el valor de configuración de una ruta determinada. Si no se especifica la ruta, se mostrarán todos los valores guardados

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genera e instala crontab para el usuario actual

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Forzar tareas de instalación

- Predeterminado: `false`
- No acepta un valor

### `--non-optional`, `-d`

Instalar solo las tareas no opcionales (predeterminadas)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Quita tareas de crontab

```bash
bin/magento cron:remove
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Ejecuta trabajos por programación

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

### `--group`

Ejecutar trabajos solo desde el grupo especificado

- Requiere un valor

### `--bootstrap`

Agregar o anular parámetros del bootstrap

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Actualizar el hash del cliente según el algoritmo más reciente

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establezca el modo de aplicación.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

El modo de aplicación que se va a establecer. Las opciones disponibles son &quot;desarrollador&quot; o &quot;producción&quot;

- Requerido

### `--skip-compilation`, `-s`

Omite la eliminación y regeneración del contenido estático (código generado, CSS preprocesado y recursos en pub/static/s)

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el modo de aplicación actual.

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Proporciona información sobre la configuración de la inyección de dependencias para el comando.

```bash
bin/magento dev:di:info <class>
```


### `class`

Nombre de clase

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Analiza las plantillas de newsletter por posibles problemas de compatibilidad de uso de variables

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Analiza las anulaciones de plantillas de correo electrónico para detectar posibles problemas de compatibilidad de uso de variables

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilite el generador de perfiles.

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Habilite el generador de perfiles.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Tipo de generador de perfiles


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilitar registro de consultas DB

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Habilitar registro de consultas DB

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Recopila y publica archivos de origen para temas.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilite las sugerencias de plantilla de front-end. Puede ser necesario vaciar la caché.

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Habilitar sugerencias de plantilla de front-end. Puede ser necesario vaciar la caché.

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Mostrar estado de sugerencias de plantilla de front-end.

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Ejecuta pruebas

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Tipo de prueba que se va a ejecutar. Tipos disponibles: todos, unidad, integración, integration-all, estático, static-all, integridad, heredado, predeterminado

- Predeterminado: `default`


### `--arguments`, `-c`

Argumentos adicionales para PHPUnit. Ejemplo: &quot;-c&#39;—filter=MyTest&#39;&quot; (sin espacios)

- Predeterminado: &quot;
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genera el catálogo de URN a asignaciones *.xsd para que el IDE resalte el xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Ruta al archivo para generar el catálogo. Para PhpStorm utilice .idea/misc.xml

- Requerido

### `--ide`

Formato en el que se generará el catálogo. Admitido: [phpstorm, vscode]

- Predeterminado: `phpstorm`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Convierte el archivo XML utilizando hojas de estilos XSL

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Añadir dominios a la lista blanca de dominios descargables

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Nombre de dominios

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Eliminar dominios de la lista blanca de dominios descargables

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Nombres de dominio

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Mostrar la lista blanca de dominios descargables

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Vuelve a cifrar los datos cifrados de la tarjeta de crédito con el último cifrado.

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:create-event-provider`

Cree un proveedor de eventos personalizado en Eventos de Adobe I/O para esta instancia. Si no especifica las opciones de etiqueta y descripción, deben definirse en el archivo del sistema app/etc/event-types.json.

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]
```


```bash
bin/magento events:provider:create 
```

### `--label`

Una etiqueta para definir el proveedor personalizado.

- Acepta un valor

### `--description`

Una descripción de su proveedor.

- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:generate:module`

Generar módulo basado en la lista de complementos

```bash
bin/magento events:generate:module
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:info`

Devuelve la carga útil del evento especificado.

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```


### `event-code`

Código de evento

- Requerido

### `--depth`

El número de niveles de la carga útil de evento que se van a devolver

- Predeterminado: `2`
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:list`

Muestra la lista de eventos suscritos

```bash
bin/magento events:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:list:all`

Devuelve una lista de eventos suscribibles definidos en el módulo especificado

```bash
bin/magento events:list:all <module_name>
```


### `module_name`

Nombre de módulo

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:metadata:populate`

Crea metadatos en el Adobe I/O a partir de la lista de configuración (configuraciones XML y de aplicación)

```bash
bin/magento events:metadata:populate
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:subscribe`

Suscribe al evento

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [--] <event-code>
```


### `event-code`

Código de evento

- Requerido

### `--force`, `-f`

Fuerza la suscripción del evento especificado, incluso si no se ha definido localmente.

- Predeterminado: `false`
- No acepta un valor

### `--fields`

La lista de campos de la carga útil de datos de evento.

- Predeterminado: `[]`
- Requiere un valor

### `--parent`

El código de evento principal de una suscripción de evento con reglas.

- Requiere un valor

### `--rules`

La lista de reglas para la suscripción de evento, donde cada regla tiene el formato &quot;campo\|operador\|valor&quot;.

- Predeterminado: `[]`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:sync-events-metadata`

Sincronizar metadatos de evento para esta instancia

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

### `--delete`, `-d`

Ya no es necesario eliminar metadatos de eventos

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `events:unsubscribe`

Quita la suscripción al evento proporcionado

```bash
bin/magento events:unsubscribe <event-code>
```


### `event-code`

Código de evento desde el que cancelar suscripción

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Descubre frases en la base de código

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Guarda el paquete de idioma

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Desinstala paquetes de idioma

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra indizadores permitidos

```bash
bin/magento indexer:info
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Reindexe datos

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Restablece el estado del indexador a no válido

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establecer modo de Dimension de indizador

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Nombre del indexador [catalog_product_price|catalogpermissions_category]


### `mode`

Modos de dimensión de indizador catalog_product_price none,sitio web,customer_group,sitio_web_and_customer_group catalogpermissions_category none,customer_group


### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establece el tipo de modo de índice

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Tipo de modo de indizador [tiempo real|programación]


### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el modo de Dimension del indizador

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Lista separada por espacios de los tipos de índice u omitir para aplicar a todos los índices (catalog_product_price,catalogpermissions_category)

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el modo de índice

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el estado del indizador

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Lista separada por espacios de los tipos de índice o omita aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el URI de administración del Magento

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Imprime una lista de los archivos de copia de seguridad disponibles

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra la lista de divisas disponibles

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el número de dependencias del marco de trabajo del Magento

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Nombre del informe

- Predeterminado: `framework-dependencies.csv`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el número de dependencias entre módulos

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Nombre del informe

- Predeterminado: `modules-dependencies.csv`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el número de dependencias circulares entre módulos

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Nombre del informe

- Predeterminado: `modules-circular-dependencies.csv`
- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra la lista de configuraciones regionales de idioma disponibles

```bash
bin/magento info:language:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra la lista de husos horarios disponibles

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Crear reservas con argumentos de compensación proporcionados

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Lista de argumentos de compensación en formato &quot;&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Predeterminado: `[]`

- Matriz

### `--raw`, `-r`

Salida en bruto

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Mostrar todos los pedidos y productos con incoherencias de cantidad vendible

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Descargar e importar nombres geográficos para el algoritmo de selección de origen

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Lista de códigos de país para importar

- Predeterminado: `[]`

- Requerido
- Matriz

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establece IP exentas del modo de mantenimiento

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Desactiva el modo de mantenimiento

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Direcciones IP permitidas (utilice &quot;ninguno&quot; para borrar la lista de direcciones IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Activa el modo de mantenimiento

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Direcciones IP permitidas (utilice &quot;ninguno&quot; para borrar la lista de direcciones IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el estado del modo de mantenimiento

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Sincronización de contenido con recursos

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Sincronizar el almacenamiento y los recursos de medios en la base de datos

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Comprueba la configuración de módulos en el archivo &#39;app/etc/config.php&#39; e informa si están actualizados o no

```bash
bin/magento module:config:status
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilita los módulos especificados

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Habilita módulos especificados

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra el estado de los módulos

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Desinstala los módulos instalados por composer

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Compruebe las entradas de la cola de implementación y cree un marcador de implementación adecuado.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Lista de consumidores de MessageQueue

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Reiniciar consumidores de MessageQueue

```bash
bin/magento queue:consumers:restart
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Iniciar consumidor de MessageQueue

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Sincronizar archivos multimedia con almacenamiento remoto.

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Implementación de módulos de datos de ejemplo para instalaciones de Magento basadas en compositores

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Elimine todos los paquetes de datos de ejemplo de composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Restablecer todos los módulos de datos de ejemplo para la reinstalación

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilitar reCAPTCHA para el usuario administrador olvidó el formulario de contraseña

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Deshabilitar reCAPTCHA para el formulario de inicio de sesión del usuario administrador

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Establezca el secreto utilizado para la generación OTP de Google.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

Nombre de usuario

- Requerido

### `secret`

Secreto

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Enumerar todos los proveedores disponibles

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Restablecer la configuración de un usuario

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

Nombre de usuario

- Requerido

### `provider`

Código de proveedor

- Requerido

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Realiza una copia de seguridad de la base de código, medios y base de datos de la aplicación Magento

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Crea o modifica la configuración de implementación

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nombre del front-end (se generará automáticamente si falta)

- Requiere un valor

### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

### `--enable-syslog-logging`

Habilitar registro syslog

- Requiere un valor

### `--id_salt`

Sal de GraphQl

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

### `--checkout-async`

¿Habilitar el procesamiento asincrónico de pedidos? 1 - Sí, 0 - No

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

### `--deferred-total-calculating`

¿Habilitar el cálculo total diferido? 1 - Sí, 0 - No

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

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Instala y actualiza datos en la base de datos

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genere el parche y colóquelo en una carpeta específica.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genere una lista blanca de tablas y columnas que el instalador de declaraciones pueda editar

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Nombre del módulo donde se generará la lista de admitidos

- Predeterminado: `all`
- Acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `setup:db-schema:add-slave`

Mover las tablas relacionadas con comillas de cierre de compra a un servidor de base de datos independiente

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host del servidor de base de datos esclava

- Predeterminado: `localhost`
- Requiere un valor

### `--dbname`

Nombre de base de datos esclava

- Requiere un valor

### `--username`

Nombre de usuario de Slave DB

- Predeterminado: `root`
- Requiere un valor

### `--password`

Contraseña de usuario de Slave DB

- Acepta un valor

### `--connection`

Nombre de conexión esclava

- Predeterminado: `default`
- Acepta un valor

### `--resource`

Nombre del recurso de esclavo

- Predeterminado: `default`
- Acepta un valor

### `--maxAllowedLag`

Número máximo permitido de conexiones de esclavos diferidos (en segundos)

- Predeterminado: &quot;
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `setup:db-schema:split-quote`

Mueva las tablas relacionadas con comillas de cierre de compra a un servidor de base de datos independiente. Obsoleto desde la versión 2.4.2 y se eliminará

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Desproteger host de DB Server

- Requiere un valor

### `--dbname`

Nombre de base de datos

- Requiere un valor

### `--username`

Nombre de usuario de BD de extracción

- Requiere un valor

### `--password`

Contraseña de usuario de extracción de base de datos

- Acepta un valor

### `--connection`

Nombre de conexión de extracción

- Predeterminado: `checkout`
- Acepta un valor

### `--resource`

Nombre del recurso de extracción

- Predeterminado: `checkout`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `setup:db-schema:split-sales`

Mover las tablas relacionadas con las ventas a un servidor de BD independiente. Obsoleto desde la versión 2.4.2 y se eliminará

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host del servidor de Sales DB

- Requiere un valor

### `--dbname`

Nombre de base de datos ventas

- Requiere un valor

### `--username`

Nombre de usuario de Sales DB

- Requiere un valor

### `--password`

Contraseña de usuario de Sales DB

- Acepta un valor

### `--connection`

Nombre de conexión de ventas

- Predeterminado: `sales`
- Acepta un valor

### `--resource`

Nombre del recurso de ventas

- Predeterminado: `sales`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Instala y actualiza el esquema de la base de datos

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Permite convertir scripts antiguos (InstallSchema, UpgradeSchema) al formato db_schema.xml.

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Comprueba si los datos o el esquema de la base de datos requieren actualización

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genera la configuración de ID y todas las clases que faltan que pueden generarse automáticamente

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Instala la aplicación Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nombre del front-end (se generará automáticamente si falta)

- Requiere un valor

### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

### `--enable-syslog-logging`

Habilitar registro syslog

- Requiere un valor

### `--id_salt`

Sal de GraphQl

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

### `--checkout-async`

¿Habilitar el procesamiento asincrónico de pedidos? 1 - Sí, 0 - No

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

### `--deferred-total-calculating`

¿Habilitar el cálculo total diferido? 1 - Sí, 0 - No

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

Motor de búsqueda. Valores: elasticsearch5, elasticsearch7, elasticsearch8, opensearch

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genera sujeciones

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

Ruta al archivo de configuración de perfil

- Requerido

### `--skip-reindex`, `-s`

Omitir reindexación

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Revierte el código base de la aplicación de Magento, los medios y la base de datos

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Implementa archivos de vista estática

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Instala la configuración de la tienda. Obsoleto desde 2.2.0. Utilice config:set en su lugar

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Desinstala la aplicación Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basar][path]=/var/www/example.com&amp;MAGE_DIRS[escondrijo][path]=/var/tmp/cache&quot;

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Actualiza la aplicación de Magento, los datos de la base de datos y el esquema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra la lista de tiendas

```bash
bin/magento store:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Muestra la lista de sitios web

```bash
bin/magento store:website:list
```

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `support:backup:code`

Crear copia de seguridad de código

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

Nombre del volcado

- Acepta un valor

### `--output`, `-o`

Ruta de salida

- Acepta un valor

### `--logs`, `-l`

Incluir registros

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `support:backup:db`

Crear copia de seguridad DB

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

Nombre del volcado

- Acepta un valor

### `--output`, `-o`

Ruta de salida

- Acepta un valor

### `--logs`, `-l`

Incluir registros

- Predeterminado: `false`
- No acepta un valor

### `--ignore-sanitize`, `-i`

Ignorar sanear

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `support:utility:check`

Compruebe las utilidades de copia de seguridad necesarias

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

Compruebe solo las utilidades de consola requeridas

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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


## `support:utility:paths`

Crear lista de rutas de utilidades

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

Forzar

- Predeterminado: `false`
- No acepta un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Desinstala el tema

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


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

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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

Genera VCL de barniz y lo hace eco de la línea de comandos

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

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

- Predeterminado: `4`
- Requiere un valor

### `--grace-period`

Período de gracia en segundos

- Predeterminado: `300`
- Requiere un valor

### `--output-file`

Ruta al archivo para escribir vcl

- Requiere un valor

### `--help`, `-h`

Muestra la ayuda del comando especificado. Cuando no se proporciona ningún comando, se muestra la ayuda para el &lt;info>lista&lt;/info> mando

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
