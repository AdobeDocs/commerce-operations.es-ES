---
title: '[!DNL Upgrade Compatibility Tool] mensajes de error'
description: Obtenga más información acerca de los mensajes de error que aparecen al usar  [!DNL Upgrade Compatibility Tool]  en su proyecto de Adobe Commerce.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] mensajes de error

{{commerce-only}}

Esta referencia de mensaje de error proporciona información sobre los errores que pueden producirse al ejecutar [!DNL Upgrade Compatibility Tool].

Los mensajes de error se clasifican por nivel (problemas críticos, errores y advertencias) y tipo (código principal, código personalizado y esquemas de GraphQL). Cada tipo contiene la siguiente información:

- **Código de error**: el identificador asignado por Adobe Commerce para el mensaje de error.
- **Descripción del error**: Una descripción que resume la causa del error.
- **Error al sugerir la acción**: si procede, proporciona instrucciones para solucionar y resolver el error.

## Problemas críticos

### Código principal

Estos errores se registran cuando faltan algunos de los archivos principales o no coinciden con el original.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 2001 | No se ha encontrado el archivo principal | Ejecute el comando `composer install` desde el directorio raíz del proyecto. |
| 2002 | Se modificó el archivo principal | Ejecute el comando `composer install` desde el directorio raíz del proyecto. |
| 2003 | La dependencia del compositor no está instalada | La falta de dependencia del compositor puede provocar problemas. Restaurar dependencia ejecutando `composer require package_name`. |
| 2005 | No se ha encontrado la carpeta principal | Ejecute el comando `composer install` desde el directorio raíz del proyecto. |

{style="table-layout:auto"}

### Custom Code

Se generan errores críticos cuando el código personalizado hace referencia a entidades que no están presentes en la versión de Adobe Commerce de destino. Estos errores también se registran cuando se han incumplido los estándares de codificación esenciales.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 1110 | Creación de una instancia de clase/interfaz de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. Crear una instancia de una clase o interfaz de Adobe Commerce inexistente. |
| 1111 | Ampliación desde una clase Adobe Commerce inexistente | La clase extendida ya no está presente en el código base. No se recomienda la herencia para ampliar la funcionalidad de Adobe Commerce. Actualice el código para utilizar una clase marcada como `@api`. |
| 1112 | Importación de una clase de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. |
| 1113 | Cargando clase de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. |
| 1114 | Uso de una clase de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. |
| 1214 | Uso de constantes de Adobe Commerce inexistentes | Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1215 | Anular una constante Adobe Commerce inexistente | Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1216 | Asignación de una constante Adobe Commerce inexistente | Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1312 | Interfaz de Adobe Commerce inexistente importada | Considere la posibilidad de eliminar la herencia o reemplazarla por la interfaz introducida en el ámbito de la personalización. |
| 1314 | Interfaz de Adobe Commerce utilizada inexistente | Considere la posibilidad de eliminar la herencia o reemplazarla por la interfaz introducida en el ámbito de la personalización. |
| 1317 | Interfaz heredada de Adobe Commerce inexistente | Considere la posibilidad de eliminar la herencia o reemplazarla por la interfaz introducida en el ámbito de la personalización. |
| 1318 | Se ha implementado una interfaz de Adobe Commerce inexistente | Considere la posibilidad de eliminar la herencia o reemplazarla por la interfaz introducida en el ámbito de la personalización. |
| 1410 | Llamar a un método de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. |
| 1514 | Uso de una propiedad de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. |
| 1515 | Omisión de una propiedad de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. |
| 1516 | Asignación de una propiedad de Adobe Commerce inexistente | Actualice el código para utilizar una clase marcada como `@api`. Actualice el nivel de acceso de la propiedad a private si solo se puede utilizar dentro de una sola clase. |
| 5002 | La etiqueta PHP de apertura debe ser el primer contenido del archivo | Asegúrese de que no haya contenido en el archivo antes de la etiqueta de apertura PHP. |
| 5003 | La función ha quedado obsoleta | Utilice un reemplazo sugerido en el mensaje de error. Si el mensaje no sugiere un reemplazo, se necesita una revisión minuciosa para seleccionar una función o implementación alternativa. |
| 5005 | Error de sintaxis de PHP | El código debe ser actualizado para cumplir con los estándares de sintaxis PHP. |
| 5072 | Posible infracción de diseño de Magento 2. Se ha detectado una construcción típica de Magento 1.x | Actualice la construcción a las normas Magento 2. |
| 5076 | No se puede usar en el espacio de nombres porque está reservado desde PHP 7 | Reemplace la palabra reservada en el espacio de nombres por una palabra clave no reservada. |
| 5077 | No se puede usar como nombre de clase porque está reservado desde PHP 7 | Reemplace el nombre de clase reservado por un nombre no reservado. |

