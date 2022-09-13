---
title: Apache
description: Siga estos pasos para instalar y configurar el servidor web Apache para instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---


# Apache

Adobe Commerce es compatible con Apache 2.4.x.

## Directivas requeridas de Apache

1. Establezca `AllowEncodedSlashes` en la configuración del servidor (globalmente) o en las configuraciones de host virtual para evitar descodificar las barras codificadas que pueden causar problemas para las direcciones URL. Por ejemplo, al recuperar productos con una barra diagonal en el SKU a través de la API, no desea que se convierta. El bloque de muestra no está completo y se requieren otras directivas.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Reescrituras de Apache y acceso remoto

En este tema se explica cómo habilitar las reescrituras de Apache 2.4 y especificar una configuración para [archivo de configuración distribuido, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce y el Magento Open Source utilizan reescrituras del servidor y `.htaccess` para proporcionar instrucciones a nivel de directorio para Apache. Las siguientes instrucciones están incluidas también en todas las demás secciones de este tema.

Utilice esta sección para habilitar las reescrituras de Apache 2.4 y especificar una configuración para [archivo de configuración distribuido, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce y el Magento Open Source utilizan reescrituras del servidor y `.htaccess` para proporcionar instrucciones a nivel de directorio para Apache.

>[!NOTE]
>
>Si no se habilita esta configuración, normalmente no se mostrarán estilos en la tienda o en el administrador.

1. Habilite el módulo de reescritura de Apache:

   ```bash
   a2enmod rewrite
   ```

1. Para permitir que la aplicación utilice el `.htaccess` , consulte las directrices de la sección [Documentación de Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >En Apache 2.4, el archivo de configuración de sitio predeterminado del servidor es `/etc/apache2/sites-available/000-default.conf`.

   Por ejemplo, puede agregar lo siguiente al final de `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >En ocasiones, pueden ser necesarios parámetros adicionales. Para obtener más información, consulte la [Documentación de Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Si ha cambiado la configuración de Apache, reinicie Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Si ha actualizado desde una versión anterior de Apache, primero busque `<Directory "/var/www/html">` o `<Directory "/var/www">` en `000-default.conf`.
   >- Debe cambiar el valor de `AllowOverride` en la directiva para el directorio en el que espera instalar el software Adobe Commerce o Magento Open Source. Por ejemplo, para instalar en el servidor web docroot, edite la directiva en `<Directory /var/www>`.


>[!NOTE]
>
>Si no se habilita esta configuración, normalmente los estilos no se mostrarán en la tienda o en el Administrador.

## Módulos requeridos por Apache

Adobe Commerce y Magento Open Source requieren que se instalen los siguientes módulos de Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verificar la versión de Apache

Para verificar la versión de Apache que está ejecutando, introduzca:

```bash
apache2 -v
```

El resultado es similar al siguiente:

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Si Apache es *not* instalado, consulte:
   - [Instalación o actualización de Apache en Ubuntu](#installing-apache-on-ubuntu)
   - [Instalación de Apache en CentOS](#installing-apache-on-centos)

## Instalación o actualización de Apache en Ubuntu

Las siguientes secciones tratan sobre cómo instalar o actualizar Apache:

- Instalación de Apache
- Actualice a Apache 2.4 en Ubuntu para utilizar PHP 7.4.

### Instalación de Apache en Ubuntu

Para instalar la versión predeterminada de Apache:

1. Instalación de Apache

   ```bash
   apt-get -y install apache2
   ```

1. Verifique la instalación.

   ```bash
   apache2 -v
   ```

   El resultado es similar al siguiente:

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Habilitar [reescribe y `.htaccess`](#apache-rewrites-and-htaccess).

### Actualización de Apache en Ubuntu

Para actualizar a Apache 2.4:

1. Agregue la variable `ppa:ondrej` repositorio, que tiene Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Instale Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Si el comando &quot;apt-get install&quot; falla debido a dependencias no satisfechas, consulte un recurso como [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Verifique la instalación.

   ```bash
   apache2 -v
   ```

   Se deben mostrar mensajes similares a los siguientes:

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Habilitar [reescribe y `.htaccess`](#apache-rewrites-and-htaccess).

## Instalación de Apache en CentOS

Adobe Commerce y Magento Open Source requieren que Apache use reescrituras del servidor. También debe especificar el tipo de directivas que se pueden usar en `.htaccess`, que la aplicación utiliza para especificar reglas de reescritura.

La instalación y configuración de Apache es básicamente un proceso de tres pasos: instalar el software, activar las reescrituras y especificar `.htaccess` directivas.

### Instalación de Apache

1. Instale Apache 2.4 si aún no lo ha hecho.

   ```bash
   yum -y install httpd
   ```

1. Verifique la instalación:

   ```bash
   httpd -v
   ```

   Se muestran mensajes similares a los siguientes para confirmar que la instalación se ha realizado correctamente:

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Continúe con la siguiente sección.

   >[!NOTE]
   >
   >Incluso si Apache 2.4 se proporciona de forma predeterminada con CentOS, consulte la siguiente sección para configurarlo.

### Habilitar reescrituras y .htaccess para CentOS

1. Apertura `/etc/httpd/conf/httpd.conf` para editar:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Busque el bloque que empieza por:

   ```conf
   <Directory "/var/www/html">
   ```

1. Cambiar el valor de `AllowOverride` a `All`.

   Por ejemplo,

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >Los valores anteriores de `Order` puede que no funcione en todos los casos. Para obtener más información, consulte la documentación de Apache ([2,4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Guarde el archivo y salga del editor de texto.

1. Para aplicar la configuración de Apache, reinicie Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Si no se habilita esta configuración, normalmente no se mostrarán estilos en la tienda o en el administrador.

### Habilitar reescrituras y .htaccess para Ubuntu

1. Apertura `/etc/apache2/sites-available/default` para editar:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Busque el bloque que empieza por:

   `<Directory "/var/www/html">`

1. Cambiar el valor de `AllowOverride` a `All`.

   Por ejemplo:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Guarde el archivo y salga del editor de texto.

1. Configure Apache para que use el `mod_rewrite` módulo:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Reinicie Apache para aplicar los cambios:

   ```bash
   service apache2 restart
   ```

## Solución de errores 403 (prohibido)

Si encuentra errores prohibidos 403 al intentar acceder al sitio, puede actualizar la configuración de Apache o la configuración del host virtual para permitir que los visitantes accedan al sitio:

### Solución de errores 403 prohibidos en Apache 2.4

Para permitir que los visitantes del sitio web accedan al sitio, use una de las [Requerir directivas](https://httpd.apache.org/docs/2.4/howto/access.html).

Por ejemplo:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>Los valores anteriores de `Order` puede que no funcione en todos los casos. Para obtener más información, consulte la [Documentación de Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
