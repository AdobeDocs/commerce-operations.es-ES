---
title: Notas de la versión
description: Obtenga información sobre los parches disponibles para Adobe Commerce y los problemas que resuelven.
source-git-commit: e9ba2d0ad8568c40335e8643ef0070d9e2bb9b3f
workflow-type: tm+mt
source-wordcount: '9581'
ht-degree: 0%

---

# Notas de la versión

La variable [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) ofrece parches individuales desarrollados por Adobe y la comunidad de Magento Open Source. Permite aplicar, revertir y ver información general sobre todos los parches individuales disponibles para la versión instalada de Adobe Commerce o Magento Open Source. Puede aplicar parches a los proyectos de Adobe Commerce y Magento Open Source independientemente de quién desarrolló el parche. Por ejemplo, puede aplicar un parche desarrollado por la comunidad a los proyectos de Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar parches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obtener instrucciones sobre la aplicación de parches a sus proyectos de Adobe Commerce o Magento Open Source. Consulte [Parches disponibles](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la Guía de actualización de software para revisar una lista completa de parches publicados.

>[!INFO]
>
>Para obtener información sobre [!DNL quality patches] creado por la comunidad para el Magento Open Source, consulte la [notas de la versión](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3): corrige la variable _Intentando acceder al desplazamiento de matriz en el valor de tipo bool_ al acceder a ciertas rutas de categoría no existentes para productos conocidos en PHP 7.4.
* **ACSD-47332** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que cron falla con un error del que solo se informa cuando se ejecuta entre las 00:00 y las 00:59 UTC.
* **ACSD-47280** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6) : corrige el problema en el que deshabilitar la función de catálogo compartido en un ámbito específico no funciona correctamente.
* **ACSD-47106** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6) : corrige el problema en el que un valor no se puede guardar en un nuevo atributo personalizado en una página de creación de empresa.
* Parche actualizado: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6) : corrige el problema en el que un usuario obtiene un error al asignar un gran número de fuentes de productos.
* **ACSD-46856** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): mejora el rendimiento actualizando los precios de nivel a través de System > Configuration > Import > Advanced Pricing.
* **ACSD-46541** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4) : corrige el problema en el que un usuario administrador no puede crear una nota de crédito si se elimina un elemento de pedido.
* **ACSD-46581** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6) : corrige el problema en el que el total de impuestos estimado no se actualiza después de seleccionar un país en el carro de compras.
* **ACSD-46618** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6) : corrige el problema en el que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.
* **ACSD-46674** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6) : corrige el problema en el que las opciones personalizadas de un tipo de imagen se muestran como HTML en los correos electrónicos de los clientes.
* **ACSD-46988** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6) : corrige el problema en el que la solicitud de API &quot;currency&quot; de GraphQL devuelve valores NULL para una moneda personalizada.
* **ACSD-47076** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5) : corrige el problema en el que los vídeos de Vimeo no se pueden reproducir en la tienda.
* **ACSD-45071** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4) : corrige el problema en el que se agregaba el origen predeterminado al producto durante la importación.
* **AC-3023** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): actualice el esquema DHL a la última versión 10.0.
* Revisiones actualizadas: MDVA-42584.
* parches reemplazados: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): corrige el problema en el que un usuario obtiene un estado de pedido incorrecto cuando se reembolsa mediante el crédito de la tienda.
* **ACSD-46703** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6*): Corrige el problema en el que no es posible arrastrar y soltar opciones personalizadas en una página de edición de producto.
* **ACSD-44851** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6*): Corrige el problema en el que una categoría con subcategorías no puede abrir ni expandir.
* **ACSD-46815** (*para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6*): Corrige el problema en el que la solicitud del árbol de categorías está limitada a 20 categorías.
* **ACSD-45675** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6*): Corrige el problema en el que la exportación del producto utiliza nombres de categoría de la variable *Vista de tienda predeterminada* ámbito.
* **ACSD-46869** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6*): Corrige el problema en el que un producto configurable en un carro de compras no se actualiza a través de un *API de REST de PUT* sin cambiar la cantidad del producto.
* **MDVA-42768-V2** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que el producto configurable muestra el precio normal como *0* when *Mostrar fuera de existencias* es *Sí*.
* Revisiones actualizadas: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Parche obsoleto: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que la solicitud del árbol de categorías está limitada a 20 categorías.
* **ACSD-45781** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.2*): Corrige el problema en el que el campo de búsqueda principal de la tienda no se mostraba en el dispositivo móvil.
* **ACSD-46192** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;2.4.5*): Corrige el problema con el uso de la variable `async/bulk/V1/configurable-products/bySku/options` punto final.
* **ACSD-46404** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5*): Corrige el problema en el que un usuario administrador no puede iniciar sesión después de actualizar a la versión 2.4.4.
* Revisiones actualizadas: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que una mutación de producto de GraphQL para un almacén específico devuelve todas las variantes configurables, incluidas las que no están asignadas al almacén solicitado.
* **ACSD-46146** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.6*) : corrige el problema en el que se envían dos correos electrónicos de confirmación de pedido después de realizar un pedido desde el administrador.
* **ACSD-45255** (*para Adobe Commerce >=2.4.3 &lt;2.4.6*): corrige una excepción en la página Informe de stock bajo para un usuario administrador restringido.
* **ACSD-45488** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6*): Corrige el problema en el que un producto configurable con varias fuentes no se devuelve automáticamente a In Stock.
* **ACSD-45754** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.6*) - Corrige el problema en el que los puntos de devolución no se agregan después de aplicar un cupón al carro de compras.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*): Corrige el problema en el que los metadatos de vídeo se pierden después de aplicar una actualización de ensayo.
* **ACSD-45257** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.4*): corrige el problema en el que GraphQL no muestra correctamente un descuento en el carro de compras.
* **ACSD-44938** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*): Corrige el problema en el que `VAT_ID` no se puede aplicar en una solicitud de GraphQL para un usuario invitado.
* Revisiones actualizadas: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.4*): corrige el problema en el que la cantidad de stock de un producto virtual no se calcula correctamente después de crear una nota de abono.
* **ACSD-43887** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando se habilitan Pedidos de compra para empresas.
* **ACSD-45143** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): Corrige el problema en el que la variable `setShippingAddressesOnCart` la mutación no permite establecer el código de región numérico como *region*.
* **ACSD-44591** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.6*): Corrige el error que se produce cuando se realiza un pedido sin confirmación de CAPTCHA.
* **ACSD-45520** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.6*): Corrige el problema en el que las opciones de muestra no están preseleccionadas en la página de detalles del producto cuando un usuario edita productos configurables desde el carro de compras.
* **ACSD-45169** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.6*): Corrige el problema en el que [!DNL Visual Merchandiser] no muestra las acciones y el precio correctos para un producto configurable después de aplicar una actualización de ensayo.
* **ACSD-45424** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.6*) - Corrige el problema en el que se crea una compensación de reserva incorrecta después de un reembolso parcial (nota de abono).
* **MDVA-42807** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.6*): corrige el problema en el que el signo de moneda personalizado no se muestra en la tienda.
* Revisiones actualizadas: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el que los totales de pedidos del informe Pedidos no se calculan correctamente para el usuario administrador restringido.
* **MDVA-44940** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el error SQL que se produce al guardar la categoría desde el Administrador.
* **MDVA-44562** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.2-p2*): Corrige el problema en el que el ID de tienda no predeterminado de los artículos de oferta se invalida por el ID de tienda predeterminado, a pesar de la solicitud de GraphQL procedente de la vista de tienda no predeterminada.
* **MDVA-43167** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*) : corrige el problema en el que la acción masiva de la cuadrícula de orden de administración no se aplica a varias páginas cuando el usuario administrador selecciona todos los pedidos.
* **MDVA-44044** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.2-p2*): Corrige el problema en el que un producto no se muestra en la página de categorías después de asignarse a un nuevo sitio web.
* **MDVA-42509** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.4*): Corrige el problema en el que no se podía cargar un CSV para un pedido rápido, lo que provocaba un error *No se puede enviar la cookie* error.
* Revisiones actualizadas: MDVA-41061, MDVA-42584.
* El prefijo del nuevo [!DNL Quality Patches Tool] los parches se cambiarán de *MDVA* a *ACSD* debido a cambios en el proceso interno.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el que no se puede agregar un artículo adicional al carro cuando la cantidad mínima del artículo ya está en el carro de compras.
* **MDVA-44887** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5*): corrige la variable *Error de sintaxis no detectado: Token &quot;const&quot; inesperado* en el panel Administración.
* **MDVA-43718** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*) - Correcciones *El consumidor no tiene autorización para acceder a %resources.* que aparece al acceder a un catálogo compartido desde una integración personalizada.
* **MDVA-44660** (*para Adobe Commerce y Magento Open Source >=2.4.2-p1 &lt;2.4.5*): corrige el problema en el que el carácter de acento grave ``` ` ``` no se pudo usar para el nombre y los apellidos de un cliente.
* **MDVA-40896** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige la variable *Error: TypeError: Argumento 3 pasado al Magento* error en la API masiva del producto asíncrono.
* **MDVA-38559** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3*): corrige la variable */V1/customer/search API* para clientes con más de una suscripción.
* **MDVA-44533** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.4*): corrige el problema en el que el descuento se aplica erróneamente a un producto secundario del paquete.
* Revisiones actualizadas: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): Corrige el problema en el que los productos *No visible individualmente* sigue apareciendo en Resultados de búsqueda avanzados del catálogo.
* **MDVA-44100** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que todos los FPT se asignan al último producto del carro de compras y se restablecen para otros productos.
* **MDVA-43605** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.5*): corrige el problema en el que los datos de pedido devuelven valores negativos para los totales de filas al utilizar la API de Rest.
* **MDVA-43102** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.5*): Corrige el problema en el que la cantidad vendible no se actualiza correctamente cuando se realiza un reembolso mediante la API de REST.
* **MDVA-43178** (*para Adobe Commerce y Magento Open Source >=2.4.3-p2 &lt;2.4.5*): corrige el problema en el que un token de cliente para una tienda personalizada no se puede recuperar en GraphQL.
* **MDVA-43859** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema en el que el error *No existe tal entidad con customerId =* se registra cuando un cliente eliminado intenta iniciar sesión.
* **MDVA-44147** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): Corrige el problema en el que una solicitud de GraphQL no devuelve listas de solicitudes.
* **MDVA-44505** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): Corrige los problemas en los que GraphQL al aplicar puntos de devolución no actualiza el total general y en los que el crédito de la tienda se aplica varias veces durante la colocación del pedido.
* Revisiones actualizadas: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): Corrige el problema en el que la regla de producto relacionada solo funciona cuando el segmento de cliente está establecido en *Todo*.
* **MDVA-39605** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*) : corrige el problema en el que la caché de Redis TTL (fecha de caducidad) tiene un valor incorrecto.
* **MDVA-43862** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.5*): Corrige el problema en el que el cliente no puede actualizar elementos del carro de compras debido a un GraphQL *Mutación UpdateCartItems* error.
* **MDVA-43824** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*): Corrige el problema en el que aparece un error al cancelar pedidos con un descuento.
* **MDVA-43451** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): Corrige el problema en el que el error *No se encontró la tienda solicitada. Compruebe la tienda e inténtelo de nuevo.* aparece al configurar un catálogo compartido para un sitio web específico.
* **MDVA-43491** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.5*): corrige el problema en el que la etiqueta de imagen base no se actualiza al importar productos para un sitio web de varias tiendas.
* **MDVA-43601** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema con los déclencheur que faltan después del reindexado completo.
* **MDVA-42046** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*): Corrige el problema en el que se asigna un valor incorrecto a un atributo de producto con un campo de entrada de fecha al actualizar un producto.
* **MDVA-43935** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema en el que el producto de venta superior se muestra dos veces.
* **MDVA-44188** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que los correos electrónicos emitidos por el sistema con `.-` en las direcciones no se envían.
* **MDVA-42283** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige un problema en el que el formato de fecha y hora de la cuadrícula de orden de administración de la configuración regional francesa no es válido.
* Revisiones actualizadas: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Se han agregado metadatos de parches para la variable [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.3.6*): corrige el problema en el que el usuario puede editar la hora de inicio de una actualización programada activa.
* **MDVA-42410** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema en el que los informes de cupones solo muestran la moneda base predeterminada.
* **MDVA-41136** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema en el que la fecha de caducidad del `mage-cache-sessid` no se amplía, lo que resulta en una limpieza de los datos del cliente.
* **MDVA-39993** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*): Corrige el problema en el que los cambios de inventario realizados mediante API no se reflejan en la página de producto del front-end.
* **MDVA-42855** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que una nueva dirección de cliente no se guarda en la libreta de direcciones durante el cierre de compra.
* **MDVA-42645** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): Corrige el problema en el que el administrador no puede devolver los puntos de recompensa si la funcionalidad de crédito de la tienda está deshabilitada.
* **MDVA-43414** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2*): corrige el error grave de PHP que ocurre al ejecutar el `inventory.reservations.updateSalabilityStatus` consumidor de cola en SKU numéricos.
* **MDVA-41628** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): Corrige el problema en el que los usuarios administradores restringidos existentes obtienen acceso a los nuevos recursos cuando se añaden nuevos módulos.
* **MDVA-43348** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): Corrige el problema en el que la tarjeta de regalo Solicitud de GraphQL muestra un error si `gift_card_options` contain *uid*.
* **MDVA-39546** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema en el que la fecha de inicio de la actualización de ensayo se podía establecer en una fecha anterior a la fecha actual durante la edición.
* **MDVA-42950** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que los vídeos no se reproducen en la página del producto.
* **MDVA-42689** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que Adobe Commerce lanza un *Violación de restricción de integridad* error al actualizar categorías de productos durante la importación.
* **MDVA-41229** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema en el que las imágenes disponibles en el servidor no se muestran en el front-end después de la importación de productos configurables.
* **MDVA-43731** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el que *Sinónimos de búsqueda* ya no funciona cuando se añade un valor en *Mínimo de términos para coincidir*.
* **MDVA-43232** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): Corrige el problema en el que se ordenaban los productos en [!DNL Visual Merchandiser] por Precio especial en Inferior/Superior causa un error al guardar la categoría.
* **MDVA-43726** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.3*): Corrige el problema en el que la regla de precio del catálogo basada en la coincidencia de atributos de nivel de tienda no se aplicaba después de un reíndice parcial.
* Revisiones actualizadas: MDVA-36464, MDVA-37478, MDVA-38608.
* Se han agregado metadatos de parches para la variable [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que los atributos de precio de producto no se pueden actualizar para un sitio web específico a través de la API de REST.
* **MDVA-41350** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*) : corrige el problema en el que se genera una excepción cuando un usuario administrador con acceso restringido añade un producto fuera de su ámbito de función por SKU en un pedido.
* **MDVA-42269** (*para Adobe Commerce y Magento Open Source >=2.4.3-p1 &lt;2.4.5*): Corrige el problema en el que un usuario administrador no puede iniciar sesión en el administrador debido al *TypeError: strtotime() espera que el parámetro 1 sea una cadena, null dado* error.
* **MDVA-40830** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que el crédito de la tienda se aplica varias veces durante la colocación del pedido.
* **MDVA-42237** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): Corrige el problema en el que un precio especial del producto configurable no se actualiza después de cambios en su precio del subproducto.
* **MDVA-42520** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el que el tipo de impuesto se aplica dos veces si *Habilitar el comercio transfronterizo* se utiliza.
* Revisiones actualizadas: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Parche obsoleto: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.4.5*): Corrige el problema en el que la actualización de atributos masivos crea la reescritura de URL para el almacén predeterminado solo después de cambiar *Visibilidad del producto*.
* **MDVA-43091** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el que al solicitar un producto de paquete desde el administrador en el servidor, se produce el error *No se puede usar la cantidad decimal para este producto*.
* **MDVA-40816** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema en el que las reglas de producto relacionadas muestran productos de categorías no definidas en las condiciones de regla.
* **MDVA-41305** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): Corrige el problema en el que la mutación de GraphQL no devuelve opciones de producto configurables después de añadirla a la lista de deseos.
* **MDVA-39181** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema en el que las reglas de producto relacionadas muestran productos de categorías no definidas en las condiciones de regla.
* **MDVA-42584** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que el estado de existencias configurable en el servidor no se actualiza después de cambiar el estado de cantidad y existencias mediante Import o API.
* **MDVA-40175** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3*): Corrige el problema en el que *Haga clic en para cambiar el método de envío* no muestra botones de opción para seleccionar métodos de envío en Administración durante el reordenamiento.
* **MDVA-42768** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): Corrige el problema en el que el producto configurable muestra un precio normal de 0 cuando *Mostrar fuera de existencias* es Sí.
* **MDVA-43201** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que se producía un error en el inicio de sesión del cliente al utilizar el atributo DOB con determinadas configuraciones regionales.
* Revisiones actualizadas: MDVA-35092, MDVA-33970.

## Versión 1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema en el que los filtros de fecha no funcionan correctamente cuando la zona horaria de Adobe Commerce es diferente de la zona horaria del entorno local.
* **MDVA-42657** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema en el que el usuario administrador no puede seleccionar categorías en las condiciones del segmento del cliente.
* **MDVA-42806** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que un *Registro de nueva empresa* se envía cada vez que se actualiza una empresa existente mediante la API de REST.
* **MDVA-37984** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema en el que la variable [!DNL Visual Merchandiser] *Hacer coincidir producto por regla* no filtra correctamente productos con actualizaciones de ensayo.
* **MDVA-40488** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que los productos configurables con productos secundarios fuera de existencias no se muestran en su rango de precios correcto.
* **MDVA-42507** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que la caché de página completa se limpia después de aplicar la actualización de ensayo para la regla del carro de compras.
* **MDVA-39163** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.5*): Corrige el problema en el que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitados.
* **MDVA-38626** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.5*): Corrige el problema en el que el usuario administrador no es capaz de realizar un pedido en el servidor mediante la función [!DNL PayPal Payflow Pro] pago.
* **MDVA-38666** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.3.6*): Corrige el problema en el que el usuario administrador no puede cambiar las opciones de producto configurables en el carro de compras del cliente.
* **MDVA-38526** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): Corrige el problema en el que el usuario administrador no puede acceder al [!DNL Site-Wide Analysis tool].
* Revisiones actualizadas: MDVA-40101.

## Versión 1.1.8 {#v1-1-8}

* **MDVA-41215** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que los usuarios obtienen el error 500 después de configurar la variable *mensajes de imagen* cookie si ya existe, pero no hay mensajes nuevos.
* **MDVA-41139** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el que los productos configurables se vuelven fuera de existencias después de la importación del producto cuando la cantidad=0 de un producto simple para una de sus fuentes.
* **MDVA-42326** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*): corrige el problema en el que los clientes obtienen un error al cerrar la compra después de un tiempo de espera de sesión, incluso si el carro de compras persistente está habilitado.
* **MDVA-42341** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que la variable `categoryList` La consulta GraphQL no filtra los resultados si una solicitud tiene el encabezado Store .
* **MDVA-38393** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que las reglas del catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple.
* **MDVA-39153** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que una cantidad de descuento se calcula incorrectamente durante la reordenación en el Administrador.
* Revisiones actualizadas: MDVA-28993, MDVA-41061, MDVA-35984.

## Versión 1.1.7 {#v1-1-7}

* **MDVA-39711** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.3*): Corrige el problema en el que los usuarios administradores no pueden acceder a la cuadrícula del cliente después de eliminar el sitio web.
* **MDVA-40311** (*para Adobe Commerce y Magento Open Source >=2.4.2-p2 &lt;2.4.4*): corrige el problema en el que los usuarios administradores reciben el mensaje de error *Seguridad o clave de formulario no válida. Actualice la página* después de iniciar sesión en el administrador si la ruta de administración personalizada está configurada y la clave secreta está habilitada.
* **MDVA-41631** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el que los usuarios obtienen un error al intentar recuperar la información de pedido sin una *phone* a través de GraphQL.
* **MDVA-27239** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.3.6*): Corrige el problema en el que no se muestran los productos de venta cruzada.
* Revisiones actualizadas: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## Versión 1.1.6 {#v1-1-6}

* **MDVA-40550** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.4*): corrige el problema con los productos que faltan en el front-end durante la reindexación.
* **MDVA-40120** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): Corrige el problema en el que la ordenación de GraphQL por DESC/ASC no funciona con productos que tienen la misma relevancia o precio.
* **MDVA-41399** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.2*): Corrige el problema en el que los usuarios administradores no pueden acceder al *Administrar carro de compras* si un cliente agrega un producto a la lista de deseos.
* **MDVA-40609** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que los datos de productos desactivados no están presentes en la variable `cataloginventory_stock_status` tabla de índice, mostrando cantidades incorrectas de productos desactivados.
* **MDVA-39031** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): Corrige el problema en el que es posible añadir un producto al carro de compras mediante GraphQL aunque no esté asignado al sitio web de destino.
* **MDVA-41597** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que los usuarios obtienen un error al agregar más de un producto configurable al carro de compras mediante GraphQL.
* **MDVA-27456** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.3.7*): corrige el problema en el que los usuarios obtienen un error al intentar cargar [!DNL Swagger].
* **MDVA-32776** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.2*): Corrige el problema en el que el estado de stock no se actualiza cuando se realiza un pedido pero no se envía.
* **MDVA-30862** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.0*): corrige el problema con la fecha de pedido incorrecta en la factura de PDF impresa.
* Se ha mejorado la página de índice para la variable [!DNL Quality Patch Tool]. Se ha añadido una búsqueda y un filtrado adecuados para [!DNL quality patches] en la última versión de la herramienta.
* Revisiones actualizadas: MDVA-33382, MDVA-39482.

## Versión 1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que es imposible crear una actualización programada nueva o editar una existente para un producto si la Fecha de finalización se ha eliminado anteriormente.
* **MDVA-41046** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que los productos simples con opciones personalizadas están disponibles para su asignación a productos configurables o agrupados.
* **MDVA-40545** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que solo se recuperaba el primer nodo de una página aunque hubiera más de un nodo para la misma página.
* **MDVA-41164** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3-p1*): Corrige el problema en el que un usuario administrador no puede guardar o editar una empresa con un atributo de cliente personalizado de tipo de archivo o imagen.
* **MDVA-39229** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*) - Corrige el problema que causaba que apareciera el siguiente error después de actualizar la regla de Catálogo en la hora de inicio Actualización de ensayo: *Cron Job staging_sync_entities_period tiene un error: La actualización activa no se puede eliminar.*
* **MDVA-40619** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que los cambios en la jerarquía de páginas de CMS causaban un error 500 al intentar realizar la edición en línea en una página de CMS.
* **MDVA-41061** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que el estado de existencias se restablece como vendible cuando se guarda un producto del administrador.
* **MDVA-31763** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que las reglas de precios del catálogo se revierten (o no se aplican) hasta que se vuelve a indexar manualmente.
* **MDVA-37748** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que una consulta de GraphQL devuelve productos no asignados a un catálogo compartido.

## Versión 1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente a través de la API de REST.
* **MDVA-40101** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.4.0*): Corrige el problema en el que los artículos no se eliminan del minicarro después de una colocación correcta de los pedidos mediante [!DNL PayPal Express] Cierre de compra.
* **MDVA-40401** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Corrige el problema en el que el valor de uso de cupones cambia incluso si falla la realización de un pedido.
* **MDVA-40537** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.4.0-p1*): corrige el problema en el que los usuarios obtienen un error al crear una vista de tienda si existen varias páginas de CMS con la misma clave de URL.
* **MDVA-37725** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) : corrige el problema en el que los correos electrónicos de pedidos asincrónicos enviados desde sitios web no predeterminados contienen direcciones URL de logotipo del sitio web predeterminado.
* **MDVA-39482** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*): Corrige el problema en el que un producto se queda sin existencias si se importa con la cantidad &quot;0&quot; cuando los pedidos secundarios están habilitados.
* **MDVA-40435** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.4*) : Corrige el problema con un descuento incorrecto en los productos de paquete con precios dinámicos cuando se aplican mediante GraphQL.
* **MC-42528** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;=2.4.3-p1*): Corrige el problema en el que la variable `categoryList` La consulta GraphQL devuelve las categorías asignadas y no asignadas.
* **MDVA-29400** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*): Corrige el problema con los pedidos duplicados colocados con [!DNL PayPal Express Checkout].
* **MDVA-26005** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.3.5-p2*): Corrige el problema en el que es imposible seleccionar una categoría en un árbol de categorías para las condiciones de regla de precio del carro de compras.
* **MDVA-25631** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) : mejora el rendimiento para editar y guardar segmentos del cliente que contienen un gran número de clientes.

## Versión 1.1.3 {#v1-1-3}

* **MDVA-40262** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que las consultas de búsqueda de GraphQL no se muestran en los términos de búsqueda populares en el Administrador.
* **MDVA-40601** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) : corrige el problema en el que los usuarios obtienen un error al intentar obtener información sobre la categoría cambiada mediante la actualización programada a través de GraphQL.
* **MDVA-37234** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*): Corrige el problema en el que, al agregar un artículo al carro varias veces (solicitud paralela) para el mismo SKU, se crea un elemento de línea duplicado para el mismo ID del carro de compras.
* **MDVA-33606** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;=2.4.2-p2*): Corrige el problema en el que los usuarios obtienen un *Infracción de restricción única* al guardar una página de CMS asignada a una jerarquía.
* **MDVA-31590** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Corrige el problema en el que los usuarios no son capaces de actualizar atributos de forma masiva utilizando colas asincrónicas de MySQL.
* **MDVA-36309** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): Corrige el problema en el que la búsqueda de productos por atributos es lenta en las cuadrículas de administración.

## Versión 1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que la factura con FPT muestra un total general incorrecto cuando el pedido se paga desde el crédito del almacén.
* **MDVA-37364** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.3*): corrige el problema en el que el atributo personalizado del cliente del tipo de fecha rompe la IU de la cuadrícula del cliente.
* **MDVA-39195** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): Corrige el problema en el que *Agregar al carro* estaba inactivo en la página de categorías cuando se habilitó el redireccionamiento al carro de compras.
* **MDVA-37115** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): Corrige el problema en el que no era necesario *Solo 0 izquierda* el aviso se muestra en la página del producto configurable.
* **MDVA-39521** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*) : corrige el problema en el que el usuario no puede establecer direcciones de envío en el carro de compras con un número de teléfono vacío a través de GraphQL.
* **MDVA-39384** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*): Corrige el problema en el que el atributo de cliente personalizado para un usuario de empresa no se guardaba.
* **MDVA-39043** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.4.3*): Corrige el problema en el que el usuario administrador con acceso limitado obtiene un error al intentar agregar la variable *Productos* a la página de CMS.
* **MDVA-39966** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*): Corrige el problema con la implementación de configuraciones regionales incorrectas.
* **MDVA-38852** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) : corrige el problema en el que el inventario de catálogos por diseño bloquea las tablas para actualizaciones que disminuyen significativamente el rendimiento en casos con varios pedidos paralelos.
* **MDVA-39986** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): Corrige el problema en el que el usuario no podía realizar un pedido en el Administrador de MacOS mediante el explorador Safari.
* **MDVA-38447** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige dos problemas: donde *No visible individualmente* los productos secundarios configurables se devuelven en la respuesta de GraphQL y optimizan la consulta MySQL para la consulta de productos GraphQL con filtro de categoría.
* **MDVA-40134** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que GraphQL no devuelve productos relacionados cuando el Catálogo compartido está habilitado.
* **MDVA-39935** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el que GraphQL devuelve productos secundarios configurables deshabilitados a nivel de sitio web.

## Versión 1.1.1 {#v1-1-1}

* **MDVA-36021** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*): Corrige el problema en el que la variable *Llamada a una función de miembro getId()* se muestra en la página de detalles del pedido en el Administrador.
* **MDVA-34948** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*): Corrige el problema con las consultas de larga duración, como `GET_LOCK`.
* **MDVA-39305** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.2-p1*): Corrige el problema en el que los clientes registrados no pueden iniciar sesión con Google ReCaptcha habilitado.
* **MDVA-37897** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema con una redirección incorrecta cuando un cliente intenta añadir productos con opciones del widget Visualizado recientemente.

## Versión 1.1.0 {#v1-1-0}

* Se han introducido categorías de parches para mejorar la experiencia del usuario y facilitar la búsqueda de los parches necesarios para los clientes.
* La variable `patches.json` se ha cambiado el nombre del archivo a `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema en el que los productos descargables no se guardaban después de crear una actualización de ensayo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): corrige el problema cuando la ordenación por precio no funciona correctamente para productos con un precio cero asignado al catálogo compartido.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*): corrige el problema en el que los clientes reciben un correo electrónico de envío de pedido que contiene un mensaje de error.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*): Corrige el error al guardar páginas de CMS: *El elemento con el mismo ID PAGE_ID ya existe*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*): Corrige el problema en el que el tiempo de creación de la cuenta de cliente no se filtraba correctamente en la cuadrícula de los clientes.
* **MDVA-37068** (*para Adobe Commerce >=2.3.1 &lt;2.4.4*): corrige el problema en el que se muestra la tasa de impuestos incorrecta cuando el carro de compras solo tiene productos virtuales.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema en el que las tablas temporales no se eliminan cuando el reíndice no ha finalizado correctamente.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*): Corrige los problemas relacionados con la adición de [!DNL Vimeo] vídeos para productos.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*): Corrige el problema en el que el cliente no es dirigido a la página de confirmación de pago al usar la variable [!DNL Paypal Payment Advanced] método.
* **MDVA-37082** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema al guardar el stock personalizado de productos agrupados, que hace que el producto se muestre sin existencias en el front-end.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*): Corrige el problema cuando las actualizaciones de las notas de crédito ya no causan actualizaciones de reservas de productos duplicadas en la base de datos.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*): Corrige el problema cuando el panel de administración no está disponible debido a una *demasiadas redirecciones* error.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): Corrige el problema de la falta de información de la tarjeta de regalo en el total del pedido en GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*para Adobe Commerce >=2.4.2 &lt;=2.4.4*): Corrige el problema de añadir un producto configurable al carro de compras mediante GraphQL cuando el ID del sitio web no coincide con el ID de la tienda.
* **MDVA-36832** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): corrige el problema en el que las imágenes se duplican en las páginas cuando la anchura de la vista es de 768 px.
* **MDVA-37874** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*): Corrige el problema en el que *Cantidad de descuento fija para todo el carro* se aplica incorrectamente a un producto de paquete que contiene más de una opción.
* **MDVA-37913** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*): Corrige el problema en el que los vínculos descargables desaparecen si el producto descargable se actualiza mediante API.
* **MDVA-34330** (*para Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*): corrige el problema en el que los pedidos de la cuadrícula Pedidos no se filtran según la zona horaria del administrador.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*para Adobe Commerce >=2.3.0 &lt;=2.3.7*): Corrige el problema en el que Adobe Commerce generaba un error al crear una factura parcial para los pedidos colocados con la variable *Pago a cuenta* método de pago a través de la API de REST.
* **MDVA-37362** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): Corrige el problema en el que los valores de opciones de producto configurables y los valores de atributos de variante estaban vacíos en la respuesta de GraphQL.
* **MDVA-37288** (*para Adobe Commerce 2.4.2*): Corrige el problema en el que se devolvían precios de nivel incorrectos después de la solicitud de GraphQL.
* **MDVA-37225** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*): Corrige el problema en el que el proceso de carga se atasca durante la creación rápida de pedidos cuando hay un valor entero en los SKU importados.
* **MDVA-37224** (*para Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*): corrige el problema en el que los clientes no pueden pagar por una cotización negociable con [!DNL PayFlow Pro] con otro producto del carro de compras.
* **MDVA-36286** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): Corrige el problema en el que la vista previa de los productos de Page Builder se rompe si el mismo SKU tiene una posición diferente en las subcategorías.
* **MDVA-30186** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*): Corrige el problema en el que las opciones de atributo se ordenan por valor de opción en lugar del recuento de elementos de atributo en la respuesta de GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Commerce >=2.3.0 &lt;=2.4.2*): Corrige el problema en el que las opciones personalizadas antiguas permanecen después de cambiarse mediante API.
* **MDVA-35773** (*para Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*): corrige el problema con el Total general que no se muestra como cero en la factura para pedidos con 100% de descuento.
* **MDVA-36833** (*para Adobe Commerce 2.4.2*) : corrige el problema con los resultados de búsqueda que muestran números aleatorios de productos por página después de excluir algunos productos del catálogo compartido.
* **MDVA-37182** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2*): Corrige el problema de obtener resultados de búsqueda incorrectos en ambas [!DNL Elasticsearch] versión 6 y versión 7.
* **MDVA-36253** (*para Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*): corrige el problema en el que se muestra el subtotal incorrecto en el minicarro tras la eliminación del elemento.
* **MDVA-36853** (*para Adobe Commerce 2.4.2*): Corrige el problema sin que aparecieran imágenes al cargar grandes galerías de medios.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*): Corrige el problema de la falta de productos empaquetados en las páginas de categoría.
* **MDVA-36615** (*para Adobe Commerce 2.4.2*): Corrige el problema con un recuento de productos incorrecto en la cuadrícula del producto Administrador .
* **MDVA-36464** (*para Adobe Commerce >=2.4.0 &lt;=2.4.2*): Corrige el problema en el que la configuración de notificaciones por correo electrónico no funciona en el nivel de vista de tienda.
* **MDVA-36138** (*para Adobe Commerce ^2.3.2*) - Corrige el problema en el que el precio de envío no se ajusta y el precio de envío completo se muestra a los clientes si no todos los artículos del carro cumplen con la regla del carro de envío gratuito.
* **MDVA-36424** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*): Corrige el problema en el que las imágenes de medios adjuntas a los elementos del creador de páginas desaparecen cuando el contenido se edita repetidamente si la URL de base del servidor es diferente de la URL de base de la tienda.
* **MDVA-35984** (*para Adobe Commerce ^2.4.0*): Corrige el problema con la cantidad de producto incorrecta y la cantidad vendible después de crear varios envíos simultáneos para el mismo producto.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) : Esto corrige el problema en el que la consulta de GraphQL no se almacena en caché mediante la etiqueta de caché de categoría.
* **MDVA-33168** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): Corrige el problema al actualizar un atributo de producto mediante API, cuando el resto de atributos cambian a un valor vacío.
* **MDVA-19640** (*para Adobe Commerce >=2.3.0*): Corrige el problema en el que [!DNL Advanced Reporting] no muestra ningún dato.
* **MDVA-11189** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): Corrige el problema que se producía al importar un archivo CSV para actualizar las existencias de productos y las filas del `cataloginventory_stock` se eliminan.
* **MDVA-26639** (*para Adobe Commerce >=2.3.3-p1 &lt;2.3.6*): Corrige el problema en el que, si se crea una nueva plantilla de correo electrónico de confirmación de pedido, faltan los elementos de pedido en el correo de pedido.
* **MDVA-15546** (*para Adobe Commerce >=2.3.0*): Corrige el problema en el que, después de crear una solicitud, *La cláusula entity_id de columna donde la cláusula es ambigua* se muestra en el registro de excepciones.
* **MDVA-21095** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): Corrige el problema cuando se realiza una consulta `INSERT INTO search_tmp` no finalizará después de la actualización del valor de atributo masivo.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): Corrige el problema en el que las plantillas de correo electrónico no se pueden previsualizar una vez habilitada la minificación de JavaScript.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): Corrige el problema en el que se producía un error al importar productos desde un archivo CSV, incluidas imágenes de direcciones URL externas.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): Corrige el problema en el que guardar un producto lleva mucho tiempo y la página se rompe.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*): Corrige el problema de la configuración incorrecta de los parámetros de cookies de SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*para Adobe Commerce 2.4.1*): Corrige el problema en el que el Generador de páginas generaba el siguiente error: *Error al iniciar el Creador de páginas. Consulte con su contacto de asistencia técnica.*
* **MDVA-35356** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema con una devolución de crédito de almacén incorrecta después de la cancelación de pedido parcialmente facturada.
* **MDVA-33289** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*): Corrige el problema en el que el código JavaScript sin procesar se muestra en la interfaz de usuario de la dirección de facturación durante el cierre de compra si [!DNL Google Tag Manager] está activada.
* **MDVA-35982** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema en el que los usuarios administradores restringidos a un sitio web específico no pueden crear un envío para el pedido realizado en el mismo sitio web.
* **MDVA-35155** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*) - Corrige el problema en el que era imposible comprar un producto de paquete si se cambiaba el título de la opción.
* **MDVA-35910** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): Corrige el problema en el que es imposible crear una nueva cuenta de cliente después de desactivar el inicio de sesión como funcionalidad de cliente.
* **MDVA-34474** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema que se producía al añadir un producto a la lista de solicitudes mediante la API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema con un cálculo de descuento de regla de carro de compras incorrecto para *El descuento de cantidad máxima se aplica a* y *Paso de cantidad de descuento (Comprar X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*): Corrige el problema en el que la variable *Recogida en la tienda* la opción de envío no aparece, aunque está configurada para estar disponible.
* **MDVA-34928** (*para Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Corrige el problema en el que el cargador de páginas se muestra indefinidamente después de que se elimine el crédito de la tienda del pago.
* **MDVA-35254** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*): Corrige los problemas con CAPTCHA durante el cierre de compra.
* **MDVA-35569** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): Corrige el problema en el que la variable *impuestos fijos* no se rellena en la respuesta de GraphQL cuando se especifica el estado.
* **MDVA-35847** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*) - Corrige el problema B2B en el que el formulario Usuarios de la empresa se rompe si se utiliza un atributo de cliente personalizado.
* **MDVA-31307** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): Corrige el problema donde hay *Memoria insuficiente* errores en ciertas categorías debido a problemas con listas blancas de CSP dinámicas para bloques en caché.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el error *en curso* el estado del mensaje es correcto *complete* mensaje para consumidores `quoteItemCleaner` después de eliminar varios productos.
* **MDVA-34102** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige que la cantidad de Stock predeterminado es cero para los productos desactivados en las páginas Cuadrícula de productos y Editar producto en el área Administración .
* **MDVA-35286** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): Corrige el problema en el que hay un error si un cliente tiene productos empaquetados en el carro de compras y cambia de la compra de Varias direcciones a la compra de una página.
* **MDVA-35312** (*para Adobe Commerce >=2.4.1-p1 &lt;2.4.2*): Corrige el código de respuesta 500 cuando una solicitud de GraphQL vacía.
* **MDVA-34189** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige el 503 primer tiempo de espera de byte en [!DNL Visual Merchandiser] consultas al cargar la página Categoría de administración .
* **MDVA-34695** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) - Correcciones negativas `children_count` después de eliminar categorías.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*): Corrige el problema en el que la variable *Utilizar valor predeterminado* se borra después de aplicar los cambios programados. El problema aparece una vez que los cambios programados ya no están en vigor.
* **MDVA-35064** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*): Corrige el problema en el que las reescrituras de URL no se generan para productos configurables creados mediante API.
* **MDVA-34943** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los pedidos rápidos almacenan en caché los SKU introducidos anteriormente.
* **MDVA-35197** (*para Adobe Commerce >=2.3.5 &lt;2.4.0*): Corrige el problema en el que se producía un error al añadir al carro de compras mediante GraphQL si los productos añadidos anteriormente no estaban en existencias.
* **MDVA-34850** (*para Adobe Commerce >=2.3.1 &lt;2.4.0*): Corrige el problema en el que las opciones sin existencias de un producto configurable no se muestran en lugar de mostrarse como pulsadas.
* **MDVA-34867** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema en el que no se están guardando los valores de un campo de condición definido para una actualización programada.
* **MDVA-35092** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*): Corrige el problema en el que los usuarios no pueden agregar [!DNL Vimeo] vídeos en desuso [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*): Corrige el problema en el que la vista previa del tipo de contenido de Productos de Page Builder se rompe si los productos coincidentes tienen precios diferentes para cada sitio web.
* **MDVA-32634** (*para Adobe Commerce ^2.3.1*): Corrige el problema en el que la variable `url_path` de la categoría asignada a todas las tiendas permanece sin cambios después de mover la categoría en la jerarquía.
* **MDVA-33344** (*para Adobe Commerce ^2.3.0*): Corrige el problema en el que estaba codificado de forma rígida `rma_item` se utiliza el ID del conjunto de atributos predeterminado de entidad en lugar del valor de la base de datos.
* **MDVA-34192** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*) - Corrige el problema en el que es imposible modificar o especificar la fecha de nacimiento del cliente utilizando el formato dd/mm/aaaa.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*): Corrige la conversión de tipo de ID de almacén a entero para la condición SQL en las colecciones de administración para el usuario administrador con permisos personalizados.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*): Corrige el problema en el que la búsqueda no devuelve resultados si *weight* el atributo product está configurado como buscable.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema de [!DNL PayPal Payflow Pro] error de pago con el formato de lista de parámetros de redireccionamiento.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema en el que el error *No existe dicha entidad con addressId* se muestra aleatoriamente en los navegadores de los visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 con extensión B2B*): corrige el problema en el que los catálogos compartidos eliminan los precios de nivel existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*): corrige el problema en el que la generación de una nota de crédito contra una factura parcial genera impuestos para el pedido total en lugar de impuestos para esa factura parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el error *El countryId proporcionado no existe*.
* **MDVA-33632** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*): Proporciona una corrección en la que el mensaje de excepción *Este producto no está en existencias* ahora se muestra a un usuario administrador al intentar reordenar un producto sin existencias.
* **MDVA-34469** (*para Adobe Commerce >=2.4.1 &lt;2.4.2*): corrige el problema en el que las mutaciones de GraphQL en el carro de compras de un cliente fallan al usar varias vistas de tienda.
* **MDVA-33976** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*): Corrige el problema en el que el producto del paquete se muestra fuera de existencias en la tienda después de eliminar la segunda opción del producto del paquete.
* **MDVA-33894** (*para Adobe Commerce >=2.4.0 &lt;2.4.1 con extensión B2B*): corrige varios problemas de la funcionalidad de pedidos rápidos, incluida la adición y eliminación de varios productos y la distinción entre mayúsculas y minúsculas en el SKU.
* **MDVA-27664** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*) - Corrige el problema en el formulario de registro de cliente que provocaba que se mostrara un error: *ERROR - La fecha de nacimiento no debería ser buena que hoy.*
* **MDVA-33970** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) - Corrige el problema en el que hay un signo de moneda incorrecto en la nota de crédito cuando el ámbito del atributo de precio está establecido en el sitio web.
* **MDVA-33992** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema de los precios especiales de B2B que se mostraban incorrectamente durante el cierre de compra.
* **MDVA-34100** (*para Adobe Commerce >=2.3.4 &lt;2.4.2 con extensión B2B*): corrige el problema en el que una cuenta de empresa no se puede crear desde la página de estructura de la empresa.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*para Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*): Corrige el problema con las imágenes duplicadas después de la importación del producto desde un archivo CSV.
* **MDVA-33382** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige los problemas con la invalidación de los indexadores después de la eliminación de productos de una categoría.
* **MDVA-28511** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*): Corrige el problema en el que no es posible finalizar [!DNL PayPal] cierre la compra si el campo Nombre contiene ciertos caracteres (como mayúsculas acentuadas).
* **MDVA-31519** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*): Corrige el problema con los tiempos de espera en el cierre de compra de un invitado cuando se está utilizando una regla de ventas para todo el sitio.
* **MDVA-33281** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*): Corrige el problema en el que hay un error grave en `inventory:reservation:list-inconsistencies` debido a un tipo de parámetro de SKU incorrecto.
* **MDVA-24201** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): Corrige el problema en el que los precios no reflejan la regla de precio del carro de compras programado hasta que se vuelven a indexar manualmente.
* **MDVA-32694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*): corrige el problema en el que un usuario administrador no puede agregar un producto a una oferta negociable si está relacionado con una tienda no predeterminada.
* **MDVA-33516** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): Corrige el problema en el que editar un producto de paquete en una lista de solicitudes producía un error.
* **MDVA-33975** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*) : corrige varios problemas relacionados con el cálculo de precios en solicitudes de GraphQL.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema con [!DNL PayPal] Los informes de liquidación no están disponibles en **Informes** > **Ventas** > **[!DNL PayPal]** Liquidación según lo esperado.
* **MCP-87** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*) - Se ha mejorado el tiempo de indexación de los indexadores de productos y existencias de categoría para perfiles grandes.
* **MDVA-33106** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que los cambios del producto reprogramados se borran después de cron `run` se ejecuta.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): Corrige el problema en el que `analytics_collect_data` está generando un error debido a registros de descripción NULL en la variable `catalog_category_entity_text` tabla.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): Corrige el problema con la variable *No existe tal entidad con customerId = 1* en el `exception.log` para clientes que han iniciado sesión después de la colocación del pedido.
* **MDVA-23764** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige el error en `JsFooterPlugin.php` que afecta a la visualización de bloques dinámicos.
* **MDVA-13203** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que la variable *Infracción de restricción de integridad search_tmp_ table* aparece después de un reíndice completo.
* **MDVA-23426** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*): corrige el problema en el que los correos electrónicos de notificación enviados por Adobe Commerce contienen un cuerpo en blanco con el contenido añadido como datos adjuntos.
* **MDVA-22150** (*para Adobe Commerce >=2.3.1 &lt;2.3.4*): Corrige el problema en el que los clientes con un producto configurable en el carro de compras y un cupón aplicado no pueden iniciar sesión si ese producto configurable está deshabilitado en el administrador.
* **MDVA-32545** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que las facturas no se envían automáticamente al crear pedidos desde el administrador.
* **MDVA-32714** (*para Adobe Commerce >=2.3.4 &lt;2.4.1*): Corrige el problema en el que el precio del grupo de clientes no funciona en la consulta de producto de GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Agrega la variable *Subtotal (incl. Impuesto)* para fijar el precio de las condiciones de la regla.
* **MDVA-31236** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): Corrige el problema en el que los administradores con acceso a recursos personalizado no podían configurar 2FA o iniciar sesión.
* **MDVA-30845** (*para Adobe Commerce >=2.3.5 &lt;2.3.7*): Corrige el problema en el que la variable *Lo sentimos, no hay comillas disponibles para este pedido en este momento* se muestra cuando no se puede conectar a UPS XML/USPS/DHL, y no hay ningún otro método de envío disponible.
* **MDVA-32133** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): Corrige el problema en el que la galería de medios no se carga desde el Creador de páginas en determinados casos.
* **MDVA-12304** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Aumenta el número máximo de cookies de 50 a 200.
* **MDVA-32632** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*) - Corrige el problema en el que los pedidos aparecen en el sistema de pago, pero no en Adobe Commerce.
* **MDVA-32449** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 con extensión B2B*) : corrige el problema en el que el historial de pedidos se carga muy lentamente o no se carga nada.
* **MDVA-32739** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que al habilitar Notificaciones de correo electrónico asincrónicas se envían correos electrónicos de ventas antiguos.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*para Adobe Commerce 2.3.6, 2.4.1*): Corrige el problema en el que la variable *Crear una cuenta* permanece desactivado después de corregir datos no válidos en el *Crear nueva cuenta de cliente* formulario.
* **MDVA-31006** (*para Adobe Commerce 2.3.0, 2.3.1*): Corrige el problema en el que aparecen los pedidos duplicados después de realizar un pedido mediante [!DNL Paypal Express] pago.
* **MDVA-25602** (*para Adobe Commerce 2.3.0*): corrige un problema con [!DNL PayPal Payflow Pro] método de pago y tratamiento de cookies como `SameSite=Lax` de forma predeterminada, en el explorador Chrome 80 y el redireccionamiento de la respuesta de API a la página de inicio de sesión del cliente.

