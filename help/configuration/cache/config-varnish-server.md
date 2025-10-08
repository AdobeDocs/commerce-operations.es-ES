---
title: Configuración del servidor web
description: Aprenda a configurar el servidor web para que funcione con el almacenamiento en caché de Varnish para Adobe Commerce. Descubra los requisitos de configuración e instalación de puertos.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Configuración del servidor web

Configure el servidor web para que escuche en un puerto que no sea el puerto predeterminado 80, ya que Varnish responde directamente a las solicitudes HTTP entrantes, no al servidor web.

Las siguientes secciones utilizan el puerto 8080 como ejemplo.

**Para cambiar el puerto de escucha Apache 2.4**:

1. Abra `/etc/httpd/conf/httpd.conf` en un editor de texto.
1. Busque la directiva `Listen`.
1. Cambie el valor del puerto de escucha a `8080`. (Puede utilizar cualquier puerto de escucha disponible).
1. Guarde los cambios en `httpd.conf` y salga del editor de texto.

## Modifique la configuración del sistema de barniz

Para modificar la configuración del sistema de barniz:

1. Como usuario con privilegios de `root`, abra el archivo de configuración de Desvanecer en un editor de texto:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Establezca el puerto de escucha de barniz en 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Para Varnish 4.x, asegúrese de que DAEMON_OPTS contiene el puerto de escucha correcto para el parámetro `-a` (incluso si VARNISH_LISTEN_PORT está establecido en el valor correcto):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Guarde los cambios en el fichero de configuración de Barniz y salga del editor de texto.

### Modificación del VCL predeterminado

En esta sección se explica cómo proporcionar una configuración mínima para que Varnish devuelva encabezados de respuesta HTTP. Esto le permite comprobar que Varnish funciona antes de configurar la aplicación [!DNL Commerce] para que use Varnish.

Para configurar mínimamente el barniz:

1. Copia de seguridad de `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Abra `/etc/varnish/default.vcl` en un editor de texto.
1. Busque la siguiente estrofa:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Reemplace el valor de `.host` por el nombre de host o la dirección IP completos y el puerto de escucha del servidor Varnish _backend_ o _origin server_; es decir, el servidor que proporciona el contenido que Varnish acelerará.

   Normalmente, es su servidor web. Consulte [Servidores back-end](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) en la _guía de barniz_.

1. Reemplace el valor de `.port` por el puerto de escucha del servidor web (8080 en este ejemplo).

   Ejemplo: Apache está instalado en el host 192.0.2.55 y Apache está escuchando en el puerto 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Si Varnish y Apache se están ejecutando en el mismo host, Adobe recomienda que utilice una dirección IP o un nombre de host y no `localhost`.

1. Guarde los cambios en `default.vcl` y salga del editor de texto.

1. Reiniciar barniz:

   ```bash
   service varnish restart
   ```

Si Varnish no se inicia, intente ejecutarlo desde la línea de comandos de la siguiente manera:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Esto debería mostrar mensajes de error.


>[!INFO]
>
>Si Varnish no se inicia como un servicio, debe configurar las reglas de SELinux para permitir que se ejecute.

## Verificar que el barniz funcione

En las secciones siguientes se explica cómo comprobar que Varnish funciona pero _sin_ configurar Commerce para usarlo. Debe intentarlo antes de configurar Commerce.

Realice las tareas descritas en las siguientes secciones en el orden mostrado:

- [Barniz inicial](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Barniz inicial

Escriba: `service varnish start`

Si Varnish no puede iniciarse como servicio, inícielo desde la línea de comandos de la siguiente manera:

1. Inicie la CLI de barniz:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Iniciar el proceso secundario Barniz:

   Cuando se le solicite, escriba `start`

   Se muestran los siguientes mensajes para confirmar que el inicio se ha realizado correctamente:

   ```
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Inicie sesión en el servidor de Varnish e introduzca el siguiente comando:

```bash
netstat -tulpn
```

Busque el siguiente resultado en particular:

```
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

El anterior muestra Varnish ejecutándose en el puerto 80 y Apache ejecutándose en el puerto 8080.

Si no ve el resultado de `varnishd`, asegúrese de que Varnish se esté ejecutando.

Ver [`netstat` opciones](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Instalación del software de Commerce

Instale el software de Commerce si aún no lo ha hecho. Cuando se le pida una URL base, utilice el host Varnish y el puerto 80 (para Varnish) porque Varnish recibe todas las solicitudes HTTP entrantes.

Posible error al instalar Commerce:

```
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Si experimenta este error, edite `default.vcl` y agregue un tiempo de espera a la estrofa `backend` de la siguiente manera:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificar encabezados de respuesta HTTP

Ahora puede comprobar que Varnish sirve páginas mirando los encabezados de respuesta de HTML devueltos desde cualquier página.

Para poder ver los encabezados, debe establecer Commerce para el modo de desarrollador. Hay varias formas de hacerlo, la más sencilla de las cuales es modificar `.htaccess` en la raíz de la aplicación de Commerce. También puede usar el comando [`magento deploy:mode:set`](../cli/set-mode.md).

### Definir Commerce para el modo de desarrollador

Para establecer Commerce para el modo de desarrollador, use el comando [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode).

### Mira el registro de barniz

Asegúrese de que Varnish se está ejecutando e introduzca el siguiente comando en el servidor Varnish:

```bash
varnishlog
```

En un explorador web, vaya a cualquier página de Commerce.

Se muestra una larga lista de encabezados de respuesta en la ventana del símbolo del sistema. Busque encabezados como los siguientes:

```
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

Si se muestran encabezados como este _no_, detenga Varnish, compruebe su `default.vcl` y vuelva a intentarlo.

### Consulte los encabezados de respuesta de HTML

Existen varias formas de ver los encabezados de respuesta, incluido el uso de un complemento del explorador o un inspector del explorador.

El ejemplo siguiente utiliza `curl`. Puede introducir este comando desde cualquier equipo que pueda acceder al servidor de Commerce mediante HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Por ejemplo,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Busque encabezados como los siguientes:

```
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
