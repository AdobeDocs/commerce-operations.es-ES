---
title: Apache
description: Siga estos pasos para instalar y configurar el servidor web Apache para las instalaciones locales de Adobe Commerce.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce admite Apache 2.4.x.

## Directivas requeridas por Apache

1. Establezca `AllowEncodedSlashes` en la configuración del servidor (de forma global) o en las configuraciones del host virtual para evitar descodificar las barras oblicuas codificadas que puedan causar problemas en las direcciones URL. Por ejemplo, al recuperar productos con una barra oblicua en el SKU mediante la API, no desea que se conviertan. El bloque de muestra no está completo y se requieren otras directivas.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache reescribe y htaccess

En este tema se explica cómo habilitar las reescrituras de Apache 2.4 y especificar una configuración para el [archivo de configuración distribuida, `.htaccess`](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample).

Adobe Commerce usa las reescrituras del servidor y `.htaccess` para proporcionar instrucciones a nivel de directorio para Apache. Las siguientes instrucciones se incluyen también en todas las demás secciones de este tema.

Utilice esta sección para habilitar las reescrituras de Apache 2.4 y especificar una configuración para el [archivo de configuración distribuido, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce usa las reescrituras del servidor y `.htaccess` para proporcionar instrucciones a nivel de directorio para Apache.

>[!NOTE]
>
>Si no se habilita esta configuración, no se muestran estilos en la tienda o el administrador.

1. Habilite el módulo de reescritura de Apache:

   ```bash
   a2enmod rewrite
   ```

1. Para permitir que la aplicación use el archivo de configuración distribuido `.htaccess`, consulte las directrices en la [documentación de Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >En Apache 2.4, el archivo de configuración de sitio predeterminado del servidor es `/etc/apache2/sites-available/000-default.conf`.

   Por ejemplo, puede agregar lo siguiente al final de `000-default.conf`:

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >A veces, pueden ser necesarios parámetros adicionales. Para obtener más información, consulte la [documentación de Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Si ha cambiado la configuración de Apache, reinicie Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Si ha actualizado desde una versión anterior de Apache, busque primero `<Directory "/var/www/html">` o `<Directory "/var/www">` en `000-default.conf`.
   >- Debe cambiar el valor de `AllowOverride` en la directiva del directorio en el que espera instalar el software de Adobe Commerce. Por ejemplo, para instalar en el servidor web docroot, edite la directiva en `<Directory /var/www>`.

>[!NOTE]
>
>Si no se habilita esta configuración, los estilos no se mostrarán en la tienda ni en el administrador.

## Módulos requeridos por Apache

Adobe Commerce requiere que se instalen los siguientes módulos Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verifique la versión de Apache

Para verificar la versión de Apache que está ejecutando actualmente, introduzca:

```bash
apache2 -v
```

El resultado es similar al siguiente:

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Si Apache está *no* instalado, consulte:
   - [Instalación o actualización de Apache en Ubuntu](#installing-apache-on-ubuntu)
   - [Instalación de Apache en CentOS](#installing-apache-on-centos)

## Instalación o actualización de Apache en Ubuntu

Las siguientes secciones tratan sobre cómo instalar o actualizar Apache:

- Instalar Apache
- Actualice a Apache 2.4 en Ubuntu para utilizar PHP 7.4.

### Instalación de Apache en Ubuntu

Para instalar la versión predeterminada de Apache:

1. Instalar Apache

   ```bash
   apt-get -y install apache2
   ```

1. Compruebe la instalación.

   ```bash
   apache2 -v
   ```

   El resultado es similar al siguiente:

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Habilite [reescrituras y `.htaccess`](#apache-rewrites-and-htaccess).

### Actualización de Apache a Ubuntu

Para actualizar a Apache 2.4:

1. Agregue el repositorio `ppa:ondrej`, que tiene Apache 2.4:

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

1. Compruebe la instalación.

   ```bash
   apache2 -v
   ```

   Se deben mostrar mensajes similares a los siguientes:

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Habilite [reescrituras y `.htaccess`](#apache-rewrites-and-htaccess).

## Instalación de Apache en CentOS

Adobe Commerce requiere reescrituras del servidor Apache. También debe especificar el tipo de directivas que se pueden usar en `.htaccess`, que la aplicación usa para especificar reglas de reescritura.

La instalación y configuración de Apache es básicamente un proceso de tres pasos: instalar el software, habilitar las reescrituras y especificar `.htaccess` directivas.

### Instalación de Apache

1. Instale Apache 2.4 si aún no lo ha hecho.

   ```bash
   yum -y install httpd
   ```

1. Compruebe la instalación:

   ```bash
   httpd -v
   ```

   Se muestran mensajes similares a los siguientes para confirmar que la instalación se ha realizado correctamente:

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Continúe con la siguiente sección.

   >[!NOTE]
   >
   >Incluso si Apache 2.4 se proporciona de forma predeterminada con CentOS, consulte la siguiente sección para configurarlo.

### Habilitar reescrituras y .htaccess para CentOS

1. Abrir `/etc/httpd/conf/httpd.conf` archivo para editar:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Busque el bloque que comienza con:

   ```conf
   <Directory "/var/www/html">
   ```

1. Cambie el valor de `AllowOverride` a `All`.

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
   >Es posible que los valores anteriores de `Order` no funcionen en todos los casos. Para obtener más información, consulte la documentación de Apache ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Guarde el archivo y salga del editor de texto.

1. Para aplicar la configuración de Apache, reinicie Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Si no se habilita esta configuración, no se muestran estilos en la tienda o el administrador.

### Habilitar reescrituras y .htaccess para Ubuntu

1. Abrir `/etc/apache2/sites-available/default` archivo para editar:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Busque el bloque que comienza con:

   `<Directory "/var/www/html">`

1. Cambie el valor de `AllowOverride` a `All`.

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

1. Configure Apache para que use el módulo `mod_rewrite`:

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

Si encuentra errores 403 prohibidos al intentar acceder al sitio, puede actualizar la configuración de Apache o la configuración del host virtual para permitir a los visitantes del sitio:

### Solución de errores 403 prohibidos para Apache 2.4

Para permitir que los visitantes del sitio web accedan al sitio, use una de las [Directivas de requisitos](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>Es posible que los valores anteriores de `Order` no funcionen en todos los casos. Para obtener más información, consulte la [documentación de Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
