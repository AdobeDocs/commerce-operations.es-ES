---
title: Instalación de Apache para implementaciones locales
description: Obtenga información sobre cómo instalar y configurar Apache para implementaciones locales de Adobe Commerce. Habilite los módulos, las reescrituras y la configuración ".htaccess" necesarios.
feature: Install, Configuration
badgePaas: label="On-Premise" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# Instalación de Apache para implementaciones locales {#apache}

Esta guía le explica cómo instalar Apache para Adobe Commerce en implementaciones locales y cómo configurar Apache que Commerce requiere. Incluye requisitos compartidos de Apache y procedimientos específicos del sistema operativo para Ubuntu y CentOS. Adobe recomienda seguir las instrucciones de configuración proporcionadas en esta guía para conservar la funcionalidad y la seguridad de la aplicación de Commerce.

Adobe es compatible con las versiones de Apache enumeradas en [requisitos del sistema](../../system-requirements.md) para su versión de Adobe Commerce. Las versiones compatibles varían según la versión. Apache también requiere una configuración de PHP compatible. Para ver los requisitos de PHP relacionados, consulte [Configuración de PHP](../php-settings.md).

Comience con la sección que coincida con su entorno:

- Si Apache ya está instalado, comience con [Revisar los requisitos de Apache](#review-apache-requirements).
- Si necesita instalar o actualizar Apache en Ubuntu, vaya a [Instalar o actualizar Apache en Ubuntu](#installing-or-upgrading-apache-on-ubuntu).
- Si necesita instalar Apache en CentOS, vaya a [Instalar Apache en CentOS](#installing-apache-on-centos).

## Revise los requisitos de Apache

Complete estos requisitos en cualquier servidor Apache que aloje Adobe Commerce.

### Configuración de directivas requeridas

Establezca `AllowEncodedSlashes` en la configuración del servidor (de forma global) o en las configuraciones del host virtual para evitar descodificar las barras oblicuas codificadas que pueden causar problemas en las direcciones URL. Por ejemplo, al recuperar productos con una barra oblicua en el SKU mediante la API, no desea que se convierta la barra oblicua. El siguiente bloque de ejemplo no está completo y se requieren otras directivas.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Configurar reescrituras y .htaccess {#apache-rewrites-and-htaccess}

Utilice esta sección para habilitar las reescrituras de Apache y configurar el archivo [distribuido `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html). Adobe Commerce usa las reescrituras del servidor y `.htaccess` para proporcionar instrucciones a nivel de directorio para Apache.

>[!IMPORTANT]
>
>Si no se habilita esta configuración, no se muestran estilos en la tienda o el administrador. También puede impedir que Apache aplique las protecciones de seguridad de Adobe Commerce definidas en `.htaccess`.

1. Habilite el módulo de reescritura de Apache:

   ```shell
   a2enmod rewrite
   ```

1. Habilite la aplicación para utilizar el archivo de configuración distribuido `.htaccess`.

   1. En Ubuntu, edite `/etc/apache2/sites-available/000-default.conf`. Para otros diseños de Apache o si se requieren parámetros adicionales, consulte la [documentación de Apache](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) y la [documentación de control de acceso de Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Agregue o actualice la directiva `AllowOverride` para el directorio en el que planea instalar Adobe Commerce.

   Por ejemplo, si instala Adobe Commerce en el `docroot` predeterminado, agregue el siguiente bloque a `000-default.conf`:

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Si ha actualizado desde una versión anterior de Apache, busque primero un bloque `<Directory "/var/www/html">` o `<Directory "/var/www">` existente en `000-default.conf`. Si instala Adobe Commerce en un(a) `docroot` diferente, actualice el bloque `<Directory>` correspondiente para esa ruta.

1. Reinicie Apache para aplicar los cambios:

   ```shell
   service apache2 restart
   ```

### Instalación de los módulos necesarios

Adobe Commerce requiere que se instalen los siguientes módulos Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verificar que Apache esté instalado

Para comprobar que Apache está instalado y ver la versión actual, introduzca:

```shell
apache2 -v
```

El resultado muestra información similar a la siguiente:

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Si Apache está *no* instalado, consulte:
   - [Instalación o actualización de Apache en Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Instalación de Apache en CentOS](#installing-apache-on-centos)

## Instalación o actualización de Apache en Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

La instalación y configuración de Apache en Ubuntu es un proceso de tres pasos:

1. Instale el software.
1. Habilitar reescrituras.
1. Especifique `.htaccess` directivas.

Al configurar las reescrituras del servidor Apache, debe especificar el tipo de directivas que se pueden utilizar en `.htaccess`, que la aplicación utiliza para especificar reglas de reescritura y protecciones de seguridad.

### Instalar Apache en Ubuntu

1. Instale Apache si aún no lo ha hecho:

   ```shell
   apt-get -y install apache2
   ```

1. Compruebe la instalación:

   ```shell
   apache2 -v
   ```

   Se muestran mensajes similares a los siguientes para confirmar que la instalación se ha realizado correctamente:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Continúe con la siguiente sección.

   >[!NOTE]
   >
   >Incluso si Apache se proporciona de forma predeterminada con Ubuntu, consulte la siguiente sección para configurarlo.

### Actualizar Apache en Ubuntu

Si Apache ya está instalado y utiliza una versión anterior a `2.4`, actualice a Apache `2.4` o a la versión más reciente compatible con la versión de Adobe Commerce que haya implementado. Consulte [requisitos del sistema](../../system-requirements.md).

1. Actualizar información del paquete:

   ```shell
   apt-get -y update
   ```

1. Añada un repositorio que proporcione una versión de Apache compatible para su entorno, si es necesario.

1. Instale o actualice Apache:

   ```shell
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Si el comando `apt-get install` falla debido a dependencias no satisfechas, consulte la documentación del paquete del sistema operativo o los recursos de soporte de distribución.

1. Compruebe la instalación:

   ```shell
   apache2 -v
   ```

1. Confirme que la versión instalada coincide con la versión compatible con su versión de Adobe Commerce en [requisitos del sistema](../../system-requirements.md).

1. Habilite [reescrituras y `.htaccess` para Ubuntu](#enable-rewrites-and-htaccess-for-ubuntu).

### Habilitar reescrituras y .htaccess para Ubuntu

1. Abra el archivo `/etc/apache2/sites-available/000-default.conf` para editarlo:

   ```shell
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Busque el bloque que comienza con:

   ```conf
   <Directory "/var/www/html">
   ```

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

   ```shell
   cd /etc/apache2/mods-enabled
   ```

   ```shell
   ln -s ../mods-available/rewrite.load
   ```

1. Reinicie Apache para aplicar los cambios:

   ```shell
   service apache2 restart
   ```

>[!IMPORTANT]
>
>Si no se habilita esta configuración, no se muestran estilos en la tienda o el administrador. También puede impedir que Apache aplique las protecciones de seguridad de Adobe Commerce definidas en `.htaccess`.

## Instalación de Apache en CentOS {#installing-apache-on-centos}

La instalación y configuración de Apache en CentOS es un proceso de tres pasos:

1. Instalación del software
2. Habilitar reescrituras
3. Especifique `.htaccess` directivas.

Al configurar las reescrituras del servidor Apache, debe especificar el tipo de directivas que se pueden utilizar en `.htaccess`, que la aplicación utiliza para especificar reglas de reescritura y protecciones de seguridad.

### Instalación de Apache

1. Instale Apache si aún no lo ha hecho.

   ```shell
   yum -y install httpd
   ```

1. Compruebe la instalación:

   ```shell
   httpd -v
   ```

   Se muestran mensajes similares a los siguientes para confirmar que la instalación se ha realizado correctamente:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Continúe con la siguiente sección.

   >[!NOTE]
   >
   >Incluso si Apache se proporciona de forma predeterminada con CentOS, consulte la siguiente sección para configurarlo.

### Habilitar reescrituras y .htaccess para CentOS

1. Abra el archivo `/etc/httpd/conf/httpd.conf` para editarlo:

   ```shell
   vim /etc/httpd/conf/httpd.conf
   ```

1. Busque el bloque que comienza con:

   ```conf
   <Directory "/var/www/html">
   ```

1. Cambie el valor de `AllowOverride` a `All`.

   Por ejemplo:

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
   >Es posible que los valores anteriores de `Order` no funcionen en todos los casos. Para obtener más información, consulte la [documentación de Apache](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Guarde el archivo y salga del editor de texto.

1. Para aplicar la configuración de Apache, reinicie Apache.

   ```shell
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>Si no se habilita esta configuración, no se muestran estilos en la tienda o el administrador. También puede impedir que Apache aplique las protecciones de seguridad de Adobe Commerce definidas en `.htaccess`.

## Solución de errores 403 (prohibido)

Si encuentra errores 403 prohibidos al intentar acceder al sitio, puede actualizar la configuración de Apache o la configuración del host virtual para permitir a los visitantes del sitio:

### Solución de errores 403 prohibidos para Apache

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
