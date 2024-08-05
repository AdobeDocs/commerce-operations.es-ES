---
title: Notas de la versión
description: Conozca los parches disponibles para Adobe Systems Commerce y los problemas que resuelven.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: 7c294a9450be46049090c78074d4fbe722a75119
workflow-type: tm+mt
source-wordcount: '20855'
ht-degree: 0%

---

# Notas de la versión

Ofrece [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) parches individuales desarrollados por Adobe Systems y el Magento Open Source comunidad. Permite aplicar, revertir y ver información general sobre todos los parches individuales disponibles para la versión instalada de Adobe Commerce. Puede aplicar parches a proyectos de Adobe Commerce y de Magento Open Source independientemente de quién lo haya desarrollado. Por ejemplo, puede aplicar un parche desarrollado por la comunidad a proyectos de Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar parches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obtener instrucciones sobre cómo aplicar parches a sus proyectos de Adobe Commerce. Consulte [[!DNL Quality Patches Tool]: busque parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la Guía de actualización de software para revisar una lista completa de parches publicados.

>[!INFO]
>
>Para obtener información acerca de [!DNL quality patches] creado por la comunidad para Magento Open Source, consulte las [notas de la versión](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que las imágenes de producto se eliminan después de eliminar una actualización de ensayo.
* **ACSD-57086** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual los pedidos realizados desde sitios web no predeterminados con los términos y condiciones habilitados no se procesan correctamente.
* **ACSD-57588** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el cual el envío de un pedido a varias direcciones déclencheur un error durante el procesamiento del ID de región.
* **ACSD-57643** (para comercio Adobe Systems y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where products with custom options are incorrectly added to the shopping cart via GraphQL.
* **ACSD-57846** (para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where GraphQL products search with a filter for zero prices does not return any results due to an exception.
* **ACSD-57941** (para comercio Adobe Systems y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where product options are incorrectly assigned to the admin store instead of their respective stores.
* **ACSD-58375** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual la configuración incorrecta de *[!DNL YouTube API Key]* provoca un error al agregar un vídeo de [!DNL YouTube] en el nivel de vista de tienda.
* **ACSD-58739** (para Adobe Commerce y Magento Open Source >=2.4.7 &lt;2.4.8): corrige el problema en el cual la reindexación parcial genera un error.
* **ACSD-58446** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el cual cuando se elimina un equipo con usuarios o equipos secundarios independientemente de su estado (inactivo), el sistema proporciona un mensaje de error no informativo coherente con la interfaz de usuario.
* **ACSD-58054** (para Adobe Commerce >=2.4.4 &lt;2.4.6): corrige el problema en el cual es posible generar tokens de cliente para clientes inactivos a través de la API.
* **ACSD-58163** (para Adobe Commerce >=2.4.3 &lt;2.4.7): corrige el problema en el cual *[!UICONTROL Cart Price Rule]* no aplica un descuento a un cliente invitado del carro de compras *[!UICONTROL Customer Segment]* coincidente sin un código de cupón.
* **ACSD-57045** (para Adobe Systems Comercio >=2.4.5 &lt;2.4.7) - Fixes the issue where URL rewrites cause infinite page looping after *[!UICONTROL Website Root]* no está activado en *[!UICONTROL Hierarchy]*.
* Parches actualizados: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que la mutación `mergeCart` falla con un &quot;*Error interno del servidor*&quot; en la respuesta [!DNL GraphQL] al combinar carros de origen y de destino que tienen los mismos elementos de paquete.
* **ACSD-56546** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el cual los productos configurables y agrupados se muestran como **Sin existencias** en la tienda cuando **se muestra sin configuración del producto** está *Deshabilitado*.
* **ACSD-56635** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que el cliente importado se duplica con la misma dirección de correo electrónico, cuando se usa una importación con **uso compartido de cuentas** establecida en *Global*.
* **ACSD-56741** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el mensaje de error &quot;*Intentando obtener acceso al desplazamiento de la matriz en el valor de tipo null*&quot; que se muestra durante `setup:upgrade` cuando la base de datos contiene un déclencheur [!DNL MySQL] personalizado no relacionado con el mecanismo de indexación y [!DNL MView].
* **ACSD-57315** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema que se produce cuando se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón [!UICONTROL Fetch] en la pantalla **[!UICONTROL View transaction]** del Administrador.
* **ACSD-57337** (para Adobe Systems > de comercio = cuadrícula 2.4.4 &lt;2.4.6) - Fixes the issue where an admin user with access restrictions to specific websites is able to see companies from all the websites in the **[!UICONTROL Companies]** .
* **ACSD-57394** (para Comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.7) - Fixes the issue of incorrect product sorting by multiple sort fields in [!DNL GraphQL].
* **ACSD-57565** (para Adobe Systems comercio y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the **[!UICONTROL Order]** panel muestra información de pedido incorrecta hasta que se actualiza el período de tiempo. Ahora, la panel muestra las estadísticas de orden correctas en la primera carga.
* **ACSD-57854** (para solicitudes de comercio Adobe Systems y Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue when product [!DNL GraphQL] devolvieron categorías deshabilitadas en las agregaciones categoría.
* **ACSD-58008** (para Adobe Systems Comercio >=2.4.5 &lt;2.4.7) - Fixes the issue where updating a scheduled update removed the previous version of a staged item, if no end date was specified.
* Parches actualizados: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (para Adobe Systems Commerce y Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where *[!UICONTROL Used]* y *[!UICONTROL Times Used]* los atributos muestran valores incorrectos para los cupones generados cuando se utilizan durante el cierre de compra con varias direcciones.
* **ACSD-56760** (para Adobe Systems Comercio >=2.4.6 &lt;2.4.7) - Fixes the issue where an admin user restricted to a specific website cannot sort or add new products inside a category in case the webstore has its own root category.
* **ACSD-56858** (para Adobe Systems Comercio >=2.4.2 &lt;2.4.7) - Fixes the issue where B2B company role permissions are displayed incorrectly for a restricted company admin.
* **ACSD-57074** (para comercio Adobe Systems y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the *Sí/No* el atributo personalizado con `attrbute_code` Comenzar con `price_` no funciona correctamente con la indexación, y los productos con tales atributos no están disponibles en el front-end.
* Revisiones actualizadas: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (para comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the category page caches invalidate when the stock quantity changes, even if the product is still in stock.
* **ACSD-54656** (para Adobe Systems Comercio >=2.4.5 &lt;2.4.6) - Fixes the issue where the invisible Recaptcha fails during checkout, preventing an order from being placed.
* **ACSD-55100** (para Adobe Systems Comercio >=2.4.6 &lt;2.4.7) - Fixes the issue where GraphQL does not return more than 10k products in the search results.
* **ACSD-56621** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el cual el nombre y los apellidos actualizados no se reflejan en la sección del encabezado de saludos del usuario administrador de la compañía.
* **ACSD-56842** (para Adobe Systems Comercio y Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the deferred proxies and the deferred proxy factories are missing after running `setup:di:compile`.
* **ACSD-57003** (para comercio Adobe Systems y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where the order status is changed to *[!UICONTROL Complete]* en lugar de cambiarse a *[!UICONTROL Processing]* cuando un pedido se reembolsa parcialmente y se envía parcialmente.
* Parches actualizados: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where a configurable product becomes out of stock when one of two child products is disabled by a scheduled update.
* **ACSD-56616** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el cual los productos agrupados se muestran como disponibles en la tienda cuando sus productos simples están agotados.
* **ACSD-56515** (para Adobe Systems Comercio >=2.4.2 &lt;2.4.7) - Fixes the issue where admin with website level permissions cannot add or edit a dynamic block.
* **ACSD-56447** (para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where adding the same product to the cart via parallel REST web API requests results in two separate items in the cart.
* **ACSD-56415** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the performance of the partial price indexing is slowed down due to a `DELETE` query when the database has a lot of partial price data to index.
* **ACSD-54965** (for Adobe Commerce >=2.4.5 &lt;2.4.6) - Fixes the issue where the Visual Merchandising grid does not display the correct stock when a product is assigned to custom stock only.
* **ACSD-52824** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que se muestran los botones PayPal Express, Google Pay y Apple Pay para los clientes de la empresa cuando estos métodos de pago están deshabilitados en la configuración de la empresa.
* Revisiones actualizadas: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el cual se redirige a un usuario al Panel de administración al ordenar productos de categoría mediante la opción **Mover de stock a la parte inferior** y aparece el error `Invalid security or form key. Please refresh the page` en la parte superior de la pantalla.
* **ACSD-56280** (para Adobe Commerce >=2.4.4 &lt;2.4.7): corrige el problema en el que ordenar elementos de un registro de regalos genera una excepción.
* **ACSD-56246** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el cual se eliminan los datos del atributo de selección múltiple personalizado cuando se activa una actualización programada para un producto.
* **ACSD-56193** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4): corrige el problema en el que la caché de Varnish/Fastly no se actualiza cuando se utiliza un bloque programado en la descripción de categoría mediante Page Builder.
* **ACSD-56158** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que la consulta &quot;carrito&quot; devuelve el valor de impuestos total para cada regla de impuestos.
* **ACSD-56023** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual el contenido del widget no se actualiza en la página de CMS cuando la caché está habilitada.
* **ACSD-55427** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual el usuario administrador no puede anular la asignación de un producto de un catálogo compartido desde la página de productos en el Administrador.
* **ACSD-55352** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual, después de crear una nota de crédito parcial con puntos de recompensa del cliente, el estado de la orden cambia a Cerrado y las opciones de nota de crédito desaparecen de la página de orden de administración.
* **ACSD-55231** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el cual no se pueden agregar productos al carro de compras mediante la funcionalidad de pedidos rápidos.
* **ACSD-54283** (para Adobe Commerce >=2.4.3 &lt;2.4.4): corrige el problema en el cual los productos/categorías no asignados al catálogo compartido para el predeterminado (grupo general) siguen incluidos en el mapa del sitio XML.
* Revisiones actualizadas: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual la URL de categoría canónica no se actualiza después de cambiar la URL de categoría.
* **ACSD-53636** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5): corrige el problema en el cual el precio normal no se muestra en las páginas de lista de productos para productos configurables que tienen productos secundarios con precios especiales.
* **ACSD-54885** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema con la desprotección de varias direcciones cuando el usuario administrador usa la funcionalidad *Iniciar sesión como cliente*.
* **ACSD-55610** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que un pedido parcialmente cancelado tiene un importe de descuento incorrecto.
* **ACSD-55334** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige las traducciones de etiquetas a través de los diccionarios de traducción en la respuesta de GraphQL.
* **ACSD-54739** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que la condición de estado de existencias del producto no se aplica a reglas de producto relacionadas.
* **ACSD-53925** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual el administrador no puede guardar el bloque CMS con el carrusel de productos cuando el modo de dimensiones `catalog_product_price` está establecido en *sitio web*.
* **ACSD-52714** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual el filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha se establece como *Y-m-d*.
* **ACSD-55055** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): mejora el rendimiento al cargar atributos de producto en reglas de precios del carro de compras.
* **ACSD-53790** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el cual se pueden crear varias RMA para un solo producto a través de la API de REST.
* **ACSD-56090** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5): corrige el problema en el que la solicitud de GraphQL responde con los datos de todos los almacenes en lugar de con los datos de almacén solicitados específicamente.
* **ACSD-54983** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el cual obtener el usuario de la compañía UID con la solicitud de GraphQL no es posible cuando el estado del usuario se establece en *[!UICONTROL Inactive]*.
* **ACSD-53309** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual el impuesto no se aplica completamente en la etiqueta *[!UICONTROL Regular Price]* cuando se selecciona la opción personalizable.
* **ACSD-55305** (para Adobe Commerce >=2.4.4 &lt;2.4.7): corrige el problema por el que la ventana emergente *[!UICONTROL Edit Company User]* de la página **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** se bloquea con un cargador en la pantalla.
* Revisiones actualizadas: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el cual los datos del producto *[!UICONTROL Recently Viewed]* no se actualizan correctamente en la vista de tienda.
* **ACSD-54626** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el cual no se puede crear una nueva regla de pedido de compra (`createPurchaseOrderApprovalRule`) con el atributo `NUMBER_OF_SKUS` a través de [!DNL GraphQL].
* **ACSD-53845** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema de tiempo de espera de conexión de [!DNL MySQL] cuando `consumer max_messages` = 0.
* **ACSD-54890** (para Adobe Commerce y el Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que `aggregate_sales_report_bestsellers_data` causa [!DNL MySQL] errores debido a que el disco `/tmp` está sin espacio.
* **ACSD-55112** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el cual se puede hacer clic en el botón *[!UICONTROL Submit review]* varias veces sin validación de [!DNL Google reCAPTCHA v3].
* **ACSD-54264** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7): corrige el problema en el que el mensaje de error *&quot;No se puede actualizar el atributo solicitado. Id. de fila: store_id&quot;* aparece cuando un cliente intenta cerrar la compra con una oferta negociable de otra vista de tienda.
* **ACSD-54418** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el cual una cantidad fija de descuento se aplica incorrectamente a cada producto secundario del paquete de precios dinámicos.
* **ACSD-55238** (para Adobe Commerce y el Magento Open Source >=2.4.4 &lt;2.4.7): correcciones que guardan el producto vacío *[!UICONTROL Meta Description]*.
* **ACSD-54966** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el cual un código de cupón con un uso limitado por cliente no se puede reutilizar si falla el pedido anterior.
* **ACSD-54060** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual un administrador restringido no puede guardar un producto si es hijo de otro producto asignado a un ámbito diferente.
* **ACSD-48910** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): se ha corregido el problema por el que un producto agrupado asignado a varios orígenes se queda sin existencias después de que se factura y envía un pedido, incluso si aún tiene una cantidad distinta de cero.
* **ACSD-55381** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige un error interno del servidor al consultar los campos `configurable_product_option_uid` y `configurable_product_option_value_uid` desde un [!DNL B2B] *[!UICONTROL Requisition list]* a través de [!DNL GraphQL].
* **ACSD-55628** (para Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6): corrige la carga de un archivo en el formulario de registro de empresa y reemplaza un archivo para un atributo de cliente en la tienda.
* Revisiones actualizadas: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema que se produce en el carro de compras cuando un producto se elimina del catálogo compartido después de que ya se haya agregado al carro de compras.
* **ACSD-53722** (para Adobe Commerce >=2.4.4 &lt;2.4.7): corrige el problema en el que el precio de las opciones de productos agrupadas cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos.
* **ACSD-53643** (para Adobe Commerce >=2.4.3 &lt;2.4.7): corrige el problema en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos deshabilitados o sin existencias. Se corrigió ocultando el botón *[!UICONTROL Place Order]* para dichos pedidos de compra.
* **ACSD-54067** (para comercio Adobe Systems y Magento Open Source >=2,4,0 &lt;2.4.7) - Fixes the issue where a product video doesn&#39;t play on a mobile device.
* **ACSD-55414** (para comercio Adobe Systems y Magento Open Source >=2,4,0 &lt;2.4.6) - Improves performance when the MariaDB tries to cast the EAV entity_id from string to integer.
* **ACSD-51819** (para Adobe Systems Comercio >=2.4.4 &lt;2.4.4-p4) - Fixes the issue where multiple orders can be placed with the same quote ID.
* **ACSD-53118** (para Adobe Systems Commerce >=2.4.0 &lt;2.4.7) - Fixes the issue where the *[!UICONTROL Cart Price Rule]* se aplica mediante código cupón mientras el producto tiene un atributo vacío.
* **ACSD-54324** (para Adobe Systems Comercio >=2.4.5 &lt;2.4.7) - Fixes the issue where the GraphQL requisition_lists request does not consider pagination settings and returns all results.
* Revisiones actualizadas: MDVA-42855-v2

## Versión 1.1.40 {#v1-1-40}

* **ACSD-54680** (para Adobe Commerce >=2.4.0 &lt;2.4.6): corrige el problema en el cual no es posible procesar una cotización B2B enviada para un producto con varios orígenes asignados.
* **ACSD-54040** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6): corrige el problema en el que el campo *[!UICONTROL Created]* está en blanco para obtener detalles del pedido cuando los módulos B2B están habilitados.
* **ACSD-54319** (para Adobe Systems informe Comercio y Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where the product price shows zero in the *[!UICONTROL Product in Cart]* .
* **ACSD-53378** (para comercio Adobe Systems y Magento Open Source >=2,4,5 &lt;2.4.7) - Improves checkout page load time for customers who have large address books.
* **ACSD-52657** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el cual la minicart no se actualiza en la vista de tienda secundaria, que usa un subdominio.
* **ACSD-53414** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el cual un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos.
* **ACSD-54472** (para Adobe Systems Comercio >=2.4.6 &lt;2.4.7) - Fixes the issue where customers of a rejected company can still authenticate, and customers of a blocked and a rejected company can still place orders. El parche agrega validación adicionales para los puntos finales de GraphQL.
* **ACSD-52801** (para comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.7) - Adds the option to do a partial match when searching for products in GraphQL.
* **ACSD-55004** (para Adobe Systems comercio y Magento Open Source >=2,4,6 &lt;2.4.7) - Fixes the issue where the validator crashes while uploading an import file larger than the value configured in `php.ini`.
* **ACSD-54989** (para Adobe Systems Comercio >=2.4.4-p5 &lt;2.4.5 ||=&quot;&quot;>=2.4.5-p4 &lt;2.4.6 ||=&quot;&quot;>=2.4.6-p2 &lt;2.4.7) - Fixes the issue where a company admin cannot place an order when *[!UICONTROL Enable Purchase Orders]* está configurado y *[!UICONTROL Yes]* *[!UICONTROL Purchase Order]* está establecido en *[!UICONTROL No]*.&lt;/2.4.6>&lt;/2.4.5>
* **ACSD-54007** (para Adobe Systems comercio y Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes the error *&quot;Clave de matriz indefinida &quot;_ámbito&quot;&quot;* al importar datos de clientes.
* **ACSD-55031** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el error *Type &quot;mixed&quot; no puede admitir valores NULL* durante la compilación.
* **ACSD-54961** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el cual un usuario administrador restringido no puede actualizar de forma masiva el estado de *Revisión del producto*.
* **ACSD-55256** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que solo se muestra correctamente la primera imagen en el regulador de imagen.
* Revisiones actualizadas: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (para Adobe Commerce >=2.4.0 &lt;2.4.7): corrige el problema en el cual el historial de saldo de puntos de recompensa se calcula de forma incorrecta después de que caduquen los puntos de recompensa.
* **ACSD-53583** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): mejora el rendimiento de reindexación parcial para los indexadores *Category Products* y *Product Categories*.
* **ACSD-54026** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige un mensaje de error incorrecto para una solicitud de GraphQL de `updateCompanyRole` para un usuario no autorizado.
* **ACSD-54106** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5): corrige el problema en el cual la ordenación de productos de categoría por nombre para caracteres acentuados turcos es incorrecta.
* **ACSD-52219** (para comercio Adobe Systems y Magento Open Source >=2,4,5 &lt;2.4.7) - Fixes the issue where Admin grids saved filters don&#39;t work as expected when frequently switching between bookmark views.
* **ACSD-54342** (para Adobe Systems Commerce y Magento Open Source >=2.4.0 &lt;2.4.7) - Fixes an incorrect error message *Error en la estructura de datos: los valores se mezclan* cuando se importa un archivo CSV sin datos válidos.
* **ACSD-54660** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): se ha agregado un nuevo atributo de entrada *sort* para ordenar los pedidos de los clientes en GraphQL por `sort_field` y `sort_direction`.
* **ACSD-54776** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual los valores de campo de producto *[!UICONTROL Use Default Value]* sin marcar y los valores de campo de producto no predeterminados no se guardan para el segundo sitio web, tienda y vista de tienda.
* **ACSD-53998** (para Adobe Commerce y Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7): corrige el problema en el que un **[!UICONTROL Dynamic Block]** basado en un **[!UICONTROL Customer Segment]** no funciona correctamente después de cerrar sesión desde una cuenta de cliente.
* **ACSD-53204** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): correcciones *El producto no se puede guardar.Error* al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el extremo `rest/V1/products/<sku>/media`.
* **ACSD-47657** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): se ha agregado un mecanismo de almacenamiento en caché para las credenciales de AWS. Un proveedor de credenciales ahora utiliza la caché de Magento para almacenar en caché las credenciales recuperadas de AWS para la configuración de EC2.
* Parches actualizados: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (para comercio Adobe Systems y Magento Open Source >=2.4.3 &lt;2.4.4) - Fixes the issue where products assigned to a shared catalog do not appear on the storefront when a partial index is executed.
* **ACSD-54018** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige los problemas de rendimiento con el widget [!UICONTROL Product List] que usa un atributo no global en la condición del widget.
* **ACSD-54111** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el cual las imágenes de miniaturas del producto no se muestran en la tienda cuando la proporción de aspecto de la imagen de marca de agua no coincide con la imagen del producto.
* **ACSD-47669** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6) - Corrige *Infracción de restricción de integridad: 1452 No se puede agregar ni actualizar una fila secundaria: falla una restricción de clave externa* error al importar productos CSV.
* **ACSD-53347** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el indizador de precios tarda demasiado en ejecutarse.
* **ACSD-52287** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema con el estado de orden incorrecto en la cuadrícula de orden archivada cuando la indexación de cuadrícula asincrónica está habilitada.
* **ACSD-52929** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema con las solicitudes redundantes para reindexar los elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico.
* **ACSD-53824** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el cual el parche de datos de migración de `UpdateMultiselectAttributesBackendTypes` supera el límite de tamaño de transacción de base de datos durante `setup:upgrade`.

## Versión 1.1.37 {#v1-1-37}

* **ACSD-52613** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el cual las cachés y los índices se actualizan incluso cuando la API de REST no realiza actualizaciones de `Inventory_source` elementos.
* **ACSD-51884** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual la ruta de acceso a la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando resize.
* **ACSD-53628** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual el informe de pedidos de ventas CSV muestra caracteres especiales incorrectos.
* **ACSD-53148** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el cual dos solicitudes paralelas en GraphQL para agregar el mismo producto configurable al carro de compras generaban dos elementos independientes en el carro de compras con el mismo SKU del producto.
* **ACSD-52606** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el que se muestra el mensaje de error *Su pedido no está listo para recogerse* cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual la imagen no se actualiza en el front-end después de reemplazarla con otra imagen con el mismo nombre.
* **ACSD-53728** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el indizador EAV del producto tarda más en completarse.
* **ACSD-53979** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema de JS que se produce en la página de inicio si el mensaje de bienvenida contiene una comilla simple.
* **ACSD-52085** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el cual un producto configurable con un precio especial no es visible en el carrusel del producto.
* **ACSD-53795** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema con el tipo de datos no válido en el trabajo cron de `indexer_update_all_views`.
* **ACSD-52143** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que las opciones personalizadas se eliminan después de importar el producto.
* **ACSD-53750** (para Adobe Commerce y el Magento Open Source >=2.4.4 &lt;2.4.7): corrige el error *Conexión rota o conexión cerrada* durante el reíndice de `catalog_product_price` de subprocesos múltiples.
* **ACSD-49843** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7): corrige el problema en el cual el vínculo de descarga del producto no está disponible después de que el elemento pedido se haya facturado automáticamente mediante el método de pago en línea con la configuración **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** habilitada.
* **ACSD-47054** (para Adobe Commerce >=2.4.2 &lt;2.4.6): corrige el problema por el que el reíndice de vista previa ejecuta el reíndice para todas las tiendas, lo que provoca lentitud.
* Se han añadido nuevas versiones para ACSD-46541, ACSD-47079.
* ACSD-49970-v3 reemplazado por ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (para comercio Adobe Systems y Magento Open Source >=2.4.3 &lt; 2.4.6) - Fixes the issue where the inventory indexer cleans all caches in the Update on Schedule mode.
* **ACSD-50887** (para Adobe Systems comercio y Magento Open Source >=2.4.0 *[!UICONTROL Use in Search Results Layered Navigation]* &lt;2.4.7) - Fixes the issue where the product attribute property puede establecerse en *Sí* sin la *[!UICONTROL Use in search]* opción establecida en *Sí*.
* **ACSD-51846** (para Adobe Commerce y Magento Open Source >=2.4.3-p2 &lt;2.4.6): corrige el problema de *error interno* que se produce porque no se validan todos los niveles de carga útil de la API REST.
* **ACSD-52906** (para Adobe Systems Comercio >=2.3.7 &lt;2.4.7) - Fixes the issue where the X-Magento-Vary cookie is set incorrectly for logged-in customers that belong to the same customer segment causing improper caching for some pages.
* **ACSD-52736** (para comercio Adobe Systems y Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where a *La regla* de precio del carro de compras que incluye los requisitos para la cantidad de producto configurable no funciona como se espera.
* **ACSD-47875** (for Adobe Commerce and Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where admin users are not able to add a product to a customer cart from the Admin for a particular store view scope with inventory management.
* **ACSD-53176** (para Adobe Commerce >=2.3.7 &lt;2.4.5): corrige el problema donde *Regla de producto relacionada* con *es una de* condición que no coincide con productos.
* **ACSD-51666** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el error *La sesión ha caducado, vuelva a iniciar sesión.* que sucede después de que un cliente intente iniciar sesión.
* Se han añadido nuevas versiones para MDVA-39305-v2.
* Requisitos actualizados para ACSD-19640.

## Versión 1.1.35 {#v1-1-35}

* **ACSD-51899** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que la dirección de envío predeterminada en el paso de envío de cierre de compra se rellena automáticamente con una dirección de recogida en tienda seleccionada anteriormente.
* **ACSD-52041** (para Adobe Commerce y el Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema por el que el mensaje de error: *[ERROR] [!DNL Page Builder] se representaba durante 5 segundos sin liberar bloqueos.* aparece en el explorador Chrome al guardar el contenido editado con [!DNL Page Builder].
* **ACSD-52095** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema por el cual el valor `manage_stock` se establecía incorrectamente en 0 en el archivo CSV después de exportar el producto.
* **ACSD-51358** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual al eliminar una actualización programada sin una fecha de finalización se eliminan otras actualizaciones programadas para la misma entidad.
* **ACSD-48070** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el cual editar una actualización programada déclencheur una excepción.
* **ACSD-51890** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el cual se puede hacer clic en el botón [!UICONTROL Submit review] varias veces sin la validación de [!DNL Google reCAPTCHA] v3.
* **ACSD-51984** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual los valores *[!UICONTROL Use Default Value]* y *[!UICONTROL non-default product field]* sin marcar no se guardan para el segundo sitio web, tienda y vista de tienda.
* **ACSD-52398** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el error *La cantidad solicitada no está disponible* que se produce al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda.
* **ACSD-52786** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el cual una condición de regla de catálogo *SKU es* se aplica a todos los productos que comienzan con la SKU dada.
* **ACSD-52921** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el cual se produce un error interno si se solicitan detalles del carro de compras a GraphQL cuando hay un producto configurable sin existencias en el carro de compras.
* **ACSD-51683** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el cual no se puede agregar una opción personalizable al carro de compras mediante GraphQL.
* **ACSD-52133** (for Adobe Commerce and Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where a customer account cannot be saved after an upgrade.
* **ACSD-52202** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que la cantidad vendible de existencias predeterminadas cambia incorrectamente a 0 cuando se cambia una existencias no predeterminada a 0 cant. en el cumplimiento del pedido.
* **ACSD-51265** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema con el rendimiento de reindexación de `catalog_product_price` cuando hay demasiados productos agrupados en el sistema.
* **ACSD-52831** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el cual los clientes no pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está habilitado.
* **ACSD-51845** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el cual los productos subsiguientes con precios de nivel y diferentes conjuntos de atributos no se pueden actualizar a través de la API de REST masiva asincrónica.
* **ACSD-52815** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que la entrada para el campo de cantidad de un origen no predeterminado solo admite hasta 6 dígitos, a diferencia de 8 para un stock predeterminado.
* **ACSD-51149** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que Importación programadaExportar con permisos de catálogo habilitados invalida los indexadores y luego los vaciados de caché por parte de cron.
* **ACSD-50815** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el cual la cantidad decimal de un producto simple no se puede usar para una nueva opción de producto agrupado.
* Versiones actualizadas para ACSD-47803.
* Título actualizado para ACSD-51892.
* ACSD-51379 actualizado.
* Se ha actualizado ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el cual un usuario administrador no es redirigido correctamente después de seleccionar una vista de tienda al crear un nuevo pedido en Administración.
* **ACSD-50813** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual el administrador no podía agregar al pedido del administrador productos agrupados que contenían una barra diagonal en el SKU con la funcionalidad [!UICONTROL Add Products by SKU].
* **ACSD-51630** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que una gran cantidad de mensajes del sistema ralentiza la descarga de páginas de administración.
* **ACSD-51853** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.7): corrige el problema en el cual los estilos de texto copiados no se aplican al usar [!UICONTROL Page Builder].
* **ACSD-52160** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que el resultado de validación del producto frente a la regla de precio del carro de compras no se evaluó correctamente según la condición de regla &quot;Si se ENCUENTRA/NO SE ENCUENTRA un artículo en el carro de compras con Todas/Cualquiera de estas condiciones como True&quot;.
* **ACSD-51636** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual el administrador de la compañía no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.
* **ACSD-51739** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que se devuelve un error cuando se solicita `structure_id` en una solicitud de CompanyTeam GraphQL.
* **ACSD-51857** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que el rendimiento lento del informe cron de `aggregate_sales_report_bestsellers_data` en tablas de base de datos sales_order y `sales_order_item` grandes se debía a la forma en que se escribió la consulta de datos principal.
* **ACSD-48448** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que se produce un problema de condición de carrera durante las cancelaciones de pedidos, lo que provoca una entrada duplicada en la tabla `inventory_reservation`.
* **ACSD-52689** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.6): corrige el problema en el cual las imágenes no se pueden cargar al almacenamiento de Amazon S3 mediante la API REST.
* **B2B-2674** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): agregue capacidad de almacenamiento en caché a la consulta de GraphQL 1customAttributeMetadata1.
* Se han añadido nuevas versiones para ACSD-44938.
* Se han añadido requisitos para ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5): corrige el comando de reversión de la base de datos para un caso en el que el volcado de la base de datos contiene déclencheur y un comando SQL *delimitador*.
* **ACSD-50512** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el *error: el vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo.* error que se produce al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.
* **ACSD-50949** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el cual el filtro de precios en la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU.
* **ACSD-51645** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el error producido al guardar una nueva regla de precio del carro de compras si la extensión `Magento_OfflineShipping` está deshabilitada.
* **ACSD-50895** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el cual no se activan las etiquetas [!DNL Google Analytics] 3 GTM si no se configura [!DNL Google Analytics] 4 GTM.
* **ACSD-51102** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el cual una regla de catálogo que se aplica a un gran número de productos no se indiza correctamente cuando una actualización programada habilita la regla.
* **ACSD-50368** (para comercio Adobe Systems y Magento Open Source >= 2.4.3 &lt;2.4.5) - Fixes the issue where the customer&#39;s `group_id` se omite cuando se crea un cliente mediante API de REST asíncrona o API de REST masiva asíncrona.
* **ACSD-51497** (para comercio Adobe Systems y Magento Open Source >=2,3,7 &lt;2.4.0 ||=&quot;&quot;>= 2,4,1 &lt;2.4.7) - Fixes the issue where a customer can&#39;t sort a catalog page by Custom Attribute of the dropdown type.&lt;/2.4.0>
* **ACSD-51408** (para Adobe Systems Comercio y Magento Open Source >=2,3,7 &lt; 2.4.7) - Fixes the issue where the order item status is incorrectly set to *[!UICONTROL Backordered]*.
* **ACSD-51735** (para Adobe Systems comercio y Magento Open Source >=2,4,4 *[!UICONTROL Ordered]* &lt;2.4.5) - Fixes the issue where the order item status is incorrectly set to cuando el stock de productos es *0*.
* **ACSD-51792** (para Adobe Systems comercio y Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where a page does not have the impression event when [!DNL Google Tag Manager] 4 está habilitado.
* **ACSD-51471** (para Adobe Systems Comercio >=2.4.3 &lt;2.4.7) - Fixes the issue where an admin user cannot save a scheduled update for a bundled product that uses a simple product that itself has a scheduled update.
* **ACSD-51700** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el error que se produce al cambiar de vista de tienda en una página de edición de producto descargable en el administrador.
* **ACSD-51120** (para Adobe Commerce >=2.3.7 &lt;2.4.3): corrige el problema en el cual la caché de solicitudes de GET de GraphQL no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo.
* **ACSD-51240** (para Adobe Commerce >=2.4.4 &lt;2.4.6): corrige el problema en el que falta el archivo cargado si el registro se realiza mediante el formulario de registro de la empresa.
* **ACSD-51907** (para Adobe Systems Comercio >=2.4.2 &lt;2.4.3) - Fixes the issue where a restricted admin user cannot create a credit memo with an offline refund.
* **ACSD-52148** (para Adobe Systems Commerce y Magento Open Source >=2.4.0 &lt;2.4.4) - Fixes the issue where the [!DNL Google V3 reCAPTCHA] inicio de sesión de administración falla ocasionalmente.
* **ACSD-51431** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que un estado de indizador es *funcionando* aunque no haya nuevas entradas en el registro de cambios.
* **ACSD-51892** (para comercio Adobe Systems y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the performance issue where config files load multiple times.
* ACSD-51114 obsoleto.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (para Adobe Systems de comercio y Magento Open Source >=2.4.2 &lt;2.4.7) - Fixes the issue where the [!UICONTROL Page Builder's] varios errores impiden que el administrador guarde un producto sin permisos contenido.
* **ACSD-51305** (para comercio Adobe Systems y Magento Open Source >=2.4.6 &lt;2.4.7) - Fixes the issue where out-of-stock configurable child products are not available in the GraphQL response.
* **ACSD-50621** (para Adobe Systems Commerce >=2.3.7 &lt;2.4.7) - Fixes the issue where [!UICONTROL Tier Prices] para diferentes sitios web en el catálogo compartido no son visibles cuando se trata de editarlos en un entorno de varios sitios web.
* **ACSD-51041** (para comercio Adobe Systems y Magento Open Source >=2.3.7 &lt;2.4.0 ||=&quot;&quot;>=2.4.1 &lt;2.4.6) - Improves performance of price indexer.&lt;/2.4.0>
* **ACSD-51379** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual los cambios realizados en el contenido de texto de la página a través de [!UICONTROL Page Builder] no se guardan.
* **ACSD-49480** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el cual solo se aplica una regla de precio de carro de compras al carro de compras.
* **ACSD-51230** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que se elimina la cuenta de tarjeta de regalo cuando se procesa un reembolso parcial de un producto simple de un pedido.
* **ACSD-51238** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que se elimina el origen de inventario al actualizar productos configurables y editar el precio.
* **ACSD-50794** (para Adobe Commerce >=2.4.1 &lt;2.4.7): corrige el problema en el cual los detalles del mensaje o el envoltorio de regalos no se actualizan en la base de datos al eliminarlos a través de GraphQL.
* **ACSD-51528** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que la columna *x_forwarded_for* tiene valores nulos en la tabla *sales_order*.
* **ACSD-50849** (para Adobe Commerce >=2.4.4 &lt;2.4.6): corrige el problema en el cual agregar un nuevo producto a la categoría después de borrar la caché resulta en una discrepancia de posiciones y selecciones de los productos existentes.
* **ACSD-51294** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema por el que el precio, la cantidad, los impuestos, el envío y los ingresos de GTM/GA se envían como una cadena a [!DNL Google Analytics] y GTM.
* **ACSD-51204** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual un producto totalmente vendido no vuelve a estar disponible después de crear un abono.
* **ACSD-51291** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3): corrige el problema en el que los administradores restringidos con acceso a un sitio web pueden agregar imágenes/vídeos al producto asignado a varios sitios web.
* Added new versions for ACSD-50336.
* Replaced patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Fixes the issue where Recaptcha v2 does not reload after submitting a failed payment.
* **ACSD-50817** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): optimiza el trabajo de Cron `sales_clean_quotes` para que se ejecute más rápido.
* **ACSD-49392** (para comercio Adobe Systems y Magento Open Source >=2.3.7 &lt;2.4.0 ||=&quot;&quot;>= 2.4.1 &lt;2.4.7) - Fixes the issue where the order status changes to closed after a partial refund for a bundled product.&lt;/2.4.0>
* **ACSD-51036** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.5) - Fixes the issue where race conditions during concurrent REST API calls result in an overwrite of shipping status information in the [!UICONTROL Items Ordered] table.
* **ACSD-50858** (for Adobe Commerce and Magento Open Source >=2.4.4 &lt;2.4.7) - Improves performance for loading banners contents.
* Added new versions for MDVA-39305-v2, ACSD-45169.
* Updated patches ACSD-50260-v2.

## Versión 1.1.30 {#v1-1-30}

* **ACSD-50336** (para Adobe Commerce y Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3): corrige el problema por el que los correos electrónicos de alerta de productos no se envían cuando un producto vuelve a estar disponible o se cambia el precio.
* **ACSD-50367** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual la exportación de direcciones de clientes no funciona cuando se crea un atributo de direcciones de clientes de selección múltiple sin valores.
* **ACSD-49877** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual la reproducción automática de vídeo no funciona en el móvil [!DNL Safari] cuando el vídeo está vinculado directamente a un archivo de vídeo remoto y no a un servicio de streaming.
* **ACSD-50165** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el error *El archivo no se puede eliminar. Advertencia: no existe el archivo o directorio* al vaciar la caché JS/CSS del administrador.
* **ACSD-49737** (para Adobe Commerce y Magento Open Source >=2.4.1-p1 &lt;2.4.7): corrige el problema en el cual un cupón se marca incorrectamente como usado después de un pago con tarjeta fallido.
* **ACSD-50814** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el cual un usuario administrador no puede crear un abono.
* **ACSD-50116** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual un usuario administrador no puede crear una reescritura de URL para subcategorías de nivel 3 o inferior.
* **ACSD-49513** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5): corrige el problema en el que la sincronización del almacenamiento remoto falla debido a archivos de 0 bytes.
* **ACSD-46683** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el precio de envío muestra *Aún no se ha calculado*.
* **ACSD-49129** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que el atributo *[!UICONTROL content]* (código de imagen base64) no se devuelve en las respuestas de la API de medios del producto `rest/V1/products/sku/media`.
* **ACSD-50276** (para Adobe Commerce >=2.4.0 &lt;2.4.7): corrige el problema en el cual el formulario de registro de cliente no funciona en la tienda si se crea un atributo de cliente de selección múltiple.
* **ACSD-50527** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el error que se produce al guardar una página con un bloque dinámico vacío.
* **ACSD-49973** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): mejora el rendimiento de recuperar productos agrupados a través de GraphQL.
* **ACSD-51114** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual un producto aleatorio desaparece de los catálogos grandes cuando la indexación asincrónica está habilitada. Mejora el rendimiento de la reindexación asíncrona para catálogos grandes.
* **B2B-2598** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): agregue capacidad de almacenamiento en caché a las consultas de GraphQL [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency] y [!UICONTROL storeConfig].
* Se han añadido nuevas versiones para MDVA-42806, ACSD-48627, ACSD-46815.
* Se han actualizado los metadatos de parches para ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el que una API envía un correo electrónico listo para recibir cuando el pedido no está listo para recibir.
* **ACSD-49822** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el cual las actualizaciones en la página [!UICONTROL Requisition List] no se reflejan en [!UICONTROL Print Requisition List].
* **ACSD-48771** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema con la actualización del tipo de contenido de bloque de columna desde versiones anteriores de [!DNL Page Builder].
* **ACSD-49464** (para Adobe Systems Comercio >=2.3.7 &lt;2.4.7) - Fixes the issue where invoices, shipments, and credit memos are not moved back from the archive when the orderId is different.
* **ACSD-49773** (para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where product export fails when AWS S3 is used as remote storage.
* **ACSD-49748** (para Adobe Systems Comercio >=2.3.7 &lt;2.4.7) - Fixes the issue where invitations cannot be sent.
* **ACSD-49502** (para Adobe Systems Comercio >=2.4.3 &lt;2.4.7) - Fixes the issue where the downloadable link is not updated properly after a staging update is applied to the downloadable product.
* **ACSD-49527** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el cual los roles de compañía de GraphQL no muestran la paginación correctamente.
* **ACSD-49706** (para comercio Adobe Systems y Magento Open Source >=2.3.7 &lt;2.4.7) - Fixes the issue where the default value is saved for a visual swatch attribute when no value is selected.
* **ACSD-49835** (for Adobe Commerce and Magento Open Source >=2.4.5 &lt;2.4.7) - Fixes the issue where the Use default checkbox value is not saved correctly on a store level for a multi-select attribute.
* **ACSD-49898** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la cuadrícula de productos genera una excepción cuando un producto agrupado tiene un precio especial que excede los 1000.
* **ACSD-50234** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.5): corrige el problema con el nombre de cliente incorrecto en el correo electrónico de confirmación si se realiza un pedido con [!DNL PayPal].
* **ACSD-49960** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el cual el filtrado por fecha no funciona para la cuadrícula de pedidos del cliente.
* **ACSD-49849** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema en el cual el correo electrónico del cliente se reemplazó con [!DNL PayPal] correo electrónico al realizar un pedido con [!DNL PayPal Express] a través de GraphQL.
* **ACSD-49839** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el cual la estructura y los precios del catálogo compartido generan un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU.
* **ACSD-49970** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el manejo incorrecto de los errores de GraphQL cuando la creación de informes de [!DNL New Relic] está activada.
* **ACSD-50260** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el cual los resultados de búsqueda de productos de GraphQL están limitados a 10 000 resultados solamente.
* **ACSD-48813** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual la búsqueda no muestra resultados relevantes según la ponderación de búsqueda de los atributos.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.3): corrige el problema en el cual una regla de precios de catálogo creada en función del atributo Yes/No no considera el ámbito seleccionado.
* **ACSD-47704** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual el producto agrupado muestra solamente el precio de los productos en existencias.
* **ACSD-49370** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el atributo de producto *Fecha y hora* tiene un tipo *FilterMatchTypeInput* en el esquema de GraphQL.
* **ACSD-48807** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.7): corrige el problema en el cual las revisiones de producto de los clientes no se filtran por la vista de tienda a través de GraphQL.
* **ACSD-49433** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual la cantidad predeterminada se muestra como subtotal en el carro de compras para tarjetas de regalo con una cantidad abierta.
* **ACSD-48866** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que se produce un error al solicitar una fuente RSS para categorías.
* **ACSD-48784** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual los precios de segmentos de clientes se almacenan incorrectamente en caché entre grupos de clientes.
* **ACSD-48857** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual un usuario no puede guardar los cambios después de editarlos con Page Builder.
* **ACSD-49065** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual los elementos de presupuesto no son visibles en el administrador si solo se asignan a las existencias personalizadas.
* **ACSD-49179** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el informe de pedidos muestra importes incorrectos en el caso de que haya distintas divisas para distintas tiendas.
* **ACSD-49286** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el cual un producto se agrega dos veces a un carro de compras cuando hay varios widgets de producto en la página.
* **ACSD-49574** (para Adobe Commerce >=2.4.4 &lt;2.4.7): agrega funcionalidad para admitir actualizaciones de productos de tarjeta regalo en un carro de compras a través de GraphQL.
* Revisión actualizada: ACSD-48694.

