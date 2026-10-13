---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '10868'
ht-degree: 0%
---
# Problemas corregidos de Adobe Commerce (v2.4.10-alpha1)

## Se han corregido problemas en la versión 2.4.10-alpha1

Hemos corregido 169 problemas en el código principal Adobe Commerce 2.4.10-alpha1. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

#### [Problema] TypeError en Creditmemo\Validation\QuantityValidator causado por min() con cantidad de cadena

Para estabilizar las canalizaciones de registro financiero y evitar errores de solicitud de API durante los reembolsos de pedidos automatizados masivos, se han agregado protecciones de fundición de tipo de datos a la fábrica de notas de crédito de ventas internas y a las capas de validación.

_AC-16056 - [Problema de GitHub](https://github.com/magento/magento2/issues/40302) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40429) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40303)_

#### La actualización de atributos de la API de REST falla sin attribute_id

Se ha corregido un problema por el cual la actualización de un atributo de producto existente a través de la API de REST fallaba cuando no se proporcionaba attribute_id. La API ahora identifica correctamente el atributo con el attribute_code de la URL y lo actualiza correctamente.

_AC-16424 - [Problema de GitHub](https://github.com/magento/magento2/issues/40458) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Mostrar un error de autenticación cuando las credenciales de Adobe Stock no son válidas

Los administradores ahora ven un error de autenticación cuando las credenciales de Adobe Stock no son válidas.

_AC-17123_

#### La muestra visual se elimina al actualizar la opción mediante la API de REST

Para proteger la integridad de los datos del catálogo y optimizar las integraciones automatizadas, se ha resuelto un error en la capa de administración de muestras de EAV en la que los valores de muestras visuales o textuales existentes se borraban de forma involuntaria durante las actualizaciones de opciones estándar.

_AC-9199 - [Problema de GitHub](https://github.com/magento/magento2/issues/37794) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40872)_

#### La API de precios de nivel masivo falla en el lote completo cuando falta un SKU

Anteriormente, la API de actualización de precios de nivel masivo (POST /V1/products/tier-price) no entregaba la solicitud completa cuando no existía ningún SKU en la carga útil, lo que dejaba SKU válidas sin actualizaciones. Ahora, los SKU válidos se procesan correctamente, mientras que los SKU que faltan se registran como errores por elemento, por lo que una sola entrada incorrecta ya no anula todo el lote.

_ACP2E-4998 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### La actualización de atributos falla con la etiqueta Valor que coincide con el ID de valor de opción existente

Se ha corregido un problema en el cual no se podía crear una nueva opción de atributo de producto desplegable/multiselección a través de la API de REST cuando su etiqueta coincidía con el ID de una opción existente. Anteriormente, la API devolvía un error &quot;ya existe&quot; (y podía devolver el ID de opción incorrecto) aunque la misma opción se pudiera crear correctamente a través de la IU del administrador.

_ACP2E-5107 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### API, importación y exportación

#### La API de REST permite precios de productos negativos mientras que la IU de administración los bloquea

La importación de productos a través del extremo de la API de REST ahora rechaza los valores negativos para atributos de tipo de precio (campos price, special_price, cost y MSRP relacionados), lo que es coherente con el comportamiento de la importación de la IU de administración. Anteriormente, la API aceptaba precios negativos en silencio y los persistía.

_ACP2E-4941 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### API, Pedido

#### Función de límite de velocidad de pedido incompatible con el backend de caché de Valkey

Anteriormente, esta limitación de velocidad fija se omitía silenciosamente y se permitía a cada solicitud pasar independientemente del límite configurado. Después de la corrección, las solicitudes que exceden el límite configurado se rechazan correctamente con HTTP 429.

_ACP2E-4899 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Cuenta

#### [Problema] corregido: etiqueta de contraseña incorrecta del formulario de inicio de sesión

Se ha corregido un problema por el cual el campo Contraseña de la página de inicio de sesión del cliente tenía una asociación de etiquetas incorrecta. La etiqueta de contraseña ahora identifica correctamente el campo Contraseña, lo que permite que se identifique correctamente con las herramientas de prueba automatizadas.

_AC-16193 - [Problema de GitHub](https://github.com/magento/magento2/issues/40353) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### [Problema] Validar tipo de entrada de front-end para cargas de archivos

Las cargas de archivos de direcciones de clientes ahora validan que el tipo de entrada del atributo de destino es un archivo o una imagen antes del procesamiento, por lo que no se puede abusar de los atributos de texto y otros atributos que no sean archivos como destinos de carga. Los intentos de carga no válidos devuelven un error de validación claro en lugar de fallar de forma impredecible o aceptar tipos de archivo no permitidos.

_AC-17076 - [Problema de GitHub](https://github.com/magento/magento2/issues/40795) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40583)_

#### El token de cliente generado en el sitio web A se puede utilizar en el sitio web B en la configuración de clientes con alcance de sitio web

Para aplicar un aislamiento estricto de los datos de los clientes en instancias de varios sitios web, se ha resuelto una brecha de seguridad en la capa de autenticación de GraphQL, donde los tokens se validaban incorrectamente a través de límites independientes.

_AC-17299 - [Problema de GitHub](https://github.com/magento/magento2/issues/40847) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40858)_

#### [Problema] corrigió el desuso de PHP 8.5: usar nulo como parámetro clave para array_key_exists()

Se ha corregido un problema en PHP 8.5 en el cual el inicio de sesión del cliente durante la comprobación de invitado fallaba debido a una llamada obsoleta array_key_exists() con una clave nula. El inicio de sesión del cliente ahora funciona correctamente sin generar el error de obsolescencia.

_AC-17395 - [Problema de GitHub](https://github.com/magento/magento2/issues/40875) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problema] magento/magento2: Agregue traducciones i18 a requestPasswordResetEmail y resetPassword Mutaciones de GraphQL

Para garantizar una experiencia de tienda sin encabezado completamente localizada, se han agregado las funcionalidades de traducción de internacionalización (i18n) a los extremos de la API de recuperación de cuentas de cliente

_AC-9356 - [Problema de GitHub](https://github.com/magento/magento2/issues/29658) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/28950)_

### IU de administración

#### El panel debe mostrar Últimos 7 días de forma predeterminada cuando se utilizan datos agregados

Se ha corregido un problema por el que el panel se mostraba Hoy de forma predeterminada cuando se habilitaban los datos de ventas agregados. El panel ahora muestra los últimos 7 días de forma predeterminada al utilizar datos agregados.

_AC-13799 - [Problema de GitHub](https://github.com/magento/magento2/issues/28152) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### El valor de FTP en la página del carro de compras y en la página del producto son diferentes para las mismas configuraciones de un producto simple

Se ha corregido un problema por el cual los valores de Impuesto de producto fijo (FPT) se mostraban de forma diferente en las páginas de producto y carro de compras para la misma configuración de impuestos. Los valores de FTP ahora se muestran de forma coherente en las páginas del producto, catálogo, minicarrito y carro de compras.

_AC-17007 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Implementación de configuración diferida

Optimización del rendimiento que mejora el rendimiento de carga de la configuración al resolver de forma diferida los datos de configuración del sistema con ámbito a la vez que conserva el comportamiento de configuración existente.

_ACP2E-4751 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/65f660bd)_

#### El editor HugeRTE bloquea los emojis: error de validación de JavaScript

Se ha corregido el problema por el cual HugeRTE bloqueaba el guardado de contenido que contenía emojis utf8mb4 (p. ej. 🔵⚪🔴) al editarlo dentro de modelos de tipo de contenido de PageBuilder (Texto, Banner, Diapositiva). Anteriormente, la configuración de validación wysiwyg para estos formularios modales resolvía `allowUtf8mb4` en `false`, lo que provocaba que el editor rechazara los caracteres UTF-8 de 4 bytes incluso en instalaciones en las que la base de datos era totalmente compatible con utf8mb4.

_ACP2E-4822 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/f2691e17)_

#### El administrador restringido no puede eliminar clientes después de la actualización

Se ha corregido un problema en el cual el administrador restringido no podía eliminar clientes después de la actualización, con un aviso rojo en la parte superior de la cuadrícula del cliente que decía: &quot;Se necesitan más permisos para ver este elemento&quot;.

_ACP2E-4838_

#### El administrador cierra la sesión cuando ve clientes con libretas de direcciones grandes en la página de edición de clientes en el Panel de administración

Se ha corregido un problema que se producía cuando el administrador cerraba la sesión de los clientes que tenían libretas de direcciones grandes en la página de edición de clientes del Panel de administración

_ACP2E-4875 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Los pedidos no aparecen en la cuadrícula de ventas

Se ha corregido un problema por el que los nuevos pedidos se retrasaban en aparecer en las cuadrículas de ventas cuando la indexación de cuadrícula asíncrona estaba habilitada, debido al restablecimiento del cursor de reconciliación una vez que se alcanzó la entidad más reciente. Las nuevas entradas ahora aparecen en la cuadrícula en la siguiente ejecución de cron.

_ACP2E-4893 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Falta el filtro de productos asignados de [Cloud] en la cuadrícula de productos de la categoría cuando Magento_VisualMerchandiser está habilitado

Se ha corregido el problema por el cual el filtro &quot;Asignado&quot; no aparecía en la cuadrícula Agregar productos modal Buscar todos los productos cuando Visual Merchandiser estaba habilitado. Anteriormente, los usuarios administradores no tenían forma de filtrar los productos por su estado asignado/no asignado en ese modal, lo que dificultaba la identificación de qué productos ya estaban en la categoría.

_ACP2E-4974_

#### El registro de acciones no muestra el número de devolución ni el ID de devolución para las acciones relacionadas con la devolución

Se ha corregido un problema por el cual el número de devolución/ID de devolución no se mostraba en las entradas del registro de acciones para las acciones de administración relacionadas con la devolución. Anteriormente, las acciones como ver o guardar una autorización de devolución de material se registraban en el registro de acciones sin ningún identificador de devolución, a diferencia de las acciones relacionadas con pedidos que mostraban correctamente el número de pedido.

_ACP2E-5050_

#### &quot;Utilizar valor predeterminado&quot; desmarcado para Precio y Clase de impuesto en el producto de administración guardado en el ámbito de vista de tienda

Los usuarios administradores restringidos ahora pueden guardar productos en el ámbito de la vista de tienda sin perder el estado &quot;Usar valor predeterminado&quot; para los atributos Precio, Estado y Clase de impuesto. Anteriormente, si se guardaba un producto como administrador restringido (con edición de estado y precio denegada), se desmarcaba silenciosamente la opción &quot;Utilizar valor predeterminado&quot; para esos campos, lo que provocaba que se escribieran invalidaciones en el nivel de vista de tienda incluso cuando no se pretendía ninguna.

_ACP2E-5081_

### IU de administración, pedido

#### Precio incorrecto mostrado para un producto agrupado en Administración Crear pedido cuando dos productos agrupados comparten el mismo producto simple

Se ha corregido un problema en el cual el precio de un producto agrupado en Administración Crear pedido se calculaba incorrectamente cuando dos productos agrupados que comparten el mismo producto simple se configuraban sin añadirse al carro de compras.

_ACP2E-4965 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### IU de administración, marco de IU

#### Magento2 redirige a la página principal en lugar de mostrar un error con una declaración de menú incorrecta

Para optimizar el flujo de trabajo de desarrollo de extensiones y garantizar una carga back-end estable, se ha resuelto un defecto de enrutamiento estructural en el que las declaraciones de menú de administración no válidas activaban errores de bucle de explorador silencioso en lugar de mostrar mensajes de diagnóstico procesables.

_AC-7543 - [Problema de GitHub](https://github.com/magento/magento2/issues/36632) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40881)_

### Análisis / Informes

#### [QUANS] ¿Es posible mostrar el nombre y el ID de correo electrónico del cliente en la tabla KPI de cliente en Informes avanzados?

Adobe Commerce ahora incluye el nombre, segundo y apellido del cliente en los datos exportados a Informes avanzados, lo que permite que la tabla KPI de cliente muestre el nombre del cliente. Anteriormente, solo se exportaba un identificador de cliente codificado, por lo que los comerciantes no podían identificar a los clientes por su nombre en los informes avanzados.

_ACP2E-3928 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### INSERCIÓN completa en sales_bestsellers_aggregated_month

Rendimiento mejorado para el cron aggregate_sales_report_bestsellers_data.

_ACP2E-4559 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### La carga útil de evento de Añadir al carro de compras está en el formato de comercio electrónico mejorado de Universal Analytics heredado en lugar del formato de comercio electrónico GA4.

Antes de la corrección, los eventos de comercio electrónico enviados a Google Analytics 4 a través de Google Tag Manager utilizaban el formato heredado de Universal Analytics y faltaban varios eventos de cierre de compra. Después de la corrección, todos los eventos de comercio electrónico utilizan el formato GA4 correcto y se rastrea el funnel de cierre de compra completo.

_ACP2E-5176 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

### B2B

#### placeNegotiableQuoteOrderV2 devuelve total.total_shipping = null para pedidos realizados desde una oferta negociable

Se ha corregido un problema por el cual placeNegotiableQuoteOrderV2 devolvía un total de envío nulo para los pedidos realizados desde una oferta negociable con envío pagado. La API ahora devuelve correctamente el importe de envío, que coincide con el cargo de envío incluido en el total del pedido.

_AC-18083_

#### [B2B] Precios de opciones de paquete faltantes en los detalles de la oferta después de convertir la oferta a pedido

Se ha corregido un problema en el cual los precios de opciones de productos agrupados faltaban en la página de detalles de oferta negociable después de que la oferta se convirtiera en un pedido.

_ACP2E-5055_

### B2B, Pedido

#### Ayuda para limpiar más de 59M tablas de presupuesto (sales_clean_quote no se puede ejecutar)

Se corrigió el problema en el cual el trabajo cron de `sales_clean_quotes` agotaba el tiempo de espera en instancias con tablas de comillas grandes. Anteriormente, la consulta de limpieza seleccionaba todas las columnas de la tabla `negotiable_quote` de forma innecesaria, lo que provocaba que MySQL realizara un orden de archivos completo en millones de filas; y cada comilla se eliminaba individualmente a través de la capa del modelo PHP, lo que agravaba el coste de rendimiento.

_ACP2E-4891 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

### Carro y cierre de compra

#### Agregar al carro de compras notificaciones para productos relacionados

Se ha corregido un problema en el cual la notificación Agregar al carro de compras no incluía el producto relacionado al agregar un producto y su producto relacionado.
La notificación ahora muestra los nombres de ambos productos agregados al carro de compras.

_AC-11976 - [Problema de GitHub](https://github.com/magento/magento2/issues/27164) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### [Problema] al actualizar CartRepositoryInterface.php

Se ha actualizado CartRepositoryInterface.php para declarar las excepciones que se pueden producir al guardar un carro de compras. Esto mantiene la interfaz coherente con la implementación de guardado del carro de compras subyacente.

_AC-13323 - [Problema de GitHub](https://github.com/magento/magento2/issues/39328) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### [Error]: el campo de la compañía en la dirección de envío se ha establecido en nulo en la configuración de varias tiendas al agregar una nueva dirección durante el paso de envío del pago y envío

Se ha corregido un problema en el cual el campo Compañía no se guardaba cuando los clientes agregaban una nueva dirección de envío durante el cierre de compra en una configuración de varias tiendas. El valor de Compañía ahora se guarda correctamente en la oferta, el pedido realizado y la libreta de direcciones del cliente.

_AC-13456 - [Problema de GitHub](https://github.com/magento/magento2/issues/39424) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

#### PayPal > Los datos del cliente no coinciden (prefijo, nombre, apellido)

Se ha corregido un problema por el cual los detalles del nombre del cliente se asignaban incorrectamente durante el flujo de pago de PayPal SEPA. Ahora, el prefijo, el nombre y los apellidos se rellenan correctamente en el orden sin discrepancias.

_AC-15366 - [Problema de GitHub](https://github.com/magento/magento2/issues/39061) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### Indicador free_shipping incorrecto para productos virtuales

Se ha corregido un problema por el cual el indicador free_shipping se establecía incorrectamente para productos virtuales cuando se añadían varios artículos al carro de compras. El indicador ahora se establece correctamente para todos los artículos cuando se aplica la regla de envío gratuito aplicable.

_AC-15648 - [Problema de GitHub](https://github.com/magento/magento2/issues/40184) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Complemento de invitado al carro: la sección de minicarro/datos de cliente del &quot;carro&quot; debajo del carro de compras de informes está vacía a pesar de que el elemento se mantiene correctamente

Se ha corregido un problema en el cual el minicarrito de invitado no reflejaba los artículos inmediatamente después de agregarle un producto. El contador y el menú desplegable del minicarrito ahora se actualizan correctamente y los productos añadidos se muestran en el carrito según lo esperado.

_AC-17973 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### Mensajes de error en línea del complemento al carro de compras de AJAX perdidos en la semántica role=&quot;alert&quot;

Se ha corregido un problema por el cual los mensajes de error de complementos al carro de compras de AJAX eran visibles en la tienda, pero los lectores de pantalla no los anunciaban. Los errores de complementos al carro de compras ahora se muestran dentro de una región accesible role=&quot;alert&quot; para ofrecer una compatibilidad de accesibilidad adecuada.

_AC-18036 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2b218686)_

#### Descartar reglas subsiguientes para el importe de envío

Para garantizar precios promocionales precisos y el estricto cumplimiento de las reglas de descuento configuradas, se ha resuelto un error en la calculadora de reglas de precios del carro de compras cuando los descuentos de envío de prioridad inferior se aplicaban incorrectamente

_AC-9612 - [Problema de GitHub](https://github.com/magento/magento2/issues/37985) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40869)_

#### Pedidos duplicados creados aunque se active el error

Se ha corregido un problema en el cual los pedidos se podían seguir realizando con una dirección de cliente no válida

_ACP2E-4774 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Impacto del rendimiento del producto configurable en el cierre de compra (totales-información, módulos de envío estimado)

Antes de la corrección, las solicitudes de cierre de compra, como la información de totales y los métodos de envío de estimación, podían resultar significativamente más lentas para los productos configurables con muchos productos secundarios cuando el primer niño vendible aparecía tarde en la lista secundaria. Después de la corrección, esta degradación del rendimiento ya no se produce y los tiempos de respuesta permanecen coherentes independientemente de la posición del primer hijo vendible.

_ACP2E-4805 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Totales del carro de compras recalculados en cada vista de página del carro de compras

Solicitudes de totales de carrito optimizadas en la página de carrito. Los totales del carro de compras se recalculan dos veces en cada vista de página del carro de compras.

_ACP2E-4817 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### Las reglas de validación de ciudad y calle de Atributo de dirección del cliente (EAV) entran en conflicto con las reglas de validación codificadas.

Se ha corregido un problema en el cual el validador de ciudades rechazaba incorrectamente los nombres de ciudades válidos que superaban los 100 caracteres (el límite de la base de datos es de 255) y en el que las direcciones de calles que superaban los 255 caracteres se podían truncar de forma silenciosa en la base de datos sin\
devolviendo un error de validación. Ambos validadores ahora aplican límites alineados con la restricción de columna de base de datos más estrecha en todas las tablas de direcciones.

_ACP2E-4861 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### El mensaje [Storefront] Add-to-cart &quot;requested qty is not available&quot; (La cantidad solicitada no está disponible) no se muestra intermitentemente en el PDP

Se ha corregido un problema por el que el mensaje de no disponibilidad de existencias (&quot;La cantidad solicitada no está disponible, reduzca la cantidad&quot;). no se mostraba intermitentemente en la página de detalles del producto después de un intento fallido de Agregar al carro de compras. Anteriormente, la página se podía actualizar de forma silenciosa sin comentarios de error cuando un comprador hacía clic repetidamente en Agregar al carro de compras para un producto cuyas existencias disponibles ya estaban totalmente reservadas en el carro de compras.

_ACP2E-5071 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### El carro de compras persistente se borra al expirar la sesión natural cuando Borrar persistencia al cerrar la sesión = Sí

Se ha corregido un problema por el cual el carro de compras persistente se borraba cuando caducaba la sesión del explorador. Anteriormente, con la opción Borrar persistencia al cerrar la sesión habilitada, una sesión caducada vaciaba el carro de compras y eliminaba la cookie persistente aunque el comprador no hubiera cerrado la sesión.

_ACP2E-5088 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### El customer_email de la cotización de invitado no se resincroniza desde la dirección de facturación después de restoreQuote() al reintentar el cierre de compra

Se ha corregido un problema en el cual al reintentar una comprobación de invitado fallida se realizaba el pedido con el correo electrónico introducido anteriormente en lugar del actualizado.

_ACP2E-5188 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Carro y cierre de compra, GraphQL

#### La API de GraphQL de oferta puede asignar objetos de divisa en lugar de códigos de divisa ISO a los campos de oferta

Se ha actualizado la API de GraphQL de oferta para asignar códigos de divisa ISO a los campos de divisa de oferta y tienda de una oferta en lugar de asignar objetos de divisa.

_ACP2E-5229 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catálogo

#### [Problema] mejoras en el archivo module.xml para los módulos Magento_ConfigurableProductGraphQl, Magento_MsrpConfigurableProduct, Magento_NewRelicReporting y Magento_Swatches.

Se ha optimizado la arquitectura de declaración de módulos al eliminar las dependencias redundantes de Magento_Catalog de los cuatro submódulos principales. Esta limpieza aborda la duplicación innecesaria en el árbol de dependencias, optimiza los cálculos del orden de carga de los módulos y mejora la capacidad de mantenimiento del marco de trabajo a largo plazo sin introducir cambios importantes.

_AC-10762 - [Problema de GitHub](https://github.com/magento/magento2/issues/30675) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30638)_

#### Posible fuga de memoria en la función getUsedProducts para configurables

Se ha corregido un problema en el cual el procesamiento de varios productos configurables provocaba que el tiempo de ejecución y el uso de memoria aumentaran con el tiempo.
Los productos configurables ahora se pueden procesar sin la ralentización progresiva y el aumento de la memoria.

_AC-10942 - [Problema de GitHub](https://github.com/magento/magento2/issues/37639) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/8c058c2e)_

#### El filtro Comprar por categoría está visible en las categorías que no son de anclaje

Se ha corregido un problema en el cual el filtro Comprar por categoría se mostraba en categorías que no eran de anclaje incluso cuando el filtro de categoría estaba deshabilitado en Administración.
El filtro ahora está oculto en la tienda según la configuración.

_AC-10945 - [Problema de GitHub](https://github.com/magento/magento2/issues/38379) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### El tipo de datos de applied_rule_ids en el artículo de oferta y de oferta es diferente

Para garantizar la coherencia absoluta del esquema de la base de datos y evitar discrepancias críticas en los datos del carro de compras en tiendas promocionales de gran volumen, las definiciones de promociones activas de seguimiento de columnas de datos se han expandido en las estructuras de cierre de compra principales.

_AC-14518 - [Problema de GitHub](https://github.com/magento/magento2/issues/39838) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40540)_

#### No se puede obtener el atributo `decimal` de ámbito de colección de productos si el precio tiene ámbito global

Para garantizar unos precios de tienda y un procesamiento de atributos precisos en configuraciones internacionales, se ha resuelto un error de recopilación de datos principales en el que los valores decimales específicos de la tienda se sustituían erróneamente por valores globales predeterminados.

_AC-15806 - [Problema de GitHub](https://github.com/magento/magento2/issues/40218) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40419)_

#### Gestión incorrecta de los parámetros GET

Para mejorar la estabilidad de la plataforma y proteger el funnel de cierre de compra, se ha agregado una capa de validación de entrada de nivel de bloque para evitar que las consultas de URL mal formadas bloqueen las páginas de productos de la tienda.

_AC-16262 - [Problema de GitHub](https://github.com/magento/magento2/issues/40405) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40433)_

#### Magento\SalesRule\Model\Plugin\QuoteConfigProductAttributes::afterGetProductAttributes en todas las consultas del carro de compras

Para reducir las tensiones de ejecución de la base de datos y eliminar las visitas a la base de datos no optimizadas durante las desprotecciones de los clientes, el complemento de configuración del producto de reglas de ventas se ha optimizado para ejecutarse de forma condicional y aprovechar las estructuras de almacenamiento en caché.

_AC-16559 - [Problema de GitHub](https://github.com/magento/magento2/issues/40226) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40251)_

#### [Problema] [PHPDOC] Funciones de corrección orderComment en Magento\Sales\Model\Order

Para eliminar las estrictas restricciones de escritura, mejorar la precisión del análisis estático y mejorar la experiencia del desarrollador bajo rigurosos motores de vinculación como PHPStan (Nivel 5 o superior), los bloques de documentación estructural en línea se han estandarizado dentro de los subsistemas principales de pedidos de ventas.

_AC-16759 - [Problema de GitHub](https://github.com/magento/magento2/issues/39575) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39572)_

#### [Problema] [Error] GraphQL SearchCriteriaValidator no cargado — eliminado por la anulación de matriz module-graph-ql di.xml

Para conservar una validación de consulta sólida y aplicar protecciones de plataforma, se ha resuelto un defecto de configuración de inyección de dependencia (ID) en el que la capa SearchCriteriaValidator se deshabilitaba de forma involuntaria.

_AC-16959 - [Problema de GitHub](https://github.com/magento/magento2/issues/40762) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40742)_

#### strpos() espera que el parámetro 1 sea una cadena, se da una matriz | magento/module-eav

Para proteger la estabilidad de la tienda y ofrecer una experiencia de detección de clientes ininterrumpida, se ha resuelto un defecto crítico de discrepancia de tipos en los motores de procesamiento de búsqueda de catálogos avanzados.

_AC-1706 - [Problema de GitHub](https://github.com/magento/magento2/issues/33588) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40422)_

#### Se crean registros de comillas vacías cuando el cliente visita una página

Visitar la página de producto en la tienda no crea registros de comillas vacías en algunas situaciones.
Anteriormente, se creaban registros de presupuesto vacíos cuando el cliente visita una página de producto en la tienda

_ACP2E-4682 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### El atributo &quot;Peso&quot; de la página de detalles del producto no muestra el sufijo de la unidad en la sección &quot;Información adicional&quot;

Corrige el problema por el cual el atributo Weight de la página de productos Storefront mostraba solamente un valor numérico sin procesar en la sección &quot;Información adicional&quot; o &quot;Más información&quot; sin la unidad de medida configurada (libras o kg).

_ACP2E-4808 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [Nube]: la activación de la regla de precio del catálogo no se reflejará en Live Search hasta la próxima vez que se force la resincronización: retraso de sincronización de fuente de precios

Se ha corregido un problema por el cual la activación de una regla de precios de catálogo no actualizaba los precios en Live Search hasta que se fuerza la resincronización más tarde. El indexador de fuente de precios podría ejecutarse antes de que el indexador de regla de catálogo del que depende hubiera finalizado y, por lo tanto, exportara precios antiguos. Los indexadores con dependencias no terminadas ahora se aplazan a la siguiente ejecución de cron, por lo que la fuente de precios siempre se ejecuta con precios actualizados.

_ACP2E-5029 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### [NUBE] problema de lógica de operador O regla de categoría de Adobe Commerce Cloud

El operador Contains ahora acepta varios valores separados por comas, evaluados como una coincidencia OR. Por lo tanto, una sola fila de regla puede coincidir con cualquiera de varios términos en lugar de uno solo.

_ACP2E-5061_

#### El texto alternativo (etiqueta) no se guarda para una imagen de producto recién agregada

Se ha corregido un problema por el cual el texto alternativo (etiqueta) de una imagen de producto recién cargada no se guardaba cuando se cambió el nombre del archivo cargado al guardarlo debido a un conflicto de nombres de archivo en la galería de medios. Anteriormente, los atributos de la función de imagen (image, small_image, thumbnail) se almacenaban correctamente, pero sus atributos *_label correspondientes se perdían sin aviso, lo que dejaba el texto alternativo vacío en las páginas de búsqueda y listado de tiendas. El controlador de creación de galería ahora vuelve a resolver el archivo con el nombre cambiado en su entrada de imagen de origen, por lo que la etiqueta se mantiene para todas las funciones de imagen asignadas. Como resultado, el texto alternativo introducido durante la creación del producto se guarda y procesa de forma fiable en la tienda.

_ACP2E-5216 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

#### Error de obsolescencia de PHP 8.5 &quot;null as array offset&quot; al abrir la página Añadir producto en el administrador cuando el usuario carece del recurso Editar estado del producto

Anteriormente, los usuarios administradores sin el permiso &quot;Editar estado del producto&quot; podían encontrar un error de obsolescencia &quot;nulo como desplazamiento de matriz&quot; al abrir la página Añadir producto. Esto se ha corregido para que la página se cargue correctamente independientemente de los permisos de estado del producto del usuario.

_ACP2E-5248 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Catálogo, GraphQL

#### [GraphQl] productos consultan problemas de filtro de precios con precios netos ingresados en adminhtml

Se ha corregido un problema en el cual la consulta de productos de GraphQL no tenía en cuenta los impuestos al aplicar un filtro de precios.
El filtro de precios ahora utiliza el precio con impuestos incluidos mostrado, de modo que solo se devuelven los productos dentro del rango de precios especificado.

_AC-6883 - [Problema de GitHub](https://github.com/magento/magento2/issues/36337) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

### Catálogo, Rendimiento

#### La canalización de indexación de Permisos de catálogo no cumple [CLOUD] customer_group_excluded_website

El índice de permisos de catálogo ahora excluye el sitio web que se excluye del grupo de clientes.

_ACP2E-5223_

### Catálogo, SEO

#### La categoría url_path no se sincroniza con el cambio url_key en todas las vistas de tienda

Anteriormente, si se cambiaba la clave URL de una categoría en el ámbito &quot;Todas las vistas de la tienda&quot;, las categorías descendientes con ámbito de tienda podían quedar con una url_path antigua o con un prefijo incorrecto, y si se editaba una categoría con su propia anulación de url_path específica de la tienda, se podía elegir la clave URL preeditada en lugar de la que se acababa de introducir. Esto ya está arreglado: la clave URL cambia correctamente en cascada a todos los descendientes con ámbito de tienda en el orden jerárquico correcto con la ruta principal correcta y se vuelve a calcular la anulación de url_path con ámbito de tienda de una categoría con su clave URL recién modificada, de modo que las URL con ámbito de tienda permanecen precisas inmediatamente después de guardar.

_ACP2E-5113 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

### Cloud, Framework

#### Regresión de rendimiento y almacenamiento de caché incorrecto con SymfonyL2 habilitado

Se ha corregido un problema en el cual la configuración de la ruta de almacenamiento de caché L1 como una ruta absoluta (por ejemplo, /dev/shm) provocaba que se redirigiera silenciosamente al directorio var/ y un problema de rendimiento independiente en el cual invalidar las etiquetas de caché en catálogos grandes podía causar retrasos significativos del tiempo de respuesta debido a una operación de bloqueo de Redis.

_ACP2E-4989 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Contenido

#### Las páginas de CMS creadas para diferentes sitios web muestran páginas incorrectas en front-end

Anteriormente, en configuraciones de varios sitios web en las que la clave de caché de la página de aterrizaje Restricción del sitio web no tenía ámbito por sitio web, lo que provocaba que se mostrara una página CMS incorrecta en la tienda del sitio web secundario. La clave de caché de WebsiteRestriction/Controller/Index/Stub.php ahora incluye correctamente el ID del sitio web actual resuelto mediante el administrador de tiendas.

_ACP2E-4593_

#### La evaluación de segmentos de clientes devuelve los clientes solo del primer sitio web en lugar de todos los sitios web asignados cuando el uso compartido de clientes globales está habilitado

Se ha corregido un problema en el cual la evaluación de segmentos de clientes devolvía clientes únicamente del primer sitio web en lugar de todos los sitios web asignados cuando el uso compartido global de clientes estaba habilitado.

_ACP2E-5079_

#### La solicitud de previsualización de Ajax del Page Builder devuelve el error 500 con la caché de traducción deshabilitada

La previsualización de PageBuilder ahora se procesa correctamente independientemente de si la caché de traducciones está habilitada o deshabilitada. Anteriormente, la previsualización de PageBuilder no se podía procesar cuando la caché de traducciones estaba deshabilitada.

_ACP2E-5118 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/606e12fd)_

#### Las cargas de GIF animadas se convierten a PNG cuando la opción Habilitar la Galería multimedia antigua está activada

Se ha corregido un problema por el cual las imágenes animadas de GIF cargadas a través de la galería de medios se convertían a PNG cuando la galería de medios heredada estaba habilitada. Anteriormente, cuando se activaba Habilitar redimensionado de front-end, los GIF animados cargados a través de la Galería multimedia antigua perdían su animación y se guardaban como archivos PNG estáticos. Los GIF animados ahora se cargan y almacenan en su formato original.

_ACP2E-5232 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Contenido / CMS

#### [Problema] Corrija la ficha de la galería de productos cuando una etiqueta de atributo de imagen contenga una comilla simple

Para garantizar una experiencia de administración de catálogos fiable e ininterrumpida en el panel de administración, se ha resuelto un defecto de formato de JavaScript que rompía completamente la interfaz del espacio de trabajo del producto back-end

_AC-16474 - [Problema de GitHub](https://github.com/magento/magento2/issues/40519) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40870)_

#### [Problema] Mejora el rendimiento cuando se accede a la dirección URL de la imagen cuyo tamaño se ha cambiado, pero aún no existe.

Para maximizar la capacidad de respuesta de la entrega de recursos, reducir significativamente la E/S del disco del servidor y evitar picos graves en el procesador del servidor, el subsistema de generación de imágenes de catálogo se ha optimizado para gestionar las URL de medios que faltan estrictamente bajo demanda.

_AC-16547 - [Problema de GitHub](https://github.com/magento/magento2/issues/40399) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40388)_

#### Regresión: el componente URI no codificado con UTF-8 sigue arrojando &quot;No se puede serializar el valor&quot; en CatalogWidget en 2.4.7-p5

Para eliminar los errores críticos de procesamiento causados por el tráfico web de producción incorrecto, el bloque de widgets del catálogo se ha reforzado para gestionar correctamente secuencias de datos que no son UTF-8 dentro de las direcciones URL solicitadas.

_AC-17264 - [Problema de GitHub](https://github.com/magento/magento2/issues/40824) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40825)_

#### `Using null as an array offset is deprecated, use an empty string instead` al editar el ámbito de configuración de diseño global

Se ha corregido un problema en el cual la edición del Alcance global en Contenido > Diseño > Configuración devolvía un error HTTP 500 en PHP 8.5 debido a un desplazamiento obsoleto de matriz nula. La configuración de diseño global ahora se abre correctamente sin el error.

_AC-17456 - [Problema de GitHub](https://github.com/magento/magento2/issues/40886) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Marco

#### SELECCIONAR de media_storage_file_storage cuando el almacenamiento de Media DB no esté en uso o desactivado

Para reducir la sobrecarga innecesaria de consultas de base de datos y eliminar las excepciones ruidosas del sistema, la capa de sincronización de archivos multimedia se ha optimizado para evitar las comprobaciones de almacenamiento de la base de datos cuando el sistema está configurado explícitamente para utilizar el sistema de archivos local

_AC-10586 - [Problema de GitHub](https://github.com/magento/magento2/issues/38116) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40480)_

#### Se produjo un error grave en el constructor de excepciones cuando el almacén de cookies es una matriz

Se ha corregido un problema por el cual un valor de cookie de almacenamiento no válido provocaba un error grave de PHP.
Magento ahora emite correctamente una excepción &quot;Parámetro de almacén no válido&quot; cuando la cookie de almacén contiene un valor no válido.

_AC-10888 - [Problema de GitHub](https://github.com/magento/magento2/issues/38365) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### [Problema] Usar constante estática en Magento\Customer\Model\Address\Config

Se ha corregido un problema en el cual las clases de configuración de direcciones personalizadas tenían que duplicar getFormats() para utilizar una ruta de plantilla de dirección personalizada. Las configuraciones de direcciones personalizadas ahora pueden definir su propia ruta de plantilla mediante una constante estática sin duplicar el método.

_AC-12906 - [Problema de GitHub](https://github.com/magento/magento2/issues/39135) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### No se puede usar processFilter en la colección de productos

Se ha corregido un problema en el cual la aplicación de varios filtros a una colección de productos mediante FilterProcessor provocaba un error de PHP. Ahora, las colecciones de productos se pueden filtrar correctamente con varias condiciones de filtro.

_AC-15018 - [Problema de GitHub](https://github.com/magento/magento2/issues/40014) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7aecc9f1)_

#### Problema potencial de rendimiento del indexador para catálogos grandes: inserción y bloqueo masivos de toda la tabla LC para identificar la última versión

Para salvaguardar el rendimiento de la base de datos en catálogos de gran escala empresarial, la canalización del indexador de la base de datos del sistema se ha endurecido para analizar las modificaciones de datos programadas en lotes enlazados, eliminando los bloqueos de base de datos de alta presión.

_AC-16238 - [Problema de GitHub](https://github.com/magento/magento2/issues/40331) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40546)_

#### [Problema] de mejora de rendimiento

Para eliminar la asignación de memoria innecesaria y reducir la sobrecarga de procesamiento en tiempo de ejecución, se han refactorizado varias rutinas de manipulación de cadenas principales para utilizar el comportamiento nativo de PHP optimizado.

_AC-16565 - [Problema de GitHub](https://github.com/magento/magento2/issues/40383) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40375)_

#### [Problema] Se corrigió la compatibilidad con GLOB_BRACE en sistemas Linux no GNU

Para garantizar una capacidad de implementación perfecta en entornos de virtualización ligeros, se ha corregido un error crítico de detección de rutas para restaurar completamente la compatibilidad de ejecución para sistemas que utilizan bibliotecas no GNU, como imágenes Alpine Linux Docker.

_AC-16568 - [Problema de GitHub](https://github.com/magento/magento2/issues/40552) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40538)_

#### Parámetros de marketing añadidos de nuevo en la consulta utilizados para la creación de identificadores FPC integrados

Para mejorar las tasas de aciertos de caché y eliminar las regresiones del rendimiento del servidor, se ha corregido un error estructural en el sistema nativo integrado de caché de página completa (FPC) en el que los parámetros de consulta de marketing y seguimiento se reintrodujeron accidentalmente en las firmas de identificadores de caché.

_AC-16583 - [Problema de GitHub](https://github.com/magento/magento2/issues/40350) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40349)_

#### Agregar compatibilidad con objetos simples con propiedades promocionadas en la comunicación de cola de mensajes

Para apoyar las prácticas modernas de desarrollo de PHP y simplificar los flujos de trabajo de arquitectura asincrónica, el motor de reflexión del marco de trabajo se ha mejorado para procesar de forma nativa los objetos de transferencia de datos (DTO) utilizando propiedades constructoras públicas, promocionadas y de solo lectura.

_AC-16672 - [Problema de GitHub](https://github.com/magento/magento2/issues/36660) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40457)_

#### [Problema] corregido: la introspección de tipo de columna real omite los procesadores sin signo/que aceptan valores NULL, usa valores predeterminados

Para garantizar un seguimiento preciso de la configuración del sistema, se ha resuelto un defecto de abstracción de la base de datos en el que los comandos de verificación del esquema declarativo informan perpetuamente de cambios de modificación pendientes para columnas DOUBLE UNSIGNED que carecen de atributos explícitos de precisión o escala.

_AC-16758 - [Problema de GitHub](https://github.com/magento/magento2/issues/40646) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40582)_

#### [Función]: admite el estado &quot;deshabilitado&quot; para las opciones individuales seleccionadas en la configuración de administración.

Para mejorar la flexibilidad del formulario back-end y proporcionar a los desarrolladores un control de diseño granular, se ha introducido compatibilidad a nivel de marco de trabajo para marcar etiquetas de opción individuales como no seleccionables dentro de los elementos del formulario.

_AC-16761 - [Problema de GitHub](https://github.com/magento/magento2/issues/40564) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40565)_

#### Rendimiento de ⚡: falta memoria en StoreManager y sobrecarga de complementos en el módulo de Store

Para reducir drásticamente la sobrecarga de ejecución de CPU y minimizar la pérdida innecesaria de memoria de las aplicaciones, se ha implementado una rutina de almacenamiento en caché de valor de configuración crítico para interceptar procesos de comprobación de almacenes redundantes.

_AC-16838 - [Problema de GitHub](https://github.com/magento/magento2/issues/40706) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40732)_

#### [Corrección de problemas]: elimine la ruta de código muerta de openssl_free_key() en JwkFactory

Para limpiar la deuda tecnológica estructural y alinear las herramientas de criptografía con los perfiles de ejecución modernos, se han eliminado los enlaces heredados de liberación de recursos del servidor de la utilidad de clave web JSON.

_AC-16958 - [Problema de GitHub](https://github.com/magento/magento2/issues/40761) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40688)_

#### [Problema] ortografía de corrección de PHPDoc

Para mantener altos estándares de calidad del código y mejorar la precisión de las sugerencias de código del entorno de desarrollo integrado (IDE), se han aplicado limpiezas estructurales a las capas de documentación de código en línea en los módulos del marco de trabajo principal.

_AC-16960 - [Problema de GitHub](https://github.com/magento/magento2/issues/40763) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40745)_

#### [Problema] perf(di:compile): crear instancias de ReflectionClass en caché en Type, Config/Reader y ClassReader

Para acelerar significativamente los tiempos de compilación y maximizar el rendimiento de implementación de integración continua (CI), el back-end del compilador de inyección de dependencia interna (`setup:di:compile`) se ha optimizado para eliminar los ciclos de reflexión PHP redundantes.

_AC-17077 - [Problema de GitHub](https://github.com/magento/magento2/issues/40796) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40615)_

#### [Problema] Actualice Filter.php para permitir `{{block template="Magento_Module::path/to/template.phtml"}}` y establecer \Magento\Framework\View\Element\Template como clase predeterminada

Para simplificar la creación de contenido y alinear las directivas de CMS con los estándares de diseño de plantilla, se ha mejorado el sistema principal de procesamiento de etiquetas de marcado para admitir declaraciones de bloque sin una definición de clase explícita.

_AC-17078 - [Problema de GitHub](https://github.com/magento/magento2/issues/38477) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38469)_

#### [Problema] perf(di:compile): el ámbito de la configuración de interceptación de memorias se lee durante la compilación

Para acelerar drásticamente las implementaciones de sitios y la compilación automatizada del servidor, se ha optimizado el compilador de inyección de dependencias (`setup:di:compile`) para eliminar las operaciones de análisis de XML redundantes.

_AC-17313 - [Problema de GitHub](https://github.com/magento/magento2/issues/40852) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40614)_

#### Actualice underscore.js a 1.13.8 para evitar vulnerabilidades de seguridad

La biblioteca Underscore.js agrupada (lib/web/underscore.js) se ha actualizado de 1.13.7 a 1.13.8. No se requieren cambios de configuración.

_AC-17349 - [Problema de GitHub](https://github.com/magento/magento2/issues/40857) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/12d0be1e)_

#### magento-composer-installer deja sin rellenar automáticamente setup/ (y otros directorios asignados) cuando un destino de implementación es un enlace simbólico

Se ha corregido un problema en el cual magento-composer-installer podía fallar al rellenar setup/ y otros directorios asignados por el compositor cuando el destino de implementación se configuraba como vínculo simbólico. Esto podría provocar la falta de archivos y una implementación incompleta de Commerce.

_AC-17360: [problema de GitHub](https://github.com/magento/magento2/issues/40864)_

#### Las claves de precarga de caché ya no necesitan prefijo de ID al utilizar el adaptador de caché Symfony

Las claves de precarga (preload_keys) para el adaptador de caché Symfony ahora se pueden configurar sin el id_prefix de caché. Anteriormente, si se seguía la configuración documentada y se incluía el prefijo en cada clave (por ejemplo, 061_SYSTEM_DEFAULT), las claves no se precargaban. Ahora puede especificar las claves exactamente como las solicita la aplicación (por ejemplo, SYSTEM_DEFAULT) y Adobe Commerce aplica el id_prefix automáticamente.

_AC-17407 - [Problema de GitHub](https://github.com/magento/magento2/issues/40877) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3a6b9667)_

#### [Problema] Corrige la obsolescencia de PHP 8.5 cuando el atributo category tiene &#39;frontend_input&#39;...

Se ha corregido un problema en el cual al abrir una categoría en el panel Administración se producía un error en PHP 8.5 cuando un atributo category tenía frontend_input establecido en null. Las páginas de categorías ahora se abren y se pueden editar correctamente sin el error de obsolescencia.

_AC-17499 - [Problema de GitHub](https://github.com/magento/magento2/issues/40908) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ecbeba3a)_

#### [Problema] Reemplaza las aserciones de PHPUnit y la configuración de prueba obsoletas

Se ha actualizado el conjunto de pruebas de la unidad central de Magento 2 para futuras actualizaciones de PHPUnit mediante la sustitución de siete usos de PHPUnit obsoletos. Los cambios se refieren a `isType()` afirmaciones y a la configuración de `with*()` en los stubs de prueba, patrones que almacenan en déclencheur los avisos de obsolescencia en las versiones actuales de PHPUnit y que están programados para su eliminación en PHPUnit 13 o posterior.

_AC-17750 - [Problema de GitHub](https://github.com/magento/magento2/issues/41040) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/41033)_

#### Las marcas de tiempo GraphQL order_date y comment devuelven una fecha de calendario incorrecta en configuraciones regionales distintas de en_US (análisis incorrecto de IntlDateFormatter) — Corrección de AC-14431 incompleta

Se ha corregido un problema en el cual las fechas de pedido de GraphQL podían mostrar una fecha de calendario incorrecta para las configuraciones regionales en francés y alemán.
Las fechas de pedido y las marcas de tiempo de comentarios relacionadas ahora devuelven la fecha y la hora correctas.
Se ha mejorado el formato de fecha para que las aplicaciones puedan analizar de forma fiable los valores de fecha de GraphQL.
El comportamiento existente para la configuración regional en_US permanece sin cambios.

_AC-18084 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d10ab92b)_

#### [Problema] Quitar etiqueta de @author prohibido

Para garantizar una alineación estricta con las directrices técnicas principales, se ha completado un barrido de mantenimiento de código incremental para limpiar bloques de documentación de recursos en línea en varios módulos del sistema.

_AC-8366 - [Problema de GitHub](https://github.com/magento/magento2/issues/37248) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36993)_

#### [Problema] Quitar la etiqueta `@author` prohibida de `Magento_Catalog` (parte 2)

Para garantizar la alineación completa con las directrices de entrega de código unificado de Magento, se ha ejecutado una pasada de limpieza incremental para eliminar sistemáticamente los comentarios de archivos no compatibles en los modelos de recursos de tienda principales.

_AC-8370 - [Problema de GitHub](https://github.com/magento/magento2/issues/37247) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36988)_

#### Nivel Precio Interfaz de almacenamiento Eliminar error no elimina todos los precios de nivel

Se ha resuelto un problema en TierPriceStorage por el que, al eliminar los precios de nivel de producto en varios sitios web, no se eliminaban todos los precios al actualizar la lógica de coincidencia de ID de precio para tener en cuenta el ID de sitio web asignado.

_AC-9738 - [Problema de GitHub](https://github.com/magento/magento2/issues/37949) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40557)_

#### [B2B] Los pedidos de compra no se convierten automáticamente en pedidos de venta con ActiveMQ

Se ha corregido un problema en el cual los consumidores iniciados por cron no procesaban mensajes cuando se utilizaba ActiveMQ con el protocolo STOMP. Como resultado, los pedidos de compra aprobados automáticamente no se convirtieron en pedidos de venta. El procesamiento de mensajes para colas STOMP es ahora más fiable y coherente con las implementaciones de colas DB y AMQP.

_ACP2E-4349 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/08b91f1a) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/239464da)_

#### Error de exportación con el almacenamiento configurado de AWS S3

La exportación del producto ahora funciona correctamente cuando se configura el almacenamiento remoto de AWS S3. Anteriormente, los archivos exportados no se podían escribir en S3 debido a una resolución de ruta no válida en el controlador de almacenamiento.

_ACP2E-4786 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d95ae6e)_

#### Los indexadores se quedaron atascados en el bucle de autobloqueo con el proveedor &quot;use_application_lock&quot; y &quot;file&quot;

Se ha corregido un problema por el cual los indexadores se bloqueaban indefinidamente durante la reindexación cuando el ajuste use_application_lock del indexador estaba habilitado junto con el proveedor de bloqueo de archivos. Las operaciones de reindexación ahora se completan según lo esperado.

_ACP2E-5027 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Rendimiento lento con variables MAGENTO_DC establecidas en la IU de la nube

Después de la corrección, la configuración de implementación no se vuelve a cargar cada vez que la clave solicitada no está presente y se definen algunas variables env.

_ACP2E-5094 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

#### [NUBE] La ruta URL mal formada devuelve HTTP 500 en lugar de 404 en el enrutador de reescritura de URL

Se ha corregido un problema en el cual una dirección URL de tienda con formato incorrecto devolvía una página de error HTTP 500 en lugar de una página 404 no encontrada estándar. Anteriormente, ciertas rutas de solicitud mal formadas provocaban un error no capturado durante la resolución de reescritura de URL.

_ACP2E-5154 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

#### Compatibilidad con [CLOUD] PHP 8.5 — ComponentRegistrar::getPath() null array offset bloquea la instalación:static-content:implementar (estrategia compacta) en 2.4.9

Se corrigió un problema en el cual `setup:static-content:deploy` fallaba en PHP 8.5 con un error &quot;Using null as a array offset&quot; al compilar archivos LESS de módulo que utilizan la directiva //@magento_import. La implementación de contenido estático ahora se completa correctamente en PHP 8.5.

_ACP2E-5183 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### [CMS] falso positivo &quot;Contenido de HTML no válido proporcionado&quot; al guardar el bloque de CMS con un href de anclaje seguido de otro atributo

El contenido de CMS que contiene un vínculo de anclaje estándar (p. ej. `&lt;a href="https://example.com/page" target="_blank" rel="noopener">`) ya no muestra como déclencheur una advertencia de validación falsa &quot;Contenido de HTML no válido proporcionado&quot; o un error al guardar cuando cms/wysiwyg/force_valid está habilitado.

_ACP2E-5203 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Marco de trabajo, GraphQL

#### el elemento de matriz di.xml se reemplaza si la configuración posterior utilizó una clave numérica

Para proteger la integridad de los datos arquitectónicos y mejorar la extensibilidad modular, se ha resuelto un error principal en el motor de análisis XML de inyección de dependencias (DI) en el que las configuraciones de matriz que utilizaban la clave numérica &quot;0&quot; se sobrescribían o soltaban silenciosamente durante la compilación del módulo.

_AC-8102 - [Problema de GitHub](https://github.com/magento/magento2/issues/36861) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40880)_

### GraphQL

#### addProductsToCart genera errores en custom_attributesV2 si el código de atributo es model

Se ha corregido un problema en el cual addProductsToCart devolvía un error de servidor interno cuando un producto tenía un atributo personalizado con el modelo de código. Ahora, el atributo personalizado se puede recuperar correctamente mediante custom_attributesV2.

_AC-16987 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/809ba93c)_

#### Cantidad GQL nula mientras stock_status es IN_STOCK

El campo de cantidad de la consulta GraphQL de productos devolvió incorrectamente un valor nulo para los productos que estaban en stock en un inventario MSI personalizado. El solucionador estaba activando la respuesta en el valor de configuración cataloginventory/options/not_available_message antes de obtener la cantidad de existencias real, y el valor XML predeterminado de esta configuración (2 — &quot;No hay suficientes artículos para la venta&quot;) provocó que se devolviera nulo en cualquier nuevo almacén sin una anulación explícita del administrador.
La comprobación ahora se evalúa después de resolver la cantidad vendible. null solo se devuelve cuando el producto no tiene existencias disponibles (saleableQty &lt;= 0) y la tienda está configurada explícitamente con &quot;No hay suficientes artículos a la venta&quot;. Los productos que están en stock siempre devuelven su cantidad vendible real, independientemente de esta configuración. La lectura de la configuración también se corrige para utilizar el ámbito del almacén, de modo que se respeten las invalidaciones en el nivel de almacén.

_ACP2E-4840 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [CLOUD] BundleProduct items.options.price ignora los precios con alcance de sitio web cuando Precios de catálogo = Sitio web

Precios fijos de opciones de paquetes con ámbito de sitio web en GraphQL: se ha resuelto un problema en el que, al consultar las opciones de productos de paquetes a través de GraphQL, se devolvían precios globales de &quot;Todas las vistas de la tienda&quot; en lugar de precios con ámbito de sitio web cuando el ámbito de precios del catálogo se establecía en Sitio web. El solucionador de Magento\BundleGraphQl\Model\Resolver\Links\Collection ahora comprueba correctamente el ámbito de precios y combina los precios de selección específicos del sitio web en función del ámbito de tienda solicitado.

_ACP2E-5057 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Carro de compras activo duplicado creado para el cliente debido a una condición de carrera de solicitudes GraphQL de customerCart simultánea

El sistema ahora garantiza que solo se cree un carro de compras activo por cliente, independientemente de la concurrencia de la solicitud. Anteriormente, dos consultas simultáneas de GraphQL customerCart o solicitudes POST /V1/carts/mine REST para el mismo cliente autenticado sin un carro de compras activo podrían resultar en registros de carro de compras activos duplicados en la base de datos.

_ACP2E-5077 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### [Cloud] administró GraphQlNoSuchEntityException desde QuoteGraphQl que registró en exception.log, lo que provocó un crecimiento de registro ilimitado

Se ha corregido un problema en el cual los errores esperados de GraphQlNoSuchEntityException, como los devueltos por un ID de carro de compras caducado o no válido, se escribían en var/log/exception.log. Estos errores controlados se siguen devolviendo al cliente como respuestas de error normales de GraphQL, pero ya no rellenan el registro de excepciones.

_ACP2E-5122 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### GraphQL, inventario/MSI

#### GraphQL: el ID de tienda pasado como ID de sitio web en ProductStock::isProductAvailable provoca el error &quot;no se encontró el sitio web ...&quot;

Anteriormente, algunos escaparates podían encontrar un error de sitio web no encontrado al comprobar la disponibilidad de existencias de productos al agregar artículos al carro de compras, debido a que se utilizaba el ID de tienda donde se requería un ID de sitio web. Esto se ha corregido para que las comprobaciones de disponibilidad de existencias utilicen el contexto de sitio web correcto, lo que evita el error.

_ACP2E-5242 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

### GraphQL, Pedido

#### [Solicitud de característica] Borrar datos redundantes en los datos de recogida de la tienda al cambiar el transportista

Al cambiar de la recogida en la tienda al método de entrega a domicilio, la ubicación de recogida y la dirección de la tienda asociada se eliminan del carro de compras. Se debe proporcionar una dirección de envío válida antes de realizar el pedido.

_ACP2E-4973 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/57047d29)_

### GraphQL, Producto

#### Falta la clave \&quot;model\&quot; en los datos de valor de la lista de deseos

Se ha corregido un problema en el cual al consultar los detalles de la lista de deseos a través de GraphQL se devolvía un error interno del servidor.
La consulta de lista de deseos ahora se devuelve correctamente sin el error &quot;Falta el modelo de clave en los datos de valor de la lista de deseos&quot;.

_AC-8062 - [Problema de GitHub](https://github.com/magento/magento2/issues/36909) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/515d3dd3)_

### Importación y exportación

#### [Problema]: corrige la visibilidad del iframe de importación

Para garantizar una interfaz de usuario limpia y pulida dentro del panel de administración de Magento, se ha resuelto un defecto de diseño de plantilla en el que un iframe de ejecución en segundo plano interno era visible para los administradores de almacén durante las validaciones de datos

_AC-13250 - [Problema de GitHub](https://github.com/magento/magento2/issues/39267) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39265)_

#### [Problema] corregido: algoritmo hash xxh128 de código duro en la importación del producto

Para limpiar subsistemas internos y aprovechar líneas de base modernas de optimización del sistema, el componente de importación de productos se ha optimizado para utilizar un único algoritmo hash permanente.

_AC-16967 - [Problema de GitHub](https://github.com/magento/magento2/issues/40770) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40687)_

#### El botón Importar permanece disponible después de los errores de validación cuando la Estrategia de validación está configurada en Detenerse si hay error

Se ha corregido el problema por el que el botón Importar seguía apareciendo en los resultados de validación después de una validación de datos fallida cuando la estrategia de validación se establecía en &quot;Detener si había error&quot;. Anteriormente, aparecía el botón y se podía hacer clic en él aunque todos los registros hubieran fallado en la validación, por lo que el intento de importación terminó inmediatamente.

_ACP2E-5124 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Instalar y administrar

#### [Corrección en la nube] de códigos de subdivisión ISO existentes obsoletos

Se han actualizado los códigos de región de 13 países para que coincidan con la norma ISO 3166-2. Anteriormente, algunos códigos de región no coincidían con el estándar, lo que podría causar problemas con integraciones de terceros y cumplimiento internacional. Se han añadido nuevas regiones para Bélgica, Colombia, España, Francia, Italia y Letonia. Códigos de región actualizados para Austria, Colombia, Costa Rica, Alemania, Estonia, España, Finlandia, Francia, India, Islandia y Letonia.

_ACP2E-4495 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

### Inventario/MSI

#### Tarjeta de regalo [CLOUD] y artículos relacionados no vendibles WF-1688

El producto no desaparece cuando se utiliza un stock/fuente no predeterminado y se guarda el producto relacionado (relacionado o de ampliación de venta o venta cruzada).

_ACP2E-4741 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/30fbdb0f)_

#### Incoherencia del estado de stock del producto agrupado

Anteriormente, cuando un administrador de tienda actualizaba manualmente el estado de stock de un producto agrupado desde el panel Administración, el cambio no se reflejaba en la tienda de las tiendas configuradas con varios orígenes de inventario. Los clientes seguirían viendo el estado de las existencias obsoleto a pesar de los cambios del administrador.

Este problema se ha corregido. Los cambios de estado de existencias de productos agrupados realizados en el panel Administración ahora se propagan correctamente en todas las fuentes de inventario y ubicaciones de existencias configuradas, lo que garantiza que los clientes siempre vean la disponibilidad de existencias precisa en la tienda.

_ACP2E-4866 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/db712a46)_

#### NoSuchEntityException &quot;el almacén solicitado no se encontró&quot; producida por GetStockIdForCurrentWebsite.php

Se ha corregido un problema que causaba que, al visitar una página de tienda con un parámetro de consulta ?store= no válido, se registrara NoSuchEntityException en el nivel CRÍTICO en cada solicitud de este tipo. Anteriormente, el complemento de datos de existencias MSI pasaba el código de almacén sin procesar directamente a StoreManager::getStore() sin procesar el caso en el que el almacén no existía, lo que daba como resultado un desorden de registro de excepciones.

_ACP2E-5003 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/1bf25e46)_

### Pedido

#### El observador de cancelación de pedidos no se ejecuta cuando el ámbito es frontend o webapi_rest

Se corrigió un problema en el cual al cancelar un pedido desde la tienda o a través del ámbito webapi_rest, el observador de cancelación no se ejecutaba correctamente. Los importes de las tarjetas de regalo ahora se restauran al crédito de la tienda del cliente cuando se cancela el pedido.

_AC-16353 - [Problema de GitHub](https://github.com/magento/magento2/issues/40414) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/64eb754d)_

#### La regla de precio del carro de compras con uso limitado no se aplica al editar un pedido existente en Administración (por ejemplo, &quot;Usos por cliente = 1&quot;)

Se ha corregido un problema en el cual los descuentos de regla de precio de carro de compras con límites de uso se eliminaban al editar un pedido existente en Administración. El descuento original ahora se conserva cuando se edita el pedido, incluso después de haber alcanzado el límite de uso.

_AC-16671 - [Problema de GitHub](https://github.com/magento/magento2/issues/40624) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Error de validación de cantidad mínima en el panel de administración para productos agrupados

Para mejorar la experiencia de pedidos back-end y eliminar bloques funcionales al generar presupuestos manuales, se ha resuelto un error de validación en el que los parámetros de artículo secundarios se evaluaban incorrectamente durante la creación de pedidos de administración.

_AC-17193 - [Problema de GitHub](https://github.com/magento/magento2/issues/40812) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40863)_

#### Incoherencia de cantidad de artículo secundario del paquete en la vista de pedidos de front-end

La página de detalles de pedidos de tienda ahora mostrará la cantidad total solicitada para cada opción de producto de paquete. Anteriormente, la columna de cantidad de cada opción secundaria mostraba la cantidad pedida del paquete principal en lugar de la cantidad total pedida por opción.

_ACP2E-4820 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b63925d9)_

#### [ASUS] OrderMutex::execute() falta DeadlockException reintentar causa un error permanente de ShipOrder/InvoiceOrder-

Las operaciones ShipOrder y InvoiceOrder ahora se resuelven correctamente en caso de interbloqueo.
Anteriormente, las operaciones ShipOrder y InvoiceOrder fallaban de forma permanente debido a interbloqueo

_ACP2E-4913 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Cálculo de nivel de fila FPT/WEEE incorrecto en artículos configurables principales durante la generación de facturas

Los totales generales de facturas y notas de abono de los productos configurables ahora incluyen correctamente el importe de impuestos sobre productos fijos. Anteriormente, los importes de nivel de fila de FTP no se propagaban al artículo de pedido configurable principal, lo que provocaba que los totales de factura y nota de abono fueran inferiores al total general del pedido en el importe de FTP.

_ACP2E-4977 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/51f6d191)_

#### Cantidades de productos modificadas al actualizar la página al crear el pedido del administrador

Se ha resuelto un problema en el cual al actualizar la página se podía agregar el mismo SKU varias veces.

_ACP2E-5046 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### Los trabajadores cron de correo electrónico asincrónico simultáneos envían correos electrónicos de confirmación de pedido duplicados para el mismo pedido

Se ha resuelto un problema en el cual los trabajadores de correo electrónico simultáneos podían enviar correos electrónicos de confirmación de pedido duplicados para el mismo pedido.

_ACP2E-5059 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8d70f246)_

#### El trabajo cron de [CLOUD] sales_clean_quote se queda sin memoria

Se ha corregido el problema por el que el trabajo cron sales_clean_quote se quedaba sin memoria al limpiar un gran número de presupuestos caducados. Anteriormente, el trabajo retenía todas las comillas procesadas en la memoria y finalizaba con un error grave de agotamiento de memoria antes de que se eliminaran todas las comillas caducadas.

_ACP2E-5137 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4d0357d7)_

### Pedido, Promoción

#### [Nube] problema al agregar varios cupones para reordenar

Se ha resuelto un problema en el cual los cupones válidos ya no se aplicaban a un pedido después de un error en un intento de cupón no válido. Ahora, si se introduce un cupón no válido, los cupones válidos aplicados anteriormente permanecerán aplicados correctamente.

_ACP2E-4810_

#### La regla de precio del carro de compras de categorías de importe fijo descuenta los elementos secundarios de paquete dinámico que no coinciden cuando la regla coincide con el elemento principal del paquete

Se ha corregido el problema en el cual una regla de precio de carro de compras de cantidad fija con una condición de categoría aplicaba incorrectamente un descuento a todos los elementos secundarios de un paquete de precio dinámico cuando la regla coincidía únicamente con el elemento principal del paquete. Anteriormente, los elementos secundarios del paquete que no pertenecían a la categoría de destino recibían una parte prorrateada del descuento en lugar de cero.

_ACP2E-5075 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2b9e8316)_

### Pagos

#### El comando config:show no funciona con rutas parciales en versiones más recientes

El comando `config:show` ahora acepta rutas de configuración parciales, como pago, y muestra los valores de configuración en esa ruta. Anteriormente, al ejecutar el pago de `php bin/magento config:show` se devolvió un error: `The "payment" path doesn't exist. Verify and try again.` en lugar de mostrar los valores correctos.

_AC-13908 - [Problema de GitHub](https://github.com/magento/magento2/issues/39610) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40432)_

### Rendimiento

#### setup:upgrade está cambiando el modo del indizador a `save` de `schedule`, lo que lo está ralentizando enormemente

Se ha resuelto un problema de larga data en el cual la ejecución de bin/magento setup:upgrade cambiaba inadvertidamente los modos de indizador de &quot;Guardar según lo programado&quot; a &quot;Guardar al guardar&quot; y soltaba y recreaba innecesariamente los déclencheur de la base de datos, reduciendo drásticamente el tiempo de inactividad y evitando cuellos de botella de rendimiento durante las implementaciones en catálogos grandes.

_AC-2423 - [Problema de GitHub](https://github.com/magento/magento2/issues/33386) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40643)_

#### Las claves de caché de Valkey LAYOUT consumen mucho espacio para un catálogo de productos grandes

Anteriormente, cada producto generaba su propia entrada de caché de DISEÑO por vista de tienda, lo que provocaba un consumo de memoria excesivo en Redis/Valkey en catálogos grandes. Ahora, las entradas de la caché de DISEÑO se comparten entre productos con el mismo tipo, conjunto de atributos y vista de tienda, lo que limita el crecimiento de la caché independientemente del tamaño del catálogo.

_ACP2E-4908 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9b6a8bd9)_

#### Error de interbloqueo en la consulta del producto

Se ha corregido un interbloqueo de InnoDB en páginas con una lista de productos CatalogWidget filtrada por categoría, que se producía cuando el indexador de precios en modo de programación se ejecutaba simultáneamente.

_ACP2E-5052 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### [Quans] degradación del rendimiento de la consulta de resolución de URL de Adobe Commerce

Se ha corregido el problema por el cual la consulta de ruta de GraphQL siempre mostraba contenido completo de la página de CMS, incluida la ejecución del widget de Page Builder y la carga de la colección de productos, incluso cuando solo se solicitaban metadatos de enrutamiento de URL (relative_url, redirect_code, type). Anteriormente, esto provocaba un procesamiento innecesario de widgets/productos y un aumento significativo de las consultas de bases de datos por solicitud para páginas de CMS que contenían widgets de Page Builder.

_ACP2E-5143 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/597c7211)_

#### Administrador Cliente Editar depósitos de rendimiento cuando Compartir cuentas de cliente está establecido en Global

Se ha corregido un problema de rendimiento en la página Admin Customers Edit, en el que el tiempo de carga y el tamaño de respuesta HTTP aumentaban cuadráticamente cuando Share Customer Accounts se establecía en Global.

_ACP2E-5164 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/24667df1)_

### Product

#### Botón Añadir al carrito dentro de la ventana emergente &quot;Click for price&quot; que no funciona.

Se ha corregido un problema que hacía que el botón Añadir al carro de compras de la ventana emergente &quot;Hacer clic para el precio&quot; de la página de la lista de productos no agregara el producto al carro de compras.
Ahora los productos se pueden añadir al carro de compras correctamente desde la ventana emergente.

_AC-11896 - [Problema de GitHub](https://github.com/magento/magento2/issues/30356) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/29a7cdbe)_

#### Los solucionadores de BundleGraphQL crean instancias de producto diferidas independientes, derrotando al agrupamiento de consultas (N+1)

Para acelerar drásticamente el rendimiento de respuesta de API y minimizar la sobrecarga del servidor, la capa de resolución de GraphQL se ha optimizado para aplicar lotes de consulta verdaderos para productos agrupados, eliminando las fugas de base de datos N+1 que agotan el rendimiento.

_AC-16647 - [Problema de GitHub](https://github.com/magento/magento2/issues/40595) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40867)_

#### La validación de atributos de selección y multiselección EAV rechaza incorrectamente las etiquetas de opción con el valor &quot;0&quot;

Para mejorar la integridad de los datos y eliminar errores de envío inesperados entre los formularios de clientes y catálogos, se ha resuelto un error de validación en el que el marco principal de EAV rechazaba erróneamente las etiquetas de opción que contenían el valor de cadena exacto &quot;0&quot;

_AC-16986 - [Problema de GitHub](https://github.com/magento/magento2/issues/40634) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40827)_

#### Las etiquetas de opciones personalizables y los títulos de opciones personalizables no se pueden guardar cuando la función de un usuario está limitada a un ámbito determinado

Se ha corregido un problema por el cual las etiquetas de opciones personalizables y los títulos se revertían cuando los editaba un usuario administrador con acceso limitado a un ámbito de tienda específico.
Las etiquetas y los títulos actualizados ahora se guardan correctamente para el ámbito seleccionado.

_AC-2684 - [Problema de GitHub](https://github.com/magento/magento2/issues/35210)_

#### El precio de la tarjeta regalo se muestra incorrectamente en la lista de deseos

Se ha corregido un problema en el cual el precio mínimo de la tarjeta regalo configurada se mostraba como 0,00 $ en la lista de deseos.
El precio mínimo correcto de la tarjeta regalo ahora se muestra en la página Mi lista de deseos y en el widget de la barra lateral de la lista de deseos.

_AC-8037_

#### El consumidor ignora el sistema con ámbito de tienda/stmp/disable

El consumidor de alertas de producto ahora cuenta con la configuración de ámbito de tienda system/stmp/disable.

_ACP2E-4870 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec436b10)_

#### La página de comparación de front-end muestra traducciones de etiquetas de descripción breve incorrectas

Anteriormente, en la página Comparar productos, las etiquetas de atributos comparables como Descripción breve podían mostrar una traducción de una vista de tienda diferente en lugar de la del almacén actual. Ahora se muestran las traducciones correctas específicas de la tienda.

_ACP2E-4929 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

#### El carrusel de productos de Page Builder ignora el orden de clasificación de posiciones de la categoría y muestra los productos en el orden DESC entity_id en su lugar

Se ha corregido un problema por el cual los productos mostrados en un carrusel de Page Builder configurado para ordenar por posición de categoría aparecían en el orden incorrecto en la tienda. Los productos ahora se muestran en el orden configurado en la pestaña Administración → Catálogo → Categorías → Productos.

_ACP2E-4980 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/51f6d191)_

### Reglas de promoción

#### Cálculo de descuento incorrecto cuando una de las reglas de precio del carro de compras aplicadas tiene un valor de paso de cantidad de descuento

Se ha corregido un problema por el cual el descuento se calculaba de forma incorrecta cuando se aplicaban varias reglas de precio del carro de compras y una regla tenía un valor de Paso de cantidad de descuento (Comprar X).
Ahora los descuentos se calculan correctamente para todas las cantidades aptas.

_AC-12307 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c10554e1)_

### Promoción, Segmentación

#### Los productos relacionados se eliminan automáticamente

Se ha corregido el problema por el cual los productos relacionados no se eliminaban cuando cambiaban los atributos de un producto y dejaban de coincidir con una regla de Target. Anteriormente, el indexador mview no eliminaba las asociaciones de productos de reglas antiguas y emitía una advertencia PHP (clave de matriz indefinida) durante la reindexación.

_ACP2E-4836_

### Devuelve

#### RMA - API de añadir comentarios de devolución: los correos electrónicos se envían al remitente (representante de ventas), pero no al cliente

Se ha corregido un problema por el cual los correos electrónicos de comentarios de devolución enviados a través de la API Devoluciones se enviaban al representante de ventas pero no al cliente.
Los clientes ahora reciben una notificación por correo electrónico cuando se agrega un comentario de retorno a través de la API con la notificación al cliente habilitada.

_AC-1138 - [Problema de GitHub](https://github.com/magento/magento2/issues/33985)_

### Ventas

#### Faltan datos en la columna product_options `[Order][REST]` sales_order_items cuando el pedido se realiza desde la api de rest V1/orders o V1/orders/create endpoints

Se ha corregido un problema en el cual los elementos de pedido creados mediante la API de REST no incluían datos completos de product_options. Las etiquetas de opciones personalizadas y los detalles de opciones relevantes ahora se guardan correctamente para los pedidos creados mediante la API de REST.

_AC-15187 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### La cuadrícula de pedidos de ventas se ha quedado permanentemente obsoleta cuando la indexación de cuadrícula asíncrona está habilitada debido a marcas de tiempo updated_at vinculadas

Se ha corregido un problema en el cual la cuadrícula de pedidos de ventas podía permanecer atascada con un estado de pedido obsoleto cuando la indexación de cuadrícula asíncrona estaba habilitada. El estado de la cuadrícula de pedidos ahora se actualiza correctamente para que coincida con el estado de pedido actual, incluidos los casos en los que se producen varias actualizaciones de pedidos en el mismo segundo.

_AC-17118 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/478f8e7c)_

### Seguridad

#### [Problema] Actualización de texto de DOM js.phtml reinterpretado como HTML

Para reforzar la línea de base de seguridad de la plataforma y minimizar el riesgo de ejecución maliciosa de la entrada, se ha refactorizado la plantilla de script en línea principal que gestiona las actualizaciones dinámicas de DOM para eliminar los vectores de inyección de scripts en sitios múltiples (XSS).

_AC-12118 - [Problema de GitHub](https://github.com/magento/magento2/issues/38821) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38804)_

### Envío

#### Problema con la API REST de USPS, tasas incorrectas para el peso máximo del paquete

Se corrigieron estimaciones de envío incorrectas cuando un pedido se divide en varios paquetes (por ejemplo, por encima de &quot;Peso máximo del paquete&quot;). El transportista solicita ahora una tarifa para cada paquete y calcula el total de las cantidades, de acuerdo con el flujo de herramientas web heredadas.

_ACP2E-4813 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6c67a9b5)_

### Ensayo y previsualización

#### Errores de consola en el modo de vista previa de actualización de programación

Se ha corregido el problema por el cual la página de vista previa de una actualización de ensayo no se cargaba correctamente con errores de consola de JavaScript cuando dos actualizaciones se compartían a la misma hora de inicio. Anteriormente, la URL de vista previa firmada utilizaba un ID de versión incrementado que no coincidía con la marca de tiempo derivada de la vista previa de JavaScript, lo que provocaba una discrepancia de firmas y evitaba que la página se cargara correctamente en el modo de vista previa.

_ACP2E-4828_

#### La instalación :upgrade tarda demasiado en aplicar el parche de datos Magento_CatalogStaging con un número elevado de vistas de tienda y categorías

Se ha corregido un problema en el cual el parche de migración de datos de CE a EE no migraba correctamente las actualizaciones de diseño de categoría programadas y los precios especiales del producto a las actualizaciones de ensayo. Las categorías con fechas de diseño programadas producían actualizaciones de ensayo vacías debido a un enfoque de contexto de ensayo incorrecto. Los productos se omitían silenciosamente en PHP 8.1+ cuando los valores de fecha y hora nulos estaban presentes desde una ejecución de migración anterior. También se mejoró el rendimiento de la migración al cargar solo las categorías y los productos afectados en lugar de repetir el catálogo completo.

_ACP2E-5009_

#### La cuadrícula Reglas de precio del catálogo del panel de ensayo de contenido muestra datos duplicados

La cuadrícula Reglas de precio de catálogo ahora muestra correctamente los detalles únicos para cada regla de precio de catálogo asignada a una actualización provisional. Anteriormente, cuando se asignaban dos o más reglas de precio de catálogo a la misma actualización de ensayo, la cuadrícula Reglas de precio de catálogo de la página de esa actualización en el panel de ensayo de contenido mostraba el número correcto de filas, pero cada fila mostraba incorrectamente los mismos datos de la regla (la última) en lugar de los detalles propios de cada regla.

_ACP2E-5097_

### Impuestos

#### base_wee_tax_applied_amount no está definido para el producto principal

el valor base_weee_tax_applied_amount ahora se rellena para el producto configurable en tablas de base de datos como sales_order_item, sales_invoice_item, sales_creditmemo_item, no solo para su secundario

_ACP2E-4922 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/08b91f1a)_

### Marco de prueba

#### [Problema] Actualización de GraphQL prueba Client.php para la comparación de subcadenas que no distinguen entre mayúsculas y minúsculas

Se ha corregido un problema en el cual las pruebas de API de GraphQL no reconocían encabezados Set-Cookie cuando el encabezado usaba mayúsculas y minúsculas diferentes. Las pruebas ahora administran correctamente los encabezados Set-Cookie, set-cookie y SET-COOKIE.

_AC-15337 - [Problema de GitHub](https://github.com/magento/magento2/issues/39713) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c10554e1)_

#### Pruebas funcionales de WebAPI GraphQL extremadamente lentas

Para optimizar las configuraciones de entrega de la compilación y acelerar los entornos de integración continua (CI), se ha resuelto un cuello de botella de la infraestructura de prueba mediante la transición de los comportamientos de borrado de caché de las llamadas de comando del sistema externo a la gestión nativa de la memoria en proceso.

_AC-15395 - [Problema de GitHub](https://github.com/magento/magento2/issues/39725) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40804)_

### Marco de IU

#### Minicart no se puede usar dos veces en la misma página

Para proporcionar a los desarrolladores de front-end una mayor flexibilidad de diseño, se ha resuelto una limitación de interfaz de usuario principal de larga data, que permite que existan varios bloques de minigráficos (por ejemplo, uno en el encabezado y otro en el pie de página) y que se actualicen de forma independiente en un solo diseño de página.

_AC-12579 - [Problema de GitHub](https://github.com/magento/magento2/issues/38958) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40871)_

### de-github

#### [Problema] corregido (pagecache): reconoce PATCH como método HTTP válido en Varnish VCL

La VCL de Varnish predeterminada de Magento ahora reconoce PATCH como un método HTTP válido, por lo que las solicitudes de actualización parcial de la API de REST (por ejemplo, PATCH /rest/V1/products/:sku) se pasan al servidor en lugar de canalizarse. Esto corrige los errores o el comportamiento incorrecto de las llamadas de PATCH cuando Caché de página completa está configurada como Barniz.

_AC-16954 - [Problema de GitHub](https://github.com/magento/magento2/issues/40757) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40657)_

#### [Problema] Reemplaza todos los parámetros gad_* en VCL

Para eliminar las regresiones de rendimiento causadas por las campañas de publicidad dinámica, las capas de almacenamiento en caché de la aplicación se han actualizado para ignorar de forma proactiva todas las cadenas de consulta gad_* de Google Ads. Esto evita que los vínculos de campañas externas invaliden las memorias caché de la página y ralenticen las páginas de destino

_AC-16980 - [Problema de GitHub](https://github.com/magento/magento2/issues/40781) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40780)_

#### [Problema] corregido: actualizar comprobación de versión mínima de PHP en bootstrap a 8.3

Para evitar errores de tiempo de ejecución confusos y mejorar la solución de problemas de instalación del desarrollador, el validador de entorno PHP nativo dentro del marco de arranque del sistema se ha alineado con los requisitos principales reales de la aplicación.

_AC-17312 - [Problema de GitHub](https://github.com/magento/magento2/issues/40851) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40686)_

#### `health_check.php` devuelve 500 cuando `igbinary` está instalado y se utiliza la caché de archivos predeterminada (Varnish 503)

Se ha corregido un problema en el cual health_check.php devolvía HTTP 500 cuando igbinary se instalaba con el backend de caché de archivos predeterminado. La comprobación de estado ahora acepta configuraciones de caché válidas sin una clave de servidor explícita, lo que evita que Varnish marque el servidor como no correcto y devuelva HTTP 503.

_AC-17400 - [Problema de GitHub](https://github.com/magento/magento2/issues/40876) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8b67e8ed)_

#### [Problema] corregido: actualice los tipos gzip y elimine la solución de IE6 en la configuración de nginx

Para mejorar las velocidades de carga de las páginas y optimizar la entrega de recursos de red, la configuración del servidor de reserva se ha modernizado para admitir mejor los componentes modernos de la tienda y eliminar la sobrecarga tecnológica heredada

_AC-17498 - [Problema de GitHub](https://github.com/magento/magento2/issues/40774) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40681)_

#### [Problema] al intentar corregir la prueba OrderStatusChangeDateTest de graphql débil.

Para mejorar la fiabilidad de la integración continua (CI) y reducir los errores de generación de falsos positivos, se ha resuelto una condición de carrera en el grupo de pruebas funcionales de WebAPI. La prueba de validación de estado de pedidos de GraphQL (OrderStatusChangeDateTest) experimentó anteriormente errores intermitentes debido a sutiles disparidades de tiempo entre la memoria PHP y las marcas de tiempo MySQL

_AC-17959 - [Problema de GitHub](https://github.com/magento/magento2/issues/41126) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/40618)_
