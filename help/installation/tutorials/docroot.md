---
title: Modifique docroot para mejorar la seguridad
description: Impida el acceso no autorizado basado en explorador al sistema de archivos local de Adobe Commerce.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Modifique docroot para mejorar la seguridad

En una instalación estándar con un servidor web Apache, Adobe Commerce está instalado en la raíz web predeterminada: `/var/www/html/magento2`.

El directorio `magento2/` contiene lo siguiente:

- `pub/`
- `setup/`
- `var/`

La aplicación se proporcionó desde `/var/www/html/magento2/pub`. El resto del sistema de archivos es vulnerable porque es accesible desde un explorador.
Al establecer la raíz web en el directorio `pub/`, se impide que los visitantes del sitio tengan acceso a áreas confidenciales del sistema de archivos desde un explorador.

En este tema se describe cómo cambiar el docroot de Apache en una instancia existente para que sirva archivos del directorio `pub/`, que es más seguro.

## Una nota sobre nginx

Si está usando [nginx](../prerequisites/web-server/nginx.md) y el archivo [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) incluido en el directorio de instalación, probablemente ya esté sirviendo archivos del directorio `pub/`.

Cuando se usa en el bloque de servidor que define el sitio, la configuración de `nginx.conf.sample` anula la configuración de docroot del servidor para servir archivos del directorio `pub/`. Por ejemplo, consulte la última línea de la siguiente configuración:

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

Para completar este tutorial, necesita acceder a una instalación en funcionamiento que se ejecute en una pila LAMP:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) o OpenSearch (1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>Consulte [Requisitos previos](../prerequisites/overview.md) y la [Guía de instalación](../overview.md) para obtener más información.

## &#x200B;1. Edite la configuración del servidor

El nombre y la ubicación del archivo host virtual dependen de la versión de Apache que esté ejecutando. Este ejemplo muestra el nombre y la ubicación del archivo host virtual en Apache v2.4.

1. Inicie sesión en el servidor de aplicaciones.
1. Edite el archivo host virtual:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Agregue la ruta de acceso al directorio `pub/` a la directiva `DocumentRoot`:

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

## &#x200B;2. Actualice la dirección URL base

Si agregó un nombre de directorio al nombre de host o la dirección IP del servidor para crear la dirección URL base al instalar la aplicación (por ejemplo, `http://192.168.33.10/magento2`), debe quitarla.

>[!NOTE]
>
>Reemplace `192.168.33.10` con el nombre de host del servidor.

1. Inicie sesión en la base de datos:

   ```bash
   mysql -u <user> -p
   ```

1. Especifique la base de datos que creó al instalar la aplicación:

   ```shell
   use <database-name>
   ```

1. Actualice la dirección URL base:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## &#x200B;3. Actualice el archivo env.php

Anexe el siguiente nodo al archivo `env.php`.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Consulte la [referencia env.php](../../configuration/reference/config-reference-envphp.md) para obtener más información.

## &#x200B;4. Cambiar de modo

[Los modos de aplicación](../../configuration/bootstrap/application-modes.md), que incluyen `production` y `developer`, están diseñados para mejorar la seguridad y facilitar el desarrollo. Como sugieren los nombres, debe cambiar al modo `developer` al ampliar o personalizar la aplicación y cambiar al modo `production` cuando se ejecute en un entorno activo.

Cambiar entre modos es un paso importante para comprobar que la configuración del servidor funciona correctamente. Puede cambiar entre los modos con la herramienta CLI:

1. Vaya al directorio de instalación.
1. Cambiar a modo `production`.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Actualice el explorador y compruebe que la tienda se muestra correctamente.
1. Cambiar a modo `developer`.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Actualice el explorador y compruebe que la tienda se muestra correctamente.

## &#x200B;5. Verificar la tienda

Vaya a la tienda en un navegador web para comprobar que todo funciona.

1. Abra un explorador web e introduzca el nombre de host o la dirección IP del servidor en la barra de direcciones. Por ejemplo, `http://192.168.33.10`.

   La siguiente figura muestra una página de tienda de muestra. Si se muestra de la siguiente manera, su instalación ha sido un éxito.

   ![Tienda que verifica una instalación correcta](../../assets/installation/install-success_store.png)

   Consulte la [sección de solución de problemas](https://support.magento.com/hc/en-us/articles/360032994352) si la página muestra un archivo 404 (no encontrado) o no puede cargar otros recursos, como imágenes, CSS y JS.

1. Intente acceder a un directorio de aplicaciones desde un explorador. Añada el nombre del directorio al nombre de host o a la dirección IP del servidor en la barra de direcciones:

   Si ve un mensaje 404 o el mensaje &quot;Acceso denegado&quot;, ha restringido correctamente el acceso al sistema de archivos.

   ![Acceso denegado](../../assets/installation/access-denied.png)
