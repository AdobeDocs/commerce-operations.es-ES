---
source-git-commit: 21da8a0133c3c70c2c37851aca79e2d5d8f82905
workflow-type: tm+mt
source-wordcount: '3327'
ht-degree: 0%

---
# Problemas corregidos de Adobe Commerce (v2.4.9)

## Se han corregido problemas en la versión 2.4.9.

Hemos corregido 84 problemas en el código principal de Adobe Commerce 2.4.9. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

* __La operación masiva asincrónica permanece en estado abierto para async.magento.configurableproduct.api.optionrepositoryinterface.save.post__
Los extremos de API masivos generarán un error si el cuerpo de la solicitud no es una matriz, por lo que las claves de elementos masivos deben ser números consecutivos a partir de 0. Anteriormente, el estado del artículo en bloque no se actualizaba debido a la clave de artículo arbitraria enviada en la solicitud en bloque.
  _ACP2E-3544 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* El error de REST de la API __[CLOUD] en su valor is_subscribed no se tiene en cuenta en el almacén actual usando searchCriteria__
API REST La consulta del cliente obtiene el valor &quot;is_subscribed&quot; correcto del almacén correcto mediante searchCriteria
Anteriormente, la consulta del cliente de REST de API no tenía en cuenta el almacén al recuperar el valor &quot;is_subscribed&quot;.
  _ACP2E-3621 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* __async.operations.all puede crear varias entradas para 1 SKU__
Las solicitudes simultáneas para guardar y actualizar el mismo producto ahora se serializan para evitar condiciones de carrera que puedan provocar incoherencia de datos o productos duplicados
  _ACP2E-3744 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/520f9e30>)_

### Cuenta

* __[La operación de eliminación en la nube] está prohibida por el error del área actual durante la creación de la cuenta del cliente__
Después de la corrección, al guardar un cliente con una dirección no válida, se devuelve un mensaje que describe el motivo de la invalidez en lugar de &quot;La operación de eliminación está prohibida para el área actual&quot; irrelevante.
  _ACP2E-3791 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/6ea61121>)_

### IU de administración

* __[Problema]: mejore la experiencia del usuario con el árbol de funciones__
Esta solicitud de extracción añade botones para contraer todo, expandir todo y expandir ramas con los elementos seleccionados. Esta funcionalidad es similar a la proporcionada en el árbol de categorías (catálogo -> inventario -> categorías)
  _AC-14020 - [Problema de GitHub](https://github.com/magento/magento2/issues/39654) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/36511>)_
* __Symfony\Component\Mime\Exception\LogicException: el encabezado &quot;Remitente&quot; debe ser una instancia de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (tiene &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)__
  _AC-14520 - [Problema de GitHub](https://github.com/magento/magento2/issues/39823) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/1e14bd72>) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/1514117f>)_
* __Proporcione una característica para eliminar tasas de impuestos de forma masiva mediante la cuadrícula__
Los usuarios administradores ahora pueden eliminar simultáneamente varios tipos impositivos de la cuadrícula Tipos impositivos de administración.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)
  _AC-2238 - [Problema de GitHub](https://github.com/magento/magento2/issues/33399) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/33484>) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/5cd64dd0>)_
* __La regla de precio del carro de compras con la condición SKU no tiene en cuenta los &quot;ceros a la izquierda&quot; en la SKU (sku: 01234 es igual que 1234)__
El sistema ahora gestiona correctamente la regla de precio del carro de compras con la condición SKU y tiene en cuenta los &quot;ceros a la izquierda&quot; en la SKU
  _AC-9428 - [Problema de GitHub](https://github.com/magento/magento2/issues/37919) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39525>)_
* __Problema con el comportamiento del valor de opción de atributo predeterminado para Multiselect__
Antes de la corrección, los valores predeterminados de los atributos de varias opciones no se guardaban correctamente. Ahora, después de la corrección, los valores se almacenan correctamente en la base de datos.
  _ACP2E-3523 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* __No se muestran los subtítulos del menú de administración back-end__
Ahora se mostrarán correctamente todos los títulos de los grupos de menús principales. Anteriormente, si la segunda o la tercera columna del menú principal contenían solo un grupo de vínculos, no se mostraba el título del grupo.
  _ACP2E-3540_
* __Problema al mover la cantidad del producto al carro de compras desde el administrador__
Al crear un pedido del administrador, los productos del carro de compras del cliente en la barra lateral no desaparecerán cuando se añadan al pedido.
  _ACP2E-3563 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/c8ba4ab1>)_

### IU de administración, B2B

* __El inicio de sesión B2B como encabezado de cliente sigue teniendo la marca Magento__
Anteriormente, el encabezado de la tienda muestra &quot;Ahora está conectado como &lt;nombre del cliente> en &lt;nombre de la tienda>&quot; con la marca Magento. Que ahora es fijo y el encabezado se muestra con la marca ADOBE.
  _AC-14361 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/fadcfa8b>)_

### IU de administración, contenido

* __Excepción &quot;No se puede crear la representación para las rutas de recursos multimedia&quot; durante la inserción de la imagen__
Después de eliminar los valores de Anchura máxima y Altura máxima de la configuración de Optimización de imágenes de la Galería de medios, el error ya no se produjo durante el proceso de optimización de imágenes.
  _ACP2E-3781 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/520f9e30>)_

