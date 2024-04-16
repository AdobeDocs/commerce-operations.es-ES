---
title: Habilitar o deshabilitar el modo de mantenimiento
description: Siga estos pasos para personalizar lo que ven los clientes cuando la implementación de Adobe Commerce o de Magento Open Source está inactiva por motivos de mantenimiento.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Habilitar o deshabilitar el modo de mantenimiento

La siguiente guía hace referencia a una página de modo de mantenimiento estándar. Si necesita utilizar una página de mantenimiento personalizada, consulte [Creación de la página de mantenimiento personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md) tema.

Adobe Commerce utiliza [modo de mantenimiento](../../configuration/bootstrap/application-modes.md#maintenance-mode) para deshabilitar el bootstrapping. Deshabilitar el arranque resulta útil mientras mantiene, actualiza o vuelve a configurar el sitio.

La aplicación detecta el modo de mantenimiento de la siguiente manera:

* If `var/.maintenance.flag` no existe, el modo de mantenimiento está desactivado y la aplicación funciona normalmente.
* De lo contrario, el modo de mantenimiento está activado a menos que `var/.maintenance.ip` existe.

  `var/.maintenance.ip` puede contener una lista de direcciones IP. Si se accede a un punto de entrada mediante HTTP y la dirección IP del cliente corresponde a una de las entradas de esa lista, el modo de mantenimiento está desactivado.

## Instalación de la aplicación

Antes de utilizar este comando para activar o desactivar el modo de mantenimiento, debe [instalar la aplicación](../advanced.md).

## Habilitar o deshabilitar el modo de mantenimiento

Utilice el `magento maintenance` Comando CLI para habilitar o deshabilitar el modo de mantenimiento.

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

El `--ip=<ip address>` es una dirección IP que se excluirá del modo de mantenimiento (por ejemplo, los desarrolladores que realizan el mantenimiento). Para eximir más de una dirección IP en el mismo comando, utilice la opción varias veces.

>[!NOTE]
>
>Uso de `--ip=<ip address>` con `magento maintenance:disable` guarda la lista de direcciones IP para su uso posterior. Para borrar la lista de direcciones IP exentas, utilice `magento maintenance:enable --ip=none` o consulte [Mantener la lista de direcciones IP exentas](#maintain-the-list-of-exempt-ip-addresses).

El `bin/magento maintenance:status` muestra el estado del modo de mantenimiento.

Por ejemplo, para habilitar el modo de mantenimiento sin excepciones de dirección IP:

```bash
bin/magento maintenance:enable
```

Para habilitar el modo de mantenimiento para todos los clientes excepto 192.0.2.10 y 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Después de colocar la aplicación en modo de mantenimiento, debe detener todos los procesos del consumidor de la cola de mensajes.
Una forma de encontrar estos procesos es ejecutar el `ps -ef | grep queue:consumers:start` y, a continuación, ejecute el `kill <process_id>` para cada consumidor. En un entorno de varios nodos, repita esta tarea en cada nodo.

## Mantener la lista de direcciones IP exentas

Para mantener la lista de direcciones IP exentas, puede utilizar el complemento `[--ip=<ip list>]` en los comandos anteriores o puede utilizar lo siguiente:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

El `<ip address> .. <ip address>` La sintaxis es una lista opcional delimitada por espacios de direcciones IP que se deben eximir.

El `--none` borra la lista.

## Configuraciones de varias tiendas

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Si desea configurar varias tiendas, cada una con un diseño y contenido localizados diferentes, pase el `$_GET['skin']` al procesador deseado.

En el siguiente ejemplo, se utiliza un `503` escriba el archivo de plantilla de error, que requiere contenido localizado.

El constructor de `Error_Processor` La clase acepta un `skin` Parámetro de GET para cambiar el diseño:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Esto también se puede añadir a una regla de reescritura en `.htaccess` archivo que anexa un `skin` a la dirección URL.

### $_GET[&#39;piel&#39;] parámetro

Para usar la variable `skin` parámetro:

1. Compruebe si la variable `.maintenance.flag` existe.
1. Tenga en cuenta la dirección de host que hace referencia a `HTTP_HOST`o cualquier otra variable, como las variables ENV.
1. Compruebe si la variable `skin` el parámetro existe.
1. Defina el parámetro utilizando las reglas de reescritura a continuación.

   Estos son algunos ejemplos de reglas de reescritura:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copie los siguientes archivos:

   * `pub/errors/default/503.phtml` hasta `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` hasta `pub/errors/sub/styles.css`

1. Edite estos archivos para proporcionar contenido localizado en `503.phtml` archivo y estilo personalizado en la `styles.css` archivo.

   Asegúrese de que las rutas apuntan a su `errors` directorio. El nombre de directorio debe coincidir con el parámetro de URL indicado en la variable `RewriteRule`. En el ejemplo anterior, la variable `sub` se utiliza, que se especifica como parámetro en la variable `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>El [nginx](../../configuration/multi-sites/ms-nginx.md) se debe agregar la configuración para las configuraciones de varias tiendas.
