---
title: Configuración de barniz para comercio
description: Aprenda a actualizar y administrar su archivo de configuración de Varnish para la aplicación Commerce.
source-git-commit: d451ea025a6f4fc8a4a9f15ca83896a63058a3a0
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Configuración de la aplicación Commerce para utilizar Varnish

Para configurar Commerce para utilizar Varnish:

1. Inicie sesión en Admin como administrador.
1. Haga clic en **[!UICONTROL Stores]** > Configuración > **Configuración** > **Avanzadas** > **Sistema** > **Caché de página completa**.
1. En el **[!UICONTROL Caching Application]** lista, haga clic en **Almacenamiento en caché de barnices**.
1. Introduzca un valor en la variable **[!UICONTROL TTL for public content]** campo .
1. Expandir **[!UICONTROL Varnish Configuration]** e introduzca la siguiente información:

   | Campo | Descripción |
   | ----- | ----------- |
   | Lista de acceso | Introduzca el nombre de host completo, la dirección IP o [Enrutamiento entre dominios sin clase (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) rango de direcciones IP de notación para el cual se va a invalidar contenido. Consulte [Depuración de caché de barniz](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host back-end | Introduzca el nombre de host o la dirección IP completa y el puerto de escucha de Varnish. _backend_ o _servidor de origen_; es decir, el servidor que proporciona el contenido se acelera. Normalmente, este es su servidor web. Consulte [Servidores back-end de la caché de Varnish](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Puerto back-end | Puerto de escucha del servidor de origen. |
   | Período de gracia | El período de gracia determina cuánto tiempo Varnish sirve contenido obsoleto si el servidor no responde. El valor predeterminado es 300 segundos. |

1. Haga clic en **Guardar configuración**.

También puede activar Varnish desde la línea de comandos (en lugar de iniciar sesión en el administrador) mediante la herramienta de interfaz de línea de comandos C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Exportación de un archivo de configuración de barniz

Para exportar un archivo de configuración de Varnish desde el administrador:

1. Haga clic en uno de los botones de exportación para crear una `varnish.vcl` puede usar con Varnish.

   Por ejemplo, si tiene Varnish 4, haga clic en **Exportar VCL para Varniz 4**

   La siguiente figura muestra un ejemplo:

   ![Configuración de Commerce para utilizar Varnish en el Administrador](../../assets/configuration/varnish-admin-22.png)

1. Haga una copia de seguridad de su `default.vcl`. A continuación, cambie el nombre del `varnish.vcl` archivo que acaba de exportar a `default.vcl`. A continuación, copie el archivo en el `/etc/varnish/` directorio.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe le recomienda que abra `default.vcl` y cambiar el valor de `acl purge` a la dirección IP del host de Varnish. (Puede especificar varios hosts en líneas separadas o también puede utilizar la notación CIDR).

   Por ejemplo,

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Si desea personalizar las comprobaciones de estado de Vagrant o la configuración del modo de gracia o del modo de santo, consulte [Configuración avanzada de barniz](config-varnish-advanced.md).

1. Reinicie Varnish y su servidor web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Almacenar en caché archivos estáticos

Los archivos estáticos no deben almacenarse en caché de forma predeterminada, pero si desea almacenarlos en caché, puede editar la sección `Static files caching` en la VCL para tener el siguiente contenido:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

Debe realizar estos cambios antes de configurar Commerce para utilizar Varnish.