### IU de administración, seguridad

* __Administración débil de contraseñas__
El usuario administrador no se puede guardar cuando se utiliza la misma contraseña. Anteriormente, se guardaba correctamente sin una validación adecuada.
  _ACP2E-3657 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_

### IU de administración, seguridad, ensayo y vista previa

* __Registros de acciones para el ensayo de contenido__
Los registros de acciones ahora mostrarán las actividades de actualización de ensayo. Anteriormente, el registro de actualización de ensayo no se registraba en los registros de acciones del administrador.
  _ACP2E-3679_

### B2B

* __Realizar pedido no funciona en Continuar con el cierre de compra mediante Oferta negociable con método de pago mediante tarjeta de crédito PayFlow Pro__
  _AC-11973_
* __El mensaje de éxito después de cambiar el nombre de la oferta desaparece intermitentemente__
  _AC-13447_
* __El cálculo del total general no incluye el importe de impuestos__
El pedido contiene los totales correctos cuando se colocan pedidos de compra existentes con la opción Comercio transfronterizo activada.
  _ACP2E-3727_
* __La desasignación de categorías en un catálogo compartido B2B a través de la API de REST es lenta__
Ahora el rendimiento mejora significativamente al anular la asignación de categorías en B2B. Anteriormente, se tardaba mucho tiempo en anular la asignación de categorías en el catálogo compartido B2B.
  _ACP2E-3796_
* __Problema de rendimiento con el nuevo parche de instalación en B2B__
Corrige el problema de rendimiento en el que la actualización del módulo Magento_Company después de actualizar a B2B 1.5.2 tardaba demasiado tiempo al procesar un gran número de registros (~100 000+) en la tabla company_structure.
  _ACP2E-3850_

### Carro y cierre de compra

* __Magento 2.4.7 update (mini)cart no se permite cantidad decimal__
Ahora Magento gestiona correctamente cuándo actualizamos la cantidad con decimales del minicarrito cuando la configuración regional era NL (neerlandés)
  _AC-13238 - [Problema de GitHub](https://github.com/magento/magento2/issues/39236) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39669>)_
* __[Problema] Actualización subtotal.phtml__
El sistema actualiza subtotal.phtml con el espaciado correcto
  _AC-13907 - [Problema de GitHub](https://github.com/magento/magento2/issues/39619) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39612>)_
* __No se pudo realizar el pedido con el invitado__
  _AC-14241 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/27217d0e>)_
* __Un trabajo cron sales_clean_quote no limpia las ofertas persistentes caducadas__
Las comillas persistentes caducadas ahora se borran cuando se ejecuta el trabajo cron &#39;persistent_clear_expire&#39;. Anteriormente, las comillas persistentes caducadas no se borraban con ningún otro trabajo cron.
  _ACP2E-3493 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/11be3dff>)_
