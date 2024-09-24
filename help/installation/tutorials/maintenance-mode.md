---
title: Habilitar o deshabilitar el modo de mantenimiento
description: Siga estos pasos para personalizar lo que los clientes ven cuando la implementación de Adobe Commerce está inactiva por motivos de mantenimiento.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Habilitar o deshabilitar el modo de mantenimiento

La siguiente guía hace referencia a una página de modo de mantenimiento estándar. Si necesita usar una página de mantenimiento personalizada, consulte [Crear la página de mantenimiento personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md).

Adobe Commerce usa [modo de mantenimiento](../../configuration/bootstrap/application-modes.md#maintenance-mode) para deshabilitar el arranque. Deshabilitar el arranque resulta útil mientras mantiene, actualiza o vuelve a configurar el sitio.

La aplicación detecta el modo de mantenimiento de la siguiente manera:

* Si existe `var/.maintenance.flag`, el modo de mantenimiento está activado y la aplicación devolverá una página de mantenimiento 503.
* Si `var/.maintenance.ip` existe y la dirección IP del cliente corresponde a una de las entradas de dirección IP de este archivo, se omite la página de mantenimiento de la solicitud.

## Instalación de la aplicación

Antes de usar este comando para habilitar o deshabilitar el modo de mantenimiento, debe [instalar la aplicación](../advanced.md).

## Habilitar o deshabilitar el modo de mantenimiento

Utilice el comando CLI `magento maintenance` para habilitar o deshabilitar el modo de mantenimiento.

Uso de comandos:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

La opción `--ip=<ip address>` es una dirección IP que se excluirá del modo de mantenimiento (por ejemplo, los desarrolladores que realizan el mantenimiento). Para eximir más de una dirección IP en el mismo comando, utilice la opción varias veces.

>[!NOTE]
>
>Al usar `--ip=<ip address>` con `magento maintenance:disable` se guarda la lista de direcciones IP para su uso posterior. Para borrar la lista de direcciones IP exentas, use `magento maintenance:enable --ip=none` o consulte [Mantener la lista de direcciones IP exentas](#maintain-the-list-of-exempt-ip-addresses).

El comando `bin/magento maintenance:status` muestra el estado del modo de mantenimiento.

Por ejemplo, para habilitar el modo de mantenimiento sin excepciones de dirección IP:

```bash
bin/magento maintenance:enable
```

Para habilitar el modo de mantenimiento para todos los clientes excepto 192.0.2.10 y 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Después de colocar la aplicación en modo de mantenimiento, debe detener todos los procesos del consumidor de la cola de mensajes.
Una forma de encontrar estos procesos es ejecutar el comando `ps -ef | grep queue:consumers:start` y, a continuación, ejecutar el comando `kill <process_id>` para cada consumidor. En un entorno de varios nodos, repita esta tarea en cada nodo.

## Mantener la lista de direcciones IP exentas

Para mantener la lista de direcciones IP exentas, puede utilizar la opción `[--ip=<ip list>]` en los comandos anteriores o puede utilizar lo siguiente:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

La sintaxis `<ip address> .. <ip address>` es una lista opcional delimitada por espacios de direcciones IP que se deben eximir.

La opción `--none` borra la lista.

## Configuraciones de varias tiendas

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Si desea configurar varias tiendas, cada una con un diseño y contenido localizados diferentes, pase el parámetro `$_GET['skin']` al procesador deseado.

En el ejemplo siguiente, se usa un archivo de plantilla de error de tipo `503`, que requiere contenido localizado.

El constructor de la clase `Error_Processor` acepta un parámetro de GET `skin` para cambiar el diseño:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Esto también se puede agregar a una regla de reescritura en el archivo `.htaccess` que anexa un parámetro `skin` a la dirección URL.

### Parámetro $_GET[&#39;skin&#39;]

Para usar el parámetro `skin`:

1. Compruebe si `.maintenance.flag` existe.
1. Observe la dirección de host, que hace referencia a `HTTP_HOST`, o cualquier otra variable como las variables ENV.
1. Compruebe si el parámetro `skin` existe.
1. Defina el parámetro utilizando las reglas de reescritura a continuación.

   Estos son algunos ejemplos de reglas de reescritura:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copie los siguientes archivos:

   * `pub/errors/default/503.phtml` a `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` a `pub/errors/sub/styles.css`

1. Edite estos archivos para proporcionar contenido localizado en el archivo `503.phtml` y estilo personalizado en el archivo `styles.css`.

   Asegúrese de que las rutas apunten al directorio `errors`. El nombre de directorio debe coincidir con el parámetro de URL indicado en `RewriteRule`. En el ejemplo anterior, se usa el directorio `sub`, que se especifica como parámetro en `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>Se debe agregar la configuración [nginx](../../configuration/multi-sites/ms-nginx.md) para las configuraciones de varias tiendas.
