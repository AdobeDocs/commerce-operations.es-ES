---
title: Configuración del compartimento de AWS S3 para almacenamiento remoto
description: Configure su proyecto de Commerce para utilizar el servicio de almacenamiento AWS S3 para el almacenamiento remoto.
feature: Configuration, Storage
exl-id: e8aeade8-2ec4-4844-bd6c-ab9489d10436
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Configuración del compartimento de AWS S3 para almacenamiento remoto

El [Amazon Simple Storage Service (Amazon S3)][AWS S3] es un servicio de almacenamiento de objetos que ofrece escalabilidad, disponibilidad de datos, seguridad y rendimiento líderes en el sector. El servicio AWS S3 utiliza contenedores para el almacenamiento de datos. Esta configuración requiere que cree un _privado_ cubo. Para obtener información sobre la infraestructura en la nube de Adobe Commerce, consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud](cloud-support.md).

>[!WARNING]
>
>El Adobe desalienta enormemente el uso de contenedores públicos porque plantea un grave riesgo para la seguridad.

**Para habilitar el almacenamiento remoto con el adaptador AWS S3**:

1. Inicie sesión en el tablero de Amazon S3 y cree una _privado_ cubo.

1. Configuración de [AWS IAM] funciones. También puede generar claves de acceso y de secreto.

1. Deshabilite el almacenamiento predeterminado de la base de datos.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configure Commerce para que utilice el bloque privado. Consulte [Opciones de almacenamiento remoto](remote-storage.md#remote-storage-options) para obtener una lista completa de los parámetros.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

1. Sincronizar archivos multimedia con almacenamiento remoto.

   ```bash
   bin/magento remote-storage:sync
   ```

## Configuración De Nginx

Nginx requiere una configuración adicional para realizar la autenticación con `proxy_pass` Directiva. Añada la siguiente información de proxy al `nginx.conf` archivo:

>nginx.conf

```conf
location ~* \.(ico|jpg|jpeg|png|gif|svg|js|css|swf|eot|ttf|otf|woff|woff2)$ {
    # Proxying to AWS S3 storage.
    resolver 8.8.8.8;
    set $bucket "<s3-bucket-name>";
    proxy_pass https://s3.amazonaws.com/$bucket$uri;
    proxy_pass_request_body off;
    proxy_pass_request_headers off;
    proxy_intercept_errors on;
    proxy_hide_header "x-amz-id-2";
    proxy_hide_header "x-amz-request-id";
    proxy_hide_header "x-amz-storage-class";
    proxy_hide_header "Set-Cookie";
    proxy_ignore_headers "Set-Cookie";
}
```

### Autenticación

Si utiliza acceso y claves secretas en lugar de [AWS IAM] funciones, debe incluir las siguientes funciones [`ngx_aws_auth` Módulo Nginx][ngx repo].

### Permisos

La integración de S3 depende de la capacidad de generar y almacenar imágenes en caché en el sistema de archivos local. Por lo tanto, permisos de carpeta para `pub/media` y directorios similares son los mismos para S3 que cuando se utiliza el almacenamiento local.

### Operaciones de archivo

Se recomienda encarecidamente que utilice [!DNL Commerce] métodos de adaptador de archivos en el desarrollo de codificación o extensión, independientemente del tipo de almacenamiento de archivos. Cuando utilice S3 para almacenamiento, no utilice operaciones de E/S de archivos PHP nativas, como `copy`, `rename`, o `file_put_contents`, porque los archivos S3 no se encuentran en el sistema de archivos. Consulte [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) para ejemplos de código.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