* __Error &quot;Se produjo un error&quot; al cerrar la compra de una compañía inactiva__
Antes de la corrección, la acción de cierre de sesión no se completaba correctamente en la página del carro de compras si la empresa del usuario que ha iniciado sesión durante mucho tiempo ya no estaba habilitada. Ahora, si la empresa ya no está disponible, el cierre de sesión se realiza correctamente.
  _ACP2E-3541 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_
* __La selección de direcciones no se guarda cuando realizamos la &quot;Desprotección con varias direcciones&quot;__
Antes de la corrección al cancelar la opción de envío múltiple, la dirección no se preseleccionaba al volver a realizar el envío múltiple. Ahora, la dirección predeterminada se reemplaza con una de las selecciones realizadas en la pantalla de envío múltiple.
  _ACP2E-3646 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/6ea61121>)_

### Carro y cierre de compra, SEO

* __URL de código de tarjeta regalo incorrecta en el correo electrónico cuando se compró en el sitio web secundario__
Anteriormente, la configuración de varias tiendas y la tarjeta regalo para tiendas no predeterminadas siempre redirigían la reclamación de tarjeta regalo al sitio web predeterminado. Después de aplicar esta corrección, el correo electrónico redireccionará el vínculo de la reclamación de la tarjeta regalo al ámbito o sitio web correcto.
  _ACP2E-3699_

### Carro y Pago, Envío

* La regla de precio del carro de compras __[Mainline] no respeta el envío múltiple__
Antes de la implementación de esta corrección, la regla de precio del carro de compras para productos de envío múltiple no se aplicaba correctamente cuando se aplicaban las condiciones de subselección y el envío gratuito estaba habilitado. Sin embargo, como se aplicó la corrección, la regla de precio del carro de compras para carros de envío múltiple ahora funciona según lo previsto.
  _ACP2E-3666 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/b12ffe36>)_

### Catálogo

* __Duplicar fpc de caché para la misma página con la misma consulta__
El sistema ahora identifica y utiliza correctamente la misma caché de página completa (FPC) para las páginas con los mismos parámetros de consulta, independientemente de su orden o los caracteres finales. Esto evita un aumento innecesario del tamaño de la carpeta de la caché de la página. Anteriormente, el sistema creaba un identificador de FPC diferente para la misma página si el orden de los parámetros de consulta era diferente o si había caracteres de cierre, lo que producía un aumento en el tamaño de la carpeta de caché de la página.
  _AC-10722 - [Problema de GitHub](https://github.com/magento/magento2/issues/38269) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/38270>)_
* __Falta la indexación de las columnas necesarias en la tabla catalog_product_entity_int__
Se ha añadido la indexación que falta de las columnas requeridas en la tabla catalog_product_entity_int
  _AC-10844 - [Problema de GitHub](https://github.com/magento/magento2/issues/38315) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/38316>)_
* __La página de producto genera un error debido a las reescrituras de URL__
Ahora la página de producto se carga correctamente cuando se reescribe la dirección URL
  _AC-2950 - [Problema de GitHub](https://github.com/magento/magento2/issues/35371) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39670>)_
* Error de __[nube] al agregar productos a la categoría__
La paginación y la etiqueta de recuento de registros ahora funcionan correctamente al añadir productos a una categoría a través de la cuadrícula emergente. Anteriormente, cargar solo una página con elementos iguales al tamaño de página causaba problemas con la lista desplegable de selección de elementos.
  _ACP2E-3526_
* Error cron de __indexer_update_all_views con MAGE_INDEXER_THREADS_COUNT__
Se ha corregido un problema para MAGE_INDEXER_THREADS_COUNT > 2 con el indexador de segmentos del cliente
  _ACP2E-3538 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* __Excepción al agregar &quot;Combinación de condiciones&quot; en la condición del widget de productos de Page Builder__
El problema se ha corregido añadiendo una comprobación para omitir las condiciones que faltaban o incompletas. Anteriormente, esto provocaba que se generaran registros de errores debido al manejo de condiciones incompletas en el sistema.
  _ACP2E-3545 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/11be3dff>)_
* __Bloqueo del explorador al cargar el conjunto de atributos__
El explorador ya no se bloquea en la página de edición del conjunto de atributos si hay más de 4000 atributos de producto
  _ACP2E-3633 - [Problema de GitHub](https://github.com/magento/magento2/issues/38810) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/b12ffe36>)_
* La URL del producto __[CLOUD] no se ha creado para la nueva tienda: Go Live Bloqueador__
Las reescrituras de URL del producto para la nueva tienda se han creado correctamente.
Anteriormente, la operación finalizaba con pérdidas de memoria o con tiempo de espera.
  _ACP2E-3669 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_
* __Valor predeterminado de atributo para las opciones que no funcionan__
Anteriormente, cuando se cambiaba el valor predeterminado de un atributo de selección de producto, aparecía como un elemento de matriz con los valores anteriores. Después de aplicar esta corrección, cuando actualicemos un valor de atributo de producto, se guardará como un solo elemento en la tabla eav_attribute.
  _ACP2E-3688 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/520f9e30>)_
* __Error de validación de tarjeta regalo al editar debido al separador de miles__
Se ha corregido un problema con el guardado del tipo de producto de la tarjeta regalo cuando la cantidad de la tarjeta regalo es 1000 o más.
  _ACP2E-3704_

### Catálogo, GraphQL, Buscar

* __Los productos que graphql devolvió categorías deshabilitadas en las agregaciones de categorías__
Después de la corrección, las categorías deshabilitadas no se devuelven para la solicitud de productos de GraphQL.
  _ACP2E-2885 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/b12ffe36>)_

### Catálogo, Producto

* __[Error aleatorio] La biblioteca de Fotorama no se ha cargado__
El sistema garantiza ahora que la biblioteca Fotorama se carga correctamente, lo que permite que todas las imágenes adjuntas se muestren en la galería de imágenes según lo esperado. Anteriormente, solo se podía ver la primera imagen debido a un problema con la biblioteca de Fotorama, que no se cargaba correctamente.
  _AC-12124 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/45b51c9c>) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/27217d0e>)_

