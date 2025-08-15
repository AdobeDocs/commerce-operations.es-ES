---
title: Configuración de varios sitios web con Nginx
description: Siga este tutorial para configurar varios sitios web con Nginx.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Configuración de varios sitios web con Nginx

Suponemos que:

- Está trabajando en una máquina de desarrollo (portátil, máquina virtual o similar).

  Es posible que se requieran tareas adicionales para implementar varios sitios web en un entorno alojado; póngase en contacto con su proveedor de alojamiento para obtener más información.

  Se requieren tareas adicionales para configurar Adobe Commerce en la infraestructura en la nube. Después de completar las tareas que se describen en este tema, vea [Configurar varios sitios web o tiendas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) en la guía _Commerce en infraestructura de nube_.

- Acepta varios dominios en un archivo host virtual o utiliza un host virtual por sitio web; los archivos de configuración de host virtual se encuentran en `/etc/nginx/sites-available`.
- Utiliza el(la) `nginx.conf.sample` proporcionado(a) por Commerce solo con las modificaciones descritas en este tutorial.
- El software de Commerce está instalado en `/var/www/html/magento2`.
- Tiene dos sitios web distintos del predeterminado:

   - `french.mysite.mg` con código de sitio web `french` y código de vista de tienda `fr`
   - `german.mysite.mg` con código de sitio web `german` y código de vista de tienda `de`
   - `mysite.mg` es el sitio web predeterminado y la vista de tienda predeterminada

