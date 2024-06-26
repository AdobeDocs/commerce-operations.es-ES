---
title: Notas de la versión
description: Obtenga información acerca de los parches disponibles para Adobe Commerce y los problemas que resuelven.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '20485'
ht-degree: 0%

---

# Notas de la versión

El [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) ofrece parches individuales desarrollados por Adobe y la comunidad de Magento Open Source. Permite aplicar, revertir y ver información general sobre todos los parches individuales disponibles para la versión instalada de Adobe Commerce. Puede aplicar parches a proyectos de Adobe Commerce y de Magento Open Source independientemente de quién lo haya desarrollado. Por ejemplo, puede aplicar un parche desarrollado por la comunidad a proyectos de Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar parches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) para obtener instrucciones sobre cómo aplicar parches a los proyectos de Adobe Commerce. Consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la Guía de actualización de software para revisar una lista completa de parches publicados.

>[!INFO]
>
>Para obtener información acerca de [!DNL quality patches] creado por la Comunidad para el Magento Open Source, consulte las [notas de la versión](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que la variable `mergeCart` La mutación falla con &quot;*Error interno del servidor*&quot; en el [!DNL GraphQL] respuesta al combinar carros de compras de origen y destino que tienen los mismos elementos de paquete.
* **ACSD-56546** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que los productos configurables y agrupados se muestran como **Sin existencias** en la tienda cuando la variable **mostrar fuera de la configuración del producto** es *Desactivado*.
* **ACSD-56635** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que el cliente importado se duplica con la misma dirección de correo electrónico cuando se utiliza una importación con **uso compartido de cuentas** establezca en *Global*.
* **ACSD-56741** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el mensaje de error &quot;*Intentando obtener acceso al desplazamiento de la matriz en un valor de tipo nulo*&quot; que se muestra durante `setup:upgrade` cuando la base de datos contiene un [!DNL MySQL] déclencheur no relacionados con el mecanismo de indexación y [!DNL MView].
* **ACSD-57315** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema cuando se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que [!UICONTROL Fetch] se hace clic en el botón **[!UICONTROL View transaction]** en la pantalla Administrador.
* **ACSD-57337** (para Adobe Commerce >=2.4.4 &lt;2.4.6): corrige el problema en el que un usuario administrador con restricciones de acceso a sitios web específicos puede ver compañías de todos los sitios web de **[!UICONTROL Companies]** rejilla.
* **ACSD-57394** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema de la ordenación incorrecta de productos por varios campos de ordenación en [!DNL GraphQL].
* **ACSD-57565** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que la variable **[!UICONTROL Order]** El panel muestra información de pedido incorrecta hasta que se actualiza el período de tiempo. El panel ahora muestra las estadísticas de pedido correctas en la primera carga.
* **ACSD-57854** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema cuando el producto [!DNL GraphQL] las solicitudes devolvían categorías deshabilitadas en las agregaciones de categorías.
* **ACSD-58008** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que al actualizar una actualización programada se eliminaba la versión anterior de un elemento ensayado si no se especificaba una fecha de finalización.
* Revisiones actualizadas: MDVA-39305-V2, ACSD-48627, ACSD-54965

## Versión 1.1.47 {#v1-1-47}

* **ACSD-55241** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema donde *[!UICONTROL Used]* y *[!UICONTROL Times Used]* Los atributos de muestran valores incorrectos para los cupones generados cuando se utilizan durante el cierre de compra con varias direcciones.
* **ACSD-56760** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que un usuario administrador restringido a un sitio web específico no puede ordenar ni agregar nuevos productos dentro de una categoría en caso de que la tienda web tenga su propia categoría raíz.
* **ACSD-56858** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que los permisos de función de compañía B2B se muestran incorrectamente para un administrador de compañía restringido.
* **ACSD-57074** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que la variable *Sí/No* atributo personalizado con `attrbute_code` comenzando por `price_` no funciona correctamente con la indexación y los productos con estos atributos no están disponibles en el front-end.
* Revisiones actualizadas: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la página de categoría almacena en caché la información no válida cuando cambia la cantidad de existencias, incluso si el producto sigue en existencias.
* **ACSD-54656** (para Adobe Commerce >=2.4.5 &lt;2.4.6): corrige el problema en el que el Recaptcha invisible falla durante el cierre de compra, lo que impide que se realice un pedido.
* **ACSD-55100** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que GraphQL no devuelve más de 10 000 productos en los resultados de búsqueda.
* **ACSD-56621** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que el nombre y los apellidos actualizados no se reflejan en la sección del encabezado de saludos del usuario administrador de la compañía.
* **ACSD-56842** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema por el que faltan los proxies diferidos y las fábricas de proxy diferidos después de ejecutarse `setup:di:compile`.
* **ACSD-57003** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que el estado del pedido se cambia a *[!UICONTROL Complete]* en lugar de cambiarse a *[!UICONTROL Processing]* cuando un pedido se reembolsa parcialmente y se envía parcialmente.
* Revisiones actualizadas: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que un producto configurable se queda sin existencias cuando una actualización programada desactiva uno de los dos productos secundarios.
* **ACSD-56616** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que los productos agrupados se muestran como en stock en la tienda cuando sus productos simples están agotados.
* **ACSD-56515** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que los administradores con permisos de nivel de sitio web no pueden agregar ni editar un bloque dinámico.
* **ACSD-56447** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que, al agregar el mismo producto al carro de compras mediante solicitudes de API web REST paralelas, se generan dos elementos independientes en el carro de compras.
* **ACSD-56415** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que el rendimiento de la indexación de precios parcial se ralentiza debido a un error de `DELETE` consulta cuando la base de datos tiene muchos datos de precios parciales para indexar.
* **ACSD-54965** (para Adobe Commerce >=2.4.5 &lt;2.4.6): corrige el problema en el que la cuadrícula de comercialización visual no muestra las existencias correctas cuando un producto se asigna solo a las existencias personalizadas.
* **ACSD-52824** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que se muestran los botones PayPal Express, Google Pay y Apple Pay a los clientes de la empresa cuando estos métodos de pago están desactivados en la configuración de la empresa.
* Revisiones actualizadas: ACSD-56193

## v1.1.44 {#v1-1-44}

* **ACSD-56790** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que se redirige a un usuario al Panel de administración al ordenar productos de categoría mediante **Mover de Stock a la parte inferior** y la opción `Invalid security or form key. Please refresh the page` El error aparece en la parte superior de la pantalla.
* **ACSD-56280** (para Adobe Commerce >=2.4.4 &lt;2.4.7): corrige el problema en el que el pedido de elementos de un registro de regalos produce una excepción.
* **ACSD-56246** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que se eliminan los datos del atributo de selección múltiple personalizado cuando se activa una actualización programada para un producto.
* **ACSD-56193** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4): corrige el problema por el que la caché de Barnish/Fastly no se actualiza cuando se utiliza un bloque programado en la descripción de categoría mediante Page Builder.
* **ACSD-56158** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que la consulta &quot;carro de compras&quot; devuelve el valor fiscal total para cada regla fiscal.
* **ACSD-56023** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el contenido del widget no se actualiza en la página del CMS cuando la caché está habilitada.
* **ACSD-55427** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que el usuario administrador no puede anular la asignación de un producto de un catálogo compartido desde la página de producto en el Administrador.
* **ACSD-55352** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema por el que, después de crear una nota de crédito parcial con puntos de recompensa del cliente, el estado del pedido cambia a Cerrado y las opciones de nota de crédito desaparecen de la página Pedido del administrador.
* **ACSD-55231** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que no se pueden agregar productos a un carro de compras mediante la funcionalidad de orden rápido.
* **ACSD-54283** (para Adobe Commerce >=2.4.3 &lt;2.4.4): corrige el problema en el que los productos/categorías no asignados al catálogo compartido para el predeterminado (grupo general) siguen incluidos en el mapa del sitio XML.
* Revisiones actualizadas: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema por el que la URL de categoría canónica no se actualiza después de cambiar la URL de categoría.
* **ACSD-53636** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5): corrige el problema en el que el precio normal no se muestra en las páginas de lista de productos para productos configurables que tienen productos secundarios con precios especiales.
* **ACSD-54885** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema con la comprobación de direcciones múltiples cuando el usuario administrador utiliza *Iniciar sesión como cliente* funcionalidad.
* **ACSD-55610** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que un pedido parcialmente cancelado tiene un importe de descuento incorrecto.
* **ACSD-55334** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige las traducciones de etiquetas a través de los diccionarios de traducción en la respuesta de GraphQL.
* **ACSD-54739** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que la condición de estado de stock del producto no se aplica a las reglas de producto relacionadas.
* **ACSD-53925** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el administrador no puede guardar el bloque CMS con el carrusel de productos cuando `catalog_product_price` dimensions-mode está configurado como *sitio web*.
* **ACSD-52714** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha se establece como *d-m-a*.
* **ACSD-55055** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): mejora el rendimiento de carga de atributos de producto en reglas de precios del carro de compras.
* **ACSD-53790** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que se pueden crear varias RMA para un solo producto mediante la API de REST.
* **ACSD-56090** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5): corrige el problema en el que la solicitud de GraphQL responde con los datos de todos los almacenes en lugar de con los datos de almacén solicitados específicamente.
* **ACSD-54983** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que obtener el UID del usuario de la empresa con la solicitud de GraphQL no es posible cuando el estado del usuario se establece en *[!UICONTROL Inactive]*.
* **ACSD-53309** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el impuesto no se aplica completamente en la *[!UICONTROL Regular Price]* etiqueta cuando se selecciona la opción personalizable.
* **ACSD-55305** (para Adobe Commerce >=2.4.4 &lt;2.4.7): corrige el problema en el que la variable *[!UICONTROL Edit Company User]* ventana emergente en **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** La página se congela con un cargador en la pantalla.
* Revisiones actualizadas: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema donde *[!UICONTROL Recently Viewed]* los datos del producto no se actualizan correctamente en la vista de tienda.
* **ACSD-54626** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que no se puede crear una nueva regla de pedido de compra (`createPurchaseOrderApprovalRule`) con el `NUMBER_OF_SKUS` attribute mediante [!DNL GraphQL].
* **ACSD-53845** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el [!DNL MySQL] problema de tiempo de espera de conexión al `consumer max_messages` = 0.
* **ACSD-54890** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema donde `aggregate_sales_report_bestsellers_data` causas [!DNL MySQL] errores debido a `/tmp` el disco no tiene espacio.
* **ACSD-55112** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que la variable *[!UICONTROL Submit review]* se puede hacer clic varias veces sin [!DNL Google reCAPTCHA v3] validación.
* **ACSD-54264** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7): corrige el problema en el que el mensaje de error *&quot;No se puede actualizar el atributo solicitado. ID de fila: &quot;store_id&quot;* aparece cuando un cliente intenta cerrar la compra con una oferta negociable de otra vista de tienda.
* **ACSD-54418** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que se aplica incorrectamente una cantidad fija de descuento a cada producto secundario del paquete al que se le asigna un precio dinámico.
* **ACSD-55238** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): correcciones que guardan el producto vacío *[!UICONTROL Meta Description]*.
* **ACSD-54966** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige la emisión en la que un código de cupón con un uso limitado por cliente no se puede reutilizar si falla el pedido anterior.
* **ACSD-54060** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que un administrador restringido no puede guardar un producto si es hijo de otro producto asignado a un ámbito diferente.
* **ACSD-48910** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): se ha corregido el problema por el que un producto agrupado asignado a varios orígenes se queda sin existencias después de que se factura y envía un pedido, incluso si aún tiene una cantidad distinta de cero.
* **ACSD-55381** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige un error interno del servidor al consultar `configurable_product_option_uid` y `configurable_product_option_value_uid` campos de un [!DNL B2B] *[!UICONTROL Requisition list]* mediante [!DNL GraphQL].
* **ACSD-55628** (para Adobe Commerce >=2.4.4-p2 &lt; 2.4.5 || >=2.4.5-p1 &lt; 2.4.6): corrige la carga de un archivo en el formulario de registro de empresa y reemplaza un archivo para un atributo de cliente en la tienda.
* Revisiones actualizadas: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema que se produce en el carro de compras cuando un producto se elimina del catálogo compartido después de que ya se haya agregado al carro de compras.
* **ACSD-53722** (para Adobe Commerce >=2.4.4 &lt;2.4.7): corrige el problema en el que el precio de las opciones de productos agrupados cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos.
* **ACSD-53643** (para Adobe Commerce >=2.4.3 &lt;2.4.7): corrige el problema en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos desactivados o sin existencias. Se corrige ocultando la variable *[!UICONTROL Place Order]* botón para estos pedidos de compra.
* **ACSD-54067** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el que el vídeo de un producto no se reproduce en un dispositivo móvil.
* **ACSD-55414** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): mejora el rendimiento cuando MariaDB intenta convertir el entity_id de EAV de cadena a entero.
* **ACSD-51819** (para Adobe Commerce >=2.4.4 &lt;2.4.4-p4): corrige el problema en el que se pueden realizar varios pedidos con el mismo ID de oferta.
* **ACSD-53118** (para Adobe Commerce >=2.4.0 &lt;2.4.7): corrige el problema en el que la variable *[!UICONTROL Cart Price Rule]* se aplica mediante un código de cupón mientras el producto tiene un atributo vacío.
* **ACSD-54324** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que la solicitud GraphQL request_lists no tiene en cuenta la configuración de paginación y devuelve todos los resultados.
* Revisiones actualizadas: MDVA-42855-v2

## Versión 1.1.40 {#v1-1-40}

