---
title: Personalice el [!DNL Data Migration Tool]
description: Aprenda a personalizar el [!DNL Data Migration Tool] para transferir los datos creados por las extensiones entre el Magento 1 y el Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---


# Configure las variables [!DNL Data Migration Tool]

A veces, el formato de datos y la estructura creados por [extensiones](https://marketplace.magento.com/extensions.html) o el código personalizado es diferente entre el Magento 1 y el Magento 2. Utilice puntos de extensión dentro de la variable [!DNL Data Migration Tool] para migrar estos datos. Si el formato y la estructura de los datos son los mismos, la herramienta puede migrar automáticamente los datos sin intervención del usuario.

Durante la migración, la variable [Paso de mapa](technical-specification.md#map-step) analiza y compara todas las tablas Magento 1 y Magento 2, incluidas las creadas por extensiones. Si las tablas son iguales, la herramienta migra automáticamente los datos. Si las tablas son diferentes, la herramienta finaliza y notifica al usuario.

>[!NOTE]
>
>Lea el [Especificación técnica](technical-specification.md) antes de intentar ampliar el [!DNL Data Migration Tool]. Además, revise el [Guía de migración](../overview.md) para obtener información general sobre el uso de la herramienta de migración.


## Cambios menores en el formato y la estructura de los datos

En la mayoría de los casos, la variable [Paso de mapa](technical-specification.md#map-step) resuelve de forma suficiente los cambios menores de formato y estructura de datos mediante los siguientes métodos en la sección `map.xml` archivo:

- Cambiar nombres de campos o tablas con reglas de asignación
- Transformar formatos de datos con controladores existentes o un controlador personalizado

A continuación se muestra un ejemplo del uso de las reglas de asignación y de un controlador. Este ejemplo utiliza una extensión hipotética de Magento 1 llamada &quot;GreatBlog&quot; que se ha mejorado para el Magento 2.

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

- No migre los datos innecesarios del `great_blog_index` índice.
- La tabla `great_blog_publication` se cambió el nombre a `great_blog_post` en el Magento 2, por lo que los datos se migran a la nueva tabla.
   - La variable `summary` se cambió el nombre del campo a `title`, por lo que los datos se migran al nuevo campo.
   - La variable `priority` se ha eliminado y ya no existe en el Magento 2.
   - Los datos de la variable `body` El campo ha cambiado el formato y el controlador personalizado debe procesarlo: `\Migration\Handler\GreatBlog\NewFormat`.
- Se desarrolló una nueva característica de clasificación para la extensión &quot;GreatBlog&quot; en el Magento 2.
   - Un nuevo `great_blog_rating` se creó.
   - Un nuevo `great_blog_post.rating` se creó.

### Ampliación de la asignación en otros pasos

Otros pasos admiten la asignación, como el [EAV Step](technical-specification.md#eav-step) y el paso Atributos del cliente. Estos pasos migran una lista predefinida de tablas de Magento. Por ejemplo, supongamos que la extensión &quot;GreatBlog&quot; tiene un campo adicional en la variable `eav_attribute` y el nombre ha cambiado en el Magento 2. Dado que la tabla la procesa el [EAV Step](technical-specification.md#eav-step), las reglas de asignación deben escribirse para la variable `map-eav.xml` archivo. La variable `map.xml` y `map-eav.xml` los archivos utilizan el mismo `map.xsd` esquema, por lo que las reglas de asignación siguen siendo las mismas.

## Cambios importantes en el formato y la estructura de los datos

Además del paso Mapa, hay otros pasos en la sección `config.xml` que migran datos con cambios importantes de formato y estructura, incluidos:

- [Paso De Reescritura De Url](technical-specification.md#url-rewrite-step)
- Paso OrderGrids
- [EAV Step](technical-specification.md#eav-step)

A diferencia de [Paso de mapa](technical-specification.md#map-step), estos pasos analizan una lista predefinida de tablas en lugar de todas las tablas.

Para cambios importantes en el formato y la estructura de los datos, cree un paso personalizado.

### Crear un paso personalizado

Con el mismo ejemplo &quot;GreatBlog&quot;, supongamos que la extensión tiene una tabla en el Magento 1, pero se ha rediseñado para tener dos tablas en el Magento 2.

En el Magento 1, hubo un único `greatblog_post` tabla:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

En el Magento 2, una nueva tabla para etiquetas `greatblog_post_tags` se introdujo:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post` ahora tiene este aspecto:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Para migrar todos los datos de la estructura de tablas antiguas a una nueva, puede crear un paso personalizado en el `config.xml` archivo. Por ejemplo:

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

La herramienta ejecuta los pasos según su posición en la variable `config.xml` archivo; de arriba a abajo. En nuestro ejemplo, la variable `GreatBlog Step` se ejecuta por última vez.

Los pasos pueden incluir cuatro tipos de clases:

- Verificación de integridad
- Entrega de datos
- Comprobación de volumen
- Entrega de Delta

>[!NOTE]
>
>Consulte [Configuración](technical-specification.md#configuration), [Paso interno](technical-specification.md#step-internals), [Etapas](technical-specification.md#step-stages)y [Modos de ejecución](technical-specification.md#running-modes) para obtener más información.


Las consultas SQL complejas se pueden ensamblar dentro de estas clases para recuperar y migrar datos. Además, estas tablas deben &quot;ignorarse&quot; en la variable [Paso de mapa](technical-specification.md#map-step) porque analiza todas las tablas existentes e intenta migrar los datos a menos que estén en la variable `<ignore>` de la variable `map.xml` archivo.

Para la comprobación de integridad, defina un archivo de asignación adicional en la variable `config.xml` para comprobar que la estructura de las tablas es la esperada.

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

Clase de comprobación de integridad `Vendor\Migration\Step\GreatBlog\Integrity` extensions `Migration\App\Step\AbstractIntegrity` y contiene el `perform` método en el que se verifica la estructura de la tabla:

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

A continuación, debe crear una clase para procesar y guardar datos en la base de datos de Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

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

En una clase Volume `Vendor\Migration\Step\GreatBlog\Volume`, comprobamos si los datos se han migrado completamente:

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

Para agregar la funcionalidad de migración delta, agregue un nuevo grupo al `deltalog.xml` archivo. En `group`, especifique el nombre de las tablas que se deben comprobar para detectar cambios:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

A continuación, cree la variable `Delta` class `Vendor\Migration\Step\GreatBlog\Delta` que se extiende `Migration\App\Step\AbstractDelta`:

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

Después de la implementación de los pasos personalizados que se proporciona en los ejemplos, el sistema toma los datos de la tabla de un solo Magento 1 y los procesa mediante `Vendor\Migration\Step\GreatBlog\Data` y almacene los datos en dos tablas Magento 2. Los registros nuevos y modificados se entregan en la migración delta mediante la variable `Vendor\Migration\Step\GreatBlog\Delta` Clase .

## Métodos de extensión prohibidos

Dado que la variable [!DNL Data Migration Tool] y el Magento 2 evoluciona constantemente, los pasos y controladores existentes están sujetos a cambios. Se recomienda no anular el comportamiento de pasos como el [Paso de mapa](technical-specification.md#map-step), [Paso de reescritura de URL](technical-specification.md#url-rewrite-step)y controladores ampliando sus clases.

Algunos pasos no admiten asignación y no se pueden cambiar sin alterar el código. Puede escribir un paso adicional que cambie los datos al final de la migración o crear un [Problema de GitHub](https://github.com/magento/data-migration-tool/issues) y solicite un nuevo punto de extensión en el paso existente.