>[!TIP]
>
>Consulte [Crear sitios web](ms-admin.md#step-2-create-websites) y [Crear vistas de tiendas](ms-admin.md#step-4-create-store-views) para obtener ayuda con la localización de estos valores.

A continuación se muestra una hoja de ruta para configurar varios sitios web con nginx:

1. [Configurar sitios web, tiendas y vistas de tiendas](ms-admin.md) en el administrador.
1. Cree un [host virtual Nginx](#step-2-create-nginx-virtual-hosts)) para asignar muchos sitios web o un host virtual Nginx por sitio web de Commerce (los pasos se detallan a continuación).
1. Pase los valores de las [variables MAGE](ms-overview.md) `$MAGE_RUN_TYPE` y `$MAGE_RUN_CODE` a nginx mediante `nginx.conf.sample` proporcionadas por Magento (los pasos se detallan a continuación).

   - `$MAGE_RUN_TYPE` puede ser `store` o `website`:

      - Use `website` para cargar el sitio web en la tienda.
      - Use `store` para cargar cualquier vista de tienda en su tienda.

   - `$MAGE_RUN_CODE` es el sitio web único o el código de vista de tienda que corresponde a `$MAGE_RUN_TYPE`.

1. Actualice la configuración de la URL básica en el administrador de Commerce.

## Paso 1: crear sitios web, tiendas y vistas de tiendas en el administrador

Ver [Configurar varios sitios web, tiendas y vistas de tiendas en el administrador](ms-admin.md).

## Paso 2: Crear hosts virtuales nginx

Este paso explica cómo cargar sitios web en la tienda. Puede utilizar sitios web o vistas de tiendas; si utiliza las vistas de tiendas, debe ajustar los valores de los parámetros en consecuencia. Debe completar las tareas de esta sección como usuario con privilegios de `sudo`.

Solo con un [archivo host virtual nginx](#step-2-create-nginx-virtual-hosts), puede mantener la configuración nginx simple y limpia. Mediante varios archivos host virtuales, puede personalizar cada almacén (para utilizar una ubicación personalizada para `french.mysite.mg`, por ejemplo).

**Para crear un host virtual** (simplificado):

Esta configuración se amplía en [nginx configuration](../../installation/prerequisites/web-server/nginx.md).

1. Abra un editor de texto y agregue el siguiente contenido a un nuevo archivo de nombre `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Guarde los cambios en los archivos y salga del editor de texto.
1. Compruebe la configuración del servidor:

   ```bash
   nginx -t
   ```

1. Si se ejecuta correctamente, aparece el siguiente mensaje:

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Si se muestran errores, compruebe la sintaxis de los archivos de configuración del host virtual.

1. Crear un vínculo simbólico en el directorio `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Para obtener más información sobre la directiva de asignación, consulte [documentación de nginx en la directiva de asignación](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Para crear varios hosts virtuales**:

1. Abra un editor de texto y agregue el siguiente contenido a un nuevo archivo de nombre `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Cree otro archivo con el nombre `german.mysite.mg` en el mismo directorio con el siguiente contenido:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Guarde los cambios en los archivos y salga del editor de texto.
1. Compruebe la configuración del servidor:

   ```bash
   nginx -t
   ```

1. Si se ejecuta correctamente, aparece el siguiente mensaje:

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Si se muestran errores, compruebe la sintaxis de los archivos de configuración del host virtual.

1. Cree vínculos simbólicos en el directorio `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Paso 3: Modificar nginx.conf.sample

>[!TIP]
>
>No edite el archivo `nginx.conf.sample`; se trata de un archivo Commerce principal que puede actualizarse con cada nueva versión. En su lugar, copie el archivo `nginx.conf.sample`, cambie su nombre y, a continuación, edite el archivo copiado.

**Para editar el punto de entrada de PHP para la aplicación principal**:

Para modificar el archivo `nginx.conf.sample`**:

1. Abra un editor de texto y revise el archivo `nginx.conf.sample` ,`<magento2_installation_directory>/nginx.conf.sample`. Busque la siguiente sección:

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Actualice el archivo `nginx.conf.sample` con las dos líneas siguientes antes de la instrucción include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Un punto de entrada de PHP actualizado de ejemplo para la aplicación principal tiene este aspecto:

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Paso 4: Actualizar la configuración de la URL base

Debe actualizar la dirección URL base de los sitios web `french` y `german` en el administrador de Commerce.

### Actualizar URL base del sitio web francés

1. Inicie sesión en el administrador de Commerce y vaya a **Tiendas** > **Configuración** > **Configuración** > **General** > **Web**.
1. Cambiar el _ámbito de configuración_ al sitio web `french`.
1. Expanda la sección **URL básicas** y actualice el valor de **URL base** y **URL de vínculo base** a `http://french.magento24.com/`.
1. Expanda la sección **URL básicas (seguras)** y actualice el valor **URL base segura** y **URL de vínculo base seguro** a `https://french.magento24.com/`.
1. Haga clic en **Guardar configuración** y guarde los cambios de configuración.

### Actualizar URL base del sitio web en alemán

1. Inicie sesión en el administrador de Commerce y vaya a **Tiendas** > **Configuración** > **Configuración** > **General** > **Web**.
1. Cambiar el _ámbito de configuración_ al sitio web `german`.
1. Expanda la sección **URL básicas** y actualice el valor de **URL base** y **URL de vínculo base** a `http://german.magento24.com/`.
1. Expanda la sección **URL básicas (seguras)** y actualice el valor **URL base segura** y **URL de vínculo base seguro** a `https://german.magento24.com/`.
1. Haga clic en **Guardar configuración** y guarde los cambios de configuración.

### Limpiar la caché

Ejecute el siguiente comando para limpiar las cachés de `config` y `full_page`.

```bash
bin/magento cache:clean config full_page
```

## Verifique su sitio

A menos que tenga DNS configurado para las direcciones URL de las tiendas, debe agregar una ruta estática al host en el archivo `hosts`:

1. Busque el archivo del sistema operativo `hosts`.
1. Añada la ruta estática con el formato:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Vaya a una de las siguientes direcciones URL en el explorador:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Es posible que se requieran tareas adicionales para implementar varios sitios web en un entorno alojado; póngase en contacto con su proveedor de alojamiento para obtener más información.
>- Se requieren tareas adicionales para configurar Adobe Commerce en la infraestructura en la nube. Consulte [Configurar varios sitios web o tiendas en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) en la guía _Commerce en la infraestructura en la nube_.

### Resolución de problemas

- Si tus sitios en francés y alemán devuelven 404s pero tu administrador carga, asegúrate de completar [Paso 6: Agrega el código de la tienda a la URL base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Si todas las direcciones URL devuelven 404, asegúrese de reiniciar el servidor web.
- Si el administrador no funciona correctamente, asegúrese de configurar correctamente los hosts virtuales.
