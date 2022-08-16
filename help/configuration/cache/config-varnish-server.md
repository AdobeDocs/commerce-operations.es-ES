---
title: Configuración del servidor web
description: Aprenda a configurar su servidor web para que funcione con Varnish.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# Configuración del servidor web

Configure el servidor web para que escuche en un puerto que no sea el puerto predeterminado 80, ya que Varnish responde directamente a las solicitudes HTTP entrantes, no al servidor web.

Las secciones siguientes utilizan el puerto 8080 como ejemplo.

**Para cambiar el puerto de escucha de Apache 2.4**:

1. Apertura `/etc/httpd/conf/httpd.conf` en un editor de texto.
1. Busque la variable `Listen` directiva.
1. Cambiar el valor del puerto de escucha a `8080`. (Puede utilizar cualquier puerto de escucha disponible).
1. Guarde los cambios en `httpd.conf` y salga del editor de texto.

## Modificación de la configuración del sistema de Varnish

Para modificar la configuración del sistema de Varnish:

1. Como usuario con `root` privilegios, abra el archivo de configuración de Vanish en un editor de texto:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Ajuste el puerto de escucha de Varnish a 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Para Varnish 4.x, asegúrese de que DAEMON_OPTS contiene el puerto de escucha correcto para la variable `-a` (incluso si VARNISH_LISTEN_PORT está establecido en el valor correcto):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Guarde los cambios en el archivo de configuración de Varnish y salga del editor de texto.

### Modificación de la VCL predeterminada

En esta sección se explica cómo proporcionar una configuración mínima para que Varnish devuelva encabezados de respuesta HTTP. Esto le permite verificar que Varnish funciona antes de configurar la variable [!DNL Commerce] para usar Varnish.

Para configurar Varnish de forma mínima:

1. Copia de seguridad `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Apertura `/etc/varnish/default.vcl` en un editor de texto.
1. Busque la siguiente configuración:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Reemplace el valor de `.host` con el nombre de host o la dirección IP completa y el puerto de escucha de Varnish _backend_ o _servidor de origen_; es decir, el servidor que proporciona el contenido Varnish se acelerará.

   Normalmente, este es su servidor web. Consulte [Servidores back-end](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) en el _Guía de barniz_.

1. Reemplace el valor de `.port` con el puerto de escucha del servidor web (8080 en este ejemplo).

   Ejemplo: Apache está instalado en el host 192.0.2.55 y Apache está escuchando en el puerto 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Si Varnish y Apache se ejecutan en el mismo host, Adobe recomienda que use una dirección IP o un nombre de host y no `localhost`.

1. Guarde los cambios en `default.vcl` y salga del editor de texto.

1. Reinicie Varnish:

   ```bash
   service varnish restart
   ```

Si Varnish no puede iniciar, intente ejecutarlo desde la línea de comandos de la siguiente manera:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Esto debería mostrar mensajes de error.


>[!INFO]
>
>Si Varnish no comienza como un servicio, debe configurar las reglas de SELinux para permitir que se ejecuten.

## Verificar que Varniz funcione

Las secciones siguientes describen cómo puede verificar que Varnish está funcionando pero _without_ configurar Commerce para usarlo. Debe intentarlo antes de configurar Commerce.

Realice las tareas descritas en las secciones siguientes en el orden mostrado:

- [Iniciar barniz](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Iniciar barniz

Escriba: `service varnish start`

Si Varnish no puede iniciarse como un servicio, inícielo desde la línea de comandos de la siguiente manera:

1. Inicie la CLI de Varnish:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Inicie el proceso secundario de Varnish:

   Cuando se le pida, introduzca `start`

   Se muestran los siguientes mensajes para confirmar que el inicio se ha realizado correctamente:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Inicie sesión en el servidor Varnish e introduzca el siguiente comando:

```bash
netstat -tulpn
```

Busque la siguiente salida en particular:

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

El anterior muestra a Varnish corriendo en el puerto 80 y a Apache en el puerto 8080.

Si no ve la salida para `varnishd`, asegúrese de que Varnish se está ejecutando.

Consulte [`netstat` opciones](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Instalación del software Commerce

Instale el software Commerce si aún no lo ha hecho. Cuando se le pida una URL base, utilice el host y el puerto 80 de Varnish (para Varniz) porque Varniz recibe todas las solicitudes HTTP entrantes.

Posible error al instalar Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Si experimenta este error, edite `default.vcl` y agregue un tiempo de espera a la variable `backend` stanza como sigue:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificar encabezados de respuesta HTTP

Ahora puede verificar que Varnish esté sirviendo páginas mirando [HTML](https://glossary.magento.com/html) encabezados de respuesta devueltos desde cualquier página.

Para poder ver los encabezados, debe establecer Commerce para el modo de desarrollador. Hay varias formas de hacerlo, la más sencilla de las cuales es modificar `.htaccess` en la raíz de la aplicación Commerce. También puede usar la variable [`magento deploy:mode:set`](../cli/set-mode.md) comando.

### Establecer Commerce para el modo de desarrollador

Para establecer el modo de Commerce for developer , use la variable [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) comando.

### Mira el tronco de Varniz

Asegúrese de que Varnish se esté ejecutando e introduzca el siguiente comando en el servidor Varnish:

```bash
varnishlog
```

En un explorador web, vaya a cualquier página de comercio.

Se muestra una larga lista de encabezados de respuesta en la ventana del símbolo del sistema. Busque encabezados como los siguientes:

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Si encabezados como estos _not_ visualice, detenga Varnish, compruebe su `default.vcl`y vuelva a intentarlo.

### Observe los encabezados de respuesta del HTML

Existen varias formas de ver los encabezados de respuesta, incluido el uso de un explorador [complemento](https://glossary.magento.com/plug-in) o un inspector del navegador.

El siguiente ejemplo utiliza `curl`. Puede introducir este comando desde cualquier equipo que pueda acceder al servidor de comercio mediante HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Por ejemplo,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Busque encabezados como los siguientes:

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```