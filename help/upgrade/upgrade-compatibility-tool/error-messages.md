---
title: '"[!DNL Upgrade Compatibility Tool] Mensajes de error"'
description: Obtenga más información sobre los mensajes de error que encuentra al usar la variable [!DNL Upgrade Compatibility Tool] en su proyecto de Adobe Commerce.
source-git-commit: 038cb256cb19c253ae9c0375258a555601428847
workflow-type: tm+mt
source-wordcount: '4140'
ht-degree: 4%

---


# [!DNL Upgrade Compatibility Tool] mensajes de error

{{commerce-only}}

Esta referencia de mensaje de error proporciona información sobre los errores que se pueden producir al ejecutar el [!DNL Upgrade Compatibility Tool].

Los mensajes de error se clasifican por nivel (problemas críticos, errores y advertencias) y tipo (código principal, código personalizado y esquemas de GraphQL). Cada tipo contiene la siguiente información:

- **Código de error**: Identificador asignado de Adobe Commerce para el mensaje de error.
- **Descripción del error**: Descripción que resume la causa del error.
- **Acción sugerida por error**: Si corresponde, proporciona instrucciones para solucionar problemas y resolver el error.

## Problemas críticos

### Código principal

Estos errores se notifican cuando faltan algunos de los archivos principales o no coinciden con el original.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 2001 | No se ha encontrado el archivo principal | Ejecute el `composer install` del directorio raíz del proyecto. |
| 2002 | Se modificó el archivo principal | Ejecute el `composer install` del directorio raíz del proyecto. |
| 2003 | La dependencia del compositor no está instalada | La falta de dependencia del compositor puede potencialmente resultar en problemas. Restaurar dependencia mediante la ejecución `composer require package_name`. |
| 2005 | No se ha encontrado la carpeta principal | Ejecute el `composer install` del directorio raíz del proyecto. |

{style=&quot;table-layout:auto&quot;}

### Código personalizado

Se generan errores críticos cuando el código personalizado hace referencia a entidades que no están presentes en la versión de Adobe Commerce de destino. Estos errores también se notifican cuando se han infringido las normas de codificación críticas.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 1110 | Creación de instancias de una clase/interfaz de Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. Creación de instancias de una clase/interfaz de Adobe Commerce inexistente. |
| 1111 | Ampliación desde una clase Adobe Commerce inexistente | La clase ampliada ya no está presente en la base de código. La herencia no es una forma recomendada de ampliar la funcionalidad de Adobe Commerce. Actualizar código para utilizar una clase marcada como `@api`. |
| 1112 | Importación de una clase Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. |
| 1113 | Carga de una clase Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. |
| 1114 | Uso de una clase Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. |
| 1214 | Uso de constante Adobe Commerce inexistente | Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1215 | Anulación de una constante Adobe Commerce inexistente | Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1216 | Asignación de una constante Adobe Commerce inexistente | Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1312 | Interfaz Adobe Commerce inexistente importada | Considere la posibilidad de eliminar la herencia o sustituirla por la interfaz introducida en el ámbito de la personalización. |
| 1314 | Interfaz Adobe Commerce inexistente usada | Considere la posibilidad de eliminar la herencia o sustituirla por la interfaz introducida en el ámbito de la personalización. |
| 1317 | Interfaz Adobe Commerce inexistente heredada | Considere la posibilidad de eliminar la herencia o sustituirla por la interfaz introducida en el ámbito de la personalización. |
| 1318 | Interfaz Adobe Commerce inexistente implementada | Considere la posibilidad de eliminar la herencia o sustituirla por la interfaz introducida en el ámbito de la personalización. |
| 1410 | Llamar a un método Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. |
| 1514 | Uso de una propiedad Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. |
| 1515 | Anulación de una propiedad Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. |
| 1516 | Asignación de una propiedad Adobe Commerce inexistente | Actualizar código para utilizar una clase marcada como `@api`. Actualice el nivel de acceso de la propiedad a privado si solo se puede utilizar dentro de una sola clase. |
| 5002 | La etiqueta PHP de apertura debe ser el primer contenido del archivo | Asegúrese de que no haya contenido en el archivo antes de la etiqueta de apertura de PHP. |
| 5003 | La función está en desuso | Utilice un reemplazo sugerido en el mensaje de error. Si el mensaje no sugiere una sustitución, se necesita una revisión detallada para seleccionar una función o implementación alternativa. |
| 5005 | Error de sintaxis de PHP | El código debe actualizarse para cumplir con los estándares de sintaxis PHP. |
| 5072 | Posible infracción de diseño del Magento 2. Se ha detectado una construcción típica de Magento 1.x | Actualice la construcción a los estándares del Magento 2. |
| 5076 | No se puede usar en el espacio de nombres porque está reservado desde PHP 7 | Reemplace la palabra reservada en el espacio de nombres con una palabra clave no reservada. |
| 5077 | No se puede usar como nombre de clase porque está reservado desde PHP 7 | Reemplace el nombre de clase reservado con un nombre no reservado. |