### Contenido

* __Colocar csp_whitelist.xml en el tema no funciona y crea un problema intermitente__
Se ha implementado el almacenamiento en caché de la lista blanca de CSP por área de sitio web.
  _AC-13069 - [Problema de GitHub](https://github.com/magento/magento2/issues/38933) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39672>)_
* __Error: error de script para &quot;Magento_Catalog/js/validate-product&quot; para el generador de páginas de contenido de administrador con carga de productos__
Esta PR corrige el error de secuencia de comandos para catalogAddToCart al editar el generador de páginas con la condición de productos
  _AC-13891 - [Problema de GitHub](https://github.com/magento/magento2/issues/39604) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39677>)_
* __Bloquear selección en widgets que tienen el mismo identificador__
El sistema ahora gestiona correctamente el bloque de selección al crear widgets cuando tenemos los mismos bloques de identificador
  _AC-14132 - [Problema de GitHub](https://github.com/magento/magento2/issues/39692) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39722>)_
* __No se tiene en cuenta el prefijo de tabla__
  _AC-14556 - [Problema de GitHub](https://github.com/magento/magento2/issues/39847) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/1bc2d6d0>)_
* __No se puede cargar la imagen con una anchura relativamente pequeña__
El sistema ya no deja de cambiar el tamaño de la imagen con una anchura relativamente pequeña a su altura.
  _ACP2E-3558 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* __Ruta de configuración incorrecta para la configuración de estilo de ruta de almacenamiento remoto__
Después de la corrección, establecer la configuración de estilo de ruta de almacenamiento remoto afectará a la configuración real del estilo de ruta de AWS S3.
  _ACP2E-3734 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_

### Marco

* __Completando código de módulo deshabilitado.__
Esta solicitud de extracción ha desactivado los módulos antes de la compilación del código.
  _AC-10933 - [Problema de GitHub](https://github.com/magento/magento2/issues/38241) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39723>)_
* __Plantilla Magento_Theme title.phtml no válida para PHP 8.2__
Esta solicitud de extracción corrige un problema cuando la página de CMS creada con el encabezado nulo como en Php 8.x que pasa nulo a trim() emite una excepción: Funcionalidad obsoleta: trim(): Pasar nulo al parámetro #1 ($string) de tipo cadena
  _AC-12856 - [Problema de GitHub](https://github.com/magento/magento2/issues/39092) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39398>)_
* __Al usar el almacenamiento de archivos para el proveedor de bloqueos, obtenemos un directorio de archivos cada vez mayor sin que se produzca ninguna limpieza__
Esta solicitud de extracción presenta un nuevo trabajo de crono que se ejecuta una vez al día y busca archivos de bloqueo que no se hayan modificado en las últimas 24 horas y que, por lo tanto, se pueden eliminar de forma segura. Esto mantendrá el contenido del directorio de archivos de bloqueo bajo control.
Este cronjob solo ejecutará algo cuando el proveedor de bloqueo esté configurado para usar archivos, no cuando se use uno de los otros (base de datos - el predeterminado, el zookeeper o la caché)
  _AC-13367 - [Problema de GitHub](https://github.com/magento/magento2/issues/39369) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39372>)_
* Limpieza de __[problema]: no use el valor devuelto nulo de las llamadas a métodos.__
Esta PR realiza una limpieza menor. A veces llamamos a métodos que no devolvían nada (void) y luego usamos ese valor de resultado. Lo cual no es necesario.
  _AC-13664 - [Problema de GitHub](https://github.com/magento/magento2/issues/39524) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39516>)_
* __[Problema] [PHPDOC] Corregir phpdoc incorrecto para Magento\Framework\Message\ManagerInterface__
Esta PR corrige el phpdoc incorrecto para \Magento\Framework\Message\ManagerInterface y elimina todos los phpdoc duplicados en \Magento\Framework\Message\Manager (utiliza sintaxis inheritdoc).
  _AC-14312 - [Problema de GitHub](https://github.com/magento/magento2/issues/39593) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39153>)_
* __Se ha eliminado la estabilidad mínima beta de composer.json__
Se ha eliminado la estabilidad mínima beta de composer.json
  _AC-14450 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/1cbbf187>)_
* La __generación de allow_allel_generation debe establecerse a través de la variable de entorno__
Después de la corrección, se puede utilizar la variable de entorno &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; para establecer la configuración &quot;allow_allel_generation&quot;.
  _ACP2E-3673 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __[Nube] Al cambiar el tipo de columna de tabla de Int a Decimal mediante el archivo db_schema.xml en Magento 2, se producen errores__
Cambiar el tipo de datos de columna no funciona correctamente. Anteriormente, genera un error: No se permite el atributo &#39;identity&#39;.
  _ACP2E-3709 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_
* __Nueva compatibilidad con moneda (XCG) en Adobe__
Florín caribeño (XCG) se agrega a la lista de monedas.
  _ACP2E-3790 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/520f9e30>)_

### GraphQL

* __La respuesta de GraphQL para la realización del pedido no incluye el mensaje de excepción__
Se ha revertido el cambio anterior que devolvía errores en un formato diferente. Ahora los posibles errores se devuelven de forma coherente, sin romper el esquema de GraphQL. Debe añadirse como BIC conocido, aprobado por PM aquí: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&amp;page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897
  _ACP2E-3399 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* __La respuesta de GraphQL para la realización del pedido está parcialmente localizada__
Los errores devueltos por la mutación placeOrder GraphQl no se han localizado completamente. Ahora, en un contexto multilingüe, los errores se traducen correctamente.
  _ACP2E-3506 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/9608ca21>)_
* __Llamadas simultáneas para reordenar la API de GraphQL - Se agregaron los mismos productos a diferentes filas__
Corrige el problema en el cual las llamadas simultáneas a la API de Reordenar GraphQL hacen que los mismos productos se agreguen como filas diferentes, lo que provoca incoherencias en los datos.
  _ACP2E-3774 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/c8ba4ab1>)_
* __updateCustomerEmail GraphQL mutation(Cambiar dirección de correo electrónico) no almacena en déclencheur la notificación por correo electrónico__
Anteriormente, el correo electrónico no se enviaba a los clientes después de actualizar correctamente sus direcciones de correo electrónico en sus cuentas. Una vez aplicada la corrección, los clientes ahora reciben notificaciones por correo electrónico después de actualizar correctamente sus direcciones de correo electrónico.
  _ACP2E-3785 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/c8ba4ab1>)_
* __El atributo dinámico no se actualiza en el registro de regalos mediante la mutación updateGiftRegistry__
Anteriormente, antes de esta corrección mediante la mutación updateGiftRegistry, el atributo personalizado del registro de regalos no se modificaba ni actualizaba mediante mutaciones de GraphQL. Después de aplicar esta corrección, el atributo dinámico del registro de regalos se puede actualizar correctamente mediante la mutación updateGiftRegistry.
  _ACP2E-3805 - [Problema de GitHub](https://mcstaging.briscoes.co.nz/)_

### Importación/exportación

* __[Problema] Copyedit: cambiar &quot;copia&quot; a &quot;copia&quot;__
PR corrige la edición de copia menor para corregir la ortografía de &quot;copia&quot;
  _AC-13300 - [Problema de GitHub](https://github.com/magento/magento2/issues/39311) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39307>)_
* __El JSON de importación de producto del extremo REST no valida los campos obligatorios__
El campo de nombre ahora es obligatorio al crear nuevos productos a través del proceso de importación (administrador o API). Antes de la corrección, podría haber creado nuevos productos sin nombre, lo que habría roto la interfaz de administración y creado productos no válidos.
  _ACP2E-3660 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_
* __Falta la opción de filtro de sitio web en el proceso de exportación__
Ahora es posible filtrar los productos por sitios web al crear la exportación de productos.
  _ACP2E-3720 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/520f9e30>)_
* __Duplicado de AC-13913: limpieza de atributo estático asincrónicamente.__
Después de la corrección, no hay ningún error &quot;Undefined array key &quot;apply_to&quot;&quot; cuando se crean numerosas instancias de \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType.
  _ACP2E-3752 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/520f9e30>)_

### Inventario/MSI

* __La recogida en la tienda no respeta el radio máximo de búsqueda cuando la dirección se cambia al pagar__
Ahora, la tienda preseleccionada en &quot;Elegir en tienda&quot; se actualizará si la dirección de envío cambia. Anteriormente, una vez preseleccionada una tienda, no cambiaba aunque la nueva dirección de envío no estuviera en el radio de la tienda seleccionada
  _ACP2E-3728 - [Contribución de código de GitHub](<https://github.com/magento/inventory/commit/07620383>)_

### Pedido

* __No se puede devolver nulo para el campo que no admite valores NULL \&amp;quot;AppliedCoupon.code\&amp;quot; problema inesperado__
  _AC-14484 - [Problema de GitHub](https://github.com/magento/magento2/issues/39841) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/97b2ea42>)_
* __[Cloud] Algunos JavaScript en línea no funcionan después de actualizar a magento 2.4.6-p7__
Al hacer clic en el botón &quot;Eliminar&quot; en &quot;Añadir a pedido por SKU&quot; en el administrador, ahora se elimina el SKU. Anteriormente, al hacer clic en el botón &quot;Eliminar&quot; en &quot;Añadir a pedido por SKU&quot;, no se eliminaba el SKU.
  _ACP2E-3515_
* Los datos serializados de __tarjetas de regalo no son coherentes en la tabla sales_order__
los datos de tarjetas de regalo de la tabla sales_order ahora se serializan correctamente. Anteriormente, se serializaba cada vez que se actualizaba el pedido.
  _ACP2E-3662_

### Pedido, Precio

* __El administrador muestra un símbolo de moneda incorrecto al crear la devolución__
En una configuración de varios sitios web con diferentes monedas (EUR/USD/GBP), la página de selección de productos de retorno del administrador ahora muestra el símbolo de moneda correcto. Anteriormente, mostraba el símbolo de moneda predeterminado.
  _ACP2E-3658 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_

### Otras herramientas para desarrolladores

* __Error de accesibilidad de Lighthouse__
El sistema ahora pasa con una puntuación de accesibilidad de 100
  _AC-12783 - [Problema de GitHub](https://github.com/magento/magento2/issues/39054) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39164>)_
* __Deshabilitar la configuración de la fuente de almacenamiento de captcha sigue cargando los archivos js de captcha__
El sistema ahora no carga archivos captcha js cuando deshabilitamos captcha
para tienda
  _AC-14267 - [Problema de GitHub](https://github.com/magento/magento2/issues/32987) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39154>)_

### Empaquetando

* __[Empaquetado] Corrija magento/magento-coding-standard dependencies+ page-builder__
  _ACPLTSRV-6383_

### Pagos

* __[Problema] Corrige la captura de factura sin conexión (404)__
Corrige el error de página 404 al capturar facturas de métodos de pago sin conexión del administrador de Magento
  _AC-13336 - [Problema de GitHub](https://github.com/magento/magento2/issues/39298) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39297>)_

### Rendimiento

* __El módulo de permisos de categoría posiblemente impide el almacenamiento en caché__
Los controladores de terceros ahora se almacenan correctamente en caché con segmentos de clientes
  _ACP2E-3721_

### Product

* __Colección de productos - addMediaGalleryData llama a getSize cuando la colección puede cargarse o cargarse (puede usar el recuento para evitar una consulta DB adicional)__
Esta PR reduce la llamada de consulta adicional mediante count() si la colección de productos ya se carga al llamar a Product Graphql con el campo media_gallery incluido en ella.
  _AC-13055 - [Problema de GitHub](https://github.com/magento/magento2/issues/39111) - [Contribución de código de GitHub](<https://github.com/magento/magento2/pull/39681>)_
* __[2.4.8] No se encontraron llamadas de retorno para el trabajo cron catalog_product_alert__
  _AC-14494 - [Problema de GitHub](https://github.com/magento/magento2/issues/39800) - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/1bc2d6d0>)_
* __La consulta lenta se ejecuta cuando el widget del producto se incluye a través de pagebuilder__
Se optimiza la consulta para la creación de widgets de producto, incluidos los SKU de producto.
  _ACP2E-3449 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_
* __No se cambió el tamaño de las imágenes del producto cuando se agregaron como producto configurable__
Anteriormente, las imágenes agregadas a través de Configuraciones en el panel de administración no respetaban el límite máximo de tamaño de carga, lo que podía generar incoherencias y desafíos de administración. Ahora, se ha implementado una corrección para garantizar que las imágenes se redimensionen automáticamente durante la carga para cumplir con el límite de tamaño máximo, simplificar el proceso y mantener los estándares del sistema.
  _ACP2E-3504 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/df92debe>)_

### Envío

* __El documento debe actualizarse para la implementación % que no es correcta en el documento oficial__
Se ha actualizado el devdoc para la compatibilidad con la API Rest de DHL
  _AC-14507_
* __[DHL]-Handle Dimensiones opcionales en la configuración de tamaño normal y la variación de precio entre las integraciones de REST y XML API__
  _AC-14601 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/1e3bde4c>)_
* __Excepción al crear la etiqueta de envío UPS__
Advertencia fija: conversión de matriz a cadena durante la creación de etiquetas de envío UPS
  _ACP2E-3676 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/b12ffe36>)_

### Ensayo y previsualización

* __Al obtener una vista previa de una actualización programada, se abre la primera vista de la tienda en orden alfabético, en lugar de la vista de la tienda que te interesa__
Antes de la corrección, la vista previa de una actualización programada se abría en la primera vista de tienda en orden alfabético en lugar de la vista de tienda asignada.
Después de la corrección, la vista previa ahora se abre correctamente en la vista de tienda asignada a la actualización de ensayo del bloque de CMS.
  _ACP2E-3671 - [Contribución de código de GitHub](<https://github.com/magento/magento2/commit/b12ffe36>)_
* __Problema de comportamiento cron de Staging_apply_version - special_price omitido__
Después de la corrección, los totales de las ofertas se recalcularán después de cambiar el precio especial por la actualización programada del producto.
  _ACP2E-3674_

### Impuestos

* __La cantidad de impuestos no se actualiza cuando se quita el envoltorio para regalos del carro de compras__
  _AC-14637_