## Versión 1.1.27 {#v1-1-27}

* **ACSD-48362** (para Adobe Commerce >=2.4.1 &lt;2.4.7): corrige el problema en el que se usa la dirección de envío predeterminada en lugar de una nueva al realizar un pedido con un presupuesto negociable.
* **ACSD-48059** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el cual los comerciantes no pueden guardar &quot;[!UICONTROL Match product by rule]&quot; en la categoría.
* **ACSD-48216** (para Comercio Adobe Systems y Magento Open Source >=2.3.7 &lt;2.3.8 ||=&quot;&quot;>=2.4.0 &lt;2.4.7) - Fixes the issue where [!UICONTROL AUTO_INCREMENT] de los aumentos de tabla [!UICONTROL inventory_source_item] en la [!UICONTROL UPDATE] operación.&lt;/2.3.8>
* **ACSD-47908** (para comercio Adobe Systems y Magento Open Source >=2,3,7 &lt;2.3.8 ||=&quot;&quot;>=2,4,0 &lt;2.4.7) - Fixes the error &quot;A value less than or equal to 0 is expected&quot; when selecting the source and qty on the shipping step during checkout.&lt;/2.3.8>
* **ACSD-49497** (para comercio Adobe Systems y Magento Open Source >=2.3.7 &lt;2.4.6) - Fixes the issue where an order remains in the processing state after shipment and a partial refund is applied.
* **ACSD-48694** (para Adobe Systems comercio y Magento Open Source >=2,3,7 &lt;2.3.8 ||=&quot;&quot;>=2,4,1 &lt;2.4.7) - Fixes the issue where the error &quot;Invalid state change requested&quot; prevents a customer from placing an order.&lt;/2.3.8>
* **ACSD-49013** (para comercio Adobe Systems y Magento Open Source >=2.4.3 &lt;2.4.7) - Fixes the issue where email confirmation is not translated to the website locale when creating customers using bulk API.
* **ACSD-48164** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual un administrador restringido no puede guardar un valor de nivel de sitio web.
* **ACSD-48404** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema en el cual &quot;Recordar paginación de categoría = Sí&quot; causa un error al presionar el botón Atrás del explorador.
* **ACSD-48634** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige los errores de JS en una página de actualización de ensayo cuando &quot;[!UICONTROL Google Analytics Content Experiments]&quot; está habilitado.
* **ACSD-49042** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): corrige el problema en el cual un producto con un pedido pendiente infinito no se puede pedir desde la Tienda.
* Revisiones actualizadas: ACSD-48366, ACSD-48661.

