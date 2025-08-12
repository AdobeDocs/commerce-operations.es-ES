---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4173'
ht-degree: 0%

---
# Notas de la versión de Magento Open Source (v2.4.9-alpha2)

## Se han corregido problemas en la versión 2.4.9-alpha2

Hemos corregido 109 problemas en el código principal Magento Open Source 2.4.9-alpha2. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

#### Precio Especial Hasta la Fecha se ha validado incorrectamente en applySpecialPrice

El sistema funciona bien con respecto al precio especial y el precio especial del producto caducará en la fecha establecida por el administrador o el sistema de terceros por la API de REST

_AC-13130 - [Problema de GitHub](https://github.com/magento/magento2/issues/39169) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39690)_

#### El cuerpo o los parámetros de solicitud mal formados provocan un &quot;error interno del servidor&quot;

_AC-746 - [Problema de GitHub](https://github.com/magento/magento2/issues/32784) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### Los pedidos &quot;base_row_total&quot; y &quot;row_total&quot; muestran el precio de un solo artículo en la respuesta de la API de REST

La respuesta de la API de REST para los detalles del pedido ahora contiene valores correctos para los atributos &quot;base_row_total&quot; y &quot;row_total&quot; en caso de que se hayan pedido varios artículos iguales

_ACP2E-3874 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### API, Pedido

#### [NUBE] Problema de información de pedido con la apariencia total de la fila para la 000075568 de pedido

Corrige el problema por el que el valor row_total_incl_tax en la respuesta de la API de pedidos se devolvía como un valor residual cercano a cero en lugar de 0,00 cuando un artículo se descontaba por completo.

_ACP2E-3950 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Cuenta

#### Problema al actualizar el correo electrónico del cliente en el Panel de administración con los dominios ö y .swiss

_AC-13409 - [Problema de GitHub](https://github.com/magento/magento2/issues/39394) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### El conmutador habilitado para suscribirse al boletín informativo no funciona por sitio web o tienda

El sistema gestiona correctamente la suscripción a la newsletter cuando tenemos varios sitios web o vistas de tiendas cuando está desactivada a nivel global

_AC-14283 - [Problema de GitHub](https://github.com/magento/magento2/issues/39751) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39752)_

#### [Problema] eliminó la divulgación del correo electrónico

El sistema muestra ahora Mostrar un mensaje de error que indica un correo electrónico incorrecto si el correo electrónico introducido no es necesario para confirmar la cuenta, independientemente de si el cliente existe o no.

_AC-14561 - [Problema de GitHub](https://github.com/magento/magento2/issues/39574) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39570)_

### IU de administración

#### El valor de FTP en la página del carro de compras y en la página del producto son diferentes para las mismas configuraciones de un producto simple

_AC-13066 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Las opciones de atributos multiselect/select no se pueden guardar cuando los módulos de muestras están desactivados

_AC-13071 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### El valor de FTP en la página del carro de compras y en la página de productos es diferente para las mismas configuraciones de un producto dinámico

_AC-13075 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8953613e)_

#### Color de desplazamiento no aplicado en cuadrículas estáticas en el administrador

Los colores de desplazamiento ahora se aplican según lo esperado en las filas de las cuadrículas estáticas de administración.[GitHub-35358](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [Problema de GitHub](https://github.com/magento/magento2/issues/35358) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35384)_

#### [Ensayo2] Las tarjetas almacenadas no están visibles en el panel de administración

Corrige el problema en el cual la opción de pago &quot;Tarjeta almacenada&quot; ya no aparecía en el formulario de colocación de pedidos back-end después de una actualización.

_ACP2E-3830 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### error de validación de campo de empresa para cierre de compra de invitado

_AC-14987 - [Problema de GitHub](https://github.com/magento/magento2/issues/40011) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

### Paquete

#### Excluir archivos JS del Editor Hugerte de la salida agrupada entre temas

_AC-15128 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/43648891) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2bc584af)_

### Carro y cierre de compra

#### Faltan validaciones de cantidad de front-end de producto agrupado

El sistema funciona correctamente y muestra un error de validación cuando se intenta agregar una cantidad negativa y una cantidad máxima

_AC-13524 - [Problema de GitHub](https://github.com/magento/magento2/issues/39479) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39480)_

#### El prefijo de invitado no se ha guardado en la dirección de oferta 2.4.8

_AC-14705 - [Problema de GitHub](https://github.com/magento/magento2/issues/39915) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f1adb44e)_

#### [Problema]: establece el precio en el artículo del presupuesto en lugar de en base_price

El sistema gestiona correctamente el precio del artículo de oferta establecido en base_price en lugar del precio si tiene varias monedas en un sitio web en el front-end

_AC-9985 - [Problema de GitHub](https://github.com/magento/magento2/issues/38094) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36878)_

#### [Nube] Pedidos recientes no aparecen en la vista de otra tienda si los pedidos se crean en una vista de tienda

Se ha resuelto un problema en el cual la página &quot;Mi cuenta&quot; no mostraba pedidos recientes de otras vistas de tienda dentro de la misma tienda. La lógica de recuperación de pedidos se ha actualizado para garantizar una visibilidad del pedido coherente en todas las vistas de la tienda, alineándose con el comportamiento de la página &quot;Mis pedidos&quot;.

_ACP2E-3807 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

#### cantidad mostrada como  0 en la sección del carro de compras del cliente de administración al agregar productos PAQUETE  

La sección Carro de compras de Actividades del cliente ahora muestra la cantidad correcta. Anteriormente, la cantidad se mostraba como 0.

_ACP2E-3872 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Carro y cierre de compra, GraphQL

#### Error al asignar el mensaje al código de error al realizar el pedido mediante GraphQL

Las llamadas de GraphQL para realizar un pedido de un carro de compras inexistente o inactivo ahora devuelven correctamente los códigos de error CART_NOT_ACTIVE o CART_NOT_FOUND en todas las vistas de tienda, lo que corrige un problema en el que los mensajes de error traducidos anteriormente resultaban en un código UNDEFINED.

_ACP2E-3942 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Carro y cierre de compra, GraphQL, inventario/MSI

#### El atributo is_available de CartItemInterface devuelve el valor &quot;false&quot; incluso cuando las existencias vendibles son altas

El atributo is_available devuelve el valor &quot;True&quot; cuando el stock vendible es alto. Anteriormente, siempre devolvía false.

_ACP2E-3885 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Catálogo

#### Error de ámbito en el recurso de URL del catálogo (_getCategories)

Esta PR agrega una alternativa al ámbito predeterminado si no hay ningún valor definido en el ámbito de almacén en el recurso de URL de categoría.

_AC-11011 - [Problema de GitHub](https://github.com/magento/magento2/issues/38393) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38394)_

#### [Problema] Comprobar si OpenGraph puede mostrar el precio

El sistema está funcionando bien cuando utilizamos el complemento que oculta el precio y con este cambio de precio no es visible en la etiqueta OG.

_AC-11635 - [Problema de GitHub](https://github.com/magento/magento2/issues/38512) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38510)_

#### [Error] en la API de REST: la actualización de precios especiales no establece valores para todas las vistas de tiendas

_AC-13671 - [Problema de GitHub](https://github.com/magento/magento2/issues/39521) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [\Magento\ConfigurableProduct\Model\Product\Type\Configurable] error de PHP desapercibido

Esta PR cambia un nombre de variable de bucle para añadir correctamente los datos &quot;_cache_instance_product_ids&quot; en el producto dado para utilizarlo en llamadas posteriores.

_AC-14159 - [Problema de GitHub](https://github.com/magento/magento2/issues/39641) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39642)_

#### [Principal] [El cambio de tamaño de la imagen en la nube] consume más de 400 GB de espacio en disco

Después de la corrección, el comando `catalog:images:resize` utilizado con el indicador —skip_hidden_images no generará cachés de imágenes para sitios web donde las imágenes no están presentes.

_ACP2E-3869 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### El CountryID proporcionado no existe: Irlanda (IE)

Después de la corrección, los códigos postales de Irlanda están disponibles para buscar ubicaciones de recogida.

_ACP2E-3932 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Catálogo, Rendimiento

#### Las categorías de administración se cargan muy lentamente

El rendimiento de carga de categorías ha mejorado considerablemente. Anteriormente, se tardaba tanto en cargar la categoría que provocaba un problema de tiempo de espera.

_ACP2E-3891 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Catálogo, precios

#### Descuento de regla de precio de catálogo incorrecto aplicado al producto secundario

Corrige el problema en el que la regla de precio de catálogo para la variación se anula con el producto configurable principal, en caso de que ambas reglas tengan la misma prioridad.

_ACP2E-3693 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a20a6ff2)_

### Catálogo, Buscar

#### La solicitud de RestApi &#39;/rest/default/V1/categories?searchCriteria%5Bpage_size%5D=1&#39; falla con un error de tiempo de espera

_AC-13358 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

### Contenido

#### Después de la actualización a magento 2.4.7 p2 no se pueden ver los archivos cargados recientemente galería de medios

_AC-13262: [problema de GitHub](https://github.com/magento/magento2/issues/39275)_

#### Al eliminar completamente una imagen de la galería, se mantiene establecidas las funciones/tipos de ámbito (base/pequeña/en miniatura) y después de volver a agregar las funciones/tipos &quot;antiguos&quot; aparecen

El sistema funciona según lo esperado en los ámbitos del almacén. Las imágenes heredan las funciones y los tipos de la nueva imagen añadida según el ámbito predeterminado

_AC-13556 - [Problema de GitHub](https://github.com/magento/magento2/issues/39481) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39680)_

#### [Pequeño error] El filtro del panel de administración `listing component` no se puede alcanzar cuando el valor del campo contiene `\`

El sistema funciona correctamente cuando filtramos el título de la página con una barra diagonal (p. ej.: Magento\Store)

_AC-13661 - [Problema de GitHub](https://github.com/magento/magento2/issues/39513) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39535)_

#### &quot;La página de CMS con el ID &quot;0&quot; no existe&quot; inundación de registro

El sistema funciona según lo esperado después de crear un usuario administrador y cuando creamos una nueva página, system.log no tiene ningún mensaje de error

_AC-14254 - [Problema de GitHub](https://github.com/magento/magento2/issues/39743) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39746)_

#### Los widgets de vínculo al catálogo utilizan una URL incorrecta

El sistema ahora gestiona correctamente los widgets después de añadir el vínculo de producto del catálogo y el vínculo de categoría del catálogo, y también muestra las direcciones URL correctas en el origen HTML

_AC-14437 - [Problema de GitHub](https://github.com/magento/magento2/issues/39464) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39710)_

#### El componente Producto del Page Builder no funciona si el usuario no tiene permiso de Widget

Antes de la corrección, al acceder a un widget sin permisos, la página generaba un error genérico y mostraba un GIF de &quot;carga&quot;. Ahora, después de la corrección, se muestra una ventana modal con &quot;Lo sentimos, necesita permisos para ver este contenido&quot;. Mensaje.

_ACP2E-3664 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### El orden de los widgets del producto de Page Builder no se aplica en GraphQL

Corrige el problema en el cual la respuesta de consulta &quot;ruta&quot; de GraphQL no devolvía productos en el orden correcto dentro de un tipo de contenido de productos de Page Builder.

_ACP2E-3898 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Problema de visualización de precios en tiendas que no están en inglés debido a la versión de la biblioteca de la UCI

Después de la corrección, el precio del producto se muestra correctamente en la configuración regional hebrea (Israel).

_ACP2E-3938 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Actualizando configuración de diseño de código de tienda borrado

Corrige el problema por el que al actualizar el código de vista de tienda se borraban los ajustes de Configuración de diseño debido a que la caché de configuración no se actualizaba correctamente.

_ACP2E-3941 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Marco

#### Error al ejecutar el comando setup:upgrade con el déclencheur de BD personalizado

_AC-11487: [problema de GitHub](https://github.com/magento/magento2/issues/38481)_

#### El formulario de entidad de sitio web/grupo/tienda no se puede ampliar con varios elementos de formulario de valor para atributos de extensión

Esta PR permite que los elementos de formulario de varios valores envíen datos al sitio web, al grupo o al formulario de tienda.

_AC-11657 - [Problema de GitHub](https://github.com/magento/magento2/issues/24070) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/24094)_

#### [Problema] Quitar uso de resolución de ámbito

Esta PR resuelve la configuración de la URL de administración de forma global en lugar de la tienda actual

_AC-11736 - [Problema de GitHub](https://github.com/magento/magento2/issues/38566) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38554)_

#### Exposición de la versión de Magento a través de la ruta de instalación con la configuración predeterminada de Nginx

El sistema funciona ahora según lo esperado y no expone la versión exacta de Magento que está ejecutando el sitio

_AC-13205 - [Problema de GitHub](https://github.com/magento/magento2/issues/39227) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39228)_

#### [Problema] dirección de presupuesto de refactorización no valida el método

Esta PR incluye mejoras de legibilidad para el método doValidate.

_AC-13214 - [Problema de GitHub](https://github.com/magento/magento2/issues/38230) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38219)_

#### Opción de Magento: ¿magento-init-params nunca se utiliza al ejecutar cli?

_AC-13231 - [Problema de GitHub](https://github.com/magento/magento2/issues/39248) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/132b9e68)_

#### declaración de tipo incorrecta de getItemsByColumnValue

El sistema ahora define correctamente el parámetro de entrada $value como un tipo primitivo, no como una matriz, en la función getItemsByColumnValue, asegurándose de que la función devuelve la colección esperada. Anteriormente, si se utilizaba una matriz con un único valor como parámetro de entrada, la función devolvía null y los IDE la marcaban como error.

_AC-13240 - [Problema de GitHub](https://github.com/magento/magento2/issues/33070) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33120)_

#### Claves de caché asociadas con FPC en implementaciones de varias tiendas de Magento 2.4.7

_AC-13719 - [Problema de GitHub](https://github.com/magento/magento2/issues/39456) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ae6f305b)_

#### API de REST de Magento que expone PII

_AC-13904: [problema de GitHub](https://github.com/magento/magento2/issues/39336)_

#### La indexación parcial deja de funcionar para los clientes con un gran número de actualizaciones

_AC-14424 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Investigar el uso estricto es innecesario dentro de los módulos

_AC-14517 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### El mecanismo MView ignora silenciosamente los errores en la ejecución del déclencheur

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

#### [Problema] Elimina el código relacionado con Microsoft IIS

Esta PR limpia el código relacionado con Microsoft IIS según la documentación de requisitos del sistema de Magento, que indica que el sistema operativo Microsoft Windows no es compatible

_AC-14702 - [Problema de GitHub](https://github.com/magento/magento2/issues/39910) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39894)_

#### Error de sintaxis de Magnifier.js

La funcionalidad del Ampliador del sistema debe seguir funcionando como antes y magnifierOptions no debe estar disponible en el ámbito global

_AC-14722 - [Problema de GitHub](https://github.com/magento/magento2/issues/36200) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39321)_

#### Modo detallado de Backport en el comando CLI `setup:db:status`

_AC-14807 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Envío de correo SMTP con tls y 2.4.8

_AC-14883 - [Problema de GitHub](https://github.com/magento/magento2/issues/39947) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3717e6cb) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8b453942) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d3ea191d)_

#### [Problema]: corrija el problema de concurrencia en la implementación de contenido estático

Esta PR corrige un error en el que varios procesos simultáneos giran para gestionar el mismo paquete de temáticas, según cómo se definan las temáticas con sus elementos principales.

_AC-14944 - [Problema de GitHub](https://github.com/magento/magento2/issues/39990) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39954)_

#### [Problema] Elimina el código de compatibilidad heredado para las versiones de PHP &lt; 8.1

Esta solicitud de extracción elimina el código diseñado para ejecutarse en PHP &lt;8.1.
Además, se ha eliminado la comprobación de la disponibilidad del contacto PHP_VERSION_ID, ya que está disponible en todas las versiones de PHP

_AC-14971 - [Problema de GitHub](https://github.com/magento/magento2/issues/39891) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39882)_

#### FPC no funciona al iniciar sesión

_AC-14999 - [Problema de GitHub](https://github.com/magento/magento2/issues/40007) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/)_

#### [Problema] mejora la administración de errores en SchemaBuilder

Esta PR mejora la gestión de mensajes de error del esquema de la base de datos. Nos ayuda a identificar el problema sin una depuración pesada.

_AC-15020 - [Problema de GitHub](https://github.com/magento/magento2/issues/39816) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39799)_

#### Error en la prueba de integración en SYNC PR para 2.4.9-alpha2-development debido a la modificación CliStateTest

_AC-15136 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2d0f8066)_

#### Corrección de errores de tipo PHP8.1

Los productos asociados ahora se inicializan en una matriz vacía en lugar de en false cuando el modo de procesamiento estricto no está activo o cuando la información del producto está disponible. Este cambio garantiza que la lógica subsiguiente que maneja los productos asociados se comporte de manera consistente, mejorando la estabilidad y la previsibilidad en el proceso de preparación del producto.

_AC-6017 - [Problema de GitHub](https://github.com/magento/magento2/issues/35808) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35842)_

#### [Problema] Quitar la etiqueta `@author` prohibida del marco de trabajo (parte 3)

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8343 - [Problema de GitHub](https://github.com/magento/magento2/issues/37270) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37020)_

#### [Problema] Use la promoción de la propiedad de constructor en el módulo Enviar gráfico de amigos SQL

El sistema ahora utiliza la promoción de la propiedad constructora en el módulo GraphQL &quot;enviar amigo&quot;, lo que mejora la legibilidad del código y reduce la complejidad. Anteriormente, el módulo utilizaba propiedades que ocupaban numerosas líneas, lo que hacía que el código fuera más complejo y menos legible.

_AC-8346 - [Problema de GitHub](https://github.com/magento/magento2/issues/37235) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37197)_

#### [Problema] Elimina la etiqueta `@author` prohibida de `Magento_Downloadable`

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8355 - [Problema de GitHub](https://github.com/magento/magento2/issues/37251) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37001)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad y coherencia del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8358 - [Problema de GitHub](https://github.com/magento/magento2/issues/37264) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37014)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8360 - [Problema de GitHub](https://github.com/magento/magento2/issues/37261) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37011)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8361 - [Problema de GitHub](https://github.com/magento/magento2/issues/37260) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37010)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que mejora la calidad general del código. Anteriormente, la presencia de esta etiqueta en algunos módulos infringía los estándares de codificación establecidos.

_AC-8363 - [Problema de GitHub](https://github.com/magento/magento2/issues/37258) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37008)_

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

#### Problema con la actualización 2.4.7-p5 debido a la nueva validación añadida

Se ha corregido un problema en la clase SchemaBuilder por el que una clave de matriz indefinida &quot;column&quot; provocaba un bloqueo durante la creación o las actualizaciones del esquema. Esto ocurría al procesar datos de tabla que no incluían una clave de &quot;columna&quot;.

_ACP2E-3871 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

#### Error de obsolescencia de PHP8.4: E_USER_ERROR después de actualizar a Adobe Commerce 2.4.8

Los escenarios orientados al cliente no se ven afectados por la corrección.

_ACP2E-3963 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

### Marco de trabajo, Buscar

#### Opensearch 2.19.1 ilegal_argument_exception en categorías de un precio

Opensearch ya no está lanzando un ilegal_argument_exception en las categorías que contienen todos los productos con el mismo precio. Anteriormente, tiene esta excepción &quot;[del parámetro ] no puede ser negativo&quot;.

_ACP2E-3896 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Los elementos de la lista de deseos no se comparten entre las vistas de tiendas de un sitio web en una solicitud de GraphQL

Antes de la corrección, los elementos de la lista de deseos se filtraban por ID de tienda. Ahora, después de la corrección, los elementos de la lista de deseos se filtran por sitio web.

_ACP2E-3987 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, Producto

#### Falta media_type de graphql del producto en MediaGalleryInterface

La solicitud de MediaGallery GraphQL ahora incluye el campo &quot;tipos&quot; para tipos de imagen de producto. Anteriormente, este campo &quot;tipos&quot; no existía en la solicitud de MediaGallery GraphQL.

_ACP2E-3880 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ad96f6a)_

### Inventario/MSI

#### No hay ninguna tienda disponible después de redirigir a la página de inicio y cerrar la compra

La tienda seleccionada anteriormente ahora se preseleccionará en el envío &quot;Elegir en tienda&quot; si el cliente navega a la página de pago, luego vuelve a la página de inicio y, finalmente, a la página de cierre de compra. Anteriormente, después de volver repetidamente a la página de cierre de compra, se borraba la tienda seleccionada en &quot;Elegir en tienda&quot;.

_ACP2E-3793 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a20a6ff2) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/62c0d79b)_

### Pedido

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue[]) interrumpe customAttributes

_AC-10568: [problema de GitHub](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento reordenar -1 números de pedido

El sistema funciona según lo esperado y después de reordenar desde el backend, el número de pedido será de 8 dígitos únicos

_AC-12854 - [Problema de GitHub](https://github.com/magento/magento2/issues/39089) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39399)_

#### Se pierde la carga del archivo de opciones personalizadas del producto al cerrar la compra con la tarjeta de crédito Adobe

_AC-14306: [problema de GitHub](https://github.com/magento/magento2/issues/39647)_

#### Estado del pedido atascado durante el procesamiento

Antes de la corrección, al solicitar un paquete de producto con la opción &quot;Enviar juntos&quot; activada, el estado del pedido no cambiaba automáticamente a &quot;completo&quot; después de la factura y el envío. Ahora, después de la corrección, el estado del pedido cambia automáticamente a &quot;completo&quot; después de que se haya facturado y enviado.

_ACP2E-3947 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2a252ae6)_

#### Código OOTB de [Cloud]Magento: problema de configuración de plantilla de correo electrónico

Antes de la corrección, al utilizar el envío de correo electrónico asincrónico, los correos electrónicos de envío no eran coherentes con el pedido de la tienda. Ahora, después de la corrección, se entrega el pedido de correo electrónico de envío de tienda adecuado.

_ACP2E-3998 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Otras herramientas para desarrolladores

#### [Problema] Sugerencia de tipo incorrecta para el miembro protegido $_urlHelper

El sistema ahora corrige la sugerencia de tipo incorrecta con la correcta, que también se utiliza en el constructor

_AC-10716 - [Problema de GitHub](https://github.com/magento/magento2/issues/32503) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32496)_

### Rendimiento

#### [Problema] al actualizar Store.php

Esta PR mejora el rendimiento al omitir la resolución actual de la tienda.

_AC-14791 - [Problema de GitHub](https://github.com/magento/magento2/issues/39949) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38717)_

### Precio

#### El precio siempre es 0 para los artículos de producto agrupados sin precio dinámico en la API de resto de pedidos

_AC-11925 - [Problema de GitHub](https://github.com/magento/magento2/issues/38687) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7da46f52)_

### Product

#### Descuento porcentual en el precio de nivel y la regla de precio de catálogo calculados en el precio original sin las opciones seleccionadas.

_AC-12004: [problema de GitHub](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minCantidad de pedido de producto faltante permitida

El sistema funciona bien y el origen de la página muestra correctamente la cantidad mínima del producto

_AC-12909 - [Problema de GitHub](https://github.com/magento/magento2/issues/39142) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39480)_

#### Problema con la cuadrícula Opciones personalizables en la página de producto en el panel de administración

El sistema funciona según lo esperado al crear opciones personalizables con el menú desplegable de tipo

_AC-14003 - [Problema de GitHub](https://github.com/magento/magento2/issues/39640) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39694)_

#### Todos los elementos de otras listas de comparación de clientes se asignan al cliente después de iniciar sesión a través del administrador

Anteriormente, cuando un administrador utilizaba la función &quot;Iniciar sesión como cliente&quot; en el backend de, los productos de la lista de comparación de un cliente que había iniciado sesión anteriormente se asignaban incorrectamente al cliente suplantado actualmente.  Después de la corrección, la lista de comparación se carga correctamente para el cliente que ha iniciado sesión correctamente.

_ACP2E-3818 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### La actualización de product url_key mediante la API de REST no genera una reescritura de URL 301

Al actualizar la clave URL del producto mediante la API de REST, con la configuración &quot;Crear redireccionamiento permanente para URL si se ha cambiado la clave URL&quot; establecida en Sí, las reescrituras de URL del producto crean una redirección de la URL antigua a una nueva.

_ACP2E-3900 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Seguridad

#### El JS agrupado/combinado no forma parte de los hash de la SRI

Antes de la corrección, los archivos agrupados o combinados generados no se añadían a la lista de hash de la SRI. Ahora, los archivos se añaden correctamente a los hash de la SRI.

_ACP2E-3854 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Envío

#### [QUANS]: ¿Comprueba el módulo principal de Magento_Fedex si hay un token activo válido antes de enviar una solicitud para obtener uno nuevo?

Adobe Commerce ya no realiza muchas solicitudes al servicio de la API de FedEx para el token de acceso. Anteriormente, aunque el token de acceso sigue siendo válido, Adobe Commerce siempre realiza nuevas solicitudes a la API de FedEx, lo que provocaba un problema de limitación de velocidad.

_ACP2E-3930 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4ca73607)_

### Ensayo y previsualización

#### No se puede previsualizar la actualización programada del producto con los permisos de categoría habilitados

Antes de la corrección, un producto que se habilitaría en el futuro no se mostraba en el modo de vista previa. Ahora se mostrará incluso si el estado actual es desactivado.

_ACP2E-3786 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7accebfa)_

#### Falta la validación para el campo de importe de descuento de la regla Precio de catálogo

Anteriormente, el campo descuento_importe en la actualización del programa de ensayo no se validaba correctamente con las reglas de validación actuales. Sin embargo, después de aplicar la corrección, el campo descuento_importe se validará correctamente.

_ACP2E-3867 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/462ede94)_

### Impuestos

#### Total de pedido incorrecto, la ronda no se aplica al cálculo del precio.

El sistema gestiona ahora correctamente el cálculo de price_after_discount, discount_amount y el importe de impuestos.
el total real del pedido

_AC-11389 - [Problema de GitHub](https://github.com/magento/magento2/issues/38455) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39687)_

### Marco de prueba

#### [Problema] Omitir lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/en...

El sistema ahora ignora el archivo &quot;env.php&quot; que se genera al ejecutar pruebas unitarias, asegurándose de que el estado de Git permanezca limpio después de ejecutar pruebas. Anteriormente, la ejecución de pruebas unitarias generaba un nuevo archivo &quot;env.php&quot;, lo que provocaba que el estado de Git mostrara un nuevo archivo encontrado y lo hacía parecer sucio.

_AC-13293 - [Problema de GitHub](https://github.com/magento/magento2/issues/39304) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37631)_

#### [Problema]: se ha corregido un problema de prueba de integración con el interceptor.

El sistema ahora identifica y administra correctamente \Magento\TestFramework\App\Config\Interceptor en la prueba de integración, lo que garantiza que la prueba pueda acceder a los datos necesarios incluso cuando exista un complemento en la clase. Anteriormente, el sistema no tenía en cuenta la posibilidad de que \Magento\TestFramework\App\Config fuera un \Magento\TestFramework\App\Config\Interceptor, lo que provocaba un error al intentar acceder a la propiedad $data.

_AC-13305 - [Problema de GitHub](https://github.com/magento/magento2/issues/39324) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37187)_

#### [Problema] MFTF: Enviando correo electrónico al formulario de un amigo con captcha habilitado

El caso de prueba aborda la funcionalidad del formulario &quot;Enviar por correo electrónico a un amigo&quot; cuando CAPTCHA está habilitado, lo que garantiza que el proceso de envío del formulario funcione correctamente con valores CAPTCHA incorrectos y correctos.

_AC-13492 - [Problema de GitHub](https://github.com/magento/magento2/issues/39462) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32830)_

#### [TestFramework] Los usos de TestCase::getTestResultObject no son válidos desde phpunit v10

_AC-13502: [problema de GitHub](https://github.com/magento/magento2/issues/39463)_

#### Fallos en las pruebas unitarias específicas del entorno en AC 2.4.7-p3

Este problema corrige los errores de las pruebas unitarias que no se reproducen en todas las versiones y entornos. Anteriormente, para corregir algunas pruebas unitarias, se producía un error debido a versiones de biblioteca diferentes o a la funcionalidad faltante agregada en una versión posterior.

_ACP2E-3712 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9ad7d277)_

### Marco de IU

#### WYSIWYG está vacío en las filas dinámicas

_AC-12336 - [Problema de GitHub](https://github.com/magento/magento2/issues/38893) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [Problema] tipo de error tipográfico de mime fijo

El sistema gestiona y fija correctamente el tipo de mime y el error tipográfico de la imagen gif

_AC-8001 - [Problema de GitHub](https://github.com/magento/magento2/issues/36899) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36669)_

#### [Problema] Evitar el acceso directo a la lista de críticas

El sistema gestiona correctamente y Evita el acceso directo a la lista de críticas Ajax

_AC-9381 - [Problema de GitHub](https://github.com/magento/magento2/issues/37920) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33876)_

### Actualizaciones: herramienta de compatibilidad de actualización

#### Funcionalidad Obsoleta: Creación de la propiedad dinámica Magento\Framework\Acl::$_roleRegistry

_AC-12343: [problema de GitHub](https://github.com/magento/magento2/issues/37469)_
