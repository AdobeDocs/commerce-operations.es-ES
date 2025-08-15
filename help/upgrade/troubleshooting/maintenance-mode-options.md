---
title: Opciones de modo de mantenimiento para la actualización
description: Cree una página de modo de mantenimiento personalizada que sus clientes vean en su tienda de Adobe Commerce mientras ejecuta una actualización.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Opciones de modo de mantenimiento para la actualización

En este tema se explica cómo crear una página de mantenimiento personalizada para mostrarla a los usuarios mientras se actualiza la aplicación de Magento. Crear una página personalizada es opcional, pero se recomienda porque el sitio es accesible durante parte de la actualización.

La creación de una página personalizada a la que redirigir a los usuarios impide cualquier acceso al sitio y también informa a los usuarios de que el sitio se está manteniendo.

>[!NOTE]
>
>Debe realizar las tareas de esta sección como usuario con privilegios de `root`. Las páginas de mantenimiento personalizadas no se pueden establecer en el modo de desarrollador.

## Creación de la página de mantenimiento personalizada

Para crear una página de mantenimiento y redirigirla, cree primero una página de mantenimiento llamada:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

Añada los siguientes contenidos:

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

   - Redirigir todo el tráfico a la página de mantenimiento
   - Lista de permitidos ciertas IP para que un administrador pueda actualizar el software de Magento.

   El siguiente ejemplo lista de permitidos 192.0.2.110.

   Agregue lo siguiente al final de su archivo de configuración de Apache:

   ```
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

1. [Actualice su sistema](../implementation/perform-upgrade.md).
1. Pruebe el sitio para asegurarse de que funciona correctamente.
1. Una vez completada la actualización, elimine `maintenance.enable`.

## Página de mantenimiento personalizada para nginx

En esta sección se explica cómo crear una página de mantenimiento personalizada y cómo redirigir el tráfico a ella.

Para redirigir el tráfico a una página de mantenimiento personalizada:

1. Utilice un editor de texto para abrir el archivo de configuración de nginx que contiene el bloque de servidor.
1. Agregue lo siguiente al bloque de servidor (`server` se muestra solo para una mayor claridad; no agregue un segundo bloque de servidor).

   La siguiente lista de permitidos la dirección IP 192.0.2.110 y 192.0.2.115 en un sistema donde Magento está instalado en `/var/www/html/magento2`:

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

1. [Actualice su sistema](../implementation/perform-upgrade.md).
1. Pruebe el sitio para asegurarse de que funciona correctamente.
1. Una vez completada la actualización, elimine `maintenance.enable` o cambie su nombre
1. Vuelva a cargar la configuración de nginx:

   ```bash
   service nginx reload
   ```