## Versión 1.1.26 {#v1-1-26}

* **ACSD-47937** (para Adobe Commerce y el Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6): corrige el problema en el que las notificaciones de caída de precios no siempre se envían debido al almacenamiento en caché de nivel de aplicación.
* **ACSD-48661** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual si el límite de crédito de la compañía es mayor que 999, el separador de comas impide guardar la compañía debido a un error de validación.
* **ACSD-48773** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema por el que la plantilla de correo electrónico de puntos de recompensa se toma de la tienda incorrecta.
* **ACSD-48587** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual los caracteres especiales de HTML en el widget de productos que coinciden con las reglas impiden que se muestren los productos coincidentes.
* **ACSD-48212** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema por el que la importación de productos asigna el producto al origen incorrecto.
* **ACSD-47988** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema en el que la exportación del producto recorta las etiquetas de HTML de la descripción del producto del generador de páginas.
* **ACSD-48366** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el cual la imagen del producto no se muestra en la plantilla de correo electrónico Volver a stock.
* **ACSD-48417** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que aparece un error SQL después de crear un cambio de programación para un producto y guardar otro.

## Versión 1.1.25 {#v1-1-25}

* **ACSD-48058** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el cual el reíndice de precios de productos no funciona si el producto del paquete no está asignado a ningún sitio web.
* **ACSD-48262** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el cual los productos no son visibles en el front-end cuando la configuración &quot;Permitir todos los productos por página&quot; está establecida en Sí.
* **ACSD-48293** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4): corrige el problema en el que los productos compuestos no están disponibles cuando los productos secundarios que se agotaron vuelven a estarlo.
* **ACSD-47520** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual los clientes pierden puntos de recompensa cuando se crea un abono.
* **ACSD-48044** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema en el cual la aplicación de varias tarjetas regalo a un único pedido con envío múltiple impide que se realicen pedidos.
* **ACSD-48300** (para comercio Adobe Systems y Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where a return cannot be created if the configurable product is removed.
* **ACSD-47910** (para comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue of missing orders, invoices, shipments, and credit memos in respective entity grids.
* **ACSD-47292** (para comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where out-of-stock bundled products are not available in the GraphQL response if the &quot;show out-of-stock products&quot; is set to Yes.
* **ACSD-48234** (para comercio Adobe Systems y Magento Open Source >=2.4.5 &lt;2.4.6) - Fixes the issue where the catalog search result shows an incorrect category item count when the &quot;show out of stock&quot; option is enabled.
* **ACSD-48313** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5): corrige el problema en el cual la columna &quot;configurable_variaciones&quot; no se analiza si el valor del atributo contiene una coma. Se utiliza el mismo algoritmo de análisis para &quot;additional_attributes&quot;.
* **ACSD-48627** (para comercio Adobe Systems y Magento Open Source >=2,4,5 &lt;2.4.6) - Fixes the issue where the out-of-stock configurable product causes an error when sending a GraphQL request to get cart details.
* Actualizado parche: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (para Adobe Systems de comercio y Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where SEO-friendly URLs are not generated for products that have *url_key* atributos se anulan en el nivel tienda-vista.
* **ACSD-46865** (para comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where the Shipment and Credit Memo grid is not populated when asynchronous indexing is enabled.
* **ACSD-47004** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que el IVA no se aplica a una dirección de facturación sin un ID de IVA.
* **ACSD-47803** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que se muestran muestras de productos configurables sin existencias como disponibles.
* **ACSD-47137** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): mejora la velocidad de carga de la galería de imágenes cuando la carpeta pub/medios es muy grande.
* **ACSD-46770** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema por el que se envían correos electrónicos de pedidos de administración incluso cuando *Confirmación de pedidos de correo electrónico* está desmarcada.
* **ACSD-47955** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el cual GraphQL no muestra correctamente el descuento del carro de compras.
* **ACSD-46617** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que el botón *Continuar con el cierre de compra* aparece atenuado aunque el subtotal sea mayor que la *Cantidad mínima del pedido* configurada.
* **ACSD-47079** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): corrige el problema en el que el estado de las existencias de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de las existencias de subproductos cambia a través del POST de API de REST /rest/V1/inventory/source-items.
* **ACSD-47336** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6) - Correcciones *Se produjo un error.Error* al descartar las notificaciones en el administrador de Commerce.
* **ACSD-47559** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que el área Vista previa de plantillas de correo electrónico no es totalmente visible.
* **ACSD-47920** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual los pedidos se pueden realizar a través de la API de REST como usuario invitado incluso cuando *Permitir cierre de compra para invitados* está desactivado.
* Parches reemplazados: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual un administrador con acceso restringido a un ámbito específico no puede eliminar críticas de productos.
* **ACSD-47107** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5): corrige el problema en el que el descuento de la regla de precio de catálogo se aplica a las opciones de producto personalizadas.
* **ACSD-47232** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual los cupones con condiciones de peso total no se pueden aplicar en Admin.
* **ACSD-46519** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.6): corrige el problema en el que la solicitud categoryList de GraphQL devuelve un product_count incorrecto para una categoría anclada.
* **ACSD-47027** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige una solicitud de GraphQL updateCompanyRole lenta.
* **ACSD-47666** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que la función de filtrado no funciona en la cuadrícula Administración > Sistema > Permisos > Funciones de usuario > una función > Funciones de usuario.
* **ACSD-47497** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual la pestaña Servicios no está visible en la configuración de Admin.
* Updated patch: ACSD-47743.
* Replaced patches: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.3) - Fixes the _Trying to access array offset on value of type bool_ error when accessing certain non-existing category paths for known products on PHP 7.4.
* **ACSD-47332** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Fixes the issue where cron fails with an error that is only reported when running between 00:00 and 00:59 UTC.
* **ACSD-47280** (para comercio Adobe Systems y Magento Open Source >=2,4,0 &lt;2.4.6) - Fixes the issue where disabling the shared catalog feature on a specific scope does not work correctly.
* **ACSD-47106** (para comercio Adobe Systems y Magento Open Source >=2.4.4 &lt;2.4.6) - Fixes the issue where a value cannot be saved in a new custom attribute on a company creation page.
* Updated patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.6) - Fixes the issue where a user gets an error when assigning a large number of product sources.
* **ACSD-46856** (for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.6) - Improves performance updating tier prices via System > Configuration > Import > Advanced Pricing.
* **ACSD-46541** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema en el cual un usuario administrador no puede crear un abono si se elimina un elemento de pedido.
* **ACSD-46581** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual el total de impuestos estimado no se actualiza después de seleccionar un país en el carro de compras.
* **ACSD-46618** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el cual el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.
* **ACSD-46674** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que las opciones personalizadas de un tipo de imagen se muestran como HTML en los correos electrónicos de los clientes.
* **ACSD-46988** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la solicitud de API &quot;currency&quot; de GraphQL devuelve valores NULL para una divisa personalizada.
* **ACSD-47076** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5): corrige el problema por el que los vídeos de Vimeo no se pueden reproducir en la tienda.
* **ACSD-45071** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4): corrige el problema en el que se agrega el origen predeterminado al producto durante la importación.
* **AC-3023** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6) - Actualice el esquema DHL a la última versión 10.0.
* Revisiones actualizadas: MDVA-42584.
* Parches reemplazados: MDVA-36572, ACSD-45241.

