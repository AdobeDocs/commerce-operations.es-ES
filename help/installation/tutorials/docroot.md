---
title: Modificar docroot para mejorar la seguridad
description: Impida el acceso no autorizado basado en explorador a Adobe Commerce o al sistema de archivos local del Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# Modificar docroot para mejorar la seguridad

En una instalación estándar con un servidor web Apache, Adobe Commerce y Magento Open Source se instalan en la raíz web predeterminada: `/var/www/html/magento2`.

La variable `magento2/` contiene lo siguiente:

- `pub/`
- `setup/`
- `var/`

La aplicación se suministra desde `/var/www/html/magento2/pub`. El resto del sistema de archivos es vulnerable porque es accesible desde un explorador.
Configuración de la raíz web en la variable `pub/` impide que los visitantes del sitio accedan a áreas confidenciales del sistema de archivos desde un explorador.

En este tema se describe cómo cambiar el docroot de Apache en una instancia existente para que sirva archivos de la `pub/` , que es más seguro.

## Una nota sobre nginx

Si está utilizando [nginx](../prerequisites/web-server/nginx.md) y [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) incluido en el directorio de instalación, probablemente ya esté sirviendo archivos del `pub/` directorio.

Cuando se utiliza en el bloque del servidor que define el sitio, la variable `nginx.conf.sample` La configuración de anula la configuración docroot del servidor para servir archivos de `pub/` directorio. Por ejemplo, consulte la última línea en la siguiente configuración:

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Antes de empezar

Para completar este tutorial, necesita acceder a una instalación en funcionamiento que se ejecute en un [LÁMPARA](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) pila:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) o OpenSearch (1.2)
- Adobe Commerce o Magento Open Source (2.4+)

>[!NOTE]
>
>Consulte [Requisitos previos](../prerequisites/overview.md) y [Guía de instalación](../overview.md) para obtener más información.

## 1. Edite la configuración del servidor

El nombre y la ubicación del archivo host virtual dependen de la versión de Apache que ejecute. Este ejemplo muestra el nombre y la ubicación del archivo host virtual en Apache v2.4.

1. Inicie sesión en el servidor de aplicaciones.
1. Edite el archivo host virtual:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Añada la ruta a su `pub/` para `DocumentRoot` directiva:

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Reinicie Apache:

   ```bash
   systemctl restart apache2
   ```

## 2. Actualice la dirección URL base

Si ha añadido un nombre de directorio al nombre de host o a la dirección IP de su servidor para crear la URL base al instalar la aplicación (por ejemplo `http://192.168.33.10/magento2`), debe eliminarlo.

>[!NOTE]
>
>Reemplazar `192.168.33.10` con el nombre de host de su servidor.

1. Inicie sesión en la base de datos:

   ```bash
   mysql -u <user> -p
   ```

1. Especifique la base de datos que creó al instalar la aplicación:

   ```shell
   use <database-name>
   ```

1. Actualice la URL base:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Actualice el archivo env.php

Anexe el siguiente nodo al `env.php` archivo.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Consulte la [referencia env.php](../../configuration/reference/config-reference-envphp.md) para obtener más información.

## 4. Cambiar modos

[Modos de aplicación](../../configuration/bootstrap/application-modes.md), que incluyen `production` y `developer`, están diseñados para mejorar la seguridad y facilitar el desarrollo. Como sugieren los nombres, debe cambiar a `developer` al ampliar o personalizar la aplicación y cambiar a `production` cuando se ejecuta en un entorno en directo.

El cambio entre modos es un paso importante para comprobar que la configuración del servidor funciona correctamente. Puede cambiar entre modos utilizando la herramienta CLI:

1. Vaya al directorio de instalación.
1. Cambie a `production` en el menú contextual.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Actualice el explorador y compruebe que la tienda se muestre correctamente.
1. Cambie a `developer` en el menú contextual.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Actualice el explorador y compruebe que la tienda se muestre correctamente.

## 5. Verifique la tienda

Vaya a la [storefront](https://glossary.magento.com/storefront) en un navegador web para comprobar que todo funciona.

1. Abra un explorador web e introduzca el nombre de host o la dirección IP del servidor en la barra de direcciones. Por ejemplo, `http://192.168.33.10`.

   La siguiente figura muestra una página de tienda de muestra. Si se muestra de la siguiente manera, la instalación se ha realizado correctamente.

   ![Tienda que comprueba una instalación correcta](../../assets/installation/install-success_store.png)

   Consulte la [sección resolución de problemas](https://support.magento.com/hc/en-us/articles/360032994352) si la página muestra un 404 (no encontrado) o no carga otros recursos, como imágenes, CSS y JS.

1. Intente acceder a un directorio de aplicaciones desde un explorador. Anexe el nombre de directorio al nombre de host o la dirección IP de su servidor en la barra de direcciones:

   Si ve un mensaje 404 o el mensaje &quot;Acceso denegado&quot;, ha restringido correctamente el acceso al sistema de archivos.

   ![Acceso denegado](../../assets/installation/access-denied.png)