{style="table-layout:auto"}

### Esquema de BD

Se informa de los problemas críticos del esquema de base de datos si las restricciones personalizadas hacen referencia a las tablas o columnas principales eliminadas.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 7009 | La restricción personalizada hace referencia a una tabla principal que se ha eliminado en la versión de destino | Quitar los atributos constraint o update referenceTable y referenceColumn |
| 7010 | La restricción personalizada hace referencia a una columna principal que se ha eliminado en la versión de destino | Elimine la restricción o actualice el atributo referenceColumn |

{style="table-layout:auto"}

### Esquema de GraphQL

Se generan problemas críticos del esquema de GraphQL si los elementos de esquema no están presentes en la versión de destino.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 3101 | Se ha eliminado el tipo | Enumerar todas las consultas que hacen referencia a este campo. Compruebe si la implementación de personalización utiliza estas consultas. Actualice el código de cliente para gestionar la interfaz de consultas modificada. |
| 3102 | Tipo eliminado de la unión | Si se utiliza el tipo de unión en la construcción de solicitudes de GraphQL o en la implementación del procesamiento de respuestas, es posible que se tenga que actualizar. |
| 3103 | Campo eliminado | Compruebe si se hace referencia al campo en la base de código de personalización. Ajuste la implementación para gestionar correctamente el nuevo tipo de campo. |
| 3105 | Interfaz implementada eliminada | Compruebe si el tipo que implementa la interfaz eliminada se utiliza en la personalización. Es posible que sea necesario actualizar la implementación si depende de la interfaz eliminada. |
| 3106 | Valor eliminado de la enumeración | Si el valor de enumeración eliminado se utiliza en la construcción de solicitudes de GraphQL o en la implementación del procesamiento de respuestas, es posible que deba actualizarse. |
| 3107 | Argumento eliminado | Compruebe si el campo se utiliza en la base de código de personalización. Elimine el argumento de este campo. |
| 3109 | Directiva eliminada | Compruebe si la directiva se utiliza en el código base de personalización. Ajuste la implementación para eliminar la referencia a la directiva. |
| 3110 | Argumento de directiva eliminado | Compruebe si la directiva se utiliza en el código base de personalización. Elimine el argumento de la directiva. |
| 3111 | Directiva eliminada repetible | Compruebe si la directiva se utiliza en el código base de personalización. Ajuste la implementación para gestionar los cambios de la interfaz. |
| 3112 | Ubicación de directiva eliminada | Compruebe si la directiva se utiliza en el código base de personalización. Ajuste la implementación para gestionar los cambios de la interfaz. |
| 3201 | Tipo cambiado tipo | Enumerar todas las consultas que hacen referencia a este campo. Compruebe si la implementación de personalización utiliza estas consultas. Actualice el código de cliente para gestionar la interfaz de consultas modificada. |
| 3203 | Tipo de campo cambiado | Compruebe si se hace referencia al campo en la base de código de personalización. Ajuste la implementación para gestionar correctamente el nuevo tipo de campo. |
| 3207 | Tipo de argumento cambiado | Compruebe si el campo se utiliza en la base de código de personalización. Actualice el tipo de argumento para este campo. |
| 3303 | Se agregó un campo de entrada obligatorio | El campo debe añadirse a la solicitud si la consulta que incluye este campo se utiliza para la personalización. |
| 3307 | Se agregó un argumento requerido | Compruebe si el campo se utiliza en la base de código de personalización. El nuevo argumento requerido debe especificarse al utilizar el campo. |
| 3310 | Se agregó un argumento de directiva requerido | Compruebe si la directiva se utiliza en el código base de personalización. Agregue el argumento directiva. |