## Versión 1.1.20 {#v1-1-20}

* **ACSD-46520** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): corrige el problema en el que un usuario obtiene un estado de pedido incorrecto al recibir un reembolso con el crédito de la tienda.
* **ACSD-46703** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6*): corrige el problema en el que no es posible arrastrar y soltar opciones personalizadas en una página de edición de producto.
* **ACSD-44851** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6*): corrige el problema en el que una categoría con subcategorías no se puede abrir ni expandir.
* **ACSD-46815** (*para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6*): corrige el problema en el que la solicitud del árbol de categorías está limitada a 20 categorías.
* **ACSD-45675** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6*): corrige el problema en el que la exportación del producto usa nombres de categoría del ámbito *Vista de tienda predeterminada*.
* **ACSD-46869** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6*): corrige el problema en el cual un producto configurable en un carro de compras no se actualiza a través de una solicitud de *API de REST de PUT* sin cambiar la cantidad del producto.
* **MDVA-42768-V2** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que el producto configurable muestra el precio normal como *0* cuando *Mostrar de existencias* es *Sí*.
* Revisiones actualizadas: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Parche obsoleto: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que la solicitud del árbol de categorías está limitada a 20 categorías.
* **ACSD-45781** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.2*): corrige el problema en el que el campo de búsqueda de la tienda no se muestra en dispositivos móviles.
* **ACSD-46192** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;2.4.5*): corrige el problema con el uso del extremo `async/bulk/V1/configurable-products/bySku/options`.
* **ACSD-46404** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5*): corrige el problema en el cual un usuario administrador no puede iniciar sesión después de actualizar a 2.4.4.
* Revisiones actualizadas: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## Versión 1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que una mutación de producto de GraphQL para un almacén específico devuelve todas las variantes configurables, incluidas las que no están asignadas al almacén solicitado.
* **ACSD-46146** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.6*): corrige el problema por el que se envían dos correos electrónicos de confirmación de pedido después de realizar un pedido desde el administrador.
* **ACSD-45255** (*para Adobe Commerce >=2.4.3 &lt;2.4.6*): corrige una excepción en la página Informe de existencias bajas para un usuario administrador restringido.
* **ACSD-45488** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6*): corrige el problema en el cual un producto configurable con múltiples orígenes no se devuelve a En existencia automáticamente.
* **ACSD-45754** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.6*): corrige el problema en el cual no se agregan puntos de recompensa después de aplicar un cupón al carro de compras.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*): corrige el problema en el que se pierden los metadatos de vídeo después de aplicar una actualización de ensayo.
* **ACSD-45257** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.4*): corrige el problema en el cual GraphQL no muestra correctamente un descuento del carro de compras.
* **ACSD-44938** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*): corrige el problema en el cual `VAT_ID` no se puede aplicar en una solicitud de GraphQL para un usuario invitado.
* Revisiones actualizadas: MDVA-43417.

## Versión 1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.4*): corrige el problema por el que la cantidad de existencias para un producto virtual se calcula de forma incorrecta después de crear un abono.
* **ACSD-43887** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando se habilitan pedidos de compra para empresas.
* **ACSD-45143** (*para Adobe Commerce y el Magento Open Source >=2.4.0 &lt;2.4.5*): corrige el problema en el que la mutación `setShippingAddressesOnCart` no permite establecer el código de región numérica como *region*.
* **ACSD-44591** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.6*): corrige el error que se produce cuando se realiza un pedido sin confirmación CAPTCHA.
* **ACSD-45520** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.6*): corrige el problema en el que las opciones de muestra no están preseleccionadas en la página de detalles del producto cuando un usuario edita productos configurables del carro de compras.
* **ACSD-45169** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.6*): corrige el problema en el cual [!DNL Visual Merchandiser] no muestra el stock y precio correctos para un producto configurable después de aplicar una actualización de ensayo.
* **ACSD-45424** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.6*): corrige el problema en el que se crea una compensación de reserva incorrecta después de un reembolso parcial (nota de crédito).
* **MDVA-42807** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.6*): corrige el problema por el que el signo de moneda personalizado no se muestra en la tienda.
* Revisiones actualizadas: MDVA-42689, AC-3022.

