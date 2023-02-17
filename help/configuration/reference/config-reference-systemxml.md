---
title: referencia system.xml
description: Descubra cómo el archivo XML del sistema administra la configuración de la aplicación Commerce.
badge: label="Contribuido por David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
source-git-commit: d7f32690b25c61fa31a99e6d02f9f1025de2bb99
workflow-type: tm+mt
source-wordcount: '2685'
ht-degree: 0%

---


# referencia system.xml

La variable `system.xml` permite administrar la configuración del sistema de comercio. Utilice este tema como referencia general para la variable `system.xml` archivo. La variable `system.xml` el archivo se encuentra en `etc/adminhtml/system.xml` en una extensión Commerce 2 determinada.

El siguiente fragmento de código muestra el esqueleto desnudo del archivo:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Si desea validación *XSD instantánea en su IDE, puede ejecutar `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Tabulaciones // Secciones // Grupos // Campos

En el `system.xml` , es posible definir cuatro tipos diferentes de entidades, que están relacionadas entre sí. En la siguiente sección se describe la relación entre fichas, secciones, grupos y campos. La siguiente captura de pantalla muestra la Configuración del sistema Commerce 2 en el servidor de administración.
Los cuadrados rojos marcan los diferentes tipos definidos en la variable `system.xml` archivo:

![Captura de pantalla que muestra una sección configurada en el Administrador.](../../assets/configuration/magento2-system-configuration.png)

Las pestañas se utilizan para dividir diferentes áreas de configuración semánticamente. Cada ficha puede contener una o más secciones, a las que también se puede hacer referencia como submenús. Una sección contiene uno o más grupos.
Cada grupo enumera uno o más campos. También puede utilizar un grupo para agregar una descripción general para los campos siguientes. Como se ha mencionado, cada grupo puede tener uno o más campos. Los campos son la entidad más pequeña del contexto de configuración del sistema.

## Pestañas

A `<tab>`-Etiqueta hace referencia a una ficha existente o nueva en la configuración del sistema.

### Referencia de atributos de tabulación

A `<tab>`-La etiqueta puede tener los siguientes atributos:

| Atributo | Descripción | Tipo | Requerido |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Define el identificador que se utiliza para hacer referencia a la sección . | `typeId` | obligatorio |
| `translate` | Define el campo que debe ser traducible. Proporcionar `label` para que la etiqueta sea traducible. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML procesado (el valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos llevan la sección al final de la página; números bajos llevan la sección a la parte superior. | `float` | opcional |
| `class` | Agrega una clase CSS definida al elemento HTML de pestañas procesado. | `string` | opcional |

### Referencia de nodo de ficha

A `<tab>`-La etiqueta puede tener el siguiente elemento secundario:

| Nodo | Descripción | Tipo |
|---------|------------------------------------------------------|----------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |

### Ejemplo: Crear una pestaña

El siguiente fragmento de código muestra la creación de una nueva pestaña con datos de ejemplo.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

El fragmento anterior crea una nueva pestaña con el identificador `A_UNIQUE_ID`. Como `translate`-attribute está definido y hace referencia a la etiqueta, la variable `label`-node es traducible. Durante el proceso de renderización, la clase CSS `a-custom-css-class-to-style-this-tab` se aplicará al elemento HTML creado para esta pestaña.
La variable `sortOrder`-attribute con el valor de `10` define la posición de la pestaña en la lista de todas las pestañas cuando se procesa.

## Secciones

A `<section>`-Etiqueta referencias a una sección existente o a una nueva sección en la configuración del sistema.

### Referencia de atributos de sección

A `<section>`-La etiqueta puede tener los siguientes atributos:

| Atributo | Descripción | Tipo | Requerido |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define el identificador que se utiliza para hacer referencia a la sección . | `typeId` | obligatorio |
| `translate` | Define el campo que debe ser traducible. Proporcionar `label` para que la etiqueta sea traducible. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML procesado. El valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos llevarán la sección a la parte inferior de la página; los números bajos llevarán la sección a la parte superior. | `float` | opcional |
| `showInDefault` | Define si la sección se muestra en el ámbito de configuración predeterminado. Especifique `1` para mostrar la sección y `0` para ocultar la sección. | `int` | opcional |
| `showInStore` | Define si la sección se muestra en el nivel de tienda. Especifique `1` para mostrar la sección y `0` para ocultar la sección. | `int` | opcional |
| `showInWebsite` | Define si la sección se muestra a nivel de sitio web. Especifique `1` para mostrar la sección y `0` para ocultar la sección. | `int` | opcional |
| `canRestore` | Define si la sección se puede restaurar a su valor predeterminado. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Al proporcionar un identificador de otra sección, el contenido de este nodo amplía la sección a la que hace referencia. | `string` | opcional |

### Referencia del nodo de sección

A `<section>`-La etiqueta puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |
| `class` | Agrega una clase CSS definida al elemento HTML de sección procesada. | `string` |
| `tab` | Hace referencia a la pestaña asociada. Espera el ID de la pestaña . | `typeTabId` |
| `header_css` | No se ha utilizado ni evaluado en el momento de escribir este artículo. | `string` |
| `resource` | Hace referencia a un recurso ACL para proporcionar la configuración de permisos para esta sección. | `typeAclResourceId` |
| `group` | Defina uno o más subgrupos. | `typeGroup` |
| `frontend_model` | Especifica un modelo de front-end diferente para cambiar la renderización y modificar la salida. | `typeModel` |
| `include` | Se utiliza para incluir elementos adicionales `system_include.xsd` archivos compatibles. Generalmente se utiliza para estructurar grandes dimensiones `system.xml` archivos. | `includeType` |

### Ejemplo: Crear una sección y asignarla a una pestaña

El siguiente fragmento de código muestra el uso básico de la creación de una nueva sección.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

La sección descrita anteriormente define el ID de `A_UNIQUE_SECTION_ID`, está visible en la vista de configuración predeterminada y en un contexto de tienda. La variable `label`-node es traducible. La sección está asociada a la pestaña con el ID de `A_UNIQUE_ID`. Solo los usuarios que tengan los permisos definidos en la ACL pueden acceder a la sección `VENDOR_MODULE::path_to_the_acl_resource`.

## Grupos

La variable `<group>`-Tag se utiliza para agrupar campos.

### Referencia de atributos de grupo

A `<group>`-La etiqueta puede tener los siguientes atributos:

| Atributo | Descripción | Tipo | Requerido |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define el identificador que se utiliza para hacer referencia al grupo. | `typeId` | obligatorio |
| `translate` | Define los campos que deben traducirse. Proporcionar `label` para que la etiqueta sea traducible. Los campos múltiples deben separarse con un espacio. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML procesado. El valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos llevarán la sección a la parte inferior de la página; los números bajos llevarán la sección a la parte superior. | `float` | opcional |
| `showInDefault` | Define si el grupo se muestra en el ámbito de configuración predeterminado. Especifique `1` para mostrar el grupo y `0` para ocultar el grupo. | `int` | opcional |
| `showInStore` | Define si el grupo se muestra en el nivel de tienda. Especifique `1` para mostrar el grupo y `0` para ocultar el grupo. | `int` | opcional |
| `showInWebsite` | Define si el grupo se muestra a nivel de sitio web. Especifique `1` para mostrar el grupo y `0` para ocultar el grupo. | `int` | opcional |
| `canRestore` | Define si el grupo se puede restaurar a su valor predeterminado. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Al proporcionar un identificador de otro grupo, el contenido de este nodo amplía la sección a la que hace referencia. | `string` | opcional |

### Referencia de nodo de grupo

A `<group>`-La etiqueta puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |
| `fieldset_css` | Agrega una o más clases CSS a un conjunto de campos de grupo. | `string` |
| `frontend_model` | Especifica un modelo de front-end diferente para cambiar la renderización y modificar la salida. | `typeModel` |
| `clone_model` | Especifica un modelo determinado para clonar campos. | `typeModel` |
| `clone_fields` | Se ha habilitado o deshabilitado la clonación de campos. | `int` |
| `help_url` | No se puede ampliar. Consulte a continuación. | `typeUrl` |
| `more_url` | No se puede ampliar. Consulte a continuación. | `typeUrl` |
| `demo_link` | No se puede ampliar. Consulte a continuación. | `typeUrl` |
| `comment` | Agrega un comentario debajo de la etiqueta de grupo. Usando `<![CDATA[//]]>` se puede aplicar el HTML . | `string` |
| `hide_in_single_store_mode` | Indica si el grupo debe estar visible en el modo de almacén único. `1` oculta el grupo; `0` muestra el grupo. | `int` |
| `field` | Defina uno o más campos que deberían estar disponibles en este grupo. | `field` |
| `group` | Defina uno o más subgrupos. | `unbounded` |
| `depends` | Se puede utilizar para declarar dependencias en otros campos. Se utiliza para mostrar campos o grupos específicos solo cuando un campo determinado tiene un valor de `1`. Este nodo espera un `section/group/field`-string. | `depends` |
| `attribute` | Los modelos de front-end pueden utilizar atributos personalizados. Normalmente se utiliza para hacer más dinámico un modelo de front-end determinado. | `attribute` |
| `include` | Se utiliza para incluir elementos adicionales `system_include.xsd` archivos compatibles. Generalmente se utiliza para estructurar grandes dimensiones `system.xml` archivos. | `includeType` |

>[!WARNING]
>
>Los nodos `more_url`, `demo_url` y `help_url` están definidas por un modelo de front-end de PayPal que solo se utiliza una vez. Estos nodos no se pueden reutilizar.

### Ejemplo: Crear un grupo para una sección determinada

El siguiente fragmento de código muestra el uso básico de la creación de un grupo nuevo.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

El grupo descrito anteriormente define el ID `A_UNIQUE_GROUP_ID`, está visible en la vista de configuración predeterminada y en un contexto de tienda. Ambas, la `label` y `comment` están marcados como traducibles.

## Campos

La variable `<field>`-Tag se usa dentro de `<group>`-Etiquetas para definir valores de configuración específicos.

### Referencia de atributos de campo

A `<field>`-La etiqueta puede tener los siguientes atributos:

| Atributo | Descripción | Tipo | Requerido |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define el identificador que se utiliza para hacer referencia al campo. | `typeId` | obligatorio |
| `translate` | Define los campos que deben traducirse. Proporcionar `label` para que la etiqueta sea traducible. Los campos múltiples deben separarse con un espacio. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML procesado. El valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos llevan la sección al final de la página; números bajos llevan la sección a la parte superior. | `float` | opcional |
| `showInDefault` | Define si el campo se muestra en el ámbito de configuración predeterminado. Especifique `1` para mostrar el campo y `0` para ocultar el campo. | `int` | opcional |
| `showInStore` | Define si el campo se muestra en el nivel de tienda. Especifique `1` para mostrar el campo y `0` para ocultar el campo. | `int` | opcional |
| `showInWebsite` | Define si el campo se muestra a nivel de sitio web. Especifique `1` para mostrar el campo y `0` para ocultar el campo. | `int` | opcional |
| `canRestore` | Define si el campo se puede restaurar a su valor predeterminado. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Al proporcionar un identificador de otro campo, el contenido de este nodo amplía la sección a la que hace referencia. | `string` | opcional |

### Referencia de tipo de campo

A `<field>`-La etiqueta puede tener los siguientes valores para la variable `type=""` atributo:

| Tipo | Descripción |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Campo de texto estándar de una sola fila |
| `textarea` | Bloque de texto |
| `select` | Menú desplegable Normal , puede necesitar un `source_model`. También se usa para `Yes/No` selecciones. Consulte `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` por ejemplo. |
| `multiselect` | Like `select` pero son válidas varias opciones. |
| `button` | Botón que déclencheur un evento inmediato. Requiere un modelo front-end personalizado para definir el texto del botón y la acción. Consulte `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` por ejemplo. |
| `obscure` | Campo de texto con el valor cifrado y mostrado como `****`. Cambiar el tipo utilizando &quot;Elemento Inspect&quot; en el navegador no muestra el valor. |
| `password` | Like `obscure` excepto que el valor oculto no está cifrado y el cambio forzado de tipo utilizando &quot;Elemento Inspect&quot; en el explorador sí revela el valor. |
| `file` | Permite cargar un archivo para procesarlo. |
| `label` | Muestra una etiqueta en lugar de un campo editable. Utilice este tipo cuando un campo solo se puede editar en ámbitos específicos, por ejemplo, en el nivel de vista de la tienda . |
| `time` | Controle para establecer la hora mediante tres listas desplegables: hora, minuto y segundo. |
| `allowspecific` | Una lista de selección múltiple de países específicos. Requiere un `source_model` como `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Permite cargar una imagen. |
| `note` | Permite agregar una nota informativa a la página. Este tipo requiere un `frontend_model` para procesar la nota. |

También es posible crear un tipo de campo personalizado. Esto suele hacerse cuando se requiere un botón especial, con una acción. Para ello, se necesitan dos elementos principales:

- Creación de un bloque en la variable `adminhtml` area
- Configuración de la variable `type=""` a la ruta a este bloque

El propio bloque requiere, como mínimo, un `__construct` método y `getElementHtml()` método. La variable [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) es un ejemplo sencillo de un tipo personalizado.

Por ejemplo, en el módulo OfflineShipping, el botón Export se define en `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` y la definición del campo tiene el siguiente aspecto:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Referencia del nodo de campo

A `<field>`-La etiqueta puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |
| `comment` | Agrega un comentario debajo de la etiqueta de campo. Usando `<![CDATA[//]]>` se puede aplicar el HTML . | `string` |
| `tooltip` | Otro posible elemento de front-end que se puede utilizar para describir el significado de este campo. Se muestra como un pequeño icono junto al campo . | `string` |
| `hint` | Muestra información adicional. Solo disponible con `frontend_model`. | `string` |
| `frontend_class` | Agrega una clase CSS definida al elemento HTML de sección procesada. | `string` |
| `frontend_model` | Especifica un modelo de front-end diferente para cambiar la renderización y modificar la salida. | `typeModel` |
| `backend_model` | Especifica un modelo backend diferente para modificar los valores configurados. | `typeModel` |
| `source_model` | Especifica un modelo de origen diferente que proporciona un conjunto específico de valores. | `typeModel` |
| `config_path` | Se puede utilizar para sobrescribir la ruta de configuración genérica de un campo. | `typeConfigPath` |
| `validate` | Defina distintas reglas de validación (separadas por espacios). A continuación se muestra la lista completa de referencia de las reglas de validación disponibles. | `string` |
| `can_be_empty` | Se usa cuando `type` es `multiselect` para especificar que un campo puede estar vacío. | `int` |
| `if_module_enabled` | Se utiliza para mostrar un campo solo cuando un módulo determinado está habilitado. | `typeModule` |
| `base_url` | Se utiliza en combinación con `upload_dir` para cargas de archivos. | `typeUrl` |
| `upload_dir` | Especifique un directorio de destino para las cargas. Este nodo tiene atributos y nodos adicionales. Búsquelos antes de usar esto. | `typeUploadDir` |
| `button_url` | Muestra un botón si `button_url` y `button_label` están especificados. Normalmente se utiliza en combinación con un modelo de front-end personalizado. | `typeUrl` |
| `button_label` | Muestra un botón si `button_label` y `button_url` están especificados. Normalmente se utiliza en combinación con un modelo de front-end personalizado. | `string` |
| `more_url` | No se puede ampliar. Consulte a continuación. | `typeUrl` |
| `demo_url` | No se puede ampliar. Consulte a continuación. | `typeUrl` |
| `hide_in_single_store_mode` | Indica si el grupo debe estar visible en el modo de almacén único. `1` oculta el grupo; `0` muestra el grupo. | `int` |
| `source_service` | Servicio utilizado para rellenar opciones seleccionadas. | `complexType` |
| `options` | No se usa. Posiblemente obsoleto. | `complexType` |
| `depends` | Se puede utilizar para declarar dependencias a otros campos. Se utiliza para mostrar solo campos o grupos específicos cuando un campo determinado tiene un valor de `1`. Este nodo espera un `section/group/field`-string. | `complexType` |
| `attribute` | Los modelos de front-end pueden utilizar atributos personalizados. Normalmente se utiliza para hacer más dinámico un modelo de front-end determinado. | `complexType` |
| `requires` | No se puede ampliar. Consulte a continuación. | `complexType` |

>[!WARNING]
>
>Los nodos `more_url`, `demo_url`, `requires` y `options` están definidas por un modelo de pago principal diferente y se utilizan solo una vez. Estos nodos no se pueden reutilizar.

### Ejemplo: Crear dos campos en un grupo determinado

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

El ejemplo anterior crea dos campos, tanto visibles como configurables de forma predeterminada como en la vista de tienda. Ambos campos tienen un comentario y una información de objeto para describir su propósito para el usuario. La variable `label`-node es traducible.
El campo con el identificador `ANOTHER_UNIQUE_FIELD_ID` está visible cuando el módulo dado de la variable `if_module_enabled` está habilitado globalmente. El campo también valida su valor frente a las reglas `required-entry` y `no-whitespace`.
El campo con el identificador `A_UNIQUE_FIELD_ID` define un modelo de origen diferente que proporciona valores que `Yes` y `No`.

### Modelos de origen comunes

Los siguientes modelos de origen son proporcionados por Commerce 2 Core. En general, hay muchos más modelos de fuente; en la siguiente lista se describen las más comunes. Tenga en cuenta que estos modelos de origen necesitan el atributo field `type` para configurar como `select` para funcionar correctamente.

| Modelo de origen | Descripción |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Proporciona los valores `Yes`, `No` y `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Proporciona los valores `Enable`, `Disable`. Guarda los valores como `0` y `1` en la base de datos. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Proporciona los valores `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` y `24 Hours`. Los valores se guardan como enteros. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Proporciona los valores del formato de hora (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Proporciona los valores `Daily`, `Weekly` y `Monthly`. Los valores se guardan en la base de datos como `D`, `W` y `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Proporciona los valores para un código de 2 letras de un idioma determinado en formato ISO 639-1 (por ejemplo, en). |
| `Magento\Config\Model\Config\Source\Locale` | Proporciona los valores similares a los anteriores, pero pertenecen a una configuración regional (por ejemplo, en_US). |

### Validación de campos

Un campo puede tener una o más clases de validador asignadas para asegurarse de que la entrada del usuario cumple los requisitos de la extensión. Las reglas de validación se pueden aplicar con la variable `<validate>`-Etiqueta.
En el siguiente ejemplo se valida un campo y se añaden varias reglas de validación diferentes.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Las siguientes reglas de validación están disponibles:

| Regla | Descripción |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Permite letras, números, espacios o guiones bajos únicamente. |
| `integer` | Permite un número no decimal positivo o negativo. |
| `ipv4` | Permite una dirección IP v4 válida. |
| `ipv6` | Permite una dirección IP v6 válida. |
| `letters-only` | Permite sólo letras. Por ejemplo, `abcABC`. |
| `letters-with-basic-punc` | Permite letras o signos de puntuación.<br>Debe pasar la siguiente expresión: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Permite un número de teléfono móvil (Reino Unido). |
| `no-marginal-whitespace` | Despermite espacios en blanco al principio o al final del valor. |
| `no-whitespace` | Despermite espacios en blanco. |
| `phoneUK` | Permite un número de teléfono (Reino Unido). |
| `phoneUS` | Permite un número de teléfono (EE. UU.). |
| `required-entry` | Despermite un valor vacío (validación equivalente a `validate-no-empty`).<br>Mensaje de error de validación: &quot;Se trata de un campo obligatorio&quot;. |
| `time` | Permite un tiempo válido en formato de 24 horas, entre las 00:00 y las 23:59. Por ejemplo `15`, `15:05` o `15:05:48`. |
| `time12h` | Permite un tiempo válido en formato de 12 horas, entre las 12:00 y las 11:59:59 pm. Por ejemplo `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Permite 7 o más caracteres, utilizando caracteres numéricos y alfabéticos. |
| `validate-alphanum-with-spaces` | Permite el uso de letras (a-z o A-Z), números (0-9) o solo espacios. |
| `validate-clean-url` | Permite una dirección URL válida. Por ejemplo, `https://www.example.com` o `www.example.com`. |
| `validate-currency-dollar` | Permite una cantidad válida (en dólares). Por ejemplo, 100,00 $. |
| `validate-data` | Permite el uso de letras (a-z o A-Z), números (0-9) o guiones bajos (\_) únicamente.<br>El primer carácter debe ser una letra.<br>(Debe coincidir con la expresión: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Mensaje de error de validación: &quot;Utilice solo letras (a-z o A-Z), números (0-9) o guiones bajos (\_) en este campo, y el primer carácter debe ser una letra.&quot; |
| `validate-date-au` | Aplica el siguiente formato de fecha: dd/mm/aaaa. Por ejemplo, 03/17/2006 para el 17 de marzo de 2006. |
| `validate-email` | Permite una dirección de correo electrónico válida. Por ejemplo, johndoe@domain.com. |
| `validate-emailSender` | Permite una dirección de correo electrónico válida. Por ejemplo, johndoe@domain.com. |
| `validate-fax` | Permite un número de fax válido. Por ejemplo, 123-456-7890. |
| `validate-no-empty` | Despermite un valor vacío (validación equivalente a `requried-entry`).<br>Mensaje de error de validación: &quot;Valor vacío&quot;. |
| `validate-no-html-tags` | No permite el uso de etiquetas de HTML. |
| `validate-password` | Permite 6 o más caracteres. Se ignorarán los espacios al inicio y al final. |
| `validate-phoneLax` | Permite un número de teléfono válido. Por ejemplo, (123) 456-7890 o 123-456-7890. |
| `validate-phoneStrict` | Permite un número de teléfono válido. Por ejemplo, (123) 456-7890 o 123-456-7890. |
| `validate-select` | Aplica que la opción seleccionada no tenga un `null` valor, valor de cadena de `none` o longitud de cadena de 0. |
| `validate-ssn` | Permite un número de seguridad social válido (EE.UU.). Por ejemplo, 123-45-6789. |
| `validate-street` | Permite el uso de letras (a-z o A-Z), números (0-9), espacios y &quot;#&quot; únicamente. |
| `validate-url` | Permite una dirección URL válida. Se requiere el protocolo (http://, https:// o ftp://). |
| `validate-xml-identifier` | Permite un identificador XML válido. Por ejemplo, algo_1, block5, id-4. |
| `validate-zip-us` | Permite un código postal válido (EE. UU.). Por ejemplo, 90602 o 90602-1234. |
| `vinUS` | Permite el valor del número de identificación (VIN) del vehículo (EE.UU.). |

### Valores predeterminados

Los valores predeterminados de los campos se pueden configurar en el `etc/config.xml` especificando el valor predeterminado en la variable `section/group/field_ID` nodo .

#### Ejemplo: Configuración del valor predeterminado para `ANOTHER_UNIQUE_FIELD_ID` (Ámbito predeterminado)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Ejemplo: Configuración del valor predeterminado para `ANOTHER_UNIQUE_FIELD_ID` (Ámbito del sitio web)

Al usar la variable `websites` especifique el valor predeterminado para un sitio web específico.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
