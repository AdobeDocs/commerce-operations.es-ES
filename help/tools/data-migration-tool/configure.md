---
title: Configure las variables [!DNL Data Migration Tool]
description: Obtenga información acerca de los dos métodos para configurar el [!DNL Data Migration Tool] para transferir datos entre Magento 1 y Magento 2.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# Configure las variables [!DNL Data Migration Tool]

Después de instalar el [!DNL Data Migration Tool], el siguiente directorio contiene los archivos de asignación y configuración:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Configuración y scripts para migrar del Magento Open Source 1 al Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: configuración y scripts para migrar del Magento Open Source 1 a Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: configuración y scripts para migrar de Adobe Commerce 1 a Adobe Commerce 2

Los directorios anteriores contienen subdirectorios para cada versión admitida.

## Configuración de la migración

Existen dos formas de configurar la variable [!DNL Data Migration Tool]:

* Configure las variables [!DNL Data Migration Tool] en un módulo independiente (recomendado)
* Cambie el [!DNL Data Migration Tool] configuración en la `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` directorio.

Para utilizar el control de código fuente para administrar la configuración de migración y utilizarla en la implementación, debe crear un módulo independiente.
Si planea ejecutar el [!DNL Data Migration Tool] solo localmente, puede editar archivos en `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` directamente.

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

1. Copie el `config.xml.dist` archivo de configuración del directorio apropiado de [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) en el `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` archivo.

   Por ejemplo, si migra `Magento 1.9.3.6 Community Edition` hasta `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. En el `config.xml` , debe establecer los detalles de acceso en las bases de datos M1 y M2 y la clave de cifrado.

1. Si el almacén M1 tiene cambios personalizados, debe asignar el resto de los archivos de configuración a las personalizaciones del almacén Magento 1. Consulte [Trabajo con archivos de configuración y asignación](#migration-config).

### Configuración de la migración en `vendor` carpeta

Antes de migrar datos, debe crear un `config.xml` archivo de configuración del ejemplo proporcionado.

Para configurar la variable [!DNL Data Migration Tool] para la migración:

1. Inicie sesión en el servidor de aplicaciones como, o cambie a, [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

1. Cambie al siguiente directorio:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Introduzca el siguiente comando para crear una `config.xml` de la muestra proporcionada:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Abrir `config.xml` en un editor de texto.

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

   El &lt;crypt_key> la etiqueta debe contener un valor. Puede encontrarlo dentro de la `<key>` , que se encuentra en el archivo app/etc/local.xml de la instancia de Magento 1.

   Parámetros opcionales:

   * Contraseña de usuario de base de datos: `password=<password>`
   * Puerto personalizado de base de datos: `port=<port>`
   * Prefijo de tabla: `<source_prefix>`, `<dest_prefix>`

   Por ejemplo, si el nombre de usuario del propietario de la base de datos es `root` con contraseña `pass` y utiliza el prefijo `magento1` en la base de datos de Magento 1, utilice lo siguiente en `config.xml`:

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

También puede conectarse a una base de datos utilizando el protocolo TLS (es decir, utilizando claves criptográficas públicas/privadas). Agregue los siguientes atributos opcionales a `database` elemento:

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

El [!DNL Data Migration Tool] utiliza *asignación de archivos* para permitirle realizar una asignación personalizada de bases de datos entre las bases de datos de Magento 1 y Magento 2, lo que incluye:

* Cambio de nombres de tabla

* Cambio de nombres de campo

* Omitir tablas o campos

* Adaptar la transferencia de datos de un campo al formato del Magento 2

Los archivos de asignación para las versiones de Magento admitidas se encuentran en subdirectorios de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Para utilizar los archivos de asignación:

1. Cópielos desde `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` hasta `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` y quite el `.dist` extensión.

1. Actualice la ruta al archivo recién copiado en la `<options>` nodo de `config.xml`. La ruta actualizada debe ser una de las siguientes:

   1. Ruta absoluta del archivo, p. ej. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. ruta relativa del archivo del módulo magento/data-migration-tool: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Ruta de archivo relativa a la raíz del Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

El `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` y `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` Los directorios contienen los siguientes archivos de configuración:

Aunque esté trabajando con el `map.xml.dist` La mayoría de las veces, la siguiente tabla describe cada asignación y otros archivos.

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
| `settings.xml.dist` | Estableciendo archivo de configuración de migración que especifica las reglas necesarias para migrar el `core_config_data` tabla. |
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

Puede hacer referencia a [[!DNL Data Migration Tool] Especificaciones técnicas](technical-specification.md) para obtener más información.