## Versión 1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema en el que los totales de pedidos del informe Pedidos se calculan incorrectamente para el usuario administrador restringido.
* **MDVA-44940** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el error de SQL que se produce al guardar la categoría desde el administrador.
* **MDVA-44562** (*para Adobe Systems Commerce y Magento Open Source >=2.4.0 &lt;2.4.2-p2*): soluciona el problema por el cual el ID de tienda predeterminado anulaba el ID de tienda no predeterminado para los elementos de cotización, a pesar de que el solicitud GraphQL se originaba en el tienda vista no predeterminado.
* **MDVA-43167** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que la acción masiva de la cuadrícula de pedidos de administración no se aplica a varias páginas cuando el usuario administrador selecciona todas las solicitudes.
* **MDVA-44044** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.2-p2*): corrige el problema en el cual un producto no se muestra en la página de categoría después de asignarse a un nuevo sitio web.
* **MDVA-42509** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.4*): corrige el problema en el cual no se pudo cargar un CSV para un pedido rápido, lo que resultó en un error de *No se pudo enviar la cookie*.
* Revisiones actualizadas: MDVA-41061, MDVA-42584.
* El prefijo de los nuevos [!DNL Quality Patches Tool] parches se cambiará de *MDVA* a *ACSD* debido a cambios en el proceso interno.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*para comercio Adobe Systems y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema por el que no se puede agregar un elemento adicional al carro de compras cuando la cantidad mínima del artículo ya está en el carro de compras.
* **MDVA-44887** (*para comercio Adobe Systems y Magento Open Source >=2.4.4*&lt;2.4.5): corrige el *error de sintaxis no detectado: error inesperado de token &#39;const&#39;* en el panel de administración.
* **MDVA-43718** (*para comercio Adobe Systems y Magento Open Source >=2.3.0 &lt;2.4.5*): correcciones *El consumidor no tiene autorización para acceder a %resources.* Error que aparece al acceder a un catálogo compartido desde una integración personalizada.
* **MDVA-44660** (*para Adobe Commerce y Magento Open Source >=2.4.2-p1 &lt;2.4.5*): corrige el problema en el que el carácter de acento grave ``` ` ``` no se podía usar para el nombre y los apellidos de un cliente.
* **MDVA-40896** (*para Adobe Commerce y el Magento Open Source >=2.4.3 &lt;2.4.4*) - Corrige el error *Error: TypeError: el argumento 3 pasado al Magento* en la API de productos asíncronos en bloque.
* **MDVA-38559** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3*): corrige el error */V1/customers/search API* para clientes con más de una suscripción.
* **MDVA-44533** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.4*): corrige el problema en el que el descuento se aplica incorrectamente a un producto secundario del paquete.
* Revisiones actualizadas: MDVA-41061, MDVA-42269.

## Versión 1.1.14 {#v1-1-14}

* **MDVA-43983** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que los productos *No visibles de forma individual* siguen apareciendo en los resultados de búsqueda avanzada del catálogo.
* **MDVA-44100** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema por el que todos los FTP se asignan al último producto del carro de compras y se restablecen para otros productos.
* **MDVA-43605** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.5*): corrige el problema en el que los datos de pedidos devuelven valores negativos para los totales de filas al usar la API de REST.
* **MDVA-43102** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.5*): corrige el problema en el que la cantidad vendible no se actualiza correctamente cuando se realiza un reembolso mediante la API de REST.
* **MDVA-43178** (*para comercio Adobe Systems y Magento Open Source >=2.4.3-p2 &lt;2.4.5*): corrige el problema por el que no se puede recuperar un token de cliente para un tienda personalizado en GraphQL.
* **MDVA-43859** (*para comercio Adobe Systems y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el que se producía el error *No se registra ninguna entidad de este tipo con customerId =* cuando un cliente eliminado intenta iniciar sesión.
* **MDVA-44147** (*para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema por el que un solicitud de GraphQL no devuelve listas de solicitudes.
* **MDVA-44505** (*para comercio Adobe Systems y Magento Open Source >=2.4.1 &lt;2.4.3*): corrige los problemas en los que GraphQL Applying Reward Puntos no actualiza Total general y donde tienda crédito se aplica varias veces durante el ubicación del pedido.
* Parches actualizados: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## Versión 1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): corrige el problema en el que la regla de producto relacionada solo funciona cuando el segmento de cliente está establecido en *Todos*.
* **MDVA-39605** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): corrige el problema en el que el TTL de caché de Redis (fecha de caducidad) tiene un valor incorrecto.
* **MDVA-43862** (*para Adobe Commerce y el Magento Open Source >=2.3.3 &lt;2.4.5*): corrige el problema en el cual el cliente no puede actualizar los elementos del carro de compras debido a un error de *UpdateCartItems* de GraphQL.
* **MDVA-43824** (*para comercio Adobe Systems y Magento Open Source >=2.3.6 &lt;=2.3.7-p3 ||=&quot;&quot;>=2.4.1 &lt;2.4.5*): soluciona el problema por el que aparece un error al cancelar pedidos con descuento.&lt;/=2.3.7-p3>
* **MDVA-43451 (para comercio Adobe Systems y Magento Open Source >=2.4.3&lt;2.4.5 *): corrige el problema por el cual no se encontraba el error*No se encontró el tienda solicitado.***Compruebe el tienda e inténtelo de nuevo.* aparece al configurar un catálogo compartido para un sitio web específico.
* **MDVA-43491** (*para comercio Adobe Systems y Magento Open Source >=2.3.5 &lt;2.4.5*): corrige el problema por el cual la etiqueta de la imagen base no se actualiza al importar productos para un sitio web de varias tienda.
* **MDVA-43601** (*para comercio Adobe Systems y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema con la falta de activadores después del reindexado completo.
* **MDVA-42046** (*para Adobe Commerce y el Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*): corrige el problema en el que se asigna un valor incorrecto a un atributo de producto con un campo de entrada de fecha al actualizar un producto.
* **MDVA-43935** (*para comercio Adobe Systems y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema por el cual el producto Upsell se mostraba dos veces.
* **MDVA-44188** (*para comercio Adobe Systems y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema por el que no se envían correos electrónicos emitidos por el sistema con `.-` direcciones in.
* **MDVA-42283** (*para comercio Adobe Systems y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema por el que el formato de fecha y hora de la cuadrícula de pedidos de administración para la configuración regional de Francés es no válido.
* Parches actualizados: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Se han añadido parches metadatos para el [!DNL Site-Wide Analysis Tool]archivo .

## Versión 1.1.12 {#v1-1-12}

* **MDVA-39713** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.3.6*): corrige el problema en el que el usuario puede editar la hora de inicio de una actualización programada activa.
* **MDVA-42410** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que los informes de cupones solo muestran la moneda base predeterminada.
* **MDVA-41136** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que la fecha de caducidad de `mage-cache-sessid` no se amplía, lo que da como resultado la limpieza de datos del cliente.
* **MDVA-39993** (*para Adobe Commerce y el Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*): corrige el problema por el que los cambios de inventario realizados mediante API no se reflejan en la página del producto en el front-end.
* **MDVA-42855** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el cual una nueva dirección de cliente no se guarda en la libreta de direcciones durante el cierre de compra.
* **MDVA-42645** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el cual el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de la tienda está deshabilitada.
* **MDVA-43414** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2*): corrige el error irrecuperable de PHP que se produce al ejecutar el consumidor de cola `inventory.reservations.updateSalabilityStatus` en SKU numéricas.
* **MDVA-41628** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): corrige el problema en el cual los usuarios administradores restringidos existentes obtienen acceso a los nuevos recursos cuando se agregan nuevos módulos.
* **MDVA-43348** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que la solicitud de GraphQL para tarjetas regalo muestra un error si `gift_card_options` contiene *uid*.
* **MDVA-39546** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema por el que la fecha de inicio de la actualización de ensayo se podía establecer en una fecha anterior a la fecha actual durante la edición.
* **MDVA-42950** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema por el que los vídeos no se reproducen en la página del producto.
* **MDVA-42689** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que Adobe Commerce genera un error de *infracción de restricción de integridad* al actualizar las categorías de productos durante la importación.
* **MDVA-41229** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el cual las imágenes disponibles en el backend no se muestran en el front-end después de importar productos configurables.
* **MDVA-43731** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema en el que *Buscar sinónimos* ya no funciona cuando se agrega un valor en *Términos mínimos que deben coincidir*.
* **MDVA-43232** (*para Adobe Commerce y el Magento Open Source >=2.3.4 &lt;2.4.5*): corrige el problema en el cual ordenar productos en [!DNL Visual Merchandiser] por precio especial a inferior/superior causa un error al guardar la categoría.
* **MDVA-43726** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.3*): corrige el problema en el que la regla de precio de catálogo basada en la coincidencia de atributos de nivel de tienda no se aplica después de una reindexación parcial.
* Revisiones actualizadas: MDVA-36464, MDVA-37478, MDVA-38608.
* Se agregaron los metadatos de revisiones para [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el cual los atributos del precio del producto no se pueden actualizar para un sitio web específico a través de la API de REST.
* **MDVA-41350** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que se genera una excepción cuando un usuario administrador con acceso restringido agrega un producto fuera del ámbito de su función por SKU en un pedido.
* **MDVA-42269** (*para Adobe Commerce y Magento Open Source >=2.4.3-p1 &lt;2.4.5*): corrige el problema en el cual un usuario administrador no puede iniciar sesión en el administrador debido al error *TypeError: strtotime() espera que el parámetro 1 sea una cadena, nulo dado*.
* **MDVA-40830** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que el crédito de tienda se aplica varias veces durante la realización del pedido.
* **MDVA-42237** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el cual un precio especial de producto configurable no se actualiza después de cambios en su precio de subproducto.
* **MDVA-42520** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema en el que la tasa impositiva se aplica dos veces si se utiliza *Habilitar comercio transfronterizo*.
* Revisiones actualizadas: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Parche obsoleto: MDVA-37725.

## Versión 1.1.10 {#v1-1-10}

* **MDVA-38728** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.4.5*): corrige el problema en el que la actualización masiva de atributos crea una reescritura de URL para el almacén predeterminado solo después de cambiar *visibilidad del producto*.
* **MDVA-43091** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema en el cual al solicitar un paquete de producto al administrador en el backend se produce el error *No se puede usar la cantidad decimal para este producto*.
* **MDVA-40816** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que las reglas de productos relacionadas muestran productos de categorías no definidas en las condiciones de regla.
* **MDVA-41305** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el cual la mutación de GraphQL no devuelve opciones de producto configurables después de agregarla a la lista de deseos.
* **MDVA-39181** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el que las reglas de productos relacionadas muestran productos de categorías no definidas en las condiciones de regla.
* **MDVA-42584** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que el estado de existencias configurable en el backend no se actualiza después de cambiar la cantidad y el estado de existencias mediante Import o API.
* **MDVA-40175** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3*): corrige el problema por el que *Hacer clic para cambiar el método de envío* no muestra botones de opción para seleccionar métodos de envío en Admin durante el repedido.
* **MDVA-42768** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): corrige el problema en el que el producto configurable muestra el precio normal como 0 cuando *Mostrar de existencias* es Sí.
* **MDVA-43201** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que se produce un error en el inicio de sesión del cliente al usar el atributo DOB con ciertas configuraciones regionales.
* Revisiones actualizadas: MDVA-35092, MDVA-33970.

## Versión 1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que los filtros de fecha no funcionan correctamente cuando la zona horaria de Adobe Commerce es diferente de la del entorno local.
* **MDVA-42657** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el cual el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente.
* **MDVA-42806** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema por el que se envía un correo electrónico de *Registro de nueva compañía* cada vez que se actualiza una compañía existente a través de la API de REST.
* **MDVA-37984** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el que la funcionalidad [!DNL Visual Merchandiser] *Hacer coincidir producto por regla* no filtra correctamente los productos con actualizaciones de ensayo.
* **MDVA-40488** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el cual los productos configurables con productos secundarios sin existencias no se muestran en su rango de precios correcto.
* **MDVA-42507** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que la caché de página completa se limpia después de aplicar la actualización de ensayo para la regla de carro de compras.
* **MDVA-39163** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.5*): corrige el problema por el que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitado.
* **MDVA-38626** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.5*): corrige el problema en el cual el usuario administrador no puede realizar un pedido en el backend usando el pago de [!DNL PayPal Payflow Pro].
* **MDVA-38666** (*for Adobe Commerce and Magento Open Source >=2.3.2 &lt;2.3.6*) - Fixes the issue where the admin user is not able to change the configurable product options in the customer&#39;s cart.
* **MDVA-38526** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.4*) - Fixes the issue where the admin user is not able to access the [!DNL Site-Wide Analysis tool].
* Updated patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.4*) - Fixes the issue where users get the 500 error after setting the *mage-messages* cookie if it already exists, but there are no new messages.
* **MDVA-41139** (*for Adobe Commerce and Magento Open Source >=2.4.3 &lt;2.4.4*) - Fixes the issue where configurable products become Out of Stock after product import when a simple product&#39;s qty=0 for one of its sources.
* **MDVA-42326** (*for Adobe Commerce and Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Fixes the issue where customers get an error on checkout after a session timeout even if the persistent shopping cart is enabled.
* **MDVA-42341** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*) - Fixes the issue where the `categoryList` GraphQL query does not filter results if a request has the Store header.
* **MDVA-38393** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.4*) - Fixes the issue where Catalog rules stop working for a configurable product if its simple product is re-named.
* **MDVA-39153** (*for Adobe Commerce and Magento Open Source >=2.4.2 &lt;2.4.4*) - Fixes the issue where a discount amount is calculated incorrectly during reorder in the Admin.
* Updated patches: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*for Adobe Commerce and Magento Open Source >=2.3.0 &lt;2.4.3*) - Fixes the issue where admin users cannot access the customer&#39;s grid after deleting the website.
* **MDVA-40311** (*for Adobe Commerce and Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Fixes the issue where admin users get the error message *Invalid security or form key. Please refresh the page* after login to the Admin if the custom Admin path is configured and secret key is enabled.
* **MDVA-41631** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.4*) - Fixes the issue where users get an error when trying to retrieve order information without an optional *telephone* value through GraphQL.
* **MDVA-27239** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.3.6*): corrige el problema en el que no se muestran los productos de venta cruzada.
* Updated patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*for Adobe Commerce and Magento Open Source >=2.3.5 &lt;2.4.4*) - Fixes the issue with missing products on the frontend during reindexing.
* **MDVA-40120** (*for Adobe Commerce and Magento Open Source >=2.4.1 &lt;2.4.4*) - Fixes the issue where GraphQL sorting by DESC/ASC doesn&#39;t work with products having the same relevance or price.
* **MDVA-41399** (*for Adobe Commerce and Magento Open Source >=2.3.3 &lt;2.4.2*) - Fixes the issue where admin users are unable to access the *Manage Shopping Cart* page if a customer adds a product to the wishlist.
* **MDVA-40609** (*para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema por el que los datos de productos deshabilitados están ausentes en la tabla de `cataloginventory_stock_status` índice, mostrando cantidades incorrectas de productos deshabilitados.
* **MDVA-39031** (*para comercio Adobe Systems y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema por el que es posible agregar un producto al carro de compras a través de GraphQL igualado si no está asignado al sitio web destino.
* **MDVA-41597** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que los usuarios reciben un error al agregar más de un producto configurable al carro de compras mediante GraphQL.
* **MDVA-27456** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.3.7*): corrige el problema en el que los usuarios reciben un error al intentar cargar [!DNL Swagger].
* **MDVA-32776** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.2*): corrige el problema en el que el estado de las existencias no se actualiza cuando se realiza un pedido, pero no se envía.
* **MDVA-30862** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.0*): corrige el problema con la fecha de pedido incorrecta en la factura de PDF impresa.
* Se mejoró la página de índice de [!DNL Quality Patch Tool]. Se agregaron la búsqueda y el filtrado convenientes para [!DNL quality patches] en la última versión de la herramienta.
* Revisiones actualizadas: MDVA-33382, MDVA-39482.

## Versión 1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que es imposible crear una actualización programada nueva o editar una existente para un producto si la fecha de finalización se ha eliminado anteriormente.
* **MDVA-41046** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que hay productos simples con opciones personalizadas disponibles para asignarlos a productos configurables o agrupados.
* **MDVA-40545** (*para comercio Adobe Systems y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema por el cual solo se recuperaba el primer nodo de un Página igualado si había más de un nodo para la misma Página.
* **MDVA-41164** (*para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.3-p1*): corrige el problema por el que un administrador usuario no podía guardar o editar una empresa con un atributo de cliente personalizado de tipo archivo o imagen.
* **MDVA-39229** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema que hace que aparezca el siguiente error después de actualizar la hora de inicio de la actualización de ensayo de la regla del catálogo: *Cron Job staging_sync_entities_period tiene un error: La actualización activa no se puede eliminar.*
* **MDVA-40619** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el cual los cambios en la jerarquía de páginas de CMS causan un error 500 al intentar realizar la edición en línea en una página de CMS.
* **MDVA-41061** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que el estado de las existencias se restablece como comercializable cuando se guarda un producto del administrador.
* **MDVA-31763** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que las reglas de precios de catálogo se revierten (o no se aplican) hasta el reíndice manual.
* **MDVA-37748** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que una consulta de GraphQL devuelve productos no asignados a un catálogo compartido.

## Versión 1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el cual las facturas parciales para el mismo pedido no se pueden crear simultáneamente a través de la API REST.
* **MDVA-40101** (*para comercio Adobe Systems y Magento Open Source >=2.3.2 &lt;2.4.0*): corrige el problema por el cual los artículos no se eliminan del mini carro de compras después de un pedido exitoso ubicación al usar [!DNL PayPal Express] Checkout.
* **MDVA-40401** (*para comercio Adobe Systems y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 ||=&quot;&quot;>=2.4.1 &lt;2.4.4*): corrige el problema por el cual cupón valor de uso cambia igualado si se realiza un pedido.&lt;/=2.3.7-p2>
* **MDVA-40537** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.4.0-p1*): corrige el problema en el cual los usuarios reciben un error al crear una vista de tienda si existen varias páginas de CMS con la misma clave de URL.
* **MDVA-37725** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.4.3-p1*): corrige el problema por el que los correos electrónicos de pedidos asincrónicos enviados desde sitios web no predeterminados contienen direcciones URL de logotipo desde el sitio web predeterminado.
* **MDVA-39482** (*para Adobe Commerce y el Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*): corrige el problema de que un producto se quede sin existencias si se importa con una cantidad &quot;0&quot; cuando los pedidos no satisfechos están habilitados.
* **MDVA-40435** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.4*): corrige el problema con un descuento incorrecto en los productos agrupados con precios dinámicos cuando se aplican a través de GraphQL.
* **MC-42528** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;=2.4.3-p1*): corrige el problema en el que la consulta de GraphQL `categoryList` devuelve categorías asignadas y no asignadas.
* **MDVA-29400 (para Adobe Systems comercio y Magento Open Source >=2,3,0 &lt;=2.3.7-p1 ||=&quot;&quot;>=2,4.0 &lt;=2.4.0-p1 *) - Soluciona el problema con pedidos duplicados realizados con [!DNL PayPal Express Checkout].&lt;/=2.3.7-p1>***
* **MDVA-26005** (*para comercio Adobe Systems y Magento Open Source >=2.3.4 &lt;=2.3.5-p2*): corrige el problema por el que es imposible seleccionar un categoría en un árbol de categoría para las condiciones del precio del carro regla.
* **MDVA-25631** (*para comercio Adobe Systems y Magento Open Source >=2.3.3 &lt;=2.3.5-p2*): mejora el rendimiento para editar y guardar segmentos de clientes que contienen un gran número de clientes.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema por el cual las consultas GraphQL búsqueda no se muestran en términos búsqueda populares en la administración.
* **MDVA-40601** (*para comercio Adobe Systems y Magento Open Source >=2.3.1 &lt;=2.4.2-p2*): corrige el problema por el que los usuarios obtienen un error al intentar obtener información sobre el categoría modificado mediante una actualización programada a través de GraphQL.
* **MDVA-37234** (*para comercio Adobe Systems y Magento Open Source >=2.3.5 &lt;2.4.0 ||=&quot;&quot;>=2.4.1 &lt;=2.4.2-p2*): soluciona el problema por el que al agregar un elemento al carro de compras varias veces (varias veces (solicitud paralelas) para el mismo unidad de almacén se crea un duplicado elemento de línea para el mismo ID de carro de compras.&lt;/2.4.0>
* **MDVA-33606** (*para comercio Adobe Systems y Magento Open Source >=2.4.1 &lt;=2.4.2-p2*): corrige el problema en el que los usuarios obtienen un *error de infracción* de restricción única al guardar un Página CMS asignado a un jerarquía.
* **MDVA-31590** (*para comercio Adobe Systems y Magento Open Source >=2.4.0 &lt;=2.4.1-p1*): corrige el problema por el que los usuarios no pueden actualizar atributos de forma masiva utilizando colas asíncronas de MySQL.
* **MDVA-36309** (*para Adobe Systems comercio y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): corrige el problema por el cual la búsqueda por atributos del producto es lenta en las cuadrículas de administración.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Commerce y el Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que la factura con FPT muestra un total general incorrecto cuando el pedido se paga desde el crédito de la tienda.
* **MDVA-37364** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.3*): corrige el problema en el que el atributo de cliente personalizado de tipo de fecha rompe la interfaz de usuario de cuadrícula del cliente.
* **MDVA-39195** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): corrige el problema por el que el botón *Agregar al carro* estaba inactivo en la página de categoría cuando se habilitó la redirección al carro de compras.
* **MDVA-37115** (*para comercio Adobe Systems y Magento Open Source >=2.4.2&lt;=2.4.2-p2*): corrige el problema por el cual se muestra un aviso de Solo 0 restantes *innecesario* en el página de producto configurable.
* **MDVA-39521** (*para comercio Adobe Systems y Magento Open Source >=2.4.0 &lt;2.4.4*): corrige el problema por el que el usuario no puede establecer las direcciones de envío en el carro de compras con un número de teléfono vacío a través de GraphQL.
* **MDVA-39384** (*para comercio Adobe Systems y Magento Open Source >=2.3.1 &lt;=2.3.6 ||=&quot;&quot;>=2.4.1 &lt;=2.4.3*) - Corrige el problema por el cual no se guardaba el atributo personalizado del cliente para un compañía usuario.&lt;/=2.3.6>
* **MDVA-39043** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.4.3*): corrige el problema en el cual el usuario administrador con acceso limitado obtiene un error al intentar agregar el widget *Productos* a la página de CMS.
* **MDVA-39966** (*para Adobe Commerce y el Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*): corrige el problema con la implementación de configuraciones regionales incorrectas.
* **MDVA-38852** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.5-p2*): corrige el problema en el que el inventario de catálogo por diseño bloquea las tablas para actualizaciones que reducen significativamente el rendimiento en casos con varios pedidos paralelos.
* **MDVA-39986** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): corrige el problema en el cual el usuario no puede realizar un pedido en Admin en MacOS usando el explorador Safari.
* **MDVA-38447** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige dos problemas: donde los productos secundarios *No visibles de forma individual* se devuelven en la respuesta de GraphQL y optimiza la consulta MySQL para la consulta de productos de GraphQL con filtro de categoría.
* **MDVA-40134** (*para comercio Adobe Systems y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema por el que GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado.
* **MDVA-39935** (*para comercio Adobe Systems y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema por el que GraphQL devuelve productos secundarios configurables deshabilitados a nivel de sitio web.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*for Adobe Commerce and Magento Open Source >=2.4.0 &lt;2.4.4*) - Fixes the issue where the *Call to a member function getId()* error is displayed on the order details page in the Admin.
* **MDVA-34948** (*para Adobe Commerce y el Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*): corrige el problema con consultas de larga ejecución, como `GET_LOCK`.
* **MDVA-39305** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.2-p1*): corrige el problema en el cual los clientes registrados no pueden iniciar sesión con Google ReCaptcha habilitado.
* **MDVA-37897** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema con una redirección incorrecta cuando un cliente intenta agregar productos con opciones del widget visualizado recientemente.

## Versión 1.1.0 {#v1-1-0}

* Las categorías de parches se introdujeron para mejorar la experiencia del usuario y facilitar la búsqueda de los parches necesarios a los clientes.
* Se cambió el nombre del archivo `patches.json` a `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema en el cual los productos descargables no se guardaban después de crear una actualización de ensayo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): corrige el problema que se produce cuando la ordenación por precio no funciona correctamente para productos con un precio cero asignado al catálogo compartido.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*): corrige el problema en el que los clientes reciben un correo electrónico de envío de pedidos que contiene un mensaje de error.

