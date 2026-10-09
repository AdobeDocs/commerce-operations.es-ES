---
title: Configurar el cambio de tamaño de la imagen para almacenamiento remoto
description: Optimice los recursos de disco configurando el cambio de tamaño de las imágenes del lado del servidor.
feature: Configuration, Storage
exl-id: 51c2b9b3-0f5f-4868-9191-911d5df341ec
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%
---
# Configurar el cambio de tamaño de la imagen para almacenamiento remoto

De forma predeterminada, Adobe Commerce admite el cambio de tamaño de las imágenes en la aplicación. Sin embargo, al habilitar el módulo Almacenamiento remoto, puede utilizar Nginx para descargar el cambio de tamaño de la imagen en el servidor, donde puede ahorrar recursos de disco y optimizar el uso del disco.

El diagrama siguiente muestra cómo Nginx recupera, cambia de tamaño y almacena imágenes en la caché. El cambio de tamaño viene determinado por los parámetros incluidos en la dirección URL, como la altura y la anchura.

![Cambio de tamaño de la imagen de almacenamiento remoto mostrando la configuración del bloque de servidor](../../assets/configuration/remote-storage-nginx-image-resize.png)

>[!TIP]
>
>Para Adobe Commerce sobre proyectos de infraestructura en la nube, consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura en la nube](cloud-support.md)

## Configuración del formato de URL en Adobe Commerce

Para cambiar el tamaño de las imágenes en el servidor, debe configurar Adobe Commerce para que proporcione argumentos para la altura, la anchura y la ubicación (URL) de la imagen.

**Para configurar Commerce para cambiar el tamaño de las imágenes del lado del servidor**:

1. En el panel _Admin_, haga clic en **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**.

1. En el panel derecho, expanda **[!UICONTROL Url options]**.

1. En la sección _Formato de URL de medios de catálogo_, borre **[!UICONTROL Use system value]**.

1. Seleccione la URL `Image optimization based on query parameters` en el campo **_Formato de URL de medios del catálogo_**.

1. Haga clic en **[!UICONTROL Save Config]**.

1. Continúe con la [configuración de Nginx](#configure-nginx).

## Configuración De Nginx

Para seguir configurando el cambio de tamaño de las imágenes del lado del servidor, debe preparar el archivo `nginx.conf` y proporcionar un valor `proxy_pass` para el adaptador seleccionado.

**Para permitir que Nginx cambie el tamaño de las imágenes**:

1. Instale [Nginx image filter module](https://nginx.org/en/docs/http/ngx_http_image_filter_module.html).

   ```shell
   load_module /etc/nginx/modules/ngx_http_image_filter_module.so;
   ```

1. Crear un archivo de `nginx.conf` basado en el archivo de plantilla `nginx.conf.sample` incluido. Por ejemplo:

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

1. [_Opcional_] Configure un valor de `proxy_pass` para su adaptador específico.

   - [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

