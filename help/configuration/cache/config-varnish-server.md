---
title: Configuración de nginx para el almacenamiento en caché de barniz
description: Aprenda a configurar el servidor web para que funcione con el almacenamiento en caché de Varnish para Adobe Commerce. Descubra los requisitos de configuración e instalación de puertos.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T21:49:41.837Z'
TQID: 'https://experienceleague.adobe.com/0vOg86gRkST8CZGhdIESzhld63HQ5IUlO4go-Hgw9Xs'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: c8faa589c9e9d1dbc01863d90aad5f91b11c0140
workflow-type: tm+mt
source-wordcount: 806
ht-degree: 0%

---

# Configuración de nginx para el almacenamiento en caché de Varnish {#configure-web-server-for-varnish-caching}

Cuando Varnish se utiliza como caché de página completa delante de Adobe Commerce, Varnish generalmente escucha en el puerto HTTP público y reenvía solicitudes a nginx en un puerto back-end no predeterminado como 8080. Actualice la configuración del sitio nginx para su servidor de origen de Commerce para escuchar en el puerto back-end que utilizará Varnish.

{{varnish-config-cloud}}

Las siguientes secciones utilizan el puerto 8080 como ejemplo.

**Cambiar el puerto de escucha nginx para el servidor de origen de Commerce**:

1. Abra la configuración del sitio de nginx para su servidor de origen de Adobe Commerce en un editor de texto.

La ubicación depende del sistema operativo y del diseño de nginx. Por ejemplo, Ubuntu usa a menudo un archivo bajo `/etc/nginx/sites-available/`.

1. En el bloque `server` para el sitio Commerce, cambie la directiva `listen` del puerto HTTP público al puerto back-end que Varnish usará para llegar a nginx.

   Por ejemplo, cambie

   ```conf
   server {
       listen 80;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   hasta:

   ```conf
   server {
       listen 8080;
       server_name example.com;
       root /var/www/html/magento2;
       include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

1. Guarde el archivo.

1. Compruebe la configuración de nginx:

   ```shell
   nginx -t
   ```

1. Reiniciar nginx:

   ```shell
   systemctl restart nginx
   ```

## Modifique la configuración del sistema de barniz

Después de actualizar nginx para escuchar en el puerto back-end, configure Varnish para reenviar solicitudes a ese host y puerto. Por ejemplo:

```conf
backend default {
    .host = "192.0.2.55";
    .port = "8080";
}
```

### Modificación del VCL predeterminado

En esta sección se explica cómo proporcionar una configuración mínima para que Varnish devuelva encabezados de respuesta HTTP. Esto le permite comprobar que Varnish funciona antes de configurar la aplicación [!DNL Commerce] para que use Varnish.

Para configurar mínimamente el barniz:

1. Copia de seguridad de `default.vcl`:

   ```shell
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

   Ejemplo: nginx está instalado en el host 192.0.2.55 y escucha en el puerto 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Si Varnish y nginx se ejecutan en el mismo host, Adobe recomienda que utilice una dirección IP o un nombre de host y no `localhost`.

1. Guarde los cambios en `default.vcl` y salga del editor de texto.

1. Reiniciar barniz:

   ```shell
   service varnish restart
   ```

Si Varnish no se inicia, intente ejecutarlo desde la línea de comandos de la siguiente manera:

```shell
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
- [`netstat`](#netstat)

### Barniz inicial

Escriba: `service varnish start`

Si Varnish no puede iniciarse como servicio, inícielo desde la línea de comandos de la siguiente manera:

1. Inicie la CLI de barniz:

   ```shell
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Iniciar el proceso secundario Barniz:

   Cuando se le solicite, escriba `start`

   Se muestran los siguientes mensajes para confirmar que el inicio se ha realizado correctamente:

   ```text
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Inicie sesión en el servidor de Varnish e introduzca el siguiente comando:

```shell
netstat -tulpn
```

Busque el siguiente resultado en particular:

```text
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/nginx
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

La anterior muestra Varnish ejecutándose en el puerto 80 y nginx ejecutándose en el puerto 8080.

Si no ve el resultado de `varnishd`, asegúrese de que Varnish se esté ejecutando.

Ver [`netstat` opciones](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Instalación del software de Commerce

Instale el software de Commerce si aún no lo ha hecho. Cuando se le pida una URL base, utilice el host Varnish y el puerto 80 (para Varnish) porque Varnish recibe todas las solicitudes HTTP entrantes.

Posible error al instalar Commerce:

```text
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

```shell
varnishlog
```

En un explorador web, vaya a cualquier página de Commerce.

Se muestra una larga lista de encabezados de respuesta en la ventana del símbolo del sistema. Busque encabezados como los siguientes:

```text
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

```shell
curl -I -v --location-trusted '<your Commerce base URL>'
```

Por ejemplo,

```shell
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Busque encabezados como los siguientes:

```text
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