{style=&quot;table-layout:auto&quot;}

### Esquema de base de datos

Los problemas críticos del esquema de base de datos se notifican si las tablas o columnas principales eliminadas son referenciadas por restricciones personalizadas.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 7009 | La restricción personalizada hace referencia a una tabla principal que se eliminó en la versión de destino | Eliminar la restricción o actualizar los atributos referenceTable y referenceColumn |
| 7010 | La restricción personalizada hace referencia a una columna principal que se eliminó en la versión de destino | Eliminar la restricción o actualizar el atributo referenceColumn |

{style=&quot;table-layout:auto&quot;}

### Esquema de GraphQL

Los problemas críticos del esquema de GraphQL se plantean si los elementos de esquema no están presentes en la versión de destino.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 3101 | Tipo eliminado | Enumere todas las consultas que hacen referencia a este campo. Compruebe si estas consultas las utiliza la implementación de personalización. Actualice el código de cliente para gestionar la interfaz de consulta modificada. |
| 3102 | Tipo eliminado de la unión | Si el tipo de unión se utiliza en la construcción de solicitudes de GraphQL o en la implementación del procesamiento de respuestas, es posible que tenga que actualizarse. |
| 3103 | Campo quitado | Compruebe si se hace referencia al campo en la base de código de personalización. Ajuste la implementación para gestionar correctamente el nuevo tipo de campo. |
| 3105 | Interfaz implementada eliminada | Compruebe si el tipo que implementa la interfaz eliminada se utiliza en la personalización. Puede que sea necesario actualizar la implementación si se basa en la interfaz eliminada. |
| 3106 | Valor eliminado de enum | Si el valor de enumeración eliminado se utiliza en la construcción de solicitudes de GraphQL o en la implementación de procesamiento de respuestas, es posible que tenga que actualizarse. |
| 3107 | Argumento eliminado | Compruebe si el campo se utiliza en la base de código de personalización. Elimine el argumento de este campo. |
| 3109 | Directiva eliminada | Compruebe si la directiva se utiliza en la base de código de personalización. Ajuste la implementación para eliminar la referencia a la directiva. |
| 3110 | Se ha eliminado el argumento de la directiva | Compruebe si la directiva se utiliza en la base de código de personalización. Elimine el argumento de directiva. |
| 3111 | Directiva repetida eliminada | Compruebe si la directiva se utiliza en la base de código de personalización. Ajuste la implementación para gestionar los cambios de la interfaz. |
| 3112 | Ubicación de la directiva eliminada | Compruebe si la directiva se utiliza en la base de código de personalización. Ajuste la implementación para gestionar los cambios de la interfaz. |
| 3201 | Tipo de cambio | Enumere todas las consultas que hacen referencia a este campo. Compruebe si estas consultas las utiliza la implementación de personalización. Actualice el código de cliente para gestionar la interfaz de consulta modificada. |
| 3203 | Tipo de cambio del campo | Compruebe si se hace referencia al campo en la base de código de personalización. Ajuste la implementación para gestionar correctamente el nuevo tipo de campo. |
| 3207 | Tipo de cambio de argumento | Compruebe si el campo se utiliza en la base de código de personalización. Actualice el tipo de argumento para este campo. |
| 3303 | Se ha añadido un campo de entrada obligatorio | El campo debe añadirse a la solicitud si la consulta que incluye este campo se utiliza para la personalización. |
| 3307 | Se agregó un argumento necesario | Compruebe si el campo se utiliza en la base de código de personalización. El nuevo argumento requerido debe especificarse al utilizar el campo . |
| 3310 | Se agregó un argumento de directiva requerido | Compruebe si la directiva se utiliza en la base de código de personalización. Añada el argumento de la directiva. |