## v1.0.10 {#v1-0-10}

Correcciones menores para versiones de parches

## Versión 1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): Corrige el problema en el que la regla de precio del carro de compras con cupón no se aplica a través de GraphQL cuando *Descuento de cantidad fija para todo el carro* se utiliza.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que se producía un error después de facturar un paquete con productos simples y virtuales como opciones.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*) : mejora el rendimiento de la página del producto en los casos en que se utilizan reglas de objetivo o productos vinculados.
* **MDVA-31168** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que el archivo CSV de exportación de producto no aparece y hay un error de asignación de memoria.
* **MDVA-32313** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): Corrige el problema en el que los productos configurables se podían agregar a la lista de deseos con las opciones de configuración incorrectas.
* **MDVA-31759** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que los productos no se actualizan con *lista desplegable* y *área de texto* durante la importación de CSV.
* **MDVA-32012** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige el problema en el que los códigos postales de Corea y Argentina no se pueden validar.
* **MDVA-31640** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*): Corrige el problema en el que un precio especial no se puede actualizar a través de la API de REST.
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 con extensión B2B*): Corrige el problema en el que hay problemas de rendimiento al cargar presupuestos negociables a través de la API de REST.

## Versión 1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Commerce >=2.3.0 &lt;2.4.1 con extensión B2B*): corrige el problema en el que se muestra un signo de moneda incorrecto en la cuadrícula Nota de crédito .
* **MDVA-31295** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que los puntos de recompensa no se calculan cuando se completa un pedido parcial y se gravan los artículos.
* **MDVA-30112** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): Corrige el problema en el que si el número de pedidos supera el valor de *tamaño de grupo* , Adobe Commerce considera los pedidos con *pending* como inconsistencias.
* **MDVA-31150** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los saldos de tarjetas de regalo y crédito de tienda no son devueltos por la llamada API de Rest de Factura de GET, cuando la factura fue registrada por la llamada de API de Rest y el pedido fue pagado parcialmente por cuentas de tarjeta de regalo y crédito de la tienda.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): Corrige el problema en el que los resultados de filtrado de productos configurados para contener solo valores especificados para *Todas las vistas de tiendas* en Admin, incluya productos con valores anulados en el nivel de vista de tienda.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 con extensión B2B*): Corrige el problema en el que la variable *Nueva solicitud de registro de empresa* y *Se le ha vinculado a una empresa* los correos electrónicos se envían desde la dirección incorrecta.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*): Reemplaza el analizador estándar con un analizador personalizado por un token de palabra clave para el campo SKU en la variable [!DNL ElasticSearch] índice para hacer que las consultas de búsqueda con comodines funcionen con SKU que contengan un guión (&quot;-&quot;).

