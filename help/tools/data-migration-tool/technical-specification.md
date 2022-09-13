---
title: "[!DNL Data Migration Tool] especificación técnica"
description: "Obtenga información sobre los detalles de implementación de la variable [!DNL Data Migration Tool] y cómo ampliar al transferir datos entre el Magento 1 y el Magento 2."
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 0%

---


# [!DNL Data Migration Tool] especificación técnica

Esta sección describe [!DNL Data Migration Tool] detalles de implementación y cómo ampliar su funcionalidad.

## Repositorios

Para acceder a la [!DNL Data Migration Tool] código fuente, consulte GitHub [repositorio](https://github.com/magento/data-migration-tool).

## Requisitos del sistema

La variable [requisitos del sistema](../../installation/system-requirements.md) para el [!DNL Data Migration Tool] son los mismos que para el Magento 2.

## Estructura interna

### Estructura del directorio

El diagrama siguiente representa la estructura de directorio de [!DNL Data Migration Tool]:

```terminal
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
│       ├── ResourceModel                   --- contains [adapter](https://glossary.magento.com/adapter) for connection to data storage and classes to work with structured data
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
│       ├── [Exception](https://glossary.magento.com/exception).php
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

La secuencia de comandos que ejecuta el proceso de migración se encuentra en: `magento-root/bin/magento`.

## Configuración

El esquema para la configuración `config.xsd` se encuentra en la `etc/` directorio. El archivo de configuración predeterminado (`config.xml.dist`) se crea para cada versión del Magento 1.x. Se encuentra en un directorio separado debajo de `etc/`.

El archivo de configuración predeterminado se puede reemplazar por uno personalizado (consulte [sintaxis del comando](migrate-data/overview.md#command-syntax)).

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

* Pasos: describe todos los pasos que se procesan durante la migración

* source: configuración para la fuente de datos. Tipos de origen disponibles: base de datos

* destination : configuración para el destino de los datos. Tipos de destino disponibles: base de datos

* opciones : lista de parámetros. Contiene parámetros obligatorios (map_file, settings_map_file, bulk_size) y opcionales (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file)

La opción Cambiar prefijo en caso de que el Magento se instalara con prefijo en las tablas de la base de datos. Se puede configurar para bases de datos de Magento 1 y Magento 2. Utilice las opciones de configuración &quot;source_prefix&quot; y &quot;dest_prefix&quot; según corresponda.

Se puede acceder a los datos de configuración mediante la variable `\Migration\Config` Clase .

## Pasos disponibles: operaciones

| Documento | Campo |
|---|---|
| `step` | Nodo de segundo nivel dentro del nodo Pasos . La descripción del paso correspondiente debe especificarse en el `title` atributo. |
| `integrity` | Especifica la clase PHP responsable de la comprobación de integridad. Compara los nombres de los campos de la tabla, los tipos y otra información para comprobar la compatibilidad entre las estructuras de datos del Magento 1 y 2. |
| `data` | Especifica la clase PHP responsable de la comprobación de datos. Transfiere los datos, cuadro por cuadro, del Magento 1 al Magento 2. |
| `volume` | Especifica la clase PHP responsable de la comprobación de volumen. Compara el número de registros entre tablas para verificar que la transferencia se haya realizado correctamente. |
| `delta` | Especifica la clase PHP responsable de la comprobación delta. Transfiere el delta del Magento 1 al Magento 2 después de la migración completa de datos. |

## Atributos de información de base de datos de origen

| Documento | Campo | ¿Requerido? |
|---|---|---|
| `name` | Nombre de base de datos del servidor Magento 1. | yes |
| `host` | Dirección IP del host del servidor Magento 1. | yes |
| `port` | Número de puerto del servidor Magento 1. | no |
| `user` | Nombre de usuario del servidor de base de datos de Magento 1. | yes |
| `password` | Contraseña del servidor de base de datos Magento 1. | yes |
| `ssl_ca` | Ruta al archivo de la autoridad de certificados SSL. | no |
| `ssl_cert` | Ruta al archivo de certificado SSL. | no |
| `ssl_key` | Ruta al archivo de clave SSL. | no |

## Atributos de información de la base de datos de destino

| Documento | Campo | ¿Requerido? |
|---|---|---|
| `name` | Nombre de base de datos del servidor Magento 2. | yes |
| `host` | Dirección IP del host del servidor Magento 2. | yes |
| `port` | Número de puerto del servidor Magento 2. | no |
| `user` | Nombre de usuario del servidor de base de datos de Magento 2. | yes |
| `password` | Contraseña del servidor de base de datos de Magento 2. | yes |
| `ssl_ca` | Ruta al archivo de la autoridad de certificados SSL. | no |
| `ssl_cert` | Ruta al archivo de certificado SSL. | no |
| `ssl_key` | Ruta al archivo de clave SSL. | no |

## Conexión mediante el protocolo TLS

También puede conectarse a una base de datos utilizando el protocolo TLS (es decir, utilizando claves criptográficas públicas/privadas). Agregue los siguientes atributos opcionales al `database` elemento:

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

## Paso interno

El proceso de migración consta de pasos.

Step es una unidad que proporciona la funcionalidad necesaria para migrar algunos datos separados. El paso puede constar de una o más etapas (comprobación de integridad, datos, comprobación de volumen y delta).

De forma predeterminada, hay varios pasos ([Mapa](#map-step), [EAV](#eav), [Reescrituras de URL](#url-rewrite-step), etc.). Opcionalmente, también puede agregar sus propios pasos.

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

Cada clase de etapa debe implementar StageInterface.

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

Si la fase de datos admite la reversión, debe implementar la variable `RollbackInterface` interfaz.

La visualización del paso en ejecución la proporciona el componente ProgressBar de Symfony (consulte [Barra de progreso](http://symfony.com/doc/current/components/console/helpers/progressbar.html)). Acceda a este componente en un paso como LogLevelProcessor.

Los principales métodos de uso son:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Etapas de paso

### Comprobación de integridad

Cada paso debe comprobar que la estructura de la fuente de datos (Magento 1 de forma predeterminada) y la estructura del destino de los datos (Magento 2) son compatibles. Si no es así, se muestra un error con entidades que no son compatibles. En caso de que los campos tengan diferentes tipos de datos (el mismo campo tiene un tipo de datos decimal en el Magento 1 y un entero en el Magento 2), se muestra un mensaje de advertencia (excepto cuando se trató en el archivo Map).

### Transferencia de datos

En caso de que se pase la comprobación de integridad, se está ejecutando la transferencia de datos. Si aparecen errores, la reversión se ejecuta para volver al estado anterior del Magento 2. Si una clase de paso implementa la variable `RollbackInterface` , el método de reversión se ejecuta cuando hay un error.

### Comprobación del volumen

Una vez migrados los datos, la comprobación de volumen proporciona una comprobación adicional de que todos los datos se transfirieron correctamente.

### Envío delta

La funcionalidad Delta es responsable de entregar el resto de los datos que se agregaron después de la migración principal.

## Modos de ejecución

La herramienta debe ejecutarse en tres modos diferentes en orden particular:

1. configuración: migración de la configuración del sistema
1. datos: migración principal de datos
1. delta: migración del resto de datos que se añadieron después de la migración principal.

Cada modo tiene su propia lista de pasos que se deben ejecutar. Consulte config.xml

### Modo de migración de configuración

El modo de migración de configuración de esta herramienta se utiliza para transferir las siguientes entidades:

1. Sitios web, tiendas, vistas de tiendas.
1. Configuración del almacén (principalmente Stores->Configuration in M2 or System->Configuration in M1)

Toda la configuración del almacén mantiene sus datos en la tabla core_config_data de la base de datos. el archivo settings.xml contiene reglas para esta tabla que se aplican durante el proceso de migración. Este archivo describe la configuración que debe ignorarse, cambiarse el nombre o cambiar sus valores. el archivo settings.xml tiene la siguiente estructura:

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

Bajo el nodo `<key>` hay reglas que funcionan con la columna &quot;ruta&quot; en la variable `core_config_data` tabla. `<ignore>` las reglas impiden que la herramienta transfiera algunos ajustes. En este nodo se pueden usar comodines. Todas las demás configuraciones no enumeradas en `<ignore>` se migran. Si la ruta a un ajuste ha cambiado en el Magento 2, debe agregarse a `//key/rename` , donde la ruta antigua indica en `//key/rename/path` el nodo y la nueva ruta de acceso indican en `//key/rename/to` nodo .

Bajo el nodo `<value>`, hay reglas que funcionan con la columna &quot;valor&quot; en la variable `core_config_data` tabla. Estas reglas tienen como objetivo transformar el valor de la configuración mediante controladores (clases que implementan `Migration\Handler\HandlerInterface`) y adaptarlo al Magento 2.

### Modo de migración de datos

En este modo, se migra la mayoría de los datos. Antes de la migración de datos, las fases de comprobación de integridad se ejecutan para cada paso. Si pasa la comprobación de integridad, la variable [!DNL Data Migration Tool] instala tablas deltalog (con prefijo `m2_cl_*`) y los déclencheur correspondientes a la base de datos de Magento 1 y ejecuta la fase de migración de datos de los pasos. Cuando la migración se completa sin errores, la comprobación de volumen comprueba la coherencia de los datos. Puede mostrar un mensaje de advertencia si migra el almacén en directo. No se preocupe, la migración delta se encarga de estos datos incrementales. Los pasos de migración más valiosos son Mapa, Reescritura de URL y EAV.

#### Paso de mapa

El paso de mapa es responsable de transferir la mayoría de los datos del Magento 1 al Magento 2. Este paso lee las instrucciones del archivo map.xml (ubicado en el `etc/` ). El archivo describe las diferencias entre las estructuras de datos de origen (Magento 1) y destino (Magento 2). En caso de que el Magento 1 contenga tablas o campos que pertenezcan a algunos [Extensión](https://glossary.magento.com/extension) que no existe en el Magento 2, estas entidades se pueden colocar aquí para ignorarlas mediante el paso de mapa. De lo contrario, muestra un mensaje de error.

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

* *source* - contiene reglas de la base de datos de origen

* *destino* - contiene reglas de la base de datos de destino

Opciones:

* *ignore* - documento, campo o tipo de datos marcado con esta opción se ignora

* *cambiar nombre* - describe las relaciones de nombre entre documentos con un nombre diferente. En un caso en el que el nombre del documento de destino no sea el mismo que el documento de origen, se puede utilizar la opción cambiar nombre para establecer el nombre del documento de origen de forma similar al nombre de la tabla de destino

* *move* - establece la regla para mover el campo especificado del documento de origen al documento de destino. NOTA: el nombre del documento de destino debe ser el mismo con el nombre del documento de origen. Si los nombres de documento de origen y destino son diferentes, debe utilizar la opción cambiar nombre para el documento que contiene el campo movido

* *transformación* : es una opción que permite al usuario migrar campos según el comportamiento descrito en los controladores

* *handler* - describe el comportamiento de transformación de los campos. Para llamar al controlador, debe especificar un nombre de clase de controlador en una `<handler>` etiqueta. Utilice la variable `<param>` etiqueta con el nombre del parámetro y los datos de valor para pasarlos al controlador

**Fuente** operaciones disponibles:

| Documento | Campo |
|--- |--- |
| ignorar cambio | ignorar transformación |

**Destino** operaciones disponibles:

| Documento | Campo |
|--- |--- |
| ignore | ignorar transformación |

#### Comodín

Para ignorar documentos con partes similares (`document_name_1`, `document_name_2`), puede utilizar la funcionalidad comodín. Put `*` símbolo en lugar de parte repetida (`document_name_*`) y esta máscara cubre todos los documentos de origen o destino que cumplan con esta máscara.

#### Paso de reescritura de URL

Este paso es complejo porque hay muchos algoritmos diferentes desarrollados en el Magento 1 que no son compatibles con el Magento 2. Para diferentes versiones del Magento 1, puede haber diferentes algoritmos. Por lo tanto, en la carpeta Step/UrlRewrite hay clases que se desarrollaron para algunas versiones particulares de Magento y Migration\Step\UrlRewrite\Version191to2000 is one of them. Puede transferir los datos de Reescrituras de URL del Magento 1.9.1 al Magento 2.

#### Paso EAV

Este paso transfiere todos los atributos (producto, cliente, RMA) del Magento 1 al Magento 2. Utiliza el archivo map-eav.xml que contiene reglas similares a las del archivo map.xml para casos específicos de procesamiento de datos.

Algunas de las tablas que se procesan en el paso :

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Modo de migración Delta

Después de la migración principal, se podrían haber agregado datos adicionales a la base de datos de Magento 1 (por ejemplo, por clientes en tienda). Para realizar un seguimiento de estos datos, la herramienta configura los déclencheur de base de datos para las tablas al principio del proceso de migración. Para obtener más información, consulte [Migración de datos creados por extensiones de terceros](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Fuentes de datos

Para llegar a las fuentes de datos del Magento 1 y del Magento 2 y operar con sus datos (seleccionar, actualizar, insertar, eliminar) hay muchas clases en la carpeta de recursos. Migration\ResourceModel\Source y Migration\ResourceModel\Destination son clases principales. Todos los pasos de migración lo utilizan para operar con datos. Estos datos están contenidos en clases como Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure, etc.

Este es un diagrama de clases de estas clases:

![Estructura de datos de la herramienta de migración](../../assets/data-migration/MmigrationToolDataStructure.png)

## Registro

Para implementar la salida del proceso de migración y controlar todos los niveles posibles se aplica el registrador PSR, que se utiliza en el Magento. `\Migration\Logger\Logger` se implementó para proporcionar funcionalidad de registro. Para utilizar el registrador, debe inyectarlo a través del constructor [inyección de dependencia](https://glossary.magento.com/dependency-injection).

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

A continuación, puede utilizar esta clase para registrar algunos eventos:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Existe la posibilidad de personalizar dónde debe escribirse la información de registro. Para ello, agregue un controlador al registrador mediante el método pushHandler() del registrador. Cada controlador debe implementar `\Monolog\Handler\HandlerInterface` interfaz. Por ahora hay dos controladores:

* Controlador de consola: escribe mensajes en la consola

* ControladorDeArchivo: escribe mensajes en el archivo de registro que se ha establecido en la opción de configuración &quot;log_file&quot;

También es posible implementar cualquier controlador adicional. Hay un conjunto de controladores en el marco de Magento. Ejemplo de adición de controladores al registrador:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Para configurar datos adicionales para registrador (modo actual, nombre de tabla) puede utilizar procesadores registradores. Hay un procesador existente (MessageProcessor). Se crea para agregar datos &quot;adicionales&quot; para el registro de mensajes y se llama cada vez que se ejecuta el método log. MessageProcessor ha protegido $extra var, que contiene valores vacíos para &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; y &#39;table&#39;. Se pueden pasar datos adicionales al procesador como un segundo parámetro (contexto) para el método de registro. Actualmente, conjuntos de datos adicionales en procesador en AbstractStep->runStage (pasar el modo actual, etapa y paso al procesador) y clases de datos donde se usa el método logger->debug (pasar el nombre de tabla de migración). Ejemplo de adición de procesadores al registrador:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Existe la posibilidad de establecer el nivel de detalle. En este momento, hay tres niveles:

* `ERROR` (solo escribe errores en el registro)
* `INFO` (solo se escribe información importante en el registro, valor predeterminado)
* `DEBUG` (todo está escrito)

El nivel de registro de versbosidad se puede configurar para cada controlador por separado llamando a `setLevel()` método. Si desea establecer el nivel de extensión mediante el parámetro de línea de comandos, debe cambiar la opción &quot;detallado&quot; al iniciar la aplicación.

Puede dar formato a los mensajes de registro con el formateador monolog. Para que la funcionalidad del formateador funcione, debe especificar el controlador de registro mediante la variable `setFormatter()` método. Actualmente, tenemos una clase de formateador (`MessageFormatter`) que establece cierto formato (depende del nivel de extensión) durante la gestión del mensaje (a través de la variable `format()` método ejecutado desde el controlador).

La manipulación del registrador (adición de controladores y procesadores) y el procesamiento en modo detallado se realiza en el `process()` método de la variable `Migration\Logger\Manager` Clase . Se llama al método cuando se inicia la aplicación.

## Pruebas automáticas

Existen tres tipos de pruebas en la variable [!DNL Data Migration Tool]:

* Estático
* Unidad
* Integración

Se encuentran en el `tests/` , que es el mismo que el tipo de prueba (las pruebas unitarias se encuentran en el `tests/unit` ). Para iniciar la prueba, debe tener instalada la unidad de teléfono. Cambie el directorio actual al directorio de prueba e inicie phpunit. Por ejemplo:

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
