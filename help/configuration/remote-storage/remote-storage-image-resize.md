---
title: Configurar el cambio de tamaño de la imagen para el almacenamiento remoto
description: Optimice los recursos de disco configurando el cambio de tamaño de las imágenes del lado del servidor.
source-git-commit: 7fc5d561baa3c2a4aab160a35a1c8a302a62a3b1
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

---

# Configurar el cambio de tamaño de la imagen para el almacenamiento remoto

De forma predeterminada, Adobe Commerce admite el cambio de tamaño de imágenes en la aplicación. Sin embargo, al habilitar el módulo Almacenamiento remoto, puede utilizar Nginx para descargar el cambio de tamaño de la imagen en el servidor, donde puede guardar recursos de disco y optimizar el uso del disco.

El diagrama siguiente muestra cómo Nginx recupera, cambia de tamaño y almacena las imágenes en la caché. El cambio de tamaño viene determinado por los parámetros incluidos en la dirección URL, como la altura y la anchura.

![cambiar tamaño de imagen](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Para Adobe Commerce en proyectos de infraestructura en la nube, consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud](cloud-support.md)

## Configuración del formato de URL en Adobe Commerce

Para cambiar el tamaño de las imágenes en el servidor, debe configurar Adobe Commerce para que proporcione argumentos sobre la altura, la anchura y la ubicación (URL) de la imagen.

**Para configurar Commerce para el cambio de tamaño de imágenes del lado del servidor**:

1. En el _Administrador_ panel, haga clic en **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. En el panel derecho, expanda **[!UICONTROL Url options]**.

1. En el _Formato de URL de contenido del catálogo_ sección, borrar **[!UICONTROL Use system value]**.

1. Seleccione el `Image optimization based on query parameters` La URL de **_Formato de URL de contenido del catálogo_** campo .

1. Haga clic **[!UICONTROL Save Config]**.

1. Continúe con el [Configuración de Nginx](#configure-nginx).

## Configurar Nginx

Para continuar configurando el cambio de tamaño de la imagen del lado del servidor, debe preparar la variable `nginx.conf` y proporcione un `proxy_pass` para el adaptador elegido.

**Para permitir que Nginx cambie el tamaño de las imágenes**:

1. Instale el [Módulo de filtro de imagen Nginx][nginx-module].

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Cree un `nginx.conf` basado en la plantilla incluida `nginx.conf.sample` archivo. Por ejemplo:

   ```conf
   location ~* \.(jpg|jpeg|png|gif|webp)$ {
       set $width "-";
       set $height "-";
       if ($arg_width != '') {
           set $width $arg_width;
       }
       if ($arg_height != '') {
           set $height $arg_height;
       }
       image_filter resize $width $height;
       image_filter_jpeg_quality 90;
   }
   ```

1. [_Opcional_] Configure un `proxy_pass` para su adaptador específico.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

<!-- link definitions -->

[nginx-module]: https://nginx.org/en/docs/http/ngx_http_image_filter_module.html
