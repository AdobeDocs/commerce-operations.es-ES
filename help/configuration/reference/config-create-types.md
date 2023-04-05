---
title: Tipos de configuración
description: Crear o ampliar tipos de configuración.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---


# Tipos de configuración

## Ampliar tipos de configuración

Para ampliar un tipo de configuración existente, solo necesita crear un archivo de configuración en el módulo.

Por ejemplo, para añadir un observador de eventos, se crea `app/code/{VendorName}/{ModuleName}/etc/events.xml` y declarar un nuevo observador.

Dado que el tipo de configuración de evento existe en Commerce, el cargador y la variable `events.xsd` el esquema de validación ya está presente y funciona.

El nuevo `events.xml` se recopila automáticamente del módulo y se fusiona con otros `events.xml` archivos para otros módulos.

## Crear tipos de configuración

Para crear un tipo de configuración, debe agregar como mínimo:

- Un cargador
- Esquema de validación XSD
- Archivos de configuración XML

Por ejemplo, para introducir un adaptador para un nuevo servidor de búsqueda que permita que las extensiones configuren cómo se indexan sus entidades en ese servidor, cree:

- Un cargador
- Un archivo de esquema XSD
- Un archivo de configuración con el nombre adecuado. Por ejemplo, `search.xml`. Este archivo se lee y valida en el esquema .
- Cualquier otra clase necesaria para su trabajo.

>[!INFO]
>
>Si los módulos nuevos tienen una `search.xml` , se combinan con el archivo cuando se carga.

### Ejemplos de uso

Para crear un tipo de configuración:

1. Cree su archivo XSD.
1. Cree el archivo XML.
1. Defina el objeto de configuración en su `di.xml`.

   El siguiente ejemplo del módulo Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) ilustra cómo debería ser un objeto de configuración.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - El primer nodo de tipo establece el nombre de archivo del Reader, asociado `Converter` y `SchemaLocator` clases .
   - A continuación, el `pdfConfigDataStorage` el nodo de tipo virtual adjunta la clase de lector a una instancia de [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Y finalmente, el último nodo de tipo adjunta esos datos de configuración tipo virtual al [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) clase , que se utiliza para leer valores de esos [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) archivos.

1. Defina un lector extendiendo [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) y reescriba los siguientes parámetros:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Ejemplo:**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>Si prefiere crear su propia versión del lector, puede hacerlo implementando `\Magento\Framework\Config\ReaderInterface`. Consulte [Lector de configuración de Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Después de definir el lector, utilícelo para recopilar, combinar, validar y convertir los archivos de configuración en una representación de matriz interna.

## Validación de un tipo de configuración

Cada archivo de configuración se valida para un esquema específico de su tipo de configuración. Ejemplo: que, en versiones anteriores de Commerce, estaban configurados en `config.xml`, ahora están configurados en `events.xml`.

Los archivos de configuración se pueden validar antes (opcional) y después de cualquier combinación de varios archivos que afecten al mismo tipo de configuración. A menos que las reglas de validación de los archivos individuales y combinados sean idénticas, debe proporcionar dos esquemas para validar los archivos de configuración:

- Esquema para validar un individuo
- Esquema para validar un archivo combinado

Los nuevos archivos de configuración deben ir acompañados de esquemas de validación XSD. Un archivo de configuración XML y su archivo de validación XSD deben tener el mismo nombre.

Si debe utilizar dos archivos XSD para un único archivo XML, los nombres de los esquemas deben ser reconocibles y estar asociados al archivo XML.
Si tiene un `events.xml` archivo y `events.xsd` , los archivos XSD para la combinación `events.xml` puede tener el nombre `events_merged.xsd`.
Para garantizar la validación de un archivo XML mediante el archivo XSD adecuado, debe añadir el nombre de recurso uniforme (URN) al archivo XSD en el archivo XML. Por ejemplo:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Su IDE puede validar sus archivos de configuración tanto en tiempo de ejecución como durante el desarrollo.