* **ACSD-54680** (para Adobe Commerce >=2.4.0 &lt;2.4.6): corrige el problema en el que no es posible procesar una cotización B2B enviada para un producto con varios orígenes asignados.
* **ACSD-54040** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6): corrige el problema en el que la variable *[!UICONTROL Created]* El campo está en blanco para obtener detalles del pedido cuando los módulos B2B están activados.
* **ACSD-54319** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que el precio del producto muestra cero en la *[!UICONTROL Product in Cart]* informe.
* **ACSD-53378** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): mejora el tiempo de carga de la página de pago para los clientes que tienen libretas de direcciones grandes.
* **ACSD-52657** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema por el que la minicart no se actualiza en la vista de tienda secundaria, que utiliza un subdominio.
* **ACSD-53414** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos.
* **ACSD-54472** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que los clientes de una compañía rechazada aún pueden autenticarse y los clientes de una compañía bloqueada y rechazada pueden realizar pedidos. El parche agrega una validación adicional para los extremos de GraphQL.
* **ACSD-52801** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): añade la opción para realizar una coincidencia parcial al buscar productos en GraphQL.
* **ACSD-55004** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que el validador se bloquea al cargar un archivo de importación más grande que el valor configurado en `php.ini`.
* **ACSD-54989** (para Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7): corrige el problema en el que un administrador de empresa no puede realizar un pedido cuando *[!UICONTROL Enable Purchase Orders]* se establece en *[!UICONTROL Yes]* y *[!UICONTROL Purchase Order]* se establece en *[!UICONTROL No]*.
* **ACSD-54007** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el error *&quot;Clave de matriz indefinida &quot;_scope&quot;&quot;* al importar datos de clientes.
* **ACSD-55031** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el *El tipo &quot;mixto&quot; no puede admitir valores NULL* error durante la compilación.
* **ACSD-54961** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que un usuario administrador restringido no puede actualizar de forma masiva la *Revisión del producto* estado.
* **ACSD-55256** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que solo se muestra correctamente la primera imagen en el regulador de imagen.
* Revisiones actualizadas: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (para Adobe Commerce >=2.4.0 &lt;2.4.7): corrige el problema en el que el historial de saldo de puntos de recompensa se calcula de forma incorrecta tras la caducidad de los puntos de recompensa.
* **ACSD-53583** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): mejora el rendimiento de reindexación parcial para *Productos de categoría* y *Categorías de productos* indexadores.
* **ACSD-54026** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige un mensaje de error incorrecto para una `updateCompanyRole` Solicitud de GraphQL para un usuario no autorizado.
* **ACSD-54106** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5): corrige el problema en el que la ordenación de productos de categoría por nombre para caracteres acentuados turcos es incorrecta.
* **ACSD-52219** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que los filtros guardados de las cuadrículas de administración no funcionan como se espera cuando se cambia con frecuencia entre vistas de marcadores.
* **ACSD-54342** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige un mensaje de error incorrecto *Error en la estructura de datos: los valores están mezclados* al importar un archivo CSV sin datos válidos.
* **ACSD-54660** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): se ha añadido un nuevo atributo de entrada *sort* para ordenar los pedidos de los clientes en GraphQL por `sort_field` y `sort_direction`.
* **ACSD-54776** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema donde no está marcado *[!UICONTROL Use Default Value]* y los valores de campo de producto no predeterminados no se guardan para la segunda vista del sitio web, la tienda y la tienda.
* **ACSD-53998** (para Adobe Commerce y Magento Open Source >=2.4.4-p2 &lt;2.4.5) || >=2.4.5-p1 &lt;2.4.7): corrige el problema en el que un **[!UICONTROL Dynamic Block]** basado en un **[!UICONTROL Customer Segment]** no funciona correctamente después de cerrar sesión en una cuenta de cliente.
* **ACSD-53204** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): correcciones *No se puede guardar el producto.* error al realizar solicitudes simultáneas para añadir imágenes a la galería de productos utilizando `rest/V1/products/<sku>/media` punto final.
* **ACSD-47657** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): Se ha añadido un mecanismo de almacenamiento en caché para credenciales de AWS. Un proveedor de credenciales ahora utiliza la caché de Magento para almacenar en caché las credenciales recuperadas de AWS para la configuración EC2.
* Revisiones actualizadas: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4): corrige el problema en el que los productos asignados a un catálogo compartido no aparecen en la tienda cuando se ejecuta un índice parcial.
* **ACSD-54018** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige los problemas de rendimiento con [!UICONTROL Product List] widget que utiliza un atributo no global en la condición de widget.
* **ACSD-54111** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema de que las imágenes en miniatura del producto no se muestren en la tienda cuando la proporción de aspecto de la imagen de marca de agua no coincide con la imagen del producto.
* **ACSD-47669** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): correcciones *Infracción de restricción de integridad: 1452 No se puede agregar ni actualizar una fila secundaria: falla una restricción de clave externa* error al importar productos en CSV.
* **ACSD-53347** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el indexador de precios tarda demasiado en ejecutarse.
* **ACSD-52287** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema con el estado de orden incorrecto en la cuadrícula de orden archivada cuando la indexación de cuadrícula asincrónica está habilitada.
* **ACSD-52929** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema con las solicitudes redundantes para reindexar los elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico.
* **ACSD-53824** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema donde `UpdateMultiselectAttributesBackendTypes` el parche de datos de migración supera el límite de tamaño de transacción de base de datos durante `setup:upgrade`.

## Versión 1.1.37 {#v1-1-37}

* **ACSD-52613** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que se actualizan las cachés y los índices aunque no se realicen actualizaciones en `Inventory_source` elementos por API de REST.
* **ACSD-51884** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que la ruta de acceso de la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando resize.
* **ACSD-53628** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el informe de pedido de ventas CSV muestra caracteres especiales incorrectos.
* **ACSD-53148** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que dos solicitudes paralelas en GraphQL para agregar el mismo producto configurable al carro de compras generaban dos elementos independientes en el carro de compras con el mismo SKU de producto.
* **ACSD-52606** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que el mensaje de error *Su pedido no está listo para recoger* cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que la imagen no se actualiza en el front-end después de reemplazarla con otra imagen con el mismo nombre.
* **ACSD-53728** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el indexador EAV del producto tarda más en completarse.
* **ACSD-53979** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema de JS que se produce en la página de inicio si el mensaje de bienvenida contiene una comilla simple.
* **ACSD-52085** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que un producto configurable con un precio especial no es visible en el carrusel del producto.
* **ACSD-53795** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema con el tipo de datos no válido en `indexer_update_all_views` trabajo cron.
* **ACSD-52143** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que las opciones personalizadas se eliminan después de importar el producto.
* **ACSD-53750** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el *Tubo roto o conexión cerrada* error durante procesos múltiples `catalog_product_price` reindexe.
* **ACSD-49843** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7): corrige el problema en el que el vínculo de descarga del producto no está disponible después de que el artículo pedido se haya facturado automáticamente mediante el método de pago en línea con el **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** configuración habilitada.
* **ACSD-47054** (para Adobe Commerce >=2.4.2 &lt;2.4.6): corrige el problema por el que el reíndice de vista previa ejecuta el reíndice para todas las tiendas, lo que provoca lentitud.
* Se han añadido nuevas versiones para ACSD-46541, ACSD-47079.
* ACSD-49970-v3 sustituido por ACSD-54095.

## Versión 1.1.36 {#v1-1-36}

* **ACSD-53239** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt; 2.4.6): corrige el problema en el que el indexador de inventario limpia todas las cachés en el modo Actualización programada.
* **ACSD-50887** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que la propiedad de atributos del producto de *[!UICONTROL Use in Search Results Layered Navigation]* se puede establecer en *Sí* sin el *[!UICONTROL Use in search]* opción establecida en *Sí*.
* **ACSD-51846** (para Adobe Commerce y Magento Open Source >=2.4.3-p2 &lt;2.4.6): corrige el *Error interno* problema que se produce porque no se validan todos los niveles de carga útil de la API de REST.
* **ACSD-52906** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que la cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión y que pertenecen al mismo segmento de cliente, lo que provoca un almacenamiento en caché incorrecto para algunas páginas.
* **ACSD-52736** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema en el que una *Regla de precio del carro* que incluye requisitos para la cantidad de productos configurables no funciona según lo esperado.
* **ACSD-47875** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el cual los usuarios administradores no pueden agregar un producto al carro de compras de un cliente desde el Administrador para un ámbito de vista de tienda en particular con administración de inventario.
* **ACSD-53176** (para Adobe Commerce >=2.3.7 &lt;2.4.5): corrige el problema donde *Regla de producto relacionada* con *es uno de* la condición no coincide con los productos.
* **ACSD-51666** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el error *La sesión ha caducado. Inicie sesión de nuevo.* esto sucede después de que un cliente intente iniciar sesión.
* Se han añadido nuevas versiones para MDVA-39305-v2.
* Requisitos actualizados para ACSD-19640.

## Versión 1.1.35 {#v1-1-35}

* **ACSD-51899** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el que la dirección de envío predeterminada en el paso de envío de pago se rellena automáticamente con una dirección de recogida en tienda seleccionada anteriormente.
* **ACSD-52041** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que el mensaje de error: *[ERROR] [!DNL Page Builder] se ha procesado durante 5 segundos sin liberar bloqueos.* aparece en el navegador Chrome al guardar contenido editado con [!DNL Page Builder].
* **ACSD-52095** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema en el que la variable `manage_stock` el valor se ha definido incorrectamente como 0 en el archivo CSV después de la exportación del producto.
* **ACSD-51358** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que al eliminar una actualización programada sin una fecha de finalización se eliminan otras actualizaciones programadas para la misma entidad.
* **ACSD-48070** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que la edición de una actualización programada déclencheur una excepción.
* **ACSD-51890** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que la variable [!UICONTROL Submit review] se puede hacer clic varias veces sin [!DNL Google reCAPTCHA] validación v3.
* **ACSD-51984** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema donde no está marcado *[!UICONTROL Use Default Value]* y *[!UICONTROL non-default product field]* Los valores de no se guardan para el segundo sitio web, tienda y vista de tienda.
* **ACSD-52398** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el error *La cantidad solicitada no está disponible* que se produce al intentar actualizar la cantidad de un producto agrupado en el carro de compras de la tienda.
* **ACSD-52786** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que una condición de regla de catálogo *El SKU es* se aplica a todos los productos que comienzan con el SKU determinado.
* **ACSD-52921** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que se produce un error interno al solicitar detalles del carro de compras a GraphQL cuando hay un producto configurable sin existencias en el carro de compras.
* **ACSD-51683** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que una opción personalizable no se puede agregar al carro de compras mediante GraphQL.
* **ACSD-52133** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que una cuenta de cliente no se puede guardar después de una actualización.
* **ACSD-52202** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que la cantidad comercializable de existencias por defecto cambia incorrectamente a 0 cuando se cambia una existencias por defecto a 0 cant. en el cumplimiento del pedido.
* **ACSD-51265** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema con `catalog_product_price` rendimiento de reindexación cuando hay demasiados productos agrupados en el sistema.
* **ACSD-52831** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que los clientes no pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está activada.
* **ACSD-51845** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que los productos subsiguientes con precios de nivel y diferentes conjuntos de atributos no se pueden actualizar a través de la API de REST masiva asincrónica.
* **ACSD-52815** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que la entrada del campo quantity de un origen no predeterminado solo admite hasta 6 dígitos, a diferencia de 8 para un stock predeterminado.
* **ACSD-51149** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que Importación programadaExport con permisos de catálogo habilitados invalida los indexadores y luego los vaciados de caché por parte de cron.
* **ACSD-50815** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que la cantidad decimal de un producto simple no se puede utilizar para una nueva opción de producto agrupado.
* Versiones actualizadas para ACSD-47803.
* Se ha actualizado el título de ACSD-51892.
* Se ha actualizado ACSD-51379.
* Se ha actualizado ACSD-49970-v2.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que un usuario administrador no se redirige correctamente después de seleccionar una vista de tienda al crear un nuevo pedido en Administración.
* **ACSD-50813** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que el administrador no podía añadir productos agrupados que contuvieran una barra oblicua en el SKU con [!UICONTROL Add Products by SKU] al orden de administración.
* **ACSD-51630** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que una gran cantidad de mensajes del sistema ralentiza la descarga de páginas de administración.
* **ACSD-51853** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.7): corrige el problema en el que los estilos de texto copiados no se aplican al utilizar [!UICONTROL Page Builder].
* **ACSD-52160** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que el resultado de validación del producto frente a la regla de precio del carro de compras no se evaluaba correctamente en función de la condición de regla &quot;Si se ENCUENTRA/NO SE ENCUENTRA un artículo en el carro de compras con Todas/Cualquiera de estas condiciones en true&quot;.
* **ACSD-51636** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema en el que el administrador de la empresa no puede agregar nuevos usuarios desde la sección de cuenta de cliente a pesar de tener todas las funciones y permisos necesarios.
* **ACSD-51739** (para Adobe Commerce >=2.4.6 &lt;2.4.7): corrige el problema en el que se devuelve un error cuando la variable `structure_id` se solicita en una solicitud de GraphQL de CompanyTeam.
* **ACSD-51857** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema en el que el bajo rendimiento del `aggregate_sales_report_bestsellers_data` informe cron sobre large sales_order y `sales_order_item` las tablas de base de datos se debían a la forma en que se escribía la consulta de datos principal.
* **ACSD-48448** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que se produce un problema de condición de carrera durante las cancelaciones de pedidos, que provoca una entrada duplicada en la `inventory_reservation` tabla.
* **ACSD-52689** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.6): corrige el problema en el que las imágenes no se pueden cargar en el almacenamiento de Amazon S3 mediante la API de REST.
* **B2B-2674** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): agregue la capacidad de almacenamiento en caché a la consulta de GraphQL 1customAttributeMetadata1.
* Se han añadido nuevas versiones para ACSD-44938.
* Se han añadido requisitos para ACSD-46988.

## v1.1.33 {#v1-1-33}

* **ACSD-50478** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5): corrige el comando de reversión de la base de datos para un caso en el que el volcado de la base de datos contiene déclencheur y una *delimitador* Comando SQL.
* **ACSD-50512** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el *Error: el vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo.* error que se produce al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.
* **ACSD-50949** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el filtro de precios en la búsqueda avanzada no devuelve los resultados adecuados cuando se utiliza junto con el filtro SKU.
* **ACSD-51645** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el error producido al guardar una nueva regla de precio del carro de compras si la extensión `Magento_OfflineShipping` está deshabilitada.
* **ACSD-50895** (para Adobe Commerce >=2.4.5 &lt;2.4.7): corrige el problema donde [!DNL Google Analytics] 3 Las etiquetas GTM no se activan si [!DNL Google Analytics] 4 La GTM no está configurada.
* **ACSD-51102** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que una regla de catálogo aplicada a un gran número de productos no se indexa correctamente cuando una actualización programada habilita la regla.
* **ACSD-50368** (para Adobe Commerce y Magento Open Source >= 2.4.3 &lt;2.4.5): corrige el problema en el que el cliente `group_id` se ignora cuando se crea un cliente mediante la API de REST asíncrona o la API de REST asíncrona masiva.
* **ACSD-51497** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7): corrige el problema en el que un cliente no puede ordenar una página de catálogo por atributo personalizado del tipo desplegable.
* **ACSD-51408** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt; 2.4.7): corrige el problema en el que el estado del elemento de pedido se establece incorrectamente como *[!UICONTROL Backordered]*.
* **ACSD-51735** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): corrige el problema en el que el estado del elemento de pedido se establece incorrectamente en *[!UICONTROL Ordered]* cuando el stock de productos es *0*.
* **ACSD-51792** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que una página no tiene el evento de impresión cuando [!DNL Google Tag Manager] 4 está activada.
* **ACSD-51471** (para Adobe Commerce >=2.4.3 &lt;2.4.7): corrige el problema en el que un usuario administrador no puede guardar una actualización programada para un producto agrupado que utiliza un producto simple que tiene una actualización programada.
* **ACSD-51700** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el error que se produce al cambiar de vista de tienda en una página de edición de producto descargable en el administrador.
* **ACSD-51120** (para Adobe Commerce >=2.3.7 &lt;2.4.3): corrige el problema en el que la caché de solicitudes de GraphQL GET no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo.
* **ACSD-51240** (para Adobe Commerce >=2.4.4 &lt;2.4.6): corrige el problema en el que falta el archivo cargado si el registro se realiza mediante el formulario de registro de la empresa.
* **ACSD-51907** (para Adobe Commerce >=2.4.2 &lt;2.4.3): corrige el problema en el que un usuario administrador restringido no puede crear una nota de crédito con un reembolso sin conexión.
* **ACSD-52148** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema en el que la variable [!DNL Google V3 reCAPTCHA] El inicio de sesión del administrador falla ocasionalmente.
* **ACSD-51431** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el estado de un indexador es *de trabajo* incluso si no hay nuevas entradas en el registro de cambios.
* **ACSD-51892** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema de rendimiento en el que los archivos de configuración se cargan varias veces.
* ACSD-51114 obsoleto.

