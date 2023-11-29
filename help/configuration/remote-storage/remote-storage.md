---
title: Configurar almacenamiento remoto
description: Obtenga información sobre cómo configurar el módulo Almacenamiento remoto para la aplicación de comercio local.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Configurar almacenamiento remoto

El módulo Almacenamiento remoto proporciona la opción de almacenar archivos multimedia y programar importaciones y exportaciones en un contenedor de almacenamiento remoto persistente mediante un servicio de almacenamiento, como AWS S3. De forma predeterminada, la aplicación de Adobe Commerce almacena los archivos multimedia en el mismo sistema de archivos que contiene la aplicación. Esto no es eficaz para configuraciones complejas de varios servidores y puede provocar una reducción del rendimiento al compartir recursos. Con el módulo Almacenamiento remoto, puede almacenar archivos multimedia en el `pub/media` e importar/exportar archivos en el `var` del almacenamiento de objetos remotos para aprovechar el cambio de tamaño de las imágenes del lado del servidor.

>[!INFO]
>
>El almacenamiento remoto solo está disponible para la versión 2.4.2 y posteriores de Commerce. Consulte la [Notas de la versión 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>El módulo Almacenamiento remoto tiene _limitado_ compatibilidad con Adobe Commerce en la infraestructura en la nube. El Adobe no puede solucionar por completo el problema del servicio del adaptador de almacenamiento de terceros. Consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud](cloud-support.md) para obtener instrucciones sobre la implementación del almacenamiento remoto para proyectos en la nube.

![imagen de esquema](../../assets/configuration/remote-storage-schema.png)

## Opciones de almacenamiento remoto

Puede configurar el almacenamiento remoto mediante el `remote-storage` con la opción [`setup` comando CLI](../../installation/tutorials/deployment.md). El `remote-storage` utiliza la siguiente sintaxis:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

El `parameter-name` hace referencia al nombre del parámetro de almacenamiento remoto específico. En la tabla siguiente se enumeran los parámetros disponibles para configurar el almacenamiento remoto:

| Parámetro de línea de comandos | Nombre del parámetro | Descripción | Valor predeterminado |
|--- |--- |--- |--- |
| `remote-storage-driver` | conductor | Nombre del adaptador<br>Valores posibles:<br>**archivo**: deshabilita el almacenamiento remoto y utiliza el sistema de archivos local <br>**aws-s3**: utilice el [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | ninguno |
| `remote-storage-bucket` | cubo | Almacenamiento de objetos o nombre de contenedor | ninguno |
| `remote-storage-prefix` | prefijo | Prefijo opcional (ubicación dentro del almacenamiento de objetos) | vaciar |
| `remote-storage-region` | región | Nombre de región | ninguno |
| `remote-storage-key` | tecla de acceso | Clave de acceso opcional | vaciar |
| `remote-storage-secret` | clave secreta | Clave secreta opcional | vaciar |

### Adaptadores de almacenamiento

La ubicación de almacenamiento predeterminada se encuentra en el sistema de archivos local. A _adaptador de almacenamiento_ le permite conectarse a un servicio de almacenamiento y almacenar sus archivos en cualquier lugar. [!DNL Commerce] admite la configuración de los siguientes servicios de almacenamiento:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Habilitar almacenamiento remoto

Puede instalar el almacenamiento remoto durante una instalación de Adobe Commerce o agregar almacenamiento remoto a una instancia de Commerce existente. Los siguientes ejemplos muestran cada método utilizando un conjunto de `remote-storage` Parámetros de con Commerce `setup` Comandos CLI. Como mínimo, debe proporcionar el almacenamiento `driver`, `bucket`, y `region`.

- Ejemplo: Instalación de Commerce con almacenamiento remoto

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Ejemplo: Habilitar el almacenamiento remoto en Commerce existente

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Para obtener información sobre la infraestructura en la nube de Adobe Commerce, consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud](cloud-support.md).

## Limitaciones

No puede tener habilitados simultáneamente el almacenamiento remoto y el almacenamiento de base de datos. Deshabilite el almacenamiento de la base de datos si utiliza el almacenamiento remoto.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Si habilita el almacenamiento remoto, podría afectar a su experiencia de desarrollo establecida. Por ejemplo, algunas funciones de archivo PHP podrían no funcionar como se esperaba. Se debe aplicar el uso de Commerce Framework para operaciones de archivo.

La lista de funciones nativas de PHP prohibidas está disponible en [repositorio magento-coding-standard][code-standard].

## Migrar contenido

Después de habilitar el almacenamiento remoto para un adaptador específico, puede utilizar la CLI para migrar los recursos existentes _medios_ archivos al almacenamiento remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>El comando sync solo migra archivos en la variable `pub/media` directorio, _no_ los archivos de importación y exportación de la `var` directorio. Consulte [Importación/Exportación programada](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) en el _Guía del usuario de Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[code-standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
