---
title: Configuración de varios sitios web con Apache
description: Siga este tutorial para configurar varios sitios web con Apache.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Configuración de varios sitios web con Apache

Suponemos que:

Si es necesario, copie el script de punto de entrada `index.php` existente para su sitio web o vista de tienda y agréguele lo siguiente:

- Está trabajando en una máquina de desarrollo (portátil, máquina virtual, etc.)

  Es posible que se requieran tareas adicionales para implementar varios sitios web en un entorno alojado; póngase en contacto con su proveedor de alojamiento para obtener más información.

  Se requieren tareas adicionales para configurar Adobe Commerce en la infraestructura en la nube. Después de completar las tareas que se describen en este tema, vea [Configurar varios sitios web o tiendas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=es) en la guía _Commerce en infraestructura de nube_.

- Utiliza un host virtual por sitio web; el archivo de configuración del host virtual es `/etc/httpd/httpd.conf`

  Las distintas versiones de Apache en diferentes sistemas operativos configuran los hosts virtuales de forma diferente. Consulte la [documentación de Apache](https://httpd.apache.org/docs/2.4/vhosts) o con un administrador de red si no está seguro de cómo configurar un host virtual.

- El software de Commerce está instalado en `/var/www/html/magento2`
- Tiene dos sitios web distintos del predeterminado:

   - `french.mysite.mg` con código de sitio web `french` y código de vista de tienda `fr`
   - `german.mysite.mg` con código de sitio web `german` y código de vista de tienda `de`

## Guía para configurar varios sitios web con Apache

La configuración de varios almacenes consta de las siguientes tareas:

1. [Configurar sitios web, tiendas y vistas de tiendas](ms-admin.md) en el administrador.
1. Cree un [host virtual Apache](#step-2-create-apache-virtual-hosts) por sitio web de Commerce.

## Paso 1: crear sitios web, tiendas y vistas de tiendas en el administrador

Ver [Configurar varios sitios web, tiendas y vistas de tiendas en el administrador](ms-admin.md).

## Paso 2: Crear hosts virtuales de Apache

En esta sección se explica cómo establecer los valores de `MAGE_RUN_TYPE` y `MAGE_RUN_CODE` mediante la variable del servidor Apache `SetEnvIf` en un host virtual.

Para obtener más información sobre `SetEnvIf`, consulte:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Para crear hosts virtuales Apache**:

1. Como usuario con privilegios de `root`, abra el archivo de configuración del host virtual en un editor de texto.

   Por ejemplo, abra `/etc/httpd/conf/httpd.conf`

1. Busque la sección que comience por `<VirtualHost *:80>`.
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
>- Se requieren tareas adicionales para configurar Adobe Commerce en la infraestructura en la nube. Consulte [Configurar varios sitios web o tiendas en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=es) en la guía _Commerce en la infraestructura en la nube_.

### Resolución de problemas

- Si tus sitios en francés y alemán devuelven 404s pero tu administrador carga, asegúrate de completar [Paso 6: Agrega el código de la tienda a la URL base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Si todas las direcciones URL devuelven 404, asegúrese de reiniciar el servidor web.
- Si el administrador no funciona correctamente, asegúrese de configurar correctamente los hosts virtuales.
