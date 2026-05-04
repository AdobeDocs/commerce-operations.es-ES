---
title: Instalación de Nginx para implementaciones locales
description: Obtenga información sobre cómo instalar y configurar el servidor web Nginx para implementaciones locales de Adobe Commerce. Configure PHP-FPM y su host virtual.
feature: Install, Configuration
badgePaas: label="On-Premise" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1477'
ht-degree: 0%

---

# Instale Nginx para implementaciones locales {#nginx}

Esta guía le explica cómo instalar Nginx para implementaciones locales de Adobe Commerce y cómo configurar los ajustes de Nginx que Commerce requiere. Incluye procedimientos específicos del sistema operativo para Ubuntu y CentOS, junto con directrices para configurar PHP-FPM. Adobe recomienda seguir las instrucciones de configuración proporcionadas en esta guía para conservar la funcionalidad y la seguridad de la aplicación de Commerce.

Adobe es compatible con las versiones de Nginx enumeradas en [requisitos del sistema](../../system-requirements.md) para su versión de Adobe Commerce. Las versiones compatibles varían según la versión. Nginx también requiere una configuración compatible con PHP-FPM. Para ver los requisitos de PHP relacionados, consulte [PHP](../php-settings.md).

## Instalar en Ubuntu

Utilice esta sección para instalar Adobe Commerce en Ubuntu con Nginx, PHP y MySQL.

### Instalar Nginx

```shell
sudo apt -y install nginx
```