## Versión 1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*): corrige el error al guardar páginas de CMS: *Ya existe un elemento con el mismo ID PAGE_ID*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*): corrige el problema por el que la hora de creación de la cuenta de cliente no se filtra correctamente en la cuadrícula de clientes.
* **MDVA-37068** (*para Adobe Commerce >=2.3.1 &lt;2.4.4*): corrige el problema en el que se muestra la tasa de impuestos incorrecta cuando el carro de compras solo tiene productos virtuales.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema en el que las tablas temporales no se eliminan cuando el reíndice no finaliza correctamente.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*): corrige los problemas relacionados con la adición de [!DNL Vimeo] vídeos a los productos.

## Versión 1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*): corrige el problema en el cual el cliente no es llevado a la página de confirmación de pago al usar el método [!DNL Paypal Payment Advanced].
* **MDVA-37082** (*for Adobe Commerce >=2.3.0 &lt;2.4.3*) - Fixes the issue when saving the custom stock of grouped products causes the product to show out of stock in the frontend.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*): corrige el problema cuando las actualizaciones de notas de crédito ya no causan actualizaciones de reservas de productos duplicadas en la base de datos.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*): corrige el problema cuando el Panel de administración no está disponible debido a un error de *demasiadas redirecciones*.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): corrige el problema por el que falta información de la tarjeta regalo en el total del pedido en GraphQL.

## Versión 1.0.24 {#v1-0-24}

* **MDVA-37779** (*para Adobe Commerce >=2.4.2 &lt;=2.4.4*): corrige el problema que se produce al agregar un producto configurable al carro de compras mediante GraphQL cuando el identificador del sitio web no coincide con el identificador de la tienda.
* **MDVA-36832** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): corrige el problema por el que las imágenes se duplican en las páginas cuando la anchura de la vista es de 768 px.
* **MDVA-37874** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*): corrige el problema por el que *la cantidad de descuento fija para el carro de compras completo* se aplica incorrectamente a un producto agrupado que contiene más de una opción.
* **MDVA-37913** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*): corrige el problema en el cual los vínculos descargables desaparecen si el producto descargable se actualiza a través de la API.
* **MDVA-34330** (*para Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*): corrige el problema en el que los pedidos de la cuadrícula Pedidos no se filtran de acuerdo con la zona horaria del administrador.

## Versión 1.0.23 {#v1-0-23}

* **MDVA-37478** (*para Adobe Commerce >=2.3.0 &lt;=2.3.7*): corrige el problema en el que Adobe Commerce genera un error al crear una factura parcial para pedidos realizados con el método de pago *Pago a cuenta* a través de la API de REST.
* **MDVA-37362** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): corrige el problema en el que los valores de opciones de productos configurables y los valores de atributos de variante estaban vacíos en la respuesta de GraphQL.
* **MDVA-37288** (*para Adobe Commerce 2.4.2*): corrige el problema en el cual se devolvieron precios de nivel incorrectos después de la solicitud de GraphQL.
* **MDVA-37225** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*): corrige el problema en el que el proceso de carga se bloquea durante la creación rápida de pedidos cuando hay un valor entero en los SKU importados.
* **MDVA-37224** (*para Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*): corrige el problema en el cual los clientes no pueden pagar la cotización negociable con [!DNL PayFlow Pro] con otro producto en el carro de compras.
* **MDVA-36286** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): corrige el problema en el que la vista previa de los widgets de productos de Page Builder se interrumpe si el mismo SKU tiene una posición diferente en las subcategorías.
* **MDVA-30186** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Corrige el problema por el que las opciones de atributo se ordenan por valor de opción en lugar del recuento de elementos de atributo en la respuesta de GraphQL.

## Versión 1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Commerce >=2.3.0 &lt;=2.4.2*): corrige el problema en el que las opciones personalizadas antiguas permanecen después de cambiarse mediante API.
* **MDVA-35773** (*para Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*): corrige el problema por el que el total general no se muestra como cero en la factura para pedidos con un descuento del 100 %.
* **MDVA-36833** (*para Adobe Commerce 2.4.2*): corrige el problema con los resultados de búsqueda que muestran números aleatorios de productos por página después de excluir algunos productos del catálogo compartido.
* **MDVA-37182** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2*): corrige el problema con la obtención de resultados de búsqueda incorrectos en [!DNL Elasticsearch] versión 6 y versión 7.
* **MDVA-36253** (*para Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*): corrige el problema por el que se muestra un subtotal incorrecto en el minicarrito después de la eliminación del elemento.
* **MDVA-36853** (*para Adobe Commerce 2.4.2*): corrige el problema sin que aparezcan imágenes al cargar galerías de medios grandes.

## Versión 1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*): corrige el problema con los productos agrupados que faltan en las páginas de categoría.
* **MDVA-36615** (*para Adobe Commerce 2.4.2*): corrige el problema con un recuento de productos incorrecto en la cuadrícula de productos de administración.
* **MDVA-36464** (*para Adobe Commerce >=2.4.0 &lt;=2.4.2*): corrige el problema en el que la configuración de las notificaciones de correo electrónico no funciona en el nivel de vista de tienda.
* **MDVA-36138** (*for Adobe Commerce ^2.3.2*) - Fixes the issue where the shipping price is not adjusted and full shipping price is shown to customers if not all items in the cart qualify for the free shipping cart rule.
* **MDVA-36424** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*): corrige el problema en el cual las imágenes multimedia adjuntas a los elementos del generador de páginas desaparecen cuando el contenido se edita repetidamente si la dirección URL base del servidor es diferente de la dirección URL base de la tienda.
* **MDVA-35984** (*para Adobe Commerce ^2.4.0*): corrige el problema con la cantidad de productos incorrecta y la cantidad vendible después de crear varios envíos simultáneos para el mismo producto.

## Versión 1.0.20 {#v1-0-20}

