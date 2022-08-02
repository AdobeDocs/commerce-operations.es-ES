---
title: Configuración de varios sitios web con Nginx
description: Siga este tutorial para configurar varios sitios web con Nginx.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---


# Configuración de varios sitios web con Nginx

Asumimos que:

- Está trabajando en una máquina de desarrollo (portátil, máquina virtual o similar).

   Es posible que se necesiten tareas adicionales para implementar varios sitios web en un entorno alojado; consulte con su proveedor de alojamiento para obtener más información.

   Se requieren tareas adicionales para configurar Adobe Commerce en la infraestructura de la nube. Después de completar las tareas tratadas en este tema, consulte [Configuración de varios sitios web o tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html) en el _guía del Commerce Cloud_.

- Acepta varios dominios en un archivo host virtual o utiliza un host virtual por sitio web; los archivos de configuración del host virtual se encuentran en `/etc/nginx/sites-available`.
- Utilice la variable `nginx.conf.sample` proporcionado por Commerce solo con las modificaciones descritas en este tutorial.
- El software Commerce está instalado en `/var/www/html/magento2`.
- Tiene dos sitios web que no son los predeterminados:

   - `french.mysite.mg` con código del sitio web `french` y almacenar código de vista `fr`
   - `german.mysite.mg` con código del sitio web `german` y almacenar código de vista `de`
   - `mysite.mg` es el sitio web predeterminado y la vista de tienda predeterminada