También puede [compilar Nginx desde el origen](https://www.armanism.com/blog/install-nginx-on-ubuntu).

Después de completar las secciones siguientes e instalar la aplicación, use el archivo de configuración de ejemplo para [configurar Nginx](#configure-nginx). Esta configuración recomendada preserva la funcionalidad y la seguridad de la aplicación de Commerce.

### Instalación y configuración de PHP-FPM

Adobe Commerce requiere varias [extensiones PHP](../php-settings.md) para funcionar correctamente. Además de estas extensiones, también debe instalar y configurar la extensión `php-fpm` si utiliza Nginx.

Para instalar y configurar `php-fpm`:

1. Instale los paquetes `php-fpm` y `php-cli` para la versión de PHP compatible con su versión de Adobe Commerce. En Ubuntu, los nombres de los paquetes suelen seguir este patrón:

   ```shell
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Reemplace `<php-version>` por la versión secundaria de PHP compatible que se enumera en [requisitos del sistema](../../system-requirements.md) para la versión de Adobe Commerce que está instalando. Utilice el mismo valor en las rutas de archivo, el nombre de servicio y la ruta de socket en los siguientes pasos.

1. Abra los `php.ini` archivos en un editor:

   ```shell
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```shell
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Edite ambos archivos para que coincidan con las siguientes líneas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe recomienda establecer el límite de memoria en 2 GB al probar Adobe Commerce. Consulte [Configuración de PHP requerida](../php-settings.md) para obtener más información.

1. Guarde y salga del editor.

1. Reinicie el servicio `php-fpm`:

   ```shell
   systemctl restart php<php-version>-fpm
   ```

### Instalar y configurar MySQL

Consulte [MySQL](../database/mysql.md) para obtener más información.

### Instalación de Adobe Commerce

Puede descargar Adobe Commerce de varias formas:

* [Obtener el metapaquete del Compositor](../../composer.md)

* [Clone el repositorio de Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Este ejemplo muestra una instalación basada en Composer mediante la línea de comandos.

1. Como [propietario del sistema de archivos](../file-system/overview.md), inicie sesión en su servidor de aplicaciones.

1. Cambie al directorio docroot del servidor web o a un directorio que haya configurado como docroot del host virtual. Para este ejemplo, se usa el valor predeterminado de Ubuntu `/var/www/html`.

   ```shell
   cd /var/www/html
   ```

1. Instale Composer globalmente. Se requiere el Compositor para actualizar las dependencias antes de instalar Adobe Commerce:

   ```shell
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Cree un proyecto Composer utilizando el metapaquete de Adobe Commerce.

   **Magento Open Source**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Cuando se le solicite, escriba sus [claves de autenticación](../authentication-keys.md). Su _clave pública_ es su nombre de usuario; su _clave privada_ es su contraseña.

1. Establezca permisos de lectura y escritura para el grupo de servidores web antes de instalar la aplicación. Esto es necesario para que la línea de comandos pueda escribir archivos en el sistema de archivos.

   ```shell
   cd /var/www/html/<magento install directory>
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```shell
   chown -R :www-data . # Ubuntu
   ```

   ```shell
   chmod u+x bin/magento
   ```

1. Instale desde la [línea de comandos](../../advanced.md). En este ejemplo se supone que el directorio de instalación se llama `magento2ee` y que el host de la base de datos está en el mismo equipo (`localhost`):

   ```shell
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Utilice el valor `--search-engine` y las opciones de host/puerto coincidentes que requiere la versión de Adobe Commerce que está instalando. Para las versiones anteriores a la 2.4.6, use `elasticsearch7` con las opciones `--elasticsearch-*` de Elasticsearch 7 o OpenSearch. En la versión 2.4.6 y posteriores, utilice el valor del motor de búsqueda y las opciones de CLI correspondientes que admite dicha versión.

1. Cambiar a modo de desarrollador:

   ```shell
   cd /var/www/html/magento2/bin
   ```

   ```shell
   ./magento deploy:mode:set developer
   ```

### Configuración De Nginx

Adobe recomienda configurar Nginx utilizando el archivo de configuración `nginx.conf.sample` proporcionado en el directorio de instalación y la configuración del host virtual Nginx para conservar tanto la funcionalidad como la seguridad de la aplicación Commerce.

>[!IMPORTANT]
>
>El archivo `nginx.conf.sample` proporciona el enrutamiento de aplicación necesario, así como reglas de protección de seguridad. Por ejemplo, restringe la ejecución de scripts dañinos cargados en el servidor. Si no utiliza este archivo ni modifica sus reglas, será responsable de implementar controles de seguridad equivalentes en la configuración de nginx personalizada.

Estas instrucciones suponen que está utilizando la ubicación predeterminada de Ubuntu para el host virtual de Nginx, como `/etc/nginx/sites-available`, y el docroot predeterminado de Ubuntu, como `/var/www/html`. Puede cambiar estas ubicaciones para adaptarlas a su entorno.

1. Cree un nuevo host virtual para el sitio:

   ```shell
   vim /etc/nginx/sites-available/magento
   ```

1. Añada la siguiente configuración:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >La directiva `include` debe apuntar al archivo de configuración nginx de ejemplo en el directorio de instalación.

1. Reemplace `www.magento-dev.com` con su nombre de dominio. Debe coincidir con la dirección URL base que especificó al instalar Adobe Commerce.

1. Guarde y salga del editor.

1. Active el host virtual recién creado creando un enlace simbólico con él en el directorio `/etc/nginx/sites-enabled`:

   ```shell
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Compruebe que la sintaxis es correcta:

   ```shell
   nginx -t
   ```

1. Reiniciar Nginx:

   ```shell
   systemctl restart nginx
   ```

### Compruebe la instalación

Para comprobar la instalación, abra un explorador web y vaya a la dirección URL base del sitio. Para obtener más información, vea [Comprobar la instalación](../../next-steps/verify.md).

## Instalar en CentOS 7

Utilice esta sección para instalar Adobe Commerce en CentOS 7 con Nginx, PHP y MySQL.

### Instalar Nginx

```shell
yum -y install epel-release
```

```shell
yum -y install nginx
```

Una vez finalizada la instalación, inicie nginx y configúrelo para que se inicie durante el arranque:

```shell
systemctl start nginx
```

```shell
systemctl enable nginx
```

Después de completar las siguientes secciones e instalar la aplicación, utilice un archivo de configuración de ejemplo para configurar Nginx.

### Instalación y configuración de PHP-FPM

Adobe Commerce requiere varias extensiones [PHP](../php-settings.md) para funcionar correctamente. Además de estas extensiones, también debe instalar y configurar la extensión `php-fpm` si utiliza Nginx.

1. Instalar `php-fpm`:

   ```shell
   yum -y install <php-fpm-package>
   ```

1. Abra el archivo `/etc/php.ini` en un editor.

   >[!NOTE]
   >
   >Instale el paquete que proporciona `php-fpm` para la versión de PHP compatible con la versión de Adobe Commerce que está instalando. Los nombres de los paquetes varían según el repositorio y el sistema operativo. Consulte [requisitos del sistema](../../system-requirements.md).

1. Elimine los comentarios de la línea `cgi.fix_pathinfo` y cambie el valor a `0`.

1. Edite el archivo para que coincida con las siguientes líneas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe recomienda establecer el límite de memoria en 2 GB al probar Adobe Commerce. Consulte [Configuración de PHP requerida](../php-settings.md) para obtener más información.

1. Elimine los comentarios del directorio de rutas de sesión y defina la ruta:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Guarde y salga del editor.

1. Abra `/etc/php-fpm.d/www.conf` en un editor.

1. Edite el archivo para que coincida con las siguientes líneas:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Elimine los comentarios de las líneas de entorno:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Guarde y salga del editor.

1. Cree un directorio para la ruta de sesión PHP y cambie el propietario al usuario y grupo `nginx`:

   ```shell
   mkdir -p /var/lib/php/session/
   ```

   ```shell
   chown -R nginx:nginx /var/lib/php/
   ```

1. Cree un directorio para el socket PHP-FPM y cambie el propietario al usuario y grupo `nginx`:

   ```shell
   mkdir -p /run/php-fpm/
   ```

   ```shell
   chown -R nginx:nginx /run/php-fpm/
   ```

1. Inicie el servicio `php-fpm` y configúrelo para que se inicie al arrancar:

   ```shell
   systemctl start php-fpm
   ```

   ```shell
   systemctl enable php-fpm
   ```

1. Compruebe que el servicio `php-fpm` se está ejecutando:

   ```shell
   netstat -pl | grep php-fpm.sock
   ```

### Instalar y configurar MySQL

Consulte [MySQL](../database/mysql.md) para obtener más información.

### Instalación de Adobe Commerce

Puede descargar Adobe Commerce de varias formas:

* [Obtener el metapaquete del Compositor](../../composer.md)

* [Clone el repositorio de Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Este ejemplo muestra una instalación basada en Composer mediante la línea de comandos.

1. Como [propietario del sistema de archivos](../file-system/overview.md), inicie sesión en su servidor de aplicaciones.

1. Cambie al directorio docroot del servidor web o a un directorio que haya configurado como docroot del host virtual. Para este ejemplo, use el valor predeterminado de CentOS `/usr/share/nginx/html`.

   ```shell
   cd /usr/share/nginx/html
   ```

1. Instale Composer globalmente. Se requiere el Compositor para actualizar las dependencias antes de instalar Adobe Commerce:

   ```shell
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Cree un proyecto Composer utilizando el metapaquete de Adobe Commerce.

   **Magento Open Source**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```shell
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Cuando se le solicite, escriba sus [claves de autenticación](../authentication-keys.md). Su _clave pública_ es su nombre de usuario; su _clave privada_ es su contraseña.

1. Establezca permisos de lectura y escritura para el grupo de servidores web antes de instalar la aplicación. Esto es necesario para que la línea de comandos pueda escribir archivos en el sistema de archivos.

   ```shell
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```shell
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```shell
   chown -R :nginx . # CentOS
   ```

   ```shell
   chmod u+x bin/magento
   ```

1. Instale desde la [línea de comandos](../../advanced.md). En este ejemplo se supone que el directorio de instalación se llama `magento2ee` y que el host de la base de datos está en el mismo equipo (`localhost`):

   ```shell
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Cambiar a modo de desarrollador:

   ```shell
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```shell
   ./magento deploy:mode:set developer
   ```

### Configuración De Nginx

Se recomienda configurar Nginx usando el archivo `nginx.conf.sample` en el directorio de instalación y la configuración de su host virtual Nginx.

>[!IMPORTANT]
>
>El archivo `nginx.conf.sample` proporciona el enrutamiento de aplicación necesario, así como reglas de protección de seguridad. Por ejemplo, restringe la ejecución de scripts dañinos cargados en el servidor. Si no utiliza este archivo ni modifica sus reglas, será responsable de implementar controles de seguridad equivalentes en la configuración de nginx personalizada.

Estas instrucciones suponen que está utilizando la ubicación predeterminada de CentOS para el host virtual Nginx, como `/etc/nginx/conf.d`, y el docroot predeterminado, como `/usr/share/nginx/html`. Puede cambiar estas ubicaciones para adaptarlas a su entorno.

1. Cree un nuevo host virtual para el sitio:

   ```shell
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Añada la siguiente configuración:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >La directiva `include` debe apuntar al archivo de configuración nginx de ejemplo en el directorio de instalación.

1. Reemplace `www.magento-dev.com` con su nombre de dominio.

1. Guarde y salga del editor.

1. Compruebe que la sintaxis es correcta:

   ```shell
   nginx -t
   ```

1. Reiniciar Nginx:

   ```shell
   systemctl restart nginx
   ```

### Configuración de SELinux y firewall

SELinux está habilitado de forma predeterminada en CentOS 7. Utilice el siguiente comando para confirmar que se está ejecutando:

```shell
sestatus
```

Para configurar SELinux y el cortafuegos:

1. Instale las herramientas de administración de SELinux:

   ```shell
   yum -y install policycoreutils-python
   ```

1. Ejecute los siguientes comandos para cambiar el contexto de seguridad del directorio de instalación:

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```shell
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```shell
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Instale el paquete del cortafuegos:

   ```shell
   yum -y install firewalld
   ```

1. Inicie el servicio de cortafuegos y configúrelo para que se inicie durante el arranque:

   ```shell
   systemctl start firewalld
   ```

   ```shell
   systemctl enable firewalld
   ```

1. Ejecute los siguientes comandos para abrir los puertos para HTTP y HTTPS y poder acceder a la dirección URL base desde un explorador web:

   ```shell
   firewall-cmd --permanent --add-service=http
   ```

   ```shell
   firewall-cmd --permanent --add-service=https
   ```

   ```shell
   firewall-cmd --reload
   ```

### Compruebe la instalación

Para comprobar la instalación, abra un explorador web y vaya a la dirección URL base del sitio. Para obtener más información, vea [Comprobar la instalación](../../next-steps/verify.md).
