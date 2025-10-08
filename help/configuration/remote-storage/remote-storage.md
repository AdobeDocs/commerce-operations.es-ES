---
title: Configurar almacenamiento remoto
description: Obtenga información sobre cómo configurar el módulo Almacenamiento remoto para la aplicación Commerce local.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Configurar almacenamiento remoto

El módulo Almacenamiento remoto proporciona la opción de almacenar archivos multimedia y programar importaciones y exportaciones en un contenedor de almacenamiento remoto persistente mediante un servicio de almacenamiento, como AWS S3.

De forma predeterminada, la aplicación de Adobe Commerce almacena los archivos multimedia en el mismo sistema de archivos que contiene la aplicación. Esto no es eficaz para configuraciones complejas de varios servidores y puede provocar una reducción del rendimiento al compartir recursos. Con el módulo Almacenamiento remoto, puede almacenar archivos multimedia en el directorio `pub/media` e importar o exportar archivos en el directorio `var` del almacenamiento de objetos remotos para aprovechar el cambio de tamaño de las imágenes del lado del servidor.

>[!BEGINSHADEBOX]

No puede tener habilitado simultáneamente el almacenamiento remoto _y el almacenamiento de la base de datos_. Debe deshabilitar el almacenamiento de la base de datos antes de habilitar el almacenamiento remoto.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Si habilita el almacenamiento remoto, podría afectar a su experiencia de desarrollo establecida. Por ejemplo, algunas funciones de archivo PHP podrían no funcionar como se esperaba. Se debe aplicar el uso de Commerce Framework para operaciones de archivo. La lista de funciones nativas de PHP prohibidas está disponible en el repositorio [magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php).

>[!ENDSHADEBOX]

>[!INFO]
>
>- El almacenamiento remoto solo está disponible para la versión 2.4.2 y posteriores de Commerce. Ver las [notas de la versión 2.4.2](https://experienceleague.adobe.com/es/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- El módulo de almacenamiento remoto tiene compatibilidad con _limited_ en Adobe Commerce en la infraestructura en la nube. Adobe no puede solucionar por completo los problemas del servicio del adaptador de almacenamiento de terceros. Consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura en la nube](cloud-support.md) para obtener instrucciones sobre la implementación del almacenamiento remoto para proyectos en la nube.

![Diagrama del esquema de configuración de almacenamiento remoto que ilustra la relación entre el almacenamiento local y el almacenamiento en la nube](../../assets/configuration/remote-storage-schema.png)

## Opciones de almacenamiento remoto

Puede configurar el almacenamiento remoto mediante la opción `remote-storage` con el comando [`setup` de CLI](../../installation/tutorials/deployment.md). La opción `remote-storage` utiliza la siguiente sintaxis:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

`parameter-name` hace referencia al nombre de parámetro de almacenamiento remoto específico. En la tabla siguiente se enumeran los parámetros disponibles para configurar el almacenamiento remoto:

| Parámetro de línea de comandos | Nombre del parámetro | Descripción | Valor predeterminado |
|--- |--- |--- |--- |
| `remote-storage-driver` | conductor | Nombre del adaptador<br>Valores posibles:<br>**archivo**: Deshabilita el almacenamiento remoto y usa el sistema de archivos local <br>**aws-s3**: Use el [servicio Amazon Simple Storage (Amazon S3)](remote-storage-aws-s3.md) | ninguno |
| `remote-storage-bucket` | cubo | Almacenamiento de objetos o nombre de contenedor | ninguno |
| `remote-storage-prefix` | prefijo | Prefijo opcional (ubicación dentro del almacenamiento de objetos) | vaciar |
| `remote-storage-region` | región | Nombre de región | ninguno |
| `remote-storage-key` | tecla de acceso | Clave de acceso opcional | vaciar |
| `remote-storage-secret` | clave secreta | Clave secreta opcional | vaciar |

### Adaptadores de almacenamiento

La ubicación de almacenamiento predeterminada se encuentra en el sistema de archivos local. Un _adaptador de almacenamiento_ le permite conectarse a un servicio de almacenamiento y almacenar sus archivos en cualquier lugar. [!DNL Commerce] admite la configuración de los siguientes servicios de almacenamiento:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Habilitar almacenamiento remoto

Puede instalar almacenamiento remoto durante una instalación de Adobe Commerce o agregar almacenamiento remoto a una instancia de Commerce existente. Los siguientes ejemplos muestran cada método utilizando un conjunto de `remote-storage` parámetros con comandos CLI de Commerce `setup`. Como mínimo, debe proporcionar el almacenamiento `driver`, `bucket` y `region`.

- Ejemplo: Instalar Commerce con almacenamiento remoto

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Ejemplo: Habilitar el almacenamiento remoto en Commerce existente

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Para Adobe Commerce sobre la infraestructura en la nube, consulte [Configuración del almacenamiento remoto para Commerce en la infraestructura en la nube](cloud-support.md).

## Migrar contenido

Después de habilitar el almacenamiento remoto para un adaptador específico, puede usar la CLI para migrar los archivos _media_ existentes al almacenamiento remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>El comando sync solo migra archivos en el directorio `pub/media`, _no_ los archivos de importación y exportación en el directorio `var`. Consulte [Importación/Exportación programada](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html?lang=es) en la _Guía del usuario de Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