## Versión 1.1.32 {#v1-1-32}

* **ACSD-49628** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que la variable [!UICONTROL Page Builder's] varios errores impiden que el administrador guarde un producto sin permisos de contenido.
* **ACSD-51305** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que los productos secundarios configurables sin existencias no están disponibles en la respuesta de GraphQL.
* **ACSD-50621** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema donde [!UICONTROL Tier Prices] para diferentes sitios web en el catálogo compartido no son visibles al intentar editarlos en un entorno de varios sitios web.
* **ACSD-51041** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6): mejora el rendimiento del indexador de precios.
* **ACSD-51379** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema por el que se realizan cambios en el contenido de texto de la página a través de [!UICONTROL Page Builder] no se han guardado.
* **ACSD-49480** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que solo se aplica una regla de precio del carro de compras.
* **ACSD-51230** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que la cuenta de la tarjeta de regalo se elimina cuando se procesa un reembolso parcial de un producto simple a partir de un pedido.
* **ACSD-51238** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): corrige el problema en el que se elimina el origen de inventario al actualizar productos configurables y editar el precio.
* **ACSD-50794** (para Adobe Commerce >=2.4.1 &lt;2.4.7): corrige el problema en el que los detalles del mensaje o el envoltorio de regalo no se actualizan en la base de datos al eliminarlos a través de GraphQL.
* **ACSD-51528** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que la variable *x_forwarded_for* tiene valores nulos en la columna *sales_order* tabla.
* **ACSD-50849** (para Adobe Commerce >=2.4.4 &lt;2.4.6): corrige el problema en el que, al añadir un nuevo producto a la categoría después de borrar la caché, no coinciden las posiciones y selecciones de los productos existentes.
* **ACSD-51294** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que el precio, la cantidad, los impuestos, el envío y los ingresos de GTM/GA se envían como una cadena a [!DNL Google Analytics] y GTM.
* **ACSD-51204** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que un producto totalmente vendido no vuelve a estar disponible después de crear una nota de crédito.
* **ACSD-51291** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.4-p4) || >=2.4.5 &lt;2.4.5-p3): corrige el problema en el que los administradores restringidos con acceso a un sitio web pueden agregar imágenes/vídeos al producto asignado a varios sitios web.
* Se han añadido nuevas versiones para ACSD-50336.
* Se reemplazaron los parches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6): corrige el problema en el que Recaptcha v2 no se vuelve a cargar después de enviar un pago fallido.
* **ACSD-50817** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): optimiza el trabajo de Cron `sales_clean_quotes` para correr más rápido.
* **ACSD-49392** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7): corrige el problema en el que el estado del pedido cambia a cerrado después de un reembolso parcial de un producto agrupado.
* **ACSD-51036** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): corrige el problema en el que las condiciones de carrera durante las llamadas simultáneas a la API de REST dan como resultado una sobrescritura de la información de estado de envío en la [!UICONTROL Items Ordered] tabla.
* **ACSD-50858** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): mejora el rendimiento para cargar el contenido de los titulares.
* Se han añadido nuevas versiones para MDVA-39305-v2, ACSD-45169.
* Se han actualizado los parches ACSD-50260-v2.

## Versión 1.1.30 {#v1-1-30}

* **ACSD-50336** (para Adobe Commerce y Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3): corrige el problema en el que los correos electrónicos de alerta de producto no se envían cuando un producto vuelve a estar en stock o se cambia el precio.
* **ACSD-50367** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que la exportación de direcciones de clientes no funciona cuando se crea un atributo de dirección de cliente de selección múltiple sin valores.
* **ACSD-49877** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que la reproducción automática de vídeo no funciona en dispositivos móviles [!DNL Safari] cuando el vídeo está vinculado directamente a un archivo de vídeo remoto y no a un servicio de streaming.
* **ACSD-50165** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el error *No se puede eliminar el archivo. Advertencia!desvincular: no existe el archivo o directorio* al vaciar la caché de JS/CSS desde el administrador.
* **ACSD-49737** (para Adobe Commerce y Magento Open Source >=2.4.1-p1 &lt;2.4.7): corrige la emisión en la que un cupón se marca incorrectamente como utilizado después de un pago con tarjeta fallido.
* **ACSD-50814** (para Adobe Commerce y Magento Open Source >=2.4.6 &lt;2.4.7): corrige el problema en el que un usuario administrador no puede crear una nota de crédito.
* **ACSD-50116** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que un usuario administrador no puede crear una reescritura de URL para subcategorías de nivel 3 o inferior.
* **ACSD-49513** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5): corrige el problema en el que la sincronización del almacenamiento remoto falla debido a archivos de 0 bytes.
* **ACSD-46683** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que se muestra el precio de envío *Aún no se ha calculado*.
* **ACSD-49129** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que la variable *[!UICONTROL content]* el atributo (código de imagen base64) no se devuelve en `rest/V1/products/sku/media` respuestas de API de medios del producto.
* **ACSD-50276** (para Adobe Commerce >=2.4.0 &lt;2.4.7): corrige el problema en el que el formulario de registro de cliente no funciona en la tienda si se crea un atributo de cliente de selección múltiple.
* **ACSD-50527** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el error que se produce al guardar una página con un bloque dinámico vacío.
* **ACSD-49973** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): mejora el rendimiento de la recuperación de productos agrupados a través de GraphQL.
* **ACSD-51114** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que un producto aleatorio desaparece de los catálogos grandes cuando la indexación asincrónica está habilitada. Mejora el rendimiento de la reindexación asíncrona para catálogos grandes.
* **B2B-2598** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.7): agregue la capacidad de almacenamiento en caché a [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], y [!UICONTROL storeConfig] Consultas de GraphQL.
* Se han añadido nuevas versiones para MDVA-42806, ACSD-48627, ACSD-46815.
* Se han actualizado los metadatos de parches para ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.7): corrige el problema por el que una API envía un correo electrónico listo para recibir cuando el pedido no está listo para recogerse.
* **ACSD-49822** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que las actualizaciones de [!UICONTROL Requisition List] páginas no se reflejan en la [!UICONTROL Print Requisition List].
* **ACSD-48771** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema con la actualización del tipo de contenido de bloque de columnas de la carpeta [!DNL Page Builder] versiones.
* **ACSD-49464** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que las facturas, los envíos y los abonos no se mueven de nuevo del archivo cuando orderId es diferente.
* **ACSD-49773** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que la exportación del producto falla cuando AWS S3 se utiliza como almacenamiento remoto.
* **ACSD-49748** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que no se pueden enviar invitaciones.
* **ACSD-49502** (para Adobe Commerce >=2.4.3 &lt;2.4.7): corrige el problema en el que el vínculo descargable no se actualiza correctamente después de aplicar una actualización de ensayo al producto descargable.
* **ACSD-49527** (para Adobe Commerce >=2.4.2 &lt;2.4.7): corrige el problema en el que los roles de compañía de GraphQL no muestran la paginación correctamente.
* **ACSD-49706** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que se guarda el valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor.
* **ACSD-49835** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que el valor de la casilla Usar valor predeterminado no se guarda correctamente en un nivel de almacén para un atributo de selección múltiple.
* **ACSD-49898** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la cuadrícula de productos emite una excepción cuando un producto agrupado tiene un precio especial que supera los 1000.
* **ACSD-50234** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.5): corrige el problema con el nombre de cliente incorrecto en el correo electrónico de confirmación si se realiza un pedido con [!DNL PayPal].
* **ACSD-49960** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que el filtrado por fecha no funciona para la cuadrícula de pedidos del cliente.
* **ACSD-49849** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema por el que el correo electrónico del cliente se sustituía por [!DNL PayPal] correo electrónico al realizar un pedido con [!DNL PayPal Express] mediante GraphQL.
* **ACSD-49839** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que la estructura y los precios del catálogo compartido generan un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU.
* **ACSD-49970** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el tratamiento incorrecto de los errores de GraphQL cuando [!DNL New Relic] el sistema de informes está activado.
* **ACSD-50260** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que los resultados de búsqueda de productos de GraphQL están limitados solo a 10 000 resultados.
* **ACSD-48813** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que la búsqueda no muestra resultados relevantes en función de la ponderación de búsqueda de los atributos.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.3): corrige el problema en el que una regla de precios de catálogo creada en función del atributo Sí/No no tiene en cuenta el ámbito seleccionado.
* **ACSD-47704** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que el producto agrupado muestra solo el precio de los productos en stock.
* **ACSD-49370** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que la variable *Fecha y hora* el atributo del producto tiene un *FilterMatchTypeInput* escriba en el esquema de GraphQL.
* **ACSD-48807** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.7): corrige el problema en el que las revisiones de producto de los clientes no se filtran por la vista de tienda a través de GraphQL.
* **ACSD-49433** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema por el que la cantidad predeterminada se muestra como subtotal en el carro de compras para la tarjeta de regalo con una cantidad abierta.
* **ACSD-48866** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que se produce un error al solicitar una fuente RSS para categorías.
* **ACSD-48784** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que los precios del segmento de cliente se almacenan incorrectamente en caché entre grupos de clientes.
* **ACSD-48857** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que un usuario no puede guardar los cambios después de editar con Page Builder.
* **ACSD-49065** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que los elementos de oferta no son visibles en la administración si solo se asignan al stock personalizado.
* **ACSD-49179** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema en el que el informe Pedidos muestra importes incorrectos en el caso de monedas diferentes para tiendas diferentes.
* **ACSD-49286** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que un producto se agrega dos veces a un carro de compras cuando hay varios widgets de producto en la página.
* **ACSD-49574** (para Adobe Commerce >=2.4.4 &lt;2.4.7): agrega funcionalidad para admitir actualizaciones de productos de tarjeta de regalo en un carro de compras a través de GraphQL.
* Revisión actualizada: ACSD-48694.

## Versión 1.1.27 {#v1-1-27}

* **ACSD-48362** (para Adobe Commerce >=2.4.1 &lt;2.4.7): corrige el problema en el que se utiliza la dirección de envío predeterminada en lugar de una nueva al realizar un pedido con un presupuesto negociable.
* **ACSD-48059** (para Adobe Commerce >=2.3.7 &lt;2.4.7): corrige el problema en el que los comerciantes no pueden guardar &quot;[!UICONTROL Match product by rule]&quot; en la categoría.
* **ACSD-48216** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7): corrige el problema donde [!UICONTROL AUTO_INCREMENT] de la [!UICONTROL inventory_source_item] incrementos de tabla en la [!UICONTROL UPDATE] operación.
* **ACSD-47908** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.0 &lt;2.4.7): corrige el error &quot;Se espera un valor menor o igual a 0&quot; al seleccionar el origen y la cantidad en el paso de envío durante el cierre de compra.
* **ACSD-49497** (para Adobe Commerce y el Magento Open Source >=2.3.7 &lt;2.4.6): corrige la incidencia en la que un pedido permanece en el estado de procesamiento después del envío y se aplica un reembolso parcial.
* **ACSD-48694** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.3.8) || >=2.4.1 &lt;2.4.7): corrige el problema en el que el error &quot;Se ha solicitado un cambio de estado no válido&quot; impide que un cliente realice un pedido.
* **ACSD-49013** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.7): corrige el problema en el que la confirmación de correo electrónico no se traduce a la configuración regional del sitio web al crear clientes mediante una API masiva.
* **ACSD-48164** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que un administrador restringido no puede guardar un valor de nivel de sitio web.
* **ACSD-48404** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema en el que &quot;Recordar paginación de categoría = Sí&quot; provoca un error al pulsar el botón Atrás del explorador.
* **ACSD-48634** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige los errores de JS en una página de actualización de ensayo cuando &quot;[!UICONTROL Google Analytics Content Experiments]&quot; está habilitado.
* **ACSD-49042** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): corrige el problema en el que un producto con un pedido pendiente infinito no se puede pedir desde la Tienda.
* Revisiones actualizadas: ACSD-48366, ACSD-48661.

## Versión 1.1.26 {#v1-1-26}

* **ACSD-47937** (para Adobe Commerce y Magento Open Source 2.4.4) || >=2.4.5 &lt;2.4.6): corrige el problema en el que las notificaciones de caída de precios no siempre se envían debido al almacenamiento en caché de nivel de aplicación.
* **ACSD-48661** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que si el límite de crédito de la empresa es mayor que 999, el separador de comas impide guardar la empresa debido a un error de validación.
* **ACSD-48773** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.7): corrige el problema por el que la plantilla de correo electrónico de puntos de recompensa se toma de la tienda incorrecta.
* **ACSD-48587** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.7): corrige el problema en el que los caracteres especiales del HTML en las reglas de coincidencia del widget de productos impiden que se muestren los productos coincidentes.
* **ACSD-48212** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema en el que la importación de productos asigna el producto al origen incorrecto.
* **ACSD-47988** (para Adobe Commerce y Magento Open Source >=2.3.7 &lt;2.4.6): corrige el problema en el que la exportación del producto recorta las etiquetas de HTML de la descripción del producto del generador de páginas.
* **ACSD-48366** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la imagen del producto no se muestra en la plantilla de correo electrónico Volver a stock.
* **ACSD-48417** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.7): corrige el problema en el que aparece un error SQL después de crear un cambio de programación para un producto y guardar otro producto.

