---
title: Configuración del almacenamiento remoto
description: Aprenda a configurar el módulo Almacenamiento remoto para la aplicación de comercio local.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# Configuración del almacenamiento remoto

El módulo Almacenamiento remoto proporciona la opción de almacenar archivos multimedia y programar importaciones/exportaciones en un contenedor de almacenamiento remoto persistente utilizando un servicio de almacenamiento, como AWS S3. De forma predeterminada, la variable [!DNL Commerce] la aplicación almacena archivos multimedia en el mismo sistema de archivos que contiene la aplicación. Esto es ineficiente en configuraciones complejas de varios servidores y puede provocar un rendimiento degradado al compartir recursos. Con el módulo Almacenamiento remoto, puede almacenar archivos multimedia en la `pub/media` directorio y archivos de importación/exportación en la variable `var` del almacenamiento de objetos remotos para aprovechar el cambio de tamaño de las imágenes del lado del servidor.

>[!INFO]
>
>El almacenamiento remoto solo está disponible en la versión 2.4.2 y posteriores. Consulte la [Notas de la versión 2.4.2](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>El módulo de almacenamiento remoto tiene _limited_ compatibilidad con Adobe Commerce en infraestructura de nube. Adobe no puede solucionar problemas del servicio del adaptador de almacenamiento de terceros.

![imagen de esquema](../../assets/configuration/remote-storage-schema.png)

## Opciones de almacenamiento remoto

Puede configurar el almacenamiento remoto mediante la variable `remote-storage` con la opción [`setup` Comando CLI][setup]. La variable `remote-storage` utiliza la siguiente sintaxis:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

La variable `parameter-name` hace referencia al nombre de parámetro de almacenamiento remoto específico. La siguiente tabla enumera los parámetros disponibles para configurar el almacenamiento remoto:

| Parámetro de línea de comandos | Nombre del parámetro | Descripción | Valor predeterminado |
|--- |--- |--- |--- |
| `remote-storage-driver` | driver | Nombre del adaptador<br>Valores posibles:<br>**file**: Deshabilita el almacenamiento remoto y utiliza el filesystem local <br>**aws-s3**: Utilice la variable [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | ninguno |
| `remote-storage-bucket` | depósito | Almacenamiento de objetos o nombre de contenedor | ninguno |
| `remote-storage-prefix` | prefix | Prefijo opcional (ubicación dentro del almacenamiento de objetos) | empty |
| `remote-storage-region` | region | Nombre de la región | ninguno |
| `remote-storage-key` | clave de acceso | Clave de acceso opcional | empty |
| `remote-storage-secret` | clave secreta | Clave secreta opcional | empty |

### Adaptadores de almacenamiento

La ubicación de almacenamiento predeterminada está en el sistema de archivos local. A _adaptador de almacenamiento_ le permite conectarse a un servicio de almacenamiento y almacenar sus archivos en cualquier parte. [!DNL Commerce] admite la configuración de los siguientes servicios de almacenamiento:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Habilitar almacenamiento remoto

Puede instalar el almacenamiento remoto durante un [!DNL Commerce] instalación o agregarla a una instancia de Commerce existente mediante `remote-storage` pares de parámetro name-and-value con `setup` Comandos CLI. Como mínimo, debe suministrar el almacenamiento `driver`, `bucket`y `region`.

Los siguientes ejemplos habilitan el almacenamiento remoto con un adaptador de almacenamiento AWS S3 en EE. UU.:

- Instalar nuevo [!DNL Commerce] con almacenamiento remoto

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Habilitar almacenamiento remoto en [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## Limitaciones

No puede tener habilitado el almacenamiento remoto y el almacenamiento de base de datos al mismo tiempo. Deshabilite el almacenamiento de la base de datos si utiliza almacenamiento remoto.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Habilitar el almacenamiento remoto puede afectar a su experiencia de desarrollo establecida. Por ejemplo, es posible que ciertas funciones de archivo PHP no funcionen como se espera. Se debe aplicar el uso de Commerce Framework para las operaciones de archivos.

La lista de funciones nativas de PHP prohibidas está disponible en [Magento estándar de codificación] repositorio.

## Migración de contenido

Después de habilitar el almacenamiento remoto para un adaptador específico, puede usar la CLI para migrar los ya existentes _medios_ al almacenamiento remoto.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>El comando sync solo migra archivos en la variable `pub/media` directorio, _not_ los archivos de importación/exportación de la variable `var` directorio. Consulte [Importación y exportación programadas][import-export] en el _Guía del usuario de Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[Magento estándar de codificación]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: ../../installation/tutorials/deployment.md
