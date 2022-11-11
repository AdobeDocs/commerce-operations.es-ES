---
source-git-commit: 23d55385046de18b238c90f6a99be692f1ce7561
workflow-type: tm+mt
source-wordcount: '15643'
ht-degree: 0%

---
# bin/magento (Adobe Commerce local)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Versión**: 2.4.5

Esta referencia contiene 118 comandos disponibles a través del `bin/magento` herramienta de línea de comandos.
La lista inicial se genera automáticamente usando la variable `bin/magento list` en la edición.
Utilice la variable [&quot;Agregar comandos CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) guía para agregar un comando CLI personalizado.

>[!NOTE]
>
>Puede llamar a `bin/magento` Los comandos CLI utilizan accesos directos en lugar del nombre completo del comando. Por ejemplo, puede llamar a `bin/magento setup:upgrade` using `bin/magento s:up`, `bin/magento s:upg`. Consulte [sintaxis de acceso directo](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) para comprender cómo usar accesos directos con cualquier comando CLI.

>[!NOTE]
>
>Esta referencia se genera a partir de la base de código de la aplicación. Para cambiar el contenido, puede actualizar el código fuente para la implementación de comandos correspondiente en la [código](https://github.com/magento) y envíe los cambios para su revisión. Otra forma es _Envíenos sus comentarios_ (busque el vínculo en la parte superior derecha). Para ver las directrices de contribución, consulte [Contribuciones de código](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

Mostrar ayuda para un comando

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `list`

Comandos de lista

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```


### `namespace`

El nombre del área de nombres


### `--raw`

Para generar la lista de comandos sin procesar

- Predeterminado: `false`
- No acepta un valor

### `--format`

El formato de salida (txt, xml, json o md)

- Predeterminado: `txt`
- Requiere un valor


## `admin:adobe-ims:disable`

Desactivación del módulo IMS de Adobe

```bash
bin/magento admin:adobe-ims:disable
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `admin:adobe-ims:enable`

Habilite el módulo IMS de Adobe.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Establezca el ID de organización para la configuración de IMS de Adobe. Requerido al habilitar el módulo

- Acepta un valor

### `--client-id`, `-c`

Establezca el ID de cliente para la configuración IMS de Adobe. Requerido al habilitar el módulo

- Acepta un valor

### `--client-secret`, `-s`

Establezca el Secreto del cliente para la configuración IMS de Adobe. Requerido al habilitar el módulo

- Acepta un valor

### `--2fa`, `-t`

Compruebe si 2FA está habilitado para la organización en Adobe Admin Console. Requerido al habilitar el módulo

- Acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `admin:adobe-ims:info`

Información sobre la configuración del módulo IMS de Adobe

```bash
bin/magento admin:adobe-ims:info
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `admin:adobe-ims:status`

Estado del módulo IMS de Adobe

```bash
bin/magento admin:adobe-ims:status
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `admin:user:unlock`

Desbloquear cuenta de administrador

```bash
bin/magento admin:user:unlock <username>
```


### `username`

El nombre de usuario del administrador para desbloquear

- Requerido

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `app:config:dump`

Crear volcado de aplicación

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Lista de tipos de configuración separados por espacios u omisión para volcar todos [ámbitos, temas, sistema, i18n]

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `app:config:import`

Importar datos de archivos de configuración compartidos a un almacenamiento de datos adecuado

```bash
bin/magento app:config:import
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `app:config:status`

Comprueba si la propagación de la configuración requiere actualización

```bash
bin/magento app:config:status
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Nombre de la base de datos

- Requiere un valor

### `--username`

Nombre de usuario de la base de datos. Debe tener acceso de lectura

- Requiere un valor

### `--password`

Contraseña

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `cache:clean`

Limpia tipos de caché

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de caché separados por espacio u omisión para aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

agregar o anular parámetros de bootstrap

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `cache:disable`

Desactiva los tipos de caché

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de caché separados por espacio u omisión para aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

agregar o anular parámetros de bootstrap

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `cache:enable`

Habilita tipos de caché

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de caché separados por espacio u omisión para aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

agregar o anular parámetros de bootstrap

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `cache:flush`

Vacía el almacenamiento de caché utilizado por los tipos de caché

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lista de tipos de caché separados por espacio u omisión para aplicar a todos los tipos de caché.

- Predeterminado: `[]`

- Matriz

### `--bootstrap`

agregar o anular parámetros de bootstrap

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `cache:status`

Comprueba el estado de la caché

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

agregar o anular parámetros de bootstrap

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `catalog:images:resize`

Crea imágenes de producto cambiadas de tamaño

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Cambiar el tamaño de la imagen en modo asíncrono

- Predeterminado: `false`
- No acepta un valor

### `--skip_hidden_images`

No procesar imágenes marcadas como ocultas desde la página de producto

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `catalog:product:attributes:cleanup`

Quita los atributos del producto no utilizados.

```bash
bin/magento catalog:product:attributes:cleanup
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `config:sensitive:set`

Definir valores de configuración confidenciales

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

Ruta de configuración, por ejemplo, group/section/field_name


### `value`

Valor de configuración


### `--interactive`, `-i`

Habilitar el modo interactivo para establecer todas las variables confidenciales

- Predeterminado: `false`
- No acepta un valor

### `--scope`

Ámbito de configuración, si no se establece, utilice &quot;predeterminado&quot;

- Predeterminado: `default`
- Acepta un valor

### `--scope-code`

Código de ámbito de configuración, cadena vacía de forma predeterminada

- Predeterminado: &quot;
- Acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `config:set`

Cambiar la configuración del sistema

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

Ruta de configuración en formato section/group/field_name

- Requerido

### `value`

Valor de configuración

- Requerido

### `--scope`

Ámbito de configuración (predeterminado, sitio web o tienda)

- Predeterminado: `default`
- Requiere un valor

### `--scope-code`

Código de ámbito (obligatorio solo si el ámbito no es &quot;predeterminado&quot;)

- Requiere un valor

### `--lock-env`, `-e`

Bloqueo del valor que impide la modificación en el administrador (se guardará en app/etc/env.php)

- Predeterminado: `false`
- No acepta un valor

### `--lock-config`, `-c`

Bloquear y compartir valores con otras instalaciones, evita la modificación en el administrador (se guardará en app/etc/config.php)

- Predeterminado: `false`
- No acepta un valor

### `--lock`, `-l`

En desuso, utilice la opción —lock-env en su lugar.

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `config:show`

Muestra el valor de configuración de una ruta determinada. Si no se especifica la ruta, se mostrarán todos los valores guardados

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Ruta de configuración, por ejemplo, section_id/group_id/field_id


### `--scope`

Ámbito de configuración, si no se especifica, se utilizará el ámbito &quot;predeterminado&quot;

- Predeterminado: `default`
- Acepta un valor

### `--scope-code`

Código de ámbito (obligatorio solo si el ámbito no `default`)

- Predeterminado: &quot;
- Acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `cron:remove`

Quita tareas de crontab

```bash
bin/magento cron:remove
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Añadir o anular parámetros del bootstrap

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `customer:hash:upgrade`

Actualice el hash del cliente según el algoritmo más reciente

```bash
bin/magento customer:hash:upgrade
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `deploy:mode:set`

Configure el modo de aplicación.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

El modo de aplicación que se va a establecer. Las opciones disponibles son &quot;desarrollador&quot; o &quot;producción&quot;

- Requerido

### `--skip-compilation`, `-s`

Omite la eliminación y regeneración del contenido estático (código generado, CSS preprocesado y recursos en pub/static/)

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `deploy:mode:show`

Muestra el modo de aplicación actual.

```bash
bin/magento deploy:mode:show
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:di:info`

Proporciona información sobre la configuración de la inyección de dependencias para el comando.

```bash
bin/magento dev:di:info <class>
```


### `class`

Nombre de la clase

- Requerido

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:email:newsletter-compatibility-check`

Analiza las plantillas de boletín para detectar posibles problemas de compatibilidad con el uso de variables

```bash
bin/magento dev:email:newsletter-compatibility-check
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:email:override-compatibility-check`

Analiza las anulaciones de plantillas de correo electrónico para detectar posibles problemas de compatibilidad con el uso de variables

```bash
bin/magento dev:email:override-compatibility-check
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:profiler:disable`

Deshabilite el perfilador.

```bash
bin/magento dev:profiler:disable
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:profiler:enable`

Habilite el perfilador.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Tipo de perfilador


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:query-log:disable`

Deshabilitar el registro de consultas de base de datos

```bash
bin/magento dev:query-log:disable
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:query-log:enable`

Habilitar el registro de consultas de base de datos

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

Registre todas las consultas. [true\|false]

- Predeterminado: `true`
- Acepta un valor

### `--query-time-threshold`

Umbrales de tiempo de consulta.

- Predeterminado: `0.001`
- Acepta un valor

### `--include-call-stack`

Incluya la pila de llamadas. [true\|false]

- Predeterminado: `true`
- Acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:source-theme:deploy`

Recopila y publica archivos de origen para el tema.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

Archivos que se van a procesar previamente (el archivo debe especificarse sin extensión)

- Predeterminado: `css/styles-mcss/styles-l`

- Matriz

### `--type`

Tipo de archivos de origen: [less]

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:template-hints:disable`

Desactivar sugerencias de plantilla de front-end. Puede que sea necesario vaciar la caché.

```bash
bin/magento dev:template-hints:disable
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:template-hints:enable`

Habilitar las sugerencias de plantilla de front-end. Puede que sea necesario vaciar la caché.

```bash
bin/magento dev:template-hints:enable
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:template-hints:status`

Mostrar el estado de las sugerencias de plantilla de front-end.

```bash
bin/magento dev:template-hints:status
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:tests:run`

Ejecuta pruebas

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Tipo de prueba que se va a ejecutar. Tipos disponibles: all, unit, integration, integration-all, static, static, static-all, integridad, heredado, predeterminado

- Predeterminado: `default`


### `--arguments`, `-c`

Argumentos adicionales para PHPUnit. Ejemplo: &quot;-c&#39;—filter=MyTest&#39;&quot; (sin espacios)

- Predeterminado: &quot;
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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:urn-catalog:generate`

Genera el catálogo de URN a asignaciones *.xsd para el IDE para resaltar xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Ruta al archivo para generar el catálogo. Para PhpStorm, utilice .idea/misc.xml

- Requerido

### `--ide`

Formato en el que se generará el catálogo. Admitido: [phptormenta, vscode]

- Predeterminado: `phpstorm`
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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `dev:xml:convert`

Convierte el archivo XML utilizando hojas de estilo XSL

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

Ruta al archivo XML que se va a transformar

- Requerido

### `processor`

Ruta a la hoja de estilo XSL que se aplicará al archivo XML

- Requerido

### `--overwrite`, `-o`

Sobrescribir archivo XML

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `downloadable:domains:add`

Agregar dominios a la lista blanca de dominios descargables

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Nombre de dominios

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `downloadable:domains:remove`

Eliminación de dominios de la lista blanca de dominios descargables

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Nombres de dominio

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `downloadable:domains:show`

Mostrar lista blanca de dominios descargables

```bash
bin/magento downloadable:domains:show
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `encryption:payment-data:update`

Vuelva a cifrar los datos cifrados de la tarjeta de crédito con el cifrado más reciente.

```bash
bin/magento encryption:payment-data:update
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `i18n:collect-phrases`

Descubre frases en la base de código

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

Ruta de acceso de directorio para analizar. No es necesario si se establece el indicador —magento


### `--output`, `-o`

Ruta (incluido el nombre de archivo) a un archivo de salida. Si no se especifica ningún archivo, el valor predeterminado es stdout.

- Requiere un valor

### `--magento`, `-m`

Utilice el parámetro —magento para analizar el código base del Magento actual. Omite el parámetro si se especifica un directorio.

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `i18n:pack`

Guarda el paquete de idioma

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

Ruta al archivo de diccionario de origen con traducciones

- Requerido

### `locale`

Configuración regional de destino para diccionario, por ejemplo &quot;de_DE&quot;

- Requerido

### `--mode`, `-m`

Modo de guardado para el diccionario - &quot;replace&quot; - replace language pack by new - &quot;merge&quot; - merge language packages, de forma predeterminada &quot;replace&quot;

- Predeterminado: `replace`
- Requiere un valor

### `--allow-duplicates`, `-d`

Utilice el parámetro —allow-duplicates para permitir guardar duplicados de translate. De lo contrario, omita el parámetro .

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:info`

Muestra los indexadores permitidos

```bash
bin/magento indexer:info
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:reindex`

Reindexa datos

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Lista de tipos de índice separados por espacios u omisión para aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:reset`

Restablece el estado del indexador a no válido

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Lista de tipos de índice separados por espacios u omisión para aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:set-dimensions-mode`

Definir modo de Dimension de indexador

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Nombre del indexador [catalog_product_price|catalogpermissions_category]


### `mode`

Modos de dimensión de indexador catálogo_producto_precio ninguno,sitio web,grupo_cliente,sitio_web_y_grupo_cliente_catálogos_categoría ninguno,grupo_cliente


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:set-mode`

Define el tipo de modo de índice

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Tipo de modo de indexador [tiempo real|programación]


### `index`

Lista de tipos de índice separados por espacios u omisión para aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:show-dimensions-mode`

Muestra el modo Dimension de indexador

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Lista de tipos de índice separados por espacio u omisión para aplicar a todos los índices (catalog_product_price,catalogpermissions_category)

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:show-mode`

Muestra el modo de índice

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Lista de tipos de índice separados por espacios u omisión para aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `indexer:status`

Muestra el estado del indexador

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Lista de tipos de índice separados por espacios u omisión para aplicar a todos los índices.

- Predeterminado: `[]`

- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:adminuri`

Muestra el URI de administración del Magento

```bash
bin/magento info:adminuri
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:backups:list`

Imprime la lista de archivos de copia de seguridad disponibles

```bash
bin/magento info:backups:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:currency:list`

Muestra la lista de monedas disponibles

```bash
bin/magento info:currency:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:dependencies:show-framework`

Muestra el número de dependencias en el marco del Magento

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Nombre del archivo del informe

- Predeterminado: `framework-dependencies.csv`
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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:dependencies:show-modules`

Muestra el número de dependencias entre módulos

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Nombre del archivo del informe

- Predeterminado: `modules-dependencies.csv`
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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:dependencies:show-modules-circular`

Muestra el número de dependencias circulares entre módulos

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Nombre del archivo del informe

- Predeterminado: `modules-circular-dependencies.csv`
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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:language:list`

Muestra la lista de configuraciones regionales de idioma disponibles

```bash
bin/magento info:language:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `info:timezone:list`

Muestra la lista de zonas horarias disponibles

```bash
bin/magento info:timezone:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `inventory:reservation:create-compensations`

Crear reservas mediante los argumentos de compensación proporcionados

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Lista de argumentos de compensación en formato &quot;&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Predeterminado: `[]`

- Matriz

### `--raw`, `-r`

Salida sin procesar

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `inventory:reservation:list-inconsistencies`

Mostrar todos los pedidos y productos con incoherencias en la cantidad salable

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

Mostrar solo incoherencias para pedidos completos

- Predeterminado: `false`
- No acepta un valor

### `--incomplete-orders`, `-i`

Mostrar solo incoherencias para pedidos incompletos

- Predeterminado: `false`
- No acepta un valor

### `--bunch-size`, `-b`

Define cuántos pedidos se cargarán a la vez

- Predeterminado: `50`
- Acepta un valor

### `--raw`, `-r`

Salida sin procesar

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `inventory-geonames:import`

Descargar e importar nombres geográficos para el algoritmo de selección de fuentes

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Lista de códigos de país a importar

- Predeterminado: `[]`

- Requerido
- Matriz

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `maintenance:allow-ips`

Establece las direcciones IP exentas del modo de mantenimiento

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

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `maintenance:disable`

Desactiva el modo de mantenimiento

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Direcciones IP permitidas (use &quot;ninguno&quot; para borrar la lista de IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `maintenance:enable`

Habilita el modo de mantenimiento

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Direcciones IP permitidas (use &quot;ninguno&quot; para borrar la lista de IP permitidas)

- Predeterminado: `[]`
- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `maintenance:status`

Muestra el estado del modo de mantenimiento

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `media-content:sync`

Sincronizar contenido con recursos

```bash
bin/magento media-content:sync
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `media-gallery:sync`

Sincronizar el almacenamiento de medios y los recursos de medios en la base de datos

```bash
bin/magento media-gallery:sync
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `module:config:status`

Comprueba la configuración de los módulos en el archivo &quot;app/etc/config.php&quot; e informa si están actualizados o no

```bash
bin/magento module:config:status
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `module:disable`

Desactiva los módulos especificados

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

Borre los archivos de vista estáticos generados. Necesario, si los módulos tienen archivos de vista estáticos

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Borre los archivos de vista estáticos generados. Necesario, si los módulos tienen archivos de vista estáticos

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `module:status`

Muestra el estado de los módulos

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

Nombre del módulo opcional

- Predeterminado: `[]`

- Matriz

### `--enabled`

Imprimir solo módulos habilitados

- Predeterminado: `false`
- No acepta un valor

### `--disabled`

Imprimir solo módulos desactivados

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `module:uninstall`

Desinstala los módulos instalados por el compositor

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

Realizar copia de seguridad completa de la base de datos

- Predeterminado: `false`
- No acepta un valor

### `--non-composer`

Todos los módulos que pasarán aquí no estarán basados en compositores

- Predeterminado: `false`
- No acepta un valor

### `--clear-static-content`, `-c`

Borre los archivos de vista estáticos generados. Necesario, si los módulos tienen archivos de vista estáticos

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `newrelic:create:deploy-marker`

Compruebe si hay entradas en la cola de implementación y cree un marcador de implementación adecuado.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

¿Implementar mensaje?

- Requerido

### `change_log`

¿Desea cambiar el registro?

- Requerido

### `user`

Usuario de implementación


### `revision`

Revisión


### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `queue:consumers:list`

Lista de consumidores de MessageQueue

```bash
bin/magento queue:consumers:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Número de mensajes que debe procesar el consumidor antes de la finalización del proceso. Si no se especifica: termine después de procesar todos los mensajes en cola.

- Requiere un valor

### `--batch-size`

Número de mensajes por lote. Aplicable únicamente al consumidor de lotes.

- Requiere un valor

### `--area-code`

El área preferida (global, adminhtml, etc.) predeterminada es global.

- Requiere un valor

### `--single-thread`

Esta opción evita ejecutar varias copias de un consumidor simultáneamente.

- Predeterminado: `false`
- No acepta un valor

### `--multi-process`

Número de procesos por consumidor.

- Acepta un valor

### `--pid-file-path`

La ruta del archivo para guardar PID (esta opción está en desuso, utilice —single-thread en su lugar)

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `remote-storage:sync`

Sincronice archivos multimedia con almacenamiento remoto.

```bash
bin/magento remote-storage:sync
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `sampledata:remove`

Eliminar todos los paquetes de datos de ejemplo de composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Actualizar composer.json sin ejecutar la actualización del compositor

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `sampledata:reset`

Restablecer todos los módulos de datos de ejemplo para su reinstalación

```bash
bin/magento sampledata:reset
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `security:recaptcha:disable-for-user-forgot-password`

Deshabilitar reCAPTCHA para el usuario administrador se olvidó del formulario de contraseña

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `security:recaptcha:disable-for-user-login`

Deshabilitar reCAPTCHA para el formulario de inicio de sesión del usuario administrador

```bash
bin/magento security:recaptcha:disable-for-user-login
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `security:tfa:providers`

Lista de todos los proveedores disponibles

```bash
bin/magento security:tfa:providers
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `security:tfa:reset`

Restablecer la configuración para un usuario

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:backup`

Toma la copia de seguridad de la base de código de la aplicación Magento, los medios y la base de datos

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

Realizar copia de seguridad completa de la base de datos

- Predeterminado: `false`
- No acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:config:set`

Crea o modifica la configuración de implementación

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nombre del frente del servidor (se generará automáticamente si falta)

- Requiere un valor

### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

### `--enable-syslog-logging`

Habilitar el registro de syslog

- Requiere un valor

### `--remote-storage-driver`

Controlador de almacenamiento remoto

- Requiere un valor

### `--remote-storage-prefix`

Prefijo de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-endpoint`

Punto de conexión de almacenamiento remoto

- Requiere un valor

### `--remote-storage-bucket`

Cubo de almacenamiento remoto

- Requiere un valor

### `--remote-storage-region`

Región de almacenamiento remoto

- Requiere un valor

### `--remote-storage-key`

Clave de acceso a almacenamiento remoto

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

¿Desea habilitar el procesamiento asincrónico de pedidos? 1 - Sí, 0 - No

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

La conexión predeterminada de colas de mensajes es predeterminada. Puede ser &#39;db&#39;, &#39;amqp&#39; o un sistema de cola personalizado. El sistema de colas debe estar instalado y configurado; de lo contrario, los mensajes no se procesarán correctamente.

- Requiere un valor

### `--deferred-total-calculating`

¿Desea habilitar el cálculo total diferido? 1 - Sí, 0 - No

- Requiere un valor

### `--key`

Clave de cifrado

- Requiere un valor

### `--db-host`

Host del servidor de bases de datos

- Requiere un valor

### `--db-name`

Nombre de la base de datos

- Requiere un valor

### `--db-user`

Nombre de usuario del servidor de bases de datos

- Requiere un valor

### `--db-engine`

Motor del servidor de bases de datos

- Requiere un valor

### `--db-password`

Contraseña del servidor de base de datos

- Requiere un valor

### `--db-prefix`

Prefijo de tabla de base de datos

- Requiere un valor

### `--db-model`

Tipo de base de datos

- Requiere un valor

### `--db-init-statements`

Conjunto inicial de comandos de base de datos

- Requiere un valor

### `--skip-db-validation`, `-s`

Si se especifica, se omitirá la validación de conexión db

- Predeterminado: `false`
- No acepta un valor

### `--http-cache-hosts`

Hosts de caché http

- Requiere un valor

### `--db-ssl-key`

Ruta completa del archivo de clave de cliente para establecer la conexión de base de datos a través de SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-cert`

Ruta completa del archivo de certificado de cliente para establecer la conexión de base de datos a través de SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-ca`

Ruta completa del archivo de certificado del servidor para establecer la conexión de base de datos a través de SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-verify`

Verificar la certificación del servidor

- Predeterminado: `false`
- No acepta un valor

### `--session-save`

Controlador de guardado de sesión

- Requiere un valor

### `--session-save-redis-host`

Nombre de host completo, dirección IP o ruta absoluta si se usan sockets UNIX

- Requiere un valor

### `--session-save-redis-port`

Puerto de escucha del servidor de Redis

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

Número de base de datos de Redis

- Requiere un valor

### `--session-save-redis-compression-threshold`

Umbral de compresión de redis

- Requiere un valor

### `--session-save-redis-compression-lib`

Biblioteca de compresión de redis. Valores: gzip (predeterminado), lzf, lz4, snpy

- Requiere un valor

### `--session-save-redis-log-level`

Nivel de registro de redis. Valores: 0 (menos detallado) a 7 (más detallado)

- Requiere un valor

### `--session-save-redis-max-concurrency`

Número máximo de procesos que pueden esperar un bloqueo en una sesión

- Requiere un valor

### `--session-save-redis-break-after-frontend`

Número de segundos que hay que esperar antes de intentar romper un bloqueo para la sesión de front-end

- Requiere un valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos que hay que esperar antes de intentar romper un bloqueo de la sesión de administrador

- Requiere un valor

### `--session-save-redis-first-lifetime`

Duración, en segundos, de la sesión para los no bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

### `--session-save-redis-bot-first-lifetime`

Duración, en segundos, de la sesión para bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

### `--session-save-redis-bot-lifetime`

Duración de la sesión para bots en escrituras posteriores (use 0 para deshabilitar)

- Requiere un valor

### `--session-save-redis-disable-locking`

Redis desactive el bloqueo. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-min-lifetime`

Duración de la sesión mínima de eliminación, en segundos

- Requiere un valor

### `--session-save-redis-max-lifetime`

Duración máxima de la sesión de Redis, en segundos

- Requiere un valor

### `--session-save-redis-sentinel-master`

Redis Sentinel maestro

- Requiere un valor

### `--session-save-redis-sentinel-servers`

Redis Centinela, servidores separados por comas

- Requiere un valor

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica maestro. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conecta reintentos.

- Requiere un valor

### `--cache-backend`

Controlador de caché predeterminado

- Requiere un valor

### `--cache-backend-redis-server`

Redis server

- Requiere un valor

### `--cache-backend-redis-db`

Número de base de datos para la caché

- Requiere un valor

### `--cache-backend-redis-port`

Puerto de escucha del servidor de Redis

- Requiere un valor

### `--cache-backend-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--cache-backend-redis-compress-data`

Establézcalo en 0 para desactivar la compresión (el valor predeterminado es 1, activado)

- Requiere un valor

### `--cache-backend-redis-compression-lib`

lib de compresión para usar [snply,lzf,l4z,zstd,gzip] (deje en blanco para determinarlo automáticamente)

- Requiere un valor

### `--cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--allow-parallel-generation`

Permitir generar caché de forma que no se bloquee

- Predeterminado: `false`
- No acepta un valor

### `--page-cache`

Controlador de caché predeterminado

- Requiere un valor

### `--page-cache-redis-server`

Redis server

- Requiere un valor

### `--page-cache-redis-db`

Número de base de datos para la caché

- Requiere un valor

### `--page-cache-redis-port`

Puerto de escucha del servidor de Redis

- Requiere un valor

### `--page-cache-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--page-cache-redis-compress-data`

Configúrelo en 1 para comprimir la caché de página completa (use 0 para deshabilitar)

- Requiere un valor

### `--page-cache-redis-compression-lib`

Biblioteca de compresión que se va a usar [snply,lzf,l4z,zstd,gzip] (deje en blanco para determinarlo automáticamente)

- Requiere un valor

### `--page-cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--lock-provider`

Bloquear nombre del proveedor

- Requiere un valor

### `--lock-db-prefix`

Prefijo de bloqueo específico de instalación para evitar conflictos de bloqueo

- Requiere un valor

### `--lock-zookeeper-host`

Host y puerto para conectarse al clúster de Zookeeper. Por ejemplo: 127.0.0.1:2181

- Requiere un valor

### `--lock-zookeeper-path`

Ruta donde Zookeeper guardará bloqueos. La ruta predeterminada es: /magento/locks

- Requiere un valor

### `--lock-file-path`

La ruta donde se guardarán los bloqueos de archivo.

- Requiere un valor

### `--document-root-is-pub`

El indicador que se muestra es Pub está en la raíz, puede ser verdadero o falso solo

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-data:upgrade`

Instala y actualiza los datos en la base de datos

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-declaration:generate-patch`

Genere el parche y colóquelo en una carpeta específica.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

Nombre del módulo

- Requerido

### `patch`

Nombre del parche

- Requerido

### `--revertable`

Compruebe si el parche es revertible o no.

- Predeterminado: `false`
- Acepta un valor

### `--type`

Averigüe qué tipo de parche debe generarse. Valores disponibles: `data`, `schema`.

- Predeterminado: `data`
- Acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-declaration:generate-whitelist`

Generar lista blanca de tablas y columnas que el instalador de declaraciones puede editar

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Nombre del módulo en el que se generará la lista blanca

- Predeterminado: `all`
- Acepta un valor

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-schema:add-slave`

Mover tablas relacionadas con comillas de cierre de compra a un servidor de base de datos independiente

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Servidor de base de datos esclavo

- Predeterminado: `localhost`
- Requiere un valor

### `--dbname`

Nombre de la base de datos esclava

- Requiere un valor

### `--username`

Nombre de usuario de la base de datos esclava

- Predeterminado: `root`
- Requiere un valor

### `--password`

Contraseña de usuario de la base de datos esclava

- Acepta un valor

### `--connection`

Nombre de conexión esclava

- Predeterminado: `default`
- Acepta un valor

### `--resource`

Nombre del recurso esclavo

- Predeterminado: `default`
- Acepta un valor

### `--maxAllowedLag`

Conexión máxima permitida del esclavo de retraso (en segundos)

- Predeterminado: &quot;
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-schema:split-quote`

Mueva las tablas relacionadas con las comillas de cierre de compra a un servidor de base de datos independiente. Obsoleto desde la versión 2.4.2 y se eliminará

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Servidor de base de datos de cierre de compra

- Requiere un valor

### `--dbname`

Nombre de la base de datos de cierre de compra

- Requiere un valor

### `--username`

Nombre de usuario de la base de datos de cierre de compra

- Requiere un valor

### `--password`

Contraseña de usuario de la base de datos de cierre de compra

- Acepta un valor

### `--connection`

Nombre de conexión de cierre de compra

- Predeterminado: `checkout`
- Acepta un valor

### `--resource`

Nombre del recurso de cierre de compra

- Predeterminado: `checkout`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-schema:split-sales`

Mueva las tablas relacionadas con las ventas a un servidor de base de datos independiente. Obsoleto desde la versión 2.4.2 y se eliminará

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host del servidor de bases de datos de ventas

- Requiere un valor

### `--dbname`

Nombre de base de datos de ventas

- Requiere un valor

### `--username`

Nombre de usuario de la base de datos de ventas

- Requiere un valor

### `--password`

Contraseña de usuario de la base de datos de ventas

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

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db-schema:upgrade`

Instala y actualiza el esquema de base de datos

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Permite convertir secuencias de comandos antiguas (InstallSchema, UpgradeSchema) al formato db_schema.xml

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:db:status`

Comprueba si el esquema o los datos de DB requieren actualización

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:di:compile`

Genera la configuración de ID y todas las clases que faltan que se pueden generar automáticamente

```bash
bin/magento setup:di:compile
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:install`

Instala la aplicación Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nombre del frente del servidor (se generará automáticamente si falta)

- Requiere un valor

### `--enable-debug-logging`

Habilitar el registro de depuración

- Requiere un valor

### `--enable-syslog-logging`

Habilitar el registro de syslog

- Requiere un valor

### `--remote-storage-driver`

Controlador de almacenamiento remoto

- Requiere un valor

### `--remote-storage-prefix`

Prefijo de almacenamiento remoto

- Predeterminado: &quot;
- Requiere un valor

### `--remote-storage-endpoint`

Punto de conexión de almacenamiento remoto

- Requiere un valor

### `--remote-storage-bucket`

Cubo de almacenamiento remoto

- Requiere un valor

### `--remote-storage-region`

Región de almacenamiento remoto

- Requiere un valor

### `--remote-storage-key`

Clave de acceso a almacenamiento remoto

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

¿Desea habilitar el procesamiento asincrónico de pedidos? 1 - Sí, 0 - No

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

La conexión predeterminada de colas de mensajes es predeterminada. Puede ser &#39;db&#39;, &#39;amqp&#39; o un sistema de cola personalizado. El sistema de colas debe estar instalado y configurado; de lo contrario, los mensajes no se procesarán correctamente.

- Requiere un valor

### `--deferred-total-calculating`

¿Desea habilitar el cálculo total diferido? 1 - Sí, 0 - No

- Requiere un valor

### `--key`

Clave de cifrado

- Requiere un valor

### `--db-host`

Host del servidor de bases de datos

- Requiere un valor

### `--db-name`

Nombre de la base de datos

- Requiere un valor

### `--db-user`

Nombre de usuario del servidor de bases de datos

- Requiere un valor

### `--db-engine`

Motor del servidor de bases de datos

- Requiere un valor

### `--db-password`

Contraseña del servidor de base de datos

- Requiere un valor

### `--db-prefix`

Prefijo de tabla de base de datos

- Requiere un valor

### `--db-model`

Tipo de base de datos

- Requiere un valor

### `--db-init-statements`

Conjunto inicial de comandos de base de datos

- Requiere un valor

### `--skip-db-validation`, `-s`

Si se especifica, se omitirá la validación de conexión db

- Predeterminado: `false`
- No acepta un valor

### `--http-cache-hosts`

Hosts de caché http

- Requiere un valor

### `--db-ssl-key`

Ruta completa del archivo de clave de cliente para establecer la conexión de base de datos a través de SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-cert`

Ruta completa del archivo de certificado de cliente para establecer la conexión de base de datos a través de SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-ca`

Ruta completa del archivo de certificado del servidor para establecer la conexión de base de datos a través de SSL

- Predeterminado: &quot;
- Requiere un valor

### `--db-ssl-verify`

Verificar la certificación del servidor

- Predeterminado: `false`
- No acepta un valor

### `--session-save`

Controlador de guardado de sesión

- Requiere un valor

### `--session-save-redis-host`

Nombre de host completo, dirección IP o ruta absoluta si se usan sockets UNIX

- Requiere un valor

### `--session-save-redis-port`

Puerto de escucha del servidor de Redis

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

Número de base de datos de Redis

- Requiere un valor

### `--session-save-redis-compression-threshold`

Umbral de compresión de redis

- Requiere un valor

### `--session-save-redis-compression-lib`

Biblioteca de compresión de redis. Valores: gzip (predeterminado), lzf, lz4, snpy

- Requiere un valor

### `--session-save-redis-log-level`

Nivel de registro de redis. Valores: 0 (menos detallado) a 7 (más detallado)

- Requiere un valor

### `--session-save-redis-max-concurrency`

Número máximo de procesos que pueden esperar un bloqueo en una sesión

- Requiere un valor

### `--session-save-redis-break-after-frontend`

Número de segundos que hay que esperar antes de intentar romper un bloqueo para la sesión de front-end

- Requiere un valor

### `--session-save-redis-break-after-adminhtml`

Número de segundos que hay que esperar antes de intentar romper un bloqueo de la sesión de administrador

- Requiere un valor

### `--session-save-redis-first-lifetime`

Duración, en segundos, de la sesión para los no bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

### `--session-save-redis-bot-first-lifetime`

Duración, en segundos, de la sesión para bots en la primera escritura (use 0 para deshabilitar)

- Requiere un valor

### `--session-save-redis-bot-lifetime`

Duración de la sesión para bots en escrituras posteriores (use 0 para deshabilitar)

- Requiere un valor

### `--session-save-redis-disable-locking`

Redis desactive el bloqueo. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-min-lifetime`

Duración de la sesión mínima de eliminación, en segundos

- Requiere un valor

### `--session-save-redis-max-lifetime`

Duración máxima de la sesión de Redis, en segundos

- Requiere un valor

### `--session-save-redis-sentinel-master`

Redis Sentinel maestro

- Requiere un valor

### `--session-save-redis-sentinel-servers`

Redis Centinela, servidores separados por comas

- Requiere un valor

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica maestro. Valores: false (predeterminado), true

- Requiere un valor

### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel conecta reintentos.

- Requiere un valor

### `--cache-backend`

Controlador de caché predeterminado

- Requiere un valor

### `--cache-backend-redis-server`

Redis server

- Requiere un valor

### `--cache-backend-redis-db`

Número de base de datos para la caché

- Requiere un valor

### `--cache-backend-redis-port`

Puerto de escucha del servidor de Redis

- Requiere un valor

### `--cache-backend-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--cache-backend-redis-compress-data`

Establézcalo en 0 para desactivar la compresión (el valor predeterminado es 1, activado)

- Requiere un valor

### `--cache-backend-redis-compression-lib`

lib de compresión para usar [snply,lzf,l4z,zstd,gzip] (deje en blanco para determinarlo automáticamente)

- Requiere un valor

### `--cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--allow-parallel-generation`

Permitir generar caché de forma que no se bloquee

- Predeterminado: `false`
- No acepta un valor

### `--page-cache`

Controlador de caché predeterminado

- Requiere un valor

### `--page-cache-redis-server`

Redis server

- Requiere un valor

### `--page-cache-redis-db`

Número de base de datos para la caché

- Requiere un valor

### `--page-cache-redis-port`

Puerto de escucha del servidor de Redis

- Requiere un valor

### `--page-cache-redis-password`

Contraseña del servidor de Redis

- Requiere un valor

### `--page-cache-redis-compress-data`

Configúrelo en 1 para comprimir la caché de página completa (use 0 para deshabilitar)

- Requiere un valor

### `--page-cache-redis-compression-lib`

Biblioteca de compresión que se va a usar [snply,lzf,l4z,zstd,gzip] (deje en blanco para determinarlo automáticamente)

- Requiere un valor

### `--page-cache-id-prefix`

Prefijo de ID para claves de caché

- Requiere un valor

### `--lock-provider`

Bloquear nombre del proveedor

- Requiere un valor

### `--lock-db-prefix`

Prefijo de bloqueo específico de instalación para evitar conflictos de bloqueo

- Requiere un valor

### `--lock-zookeeper-host`

Host y puerto para conectarse al clúster de Zookeeper. Por ejemplo: 127.0.0.1:2181

- Requiere un valor

### `--lock-zookeeper-path`

Ruta donde Zookeeper guardará bloqueos. La ruta predeterminada es: /magento/locks

- Requiere un valor

### `--lock-file-path`

La ruta donde se guardarán los bloqueos de archivo.

- Requiere un valor

### `--document-root-is-pub`

El indicador que se muestra es Pub está en la raíz, puede ser verdadero o falso solo

- Requiere un valor

### `--base-url`

URL en la que se supone que la tienda está disponible. En desuso, utilice config:set con la ruta web/unsecure/base_url

- Requiere un valor

### `--language`

Código de idioma predeterminado. En desuso, utilice config:set con la ruta general/locale/code

- Requiere un valor

### `--timezone`

Código de zona horaria predeterminado. En desuso, utilice config:set con path general/locale/timezone

- Requiere un valor

### `--currency`

Código de moneda predeterminado. En desuso, utilice config:set con ruta de acceso currency/options/base, currency/options/default y currency/options/allow

- Requiere un valor

### `--use-rewrites`

Utilice las reescrituras. En desuso, utilice config:set con la ruta web/seo/use_rewrites

- Requiere un valor

### `--use-secure`

Utilice direcciones URL seguras. Active esta opción solo si SSL está disponible. En desuso, utilice config:set con la ruta web/secure/use_in_frontend

- Requiere un valor

### `--base-url-secure`

Dirección URL base para la conexión SSL. En desuso, utilice config:set con la ruta web/secure/base_url

- Requiere un valor

### `--use-secure-admin`

Ejecute la interfaz de administración con SSL. En desuso, utilice config:set con la ruta web/secure/use_in_adminhtml

- Requiere un valor

### `--admin-use-security-key`

Indica si se utiliza la función &quot;clave de seguridad&quot; en las direcciones URL y los formularios de administración de Magento. En desuso, utilice config:set con la ruta admin/security/use_form_key

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

Apellido del administrador

- Acepta un valor

### `--search-engine`

Motor de búsqueda. Valores: elasticsearch5, elasticsearch6, elasticsearch7

- Requiere un valor

### `--elasticsearch-host`

host del servidor Elasticsearch.

- Requiere un valor

### `--elasticsearch-port`

puerto del servidor Elasticsearch.

- Requiere un valor

### `--elasticsearch-enable-auth`

Configúrelo en 1 para habilitar la autenticación. (el valor predeterminado es 0, desactivado)

- Requiere un valor

### `--elasticsearch-username`

nombre de usuario del Elasticsearch. Solo aplicable si la autenticación HTTP está habilitada

- Requiere un valor

### `--elasticsearch-password`

contraseña de Elasticsearch. Solo aplicable si la autenticación HTTP está habilitada

- Requiere un valor

### `--elasticsearch-index-prefix`

Prefijo de índice del Elasticsearch.

- Requiere un valor

### `--elasticsearch-timeout`

tiempo de espera del servidor Elasticsearch.

- Requiere un valor

### `--cleanup-database`

Limpiar la base de datos antes de la instalación

- Predeterminado: `false`
- No acepta un valor

### `--sales-order-increment-prefix`

Prefijo de número de pedido de venta

- Requiere un valor

### `--use-sample-data`

Usar datos de ejemplo

- Predeterminado: `false`
- No acepta un valor

### `--enable-modules`

Lista de nombres de módulos separados por comas. Esto debe incluirse durante la instalación. Parámetro mágico disponible &quot;todo&quot;.

- Acepta un valor

### `--disable-modules`

Lista de nombres de módulos separados por comas. Esto debe evitarse durante la instalación. Parámetro mágico disponible &quot;todo&quot;.

- Acepta un valor

### `--convert-old-scripts`

Permite convertir secuencias de comandos antiguas (InstallSchema, UpgradeSchema) al formato db_schema.xml

- Predeterminado: `false`
- Acepta un valor

### `--interactive`, `-i`

Instalación del Magento interactivo

- Predeterminado: `false`
- No acepta un valor

### `--safe-mode`

Instalación segura del Magento con volcados en operaciones destructivas, como la eliminación de columnas

- Acepta un valor

### `--data-restore`

Restaurar datos eliminados de los volcados

- Acepta un valor

### `--dry-run`

La instalación del Magento se ejecutará en modo de ejecución en seco

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:performance:generate-fixtures`

Genera fijaciones

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:rollback`

Revierte la base de código de la aplicación Magento, el medio y la base de datos

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

Nombre base del archivo de copia de seguridad de db en var/backups

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:static-content:deploy`

Implementa archivos de vista estáticos

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

Lista separada por espacios de códigos de idioma ISO-639 para los que se pueden generar archivos de vista estáticos.

- Predeterminado: `[]`

- Matriz

### `--force`, `-f`

Implemente archivos en cualquier modo.

- Predeterminado: `false`
- No acepta un valor

### `--strategy`, `-s`

Implementar archivos utilizando la estrategia especificada.

- Predeterminado: `quick`
- Acepta un valor

### `--area`, `-a`

Genere archivos sólo para las áreas especificadas.

- Predeterminado: `all`
- Acepta varios valores

### `--exclude-area`

No genere archivos para las áreas especificadas.

- Predeterminado: `none`
- Acepta varios valores

### `--theme`, `-t`

Genere archivos de vista estáticos solo para los temas especificados.

- Predeterminado: `all`
- Acepta varios valores

### `--exclude-theme`

No genere archivos para los temas especificados.

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

Habilite el procesamiento paralelo con el número especificado de trabajos.

- Predeterminado: `0`
- Acepta un valor

### `--max-execution-time`

El tiempo de ejecución máximo esperado del proceso estático de implementación (en segundos).

- Predeterminado: `900`
- Acepta un valor

### `--symlink-locale`

Cree enlaces simbólicos para los archivos de esas configuraciones regionales, que se pasan para su implementación, pero que no tienen personalizaciones.

- Predeterminado: `false`
- No acepta un valor

### `--content-version`

Se puede utilizar una versión personalizada del contenido estático si se ejecuta la implementación en varios nodos para garantizar que la versión del contenido estático sea idéntica y el almacenamiento en caché funcione correctamente.

- Requiere un valor

### `--refresh-content-version-only`

La actualización de la versión de contenido estático solo se puede utilizar para actualizar contenido estático en la caché del navegador y de la caché de la CDN.

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

No implemente archivos de fuente.

- Predeterminado: `false`
- No acepta un valor

### `--no-html`

No implemente archivos HTML.

- Predeterminado: `false`
- No acepta un valor

### `--no-misc`

No implemente archivos de otros tipos (.md, .jbf, .csv, etc.).

- Predeterminado: `false`
- No acepta un valor

### `--no-html-minify`

No minifique los archivos HTML.

- Predeterminado: `false`
- No acepta un valor

### `--no-parent`

No compile temas principales. Compatible únicamente con estrategias rápidas y estándar.

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:store-config:set`

Instala la configuración de la tienda. Obsoleto desde 2.2.0. Use config:set en su lugar

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

URL en la que se supone que la tienda está disponible. En desuso, utilice config:set con la ruta web/unsecure/base_url

- Requiere un valor

### `--language`

Código de idioma predeterminado. En desuso, utilice config:set con la ruta general/locale/code

- Requiere un valor

### `--timezone`

Código de zona horaria predeterminado. En desuso, utilice config:set con path general/locale/timezone

- Requiere un valor

### `--currency`

Código de moneda predeterminado. En desuso, utilice config:set con ruta de acceso currency/options/base, currency/options/default y currency/options/allow

- Requiere un valor

### `--use-rewrites`

Utilice las reescrituras. En desuso, utilice config:set con la ruta web/seo/use_rewrites

- Requiere un valor

### `--use-secure`

Utilice direcciones URL seguras. Active esta opción solo si SSL está disponible. En desuso, utilice config:set con la ruta web/secure/use_in_frontend

- Requiere un valor

### `--base-url-secure`

Dirección URL base para la conexión SSL. En desuso, utilice config:set con la ruta web/secure/base_url

- Requiere un valor

### `--use-secure-admin`

Ejecute la interfaz de administración con SSL. En desuso, utilice config:set con la ruta web/secure/use_in_adminhtml

- Requiere un valor

### `--admin-use-security-key`

Indica si se utiliza la función &quot;clave de seguridad&quot; en las direcciones URL y los formularios de administración de Magento. En desuso, utilice config:set con la ruta admin/security/use_form_key

- Requiere un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:uninstall`

Desinstala la aplicación Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `setup:upgrade`

Actualiza la aplicación de Magento, los datos de base de datos y el esquema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

Evita que se eliminen los archivos generados. Se desaconseja utilizar esta opción excepto al implementar en producción. Para obtener más información, consulte con el integrador o administrador del sistema.

- Predeterminado: `false`
- No acepta un valor

### `--convert-old-scripts`

Permite convertir secuencias de comandos antiguas (InstallSchema, UpgradeSchema) al formato db_schema.xml

- Predeterminado: `false`
- Acepta un valor

### `--safe-mode`

Instalación segura del Magento con volcados en operaciones destructivas, como la eliminación de columnas

- Acepta un valor

### `--data-restore`

Restaurar datos eliminados de los volcados

- Acepta un valor

### `--dry-run`

La instalación del Magento se ejecutará en modo de ejecución en seco

- Predeterminado: `false`
- Acepta un valor

### `--magento-init-params`

Añada a cualquier comando para personalizar los parámetros de inicialización del Magento. Por ejemplo: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `store:list`

Muestra la lista de tiendas

```bash
bin/magento store:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `store:website:list`

Muestra la lista de sitios web

```bash
bin/magento store:website:list
```

### `--help`, `-h`

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `support:backup:code`

Crear copia de seguridad de código

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

Nombre de volcado

- Acepta un valor

### `--output`, `-o`

Ruta de salida

- Acepta un valor

### `--logs`, `-l`

Incluir registros

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `support:backup:db`

Crear copia de seguridad de base de datos

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

Nombre de volcado

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `support:utility:check`

Comprobar las utilidades de copia de seguridad necesarias

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

Compruebe únicamente las utilidades de consola requeridas

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `support:utility:paths`

Crear lista de rutas de utilidades

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

Fuerza

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

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

Realizar copia de seguridad de código (excepto archivos temporales)

- Predeterminado: `false`
- No acepta un valor

### `--clear-static-content`, `-c`

Borre los archivos de vista estáticos generados.

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

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor


## `varnish:vcl:generate`

Genera VCL de barniz y la hace eco en la línea de comandos

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

Lista de acceso de direcciones IP que puede depurar Varnish

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

Mostrar este mensaje de ayuda

- Predeterminado: `false`
- No acepta un valor

### `--quiet`, `-q`

No mostrar ningún mensaje

- Predeterminado: `false`
- No acepta un valor

### `--verbose`, `-v|-vv|-vvv`

Aumente la diversidad de los mensajes: 1 para la salida normal, 2 para la salida más detallada y 3 para la depuración

- Predeterminado: `false`
- No acepta un valor

### `--version`, `-V`

Mostrar esta versión de la aplicación

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

### `--no-interaction`, `-n`

No hacer ninguna pregunta interactiva

- Predeterminado: `false`
- No acepta un valor
