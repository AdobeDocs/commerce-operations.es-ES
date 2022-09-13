---
title: Nginx
description: Siga estos pasos para instalar y configurar el servidor web Nginx para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

Adobe Commerce es compatible con nginx 1.18 (o [versión más reciente de mainline](https://nginx.org/en/linux_packages.html#mainline)). También debe instalar la última versión de `php-fpm`.

Las instrucciones de instalación varían en función del sistema operativo que utilice. Consulte [PHP](../php-settings.md) para obtener más información.

## Ubuntu

En la siguiente sección se describe cómo instalar Adobe Commerce y Magento Open Source 2.x en Ubuntu utilizando nginx, PHP y MySQL.

### Instalar nginx

```bash
sudo apt -y install nginx
```

También puede [compilar nginx desde el origen](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Después de completar las siguientes secciones e instalar la aplicación, utilizaremos un archivo de configuración de ejemplo para [configurar nginx](#configure-nginx).

### Instalación y configuración de php-fpm

Adobe Commerce y Magento Open Source requieren varias [Extensiones PHP](../php-settings.md) para funcionar correctamente. Además de estas extensiones, también debe instalar y configurar el `php-fpm` extensión si está utilizando nginx.

Para instalar y configurar `php-fpm`:

1. Instalar `php-fpm` y `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Este comando instala la última versión disponible de PHP 7.2.X. Consulte [requisitos del sistema](../../system-requirements.md) para versiones PHP compatibles.

1. Abra el `php.ini` archivos en un editor:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Edite ambos archivos para que coincidan con las siguientes líneas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Se recomienda establecer el límite de memoria en 2 G al probar Adobe Commerce y el Magento Open Source. Consulte [Configuración de PHP requerida](../php-settings.md) para obtener más información.

1. Guarde y salga del editor.

1. Reinicie el `php-fpm` servicio:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Instalar y configurar MySQL

Consulte [MySQL](../database/mysql.md) para obtener más información.

### Instalación y configuración

Hay varias formas de descargar Adobe Commerce y Magento Open Source, entre ellas:

* [Obtenga el paquete de metapaversión del Compositor](../../composer.md)

* [Clonar el repositorio de Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Este ejemplo muestra una instalación basada en Compositor utilizando la línea de comandos.

1. Como [propietario del sistema de archivos](../file-system/overview.md), inicie sesión en el servidor de aplicaciones.

1. Cambie al directorio docroot del servidor web o a un directorio que haya configurado como docroot de host virtual. Para este ejemplo, se utiliza el valor predeterminado Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Instale el Compositor globalmente. Se requiere el Compositor para actualizar las dependencias antes de instalar Adobe Commerce o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Cree un proyecto de Compositor utilizando el Magento Open Source o el paquete de metapaídas de Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Cuando se le solicite, introduzca su [claves de autenticación](../authentication-keys.md). Su _clave pública_ es su nombre de usuario; your _clave privada_ es su contraseña.

1. Establezca permisos de lectura y escritura para el grupo de servidores web antes de instalar la aplicación. Esto es necesario para que la línea de comandos pueda escribir archivos en el sistema de archivos.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Instale desde el [línea de comandos](../../advanced.md). Este ejemplo asume que el directorio de instalación tiene el nombre `magento2ee`, el `db-host` está en la misma máquina (`localhost`) y que la variable `db-name`, `db-user`y `db-password` son todos `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Cambie al modo de desarrollador:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar nginx

Se recomienda configurar nginx usando la variable `nginx.conf.sample` archivo de configuración proporcionado en el directorio de instalación y en el host virtual nginx.

Estas instrucciones suponen que está utilizando la ubicación predeterminada de Ubuntu para el host virtual nginx (por ejemplo, `/etc/nginx/sites-available`) y Ubuntu default docroot (por ejemplo, `/var/www/html`), sin embargo, puede cambiar estas ubicaciones para adaptarlas a su entorno.

1. Cree un nuevo host virtual para su sitio:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Añada la siguiente configuración:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
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
   >La variable `include` debe apuntar al archivo de configuración nginx de ejemplo en el directorio de instalación.

1. Reemplazar `www.magento-dev.com` con su nombre de dominio. Debe coincidir con la dirección URL base especificada al instalar Adobe Commerce o Magento Open Source.

1. Guarde y salga del editor.

1. Active el host virtual recién creado creando un enlace simbólico a él en el `/etc/nginx/sites-enabled` directorio:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Compruebe que la sintaxis es correcta:

   ```bash
   nginx -t
   ```

1. Reinicie nginx:

   ```bash
   systemctl restart nginx
   ```

### Verifique la instalación

Abra un explorador web y vaya a la dirección URL base de su sitio a [verificar la instalación](../../next-steps/verify.md).

## CentOS 7

En la siguiente sección se describe cómo instalar Adobe Commerce y Magento Open Source 2.x en CentOS 7 utilizando nginx, PHP y MySQL.

### Instalar nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Una vez finalizada la instalación, inicie nginx y configúrelo para que se inicie en el momento del inicio:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Después de completar las siguientes secciones e instalar la aplicación, utilizaremos un archivo de configuración de ejemplo para configurar nginx.

### Instalación y configuración de php-fpm

Adobe Commerce y Magento Open Source requieren varias [PHP](../php-settings.md) para que funcionen correctamente. Además de estas extensiones, también debe instalar y configurar el `php-fpm` extensión si está utilizando nginx.

1. Instalar `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Abra el `/etc/php.ini` en un editor.

1. Descomente el `cgi.fix_pathinfo` línea y cambie el valor a `0`.

1. Edite el archivo para que coincida con las siguientes líneas:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Se recomienda establecer el límite de memoria en 2 G al probar Adobe Commerce o Magento Open Source. Consulte [Configuración de PHP requerida](../php-settings.md) para obtener más información.

1. Descomente el directorio de rutas de sesión y establezca la ruta:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Guarde y salga del editor.

1. Apertura `/etc/php-fpm.d/www.conf` en un editor.

1. Edite el archivo para que coincida con las siguientes líneas:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Descomente las líneas de entorno:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Guarde y salga del editor.

1. Cree un directorio para la ruta de sesión de PHP y cambie el propietario a `apache` usuario y grupo:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Cree un directorio para la ruta de sesión de PHP y cambie el propietario a `apache` usuario y grupo:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Inicie el `php-fpm` y configúrelo para que se inicie en el momento del inicio:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Compruebe que la variable `php-fpm` se está ejecutando el servicio:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Instalar y configurar MySQL

Consulte [MySQL](..//database/mysql.md) para obtener más información.

### Instalación y configuración

Existen varias formas de descargar el Adobe Commerce y el Magento Open Source, entre ellas:

* [Obtenga el paquete de metapaversión del Compositor](../../composer.md)

* [Clonar el repositorio de Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Este ejemplo muestra una instalación basada en Compositor utilizando la línea de comandos.

1. Como [propietario del sistema de archivos](../file-system/overview.md), inicie sesión en el servidor de aplicaciones.

1. Cambie al directorio docroot del servidor web o a un directorio que haya configurado como docroot de host virtual. Para este ejemplo, se utiliza el valor predeterminado Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Instale el Compositor globalmente. Se requiere el Compositor para actualizar las dependencias antes de instalar Adobe Commerce o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Cree un proyecto de Compositor utilizando el Magento Open Source o el paquete de metapaídas de Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Cuando se le solicite, introduzca su [claves de autenticación](../authentication-keys.md). Su _clave pública_ es su nombre de usuario; your _clave privada_ es su contraseña.

1. Establezca permisos de lectura y escritura para el grupo de servidores web antes de instalar la aplicación. Esto es necesario para que la línea de comandos pueda escribir archivos en el sistema de archivos.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Instale desde el [línea de comandos](../../advanced.md). Este ejemplo asume que el directorio de instalación tiene el nombre `magento2ee`, el `db-host` está en la misma máquina (`localhost`) y que la variable `db-name`, `db-user`y `db-password` son todos `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Cambie al modo de desarrollador:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurar nginx

Se recomienda configurar nginx usando la variable `nginx.conf.sample` archivo de configuración proporcionado en el directorio de instalación y en el host virtual nginx.

Estas instrucciones suponen que está utilizando la ubicación predeterminada de CentOS para el host virtual nginx (por ejemplo, `/etc/nginx/conf.d`) y docroot predeterminado (por ejemplo, `/usr/share/nginx/html`), sin embargo, puede cambiar estas ubicaciones para adaptarlas a su entorno.

1. Cree un nuevo host virtual para su sitio:

   ```bash
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
   >La variable `include` debe apuntar al archivo de configuración nginx de ejemplo en el directorio de instalación.

1. Reemplazar `www.magento-dev.com` con su nombre de dominio.

1. Guarde y salga del editor.

1. Compruebe que la sintaxis es correcta:

   ```bash
   nginx -t
   ```

1. Reinicie nginx:

   ```bash
   systemctl restart nginx
   ```

### Configuración de SELinux y Firewalld

SELinux está habilitado de forma predeterminada en CentOS 7. Utilice el siguiente comando para ver si se está ejecutando:

```bash
sestatus
```

Para configurar SELinux y firewalld:

1. Instale las herramientas de administración de SELinux:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Ejecute los siguientes comandos para cambiar el contexto de seguridad del directorio de instalación:

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Instale el paquete firewalld:

   ```bash
   yum -y install firewalld
   ```

1. Inicie el servicio de firewall y configúrelo para que se inicie en el momento del inicio:

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Ejecute los siguientes comandos para abrir puertos para HTTP y HTTPS y así poder acceder a la URL base desde un explorador web:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Verifique la instalación

Abra un explorador web y vaya a la dirección URL base de su sitio a [verificar la instalación](../../next-steps/verify.md).