{style=&quot;table-layout:auto&quot;}

## Errores

### Código personalizado

Los errores de código personalizado se generan cuando el código personalizado utiliza puntos de entrada de Adobe Commerce que no se consideran o marcan como `@api`. No se garantiza el comportamiento preservado de estos puntos de entrada. La personalización debe depender de `@api` puntos de entrada en su lugar. La funcionalidad basada en código Adobe Commerce que no sea de API debe probarse después de la actualización. Estos errores también se notifican cuando se han infringido las principales normas de codificación.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 1104 | Uso de clase que no es de API y que hereda la interfaz de API | Clases que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de actualizar el código para que dependa de la interfaz marcada como `@api` en su lugar. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1121 | Ampliación desde una clase de API que no es de Adobe Commerce | La clase ampliada ya no está presente en la base de código. La herencia no es una forma recomendada de ampliar la funcionalidad de Adobe Commerce. Actualizar código para utilizar una clase marcada como `@api`. |
| 1122 | Importación de clases de API que no sean de Adobe Commerce | La clase ampliada ya no está presente en la base de código. Actualizar código para utilizar una clase marcada como `@api`. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1123 | Cargando clase de API que no es de Adobe Commerce | La clase ampliada ya no está presente en la base de código. Actualizar código para utilizar una clase marcada como `@api`. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1124 | Uso de clases API que no son de Adobe Commerce | La clase ampliada ya no está presente en la base de código. Actualizar código para utilizar una clase marcada como `@api`. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1224 | Uso de constantes de API que no son de Adobe Commerce | Constantes que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1225 | Anulación de la constante de API que no es de Adobe Commerce | Constantes que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1226 | Asignación de constantes de API que no son de Adobe Commerce | Constantes que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1322 | Interfaz de API no de Adobe Commerce importada | Interfaces no marcadas como `@api` se puede cambiar. Considere la posibilidad de eliminar esta herencia o sustituirla por herencia de la interfaz de Adobe Commerce marcada como `@api` o una interfaz introducida en el ámbito del código de personalización. |
| 1324 | Interfaz de API utilizada que no es de Adobe Commerce | Interfaces no marcadas como `@api` se puede cambiar. Considere la posibilidad de eliminar esta herencia o sustituirla por herencia de la interfaz de Adobe Commerce marcada como `@api` o una interfaz introducida en el ámbito del código de personalización. |
| 1327 | Interfaz de API heredada que no es de Adobe Commerce | Constantes que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de introducir y utilizar una constante privada del valor requerido dentro del código personalizado. |
| 1328 | Interfaz de API implementada que no es de Adobe Commerce | Interfaces no marcadas como `@api` se puede cambiar. Considere la posibilidad de eliminar esta herencia o sustituirla por herencia de la interfaz de Adobe Commerce marcada como `@api` o una interfaz introducida en el ámbito del código de personalización. |
| 1420 | Creación de instancias de una clase/interfaz de API que no sea de Adobe Commerce | Clases que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de actualizar el código para que dependa de la interfaz marcada como `@api` en su lugar. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. Además, la forma recomendada de recuperar una instancia de la clase es mediante el uso de ID. Considere la posibilidad de utilizar una fábrica si se requiere una nueva instancia de la clase. |
| 1428 | Posible dependencia de los detalles de implementación. | Clases que no están marcadas como `@api` se puede cambiar. Considere la posibilidad de actualizar el código para que dependa de la interfaz marcada como `@api` en su lugar. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1429 | Llamar a métodos de API que no sean de Adobe Commerce | Métodos que no están marcados como `@api` o no están declarados dentro de la clase o interfaz de API se pueden cambiar. Incluso si la interfaz del método no se actualiza en la nueva versión, su comportamiento o salida pueden ser diferentes. Considere la posibilidad de confiar en un método de interfaz. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1449 | Llamada a un método que no es de interfaz (que está presente en la implementación) | Los métodos que no están declarados en la interfaz pueden modificarse. Considere la posibilidad de confiar en un método de interfaz. De lo contrario, la funcionalidad que se basa en esta implementación debe probarse después de la actualización. |
| 1524 | Uso de la propiedad API que no es de Adobe Commerce | Valores de las propiedades que no están marcadas como `@api` se puede cambiar. Considere la opción de confiar en el método de interfaz de API en su lugar. |
| 1525 | Anulación de la propiedad de API que no es de Adobe Commerce | Valores de las propiedades que no están marcadas como `@api` se puede cambiar. Considere la opción de confiar en el método de interfaz de API en su lugar. |
| 1526 | Asignación de una propiedad de API que no sea de Adobe Commerce | Valores de las propiedades que no están marcadas como `@api` se puede cambiar. Considere la opción de confiar en el método de interfaz de API en su lugar. |
| 5004 | La función sin argumento ha quedado obsoleta | Pasa la entrada para validar como el primer argumento de la función. |
| 5007 | Se desaconseja el uso de determinadas funciones | Evite utilizar estas funciones. |
| 5009 | Las directivas de plantilla no pueden invocar métodos. Solo se permite el acceso a arreglos de discos escalares | Elimine las invocaciones de método de la plantilla. |
| 5010 | Plantilla `@vars` el bloque de comentarios contiene un JSON no válido | Corrección de JSON no válido. |
| 5011 | Plantilla `@vars` el bloque de comentarios contiene una etiqueta no válida | Se ha corregido una etiqueta no válida. |
| 5012 | Plantilla `@vars` falta una variable utilizada en la plantilla en el bloque de comentarios | Agregue la variable que falta al bloque de comentarios @vars. |
| 5013 | Evite utilizar una etiqueta de cierre automático con un elemento html no nulo | Utilice la etiqueta close en su lugar. |
| 5014 | La variable `"active"` el atributo está obsoleto | La lista de módulos activos se define en la configuración de implementación. |
| 5015 | La variable `<param>` el nodo está obsoleto | Uso `<argument name="..." xsi:type="...">` en su lugar. |
| 5016 | La variable `<instance>` el nodo está obsoleto | Uso `<argument name="..." xsi:type="object">` en su lugar. |
| 5017 | La variable `<array>` el nodo está obsoleto | Uso `<argument name="..." xsi:type="array">` en su lugar. |
| 5018 | La variable `<item key="...">` el nodo está obsoleto | Uso `<item name="..." xsi:type="...">` en su lugar. |
| 5019 | La variable `<value>` el nodo está obsoleto | En su lugar, proporcione el valor real como literal de texto. |
| 5020 | Nodo obsoleto: `<supported_blocks>` | Se reemplazará por `<supported_containers>`. |
| 5021 | Nodo obsoleto: `<block_name>` | Se reemplazará por `<container_name>`. |
| 5022 | Nombre de fábrica detectado | El tipo de utilidad no debe comenzar por /. |
| 5023 | Estructura ACL obsoleta detectada en línea | Consulte lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Estructura de menú obsoleta detectada en línea | Consulte app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Estructura de configuración del sistema obsoleta detectada en el archivo | Consulte app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | No use `"text/javascript"` atributo type | Utilice solo miembros públicos. |
| 5028 | Acceso a miembros protegidos y privados de `Block` la clase está obsoleta en plantillas phtml | Utilice solo miembros públicos. |
| 5031 | Contiene un método obsoleto | Uso `getConnection()` en su lugar. |
| 5042 | Formato incorrecto de la referencia de clase PHP | Compruebe que solo se hace referencia a la clase mediante letras de camelCased, números y ninguna barra diagonal. |
| 5043 | Formato incorrecto de referencia de módulo | Compruebe que solo se haga referencia al módulo mediante letras, números, guiones bajos y ninguna barra diagonal. |
| 5044 | Clase `Zend_Db_Select` está restringido | Sustitución sugerida: `\Magento\Framework\DB\Select`. |
| 5045 | Clase `Zend_Db_Adapter_Pdo_Mysql` está restringido | Sustitución sugerida: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Clase `Magento\Framework\Serialize\Serializer\Serialize` está restringido | Sustitución sugerida: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Clase `ArrayObject` está restringido | Sustitución sugerida: Clase personalizada, extendida desde `ArrayObject` con métodos de serialización/deserialización sobrescritos. |
| 5048 | Clase `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` está restringido | Sustitución sugerida: Fábrica que crea una clase personalizada, ampliada desde `ArrayObject` con métodos de serialización/deserialización sobrescritos. |
| 5050 | Se elimina el bloque al que se hace referencia | Quitar referencia al bloque. |
| 5051 | `output="toHtml"` está obsoleto | Uso `output="1"`. |
| 5052 | La clase `\Magento\Framework\View\Element\Text\ListText` no se supone que se utilice en el diseño | Quitar clase `\Magento\Framework\View\Element\Text\ListText` desde el diseño. |
| 5053 | Llamada al método mediante instrucción de diseño `<action>` no está permitido | Evite utilizar el método ofensivo en `<action>`. |
| 5054 | `helper` el atributo contiene `/` | Eliminar `/` del atributo de ayuda. |
| 5055 | `helper` el atributo no contiene `::` | Agregar `::` para ayudar al atributo . |
| 5056 | Los scripts de instalación están obsoletos | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo. |
| 5057 | Las secuencias de comandos InstallSchema están obsoletas | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo. |
| 5058 | Las secuencias de comandos InstallData están obsoletas | Utilice el método de parches de datos en el directorio Setup/Patch/Data del módulo. |
| 5059 | Los scripts de instalación están obsoletos | Cree una clase InstallData en la carpeta Setup del módulo. |
| 5060 | Las secuencias de comandos de actualización están obsoletas | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo. |
| 5061 | Las secuencias de comandos UpgradeSchema están obsoletas | Utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo. |
| 5062 | Las secuencias de comandos UpgradeData están obsoletas | Utilice el método de parches de datos en el directorio Setup/Patch/Data del módulo. |
| 5063 | Las secuencias de comandos de actualización están obsoletas | Utilice el método de parches de datos en el directorio Setup/Patch/Data del módulo. |
| 5064 | Los scripts recurrentes están obsoletos | Cree la clase Recurring en la carpeta Setup del módulo. |
| 5065 | &#39;data&#39; está en un directorio no válido | Cree un parche de datos en la carpeta Setup/Patch/Data del módulo para las actualizaciones de datos o utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo para los cambios de esquema. |
| 5066 | &#39;sql&#39; está en un directorio no válido | Cree un parche de datos en la carpeta Setup/Patch/Data del módulo para las actualizaciones de datos o utilice el método de esquema declarativo en el archivo etc/db_schema.xml del módulo para los cambios de esquema. |
| 5067 | Los nodos identificados por XPath son obsoletos | XML obsoleto señalado en el error debe actualizarse. Siga las sugerencias del mensaje de error. |
| 5068 | Directiva `{{htmlescape}}` está obsoleto | Uso `{{var}}` en su lugar. |
| 5069 | Directiva `{{escapehtml}}` está obsoleto | Uso `{{var}}` en su lugar. |
| 5070 | El tercer parámetro ya no es necesario para `getChildHtml()` | Quitar el tercer parámetro de la llamada a `getChildHtml()`. |
| 5071 | El cuarto parámetro ya no es necesario para `getChildHtml()` | Eliminar el cuarto parámetro de la llamada a `getChildHtml()`. |
| 5073 | Los nombres de tablas heredadas con barra oblicua deben corregirse en los nombres de tablas directas | Utilice el nombre de tabla directa en su lugar. |
| 5075 | Los módulos de aplicación no deben utilizar clases de módulos de prueba | Elimine el uso de clases de los módulos de prueba. |
| 5078 | La clase debe solicitarse en el constructor, de lo contrario el compilador no podrá encontrar y generar estas clases | Agregue clase al constructor. |
| 5079 | Se desaconseja el uso de variables de clase var | Evite utilizar &#39;var&#39; para declarar la variable de clase. |
| 5080 | Posible instrucción SQL sin procesar detectada | Utilice repositorios o parches de datos en su lugar. |
| 5081 | Se desaconseja el uso de asistentes en las plantillas | Utilice ViewModel en su lugar. |
| 5082 | El uso de $this en plantillas está en desuso | Utilice $block en su lugar. |
| 5083 | No se permiten constantes como el primer argumento de la función de traducción | Utilice literal de cadena en su lugar. |
| 5085 | Se desaconseja el uso de determinadas funciones | En su lugar, utilice la función alternativa que se indica en el mensaje. |
| 5087 | Problema de compatibilidad entre versiones de PHP | Siga las sugerencias del mensaje y compruebe el [guía de migración](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parámetros opcionales que se encuentran después de los necesarios | Mueva los parámetros necesarios después de los opcionales. |
| 5089 | Visibilidad del método `final private` found | Cambiar la visibilidad del método desde `final private` solo para `private`. |
| 5090 | Método mágico `__set_state` no está definido como `static` | Método mágico `__set_state` debe definirse como `static`. |
| 5091 | Clase con `__toString()` método que no hereda de `Stringable` interfaz | Agregar `Stringable` interfaz a clase con `__toString()` método. |
| 5092 | `is_resource()` método utilizado para funciones que ahora devuelven Object | Cambiar `is_resource()` a `instanceof` Objeto. |
| 6001 | `jQuery.andSelf()` eliminado | Uso `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` y `$.unbind` están en desuso | Uso `$.on` y `$.off` en su lugar. |
| 6003 | El método jQuery para suscribirse al evento está obsoleto y no debería usarse | Uso `.on("event name", fn)` para suscribirse a ese evento. |
| 6003 | El método jQuery para el evento de déclencheur está obsoleto y no debería usarse | Uso `.trigger("event name")` para almacenar en déclencheur ese evento. |
| 6004 | jQuery `$.delegate` y `$.undelegate` están en desuso | Uso `$.on` y `$.off` en su lugar. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) se ha eliminado | Use (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` eliminado | Uso `jQuery.length`. |
| 6007 | `jQuery.trim` está en desuso | Uso `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, se ha eliminado el tema &quot;inlite&quot;, el tema &quot;mobile&quot;, el tema &quot;moderna&quot;) | Actualice el código para que sea compatible con tinymce5. |
| 6009 | `jQuery.isFunction()` está en desuso | En la mayoría de los casos, se puede reemplazar por [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` está en desuso | Reemplazar por una comprobación de tipo adecuada como [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` está en desuso | En su lugar, utilice el método nativo Array.isArray. |
| 6009 | `jQuery.parseJSON()` está en desuso | Para analizar cadenas JSON, utilice el método nativo JSON.parse en su lugar. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) está en desuso | Utilice jQuery.expr.pseudos en su lugar. |

