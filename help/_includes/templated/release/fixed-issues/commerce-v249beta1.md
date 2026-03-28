---
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '26968'
ht-degree: 0%

---
# Adobe Commerce ha solucionado problemas (versión 2.4.9-beta1)

## Se han corregido problemas en la versión 2.4.9-beta1

Hemos corregido 560 problemas en el código principal Adobe Commerce 2.4.9-beta1. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

#### Precio Especial Hasta la Fecha se ha validado incorrectamente en applySpecialPrice

El sistema funciona bien con respecto al precio especial y el precio especial del producto caducará en la fecha establecida por el administrador o el sistema de terceros por la API de REST

_AC-13130 - [Problema de GitHub](https://github.com/magento/magento2/issues/39169) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39690)_

#### Confirmación de correo electrónico de cliente de [WebAPI] mediante la paradoja de WebAPI

Se ha corregido un problema en el cual los clientes no podían activar sus cuentas a través de WebAPI debido a una paradoja de autorización que requería un token antes de la confirmación. La actualización permite a los clientes sin confirmar activar sus cuentas correctamente a través de la API, lo que garantiza un flujo de confirmación coherente y funcional.

_AC-13281 - [Problema de GitHub](https://github.com/magento/magento2/issues/39255) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Error de dirección de facturación faltante en el panel de administración al crear el pedido mediante la API de REST con solo información de pago

Se ha corregido un problema en el cual los pedidos se podían crear mediante API sin una dirección de facturación, lo que ocasionaba bloqueos en el panel de administración.
Ahora, los pedidos sin dirección de facturación están restringidos y ya no se crean.

_AC-14049 - [Problema de GitHub](https://github.com/magento/magento2/issues/39651) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Problema de producto añadido al carro de compras en la API de REST

Se ha corregido un problema en el cual los productos no asignados a un sitio web específico se podían seguir agregando al carro de compras y comprando.
Ahora, se muestra un mensaje de error: &quot;El producto que intenta agregar no está disponible&quot;.

_AC-15054 - [Problema de GitHub](https://github.com/magento/magento2/issues/40029) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f5cc09fc)_

#### La Etiqueta De Opción De Atributo Se Sobrescribe Al Actualizar Las Etiquetas De Tienda

Se ha corregido un problema en el cual la actualización de un atributo de producto multiselección mediante la API de REST sobrescribía todas las etiquetas store_labels, eliminando las etiquetas específicas de tienda existentes.
Ahora, al actualizar la etiqueta de vista de tienda predeterminada, Magento combina las etiquetas proporcionadas con las existentes en lugar de sobrescribirlas por completo.
Esto garantiza que las etiquetas específicas de la tienda para otras vistas de la tienda permanezcan intactas después de las actualizaciones.

_AC-15208 - [Problema de GitHub](https://github.com/magento/magento2/issues/40093) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [Problema] La opción de atributo aclarado ya existe como respuesta

El sistema ha reemplazado ahora la incómoda frase &quot;Obtener nuevo nombre de archivo si ya existe el mismo&quot; con una versión más clara y gramaticalmente correcta: &quot;Obtener un nuevo nombre de archivo si ya existe uno&quot;. Esto mejora la legibilidad y la comprensión del usuario.
Lo mismo para la respuesta de opción de atributo.

_AC-15473 - [Problema de GitHub](https://github.com/magento/magento2/issues/39943) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39941)_

#### Error interno del servidor en /V1/products/special-price API Endpoint

Se ha corregido un problema en el cual las solicitudes mal formadas a /V1/products/special-price y las API de precios relacionadas devolvían un error de servidor interno 500 debido a un TypeError nulo.
Ahora, las API validan correctamente la entrada y devuelven un error 400 para cargas no válidas, lo que mejora la gestión de errores y la fiabilidad de la API.

_AC-6419 - [Problema de GitHub](https://github.com/magento/magento2/issues/35934) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Error interno del servidor en el extremo de API `/V1/order/&lbrace;orderId&rbrace;/ship`

El sistema corrige ahora el error interno del servidor en el extremo de API `/V1/order/{orderId}/ship` y devuelve un error 400, ya que la solicitud tiene un formato incorrecto.

_AC-6420 - [Problema de GitHub](https://github.com/magento/magento2/issues/35931) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38282)_

#### Error interno del servidor en el extremo de API /V1/creditmemo

Se ha corregido un problema en el cual las solicitudes mal formadas a la API /V1/creditmemo devolvían un error de servidor interno 500.
Ahora, la API valida correctamente la solicitud y devuelve un error 400 para cargas no válidas, lo que mejora la gestión y la estabilidad de errores.

_AC-6422 - [Problema de GitHub](https://github.com/magento/magento2/issues/35924) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### El back-end de la API de REST y Magento utiliza métodos de validación diferentes para attribute_code al crear atributos nuevos

Se ha corregido una incoherencia en la que el administrador de Magento permitía letras mayúsculas en attribute_code, pero la API de REST las rechazaba durante la creación de atributos del producto.
Ahora, tanto la API de administrador como la de REST siguen la misma validación, lo que permite crear correctamente atributos con letras mayúsculas.

_AC-6660 - [Problema de GitHub](https://github.com/magento/magento2/issues/33138) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Diferente validación entre la creación de atributos y la actualización mediante la API de REST

Se ha corregido un problema en el cual la validación incoherente durante la creación de atributos mediante la API de REST provocaba que se asignara un backend_type incorrecto.
Ahora, el sistema establece el tipo de backend correcto cuando es válido, emite una excepción para valores no válidos o retrocede apropiadamente si no se proporciona, lo que garantiza un comportamiento de atributo coherente.

_AC-6885 - [Problema de GitHub](https://github.com/magento/magento2/issues/36327) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### El cuerpo o los parámetros de solicitud mal formados provocan un &quot;error interno del servidor&quot;

Los cuerpos o parámetros de solicitud mal formados ahora devuelven una respuesta clara &quot;400 Solicitud incorrecta&quot;.
Anteriormente, el envío de cuerpos de solicitud o parámetros mal formados a varios extremos de API de REST (como /V1/carts/search, /V1/orders, /V1/products, etc.) resultaba en un &quot;error de servidor interno&quot; genérico (500), lo que dificultaba el diagnóstico de problemas de entrada.
Ahora, Adobe Commerce devuelve una respuesta &quot;400 solicitudes incorrectas&quot;, lo que proporciona comentarios más claros cuando las solicitudes no son válidas.

_AC-746 - [Problema de GitHub](https://github.com/magento/magento2/issues/32784) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Faltan los campos &quot;estado&quot; y &quot;estado&quot; en el extremo `/orders`(o `/orders/:id`)

Se ha corregido un problema por el cual las respuestas de API `/orders` y `/orders/{id}` omitían los campos de estado y estado cuando los valores de la base de datos eran nulos.
Ahora, ambos campos se devuelven de forma coherente en la respuesta, lo que garantiza el cumplimiento de la documentación de la API y mejora la fiabilidad de los datos.

_AC-9244 - [Problema de GitHub](https://github.com/magento/magento2/issues/37807) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### La operación masiva asincrónica permanece en estado abierto para async.magento.configurableproduct.api.optionrepositoryinterface.save.post

Los extremos de API masivos generarán un error si el cuerpo de la solicitud no es una matriz, por lo que las claves de elementos masivos deben ser números consecutivos a partir de 0. Anteriormente, el estado del artículo en bloque no se actualizaba debido a la clave de artículo arbitraria enviada en la solicitud en bloque.

_ACP2E-3544 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### El error de REST de la API [CLOUD] en su valor is_subscribed no se tiene en cuenta desde el almacén actual usando searchCriteria

API REST La consulta del cliente obtiene el valor &quot;is_subscribed&quot; correcto del almacén correcto mediante searchCriteria
Anteriormente, la consulta del cliente de REST de API no tenía en cuenta el almacén al recuperar el valor &quot;is_subscribed&quot;.

_ACP2E-3621 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all puede crear varias entradas para 1 SKU

Las solicitudes simultáneas para guardar y actualizar el mismo producto ahora se serializan para evitar condiciones de carrera que puedan provocar incoherencia de datos o productos duplicados

_ACP2E-3744 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Los pedidos &quot;base_row_total&quot; y &quot;row_total&quot; muestran el precio de un solo artículo en la respuesta de la API de REST

La respuesta de la API de REST para los detalles del pedido ahora contiene valores correctos para los atributos &quot;base_row_total&quot; y &quot;row_total&quot; en caso de que se hayan pedido varios artículos iguales

_ACP2E-3874 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### El extremo de la API de REST export-stock-salable-qty devuelve elementos incorrectos total_count

Se ha corregido un problema de paginación en la API de cantidad vendible de stock de exportación de inventario en el que total_count se limitaba incorrectamente al tamaño de página. Anteriormente, al usar el punto de conexión /rest/all/V1/inventory/export-stock-salable-qty/website/base con parámetros de paginación como page_size=5, el campo total_count de la respuesta devolvía 5 en lugar del número total real de productos que coinciden con los criterios de búsqueda. Después de esta corrección, el campo total_count ahora refleja correctamente el número total de productos disponibles independientemente del parámetro page_size, lo que garantiza un comportamiento de paginación coherente en todos los extremos de la API REST de Magento.

_ACP2E-4086 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Problema de validación con ID de opciones personalizadas en las API de REST de elementos del carro de compras.

Las API de REST V1/guest-carts/&lt;cartId>/items/ y V1/carts/mine/items/ ahora validan &quot;product_options.extension_attributes.custom_options&quot;.*.option_id&quot; para asegurarse de que hace referencia a un option_id válido para el SKU del artículo del carro de compras. Anteriormente, este parámetro se procesaba y se guardaba en la base de datos sin validación.

_ACP2E-4138 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Al recuperar el producto del carro de compras y cambiar el idioma del encabezado de la tienda, no cambia

La consulta customerCart de GraphQL ahora devuelve valores de atributo de producto según el valor del encabezado de tienda. Anteriormente, al cambiar el idioma del encabezado de la tienda mientras se recuperaba un producto del carro de compras mediante GraphQL, no se reflejaba el idioma actualizado, lo que producía una localización incoherente.

_ACP2E-4227 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### La API de REST/extremo de medios falla en los productos de tarjeta de regalo. Devuelve &quot;El producto no se puede guardar&quot;

Antes de la corrección, se le permitía crear productos de tarjeta regalo que no incluían una cantidad en el ámbito global. Con la corrección, se ha agregado una validación que comprueba las cantidades en el ámbito global.

_ACP2E-4395 - [Problema de GitHub](https://mcstaging.panini.it/shp_ita_it/)_

### API, carro y cierre de compra

#### Para la información de envío, la validación del lado del servidor no funciona con la API de REST

Se ha corregido un problema en la API de REST por el que la validación de la información de la dirección de envío no se ajustaba a la configuración de atributos definida en el backend de administración. La validación ahora sigue correctamente los ajustes configurados.

_ACP2E-4156 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### API, catálogo

#### Eliminar el punto final de API predeterminado de precios de nivel de tarifa de sitio web/tienda

Anteriormente, al eliminar el sitio web base predeterminado y utilizar el sitio web secundario como sitio web predeterminado, se producía un error al intentar actualizar el precio de nivel del sitio web secundario. Sin embargo, después de aplicar esta corrección, el precio de nivel se puede actualizar correctamente incluso si se elimina o desactiva el sitio web base.

_ACP2E-4334 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### API, marco

#### Excepción RedisRequestLogger\RedisClient (limitador de velocidad) en Application Server

Después de la corrección, la función de limitación de velocidad se puede utilizar junto con el servidor de aplicaciones de GraphQL en casos en los que la extensión PHP redis está instalada.

_ACP2E-4237 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e885088b)_

### API, importación/exportación

#### La API de reembolso de factura asíncrona crea reembolsos sin conexión en lugar de reembolsos en línea

Se corrigieron operaciones de devolución de fondos asincrónicas en las que las solicitudes de devolución con el parámetro `is_online` no se procesaban correctamente.

_ACP2E-4394 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

### API, Pedido

#### [NUBE] Problema de información de pedido con la apariencia total de la fila para la 000075568 de pedido

Corrige el problema por el que el valor row_total_incl_tax en la respuesta de la API de pedidos se devolvía como un valor residual cercano a cero en lugar de 0,00 cuando un artículo se descontaba por completo.

_ACP2E-3950 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Cuenta

#### [Problema]: corrija errores tipográficos en las opciones de la plantilla del widget de catálogo

El sistema ahora corrige errores tipográficos en las opciones de la plantilla del widget de catálogo.

_AC-11576 - [Problema de GitHub](https://github.com/magento/magento2/issues/38185) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38178)_

#### [Problema] eliminó el espaciado innecesario en la cuadrícula del servidor

El sistema ahora elimina el espaciado innecesario en la cuadrícula back-end cuando hay elementos seleccionados

_AC-11579 - [Problema de GitHub](https://github.com/magento/magento2/issues/38502) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32622)_

#### El código de grupo de clientes guardado no coincide con la entrada cuando se utilizan caracteres multibyte

Se ha corregido un problema por el cual los códigos de grupo de clientes que utilizan caracteres multibyte se truncaban y no coincidían con el valor introducido. La actualización garantiza que toda la entrada se guarde correctamente, lo que permite la creación precisa de grupos de clientes con nombres multibyte.

_AC-13335 - [Problema de GitHub](https://github.com/magento/magento2/issues/39342) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Problema al actualizar el correo electrónico del cliente en el Panel de administración con los dominios ö y .swiss

El Panel de administración ahora acepta correos electrónicos de clientes con caracteres especiales y dominios .swiss.
Anteriormente, al actualizar un correo electrónico de cliente a una dirección como max@möstermann.swiss, se producían errores en los nombres de host y los TLD no válidos.
AC-13409

_AC-13409 - [Problema de GitHub](https://github.com/magento/magento2/issues/39394) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### El conmutador habilitado para suscribirse al boletín informativo no funciona por sitio web o tienda

El sistema gestiona correctamente la suscripción a la newsletter cuando tenemos varios sitios web o vistas de tiendas cuando está desactivada a nivel global

_AC-14283 - [Problema de GitHub](https://github.com/magento/magento2/issues/39751) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39752)_

#### Dejar de utilizar una condición de segmento de cliente &quot;Se vio el producto&quot;

La condición del segmento de cliente &quot;Se vio el producto&quot; ya no se utiliza.
Anteriormente, el uso de esta condición podía provocar interrupciones en el sitio debido a consultas MySQL pesadas. La condición ahora está marcada como obsoleta y no es compatible.

_AC-14542_

#### [Problema] eliminó la divulgación del correo electrónico

El sistema muestra ahora Mostrar un mensaje de error que indica un correo electrónico incorrecto si el correo electrónico introducido no es necesario para confirmar la cuenta, independientemente de si el cliente existe o no.

_AC-14561 - [Problema de GitHub](https://github.com/magento/magento2/issues/39574) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39570)_

#### No se pudo borrar el comentario del elemento de la lista de deseos mediante `updateProductsInWishlist` mutación de GraphQL

Se ha corregido un problema por el cual los comentarios de lista de deseos no se actualizaban mediante mutaciones de GraphQL.
Ahora, los comentarios se actualizan correctamente y se reflejan tanto en la respuesta de la API como en la tienda.

_AC-14682 - [Problema de GitHub](https://github.com/magento/magento2/issues/39911) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### El producto eliminado en el móvil sigue apareciendo en la sección de minicomparación de la web hasta que se vuelve a iniciar sesión

El sistema ahora elimina el producto y desaparece inmediatamente de todas las vistas de comparación, tanto móviles como web, incluida la sección de mini comparación.

_AC-14703 - [Problema de GitHub](https://github.com/magento/magento2/issues/39905) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40023)_

#### Mostrar configuración de prefijo/sufijo ignorada cuando se establece en No

Se ha corregido un problema por el cual el prefijo o sufijo del nombre del cliente seguía apareciendo en los pedidos incluso cuando estaba deshabilitado en la configuración.
Ahora, los valores de prefijo/sufijo se eliminan de los detalles del pedido en función de la configuración.

_AC-15074 - [Problema de GitHub](https://github.com/magento/magento2/issues/40036) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Registro de cuenta de cliente de tienda: formato de dirección de correo electrónico convertido con otro formato de dominio

Este error solucionó un problema en el que los correos electrónicos de los clientes con caracteres especiales en el dominio (por ejemplo, tec55241@adòbe.com) se convertían automáticamente al formato punycode (tec55241@xn--adbe-mqa.com).
En Magento 2.4.9-alpha3, la corrección garantiza que estos ID de correo electrónico permanezcan sin cambios y sean válidos, lo que evita errores de entrega.

_AC-15177 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Faltan mensajes de validación (image-error) en el formulario de registro

Se ha corregido un problema por el cual los campos obligatorios de la página de creación de cuenta de cliente no mostraban mensajes de validación cuando se dejaban vacíos.
Ahora se muestran los mensajes de error adecuados para todos los campos vacíos o incorrectos.

_AC-15185 - [Problema de GitHub](https://github.com/magento/magento2/issues/40076) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Falta la traducción del título modal de cancelación de pedido

El sistema ahora corrige una traducción que falta en el modal de cancelación de pedidos de la tienda. Cuando un cliente hace clic en el botón &quot;Cancelar&quot; de la página Mi cuenta > Mis pedidos, aparece un modal que solicita un motivo de cancelación. Sin embargo, el título modal estaba codificado anteriormente y no se podía traducir. Este cambio garantiza que el título modal utilice un método de traducción adecuado.

_AC-15260 - [Problema de GitHub](https://github.com/magento/magento2/issues/40098) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40100)_

#### Problema tras el inicio de sesión en magento 2.4.8-p1

Se ha corregido un problema en Magento 2.4.8-p1 por el que el vínculo &quot;Crear una cuenta&quot; seguía visible en la página de inicio después de iniciar sesión.
Ahora, el vínculo se oculta correctamente después de iniciar sesión, de forma coherente con otras páginas.

_AC-15292: [problema de GitHub](https://github.com/magento/magento2/issues/40120)_

#### [Problema] establecido en isSecureArea antes de eliminar el cliente

El sistema funciona bien y esta PR establece isSecureArea para el proceso de eliminación, y el cliente puede volver a registrarse correctamente.

_AC-15723 - [Problema de GitHub](https://github.com/magento/magento2/issues/40211) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38462)_

#### [La operación de eliminación en la nube] está prohibida por el error del área actual durante la creación de la cuenta del cliente

Después de la corrección, al guardar un cliente con una dirección no válida, se devuelve un mensaje que describe el motivo de la invalidez en lugar de &quot;La operación de eliminación está prohibida para el área actual&quot; irrelevante.

_ACP2E-3791 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [Las solicitudes de API web B2B] hacen un bucle infinito para los clientes que iniciaron sesión cuando se deshabilita la caché &#39;evav&#39;

Después de la corrección, la desactivación de la caché de Java no provoca un bucle infinito durante determinadas solicitudes REST.

_ACP2E-4191 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Error al cargar algunas configuraciones regionales

Se ha corregido un problema por el cual al crear una cuenta de cliente se producía un error al usar la configuración regional árabe y el atributo Fecha de nacimiento se establecía para mostrarse en la tienda. La cuenta ahora se puede crear correctamente en esta configuración.

_ACP2E-4311 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Error Fecha no válida al actualizar la información de cuenta

Los clientes ahora pueden actualizar su cuenta correctamente al utilizar la configuración regional árabe. Anteriormente, al intentar guardar la información de la cuenta, la fecha de nacimiento fallaba debido a un error de fecha no válido.

_ACP2E-4344 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Mensaje de advertencia durante la funcionalidad de envío de invitaciones

Se ha corregido un problema por el cual el mensaje de advertencia &quot;Máximo de X direcciones de correo electrónico permitidas&quot; no se mostraba al agregar campos de correo electrónico en la página Enviar invitaciones si la configuración &quot;Permitir a los clientes agregar un mensaje personalizado al correo electrónico de invitación&quot; estaba deshabilitada.
Anteriormente, la advertencia solo aparecía cuando los mensajes personalizados estaban habilitados, lo que creaba una experiencia de usuario incoherente. Ahora, la advertencia de límite máximo de correo electrónico se muestra de forma coherente independientemente de la configuración del mensaje personalizado.

_ACP2E-4374_

### Cuenta, IU de administración

#### [Cloud] No existe esa entidad con cartId

Se ha resuelto un problema en el cual el uso de Iniciar sesión como cliente con dos cuentas de administrador de empresa en la misma sesión provocaba el error &quot;No existe esa entidad con cartId&quot;.

_ACP2E-4137 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Los mensajes de error del formulario creado por el cliente no están traducidos

Se ha corregido un problema en el cual los mensajes de error de validación del cliente no se traducían y formateaban correctamente en diferentes interfaces. Los errores de validación ahora muestran mensajes traducidos correctamente en todas las áreas de la aplicación: storefront, adminhtml, rest api y graphql.

_ACP2E-4354 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### IU de administración

#### Categoría Productos Cuadrícula > Estado y visibilidad Las columnas están vacías al ordenar por nombre

Se ha corregido un problema por el que las columnas Estado y Visibilidad aparecían vacías en la cuadrícula Productos de categoría al ordenar por nombre de producto.
La cuadrícula ahora muestra correctamente todos los datos de columna después de la ordenación, lo que garantiza una información precisa del producto en el panel de administración.

_AC-10659 - [Problema de GitHub](https://github.com/magento/magento2/issues/38233) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### Conmutador de almacén de plantillas de correo electrónico

Se ha corregido un problema en el cual el conmutador de tienda de la vista previa de la plantilla de correo electrónico del boletín informativo no se abría cuando se hacía clic debido a un código jQuery obsoleto. Al actualizar el evento de carga, se restauró la funcionalidad adecuada, lo que permitió a los usuarios acceder al conmutador de tienda según lo esperado.

_AC-12334 - [Problema de GitHub](https://github.com/magento/magento2/issues/38892) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### El valor de FTP en la página del carro de compras y en la página del producto son diferentes para las mismas configuraciones de un producto simple

Los valores de FTP ahora son coherentes entre el carro de compras y las páginas de productos para productos simples.
Anteriormente, los valores de Impuesto sobre productos fijos (FPT) podían diferir en decimales entre las páginas de carro de compras y producto, incluso cuando se aplicaban las mismas configuraciones.
AC-13066

_AC-13066 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Las opciones de atributos multiselect/select no se pueden guardar cuando los módulos de muestras están desactivados

Ahora, las opciones de atributo Multiselect/select se pueden guardar cuando los módulos Muestras están desactivados.
Anteriormente, al deshabilitar los módulos de Muestras se producían excepciones al crear nuevas opciones de atributos de selección múltiple.
AC-13071

_AC-13071 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### El valor de FTP en la página del carro de compras y en la página de productos es diferente para las mismas configuraciones de un producto dinámico

Los valores de FTP ahora son coherentes entre las páginas de carro y producto para los productos dinámicos.
Anteriormente, los valores de FTP (Impuesto de producto fijo) podían diferir en decimales entre las páginas de carro de compras y producto para las mismas configuraciones.
AC-13075

_AC-13075 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### No se respeta el formato de fecha en el componente de interfaz de usuario

Se ha resuelto un problema en el que el componente IU de fecha ignoraba el formato configurado y mostraba valores incorrectos. La corrección garantiza que el campo de fecha ahora respete el formato especificado (por ejemplo, Y-m-d) tanto para la visualización como para la entrada.

_AC-13174 - [Problema de GitHub](https://github.com/magento/magento2/issues/39218) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### No hay ninguna opción disponible para eliminar orígenes

Se ha añadido una opción de eliminación para fuentes de inventario en la IU de administración, lo que permite a los administradores eliminar fuentes adicionales en lugar de habilitarlas o deshabilitarlas únicamente. Esta mejora mejora la administración del inventario al proporcionar un mejor control sobre las fuentes no utilizadas.

_AC-13354 - [Problema de GitHub](https://github.com/magento/magento2/issues/32362) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### El árbol de categorías de la administración no se ha expandido para mostrar todas las categorías anidadas seleccionadas del nivel 3

Se ha corregido un problema en el cual el árbol de categorías de administración no se ampliaba para mostrar las categorías anidadas seleccionadas más allá del nivel 3. Después de la corrección, todas las categorías seleccionadas se expanden automáticamente, lo que mejora la visibilidad y la facilidad de uso en las condiciones relacionadas con las categorías.

_AC-13363 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problema]: mejore la experiencia del usuario con el árbol de funciones

Esta solicitud de extracción añade botones para contraer todo, expandir todo y expandir ramas con los elementos seleccionados. Esta funcionalidad es similar a la proporcionada en el árbol de categorías (catálogo -> inventario -> categorías)

_AC-14020 - [Problema de GitHub](https://github.com/magento/magento2/issues/39654) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36511)_

#### Los registros de acciones de importación o exportación no se crean en Sistema > Registros de acciones > Cuadrícula de informes

Se ha implementado el registro de las acciones de administración Importar/Exportar, de modo que ahora aparezcan en Sistema > Registros de acciones > Informe. Esto garantiza un mejor seguimiento de la auditoría registrando las actividades de importación que faltaban anteriormente.

_AC-14266 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: El encabezado &quot;Remitente&quot; debe ser una instancia de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (tiene &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

Adobe Commerce ahora envía correctamente correos electrónicos de registro cuando se configura una dirección de ruta de retorno personalizada para SMTP. Anteriormente, en Adobe Commerce 2.4.8 de vainilla con system/smtp/set_return_path establecido en 2 y system/smtp/return_path_email establecido en una dirección personalizada, el registro de cliente se completaba, pero no se enviaba el correo electrónico de registro y Adobe Commerce registraba este error: Symfony\Component\Mime\Exception\LogicException: El encabezado &quot;Remitente&quot; debe ser una instancia de &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (obtuvo &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

_AC-14520 - [Problema de GitHub](https://github.com/magento/magento2/issues/39823) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1e14bd72) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1514117f)_

#### El orden de actualización no obtiene los últimos datos de atributos personalizados

Se ha corregido un problema en el cual al actualizar la página de pedidos no se mostraban los datos de atributos personalizados de cliente más recientes; después de la corrección, los valores de atributos actualizados ahora se reflejan sin necesidad de cancelar y volver a crear el pedido.

_AC-14690: [problema de GitHub](https://github.com/magento/magento2/issues/30301)_

#### [Problema] reemplaza al escape obsoleto

Se ha eliminado el obsoleto getEscaper() y se ha añadido a través de la inyección de constructor.

_AC-15132 - [Problema de GitHub](https://github.com/magento/magento2/issues/40062) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38135)_

#### Mensaje de bienvenida superpuesto a la categoría del producto en la vista móvil

Se ha corregido un problema de la interfaz de usuario por el que el nombre de bienvenida se superponía con las categorías de productos en la vista móvil, bloqueando los clics.
Ahora, las categorías son totalmente visibles y en las que se puede hacer clic sin problemas de superposición.

_AC-15166 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### El botón Restablecer formulario de interfaz de usuario no funciona correctamente

El sistema ahora funciona bien cuando se hace clic en el botón restablecer sin volver a cargar toda la página, se restablecerán los datos del formulario.

_AC-15204 - [Problema de GitHub](https://github.com/magento/magento2/issues/40092) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40094)_

#### [Problema] PageCache/AccessList: Agregar compatibilidad con CIDR

El sistema ahora acepta solicitudes de purga dentro de una red, es más fácil simplemente suministrar un rango CIDR.

_AC-15804 - [Problema de GitHub](https://github.com/magento/magento2/issues/39953) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37809)_

#### [Problema] Agregar títulos explicativos a los botones de administración de caché

El sistema ahora añade títulos explicativos a los botones de gestión de caché cuando mueve el cursor

_AC-16212 - [Problema de GitHub](https://github.com/magento/magento2/issues/38607) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38598)_

#### Proporcionar una función para eliminar tipos impositivos de forma masiva mediante la cuadrícula

Los usuarios administradores ahora pueden eliminar simultáneamente varios tipos impositivos de la cuadrícula Tipos impositivos de administración.  [GitHub-33399](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [Problema de GitHub](https://github.com/magento/magento2/issues/33399) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33484) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Color de desplazamiento no aplicado en cuadrículas estáticas en el administrador

Los colores de desplazamiento ahora se aplican según lo esperado en las filas de las cuadrículas estáticas de administración.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problema de GitHub](https://github.com/magento/magento2/issues/35358) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35384)_

#### Entradas del tipo &quot;No se puede resolver el parámetro reCAPTCHA&quot; en exception.log para el panel de administración de Google reCAPTCHA

Se ha resuelto un error de reCaptcha en el archivo `var/log/exception.log` para el inicio de sesión del administrador de reCAPTCHA de Google V3 y no se ha registrado ningún mensaje de error. Anteriormente, se producía el siguiente error cada pocos segundos cuando un usuario administrador configuraba su configuración de **Configuración** > **Seguridad** > **Panel de administración de Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problema de GitHub](https://github.com/magento/magento2/issues/34975) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contribución de código de GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

#### La regla de precio del carro de compras con la condición SKU no tiene en cuenta los &quot;ceros a la izquierda&quot; en la SKU (sku: 01234 es igual que 1234)

El sistema ahora gestiona correctamente la regla de precio del carro de compras con la condición SKU y tiene en cuenta los &quot;ceros a la izquierda&quot; en la SKU

_AC-9428 - [Problema de GitHub](https://github.com/magento/magento2/issues/37919) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39525)_

#### Problema con el comportamiento del valor de la opción de atributo predeterminado para la selección múltiple

Antes de la corrección, los valores predeterminados de los atributos de varias opciones no se guardaban correctamente. Ahora, después de la corrección, los valores se almacenan correctamente en la base de datos.

_ACP2E-3523 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Los subtítulos del menú de administración del servidor no se muestran

Ahora se mostrarán correctamente todos los títulos de los grupos de menús principales. Anteriormente, si la segunda o la tercera columna del menú principal contenían solo un grupo de vínculos, no se mostraba el título del grupo.

_ACP2E-3540_

#### Problema al mover la cantidad del producto al carro de compras desde el administrador

Al crear un pedido del administrador, los productos del carro de compras del cliente en la barra lateral no desaparecerán cuando se añadan al pedido.

_ACP2E-3563 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Los usuarios administradores restringidos no pueden actualizar el estado del producto de forma masiva

El administrador personalizado puede actualizar el estado del producto de forma masiva, ya que es una propiedad de nivel de sitio web. El estado solo se actualiza en los sitios web a los que el administrador restringido tiene acceso.

_ACP2E-3772_

#### [Ensayo2] Las tarjetas almacenadas no están visibles en el panel de administración

Corrige el problema en el cual la opción de pago &quot;Tarjeta almacenada&quot; ya no aparecía en el formulario de colocación de pedidos back-end después de una actualización.

_ACP2E-3830 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### El usuario administrador restringido puede guardar o actualizar las configuraciones predeterminadas a pesar de los permisos específicos de la tienda

Corrige el problema en el cual los usuarios administradores restringidos podían ver e intentar actualizar el ámbito de &quot;Configuración predeterminada&quot; a pesar de estar asignado únicamente a ámbitos específicos del sitio web, lo que podía causar confusión.

_ACP2E-4011 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Precio de producto configurable guardado en BD para cualquier ámbito de vista de tienda, lo que provoca problemas en la función de clasificación Productos en categoría donde el precio guardado no tiene relevancia en front-end

Se ha eliminado la casilla &quot;Utilizar valor predeterminado&quot; para un producto configurable cuando el precio está configurado por sitio web y se selecciona una vista de tienda en la página de edición de productos configurables de la interfaz de usuario de administración.

_ACP2E-4036 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### La directiva de contraseñas de administrador de [QUANS]no cumple con el cumplimiento de PCI DSS 4.0 (mínimo de 12 caracteres)

Los administradores ahora pueden configurar el requisito de longitud mínima de contraseña para los usuarios administradores a través de Tiendas > Configuración > Avanzado > Administración > Seguridad. Esta mejora proporciona una mayor flexibilidad de seguridad al tiempo que mantiene las directivas de contraseñas existentes. La validación se aplica durante la creación/modificación del usuario administrador y el guardado de la configuración, con validación de front-end en tiempo real para mejorar la experiencia del usuario.

_ACP2E-4044 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Problema con el filtro de fecha cuando el idioma de la interfaz de administración es japonés

El filtro y la columna de cumpleaños utilizarán el formato unificado d/M/y, igual que el filtro o la columna &quot;Cliente desde&quot;

_ACP2E-4052 - [Problema de GitHub](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Bloques blancos que aparecen a ambos lados del encabezado de la cuadrícula de administración

Se ha corregido un problema de alineación visual en las cuadrículas de administración. Anteriormente, al desplazarse horizontalmente por las cuadrículas de producto en el panel de administración, los bloques blancos aparecían mal alineados en los lados izquierdo y derecho del encabezado de la cuadrícula. Los elementos del encabezado de la cuadrícula ahora mantienen la alineación vertical adecuada al desplazarse, lo que proporciona una experiencia visual más nítida para los administradores que administran catálogos de productos grandes.

_ACP2E-4104 - [Problema de GitHub](https://mcprod.pap-store.acer.com/index.html)_

#### El cargador de archivos de componentes de interfaz de usuario no funciona correctamente en 2.4.8-p1/ 2.4-development

Se ha mejorado la carga de archivos para el componente de interfaz de usuario personalizado con varias selecciones para permitir la carga al hacer clic en el área de carga.

_ACP2E-4162 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [En Prem] Pedidos/Compañías/Clientes Recién Creados Incluidos Automáticamente En El Ámbito &quot;Seleccionar Todo&quot; Durante El Proceso De Selección

Se ha corregido el problema que causaba que, al seleccionar manualmente todos los registros en una página de cuadrícula de administración obsoleta, se eliminaran involuntariamente todos los registros al realizar acciones masivas. Anteriormente, la cuadrícula cambiaba automáticamente al modo &quot;seleccionar todo&quot; internamente cuando el número de elementos seleccionados coincidía con el recuento total, lo que provocaba que las acciones masivas afectaran a todos los registros en lugar de solo a los seleccionados explícitamente.

_ACP2E-4202 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### La solución de ACP2E-3362 funciona lentamente en MariaDB 10.6

Se ha mejorado el rendimiento de la página de búsqueda de front-end en caso de un gran número de solicitudes de búsqueda históricas.

_ACP2E-4225 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### El filtro de fecha no funciona según la zona horaria del almacén en la cuadrícula de notas de crédito

Antes de la corrección, las listas de filtrado por atributos de fecha causaban la falta de elementos debido a las diferencias de zona horaria entre las fechas seleccionadas y las fechas almacenadas Ahora, después de aplicar correctamente los filtros de fecha fija.

_ACP2E-4239 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### El cuadro de diálogo Cargador de archivos se abre dos veces al instalar pagebuilder

Antes, el botón Corregir carga de componente personalizado déclencheur dos veces. Después de la corrección, el botón Upload funciona según lo esperado.

_ACP2E-4241 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Errores de validación en atributos de cliente eliminados al cambiar los datos del cliente.

Antes de la corrección, al guardar el cliente y la dirección del cliente se producía un error si se incluían varias opciones de atributo que se habían eliminado. Después de la corrección, ambas se pueden guardar correctamente incluso cuando hay varias opciones de atributo presentes.

_ACP2E-4281 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Cambios en la imagen del producto no registrados en el registro de acciones

Se ha corregido el problema por el cual las cargas y eliminaciones de imágenes de productos no se rastreaban en los registros de acciones de administración. Anteriormente, cuando los administradores añadían nuevas imágenes a un producto o eliminaban imágenes existentes de la galería de medios del producto, estos cambios no se registraban en el sistema de registro. Solo se registraban los cambios en las funciones de imagen (como asignar una imagen como imagen de producto principal, miniatura o imagen pequeña). Ahora, todos los cambios de la galería de medios, incluidas las adiciones y eliminaciones de imágenes, se registran correctamente en los registros de acciones de administración, lo que proporciona una visibilidad completa del registro de auditoría para las actividades de administración de imágenes de productos.

_ACP2E-4302_

#### Advertencia de JS en el tablero de administración: &quot;Se esperaba el inicio del cargador, pero no se encontró ninguno en el dom&quot;

Se ha corregido la advertencia de JavaScript que aparecía en la consola del explorador cuando los gráficos estaban habilitados para el tablero de administración. Anteriormente, al acceder al panel de administración con los gráficos habilitados, una comprobación de depuración obsoleta advertía incorrectamente &quot;Se esperaba iniciar el cargador, pero no se encontró uno en el dom&quot; aunque la funcionalidad funcionaba correctamente.

_ACP2E-4336 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Configuración de [CLOUD] con configuración de dependencia editable cuando se usa la configuración predeterminada de almacén protegida

Se ha corregido el problema que se producía cuando los campos de Configuración del sistema se podían procesar como habilitados después de cargar la página, a pesar de que se estaba marcando &quot;Usar predeterminado/sitio web&quot;.

_ACP2E-4337 - [Problema de GitHub](https://mcstaging.pap-store.acer.com) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### El gráfico de pedidos del tablero de administración se anima al tamaño final

El gráfico de orden del tablero de administración ahora se mostrará inmediatamente sin necesidad de una animación de cambio de tamaño innecesaria.

_ACP2E-4398 - [Problema de GitHub](https://github.com/magento/magento2/issues/38860) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Page Builder no puede guardar contenido en la vista móvil debido a un error de JS (TypeError: No se pueden leer las propiedades de undefined)

Se ha corregido un problema que impedía guardar páginas en el Page Builder al añadir titulares en la vista móvil.

_ACP2E-4399 - [Problema de GitHub](https://github.com/magento/magento2/issues/38565) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### IU de administración, B2B

#### El inicio de sesión B2B como encabezado de cliente sigue teniendo la marca Magento

Anteriormente, el encabezado de la tienda muestra &quot;Ahora está conectado como &lt;nombre del cliente> en &lt;nombre de la tienda>&quot; con la marca Magento. Que ahora es fijo y el encabezado se muestra con la marca ADOBE.

_AC-14361 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fadcfa8b)_

### IU de administración, catálogo

#### El guardado del producto falla cuando la regla de catálogo está activa y el modo en tiempo real está activado

Se ha corregido un problema en el cual la indexación de reglas de catálogo podía fallar con un error de transacción DDL durante las operaciones de guardado del producto al desacoplar la indexación de reglas de catálogo de la transacción del producto.

_ACP2E-4378 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### IU de administración, contenido

#### Excepción &quot;No se puede crear la representación para las rutas de recursos de medios&quot; durante la inserción de la imagen

Después de eliminar los valores de Anchura máxima y Altura máxima de la configuración de Optimización de imágenes de la Galería de medios, el error ya no se produjo durante el proceso de optimización de imágenes.

_ACP2E-3781 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### IU de administración, pedido

#### Creación de pedidos de administración: desbordamiento de tamaño de sesión al añadir más de 20 productos (el tamaño de la sesión superaba el límite de 256 KB)

Se ha resuelto un desbordamiento de tamaño de sesión durante la creación de la solicitud de administrador al evitar que las respuestas de HTML grandes se almacenaran en la sesión para solicitudes JSON, lo que garantiza que las adiciones de productos en lote funcionen sin problemas sin cerrar la sesión del administrador.

_AC-15893_

### IU de administración, seguridad

#### Administración de contraseñas poco fiable

El usuario administrador no se puede guardar cuando se utiliza la misma contraseña. Anteriormente, se guardaba correctamente sin una validación adecuada.

_ACP2E-3657 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

### IU de administración, seguridad, ensayo y vista previa

#### Registros de acciones para ensayo de contenido

Los registros de acciones ahora mostrarán las actividades de actualización de ensayo. Anteriormente, el registro de actualización de ensayo no se registraba en los registros de acciones del administrador.

_ACP2E-3679_

### IU de administración, impuestos

#### Error de IU de administración de tasa impositiva

Este ticket solucionó un problema de la interfaz de usuario de administración de tasa impositiva en el que al cambiar el país (por ejemplo, de EE. UU. → Reino Unido) aún se mostraba el estado de EE. UU. seleccionado anteriormente, lo que confundía a los usuarios.
En 2.4.9-alpha3, el campo de estado ahora se restablece como * cuando el país seleccionado no tiene estados.

_AC-8440 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### Análisis / Informes

#### [Problema] agregó la lista de permitidos scp para Analytics si solo usa Google Analytics

Esta PR agrega una lista blanca de CSP al módulo de Google Analytics, lo que le permite funcionar de forma independiente sin una dependencia de Google AdWords. Google Analytics ahora funciona correctamente incluso cuando el módulo Google AdWords está desactivado.

_AC-16311 - [Problema de GitHub](https://github.com/magento/magento2/issues/40051) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40032)_

#### El informe de usuario de registro de acciones de administración no muestra detalles de qué filtro se utilizó al aplicar filtros

Antes de la corrección, los parámetros de filtrado no se registraban en el informe de actividad de administración. Ahora, después de la corrección, se registran todos los datos de solicitud.

_ACP2E-4099_

#### Encabezados de archivo duplicados en los archivos CSV de informes avanzados que producen informes vacíos

Después de la corrección, los informes generados para la función de creación de informes avanzada ya no contienen filas de encabezado duplicadas en los casos en que el recuento de filas supera el tamaño del lote.

_ACP2E-4187 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### El informe de carrito abandonado contiene caracteres no válidos

El informe de carro de compras abandonado exportado como archivo CSV ahora contiene caracteres procesados correctamente para símbolos de moneda como Rupia india cuando se abre en MS Excel.

_ACP2E-4288 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Actualización de la compatibilidad con MDVA-19640 para 2.4.8

La corrección mueve las tareas de trabajo cron de Analytics del grupo predeterminado al grupo de Analytics

_ACP2E-4309 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### Los ingresos no se muestran en los informes de pedidos/facturas del sitio web/moneda de Administración para Canadá

Algunos de los informes relacionados con pedidos no aplicaban tasas de cambio de divisa de la tienda. Después de la corrección, los informes aplican correctamente las tasas de almacenamiento configuradas.

_ACP2E-4361 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### Realizar pedido no funciona en Continuar con el pago mediante Oferta negociable con el método de pago mediante tarjeta de crédito PayFlow Pro

Adobe Commerce ahora realiza correctamente pedidos al realizar el pago desde una oferta negociable mediante el método de pago con tarjeta de crédito Payflow Pro. Anteriormente, cuando las funciones B2B estaban habilitadas y un comprador procedía a pagar desde una oferta negociable, seleccionar Payflow Pro y hacer clic en Realizar pedido provocaba que la página se siguiera cargando indefinidamente sin mensaje de error y que el pedido nunca se creara. AC-11973

_AC-11973_

#### El mensaje de éxito tras el cambio de nombre de oferta desaparece intermitentemente

Adobe Commerce ahora muestra de forma consistente un mensaje de éxito después de cambiar el nombre de una oferta negociable o una plantilla de oferta en la tienda. Anteriormente, cuando un comprador cambiaba el nombre de una oferta negociable, el mensaje de éxito no aparecía de forma intermitente (a menudo se borraba casi inmediatamente), lo que también provocaba pruebas automatizadas que esperaban a que este mensaje fallara aunque la operación de cambio de nombre en sí se hubiera realizado correctamente. AC-13447

_AC-13447_

#### error de validación de campo de empresa para cierre de compra de invitado

El cierre de compra de invitados ahora valida correctamente el campo de empresa.
Anteriormente, cuando se requería el atributo de empresa, el cierre de compra de invitado fallaba con el error: &quot;La empresa es un valor requerido&quot;, incluso cuando se rellenaba el campo.
AC-14987

_AC-14987 - [Problema de GitHub](https://github.com/magento/magento2/issues/40011) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### El administrador restringido no puede asignar una empresa al catálogo compartido

Se ha corregido un problema en el cual los usuarios administradores restringidos encontraban una excepción al asignar una empresa a un catálogo compartido; la actualización garantiza que la asignación funcione correctamente sin errores.

_AC-15662_

#### Excepción al agregar un producto agrupado a una lista de solicitudes cuando los permisos de categoría están habilitados

Se ha corregido un error de tipo que se producía al agregar productos agrupados a una lista de solicitudes con permisos de categoría habilitados, al garantizar que las opciones de productos se gestionan de forma segura como matrices, lo que permite agregar todos los tipos de productos sin excepciones.

_AC-15862_

#### La API de REST products-render-info devuelve un precio final incorrecto para el cliente que ha iniciado sesión

El ticket tiene una corrección para la API de REST products-render-info que devuelve un precio final incorrecto para el cliente que ha iniciado sesión

_AC-5979 - [Problema de GitHub](https://github.com/magento/magento2/issues/35757)_

#### El botón Añadir a la lista de solicitudes desaparece cuando intentamos añadirlo desde la página de categoría

Anteriormente, el botón Añadir a la lista de solicitudes desaparece cuando se intenta añadirlo desde la página de categoría, que ahora es fija y se puede ver el botón de solicitud en la página de categoría

_AC-8575_

#### El cálculo del total general no incluye el importe de impuestos

El pedido contiene los totales correctos cuando se colocan pedidos de compra existentes con la opción Comercio transfronterizo activada.

_ACP2E-3727_

#### La desasignación de categorías en un catálogo compartido B2B mediante la API de REST es lenta

Ahora el rendimiento mejora significativamente al anular la asignación de categorías en B2B. Anteriormente, se tardaba mucho tiempo en anular la asignación de categorías en el catálogo compartido B2B.

_ACP2E-3796_

### B2B, carro y cierre de compra

#### No existe esa entidad con cartId = se muestra el error X en Storefront cuando se inicia sesión del usuario de la empresa B2B desde la función de administración &quot;Iniciar sesión como cliente&quot;

Ahora el error &quot;No existe esa entidad con cartId = X&quot; ya no está visible después de iniciar sesión correctamente desde el backend de administración al utilizar la función &quot;Iniciar sesión como cliente&quot;.

_ACP2E-3994 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### La falta de dirección de facturación impide la realización de pedidos con el método de envío &quot;Entrega en tienda&quot;

Se ha resuelto un problema en el cual la dirección de facturación no se rellenaba automáticamente durante el cierre de compra cuando se seleccionaba Recogida en la tienda como método de entrega. Sin una dirección de facturación, no se pudo completar el cierre de compra.

_ACP2E-4030 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/42d23211)_

### Carro y cierre de compra

#### Magento 2.4.7 update (mini)cart no se permite una cantidad decimal

Ahora Magento gestiona correctamente cuándo actualizamos la cantidad con decimales del minicarrito cuando la configuración regional era NL (neerlandés)

_AC-13238 - [Problema de GitHub](https://github.com/magento/magento2/issues/39236) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39669)_

#### [Problema] Agregar EventPrefix y EventObject al modelo de acuerdo de cierre de compra

El sistema ahora incluye EventPrefix y EventObject para el modelo de acuerdo de retirada, lo que permite activar eventos con un prefijo de evento. Esta mejora proporciona más flexibilidad para los desarrolladores cuando trabajan con eventos de acuerdo de cierre de compra. Anteriormente, el modelo de acuerdo de cierre de compra no era compatible con EventPrefix y EventObject, lo que limitaba la capacidad de personalizar la administración de eventos.

_AC-13252 - [Problema de GitHub](https://github.com/magento/magento2/issues/32510) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Problema] Experiencia del desarrollador: Cotizar estilo de código AbstractItem (SOP-348 de SwiftOtter)

Esta solicitud de extracción corrige las declaraciones de métodos engañosas para los métodos de elementos abstractos.

_AC-13334: [problema de GitHub](https://github.com/magento/magento2/issues/39340)_

#### Faltan validaciones de cantidad de front-end de producto agrupado

El sistema funciona correctamente y muestra un error de validación cuando se intenta agregar una cantidad negativa y una cantidad máxima

_AC-13524 - [Problema de GitHub](https://github.com/magento/magento2/issues/39479) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39480)_

#### [Problema] al actualizar subtotal.phtml

El sistema actualiza subtotal.phtml con el espaciado correcto

_AC-13907 - [Problema de GitHub](https://github.com/magento/magento2/issues/39619) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39612)_

#### No se puede realizar el pedido con el invitado

Adobe Commerce ahora permite a los compradores invitados realizar pedidos correctamente cuando el campo del segundo nombre está configurado según se requiere en el Administrador. Anteriormente, en Adobe Commerce 2.4.8-beta1 (PHP 8.3/8.4), configurar el segundo nombre como obligatorio y desprotegerlo como invitado impedía la colocación de pedidos incluso cuando se proporcionaba un segundo nombre, lo que bloqueaba la finalización del cierre de compra. AC-14241

_AC-14241 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### [Graphql] no puede devolver un valor nulo para el campo que no acepta valores NULL &quot;SelectedCustomizableOption.label&quot;

El sistema ahora no generará un error de servidor interno con un mensaje cuando la opción seleccionada ya no exista

_AC-14256 - [Problema de GitHub](https://github.com/magento/magento2/issues/39729) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39888)_

#### GraphQL addWishlistItemsToCart no puede actualizar la cantidad de artículos existentes del carro de compras cuando un artículo de la lista de deseos no es válido (Magento 2.4.7-p3)

Se ha corregido un problema en el cual la mutación addWishlistItemsToCart de GraphQL dejaba de procesarse cuando se encontraba un producto configurable no válido. Después de la corrección, se añaden artículos válidos a la lista de deseos al carro y se actualizan las cantidades, mientras que los artículos no válidos se omiten y se devuelven los errores correspondientes.

_AC-14464 - [Problema de GitHub](https://github.com/magento/magento2/issues/39820) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [2.4.8] No se pueden realizar pedidos en los que la ciudad tenga dígitos 0-9, símbolo et, punto final o paréntesis en el nombre de la ciudad

Se ha corregido un problema por el cual el cierre de compra fallaba para nombres de ciudades que contenían caracteres especiales como . , &amp; o paréntesis.
Ahora, los pedidos con estos nombres de ciudad se colocan correctamente sin errores de validación.

_AC-14495 - [Problema de GitHub](https://github.com/magento/magento2/issues/39854) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### El prefijo de invitado no se ha guardado en la dirección de oferta 2.4.8

El prefijo de cliente invitado (Sr./Sra.) ahora se guarda durante el cierre de compra.
Anteriormente, los saludos seleccionados por los clientes invitados se perdían antes de llegar al pedido final, mientras que el resto de los campos de dirección se transferían correctamente.
AC-14705

_AC-14705 - [Problema de GitHub](https://github.com/magento/magento2/issues/39915) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Subselección de regla de ventas con condición de cantidad No se puede aplicar

Se ha corregido un problema en el cual las reglas de precio del carro de compras con condiciones de subselección de productos no se aplicaban al cierre de compra.
Ahora, los descuentos se aplican correctamente según las reglas configuradas.

_AC-14884 - [Problema de GitHub](https://github.com/magento/magento2/issues/39965) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### [Problema] Eliminar espacio en el atributo de clase

El sistema ahora elimina un espacio adicional en el atributo class

_AC-14939 - [Problema de GitHub](https://github.com/magento/magento2/issues/39977) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39970)_

#### Graphql: el carro de combinación no funciona correctamente cuando está habilitado el pedido pendiente

Se ha corregido un problema por el cual los elementos del carro de compras de invitados no se combinaban con el carro de compras de clientes durante la combinación de carros de compras mediante GraphQL.
Ahora, el carro de compras del cliente refleja correctamente la cantidad combinada de los carros de compras de clientes e invitados.

_AC-15148 - [Problema de GitHub](https://github.com/magento/magento2/issues/40064) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integración] [Cierre de compra] Directivas dependientes actualizadas en la plantilla de correo electrónico de pago con errores

Se ha actualizado la plantilla de correo electrónico de pago errónea para gestionar correctamente las directivas de dependencia.
La corrección garantiza que la dirección de envío y el método de envío se muestren correctamente cuando corresponda.
Anteriormente, estos campos faltaban en los correos electrónicos de pago fallidos.

_AC-15363 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Pasar a Finalizar compra redireccionando página de Mi cuenta tras iniciar sesión

Se ha corregido un problema que hacía que se redirigiera a los usuarios a la página de inicio de sesión de Mi cuenta en lugar de al inicio de sesión de cierre de compra después de la caducidad de la sesión, lo que garantizaba que se los llevaba correctamente al cierre de compra con el formulario de inicio de sesión.

_AC-15962_

#### [Carro] La página del carro de compras no se carga cuando se habilita Impuesto sobre productos fijos

Se ha corregido un problema en el cual la página del carro de compras entraba en carga infinita cuando se habilitaba Impuesto de producto fijo (FPT). El problema se debía a cálculos de subtotales incorrectos debido a que los impuestos se incluían en el mismo elemento de HTML que el precio del artículo, lo que provocaba una discrepancia entre los subtotales central y de resumen. Después de la corrección, el carro de compras se carga correctamente y muestra los totales precisos.

_AC-16096 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Regla de precio del carro de compras Acción &quot;Precio en el carro de compras&quot;, condición que se aplica cuando No debe

Se ha corregido un problema por el que las reglas de precios del carro de compras con la condición &quot;Precio en el carro menor que&quot; se aplicaban incorrectamente a los productos no aptos.
Ahora, los cupones se validan y rechazan correctamente cuando los precios de los artículos del carro de compras no cumplen las condiciones de regla configuradas.

_AC-6997 - [Problema de GitHub](https://github.com/magento/magento2/issues/36433) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### [Problema]: establece el precio en el artículo del presupuesto en lugar de en base_price

El sistema gestiona correctamente el precio del artículo de oferta establecido en base_price en lugar del precio si tiene varias monedas en un sitio web en el front-end

_AC-9985 - [Problema de GitHub](https://github.com/magento/magento2/issues/38094) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36878)_

#### Un trabajo cron sales_clean_quote no limpia las ofertas persistentes caducadas

Las comillas persistentes caducadas ahora se borran cuando se ejecuta el trabajo cron &#39;persistent_clear_expire&#39;. Anteriormente, las comillas persistentes caducadas no se borraban con ningún otro trabajo cron.

_ACP2E-3493 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Error &quot;Se ha producido un error&quot; al cerrar la compra de una empresa inactiva

Antes de la corrección, la acción de cierre de sesión no se completaba correctamente en la página del carro de compras si la empresa del usuario que ha iniciado sesión durante mucho tiempo ya no estaba habilitada. Ahora, si la empresa ya no está disponible, el cierre de sesión se realiza correctamente.

_ACP2E-3541 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### La selección de direcciones no se guarda cuando se selecciona &quot;Desproteger con varias direcciones&quot;

Antes de la corrección al cancelar la opción de envío múltiple, la dirección no se preseleccionaba al volver a realizar el envío múltiple. Ahora, la dirección predeterminada se reemplaza con una de las selecciones realizadas en la pantalla de envío múltiple.

_ACP2E-3646 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6ea61121)_

#### [Nube] Pedidos recientes no aparecen en la vista de otra tienda si los pedidos se crean en una vista de tienda

Se ha resuelto un problema en el cual la página &quot;Mi cuenta&quot; no mostraba pedidos recientes de otras vistas de tienda dentro de la misma tienda. La lógica de recuperación de pedidos se ha actualizado para garantizar una visibilidad del pedido coherente en todas las vistas de la tienda, alineándose con el comportamiento de la página &quot;Mis pedidos&quot;.

_ACP2E-3807 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### cantidad mostrada como  0 en la sección del carro de compras del cliente de administración al agregar productos PAQUETE  

La sección Carro de compras de Actividades del cliente ahora muestra la cantidad correcta. Anteriormente, la cantidad se mostraba como 0.

_ACP2E-3872 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

#### El descuento en el envío gratuito de [Cloud] no se eliminó correctamente cuando el carro de compras ya no cumple los requisitos

El Subtotal (Excluido Impuestos) en la regla de precio del carro de compras ahora incorporará descuentos de reglas anteriores.

_ACP2E-3973 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Se ha encontrado un pedido duplicado para el mismo cliente en Multishipping

Las solicitudes simultáneas para realizar pedidos con varias direcciones de envío ya no resultan en pedidos duplicados para el mismo cliente

_ACP2E-4117 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Nube] El mensaje de notificación de límite de existencias superado se muestra dos veces cuando se alcanza el umbral de existencias

Se ha corregido un problema en el cual las actualizaciones del carro de compras podían mostrar titulares de error duplicados. Anteriormente, después de un error de validación de AJAX, el backend volvía a agregar el mismo mensaje durante el envío del formulario, por lo que los compradores veían dos alertas idénticas. Ahora omitimos añadir el mensaje de back-end adicional, manteniendo la página del carro de compras en un único banner de error claro.

_ACP2E-4192 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Para la información de facturación, la validación del lado del servidor no funciona con la API de REST de información de envío

Se ha mejorado la validación de datos de direcciones de clientes para que sea más coherente entre REST y GraphQl para el cierre de compra.

_ACP2E-4223 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Problema con el precio del paquete [Cloud] en la página del carro de compras

Se ha corregido el problema de precio del producto del paquete en la página del carro de compras para tiendas de varias monedas

_ACP2E-4245 - [Problema de GitHub](https://www.techbuyer.com/) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Administrar problemas de ámbito de tienda del carro de compras

Ahora, los errores del carro de compras se mostrarán al usuario administrador al administrar el carro de compras para un cliente asignado a un sitio web no predeterminado. Anteriormente, no se mostraban errores.

_ACP2E-4348 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Coupon times_used se restablece después de la cancelación parcial de la factura

El recuento Coupon times_used ahora se actualiza correctamente cuando se cancela parcialmente un pedido.

_ACP2E-4365 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Carro y cierre de compra, GraphQL

#### Error al asignar el mensaje al código de error al realizar el pedido mediante GraphQL

Las llamadas de GraphQL para realizar un pedido de un carro de compras inexistente o inactivo ahora devuelven correctamente los códigos de error CART_NOT_ACTIVE o CART_NOT_FOUND en todas las vistas de tienda, lo que corrige un problema en el que los mensajes de error traducidos anteriormente resultaban en un código UNDEFINED.

_ACP2E-3942 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### [GraphQl] problema de descuento de artículo de carrito de consulta de carrito en presupuestos virtuales

Se ha resuelto un problema en el cual la consulta del carro de compras de GraphQL devolvía una cantidad de descuento incorrecta para las ofertas virtuales. Anteriormente, los descuentos se aplicaban incorrectamente a ciertos productos virtuales que no eran aptos.

_ACP2E-4248 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### [Cloud] ACSD-68499_2.4.8-p2 crea otro problema

Cuando se realizó una solicitud de graphQL para un artículo con una cantidad insuficiente, se devolvió un mensaje de error correcto con un código de error y, si la cantidad solicitada está disponible, la actualización del carro de compras se realizó correctamente.

_ACP2E-4404 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Carro y cierre de compra, GraphQL, inventario/MSI

#### El atributo is_available de CartItemInterface devuelve el valor &quot;false&quot; incluso cuando las existencias vendibles son altas

El atributo is_available devuelve el valor &quot;True&quot; cuando el stock vendible es alto. Anteriormente, siempre devolvía false.

_ACP2E-3885 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Carro y cierre de compra, inventario/MSI

#### Error 414 en el punto final &quot;Buscar ubicación de recogida&quot; con tamaños de carrito grandes

La selección de una tienda durante el cierre de compra mediante &quot;Elegir en tienda&quot; ya no falla debido a las largas URL cuando hay muchos productos en el carro de compras.
Anteriormente, esto activaba un error 414 provocado por direcciones URL excesivamente largas generadas durante la selección de la tienda, lo que impedía a los clientes completar el cierre de compra.

_ACP2E-4266 - [Problema de GitHub](https://mcstaging.casamyers.com.mx/) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/ae1f272f)_

### Carro de compras y cierre de compra, pedido, producto

#### El correo electrónico de la tarjeta regalo se envía aunque falle la factura del pedido

Antes de la implementación de esta corrección, los correos electrónicos con tarjetas de regalo se enviaban después de crear la factura. Sin embargo, después de aplicar la corrección, los correos electrónicos con tarjetas regalo ahora se envían después de que las facturas se hayan guardado y confirmado correctamente.

_ACP2E-3905_

### Carro y cierre de compra, promoción

#### Mostrar saldo en la tarjeta regalo no está restringido por el ámbito del sitio web

Se ha restringido la comprobación del saldo de la tarjeta regalo con el ámbito del sitio web asignado.

_ACP2E-4379 - [Problema de GitHub](https://www.panini.it)_

### Carro y cierre de compra, SEO

#### URL de código de tarjeta de regalo incorrecta en el correo electrónico cuando se compra en el sitio web secundario

Anteriormente, la configuración de varias tiendas y la tarjeta regalo para tiendas no predeterminadas siempre redirigían la reclamación de tarjeta regalo al sitio web predeterminado. Después de aplicar esta corrección, el correo electrónico redireccionará el vínculo de la reclamación de la tarjeta regalo al ámbito o sitio web correcto.

_ACP2E-3699_

### Carro y cierre de compra, Seguridad

#### [CLOUD] está obteniendo 404 para el archivo JS en la página de cierre de compra al primer intento después de implementar el parche sri

Anterior a la corrección, los mixins no se habrían cargado en el carro y se habrían cerrado cuando las opciones minificar y agrupar estaban habilitadas. Después de la corrección, todos los mixins deben cargarse según lo esperado.

_ACP2E-4128 - [Problema de GitHub](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Carro y Pago, Envío

#### La regla de precio del carro de compras [Mainline] no respeta el envío múltiple

Antes de la implementación de esta corrección, la regla de precio del carro de compras para productos de envío múltiple no se aplicaba correctamente cuando se aplicaban las condiciones de subselección y el envío gratuito estaba habilitado. Sin embargo, como se aplicó la corrección, la regla de precio del carro de compras para carros de envío múltiple ahora funciona según lo previsto.

_ACP2E-3666 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo

#### Fpc de caché duplicado para la misma página con la misma consulta

El sistema ahora identifica y utiliza correctamente la misma caché de página completa (FPC) para las páginas con los mismos parámetros de consulta, independientemente de su orden o los caracteres finales. Esto evita un aumento innecesario del tamaño de la carpeta de la caché de la página. Anteriormente, el sistema creaba un identificador de FPC diferente para la misma página si el orden de los parámetros de consulta era diferente o si había caracteres de cierre, lo que producía un aumento en el tamaño de la carpeta de caché de la página.

_AC-10722 - [Problema de GitHub](https://github.com/magento/magento2/issues/38269) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38270)_

#### Falta la indexación de las columnas necesarias en la tabla catalog_product_entity_int

Se ha añadido la indexación que falta de las columnas requeridas en la tabla catalog_product_entity_int

_AC-10844 - [Problema de GitHub](https://github.com/magento/magento2/issues/38315) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38316)_

#### Error de ámbito en el recurso de URL del catálogo (_getCategories)

Esta PR agrega una alternativa al ámbito predeterminado si no hay ningún valor definido en el ámbito de almacén en el recurso de URL de categoría.

_AC-11011 - [Problema de GitHub](https://github.com/magento/magento2/issues/38393) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problema] Comprobar si OpenGraph puede mostrar el precio

El sistema está funcionando bien cuando utilizamos el complemento que oculta el precio y con este cambio de precio no es visible en la etiqueta OG.

_AC-11635 - [Problema de GitHub](https://github.com/magento/magento2/issues/38512) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38510)_

#### Problema de redondeo de los precios al añadir impuestos para mostrar los precios

El sistema ahora corrige el problema de redondeo en los precios al añadir impuestos a los precios de visualización

_AC-11725 - [Problema de GitHub](https://github.com/magento/magento2/issues/18025) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35730)_

#### [Problema]: permitir condiciones de regla de catálogo personalizadas

Se ha resuelto un problema que impedía que se usaran condiciones de regla de catálogo personalizadas debido a una comprobación de tipo estricta. La corrección reemplaza la comprobación de igualdad de clase por instanceof, lo que permite que las clases de condición personalizadas funcionen correctamente y que la validación y la indexación de reglas se realicen correctamente.

_AC-13338 - [Problema de GitHub](https://github.com/magento/magento2/issues/39339) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Productos configurables pierden opciones cuando se añaden a la lista de deseos

Se ha corregido un problema en el cual las opciones de productos configurables se perdían después de agregar el producto a la lista de deseos. Ahora, las opciones seleccionadas se conservan, lo que permite agregar el producto al carro de compras sin problemas sin pedir a los usuarios que vuelvan a seleccionar las opciones.

_AC-13373 - [Problema de GitHub](https://github.com/magento/magento2/issues/39363) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### El precio especial no se muestra correctamente para el producto secundario del producto configurable (producto simple)

Se ha corregido un problema en el cual el precio especial del producto secundario (simple) de un producto configurable no se mostraba correctamente en la página de lista de productos cuando &quot;Utilizado en la lista de productos&quot; se establecía en No. Ahora, el precio especial se muestra correctamente junto con el precio normal, lo que garantiza una visualización coherente de los precios en todos los tipos de productos.

_AC-13594 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### [Error] en la API de REST: la actualización de precios especiales no establece valores para todas las vistas de tiendas

La API de REST ahora actualiza los precios especiales para todas las vistas de la tienda en un sitio web.
Anteriormente, la actualización de precios especiales mediante la API de REST solo afectaba a la vista de tienda especificada, no a todas las vistas de tienda del sitio web.
AC-13671

_AC-13671 - [Problema de GitHub](https://github.com/magento/magento2/issues/39521) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Problemas con el alcance del precio y config.php

En Magento 2.4.2, cambiar el ámbito del precio a través de config.php no actualiza correctamente el valor is_global en catalog_eav_attribute para el atributo de precio.
Como resultado, los precios de los productos siguen siendo globales y no se pueden guardar por sitio web, incluso cuando el alcance de los precios se establece en sitio web.
La solución requiere actualizar manualmente la columna is_global en la base de datos, lo que no es ideal para entornos de producción.
Este comportamiento es coherente con el diseño predeterminado de Magento, donde el ámbito del precio es Global o Sitio web, pero no por vista de tienda.

_AC-13857: [problema de GitHub](https://github.com/magento/magento2/issues/33559)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] error de PHP desapercibido

Se ha cambiado el nombre de una variable de bucle para añadir correctamente los datos &quot;_cache_instance_product_ids&quot; en el producto dado para utilizarlo en llamadas posteriores.

_AC-14159 - [Problema de GitHub](https://github.com/magento/magento2/issues/39641) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39642)_

#### La búsqueda elástica interfiere con el orden de clasificación predeterminado de los productos (cambiando primero el más reciente por el más antiguo)

El sistema ordena ahora Los productos más recientes de la base de datos (el que tiene el entity_id más alto) se muestran primero

_AC-14411 - [Problema de GitHub](https://github.com/magento/magento2/issues/31043) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36900)_

#### La página de cambio después del almacenamiento proviene de la caché (el conmutador de almacenamiento no funciona) en 2.4.8

Se ha corregido un problema por el cual el cambio de vistas de tienda desde el encabezado de tienda no funcionaba hasta que se borraba manualmente la caché de.
Ahora, el cambio de vista de tienda funciona correctamente sin necesidad de limpiar la caché.

_AC-14426: [problema de GitHub](https://github.com/magento/magento2/issues/39806)_

#### Estilos .less ignorados con ancho mínimo: (@screen__l)

Se ha corregido un problema por el cual solo se mostraban tres productos por fila en las páginas de categoría.
Ahora, se muestran cuatro productos por fila según lo esperado.

_AC-14463 - [Problema de GitHub](https://github.com/magento/magento2/issues/39817) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### El recuento de listas de deseos no se muestra en la página principal/en otras páginas excepto en la página de lista de deseos del menú de cliente

Se ha corregido un problema por el cual el recuento de listas de deseos aparecía como paréntesis vacíos en páginas que no eran de lista de deseos.
Ahora, el recuento correcto de artículos en la lista de deseos se mostrará junto a &quot;Mi lista de deseos&quot; en todas las páginas.

_AC-14607 - [Problema de GitHub](https://github.com/magento/magento2/issues/39892) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before Observer genera un error relacionado con la fecha al utilizar la API de REST sin valores en el nivel de tienda (problema getFinalPrice() )

Esta PR ajusta el procesamiento de SpecialFromDate para garantizar un formato adecuado cuando la fecha se proporciona como una instancia de DateTimeInterface. Esto evita que se produzcan errores durante la ejecución de getFinalPrice() en determinados casos.

_AC-14847 - [Problema de GitHub](https://github.com/magento/magento2/issues/39959) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40003)_

#### URGENTE: no se puede agregar un producto al paquete cuando el producto que se va a agregar tiene opciones personalizables

Se ha corregido un problema en el cual los productos con opciones personalizables no se podían agregar a productos agrupados.
Anteriormente, estos productos se excluían de la lista &quot;Agregar productos a la opción&quot; en la creación de paquetes.
Ahora, los productos con opciones personalizables se pueden añadir a paquetes sin incluir sus opciones personalizadas, lo que permite una administración adecuada de existencias.
Esto permite la creación de paquetes sin duplicar productos ni afectar a los niveles de inventario.

_AC-14958: [problema de GitHub](https://github.com/magento/magento2/issues/39993)_

#### La cadena de consulta `?p=` negativa causa una excepción de Elasticsearch

El sistema ahora aborda el valor negativo ?p= en la paginación Categoría, que actualmente resulta en una excepción y se considera una solicitud válida

_AC-15191 - [Problema de GitHub](https://github.com/magento/magento2/issues/40079) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40080)_

#### Se muestra la etiqueta de precio &quot;Tan bajo como&quot; para productos configurables con una sola opción

Se ha corregido un problema por el cual los productos configurables mostraban el precio con una etiqueta incorrecta &quot;Tan bajo como&quot; en PDP/PLP.
Ahora, el producto muestra el precio correcto ($500) sin ninguna etiqueta engañosa.

_AC-15237 - [Problema de GitHub](https://github.com/magento/magento2/issues/40104) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Se ha llamado un método incorrecto para el botón Agregar a comparar

Se ha corregido el método utilizado en \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect().
Anteriormente, se llamaba incorrectamente a getAddToCartButton() en lugar de a getAddToCompareButton().
Este cambio garantiza el comportamiento correcto al procesar el botón &quot;Agregar para comparar&quot; en las listas de productos.
No se introducen cambios de comportamiento funcional; la actualización mejora la experiencia del desarrollador y la corrección del código.

_AC-15323 - [Problema de GitHub](https://github.com/magento/magento2/issues/39754) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### El precio del producto incorrecto se muestra en el carro de compras con diferentes monedas en diferentes vistas de la tienda

Se ha corregido un problema por el cual se mostraban precios de productos incorrectos en el carro de compras al usar distintas monedas en las vistas de tiendas. Después de la corrección, el carro ahora muestra el precio convertido correcto en función de la moneda configurada, lo que garantiza la coherencia entre la página del producto y el carro de compras.

_AC-15385 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Visualización de precio &quot;Tan bajo como&quot; incorrecta para productos configurables cuando FPT está habilitado

Se ha confirmado que el precio incorrecto de &quot;Hasta&quot; para los productos configurables cuando FPT estaba habilitado se debía a que el impuesto se aplicaba dos veces; la corrección garantiza que el cálculo final del precio respeta la configuración de impuestos y ahora muestra el precio correcto.

_AC-15718 - [Problema de GitHub](https://github.com/magento/magento2/issues/40171) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### La complejidad temporal de _loadAttributes en Eav\Model\Entity\Collection\AbstractCollection aumenta con la cantidad de productos en el carro y los atributos

Este PR optimizó _loadAttributes en Eav\Model\Entity\Collection\AbstractCollection al reemplazar bucles anidados con unión de matriz (+) y reducir las llamadas a _setItemAttributeValue, mejorando el rendimiento para carros de productos grandes.

_AC-15833 - [Problema de GitHub](https://github.com/magento/magento2/issues/40216) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40217)_

#### Interacción incorrecta entre la caché de la colección y la galería de productos configurables

Se ha resuelto un problema de almacenamiento en caché con galerías de productos configurables añadiendo una comprobación de tipo defensivo para garantizar que media_gallery_images siempre se trate como una colección, lo que evita errores fatales causados por datos de caché dañados.

_AC-16066 - [Problema de GitHub](https://github.com/magento/magento2/issues/33965) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### La eliminación de la opción desplegable no funciona al crear el atributo en la página del producto

_AC-16437_

#### La página del producto da error debido a las reescrituras de URL

Ahora la página de producto se carga correctamente cuando se reescribe la dirección URL

_AC-2950 - [Problema de GitHub](https://github.com/magento/magento2/issues/35371) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39670)_

#### Error de [nube] al agregar productos a la categoría

La paginación y la etiqueta de recuento de registros ahora funcionan correctamente al añadir productos a una categoría a través de la cuadrícula emergente. Anteriormente, cargar solo una página con elementos iguales al tamaño de página causaba problemas con la lista desplegable de selección de elementos.

_ACP2E-3526_

#### error cron indexer_update_all_views con MAGE_INDEXER_THREADS_COUNT

Se ha corregido un problema para MAGE_INDEXER_THREADS_COUNT > 2 con el indexador de segmentos del cliente

_ACP2E-3538 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Excepción al añadir &quot;Combinación de condiciones&quot; en la condición del widget de productos de Page Builder

El problema se ha corregido añadiendo una comprobación para omitir las condiciones que faltaban o incompletas. Anteriormente, esto provocaba que se generaran registros de errores debido al manejo de condiciones incompletas en el sistema.

_ACP2E-3545 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/11be3dff)_

#### Bloqueo del explorador al cargar el conjunto de atributos

El explorador ya no se bloquea en la página de edición del conjunto de atributos si hay más de 4000 atributos de producto

_ACP2E-3633 - [Problema de GitHub](https://github.com/magento/magento2/issues/38810) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### La URL del producto [CLOUD] no se ha creado para la nueva tienda: Bloqueador de Go Live

Las reescrituras de URL del producto para la nueva tienda se han creado correctamente.
Anteriormente, la operación finalizaba con pérdidas de memoria o con tiempo de espera.

_ACP2E-3669 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Valor predeterminado de atributo para opciones que no funcionan

Anteriormente, cuando se cambiaba el valor predeterminado de un atributo de selección de producto, aparecía como un elemento de matriz con los valores anteriores. Después de aplicar esta corrección, cuando actualicemos un valor de atributo de producto, se guardará como un solo elemento en la tabla eav_attribute.

_ACP2E-3688 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### La validación de la tarjeta regalo falla al editar debido al separador de miles

Se ha corregido un problema con el guardado del tipo de producto de la tarjeta regalo cuando la cantidad de la tarjeta regalo es 1000 o más.

_ACP2E-3704_

#### [Principal] [El cambio de tamaño de la imagen en la nube] consume más de 400 GB de espacio en disco

Después de la corrección, el comando `catalog:images:resize` utilizado con el indicador `--skip_hidden_images` no generará memorias caché de imágenes para sitios web en los que las imágenes no estén presentes.

_ACP2E-3869 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### La generación dinámica de imágenes genera un gran número de imágenes

Después de la corrección, las imágenes se generarán únicamente para los sitios web a los que esté asignado el producto.

_ACP2E-3927 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### El CountryID proporcionado no existe: Irlanda (IE)

Después de la corrección, los códigos postales de Irlanda están disponibles para buscar ubicaciones de recogida.

_ACP2E-3932 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### Error 500 en front-end debido a que la estructura de diseño incorrecta se almacena en caché en el diseño

Se ha corregido un problema que se producía cuando una página devolvía un código de error 500, debido a que una estructura de diseño incorrecta se almacenaba en caché en el diseño

_ACP2E-4040 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Informe de vistas del producto incorrecto: menor recuento comparado con GA

Se ha corregido un error por el cual la tabla report_views_product_index no mostraba el número correcto de vistas de página de productos.

_ACP2E-4045 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6e134409)_

#### Error de validación para el campo de importe de descuento de la regla de precio de catálogo en Actualización programada

Anteriormente, antes de solucionar este problema, para la actualización de programación de la regla de precio de catálogo, si el importe de descuento es by_fixed, no se validó correctamente debido a la regla validation-number-range. Una vez aplicada esta corrección, la validación funciona correctamente para la regla de precio de catálogo de precio fijo.

_ACP2E-4054 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### La validación del IVA falla debido al limitador de tasa de API de IVA: déclencheur de cambio de grupo de clientes falsos positivos

Se han optimizado las solicitudes a la herramienta de validación Europa Vat, lo que reduce el error de &quot;limitador de tasa&quot;

_ACP2E-4072 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Eliminación masiva en el indexador principal que activa el error de tamaño máximo de conjunto de escritura en producción

Optimiza la limpieza del índice de productos de las reglas del catálogo implementando dos estrategias de eliminación basadas en el volumen de datos.

_ACP2E-4085 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### Los productos se muestran como agotados después de deshabilitarlos

Después de la corrección, los productos deshabilitados no están presentes en el widget de productos.

_ACP2E-4136 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Nube] errores con entradas duplicadas (temp_category_descendientes_%)

Se ha corregido un problema con las entradas duplicadas durante la creación de actualizaciones programadas para entornos con un alto número de categorías anidadas

_ACP2E-4159 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [CLOUD] Comparar productos con un problema de recuento incorrecto para diferentes tiendas

Comparar lista de productos ahora funciona correctamente después de cambiar a otra vista de tienda

_ACP2E-4249 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### Botón &quot;Agregar nuevo atributo&quot; visible para el usuario administrador restringido durante la creación de productos configurables

El botón &quot;Agregar nuevo atributo&quot; ahora solo está visible para el usuario administrador general durante la creación configurable del producto.
Anteriormente, se mostraba el botón &quot;Agregar nuevo atributo&quot; para el usuario administrador restringido

_ACP2E-4279_

#### No hay opción para &#39;usar predeterminada&#39; en &#39;Imágenes y vídeos&#39; para la asignación de funciones de imagen

Se han agregado las opciones &quot;Usar valor predeterminado&quot; a la sección de imágenes y vídeos del producto, lo que permite heredar la configuración del ámbito predeterminado.

_ACP2E-4280 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Los productos de categoría restringida aún se cuentan en la lista de deseos después de actualizar el grupo de clientes

Antes de la corrección, los permisos de categoría no se aplicaban correctamente a los elementos de la lista de deseos del cliente. Ahora, después de la corrección, los elementos de la lista de deseos se muestran y paginan correctamente tanto en la web como en GraphQL.

_ACP2E-4294 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### Problema con el precio del paquete [Cloud] en PDP y PLP

El precio del paquete de producto con precio regular se muestra correctamente en PDP/PLP para la moneda no predeterminada

_ACP2E-4298 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

#### El cliente puede realizar el pedido de un producto inaccesible después de un cambio de grupo de clientes

Anteriormente, al cambiar el grupo de clientes de administrador, el catálogo de front-end y el carro de compras no reflejaban los cambios en los permisos del catálogo. Sin embargo, después de aplicar esta corrección, la oferta de front-end ahora cambia según los permisos de catálogo actualizados cuando el grupo de clientes cambia de administrador.

_ACP2E-4300 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Reindexación atascada debido al alto uso de memoria

Se ha corregido el problema por el que el indexador de reglas de catálogo consumía memoria excesiva y no se completaba, lo que provocaba inestabilidad y errores de falta de memoria.

_ACP2E-4303 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### [El vínculo de vista previa de la actualización programada de CMS] redirige a la página de mantenimiento

La Vista previa de la actualización programada del vínculo a la página de inicio con productos configurables muestra correctamente la lista de productos. Anteriormente, redirigía a los usuarios a la página de mantenimiento

_ACP2E-4401 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1c547060)_

#### Los productos relacionados se eliminan automáticamente

Los productos relacionados que coinciden con las reglas de destino ahora permanecen correctamente asociados durante todo el proceso de reindexación

_ACP2E-4430_

### Catálogo, GraphQL

#### Cálculo de descuento no válido de GraphQl

GraphQL ahora muestra correctamente los porcentajes de descuento y los precios base cuando los precios de catálogo están configurados para incluir impuestos. Anteriormente, se producían errores de redondeo, como mostrar el 19,99 % en lugar del 20 %.

_ACP2E-3993 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### El campo GetCart GraphQL Media Gallery devuelve datos vacíos después del vaciado de la caché

Después de la corrección, media_gallery del producto se devuelve como se espera en la respuesta de GraphQL para la solicitud del carro de compras.

_ACP2E-4185 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Catálogo, GraphQL, Buscar

#### Los productos que graphql devolvió categorías deshabilitadas en las agregaciones de categorías

Después de la corrección, las categorías deshabilitadas no se devuelven para la solicitud de productos de GraphQL.

_ACP2E-2885 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

### Catálogo, Rendimiento

#### Las categorías de administración se cargan muy lentamente

El rendimiento de carga de categorías ha mejorado considerablemente. Anteriormente, se tardaba tanto en cargar la categoría que provocaba un problema de tiempo de espera.

_ACP2E-3891 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catálogo, precios

#### Descuento de regla de precio de catálogo incorrecto aplicado al producto secundario

Corrige el problema en el que la regla de precio de catálogo para la variación se anula con el producto configurable principal, en caso de que ambas reglas tengan la misma prioridad.

_ACP2E-3693 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### Problema con el precio del paquete [Cloud]

El precio del paquete de producto con precio especial se muestra correctamente en PDP/PLP para la moneda no predeterminada

_ACP2E-4110 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6e134409)_

### Catálogo, Producto

#### [Error aleatorio] La biblioteca de Fotorama no se ha cargado

El sistema garantiza ahora que la biblioteca Fotorama se carga correctamente, lo que permite que todas las imágenes adjuntas se muestren en la galería de imágenes según lo esperado. Anteriormente, solo se podía ver la primera imagen debido a un problema con la biblioteca de Fotorama, que no se cargaba correctamente.

_AC-12124 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45b51c9c) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/27217d0e)_

#### El vínculo &quot;Añadir productos manualmente&quot; siempre debe estar visible

Se ha corregido un problema por el cual el vínculo &quot;Añadir productos manualmente&quot; no estaba visible al crear un producto configurable sin configuraciones existentes. El vínculo ahora siempre se muestra, lo que permite a los administradores asociar fácilmente productos simples sin crear configuraciones simuladas.

_AC-13866 - [Problema de GitHub](https://github.com/magento/magento2/issues/39595) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Editar un producto en el backend Elimina los lugares decimales adicionales del precio de las opciones del producto

Se ha corregido un problema en el cual al editar un producto en la opción de producto del administrador se truncaba el precio a dos decimales. El sistema ahora conserva los precios con mayor precisión decimal, lo que garantiza que los valores precisos se conserven después de guardar.

_AC-14050 - [Problema de GitHub](https://github.com/magento/magento2/issues/39655) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Los productos relacionados a través de una regla de producto relacionada no aparecen en PDP a través de GraphQL

Anteriormente, antes de aplicar esta corrección, la regla de producto relativa devolvía vacío/nulo para un producto que coincidía con la regla. Una vez aplicada esta corrección, la regla relativa para el producto devuelve correctamente los productos coincidentes.

_ACP2E-3949_

### Catálogo, devoluciones

#### La página de devolución de pedidos de [Cloud] para la fila de productos del paquete se deselecciona automáticamente

Anteriormente, para el producto del paquete Enviar juntos de vuelta en la vista de cuadrícula del panel de administración, teníamos una opción &quot;Seleccionar elementos&quot; que creaba confusión para la opción Enviar juntos del producto del paquete. Después de aplicar esta corrección, para los envíos de productos agrupados, ya no hay la opción &quot;Seleccionar elementos&quot;.

_ACP2E-4180_

### Catálogo, Buscar

#### La solicitud de RestApi &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; falla con un error de tiempo de espera

Las solicitudes de API de REST de categoría ya no fallan con errores de tiempo de espera.
Anteriormente, las solicitudes a /rest/default/V1/categories?searchCriteria[page_size]=1 podían fallar con un tiempo de espera después de ciertos cambios en el código.
AC-13358

_AC-13358 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Contenido

#### graphql (magento 2.4.6-p4 ): error al intentar obtener la página de cms sin estado activo

Se ha corregido un problema en el cual la consulta de GraphQL para una página de CMS deshabilitada devolvía un error interno del servidor.
Ahora, la consulta obtiene una respuesta adecuada sin errores.

_AC-12302 - [Problema de GitHub](https://github.com/magento/magento2/issues/38877) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### El formulario para compartir listas de deseos permite el uso de código aleatorio en los campos de nombre

Se ha corregido una vulnerabilidad crítica de inyección de plantillas del lado del servidor (SSTI) en el formulario de uso compartido de listas de deseos en la que se podía introducir código malintencionado en el campo de mensaje y enviarlo por correo electrónico. La actualización agrega validación de entrada a directivas de plantilla de bloque y patrones no seguros, y ahora muestra un mensaje de error cuando se detecta contenido no válido.

_AC-12730 - [Problema de GitHub](https://github.com/magento/magento2/issues/39024) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Colocar csp_whitelist.xml en el tema no funciona y crea un problema intermitente

Se ha implementado el almacenamiento en caché de la lista blanca de CSP por área de sitio web.

_AC-13069 - [Problema de GitHub](https://github.com/magento/magento2/issues/38933) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39672)_

#### Después de la actualización a magento 2.4.7 p2 no se pueden ver los archivos cargados recientemente galería de medios

Los archivos cargados recientemente ahora aparecen en la Galería de medios después de la actualización.
Anteriormente, después de actualizar a Magento 2.4.7 p2, las imágenes recién cargadas no aparecían en la Galería de medios hasta que se realizaba una sincronización manual.
AC-13262

_AC-13262: [problema de GitHub](https://github.com/magento/magento2/issues/39275)_

#### La galería de medios muestra imágenes incorrectas de directorios con nombres idénticos pero mayúsculas y minúsculas diferentes

El sistema ahora resuelve un problema en el que los archivos cargados en un directorio específico en la Galería multimedia también son visibles en directorios con nombres similares pero mayúsculas y minúsculas diferentes.

_AC-13489 - [Problema de GitHub](https://github.com/magento/magento2/issues/39382) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39502)_

#### Al eliminar completamente una imagen de la galería, se mantiene establecidas las funciones/tipos de ámbito (base/pequeña/en miniatura) y después de volver a agregar las funciones/tipos &quot;antiguos&quot; aparecen

El sistema funciona según lo esperado en los ámbitos del almacén. Las imágenes heredan las funciones y los tipos de la nueva imagen añadida según el ámbito predeterminado

_AC-13556 - [Problema de GitHub](https://github.com/magento/magento2/issues/39481) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Pequeño error] El filtro del panel de administración `listing component` no se puede alcanzar cuando el valor del campo contiene `\`

El sistema funciona correctamente cuando filtramos el título de la página con una barra diagonal (p. ej.: Magento\Store)

_AC-13661 - [Problema de GitHub](https://github.com/magento/magento2/issues/39513) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39535)_

#### Error: Error de script para &quot;Magento_Catalog/js/validate-product&quot; para el generador de páginas de contenido de administrador con carga de productos

Esta PR corrige el error de secuencia de comandos para catalogAddToCart al editar el generador de páginas con la condición de productos

_AC-13891 - [Problema de GitHub](https://github.com/magento/magento2/issues/39604) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39677)_

#### Error de secuencia de comandos catalogAddToCart al configurar el widget de producto.

Se ha corregido un error de script que se producía al configurar el widget Productos con &quot;Combinación de condiciones&quot; en Page Builder. El problema se debía a que faltaban archivos JS de front-end, lo que provocaba errores de consola. Después de la corrección, el widget se carga correctamente sin errores de consola.

_AC-13892 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Bloquear la selección en widgets que tengan el mismo identificador

El sistema ahora gestiona correctamente el bloque de selección al crear widgets cuando tenemos los mismos bloques de identificador

_AC-14132 - [Problema de GitHub](https://github.com/magento/magento2/issues/39692) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39722)_

#### &quot;La página de CMS con el ID &quot;0&quot; no existe&quot; inundación de registro

El sistema funciona según lo esperado después de crear un usuario administrador y cuando creamos una nueva página, system.log no tiene ningún mensaje de error

_AC-14254 - [Problema de GitHub](https://github.com/magento/magento2/issues/39743) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39746)_

#### [GraphQl] Bucle infinito de consulta de ruta

Este ticket corrigió el problema en el que una consulta de ruta de GraphQL con una ruta de solicitud y una ruta de destino idénticas provocaban un bucle infinito y, finalmente, se agotaba el tiempo de espera.
En 2.4.9-alpha3, la consulta ahora devuelve la respuesta de error correcta en lugar de crear un bucle.

_AC-14269 - [Problema de GitHub](https://github.com/magento/magento2/issues/39707) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### El mapa del sitio no existente responde con la imagen del producto

El sistema ahora corrige cuando accedemos a Mapa del sitio no existente responde con la imagen del producto con Respuesta: 404 NO ENCONTRADO

_AC-14295 - [Problema de GitHub](https://github.com/magento/magento2/issues/39756) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40135)_

#### Los widgets de vínculo al catálogo utilizan una URL incorrecta

El sistema ahora gestiona correctamente los widgets después de añadir el vínculo de producto del catálogo y el vínculo de categoría del catálogo, y también muestra las direcciones URL correctas en el origen HTML

_AC-14437 - [Problema de GitHub](https://github.com/magento/magento2/issues/39464) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39710)_

#### No se tiene en cuenta el prefijo de tabla

Adobe Commerce ahora respeta correctamente los prefijos de tabla de la base de datos al cargar la cuadrícula de temas Diseño > Configuración en Admin. Anteriormente, en Adobe Commerce 2.4.8 con un prefijo de tabla configurado en app/etc/env.php, al navegar a Contenido > Diseño > Configuración, se producía un error porque el prefijo de tabla no se tenía en cuenta y la cuadrícula de temáticas no se representaba.

_AC-14556 - [Problema de GitHub](https://github.com/magento/magento2/issues/39847) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Cambie la constante IMAGE_FILE_NAME_PATTERN a public visible para obtener más flexibilidad

La constante IMAGE_FILE_NAME_PATTERN en GenerateRenditions.php se hizo pública para permitir a los desarrolladores más flexibilidad cuando trabajan con representaciones de imágenes. La corrección se incluye en Magento 2.4.9-alpha3 con unidad completa y cobertura de prueba de integración.

_AC-15338 - [Problema de GitHub](https://github.com/magento/magento2/issues/39733) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### El método de envío incorrecto se muestra en la página de pedido de revisión para envíos múltiples

Se ha corregido un problema en el cierre de compra de varios envíos en el que la página de revisión de pedidos mostraba un coste de envío incorrecto (5 INR en lugar de 10 INR); la actualización garantiza que se muestre la cantidad de envío correcta para cada dirección.

_AC-15664 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3cf1a106)_

#### error de bin/magento config:show(o set) design/theme/theme_id

Se corrigió un problema en el cual los comandos de CLI bin/magento config:show y config:set fallaban en la ruta design/theme/theme_id a pesar de que la configuración estaba presente.
Ahora, los comandos se ejecutan correctamente y permiten ver y establecer el ID de tema sin errores.

_AC-5915 - [Problema de GitHub](https://github.com/magento/magento2/issues/35751) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### No se puede cargar la imagen con una anchura relativamente pequeña

El sistema ya no deja de cambiar el tamaño de la imagen con una anchura relativamente pequeña a su altura.

_ACP2E-3558 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### El componente Producto del Page Builder no funciona si el usuario no tiene permiso de Widget

Antes de la corrección, al acceder a un widget sin permisos, la página generaba un error genérico y mostraba un GIF de &quot;carga&quot;. Ahora, después de la corrección, se muestra una ventana modal con &quot;Lo sentimos, necesita permisos para ver este contenido&quot;. Mensaje.

_ACP2E-3664 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Ruta de configuración incorrecta para la configuración de estilo de ruta de almacenamiento remoto

Después de la corrección, establecer la configuración de estilo de ruta de almacenamiento remoto afectará a la configuración real del estilo de ruta de AWS S3.

_ACP2E-3734 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### El orden de los widgets del producto de Page Builder no se aplica en GraphQL

Corrige el problema en el cual la respuesta de consulta &quot;ruta&quot; de GraphQL no devolvía productos en el orden correcto dentro de un tipo de contenido de productos de Page Builder.

_ACP2E-3898 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problema de visualización de precios en tiendas que no están en inglés debido a la versión de la biblioteca de la UCI

Después de la corrección, el precio del producto se muestra correctamente en la configuración regional hebrea (Israel).

_ACP2E-3938 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Actualizando configuración de diseño de código de tienda borrado

Corrige el problema por el que al actualizar el código de vista de tienda se borraban los ajustes de Configuración de diseño debido a que la caché de configuración no se actualizaba correctamente.

_ACP2E-3941 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### La previsualización de ensayo de contenido no funciona con los resultados de búsqueda

La búsqueda en la vista previa de ensayo ahora devuelve productos según el ámbito seleccionado. Anteriormente, la búsqueda devolvía resultados en el ámbito predeterminado, sin tener en cuenta el almacén seleccionado.

_ACP2E-4095_

#### Page Builder: problema de lógica de condición de producto (la lógica OR se comporta incorrectamente al mostrar menos productos)

El widget de productos del generador de páginas ahora devuelve el resultado correcto cuando se utiliza un atributo con ámbito global en la condición &quot;Coincidir con cualquiera&quot;

_ACP2E-4096 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### El carrusel de productos añade productos incorrectos a Page Builder

Antes de la corrección, se habría incluido automáticamente un producto configurable en los listados de carrusel de productos de PageBuilder si alguno de sus elementos secundarios hubiera cumplido las condiciones de filtrado. Ahora, después de la corrección, el producto principal se incluirá solo si el producto secundario no es visible por sí solo.

_ACP2E-4341 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### El widget de lista de productos devuelve un resultado incorrecto si se enumeran varias categorías en la condición de categoría

El widget &quot;Lista de productos del catálogo&quot; ahora mostrará resultados precisos cuando varias categorías enumeradas en la condición &quot;Categoría es una de&quot;. Anteriormente, solo se procesaba la primera categoría de la lista.

_ACP2E-4353 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### La creación de carpetas de la Galería multimedia de [Cloud] requiere el permiso delete_folder en la Galería de nuevos medios. Los roles que solo tengan create_folder no pueden crear carpetas

Anteriormente, antes de que esta corrección se implementara, un usuario administrador con solo permiso de creación de carpeta de contenido no podía crear una carpeta en la galería de medios de CMS. Sin embargo, después de la corrección, los creadores de contenido de la galería de medios ahora pueden crear carpetas con solo el permiso Crear carpeta.

_ACP2E-4376 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### [QUANS] duplicando una página de CMS

Antes de esta corrección, habría fallado la duplicación de una página de cms con actualización de diseño personalizada. Ahora, las páginas de CMS con actualizaciones de diseño personalizadas se pueden duplicar sin errores.

_ACP2E-4449 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Los administradores con permisos de nivel de sitio web no pueden editar Dynamic Block

Ahora, los usuarios administradores con permisos de ámbito de sitio web pueden editar el contenido de los titulares en vistas almacenadas accesibles.

_ACP2E-4468_

### Cliente/ Clientes

#### Excepción en Storefront cuando el administrador agrega el bloque CustomerCustomAttribute a través del contenido de la página de CMS

Se ha corregido un problema que causaba que, al agregar el bloque CustomerCustomAttribute a través del contenido de la página CMS, se produjera una excepción en la tienda que impedía que se cargara la página.
Storefront ahora se muestra con normalidad y muestra un mensaje significativo cuando el contenido no se puede procesar, lo que evita errores críticos.

_AC-11004_

#### Los clientes ahora en línea Cuadrícula de administración muestra filas duplicadas cada vez que un usuario inicia sesión, luego cierra y luego inicia sesión

Se ha corregido un problema en el cual la cuadrícula de administración Clientes ahora en línea mostraba filas duplicadas cuando un cliente cerraba la sesión y volvía a iniciarla.
La cuadrícula ahora actualiza el registro existente con la última actividad en lugar de crear entradas duplicadas, lo que garantiza un seguimiento preciso de la sesión del cliente.

_AC-11511 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### La validación del valor mínimo y máximo no funciona para el atributo DOB en Storefront

Este error corrigió un problema en el cual la validación de fechas mínima y máxima del atributo de fecha de nacimiento (DOB) no funcionaba en la tienda (aunque sí en el administrador).
En 2.4.9-alpha3, la validación ahora bloquea correctamente el guardado de clientes con DOB fuera del rango permitido, mostrando un mensaje de error.

_AC-13535 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Error de carga de Ajax 401 en la pantalla de advertencia del panel de administración al revocar el permiso de Iniciar sesión como cliente

Este error ha corregido un problema por el que un permiso revocado de Iniciar sesión como cliente provocaba que apareciera un error de Ajax 401 con HTML sin procesar en la ventana emergente de advertencia.
Después de la corrección, el sistema ahora muestra correctamente un mensaje de advertencia normal en lugar de HTML sin procesar.
La solución se entregó en Magento 2.4.9-alpha3

_AC-15336 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

### Marco

#### Código de finalización del módulo deshabilitado.

Esta solicitud de extracción ha desactivado los módulos antes de la compilación del código.

_AC-10933 - [Problema de GitHub](https://github.com/magento/magento2/issues/38241) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39723)_

#### Error al ejecutar el comando setup:upgrade con el déclencheur de BD personalizado

Los déclencheur personalizados de base de datos ya no causan errores durante la instalación :upgrade.
Anteriormente, si se ejecutaba el programa de instalación de bin/magento :upgrade con un déclencheur de base de datos personalizado (por ejemplo, DESPUÉS DE INSERTAR en la tabla de almacenamiento), se podía producir el siguiente error:
&quot;Advertencia: Intentando acceder al desplazamiento de la matriz en el valor de tipo nulo en vendor/magento/framework/Mview/View/Subscription.php en la línea 357&quot;
AC-11487

_AC-11487: [problema de GitHub](https://github.com/magento/magento2/issues/38481)_

#### [Problema] Hacer que la firma del método sea coherente con la interfaz

La firma del método para getAttributes ahora es coherente con su interfaz, lo que evita cualquier error al sobrescribir el método. Anteriormente, las incoherencias en la firma del método provocaban errores al intentar sobrescribir el método getAttributes.

_AC-11578 - [Problema de GitHub](https://github.com/magento/magento2/issues/38501) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31955)_

#### El formulario de entidad de sitio web/grupo/tienda no se puede ampliar con varios elementos de formulario de valor para atributos de extensión

Esta PR permite que los elementos de formulario de varios valores envíen datos al sitio web, al grupo o al formulario de tienda.

_AC-11657 - [Problema de GitHub](https://github.com/magento/magento2/issues/24070) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problema]: Corrija la regla validate-emails para el componente ui.

El sistema ahora valida correctamente varias direcciones de correo electrónico introducidas en los componentes de la interfaz de usuario, asegurándose de que cada correo electrónico se recorta y valida correctamente. Anteriormente, el sistema utilizaba un método incorrecto para recortar las direcciones de correo electrónico, lo que podía provocar errores de validación.

_AC-11719 - [Problema de GitHub](https://github.com/magento/magento2/issues/38528) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problema] Quitar uso de resolución de ámbito

Esta PR resuelve la configuración de la URL de administración de forma global en lugar de la tienda actual

_AC-11736 - [Problema de GitHub](https://github.com/magento/magento2/issues/38566) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38554)_

#### [Problema]: quite métodos redundantes

Calidad del código: se han eliminado los métodos redundantes en los componentes de operaciones asincrónicas y ventas que solo llamaban a métodos principales sin agregar funcionalidad, lo que mejora la capacidad de mantenimiento del código.

_AC-11915 - [Problema de GitHub](https://github.com/magento/magento2/issues/29748) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/29147)_

#### Plantilla Magento_Theme title.phtml no válida para PHP 8.2

Esta solicitud de extracción corrige un problema cuando la página de CMS creada con el encabezado nulo como en Php 8.x que pasa nulo a trim() emite una excepción: Funcionalidad obsoleta: trim(): Pasar nulo al parámetro #1 ($string) de tipo cadena

_AC-12856 - [Problema de GitHub](https://github.com/magento/magento2/issues/39092) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39398)_

#### la validación xsd falla en los archivos etc/adminhtml/system.xml que contienen comentarios debajo de los elementos de campo.

Esta PR corrige las definiciones de esquema XML en phpstorm para el nodo de comentarios

_AC-12945 - [Problema de GitHub](https://github.com/magento/magento2/issues/39148) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39867)_

#### Exposición de la versión de Magento a través de la ruta de instalación con la configuración predeterminada de Nginx

El sistema funciona ahora según lo esperado y no expone la versión exacta de Magento que está ejecutando el sitio

_AC-13205 - [Problema de GitHub](https://github.com/magento/magento2/issues/39227) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problema] Desempaqueta argumentos de objeto como parámetros con nombre

El sistema ahora utiliza la función PHP 8.1 de desempaquetar matrices con parámetros con nombre, lo que elimina la necesidad de llamadas array_values y mejora potencialmente el rendimiento general. Anteriormente, el sistema requería que array_values llamara a desempaquetar argumentos de objeto.

_AC-13210 - [Problema de GitHub](https://github.com/magento/magento2/issues/39233) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37411)_

#### [Problema] dirección de presupuesto de refactorización no valida el método

Esta PR incluye mejoras de legibilidad para el método doValidate.

_AC-13214 - [Problema de GitHub](https://github.com/magento/magento2/issues/38230) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38219)_

#### Opción de Magento: ¿magento-init-params nunca se utiliza al ejecutar cli?

La opción —magento-init-params ahora se usa cuando se ejecutan comandos CLI.
Anteriormente, pasar —magento-init-params a comandos CLI no tenía ningún efecto en parámetros como MAGE_MODE.
AC-13231

_AC-13231 - [Problema de GitHub](https://github.com/magento/magento2/issues/39248) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### declaración de tipo incorrecta de getItemsByColumnValue

El sistema ahora define correctamente el parámetro de entrada $value como un tipo primitivo, no como una matriz, en la función getItemsByColumnValue, asegurándose de que la función devuelve la colección esperada. Anteriormente, si se utilizaba una matriz con un único valor como parámetro de entrada, la función devolvía null y los IDE la marcaban como error.

_AC-13240 - [Problema de GitHub](https://github.com/magento/magento2/issues/33070) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33120)_

#### Al utilizar el almacenamiento de archivos para el proveedor de bloqueos, obtenemos un directorio de archivos cada vez más grande sin que se produzca ninguna limpieza

Esta solicitud de extracción presenta un nuevo trabajo de crono que se ejecuta una vez al día y busca archivos de bloqueo que no se hayan modificado en las últimas 24 horas y que, por lo tanto, se pueden eliminar de forma segura. Esto mantendrá el contenido del directorio de archivos de bloqueo bajo control.
Este cronjob solo ejecutará algo cuando el proveedor de bloqueo esté configurado para usar archivos, no cuando se use uno de los otros (base de datos - el predeterminado, el zookeeper o la caché)

_AC-13367 - [Problema de GitHub](https://github.com/magento/magento2/issues/39369) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39372)_

#### Limpieza de [problema]: no use el valor devuelto nulo de las llamadas a métodos.

Esta PR realiza una limpieza menor. A veces llamamos a métodos que no devolvían nada (void) y luego usamos ese valor de resultado. Lo cual no es necesario.

_AC-13664 - [Problema de GitHub](https://github.com/magento/magento2/issues/39524) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39516)_

#### Claves de caché asociadas con FPC en implementaciones de varias tiendas de Magento 2.4.7

Se ha corregido un problema en el cual las claves de caché de caché de página completa (FPC) en configuraciones de varias tiendas no incluían MAGE_RUN_CODE ni MAGE_RUN_TYPE, lo que provocaba un comportamiento incoherente de la clave de caché en comparación con versiones anteriores. Las claves de caché ahora incluyen correctamente el contexto de la tienda, lo que garantiza un aislamiento adecuado de la caché en todas las tiendas.

_AC-13719 - [Problema de GitHub](https://github.com/magento/magento2/issues/39456) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problema] [PHPDOC] Corregir phpdoc incorrecto para Magento\Framework\Message\ManagerInterface

Esta PR corrige el phpdoc incorrecto para \Magento\Framework\Message\ManagerInterface y elimina todos los phpdoc duplicados en \Magento\Framework\Message\Manager (utiliza sintaxis inheritdoc).

_AC-14312 - [Problema de GitHub](https://github.com/magento/magento2/issues/39593) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39153)_

#### La indexación parcial deja de funcionar para los clientes con un gran número de actualizaciones

La indexación parcial ahora funciona para clientes con un gran número de actualizaciones.
Anteriormente, alcanzar el valor máximo de la columna version_id en la tabla changelog provocaba que se detuvieran las actualizaciones de índice.
AC-14424

_AC-14424 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 utiliza paquetes dev que no siguen el control de versiones semántico

Magento 2.4.8 requiere versiones dev de pdepend/pdepend y phpmd/phpmd (3.x-dev) para compatibilidad con PHP 8.4.
Estas versiones de desarrollo entran en conflicto con las herramientas de terceros que esperan paquetes compatibles con SemVer, lo que impide algunas actualizaciones.
Una solución temporal consiste en alias de las versiones de desarrollo en composer.json (por ejemplo, &quot;3.x-dev as 3.99.0&quot;), lo que permite la compatibilidad al tiempo que satisface las versiones semánticas.
Esto garantiza la compatibilidad con PHP 8.4 y evita conflictos hasta que haya versiones estables disponibles.

_AC-14519: [problema de GitHub](https://github.com/magento/magento2/issues/39796)_

#### Después de descargar la etiqueta de envío, podemos ver algunos importes de envío que no coincidían con el precio de envío y manipulación.

Los importes de las etiquetas de envío ahora coinciden con los precios de envío y manipulación.
Anteriormente, después de descargar una etiqueta de envío, la cantidad mostrada no coincidía con el precio de envío y manipulación.
AC-14560

_AC-14560_

#### El mecanismo MView ignora silenciosamente los errores en la ejecución del déclencheur

Ahora, el mecanismo MView informa correctamente de los errores en la ejecución del déclencheur.
Anteriormente, los errores durante la ejecución de la déclencheur se ignoraban silenciosamente, lo que podía provocar la falta de actualizaciones de índice sin ninguna notificación.
AC-14567

_AC-14567 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### [Problema] Evite muchas excepciones innecesarias durante la carga de la combinación XML de diseño

Esta PR introduce una nueva función (para B/C compat no sobrescribimos el _loadXmlString protegido) para cargar y no iniciar una excepción

_AC-14580 - [Problema de GitHub](https://github.com/magento/magento2/issues/39877) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37570)_

#### [Problema] Use la promoción de propiedad de constructor en el módulo Gráfico Ql de Vault

Esta PR reemplaza las propiedades del constructor con la promoción de propiedades en el módulo VaultGraphQl

_AC-14616 - [Problema de GitHub](https://github.com/magento/magento2/issues/39900) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36996)_

#### [Problema] eliminó la redundancia de código para los diseños de front-end del módulo.

Esta PR elimina la redundancia de código en los diseños de temas para los módulos de front-end Magento_Msrp, Magento_LoginAsCustomerAssistance, Magento_Newsletter y Magento_Sitemap.

_AC-14625 - [Problema de GitHub](https://github.com/magento/magento2/issues/30673) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30644)_

#### [Problema] incluye el constructor para que forme parte de la API `CommandListInterface` y amplía la documentación en línea

Esta actualización PR marca Magento\Framework\Console\CommandList como una API e introduce el constructor en CommandListInterface para mejorar la extensibilidad. También mejora la documentación en línea para mejorar la claridad y la capacidad de mantenimiento de los desarrolladores que amplían los comandos de la consola.

_AC-14680 - [Problema de GitHub](https://github.com/magento/magento2/issues/31102) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37901)_

#### [Problema] Elimina el código relacionado con Microsoft IIS

Esta PR limpia el código relacionado con Microsoft IIS según la documentación de requisitos del sistema de Magento, que indica que el sistema operativo Microsoft Windows no es compatible

_AC-14702 - [Problema de GitHub](https://github.com/magento/magento2/issues/39910) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39894)_

#### Error de sintaxis de Magnifier.js

La funcionalidad del Ampliador del sistema debe seguir funcionando como antes y magnifierOptions no debe estar disponible en el ámbito global

_AC-14722 - [Problema de GitHub](https://github.com/magento/magento2/issues/36200) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39321)_

#### Modo detallado de Backport en el comando CLI `setup:db:status`

El comando CLI `setup:db:status` ahora admite el modo detallado.
Anteriormente, era difícil comprender los cambios en la base de datos necesarios para las actualizaciones. Ahora, al ejecutar `bin/magento setup:db:status -v` se proporciona información detallada acerca de las diferencias de esquema y de datos.
AC-14807

_AC-14807 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Envío de correo SMTP con tls y 2.4.8

El envío de correo electrónico SMTP con TLS ahora funciona según lo esperado.
Anteriormente, al enviar correos electrónicos a través de SMTP con TLS se producía el siguiente error: error:1408F10B:Rutinas SSL:ssl3_get_record:número de versión incorrecto.
AC-14883

_AC-14883 - [Problema de GitHub](https://github.com/magento/magento2/issues/39947) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problema]: corrija el problema de concurrencia en la implementación de contenido estático

Esta PR corrige un error en el que varios procesos simultáneos giran para gestionar el mismo paquete de temáticas, según cómo se definan las temáticas con sus elementos principales.

_AC-14944 - [Problema de GitHub](https://github.com/magento/magento2/issues/39990) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problema] Elimina el código de compatibilidad heredado para las versiones de PHP &lt; 8.1

Esta solicitud de extracción elimina el código diseñado para ejecutarse en PHP &lt;8.1.
Además, se ha eliminado la comprobación de la disponibilidad del contacto PHP_VERSION_ID, ya que está disponible en todas las versiones de PHP

_AC-14971 - [Problema de GitHub](https://github.com/magento/magento2/issues/39891) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39882)_

#### FPC no funciona al iniciar sesión

Caché de página completa (FPC) ahora funciona correctamente para los clientes que iniciaron sesión.
Anteriormente, después de iniciar sesión, la página de inicio no se cargaba desde la caché y el encabezado x-magento-cache-debug mostraba MISS en lugar de HIT.
AC-14999

_AC-14999: [problema de GitHub](https://github.com/magento/magento2/issues/40007)_

#### Agregue tipos genéricos en ciertas clases php para mejorar el soporte del análisis estático

El sistema ahora utiliza la definición de tipo genérico para mejorar esto de forma significativa al interpretarla como la clase exacta que devuelve una llamada de método

_AC-15013 - [Problema de GitHub](https://github.com/magento/magento2/issues/40017) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40119)_

#### [Problema] mejora la administración de errores en SchemaBuilder

Esta PR mejora la gestión de mensajes de error del esquema de la base de datos. Nos ayuda a identificar el problema sin una depuración pesada.

_AC-15020 - [Problema de GitHub](https://github.com/magento/magento2/issues/39816) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39799)_

#### API de REST: Llamada a una función de miembro getVideoProvider() en nulo

Se ha corregido un problema en el cual llamar a la API secundaria configurable de productos devolvía un error de servidor interno 500 si un producto secundario solo tenía un vídeo de YouTube y ninguna otra imagen.
El error se debe a una referencia nula en ExternalVideoEntryConverter.
Ahora, la API devuelve correctamente productos secundarios con entradas de la galería de medios, incluidos datos de vídeo externos, sin arrojar errores.
Esto garantiza la recuperación adecuada de todos los tipos de medios para los productos secundarios a través de la API de REST.

_AC-15046: [problema de GitHub](https://github.com/magento/magento2/issues/40021)_

#### [W3C] Quitar texto/javascript de la declaración de etiqueta de script de cookie

Esta PR ha eliminado el atributo type=&quot;text/javascript&quot; innecesario de la etiqueta de script de la cookie para la conformidad con HTML5.

_AC-15061 - [Problema de GitHub](https://github.com/magento/magento2/issues/39982) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39983)_

#### [Problema] Corrija algunos errores tipográficos en los comentarios de PHPDoc

Esta PR corrige los pocos errores tipográficos en el phpdoc

_AC-15075 - [Problema de GitHub](https://github.com/magento/magento2/issues/40042) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38809)_

#### [Problema] Elimina el uso de sprintf en las llamadas de frases

Esta PR elimina el uso de sprintf en la llamada de función de frase del núcleo de Magento.

_AC-15183 - [Problema de GitHub](https://github.com/magento/magento2/issues/40050) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40033)_

#### No se pueden reindexar todos los elementos no válidos en indexadores de varios subprocesos con bloqueo de aplicación activo

Este problema solucionaba un error en el indizador de subprocesos múltiples cuando use_application_lock estaba habilitado.
Anteriormente, los bloqueos de la base de datos se perdían durante el procesamiento paralelo, lo que provocaba que los indexadores permanecieran en el estado &quot;funcionando&quot; y lanzaran errores de SQL (no se encontró la tabla).
En Magento 2.4.9-alpha3, la corrección garantiza que los indexadores se reindexen correctamente con el bloqueo de la aplicación habilitado.

_AC-15270 - [Problema de GitHub](https://github.com/magento/magento2/issues/40102) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Tipos de valor devuelto no claros o no válidos en Magento\Framework\Escaper

El sistema aceptará tipos para métodos de escape cuando se realice el análisis estático usando phpstan en el nivel 5

_AC-15272 - [Problema de GitHub](https://github.com/magento/magento2/issues/40012) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40114)_

#### [Problema] Permite que la configuración específica de la cola supere el valor predeterminado de mensajes máximos

El sistema ahora permite que la configuración específica de la cola supere el valor predeterminado de mensajes máximos

_AC-15284 - [Problema de GitHub](https://github.com/magento/magento2/issues/40121) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40110)_

#### [Problema]: memoria caché fpc duplicada para la misma página con la misma consulta al usar barniz

Esta PR corrige entradas de caché de página completa duplicadas cuando se usa Varnish. Normaliza el orden de los parámetros de consulta y garantiza claves de caché coherentes para solicitudes idénticas.
Mejora el ratio de aciertos de caché y el rendimiento para las direcciones URL con los mismos parámetros en diferentes secuencias.

_AC-15325 - [Problema de GitHub](https://github.com/magento/magento2/issues/39706) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39704)_

#### Los temas de la comunidad contienen recursos para los módulos de edición de Commerce

Se han eliminado los recursos de estilo solo de Commerce de las temáticas de la comunidad reubicándolos en sus respectivos directorios de módulos. Esto evita que el CSS no utilizado se incluya en la edición comunitaria, lo que reduce la carga útil innecesaria y elimina las reglas de estilo muerto, a la vez que garantiza un estilo adecuado cuando los módulos Commerce están habilitados.

_AC-15347 - [Problema de GitHub](https://github.com/magento/magento2/issues/21446) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9bcd880a)_

#### [Problema] Añadir código de tienda a las direcciones URL debe ser global

Esta PR soluciona el problema asegurándose de que la configuración &quot;Añadir código de tienda a las URL&quot; se recupera usando el ámbito global en el código principal

_AC-15365 - [Problema de GitHub](https://github.com/magento/magento2/issues/40069) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40065)_

#### [Problema] registra el complemento no declarado solo si no está deshabilitado

Esta PR corrige y registra el complemento que no está declarado y no se utiliza (habilitado y sin instancia).

_AC-15386 - [Problema de GitHub](https://github.com/magento/magento2/issues/40086) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40081)_

#### [Problema] Limpieza pequeña, se eliminaron las claves duplicadas de la matriz

El sistema ahora realiza una pequeña limpieza y No se ha encontrado ningún error relacionado con la matriz tiene 2 claves duplicadas con el valor &quot;Weight (and above)&quot;

_AC-15414 - [Problema de GitHub](https://github.com/magento/magento2/issues/39851) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework versión 103.0.8-p2: La clase EmailMessage llama a un método inexistente

La clase EmailMessage ahora gestiona correctamente la recuperación del cuerpo del correo electrónico.
Anteriormente, en Magento 2.4.8-p2 con magento/framework versión 103.0.8-p2, la clase Magento\Framework\Mail\EmailMessage intentaba llamar a un método inexistente (getTextBody) en el objeto de mensaje de correo Symfony. Esto provocaba errores cuando los módulos o personalizaciones de terceros dependían de este método para el procesamiento de correo electrónico.
Ahora, la clase EmailMessage ya no llama a métodos indefinidos para evitar estos errores. AC-15446

_AC-15446 - [Problema de GitHub](https://github.com/magento/magento2/issues/40170) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Parches de datos/esquemas getAliases() causa errores durante `setup:upgrade`

getAliases() causa errores durante la instalación :upgrade, este PR corrige lo mismo

_AC-15559 - [Problema de GitHub](https://github.com/magento/magento2/issues/31396) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38239)_

#### Combinación no válida de intercalaciones para la operación

_AC-15614 - [Problema de GitHub](https://github.com/magento/magento2/issues/40138) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs()

Esta PR actualiza el PHPDoc para \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs() para reflejar correctamente que el parámetro $alias puede ser nulo además de cadena. Esto resuelve los problemas de PHPStan en el nivel 5+ y mejora la compatibilidad de herramientas de calidad de código.

_AC-15626 - [Problema de GitHub](https://github.com/magento/magento2/issues/39598) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39581)_

#### Combinación no válida de intercalaciones en el módulo urlrewrite

_AC-15647 - [Problema de GitHub](https://github.com/magento/magento2/issues/40189) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/44329e9d)_

#### La condición nunca se cumplió en `\Magento\Framework\Escaper::escapeScriptIdentifiers`

Se ha corregido una condición inaccesible en \Magento\Framework\Escaper::escapeScriptIdentifiers reemplazando la comprobación de false por null, alineándola con los valores de retorno preg_replace y mejorando la precisión del código sin afectar a la funcionalidad.

_AC-15667 - [Problema de GitHub](https://github.com/magento/magento2/issues/40195) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### Barniz 7.3 (última versión)- Los enlaces de subcategorías / opciones de la categoría por defecto no se muestran en la portada de la tienda

Se ha confirmado que los vínculos de subcategoría que faltaban en la página principal de la tienda al usar Varnish 7.3 se debían a la administración de solicitudes de ESI y a la configuración del servidor en lugar de a un defecto de código de Magento; el problema se resuelve mediante los ajustes de configuración recomendados de Varnish, sin que se requieran cambios en el código principal.

_AC-15674 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3cf1a106) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9a62604c)_

#### [Problema] Agregar datos de depuración adicionales al registro `cache_invalidate`

Esta PR mejoró el registro cache_invalidate para incluir el contexto de la solicitud y el seguimiento de pila para las purgas de caché completas, lo que mejoró la depuración y la visibilidad.
Esto ayuda a identificar el origen de las invalidaciones de caché completas inesperadas sin cambiar la funcionalidad existente.

_AC-15719 - [Problema de GitHub](https://github.com/magento/magento2/issues/40204) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40196)_

#### [Problema] mejoró un poco la lista de exclusión de autocargadores del compositor.

Este PR refina las exclusiones del autocargador Composer para omitir clases de prueba, reduciendo entradas de mapa de clase innecesarias y evitando advertencias de PSR-4.

_AC-15743 - [Problema de GitHub](https://github.com/magento/magento2/issues/40109) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40107)_

#### [Problema] impide que las declaraciones de `db_schema.xml` con `comment=""` rompan las implementaciones de tiempo de inactividad cero

El sistema ahora evita que las declaraciones db_schema.xml con comment=&quot;&quot; rompan las implementaciones de tiempo de inactividad cero

_AC-15980 - [Problema de GitHub](https://github.com/magento/magento2/issues/40254) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40242)_

#### No se puede borrar la caché de `\Magento\Framework\Filesystem\Glob::glob(...)`

Esta actualización PR introduce una forma de borrar la caché estática interna utilizada por \Magento\Framework\Filesystem\Glob, lo que garantiza resultados nuevos y precisos cuando cambian las estructuras de archivos. Mejora la fiabilidad y la experiencia del desarrollador, especialmente en escenarios de prueba y procesos de larga duración en los que los resultados de glob deben estar actualizados.

_AC-15989 - [Problema de GitHub](https://github.com/magento/magento2/issues/35741) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35742)_

#### La URL del vínculo LeerME Leaders tiene una redirección permanente

Se ha actualizado el vínculo LÉAME - Líderes reemplazando la dirección URL permanentemente redirigida y caducada por vínculos de trabajo correctos, lo que garantiza que las páginas de los colaboradores y administradores se abran correctamente.

_AC-16046 - [Problema de GitHub](https://github.com/magento/magento2/issues/40292) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

Se corrigieron las anotaciones PHPDoc para joinLeft() en la colección de atributos para permitir definiciones de matrices adecuadas, mejorando la corrección del código y la compatibilidad con herramientas como PHPStan.

_AC-16187 - [Problema de GitHub](https://github.com/magento/magento2/issues/40354) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39155)_

#### Asegúrese de que un solo error de comando registra el error (archivo o stderr) sin detener la ejecución de los comandos CLI subsiguientes.

El sistema ahora Asegúrese de que un solo error de comando registra el error (archivo o stderr) sin detener la ejecución de los comandos CLI subsiguientes

_AC-16244 - [Problema de GitHub](https://github.com/magento/magento2/issues/40006) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40063)_

#### [Problema] Agregar tipo int a $maxAge en el kernel de PageCache

Esta PR garantiza que el parámetro $maxAge del kernel de PageCache esté estrictamente escrito como un entero para mejorar la seguridad de tipos y evitar errores de análisis estático/PHPStan en la administración de caché.

_AC-16313 - [Problema de GitHub](https://github.com/magento/magento2/issues/40438) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36600)_

#### Los módulos falsos requieren desarrollo/ directorio en repositorios de extensiones

_AC-16487_

#### Añadir al carrito evento : precios vacíos

Se ha corregido un problema por el cual los precios de productos se devolvían como nulos en el observador de eventos checkout_cart_product_add_after durante el proceso de añadir al carro de compras.
Ahora, el precio base y los valores de precio relacionados se recuperan correctamente, lo que garantiza que haya datos precisos disponibles para observadores e implementaciones personalizadas.

_AC-5966 - [Problema de GitHub](https://github.com/magento/magento2/issues/35638) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### Corrección de errores de tipo PHP8.1

Los productos asociados ahora se inicializan en una matriz vacía en lugar de en false cuando el modo de procesamiento estricto no está activo o cuando la información del producto está disponible. Este cambio garantiza que la lógica subsiguiente que maneja los productos asociados se comporte de manera consistente, mejorando la estabilidad y la previsibilidad en el proceso de preparación del producto.

_AC-6017 - [Problema de GitHub](https://github.com/magento/magento2/issues/35808) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35842)_

#### Tipo esperado &#39;Magento\Customer\Api\Data\GroupInterface&#39;. Se ha encontrado &#39;Magento\Customer\Model\Group&#39;.

Se ha corregido un problema por el cual al guardar un grupo de clientes a través de GroupRepositoryInterface mediante GroupFactory se producía un error de tipo.
Anteriormente, el repositorio esperaba GroupInterface, pero se pasaron las instancias del modelo Group, lo que provocó un error grave.
Ahora, los grupos de clientes se pueden guardar correctamente a través del repositorio asegurando la correcta implementación de la interfaz.
Esto resuelve las advertencias del IDE y los errores de tiempo de ejecución al crear o actualizar mediante programación grupos de clientes.

_AC-6909 - [Problema de GitHub](https://github.com/magento/magento2/issues/36269)_

#### Validación de campos en abonos

Se ha corregido un problema por el cual la validación de campos en la página de nota de crédito impedía el envío incluso después de rellenar los campos personalizados obligatorios.
Ahora, la validación funciona correctamente y el botón de envío está habilitado una vez completados todos los campos obligatorios.

_AC-8308 - [Problema de GitHub](https://github.com/magento/magento2/issues/37182) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### [Problema] Quitar la etiqueta `@author` prohibida del marco de trabajo (parte 3)

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8343 - [Problema de GitHub](https://github.com/magento/magento2/issues/37270) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problema] Use la promoción de la propiedad de constructor en el módulo Enviar gráfico de amigos SQL

El sistema ahora utiliza la promoción de la propiedad constructora en el módulo GraphQL &quot;enviar amigo&quot;, lo que mejora la legibilidad del código y reduce la complejidad. Anteriormente, el módulo utilizaba propiedades que ocupaban numerosas líneas, lo que hacía que el código fuera más complejo y menos legible.

_AC-8346 - [Problema de GitHub](https://github.com/magento/magento2/issues/37235) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8349 - [Problema de GitHub](https://github.com/magento/magento2/issues/37266) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8350 - [Problema de GitHub](https://github.com/magento/magento2/issues/37265) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problema] Elimina la etiqueta `@author` prohibida de `Magento_Downloadable`

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8355 - [Problema de GitHub](https://github.com/magento/magento2/issues/37251) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad y coherencia del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8358 - [Problema de GitHub](https://github.com/magento/magento2/issues/37264) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8359 - [Problema de GitHub](https://github.com/magento/magento2/issues/37262) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8360 - [Problema de GitHub](https://github.com/magento/magento2/issues/37261) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8361 - [Problema de GitHub](https://github.com/magento/magento2/issues/37260) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8362 - [Problema de GitHub](https://github.com/magento/magento2/issues/37259) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8363 - [Problema de GitHub](https://github.com/magento/magento2/issues/37258) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37008)_

#### [Problema] Elimina la etiqueta `@author` prohibida de `Magento_Backup` y `Magento_Bundle`

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8367 - [Problema de GitHub](https://github.com/magento/magento2/issues/37244) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36979)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8375 - [Problema de GitHub](https://github.com/magento/magento2/issues/37257) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37007)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8376 - [Problema de GitHub](https://github.com/magento/magento2/issues/37256) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37006)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8400 - [Problema de GitHub](https://github.com/magento/magento2/issues/37254) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37004)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8401 - [Problema de GitHub](https://github.com/magento/magento2/issues/37255) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37005)_

#### [Problema] que mejora la extensibilidad de la generación de URL del servicio

El sistema ahora permite la personalización de la función de generación de URL del servicio mediante complementos, lo que promueve un enfoque más mantenible de las modificaciones. Anteriormente, la personalización de esta función se lograba mediante preferencias, que pueden no haber sido tan eficientes o mantenibles.

_AC-8813 - [Problema de GitHub](https://github.com/magento/magento2/issues/37404) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37403)_

#### [Problema]: se corrigió el nombre de variable en la búsqueda de catálogos

El sistema ahora asigna un nombre correcto a las variables en el módulo del motor de búsqueda, lo que mejora la claridad y el mantenimiento del código. Anteriormente, se usaba un nombre de variable irrelevante, $defaultCountry, en el módulo del motor de búsqueda, lo que causaba confusión.

_AC-9215 - [Problema de GitHub](https://github.com/magento/magento2/issues/37810) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33533)_

#### allow_allel_generation debe configurarse mediante la variable de entorno

Después de la corrección, se puede utilizar la variable de entorno &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; para establecer la configuración &quot;allow_allel_generation&quot;.

_ACP2E-3673 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [Nube] Al cambiar el tipo de columna de tabla de Int a Decimal mediante el archivo db_schema.xml en Magento 2, se producen errores

Cambiar el tipo de datos de columna no funciona correctamente. Anteriormente, genera un error: No se permite el atributo &#39;identity&#39;.

_ACP2E-3709 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Nueva compatibilidad con moneda (XCG) en Adobe

Florín caribeño (XCG) se agrega a la lista de monedas.

_ACP2E-3790 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Problema con la actualización 2.4.7-p5 debido a la nueva validación añadida

Se ha corregido un problema en la clase SchemaBuilder por el que una clave de matriz indefinida &quot;column&quot; provocaba un bloqueo durante la creación o las actualizaciones del esquema. Esto ocurría al procesar datos de tabla que no incluían una clave de &quot;columna&quot;.

_ACP2E-3871 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### [QUANS]Problema de servidor causado potencialmente por clave de acceso S3 no válida

Las credenciales incorrectas de AWS S3 ya no hacen que las páginas se carguen infinitamente en la tienda.

_ACP2E-3890 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js no funciona

Los siguientes archivos JS se minifican ahora de forma completa y correcta cuando se habilita la minificación JS: mage/backend/tabs.min.j, jquery/jquery.validate.min.js y Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Como resultado, la validación del campo Clase CSS de Page Builder funciona según lo esperado.

_ACP2E-3925 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Error de obsolescencia de PHP8.4: E_USER_ERROR después de actualizar a Adobe Commerce 2.4.8

*NO SE REQUIEREN NOTAS DE LA VERSIÓN*
Los escenarios orientados al cliente no se ven afectados por la corrección.

_ACP2E-3963 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### El trabajo de cron no borra la tabla de la base de datos, lo que provoca una interrupción debido al bloqueo de Galera

La limpieza de tablas de registro de cambios se está ejecutando en lotes para evitar operaciones de eliminación pesadas.

_ACP2E-3995 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### JS no minificado a veces carga ignorando &quot;habilitar minificaciones de js&quot;

Antes de la corrección, incluso si tenía la minificación habilitada, algunos de los archivos JS se solicitaban sin el prefijo &quot;min&quot;, lo que resultaba en un código de estado 404. Después de la corrección, cuando la minificación está habilitada, no se solicitan recursos JS no minificados.

_ACP2E-4058 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### El atributo de fecha del grupo de atributos personalizado no muestra el selector de fecha en el administrador

Se ha corregido un problema por el cual la ventana emergente del calendario para los atributos de fecha aparecía fuera de pantalla cuando se asignaba a grupos de atributos personalizados.

_ACP2E-4060 - [Problema de GitHub](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### La comprobación del permiso de la ACL de producción ha causado una degradación del rendimiento - el método PopulateAcl es el cuello de botella

Procesamiento optimizado de reglas ACL

_ACP2E-4114 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### El Checkout no se carga en la última versión con AC-15867 + ACP2E-4296 y SCD compacto

Antes de la corrección, tener JavaScript personalizado cargado a través de la sección de encabezado podría haber causado problemas. Después de la introducción de la nueva configuración, estos scripts se pueden diferir automáticamente, lo que garantiza una mayor compatibilidad con el marco de trabajo de Magento 2.

_ACP2E-4319 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1c547060)_

#### Advertencia de obsolescencia: use moment.updateLocale(localeName, config) para cambiar una configuración regional existente. moment.defineLocale(localeName, config)

Antes de la corrección, se lanzaba una advertencia obsoleta en la consola del explorador. Ahora, después de la corrección, ya no se muestra esa advertencia.

_ACP2E-4338 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Error de [CLOUD] DateTimeZone al guardar los cambios del producto mediante la API de REST

Antes de la corrección, una solicitud de API de REST de actualización de producto generaba un error si no había ningún almacén con el código predeterminado. Ahora, después de la corrección, la solicitud de actualización del producto se ejecuta correctamente, independientemente de si existe o no una tienda &quot;predeterminada&quot;.

_ACP2E-4339_

#### Incompatibilidad con MariaDB 10.11

Anteriormente, se producía un error en la instalación de la última versión de Magento 2 al utilizar MariaDB 10.11, lo que impedía completar el proceso de instalación. Este problema se resolvió al actualizar el control de compatibilidad de bases de datos para admitir MariaDB 10.11.x durante la instalación.

_ACP2E-4367 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Marco de trabajo, Buscar

#### Opensearch 2.19.1 ilegal_argument_exception en categorías de un precio

Opensearch ya no está lanzando un ilegal_argument_exception en las categorías que contienen todos los productos con el mismo precio. Anteriormente, tiene esta excepción &quot;[del parámetro ] no puede ser negativo&quot;.

_ACP2E-3896 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Realizar un pedido en GraphQL se realiza correctamente con un método de envío no válido

Se ha corregido un problema en el cual los pedidos se podían realizar mediante GraphQL mediante un método de envío deshabilitado o no válido.
Ahora, el sistema valida el método de envío seleccionado y devuelve un error si no está disponible, lo que impide que se cree el pedido.

_AC-10472 - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38268) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Excepción al ejecutar la consulta de GraphQl

Se ha corregido un problema por el que una consulta de GraphQL arrojaba una excepción debido a un parámetro de ordenación no válido. Después de la corrección, la consulta se ejecuta correctamente sin generar errores ni registros de excepciones.

_AC-14835 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Error interno del servidor al añadir un producto de tarjeta de regalo al carro de compras mediante la mutación AddProductsToCart, incluido custom_attributesV2

Se ha resuelto un error de servidor interno que se activaba al añadir productos de tarjeta regalo (y opciones personalizadas similares) al carro de compras mediante GraphQL con custom_attributesV2; la corrección gestiona correctamente valores de atributos complejos, lo que permite agregar productos sin errores.

_AC-15856 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7fa400a7)_

#### Campos nulos en la consulta `Country`

Se ha corregido un problema que causaba que los pedidos que contenían artículos virtuales, reembolsados y enviados permanecieran en procesamiento, ya que se garantizaba que los artículos virtuales se incluyeran en los cálculos de cantidad enviada, lo que permitía que el estado del pedido pasara correctamente a completo.

_AC-7731 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La consulta GraphQL &quot;customerOrders&quot; con el atributo &quot;number&quot; provoca un error interno del servidor

Se ha corregido un problema en el cual la consulta GraphQL customerOrders devolvía un error interno del servidor al solicitar el campo de número.
Ahora, el solucionador devuelve correctamente el ID de incremento de pedido, lo que permite que la consulta se ejecute correctamente y recupere el número de pedido.

_AC-8949 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### La respuesta de GraphQL para la colocación de pedidos no incluye el mensaje de excepción

Se ha revertido el cambio anterior que devolvía errores en un formato diferente. Ahora los posibles errores se devuelven de forma coherente, sin romper el esquema de GraphQL. Debe agregarse como BIC conocido, aprobado por PM aquí: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-45248897

_ACP2E-3399 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### La respuesta de GraphQL para la colocación de pedidos está parcialmente localizada

Los errores devueltos por la mutación placeOrder GraphQl no se han localizado completamente. Ahora, en un contexto multilingüe, los errores se traducen correctamente.

_ACP2E-3506 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9608ca21)_

#### Llamadas simultáneas para reordenar la API de GraphQL: los mismos productos añadidos a filas diferentes

Corrige el problema en el cual las llamadas simultáneas a la API de Reordenar GraphQL hacen que los mismos productos se agreguen como filas diferentes, lo que provoca incoherencias en los datos.

_ACP2E-3774 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail La mutación de GraphQL (Cambiar dirección de correo electrónico) no almacena en déclencheur la notificación por correo electrónico

Anteriormente, el correo electrónico no se enviaba a los clientes después de actualizar correctamente sus direcciones de correo electrónico en sus cuentas. Una vez aplicada la corrección, los clientes ahora reciben notificaciones por correo electrónico después de actualizar correctamente sus direcciones de correo electrónico.

_ACP2E-3785 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### El atributo dinámico no se actualiza en el registro de regalos mediante la mutación updateGiftRegistry

Anteriormente, antes de esta corrección mediante la mutación updateGiftRegistry, el atributo personalizado del registro de regalos no se modificaba ni actualizaba mediante mutaciones de GraphQL. Después de aplicar esta corrección, el atributo dinámico del registro de regalos se puede actualizar correctamente mediante la mutación updateGiftRegistry.

_ACP2E-3805 - [Problema de GitHub](https://mcstaging.briscoes.co.nz/)_

#### customerOrders graphql devuelve un error cuando el producto se elimina

La solicitud de graphql customerOrders ya no genera un error incluso cuando se elimina el producto del pedido. Anteriormente, se producía el error &quot;Error interno del servidor&quot;.

_ACP2E-3936_

#### GraphQL de pedidos de clientes: recuperar las categorías de productos para el producto asociado &quot;no es visible de forma individual

Antes de la corrección, si el pedido contenía un producto oculto, sus categorías mostraban una matriz vacía en la respuesta de GraphQL de pedidos del cliente.
Ahora, después de la corrección, las categorías de productos se incluyen en la respuesta de una solicitud de GraphQL de pedido del cliente incluso si el producto está oculto.

_ACP2E-3945 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Los elementos de la lista de deseos no se comparten entre las vistas de tiendas de un sitio web en una solicitud de GraphQL

Antes de la corrección, los elementos de la lista de deseos se filtraban por ID de tienda. Ahora, después de la corrección, los elementos de la lista de deseos se filtran por sitio web.

_ACP2E-3987 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### [Cloud] getRemoteAddress devolvió 127.0.0.1 en producción

Antes de esta corrección, la dirección remota no se determinaba correctamente cuando se utilizaba el servidor de aplicaciones. Después de la corrección, la dirección remota se determina correctamente junto con la configuración del encabezado adecuada en nginx y la configuración del encabezado.

_ACP2E-3991 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### [QUANS] confirma la reversión del comportamiento de gestión de excepciones de colocación de pedidos GQL

Se ha corregido un cambio incompatible con versiones anteriores para la mutación placeOrder.

_ACP2E-4031 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Asignación de problemas del mensaje traducido al código de error al realizar el pedido mediante GraphQL

Se ha corregido un problema que se producía cuando se utilizaba un mensaje de excepción traducido para asignar el código de error para las solicitudes de GraphQL, lo que provocaba que se mostraran códigos de error desconocidos para los errores conocidos.

_ACP2E-4033 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### El filtro de pedidos de clientes de [CLOUD] no funciona para las fechas

Después de la corrección, la recuperación de pedidos a través de GraphQL mediante un filtro de intervalo de fechas devuelve el resultado correcto.

_ACP2E-4090 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Aborde los problemas planteados en ACP2E-4031

Antes de la corrección, la posición del nodo de error no proporcionaba una compatibilidad perfecta con las versiones 2.4.7 y 2.4.9. Ahora, después de la corrección, el nodo de error se coloca correctamente para adaptarse a ambas versiones.

_ACP2E-4115 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### Paquete principal que muestra Agotado incluso el elemento secundario tiene stock en la llamada de Graphql

Después de la corrección, al solicitar una lista de productos mediante GraphQL, se devuelve el estado de stock correcto para los productos agrupados.

_ACP2E-4168 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### Excepción de GraphQL en SWAT

Después de la corrección, las respuestas para solicitudes de GraphQL se alinean con las especificaciones de GraphQL sobre HTTP. Se devuelve un código de respuesta 4XX cuando es imposible analizar la solicitud, la solicitud no está autorizada o hay otro problema general con la solicitud. Si se analiza la solicitud y se puede procesar, se devuelve un código de respuesta 200.

_ACP2E-4194 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### El producto no se elimina de la lista de comparación una vez que la lista se ha asignado al cliente

Una vez que la lista de comparación de un usuario invitado se asigna a una cuenta de cliente, el cliente puede eliminar los productos añadidos como invitados.
Anteriormente, las operaciones de eliminación fallaban porque los elementos agregados por invitado no estaban correctamente vinculados a la cuenta del cliente después de la asignación.

_ACP2E-4244 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

#### Respuesta de error incorrecta de updateCartItems GraphQL

Anteriormente, cuando se realizaba una solicitud de graphQL para un artículo con cantidad insuficiente, se devolvía un mensaje de error correcto con un código de error, junto con la cantidad solicitada y el cálculo del precio, incluso si el artículo no estaba disponible. Después de aplicar esta corrección, ahora se devuelve un mensaje de error correcto con un código de error y la cantidad del artículo se establece en su valor antiguo si no está disponible en la respuesta.

_ACP2E-4283 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cbca0396)_

#### Error de asignación de pedidos de invitados entre sitios web en el complemento MergeGuestOrder

Antes de la corrección, una asignación de cliente de pedido invitado no estaba considerando opciones de uso compartido de cuentas. Ahora, después de la corrección, se asigna un pedido a un cliente si el cliente y el almacén de pedidos coinciden (dado que la opción de uso compartido de cuentas del cliente está establecida en &quot;Por sitio web&quot;).

_ACP2E-4312 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, inventario/MSI

#### Problema con only_x_left_in_stock en Magento 2 GraphQL: cálculo incorrecto al utilizar umbrales

Se ha corregido un problema en el cual el campo GraphQL only_x_left_in_stock devolvía nulo debido a una doble deducción incorrecta de MinQty; el cálculo se corrigió para que ahora devuelva el valor de stock preciso basado en los umbrales.

_AC-15832 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/35458c7f)_

#### Discrepancias en la mutación mergeCart de GraphQL

Después de la corrección, la solicitud de GraphQL de los carros de combinación comprueba correctamente la cantidad del producto, teniendo en cuenta la configuración de stock.

_ACP2E-4184 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Producto

#### Falta media_type de graphql del producto en MediaGalleryInterface

La solicitud de MediaGallery GraphQL ahora incluye el campo &quot;tipos&quot; para tipos de imagen de producto. Anteriormente, este campo &quot;tipos&quot; no existía en la solicitud de MediaGallery GraphQL.

_ACP2E-3880 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, Seguridad

#### El restablecimiento de la contraseña del cliente mediante GraphQL no cumple las restricciones

Se ha resuelto un problema en el cual las solicitudes de restablecimiento de contraseña de cliente realizadas a través de mutaciones de GraphQL no cumplían con las restricciones de restablecimiento de contraseña configuradas en Tienda > Configuración > Clientes > Configuración del cliente > Opciones de contraseña. Esta configuración ahora se aplica correctamente.

_ACP2E-3992 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importación/exportación

#### [Problema] Tipo de parámetro de corrección

Se ha corregido un error de coincidencia de tipos de parámetros en el módulo Importar/Exportar, en el que un valor previamente definido como cadena ahora se establece correctamente como matriz. Esto se ajusta a la entrada esperada del controlador de exportación y evita las advertencias del análisis estático.

_AC-11665 - [Problema de GitHub](https://github.com/magento/magento2/issues/38529) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### [Problema] Copyedit: cambiar &quot;copiar&quot; a &quot;copiar&quot;

PR corrige la edición de copia menor para corregir la ortografía de &quot;copia&quot;

_AC-13300 - [Problema de GitHub](https://github.com/magento/magento2/issues/39311) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39307)_

#### El JSON de importación de producto del extremo REST no valida los campos obligatorios

El campo de nombre ahora es obligatorio al crear nuevos productos a través del proceso de importación (administrador o API). Antes de la corrección, podría haber creado nuevos productos sin nombre, lo que habría roto la interfaz de administración y creado productos no válidos.

_ACP2E-3660 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Falta la opción de filtro de sitio web en el proceso de exportación

Ahora es posible filtrar los productos por sitios web al crear la exportación de productos.

_ACP2E-3720 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplicado de AC-13913: limpieza de atributos estáticos asincrónicamente.

Después de la corrección, no hay ningún error &quot;Undefined array key &quot;apply_to&quot;&quot; cuando se crean numerosas instancias de \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType.

_ACP2E-3752 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### Importación de producto CSV: no se puede anular la configuración de una imagen de muestra

Antes de la corrección, no se podía actualizar la imagen de muestra de un producto mediante la importación de productos. Ahora, después de la corrección, si marca la columna de imagen de muestra de producto con el marcador vacío configurado, la imagen se establecerá en oculta.

_ACP2E-3972 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### La importación de productos genera direcciones URL vacías para el ámbito del almacén

La clave de URL del producto en la vista de tienda ahora heredará el valor establecido en el ámbito predeterminado si url_key tiene un valor vacío en la fuente de datos de importación. Si anteriormente se establecía url_key en un valor vacío en la fuente de datos de importación para un registro de vista de tienda, se anulaba url_key con un valor vacío en ese ámbito.

_ACP2E-4038 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### El proceso de importación de productos encuentra un error si se configura un atributo de selección múltiple como obligatorio

Se ha resuelto un problema en el cual las importaciones de productos fallaban si se incluía un atributo requerido de tipo multiselección. La validación de datos ahora se realiza correctamente, lo que permite que el proceso de importación del producto se complete correctamente.

_ACP2E-4057 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [NUBE] productos sin pedidos pendientes seleccionados en administrar existencias aún permiten a los clientes realizar pedidos superiores a nuestros niveles de existencias cuando se importan

Después de la corrección, ya no es posible importar un valor inaceptable para el atributo &quot;allow_backorders&quot; del producto.

_ACP2E-4116 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Error en la importación del producto debido a que la longitud de la descripción supera los 65.536 caracteres Validación

Después de la corrección, es posible importar atributos de producto con texto de tipo cuyos valores superen los 65 536 caracteres.

_ACP2E-4119 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Filtros de exportación para el producto Atributos Sí-No que no funcionan según lo esperado

Después de la corrección, los productos exportados filtrados con un atributo Yes/No contienen los productos esperados que respetan los filtros aplicados.

_ACP2E-4160 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### Problema con el precio de la opción de paquete de actualización por sitio web mediante importación

Ahora es posible exportar e importar precios de selección de opciones de paquetes por sitio web

_ACP2E-4243 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98f028ab)_

#### No se puede importar un cliente con una dirección de correo electrónico en mayúsculas

Se ha corregido un error de clave de matriz no definida al importar clientes con correos electrónicos en mayúsculas cuando Uso compartido de cuentas está establecido en Global. La normalización de correo electrónico ahora es coherente a lo largo del proceso de importación, lo que garantiza que los clientes se puedan importar independientemente de las mayúsculas y minúsculas del correo electrónico. El comportamiento de uso compartido de cuentas en el nivel de sitio web permanece sin cambios.

_ACP2E-4373 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

### Importación/exportación, cliente/clientes

#### El administrador puede importar un cliente con una fecha de nacimiento superior a la fecha actual

Se ha corregido un problema en el cual los administradores podían importar clientes con una fecha de nacimiento establecida en el futuro. El sistema ahora valida el DOB durante la importación, muestra un error para registros no válidos e impide que se importen clientes con fechas de nacimiento futuras, lo que garantiza datos de clientes precisos.

_AC-13641 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

### Inventario/MSI

#### La recogida en tienda no respeta el radio máximo de búsqueda cuando la dirección se cambia al finalizar la compra

Ahora, la tienda preseleccionada en &quot;Elegir en tienda&quot; se actualizará si la dirección de envío cambia. Anteriormente, una vez preseleccionada una tienda, no cambiaba aunque la nueva dirección de envío no estuviera en el radio de la tienda seleccionada

_ACP2E-3728 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/07620383)_

#### No hay ninguna tienda disponible después de redirigir a la página de inicio y cerrar la compra

La tienda seleccionada anteriormente ahora se preseleccionará en el envío &quot;Elegir en tienda&quot; si el cliente navega a la página de pago, luego vuelve a la página de inicio y, finalmente, a la página de cierre de compra. Anteriormente, después de volver repetidamente a la página de cierre de compra, se borraba la tienda seleccionada en &quot;Elegir en tienda&quot;.

_ACP2E-3793 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

#### La operación de eliminación de stock no se ha completado

Después de la corrección, la eliminación de un elemento de origen no provoca una reindexación completa y actualiza solo los productos afectados, lo que aumenta el rendimiento.

_ACP2E-3917 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [MSI]: no hay indicación en el administrador de si el cliente recibió una notificación asincrónica de que el pedido está listo para recogerse

Se ha agregado a la notificación del historial de pedidos acerca de que el cliente ha recibido una notificación asincrónica acerca de Pedido listo para recoger

_ACP2E-3968 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### Duplicado de consultas de estado de stock al cargar el presupuesto

Se ha corregido la ejecución duplicada de la consulta cataloginventory_stock_status al cargar una oferta en la tienda, lo que provocaba llamadas a BD redundantes.

_ACP2E-4102 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/fc15a9ae)_

#### Post-Patch ACP2E-4118: Cambio de Umbral de Stock en Administración Causa Cantidades Vendibles Negativas y Discordancia de Estado de Stock

El estado de stock de inventario ahora se ajusta automáticamente cuando las configuraciones de inventario global Cantidad, Pedidos no Satisfechos y Umbral de Agotado se actualizan mediante importación.

_ACP2E-4142 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### El informe del administrador [CLOUD] no muestra detalles cuando se actualiza el inventario

Los cambios de origen del inventario de productos ahora se registran mediante el módulo de registro. Antes de la corrección, al guardar un producto y realizar cambios relacionados con el inventario, no se registraban los detalles.

_ACP2E-4167 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### El producto agrupado no puede añadirse al carro de compras mientras está marcado como en stock

El estado de stock del paquete ahora refleja correctamente las reservas de productos secundarios y los umbrales de falta de existencias.
Anteriormente, los productos agrupados se marcaban como &quot;en existencias&quot; incluso cuando uno o más productos secundarios carecían de una cantidad vendible suficiente. Esto provocaba errores de &quot;No hay suficientes artículos en venta&quot; al añadir el paquete al carro de compras.

_ACP2E-4220 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cbca0396) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### El producto agrupado se muestra incorrectamente como Agotado en PDP después de la importación desde CSV cuando el elemento secundario se asigna a un origen o stock personalizado (corregido después de la reindexación manual)

Después de la corrección, al crear un producto compuesto mediante la importación, se realiza automáticamente una reindexación de existencias, lo que hace que el producto esté disponible sin necesidad de reindexación manual.

_ACP2E-4233 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98f028ab) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### [MSI] pruebas MFTF con errores relacionadas con los cambios más recientes de la línea principal.

Antes de la corrección, los clientes invitados que elegían la opción de recogida en tienda sin una dirección de envío tenían su dirección de facturación rellenada automáticamente con la dirección de la tienda, lo que no se podía cambiar, lo que provocaba detalles de factura incorrectos. Después de corregir, la dirección de facturación ahora se puede editar en este escenario, lo que permite a los invitados introducir sus propios detalles. Los usuarios registrados verán su dirección de facturación guardada en lugar de la de la tienda.

_ACP2E-4260 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ab891304) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/13e432a6)_

#### Reserva de inventario incorrecta creada para tarjetas de regalo virtuales

Antes de la implementación de esta corrección, la cantidad de una tarjeta de regalo virtual que contenía varios artículos no se reflejaba con precisión en la reserva de inventario. Sin embargo, después de que se aplicara la corrección, se sincronizó la cantidad de la reserva de inventario y las existencias.

_ACP2E-4267 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5704166a)_

#### El comando de compensación de reserva de inventario falla con referencias de producto nulas e inexistentes

Se ha corregido un problema en el cual la CLI de compensación de reserva de inventario generaba una excepción si la combinación procesada tenía un ID de pedido que faltaba

_ACP2E-4301 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/76b88f7c)_

#### El producto está agotado después de cambiar el estuche del SKU

La modificación del caso del SKU ya no hace que el producto esté agotado en la tienda.

_ACP2E-4375 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/0836c2ed)_

#### Ordenar por facetas de precio/precio con datos no válidos

Antes de la corrección, los precios de los paquetes no se indexaban correctamente cuando los productos secundarios tenían existencias de fuentes personalizadas. Ahora, después de la corrección, los precios de los paquetes se indexan correctamente, independientemente de la asignación de existencias de productos secundarios.

_ACP2E-4380 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1c547060) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/1f83ed24)_

#### El estado de Stock se restableció incorrectamente a En stock con la cantidad después del cambio de SKU durante la actualización del ensayo

Los cambios de SKU están ahora prohibidos para los productos con una actualización programada activa; los guardados fallarán con un error claro y el campo SKU de administrador estará desactivado durante las actualizaciones activas. Esto evita las incoherencias en el inventario MSI causadas por los cambios de SKU durante las reversiones de ensayo.

_ACP2E-4389_

### Pedido

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) interrumpe customAttributes

Los atributos personalizados en las direcciones ahora se gestionan correctamente durante las operaciones de cierre de compra y API.
Anteriormente, el uso de $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) podía interrumpir la administración de atributos personalizados, lo que provocaba que los valores de atributos se estructuraran de forma incorrecta.
AC-10568

_AC-10568: [problema de GitHub](https://github.com/magento/magento2/issues/31644)_

#### Cuando el cliente está configurado para el pedido de presupuesto sigue siendo un pedido de invitado

_AC-11689: [problema de GitHub](https://github.com/magento/magento2/issues/38540)_

#### El pedido no se ha completado al combinar artículos virtuales, reembolsados y enviados

Se ha corregido un problema que causaba que los pedidos que contenían artículos virtuales, reembolsados y enviados permanecieran en procesamiento, ya que se garantizaba que los artículos virtuales se incluyeran en los cálculos de cantidad enviada, lo que permitía que el estado del pedido pasara correctamente a completo.

_AC-11691: [problema de GitHub](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento reordenar -1 números de pedido

El sistema funciona según lo esperado y después de reordenar desde el backend, el número de pedido será de 8 dígitos únicos

_AC-12854 - [Problema de GitHub](https://github.com/magento/magento2/issues/39089) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39399)_

#### Se pierde la carga del archivo de opciones personalizadas del producto al cerrar la compra con la tarjeta de crédito Adobe

Las cargas de archivos de opciones personalizadas de productos ahora se conservan al realizar la retirada con el método de pago con tarjeta de crédito Adobe.
Anteriormente, la carga de archivos se perdía al utilizar este método de pago, pero funcionaba con otros.
AC-14306

_AC-14306: [problema de GitHub](https://github.com/magento/magento2/issues/39647)_

#### Pedidos de administrador - no se puede buscar Testamento

Se ha corregido un problema en el cual la búsqueda de pedidos por nombre de cliente (por ejemplo, &quot;Will&quot;) en la cuadrícula de pedidos de administración no arrojaba resultados. Después de la corrección, los pedidos relevantes se muestran correctamente cuando se filtran por nombre de cliente.

_AC-14360 - [Problema de GitHub](https://github.com/magento/magento2/issues/36596) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL: los elementos de pedido tienen un formato incorrecto de fecha_pedido

Se ha corregido un problema en el cual el campo fecha_pedido de la respuesta de GraphQL se devolvía en formato aaaa-mm-dd.
Ahora, fecha_pedido se muestra correctamente en formato dd-mm-aaaa.

_AC-14431 - [Problema de GitHub](https://github.com/magento/magento2/issues/39805) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### No se puede devolver nulo para el campo que no admite valores NULL \&quot;AppliedCoupon.code\&quot;. Problema inesperado

Adobe Commerce ahora devuelve correctamente los códigos de cupón aplicados a través de GraphQL al consultar los pedidos de los clientes. Anteriormente, en Adobe Commerce 2.4.8, al recuperar un pedido con el campo applied_coupons.code (por ejemplo, a través de la consulta customer.orders), se podía producir un error de servidor interno y el mensaje No se puede devolver nulo para el campo que no admite valores NULL &quot;AppliedCoupon.code&quot;, y applied_coupons se devolvía como [null] en lugar de una lista que contenía el código de cupón. AC-14484

_AC-14484 - [Problema de GitHub](https://github.com/magento/magento2/issues/39841) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/97b2ea42)_

#### El correo electrónico de envío no se envía cuando se envía desde la vista de pedidos del administrador a pesar de estar habilitado en la configuración de la tienda

El sistema ahora envía un correo electrónico de confirmación de envío, ya que está activado en la configuración de la tienda en la que se realizó el pedido.

_AC-14563 - [Problema de GitHub](https://github.com/magento/magento2/issues/39861) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39897)_

#### El filtrado por fecha no funciona debido a nombres de campo ambiguos

En Magento 2.4.7-p6, se informó que filtrar la cuadrícula de pedidos por fecha causaba un error debido a las uniones con módulos Braintree.
El problema involucraba consultas que unían tablas braintree_transaction_details y sales_order al aplicar filtros de fecha.
Adobe Commerce Engineering revisó el caso, pero no pudo reproducir el error en el entorno.
El comportamiento esperado es que el filtrado por fecha devuelva pedidos que coincidan con el filtro sin errores.

_AC-15037: [problema de GitHub](https://github.com/magento/magento2/issues/40024)_

#### La creación de pedidos en backoffice con varios productos de los cuales al menos uno contiene opciones personalizadas, conduce a que se añadan productos adicionales no deseados al pedido

Se ha corregido un problema que causaba errores al crear un pedido en la oficina central con varios productos, incluido uno con opciones personalizadas, se agregaban involuntariamente productos adicionales y se producía un error. El sistema ahora agrega solamente los productos seleccionados, permitiendo que los pedidos se creen sin ningún elemento inesperado.

_AC-15286 - [Problema de GitHub](https://github.com/magento/magento2/issues/40122) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: No se puede crear la regla de promoción

Esta corrección de PR, obtenemos
Modelo \Magento\Catalog\Model\ResourceModel\Eav\Attribute en lugar de \Magento\Catalog\Model\ResourceModel\Eav\Attribute en el método \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problema de GitHub](https://github.com/magento/magento2/issues/12176) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30479)_

#### Magento cambió el tipo de entidad de $order después de las llamadas a $invoice = $this->_invoiceService->prepareInvoice($order);

Se ha corregido un problema por el cual la edición de una actualización programada existente para una subcategoría aumentaba incorrectamente el child_count para categorías principales en la base de datos. El problema provocaba datos inexactos de la jerarquía de categorías después de guardar las actualizaciones. Después de la corrección, el recuento de elementos secundarios sigue siendo correcto y ya no aumenta de forma inesperada.

_AC-15401: [problema de GitHub](https://github.com/magento/magento2/issues/40154)_

#### El pedido permanece en estado de &#39;procesamiento&#39; después del envío, si los artículos se reembolsan parcialmente

Se ha corregido un problema por el cual los pedidos permanecían en estado Procesando después de reembolsar parcialmente los artículos y enviar el resto. El estado del pedido ahora se actualiza correctamente a Completo una vez que las cantidades totales enviadas y reembolsadas coinciden con la cantidad facturada, lo que garantiza una gestión precisa del ciclo de vida del pedido.

_AC-15419 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### El envío de un correo electrónico de ventas desde el backend siempre da éxito, incluso cuando está desactivado

Se ha corregido la notificación de correo electrónico de ventas back-end para mostrar mensajes precisos mediante la validación del resultado del servicio de correo electrónico, lo que garantiza que los usuarios estén informados cuando los correos electrónicos de pedidos o facturas están desactivados y no se envían.

_AC-16059 - [Problema de GitHub](https://github.com/magento/magento2/issues/40309) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### No se puede crear la lista de solicitudes para el producto asignado al nuevo sitio web y origen

Se ha corregido un problema en el cual no se podían crear listas de solicitudes para productos asignados a un nuevo sitio web y origen cuando &quot;Agregar código de tienda a direcciones URL&quot; estaba habilitado. El problema se produjo porque el código de la tienda se eliminó de la solicitud de la API, lo que provocó un error no autorizado. Después de la corrección, se conserva el contexto de almacén correcto y las listas de solicitudes se crean correctamente.

_AC-16226_

#### El precio personalizado de 0 se restablece al precio original en el repedido.

Se ha corregido un problema en el cual los productos con un precio personalizado de 0 volvían a su precio original durante el repedido.
Ahora, el precio personalizado se conserva correctamente, lo que garantiza precios precisos al reordenar artículos.

_AC-8147 - [Problema de GitHub](https://github.com/magento/magento2/issues/36970) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/01cee3c3)_

#### Realizar pedido con el método de pago desactivado funcionando

Se ha corregido un problema en el cual los pedidos se podían realizar mediante un método de pago deshabilitado a través de GraphQL.
Ahora, se devuelve un error al intentar establecer o utilizar un método de pago no disponible, lo que impide que se cree el pedido.

_AC-9605 - [Problema de GitHub](https://github.com/magento/magento2/issues/37983) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### [Cloud] Algunos JavaScript en línea no funcionan después de actualizar a magento 2.4.6-p7

Al hacer clic en el botón &quot;Eliminar&quot; en &quot;Añadir a pedido por SKU&quot; en el administrador, ahora se elimina el SKU. Anteriormente, al hacer clic en el botón &quot;Eliminar&quot; en &quot;Añadir a pedido por SKU&quot;, no se eliminaba el SKU.

_ACP2E-3515_

#### los datos serializados de tarjetas de regalo no son coherentes en la tabla sales_order

los datos de tarjetas de regalo de la tabla sales_order ahora se serializan correctamente. Anteriormente, se serializaba cada vez que se actualizaba el pedido.

_ACP2E-3662_

#### Estado del pedido atascado durante el procesamiento

Antes de la corrección, al solicitar un paquete de producto con la opción &quot;Enviar juntos&quot; activada, el estado del pedido no cambiaba automáticamente a &quot;completo&quot; después de la factura y el envío. Ahora, después de la corrección, el estado del pedido cambia automáticamente a &quot;completo&quot; después de que se haya facturado y enviado.

_ACP2E-3947 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### Código OOTB de [Cloud]Magento: problema de configuración de plantilla de correo electrónico

Antes de la corrección, al utilizar el envío de correo electrónico asincrónico, los correos electrónicos de envío no eran coherentes con el pedido de la tienda. Ahora, después de la corrección, se entrega el pedido de correo electrónico de envío de tienda adecuado.

_ACP2E-3998 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Cancelar redirecciones de factura a 404

La cancelación de la factura realizada con el tipo No Capturar ya no lleva a la página 404.

_ACP2E-4001 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Los trabajos de Cron del archivo de ventas están causando problemas de bloqueo de BD

Antes de la corrección, las consultas de DELETE sin enlazar ubicadas en el archivo cron estaban causando problemas con Galera. Ahora, después de la actualización, las consultas de eliminación se ejecutan con límites.

_ACP2E-4010_

#### Problema con pedidos actualizados con opciones configurables que utilizan la API de REST

Conservar las opciones de producto existentes en los artículos de pedidos de venta al actualizar un pedido a través de puntos finales de API de REST.

_ACP2E-4061 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### El remitente específico de la tienda no se utiliza para los correos electrónicos con tarjetas regalo

Anteriormente, al enviar una plantilla de correo electrónico para una tarjeta regalo después de crear una factura desde una tienda diferente, el nombre del propietario en la configuración de administración no se reflejaba en los encabezados de correo electrónico cuando el cliente recibía el correo electrónico. Después de aplicar esta corrección, los encabezados de correo electrónico ahora incluyen la información de correo electrónico del propietario de la tienda correspondiente.

_ACP2E-4310_

#### Inserción de ventas asincrónicas por id limitada a 100 entradas por ejecución de cron

Se ha mejorado el procesamiento de la inserción asincrónica de la cuadrícula de ventas. Una ejecución de cron ahora inserta todas las filas pendientes en lotes, en lugar de un estricto 100 por ejecución.

_ACP2E-4360 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/31258bf6)_

#### Mensaje de error &quot;El producto con ID &quot;1&quot; no existe.&quot; se registra repetidamente en exception.log

Antes de la corrección, se registraban errores críticos cuando se encontraban productos eliminados en la sección Últimos artículos pedidos. Después de la corrección, los comerciantes pueden configurar si desean registrar u omitir los productos eliminados a través del parámetro `skipDeletedProductLogging` en di.xml. De manera predeterminada, el comportamiento permanece sin cambios para la compatibilidad con versiones anteriores, pero los comerciantes pueden establecer el parámetro en `true` para omitir silenciosamente los productos eliminados y evitar el ruido del registro.

_ACP2E-4366 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

#### Impuesto doble sobre el reembolso del segundo abono

Se ha corregido un cálculo de impuestos incorrecto en las notas de abono al crear una devolución parcial a partir de una factura después de crear una nota de abono anterior desde la página de vista de pedidos.

_ACP2E-4384 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Pedido, Precio

#### El administrador muestra un símbolo de moneda incorrecto en al crear la devolución

En una configuración de varios sitios web con diferentes monedas (EUR/USD/GBP), la página de selección de productos de retorno del administrador ahora muestra el símbolo de moneda correcto. Anteriormente, mostraba el símbolo de moneda predeterminado.

_ACP2E-3658 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

### Pedido, Devoluciones

#### Error al crear nota de abono para devolución sin conexión

Se ha corregido un problema por el cual se producía un error al crear una nota de crédito para productos agrupados con el ajuste Precio dinámico = No. Ahora, las notas de abono se pueden crear correctamente sin errores.

_ACP2E-4157 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

### Otros

#### No es posible dejar el valor vacío para &quot;Puntos de recompensa de límite de saldo en&quot;- Guardado

Adobe Commerce ahora permite a los comerciantes dejar vacío el campo Cap Reward Points Balance At mientras se sigue estableciendo un valor para el Umbral de canje de saldo de puntos de recompensa. Anteriormente, al configurar los puntos de recompensa en Tiendas > Configuración > Clientes > Puntos de recompensa, al introducir un número positivo para Umbral de canje de saldo de puntos de recompensa de puntos de recompensa y dejar Saldo de puntos de recompensa de límite en blanco se activaba el error de validación: &quot;El \&quot;Saldo de puntos de recompensa de límite\&quot; no es válido. El saldo debe ser un número positivo o dejarse vacío. Verifique e inténtelo de nuevo&quot;. Esto evita que los comerciantes guarden la configuración sin un límite. ACP2E-3977

_ACP2E-3977_

### Otras herramientas para desarrolladores

#### [Problema] Sugerencia de tipo incorrecta para el miembro protegido $_urlHelper

El sistema ahora corrige la sugerencia de tipo incorrecta con la correcta, que también se utiliza en el constructor

_AC-10716 - [Problema de GitHub](https://github.com/magento/magento2/issues/32503) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32496)_

#### [Problema] al limpiar el código no utilizado.

El sistema ahora elimina el código no utilizado con respecto a las importaciones no utilizadas.

_AC-10980 - [Problema de GitHub](https://github.com/magento/magento2/issues/38424) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33499)_

#### Error de accesibilidad de Lighthouse

El sistema ahora pasa con una puntuación de accesibilidad de 100

_AC-12783 - [Problema de GitHub](https://github.com/magento/magento2/issues/39054) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39164)_

#### Deshabilitar configuración de tienda captcha seguir cargando archivos js captcha

El sistema ahora no carga archivos captcha js cuando deshabilitamos captcha
para tienda

_AC-14267 - [Problema de GitHub](https://github.com/magento/magento2/issues/32987) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39154)_

#### [Problema] de accesibilidad: los roles WAI-ARIA anidan incorrectamente en el menú

El sistema ahora genera accesibilidad de faro sin funciones WAI-ARIA anidando mal en el error de menú y el informe debe ser verde

_AC-15082 - [Problema de GitHub](https://github.com/magento/magento2/issues/40045) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38617)_

#### Error de consola en la previsualización de correo electrónico en el administrador de Magento

El sistema no generará ningún error de consola al previsualizar la plantilla de correo electrónico

_AC-9245 - [Problema de GitHub](https://github.com/magento/magento2/issues/37820) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37933)_

### Pago/ Métodos de pago

#### El mensaje de Paylater no se muestra en la tienda mientras se configura correctamente en el servidor

Se ha corregido un problema por el cual el mensaje PayPal Más tarde no se mostraba en las páginas de Inicio y Carro de compras a pesar de estar configurado en el servidor. El banner no se podía mostrar cuando el país comprador era nulo para los invitados o clientes sin una dirección predeterminada. Después de la corrección, el mensaje Pagar más tarde se muestra correctamente en la tienda.

_AC-12335 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/528af81a)_

### Pagos

#### [Problema] Corregir captura de factura sin conexión (404)

Corrige el error de página 404 al capturar facturas de métodos de pago sin conexión del administrador de Magento

_AC-13336 - [Problema de GitHub](https://github.com/magento/magento2/issues/39298) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39297)_

#### IPN desconocidos de PayPal abusa del procesador IPN de la aplicación

El controlador IPN ahora ignora los tipos IPN no admitidos o desconocidos. En lugar de devolver un error 500, registra el problema y continúa procesando sin interrupción.

_ACP2E-4049 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Error al pagar el token de tarjeta guardada de PayflowPro

Los ID de transacción de PayPal PayFlow Pro (PNREF) ahora son válidos para su uso en transacciones de referencia durante un periodo fijo de 12 meses. Una vez caducada, la tarjeta guardada ya no se mostrará y debe añadirse de nuevo. Anteriormente, la validez estaba determinada por la fecha de caducidad de la tarjeta de pago utilizada en la transacción original.

_ACP2E-4064 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### Problema con la tarjeta abovedada al realizar el pedido en el administrador

Realizar un pedido con tarjeta de crédito almacenada en un sitio web con una configuración de acción de pago diferente ya no da como resultado un tipo de transacción erróneo o de error

_ACP2E-4270 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### La tarjeta guardada (Vault) de [Cloud] PayflowPro de los últimos 4 dígitos no se muestra en el pedido

La información de la tarjeta ahora se mantiene y muestra correctamente cuando se utilizan tarjetas guardadas con la acción de pago Ventas, que coincide con el comportamiento al utilizar la acción de pago Autorización para PayflowPro.

_ACP2E-4346 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Rendimiento

#### [Problema] al actualizar Store.php

Esta PR mejora el rendimiento al omitir la resolución actual de la tienda.

_AC-14791 - [Problema de GitHub](https://github.com/magento/magento2/issues/39949) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38717)_

#### [Problema] La actualización usa el control de caché inmutable para el sitio estático

Esta PR mejora el rendimiento al no validar el contenido estático en cada carga de página hasta y a menos que cambie.

_AC-15171 - [Problema de GitHub](https://github.com/magento/magento2/issues/39486) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39484)_

#### [Problema] Almacene en caché los resultados de las llamadas isCacheable para mejorar el rendimiento

Esta PR agrega almacenamiento en caché para los resultados del método isCacheable() en el proceso de representación del diseño para reducir las comprobaciones redundantes y mejorar el rendimiento general del procesamiento de páginas.

_AC-16054 - [Problema de GitHub](https://github.com/magento/magento2/issues/40156) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40112)_

#### [Problema] Mejora menor del rendimiento del procesamiento asincrónico de cuadrícula de pedidos

Esta PR introduce una optimización del rendimiento para el procesamiento asincrónico de cuadrículas de pedidos de Magento al reemplazar la búsqueda last_updated_at basada en caché transitoria con un indicador respaldado por DB persistente almacenado en la tabla de indicadores. Esto garantiza que el sistema conserve de forma consistente la última marca de tiempo procesada, incluso después de vaciados o implementaciones de caché, lo que evita análisis innecesarios de tabla completa en grandes conjuntos de datos sales_order. Como resultado, las actualizaciones de la cuadrícula asíncrona se vuelven más eficientes y predecibles, especialmente en tiendas de gran volumen con actividad de pedidos frecuente.

_AC-16109 - [Problema de GitHub](https://github.com/magento/magento2/issues/40282) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40271)_

#### Módulo de permisos de categoría que posiblemente impide el almacenamiento en caché

Los controladores de terceros ahora se almacenan correctamente en caché con segmentos de clientes

_ACP2E-3721_

#### [NUBE] no puede agregar productos a las categorías

Se ha mejorado el rendimiento al agregar un producto a una categoría mediante Visual Merchandiser.

_ACP2E-3946 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate a más de 10 000 registros

Anteriormente, la caché se borraba en cada visita al PLP o al carro de compras, lo que provocaba una sobrecarga de rendimiento innecesaria. La caché de reglas de Target ya no se invalida en estas páginas, lo que mejora la eficacia de la exploración.

_ACP2E-4059_

#### [Cloud] php-fpm no respeta max_execution_time

La configuración de implementación ahora se carga una vez en una sola solicitud.

_ACP2E-4201_

#### Problema de rendimiento de limpieza del registro de cambios después de ACP2E-3995

Después de la corrección, el trabajo cron indexer_clean_all_changelogs limpia completamente los changelogs, manteniendo el agrupamiento en su lugar.

_ACP2E-4211 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ee918f0d)_

#### [NUBE]: La caché de Fastly no funciona después de actualizar a 2.4.8

Se ha resuelto un problema en el cual las páginas almacenables en caché no se almacenaban ni servían correctamente desde la caché de Fastly, lo que resultaba en un comportamiento de almacenamiento en caché incoherente y un rendimiento reducido.

_ACP2E-4324 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2687b487)_

#### Investigue los motivos del aumento de la creación de claves de redis y de caché

Antes de la corrección, las claves de caché utilizadas para los metadatos de almacenamiento remoto no caducaban. Ahora, después de la corrección, puede establecer un TTL para estas claves de caché mediante la inyección de dependencia.

_ACP2E-4345 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Precio

#### El precio siempre es 0 para los artículos de producto agrupados sin precio dinámico en la API de resto de pedidos

La API de REST de pedido ahora devuelve los precios correctos para los artículos de producto agrupados sin precio dinámico.
Anteriormente, al exportar pedidos a través de la API de REST, el precio de los elementos de producto del paquete sin asignación de precios dinámica siempre se devolvía como 0, en lugar del precio real que se muestra en la página del paquete.
AC-11925

_AC-11925 - [Problema de GitHub](https://github.com/magento/magento2/issues/38687) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7da46f52)_

#### Ámbito Incorrecto Asignado a Atributos de Precio en Creación

Se ha corregido un problema por el cual los atributos de precio recién creados se asignaban incorrectamente al ámbito de vista de tienda independientemente de la configuración; después de la corrección, el ámbito de atributo ahora se alinea con la configuración de ámbito de precio de catálogo (global o sitio web) de forma predeterminada.

_AC-14945 - [Problema de GitHub](https://github.com/magento/magento2/issues/39986) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### El producto se está guardando incluso cuando el precio especial desde la fecha es posterior a hasta la fecha mediante una acción masiva

Se ha corregido un problema en el cual los productos se podían guardar con un intervalo de fechas de precio especial no válido sin validación.
Ahora, se muestra un mensaje de error: &quot;Asegúrese de que la fecha &quot;Hasta&quot; sea posterior o igual a la fecha &quot;Desde&quot;.&quot;

_AC-15252 - [Problema de GitHub](https://github.com/magento/magento2/issues/40113) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Los detalles del envío no coinciden después de completar el pago y envío de PayPal Express para una cotización negociable.

Este problema ha corregido un desajuste en los gastos de envío al completar el Pago y envío de PayPal Express para una oferta negociable aprobada.
Antes de la corrección, el envío se duplicaba incorrectamente (mostrando 10 $ en lugar de 5 $), lo que producía totales inflados.
La corrección en Magento 2.4.9-alpha3 garantiza que se apliquen los costes de envío correctos

_AC-15280_

#### El precio especial no tiene efecto con los sitios web creados con diferentes zonas horarias

Antes de la corrección, la validez de la fecha de precio especial se creaba en el ámbito de la marca de tiempo del almacén actual. Ahora, después de la corrección, se tiene en cuenta la zona horaria predeterminada de la tienda.

_ACP2E-4002_

#### El precio normal no es visible, aunque se aplique un precio especial.

Se ha resuelto un problema en el cual el precio normal no se mostraba cuando se aplicaba un precio especial. Ahora, el precio normal aparece correctamente junto al precio especial, tal como se esperaba.

_ACP2E-4100 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

### Product

#### Producto configurable con mal comportamiento en el front-end

Se ha corregido un problema en el cual los productos configurables mostraban un comportamiento de front-end incorrecto cuando se incluía un atributo de muestra de color, lo que provocaba que los precios, el diseño desplegable y los indicadores de campo requeridos aparecieran incorrectamente.
Ahora, los productos configurables se representan correctamente con unos precios adecuados, menús desplegables alineados y el comportamiento esperado de la interfaz de usuario.

_AC-1014 - [Problema de GitHub](https://github.com/magento/magento2/issues/14296) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La cadena de afirmación de precios no coincide cuando el producto configurable se asigna al sitio web de prueba de stock y prueba con la opción de mostrar los productos sin existencias activada

Se ha actualizado la prueba de fallo para que se ajuste al comportamiento de precios real de los productos configurables cuando todos los productos secundarios tienen el mismo precio.
La afirmación ahora valida correctamente el precio mostrado, lo que evita errores de prueba falsos sin afectar a la funcionalidad.

_AC-10843 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/1ccc786b)_

#### La etiqueta &quot;Tan bajo como&quot; se sigue mostrando para un producto configurable para el caso de prueba AC-6158

Productos configurables implementados y verificados (P1-P7) con sus respectivas variaciones y asignaciones de categorías. Se garantizó la visualización correcta del precio de la tienda y el comportamiento de la etiqueta &quot;Tan bajo como&quot; para los productos de la categoría C.

_AC-10847 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Descuento porcentual en el precio de nivel y la regla de precio de catálogo calculados en el precio original sin las opciones seleccionadas.

Los descuentos porcentuales en las reglas de precio de nivel y de catálogo ahora incluyen opciones personalizadas seleccionadas.
Anteriormente, los descuentos porcentuales se calculaban sobre el precio original del producto sin tener en cuenta las opciones personalizadas seleccionadas, lo que daba como resultado precios finales incorrectos.
AC-12004

_AC-12004: [problema de GitHub](https://github.com/magento/magento2/issues/38750)_

#### [El problema] de la clasificación de validación no funciona, el selector de clasificación de revisión ha cambiado

Se ha corregido un problema en el cual la validación de la clasificación de revisión no se activaba debido a un selector modificado. Anteriormente, las revisiones se podían guardar sin seleccionar una clasificación. Después de la corrección, la validación funciona correctamente y evita que se guarde una revisión a menos que se seleccione una clasificación.

_AC-12686 - [Problema de GitHub](https://github.com/magento/magento2/issues/33424) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minCantidad de pedido de producto faltante permitida

El sistema funciona bien y el origen de la página muestra correctamente la cantidad mínima del producto

_AC-12909 - [Problema de GitHub](https://github.com/magento/magento2/issues/39142) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39480)_

#### Colección de productos: addMediaGalleryData llama a getSize cuando la colección puede cargarse o cargarse (puede utilizar el recuento para evitar una consulta de base de datos adicional)

Esta PR reduce la llamada de consulta adicional mediante count() si la colección de productos ya se carga al llamar a Product Graphql con el campo media_gallery incluido en ella.

_AC-13055 - [Problema de GitHub](https://github.com/magento/magento2/issues/39111) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39681)_

#### Gestión de SKU no válida para productos vinculados en Magento

Se ha corregido un problema en el cual los productos con SKU &quot;0&quot; no se podían vincular como artículos relacionados, de venta ascendente o de venta cruzada debido a una validación de SKU no válida. La actualización garantiza que estos productos se puedan vincular correctamente, lo que permite guardar el producto sin errores.

_AC-13311 - [Problema de GitHub](https://github.com/magento/magento2/issues/39329) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

#### Problema con la cuadrícula Opciones personalizables en la página de producto en el panel de administración

El sistema funciona según lo esperado al crear opciones personalizables con el menú desplegable de tipo

_AC-14003 - [Problema de GitHub](https://github.com/magento/magento2/issues/39640) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39694)_

#### Error en la página de producto del administrador cuando todos los atributos de producto están configurados en el ámbito global

Se ha corregido un problema en el cual la página de edición de producto de administración mostraba un error cuando todos los atributos de producto se establecían en el ámbito global. El error se debía a una consulta de base de datos vacía, lo que hacía que la página no se pudiera utilizar. Después de la corrección, la página del producto se procesa correctamente y los productos se pueden crear sin problemas.

_AC-14011: [problema de GitHub](https://github.com/magento/magento2/issues/39646)_

#### [2.4.8] No se encontraron llamadas de retorno para el trabajo cron catalog_product_alert

Adobe Commerce ahora evita correctamente que se programen trabajos cron catalog_product_alert incorrectos después de cambiar el nombre del trabajo cron de alerta de producto a product_alert. Anteriormente, en Adobe Commerce 2.4.8, la configuración de Tiendas > Configuración > Catálogo > Catálogo > Configuración de ejecución de alertas de producto provocaba que se creara una entrada cron catalog_product_alert en core_config_data y, cuando se ejecutaba cron, se registraba el error Magento_Cron.CRITICAL: Exception: No se encontraron devoluciones de llamada para el trabajo cron catalog_product_alert aunque los trabajos product_alert válidos se ejecutaban correctamente.

_AC-14494 - [Problema de GitHub](https://github.com/magento/magento2/issues/39800) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### La Opción De Impresión De Página De Lista De Solicitudes No Funciona

La opción Imprimir de la página Lista de Solicitudes ahora funciona correctamente.
Anteriormente, al hacer clic en &quot;Imprimir&quot; se producía el siguiente error: &quot;Se ha producido un error durante la ejecución de la aplicación. Consulte el registro de excepciones para obtener más información&quot;.
AC-14711

_AC-14711_

#### La lista de comparación de [productos] no se podrá utilizar

Se ha corregido un problema en el cual la lista de comparación dejaba de utilizarse cuando se agregaba el mismo producto desde distintas vistas de tienda. Después de la corrección, la lista de comparación se carga correctamente y muestra los elementos en función del almacén específico.

_AC-14885 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Error De Registro Adicional Al Solicitar Un Producto A Través Del Repositorio

Mensajes de error mejorados para ProductRepository::get y getById cuando no se encuentra un SKU o ID.
Anteriormente, las excepciones no proporcionaban ningún contexto sobre el SKU o el ID que provocaba el error.
Ahora, el mensaje de excepción incluye el SKU o ID que falta, lo que ayuda a depurar y mejorar la experiencia del desarrollador.
Este cambio no afecta a ningún comportamiento funcional de la API.

_AC-15199 - [Problema de GitHub](https://github.com/magento/magento2/issues/40090) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### El error No existe en el conjunto de atributos rompe la página

Se ha corregido un problema que causaba un error grave al introducir un ID de conjunto de atributos no válido en la URL; el sistema ahora muestra un mensaje de error correcto que indica que el conjunto de atributos no existe en lugar de romper la página.

_AC-15753 - [Problema de GitHub](https://github.com/magento/magento2/issues/40213) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a06a4a57)_

#### Devolución con descuento de devolución de cantidad siempre negativo

Se ha corregido un problema por el cual al crear una nota de abono con una cantidad negativa se devolvía incorrectamente el importe del descuento.
Ahora, los descuentos no se reembolsan por cantidades negativas y la cantidad de devolución se establece correctamente en cero.

_AC-9424 - [Problema de GitHub](https://github.com/magento/magento2/issues/37917) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### La consulta lenta se ejecuta cuando el widget de producto se incluye mediante pagebuilder

Se optimiza la consulta para la creación de widgets de producto, incluidos los SKU de producto.

_ACP2E-3449 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Las imágenes de producto no cambian de tamaño cuando se añaden como producto configurable

Anteriormente, las imágenes agregadas a través de Configuraciones en el panel de administración no respetaban el límite máximo de tamaño de carga, lo que podía generar incoherencias y desafíos de administración. Ahora, se ha implementado una corrección para garantizar que las imágenes se redimensionen automáticamente durante la carga para cumplir con el límite de tamaño máximo, simplificar el proceso y mantener los estándares del sistema.

_ACP2E-3504 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/df92debe)_

#### Todos los elementos de otras listas de comparación de clientes se asignan al cliente después de iniciar sesión a través del administrador

Anteriormente, cuando un administrador utilizaba la función &quot;Iniciar sesión como cliente&quot; en el backend de, los productos de la lista de comparación de un cliente que había iniciado sesión anteriormente se asignaban incorrectamente al cliente suplantado actualmente.  Después de la corrección, la lista de comparación se carga correctamente para el cliente que ha iniciado sesión correctamente.

_ACP2E-3818 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### Productos simples sin asignar cuando el producto configurable está editado por una función limitada

Antes de esta corrección, si un usuario administrador restringido guardaba un producto configurable que contenía productos simples a los que el usuario administrador no tenía acceso, se eliminaban del producto configurable al guardarlo. Después de la corrección, el producto configurable se conserva como guardado de un administrador de derechos completo.

_ACP2E-4081_

#### [Guardar catálogo compartido B2B] devuelve un error de funcionalidad obsoleto

El administrador puede anular la asignación de productos del catálogo compartido correctamente.
Si se han anulado las asignaciones de productos con un gran número de SKU de producto largas del catálogo compartido, se han producido errores

_ACP2E-4097 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### El rendimiento de generación de mapas de sitio de [Cloud] se ha degradado significativamente

La generación de mapas del sitio para productos con imágenes ya no experimenta una ralentización exponencial. Anteriormente, la generación de mapas del sitio para tiendas con la inclusión de imágenes habilitada resultaba en tiempos de procesamiento largos.

_ACP2E-4153 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

#### La incoherencia del orden de clasificación de segmentos del cliente está provocando que la cookie X-Magento-Vary se regenere todo el tiempo en algunas páginas

La cookie X-Magento-Vary ahora se establece una vez en la página del producto; anteriormente, con algunas configuraciones de segmentos de clientes, la cookie se establece varias veces durante la carga de PDP

_ACP2E-4261_

### Producto, Impuestos

#### El impuesto sobre productos fijos (FPT) no se muestra por separado con los productos configurables

Se ha corregido un problema por el cual el impuesto sobre el producto fijo (FPT) no se mostraba por separado para los productos configurables después de seleccionar una opción. Ahora, el desglose de FTP aparece correctamente en las páginas de detalles y listas de productos, coincidiendo con el formato de visualización de los productos simples.

_AC-13171 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b5e99d20)_

### Promoción

#### La regla de precio Comprar X Obtener Y en el carro agrega un descuento incorrecto cuando ya se ha aplicado otra regla

Se ha corregido un problema en el cual la regla de precio Comprar X Obtener Y del carro de compras calculaba los descuentos utilizando el precio del producto original incluso después de que otra regla ya lo hubiera reducido. La actualización garantiza que la segunda regla ahora aplique el descuento al precio ajustado, lo que da como resultado descuentos totales precisos cuando hay varias promociones activas.

_AC-12325 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Error al obtener descuentos de artículo de pedido aplicados a para el pedido del cliente mediante la solicitud de cliente de GraphQl

Anteriormente, cuando se aplicaban descuentos_a para el pedido del cliente a través de GraphQl, se observaba un error de servidor interno de solicitud del cliente que ahora es fijo y se recuperan los datos adecuados del pedido del cliente con el descuento aplicado

_AC-14888 - [Problema de GitHub](https://github.com/magento/magento2/issues/39963) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Error al obtener el código de cupón de artículo de pedido para el pedido del cliente mediante la solicitud de cliente de GraphQl

Se ha corregido un problema por el cual la recuperación de pedidos con detalles de cupones a través de GraphQL devolvía un error interno del servidor.
Ahora, la consulta se ejecuta correctamente y devuelve la información de cupón correcta en la respuesta.

_AC-14889 - [Problema de GitHub](https://github.com/magento/magento2/issues/39962) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Después de la corrección para ACP2E-2926, los segmentos del cliente coinciden en cada solicitud de cierre de compra, lo que provoca un procesamiento innecesario

La funcionalidad de segmentos del cliente ahora incluye un mecanismo de almacenamiento en caché para mejorar el rendimiento.

_ACP2E-4299_

#### `[Cloud][experienceleague]` regla de precio de catálogo no aplicada

Antes de la corrección, las reglas de precios de catálogo no se aplicaban cuando `special_price` se establecía solamente en el nivel de sitio web (no en &quot;Todas las vistas de tienda&quot;). Después de corregir las reglas de precios del catálogo, ahora se aplican correctamente cuando `special_price` se establece en el nivel de sitio web comprobando primero la tienda predeterminada del sitio web.

_ACP2E-4372 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() carece de filtrado entity_type, lo que provoca que las páginas de CMS se traten como productos en las direcciones URL de categoría

Se ha corregido un problema en el cual DynamicStorage no filtraba por entity_type, lo que provocaba que las páginas de CMS se trataran incorrectamente como productos en direcciones URL de categoría; las direcciones URL mal formadas ahora devuelven correctamente un error 404 en lugar de mostrar contenido de CMS.

_AC-14991 - [Problema de GitHub](https://github.com/magento/magento2/issues/39996) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64823f95)_

#### Al habilitar la ruta de categoría en las direcciones URL del producto, se interrumpe el conmutador de tiendas de varias formas

Se ha corregido un problema que causaba que, al habilitar rutas de categoría en las direcciones URL de productos, fallara el conmutador de tiendas; el cambio de tienda ahora resuelve correctamente las direcciones URL de productos en las vistas de tiendas sin redirigir a la página principal ni devolver errores.

_AC-15110 - [Problema de GitHub](https://github.com/magento/magento2/issues/40037) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a7ef6300)_

#### Clave de matriz no definida en ProductRepository getById

El problema se producía cuando se llamaba a ProductRepository::getById() con un ID no válido como 123abc, lo que provocaba un error de &quot;Clave de matriz no definida&quot;.
Después de la corrección en Magento 2.4.9-alpha3, estas solicitudes ahora devuelven correctamente una página 404 en lugar de iniciar una excepción.
El control de calidad se confirmó con ID válidos y mal formados, y no se observaron más problemas.

_AC-15345 - [Problema de GitHub](https://github.com/magento/magento2/issues/40146) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### La comparación de tiendas crea un error de SEO de Google. Los vínculos no se pueden rastrear

Se ha resuelto un problema de SEO en el cual los motores de búsqueda no podían rastrear el vínculo &quot;Comparar productos&quot; de la tienda debido a que faltaba un atributo href o estaba enlazado incorrectamente. La actualización garantiza que el vínculo ahora contenga una dirección URL válida y rastreable, lo que mejora la capacidad de detección del sitio y ayuda a pasar auditorías de SEO de Google.

_AC-15547 - [Problema de GitHub](https://github.com/magento/magento2/issues/40185) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c95ed7d7)_

#### La actualización de product url_key mediante la API de REST no genera una reescritura de URL 301

Al actualizar la clave URL del producto mediante la API de REST, con la configuración &quot;Crear redireccionamiento permanente para URL si se ha cambiado la clave URL&quot; establecida en Sí, las reescrituras de URL del producto crean una redirección de la URL antigua a una nueva.

_ACP2E-3900 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### La generación de mapas de sitios de [Cloud] nunca termina

Antes de la corrección, la generación del mapa del sitio no podía finalizar correctamente si el catálogo contenía más de un millón de productos. Después de la corrección, la generación del mapa del sitio terminará con una asignación de memoria más baja y con hasta un millón de productos por tienda.

_ACP2E-3902 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### El conmutador de tienda [Cloud] no funciona de EN a FR para la página de preguntas más frecuentes

Se ha corregido un problema que causaba que, al cambiar entre vistas de tienda, se redirigiera a los usuarios a la página principal en lugar de a la página de CMS traducida correspondiente. El conmutador de tienda ahora comprueba las reescrituras de URL en el almacén de destino para garantizar una redirección correcta (por ejemplo, la página de preguntas frecuentes en inglés → la página de preguntas frecuentes en francés).

_ACP2E-4112 - [Problema de GitHub](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [Nube] Desactivar la generación antigua de mapa del sitio

Ahora hay disponible una nueva opción de configuración para cambiar entre el proceso estándar de generación de mapas del sitio y un modo por lotes recién implementado. Esta mejora permite una mayor flexibilidad y escalabilidad en los flujos de trabajo de creación de mapas del sitio.

_ACP2E-4132 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Las solicitudes sospechosas producen excepciones en exception.log

Se ha corregido un problema en el cual las solicitudes de URL malintencionadas o mal formadas causaban errores de intercalación de bases de datos y rellenaban registros de excepciones.
Anteriormente, cuando se recibían solicitudes sospechosas que contenían codificaciones de caracteres no válidas o caracteres no admitidos, el sistema intentaba descodificarlos y procesarlos, lo que provocaba conflictos de intercalación MySQL.

_ACP2E-4328 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2687b487)_

### Ventas

#### El estado del pedido desaparece al seleccionar un valor en la lista desplegable Estado del pedido

La asignación de estado de pedido ahora funciona según lo esperado.
Anteriormente, al asignar estados de pedidos personalizados, el estado &quot;Procesando&quot; podía desaparecer del menú desplegable después de anular la asignación de un estado, lo que imposibilitaba su reasignación.
AC-15010

_AC-15010_

#### Cuando el mensaje de regalo está habilitado en el nivel de pedido, pero el usuario no introduce ningún dato ni realiza ningún pedido, a continuación, sigue apareciendo Nombre de remitente y Nombre de destino en el Administrador, mostrando el nombre y los apellidos del cliente.

Se ha corregido un problema por el cual los campos de remitente y destinatario de mensajes de regalo se rellenaban automáticamente con los nombres de los clientes incluso cuando no se introducía ningún mensaje de regalo; los campos ahora permanecen vacíos a menos que el usuario proporcione los detalles.

_AC-15140 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a8cf637b)_

### Buscar

#### &quot;Confirmar el envío del formulario&quot; en la búsqueda del catálogo con &quot;Recordar paginación de la categoría&quot;

Cuando se vuelve de una página de producto a la página de resultados de búsqueda del catálogo después de modificar la configuración de la barra de herramientas, ya no aparece el déclencheur del cuadro de diálogo &quot;Confirmar envío del formulario&quot; cuando &quot;Recordar paginación de categoría&quot; está habilitado.
Anteriormente, los usuarios encontraban un error del explorador o una advertencia sobre el nuevo envío del formulario al volver a la página de resultados de búsqueda después de cambiar parámetros de la barra de herramientas como el criterio de ordenación.

_ACP2E-4208 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### El campo de búsqueda agregado &quot;_search&quot; ya no se utiliza en la consulta de búsqueda

Ahora, la búsqueda de texto completo devuelve productos coincidentes si la condición mínima debe coincidir de forma colectiva en todos los campos en los que se puede buscar, en lugar de requerir que la condición se cumpla con un solo campo.

_ACP2E-4285 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cbca0396)_

### Seguridad

#### Error interno del servidor

Magento ahora agrega correctamente productos al carro de compras de un cliente al usar el extremo REST asincrónico POST /rest/default/async/V1/carts/mine/items. Anteriormente, esta solicitud asincrónica de &quot;agregar al carro de compras&quot; generaba un error interno del servidor y Magento registraba el siguiente error: Error: Call to a member function setFinalPrice() on null en app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php:162.

_AC-16344 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### El JS agrupado/combinado no forma parte de los hash de la SRI

Antes de la corrección, los archivos agrupados o combinados generados no se añadían a la lista de hash de la SRI. Ahora, los archivos se añaden correctamente a los hash de la SRI.

_ACP2E-3854 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

#### [CLOUD] obtuvo un problema de permiso de escritura en newrelic

Antes de la corrección, los registros estaban llenos de excepciones. Después de aplicar la corrección, los registros ahora están limpios y libres de excepciones.

_ACP2E-4296 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/61c96348)_

### Envío

#### Cantidad incorrecta para enviar después de unos pocos abonos

Se ha corregido un problema por el que el valor de Cant. a enviar se calculaba incorrectamente después de varias notas de abono, lo que permitía el envío de artículos reembolsados.
Ahora, el sistema actualiza con precisión la cantidad de envío restante en función de los artículos enviados y reembolsados, lo que evita envíos no válidos.

_AC-1479 - [Problema de GitHub](https://github.com/magento/magento2/issues/34289) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Problema de rendimiento potencial al cargar métodos de envío

Se ha optimizado el proceso de carga de los métodos de envío asegurándose de que solo se carguen los transportistas activos cuando se solicite. Anteriormente, se inicializaban las fábricas para todos los métodos de envío, lo que provocaba una sobrecarga de rendimiento innecesaria. La corrección mejora la eficacia al cargar condicionalmente solo transportistas de envío activos, lo que reduce el tiempo de carga y el uso de recursos.

_AC-15415 - [Problema de GitHub](https://github.com/magento/magento2/issues/40153) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/cc0ec250)_

#### [Problema] El destino comercial no debe tratarse como residencial

Se ha corregido un problema en la integración de envíos REST de UPS por el que los destinos comerciales se trataban incorrectamente como residenciales. El indicador de dirección residencial ahora se incluye en la solicitud de tarifa de UPS solo para direcciones residenciales, lo que evita recargos residenciales no deseados y garantiza tarifas de envío comerciales precisas.

_AC-16285 - [Problema de GitHub](https://github.com/magento/magento2/issues/40314) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40307)_

#### Excepción al crear la etiqueta de envío UPS

Advertencia fija: conversión de matriz a cadena durante la creación de etiquetas de envío UPS

_ACP2E-3676 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### [QUANS]: ¿Comprueba el módulo principal de Magento_Fedex si hay un token activo válido antes de enviar una solicitud para obtener uno nuevo?

Adobe Commerce ya no realiza muchas solicitudes al servicio de la API de FedEx para el token de acceso. Anteriormente, aunque el token de acceso sigue siendo válido, Adobe Commerce siempre realiza nuevas solicitudes a la API de FedEx, lo que provocaba un problema de limitación de velocidad.

_ACP2E-3930 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Ensayo y previsualización

#### El precio del producto en el carro afectado por la regla de precio del catálogo no cambia cuando la regla se ajusta mediante la actualización de ensayo

Se ha corregido un problema por el cual los precios de productos en el carro de compras no se actualizaban completamente después de modificar una regla de precios de catálogo a través de una actualización de ensayo. Anteriormente, el precio actualizado solo aparecía en la sección de resumen, mientras que el bloque central del carro de compras mostraba el valor antiguo. Ahora, la regla revisada actualiza correctamente el precio del producto en todo el carro de compras.

_AC-15304 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/913bf1a6)_

#### Cuando se elimina la actualización programada para la categoría, la cantidad de elementos secundarios no disminuye para la categoría principal

Se ha corregido un problema que causaba que, al eliminar una actualización programada para una categoría, no se redujera el recuento de elementos secundarios de la categoría principal, lo que garantizaba que el recuento de actualizaciones se realizara correctamente cuando se eliminaban actualizaciones programadas o subcategorías.

_AC-15670 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ef666cd9)_

#### Al editar la actualización programada para las categorías, añade que las tareas secundarias ascienden a la categoría principal

Se ha corregido un problema por el cual la edición de una actualización programada existente para una subcategoría aumentaba incorrectamente el child_count para categorías principales en la base de datos. El problema provocaba datos inexactos de la jerarquía de categorías después de guardar las actualizaciones. Después de la corrección, el recuento de elementos secundarios sigue siendo correcto y ya no aumenta de forma inesperada.

_AC-16239 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8670a2b4)_

#### Al obtener una vista previa de una actualización programada, se abre la primera vista de la tienda en orden alfabético, en lugar de la vista de la tienda en cuestión

Antes de la corrección, la vista previa de una actualización programada se abría en la primera vista de tienda en orden alfabético en lugar de la vista de tienda asignada.
Después de la corrección, la vista previa ahora se abre correctamente en la vista de tienda asignada a la actualización de ensayo del bloque de CMS.

_ACP2E-3671 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b12ffe36)_

#### Problema de comportamiento Cron de Staging_apply_version - special_price omitido

Después de la corrección, los totales de las ofertas se recalcularán después de cambiar el precio especial por la actualización programada del producto.

_ACP2E-3674_

#### No se puede previsualizar la actualización programada del producto con los permisos de categoría habilitados

Antes de la corrección, un producto que se habilitaría en el futuro no se mostraba en el modo de vista previa. Ahora se mostrará incluso si el estado actual es desactivado.

_ACP2E-3786 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### El ámbito muestra diferentes vistas de la tienda durante la vista previa

Antes de la corrección, es posible que se haya abierto una previsualización de actualización de ensayo del bloque cms y del contenido de la página cms en un almacén diferente al asignado en el bloque cms o la página cuando se accede a él desde el panel de ensayo de contenido. Después de la corrección, si el bloque o la página de cms solo tienen un almacén específico asignado en la actualización de ensayo, la vista previa del panel de ensayo de contenido se abrirá con el almacén correcto seleccionado.

_ACP2E-3815_

#### Falta la validación para el campo de importe de descuento de la regla Precio de catálogo

Anteriormente, el campo descuento_importe en la actualización del programa de ensayo no se validaba correctamente con las reglas de validación actuales. Sin embargo, después de aplicar la corrección, el campo descuento_importe se validará correctamente.

_ACP2E-3867 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

#### La previsualización de la actualización de ensayo se interrumpe al cerrar la compra al utilizar un dominio de administración diferente

Un cliente puede iniciar sesión y ver su carro de compras en el modo de vista previa de la tienda cuando la URL de la base de la tienda es diferente de la URL de administración.

_ACP2E-3906_

#### Visualización del tiempo del panel de ensayo de contenido incorrecta

Ahora, los filtros de fecha &quot;Hora de inicio&quot; y &quot;Hora de finalización&quot; del &quot;Panel de ensayo de contenido&quot; muestran la fecha y la hora correctas. Anteriormente, se mostraba una fecha y hora incorrectas después de seleccionar la fecha y la hora en el selector de fechas

_ACP2E-3969_

#### El ámbito muestra diferentes vistas de tienda durante la vista previa de los productos y las categorías de actualización programada

Anteriormente, se corrigió que el vínculo de vista previa de categorías y productos no se generaba para la tienda correcta. Después de esta corrección, el vínculo de vista previa selecciona automáticamente el almacén en el que se creó la vista previa.

_ACP2E-4053_

#### El paquete de productos con actualizaciones programadas elimina la opción de elementos del paquete al guardar el producto

La eliminación de las opciones de producto del paquete o de los productos asociados en la actualización programada ya no afecta a las opciones del paquete original y a los productos asociados, y viceversa. Eliminar también las opciones de producción de paquetes en el producto original y reemplazarlas con otras opciones después de programar una actualización ya no resulta en la eliminación de las opciones recién agregadas

_ACP2E-4212 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ab891304)_

#### Problema con el modo de previsualización de promoción en el que los cupones aplicados desaparecen poco después de aplicarse.

Antes de la corrección, los códigos de cupón no se podían utilizar correctamente en el modo de vista previa de ensayo. Ahora, después de la corrección, los códigos de cupón se aplican correctamente en la página de pago.

_ACP2E-4226_

#### No se puede navegar entre sitios web en la vista previa Programar actualización

Antes de esta corrección, la vista previa de la actualización programada se dañaría al intentar obtener una vista previa del contenido de las tiendas con dominios personalizados. Después de esta corrección, los dominios de tienda personalizados se pueden previsualizar tal cual y navegar dentro del iframe de vista previa. La corrección cubre productos, categorías, páginas de CMS y bloques de CMS, y admite vínculos de navegación con etiquetas de marcado `{{store url}}`, como se documenta en [Variables de Adobe Commerce y Etiquetas de marcado](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/variables/markup-tags).

_ACP2E-4308 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0a3b7032)_

### Impuestos

#### Total de pedido incorrecto, la ronda no se aplica al cálculo del precio.

El sistema gestiona ahora correctamente el cálculo de price_after_discount, discount_amount y el importe de impuestos.
el total real del pedido

_AC-11389 - [Problema de GitHub](https://github.com/magento/magento2/issues/38455) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39687)_

#### [Corrección de problema]: El valor base_weee_tax_applied_row_amnt de los elementos de nota de abono es incorrecto

Se ha corregido el cálculo de la nota de abono utilizando el valor adecuado para base_weee_tax_applied_row_amnt, asegurándose de que el valor de impuesto refleje únicamente la cantidad reembolsada. Anteriormente, el importe de fila utilizaba incorrectamente el valor de pedido completo en lugar del importe de abono parcial.

_AC-12049 - [Problema de GitHub](https://github.com/magento/magento2/issues/38765) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3b5ac075)_

#### La cantidad de impuestos no se actualiza cuando el envoltorio para regalos se elimina del carro de compras

Magento ahora actualiza correctamente los totales de impuestos del carro de compras cuando se elimina el envoltorio para regalos mediante la mutación de GraphQL setGiftOptionsOnCart. Anteriormente, cuando se seleccionaba una opción de envoltorio para regalos y se anulaba pasando &quot;gifWrappingId&quot;: null en la entrada de mutación, la cantidad de impuestos de la cotización no se actualizaba y Magento seguía incluyendo el impuesto de envoltorio para regalos en los totales del carro de compras, aunque no se aplicaba ningún envoltorio para regalos.

_AC-14637_

#### Los artículos en el mini-carrito muestran precios en moneda extranjera sin conversión

El minicarrito ahora convierte correctamente la moneda y muestra la cantidad exacta en función de las tasas de conversión configuradas.

_ACP2E-4364 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1c547060)_

### Marco de prueba

#### [Problema] Quite una etiqueta &lt;gravedad> duplicada de la prueba MFTF AdminSetUpWatermarkForSwatchImageTest

El sistema ahora solo incluye una etiqueta de gravedad única en AdminSetUpWatermarkForSwatchImageTest, lo que mejora la claridad y coherencia del código. Anteriormente, esta prueba contenía dos etiquetas de gravedad idénticas, lo que era innecesario y podía generar confusión.

_AC-11873 - [Problema de GitHub](https://github.com/magento/magento2/issues/38504) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31862)_

#### [Problema] Omitir lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

El sistema ahora ignora el archivo &quot;env.php&quot; que se genera al ejecutar pruebas unitarias, asegurándose de que el estado de Git permanezca limpio después de ejecutar pruebas. Anteriormente, la ejecución de pruebas unitarias generaba un nuevo archivo &quot;env.php&quot;, lo que provocaba que el estado de Git mostrara un nuevo archivo encontrado y lo hacía parecer sucio.

_AC-13293 - [Problema de GitHub](https://github.com/magento/magento2/issues/39304) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problema]: se ha corregido un problema de prueba de integración con el interceptor.

El sistema ahora identifica y administra correctamente \Magento\TestFramework\App\Config\Interceptor en la prueba de integración, lo que garantiza que la prueba pueda acceder a los datos necesarios incluso cuando exista un complemento en la clase. Anteriormente, el sistema no tenía en cuenta la posibilidad de que \Magento\TestFramework\App\Config fuera un \Magento\TestFramework\App\Config\Interceptor, lo que provocaba un error al intentar acceder a la propiedad $data.

_AC-13305 - [Problema de GitHub](https://github.com/magento/magento2/issues/39324) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problema] MFTF: Enviando correo electrónico al formulario de un amigo con captcha habilitado

El caso de prueba aborda la funcionalidad del formulario &quot;Enviar por correo electrónico a un amigo&quot; cuando CAPTCHA está habilitado, lo que garantiza que el proceso de envío del formulario funcione correctamente con valores CAPTCHA incorrectos y correctos.

_AC-13492 - [Problema de GitHub](https://github.com/magento/magento2/issues/39462) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32830)_

#### [Servicio nativo en la nube] Error de compilación de CNS - 2.4.9-beta1- Integración

_AC-16427_

#### Las rutas de sujeción codificadas fallan en las compilaciones del compositor

_AC-16488_

#### El archivo de configuración de PHPUnit no coincide entre las compilaciones de PR y Compositor

_AC-16501_

#### [Problema] magento/magento2#: Mutación de GraphQl. Cobertura de prueba adicional para la configuración de customer storeConfig.

El sistema ahora agrega la cobertura de prueba adicional para las siguientes opciones de customer storeConfig:
required_character_classes_number
minimum_password_length

_AC-9370 - [Problema de GitHub](https://github.com/magento/magento2/issues/37915) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/28761)_

#### Fallos en las pruebas unitarias específicas del entorno en AC 2.4.7-p3

Este problema corrige los errores de las pruebas unitarias que no se reproducen en todas las versiones y entornos. Anteriormente, para corregir algunas pruebas unitarias, se producía un error debido a versiones de biblioteca diferentes o a la funcionalidad faltante agregada en una versión posterior.

_ACP2E-3712 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### [Prueba unitaria] Magento\GiftCardImportExport\Test\Unit\Model\Import\Product\Type\GiftCardTest::testIsRowValid

Se proporcionó una corrección para una prueba unitaria errónea aleatoria

_ACP2E-4263_

### Marco de IU

#### [Problema] Elimina variables duplicadas de uno de los archivos menos

El sistema ahora elimina las variables duplicadas de menos archivos, lo que garantiza un código más limpio y eficiente. Anteriormente, estas variables duplicadas estaban presentes en los archivos Less, lo que producía una redundancia innecesaria en el código.

_AC-11743 - [Problema de GitHub](https://github.com/magento/magento2/issues/31154) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG está vacío en las filas dinámicas

Los campos de WYSIWYG de las filas dinámicas ahora se inicializan y rellenan correctamente.
Anteriormente, los campos de WYSIWYG en filas dinámicas (como en los formularios de configuración de diseño) podían aparecer vacíos o perder su contenido después de determinadas acciones, lo que requería una intervención manual para restaurar los datos.
AC-12336

_AC-12336 - [Problema de GitHub](https://github.com/magento/magento2/issues/38893) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problema] tipo de error tipográfico de mime fijo

El sistema gestiona y fija correctamente el tipo de mime y el error tipográfico de la imagen gif

_AC-8001 - [Problema de GitHub](https://github.com/magento/magento2/issues/36899) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problema] Elimina la etiqueta `@author` prohibida de `Magento_Backend`

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8814 - [Problema de GitHub](https://github.com/magento/magento2/issues/37522) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36976)_

#### [Problema] Evitar el acceso directo a la lista de críticas

El sistema gestiona correctamente y Evita el acceso directo a la lista de críticas Ajax

_AC-9381 - [Problema de GitHub](https://github.com/magento/magento2/issues/37920) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33876)_

#### Encabezado Inicio/cierre de sesión No se actualiza en la configuración de varias tiendas con cookies compartidas

El encabezado de Inicio de sesión se actualiza correctamente al cerrar la sesión según los ajustes de configuración. customer-data.js utilizará una cookie para almacenar el valor &quot;image-customer-login&quot; si las cuentas de los clientes se comparten globalmente. De lo contrario, se utilizará almacenamiento local.

_ACP2E-4149 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### [Móvil] Fotorama puede abrir el minicarrito en la acción de cierre del visor de imágenes

Se ha corregido el problema con Fotorama. Anteriormente, se abría un minicarrito en la acción de cierre del Visor de imágenes

_ACP2E-4231 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e885088b)_

#### Los archivos js combinados no se generan correctamente en proyectos con muchos almacenes.

La combinación de archivos JavaScript ahora funciona correctamente cuando se configuran varios almacenes.
Anteriormente, los archivos a veces no se combinaban correctamente en configuraciones de varias tiendas, lo que producía resultados incompletos o incoherentes.

_ACP2E-4246 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ab891304)_

### Actualizaciones: herramienta de compatibilidad de actualización

#### Funcionalidad Obsoleta: Creación de la propiedad dinámica Magento\Framework\Acl::$_roleRegistry

Los errores de funcionalidad obsoletos ya no impiden el acceso al panel de administración después de la actualización.
Anteriormente, después de actualizar a Magento 2.4.6, al intentar acceder al panel de administración se podía producir el siguiente error:
&quot;Funcionalidad Obsoleta: La creación de la propiedad dinámica Magento\Framework\Acl::$_roleRegistry está obsoleta en vendor/magento/framework/Session/SessionManager.php en la línea 186&quot;
Esto impedía que los administradores iniciaran sesión.
AC-12343

_AC-12343: [problema de GitHub](https://github.com/magento/magento2/issues/37469)_

#### El GUID no se está guardando como formato protegido

_AC-15809_

#### Actualización de la herramienta de compatibilidad con un problema crítico incorrecto

N/D

_ACP2E-3856_
