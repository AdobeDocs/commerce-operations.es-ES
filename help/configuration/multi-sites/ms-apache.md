---
title: Configuración de varios sitios web con Apache
description: Siga este tutorial para configurar varios sitios web con Apache.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Configuración de varios sitios web con Apache

Asumimos que:

Si es necesario, copie la `index.php` script de punto de entrada para su sitio web o [vista de tienda](https://glossary.magento.com/store-view) y agréguele lo siguiente:

- Está trabajando en una máquina de desarrollo (portátil, máquina virtual, etc.)

   Es posible que se necesiten tareas adicionales para implementar varios sitios web en un entorno alojado; consulte con su proveedor de alojamiento para obtener más información.

   Se requieren tareas adicionales para configurar Adobe Commerce en la infraestructura de la nube. Después de completar las tareas tratadas en este tema, consulte [Configuración de varios sitios web o tiendas](https://devdocs.magento.com/cloud/project/project-multi-sites.html) en el _guía del Commerce Cloud_.

- Utiliza un host virtual por sitio web; el archivo de configuración del host virtual es `/etc/httpd/httpd.conf`

   Las diferentes versiones de Apache en diferentes sistemas operativos configuran hosts virtuales de forma diferente. Consulte la [Documentación de Apache](https://httpd.apache.org/docs/2.4/vhosts) o un administrador de red si no está seguro de cómo configurar un host virtual.

- El software Commerce está instalado en `/var/www/html/magento2`
- Tiene dos sitios web que no son los predeterminados:

   - `french.mysite.mg` con código del sitio web `french` y almacenar código de vista `fr`
   - `german.mysite.mg` con código del sitio web `german` y almacenar código de vista `de`

## Hoja de ruta para configurar varios sitios web con Apache

La configuración de varias tiendas consiste en las siguientes tareas:

1. [Configuración de sitios web, tiendas y vistas de tiendas](ms-admin.md) en el menú
1. Crear una [Host virtual Apache](#step-2-create-apache-virtual-hosts) por sitio web de Commerce.

## Paso 1: Cree sitios web, tiendas y vistas de tiendas en el administrador

Consulte [Configure varios sitios web, tiendas y vistas de tienda en el administrador](ms-admin.md).

## Paso 2: Creación de hosts virtuales de Apache

En esta sección se explica cómo establecer valores para `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` uso de la variable del servidor Apache `SetEnvIf` en un host virtual.

Para obtener más información, consulte `SetEnvIf`, consulte:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Para crear hosts virtuales de Apache**:

1. Como usuario con `root` privilegios, abra el archivo de configuración de host virtual en un editor de texto.

   Por ejemplo, abra `/etc/httpd/conf/httpd.conf`

1. Busque la sección que comienza con `<VirtualHost *:80>`.
1. Cree los siguientes hosts virtuales después de cualquier host virtual existente:

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Guarde los cambios en `httpd.conf` y salga del editor de texto.
1. Reinicie Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

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
