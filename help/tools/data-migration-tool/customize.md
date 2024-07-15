---
title: Personalizar  [!DNL Data Migration Tool]
description: Aprenda a personalizar  [!DNL Data Migration Tool]  para transferir datos creados por extensiones entre el Magento 1 y el Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Configurar [!DNL Data Migration Tool]

A veces, el formato de datos y la estructura creados por [extensiones](https://marketplace.magento.com/extensions.html) o código personalizado son diferentes entre el Magento 1 y el Magento 2. Utilice puntos de extensión dentro de [!DNL Data Migration Tool] para migrar estos datos. Si el formato y la estructura de los datos son los mismos, la herramienta puede migrar automáticamente los datos sin la intervención del usuario.

Durante la migración, el [Paso de asignación](technical-specification.md#map-step) analiza y compara todas las tablas de Magento 1 y Magento 2, incluidas las creadas por las extensiones. Si las tablas son iguales, la herramienta migra automáticamente los datos. Si las tablas difieren, la herramienta finaliza y se lo comunica al usuario.

>[!NOTE]
>
>Lea la [especificación técnica](technical-specification.md) antes de intentar extender [!DNL Data Migration Tool]. Además, revise la [Guía de migración](../overview.md) para obtener información general acerca del uso de la herramienta de migración.


## Pequeños cambios de formato y estructura de datos

En la mayoría de los casos, el [paso de asignación](technical-specification.md#map-step) resuelve suficientemente los cambios menores de formato y estructura de datos mediante los siguientes métodos en el archivo `map.xml`:

- Cambiar nombres de tablas o campos con reglas de asignación
- Transformar formatos de datos con controladores existentes o con un controlador personalizado

A continuación se muestra un ejemplo de uso de reglas de asignación y de un controlador. Este ejemplo utiliza una extensión hipotética de Magento 1 llamada &quot;GreatBlog&quot; que se ha mejorado para el Magento 2.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- No migre datos innecesarios de la tabla de índice `great_blog_index`.
- Se cambió el nombre de la tabla `great_blog_publication` a `great_blog_post` en el Magento 2, por lo que los datos se migran a la nueva tabla.
   - Se cambió el nombre del campo `summary` a `title`, por lo que los datos se migran al nuevo campo.
   - El campo `priority` se eliminó y ya no existe en el Magento 2.
   - Los datos del campo `body` han cambiado de formato y el controlador personalizado debe procesarlos: `\Migration\Handler\GreatBlog\NewFormat`.
- Se ha desarrollado una nueva función de clasificación para la extensión &quot;GreatBlog&quot; en Magento 2.
   - Se creó una nueva tabla `great_blog_rating`.
   - Se creó un nuevo campo `great_blog_post.rating`.

### Ampliación de la asignación en otros pasos

Otros pasos admiten la asignación, como el [paso EAV](technical-specification.md#eav-step) y el paso Atributos del cliente. Estos pasos migran una lista predefinida de tablas de Magento. Por ejemplo, supongamos que la extensión &quot;GreatBlog&quot; tiene un campo adicional en la tabla `eav_attribute` y el nombre ha cambiado en el Magento 2. Dado que el [paso EAV](technical-specification.md#eav-step) procesa la tabla, las reglas de asignación deben escribirse para el archivo `map-eav.xml`. Los archivos `map.xml` y `map-eav.xml` utilizan el mismo esquema `map.xsd`, por lo que las reglas de asignación siguen siendo las mismas.

## Principales cambios de formato y estructura de datos

Además del paso Asignar, hay otros pasos en el archivo `config.xml` que migran datos con cambios importantes de formato y estructura, entre los que se incluyen:

- [Paso de reescritura de URL](technical-specification.md#url-rewrite-step)
- Paso de OrderGrids
- [Paso EAV](technical-specification.md#eav-step)

A diferencia del [Paso de asignación](technical-specification.md#map-step), estos pasos exploran una lista predefinida de tablas en lugar de todas las tablas.

Para realizar cambios importantes en el formato y la estructura de los datos, cree un paso personalizado.

### Creación de una etapa personalizada

En el mismo ejemplo de &quot;GreatBlog&quot;, supongamos que la extensión tiene una tabla en el Magento 1, pero se ha rediseñado para tener dos tablas en el Magento 2.

En el Magento 1, había una sola tabla `greatblog_post`:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

En el Magento 2, se creó una nueva tabla para las etiquetas `greatblog_post_tags`:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

La tabla del Magento 2 `greatblog_post` ahora tiene este aspecto:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Para migrar todos los datos de la estructura de tablas antigua a una nueva, puede crear un paso personalizado en el archivo `config.xml`. Por ejemplo:

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

La herramienta ejecuta pasos de acuerdo con su posición en el archivo `config.xml`; de arriba abajo. En nuestro ejemplo, `GreatBlog Step` se ejecuta en último lugar.

Los pasos pueden incluir cuatro tipos de clases:

- Comprobación de integridad
- Entrega de datos
- Comprobación del volumen
- Entrega Delta

>[!NOTE]
>
>Consulte [Configuración](technical-specification.md#configuration), [Pasos internos](technical-specification.md#step-internals), [Etapas](technical-specification.md#step-stages) y [Modos de ejecución](technical-specification.md#running-modes) para obtener más información.


Las consultas SQL complejas se pueden ensamblar dentro de estas clases para recuperar y migrar datos. Además, estas tablas deben &quot;ignorarse&quot; en el [Paso de asignación](technical-specification.md#map-step) porque analiza todas las tablas existentes e intenta migrar los datos a menos que se encuentren en la etiqueta `<ignore>` del archivo `map.xml`.

Para la comprobación de integridad, defina un archivo de asignación adicional en el archivo `config.xml` para comprobar que la estructura de las tablas es la esperada.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

Asignar archivo `map-greatblog.xml`:

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

La clase de comprobación de integridad `Vendor\Migration\Step\GreatBlog\Integrity` extiende `Migration\App\Step\AbstractIntegrity` y contiene el método `perform` donde se comprueba la estructura de la tabla:

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

A continuación, debe crear una clase para procesar y guardar datos en la base de datos del Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

En una clase de volumen `Vendor\Migration\Step\GreatBlog\Volume`, comprobamos si los datos se han migrado completamente:

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

Para agregar la funcionalidad de migración delta, agregue un nuevo grupo al archivo `deltalog.xml`. En `group`, especifique el nombre de las tablas en las que se deben comprobar los cambios:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

A continuación, cree la clase `Delta` `Vendor\Migration\Step\GreatBlog\Delta` que extiende `Migration\App\Step\AbstractDelta`:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

Después de la implementación de los pasos personalizados que se proporciona en los ejemplos, el sistema toma los datos de la tabla del Magento único 1,
procesarlo con la clase `Vendor\Migration\Step\GreatBlog\Data` y almacenar los datos en dos tablas de Magento 2. Los registros nuevos y modificados se entregan en la migración delta mediante la clase `Vendor\Migration\Step\GreatBlog\Delta`.

## Métodos de extensión prohibidos

Dado que [!DNL Data Migration Tool] y el Magento 2 evolucionan constantemente, los pasos y controladores existentes están sujetos a cambios. Recomendamos encarecidamente no anular el comportamiento de pasos como el [Paso de asignación](technical-specification.md#map-step), el [Paso de reescritura de URL](technical-specification.md#url-rewrite-step) y los controladores ampliando sus clases.

Algunos pasos no admiten la asignación y no se pueden cambiar sin modificar el código. Puede escribir un paso adicional que cambie los datos al final de la migración o crear un [problema de GitHub](https://github.com/magento/data-migration-tool/issues) y solicitar un nuevo punto de extensión en el paso existente.