{style=&quot;table-layout:auto&quot;}

### Esquema de base de datos

Los errores del esquema de base de datos se generan si las tablas, columnas, índices o restricciones de la base de datos, añadidas o eliminadas en la versión de Adobe Commerce de destino, pueden dar lugar a conflictos con el esquema de base de datos personalizado.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 7001 | La versión principal de destino introduce una tabla con el mismo nombre que una tabla declarada por un módulo personalizado | Usar la nueva tabla principal (si es adecuado) o cambiar el nombre de la tabla personalizada |
| 7002 | La tabla principal ampliada por un módulo personalizado se ha eliminado en la versión de destino | Todas las referencias de tabla principal eliminadas deben eliminarse de la base de código |
| 7003 | La versión principal de destino introduce una columna con el mismo nombre que una columna declarada por un módulo personalizado | Utilice la nueva columna principal (si corresponde) o cambie el nombre de la columna personalizada |
| 7004 | La columna principal que se amplía con un módulo personalizado se eliminó en la versión de destino | Todas las referencias de columnas principales eliminadas deben eliminarse de la base de código |
| 7005 | La versión principal de destino introduce un índice con el mismo referenceId que un índice declarado por un módulo personalizado | Eliminar (si está duplicado en el índice principal introducido) o cambiar el nombre del índice personalizado |
| 7006 | El índice principal ampliado por un módulo personalizado se eliminó en la versión de destino | Todas las referencias de índice principal eliminadas deben eliminarse de la base de código |
| 7007 | La versión principal de destino introduce una restricción con el mismo nombre que una restricción declarada por un módulo personalizado | Eliminar (si está duplicado con la restricción principal introducida) o cambiar el nombre de la restricción personalizada |
| 7008 | La restricción principal extendida por un módulo personalizado se eliminó en la versión de destino | Utilice la nueva restricción principal (si procede) o cambie el nombre de la restricción personalizada |