>[!TIP]
>
>Consulte [Creación de sitios web](ms-admin.md#step-2-create-websites) y [Crear vistas de tiendas](ms-admin.md#step-4-create-store-views) para obtener ayuda sobre la localización de estos valores.

El siguiente es un plan para configurar varios sitios web con nginx:

1. [Configuración de sitios web, tiendas y vistas de tiendas](ms-admin.md) en el menú
1. Cree un [Host virtual Nginx](#step-2-create-nginx-virtual-hosts)) para asignar muchos sitios web o un host virtual Nginx por sitio web de comercio (pasos detallados a continuación).
1. Pasa los valores de la variable [MAGE variables](ms-overview.md) `$MAGE_RUN_TYPE` y `$MAGE_RUN_CODE` a nginx utilizando el Magento proporcionado `nginx.conf.sample` (pasos detallados a continuación).

   - `$MAGE_RUN_TYPE` puede `store` o `website`:

      - Uso `website` para cargar su sitio web en su tienda.
      - Uso `store` para cargar cualquier vista de tienda en tu tienda.
   - `$MAGE_RUN_CODE` es el código de vista de tienda o sitio web único que corresponde a `$MAGE_RUN_TYPE`.


1. Actualice la configuración de la URL base en el administrador de comercio.

## Paso 1: Cree sitios web, tiendas y vistas de tiendas en el administrador

Consulte [Configure varios sitios web, tiendas y vistas de tienda en el administrador](ms-admin.md).

## Paso 2: Crear hosts virtuales nginx

Este paso explica cómo cargar sitios web en la variable [storefront](https://glossary.magento.com/storefront). Puede utilizar sitios web o almacenar vistas; si utiliza vistas de tienda, debe ajustar los valores de los parámetros en consecuencia. Debe completar las tareas de esta sección como usuario con `sudo` privilegios.

Usando solo una [archivo host virtual nginx](#step-2-create-nginx-virtual-hosts), puede mantener la configuración de nginx sencilla y limpia. Mediante el uso de varios archivos host virtuales, puede personalizar cada almacén (para utilizar una ubicación personalizada para `french.mysite.mg` por ejemplo).

**Para crear un host virtual** (simplificado):

Esta configuración se amplía [Configuración de Nginx](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html).

1. Abra un editor de texto y añada el siguiente contenido a un nuevo archivo denominado `/etc/nginx/sites-available/magento`:

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

1. Si se realiza correctamente, se muestra el siguiente mensaje:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Si se muestran errores, compruebe la sintaxis de los archivos de configuración del host virtual.

1. Cree un vínculo simbólico en la variable `/etc/nginx/sites-enabled` directorio:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Para obtener más información sobre la directiva de asignación, consulte [documentación de nginx sobre la directiva de mapa](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Para crear varios hosts virtuales**:

1. Abra un editor de texto y añada el siguiente contenido a un nuevo archivo denominado `/etc/nginx/sites-available/french.mysite.mg`:

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

1. Crear otro archivo con el nombre `german.mysite.mg` en el mismo directorio con el siguiente contenido:

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

1. Si se realiza correctamente, se muestra el siguiente mensaje:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Si se muestran errores, compruebe la sintaxis de los archivos de configuración del host virtual.

1. Cree vínculos simbólicos en la variable `/etc/nginx/sites-enabled` directorio:

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
>No edite el `nginx.conf.sample` archivo; es un archivo principal de Commerce que se puede actualizar con cada nueva versión. En su lugar, copie el `nginx.conf.sample` , cambie el nombre del archivo y, a continuación, edite el archivo copiado.

**Para editar el punto de entrada PHP para la aplicación principal**:

Para modificar el `nginx.conf.sample` archivo**:

1. Abra un editor de texto y revise la `nginx.conf.sample` archivo ,`<magento2_installation_directory>/nginx.conf.sample`. Busque la siguiente sección:

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

1. Actualice el `nginx.conf.sample` con las dos líneas siguientes antes de la instrucción include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Un ejemplo de punto de entrada PHP actualizado para la aplicación principal tiene el siguiente aspecto:

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

Debe actualizar la dirección URL base para la variable `french` y `german` sitios web en el administrador de comercio.

### Actualizar URL base del sitio web francés

1. Inicie sesión en el administrador de comercio y vaya a **Almacenes** > **Configuración** > **Configuración** > **General** > **Web**.
1. Cambie el _ámbito de configuración_ a `french` sitio web.
1. Expandir **Direcciones URL base** y actualice la **Dirección URL base** y **URL del vínculo base** valor `http://french.magento24.com/`.
1. Expandir **URL base (segura)** y actualice la **URL de base segura** y **URL del vínculo base seguro** valor `https://french.magento24.com/`.
1. Haga clic en **Guardar configuración** y guarde los cambios de configuración.

### Actualizar URL de base del sitio web alemán

1. Inicie sesión en el administrador de comercio y vaya a **Almacenes** > **Configuración** > **Configuración** > **General** > **Web**.
1. Cambie el _ámbito de configuración_ a `german` sitio web.
1. Expandir **Direcciones URL base** y actualice la **Dirección URL base** y **URL del vínculo base** valor `http://german.magento24.com/`.
1. Expandir **URL base (segura)** y actualice la **URL de base segura** y **URL del vínculo base seguro** valor `https://german.magento24.com/`.
1. Haga clic en **Guardar configuración** y guarde los cambios de configuración.

### Limpiar la caché

Ejecute el siguiente comando para limpiar el `config` y `full_page` cachés.

```bash
bin/magento cache:clean config full_page
```

## Verificar el sitio

A menos que tenga DNS configurado para las URL de sus tiendas, debe agregar una ruta estática al host en su `hosts` archivo:

1. Localizar el sistema operativo `hosts` archivo.
1. Añada la ruta estática con el formato :

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. Vaya a una de las siguientes direcciones URL en su explorador:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Es posible que se necesiten tareas adicionales para implementar varios sitios web en un entorno alojado; consulte con su proveedor de alojamiento para obtener más información.
>- Se necesitan tareas adicionales para configurar Adobe Commerce en la infraestructura de la nube; see [Configuración de varios sitios web o tiendas de Cloud](https://devdocs.magento.com/cloud/project/project-multi-sites.html) en el _guía del Commerce Cloud_.


### Resolución de problemas

- Si sus sitios en francés y alemán devuelven 404 s pero su administrador carga, asegúrese de haber completado [Paso 6: Añadir el código de tienda a la URL base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Si todas las direcciones URL devuelven 404 s, asegúrese de reiniciar el servidor web.
- Si el administrador no funciona correctamente, asegúrese de configurar correctamente los hosts virtuales.
