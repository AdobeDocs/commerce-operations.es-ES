---
title: referencia de system.xml
description: Obtenga información sobre cómo administra el archivo XML del sistema la configuración de la aplicación de Commerce.
feature: Configuration, System
badge: label="Colaboró David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2708'
ht-degree: 0%

---

# referencia de system.xml

El archivo `system.xml` le permite administrar la configuración del sistema de Commerce. Utilice este tema como referencia general para el archivo `system.xml`. El archivo `system.xml` se encuentra en `etc/adminhtml/system.xml`, en una extensión de Commerce 2 determinada.

El siguiente fragmento de código muestra el esqueleto vacío del archivo:

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
>Si desea una validación *XSD instantánea en su IDE, puede ejecutar `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Pestañas // Secciones // Grupos // Campos

En el archivo `system.xml`, es posible definir cuatro tipos diferentes de entidades, que están relacionadas entre sí. En la siguiente sección se describe la relación entre pestañas, secciones, grupos y campos. La siguiente captura de pantalla muestra la Configuración del sistema de Commerce 2 en el backend de administración.
Los cuadrados rojos marcan los diferentes tipos definidos en el archivo `system.xml`:

![Captura de pantalla que muestra una sección configurada en el administrador.](../../assets/configuration/magento2-system-configuration.png)

Las pestañas se utilizan para dividir semánticamente las diferentes áreas de configuración. Cada ficha puede contener una o más secciones, a las que también se puede hacer referencia como submenús. Una sección contiene uno o más grupos.
Cada grupo enumera uno o varios campos. También puede utilizar un grupo para agregar una descripción general para los siguientes campos. Como se ha mencionado, cada grupo puede tener uno o más campos. Los campos son la entidad más pequeña
en el contexto de configuración del sistema.

## Fichas

Una etiqueta `<tab>` hace referencia a una ficha existente o a una nueva en la configuración del sistema.

### Referencia de atributo de ficha

Una etiqueta `<tab>` puede tener los atributos siguientes:

| Atributo | Descripción | Tipo | Requerido |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Define el identificador que se utiliza para hacer referencia a la sección. | `typeId` | obligatorio |
| `translate` | Define el campo que debe traducirse. Proporcione `label` para que la etiqueta sea traducible. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos empujan la sección al final de la página; los números bajos empujan la sección al principio. | `float` | opcional |
| `class` | Agrega una clase CSS definida al elemento de HTML de pestañas procesado. | `string` | opcional |

### Referencia del nodo de pestañas

Una etiqueta `<tab>` puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|---------|------------------------------------------------------|----------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |

### Ejemplo: Creación de una pestaña

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

El fragmento anterior crea una nueva ficha con el identificador `A_UNIQUE_ID`. A medida que se define el atributo `translate` y hace referencia a la etiqueta, el nodo `label` se puede traducir. Durante el proceso de representación, la clase CSS `a-custom-css-class-to-style-this-tab` se aplicará en el elemento HTML creado para esta pestaña.
El atributo `sortOrder` con el valor `10` define la posición de la ficha en la lista de todas las fichas cuando se representa.

## Secciones

Una etiqueta `<section>` hace referencia a una sección existente o a una nueva en la configuración del sistema.

### Referencia de atributo de sección

Una etiqueta `<section>` puede tener los atributos siguientes:

| Atributo | Descripción | Tipo | Requerido |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define el identificador que se utiliza para hacer referencia a la sección. | `typeId` | obligatorio |
| `translate` | Define el campo que debe traducirse. Proporcione `label` para que la etiqueta sea traducible. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML representado. El valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos insertarán la sección en la parte inferior de la página; los números bajos insertarán la sección en la parte superior. | `float` | opcional |
| `showInDefault` | Define si la sección se muestra en el ámbito de configuración predeterminado. Especifique `1` para mostrar la sección y `0` para ocultar la sección. | `int` | opcional |
| `showInStore` | Define si la sección se muestra en el nivel de tienda. Especifique `1` para mostrar la sección y `0` para ocultar la sección. | `int` | opcional |
| `showInWebsite` | Define si la sección se muestra en el nivel de sitio web. Especifique `1` para mostrar la sección y `0` para ocultar la sección. | `int` | opcional |
| `canRestore` | Define si la sección se puede restaurar a los valores predeterminados. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Al proporcionar un identificador de otra sección, el contenido de este nodo amplía la sección a la que hace referencia. | `string` | opcional |

### Referencia del nodo de sección

Una etiqueta `<section>` puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |
| `class` | Agrega una clase CSS definida al elemento HTML de sección procesada. | `string` |
| `tab` | Hace referencia a la pestaña asociada. Espera el ID de la pestaña. | `typeTabId` |
| `header_css` | No se usaron ni evaluaron en el momento de escribir este artículo. | `string` |
| `resource` | Hace referencia a un recurso ACL para proporcionar la configuración de permisos para esta sección. | `typeAclResourceId` |
| `group` | Defina uno o varios subgrupos. | `typeGroup` |
| `frontend_model` | Especifica un modelo de front-end diferente para cambiar el procesamiento y modificar la salida. | `typeModel` |
| `include` | Se usa para incluir `system_include.xsd` archivos compatibles adicionales. Normalmente se usa para estructurar `system.xml` archivos grandes. | `includeType` |

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

La sección descrita anteriormente define el ID `A_UNIQUE_SECTION_ID`, que es visible en la vista de configuración predeterminada y en un contexto de tienda. El nodo `label` es traducible. La sección está asociada a la pestaña con el ID `A_UNIQUE_ID`. Solo pueden obtener acceso a la sección los usuarios que tengan los permisos definidos en la ACL `VENDOR_MODULE::path_to_the_acl_resource`.

## Grupos

La etiqueta `<group>` se usa para agrupar campos.

### Referencia de atributo de grupo

Una etiqueta `<group>` puede tener los atributos siguientes:

| Atributo | Descripción | Tipo | Requerido |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define el identificador que se utiliza para hacer referencia al grupo. | `typeId` | obligatorio |
| `translate` | Define los campos que deben traducirse. Proporcione `label` para que la etiqueta sea traducible. Los campos múltiples deben separarse con un espacio. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML representado. El valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos insertarán la sección en la parte inferior de la página; los números bajos insertarán la sección en la parte superior. | `float` | opcional |
| `showInDefault` | Define si el grupo se muestra en el ámbito de configuración predeterminado. Especifique `1` para mostrar el grupo y `0` para ocultarlo. | `int` | opcional |
| `showInStore` | Define si el grupo se muestra en el nivel de tienda. Especifique `1` para mostrar el grupo y `0` para ocultarlo. | `int` | opcional |
| `showInWebsite` | Define si el grupo se muestra en el nivel de sitio web. Especifique `1` para mostrar el grupo y `0` para ocultarlo. | `int` | opcional |
| `canRestore` | Define si el grupo se puede restaurar a los valores predeterminados. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Al proporcionar un identificador de otro grupo, el contenido de este nodo amplía la sección a la que hace referencia. | `string` | opcional |

### Referencia del nodo de grupo

Una etiqueta `<group>` puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |
| `fieldset_css` | Agrega una o más clases CSS a un conjunto de campos de grupo. | `string` |
| `frontend_model` | Especifica un modelo de front-end diferente para cambiar el procesamiento y modificar la salida. | `typeModel` |
| `clone_model` | Especifica un modelo determinado para clonar campos. | `typeModel` |
| `clone_fields` | Se ha habilitado o deshabilitado la clonación de campos. | `int` |
| `help_url` | No extensible. Consulte a continuación. | `typeUrl` |
| `more_url` | No extensible. Consulte a continuación. | `typeUrl` |
| `demo_link` | No extensible. Consulte a continuación. | `typeUrl` |
| `comment` | Agrega un comentario debajo de la etiqueta de grupo. Mediante el uso del HTML `<![CDATA[//]]>` se puede aplicar. | `string` |
| `hide_in_single_store_mode` | Si el grupo debe ser visible en el modo de tienda única. `1` oculta el grupo; `0` muestra el grupo. | `int` |
| `field` | Defina uno o varios campos que deben estar disponibles en este grupo. | `field` |
| `group` | Defina uno o varios subgrupos. | `unbounded` |
| `depends` | Se puede utilizar para declarar dependencias en otros campos. Se usa para mostrar campos/grupos específicos solamente cuando un campo dado tiene un valor de `1`. Este nodo espera una cadena de `section/group/field`. | `depends` |
| `attribute` | Los modelos de front-end pueden utilizar atributos personalizados. Normalmente se utiliza para hacer que un modelo de front-end determinado sea más dinámico. | `attribute` |
| `include` | Se usa para incluir `system_include.xsd` archivos compatibles adicionales. Normalmente se usa para estructurar `system.xml` archivos grandes. | `includeType` |

>[!WARNING]
>
>Los nodos `more_url`, `demo_url` y `help_url` se definen mediante un modelo de front-end de PayPal que solo se utiliza una vez. Estos nodos no se pueden reutilizar.

### Ejemplo: Creación de un grupo para una sección determinada

El siguiente fragmento de código muestra el uso básico de la creación de un nuevo grupo.

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

El grupo descrito anteriormente define el ID `A_UNIQUE_GROUP_ID`, que es visible en la vista de configuración predeterminada y en un contexto de tienda. Tanto `label` como `comment` se marcan como traducibles.

## Campos

La etiqueta `<field>` se usa dentro de etiquetas `<group>` para definir valores de configuración específicos.

### Referencia de atributo de campo

Una etiqueta `<field>` puede tener los atributos siguientes:

| Atributo | Descripción | Tipo | Requerido |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Define el identificador que se utiliza para hacer referencia al campo. | `typeId` | obligatorio |
| `translate` | Define los campos que deben traducirse. Proporcione `label` para que la etiqueta sea traducible. Los campos múltiples deben separarse con un espacio. | `string` | opcional |
| `type` | Define el tipo de entrada del elemento HTML representado. El valor predeterminado es `text`. | `string` | opcional |
| `sortOrder` | Define el orden de la sección. Los números altos empujan la sección al final de la página; los números bajos empujan la sección al principio. | `float` | opcional |
| `showInDefault` | Define si el campo se muestra en el ámbito de configuración predeterminado. Especifique `1` para mostrar el campo y `0` para ocultarlo. | `int` | opcional |
| `showInStore` | Define si el campo se muestra en el nivel de tienda. Especifique `1` para mostrar el campo y `0` para ocultarlo. | `int` | opcional |
| `showInWebsite` | Define si el campo se muestra en el nivel de sitio web. Especifique `1` para mostrar el campo y `0` para ocultarlo. | `int` | opcional |
| `canRestore` | Define si el campo se puede restaurar a los valores predeterminados. | `int` | opcional |
| `advanced` | Obsoleto desde 100.0.2. | `bool` | opcional |
| `extends` | Al proporcionar un identificador de otro campo, el contenido de este nodo amplía la sección a la que hace referencia. | `string` | opcional |

### Referencia de tipo de campo

Una etiqueta `<field>` puede tener los siguientes valores para el atributo `type=""`:

| Tipo | Descripción |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Campo de texto estándar de una sola fila |
| `textarea` | Bloque de texto |
| `select` | Menú desplegable normal; es posible que necesite un(a) `source_model` personalizado. También se usa para `Yes/No` selecciones. Vea `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` para ver un ejemplo. |
| `multiselect` | Como `select`, pero varias opciones son válidas. |
| `button` | Botón que almacena en déclencheur un evento inmediato. Requiere un modelo front-end personalizado para definir el texto del botón y la acción. Vea `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` para ver un ejemplo. |
| `obscure` | Campo de texto con el valor cifrado y mostrado como `**&#x200B;**`. Si se cambia el tipo con &quot;Inspect Element&quot; en el explorador, no se muestra el valor. |
| `password` | Como `obscure`, excepto que el valor oculto no está cifrado y si se cambia el tipo mediante &quot;Inspect Element&quot; en el explorador, se revelará el valor. |
| `file` | Permite cargar un archivo para su procesamiento. |
| `label` | Muestra una etiqueta en lugar de un campo editable. Utilice este tipo cuando un campo solo se pueda editar en ámbitos específicos; por ejemplo, en el nivel de vista de tienda. |
| `time` | Control para establecer la hora mediante tres menús desplegables: hora, minuto y segundo. |
| `allowspecific` | Una lista de selección múltiple de países específicos. Requiere un `source_model` como `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Permite cargar una imagen. |
| `note` | Permite añadir una nota informativa a la página. Este tipo requiere un `frontend_model` para procesar la nota. |

También es posible crear un tipo de campo personalizado. Esto suele hacerse cuando se requiere un botón especial, con una acción. Para ello, se requieren dos elementos principales:

- Creando un bloque en el área `adminhtml`
- Estableciendo `type=""` en la ruta de acceso a este bloque

El propio bloque requiere, como mínimo, un método `__construct` y un método `getElementHtml()`. El [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) es un ejemplo sencillo de un tipo personalizado.

Por ejemplo, en el módulo OfflineShipping, el botón Exportar se define en `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` y la definición del campo tiene el siguiente aspecto:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Referencia del nodo de campo

Una etiqueta `<field>` puede tener los siguientes elementos secundarios:

| Nodo | Descripción | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Define la etiqueta que se muestra en el front-end. | `string` |
| `comment` | Agrega un comentario debajo de la etiqueta de campo. Mediante el uso del HTML `<![CDATA[//]]>` se puede aplicar. | `string` |
| `tooltip` | Otro posible elemento de front-end que se puede utilizar para describir el significado de este campo. Se muestra como un pequeño icono junto al campo. | `string` |
| `hint` | Muestra información adicional. Solo disponible con `frontend_model` específico. | `string` |
| `frontend_class` | Agrega una clase CSS definida al elemento HTML de sección procesada. | `string` |
| `frontend_model` | Especifica un modelo de front-end diferente para cambiar el procesamiento y modificar la salida. | `typeModel` |
| `backend_model` | Especifica un modelo backend diferente para modificar los valores configurados. | `typeModel` |
| `source_model` | Especifica un modelo de origen diferente que proporciona un conjunto de valores específico. | `typeModel` |
| `config_path` | Se puede utilizar para sobrescribir la ruta de configuración genérica de un campo. | `typeConfigPath` |
| `validate` | Defina reglas de validación diferentes (separadas por espacios). A continuación, se muestra una lista de referencia completa de las reglas de validación disponibles. | `string` |
| `can_be_empty` | Se usa cuando `type` es `multiselect` para especificar que un campo puede estar vacío. | `int` |
| `if_module_enabled` | Se utiliza para mostrar un campo solo cuando un módulo determinado está habilitado. | `typeModule` |
| `base_url` | Se utiliza en combinación con `upload_dir` para cargas de archivos. | `typeUrl` |
| `upload_dir` | Especifique un directorio de destino para las cargas. Este nodo tiene atributos y nodos adicionales. Búsquelos antes de usar esto. | `typeUploadDir` |
| `button_url` | Muestra un botón si se especifican `button_url` y `button_label`. Normalmente se utiliza en combinación con un modelo de front-end personalizado. | `typeUrl` |
| `button_label` | Muestra un botón si se especifican `button_label` y `button_url`. Normalmente se utiliza en combinación con un modelo de front-end personalizado. | `string` |
| `more_url` | No extensible. Consulte a continuación. | `typeUrl` |
| `demo_url` | No extensible. Consulte a continuación. | `typeUrl` |
| `hide_in_single_store_mode` | Si el grupo debe ser visible en el modo de tienda única. `1` oculta el grupo; `0` muestra el grupo. | `int` |
| `options` | No se usa. Potencialmente obsoleto. | `complexType` |
| `depends` | Se puede utilizar para declarar dependencias en otros campos. Se usa para mostrar únicamente campos/grupos específicos cuando un campo determinado tiene un valor de `1`. Este nodo espera una cadena de `section/group/field`. | `complexType` |
| `attribute` | Los modelos de front-end pueden utilizar atributos personalizados. Normalmente se utiliza para hacer que un modelo de front-end determinado sea más dinámico. | `complexType` |
| `requires` | No extensible. Consulte a continuación. | `complexType` |

>[!WARNING]
>
>Los nodos `more_url`, `demo_url`, `requires` y `options` se definen mediante un modelo de pago principal diferente y solo se utilizan una vez. Estos nodos no se pueden reutilizar.

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

El ejemplo anterior crea dos campos, visibles/configurables en la vista predeterminada y en la vista de tienda. Ambos campos tienen un comentario y una información del objeto para describir su propósito al usuario. El nodo `label` es traducible.
El campo con el identificador `ANOTHER_UNIQUE_FIELD_ID` es visible cuando el módulo dado en `if_module_enabled` está habilitado globalmente. El campo también valida su valor con las reglas `required-entry` y `no-whitespace`.
El campo con el identificador `A_UNIQUE_FIELD_ID` define un modelo de origen diferente que proporciona esos valores `Yes` y `No`.

### Modelos de origen comunes

Commerce 2 Core proporciona los siguientes modelos de origen. En general, hay muchos más modelos de origen; la siguiente lista describe los más comunes. Tenga en cuenta que estos modelos de origen necesitan que el atributo de campo `type` se establezca en `select` para que funcione correctamente.

| Modelo Source | Descripción |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Proporciona los valores `Yes`, `No` y `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Proporciona los valores `Enable`, `Disable`. Guarda los valores como `0` y `1` en la base de datos. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Proporciona los valores `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` y `24 Hours`. Los valores se guardan como números enteros. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Proporciona los valores del formato de hora (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Proporciona los valores `Daily`, `Weekly` y `Monthly`. Los valores se guardan en la base de datos como `D`, `W` y `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Proporciona los valores de un código de 2 letras de un idioma determinado en formato ISO 639-1 (por ejemplo, en). |
| `Magento\Config\Model\Config\Source\Locale` | Proporciona los valores similares al anterior, pero pertenece a un código de configuración regional (por ejemplo, en_US). |

### Validación de campos

Un campo puede tener una o más clases de validador asignadas para asegurarse de que la entrada del usuario cumple los requisitos de la extensión. Las reglas de validación se pueden aplicar con la etiqueta `<validate>`.
En el siguiente ejemplo se valida un campo y se agregan distintas reglas de validación.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Están disponibles las siguientes reglas de validación:

| Regla | Descripción |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Solo permite letras, números, espacios o guiones bajos. |
| `integer` | Permite un número no decimal positivo o negativo. |
| `ipv4` | Permite una dirección IP v4 válida. |
| `ipv6` | Permite una dirección IP v6 válida. |
| `letters-only` | Solo permite cartas. Por ejemplo, `abcABC`. |
| `letters-with-basic-punc` | Solo permite letras o puntuación.<br>Debe pasar la siguiente expresión: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Permite un número de teléfono móvil (Reino Unido). |
| `no-marginal-whitespace` | No permite espacios en blanco al principio o al final del valor. |
| `no-whitespace` | No admite espacios en blanco. |
| `phoneUK` | Permite un número de teléfono (RU). |
| `phoneUS` | Permite un número de teléfono (EE.UU.). |
| `required-entry` | No permite un valor vacío (validación equivalente a `validate-no-empty`).<br>Mensaje de error de validación: &quot;Este campo es obligatorio&quot;. |
| `time` | Permite una hora válida en formato de 24 horas, entre 00:00 y 23:59. Por ejemplo `15`, `15:05` o `15:05:48`. |
| `time12h` | Permite una hora válida en formato de 12 horas, entre las 12:00 y las 11:59:59 p.m. Por ejemplo `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Permite 7 o más caracteres, tanto numéricos como alfabéticos. |
| `validate-alphanum-with-spaces` | Solo permite el uso de letras (a-z o A-Z), números (0-9) o espacios. |
| `validate-clean-url` | Permite una dirección URL válida. Por ejemplo, `https://www.example.com` o `www.example.com`. |
| `validate-currency-dollar` | Permite una cantidad válida (en dólares). Por ejemplo, 100,00 $. |
| `validate-data` | Solo permite el uso de letras (a-z o A-Z), números (0-9) o guiones bajos (\_).<br>El primer carácter debe ser una letra.<br>(Debe coincidir con la expresión: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Mensaje de error de validación: &quot;Use solo letras (a-z o A-Z), números (0-9) o guiones bajos (\_) en este campo, y el primer carácter debe ser una letra&quot;. |
| `validate-date-au` | Aplica el siguiente formato de fecha: dd/mm/aaaa. Por ejemplo, 17/03/2006 para el 17 de marzo de 2006. |
| `validate-email` | Permite una dirección de correo electrónico válida. Por ejemplo, johndoe@domain.com. |
| `validate-emailSender` | Permite una dirección de correo electrónico válida. Por ejemplo, johndoe@domain.com. |
| `validate-fax` | Permite un número de fax válido. Por ejemplo, 123-456-7890. |
| `validate-no-empty` | No permite un valor vacío (validación equivalente a `requried-entry`).<br>Mensaje de error de validación: &quot;Valor vacío&quot;. |
| `validate-no-html-tags` | No permite el uso de etiquetas de HTML. |
| `validate-password` | Permite 6 caracteres o más. Los espacios iniciales y finales se omitirán. |
| `validate-phoneLax` | Permite un número de teléfono válido. Por ejemplo, (123) 456-7890 o 123-456-7890. |
| `validate-phoneStrict` | Permite un número de teléfono válido. Por ejemplo, (123) 456-7890 o 123-456-7890. |
| `validate-select` | Exige que la opción seleccionada no tenga un valor `null`, un valor de cadena de `none` o una longitud de cadena de 0. |
| `validate-ssn` | Permite un número de la seguridad social válido (EE.UU.). Por ejemplo, 123-45-6789. |
| `validate-street` | Permite el uso de letras (a-z o A-Z), números (0-9), espacios y &quot;#&quot; únicamente. |
| `validate-url` | Permite una dirección URL válida. Se requiere el protocolo (http://, https:// o ftp://). |
| `validate-xml-identifier` | Permite un identificador XML válido. Por ejemplo, algo_1, bloque5, id-4. |
| `validate-zip-us` | Permite un código postal válido (EE.UU.). Por ejemplo, 90602 o 90602-1234. |
| `vinUS` | Permite el valor (US) del número de identificación del vehículo (VIN). |

### Valores predeterminados

Los valores predeterminados para los campos se pueden establecer en el archivo `etc/config.xml` del módulo especificando el valor predeterminado en el nodo `section/group/field_ID`.

#### Ejemplo: Configuración del valor predeterminado para `ANOTHER_UNIQUE_FIELD_ID` (ámbito predeterminado)

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

#### Ejemplo: Configuración del valor predeterminado para `ANOTHER_UNIQUE_FIELD_ID` (ámbito del sitio web)

Con la etiqueta `websites`, especifique el valor predeterminado para un sitio web específico.

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