{style=&quot;table-layout:auto&quot;}

## Advertencias

### Código principal

Estas advertencias se notifican cuando hay incoherencias menores en el código base principal.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 2004 | La versión de dependencia del compositor no coincide | El problema indica que la versión de dependencia del Compositor en el etalón y el proyecto real son diferentes. Actualizar dependencia ejecutando `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### Código personalizado

Las advertencias de código personalizado se generan cuando se detectan las referencias a código obsoleto. Estas referencias deben sustituirse por los puntos de extensión admitidos. Preste atención a la `@see` anotación de elemento obsoleto para recomendaciones. Estos errores también se notifican cuando se han infringido normas de codificación menores.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 1131 | Ampliación desde Adobe Commerce ``@deprecated`` class | La clase ampliada se eliminará en las próximas versiones. La herencia no es una forma recomendada de ampliar la funcionalidad de Adobe Commerce. Actualizar código para utilizar una clase marcada como `@api`. |
| 1132 | Importación de Adobe Commerce `@deprecated` class | La clase ampliada se eliminará en las próximas versiones. Considere utilizar la clase Adobe Commerce marcada como `@api` en su lugar. |
| 1133 | Carga de Adobe Commerce `@deprecated` class | La clase ampliada se eliminará en las próximas versiones. Considere utilizar la clase Adobe Commerce marcada como `@api` en su lugar. |
| 1134 | Uso de Adobe Commerce `@deprecated` class | La clase ampliada se eliminará en las próximas versiones. Considere utilizar la clase Adobe Commerce marcada como `@api` en su lugar. |
| 1234 | Uso de Adobe Commerce `@deprecated` constante | La constante obsoleta se eliminará en las próximas versiones. Considere utilizar una constante marcada como `@api` o una constante privada en su implementación. |
| 1235 | Anulación de Adobe Commerce `@deprecated` constante | La constante obsoleta se eliminará en las próximas versiones. Considere utilizar una constante marcada como `@api` o una constante privada en su implementación. |
| 1236 | Asignación de Adobe Commerce `@deprecated` constante | La constante obsoleta se eliminará en las próximas versiones. Considere utilizar una constante marcada como `@api` o una constante privada en su implementación. |
| 1332 | Adobe Commerce importado `@deprecated` interfaz | La interfaz obsoleta se eliminará en las próximas versiones. Considere utilizar una interfaz o clase marcada como `@api` en su lugar. |
| 1334 | Uso de Adobe Commerce `@deprecated` interfaz | La interfaz obsoleta se eliminará en las próximas versiones. Considere utilizar una interfaz o clase marcada como `@api` en su lugar. |
| 1337 | Heredado de Adobe Commerce `@deprecated` interfaz | La interfaz obsoleta se eliminará en las próximas versiones. Considere la posibilidad de eliminar la herencia de la interfaz mediante una interfaz marcada como `@api` o una interfaz introducida en su implementación en su lugar. |
| 1338 | Adobe Commerce implementado `@deprecated` interfaz | La interfaz obsoleta se eliminará en las próximas versiones. Considere la posibilidad de eliminar la herencia de la interfaz mediante una interfaz marcada como `@api` o una interfaz introducida en su implementación en su lugar. |
| 1430 | Llamada a método dataobject no declarado | Los métodos mágicos que no se declaran pueden cambiar. Considere la opción de confiar en los métodos de interfaz en su lugar. |
| 1439 | Llamar a Adobe Commerce `@deprecated` method | El método obsoleto se eliminará en las próximas versiones. Considere la opción de confiar en métodos declarados en las interfaces de API en su lugar. |
| 1440 | Discordancia de firma del método | Se detecta una llamada o anulación de un método principal con parámetros, argumentos o tipos de devolución que no coinciden con la firma del método. |
| 1534 | Uso de Adobe Commerce `@deprecated` property | El método obsoleto se eliminará en las próximas versiones. Considere la opción de confiar en métodos declarados en las interfaces de API en su lugar. |
| 1535 | Anulación de Adobe Commerce `@deprecated` property | La propiedad obsoleta se eliminará en las próximas versiones. Considere la posibilidad de depender de métodos declarados en las interfaces de API o de utilizar una propiedad privada en su implementación. |
| 1536 | Asignación de Adobe Commerce `@deprecated` property | El método obsoleto se eliminará en las próximas versiones. Considere la opción de confiar en métodos declarados en las interfaces de API en su lugar. |
| 5006 | Los proxys y los interceptores nunca deben solicitarse explícitamente en constructores | La clase original debe declararse como un tipo del parámetro constructor . La implementación de inyección de dependencias del marco pasará la clase Interceptor/Proxy. |
| 5074 | Uso del método obsoleto `getResource()` a datos detectados (guardar, cargar o eliminar). | Utilice un repositorio en su lugar. |
| 5086 | La visibilidad no se declara en una constante | Declare la visibilidad de todas las constantes. |

{style=&quot;table-layout:auto&quot;}

### Esquema de GraphQL

Las advertencias del esquema de GraphQL se generan cuando los elementos adicionales se agregan al esquema en la nueva versión. Se recomienda revisar la implementación para ver si se deben utilizar para las solicitudes.

| Código de error | Descripción del error | Acción sugerida |
| --- | --- | --- |
| 3206 | Se ha cambiado el valor predeterminado del argumento | Si la consulta se utiliza en la personalización, es posible que el valor del argumento tenga que especificarse explícitamente. |
| 3302 | Tipo añadido a la unión | El tipo se agregó a la unión. Compruebe la implementación procesando el resultado de la consulta que devuelve este tipo de unión y asegúrese de que es capaz de gestionar el tipo agregado. |
| 3304 | Se ha añadido un campo de entrada opcional | Se ha añadido un campo de entrada opcional. Compruebe la implementación para asegurarse. |
| 3305 | Interfaz implementada agregada | El campo puede aceptar/proporcionar más información que se pueda considerar en la implementación. |
| 3306 | Valor añadido a enum | Se ha añadido un valor a una enumeración. Si los clientes contienen una sentencia switch en el valor de la enumeración y no incluyen un caso predeterminado, este cambio puede provocar un comportamiento inesperado. |
| 3308 | Se agregó un argumento opcional | Si la consulta está utilizando un nuevo argumento en la personalización, puede que sea necesario añadirlo a la solicitud. |

{style=&quot;table-layout:auto&quot;}