* **MDVA-36170** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): esto corrige el problema en el cual la consulta de GraphQL no está almacenando en caché usando la etiqueta de caché de categoría.
* **MDVA-33168** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): corrige el problema que se producía al actualizar un atributo de producto a través de la API y todos los demás atributos cambian a un valor vacío.
* **MDVA-19640** (*para Adobe Systems Commerce >=2.3.0*) - Corrige el problema por el cual [!DNL Advanced Reporting] no se muestra ningún dato.
* **MDVA-11189** (*para Adobe Systems Commerce >=2.3.0*&lt;2.3.5 ) - Corrige el problema cuando, después de importar un archivo CSV para actualizar el stock de productos, se eliminan las filas de la `cataloginventory_stock` tabla.
* **MDVA-26639** (*para Adobe Systems Commerce >=2.3.3-p1 &lt;2.3.6*) - Corrige el problema por el cual si se crea un nuevo correo electrónico plantilla de confirmación de pedido, los elementos del pedido faltan en el correo del pedido.
* **MDVA-15546** (*para Adobe Systems Commerce >=2.3.0*) - Corrige el problema donde, después de crear un pedido, aparece un *error de columna entity_id donde la cláusula es ambigua* en el registro de excepciones.
* **MDVA-21095** (*para Adobe Systems Commerce >=2.3.0 &lt;2.3.5*): corrige el problema cuando un consulta `INSERT INTO search_tmp` no termina después de una actualización masiva del valor de atributo.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): corrige el problema en el cual las plantillas de correo electrónico no se pueden previsualizar después de habilitar la minificación de JavaScript.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige el problema en el que falla la importación de productos desde un archivo CSV que incluye imágenes de direcciones URL externas.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema que causa que guardar un producto tarde mucho tiempo y que la página se rompa.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*): corrige el problema de la configuración incorrecta de los parámetros de la cookie de SameSite.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*para Adobe Commerce 2.4.1*): corrige el problema en el que Page Builder genera el siguiente error: *Se produjo un error al iniciar Page Builder. Consulte con el contacto de soporte técnico.*
* **MDVA-35356** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema con la devolución incorrecta del crédito de tienda después de la cancelación de pedidos facturados parcialmente.
* **MDVA-33289 (para Adobe Systems Commerce >=2.4.0 &lt;2.4.3 *) - Soluciona el problema por el cual el código JavaScript sin procesar se muestra en la dirección del facturación IU durante el cierre de compra si [!DNL Google Tag Manager] está habilitado.***
* **MDVA-35982** (*para Adobe Systems Commerce >=2.3.0 &lt;2.4.3*) - Corrige el problema por el cual los usuarios administradores restringidos a un sitio web específico no pueden crear un envío para el pedido realizado en el mismo sitio web.
* **MDVA-35155** (*para Adobe Systems Commerce >=2.3.0 &lt;2.3.6*): Soluciona el problema por el que era imposible comprar un producto paquete si se cambiaba el título de la opción.
* **MDVA-35910** (*para Adobe Systems Commerce >=2.4.1 &lt;2.4.3*): Soluciona el problema por el que es imposible crear un nuevo cuenta de cliente después de deshabilitar el funcionalidad de inicio de sesión como cliente.
* **MDVA-34474** (*para Adobe Systems Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema con la adición de un producto a la solicitud lista el uso de la API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema con un cálculo incorrecto de descuento de regla de carro de compras para *Se aplica descuento máximo en cantidad a* y *Paso de descuento en cantidad (comprar X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*): corrige el problema en el que la opción de envío *Recogida en tienda* no aparece, aunque está disponible.
* **MDVA-34928** (*para Adobe Commerce >=2.3.5 &lt;2.3.5-p2*): corrige el problema en el que el cargador de páginas se muestra indefinidamente después de que se elimine el crédito de tienda del pago.
* **MDVA-35254** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*): corrige los problemas con CAPTCHA durante el cierre de compra.
* **MDVA-35569** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema por el que el campo *impuestos fijos sobre productos* no se rellena en la respuesta de GraphQL cuando se especifica el estado.
* **MDVA-35847** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): corrige el problema B2B en el que el formulario Usuarios de la compañía se rompe si se utiliza un atributo de cliente personalizado.
* **MDVA-31307** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): corrige el problema en el que hay *errores de memoria insuficiente* en ciertas categorías debido a problemas con la lista blanca de CSP dinámicos para bloques en caché.

## Versión 1.0.18 {#v1-0-18}

* **MDVA-32655** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el estado de mensaje *en curso* incorrecto al mensaje *completado* correcto para el consumidor `quoteItemCleaner` después de eliminar varios productos.
* **MDVA-34102** (*para Adobe Systems Commerce >=2.3.0 &lt;2.4.3*): corrige el cantidad de Stock predeterminado es cero para los productos deshabilitados en la cuadrícula de productos y Editar páginas de productos en el área de administración.
* **MDVA-35286** (*para Adobe Systems Commerce >=2.4.0 &lt;2.4.2*) - Corrige el problema por el que hay un error si un cliente ha agrupado productos en el carro de compras y cambia de cierre de direcciones múltiples a pago de Onepage.
* **MDVA-35312** (*para Adobe Commerce >=2.4.1-p1 &lt;2.4.2*): corrige el código de respuesta 500 cuando una solicitud de GraphQL está vacía.
* **MDVA-34189** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*): corrige el tiempo de espera del primer byte 503 en consultas [!DNL Visual Merchandiser] al cargar la página Categoría de administración.
* **MDVA-34695** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): corrige `children_count` negativos después de eliminar las categorías.

## Versión 1.0.17 {#v1-0-17}

* **MDVA-34012** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*): corrige el problema en el que la casilla de verificación *Usar valor predeterminado* se borra después de aplicar los cambios programados. El problema aparece una vez que los cambios programados ya no están en vigor.
* **MDVA-35064** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*): corrige el problema en el cual las reescrituras de URL no se generan para productos configurables creados mediante API.
* **MDVA-34943** (*para Adobe Systems Commerce >=2.3.0 &lt;2.4.2*): corrige el problema por el que el pedido rápido almacena en caché los SKU introducidos previamente.
* **MDVA-35197** (*para Adobe Systems Commerce >=2.3.5 &lt;2.4.0*): corrige el problema por el que hay un error al agregar a carro de compras usar GraphQL si los productos agregados anteriormente se agotan.
* **MDVA-34850** (*para Adobe Systems Commerce >=2.3.1 &lt;2.4.0*): Corrige el problema por el que las opciones de falta de existencias de un producto configurable no se muestran en lugar de mostrarse como tachadas.
* **MDVA-34867** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema en el que los valores de un campo de condición establecido para una actualización programada no se guardan.
* **MDVA-35092** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*): corrige el problema en el cual los usuarios no pueden agregar [!DNL Vimeo] vídeos debido a la API [!DNL Vimeo] obsoleta.

## Versión 1.0.16 {#v1-0-16}

* **MDVA-33453** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*): corrige el problema en el que la vista previa del tipo de contenido de productos de Page Builder se interrumpe si los productos coincidentes tienen precios diferentes para cada sitio web.
* **MDVA-32634** (*para Adobe Commerce ^2.3.1*): corrige el problema en el que el `url_path` de la categoría asignada a todo el almacén permanece sin cambios después de mover la categoría en la jerarquía.
* **MDVA-33344** (*para Adobe Systems Commerce ^2.3.0*) - Corrige el problema por el que se utiliza codificado de forma rígida `rma_item` ID de conjunto de atributos predeterminado de entidad en lugar del valor de la base de datos.
* **MDVA-34192** (*para Adobe Systems Commerce >=2.3.4 &lt;2.4.3*): Soluciona el problema en el que es imposible modificar o especificar la fecha de nacimiento del cliente utilizando dd/mm/aaaa formato.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*): corrige la conversión de tipos de ID de almacén a entero para la condición SQL en las colecciones Admin para el usuario administrador con permisos personalizados.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*): corrige el problema en el que la búsqueda no devuelve resultados si el atributo de producto *weight* está configurado como en el que se pueden realizar búsquedas.

## Versión 1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema del pago de [!DNL PayPal Payflow Pro] que falla con un error de formato de lista de parámetros de redireccionamiento.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema por el que el error *No existe esa entidad con addressId* se muestra aleatoriamente en los exploradores de los visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 con extensión B2B*): corrige el problema por el que los catálogos compartidos eliminan los precios de nivel existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*): corrige el problema en el cual generar un abono contra una factura parcial genera impuestos para el pedido total en lugar de impuestos para esa factura parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el error *El countryId proporcionado no existe*.
* **MDVA-33632** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*): proporciona una corrección en la que el mensaje de excepción *Este producto está agotado* se muestra ahora a un usuario administrador al intentar reordenar un producto agotado.
* **MDVA-34469** (*para Adobe Commerce >=2.4.1 &lt;2.4.2*): corrige el problema en el que las mutaciones de GraphQL en el carro de compras de un cliente fallan al usar varias vistas de tiendas.
* **MDVA-33976** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*): corrige el problema en el cual el producto del paquete se muestra Agotado en la tienda después de eliminar la segunda opción del producto del paquete.
* **MDVA-33894** (*para Adobe Commerce >=2.4.0 &lt;2.4.1 con extensión B2B*): corrige varios problemas para la funcionalidad de pedidos rápidos, incluida la adición y eliminación de varios productos y la distinción de mayúsculas y minúsculas de SKU.
* **MDVA-27664** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*): corrige el problema en el formulario de registro de cliente que provocó un error al mostrar: *ERROR - La fecha de nacimiento no debe ser mayor que hoy.*
* **MDVA-33970** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el que hay un signo de moneda incorrecto en la nota de crédito cuando el ámbito del atributo de precio está establecido en sitio web.
* **MDVA-33992** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema de que los precios especiales B2B se muestren incorrectamente durante el cierre de compra.
* **MDVA-34100** (*para Adobe Commerce >=2.3.4 &lt;2.4.2 con extensión B2B*): corrige el problema en el que no se puede crear una cuenta de compañía desde la página de estructura de la compañía.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*para Adobe Systems Commerce >=2.3.3 &lt;2.3.5,>=2.4.0 &lt;2.4.2*) - Corrige el problema con imágenes duplicadas después de la importación de productos desde un archivo CSV.&lt;/2.3.5,>
* **MDVA-33382** (*para Adobe Systems Commerce >=2.3.0 &lt;2.4.2*): corrige los problemas con la invalidación de los indexadores después de la eliminación de productos de una categoría.
* **MDVA-28511** (*para Adobe Systems Commerce >=2.3.5 &lt;2.3.6*): corrige el problema por el que no es posible completar [!DNL PayPal] el cierre de compra si el campo Nombre contiene ciertos caracteres (gustar letras mayúsculas acentuadas).
* **MDVA-31519** (*para Adobe Systems Commerce >=2.3.5 &lt;2.3.6*): Corrige el problema con los tiempos de espera en el cierre de compra de invitado cuando se utiliza un regla de ventas de todo el sitio.
* **MDVA-33281** (*para Adobe Systems Commerce >=2.3.4 &lt;2.3.6*): Corrige el problema por el que hay un error fatal debido `inventory:reservation:list-inconsistencies` a un tipo de parámetro de unidad de almacén incorrecto.
* **MDVA-24201** (*for Adobe Commerce >=2.3.0 &lt;2.3.5*) - Fixes the issue where prices do not reflect the scheduled cart price rule until manually re-indexed.
* **MDVA-32694** (*for Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Fixes the issue where an admin user cannot add a product to a negotiable quote if it is related to a not default store.
* **MDVA-33516** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): corrige el problema en el cual al editar un producto agrupado en una lista de solicitudes se produce un error.
* **MDVA-33975** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige varios problemas relacionados con el cálculo de precios en solicitudes de GraphQL.

## Versión 1.0.13 {#v1-0-13}

* **MDVA-30858** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema con los informes de liquidación de [!DNL PayPal] que no están disponibles en **Informes** > **Ventas** > **[!DNL PayPal]** Acuerdo según lo esperado.
* **MCP-87** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*): se mejoró el tiempo de indexación para los indexadores de productos de categoría y de existencias para perfiles grandes.
* **MDVA-33106** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los cambios de producto reprogramados se borran después de ejecutar el comando cron `run`.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): corrige el problema en el que `analytics_collect_data` está generando un error debido a registros de descripción NULL en la tabla `catalog_category_entity_text`.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige el problema con el error *No existe esa entidad con customerId = 1* en el `exception.log` para clientes que iniciaron sesión después de realizar el pedido.
* **MDVA-23764** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): corrige el error en `JsFooterPlugin.php` que afecta a la visualización de bloques dinámicos.
* **MDVA-13203** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que el error *Infracción de restricción de integridad search_tmp_ table* aparece después de un reíndice completo.
* **MDVA-23426** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*): corrige el problema por el cual los correos electrónicos de notificación enviados por Adobe Commerce contienen un cuerpo en blanco con contenido que se agrega como adjunto.
* **MDVA-22150** (*para Adobe Commerce >=2.3.1 &lt;2.3.4*): corrige el problema en el cual los clientes con un producto configurable en el carro de compras y un cupón aplicado no pueden iniciar sesión si ese producto configurable está deshabilitado en el administrador.
* **MDVA-32545** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el cual las facturas no se envían automáticamente al crear pedidos desde el administrador.
* **MDVA-32714** (*para Adobe Commerce >=2.3.4 &lt;2.4.1*): corrige el problema por el que el precio de grupo de clientes no funciona en la consulta de productos de GraphQL.

## Versión 1.0.12 {#v1-0-12}

* **MDVA-31399** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*) - Agrega el *subtotal (incl. Opción de impuestos)* a las condiciones de regla de precios.
* **MDVA-31236** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): corrige el problema en el cual los administradores con acceso a recursos personalizados no pueden configurar 2FA ni iniciar sesión.
* **MDVA-30845** (*for Adobe Commerce >=2.3.5 &lt;2.3.7*) - Fixes the issue where the *Sorry, no quotes are available for this order at this time* error is displayed when failing to connect to UPS XML/USPS/DHL, and no other shipping method is available.
* **MDVA-32133** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige el problema en el que la galería de medios no se carga desde Page Builder en determinados casos.
* **MDVA-12304** (*para Adobe Commerce >=2.3.0*): aumenta el número máximo de cookies de 50 a 200.
* **MDVA-32632** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): corrige el problema en el que los pedidos aparecen en el sistema de pago, pero no en Adobe Commerce.
* **MDVA-32449** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 con extensión B2B*): corrige el problema en el que el historial de pedidos se carga muy lentamente o no se carga en absoluto.
* **MDVA-32739** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que al habilitar notificaciones asincrónicas por correo electrónico se envían correos electrónicos de ventas antiguos.

## Versión 1.0.11 {#v1-0-11}

* **MC-38509** (*para Adobe Commerce 2.3.6, 2.4.1*): corrige el problema en el que el botón *Crear una cuenta* permanece deshabilitado después de corregir datos no válidos en el formulario *Crear nueva cuenta de cliente*.
* **MDVA-31006** (*para Adobe Systems Commerce 2.3.0, 2.3.1*): Corrige el problema por el cual aparecen pedidos duplicados después de realizar un pedido mediante [!DNL Paypal Express] pago.
* **MDVA-25602** (*para Adobe Systems Commerce 2.3.0*): Corrige problemas con [!DNL PayPal Payflow Pro] el método de pago y el tratamiento de cookies de `SameSite=Lax` forma predeterminada en el Cromo 80 explorador y el redirección de respuesta de API a la inicio de sesión Página del cliente.

