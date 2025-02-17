---
title: Tipos de configuración
description: Crear o ampliar tipos de configuración.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Tipos de configuración

## Ampliar tipos de configuración

Para ampliar un tipo de configuración existente, solo es necesario crear un archivo de configuración en el módulo.

Por ejemplo, para agregar un observador de eventos, cree `app/code/{VendorName}/{ModuleName}/etc/events.xml` y declare un nuevo observador.

Dado que el tipo de configuración de evento existe en Commerce, el cargador y el esquema de validación `events.xsd` ya están presentes y funcionan.

El nuevo `events.xml` se recopila automáticamente del módulo y se combina con otros `events.xml` archivos de otros módulos.

## Crear tipos de configuración

Para crear un tipo de configuración, debe agregar como mínimo:

- Un cargador
- Esquema de validación XSD
- Archivos de configuración XML

Por ejemplo, para introducir un adaptador para un nuevo servidor de búsqueda que permita a las extensiones configurar cómo se indexan sus entidades en ese servidor, cree lo siguiente:

- Un cargador
- Un archivo de esquema XSD
- Un archivo de configuración con el nombre adecuado. Por ejemplo, `search.xml`. Este archivo se lee y valida con el esquema.
- Cualquier otra clase requerida para su trabajo.

>[!INFO]
>
>Si los módulos nuevos tienen un archivo `search.xml`, se combinarán con el archivo cuando se cargue.

### Ejemplos de uso

Para crear un tipo de configuración:

1. Cree su archivo XSD.
1. Cree su archivo XML.
1. Defina el objeto de configuración en su `di.xml`.

   El siguiente ejemplo del [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) del módulo Magento_Sales ilustra el aspecto que debería tener un objeto de configuración.

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

   - El primer nodo de tipo establece el nombre de archivo del Reader, asociado con las clases `Converter` y `SchemaLocator`.
   - A continuación, el nodo de tipo virtual `pdfConfigDataStorage` adjunta la clase de lector a una instancia de [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Y, por último, el último nodo de tipo adjunta ese tipo virtual de datos de configuración a la clase [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php), que se utiliza para leer valores en de esos archivos [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml).

1. Defina un lector ampliando la clase [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) y vuelva a escribir los parámetros siguientes:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Ejemplo:**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
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
>Si prefiere crear su propia versión del lector, puede hacerlo implementando `\Magento\Framework\Config\ReaderInterface`. Ver [Magento de configuración de Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Después de definir el lector, utilícelo para recopilar, combinar, validar y convertir los archivos de configuración en una representación de matriz interna.

## Validación de un tipo de configuración

Cada archivo de configuración se valida con un esquema específico para su tipo de configuración. Ejemplo: los eventos que, en versiones anteriores de Commerce, se configuraban en `config.xml`, ahora se configuran en `events.xml`.

Los archivos de configuración se pueden validar antes (opcional) y después de cualquier combinación de varios archivos que afecten al mismo tipo de configuración. A menos que las reglas de validación para los archivos individuales y combinados sean idénticas, debe proporcionar dos esquemas para validar los archivos de configuración:

- Esquema para validar un individuo
- Esquema para validar un archivo combinado

Los nuevos archivos de configuración deben ir acompañados de esquemas de validación XSD. Un archivo de configuración XML y su archivo de validación XSD deben tener el mismo nombre.

Si debe utilizar dos archivos XSD para un solo archivo XML, los nombres de los esquemas deben ser reconocibles y asociados al archivo XML.
Si tiene un archivo `events.xml` y un primer archivo `events.xsd`, los archivos XSD del archivo `events.xml` combinado podrían llamarse `events_merged.xsd`.
Para garantizar la validación de un archivo XML mediante el archivo XSD adecuado, debe agregar el Nombre de recurso uniforme (URN) al archivo XSD en el archivo XML. Por ejemplo:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

El IDE puede validar los archivos de configuración tanto en tiempo de ejecución como durante el desarrollo.