## Versión 1.1.25 {#v1-1-25}

* **ACSD-48058** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que el reíndice de precios del producto no funciona si el producto del paquete no está asignado a ningún sitio web.
* **ACSD-48262** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que los productos no son visibles en el front-end cuando la configuración Permitir todos los productos por página está establecida en Sí.
* **ACSD-48293** (para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4): corrige el problema en el que los productos compuestos no están disponibles cuando los productos secundarios que se agotaron vuelven a estar disponibles.
* **ACSD-47520** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que los clientes pierden puntos de recompensa cuando se crea una nota de crédito.
* **ACSD-48044** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema de que la aplicación de varias tarjetas regalo a un único pedido con envío múltiple impide que se realicen pedidos.
* **ACSD-48300** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que no se puede crear una devolución si se elimina el producto configurable.
* **ACSD-47910** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige la emisión de pedidos, facturas, envíos y notas de abono que faltan en las respectivas cuadrículas de entidades.
* **ACSD-47292** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que los productos agrupados sin existencias no están disponibles en la respuesta de GraphQL si &quot;mostrar productos sin existencias&quot; está establecido en Sí.
* **ACSD-48234** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema por el que el resultado de la búsqueda en el catálogo muestra un recuento de elementos de categoría incorrecto cuando la opción &quot;mostrar sin existencias&quot; está activada.
* **ACSD-48313** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5): corrige el problema en el que la columna &quot;configurable_variaciones&quot; no se analiza si el valor del atributo contiene una coma. Se utiliza el mismo algoritmo de análisis para &quot;additional_attributes&quot;.
* **ACSD-48627** (para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6): corrige el problema en el que el producto configurable sin existencias causa un error al enviar una solicitud de GraphQL para obtener los detalles del carro de compras.
* Revisión actualizada: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que las URL compatibles con SEO no se generan para los productos que tienen *url_key* atributos anulados en el nivel de vista de tienda.
* **ACSD-46865** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la cuadrícula Envío y Nota de crédito no se rellena cuando la indexación asíncrona está habilitada.
* **ACSD-47004** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que el IVA no se aplica a una dirección de facturación sin ID de IVA.
* **ACSD-47803** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que las muestras de productos configurables sin existencias se muestran como disponibles.
* **ACSD-47137** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): mejora la velocidad de carga de la galería de imágenes cuando la carpeta pub/media es muy grande.
* **ACSD-46770** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema por el que se envían correos electrónicos de pedidos de administración incluso cuando la variable *Confirmación de pedido por correo electrónico* está desmarcada.
* **ACSD-47955** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que GraphQL no muestra correctamente el descuento del carro de compras.
* **ACSD-46617** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que la variable *Continuar a cierre de compra* aparece en gris aunque el subtotal sea mayor que el configurado *Cantidad mínima del pedido*.
* **ACSD-47079** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5): corrige el problema en el que el estado de las existencias de los productos compuestos (paquete, agrupados y configurables) no se actualiza cuando el estado de las existencias de subproductos cambia a través del POST de API de REST /rest/V1/inventory/source-items.
* **ACSD-47336** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): correcciones *Se ha producido un error.* error al descartar las notificaciones en el administrador de Commerce.
* **ACSD-47559** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que el área Vista previa de plantilla de correo electrónico no es totalmente visible.
* **ACSD-47920** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando la variable *Permitir cierre de compra de invitado* está desactivado.
* Parches reemplazados: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que un administrador con acceso restringido a un ámbito específico no puede eliminar críticas de producto.
* **ACSD-47107** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5): corrige el problema en el que el descuento de la regla de precio de catálogo se aplica a las opciones de producto personalizadas.
* **ACSD-47232** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que los cupones con condiciones de peso total no se pueden aplicar en Admin.
* **ACSD-46519** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.6): corrige el problema en el que la solicitud categoryList de GraphQL devuelve un product_count incorrecto para una categoría anclada.
* **ACSD-47027** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige una solicitud de GraphQL updateCompanyRole lenta.
* **ACSD-47666** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que la función de filtrado no funciona en la cuadrícula Administración > Sistema > Permisos > Funciones de usuario > una función > Función > Usuarios.
* **ACSD-47497** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que la pestaña Servicios no está visible en la configuración, en Administración.
* Revisión actualizada: ACSD-47743.
* Parches reemplazados: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3): corrige el _Intentando acceder al desplazamiento de la matriz en el valor del tipo bool_ error al acceder a ciertas rutas de categoría no existentes para productos conocidos en PHP 7.4.
* **ACSD-47332** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que cron falla con un error que solo se comunica al ejecutarse entre las 00:00 y las 00:59 UTC.
* **ACSD-47280** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que la deshabilitación de la función de catálogo compartido en un ámbito específico no funciona correctamente.
* **ACSD-47106** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que un valor no se puede guardar en un nuevo atributo personalizado en una página de creación de empresa.
* Revisión actualizada: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6): corrige el problema en el que un usuario recibe un error al asignar un gran número de fuentes de producto.
* **ACSD-46856** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): mejora el rendimiento al actualizar los precios de nivel mediante Sistema > Configuración > Importar > Precios avanzados.
* **ACSD-46541** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4): corrige el problema en el que un usuario administrador no puede crear una nota de crédito si se elimina un elemento de pedido.
* **ACSD-46581** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que el total de impuestos estimado no se actualiza después de seleccionar un país en el carro de compras.
* **ACSD-46618** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que el widget de lista de productos muestra precios en caché incorrectos para un cliente que ha iniciado sesión.
* **ACSD-46674** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): corrige el problema en el que las opciones personalizadas de un tipo de imagen se muestran como HTML en los correos electrónicos del cliente.
* **ACSD-46988** (para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6): corrige el problema en el que la solicitud de API &quot;currency&quot; de GraphQL devuelve valores NULL para una moneda personalizada.
* **ACSD-47076** (para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5): corrige el problema por el que los vídeos de Vimeo no se pueden reproducir en la tienda.
* **ACSD-45071** (para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4): corrige el problema en el que se agrega el origen predeterminado al producto durante la importación.
* **AC-3023** (para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6): actualice el esquema DHL a la versión 10.0 más reciente.
* Revisiones actualizadas: MDVA-42584.
* Parches reemplazados: MDVA-36572, ACSD-45241.

## Versión 1.1.20 {#v1-1-20}

* **ACSD-46520** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): Corrige el problema en el que un usuario obtiene un estado de pedido incorrecto al ser reembolsado mediante el crédito de tienda.
* **ACSD-46703** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6*): corrige el problema en el que no es posible arrastrar y soltar opciones personalizadas en una página de edición de productos.
* **ACSD-44851** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6*): Corrige el problema que impedía abrir o expandir una categoría con subcategorías.
* **ACSD-46815** (*para Adobe Commerce y Magento Open Source >=2.4.5 &lt;2.4.6*): corrige el problema en el que la solicitud del árbol de categorías está limitada a 20 categorías.
* **ACSD-45675** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.6*): corrige el problema en el que la exportación del producto utiliza nombres de categoría de *Vista de tienda predeterminada* ámbito.
* **ACSD-46869** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.6*): Corrige el problema de que un producto configurable en un carro de compras no se actualiza a través de una *API DE REST DE PUT* solicitud sin cambiar la cantidad del producto.
* **MDVA-42768-V2** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): Corrige el problema en el que el producto configurable muestra el precio normal como *0* cuando *Mostrar fuera de stock* es *Sí*.
* Revisiones actualizadas: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Parche obsoleto: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que la solicitud del árbol de categorías está limitada a 20 categorías.
* **ACSD-45781** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.2*): corrige el problema en el cual el campo de búsqueda de la tienda no se muestra en dispositivos móviles.
* **ACSD-46192** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;2.4.5*): corrige el problema con el uso de `async/bulk/V1/configurable-products/bySku/options` punto final.
* **ACSD-46404** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5*): corrige el problema en el cual un usuario administrador no puede iniciar sesión después de actualizar a 2.4.4.
* Revisiones actualizadas: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## Versión 1.1.18 {#v1-1-18}

* **ACSD-45817** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que una mutación de producto de GraphQL para un almacén específico devuelve todas las variantes configurables, incluidas las que no están asignadas al almacén solicitado.
* **ACSD-46146** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.6*): Corrige el problema por el que se envían dos correos electrónicos de confirmación de pedido después de realizar un pedido desde el administrador.
* **ACSD-45255** (*para Adobe Commerce >=2.4.3 &lt;2.4.6*): corrige una excepción en la página Informe de existencias bajas para un usuario administrador restringido.
* **ACSD-45488** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.6*): corrige el problema en el que un producto configurable con varias fuentes no se devuelve automáticamente a En stock.
* **ACSD-45754** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.6*): Corrige el problema en el que los puntos de Recompensa no se agregan después de aplicar un cupón al carro de compras.
* **ACSD-45849** (*para Adobe Commerce >=2.4.3 &lt;2.4.4*): Corrige el problema por el que los metadatos de vídeo se pierden después de aplicar una actualización de ensayo.
* **ACSD-45257** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.4*): Corrige el problema por el que GraphQL no muestra correctamente un descuento del carro de compras.
* **ACSD-44938** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*): corrige el problema donde `VAT_ID` no se puede aplicar en una solicitud de GraphQL para un usuario invitado.
* Revisiones actualizadas: MDVA-43417.

## Versión 1.1.17 {#v1-1-17}

* **ACSD-45241** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.4*): corrige el problema en el que la cantidad de stock de un producto virtual se calcula de forma incorrecta después de crear una nota de crédito.
* **ACSD-43887** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que se muestran detalles incorrectos en la página de pago de cierre de compra cuando las órdenes de compra para empresas están habilitadas.
* **ACSD-45143** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): corrige el problema en el que las variables `setShippingAddressesOnCart` La mutación no permite definir código de región numérica como *región*.
* **ACSD-44591** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.6*): Corrige el error que se produce cuando se realiza un pedido sin confirmación CAPTCHA.
* **ACSD-45520** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.6*): corrige el problema en el que las opciones de muestra no están preseleccionadas en la página de detalles del producto cuando un usuario edita productos configurables desde el carro de compras.
* **ACSD-45169** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.6*): corrige el problema donde [!DNL Visual Merchandiser] no muestra el stock y el precio correctos para un producto configurable después de aplicar una actualización de ensayo.
* **ACSD-45424** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.6*): corrige el problema en el que se crea una compensación de reserva incorrecta después de un reembolso parcial (nota de crédito).
* **MDVA-42807** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.6*): corrige el problema en el que el signo de moneda personalizado no se muestra en la tienda.
* Revisiones actualizadas: MDVA-42689, AC-3022.

## Versión 1.1.16 {#v1-1-16}

* **MDVA-44703** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema por el que los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido.
* **MDVA-44940** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el error SQL que se produce al guardar la categoría desde el Administrador.
* **MDVA-44562** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.2-p2*): corrige el problema en el que el ID de tienda predeterminado de los artículos de oferta se sobrescribe con el ID de tienda predeterminado, a pesar de la solicitud de GraphQL originada en la vista de tienda no predeterminada.
* **MDVA-43167** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que la acción masiva de la cuadrícula de pedidos de administración no se aplica a varias páginas cuando el usuario administrador selecciona todos los pedidos.
* **MDVA-44044** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.2-p2*): corrige el problema que causaba que un producto no se mostrara en la página de categoría después de asignarse a un nuevo sitio web.
* **MDVA-42509** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.4*): Corrige el problema en el que no se podía cargar un CSV para un pedido rápido, lo que resultaba en una *No se puede enviar la cookie* error.
* Revisiones actualizadas: MDVA-41061, MDVA-42584.
* El prefijo del nuevo [!DNL Quality Patches Tool] los parches se cambiarán de *MDVA* hasta *ACSD* debido a cambios en el proceso interno.

## Versión 1.1.15 {#v1-1-15}

