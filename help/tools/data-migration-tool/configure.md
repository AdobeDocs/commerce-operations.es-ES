---
title: Configurar  [!DNL Data Migration Tool]
description: Obtenga información acerca de los dos métodos para configurar  [!DNL Data Migration Tool]  para transferir datos entre el Magento 1 y el Magento 2.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# Configurar [!DNL Data Migration Tool]

Después de instalar [!DNL Data Migration Tool], el siguiente directorio contiene los archivos de asignación y configuración:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: configuración y scripts para migrar del Magento Open Source 1 al Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: configuración y scripts para migrar del Magento Open Source 1 a Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: configuración y scripts para migrar de Adobe Commerce 1 a Adobe Commerce 2

Los directorios anteriores contienen subdirectorios para cada versión admitida.

## Configuración de la migración

Hay dos formas de configurar [!DNL Data Migration Tool]:

* Configurar [!DNL Data Migration Tool] en un módulo independiente (recomendado)
* Cambie la configuración de [!DNL Data Migration Tool] en el directorio `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/`.

Para utilizar el control de código fuente para administrar la configuración de migración y utilizarla en la implementación, debe crear un módulo independiente.
Si planea ejecutar [!DNL Data Migration Tool] solo localmente, puede editar los archivos en el directorio `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` directamente.

### Configuración de la migración en un módulo independiente

Antes de migrar datos, debe crear un módulo de Magento 2.

1. Cree un módulo de Magento 2.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Copie el archivo de configuración `config.xml.dist` del directorio apropiado de [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) en el archivo `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml`.

   Por ejemplo, si migra `Magento 1.9.3.6 Community Edition` a `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. En el archivo `config.xml`, debe establecer los detalles de acceso en las bases de datos M1 y M2, así como la clave de cifrado.

1. Si el almacén M1 tiene cambios personalizados, debe asignar el resto de los archivos de configuración a las personalizaciones del almacén Magento 1. Consulte [Trabajar con archivos de configuración y asignación](#migration-config).

### Configurar la migración en la carpeta `vendor`

Antes de migrar datos, debe crear un archivo de configuración de `config.xml` a partir del ejemplo proporcionado.

Para configurar [!DNL Data Migration Tool] para la migración:

1. Inicie sesión en el servidor de aplicaciones como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.

1. Cambie al siguiente directorio:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Escriba el siguiente comando para crear un `config.xml` a partir del ejemplo proporcionado:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Abra `config.xml` en un editor de texto.

1. Como mínimo, el archivo config.xml debe contener detalles de acceso a las bases de datos M1 y M2 y claves de cifrado.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   La etiqueta &lt;crypt_key> debe contener un valor. Puede encontrarlo dentro de la etiqueta `<key>`, que se encuentra en el archivo app/etc/local.xml en su instancia de Magento 1.

   Parámetros opcionales:

   * Contraseña de usuario de base de datos: `password=<password>`
   * Puerto personalizado de base de datos: `port=<port>`
   * Prefijo de tabla: `<source_prefix>`, `<dest_prefix>`

   Por ejemplo, si el nombre de usuario del propietario de la base de datos es `root` con la contraseña `pass` y utiliza el prefijo `magento1` en la base de datos del Magento 1, utilice lo siguiente en `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

Cuando termine, guarde los cambios en `config.xml` y salga del editor de texto.

### Conexión mediante el protocolo TLS

También puede conectarse a una base de datos utilizando el protocolo TLS (es decir, utilizando claves criptográficas públicas/privadas). Agregue los siguientes atributos opcionales al elemento `database`:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Por ejemplo:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Trabajo con archivos de configuración y asignación

[!DNL Data Migration Tool] usa *archivos de asignación* para permitirle realizar asignaciones de base de datos personalizadas entre las bases de datos de Magento 1 y Magento 2, entre las que se incluyen:

* Cambio de nombres de tabla

* Cambio de nombres de campo

* Omitir tablas o campos

* Adaptar la transferencia de datos de un campo al formato del Magento 2

Los archivos de asignación para las versiones de Magento admitidas se encuentran en los subdirectorios de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Para utilizar los archivos de asignación:

1. Cópielos de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` a `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` y quite la extensión `.dist`.

1. Actualice la ruta al archivo recién copiado en el nodo `<options>` de `config.xml`. La ruta actualizada debe ser una de las siguientes:

   1. Ruta absoluta del archivo, p. ej. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. ruta de archivo relativa del módulo magento/data-migration-tool: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Ruta de acceso del archivo relativo a la raíz del Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

Los directorios `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` y `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` contienen los siguientes archivos de configuración:

Aunque esté trabajando con el archivo `map.xml.dist` la mayor parte del tiempo, la siguiente tabla describe cada asignación y otros archivos.

| Nombre de archivo de asignación | Descripción |
| --- | --- |
| `class-map.xml.dist` | Diccionario de asignaciones de clase entre el Magento 1 y el Magento 2 |
| `config.xml.dist` | Archivo de configuración principal que especifica las configuraciones de base de datos de Magento 1 y Magento 2, la configuración de pasos y los vínculos a archivos de asignación |
| *Solo Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Lista de tablas utilizadas en el paso de atributos del cliente personalizados. |
| *Solo Adobe Commerce*. `customer-attr-map.xml.dist` | Asignar archivo que se utiliza en el paso Atributos del cliente personalizados. |
| `deltalog.xml.dist` | Contiene la lista de tablas necesarias para la configuración de rutinas de base de datos. |
| `eav-attribute-groups.xml.dist` | Contiene la lista de atributos que se utilizan en Eav Step. |
| `eav-document-groups.xml.dist` | Contiene la lista de tablas que se utilizan en Eav Step. |
| `log-document-groups.xml.dist` | Contiene la lista de tablas que se utilizan en el paso de registro. |
| `map-eav.xml.dist` | Asignar archivo que se utiliza en el paso EAV. |
| `map-log.xml.dist` | Archivo de asignación de registros. |
| *Solo Adobe Commerce*. `map-sales.xml.dist` | Asignar archivo que se utiliza en el paso de pedido de ventas. |
| `map.xml.dist` | Archivo de asignación necesario para el paso de asignación. |
| `settings.xml.dist` | Estableciendo archivo de configuración de migración que especifica las reglas necesarias para migrar la tabla `core_config_data`. |
| `customer-attribute-groups.xml.dist` | Contiene la lista de atributos que se utilizan en el paso Atributos del cliente. |
| `customer-document-groups.xml.dist` | Contiene la lista de tablas que se utilizan en el paso Atributos del cliente. |
| `map-customer.xml.dist` | Asignar archivo que se utiliza en el paso Atributos del cliente. |
| `order-grids-document-groups.xml.dist` | Contiene la lista de tablas que se utilizan en el paso OrderGrids. |
| `map-document-groups.xml.dist` | Define qué campos se actualizan cuando se producen duplicados al insertar datos |
| `map-stores.xml.dist` | Asignar archivo que se utiliza en el paso Tiendas. |
| `map-tier-price.xml.dist` | Archivo de mapa que se utiliza en el paso de nivel de precio. |
| *Solo Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Asignar archivo que se utiliza en el paso de VisualMerchandiser. |
| *Solo Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Contiene la lista de atributos que se utilizan en el paso de VisualMerchandiser. |
| *Solo Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Contiene la lista de tablas que se utilizan en VisualMerchandiser Step. |

Puede consultar [[!DNL Data Migration Tool] Especificación técnica](technical-specification.md) para obtener más detalles.
