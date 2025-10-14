---
source-git-commit: 151272eed6c4bb2e1c2e5138a5c8a3a7e7bd8fe6
workflow-type: tm+mt
source-wordcount: '6079'
ht-degree: 0%

---
# Notas de la versión de Magento Open Source (v2.4.9-alpha3)

## Se han corregido problemas en la versión 2.4.9-alpha3

Hemos corregido 129 problemas en el código principal Magento Open Source 2.4.9-alpha3. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

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

#### El extremo de la API de REST export-stock-salable-qty devuelve elementos incorrectos total_count

Se ha corregido un problema de paginación en la API de cantidad vendible de stock de exportación de inventario en el que total_count se limitaba incorrectamente al tamaño de página. Anteriormente, al usar el punto de conexión /rest/all/V1/inventory/export-stock-salable-qty/website/base con parámetros de paginación como page_size=5, el campo total_count de la respuesta devolvía 5 en lugar del número total real de productos que coinciden con los criterios de búsqueda. Después de esta corrección, el campo total_count ahora refleja correctamente el número total de productos disponibles independientemente del parámetro page_size, lo que garantiza un comportamiento de paginación coherente en todos los extremos de la API REST de Magento.

_ACP2E-4086 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

#### El atacante podría usar la petición POST usando la API REST y puede enviar la carga útil RCE

Las API de REST V1/guest-carts/&lt;cartId>/items/ y V1/carts/mine/items/ ahora validan &quot;product_options.extension_attributes.custom_options&quot;.*.option_id&quot; para que sea un option_id válido en el SKU del elemento del carro de compras. Anteriormente, esta opción se procesaba y guardaba en la base de datos sin ninguna validación.

_ACP2E-4138 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Cuenta

#### [Problema] eliminó el espaciado innecesario en la cuadrícula del servidor

El sistema ahora elimina el espaciado innecesario en la cuadrícula back-end cuando hay elementos seleccionados