* **MDVA-40961** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige un problema que impedía agregar un elemento adicional al carro de compras cuando la cantidad mínima del artículo ya estaba en el carro de compras.
* **MDVA-44887** (*para Adobe Commerce y Magento Open Source >=2.4.4 &lt;2.4.5*): corrige el *SyntaxError no capturado: Token inesperado &#39;const&#39;* error en el panel de administración.
* **MDVA-43718** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Correcciones *El consumidor no tiene autorización para acceder a %resources.* error que aparece al acceder a un catálogo compartido desde una integración personalizada.
* **MDVA-44660** (*para Adobe Commerce y Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Soluciona el problema donde el carácter de acento grave ``` ` ``` no se ha podido utilizar para el nombre y los apellidos de un cliente.
* **MDVA-40896** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el *Error: TypeError: se pasó el argumento 3 al Magento* error en la API asíncrona de productos por lotes.
* **MDVA-38559** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3*): corrige el */V1/customers/search API* error para clientes con más de una suscripción.
* **MDVA-44533** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.4*): corrige el problema en el que el descuento se aplica incorrectamente a un producto secundario del paquete.
* Revisiones actualizadas: MDVA-41061, MDVA-42269.

## Versión 1.1.14 {#v1-1-14}

* **MDVA-43983** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que los productos de *No visible individualmente* seguirá apareciendo en los resultados de búsqueda avanzada del catálogo.
* **MDVA-44100** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema por el que todos los FTP se asignan al último producto del carro de compras y se restablecen para otros productos.
* **MDVA-43605** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.5*): Corrige el problema por el que los datos de pedidos devuelven valores negativos para los totales de fila al utilizar la API de REST.
* **MDVA-43102** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;2.4.5*): Corrige el problema en el que la cantidad vendible no se actualiza correctamente cuando se realiza un reembolso a través de la API de REST.
* **MDVA-43178** (*para Adobe Commerce y Magento Open Source >=2.4.3-p2 &lt;2.4.5*): corrige el problema en el cual no se puede recuperar un token de cliente para una tienda personalizada en GraphQL.
* **MDVA-43859** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema donde el error *No existe esa entidad con customerId =* se registra cuando un cliente eliminado intenta iniciar sesión.
* **MDVA-44147** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): Corrige el problema en el que una solicitud de GraphQL no devuelve Listas de solicitudes.
* **MDVA-44505** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): Corrige los problemas en los que GraphQL aplica puntos de recompensa no actualiza el total general y en los que el crédito de tienda se aplica varias veces durante la realización del pedido.
* Revisiones actualizadas: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## Versión 1.1.13 {#v1-1-13}

* **MDVA-42969** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): corrige el problema en el que la regla de producto relacionada solo funciona cuando el segmento de cliente está establecido en *Todo*.
* **MDVA-39605** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): corrige el problema en el que el TTL de caché de Redis (fecha de caducidad) tiene un valor incorrecto.
* **MDVA-43862** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.5*): corrige un problema en el cual el cliente no puede actualizar los elementos del carro de compras debido a un GraphQL *Mutación de UpdateCartItems* error.
* **MDVA-43824** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*): Corrige el problema en el que aparece un error al cancelar pedidos con un descuento.
* **MDVA-43451** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): Corrige el problema donde el error *No se ha encontrado el almacén solicitado. Compruebe el almacén e inténtelo de nuevo.* aparece al configurar un catálogo compartido para un sitio web específico.
* **MDVA-43491** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.5*): corrige un problema en el que la etiqueta de imagen base no se actualiza al importar productos para un sitio web de varias tiendas.
* **MDVA-43601** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema de falta de déclencheur después de la reindexación completa.
* **MDVA-42046** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*): corrige el problema en el que se asigna un valor incorrecto a un atributo de producto con un campo de entrada de fecha al actualizar un producto.
* **MDVA-43935** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): Corrige el problema por el que Ampliar venta del producto se muestra dos veces.
* **MDVA-44188** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que los correos electrónicos emitidos por el sistema con `.-` en las direcciones no se envían.
* **MDVA-42283** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige un problema en el que el formato de fecha y hora de la cuadrícula de orden de administración de la configuración regional en francés no es válido.
* Revisiones actualizadas: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Se han añadido parches y metadatos para [!DNL Site-Wide Analysis Tool].

## Versión 1.1.12 {#v1-1-12}

* **MDVA-39713** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.3.6*): corrige el problema en el que el usuario puede editar la hora de inicio de una actualización programada activa.
* **MDVA-42410** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige la emisión en la que los informes de cupones solo muestran la moneda base predeterminada.
* **MDVA-41136** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que la fecha de caducidad del `mage-cache-sessid` no se amplía, lo que provoca la limpieza de datos del cliente.
* **MDVA-39993** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*): corrige el problema en el cual los cambios de inventario realizados a través de la API no se reflejan en la página del producto en el front-end.
* **MDVA-42855** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el cual una nueva dirección de cliente no se guarda en la libreta de direcciones durante el cierre de compra.
* **MDVA-42645** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de tienda está deshabilitada.
* **MDVA-43414** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2*): corrige el error grave de PHP que se produce al ejecutar el `inventory.reservations.updateSalabilityStatus` poner en cola al consumidor con SKU numéricas.
* **MDVA-41628** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.5*): corrige el problema en el cual los usuarios administradores restringidos existentes obtienen acceso a los nuevos recursos cuando se agregan nuevos módulos.
* **MDVA-43348** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que la solicitud GraphQL de tarjeta de regalo muestra un error si `gift_card_options` contain *uid*.
* **MDVA-39546** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema por el que la fecha de inicio de la actualización de ensayo se podía establecer en una fecha anterior a la fecha actual durante la edición.
* **MDVA-42950** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema de que los vídeos no se reproduzcan en la página del producto.
* **MDVA-42689** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que Adobe Commerce emite un *Infracción de restricción de integridad* error al actualizar las categorías de productos durante la importación.
* **MDVA-41229** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el cual las imágenes disponibles en el back-end no se muestran en el front-end después de la importación de productos configurables.
* **MDVA-43731** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema donde *Buscar sinónimos* ya no funciona cuando se agrega un valor en *Términos mínimos que deben cumplirse*.
* **MDVA-43232** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): corrige el problema que causaba que se ordenaran productos en [!DNL Visual Merchandiser] por Precio especial inferior/superior causa un error al guardar la categoría.
* **MDVA-43726** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.3*): corrige el problema en el que la regla de precio de catálogo basada en la coincidencia de atributos de nivel de tienda no se aplica después de una reindexación parcial.
* Revisiones actualizadas: MDVA-36464, MDVA-37478, MDVA-38608.
* Se han añadido parches y metadatos para [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que los atributos de precio del producto no se pueden actualizar para un sitio web específico mediante la API de REST.
* **MDVA-41350** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que se produce una excepción cuando un usuario administrador con acceso restringido agrega un producto fuera del ámbito de su función por SKU en un pedido.
* **MDVA-42269** (*para Adobe Commerce y Magento Open Source >=2.4.3-p1 &lt;2.4.5*): corrige el problema en el cual un usuario administrador no puede iniciar sesión en el administrador debido a la *TypeError: startTime() espera que el parámetro 1 sea una cadena, dado nulo* error.
* **MDVA-40830** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): Corrige el problema por el que el crédito de tienda se aplica varias veces durante la realización del pedido.
* **MDVA-42237** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que un precio especial de producto configurable no se actualiza después de cambios en el precio del subproducto.
* **MDVA-42520** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema en el que la tasa impositiva se aplica dos veces si *Habilitar el comercio transfronterizo* se utiliza.
* Revisiones actualizadas: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Parche obsoleto: MDVA-37725.

## Versión 1.1.10 {#v1-1-10}

* **MDVA-38728** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.4.5*): corrige el problema en el que la actualización masiva de atributos crea una reescritura de URL para el almacén predeterminado solo después de cambiar *Visibilidad del producto*.
* **MDVA-43091** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): Corrige el problema en el cual al solicitar un paquete de producto al administrador en el backend de, se produce el error *No se puede usar la cantidad decimal para este producto*.
* **MDVA-40816** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema en el que las reglas de producto relacionadas muestran productos de categorías no definidas en las condiciones de regla.
* **MDVA-41305** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.5*): corrige el problema en el que la mutación de GraphQL no devuelve opciones de producto configurables después de agregarla a la lista de deseos.
* **MDVA-39181** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el que las reglas de producto relacionadas muestran productos de categorías no definidas en las condiciones de regla.
* **MDVA-42584** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que el estado de stock configurable en el backend no se actualiza después de cambiar la cantidad y el estado de stock mediante Importar o API.
* **MDVA-40175** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.3*): corrige el problema donde *Haga clic para cambiar el método de envío* no muestra los botones de opción para seleccionar los métodos de envío en Admin durante el repedido.
* **MDVA-42768** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.5*): Corrige el problema en el que el producto configurable muestra el precio normal como 0 cuando *Mostrar fuera de stock* es Sí.
* **MDVA-43201** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que se produce un error en el inicio de sesión del cliente al utilizar el atributo DOB con determinadas configuraciones regionales.
* Revisiones actualizadas: MDVA-35092, MDVA-33970.

## Versión 1.1.9 {#v1-1-9}

* **MDVA-38346** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.5*): corrige el problema de los filtros de fecha que no funcionan correctamente cuando la zona horaria de Adobe Commerce es diferente de la del entorno local.
* **MDVA-42657** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el cual el usuario administrador no puede seleccionar categorías en las condiciones del segmento de cliente.
* **MDVA-42806** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema en el que un *Nuevo registro de empresa* se envía un correo electrónico cada vez que se actualiza una empresa existente a través de la API de REST.
* **MDVA-37984** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.5*): corrige el problema en el que las variables [!DNL Visual Merchandiser] *Hacer coincidir producto por regla* La funcionalidad de no filtra correctamente los productos con actualizaciones de ensayo.
* **MDVA-40488** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que los productos configurables con productos secundarios sin existencias no se muestran en su rango de precios correcto.
* **MDVA-42507** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.5*): corrige el problema en el que la caché de página completa se limpia después de aplicar la actualización de ensayo para la regla de carro de compras.
* **MDVA-39163** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.5*): soluciona el problema de que los métodos de envío no están disponibles cuando se registra un nuevo usuario y los productos del carro de compras proceden de la sesión de invitado.
* **MDVA-38626** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.5*): corrige el problema en el que el usuario administrador no puede realizar un pedido en el backend de mediante [!DNL PayPal Payflow Pro] pago.
* **MDVA-38666** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.3.6*): corrige el problema en el que el usuario administrador no puede cambiar las opciones de producto configurables en el carro de compras del cliente.
* **MDVA-38526** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el que el usuario administrador no puede acceder a [!DNL Site-Wide Analysis tool].
* Revisiones actualizadas: MDVA-40101.

## Versión 1.1.8 {#v1-1-8}

* **MDVA-41215** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que los usuarios reciben el error 500 después de configurar el *mage-messages* cookie si ya existe, pero no hay mensajes nuevos.
* **MDVA-41139** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;2.4.4*): corrige el problema en el que los productos configurables quedan sin existencias después de la importación de productos cuando la cantidad de un producto simple es 0 para uno de sus orígenes.
* **MDVA-42326** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*): corrige el problema en el que los clientes reciben un error en el cierre de compra después de un tiempo de espera de sesión, incluso si el carro de compras persistente está habilitado.
* **MDVA-42341** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que las variables `categoryList` La consulta GraphQL no filtra los resultados si una solicitud tiene el encabezado Tienda.
* **MDVA-38393** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple.
* **MDVA-39153** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): Corrige el problema por el que una cantidad de descuento se calcula incorrectamente durante el repedido en el administrador.
* Revisiones actualizadas: MDVA-28993, MDVA-41061, MDVA-35984.

## Versión 1.1.7 {#v1-1-7}

* **MDVA-39711** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.3*): corrige el problema en el cual los usuarios administradores no pueden acceder a la cuadrícula del cliente después de eliminar el sitio web.
* **MDVA-40311** (*para Adobe Commerce y Magento Open Source >=2.4.2-p2 &lt;2.4.4*): corrige el problema en el que los usuarios administradores reciben el mensaje de error *Seguridad o clave de formulario no válidas. Actualice la página* después de iniciar sesión en Admin, si la ruta de Admin personalizada está configurada y la clave secreta está habilitada.
* **MDVA-41631** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el que los usuarios reciben un error al intentar recuperar información de pedidos sin un *telephone* mediante GraphQL.
* **MDVA-27239** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.3.6*): corrige el problema en el que no se muestran los productos de venta cruzada.
* Revisiones actualizadas: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## Versión 1.1.6 {#v1-1-6}

* **MDVA-40550** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.4*): corrige el problema con los productos que faltan en el front-end durante la reindexación.
* **MDVA-40120** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el que la clasificación de GraphQL por DESC/ASC no funciona con productos que tienen la misma relevancia o precio.
* **MDVA-41399** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;2.4.2*): corrige el problema en el cual los usuarios administradores no pueden acceder a *Administrar carro de compras* página si un cliente añade un producto a la lista de deseos.
* **MDVA-40609** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema de ausencia de datos de productos desactivados en la `cataloginventory_stock_status` tabla de índice, mostrando cantidades de producto incorrectas y desactivadas.
* **MDVA-39031** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el cual es posible agregar un producto al carro de compras mediante GraphQL aunque no esté asignado al sitio web de destino.
* **MDVA-41597** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que los usuarios reciben un error al añadir más de un producto configurable al carro de compras mediante GraphQL.
* **MDVA-27456** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.3.7*): corrige el problema en el que los usuarios reciben un error al intentar cargar [!DNL Swagger].
* **MDVA-32776** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.2*): corrige el problema en el que el estado de stock no se actualiza cuando se realiza un pedido, pero no se envía.
* **MDVA-30862** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.0*): corrige el problema con la fecha de pedido incorrecta en la factura de PDF impresa.
* Se ha mejorado la página de índice del [!DNL Quality Patch Tool]. Se ha añadido la búsqueda y el filtrado convenientes para [!DNL quality patches] en la última versión de la herramienta.
* Revisiones actualizadas: MDVA-33382, MDVA-39482.

## Versión 1.1.5 {#v1-1-5}

* **MDVA-41236** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): Corrige el problema en el que es imposible crear una actualización programada nueva o editar una existente para un producto si la fecha de finalización se ha eliminado anteriormente.
* **MDVA-41046** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que hay productos simples con opciones personalizadas disponibles para asignarlos a productos configurables o agrupados.
* **MDVA-40545** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el cual solo se recuperaba el primer nodo de una página aunque hubiera más de un nodo para la misma página.
* **MDVA-41164** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3-p1*): corrige el problema en el que un usuario administrador no puede guardar o editar una compañía con un atributo de cliente personalizado de tipo de archivo o imagen.
* **MDVA-39229** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema que hace que aparezca el siguiente error después de actualizar la regla de catálogo Ensayo Actualización de hora de inicio: *El trabajo cron staging_sync_entities_period tiene un error: no se puede eliminar la actualización activa.*
* **MDVA-40619** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que los cambios en la jerarquía de páginas de CMS causan un error 500 al intentar realizar la edición en línea en una página de CMS.
* **MDVA-41061** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que el estado de las existencias se restablece como comercializable cuando se guarda un producto del administrador.
* **MDVA-31763** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que las reglas de precios de catálogo se revierten (o no se aplican) hasta la reindexación manual.
* **MDVA-37748** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que una consulta de GraphQL devuelve productos no asignados a un catálogo compartido.

## Versión 1.1.4 {#v1-1-4}

* **MDVA-40399** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST.
* **MDVA-40101** (*para Adobe Commerce y Magento Open Source >=2.3.2 &lt;2.4.0*): corrige el problema en el cual los elementos no se eliminan del minicarrito después de una colocación de pedido correcta usando [!DNL PayPal Express] Cierre.
* **MDVA-40401** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*): Corrige el problema en el que el valor de uso de cupones cambia incluso si falla la realización de un pedido.
* **MDVA-40537** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.4.0-p1*): corrige el problema en el que los usuarios reciben un error al crear una vista de tienda si existen varias páginas de CMS con la misma clave URL.
* **MDVA-37725** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.4.3-p1*): corrige el problema en el que los correos electrónicos de pedido asincrónico enviados desde sitios web no predeterminados contienen direcciones URL de logotipo del sitio web predeterminado.
* **MDVA-39482** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*): Corrige el problema de que un producto se quede sin existencias si se importa con una cantidad &quot;0&quot; cuando se activan los pedidos no satisfechos.
* **MDVA-40435** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;2.4.4*): Corrige el problema con un descuento incorrecto en los productos agrupados con precios dinámicos cuando se aplican a través de GraphQL.
* **MC-42528** (*para Adobe Commerce y Magento Open Source >=2.4.3 &lt;=2.4.3-p1*): corrige el problema en el que las variables `categoryList` La consulta GraphQL devuelve las categorías asignadas y no asignadas.
* **MDVA-29400** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*): Corrige el problema con los pedidos duplicados realizados con [!DNL PayPal Express Checkout].
* **MDVA-26005** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.3.5-p2*): Corrige el problema en el que es imposible seleccionar una categoría en un árbol de categorías para las condiciones de regla Precio del carro de compras.
* **MDVA-25631** (*para Adobe Commerce y Magento Open Source >=2.3.3 &lt;=2.3.5-p2*): Mejora el rendimiento para editar y guardar segmentos de clientes que contienen un gran número de clientes.

## Versión 1.1.3 {#v1-1-3}

* **MDVA-40262** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige el problema en el cual las consultas de búsqueda de GraphQL no se muestran en términos de búsqueda populares en Admin.
* **MDVA-40601** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;=2.4.2-p2*): corrige el problema en el que los usuarios reciben un error al intentar obtener información acerca de la categoría modificada por la actualización programada a través de GraphQL.
* **MDVA-37234** (*para Adobe Commerce y Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*): corrige un problema que causaba que, al agregar un elemento al carro de compras varias veces (solicitud paralela) para el mismo SKU, se creara un elemento de línea duplicado para el mismo ID de carro de compras.
* **MDVA-33606** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;=2.4.2-p2*): corrige el problema en el que los usuarios reciben una *Infracción de restricción única* error al guardar una página de CMS asignada a una jerarquía.
* **MDVA-31590** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.1-p1*): corrige el problema en el que los usuarios no pueden actualizar atributos por lotes mediante colas asincrónicas de MySQL.
* **MDVA-36309** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): corrige el problema en el que la búsqueda de productos por atributos es lenta en las cuadrículas de administración.

## Versión 1.1.2 {#v1-1-2}

* **MDVA-38929** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema en el que la factura con FTP muestra un total general incorrecto cuando el pedido se paga desde el crédito del almacén.
* **MDVA-37364** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.3*): corrige el problema en el que el atributo de cliente personalizado de tipo de fecha rompe la interfaz de usuario de cuadrícula del cliente.
* **MDVA-39195** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): corrige el problema donde *Añadir al carro* El botón estaba inactivo en la página de categoría cuando se habilitó el redireccionamiento al carro de compras.
* **MDVA-37115** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;=2.4.2-p2*): corrige el problema en el que un archivo innecesario *Solo quedan 0* el aviso se muestra en la página de productos configurables.
* **MDVA-39521** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*): corrige el problema en el que el usuario no puede establecer direcciones de envío en el carro de compras con un número de teléfono vacío a través de GraphQL.
* **MDVA-39384** (*para Adobe Commerce y Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*): corrige el problema en el que el atributo de cliente personalizado de un usuario de la compañía no se guarda.
* **MDVA-39043** (*para Adobe Commerce y Magento Open Source >=2.3.4 &lt;=2.4.3*): corrige un problema en el cual el usuario administrador con acceso limitado recibe un error al intentar agregar el *Productos* a la página de CMS.
* **MDVA-39966** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*): corrige el problema con la implementación de configuraciones regionales incorrectas.
* **MDVA-38852** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;=2.3.5-p2*): corrige el problema en el que el inventario de catálogo por diseño bloquea las tablas para las actualizaciones que reducen significativamente el rendimiento en casos con varios pedidos paralelos.
* **MDVA-39986** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.3*): corrige el problema en el que el usuario no puede realizar un pedido en Admin en MacOS mediante el explorador Safari.
* **MDVA-38447** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.4*): corrige dos problemas: donde la variable *No visible individualmente* Los productos secundarios configurables se devuelven en la respuesta de GraphQL y optimizan la consulta MySQL para la consulta de productos de GraphQL con el filtro de categoría.
* **MDVA-40134** (*para Adobe Commerce y Magento Open Source >=2.4.2 &lt;2.4.3*): corrige el problema en el que GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado.
* **MDVA-39935** (*para Adobe Commerce y Magento Open Source >=2.4.1 &lt;2.4.4*): corrige el problema en el que GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web.

## Versión 1.1.1 {#v1-1-1}

* **MDVA-36021** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;2.4.4*): corrige el problema en el que las variables *Llamada a una función de miembro getId()* El error se muestra en la página de detalles del pedido en Admin.
* **MDVA-34948** (*para Adobe Commerce y Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*): soluciona el problema de las consultas de larga duración, como `GET_LOCK`.
* **MDVA-39305** (*para Adobe Commerce y Magento Open Source >=2.4.0 &lt;=2.4.2-p1*): corrige el problema en el cual los clientes registrados no pueden iniciar sesión con Google ReCaptcha habilitado.
* **MDVA-37897** (*para Adobe Commerce y Magento Open Source >=2.3.0 &lt;2.4.4*): corrige el problema con una redirección incorrecta cuando un cliente intenta agregar productos con opciones del widget Vistos recientemente.

## Versión 1.1.0 {#v1-1-0}

* Las categorías de parches se introdujeron para mejorar la experiencia del usuario y facilitar la búsqueda de los parches necesarios a los clientes.
* El `patches.json` se ha cambiado el nombre del archivo a `support-patches.json`.
* **MDVA-38799** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema por el que los productos descargables no se guardaban después de crear una actualización de ensayo.
* **MDVA-37592** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): corrige el problema que se producía cuando la ordenación por precio no funcionaba correctamente para los productos con un precio cero asignado al catálogo compartido.
* **MDVA-38827** (*para Adobe Commerce >=2.3.3-p1 &lt;2.4.4*): corrige el problema en el que los clientes reciben un correo electrónico de envío de pedido que contiene un mensaje de error.

## Versión 1.0.26 {#v1-0-26}

* **MDVA-38468** (*para Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*): corrige el error al guardar páginas CMS: *Ya existe un elemento con el mismo ID PAGE_ID*.
* **MDVA-34680** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*): corrige el problema en el que el tiempo de creación de la cuenta del cliente no se filtra correctamente en la cuadrícula de clientes.
* **MDVA-37068** (*para Adobe Commerce >=2.3.1 &lt;2.4.4*): corrige el problema en el que la tasa de impuestos incorrecta se muestra cuando el carro de compras solo tiene productos virtuales.
* **MDVA-38608** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema en el que las tablas temporales no se eliminan cuando el reíndice no termina correctamente.
* **MDVA-38308** (*para Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*): corrige los problemas relacionados con la adición de [!DNL Vimeo] vídeos a productos.

## Versión 1.0.25 {#v1-0-25}

* **MDVA-37916** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*): corrige el problema en el que el cliente no es llevado a la página de confirmación de pago al utilizar [!DNL Paypal Payment Advanced] método.
* **MDVA-37082** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema que se producía al guardar las existencias personalizadas de productos agrupados y hacía que el producto se mostrara sin existencias en el front-end.
* **MDVA-36572** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*): corrige el problema cuando las actualizaciones de notas de abono ya no causan actualizaciones de reservas de productos duplicadas en la base de datos.
* **MDVA-38132** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*): Corrige el problema cuando el panel de administración no está disponible debido a un *demasiadas redirecciones* error.
* **MDVA-38270** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): Corrige el problema por el que faltaba información de la tarjeta de regalo en el total del pedido en GraphQL.

## Versión 1.0.24 {#v1-0-24}

* **MDVA-37779** (*para Adobe Commerce >=2.4.2 &lt;=2.4.4*): corrige el problema que se producía al agregar un producto configurable al carro de compras mediante GraphQL cuando el ID del sitio web no coincide con el ID de la tienda.
* **MDVA-36832** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): corrige el problema de duplicación de imágenes en páginas cuando la anchura de vista es de 768 píxeles.
* **MDVA-37874** (*para Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*): corrige el problema donde *Importe de descuento fijo para todo el carro* se aplica incorrectamente a un paquete de productos que contiene más de una opción.
* **MDVA-37913** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*): corrige el problema de los vínculos descargables que desaparecen si el producto descargable se actualiza mediante una API.
* **MDVA-34330** (*para Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*): corrige el problema en el que los pedidos de la cuadrícula Pedidos no se filtran según la zona horaria de administración.

## Versión 1.0.23 {#v1-0-23}

* **MDVA-37478** (*para Adobe Commerce >=2.3.0 &lt;=2.3.7*): Corrige el problema por el que Adobe Commerce generaba un error al crear una factura parcial para los pedidos realizados con *Pago a cuenta* método de pago mediante la API de REST.
* **MDVA-37362** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*): corrige el problema en el que los valores de opciones de producto configurables y los valores de atributos de variante estaban vacíos en la respuesta de GraphQL.
* **MDVA-37288** (*para Adobe Commerce 2.4.2*): corrige el problema en el que se devolvían precios de nivel incorrectos después de la solicitud de GraphQL.
* **MDVA-37225** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*): corrige el problema en el que el proceso de carga se bloquea durante la creación rápida de pedidos cuando hay un valor entero en los SKU importados.
* **MDVA-37224** (*para Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*): corrige el problema en el que los clientes no pueden pagar la cotización negociable con [!DNL PayFlow Pro] con otro producto en el carro de compras.
* **MDVA-36286** (*para Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*): corrige el problema en el que la previsualización del widget de productos de Page Builder se interrumpe si el mismo SKU tiene una posición diferente en las subcategorías.
* **MDVA-30186** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*): corrige el problema en el que las opciones de atributo se ordenan por valor de opción en lugar del recuento de elementos de atributo en la respuesta de GraphQL.

## Versión 1.0.22 {#v1-0-22}

* **MDVA-36718** (*para Adobe Commerce >=2.3.0 &lt;=2.4.2*): corrige el problema en el que las opciones personalizadas antiguas permanecen después de cambiarse mediante API.
* **MDVA-35773** (*para Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*): Corrige el problema por el que el total general no se mostraba como cero en la factura para pedidos con un descuento del 100 %.
* **MDVA-36833** (*para Adobe Commerce 2.4.2*): corrige el problema con los resultados de búsqueda que muestran números aleatorios de productos por página después de excluir algunos productos del catálogo compartido.
* **MDVA-37182** (*para Adobe Commerce >=2.4.1 &lt;=2.4.2*): corrige el problema de obtención de resultados de búsqueda incorrectos en ambos [!DNL Elasticsearch] versión 6 y versión 7.
* **MDVA-36253** (*para Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*): corrige el problema por el que se muestra el subtotal incorrecto en el minicarrito después de la eliminación del elemento.
* **MDVA-36853** (*para Adobe Commerce 2.4.2*): corrige el problema por el que no aparecían imágenes al cargar galerías de medios grandes.

## Versión 1.0.21 {#v1-0-21}

* **MDVA-34665** (*para Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*): corrige el problema con los productos agrupados que faltan en las páginas de categoría.
* **MDVA-36615** (*para Adobe Commerce 2.4.2*): corrige el problema con el recuento de productos incorrecto en la cuadrícula de productos de administración.
* **MDVA-36464** (*para Adobe Commerce >=2.4.0 &lt;=2.4.2*): corrige el problema en el que la configuración de las notificaciones de correo electrónico no funciona en el nivel de vista de tienda.
* **MDVA-36138** (*para Adobe Commerce ^2.3.2*): soluciona el problema de que el precio de envío no se ajusta y se muestra el precio de envío completo a los clientes si no todos los artículos del carro cumplen los requisitos para la regla de carro de envío gratuito.
* **MDVA-36424** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*): corrige el problema de que las imágenes de medios adjuntas a los elementos del generador de páginas desaparecen cuando el contenido se edita repetidamente si la URL base del servidor es diferente de la URL base de la tienda.
* **MDVA-35984** (*para Adobe Commerce ^2.4.0*): corrige el problema con la cantidad de producto incorrecta y la cantidad vendible después de crear varios envíos simultáneos para el mismo producto.

## Versión 1.0.20 {#v1-0-20}

* **MDVA-36170** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): esto corrige el problema en el que la consulta de GraphQL no se almacena en caché mediante la etiqueta de caché de categoría.
* **MDVA-33168** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): Corrige el problema que se producía al actualizar un atributo de producto mediante API cuando todos los demás atributos cambiaban a un valor vacío.
* **MDVA-19640** (*para Adobe Commerce >=2.3.0*): corrige el problema donde [!DNL Advanced Reporting] no muestra ningún dato.
* **MDVA-11189** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): corrige el problema que se producía tras importar un archivo CSV para actualizar las existencias del producto y las filas del `cataloginventory_stock` se eliminan.
* **MDVA-26639** (*para Adobe Commerce >=2.3.3-p1 &lt;2.3.6*): Corrige el problema por el que, si se crea una nueva plantilla de correo electrónico de confirmación de pedido, los elementos del pedido no aparecen en el correo del pedido.
* **MDVA-15546** (*para Adobe Commerce >=2.3.0*): corrige el problema en el que después de crear una solicitud de *Columna entity_id donde la cláusula es ambigua* el error aparece en el registro de excepciones.
* **MDVA-21095** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): corrige el problema que se producía al enviar una consulta `INSERT INTO search_tmp` no finalizará después de actualizar el valor de atributo masivo.
* **MDVA-23845** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): corrige el problema en el que las plantillas de correo electrónico no se pueden previsualizar después de habilitar la minificación de JavaScript.
* **MDVA-22026** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige el problema en el que falla la importación de productos desde un archivo CSV, incluidas imágenes de direcciones URL externas.
* **MDVA-22383** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema que causaba que tardara mucho tiempo en guardar un producto y se produjeran saltos de página.
* **MC-41359** (*para Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*): corrige el problema de la configuración incorrecta de los parámetros de cookie de SameSite.

## Versión 1.0.19 {#v1-0-19}

* **MDVA-33614** (*para Adobe Commerce 2.4.1*): corrige el problema en el que Page Builder generaba el siguiente error: *Se ha producido un error al iniciar el Page Builder. Consulte con su contacto de asistencia técnica.*
* **MDVA-35356** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema de la devolución de crédito de tienda incorrecta después de la cancelación de pedidos facturados parcialmente.
* **MDVA-33289** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*): corrige el problema en el que el código JavaScript sin procesar se muestra en la interfaz de usuario de la dirección de facturación durante el cierre de compra si [!DNL Google Tag Manager] está activada.
* **MDVA-35982** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema en el que los usuarios administradores restringidos a un sitio web específico no pueden crear un envío para el pedido realizado en el mismo sitio web.
* **MDVA-35155** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): Corrige el problema en el que es imposible comprar un producto agrupado si se cambió el título de la opción.
* **MDVA-35910** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): corrige el problema en el que es imposible crear una nueva cuenta de cliente después de deshabilitar la funcionalidad Iniciar sesión como cliente.
* **MDVA-34474** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): soluciona el problema de añadir un producto a la lista de solicitudes mediante la API.
* **MDVA-34591** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige el problema con un cálculo de descuento incorrecto de la regla de carro de compras para *El descuento de cantidad máxima se aplica a* y *Etapa de cantidad de descuento (comprar X)*.
* **MDVA-33704** (*para Adobe Commerce >=2.4.0 &lt;2.4.3*): corrige el problema en el que las variables *Recogida en tienda* la opción de envío no aparece, aunque se está configurando para que esté disponible.
* **MDVA-34928** (*para Adobe Commerce >=2.3.5 &lt;2.3.5-p2*): corrige el problema en el que el cargador de página se muestra indefinidamente después de que se elimine el crédito de tienda del pago.
* **MDVA-35254** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*): corrige los problemas con CAPTCHA durante el cierre de compra.
* **MDVA-35569** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el que las variables *impuestos fijos sobre productos* el campo no se rellena en la respuesta de GraphQL cuando se especifica el estado.
* **MDVA-35847** (*para Adobe Commerce >=2.4.1 &lt;2.4.3*): Corrige el problema B2B en el que el formulario Usuarios de la compañía se interrumpe si se utiliza un atributo de cliente personalizado.
* **MDVA-31307** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): corrige el problema donde hay *Memoria insuficiente* errores en ciertas categorías debido a problemas con la lista blanca de CSP dinámicos para bloques en caché.

## Versión 1.0.18 {#v1-0-18}

* **MDVA-32655** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige los errores *en curso* estado del mensaje al correcto *complete* mensaje para el consumidor `quoteItemCleaner` después de eliminar varios productos.
* **MDVA-34102** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige que la cantidad de stock predeterminado es cero para los productos desactivados en las páginas Cuadrícula de productos y Editar producto en el área de Administración.
* **MDVA-35286** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): Corrige el problema en el que hay un error si un cliente ha agrupado productos en el carro de compras y cambia de cierre de compra de varias direcciones a cierre de compra de una sola página.
* **MDVA-35312** (*para Adobe Commerce >=2.4.1-p1 &lt;2.4.2*): Corrige el código de respuesta 500 cuando una solicitud de GraphQL está vacía.
* **MDVA-34189** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*): Corrige el tiempo de espera de primer byte de 503 en [!DNL Visual Merchandiser] al cargar la página Categoría de administración.
* **MDVA-34695** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): Correcciones negativas `children_count` después de eliminar las categorías.

## Versión 1.0.17 {#v1-0-17}

* **MDVA-34012** (*para Adobe Commerce >=2.3.1 &lt;2.4.3*): corrige el problema en el que las variables *Usar valor predeterminado* La casilla de verificación de se borra después de aplicar los cambios programados. El problema aparece una vez que los cambios programados ya no están en vigor.
* **MDVA-35064** (*para Adobe Commerce >=2.3.3 &lt;2.4.3*): corrige el problema en el que las reescrituras de URL no se generan para productos configurables creados mediante API.
* **MDVA-34943** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que el pedido rápido almacena en caché los SKU introducidos anteriormente.
* **MDVA-35197** (*para Adobe Commerce >=2.3.5 &lt;2.4.0*): corrige el problema en el que se produce un error al agregar al carro de compras con GraphQL si los productos agregados anteriormente no están disponibles.
* **MDVA-34850** (*para Adobe Commerce >=2.3.1 &lt;2.4.0*): corrige el problema en el que las opciones sin existencias de un producto configurable no se muestran en lugar de mostrarse como tachadas.
* **MDVA-34867** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): corrige un problema en el que los valores de un campo de condición establecido para una actualización programada no se guardan.
* **MDVA-35092** (*para Adobe Commerce >=2.3.5 &lt;2.4.3*): corrige el problema en el que los usuarios no pueden agregar elementos [!DNL Vimeo] vídeos debido a funciones obsoletas [!DNL Vimeo] API.

## Versión 1.0.16 {#v1-0-16}

* **MDVA-33453** (*para Adobe Commerce >=2.3.6 &lt;2.4.3*): corrige el problema en el que la previsualización del tipo de contenido de Productos de Page Builder se interrumpe si los productos coincidentes tienen precios diferentes para cada sitio web.
* **MDVA-32634** (*para Adobe Commerce ^2.3.1*): corrige el problema en el que las variables `url_path` de la categoría asignada a todo el almacén permanece sin cambios después de mover la categoría en la jerarquía.
* **MDVA-33344** (*para Adobe Commerce ^2.3.0*): Corrige el problema en el que el código estaba codificado `rma_item` Se utiliza el ID del conjunto de atributos predeterminado de entidad en lugar del valor de la base de datos.
* **MDVA-34192** (*para Adobe Commerce >=2.3.4 &lt;2.4.3*): Corrige el problema en el que es imposible modificar/especificar la fecha de nacimiento del cliente con el formato dd/mm/aaaa.
* **MDVA-34847** (*para Adobe Commerce ^2.3.0*): Corrige la conversión de tipo de ID de almacén a entero para la condición SQL en colecciones de Administradores para usuarios administradores con permisos personalizados.
* **MDVA-34886** (*para Adobe Commerce ^2.3.2*): corrige el problema en el que la búsqueda no devuelve resultados si *peso* el atributo de producto está configurado como en el que se pueden buscar.

## Versión 1.0.15 {#v1-0-15}

* **MDVA-33559** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema de [!DNL PayPal Payflow Pro] error de formato de lista de parámetros de redireccionamiento al realizar el pago.
* **MDVA-34023** (*para Adobe Commerce >=2.3.0 &lt;2.4.3*): Corrige el problema donde el error *No existe esa entidad con addressId* se muestra de forma aleatoria en los navegadores de los visitantes.
* **MDVA-32759** (*para Adobe Commerce >=2.3.1 &lt;2.4.3 con extensión B2B*): Corrige el problema por el que los catálogos compartidos eliminan los precios de nivel existentes.
* **MDVA-33482** (*para Adobe Commerce ^2.3.5*): corrige el problema en el que la generación de una nota de abono con una factura parcial genera impuestos para el pedido total en lugar de impuestos para esa factura parcial.
* **MDVA-33393** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el error *El countryId proporcionado no existe*.
* **MDVA-33632** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*): Proporciona una corrección en la que el mensaje de excepción *Este producto está agotado* ahora se muestra a un usuario administrador al intentar reordenar un producto sin existencias.
* **MDVA-34469** (*para Adobe Commerce >=2.4.1 &lt;2.4.2*): corrige el problema en el que las mutaciones de GraphQL en el carro de compras de un cliente fallan al usar varias vistas de la tienda.
* **MDVA-33976** (*para Adobe Commerce >=2.3.0 &lt;2.3.7*): Corrige el problema en el que el producto del paquete se muestra Sin existencias en la tienda después de eliminar la segunda opción del producto del paquete.
* **MDVA-33894** (*para Adobe Commerce >=2.4.0 &lt;2.4.1 con extensión B2B*): soluciona varios problemas relacionados con la funcionalidad de pedidos rápidos, incluida la adición y eliminación de varios productos y la distinción entre mayúsculas y minúsculas de SKU.
* **MDVA-27664** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*): corrige el problema en el formulario de registro de cliente, que provocaba que se mostrara un error: *ERROR: la fecha de nacimiento no debe ser posterior a hoy.*
* **MDVA-33970** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el que hay un signo de moneda incorrecto en la nota de crédito cuando el ámbito del atributo de precio se establece en sitio web.
* **MDVA-33992** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema de los precios especiales B2B que se muestran incorrectamente durante el cierre de compra.
* **MDVA-34100** (*para Adobe Commerce >=2.3.4 &lt;2.4.2 con extensión B2B*): corrige el problema en el que no se puede crear una cuenta de compañía desde la página de estructura de la compañía.

## Versión 1.0.14 {#v1-0-14}

* **MDVA-31969** (*para Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*): corrige el problema de las imágenes duplicadas tras la importación de productos desde un archivo CSV.
* **MDVA-33382** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige los problemas con la invalidación de los indexadores después de la eliminación de productos de una categoría.
* **MDVA-28511** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*): corrige el problema en los casos en los que no es posible completar [!DNL PayPal] cierre la compra si el campo Nombre contiene ciertos caracteres (como mayúsculas acentuadas).
* **MDVA-31519** (*para Adobe Commerce >=2.3.5 &lt;2.3.6*): corrige el problema de los tiempos de espera en el cierre de compra de invitados cuando se utiliza una regla de ventas para todo el sitio.
* **MDVA-33281** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*): corrige el problema en el que hay un error grave en `inventory:reservation:list-inconsistencies` debido a un tipo de parámetro de SKU incorrecto.
* **MDVA-24201** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): corrige el problema en el que los precios no reflejan la regla de precios del carro de compras programada hasta que se vuelve a indexar manualmente.
* **MDVA-32694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*): corrige el problema en el cual un usuario administrador no puede agregar un producto a una cotización negociable si está relacionado con una tienda no predeterminada.
* **MDVA-33516** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): corrige un problema que causaba un error al editar un producto agrupado en una lista de solicitudes.
* **MDVA-33975** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige varios problemas relacionados con el cálculo de precios en solicitudes de GraphQL.

## Versión 1.0.13 {#v1-0-13}

* **MDVA-30858** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema con [!DNL PayPal] Los informes de liquidación no están disponibles en **Informes** > **Ventas** > **[!DNL PayPal]** Liquidación según lo esperado.
* **MCP-87** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*): Se ha mejorado el tiempo de indexación para los indexadores de productos de categoría y de existencias para perfiles grandes.
* **MDVA-33106** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los cambios de producto reprogramados se borran después de la activación `run` se ejecuta el comando.
* **MDVA-19391** (*para Adobe Commerce >=2.3.0 &lt;2.3.5*): corrige el problema donde `analytics_collect_data` está generando un error debido a registros de descripción NULL en la `catalog_category_entity_text` tabla.
* **MDVA-20376** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige el problema con *No existe esa entidad con customerId = 1* error en `exception.log` para clientes que iniciaron sesión después de realizar el pedido.
* **MDVA-23764** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): Corrige el error en `JsFooterPlugin.php` que afecta a la visualización de bloques dinámicos.
* **MDVA-13203** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que las variables *Infracción de restricción de integridad search_tmp_ table* El error aparece después de una reindexación completa.
* **MDVA-23426** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*): Corrige el problema por el que los correos electrónicos de notificación enviados por Adobe Commerce contienen un cuerpo en blanco con contenido que se agrega como adjunto.
* **MDVA-22150** (*para Adobe Commerce >=2.3.1 &lt;2.3.4*): Corrige el problema en el que los clientes con un producto configurable en el carro de compras y un cupón aplicado no pueden iniciar sesión si ese producto configurable está deshabilitado en el Administrador.
* **MDVA-32545** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que las facturas no se envían automáticamente al crear pedidos desde el administrador.
* **MDVA-32714** (*para Adobe Commerce >=2.3.4 &lt;2.4.1*): corrige el problema en el que el precio de grupo de clientes no funciona en la consulta de productos de GraphQL.

## Versión 1.0.12 {#v1-0-12}

* **MDVA-31399** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): Añade el *Subtotal (incl. Tax)* opción para las condiciones de regla de precios.
* **MDVA-31236** (*para Adobe Commerce >=2.4.0 &lt;2.4.2*): corrige el problema en el que los administradores con acceso a recursos personalizados no pueden configurar 2FA ni iniciar sesión.
* **MDVA-30845** (*para Adobe Commerce >=2.3.5 &lt;2.3.7*): corrige el problema en el que las variables *Lo sentimos, no hay presupuestos disponibles para este pedido en este momento* Se muestra un error cuando no se puede conectar a UPS XML/USPS/DHL, y no hay ningún otro método de envío disponible.
* **MDVA-32133** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige el problema en el que la galería de medios no se carga desde Page Builder en determinados casos.
* **MDVA-12304** (*para Adobe Commerce >=2.3.0*): Aumenta el número máximo de cookies de 50 a 200.
* **MDVA-32632** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): corrige el problema en el que los pedidos aparecen en el sistema de pago, pero no en Adobe Commerce.
* **MDVA-32449** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 con extensión B2B*): corrige el problema en el que el historial de pedidos se carga muy lentamente o no se carga en absoluto.
* **MDVA-32739** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que al habilitar las notificaciones de correo electrónico asincrónicas se envían correos electrónicos de ventas antiguos.

## Versión 1.0.11 {#v1-0-11}

* **MC-38509** (*para Adobe Commerce 2.3.6, 2.4.1*): corrige el problema en el que las variables *Crear una cuenta* El botón permanece desactivado después de corregir datos no válidos en *Crear nueva cuenta de cliente* formulario.
* **MDVA-31006** (*para Adobe Commerce 2.3.0, 2.3.1*): Corrige el problema en el que aparecen pedidos duplicados después de realizar un pedido utilizando [!DNL Paypal Express] pago.
* **MDVA-25602** (*para Adobe Commerce 2.3.0*): Corrige el problema con [!DNL PayPal Payflow Pro] método de pago y tratamiento de las cookies como `SameSite=Lax` de forma predeterminada, en el explorador Chrome 80 y la respuesta de API redirige a la página de inicio de sesión del cliente.

## Versión 1.0.10 {#v1-0-10}

Correcciones menores para las versiones de parches

## Versión 1.0.9 {#v1-0-9}

* **MDVA-31363** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): Corrige el problema en el que la regla de precio del carro de compras con cupón no se aplica a través de GraphQL cuando *Descuento de cantidad fija para todo el carro* se utiliza la acción.
* **MDVA-30889** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema en el que se produce un error después de facturar un paquete con productos virtuales y simples como opciones.
* **MDVA-31791** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*): mejora el rendimiento de la página de producto en los casos en que se utilizan reglas de destino o productos vinculados.
* **MDVA-31168** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que el archivo CSV de exportación de productos no aparece y hay un error de asignación de memoria.
* **MDVA-32313** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema en el que los productos configurables se podían agregar a la lista de deseos con las opciones de configuración incorrectas.
* **MDVA-31759** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los productos de no se actualizan con *desplegable* y *área de texto* valores de atributo durante la importación de CSV.
* **MDVA-32012** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige un problema en el que los códigos postales de Corea y Argentina no se pueden validar.
* **MDVA-31640** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*): corrige un problema en el que un precio especial no se puede actualizar mediante la API de REST.
* **MDVA-28651** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 con extensión B2B*): corrige el problema en el que hay problemas de rendimiento con la carga de presupuestos negociables mediante la API de REST.

## Versión 1.0.8 {#v1-0-8}

* **MDVA-31242** (*para Adobe Commerce >=2.3.0 &lt;2.4.1 con extensión B2B*): corrige el problema en el que se muestra un signo de moneda incorrecto en la cuadrícula Nota de crédito.
* **MDVA-31295** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*) - Corrige el problema en el que los puntos de recompensa no se calculan cuando se completa un pedido parcial y los artículos se gravan.
* **MDVA-30112** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el que, si el número de pedidos supera el *del mismo tamaño* valor, Adobe Commerce considera los pedidos con *pendiente* estado como incoherencias.
* **MDVA-31150** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que los saldos de crédito y tarjeta regalo de la tienda no se devuelven mediante la llamada a la API Rest de factura de GET, cuando la factura se registró mediante la llamada a la API Rest y el pedido se pagó parcialmente mediante cuentas de crédito y tarjeta regalo de la tienda.
* **MDVA-30963** (*para Adobe Commerce >=2.3.2 &lt;2.4.2*): corrige el problema en el que los resultados de filtrado de productos establecidos en solo contienen valores especificados para *Todas las vistas de tiendas* En el ámbito de administración, incluya productos con valores anulados en el nivel de vista de tienda.
* **MDVA-29954** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 con extensión B2B*): corrige el problema en el que las variables *Nueva solicitud de registro de empresa* y *Se le ha vinculado a una compañía* los correos electrónicos se envían desde una dirección incorrecta.
* **MDVA-28357** (*para Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*): reemplaza el analizador estándar por un analizador personalizado con un token de palabra clave para el campo SKU en la [!DNL ElasticSearch] índice para hacer que las consultas de búsqueda con comodines funcionen con SKU que contengan un guion (&quot;-&quot;).

## Versión 1.0.7 {#v1-0-7}

* **MDVA-30972** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema por el que el estado de pedido personalizado se cambiaba a *Procesando* después de la creación parcial del envío mediante WebApi.
* **MDVA-30428** (*para Adobe Commerce >=2.3.4 &lt;2.3.5*): corrige el problema en el cual los clientes no pueden agregar un producto a la lista de deseos si este producto está asignado a un origen de inventario personalizado.
* **MDVA-30594** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que un pedido con varias direcciones no se podía guardar durante la desprotección cuando se configuraba FTP.
* **MDVA-29148** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema que se producía al crear un producto mediante una llamada de API, el atributo personalizado del producto de `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (como Multiselect) no utiliza su valor predeterminado si no se proporcionó ningún valor en la carga útil.
* **MDVA-30837** (*para Adobe Commerce >=2.3.1 &lt;2.3.5*): Se ha añadido una opción de configuración *Incluir Impuesto a Importe: Sí/No* en la configuración del método de envío gratuito. Cuándo *Incluir impuesto al importe* se establece en *Sí*, el importe mínimo del pedido se calcula como subtotal + impuestos. Cuándo *Incluir impuesto al importe* se establece en *No*, la cantidad mínima del pedido se calcula como subtotal
* **MDVA-25028** (*para Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*): corrige el problema que se producía cuando los pedidos se realizaban utilizando [!DNL PayPal Payflow Pro] no se establecen en el estado de Sospechoso de fraude cuando se activan los filtros de fraude.
* **MDVA-31224** (*para Adobe Commerce >=2.3.3 &lt;2.3.5*): Mejora el rendimiento del `catalog_product_price` operación de reindexación para productos agrupados.
* **MDVA-31321** (*para Adobe Commerce >=2.3.2 &lt;2.3.5*): corrige una página en blanco (error) al *Mostrar todo* está seleccionado. [!DNL Elasticsearch] devuelve una gran lista de id de productos. En este escenario, la cláusula order by se convierte a un formato SQL incorrecto.
* **MDVA-30815** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige un problema por el cual al cambiar la cantidad de resultados de búsqueda que deben mostrarse en la página de resultados de búsqueda, Adobe Commerce muestra una página en blanco. [!DNL Elasticsearch] ahora muestra correctamente los resultados de las páginas de categoría cuando cambia el número de resultados de búsqueda vistos por página.
* **MDVA-30782** (*para Adobe Commerce >=2.3.5 &lt;2.4.2*): corrige el problema en el que el bloque dinámico se muestra independientemente de la regla del carro de compras.
* **MDVA-31021** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que existen problemas de rendimiento en `module-catalog-import-export/Model/Import/Product/Option.php`. Si hay más de ~100k registros en `catalog_product_option` , un nuevo CSV con un solo producto tarda menos de 10 segundos en validarse.
* **MDVA-31007** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige el problema de que los atributos de dirección personalizados no se muestran correctamente en la página de detalles del pedido en el área de mi cuenta y en el backend de.
* **MDVA-29389** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema con los informes avanzados en el que las variables `analytics_collect_data` cronjob dice: *El puerto debe configurarse en el parámetro host (como localhost:3306)*.
* **MDVA-31343** (*para Adobe Commerce >=2.3.4 &lt;2.3.6*): corrige el problema con la clase de cuerpo eliminada `page-layout-category-full-width` cuando se programa una categoría.
* **MDVA-30945** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige un problema por el que recibía un mensaje de error grave al actualizar los carros de compras `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## Versión 1.0.6 {#v1-0-6}

* **MDVA-28993** (*para Adobe Commerce >=2.3.4 &lt;2.4.0*): Implementa el *El mínimo debe coincidir* funcionalidad y búsqueda parcial de [!DNL Elasticsearch] motor. Soluciona problemas con guiones en consultas de búsqueda.
* **MDVA-30102** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*): corrige el problema en el que la caché de Redis crece rápidamente, ya que las cachés de diseño no tienen TTL.
* **MDVA-30599** (*para Adobe Commerce >=2.3.4 &lt;=2.4.0*): corrige el problema en el que las comillas de invitado creadas mediante API se marcan incorrectamente como comillas para los clientes que iniciaron sesión.
* **MDVA-29446** (*para Adobe Commerce >=2.3.3 &lt;=2.4.0*): corrige el problema en el que el precio del método de envío no aplicable se muestra como cero durante el cierre de compra.
* **MDVA-30357** (*para Adobe Commerce >=2.3.2 &lt;=2.4.0*): Corrige el problema con las direcciones URL de imagen incorrectas que se crean al generar un mapa del sitio mediante cron.
* **MDVA-30565** (*para Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*): corrige el problema donde *No existe tal entidad con cartíd = 0* se muestra un error para el cliente invitado en el cierre de compra de la tienda si el carro de compras persistente está habilitado.
* **MDVA-29787** (*para Adobe Commerce >=2.3.0 &lt;=2.4.0*): corrige el problema en el que la regla de destino para productos relacionados no funciona cuando *es uno de* se utiliza la condición para definir los productos que se van a mostrar.
* **MDVA-30977** (*para Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*): corrige el problema con los productos aleatorios que faltan en las categorías después del reíndice.
* **MDVA-28202** (*para Adobe Commerce >=2.3.4 &lt;=2.4.2*): corrige el problema en el que la navegación por capas no filtra correctamente los productos configurables cuando se utiliza MSI.
* **MDVA-28300** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): Corrige el problema en el que la solicitud de GQL no refleja los cambios de precio de las reglas de precios de catálogo.
* **MDVA-31006** (*para Adobe Commerce >=2.3.2 &lt;=2.4.2*): Corrige el problema en el que aparecen pedidos duplicados después de realizar un pedido utilizando [!DNL Paypal Express] pago.

## Versión 1.0.5 {#v1-0-5}

* **MDVA-30841** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): corrige el problema de la navegación por capas, en el que la variable *No* el valor de los atributos de producto de tipo booleano no se incluía en la navegación por capas si [!DNL Elasticsearch] se utilizó como motor de búsqueda.
* **MDVA-28191** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): Corrige el problema de que no se cargan métodos de pago durante la creación de la solicitud a través del administrador.
* **MDVA-29959** (*para Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 con extensión B2B*): corrige el problema en el que el usuario administrador restringido con *Compañías* permissions no tiene permiso para eliminar cuenta de compañía.
* **MDVA-30265** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): Corrige el problema por el que el vínculo de seguimiento de envíos deja de funcionar después de la creación de la factura.
* **MDVA-28409** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): corrige el problema en el que las variables `sales_clean_quotes` el trabajo cron falla con *memoria insuficiente* error cuando el número de comillas caducadas en la base de datos es enorme.
* **MDVA-30593** (*para Adobe Commerce >=2.3.0 &lt;2.3.4*): corrige el problema en el que las ofertas que caducaron según la configuración de Duración de la oferta no se limpian.
* **MDVA-30107** (*para Adobe Commerce >=2.3.0 &lt;2.3.6*): corrige el problema de que el conmutador de tiendas no funciona como se esperaba si se usan direcciones URL base diferentes para las vistas de tiendas.
* **MDVA-28763** (*para Adobe Commerce >=2.3.2 &lt;2.3.4*): corrige el problema en el que la imagen del producto se duplica después de actualizar la información del producto mediante la API de REST más de una vez.
* **MDVA-30284** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): corrige el problema en el que el indexador Búsqueda en el catálogo falla debido a lo siguiente *[!DNL Elasticsearch]error: se ha superado el límite del total de campos en el índice.*
* **MDVA-29042** (*para Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 con extensión B2B*): corrige el problema por el que los permisos de catálogo se cambiaban a *Permitir* automáticamente después de agregar un nuevo producto al catálogo compartido.
* **MDVA-30428** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): corrige el problema en el cual los clientes no pueden agregar un producto a la lista de deseos si este producto está asignado a un origen de inventario personalizado.
* **MDVA-28661** (*para Adobe Commerce >=2.3.0 &lt;2.4.2 con extensión B2B*): corrige el problema en el que se generaba un error en la sección de cuenta de compañía de Usuarios de la compañía después de que se cambiara el administrador de la compañía.

## Versión 1.0.4 {#v1-0-4}

* **MDVA-30195** (*para Adobe Commerce 2.3.1 - 2.3.4-p2*): corrige el problema en el que los trabajos cron fallan si el nombre de la base de datos es demasiado largo, lo que da como resultado que las categorías no se actualicen en el front-end.
* **MDVA-30106** (*para Adobe Commerce ^2.3.0*): corrige un problema en el que durante el cierre de compra los pagos no se cargan con *No se puede leer la propiedad &#39;length&#39; de null* error en la consola JS.
* **MDVA-28656** (*para Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*): Corrige el problema en el que si se realiza un pedido sin información de pago necesaria (por ejemplo, con un descuento del 100 %) y se crea una factura para el pedido, el estado del pedido cambia a *Cerrado* en lugar de Completar.
* **MDVA-30209** (*para Adobe Commerce 2.3.0: 2.3.3-p1*): corrige el problema en el que el grupo de clientes se cambiaba a predeterminado si el cliente actualizaba la información de su cuenta.
* **MDVA-30123** (*para Adobe Commerce >=2.3.4 &lt;2.4.2*): corrige el problema en el que las etiquetas de opciones de atributos no se traducen correctamente para consultas de GraphQL.
* **MDVA-29996** (*para Adobe Commerce >=2.3.3 &lt;2.4.2*): corrige un problema por el cual, después de habilitar el permiso de categoría, la página de categoría no se almacena en caché en la caché de página completa.
* **MDVA-30164** (*para Adobe Commerce >=2.3.1 &lt;2.4.2*): corrige el problema en el que los registros de clientes no se pueden exportar desde la cuadrícula Clientes si existen atributos de cliente personalizados.
* **MDVA-30444** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): Corrige el problema por el que no se envía ningún correo electrónico de confirmación para los pedidos realizados con GraphQL.
* **MDVA-30490** (*para Adobe Commerce 2.3.4: 2.3.5-p2*): corrige el problema en el que la comparación de productos genera la página de error 500 si uno de los productos tiene una descripción breve vacía.
* **MDVA-30232** (*para Adobe Commerce >=2.3.1 &lt;2.4.1*) - Soluciona el problema donde no es posible volver a pedir si el pedido original contiene una tarjeta de regalo.
* **MDVA-29965** (*para Adobe Commerce >=2.3.3 &lt;2.4.0*): corrige el problema en el que los clientes obtienen un error de clave de formulario no válida al agregar un producto al carro de compras.
* **MDVA-30008** (*para Adobe Commerce >=2.3.0 &lt;2.4.2*): Corrige el problema B2B en el que no es posible realizar pedidos a través de la API de administración para un producto que está en un catálogo público.
* **MDVA-22469** (*para Adobe Commerce 2.3.2-p2 - 2.3.3-p1*): Corrige el problema por el que después de actualizar a Adobe Commerce 2.3.3, Page Builder no funciona en el panel de administración y algunos archivos JS y CSS no se cargan.
* **MC-35984** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige un problema en el que los comerciantes no podían interactuar con ningún elemento de página en la página Devoluciones después de crear una etiqueta de envío para una autorización de devolución de mercancía (RMA).

## Versión 1.0.3 {#v1-0-3}

* **MDVA-25602** (*para Adobe Commerce 2.3.0: 2.3.4*): Corrige el problema con [!DNL PayPal Payflow Pro] método de pago y tratamiento de las cookies como `SameSite=Lax` de forma predeterminada, en el explorador Chrome 80 y la respuesta de API redirige a la página de inicio de sesión del cliente.
* **MDVA-26694** (*para Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*): corrige el problema con las cachés de productos y catálogos que caducan a diario, aunque se ha programado para que caduquen de forma diferente.
* **MDVA-27825** (*para Adobe Commerce >=2.3.0 &lt;2.4.1*): corrige el problema en el que la exportación de grandes cantidades de datos fallaba debido a una fuga de memoria.
* **MDVA-29085** (*para Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*): Corrige el problema B2B por el que no se envían nuevos correos electrónicos de la empresa requeridos si la API crea una empresa.
* **MDVA-29344** (*para Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*): Corrige el problema por el que Page Builder se quedaba atascado después de copiar texto de un elemento de encabezado a un elemento de texto.
* **MDVA-29835** (*para Adobe Commerce >2.3.1 &lt;2.4.2*): corrige el problema en el que los pedidos de tarjetas de regalo contenían dos códigos en lugar de uno.
* **MDVA-30052** (*para Adobe Commerce >=2.3.2-p2 &lt;2.3.5*): corrige el problema de que el contenido privado (almacenamiento local) no se rellenaba correctamente, lo que provocaba problemas de rendimiento.
* **MDVA-30131** (*para Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*): corrige el problema de la navegación por capas, en el que la variable *No* el valor de los atributos de producto de tipo booleano no se incluía en la navegación por capas si [!DNL Elasticsearch] se utilizó como motor de búsqueda.
* **MDVA-35514** (*para Adobe Commerce >=2.4.0 &lt;2.4.1*): corrige el problema con la creación de una etiqueta de envío y la adición de productos pedidos a un paquete en la ventana modal Crear paquetes.
