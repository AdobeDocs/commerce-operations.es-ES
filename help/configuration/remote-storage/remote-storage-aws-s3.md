---
title: Configuración de AWS S3 bucket para almacenamiento remoto
description: Configure su proyecto de Commerce para utilizar el servicio de almacenamiento AWS S3 para almacenamiento remoto.
source-git-commit: 9a5993c9a65ad210f1a9682734730f235bbc3d44
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Configuración de AWS S3 bucket para almacenamiento remoto

La variable [Amazon Simple Storage Service (Amazon S3)][AWS S3] es un servicio de almacenamiento de objetos que ofrece escalabilidad, disponibilidad, seguridad y performance líderes en la industria. El servicio AWS S3 utiliza contenedores o contenedores para el almacenamiento de datos. Esta configuración requiere que cree un _private_ cubo. Para obtener Adobe Commerce sobre la infraestructura de nube, consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud](cloud-support.md).

>[!WARNING]
>
>El Adobe desalienta enormemente el uso de baldes públicos porque plantea un grave riesgo para la seguridad.

**Para habilitar el almacenamiento remoto con el adaptador AWS S3**:

1. Inicie sesión en el panel de Amazon S3 y cree un _private_ cubo.

1. Configuración [AWS IAM] funciones. Como alternativa, genere claves de acceso y de secreto.

1. Deshabilite el almacenamiento predeterminado de la base de datos.

   ```bash
   bin/magento config:set system/media_storage_configuration/media_database 0
   ```

1. Configure Commerce para utilizar el compartimento privado. Consulte [Opciones de almacenamiento remoto](remote-storage.md#remote-storage-options) para obtener una lista completa de los parámetros.

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="<bucket-name>" --remote-storage-region="<region-name>" --remote-storage-prefix="<optional-prefix>" --remote-storage-key=<optional-access-key> --remote-storage-secret=<optional-secret-key> -n
   ```

## Configurar Nginx

Nginx requiere una configuración adicional para realizar la autenticación con la variable `proxy_pass` directiva. Agregue la siguiente información del proxy al `nginx.conf` archivo:

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

Si utiliza claves de acceso y secreto en lugar de [AWS IAM] , debe incluir el [`ngx_aws_auth` Módulo Nginx][ngx repo].

### Permisos

La integración de S3 depende de la capacidad de generar y almacenar imágenes en caché en el sistema de archivos local. Por lo tanto, los permisos de carpeta de `pub/media` y directorios similares son los mismos para S3 que cuando se utiliza almacenamiento local.

### Operaciones de archivo

Se recomienda encarecidamente que utilice [!DNL Commerce] métodos del adaptador de archivos en el desarrollo de la codificación o extensión, independientemente del tipo de almacenamiento de archivos. Cuando utilice S3 para almacenamiento, no utilice operaciones nativas de E/S de archivos PHP, como `copy`, `rename`o `file_put_contents`, ya que los archivos S3 no se encuentran en el sistema de archivos. Consulte [DriverInterface.php](https://github.com/magento/magento2/blob/2.4-develop/lib/internal/Magento/Framework/Filesystem/DriverInterface.php#L18) para ver ejemplos de código.

<!-- link definitions -->

[AWS S3]: https://aws.amazon.com/s3
[AWS IAM]: https://aws.amazon.com/iam/
[ngx repo]: https://github.com/anomalizer/ngx_aws_auth