_AC-11579 - [Problema de GitHub](https://github.com/magento/magento2/issues/38502) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32622)_

#### No se pudo borrar el comentario del elemento de la lista de deseos mediante `updateProductsInWishlist` mutación de GraphQL

Se ha corregido un problema por el cual los comentarios de lista de deseos no se actualizaban mediante mutaciones de GraphQL.
Ahora, los comentarios se actualizan correctamente y se reflejan tanto en la respuesta de la API como en la tienda.

_AC-14682 - [Problema de GitHub](https://github.com/magento/magento2/issues/39911) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

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

#### Problema tras el inicio de sesión en magento 2.4.8-p1

Se ha corregido un problema en Magento 2.4.8-p1 por el que el vínculo &quot;Crear una cuenta&quot; seguía visible en la página de inicio después de iniciar sesión.
Ahora, el vínculo se oculta correctamente después de iniciar sesión, de forma coherente con otras páginas.

_AC-15292: [problema de GitHub](https://github.com/magento/magento2/issues/40120)_

### IU de administración

#### [Problema] reemplaza al escape obsoleto

Esta PR elimina el getEscaper() obsoleto y lo añade mediante inyección de constructor

_AC-15132 - [Problema de GitHub](https://github.com/magento/magento2/issues/40062) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38135)_

#### Mensaje de bienvenida superpuesto a la categoría del producto en la vista móvil.

Se ha corregido un problema de la interfaz de usuario por el que el nombre de bienvenida se superponía con las categorías de productos en la vista móvil, bloqueando los clics.
Ahora, las categorías son totalmente visibles y en las que se puede hacer clic sin problemas de superposición.

_AC-15166 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Entradas del tipo &quot;No se puede resolver el parámetro reCAPTCHA&quot; en exception.log para el panel de administración de Google reCAPTCHA

Se ha resuelto un error de reCaptcha en el archivo `var/log/exception.log` para el inicio de sesión del administrador de reCAPTCHA de Google V3 y no se ha registrado ningún mensaje de error. Anteriormente, se producía el siguiente error cada pocos segundos cuando un usuario administrador configuraba su configuración de **Configuración** > **Seguridad** > **Panel de administración de Google reCAPTCHA**: `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [GitHub-34975](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [Problema de GitHub](https://github.com/magento/magento2/issues/34975) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4f7e5983) - [Contribución de código de GitHub](https://github.com/magento/security-package/commit/804dbc2a)_

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

_ACP2E-4052 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

### IU de administración, impuestos

#### Error de IU de administración de tasa impositiva

Este ticket solucionó un problema de la interfaz de usuario de administración de tasa impositiva en el que al cambiar el país (por ejemplo, de EE. UU. → Reino Unido) aún se mostraba el estado de EE. UU. seleccionado anteriormente, lo que confundía a los usuarios.
En 2.4.9-alpha3, el campo de estado ahora se restablece como * cuando el país seleccionado no tiene estados.

_AC-8440 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### La API de REST products-render-info devuelve un precio final incorrecto para el cliente que ha iniciado sesión

El ticket tiene una corrección para la API de REST products-render-info que devuelve un precio final incorrecto para el cliente que ha iniciado sesión

_AC-5979 - [Problema de GitHub](https://github.com/magento/magento2/issues/35757) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/)_

#### El botón Añadir a la lista de solicitudes desaparece cuando intentamos añadirlo desde la página de categoría

Anteriormente, el botón Añadir a la lista de solicitudes desaparece cuando se intenta añadirlo desde la página de categoría, que ahora es fija y se puede ver el botón de solicitud en la página de categoría

_AC-8575_

### B2B, carro y cierre de compra

#### No existe esa entidad con cartId = se muestra el error X en Storefront cuando se inicia sesión del usuario de la empresa B2B desde la función de administración &quot;Iniciar sesión como cliente&quot;

Ahora el error &quot;No existe esa entidad con cartId = X&quot; ya no está visible después de iniciar sesión correctamente desde el backend de administración al utilizar la función &quot;Iniciar sesión como cliente&quot;.

_ACP2E-3994 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

### Carro y cierre de compra

#### [Problema] Agregar EventPrefix y EventObject al modelo de acuerdo de cierre de compra

El sistema ahora incluye EventPrefix y EventObject para el modelo de acuerdo de retirada, lo que permite activar eventos con un prefijo de evento. Esta mejora proporciona más flexibilidad para los desarrolladores cuando trabajan con eventos de acuerdo de cierre de compra. Anteriormente, el modelo de acuerdo de cierre de compra no era compatible con EventPrefix y EventObject, lo que limitaba la capacidad de personalizar la administración de eventos.

_AC-13252 - [Problema de GitHub](https://github.com/magento/magento2/issues/32510) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32451)_

#### [Graphql] no puede devolver un valor nulo para el campo que no acepta valores NULL &quot;SelectedCustomizableOption.label&quot;

El sistema ahora no generará un error de servidor interno con un mensaje cuando la opción seleccionada ya no exista

_AC-14256 - [Problema de GitHub](https://github.com/magento/magento2/issues/39729) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39888)_

#### [2.4.8] No se pueden realizar pedidos en los que la ciudad tenga dígitos 0-9, símbolo et, punto final o paréntesis en el nombre de la ciudad

Se ha corregido un problema por el cual el cierre de compra fallaba para nombres de ciudades que contenían caracteres especiales como . , &amp; o entre paréntesis.
Ahora, los pedidos con estos nombres de ciudad se colocan correctamente sin errores de validación.

_AC-14495 - [Problema de GitHub](https://github.com/magento/magento2/issues/39854) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Subselección de regla de ventas con condición de cantidad No se puede aplicar

Se ha corregido un problema en el cual las reglas de precio del carro de compras con condiciones de subselección de productos no se aplicaban al cierre de compra.
Ahora, los descuentos se aplican correctamente según las reglas configuradas.

_AC-14884 - [Problema de GitHub](https://github.com/magento/magento2/issues/39965) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Graphql: el carro de combinación no funciona correctamente cuando está habilitado el pedido pendiente

Se ha corregido un problema por el cual los elementos del carro de compras de invitados no se combinaban con el carro de compras de clientes durante la combinación de carros de compras mediante GraphQL.
Ahora, el carro de compras del cliente refleja correctamente la cantidad combinada de los carros de compras de clientes e invitados.

_AC-15148 - [Problema de GitHub](https://github.com/magento/magento2/issues/40064) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [Integración] [Cierre de compra] Directivas dependientes actualizadas en la plantilla de correo electrónico de pago con errores

Se ha actualizado la plantilla de correo electrónico de pago errónea para gestionar correctamente las directivas de dependencia.
La corrección garantiza que la dirección de envío y el método de envío se muestren correctamente cuando corresponda.
Anteriormente, estos campos faltaban en los correos electrónicos de pago fallidos.

_AC-15363 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/36d4d6fb)_

#### El descuento en el envío gratuito de [Cloud] no se eliminó correctamente cuando el carro de compras ya no cumple los requisitos

El Subtotal (Excluido Impuestos) en la regla de precio del carro de compras ahora incorporará descuentos de reglas anteriores.

_ACP2E-3973 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Se ha encontrado un pedido duplicado para el mismo cliente en Multishipping

Las solicitudes simultáneas para realizar pedidos con varias direcciones de envío ya no resultan en pedidos duplicados para el mismo cliente

_ACP2E-4117 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Carro de compras y cierre de compra, pedido, producto

#### El correo electrónico de la tarjeta regalo se envía aunque falle la factura del pedido

Antes de la implementación de esta corrección, los correos electrónicos con tarjetas de regalo se enviaban después de crear la factura. Sin embargo, después de aplicar la corrección, los correos electrónicos con tarjetas regalo ahora se envían después de que las facturas se hayan guardado y confirmado correctamente.

_ACP2E-3905_

### Carro y cierre de compra, Seguridad

#### [CLOUD] está obteniendo 404 para el archivo JS en la página de cierre de compra al primer intento después de implementar el parche sri

Anterior a la corrección, los mixins no se habrían cargado en el carro y se habrían cerrado cuando las opciones minificar y agrupar estaban habilitadas. Después de la corrección, todos los mixins deben cargarse según lo esperado.

_ACP2E-4128 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catálogo

#### Problemas con el alcance del precio y config.php

En Magento 2.4.2, cambiar el ámbito del precio a través de config.php no actualiza correctamente el valor is_global en catalog_eav_attribute para el atributo de precio.
Como resultado, los precios de los productos siguen siendo globales y no se pueden guardar por sitio web, incluso cuando el alcance de los precios se establece en sitio web.
La solución requiere actualizar manualmente la columna is_global en la base de datos, lo que no es ideal para entornos de producción.
Este comportamiento es coherente con el diseño predeterminado de Magento, donde el ámbito del precio es Global o Sitio web, pero no por vista de tienda.

_AC-13857: [problema de GitHub](https://github.com/magento/magento2/issues/33559)_

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

#### La generación dinámica de imágenes genera un gran número de imágenes

Después de la corrección, las imágenes se generarán únicamente para los sitios web a los que esté asignado el producto.

_ACP2E-3927 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fab20b00)_

#### Error 500 en front-end debido a que la estructura de diseño incorrecta se almacena en caché en el diseño

Se ha corregido un problema que se producía cuando una página devolvía un código de error 500, debido a que una estructura de diseño incorrecta se almacenaba en caché en el diseño

_ACP2E-4040 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### Error de validación para el campo de importe de descuento de la regla de precio de catálogo en Actualización programada

Anteriormente, antes de solucionar este problema, para la actualización de programación de la regla de precio de catálogo, si el importe de descuento es by_fixed, no se validó correctamente debido a la regla validation-number-range. Una vez aplicada esta corrección, la validación funciona correctamente para la regla de precio de catálogo de precio fijo.

_ACP2E-4054 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Los productos se muestran como agotados después de deshabilitarlos

Después de la corrección, los productos deshabilitados no están presentes en el widget de productos.

_ACP2E-4136 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [Nube] errores con entradas duplicadas (temp_category_descendientes_%)

Se ha corregido un problema con las entradas duplicadas durante la creación de actualizaciones programadas para entornos con un alto número de categorías anidadas

_ACP2E-4159 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a1c57b2e)_

### Catálogo, GraphQL

#### Cálculo de descuento no válido de GraphQl

GraphQL ahora muestra correctamente los porcentajes de descuento y los precios base cuando los precios de catálogo están configurados para incluir impuestos. Anteriormente, se producían errores de redondeo, como mostrar el 19,99 % en lugar del 20 %.

_ACP2E-3993 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Catálogo, Producto

#### Los productos relacionados a través de una regla de producto relacionada no aparecen en PDP a través de GraphQL

Anteriormente, antes de aplicar esta corrección, la regla de producto relativa devolvía vacío/nulo para un producto que coincidía con la regla. Una vez aplicada esta corrección, la regla relativa para el producto devuelve correctamente los productos coincidentes.

_ACP2E-3949_

### Contenido

#### graphql (magento 2.4.6-p4 ): error al intentar obtener la página de cms sin estado activo

Se ha corregido un problema en el cual la consulta de GraphQL para una página de CMS deshabilitada devolvía un error interno del servidor.
Ahora, la consulta obtiene una respuesta adecuada sin errores.

_AC-12302 - [Problema de GitHub](https://github.com/magento/magento2/issues/38877) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [GraphQl] Bucle infinito de consulta de ruta

Este ticket corrigió el problema en el que una consulta de ruta de GraphQL con una ruta de solicitud y una ruta de destino idénticas provocaban un bucle infinito y, finalmente, se agotaba el tiempo de espera.
En 2.4.9-alpha3, la consulta ahora devuelve la respuesta de error correcta en lugar de crear un bucle.

_AC-14269 - [Problema de GitHub](https://github.com/magento/magento2/issues/39707) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### Cambie la constante IMAGE_FILE_NAME_PATTERN a public visible para obtener más flexibilidad

La constante IMAGE_FILE_NAME_PATTERN en GenerateRenditions.php se hizo pública para permitir a los desarrolladores una mayor flexibilidad al trabajar con representaciones de imágenes. La corrección está incluida en Magento 2.4.9-alpha3 con cobertura de prueba de integración y unidad completa.

_AC-15338 - [Problema de GitHub](https://github.com/magento/magento2/issues/39733) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### La previsualización de ensayo de contenido no funciona con los resultados de búsqueda

La búsqueda en la vista previa de ensayo ahora devuelve productos según el ámbito seleccionado. Anteriormente, la búsqueda devolvía resultados en el ámbito predeterminado, sin tener en cuenta el almacén seleccionado.

_ACP2E-4095_

#### Page Builder: problema de lógica de condición de producto (la lógica OR se comporta incorrectamente al mostrar menos productos)

El widget de productos del generador de páginas ahora devuelve el resultado correcto cuando se utiliza un atributo con ámbito global en la condición &quot;Coincidir con cualquiera&quot;

_ACP2E-4096 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Cliente/ Clientes

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

#### [Problema] Hacer que la firma del método sea coherente con la interfaz

La firma del método para getAttributes ahora es coherente con su interfaz, lo que evita cualquier error al sobrescribir el método. Anteriormente, las incoherencias en la firma del método provocaban errores al intentar sobrescribir el método getAttributes.

_AC-11578 - [Problema de GitHub](https://github.com/magento/magento2/issues/38501) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31955)_

#### [Problema]: Corrija la regla validate-emails para el componente ui.

El sistema ahora valida correctamente varias direcciones de correo electrónico introducidas en los componentes de la interfaz de usuario, asegurándose de que cada correo electrónico se recorta y valida correctamente. Anteriormente, el sistema utilizaba un método incorrecto para recortar las direcciones de correo electrónico, lo que podía provocar errores de validación.

_AC-11719 - [Problema de GitHub](https://github.com/magento/magento2/issues/38528) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33470)_

#### [Problema]: quite métodos redundantes

Calidad del código: se han eliminado los métodos redundantes en los componentes de operaciones asincrónicas y ventas que solo llamaban a métodos principales sin agregar funcionalidad, lo que mejora la capacidad de mantenimiento del código.

_AC-11915 - [Problema de GitHub](https://github.com/magento/magento2/issues/29748) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/29147)_

#### la validación xsd falla en los archivos etc/adminhtml/system.xml que contienen comentarios debajo de los elementos de campo.

Esta PR corrige las definiciones de esquema XML en phpstorm para el nodo de comentarios

_AC-12945 - [Problema de GitHub](https://github.com/magento/magento2/issues/39148) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 utiliza paquetes dev que no siguen el control de versiones semántico

Magento 2.4.8 requiere versiones dev de pdepend/pdepend y phpmd/phpmd (3.x-dev) para compatibilidad con PHP 8.4.
Estas versiones de desarrollo entran en conflicto con las herramientas de terceros que esperan paquetes compatibles con SemVer, lo que impide algunas actualizaciones.
Una solución temporal consiste en alias de las versiones de desarrollo en composer.json (por ejemplo, &quot;3.x-dev as 3.99.0&quot;), lo que permite la compatibilidad al tiempo que satisface las versiones semánticas.
Esto garantiza la compatibilidad con PHP 8.4 y evita conflictos hasta que haya versiones estables disponibles.

_AC-14519: [problema de GitHub](https://github.com/magento/magento2/issues/39796)_

#### API de REST: Llamada a una función de miembro getVideoProvider() en nulo

Se ha corregido un problema en el cual llamar a la API secundaria configurable de productos devolvía un error de servidor interno 500 si un producto secundario solo tenía un vídeo de YouTube y ninguna otra imagen.
El error se debe a una referencia nula en ExternalVideoEntryConverter.
Ahora, la API devuelve correctamente productos secundarios con entradas de la galería de medios, incluidos datos de vídeo externos, sin arrojar errores.
Esto garantiza la recuperación adecuada de todos los tipos de medios para los productos secundarios a través de la API de REST.

_AC-15046: [problema de GitHub](https://github.com/magento/magento2/issues/40021)_

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

#### Actualizar vínculos de Readmes y documentos de módulos y correcciones

_AC-15340 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec9459d0)_

#### [Problema] registra el complemento no declarado solo si no está deshabilitado

Esta PR corrige y registra el complemento que no está declarado y no se utiliza (habilitado y sin instancia).

_AC-15386 - [Problema de GitHub](https://github.com/magento/magento2/issues/40086) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework versión 103.0.8-p2: La clase EmailMessage llama a un método inexistente

_AC-15446 - [Problema de GitHub](https://github.com/magento/magento2/issues/40170) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/059fd469) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e9412b24)_

#### [Magento 2.3.x] Parches de datos/esquemas getAliases() causa errores durante `setup:upgrade`

getAliases() causa errores durante la instalación :upgrade, este PR corrige lo mismo

_AC-15559 - [Problema de GitHub](https://github.com/magento/magento2/issues/31396) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38239)_

#### Tipo esperado &#39;Magento\Customer\Api\Data\GroupInterface&#39;. Se ha encontrado &#39;Magento\Customer\Model\Group&#39;.

Se ha corregido un problema por el cual al guardar un grupo de clientes a través de GroupRepositoryInterface mediante GroupFactory se producía un error de tipo.
Anteriormente, el repositorio esperaba GroupInterface, pero se pasaron las instancias del modelo Group, lo que provocó un error grave.
Ahora, los grupos de clientes se pueden guardar correctamente a través del repositorio asegurando la correcta implementación de la interfaz.
Esto resuelve las advertencias del IDE y los errores de tiempo de ejecución al crear o actualizar mediante programación grupos de clientes.

_AC-6909 - [Problema de GitHub](https://github.com/magento/magento2/issues/36269)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8349 - [Problema de GitHub](https://github.com/magento/magento2/issues/37266) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37016)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8350 - [Problema de GitHub](https://github.com/magento/magento2/issues/37265) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37015)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8359 - [Problema de GitHub](https://github.com/magento/magento2/issues/37262) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37012)_

#### [Problema] Elimina la etiqueta `@author` prohibida

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8362 - [Problema de GitHub](https://github.com/magento/magento2/issues/37259) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37009)_

#### [Problema] Elimina la etiqueta `@author` prohibida de `Magento_Backup` y `Magento_Bundle`

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8367 - [Problema de GitHub](https://github.com/magento/magento2/issues/37244) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36979)_

#### [Problema]: se corrigió el nombre de variable en la búsqueda de catálogos

El sistema ahora asigna un nombre correcto a las variables en el módulo del motor de búsqueda, lo que mejora la claridad y el mantenimiento del código. Anteriormente, se usaba un nombre de variable irrelevante, $defaultCountry, en el módulo del motor de búsqueda, lo que causaba confusión.

_AC-9215 - [Problema de GitHub](https://github.com/magento/magento2/issues/37810) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33533)_

#### [QUANS]Problema de servidor causado potencialmente por clave de acceso S3 no válida

Las credenciales incorrectas de AWS S3 ya no hacen que las páginas se carguen infinitamente en la tienda.

_ACP2E-3890 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [QUANS] [Cloud] Minify js no funciona

Los siguientes archivos JS se minifican ahora de forma completa y correcta cuando se habilita la minificación JS: mage/backend/tabs.min.j, jquery/jquery.validate.min.js y Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Como resultado, la validación del campo Clase CSS de Page Builder funciona según lo esperado.

_ACP2E-3925 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47721be6)_

#### El trabajo de cron no borra la tabla de la base de datos, lo que provoca una interrupción debido al bloqueo de Galera

La limpieza de tablas de registro de cambios se está ejecutando en lotes para evitar operaciones de eliminación pesadas.

_ACP2E-3995 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### JS no minificado a veces carga ignorando &quot;habilitar minificaciones de js&quot;

Antes de la corrección, incluso si tenía la minificación habilitada, algunos de los archivos JS se solicitaban sin el prefijo &quot;min&quot;, lo que resultaba en un código de estado 404. Después de la corrección, cuando la minificación está habilitada, no se solicitan recursos JS no minificados.

_ACP2E-4058 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### El atributo de fecha del grupo de atributos personalizado no muestra el selector de fecha en el administrador

Se ha corregido un problema por el cual la ventana emergente del calendario para los atributos de fecha aparecía fuera de pantalla cuando se asignaba a grupos de atributos personalizados.

_ACP2E-4060 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### GraphQL de pedidos de clientes: recuperar las categorías de productos para el producto asociado &quot;no es visible de forma individual

Antes de la corrección, si el pedido contenía un producto oculto, sus categorías mostraban una matriz vacía en la respuesta de GraphQL de pedidos del cliente.
Ahora, después de la corrección, las categorías de productos se incluyen en la respuesta de una solicitud de GraphQL de pedido del cliente incluso si el producto está oculto.

_ACP2E-3945 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

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

### GraphQL, inventario/MSI

#### Discrepancias en la mutación mergeCart de GraphQL

Después de la corrección, la solicitud de GraphQL de los carros de combinación comprueba correctamente la cantidad del producto, teniendo en cuenta la configuración de stock.

_ACP2E-4184 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Seguridad

#### El restablecimiento de la contraseña del cliente mediante GraphQL no cumple las restricciones

Se ha resuelto un problema en el cual las solicitudes de restablecimiento de contraseña de cliente realizadas a través de mutaciones de GraphQL no cumplían con las restricciones de restablecimiento de contraseña configuradas en Tienda > Configuración > Clientes > Configuración del cliente > Opciones de contraseña. Esta configuración ahora se aplica correctamente.

_ACP2E-3992 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importación/exportación

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

### Inventario/MSI

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

### Pedido

#### Magento 2.4.8 GraphQL: los elementos de pedido tienen un formato incorrecto de fecha_pedido

Se ha corregido un problema en el cual el campo fecha_pedido de la respuesta de GraphQL se devolvía en formato aaaa-mm-dd.
Ahora, fecha_pedido se muestra correctamente en formato dd-mm-aaaa.

_AC-14431 - [Problema de GitHub](https://github.com/magento/magento2/issues/39805) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### El correo electrónico de envío no se envía cuando se envía desde la vista de pedidos del administrador a pesar de estar habilitado en la configuración de la tienda

El sistema ahora envía un correo electrónico de confirmación de envío, ya que está activado en la configuración de la tienda en la que se realizó el pedido.

_AC-14563 - [Problema de GitHub](https://github.com/magento/magento2/issues/39861) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39897)_

#### El filtrado por fecha no funciona debido a nombres de campo ambiguos

En Magento 2.4.7-p6, se informó que filtrar la cuadrícula de pedidos por fecha causaba un error debido a las uniones con módulos Braintree.
El problema involucraba consultas que unían tablas braintree_transaction_details y sales_order al aplicar filtros de fecha.
Adobe Commerce Engineering revisó el caso, pero no pudo reproducir el error en el entorno.
El comportamiento esperado es que el filtrado por fecha devuelva pedidos que coincidan con el filtro sin errores.

_AC-15037: [problema de GitHub](https://github.com/magento/magento2/issues/40024)_

#### Magento2: No se puede crear la regla de promoción

Esta corrección de PR, obtenemos
Modelo \Magento\Catalog\Model\ResourceModel\Eav\Attribute en lugar de \Magento\Catalog\Model\ResourceModel\Eav\Attribute en el método \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [Problema de GitHub](https://github.com/magento/magento2/issues/12176) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30479)_

#### Cancelar redirecciones de factura a 404

La cancelación de la factura realizada con el tipo No Capturar ya no lleva a la página 404.

_ACP2E-4001 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Los trabajos de Cron del archivo de ventas están causando problemas de bloqueo de BD

Antes de la corrección, las consultas de DELETE sin enlazar ubicadas en el archivo cron estaban causando problemas con Galera. Ahora, después de la actualización, las consultas de eliminación se ejecutan con límites.

_ACP2E-4010_

#### Problema con pedidos actualizados con opciones configurables que utilizan la API de REST

Conservar las opciones de producto existentes en los artículos de pedidos de venta al actualizar un pedido a través de puntos finales de API de REST.

_ACP2E-4061 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

### Otras herramientas para desarrolladores

#### [Problema] al limpiar el código no utilizado.

El sistema ahora elimina el código no utilizado con respecto a las importaciones no utilizadas.

_AC-10980 - [Problema de GitHub](https://github.com/magento/magento2/issues/38424) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33499)_

#### [Problema] de accesibilidad: los roles WAI-ARIA anidan incorrectamente en el menú

El sistema ahora genera accesibilidad de faro sin funciones WAI-ARIA anidando mal en el error de menú y el informe debe ser verde

_AC-15082 - [Problema de GitHub](https://github.com/magento/magento2/issues/40045) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38617)_

#### Error de consola en la previsualización de correo electrónico en el administrador de Magento

El sistema no generará ningún error de consola al previsualizar la plantilla de correo electrónico

_AC-9245 - [Problema de GitHub](https://github.com/magento/magento2/issues/37820) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37933)_

### Pagos

#### IPN desconocidos de PayPal abusa del procesador IPN de la aplicación

El controlador IPN ahora ignora los tipos IPN no admitidos o desconocidos. En lugar de devolver un error 500, registra el problema y continúa procesando sin interrupción.

_ACP2E-4049 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Error al pagar el token de tarjeta guardada de PayflowPro

Los ID de transacción de PayPal PayFlow Pro (PNREF) ahora son válidos para su uso en transacciones de referencia durante un periodo fijo de 12 meses. Una vez caducada, la tarjeta guardada ya no se mostrará y debe añadirse de nuevo. Anteriormente, la validez estaba determinada por la fecha de caducidad de la tarjeta de pago utilizada en la transacción original.

_ACP2E-4064 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

### Rendimiento

#### [Problema] La actualización usa el control de caché inmutable para el sitio estático

Esta PR mejora el rendimiento al no validar el contenido estático en cada carga de página hasta y a menos que cambie.

_AC-15171 - [Problema de GitHub](https://github.com/magento/magento2/issues/39486) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39484)_

#### [NUBE] no puede agregar productos a las categorías

Se ha mejorado el rendimiento al agregar un producto a una categoría mediante Visual Merchandiser.

_ACP2E-3946 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/29653b1d)_

#### [Cloud] cache_invalidate a más de 10 000 registros

Anteriormente, la caché se borraba en cada visita al PLP o al carro de compras, lo que provocaba una sobrecarga de rendimiento innecesaria. La caché de reglas de Target ya no se invalida en estas páginas, lo que mejora la eficacia de la exploración.

_ACP2E-4059_

### Precio

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

#### La etiqueta &quot;Tan bajo como&quot; se sigue mostrando para un producto configurable para el caso de prueba AC-6158

Productos configurables implementados y verificados (P1-P7) con sus respectivas variaciones y asignaciones de categorías. Se garantizó la visualización correcta del precio de la tienda y el comportamiento de la etiqueta &quot;Tan bajo como&quot; para los productos de la categoría C.

_AC-10847 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Error De Registro Adicional Al Solicitar Un Producto A Través Del Repositorio

Mensajes de error mejorados para ProductRepository::get y getById cuando no se encuentra un SKU o ID.
Anteriormente, las excepciones no proporcionaban ningún contexto sobre el SKU o el ID que provocaba el error.
Ahora, el mensaje de excepción incluye el SKU o ID que falta, lo que ayuda a depurar y mejorar la experiencia del desarrollador.
Este cambio no afecta a ningún comportamiento funcional de la API.

_AC-15199 - [Problema de GitHub](https://github.com/magento/magento2/issues/40090) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Productos simples sin asignar cuando el producto configurable está editado por una función limitada

Antes de esta corrección, si un usuario administrador restringido guardaba un producto configurable que contenía productos simples a los que el usuario administrador no tenía acceso, se eliminaban del producto configurable al guardarlo. Después de la corrección, el producto configurable se conserva como guardado de un administrador de derechos completo.

_ACP2E-4081_

#### El rendimiento de generación de mapas de sitio de [Cloud] se ha degradado significativamente

La generación de mapas del sitio para productos con imágenes ya no experimenta una ralentización exponencial. Anteriormente, la generación de mapas del sitio para tiendas con la inclusión de imágenes habilitada resultaba en tiempos de procesamiento largos.

_ACP2E-4153 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e457c5e2)_

### Promoción

#### Error al obtener descuentos de artículo de pedido aplicados a para el pedido del cliente mediante la solicitud de cliente de GraphQl

Anteriormente, cuando se aplicaban descuentos_a para el pedido del cliente a través de GraphQl, se observaba un error de servidor interno de solicitud del cliente que ahora es fijo y se recuperan los datos adecuados del pedido del cliente con el descuento aplicado

_AC-14888 - [Problema de GitHub](https://github.com/magento/magento2/issues/39963) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fe72c407)_

#### Error al obtener el código de cupón de artículo de pedido para el pedido del cliente mediante la solicitud de cliente de GraphQl

Se ha corregido un problema por el cual la recuperación de pedidos con detalles de cupones a través de GraphQL devolvía un error interno del servidor.
Ahora, la consulta se ejecuta correctamente y devuelve la información de cupón correcta en la respuesta.

_AC-14889 - [Problema de GitHub](https://github.com/magento/magento2/issues/39962) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Clave de matriz no definida en ProductRepository getById

El problema se producía cuando se llamaba a ProductRepository::getById() con un ID no válido como 123abc, lo que provocaba un error de &quot;Clave de matriz no definida&quot;.
Después de la corrección en Magento 2.4.9-alpha3, estas solicitudes ahora devuelven correctamente una página 404 en lugar de iniciar una excepción.
El control de calidad se confirmó con ID válidos y mal formados, y no se observaron más problemas.

_AC-15345 - [Problema de GitHub](https://github.com/magento/magento2/issues/40146) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/68a45d0a)_

#### La generación de mapas de sitios de [Cloud] nunca termina

Antes de la corrección, la generación del mapa del sitio no podía finalizar correctamente si el catálogo contenía más de un millón de productos. Después de la corrección, la generación del mapa del sitio terminará con una asignación de memoria más baja y con hasta un millón de productos por tienda.

_ACP2E-3902 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/52f46328)_

#### El conmutador de tienda [Cloud] no funciona de EN a FR para la página de preguntas más frecuentes

Se ha corregido un problema que causaba que, al cambiar entre vistas de tienda, se redirigiera a los usuarios a la página principal en lugar de a la página de CMS traducida correspondiente. El conmutador de tienda ahora comprueba las reescrituras de URL en el almacén de destino para garantizar una redirección correcta (por ejemplo, la página de preguntas frecuentes en inglés → la página de preguntas frecuentes en francés).

_ACP2E-4112_

### Ensayo y previsualización

#### La previsualización de la actualización de ensayo se interrumpe al cerrar la compra al utilizar un dominio de administración diferente

Un cliente puede iniciar sesión y ver su carro de compras en el modo de vista previa de la tienda cuando la URL de la base de la tienda es diferente de la URL de administración.

_ACP2E-3906_

#### Visualización del tiempo del panel de ensayo de contenido incorrecta

Ahora, los filtros de fecha &quot;Hora de inicio&quot; y &quot;Hora de finalización&quot; del &quot;Panel de ensayo de contenido&quot; muestran la fecha y la hora correctas. Anteriormente, se mostraba una fecha y hora incorrectas después de seleccionar la fecha y la hora en el selector de fechas

_ACP2E-3969_

#### El ámbito muestra diferentes vistas de tienda durante la vista previa de los productos y las categorías de actualización programada

Anteriormente, se corrigió que el vínculo de vista previa de categorías y productos no se generaba para la tienda correcta. Después de esta corrección, el vínculo de vista previa selecciona automáticamente el almacén en el que se creó la vista previa.

_ACP2E-4053_

### Marco de IU

#### [Problema] Elimina la etiqueta `@author` prohibida de `Magento_Backend`

Esta PR elimina la etiqueta `@author` de la base de código

_AC-8814 - [Problema de GitHub](https://github.com/magento/magento2/issues/37522) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36976)_