## v1.0.10 {#v1-0-10}

Correcciones menores para versiones de parche

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): corrige el problema en el que la regla de precio del carro de compras con cupón no se aplica a través de GraphQL cuando se utiliza la acción *Descuento de cantidad fija para todo el carro de compras*.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que se produce un error después de facturar un paquete con productos virtuales y simples como opciones.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*): mejora el rendimiento de la página de productos en los casos en que se usan reglas de destino o productos vinculados.
* **MDVA-31168** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que el archivo CSV de exportación de productos no aparece y hay un error de asignación de memoria.
* **MDVA-32313** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema en el cual los productos configurables se podían agregar a la lista de deseos con las opciones de configuración incorrectas.
* **MDVA-31759** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el cual los productos no se actualizan con los valores de atributo *dropdown* y *textarea* durante la importación de CSV.
* **MDVA-32012** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema por el que los códigos postales de Corea y Argentina no se pueden validar.
* **MDVA-31640** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*): corrige el problema en el que un precio especial no se puede actualizar mediante la API de REST.
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 con extensión B2B*): corrige el problema en el que hay problemas de rendimiento con la carga de presupuestos negociables mediante la API de REST.

## Versión 1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Commerce >=2.3.0 &lt;2.4.1 con extensión B2B*): corrige el problema por el que se muestra un signo de moneda incorrecto en la cuadrícula de nota de crédito.
* **MDVA-31295** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el cual los puntos de recompensa no se calculan cuando se completa un pedido parcial y los artículos se gravan.
* **MDVA-30112** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el cual si el número de pedidos excede el valor de *tamaño del grupo*, Adobe Commerce considera inconsistencias los pedidos con estado *pendiente*.
* **MDVA-31150** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los saldos de tarjetas de regalo y crédito de tienda no son devueltos por la llamada a la API Rest de facturas de GET, cuando la factura fue registrada por la llamada a la API Rest y el pedido fue pagado parcialmente por las cuentas de tarjeta de regalo y crédito de tienda.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): corrige el problema en el cual los resultados de filtrado de productos configurados para contener solo valores especificados para el ámbito *Todas las vistas de tiendas* en el administrador, incluyen productos con valores anulados en el nivel de vista de tienda.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 con extensión B2B*): corrige el problema por el que *se han enviado desde la dirección incorrecta* *la nueva solicitud de registro de empresa* y se le ha vinculado a una empresa.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*): reemplaza el analizador estándar por un analizador personalizado con un token de palabra clave para el campo SKU en el índice [!DNL ElasticSearch] para que las consultas de búsqueda con comodines funcionen con los SKU que contienen un guion (&quot;-&quot;).

## Versión 1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema por el que el estado del pedido personalizado se cambió a *Procesando* después de la creación parcial del envío mediante WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*): corrige el problema en el cual los clientes no pueden agregar un producto a la lista de deseos si este producto está asignado a un origen de inventario personalizado.
* **MDVA-30594** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el cual no se podía guardar un pedido con varias direcciones durante el cierre de compra cuando se configuraba FTP.
* **MDVA-29148 (para Adobe Systems Commerce >=2.3.0 &lt;2.4.2 *) - Corrige el problema al crear un producto a través de una llamada a la API, el atributo personalizado del producto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` tipo (gustar Multiselect) no utiliza su valor predeterminado si no se proporcionó ningún valor en la carga útil.***
* **MDVA-30837** (*para Adobe Systems Commerce >=2.3.1*&lt;2.3.5 ) - Se ha añadido un ajuste *de configuración Incluir impuestos a la cantidad: Sí/No* en la configuración del método de envío gratuito. Cuando *Incluir impuestos a importe* se establece en *Sí*, Importe mínimo del pedido se calcula como Subtotal + Impuestos. Cuando *Incluir impuestos a importe* se establece en *No*, el Importe mínimo de pedido se calcula como Subtotal
* **MDVA-25028 (para Adobe Systems Commerce >=2.3.2 &lt;2.3.3 ||=&quot;&quot;>=2.3.5 &lt;2.3.6 *) - Soluciona el problema cuando los pedidos que se realizan con [!DNL PayPal Payflow Pro] el estado de Sospecha de fraude cuando se activan filtros de fraude.&lt;/2.3.3>***
* **MDVA-31224** (*para Adobe Systems Commerce >=2.3.3*&lt;2.3.5 ) - Mejora el rendimiento de la `catalog_product_price` operación de reindexación para paquete productos.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): corrige una página en blanco (error) cuando se selecciona *Mostrar todo*. [!DNL Elasticsearch] devuelve una gran lista de id de productos. En este escenario, la cláusula order by se convierte a un formato SQL incorrecto.
* **MDVA-30815** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige el problema por el cual al cambiar la cantidad de resultados de búsqueda que deben mostrarse en la página de resultados de búsqueda, Adobe Commerce muestra una página en blanco. [!DNL Elasticsearch] ahora muestra correctamente los resultados de las páginas de categoría cuando cambia el número de resultados de búsqueda vistos por página.
* **MDVA-30782** (*para Adobe Commerce >=2.3.5 &lt;2.4.2*): corrige el problema en el que se muestra el bloque dinámico independientemente de la regla del carro de compras.
* **MDVA-31021 (para Adobe Systems Commerce >=2.3.0&lt;2.4.2 *): corrige el problema por el que existían problemas de rendimiento en `module-catalog-import-export/Model/Import/Product/Option.php`.*** Si hay más de ~100k registros en la tabla, un nuevo CSV con un solo producto tarda menos de 10 segundos en `catalog_product_option` validarse.
* **MDVA-31007** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige el problema en el cual los atributos de dirección personalizados no se muestran correctamente en la página de detalles de pedidos del área de mi cuenta y del servidor.
* **MDVA-29389** (*para Adobe Systems Commerce >=2.3.0*&lt;2.4.2): corrige el problema con Avanzadas informes donde cronjob `analytics_collect_data` dice: *El puerto debe configurarse dentro host parámetro (gustar localhost:3306).*
* **MDVA-31343** (*para Adobe Systems Commerce >=2.3.4 &lt;2.3.6*): Corrige el problema con la clase `page-layout-category-full-width` body quitada cuando se programa un categoría.
* **MDVA-30945 (para Adobe Systems Commerce >=2.3.0&lt;2.4.2 *) - Corrige el problema por el que recibe un mensaje de error fatal al actualizar los carros`Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.***

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*para Adobe Systems Commerce >=2.3.4&lt;2.4.0*) - Implementa que el mínimo debe coincidir con *funcionalidad y parcial búsqueda para [!DNL Elasticsearch] el* motor. Resuelve problemas con guiones en búsqueda consultas.
* **MDVA-30102** (*para Adobe Systems Commerce >=2.3.2 &lt;=2.4.0*) - Corrige el problema por el que la caché de Redis crece rápidamente ya que las cachés de diseño no tienen TTL.
* **MDVA-30599** (*para Adobe Commerce >=2.3.4 &lt;=2.4.0*): corrige el problema en el cual las comillas de invitado creadas mediante API se marcan incorrectamente como comillas para clientes que iniciaron sesión.
* **MDVA-29446** (*para Adobe Commerce >=2.3.3 &lt;=2.4.0*): corrige el problema en el que el precio del método de envío no aplicable se muestra como cero durante el cierre de compra.
* **MDVA-30357** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*): corrige el problema con las URL de imagen incorrectas que se crean al generar un mapa del sitio mediante cron.
* **MDVA-30565** (*para Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*): corrige el problema por el que se muestra el error *No existe esa entidad con cartid = 0* para el cliente invitado en el cierre de compra de la tienda si el carro de compras persistente está habilitado.
* **MDVA-29787** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0*): corrige el problema en el que la regla de destino para productos relacionados no funciona cuando *es una de* condición que se usa para definir los productos que se van a mostrar.
* **MDVA-30977** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*): corrige el problema con los productos aleatorios que faltan en las categorías después del reíndice.
* **MDVA-28202** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2*): corrige el problema en el que la navegación por capas no filtra correctamente los productos configurables cuando se utiliza MSI.
* **MDVA-28300** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): corrige el problema en el cual la solicitud GQL no refleja los cambios de precio de las reglas de precios de catálogo.
* **MDVA-31006** (*para Adobe Commerce >=2.3.2 &lt;=2.4.2*): corrige el problema en el que aparecen pedidos duplicados después de realizar un pedido mediante el pago de [!DNL Paypal Express].

## Versión 1.0.5 {#v1-0-5}

* **MDVA-30841** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): corrige el problema de la navegación por capas, en el que el valor *No* de los atributos de producto de tipo booleano no se incluía en la navegación por capas si [!DNL Elasticsearch] se utilizaba como motor de búsqueda.
* **MDVA-28191** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where no payment methods are loaded during order creation via the Admin.
* **MDVA-29959** (*for Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 with B2B extension*) - Fixes the issue where restricted admin user with *Companies* permissions is not allowed to delete company account.
* **MDVA-30265** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where shipment tracking link stops working after Invoice creation.
* **MDVA-28409** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): corrige el problema en el que el trabajo cron de `sales_clean_quotes` falla con el error *falta de memoria* cuando el número de comillas caducadas en la base de datos es enorme.
* **MDVA-30593** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema en el que las ofertas que caducaron según la configuración de Duración de la oferta no se limpian.
* **MDVA-30107** (*for Adobe Commerce >=2.3.0 &lt;2.3.6*) - Fixes the issue where store switcher doesn&#39;t work as expected if different base URLs are used for store views.
* **MDVA-28763** (*for Adobe Commerce >=2.3.2 &lt;2.3.4*) - Fixes the issue where product image is getting duplicated after updating product information using REST API more than once.
* **MDVA-30284** (*for Adobe Commerce >=2.3.0 &lt;2.4.2*) - Fixes the issue where Catalog Search indexer fails due to the following *[!DNL Elasticsearch]error: limit of total fields in index has been exceeded.*
* **MDVA-29042** (*for Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 with B2B extension*) - Fixes the issue where Catalog permissions were changed to *Allow* automatically after new product was added to the shared catalog.
* **MDVA-30428** (*for Adobe Commerce >=2.3.3 &lt;2.4.2*) - Fixes the issue where customers cannot add a product to wishlist if this product is assigned to a custom inventory source.
* **MDVA-28661** (*para Adobe Commerce >=2.3.0 &lt;2.4.2 con extensión B2B*): corrige el problema en el que se genera un error en la sección de cuenta de compañía de los usuarios de la compañía después de que se cambie el administrador de la compañía.

## Versión 1.0.4 {#v1-0-4}

* **MDVA-30195** (*para Adobe Commerce 2.3.1 - 2.3.4-p2*): corrige el problema en el que los trabajos cron fallan si el nombre de la base de datos es demasiado largo, lo que da como resultado que las categorías no se actualicen en el front-end.
* **MDVA-30106** (*para Adobe Commerce ^2.3.0*): corrige un problema en el cual durante el cierre de compra los pagos no se cargan con *No se puede leer el error de propiedad &#39;length&#39; de null* en la consola JS.
* **MDVA-28656** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*): corrige el problema en el que, si se realiza un pedido sin información de pago necesaria (por ejemplo, con un descuento del 100%) y se crea una factura para el pedido, el estado del pedido cambia a *Cerrado* en lugar de Completado.
* **MDVA-30209** (*para Adobe Commerce 2.3.0 - 2.3.3-p1*): corrige el problema en el que el grupo de clientes se cambió a predeterminado si el cliente actualizaba la información de su cuenta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el que las etiquetas de opciones de atributos no se traducen correctamente para las consultas de GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): corrige el problema en el cual, después de habilitar el permiso de categoría, la caché de página completa no almacena en caché la página de categoría.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*): corrige el problema en el cual los registros de clientes no se pueden exportar desde la cuadrícula Clientes si existen atributos de cliente personalizados.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): corrige el problema por el que no se envía ningún correo electrónico de confirmación para los pedidos realizados mediante GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4 - 2.3.5-p2*): corrige el problema en el que la comparación de productos genera la página de error 500 si uno de los productos tiene una descripción breve vacía.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*): corrige el problema en el cual no es posible volver a pedir si el pedido original contiene una tarjeta de regalo.
* **MDVA-29965** (*para Adobe Commerce >=2.3.3 &lt;2.4.0*): corrige el problema en el cual los clientes obtienen un error de clave de formulario no válida al agregar un producto al carro de compras.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema B2B en el que no es posible realizar pedidos a través de la API de administración para un producto que está en un catálogo público.
* **MDVA-22469** (*para Adobe Commerce 2.3.2-p2 - 2.3.3-p1*): corrige el problema por el cual después de actualizar a Adobe Commerce 2.3.3, Page Builder no funciona en el panel Administración y algunos archivos JS y CSS no se cargan.
* **MC-35984** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige el problema en el cual los comerciantes no podían interactuar con ningún elemento de página en la página Devoluciones después de crear una etiqueta de envío para una Autorización de devolución de mercancía (RMA).

## Versión 1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Commerce 2.3.0 - 2.3.4*): corrige el problema con el método de pago [!DNL PayPal Payflow Pro] y trata las cookies como `SameSite=Lax` de forma predeterminada en el explorador Chrome 80 y redirecciona la respuesta de API a la página de inicio de sesión del cliente.
* **MDVA-26694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*): corrige el problema con las cachés de productos y catálogos que caducan a diario, aunque se ha programado para que caduquen de forma diferente.
* **MDVA-27825** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): corrige el problema en el que la exportación de grandes cantidades de datos falló debido a una fuga de memoria.
* **MDVA-29085** (*para Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*): corrige el problema B2B en el que no se envían nuevos correos electrónicos de la compañía si la API crea una compañía.
* **MDVA-29344** (*para Adobe Systems Commerce >=2.3.5 &lt;=2.4.0-p1*): corrige el problema por el que Page Builder se atascaba después de copiar texto de un elemento de encabezado a un elemento de texto.
* **MDVA-29835** (*para Adobe Systems Commerce >2.3.1 &lt;2.4.2*): corrige el problema por el que los pedidos de tarjeta regalo contenían dos códigos en lugar de uno.
* **MDVA-30052** (*para Adobe Systems Commerce >=2.3.2-p2 &lt;2.3.5*): corrige el problema por el que los contenido privados (almacenamiento locales) no se rellenaban correctamente, lo que provocaba problemas de rendimiento.
* **MDVA-30131** (*para Adobe Systems Commerce >=2.3.4*&lt;2.3.6 || 2.4.0): corrige el problema con la navegación en capas, donde el ** valor No value for boolean type product attributes no se incluía en el navegación en capas si [!DNL Elasticsearch] se usaba como motor de búsqueda.
* **MDVA-35514** (*para Adobe Systems Commerce >=2.4.0 &lt;2.4.1*): corrige el problema con la creación de una etiqueta de envío y la adición de productos pedidos a un paquete en la ventana modal Paquetes de Crear.
