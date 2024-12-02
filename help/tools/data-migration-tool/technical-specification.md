---
title: Especificación técnica de [!DNL Data Migration Tool]
description: Obtenga información acerca de los detalles de implementación de  [!DNL Data Migration Tool]  y cómo ampliarlos al transferir datos entre el Magento 1 y el Magento 2.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# Especificación técnica de [!DNL Data Migration Tool]

Esta sección describe los detalles de implementación de [!DNL Data Migration Tool] y cómo ampliar su funcionalidad.

## Repositorios

Para acceder al código fuente de [!DNL Data Migration Tool], consulte el [repositorio](https://github.com/magento/data-migration-tool) de GitHub.

## Requisitos del sistema

Los [requisitos del sistema](../../installation/system-requirements.md) para [!DNL Data Migration Tool] son los mismos que para el Magento 2.

## Estructura interna

### Estructura de directorio

El diagrama siguiente representa la estructura de directorios de [!DNL Data Migration Tool]:

```
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## Punto de entrada

El script que ejecuta el proceso de migración se encuentra en: `magento-root/bin/magento`.

## Configuración

El esquema para el archivo de configuración `config.xsd` se encuentra en el directorio `etc/`. El archivo de configuración predeterminado (`config.xml.dist`) se crea para cada versión de Magento 1.x. Se encuentra en un directorio independiente bajo `etc/`.

El archivo de configuración predeterminado se puede reemplazar por uno personalizado (consulte [sintaxis de comando](migrate-data/overview.md#command-syntax)).

El archivo de configuración tiene la siguiente estructura:

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* pasos: describe todos los pasos que se procesan durante la migración.

* source: configuración de la fuente de datos. Tipos de origen disponibles: base de datos

* destino: configuración del destino de datos. Tipos de destino disponibles: base de datos

* options: lista de parámetros. Contiene parámetros obligatorios (map_file, settings_map_file, bulk_size) y opcionales (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file)

Cambie la opción prefix en caso de que el Magento se haya instalado con prefix en las tablas de la base de datos. Se puede configurar para bases de datos de Magento 1 y Magento 2. Utilice las opciones de configuración &quot;source_prefix&quot; y &quot;dest_prefix&quot; según corresponda.

Se puede acceder a los datos de configuración con la clase `\Migration\Config`.

## Pasos de las operaciones disponibles

| Documento | Campo |
|---|---|
| `step` | Nodo de segundo nivel dentro del nodo Steps. Se debe especificar la descripción del paso correspondiente en el atributo `title`. |
| `integrity` | Especifica la clase PHP responsable de la comprobación de integridad. Compara los nombres de los campos de tabla, los tipos y otra información para comprobar la compatibilidad entre las estructuras de datos del Magento 1 y 2. |
| `data` | Especifica la clase PHP responsable de la comprobación de datos. Transfiere los datos tabla por tabla del Magento 1 al Magento 2. |
| `volume` | Especifica la clase PHP responsable de la comprobación de volumen. Compara el número de registros entre tablas para comprobar que la transferencia se realizó correctamente. |
| `delta` | Especifica la clase PHP responsable de la comprobación delta. Transfiere el delta del Magento 1 al Magento 2 después de la migración de datos completa. |

## Atributos de información de base de datos Source

| Documento | Campo | ¿Requerido? |
|---|---|---|
| `name` | Nombre de base de datos del servidor de Magento 1. | yes |
| `host` | Dirección IP del host del servidor de Magento 1. | yes |
| `port` | Número de puerto del servidor de Magento 1. | no |
| `user` | Nombre de usuario del servidor de base de datos de Magento 1. | yes |
| `password` | Contraseña del servidor de base de datos de Magento 1. | yes |
| `ssl_ca` | Ruta al archivo de autoridad de certificación SSL. | no |
| `ssl_cert` | Ruta al archivo de certificado SSL. | no |
| `ssl_key` | Ruta al archivo de clave SSL. | no |

## Atributos de información de base de datos destino

| Documento | Campo | ¿Requerido? |
|---|---|---|
| `name` | Nombre de base de datos del servidor de Magento 2. | yes |
| `host` | Dirección IP del host del servidor de Magento 2. | yes |
| `port` | Número de puerto del servidor de Magento 2. | no |
| `user` | Nombre de usuario del servidor de base de datos de Magento 2. | yes |
| `password` | Contraseña del servidor de base de datos de Magento 2. | yes |
| `ssl_ca` | Ruta al archivo de autoridad de certificación SSL. | no |
| `ssl_cert` | Ruta al archivo de certificado SSL. | no |
| `ssl_key` | Ruta al archivo de clave SSL. | no |

## Conexión mediante el protocolo TLS

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

## Pasos internos

El proceso de migración consta de pasos.

Step es una unidad que proporciona la funcionalidad necesaria para la migración de algunos datos separados. El paso puede constar de una o más etapas (comprobación de integridad, datos, comprobación de volumen y delta).

De manera predeterminada, hay varios pasos ([Mapa](#map-step), [EAV](#eav), [Reescrituras de URL](#url-rewrite-step), etc.). Si lo desea, también puede agregar sus propios pasos.

Las clases relacionadas con los pasos se encuentran en el directorio src/Migration/Step.

Para ejecutar una clase Step, la clase debe definirse en el archivo config.xml.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

Cada clase de fase debe implementar StageInterface.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

Si la fase de datos admite la reversión, debe implementar la interfaz `RollbackInterface`.

El componente ProgressBar de Symfony proporciona la visualización del paso en ejecución (consulte [Barra de progreso](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Acceda a este componente en un paso como LogLevelProcessor.

Los principales métodos de uso son:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Fases del paso

### Comprobación de integridad

Cada paso debe comprobar que la estructura de la fuente de datos (Magento 1 de forma predeterminada) y la estructura del destino de datos (Magento 2) son compatibles. Si no es así: se muestra un error con entidades que no son compatibles. Si los campos tienen tipos de datos diferentes (el mismo campo tiene un tipo de datos decimal en el Magento 1 y un entero en el Magento 2), se muestra un mensaje de advertencia (excepto cuando se cubrió en el archivo Map).

### Transferencia de datos

Si se supera la comprobación de integridad, se están ejecutando los datos de transferencia. Si aparecen errores, se ejecuta la reversión para volver al estado anterior del Magento 2. Si una clase step implementa la interfaz `RollbackInterface`, el método rollback se ejecuta cuando hay un error.

### Comprobación del volumen

Una vez migrados los datos, la comprobación de volumen proporciona una comprobación adicional de que todos los datos se transfirieron correctamente.

### Entrega delta

La funcionalidad Delta es responsable de entregar el resto de los datos agregados después de la migración principal.

## Modos de ejecución

La herramienta debe ejecutarse en tres modos diferentes en orden particular:

1. configuración: migración de la configuración del sistema
1. data: migración principal de datos
1. delta: migración del resto de los datos agregados después de la migración principal

Cada modo tiene su propia lista de pasos a ejecutar. Consulte config.xml

### Modo de migración de configuración

El modo de migración de configuración de esta herramienta se utiliza para transferir las siguientes entidades:

1. Sitios web, tiendas, vistas de tiendas.
1. Configuración de tienda (principalmente Tiendas->Configuración en M2 o Sistema->Configuración en M1)

Toda la configuración del almacén mantiene sus datos en la tabla core_config_data de la base de datos. El archivo settings.xml contiene reglas para esta tabla que se aplican durante el proceso de migración. Este archivo describe las opciones que se deben ignorar, cambiar de nombre o cambiar sus valores. El archivo settings.xml tiene la siguiente estructura:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

En el nodo `<key>` hay reglas que funcionan con la columna &quot;ruta&quot; en la tabla `core_config_data`. `<ignore>` reglas impiden que la herramienta transfiera algunas configuraciones. En este nodo se pueden utilizar caracteres comodín. Se migrarán todas las demás configuraciones que no aparezcan en el nodo `<ignore>`. Si la ruta de acceso a una configuración ha cambiado en el Magento 2, debe agregarse al nodo `//key/rename`, donde la ruta de acceso antigua indica en el nodo `//key/rename/path` y la nueva en el nodo `//key/rename/to`.

En el nodo `<value>`, hay reglas que funcionan con la columna &quot;value&quot; en la tabla `core_config_data`. Estas reglas pretenden transformar el valor de la configuración mediante controladores (clases que implementan `Migration\Handler\HandlerInterface`) y adaptarlo para el Magento 2.

### Modo de migración de datos

En este modo, se migran la mayoría de los datos. Antes de la migración de datos, se ejecutan las fases de comprobación de integridad de cada paso. Si la comprobación de integridad es correcta, [!DNL Data Migration Tool] instala las tablas deltalog (con el prefijo `m2_cl_*`) y los déclencheur correspondientes en la base de datos de Magento 1 y ejecuta la fase de migración de datos de los pasos. Cuando la migración se completa sin errores, la comprobación de volumen comprueba la coherencia de los datos. Puede mostrar un mensaje de advertencia si migra el almacén activo. No se preocupe, la migración delta se encarga de estos datos incrementales. Los pasos de migración más valiosos son Asignación, Reescritura de URL y EAV.

#### Etapa de mapa

El paso de asignación es responsable de transferir la mayoría de los datos del Magento 1 al Magento 2. Este paso lee las instrucciones del archivo map.xml (ubicado en el directorio `etc/`). El archivo describe las diferencias entre las estructuras de datos de origen (Magento 1) y destino (Magento 2). Si el Magento 1 contiene tablas o campos que pertenecen a alguna extensión que no existe en el Magento 2, estas entidades se pueden colocar aquí para ignorarlos mediante el paso de asignación. De lo contrario, muestra un mensaje de error.

El archivo de mapa tiene el siguiente formato:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

Áreas:

* *origen*: contiene reglas de la base de datos de origen

* *destino* - contiene reglas de la base de datos de destino

Opciones:

* *omitir* - documento, campo o tipo de datos marcado con esta opción es ignorado

* *cambiar nombre* - describe las relaciones de nombre entre documentos con un nombre diferente. En caso de que el nombre del documento de destino no sea el mismo que el del documento de origen, puede utilizar la opción de cambio de nombre para establecer un nombre de documento de origen similar al nombre de la tabla de destino

* *mover*: establece la regla para mover el campo especificado del documento de origen al documento de destino. NOTA: el nombre del documento de destino debe ser el mismo que el nombre del documento de origen. Si los nombres de los documentos de origen y destino son diferentes, debe utilizar la opción de cambio de nombre para el documento que contiene el campo movido

* *transform*: es una opción que permite al usuario migrar campos según el comportamiento descrito en los controladores

* *handler*: describe el comportamiento de transformación de los campos. Para llamar al controlador, debe especificar un nombre de clase de controlador en una etiqueta `<handler>`. Utilice la etiqueta `<param>` con los datos de nombre y valor del parámetro para pasarlo al controlador

**Source** operaciones disponibles:

| Documento | Campo |
|--- |--- |
| ignorar cambio de nombre | omitir transformación de movimiento |

**Destino** operaciones disponibles:

| Documento | Campo |
|--- |--- |
| pasar por alto | ignorar transformación |

#### Comodines

Para omitir documentos con partes similares (`document_name_1`, `document_name_2`), puede utilizar la funcionalidad comodín. Coloque el símbolo `*` en lugar de la parte repetida (`document_name_*`) y esta máscara cubrirá todos los documentos de origen o destino que cumplan esta máscara.

#### Paso de reescritura de URL

Este paso es complejo porque hay muchos algoritmos diferentes desarrollados en el Magento 1 que no son compatibles con el Magento 2. Para diferentes versiones de Magento 1, puede haber diferentes algoritmos. Por lo tanto, en la carpeta Step/UrlRewrite hay clases que se desarrollaron para algunas versiones particulares de Magento y Migration\Step\UrlRewrite\Version191to2000 es una de ellas. Puede transferir los datos de reescritura de URL del Magento 1.9.1 al Magento 2.

#### Paso EAV

Este paso transfiere todos los atributos (producto, cliente, RMA) del Magento 1 al Magento 2. Utiliza el archivo map-eav.xml que contiene reglas similares a las del archivo map.xml para casos específicos de procesamiento de datos.

Algunas de las tablas que se procesan en el paso:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Modo de migración delta

Después de la migración principal, es posible que se hayan agregado datos adicionales a la base de datos de Magento 1 (por ejemplo, por parte de los clientes de la tienda). Para realizar un seguimiento de estos datos, la herramienta configura los déclencheur de base de datos para tablas al principio del proceso de migración. Para obtener más información, consulte [Migrar datos creados por extensiones de terceros](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Fuentes de datos

Para llegar a las fuentes de datos del Magento 1 y del Magento 2 y trabajar con sus datos (seleccionar, actualizar, insertar, eliminar) hay muchas clases en Resource folder. Migration\ResourceModel\Source y Migration\ResourceModel\Destination son clases principales. Todos los pasos de migración lo utilizan para operar con datos. Estos datos se incluyen en clases como Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure, etc.

Este es un diagrama de clase de estas clases:

![Estructura de datos de la herramienta de migración](../../assets/data-migration/MmigrationToolDataStructure.png)

## Registro

Para implementar la salida del proceso de migración y controlar todos los niveles posibles se aplica el registrador de PSR, que se utiliza en el Magento. La clase `\Migration\Logger\Logger` se implementó para proporcionar funcionalidad de registro. Para utilizar el registrador, debe inyectarlo a través de la inyección de dependencia del constructor.

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

Después, puede utilizar esta clase para registrar algunos eventos:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Existe la posibilidad de personalizar dónde se debe escribir la información de registro. Puede hacerlo agregando el controlador al registrador mediante el método pushHandler() del registrador. Cada controlador debe implementar la interfaz `\Monolog\Handler\HandlerInterface`. Por ahora, hay dos controladores:

* ConsoleHandler: escribe mensajes en la consola

* FileHandler: escribe mensajes en el archivo de registro que se ha establecido en la opción de configuración &quot;log_file&quot;

Además, es posible implementar cualquier controlador adicional. Hay un conjunto de controladores en el marco del Magento. Ejemplo de adición de controladores al registrador:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Para establecer datos adicionales para el registrador (modo actual, nombre de tabla) puede utilizar procesadores de registrador. Ya existe un procesador (MessageProcessor). Se crea para agregar datos &quot;adicionales&quot; para registrar mensajes y se llama cada vez que se ejecuta el método de registro. MessageProcessor ha protegido $extra var, que contiene valores vacíos para &quot;mode&quot;, &quot;stage&quot;, &quot;step&quot; y &quot;table&quot;. Se pueden pasar datos adicionales al procesador como un segundo parámetro (contexto) para el método de registro. Actualmente se utilizan conjuntos de datos adicionales para el método processor en AbstractStep->runStage (pasar modo, fase y paso actual al procesador) y clases de datos donde se utiliza el método logger->debug (pasar nombre de tabla de migración). Ejemplo de adición de procesadores al registrador:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Existe la posibilidad de establecer el nivel de detalle. Por ahora hay tres niveles:

* `ERROR` (solo escribe errores en el registro)
* `INFO` (solo se escribe información importante en el registro, valor predeterminado)
* `DEBUG` (todo está escrito)

El nivel de registro de detalle se puede establecer para cada controlador por separado llamando al método `setLevel()`. Si desea establecer el nivel de detalle mediante el parámetro de línea de comandos, debe cambiar la opción &quot;detallado&quot; al iniciar la aplicación.

Puede dar formato a los mensajes de registro con el formateador de monólogos. Para que funcione la funcionalidad del formateador, debe especificar el controlador de registro mediante el método `setFormatter()`. Actualmente, tenemos una clase de formateador (`MessageFormatter`) que establece cierto formato (depende del nivel de detalle) durante la administración de mensajes (a través del método `format()` ejecutado desde el controlador).

La manipulación del registrador (agregando controladores y procesadores) y el procesamiento en modo detallado se realizan en el método `process()` de la clase `Migration\Logger\Manager`. Se llama al método cuando se inicia la aplicación.

## Pruebas automáticas

Hay tres tipos de pruebas en [!DNL Data Migration Tool]:

* Estático
* Unidad
* Integración

Se encuentran en el directorio `tests/` de la herramienta, que es el mismo que el tipo de prueba (las pruebas unitarias se encuentran en el directorio `tests/unit`). Para iniciar la prueba, debe tener phpunit instalado. Cambie el directorio actual al directorio de prueba e inicie phpunit. Por ejemplo:

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