{style="table-layout:auto"}

## Errores

### Custom Code

Se generan errores de código personalizado cuando el código personalizado utiliza puntos de entrada de Adobe Commerce que no se consideran o marcan como `@api`. No se garantiza el comportamiento conservado de estos puntos de entrada. La personalización debería depender de `@api` puntos de entrada en su lugar. La funcionalidad basada en código Adobe Commerce no API debe probarse después de la actualización. Estos errores también se notifican cuando se han roto los principales estándares de codificación.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 1104 | Utilizar una clase que no es de API y que hereda la interfaz de API de | Las clases que no están marcadas como `@api` se pueden cambiar. Considere la posibilidad de actualizar el código para que dependa de la interfaz marcada como `@api`. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1121 | Ampliación desde una clase de API que no es Adobe Commerce | La clase extendida ya no está presente en el código base. No se recomienda la herencia para ampliar la funcionalidad de Adobe Commerce. Actualice el código para utilizar una clase marcada como `@api`. |
| 1122 | Importación de clases de API que no son de Adobe Commerce | La clase extendida ya no está presente en el código base. Actualice el código para utilizar una clase marcada como `@api`. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1123 | Carga de una clase de API que no es Adobe Commerce | La clase extendida ya no está presente en el código base. Actualice el código para utilizar una clase marcada como `@api`. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1124 | Uso de clases de API que no son de Adobe Commerce | La clase extendida ya no está presente en el código base. Actualice el código para utilizar una clase marcada como `@api`. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1224 | Uso de constantes de API que no son de Adobe Commerce | Las constantes que no están marcadas como `@api` pueden cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1225 | Anulación de una constante de API que no es Adobe Commerce | Las constantes que no están marcadas como `@api` pueden cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1226 | Asignación de una constante de API que no sea de Adobe Commerce | Las constantes que no están marcadas como `@api` pueden cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1322 | Interfaz de API importada que no es de Adobe Commerce | Las interfaces no marcadas como `@api` se pueden cambiar. Considere la posibilidad de quitar esta herencia o reemplazarla por la herencia de la interfaz de Adobe Commerce marcada como `@api` o una interfaz incluida en el ámbito del código de personalización. |
| 1324 | Interfaz de API no utilizada de Adobe Commerce | Las interfaces no marcadas como `@api` se pueden cambiar. Considere la posibilidad de quitar esta herencia o reemplazarla por la herencia de la interfaz de Adobe Commerce marcada como `@api` o una interfaz incluida en el ámbito del código de personalización. |
| 1327 | Interfaz de API heredada que no es de Adobe Commerce | Las constantes que no están marcadas como `@api` pueden cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado en su lugar. |
| 1328 | Interfaz de API no implementada en Adobe Commerce | Las interfaces no marcadas como `@api` se pueden cambiar. Considere la posibilidad de quitar esta herencia o reemplazarla por la herencia de la interfaz de Adobe Commerce marcada como `@api` o una interfaz incluida en el ámbito del código de personalización. |
| 1420 | Creación de una instancia de clase/interfaz de API que no sea Adobe Commerce | Las clases que no están marcadas como `@api` se pueden cambiar. Considere la posibilidad de actualizar el código para que dependa de la interfaz marcada como `@api`. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. Además, la forma recomendada de recuperar una instancia de la clase es utilizar ID. Considere la posibilidad de utilizar una fábrica si es necesaria una nueva instancia de la clase. |
| 1428 | Posible dependencia de los detalles de implementación. | Las clases que no están marcadas como `@api` se pueden cambiar. Considere la posibilidad de actualizar el código para que dependa de la interfaz marcada como `@api`. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1429 | Llamar a métodos de API que no son de Adobe Commerce | Los métodos que no están marcados como `@api` o que no están declarados dentro de la clase/interfaz de API se pueden cambiar. Incluso si la interfaz del método no se actualiza en la nueva versión, su comportamiento o resultado puede ser diferente. Considere confiar en un método de interfaz. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1449 | Llamada a un método que no es de interfaz (presente en la implementación) | Los métodos que no se declaran en la interfaz se pueden cambiar. Considere confiar en un método de interfaz. De lo contrario, la funcionalidad que depende de esta implementación debe probarse después de la actualización. |
| 1524 | Uso de una propiedad de API que no es Adobe Commerce | Los valores de las propiedades que no están marcadas como `@api` se pueden cambiar. Considere utilizar el método de interfaz de API en su lugar. |
| 1525 | Anulación de una propiedad de API que no es Adobe Commerce | Los valores de las propiedades que no están marcadas como `@api` se pueden cambiar. Considere utilizar el método de interfaz de API en su lugar. |
| 1526 | Asignación de una propiedad de API que no es de Adobe Commerce | Los valores de las propiedades que no están marcadas como `@api` se pueden cambiar. Considere utilizar el método de interfaz de API en su lugar. |
| 5004 | La función sin argumento ha quedado obsoleta | Pase la entrada para validar como el primer argumento de la función. |
| 5007 | Se desaconseja el uso de ciertas funciones | Evite utilizar estas funciones. |
| 5009 | Las directivas de plantilla no pueden invocar métodos. Solo se permite el acceso a la matriz escalar | Elimine las invocaciones de método de la plantilla. |
| 5010 | El bloque de comentarios de la plantilla `@vars` contiene un JSON no válido | Se ha corregido un JSON no válido. |
| 5011 | El bloque de comentarios de la plantilla `@vars` contiene una etiqueta no válida | Se ha corregido una etiqueta no válida. |
| 5012 | Al bloque de comentarios de la plantilla `@vars` le falta una variable utilizada en la plantilla | Añada la variable que falta @vars bloque de comentarios. |
| 5013 | Evite utilizar etiquetas de cierre automático con elementos html no nulos | En su lugar, utilice una etiqueta de cierre. |
| 5014 | El atributo `"active"` está obsoleto | La lista de módulos activos se define en la configuración de implementación. |
| 5015 | El nodo `<param>` está obsoleto | Utilice `<argument name="..." xsi:type="...">` en su lugar. |
| 5016 | El nodo `<instance>` está obsoleto | Utilice `<argument name="..." xsi:type="object">` en su lugar. |
| 5017 | El nodo `<array>` está obsoleto | Utilice `<argument name="..." xsi:type="array">` en su lugar. |
| 5018 | El nodo `<item key="...">` está obsoleto | Utilice `<item name="..." xsi:type="...">` en su lugar. |
| 5019 | El nodo `<value>` está obsoleto | En su lugar, proporcione el valor real como un literal de texto. |
| 5020 | Nodo obsoleto: `<supported_blocks>` | Se reemplazará con `<supported_containers>`. |
| 5021 | Nodo obsoleto: `<block_name>` | Se reemplazará con `<container_name>`. |
| 5022 | Nombre de fábrica detectado | El tipo de widget no debe comenzar por /. |
| 5023 | Se detectó una estructura ACL obsoleta en la línea | Consulte lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Estructura de menú obsoleta detectada en la línea | Consulte app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Estructura de configuración del sistema obsoleta detectada en el archivo | Consulte app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | No use el atributo de tipo `"text/javascript"` | Usar sólo miembros públicos. |
| 5028 | El acceso a los miembros protegidos y privados de la clase `Block` está obsoleto en las plantillas phtml | Usar sólo miembros públicos. |
| 5031 | Contiene un método obsoleto | En su lugar, utilice el método `getConnection()`. |
| 5042 | Formato incorrecto de referencia de clase PHP | Compruebe que se hace referencia a esta clase utilizando solo letras en minúscula, números y sin barra diagonal. |
| 5043 | Formato incorrecto de referencia de módulo | Compruebe que solo se hace referencia al módulo mediante letras, números, guiones bajos y sin barra diagonal. |
| 5044 | La clase `Zend_Db_Select` está restringida | Reemplazo sugerido: `\Magento\Framework\DB\Select`. |
| 5045 | La clase `Zend_Db_Adapter_Pdo_Mysql` está restringida | Reemplazo sugerido: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | La clase `Magento\Framework\Serialize\Serializer\Serialize` está restringida | Reemplazo sugerido: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | La clase `ArrayObject` está restringida | Reemplazo sugerido: Clase personalizada, extendida desde `ArrayObject` con métodos serialize/unserialize sobrescritos. |
| 5048 | La clase `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` está restringida | Reemplazo sugerido: Fábrica que crea la clase personalizada, extendida desde `ArrayObject` con métodos serialize/unserialize sobrescritos. |
| 5050 | Se elimina el bloque al que se hace referencia | Quitar referencia al bloque. |
| 5051 | `output="toHtml"` está obsoleto | Usar `output="1"`. |
| 5052 | Se supone que la clase `\Magento\Framework\View\Element\Text\ListText` ya no se debe usar en el diseño | Quitar la clase `\Magento\Framework\View\Element\Text\ListText` del diseño. |
| 5053 | No se permite la llamada al método mediante la instrucción de diseño `<action>` | Evite utilizar un método ofensivo en `<action>`. |
| 5054 | `helper` atributo contiene `/` | Quitar a `/` del atributo de ayuda. |
| 5055 | El atributo `helper` no contiene `::` | Agregar `::` al atributo de ayuda. |
| 5056 | Los scripts de instalación están obsoletos | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml de module\. |
| 5057 | Los scripts InstallSchema están obsoletos | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml de module\. |
| 5058 | Los scripts InstallData están obsoletos | Utilice el método de parches de datos en el directorio Setup/Patch/Data del módulo. |
| 5059 | Los scripts de instalación están obsoletos | Cree una clase InstallData en la carpeta Setup del módulo. |
| 5060 | Los scripts de actualización están obsoletos | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml de module\. |
| 5061 | Los scripts UpgradeSchema están obsoletos | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml de module\. |
| 5062 | Los scripts UpgradeData están obsoletos | Utilice el método de parches de datos en el directorio Setup/Patch/Data del módulo. |
| 5063 | Los scripts de actualización están obsoletos | Utilice el método de parches de datos en el directorio Setup/Patch/Data del módulo. |
| 5064 | Los scripts recurrentes están obsoletos | Cree la clase Recurring en la carpeta Setup del módulo. |
| 5065 | &#39;data&#39; está en un directorio no válido | Cree un parche de datos en la carpeta Setup/Patch/Data del módulo para actualizar los datos o utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo para realizar cambios en el esquema. |
| 5066 | &#39;sql&#39; está en un directorio no válido | Cree un parche de datos en la carpeta Setup/Patch/Data del módulo para actualizar los datos o utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo para realizar cambios en el esquema. |
| 5067 | Los nodos identificados por XPath están obsoletos | El XML obsoleto señalado en el error debe actualizarse. Siga las sugerencias del mensaje de error. |
| 5068 | La directiva `{{htmlescape}}` está obsoleta | Utilice `{{var}}` en su lugar. |
| 5069 | La directiva `{{escapehtml}}` está obsoleta | Utilice `{{var}}` en su lugar. |
| 5070 | El tercer parámetro ya no es necesario para `getChildHtml()` | Quitar el tercer parámetro de la llamada a `getChildHtml()`. |
| 5071 | El cuarto parámetro ya no es necesario para `getChildHtml()` | Quitar el cuarto parámetro de la llamada a `getChildHtml()`. |
| 5073 | Los nombres de tablas heredadas con barra diagonal deben corregirse para dirigir los nombres de tablas | En su lugar, utilice un nombre de tabla directo. |
| 5075 | Los módulos de aplicación no deben utilizar clases de módulos de prueba | Quite el uso de clases de los módulos de prueba. |
| 5078 | La clase debe solicitarse en el constructor; de lo contrario, el compilador no podrá encontrar y generar estas clases | Agregue la clase al constructor. |
| 5079 | Se desaconseja el uso de variables de clase var | Evite utilizar &#39;var&#39; para declarar una variable de clase. |
| 5080 | Posible instrucción SQL sin procesar detectada | En su lugar, utilice repositorios o parches de datos. |
| 5081 | Se desaconseja el uso de ayudantes en las plantillas | En su lugar, utilice ViewModel. |
| 5082 | El uso de $this en plantillas está obsoleto | En su lugar, utilice $block. |
| 5083 | No se permiten constantes como el primer argumento de la función de traducción | En su lugar, utilice un literal de cadena. |
| 5085 | Se desaconseja el uso de ciertas funciones | En su lugar, utilice la función alternativa que se indica en el mensaje. |
| 5087 | Problema de compatibilidad entre versiones de PHP | Siga las sugerencias del mensaje y consulte la [guía de migración](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parámetros opcionales encontrados después de los necesarios | Mueva los parámetros necesarios después de los opcionales. |
| 5089 | Se encontró la visibilidad del método `final private` | Cambie la visibilidad del método de `final private` a solo `private`. |
| 5090 | El método mágico `__set_state` no está definido como `static` | El método mágico `__set_state` debe definirse como `static`. |
| 5091 | La clase con el método `__toString()` no se hereda de la interfaz `Stringable` | Agregar la interfaz `Stringable` a la clase con el método `__toString()`. |
| 5092 | Método `is_resource()` utilizado para funciones que ahora devuelven Object | Cambiar `is_resource()` a objeto `instanceof`. |
| 6001 | `jQuery.andSelf()` eliminado | Usar `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` y `$.unbind` están obsoletos | En su lugar, use `$.on` y `$.off`. |
| 6003 | El método jQuery para suscribirse al evento está obsoleto y no debe usarse | En su lugar, utilice el método `.on("event name", fn)` para suscribirse a ese evento. |
| 6003 | El método jQuery para el evento de déclencheur está obsoleto y no debe usarse | En su lugar, utilice el método `.trigger("event name")` para almacenar en déclencheur ese evento. |
| 6004 | jQuery `$.delegate` y `$.undelegate` están obsoletos | En su lugar, use `$.on` y `$.off`. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) se eliminó | Use (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`) en su lugar. |
| 6006 | `jQuery.size()` eliminado | Usar `jQuery.length`. |
| 6007 | `jQuery.trim` está obsoleto | Usar `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, tema &#39;inlite&#39;, tema &#39;mobile&#39;, tema &#39;modern&#39;) se ha eliminado | Actualice el código para que sea compatible con tinymce5. |
| 6009 | `jQuery.isFunction()` está obsoleto | En la mayoría de los casos, se puede reemplazar por [type de x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` está obsoleto | Reemplazar por una comprobación de tipo adecuada como [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` está obsoleto | En su lugar, utilice el método nativo Array.isArray. |
| 6009 | `jQuery.parseJSON()` está obsoleto | Para analizar cadenas JSON, utilice el método nativo JSON.parse en su lugar. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) está obsoleto | En su lugar, utilice jQuery.expr.pseudos. |

{style="table-layout:auto"}

### Esquema de BD

Se generan errores de esquema de base de datos si las tablas, columnas, índices o restricciones de la base de datos, agregados o eliminados en la versión de Adobe Commerce de destino, pueden provocar conflictos con el esquema de base de datos personalizado.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 7001 | La versión principal de destino introduce una tabla con el mismo nombre que una tabla declarada por un módulo personalizado | Utilice la nueva tabla principal (si procede) o cambie el nombre de la tabla personalizada |
| 7002 | La tabla principal ampliada mediante un módulo personalizado se ha eliminado de la versión de destino | Todas las referencias de tabla principal eliminadas deben eliminarse de la base de código |
| 7003 | La versión principal de destino introduce una columna con el mismo nombre que una columna declarada por un módulo personalizado | Utilice la nueva columna principal (si procede) o cambie el nombre de la columna personalizada |
| 7004 | La columna principal ampliada mediante un módulo personalizado se ha eliminado de la versión de destino | Todas las referencias de columnas principales eliminadas deben eliminarse de la base de código |
| 7005 | La versión principal de destino introduce un índice con el mismo referenceId que un índice declarado por un módulo personalizado | Elimine (si está duplicado en el índice principal introducido) o cambie el nombre del índice personalizado |
| 7006 | El índice principal ampliado por un módulo personalizado se ha eliminado de la versión de destino | Todas las referencias de índice principal eliminadas deben eliminarse de la base de código |
| 7007 | La versión principal de destino introduce una restricción con el mismo nombre que una restricción declarada por un módulo personalizado | Quitar (si está duplicada con la restricción principal introducida) o cambiar el nombre de la restricción personalizada |
| 7008 | La restricción principal extendida por un módulo personalizado se ha eliminado en la versión de destino | Utilice la nueva restricción principal (si procede) o cambie el nombre de la restricción personalizada |

{style="table-layout:auto"}

## Advertencias

### Código principal

Estas advertencias se registran cuando hay incoherencias menores en la base de código principal.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 2004 | Versión de dependencia del compositor no coincidente | Este problema indica que la versión de dependencia del Compositor en el proyecto de Tealon y en el proyecto real es diferente. Actualice la dependencia ejecutando `composer update <package_name>`. |

{style="table-layout:auto"}

### Custom Code

Se generan advertencias de código personalizado cuando se detectan las referencias a código obsoleto. Estas referencias deben sustituirse por los puntos de extensión admitidos. Preste atención a la anotación `@see` del elemento obsoleto para recomendaciones. Estos errores también se notifican cuando se han roto estándares de codificación menores.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 1131 | Ampliando desde la clase ``@deprecated`` de Adobe Commerce | La clase extendida se eliminará en las próximas versiones. No se recomienda la herencia para ampliar la funcionalidad de Adobe Commerce. Actualice el código para utilizar una clase marcada como `@api`. |
| 1132 | Importando clase de Adobe Commerce `@deprecated` | La clase extendida se eliminará en las próximas versiones. Considere utilizar la clase Adobe Commerce marcada como `@api` en su lugar. |
| 1133 | Cargando clase `@deprecated` de Adobe Commerce | La clase extendida se eliminará en las próximas versiones. Considere utilizar la clase Adobe Commerce marcada como `@api` en su lugar. |
| 1134 | Usando la clase `@deprecated` de Adobe Commerce | La clase extendida se eliminará en las próximas versiones. Considere utilizar la clase Adobe Commerce marcada como `@api` en su lugar. |
| 1234 | Usando la constante `@deprecated` de Adobe Commerce | La constante obsoleta se eliminará en las próximas versiones. Considere utilizar una constante marcada como `@api` o una constante privada en su implementación. |
| 1235 | Anulando constante de Adobe Commerce `@deprecated` | La constante obsoleta se eliminará en las próximas versiones. Considere utilizar una constante marcada como `@api` o una constante privada en su implementación. |
| 1236 | Asignación de la constante `@deprecated` de Adobe Commerce | La constante obsoleta se eliminará en las próximas versiones. Considere utilizar una constante marcada como `@api` o una constante privada en su implementación. |
| 1332 | Interfaz de Adobe Commerce `@deprecated` importada | La interfaz obsoleta se eliminará en las próximas versiones. Considere utilizar una interfaz o clase marcada como `@api` en su lugar. |
| 1334 | Interfaz de Adobe Commerce `@deprecated` usada | La interfaz obsoleta se eliminará en las próximas versiones. Considere utilizar una interfaz o clase marcada como `@api` en su lugar. |
| 1337 | Heredado de la interfaz de Adobe Commerce `@deprecated` | La interfaz obsoleta se eliminará en las próximas versiones. Considere la posibilidad de eliminar la herencia de la interfaz, utilizando una interfaz marcada como `@api` o una interfaz introducida en su implementación en su lugar. |
| 1338 | Se implementó la interfaz de Adobe Commerce `@deprecated` | La interfaz obsoleta se eliminará en las próximas versiones. Considere la posibilidad de eliminar la herencia de la interfaz, utilizando una interfaz marcada como `@api` o una interfaz introducida en su implementación en su lugar. |
| 1430 | Llamada a método dataobject no declarado | Los métodos mágicos que no se declaran pueden cambiarse. Considere la posibilidad de confiar en los métodos de interfaz en su lugar. |
| 1439 | Llamar al método de Adobe Commerce `@deprecated` | El método obsoleto se eliminará en las próximas versiones. Considere la posibilidad de confiar en los métodos declarados en las interfaces de API en su lugar. |
| 1440 | No coinciden las firmas de método | Se detecta una llamada o anulación del método principal con parámetros, argumentos o tipo de valor devuelto que no coincide con la firma del método. |
| 1534 | Usando la propiedad de Adobe Commerce `@deprecated` | El método obsoleto se eliminará en las próximas versiones. Considere la posibilidad de confiar en los métodos declarados en las interfaces de API en su lugar. |
| 1535 | Anulando propiedad de Adobe Commerce `@deprecated` | La propiedad obsoleta se eliminará en las próximas versiones. Considere la posibilidad de confiar en los métodos declarados en las interfaces de API o utilizar una propiedad privada dentro de la implementación. |
| 1536 | Asignación de la propiedad de Adobe Commerce `@deprecated` | El método obsoleto se eliminará en las próximas versiones. Considere la posibilidad de confiar en los métodos declarados en las interfaces de API en su lugar. |
| 5006 | Los proxies e interceptores nunca DEBEN solicitarse explícitamente en constructores | La clase original debe declararse como un tipo del parámetro constructor. La implementación de inyección de dependencia de marco pasará la clase Interceptor/Proxy. |
| 5074 | Se ha detectado el uso del método obsoleto `getResource()` para (guardar/cargar/eliminar) datos. | En su lugar, utilice un repositorio. |
| 5086 | La visibilidad no se declara en una constante | Declare la visibilidad en todas las constantes. |

{style="table-layout:auto"}

### Esquema de GraphQL

Las advertencias del esquema GraphQL se generan cuando se añaden elementos adicionales al esquema en la nueva versión. Se recomienda revisar la implementación para ver si debe utilizarse para solicitudes.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 3206 | Valor predeterminado del argumento cambiado | Si la consulta se utiliza en la personalización, es posible que el valor del argumento tenga que especificarse explícitamente. |
| 3302 | Tipo añadido a la unión | El tipo se ha añadido a la unión. Compruebe el procesamiento de la implementación después de que la consulta devuelva este tipo de unión y asegúrese de que puede gestionar el tipo añadido. |
| 3304 | Campo de entrada opcional añadido | Campo de entrada opcional añadido. Compruebe la implementación para asegurarse de que. |
| 3305 | Interfaz implementada agregada | El campo puede aceptar o proporcionar más información que se puede tener en cuenta en la implementación. |
| 3306 | Valor añadido a la enumeración | Se agregó un valor a una enumeración. Si los clientes contienen una instrucción switch en el valor de la enumeración y no incluyen un caso predeterminado, este cambio puede provocar un comportamiento inesperado. |
| 3308 | Argumento opcional añadido | Si la consulta utiliza un nuevo argumento en la personalización, es posible que deba agregarse a la solicitud. |

{style="table-layout:auto"}
