---
title: Archivos de configuración de módulos
description: Obtenga información sobre cómo personalizar un módulo mediante tipos de configuración.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---


# Descripción general de los archivos de configuración del módulo

Las responsabilidades del `config.xml` el archivo de configuración utilizado en versiones anteriores de Commerce ahora se divide entre varios archivos, ubicados en varios directorios de módulos. Los varios archivos de configuración de Commerce se cargan bajo demanda solo cuando un módulo solicita un tipo de configuración específico.

Puede utilizar estos archivos, también conocidos como _tipos de configuración_: para personalizar aspectos específicos del comportamiento del módulo.

Varios módulos pueden declarar archivos de configuración que afecten al mismo tipo de configuración (por ejemplo, eventos) y estos archivos de configuración se combinan.

A continuación se indican los términos comunes utilizados en este tema:

- **Objeto de configuración**: biblioteca de comercio o clase responsable de definir y validar el tipo de configuración. Por ejemplo, el objeto de configuración de `config.xml` es [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Fase de configuración**—Las etapas se definen como _principal_, _global_ y _area_. Cada etapa determina cuándo se carga y combina el tipo de configuración con tipos de configuración con el mismo nombre. Por ejemplo, `module.xml` los archivos se combinan con otros `module.xml` archivos.

- **Ámbito de configuración**: como complemento de las etapas de configuración, un ámbito define el modelo de tipo de configuración. Por ejemplo, `adminhtml` es un ámbito de área que se carga en el escenario con otros módulos&quot; `adminhtml` configuraciones. Para obtener más información, consulte [Módulos y áreas](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Carga de configuración y combinación

En esta sección se explica cómo se cargan y combinan los archivos de configuración.

### Cómo carga Commerce los archivos de configuración

Commerce carga los archivos de configuración en el siguiente orden (todas las rutas son relativas a su directorio de instalación de Commerce):

- Configuración principal ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Este archivo se utiliza para arrancar Commerce.
- Configuraciones globales de módulos (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Recopila ciertos archivos de configuración de todos los módulos y los combina.
- Configuración específica de área de los módulos (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Recopila archivos de configuración de todos los módulos y los combina en la configuración global. Algunas configuraciones específicas de área pueden anular o ampliar la configuración global.

donde

- `<your component base dir>` es el directorio base en el que se encuentra su componente. Los valores típicos son `app/code` o `vendor` relativa al directorio de instalación de Commerce.
- `<vendorname>` es el nombre de proveedor del componente; por ejemplo, el nombre del proveedor de Commerce es `magento`.
- `<component-type>` es una de las siguientes:

   - `module-`: Una extensión o módulo.
   - `theme-`: Tema.
   - `language-`: Paquete de idioma.

>[!INFO]
>
>Actualmente, los temas se encuentran en `<magento_root>/app/design/frontend` o `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Nombre del componente tal como se define en [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Combinación de archivos de configuración

Los nodos de los archivos de configuración se combinan en función de XPath totalmente cualificado, que tiene un atributo especial definido en `$idAttributes` matriz declarada como identificador. Este identificador debe ser único para todos los nodos anidados en el mismo nodo principal.

Algoritmo de combinación de aplicaciones de comercio:

- Si los identificadores de nodo son iguales (o si no hay ningún identificador definido), todo el contenido subyacente del nodo (atributos, nodos secundarios y contenido escalar) se sobrescribe.
- Si los identificadores de nodo no son iguales, el nodo es un nuevo nodo secundario del nodo principal.
- Si el documento original tiene varios nodos con el mismo identificador, se activa un error porque los identificadores no se pueden distinguir.

Una vez combinados los archivos de configuración, el documento resultante contiene todos los nodos de los archivos originales.

>[!INFO]
>
>Puede usar [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) clase para depurar y comprender la lógica subyacente [cargador de archivos de configuración](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) y [combinar configuraciones](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) proceso.

## Tipos de configuración, objetos e interfaces

Las secciones siguientes proporcionan información sobre los tipos de configuración, sus objetos de configuración correspondientes y las interfaces que puede utilizar para trabajar con los objetos:

### Tipos y objetos de configuración

La tabla siguiente muestra cada tipo de configuración y el objeto de configuración de comercio al que se relaciona.

| Archivo de configuración | Descripción | Prueba | Objeto de configuración |
| --- | --- | --- | --- |
| `address_formats.xml` | Declaración de formato de dirección | principal, global | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Lista de control de acceso](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | global | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Informes avanzados](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | principal, global | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Declaración de tipo de caché | principal, global | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuración de atributos del catálogo | global | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` y `env.php` | [Configuración de implementación](../reference/deployment-files.md) | El procesador de configuración interno puede leer o escribir estos archivos. | No tiene objeto, no se puede personalizar |
| `config.xml` | Configuración del sistema | principal, global | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Define aspectos del sistema de cola de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configura grupos cron](../cron/custom-cron-reference.md#configure-cron-groups) | global | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Especifica las opciones del grupo cron](../cron/custom-cron-reference.md) | global | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Esquema declarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | global | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Inyección de dependencias](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) configuración | principal, global, área | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Proporciona configuración de atributos EAV | global | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuración de plantillas de correo electrónico | global | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configuración de palabras clave de la configuración regional del motor de búsqueda](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | global | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuración de evento/observador | global, área | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Exportar configuración de entidad | global | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Atributos de extensión](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | global | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Define los conjuntos de campos | global | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Declara indexadores](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | global | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Declara entidades de importación | global | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Define los elementos de menú para el administrador | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Define los datos de configuración del módulo y la dependencia de software | principal, global | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configuración de MView](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | principal, global | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuración del módulo de pagos | principal, global | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Persistente](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) archivo de configuración | global | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Configuración del PDF | global | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Proporciona configuración de opciones de producto | global | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Define el tipo de producto | global | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Define la relación entre una cola existente y su consumidor](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | global | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Define el intercambio en el que se publica un tema.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | global | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Define las reglas de enrutamiento de mensajes, declara las colas y los intercambios](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | global | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Informes avanzados](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | global | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Define el recurso del módulo | global | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Ruta](https://developer.adobe.com/commerce/php/development/components/routing/) configuración | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Define la configuración total de ventas | global | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Proporciona configuración del motor de búsqueda | global | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Define la configuración de búsqueda en el catálogo | global | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Define acciones que déclencheur la invalidación de caché para bloques de contenido privado | front-end | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Define las opciones de la página de configuración del sistema | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Archivo de configuración de validación del módulo | global | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Define los valores de configuración de la vista Proveedor_Module | global | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Configura una API web](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | global | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Define rutas personalizadas REST](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | global | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Define los widgets | global | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Define el formato del código postal de cada país | global | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfaces de configuración

Puede interactuar con archivos de configuración mediante interfaces en [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Puede utilizar estas interfaces si [crear un tipo de configuración](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` proporciona las siguientes interfaces:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), que convierte el XML en una representación de matriz en memoria de las configuraciones.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), que recupera los datos de configuración en un ámbito especificado.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), que identifica la ubicación de los archivos que desea leer [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), que lee los datos de configuración del almacenamiento y selecciona el almacenamiento desde el que lee.

Es decir, el sistema de archivos, la base de datos y otros tipos de almacenamiento combinan los archivos de configuración según las reglas de combinación y validan los archivos de configuración con los esquemas de validación.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), que localiza el esquema XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), que devuelve una lista de ámbitos.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), que recupera el estado de validación.
