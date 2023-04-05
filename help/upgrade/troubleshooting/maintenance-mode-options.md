---
title: Opciones del modo de mantenimiento para la actualización
description: Cree una página de modo de mantenimiento personalizado que sus clientes vean en su tienda de Adobe Commerce o Magento Open Source mientras ejecuta una actualización.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Opciones del modo de mantenimiento para la actualización

En este tema se explica cómo crear una página de mantenimiento personalizada para que se muestre a los usuarios mientras se actualiza la aplicación de Magento. La creación de una página personalizada es opcional, pero se recomienda porque el sitio es accesible durante parte de la actualización.

La creación de una página personalizada a la cual redirigir a los usuarios impide el acceso al sitio y también informa a los usuarios de que el sitio se está manteniendo.

>[!NOTE]
>
>Debe realizar las tareas de esta sección como usuario con `root` privilegios. Las páginas de mantenimiento personalizadas no se pueden configurar en el modo de desarrollador.

## Crear la página de mantenimiento personalizada

Para crear una página de mantenimiento y redirigirla, cree primero una página de mantenimiento con el nombre:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

Añada el siguiente contenido:

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Página de mantenimiento personalizada para Apache

En esta sección se explica cómo crear una página de mantenimiento personalizada y cómo redirigir el tráfico a ella.

El ejemplo de esta sección muestra cómo modificar los siguientes archivos, que es una forma de configurar la página de mantenimiento:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

Para redirigir el tráfico a una página de mantenimiento personalizada:

1. Actualice la configuración de Apache para hacer lo siguiente:

   - Redireccionar todo el tráfico a la página de mantenimiento
   - Lista de permitidos ciertas IP para que un administrador pueda actualizar el software del Magento.

   El siguiente ejemplo lista de permitidos 192.0.2.110.

   Añada lo siguiente al final del archivo de configuración de Apache:

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Reinicie Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Introduzca el siguiente comando:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [Actualizar el sistema](../implementation/perform-upgrade.md).
1. Pruebe el sitio para asegurarse de que funciona correctamente.
1. Una vez completada la actualización, elimine `maintenance.enable`.

## Página de mantenimiento personalizada para nginx

En esta sección se explica cómo crear una página de mantenimiento personalizada y cómo redirigir el tráfico a ella.

Para redirigir el tráfico a una página de mantenimiento personalizada:

1. Utilice un editor de texto para abrir el archivo de configuración nginx que contiene el bloque del servidor.
1. Agregue lo siguiente al bloque de servidor (`server` se muestra únicamente para la claridad; no agregue un segundo bloque de servidor).

   Las siguientes listas de permitidos son las direcciones IP 192.0.2.110 y 192.0.2.115 de un sistema en el que el Magento está instalado en `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Introduzca el siguiente comando:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Vuelva a cargar la configuración de nginx:

   ```bash
   service nginx reload
   ```

1. [Actualizar el sistema](../implementation/perform-upgrade.md).
1. Pruebe el sitio para asegurarse de que funciona correctamente.
1. Una vez completada la actualización, elimine o cambie el nombre `maintenance.enable`
1. Vuelva a cargar la configuración de nginx:

   ```bash
   service nginx reload
   ```
