---
title: Habilitar o deshabilitar el modo de mantenimiento
description: Siga estos pasos para personalizar lo que los clientes ven cuando su implementación de Adobe Commerce o Magento Open Source está inactiva para realizar tareas de mantenimiento.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---


# Habilitar o deshabilitar el modo de mantenimiento

La siguiente guía hace referencia a una página de modo de mantenimiento estándar. Si necesita utilizar una página de mantenimiento personalizada, consulte [Crear la página de mantenimiento personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md) tema.

Uso de Adobe Commerce y Magento Open Source [modo de mantenimiento](../../configuration/bootstrap/application-modes.md#maintenance-mode) para desactivar el arranque. Deshabilitar el inicio es útil mientras mantiene, actualiza o reconfigura el sitio.

La aplicación detecta el modo de mantenimiento de la siguiente manera:

* If `var/.maintenance.flag` no existe, el modo de mantenimiento está desactivado y la aplicación funciona normalmente.
* De lo contrario, el modo de mantenimiento estará activado a menos que `var/.maintenance.ip` existe.

   `var/.maintenance.ip` puede contener una lista de direcciones IP. Si se accede a un punto de entrada mediante HTTP y la dirección IP del cliente corresponde a una de las entradas de esa lista, el modo de mantenimiento está desactivado.

## Instalación de la aplicación

Antes de utilizar este comando para habilitar o deshabilitar el modo de mantenimiento, debe [instalar la aplicación](../advanced.md).

## Habilitar o deshabilitar el modo de mantenimiento

Utilice la variable `magento maintenance` Comando CLI para habilitar o deshabilitar el modo de mantenimiento.

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

La variable `--ip=<ip address>` es una dirección IP que se exime del modo de mantenimiento (por ejemplo, los desarrolladores que realizan el mantenimiento). Para eximir más de una dirección IP en el mismo comando, utilice la opción varias veces.

>[!NOTE]
>
>Uso `--ip=<ip address>` con `magento maintenance:disable` guarda la lista de direcciones IP para su uso posterior. Para borrar la lista de IP exentas, utilice `magento maintenance:enable --ip=none` o consulte [Mantener la lista de direcciones IP exentas](#maintain-the-list-of-exempt-ip-addresses).

La variable `bin/magento maintenance:status` muestra el estado del modo de mantenimiento.

Por ejemplo, para habilitar el modo de mantenimiento sin exenciones de direcciones IP:

```bash
bin/magento maintenance:enable
```

Para habilitar el modo de mantenimiento para todos los clientes excepto 192.0.2.10 y 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Después de colocar la aplicación en modo de mantenimiento, debe detener todos los procesos de consumidores de la cola de mensajes.
Una forma de encontrar estos procesos es ejecutar el `ps -ef | grep queue:consumers:start` y luego ejecute el `kill <process_id>` para cada consumidor. En un entorno de varios nodos, repita esta tarea en cada nodo.

## Mantener la lista de direcciones IP exentas

Para mantener la lista de direcciones IP exentas, puede usar la variable `[--ip=<ip list>]` en los comandos anteriores o puede utilizar lo siguiente:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

La variable `<ip address> .. <ip address>` es una lista opcional delimitada por espacios de direcciones IP que se van a excluir.

La variable `--none` borra la lista.

## Configuración de varias tiendas

Para configurar varias tiendas, cada una con un diseño diferente y contenido localizado, cree un aspecto para cada una y configúrelo en `pub/errors/{name}` donde `{name}` es el código de tienda. Para distinguir entre tiendas y sitios web con la misma instancia, utilice `pub/errors/{type}-{name}` donde `{type}` es `store` o `website` y coincide con la variable `MAGE_RUN_TYPE` en la configuración del servidor.

Otra opción es pasar la variable `$_GET['skin']` al procesador deseado. Este método requiere una configuración específica en el servidor.

En el ejemplo siguiente, se usa un `503` escriba el archivo de plantilla de error, que requiere contenido localizado.

El constructor de la variable `Error_Processor` la clase acepta `skin` parámetro de GET para cambiar el diseño:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Esto también se puede agregar a una regla de reescritura en el `.htaccess` archivo que adjunta un `skin` a la dirección URL.

### $_GET[&#39;piel&#39;] parameter

Para usar la variable `skin` parámetro:

1. Compruebe si la variable `.maintenance.flag` existe.
1. Tenga en cuenta la dirección de host que hace referencia a la variable `HTTP_HOST`, o cualquier otra variable como variables ENV.
1. Compruebe si la variable `skin` existe.
1. Establezca el parámetro utilizando las siguientes reglas de reescritura.

   A continuación se muestran algunos ejemplos de reglas de reescritura:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copie los siguientes archivos:

   * `pub/errors/default/503.phtml` a `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` a `pub/errors/sub/styles.css`

1. Edite estos archivos para proporcionar contenido localizado en el `503.phtml` y estilo personalizado en la variable `styles.css` archivo.

   Asegúrese de que las rutas apunten a su `errors` directorio. El nombre del directorio debe coincidir con el parámetro de URL indicado en la variable `RewriteRule`. En el ejemplo anterior, la variable `sub` se utiliza, que se especifica como parámetro en la variable `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>La variable [nginx](../../configuration/multi-sites/ms-nginx.md) debe agregarse para las configuraciones de varias tiendas.
