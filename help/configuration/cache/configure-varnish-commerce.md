---
title: Configuración de Barniz para Commerce
description: Obtenga información sobre cómo actualizar y administrar el archivo de configuración de Barniz para la aplicación Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Configure la aplicación Commerce para utilizar Barniz

Para configurar Commerce para que utilice Barniz:

1. Inicie sesión en el administrador como administrador.
1. Clic **[!UICONTROL Stores]** > Configuración > **Configuración** > **Avanzadas** > **Sistema** > **Caché de página completa**.
1. Desde el **[!UICONTROL Caching Application]** , haga clic en **Almacenamiento en caché de barniz**.
1. Introduzca un valor en la variable **[!UICONTROL TTL for public content]** field.
1. Expandir **[!UICONTROL Varnish Configuration]** e introduzca la siguiente información:

   | Campo | Descripción |
   | ----- | ----------- |
   | Lista de acceso | Introduzca el nombre de host completo, la dirección IP o [Enrutamiento entre dominios sin clase (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) intervalo de direcciones IP de notación para el que se va a invalidar el contenido. Consulte [Depuración de caché de barniz](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host back-end | Introduzca el nombre de host completo o la dirección IP y el puerto de escucha del barniz _servidor_ o _servidor de origen_; es decir, el servidor que proporciona el contenido que Barnish acelera. Normalmente, es su servidor web. Consulte [Servidores back-end de caché de barniz](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Puerto back-end | Puerto de escucha del servidor de origen. |
   | Período de gracia | El periodo de gracia determina cuánto tiempo sirve Barnish al contenido obsoleto si el backend no responde. El valor predeterminado es 300 segundos. |

1. Clic **Guardar configuración**.

También puede activar Varnish desde la línea de comandos, en lugar de iniciar sesión en Admin, mediante la herramienta de interfaz de línea de comandos de C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportar un archivo de configuración de barniz

Para exportar un archivo de configuración de Barniz desde Admin:

1. Haga clic en uno de los botones de exportación para crear una `varnish.vcl` se puede usar con Barnish.

   Por ejemplo, si tiene Barniz 4, haga clic en **Exportar VCL para Barniz 4**

   La siguiente figura muestra un ejemplo:

   ![Configuración de Commerce para utilizar Barniz en el administrador](../../assets/configuration/varnish-admin-22.png)

1. Haga una copia de seguridad de los existentes `default.vcl`. A continuación, cambie el nombre `varnish.vcl` archivo al que acaba de exportar `default.vcl`. A continuación, copie el archivo en la `/etc/varnish/` directorio.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. El Adobe recomienda abrir `default.vcl` y cambie el valor de `acl purge` a la dirección IP del host de Varnish. (Puede especificar varios hosts en líneas independientes o también puede utilizar la notación CIDR).

   Por ejemplo,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Si desea personalizar las comprobaciones de estado de Vagrant para la configuración del modo de gracia o del modo de san, consulte [Configuración avanzada de barniz](config-varnish-advanced.md).

1. Reinicie Varnish y su servidor web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Archivos estáticos de caché

Los archivos estáticos no deben almacenarse en caché de forma predeterminada, pero si desea almacenarlos, puede editar la sección `Static files caching` en la VCL para que tenga el siguiente contenido:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Debe realizar estos cambios antes de configurar Commerce para que utilice Barnish.