## Versión 1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que el estado de pedido personalizado se cambiaba a *Procesamiento* después de la creación parcial del envío utilizando WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*): Corrige el problema en el que los clientes no pueden agregar un producto a la lista de deseos si este producto está asignado a un origen de inventario personalizado.
* **MDVA-30594** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que un pedido con varias direcciones no se podía guardar durante el cierre de compra cuando se configuraba FPT.
* **MDVA-29148** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema al crear un producto mediante una llamada de API, el atributo personalizado del producto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multiselect) no utiliza su valor predeterminado si no se proporcionó ningún valor en la carga útil.
* **MDVA-30837** (*para Adobe Commerce >=2.3.1 &lt;2.3.5*) - Se ha añadido una configuración *Incluir Impuesto al Importe: Sí/No* en la configuración del método de envío gratuito. When *Incluir impuesto a importe* está configurado como *Sí*, el importe mínimo de pedido se calcula como subtotal + impuesto. When *Incluir impuesto a importe* está configurado como *No*, el importe mínimo del pedido se calcula como subtotal
* **MDVA-25028** (*para Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*): Corrige el problema cuando se realizan pedidos mediante [!DNL PayPal Payflow Pro] no se establecen en estado de Fraude sospechoso cuando se activan los filtros de fraude.
* **MDVA-31224** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*): mejora el rendimiento del `catalog_product_price` reindexe la operación para productos de paquetes.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): Corrige una página en blanco (error) al *Mostrar todo* está seleccionado. [!DNL Elasticsearch] devuelve una larga lista de id de producto. En este escenario, el orden por cláusula se convierte a un formato SQL incorrecto.
* **MDVA-30815** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): Corrige el problema en el que, al cambiar cuántos resultados de búsqueda se deben mostrar en la página de resultados de la búsqueda, Adobe Commerce muestra una página en blanco. [!DNL Elasticsearch] ahora muestra correctamente los resultados de las páginas de categoría al cambiar el número de resultados de búsqueda vistos por página.
* **MDVA-30782** (*para Adobe Commerce >=2.3.5 &lt;2.4.2*): corrige el problema en el que el bloque dinámico se muestra independientemente de la regla del carro de compras.
* **MDVA-31021** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que existen problemas de rendimiento en `module-catalog-import-export/Model/Import/Product/Option.php`. Si hay más de ~100.000 registros en `catalog_product_option` , un nuevo CSV con un solo producto tarda menos de 10 segundos en validarse.
* **MDVA-31007** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): Corrige el problema en el que los atributos de dirección personalizados no se mostraban correctamente en la página de detalles del pedido en el área de mi cuenta y en el servidor.
* **MDVA-29389** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema de los Informes avanzados en el que la variable `analytics_collect_data` cronjob dice: *El puerto debe configurarse dentro del parámetro de host (como localhost:3306)*.
* **MDVA-31343** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*): Corrige el problema con la clase body eliminada `page-layout-category-full-width` cuando se programa una categoría.
* **MDVA-30945** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que recibe un mensaje de error grave al actualizar los carros de compras `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## Versión 1.0.6 {#v1-0-6}

* **MDVA-28993** (*para Adobe Commerce >=2.3.4 &lt;2.4.0*): implementa el *El mínimo debe coincidir* funcionalidad y búsqueda parcial de [!DNL Elasticsearch] motor. Soluciona los problemas con guiones en las consultas de búsqueda.
* **MDVA-30102** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) : corrige el problema en el que la caché de Redis crece rápidamente ya que las cachés de diseño no tienen TTL.
* **MDVA-30599** (*para Adobe Commerce >=2.3.4 &lt;=2.4.0*): Corrige el problema en el que las comillas de invitado creadas con API se marcan incorrectamente como comillas para los clientes que han iniciado sesión.
* **MDVA-29446** (*para Adobe Commerce >=2.3.3 &lt;=2.4.0*): corrige el problema en el que el precio del método de envío no aplicable se muestra como cero durante el cierre de compra.
* **MDVA-30357** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*) : corrige el problema con las URL de imagen erróneas que se crean al generar un mapa del sitio mediante cron.
* **MDVA-30565** (*para Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*): Corrige el problema en el que *No existe tal entidad con cartid = 0* se muestra un error para el cliente invitado en el cierre de compra de tienda si el carro de compras persistente está habilitado.
* **MDVA-29787** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0*): Corrige el problema en el que la regla de objetivo para productos relacionados no funciona cuando *es uno de* se utiliza para definir los productos que se van a mostrar.
* **MDVA-30977** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*): Corrige el problema con los productos aleatorios que faltan en las categorías después del reindexado.
* **MDVA-28202** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2*): Corrige el problema en el que la navegación en capas no filtra correctamente los productos configurables cuando se utiliza MSI.
* **MDVA-28300** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): Corrige el problema en el que la solicitud de GQL no refleja los cambios de precio de las reglas de precio del catálogo.
* **MDVA-31006** (*para Adobe Commerce >=2.3.2 &lt;=2.4.2*): Corrige el problema en el que aparecen los pedidos duplicados después de realizar un pedido mediante [!DNL Paypal Express] pago.

## Versión 1.0.5 {#v1-0-5}

* **MDVA-30841** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): Corrige el problema de la navegación en capas, en la que la función *No* el valor de los atributos de producto de tipo booleano no se incluyó en la navegación en capas si [!DNL Elasticsearch] se usaba como motor de búsqueda.
* **MDVA-28191** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) - Corrige el problema en el que no se cargaban métodos de pago durante la creación del pedido a través del administrador.
* **MDVA-29959** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 con extensión B2B*): corrige el problema en el que el usuario administrador restringido con *Compañías* no se permite que los permisos eliminen la cuenta de empresa.
* **MDVA-30265** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): corrige el problema en el que el vínculo de seguimiento de envíos deja de funcionar después de la creación de la factura.
* **MDVA-28409** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): Corrige el problema en el que la variable `sales_clean_quotes` el trabajo cron falla con *memoria insuficiente* cuando el número de comillas caducadas en la base de datos es enorme.
* **MDVA-30593** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema en el que las comillas que caducaron de acuerdo con la configuración Duración de la cotización no se limpian.
* **MDVA-30107** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): Corrige el problema en el que el conmutador de tienda no funciona como se esperaba si se usan distintas URL base para las vistas de tienda.
* **MDVA-28763** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): Corrige el problema en el que la imagen del producto se duplica después de actualizar la información del producto con la API de REST más de una vez.
* **MDVA-30284** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige el problema en el que el indexador de Búsqueda en el catálogo falla debido a lo siguiente *[!DNL Elasticsearch]error: se ha superado el límite de campos totales en el índice.*
* **MDVA-29042** (*para Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 con extensión B2B*): Corrige el problema en el que los permisos del catálogo se cambiaban a *Permitir* automáticamente después de agregar el nuevo producto al catálogo compartido.
* **MDVA-30428** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): Corrige el problema en el que los clientes no pueden agregar un producto a la lista de deseos si este producto está asignado a un origen de inventario personalizado.
* **MDVA-28661** (*para Adobe Commerce >=2.3.0 &lt;2.4.2 con extensión B2B*): Corrige el problema en el que se produce un error en la sección de cuenta de empresa de usuarios de la empresa después de cambiar el administrador de la empresa.

## Versión 1.0.4 {#v1-0-4}

* **MDVA-30195** (*para Adobe Commerce 2.3.1 - 2.3.4-p2*) : corrige el problema en el que los trabajos cron fallan si el nombre de la base de datos es demasiado largo, lo que provoca que las categorías no se actualicen en el front-end.
* **MDVA-30106** (*para Adobe Commerce ^2.3.0*): corrige un problema en el que durante los pagos de cierre de compra no se cargan con *No se puede leer la propiedad &#39;length&#39; de null* en la consola JS.
* **MDVA-28656** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*): Corrige el problema en el que si se realizaba un pedido sin información de pago necesaria (por ejemplo, con descuento del 100 %) y se creaba una factura para el pedido, el estado del pedido cambia a *Cerrado* en lugar de Completar.
* **MDVA-30209** (*para Adobe Commerce 2.3.0 - 2.3.3-p1*): Corrige el problema en el que el grupo de clientes se cambiaba a predeterminado si el cliente actualizaba su información de cuenta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): Corrige el problema en el que las etiquetas de opciones de atributos no se traducen correctamente para las consultas de GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*) : corrige el problema en el que después de habilitar el permiso de categoría, la página de categoría no se almacena en caché en la caché de página completa.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*): Corrige el problema en el que los registros de clientes no se pueden exportar de la cuadrícula Clientes si existen atributos de cliente personalizados.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*) : corrige el problema en el que no se envía ningún correo electrónico de confirmación para los pedidos realizados con GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4 - 2.3.5-p2*): Corrige el problema en el que la comparación de productos lanza la página de error 500 si uno de los productos tiene una descripción breve vacía.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*): Corrige el problema en el que no es posible realizar un nuevo pedido si el pedido original contiene una tarjeta de regalo.
* **MDVA-29965** (*para Adobe Commerce >=2.3.3 &lt;2.4.0*): corrige el problema en el que los clientes obtienen un error de clave de formulario no válida al agregar un producto al carro de compras.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema B2B en el que no es posible realizar pedidos a través de la API de administrador para un producto que está en un catálogo público.
* **MDVA-22469** (*para Adobe Commerce 2.3.2-p2 - 2.3.3-p1*): Corrige el problema en el que, después de actualizar a Adobe Commerce 2.3.3, el Creador de páginas no funciona en el panel de administración y algunos archivos JS y CSS no se cargan.
* **MC-35984** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): Corrige el problema en el que los comerciantes no podían interactuar con ningún elemento de página de la página Devuelve después de crear una etiqueta de envío para una autorización de devolución de mercancías (RMA).

## Versión 1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Commerce 2.3.0 - 2.3.4*): Corrige el problema con [!DNL PayPal Payflow Pro] método de pago y tratamiento de cookies como `SameSite=Lax` de forma predeterminada, en el explorador Chrome 80 y el redireccionamiento de la respuesta de API a la página de inicio de sesión del cliente.
* **MDVA-26694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*): Corrige el problema con las cachés de productos y catálogos que caducan a diario, aunque se ha programado que caduquen de forma diferente.
* **MDVA-27825** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): Corrige el problema en el que la exportación de grandes cantidades de datos fallaba debido a una fuga de memoria.
* **MDVA-29085** (*para Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*): Corrige el problema B2B en el que no se envían correos electrónicos de empresa nuevos necesarios si API crea una empresa.
* **MDVA-29344** (*para Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*): corrige el problema en el que el Creador de páginas se atasca después de copiar texto de un elemento de encabezado a un elemento de texto.
* **MDVA-29835** (*para Adobe Commerce >2.3.1 &lt;2.4.2*): corrige el problema en el que los pedidos de tarjetas de regalo contenían dos códigos en lugar de uno.
* **MDVA-30052** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): Corrige el problema con el contenido privado (almacenamiento local) que no se rellena correctamente, lo que daba como resultado problemas de rendimiento.
* **MDVA-30131** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): Corrige el problema de la navegación en capas, en la que la función *No* el valor de los atributos de producto de tipo booleano no se incluyó en la navegación en capas si [!DNL Elasticsearch] se usaba como motor de búsqueda.
* **MDVA-35514** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*) : corrige el problema con la creación de una etiqueta de envío y la adición de productos pedidos a un paquete en la ventana modal Crear paquetes .
