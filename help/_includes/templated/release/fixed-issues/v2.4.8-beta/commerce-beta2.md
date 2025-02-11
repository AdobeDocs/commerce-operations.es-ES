---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Problemas corregidos de Adobe Commerce (versión 2.4.8-beta2)

## Se han corregido problemas en la versión 2.4.8-beta2

Hemos corregido 206 problemas en el código principal de Adobe Commerce 2.4.8. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

* _ACP2E-3236_: La operación asincrónica falla cuando falta el SKU en la carga
   * _Nota de corrección_: las operaciones asíncronas y sincronizadas anteriormente fallaron debido a errores al guardar el producto si falta sku en la carga útil. Después de la corrección, las operaciones de API de rest de guardado de producto asincrónico y sincrónico fallan con un mensaje de excepción relevante.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [NUBE] No se pueden actualizar los precios base mediante la API de REST (el valor de &#39;value_id&#39; en &#39;catalog_product_entity_decimal&#39; no se incrementa correctamente).
   * _Nota de corrección_: Anteriormente a esta corrección, cuando se llamó a rest api /rest/default/V1/products/base-price, el id de incremento se aumentó erróneamente dejando un espacio entre los valores. Después de la corrección, el ID de incremento se incrementa según lo esperado. También se aumentó el rango del campo value_id.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3486_: No se han establecido valores predeterminados para los atributos de fecha y hora con productos RestAPI
   * _Nota de corrección_: Los valores predeterminados ahora se establecen correctamente para los atributos de fecha y hora mediante RestAPI
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### API, carro y cierre de compra

* _ACP2E-3343_: Error crítico 500: Magento\Framework\Webapi\Exception Relacionado con aceptar encabezado HTTP
   * _Nota de corrección_: después de la corrección, no hay ningún problema para especificar el encabezado &quot;Accept&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>

### API, GraphQL

* _ACP2E-3348_: no hay graphQl disponible para suscribirse a las actualizaciones de puntos de recompensa para el cliente
   * _Nota de corrección_: Anteriormente a la corrección, el atributo de cliente premio_advertencia_notificación no se podía actualizar mediante la mutación de GraphQL y la llamada a la API de REST. Ahora se puede actualizar de la misma forma que el atributo de cliente premio_actualizar_notificación.

### Cuenta

* _AC-10886_: actualización de contraseña de administrador.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38352>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: bucle de redireccionamiento cuando la dirección URL está en mayúsculas
   * _Nota de corrección_: El sistema ahora convierte automáticamente los caracteres en mayúsculas de las direcciones URL en minúsculas, lo que evita un bucle de redireccionamiento al acceder a la página principal. Anteriormente, tener caracteres en mayúsculas en la URL de base segura provocaba un bucle de redirección continuo al intentar acceder a la página principal.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38538>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: la casilla de verificación de inclusión de Iniciar sesión como cliente no se puede traducir
   * _Nota de corrección_: el sistema ahora permite que los campos &quot;Casilla de verificación de inclusión de Iniciar sesión como cliente&quot; e &quot;Información de objeto de casilla de verificación de Iniciar sesión como cliente&quot; se establezcan en el ámbito &quot;Vista de tienda&quot;, lo que permite realizar traducciones para distintas vistas de tienda. Anteriormente, estos campos solo se establecían en el ámbito &quot;Sitio web&quot;, lo que impedía las traducciones para vistas de tiendas individuales.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32329>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: Después de iniciar sesión, los productos agregados a la lista de comparación como usuarios invitados no son visibles.
   * _Nota de corrección_: los productos que se agregaron a la lista de comparación de productos antes de iniciar sesión como clientes ahora se conservan después de iniciar sesión.
Anteriormente, después de iniciar sesión, los productos agregados a la lista de comparación como usuarios invitados no eran visibles.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: La configuración de Permitir países causa problemas en las configuraciones de direcciones de clientes
   * _Nota de corrección_: al seleccionar Permitir países, la configuración no influye en los países mostrados fuera del ámbito determinado. Anteriormente, la configuración de Permitir países influía en el atributo de dirección del cliente fuera del ámbito determinado
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: Registro de regalos compartidos muestra la fecha del evento como 1 día antes
   * _Nota de corrección_: la fecha del registro de regalos se muestra correctamente ahora en Storefront

### Cuenta, API, GraphQL

* _ACP2E-3246_: API De Cliente - Número De Errores De Inicio De Sesión No Se Puede Restablecer A 0 Después De Iniciar Sesión Correctamente
   * _Nota de corrección_: Ahora el número de error se restablece a cero en la tabla de entidades del cliente después de que el cliente haya iniciado sesión correctamente a través de los extremos de la API.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Cuenta, IU de administración, B2B

* _ACP2E-3038_: Los usuarios administradores restringidos no siempre pueden ver los catálogos compartidos personalizados
   * _Nota de corrección_: Los usuarios administradores restringidos ahora pueden ver y administrar de manera consistente los clientes y todos los catálogos compartidos a los que están asignados los productos, siempre que tengan acceso al almacén específico. Anteriormente, un usuario administrador restringido con acceso a un almacén determinado no siempre podía ver todos los catálogos compartidos a los que se asignaban los productos o podía ver clientes que no se podían guardar, lo que producía incoherencias en el sistema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>

### Cuenta, carro y cierre de compra

* _AC-2341_: el atributo de dirección de cliente personalizado &quot;select&quot; no se representa para la nueva dirección de cliente
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/34950>

### IU de administración

* _AC-10705_: [Problema] agregar comprobación de permiso para el botón de datos &quot;volver a cargar datos&quot;
   * _Nota de corrección_: El sistema incluye ahora una comprobación de permisos para el botón &quot;Recargar datos&quot;, asegurándose de que solo se muestre y de que los usuarios con los permisos adecuados puedan obtener acceso a él. Anteriormente, el botón &quot;Recargar datos&quot; era visible y se podía hacer clic en él para todos los usuarios, lo que conducía a una página &quot;no permitida&quot; cuando los usuarios hacían clic sin los permisos necesarios.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38283>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38279>
* _AC-13131_: [Advertencia de corrección de problema]: &quot;filtros&quot; de clave de matriz sin definir
   * _Nota de corrección_: el sistema ahora administra escenarios en los que un nuevo usuario aún no ha interactuado con marcadores, lo que impide que se registre una advertencia de &quot;filtros&quot; de clave de matriz no definida. Anteriormente, esta advertencia se registraba cuando un usuario nuevo no había interactuado con los marcadores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39013>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: el archivo csv de importación de productos con caracteres especiales falla debido a cambios de código en el archivo Validate.php
   * _Nota de corrección_: el sistema ahora valida e importa correctamente los archivos CSV del producto que contienen caracteres especiales, lo que permite la transferencia de datos correcta. Anteriormente, al intentar importar un archivo CSV de productos con caracteres especiales, se producía un error que impedía el proceso de importación.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: Cuando el número máximo de solicitudes de restablecimiento de contraseña&quot; está establecido en más de 0, p. ej.: 3 , &quot;Los mensajes de error que exceden el límite se envían antes de alcanzar el límite, es decir, desde la segunda vez
* _AC-13768_: aunque el número máximo de solicitudes de restablecimiento de contraseña&quot; está establecido en 0( deshabilitado) , &quot;Los mensajes de error que sobrepasan el límite se envían desde la segunda vez&quot;
* _AC-7962_: no hay vínculo de envío en los pagos al pagar en la vista de teléfono móvil
   * _Nota de corrección_: El sistema ahora garantiza que los títulos/vínculos de pago y envío y &quot;Revisión y pagos&quot; estén siempre visibles en la parte superior de la página en la vista móvil, lo que permite a los usuarios navegar fácilmente entre los pasos y realizar las correcciones necesarias. Anteriormente, estos títulos o vínculos estaban ocultos en la vista móvil, lo que dificultaba a los usuarios conocer su paso actual o volver a pasos anteriores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36856>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: los comentarios de envío de consulta de pedidos de clientes created_at se devuelven en la zona horaria +0 que no está configurada en la tienda
   * _Nota de corrección_: el sistema ahora muestra correctamente el campo &quot;created_at&quot; de los comentarios de envío en la zona horaria configurada del cliente al utilizar la consulta de pedidos del cliente. Anteriormente, el campo &quot;created_at&quot; se mostraba en la zona horaria +0, independientemente de la configurada por el cliente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36947>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: El estado de la dirección de envío no se actualiza automáticamente
   * _Nota de corrección_: antes de la corrección, la región de dirección de envío (o id de región) no estaba sincronizada con la información de facturación de direcciones. Ahora, tanto la región de la dirección de envío como el ID de región se actualizan correctamente cuando se cambia la información de la dirección de facturación.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: El botón Restablecer no funciona en Agregar/Editar usuario administrador
   * _Nota de corrección_: anteriormente, el botón Restablecer no funcionaba en la página Agregar o editar usuario administrador. Ahora, en el panel Administración en Sistema -> Permisos -> Todos los usuarios, el botón Restablecer funcionará correctamente en la página Agregar/Editar usuario administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3392_: validación dañada para &quot;Cantidad máxima permitida en el carro de compras&quot;
   * _Nota de corrección_: anteriormente, cuando dejamos `Maximum Qty Allowed in Shopping Cart` vacío, no arrojó ninguna excepción, aunque no se acepta un valor vacío aquí. Una vez aplicada esta corrección, al colocar una cadena vacía se producirán excepciones y no se permitirá guardar el producto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problema de IU de vista previa de Pagebuilder] Los botones de la columna Page Builder no se alinean correctamente
   * _Nota de corrección_: los botones de las columnas de Page Builder ahora están correctamente alineados. Anteriormente, se desalineaban dentro de las columnas de Page Builder.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: el informe de productos pedidos no se está exportando. Error 404 en su lugar.
   * _Nota de corrección_: la exportación de informes de productos ordenados a CSV y XML ahora funciona según lo esperado
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: Error de TinyMCE JS en la consola tras habilitar la minificación de Js con el modo de producción
   * _Nota de corrección_: Anteriormente, al habilitar la minificación de JavaScript en el modo de producción dentro del panel de administración, aparecían errores de JavaScript relacionados con TinyMCE 7 en la consola del explorador, lo que afectaba a la funcionalidad y a la experiencia del usuario. Ahora, este problema se ha resuelto, lo que garantiza que TinyMCE 7 funcione sin problemas sin generar errores, incluso cuando la minificación JS esté habilitada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Solicitud de cambios adicionales para completar completamente la corrección de ACP2E-3375
   * _Nota de corrección_: &#39;-
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### IU de administración, métodos de pago/pago, pedido

* _AC-13520_: la autorización de transacción no se muestra en la ficha Transacción después de que se haya realizado el pedido del botón inteligente de PayPal
   * _Nota de corrección_: El sistema ahora muestra correctamente la autorización de transacción en la ficha Transacción después de realizar un pedido mediante el botón Smart Button de PayPal. Anteriormente, la transacción de autorización no aparecía en la pestaña Transacción después de hacer clic en el botón &quot;Autorizar&quot; y no se creaba ninguna nueva transacción de tipo &quot;Autorización&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### IU de administración, ensayo y vista previa

* _ACP2E-3424_: [Nube] Al eliminar la plantilla con imágenes que faltan, se eliminan los medios/pub
   * _Nota de corrección_: Anteriormente a esta corrección, si faltaba el nombre de la imagen de vista previa para una plantilla de pagebuilder, se eliminaba la carpeta pub/media. Después de la corrección, solo se eliminará la plantilla y la imagen de vista previa si se encuentra.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Análisis / Informes

* _AC-9922_: error de CSP de Google Analytics https://region1.analytics.google.com
   * _Nota de corrección_: El sistema ahora permite correctamente las conexiones a &#39;https://region1.analytics.google.com&#39; cuando Google Analytics está habilitado, lo que evita errores de la Política de seguridad de contenido (CSP). Anteriormente, habilitar Google Analytics y ver el sitio web desde la UE resultaba en errores de la consola CSP debido a la negativa a conectarse a &quot;https://region1.analytics.google.com&#39;&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37750>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-3146_: falta el evento addToCart de GTM en dataLayer para un producto configurable con opción personalizada
   * _Nota de corrección_: anteriormente, el evento addToCart no se activaba para los productos configurables. Ahora, el evento se agrega correctamente a la variable dataLayer de GTM.
* _ACP2E-3183_: La supervisión del explorador NewRelic mediante script inlineJS causa errores de CSP
   * _Nota de corrección_: los scripts de supervisión del explorador NewRelic ahora son insertados por la aplicación en lugar del agente de APM para el cumplimiento de la CSP (Política de seguridad de contenido). Anteriormente, los scripts de monitorización del explorador de NewRelic insertados por el agente de APM no eran compatibles con el CSP y provocaban que los scripts no se ejecutaran.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: LAS consultas INSERT a la tabla sales_bestsellers_aggregated_daily se ralentizan en un proyecto con un gran volumen de pedidos de ventas
   * _Nota de corrección_: Anteriormente, el informe diario agregado de superventas tardaba mucho tiempo en generarse para un gran volumen de pedidos realizados. Ahora el informe se genera de manera oportuna.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Informes de pedidos que muestran el símbolo de moneda incorrecto
   * _Nota de corrección_: El símbolo de divisa para los importes de pedido en el informe de pedidos se tomó incorrectamente de la divisa/opciones/base. Ahora se ha corregido para utilizar moneda/opciones/predeterminado para un sistema de informes preciso.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Nube] Cálculos incorrectos en informe de uso de cupones
   * _Nota de corrección_: El total de ventas en la cuadrícula del informe de cupones ahora se calcula con precisión mediante la incorporación del &quot;Importe de compensación de impuestos de descuento&quot; y del &quot;Importe de compensación de impuestos de descuento de envío&quot;. Anteriormente, estas cantidades no aparecían en el cálculo, lo que producía discrepancias entre el total de ventas y los datos del pedido de ventas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: Problemas con el &quot;&lt;project_id>/var/tmp&quot; compartido
   * _Nota de corrección_: los archivos temporales de DataExport de Analytics utilizarán el directorio tmp de sys, que es más adecuado para cambios y accesos frecuentes. Para evitar conflictos en caso de que se ejecuten varias instancias en el mismo servidor, la ruta tmp se actualizó para utilizar un ID único de instancia
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics / Creación de informes, Cloud

* _ACP2E-3187_: La métrica en NR puede ser engañosa para transacciones en segundo plano- Seguimiento de ACP2E-3067
   * _Nota de corrección_: las transacciones en segundo plano (cron) utilizarán el nombre de aplicación de New Relic definido en la configuración
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: el paquete Enterprise Edition 2.4.8-beta102 está fallando con excepciones de aplicación
* _AC-13816_: no se puede habilitar la característica b2b en el administrador back-end por primera vez
* _ACP2E-2139_: Los productos asignados al catálogo compartido no se reflejan en el front-end cuando se ejecuta el índice parcial
   * _Nota de corrección_: los productos asignados al catálogo compartido mediante la API de REST ahora están visibles inmediatamente en la tienda una vez completada la indexación parcial. Anteriormente, los productos solo eran visibles después de una reindexación completa.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quote cron elimina las ofertas de los pedidos de compra aún aprobados
   * _Nota de corrección_: el trabajo cron sales_clean_quote no eliminará las ofertas usadas en los pedidos de compra ahora
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: El botón Realizar pedido desaparece en los detalles del pedido de compra
   * _Nota de corrección_: se corrigió un problema por el que el botón Realizar pedido estaba oculto para pedidos de compra aprobados cuando una variación de producto tenía un número mínimo en la tarjeta especificada
* _ACP2E-3474_: [NUBE] No existe esa entidad con id = 0 con módulo b2b
   * _Nota de corrección_: el usuario que ha iniciado sesión puede agregar un producto al carro de compras cuando las características de Catálogo compartido están habilitadas.
Si se agregaba anteriormente un producto al carro, se producía el error &quot;no existe esa entidad con ID = 0&quot;

### B2B, carro y cierre de compra

* _AC-13817_: no se pueden ver los productos en el carro de compras cuando todas las características de b2b están habilitadas

### B2B, GraphQL

* _ACP2E-3391_: [Nube] No se pueden establecer custom_attributes al crear la compañía a través de la llamada de graphql
   * _Nota de corrección_: después de la corrección, es posible establecer el atributo &quot;custom_attributes&quot; para el administrador de la compañía durante la creación de la compañía mediante una solicitud de graphql.

### Paquete

* _AC-10826_: validación de casilla de verificación de paquete de tienda Error de recuento de mensajes de más de 1
   * _Nota de corrección_: el sistema ahora muestra un solo mensaje de error de validación cuando se hace clic en el botón &#39;Agregar al carro de compras&#39; sin seleccionar ninguna opción de casilla de verificación para un producto agrupado. Anteriormente, el sistema mostraba varios mensajes de error de validación para cada casilla de verificación no seleccionada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: se produjo una excepción de Magento en algunos casos de prueba relacionados con pedidos
   * _Nota de corrección_: el sistema ahora administra correctamente el paso &#39;sendGuestPaymentInformation&#39; en varios casos de prueba, lo que impide que se produzcan excepciones de Magento. Anteriormente, estas excepciones se producían debido a un método de pago nulo, lo que provocaba errores en varios casos de prueba.

### Carro y cierre de compra

* _AC-11914_: [Problema] Cálculo del carro de compras de la regla de ventasCálculo corregido : cantidad de descuento incorrecta
   * _Nota de corrección_: El sistema ahora calcula correctamente el importe de descuento de las reglas de ventas con importes fijos del carro de compras, lo que garantiza que se apliquen descuentos precisos independientemente de los cambios en los elementos del carro de compras. Anteriormente, la cantidad de descuento podía variar incorrectamente cuando cambiaban los artículos del carro de compras, lo que a veces resultaba en descuentos significativamente mayores de lo esperado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38694>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-12479_: la casilla de verificación de Términos y condiciones no permite HTML en la tienda
   * _Nota de corrección_: el sistema ahora admite el formato HTML en el texto de la casilla de verificación &quot;Términos y condiciones&quot; de la tienda, lo que permite una mayor personalización y legibilidad. Anteriormente, el texto de la casilla de verificación se mostraba en formato de texto sin formato, ignorando las etiquetas de HTML utilizadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: la regla de precio del carro de compras creada para el usuario que inició sesión incorrectamente se aplica para el usuario que no inició sesión
   * _Nota de corrección_: el sistema ahora elimina correctamente la regla de precio del carro de compras para los usuarios que iniciaron sesión cuando cerraron sesión automáticamente debido a la caducidad de la cookie, lo que garantiza que el descuento no se aplique a los usuarios que no iniciaron sesión. Anteriormente, la regla de precio del carro de compras se seguía aplicando incluso cuando se cerraba la sesión del usuario, lo que provocaba que se aplicara un descuento incorrecto a los usuarios que no iniciaban sesión.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38944>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Problema] [CARACTERÍSTICA] Optimización del rendimiento para carros de compras grandes al evitar...
   * _Nota de corrección_: El sistema ahora optimiza el rendimiento de los carros de compras grandes al evitar llamadas getActions duplicadas, lo que mejora la velocidad y la eficacia de las operaciones del carro de compras. Anteriormente, para un carro de compras con varios elementos, se llamaba varias veces a la función getActions, lo que ralentizaba el rendimiento del sistema.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39292>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39290>
* _AC-13797_: el vínculo del registro de regalos no funciona correctamente
* _ACP2E-3176_: orden rápida de [nube] con una gran cantidad de rendimiento de SKU
   * _Nota de corrección_: El rendimiento del cierre de compra se mejoró cuando los atributos utilizados en las condiciones de las reglas de precios del carro de compras no están presentes en todos los productos y cuando la característica MAP (Precio mínimo anunciado) está habilitada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Elementos duplicados en el carro de compras
   * _Nota de corrección_: el sistema ahora procesa correctamente varias solicitudes paralelas para agregar el mismo producto al carro de compras en un solo elemento de línea, lo que impide la creación de elementos de línea independientes para el mismo SKU. Anteriormente, realizar solicitudes paralelas para agregar el mismo producto al carro de compras en Storefront resultaba en varios elementos de línea para el mismo SKU.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: La confirmación por correo electrónico del pedido de cierre de compra se envía a los mensajes de correo electrónico introducidos en Nombre/Apellidos
   * _Nota de corrección_: La confirmación de correo electrónico del pedido de cierre de compra, que se envió anteriormente cuando se introdujo un patrón de correo electrónico en los campos Nombre y Apellido, ya no se envía.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: El formulario de la dirección de envío de cierre de compra se actualizará con la dirección incorrecta
   * _Nota de corrección_: shippingAddressFromData ahora se guarda en el almacenamiento local por sitio web. Anteriormente, una dirección del sitio web incorrecto se podía rellenar automáticamente en el formulario de dirección de envío durante el cierre de compra si se utilizaba un código de tienda en la dirección URL y el cierre de compra se iniciaba desde varios sitios web durante la misma sesión de invitado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_: el proceso de cierre de compra de [CLOUD] no conserva la dirección de facturación seleccionada cuando la búsqueda de direcciones está habilitada
   * _Nota de corrección_: la página de pago de cierre de compra ahora conservará la dirección de facturación seleccionada cuando la búsqueda de direcciones esté habilitada. Anteriormente, si &quot;Límite de número de direcciones del cliente&quot; está configurado en 1 y el cliente tiene más de una dirección, la dirección de facturación seleccionada desaparecería después de volver a cargar la página.
* _ACP2E-3407_: Producto de tarjeta de regalo | Combinar carrito es combinar tarjetas de regalo
   * _Nota de corrección_: los productos de tarjeta de regalo ahora se combinaron correctamente en el carro de compras
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3488_: Los datos de comillas existentes no se actualizan o no son visibles; en su lugar, cree un nuevo registro de comillas cuando déclencheur_recollect = 1
   * _Nota de corrección_: los elementos del carro de compras del cliente ya no desaparecen como resultado de la eliminación de un producto después de agregarlo al carro de compras.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catálogo

* _AC-11970_: no se pueden reordenar los productos configurables con una casilla de verificación seleccionada como opción personalizada
   * _Nota de corrección_: El sistema ahora procesa correctamente la reordenación de los productos configurables con una sola opción personalizada de casilla de verificación seleccionada, lo que permite crear correctamente la cesta. Anteriormente, al intentar reordenar estos productos, se producía un error e impedía que se agregaran elementos al carro de compras.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38736>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_: faltan opciones desplegables
   * _Nota de corrección_: El sistema ahora muestra correctamente todos los valores de la lista desplegable al crear un nuevo atributo con más de 20 valores. Anteriormente, solo se mostraban los 20 primeros valores u otros valores de página seleccionados, lo que provocaba que faltaran los valores restantes.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Problema] Use el identificador de almacén actual para la caché de tiempo de ejecución de categoría
   * _Nota de corrección_: el sistema ahora utiliza correctamente el identificador de almacén actual para la caché de tiempo de ejecución de categoría, lo que evita la invalidación de datos cuando se utiliza la emulación o el código personalizado guarda la categoría en diferentes almacenes. Anteriormente, el objeto almacenado en tiempo de ejecución podría haber sido del almacén incorrecto, lo que provocaba la anulación de datos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39310>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:deploy —no-update genera una excepción
   * _Nota de corrección_: El sistema ahora acepta correctamente un valor booleano al utilizar la opción —no-update en el comando sampledata:deploy, lo que evita cualquier error durante la implementación de datos de ejemplo. Anteriormente, se producía un error al utilizar este comando, ya que el sistema esperaba incorrectamente un valor entero.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39344>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [Problema] Corrija el uso del tipo de caché EAV
   * _Nota de corrección_: El sistema ahora utiliza correctamente el tipo de caché EAV en todos los lugares relevantes, lo que garantiza un almacenamiento en caché de datos coherente y eficaz. Anteriormente, el tipo de caché de EAV no se utilizaba de forma coherente, lo que producía posibles ineficiencias e incoherencias en el almacenamiento en caché de datos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32322>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: la búsqueda avanzada en el catálogo con datos vacíos va a la página de resultados de búsqueda[2.4.dev branch]
   * _Nota de corrección_: el sistema retiene correctamente a los usuarios en la página Búsqueda avanzada y muestra un mensaje de error cuando intentan realizar una búsqueda sin introducir ningún dato. Anteriormente, realizar una búsqueda vacía redirigía a los usuarios a la página Búsqueda avanzada en el catálogo con un mensaje que les solicitaba que modificaran su búsqueda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13786_: el borde blanco no se está quitando después de deshabilitar product_image_white_border para el tema personalizado
* _ACP2E-3103_: la fuente RSS de nuevos productos no se actualiza con nuevos productos debido a la caché
   * _Nota de corrección_: la fuente Rss para nuevos productos ahora se actualiza cuando un producto se establece como nuevo y se guarda
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3198_: [nube] Problema de zoom y movimiento de dos dedos en el dispositivo móvil real
   * _Nota de corrección_: El sistema ahora garantiza una funcionalidad de zoom de imagen consistente en dispositivos móviles, lo que proporciona una experiencia de usuario fácil y predecible. Anteriormente, la función de zoom de imagen era incoherente y, de repente, se alejaba después de un determinado punto cuando se visualizaba en un dispositivo móvil.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: Cuando anulamos la asignación de productos del catálogo compartido, los productos de la lista de deseos no se borran
   * _Nota de corrección_: Ahora no hay elementos visibles en la lista de deseos si un producto no está disponible en el catálogo compartido. Anteriormente, la página de lista de deseos mostraba incorrectamente un recuento de &quot;1 elemento&quot; incluso cuando en realidad no había elementos disponibles en la lista de deseos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Productos relacionados Seleccionar todo/Anular selección de todos los problemas
   * _Nota de corrección_: anteriormente, los botones &quot;Seleccionar todo&quot;/&quot;Anular la selección de todo&quot; de los productos relacionados no funcionaban correctamente si se seleccionaba un producto manualmente. Después de la corrección, estos botones ahora funcionan de forma coherente, incluso después de la selección manual, lo que garantiza que todos los productos estén seleccionados correctamente o no.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Nube] Traducción de correo electrónico de alertas de stock al idioma incorrecto
   * _Nota de corrección_: al enviar alertas de cotizaciones/precios para un sitio web con varias vistas de tiendas en distintos idiomas, se utilizará en el correo electrónico el idioma de la vista de tienda en la que se creó la alerta.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: ya no aparecen atenuados los nombres de las categorías deshabilitadas en el árbol de categorías
   * _Nota de corrección_: anteriormente, las categorías deshabilitadas no aparecían atenuadas en el árbol de categorías. Ahora, se muestran con un efecto gris.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: La carga del formulario de edición de productos configurables causa tiempo de espera y agotamiento de memoria
   * _Nota de corrección_: antes de la corrección, las variaciones de productos configurables se construían en función de todas las combinaciones de opciones de atributos posibles. En los casos en los que los atributos tenían muchas opciones, esto resultaba en una operación larga y que consumía recursos. Ahora, las variaciones de producto configurables se construyen en función de los atributos de producto secundarios existentes. Esto da como resultado muchos menos cálculos, lo que mejora el uso de los recursos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama no carga el vídeo correctamente al usar Muestras y la opción está preseleccionada mediante una URL
   * _Nota de corrección_: los vídeos del producto ahora se representarán correctamente en la página de detalles del producto configurable, si la dirección URL contiene opciones seleccionadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: El widget de carrusel de PageBuilder muestra productos que no cumplen las condiciones
   * _Nota de corrección_: La lista de productos utilizada en los widgets ahora respeta la condición de categoría
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Error de validación activado para todos los productos del grupo cuando uno tiene una cantidad no válida
   * _Nota de corrección_: Ahora, el error de validación se activa correctamente para todos los productos del grupo cuando un producto tiene una cantidad no válida, lo que no ocurría anteriormente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: los indizadores Las tablas temporales no se limpian si el proceso finaliza
   * _Nota de corrección_: las tablas temporales del indizador CatalogRule ahora se limpian si ha finalizado el proceso del indizador
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] errores de prueba de unidad principal en 2.4.7-p3
   * _Nota de corrección_: no se necesitan notas de la versión para esta prueba porque es una mejora de prueba unitaria.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catálogo, Contenido

* _ACP2E-3063_: La caché de [Cloud] no se va a invalidar.
   * _Nota de corrección_: Anteriormente, al guardar una página de CMS con un diseño actualizado, no se reflejaba correctamente en el front-end. Después de aplicar esta corrección, el diseño de diseño adecuado será visible en el front-end cuando cambiemos el diseño y guardemos la página de CMS.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Categorías de anclaje/no anclaje en la nube] invertidas en el widget de contenido
   * _Nota de corrección_: anteriormente, cuando seleccionamos Mostrar en -> Categorías de anclaje, se mostraban todas las categorías que no reflejaban la relación principal-secundario entre el anclaje y el no anclaje. Después de aplicar esta corrección, la opción Mostrar activado -> Categorías de anclaje solo muestra Categorías de anclaje (seleccionable) y Mostrar activado -> Categorías de no anclaje muestra Categorías de no anclaje (seleccionable)
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Las categorías no funcionan con widgets
   * _Nota de corrección_: anteriormente, si guardábamos el bloque de CMS para diferentes categorías de anclaje/no anclaje, no funcionaba para las categorías secundarias cuando se mostraba en el front-end. Después de aplicar esta corrección, el bloque se muestra en el front-end para diferentes categorías.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>

### Catálogo, GraphQL

* _ACP2E-3312_: Los precios de nivel devuelven un valor incorrecto en los productos GraphQL (en comparación con Storefront)
   * _Nota de corrección_: después de la corrección, los precios de nivel del producto devueltos para las solicitudes de graphql tienen un precio por elemento.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [NUBE] B2B: problema de categoría a través de GraphQL
   * _Nota de corrección_: después de la corrección, la consulta de categorías de graphql devuelve categorías con permiso de permiso aunque la categoría raíz no tenga permiso de permiso.

### Catálogo, Buscar

* _ACP2E-3345_: Error de tipo al crear el objeto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Nota de corrección_: después de la corrección, se puede crear una instancia de la clase Magento\CatalogSearch\Model\Indexer\Fulltext sin especificar $data.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [NUBE] El problema con los productos no es visible en Frontend después de guardarlo en Magento Admin
   * _Nota de corrección_: después de la corrección, los productos configurables que tengan productos secundarios con nombres largos no se perderán en la tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catálogo, Envío

* _ACP2E-3195_: Dirección de envío vacía al realizar un pedido de un artículo del registro de regalos
   * _Nota de corrección_: anteriormente, para los elementos del registro de regalos de usuario invitado, cuando se devolvían desde la función de correo electrónico, generaba una dirección vacía en blanco, que es incorrecta para realizar un pedido. Después de aplicar esta corrección, el Registro de regalos comprueba los usuarios que han iniciado sesión o los usuarios invitados y las direcciones asignadas si existen.

### Contenido

* _AC-12692_: el árbol de categorías del widget no se representa correctamente
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39008>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: no se puede ver el mensaje &quot;Usar valor predeterminado&quot; al cambiar el tema en la página de configuración de diseño
   * _Nota de corrección_: el sistema ahora incluye una columna independiente para mostrar el mensaje &quot;Utilizar valor predeterminado&quot; en función del tema seleccionado en la página de configuración de diseño. Esto garantiza la claridad y visibilidad del estado del valor predeterminado. Anteriormente, no se mostraba el mensaje &quot;Using Default value&quot;, lo que producía confusión sobre el estado de la temática seleccionada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problema] Restaura de nuevo la compatibilidad con los complementos TinyMCE (después de...
   * _Nota de corrección_: El sistema ahora restaura la compatibilidad con versiones anteriores de los complementos TinyMCE, lo que permite llamar a las funciones definidas dentro del complemento cuando se utiliza el widget desde otra ubicación. Anteriormente, debido a un cambio en la versión de TinyMCE, los complementos no devolvían los widgets como un objeto, lo que provocaba un error al intentar llamar a ciertas funciones en la instancia del widget.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39262>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_: [NUBE] El botón Cargar imagen no funciona
   * _Nota de corrección_: Antes el botón Cargar imagen para Banner y Slider de PageBuilder no funcionaba como se esperaba y ahora al pulsarlo se abre el administrador de archivos local para seleccionar la imagen que se desea cargar.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [Nube] - El control deslizante de CMS no refleja los cambios más recientes
   * _Nota de corrección_: el problema se ha corregido asegurándose de que la lista del control deslizante se actualice mientras se activa el evento de guardado en la pantalla de edición de diapositivas. Anteriormente, se activaba y causaba el problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Se produce un error en la página CSM cuando se insertan bloques de CMS usando el generador de páginas en un orden determinado
   * _Nota de corrección_: Anteriormente en algunas versiones de PHP y OS (Linux), la representación de bloques que hacían referencia a otros bloques cms a través de PageBuilder habría fallado con un &quot;Error desconocido&quot;. Inténtelo de nuevo&quot;. Ahora el contenido de los bloques cms se representa correctamente dentro de un contenido controlado por PageBuilder.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [Los bloques dinámicos de la nube] no funcionarán correctamente
   * _Nota de corrección_: los segmentos de clientes que iniciaron sesión ahora se borran tras cerrar la sesión, lo que impide que la sesión de invitado herede los segmentos que iniciaron sesión anteriormente
* _ACP2E-3430_: Faltan las últimas actualizaciones de seguridad con TinyMCE 7
   * _Nota de corrección_: Los selectores de tamaño de fuente y familia de fuentes ya están disponibles en el editor de WYSIWYG. Antes de esta corrección, con TinyMCE 7 estos no estaban disponibles en la interfaz del editor.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Cliente/ Clientes

* _AC-13060_: Segmento del cliente > Condición > Historial del producto* > &quot;El producto se ha visto&quot; no funciona
   * _Nota de corrección_: el sistema ahora muestra correctamente los clientes registrados coincidentes en la condición &quot;Se vio el producto&quot; en Segmentos de clientes, cuando se cumple la condición. Anteriormente, incluso cuando se cumplía la condición, el recuento de clientes registrados coincidentes permanecía en cero.
* _AC-8499_: el campo de texto de región no se restablece cuando se cambia la lista desplegable de países
   * _Nota de corrección_: El sistema ahora restablece el campo de texto de región cuando se cambia el país en el menú desplegable, asegurándose de que los valores anteriores no persistan. Anteriormente, al cambiar el país de la lista desplegable, no se restablecía el campo de región, lo que provocaba que se conservara el último valor guardado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: al eliminar el cliente, no se limpian todos los datos de sesión del explorador en Storefront para el cliente que inició sesión y lo eliminó
   * _Nota de corrección_: al eliminar un cliente, ahora se limpian todos los datos de sesión del explorador de la tienda para los clientes que iniciaron sesión y se eliminaron según lo esperado. El comprador puede seguir comprando y su navegador trata su sesión como una sesión de invitado. Anteriormente, cuando la cuenta de cliente de un comprador que iniciaba sesión se eliminaba del administrador, el explorador del comprador arrojaba errores de JavaScript.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>

### Marco

* _AC-10738_: la configuración del barniz no excluye todos los parámetros de marketing
   * _Nota de corrección_: el sistema ahora excluye correctamente todos los parámetros de marketing comunes en la configuración de Barniz, lo que garantiza un seguimiento y análisis precisos. Anteriormente, no se excluían ciertos parámetros de marketing como gad_source, srsltid y msclkid, lo que producía posibles imprecisiones en la recopilación de datos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38298>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [Problema] Permitir solo las preferencias válidas durante la instalación:di:compilación
   * _Nota de corrección_: El sistema genera un error durante el comando setup:di:compile si se crea una preferencia para una clase que no existe o se excluye específicamente, asegurándose de que solo se permiten preferencias válidas. Anteriormente, estos escenarios fallaban de forma silenciosa, lo que podía inutilizar cualquier complemento asociado con las clases originales.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38517>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [Problema] Pasar atributos personalizados al vínculo actual a través de XML
   * _Nota de corrección_: el sistema ahora permite que los atributos personalizados se pasen al vínculo actual a través de XML, asegurándose de que estos atributos se muestren correctamente incluso cuando el vínculo sea la página actual. Anteriormente, los atributos personalizados no se mostraban para el vínculo de página actual debido a que el método getAttributesHtml() no se utilizaba para el vínculo actual.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38500>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/30070>
* _AC-12127_: [Problema] para evitar un bucle infinito de configuración incorrecta
   * _Nota de corrección_: el sistema ahora evita un bucle infinito al impedir la asignación de autorreferencia en configuraciones de tipo virtual. Esto garantiza que la aplicación no se quede atascada en un bucle interminable al intentar anular la referencia a un nodo de referencia automática. Anteriormente, si una configuración de tipo virtual era de referencia propia, la aplicación giraba indefinidamente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38822>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: no se usa el Administrador de objetos para Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Nota de corrección_: El sistema ahora utiliza correctamente el Administrador de objetos al crear el objeto ModeConficonfigured, lo que permite que se utilicen complementos en este objeto. Anteriormente, no se utilizaba el Administrador de objetos, lo que impedía que se aplicaran complementos al objeto ModeConficonfigured.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38875>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: comentario de bloque de documento incorrecto en las alertas de precio y existencias de productos
   * _Nota de corrección_: El comentario del bloque de documentación para el método deleteCustomer en las alertas de precios y existencias de productos se ha corregido para reflejar con precisión que el método elimina todas las alertas de precios o productos de existencias asociadas a un cliente y sitio web determinados, no al cliente del sitio web. Anteriormente, el comentario indicaba de forma incorrecta que el método era para eliminar un cliente del sitio web.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38939>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39001>
* _AC-12857_: PHP 8.2.15 eliminó la extensión FTP
   * _Nota de corrección_: El sistema ahora incluye la extensión FTP como dependencia en el archivo composer.json, lo que garantiza la correcta configuración de las importaciones CSV a través de FTP. Anteriormente, se producía un error al intentar configurar las importaciones de CSV a través de FTP debido a que la extensión FTP no estaba presente en el paquete PHP.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39083>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: capacidad para definir el área para el comando dev:di:info CLI
   * _Nota de corrección_: El sistema ahora permite a los desarrolladores definir un área para el comando dev:di:info CLI, lo que mejora el proceso de desarrollo y depuración. Anteriormente, este comando solo podía mostrar información del área GLOBAL.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38758>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38759>
* _AC-13247_: setup:upgrade está fallando con la versión MariaDB 11.4 debido a cambios en charset y intercalación
* _AC-13279_: [Problema] Elimine todos los parámetros de obtención de marketing para minimizar la caché
   * _Nota de corrección_: El sistema ahora elimina todos los parámetros de obtención de marketing para optimizar el uso de la caché, reflejando la lógica utilizada cuando Varnish está en uso. Anteriormente, estos parámetros podían provocar una hinchazón de la caché y reducir el rendimiento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39266>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Nota de corrección_: El método PHPDoc para AllowedCountries::getAllowedCountries() se ha corregido para proporcionar información precisa, lo que mejora la claridad y utilidad de la documentación. Anteriormente, el PHPDoc de este método contenía información incorrecta, lo que podría llevar a confusión o uso indebido del método.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39246>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [Problema] elimina código de versiones de PHP que ya no admitimos.
   * _Nota de corrección_: eliminación de código para versiones de PHP que ya no son compatibles con Magento
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39361>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Problema] hace que el adaptador ImageMagick sea compatible con php8 (conversión implícita de flotante a int)
   * _Nota de corrección_: El sistema ahora garantiza la compatibilidad con PHP8 administrando correctamente los números flotantes al calcular las dimensiones de la imagen, evitando cualquier error debido a la conversión implícita de flotante a int. Anteriormente, el cálculo de las dimensiones de imagen podía dar como resultado números flotantes, que cuando se redondeaban implícitamente, provocaban un error.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39402>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Framework\App\Config\ScopeConfigInterface
   * _Nota de corrección_: esta actualización corrige las anotaciones PHPDoc en el archivo Magento\Framework\App\Config\ScopeConfigInterface para reflejar con precisión el tipo del argumento $scopeCode para los métodos getValue e isSetFlag.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39492>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39199>
* _AC-8662_: [Problema] Mejora el registro de errores cron
   * _Nota de corrección_: El sistema ahora captura y registra tanto STDERR como STDOUT para los procesos cron, proporcionando información de diagnóstico valiosa en escenarios donde los procesos cron fallan. Anteriormente, no se registraba ningún mensaje de error en los procesos cron y se perdían STDERR y STDOUT para los grupos cron que se ejecutaban en procesos independientes.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37453>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32690>
* _ACP2E-3230_: La modificación de la longitud de la columna a través de db_schema.xml no funciona en el caso de claves externas
   * _Nota de corrección_: la modificación de la columna con clave externa a través del esquema declarativo ahora no genera errores con MariaDB
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Algunos de los registros de relaciones se guardan en la base de datos cuando se guarda el registro del pedido
   * _Nota de corrección_: antes de corregir, se activaban consultas UPDATE innecesarias que pueden afectar al rendimiento. Después de la corrección, se eliminaron las consultas UPDATE innecesarias.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [NUBE] En el administrador hay muchos errores de JavaScript en la consola
   * _Nota de corrección_: anteriormente, en el panel de administración hay muchos errores de JavaScript en la consola. Ahora, en el panel de administración, no habrá errores de JavaScript en la consola y todas las funciones predeterminadas de JavaScript se ejecutarán correctamente sin ningún problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Nube] Magento: se eliminó el mensaje en cola
   * _Nota de corrección_: los mensajes de la cola se están borrando correctamente. Antes de la corrección, dado que se estaba utilizando el sistema de cola SQL, se podían haber eliminado nuevos mensajes si el mensaje de la cola de limpieza se estaba ejecutando al mismo tiempo.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Marco, marco de IU

* _ACP2E-3324_: Posibilidad de sobrescribir el valor de configuración aunque esté bloqueado
   * _Nota de la corrección_: Anteriormente a esta corrección, la configuración del diseño no se podía establecer mediante el comando bin/magento config:set y los valores bloqueados se podían cambiar manipulando el formulario que los mostraba. Después de la corrección, los valores bloqueados establecidos desde cli con —lock-env o —lock-conf ya no se pueden actualizar.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: las traducciones de los atributos devueltos por el cliente no se reflejan en la API de GraphQL para el StoreView correspondiente
   * _Nota de corrección_: las traducciones para atributos de devolución del cliente se reflejan en la API de GraphQL para el StoreView correspondiente.
Anteriormente, los atributos de retorno de los clientes para las respectivas vistas de tienda no se reflejaban en la API de GraphQL.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: [Nube] problema con autenticación de usuarios y acceso de tokens entre sitios en la configuración de varios sitios
   * _Nota de corrección_: Las consultas de Información del cliente y del carro de compras de GraphQl en la configuración de varios sitios comprueban si existe el cliente en un sitio web no predeterminado.
Anteriormente, la consulta funcionaba sin asegurarse de que el cliente existe en un sitio web no predeterminado en la configuración de varios sitios.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_: El valor del modelo [GRAPHQL] debe especificarse al obtener customerCart
   * _Nota de corrección_: La consulta &quot;customerCart&quot; de GraphQL ahora puede crear un carro de compras vacío aunque el presupuesto no esté disponible en la base de datos. Anteriormente, esta operación fallaba debido a problemas de validación de país al crear el carro de compras vacío.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [GraphQl] Los elementos de la lista de deseos son visibles a través de GraphQl, pero no en la tienda
   * _Nota de corrección_: Los productos de la lista de deseos no se enumeraban correctamente cuando se solicitaban a través de GraphQL. Ahora, los productos de la lista de deseos se filtran según el contexto de tienda proporcionado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] Restablecer incoherencia de correo electrónico de contraseña entre contenido y asunto/vínculo
   * _Nota de corrección_: el problema se resolvió al simular el almacén correcto en el que está registrada la cuenta del cliente al enviar la solicitud de restablecimiento de contraseña, independientemente del almacén del sitio web.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: La consulta de GraphQL de [Cloud] productos devuelve productos relacionados no asignados al sitio web actual
   * _Nota de corrección_: anteriormente, para la consulta de graphQL, los productos relacionados con varias tiendas no se muestran correctamente para la consulta de productos. Después de aplicar esta corrección, para los productos de, graphQL consulta los productos relacionados con varias tiendas que se muestran en consecuencia.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: El uso del ID de almacén incorrecto en el encabezado de GraphQL causa un error grave de memoria
   * _Nota de corrección_: el envío de código de almacén incorrecto en la solicitud de GraphQL ya no provoca un consumo excesivo de memoria.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [Nube] 500 respuestas a Graphql vacío en 2.4.7
   * _Nota de corrección_: después de la corrección, las solicitudes de graphql no válidas no se registrarán en el archivo exception.log.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _LYNX-600_: aumente la complejidad máxima predeterminada de las consultas de GraphQL a 1000

### GraphQL, Buscar

* _ACP2E-948_: la consulta de GraphQL de listado de productos está limitada únicamente a total_count 10.000 productos
   * _Nota de corrección_: después de la corrección, el resultado de la búsqueda no se limita a 10000 productos, es posible obtener todos los productos que coincidan con los criterios de búsqueda aunque el recuento sea superior a 10000.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, marco de prueba

* _ACP2E-3363_: Error en la prueba de integración de Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Nota de corrección_: &#39;-
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importación/exportación

* _ACP2E-3172_: Falta el botón Importar
   * _Nota de corrección_: resuelva el problema de falta del botón Importar después de comprobar los datos con registros correctos e incorrectos en el CSV. Anteriormente, el botón de importación no se muestra después de la comprobación de datos con registros correctos e incorrectos en el CSV.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: no se puede importar la dirección de cliente exportada
   * _Nota de corrección_: la importación de direcciones de clientes se realizará según lo esperado. Anteriormente, un archivo de importación de direcciones de clientes no pasaba la validación si Compartir cuentas de clientes = Global y hay dos sitios web en los que el sitio web predeterminado tiene una lista de países restringidos y la dirección que se importa es para otro sitio web en el que los países permitidos son diferentes
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Nube] La cantidad incorrecta en el archivo CSV no produjo error
   * _Nota de corrección_: Ahora la importación de orígenes de existencias generará un error de validación para los valores no numéricos de la columna de cantidad. Anteriormente, al importar orígenes de stock con valores no numéricos en la columna de cantidad, la cantidad se establecía en 0.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: La exportación de productos causa OOM incluso con límite de memoria 4G
   * _Nota de corrección_: antes de esta corrección, la exportación del producto fallaba si los atributos del producto tenían miles de valores de opción incluso con memoria disponible 4G. Después de esta corrección, la exportación del producto debe terminar de exportar el archivo CSV.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Importación/exportación, Rendimiento

* _ACP2E-3476_: El tiempo de importación del producto de [Cloud] ha aumentado significativamente
   * _Nota de corrección_: antes de la corrección, la importación de productos del catálogo con más de 10 000 entradas experimentaba una degradación del tiempo significativa. Después de la corrección, la importación del producto del catálogo se ejecuta de manera oportuna.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/87d012e5>

### Instalar y administrar

* _AC-13242_: la actualización de Magento falla en MariaDB 11.4 + 2.4.8-beta1
   * _Nota de corrección_: la actualización debe realizarse sin errores.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7b336d0a>

### Inventario/MSI

* _ACP2E-3335_: No se puede enviar el pedido cuando el almacén de recogida MSI está habilitado
   * _Nota de corrección_: se ha mejorado el rendimiento de inventario de la creación de envíos en caso de que haya muchas fuentes con recogida en la tienda
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: el reíndice de Cron no puede actualizar la disponibilidad del producto en el front-end
   * _Nota de corrección_: anteriormente, los productos permanecían sin existencias en el front-end después de actualizar el estado del pedido pendiente a través de la API de REST. Ahora, después de actualizar el estado del pedido pendiente mediante la API de REST, los productos se muestran como en stock.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: La adición de imágenes a configurables no funciona cuando MSI está habilitado.
   * _Nota de corrección_: la carga de imágenes para el producto configurable ahora funcionará como se espera cuando se utilice el módulo de inventario. Anteriormente, la carga de imagen no funcionaba
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/fdf409aa>

### Inventario / MSI, búsqueda

* _ACP2E-3413_: Todos los productos están indexados con [is_out_of_stock] = 1 cuando el SKU no está establecido como atributo en el que se puede buscar
   * _Nota de corrección_: después de la corrección, el valor &quot;is_out_of_stock&quot; en el índice de búsqueda del catálogo es correcto, incluso cuando no se puede buscar en el SKU.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>

### Pedido

* _ACP2E-3311_: [Nube] No se puede crear un pedido en administración en un almacén si solamente no se configuró la dirección de facturación predeterminada
   * _Nota de corrección_: Ahora existe un mensaje de error relevante &quot;Ya existe un cliente con la misma dirección de correo electrónico en un sitio web asociado&quot;. se muestra si un cliente no tiene una dirección de facturación predeterminada e intenta crear un pedido en otra tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Se han enviado solicitudes de pedidos de lugares duplicadas por el administrador
   * _Nota de corrección_: anteriormente, se podía hacer clic en el botón &quot;Enviar pedido&quot; en el panel de administración varias veces o activarlo presionando repetidamente la tecla &quot;Intro&quot;, lo que provocaba envíos duplicados o de pedidos con errores. Ahora, evita acciones adicionales hasta que la solicitud se procese por completo, lo que garantiza que solo se envíe una solicitud.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: El administrador aún puede hacer el pedido incluso sin el método de pago
   * _Nota de corrección_: el método de pago seleccionado anteriormente ahora se conserva cuando el método de pago vuelve a aparecer en la lista de pagos disponibles.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Pedido, Pagos

* _ACP2E-3233_: El administrador aún puede hacer el pedido incluso sin el método de pago
   * _Nota de corrección_: anteriormente, el comerciante podía realizar pedidos desde el panel de administración sin seleccionar un método de pago. Ahora, el comerciante necesita un método de pago para proceder a realizar un pedido.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Otros

* _LYNX-426_: el porcentaje de descuento no se calcula para los productos agrupados con precio dinámico
* _LYNX-485_: el paquete de productos todavía muestra &quot;IN_STOCK&quot; cuando uno de sus paquetes está agotado
* _LYNX-486_: not_available_message y only_x_left_in_stock no muestra el mismo stock disponible
* _LYNX-488_: el campo original_row_total devuelve un valor incorrecto
* _LYNX-503_: la miniatura del producto agrupado debe mostrarse según la configuración     .
* _LYNX-510_: error al consultar selected_options en OrderAddress
* _LYNX-512_: original_item_price no incluye descuentos
* _LYNX-530_: el mensaje no disponible no muestra la cantidad de inventario disponible
* _LYNX-532_: el estado &quot;OUT_OF_STOCK&quot; vuelve a aparecer en Simple con productos de opciones personalizadas con opciones de selección múltiple
* _LYNX-533_: error (GQL): cart.itemsV2.items.product.custom_attributesV2 devuelve un error de servidor
* _LYNX-536_: pedidos/date_of_first_order siempre devuelven un valor nulo
* _LYNX-544_: el cliente no debe poder cancelar un pedido enviado parcialmente
* _LYNX-548_: códigos de error para la cancelación de pedidos basados en el mensaje de error
* _LYNX-581_: retroceda las propiedades relacionadas con cookies de privadas a protegidas

### Otras herramientas para desarrolladores

* _AC-12731_: problemas de CSP combinados con dev/css/use_css_critical_path
   * _Nota de corrección_: El sistema ahora carga correctamente los archivos CSS de forma asíncrona en las páginas de cierre de compra, incluso cuando la configuración &quot;dev/css/use_css_critical_path&quot; esté habilitada, lo que garantiza que estas páginas se representen con los estilos CSS adecuados. Anteriormente, una directiva de seguridad de contenido (CSP) restringida impedía la ejecución de JavaScript en línea, lo que provocaba que los archivos CSS no se cargaran según lo esperado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39020>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: usando el tipo virtual para configurar el complemento, el método interceptor no se puede generar correctamente en el comando setup:di:compile
   * _Nota de corrección_: El sistema ahora genera correctamente métodos interceptores cuando se utiliza un tipo virtual para configurar un complemento, lo que garantiza resultados coherentes, ya sean precompilados o compilados en tiempo de ejecución. Anteriormente, el sistema generaba resultados incorrectos cuando se precompilaba en comparación con la compilación en tiempo de ejecución.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/33980>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: No se pueden descargar archivos del Recopilador de datos
   * _Nota de corrección_: al descargar la copia de seguridad ya no se muestra una página en blanco en lugar de descargar el archivo.

### Pagos

* _ACP2E-3143_: El reembolso del pedido de PayPal genera un duplicado del abono
   * _Nota de corrección_: se ha corregido el problema de simultaneidad de los abonos creados por IPN para el servicio de pago de PayPal.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: La regla de precio del carro de compras no funciona para Paypal
   * _Nota de corrección_: el importe correcto se muestra en el lado de PayPal cuando se aplica el descuento por la forma de pago
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Nube] Los usuarios con un rol específico no pueden iniciar sesión
   * _Nota de corrección_: el usuario administrador con un rol que solo contiene acceso a la sección de PayPal ahora puede iniciar sesión sin errores
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>

### Rendimiento

* _AC-11932_: problema de configuración de atributos de producto predeterminados
   * _Nota de corrección_: el sistema ahora permite a los usuarios anular la selección de una opción predeterminada para un atributo de producto, asegurándose de que el atributo no siempre tenga un conjunto predeterminado. Anteriormente, una vez que se establecía un valor predeterminado para un atributo de producto, no había forma de anular la selección, lo que provocaba que el atributo siempre tuviera un valor predeterminado establecido.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38703>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_: compatibilidad con CommandLoaderInterface de Symfony en Magento CLI
   * _Nota de corrección_: Este cambio reduce el tiempo de inicialización de la aplicación CLI de Magento al permitir la inicialización diferida de comandos hasta que se necesitan.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/29266>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/29355>

### Product

* _AC-13173_: [Problema] Se corrigió un error tipográfico en el bloque PHPDoc
   * _Nota de corrección_: El sistema ahora quita correctamente una variable de referencia desconocida en PHPDoc para la declaración de la variable $helper, lo que mejora la claridad y precisión del código. Anteriormente, esta variable de referencia desconocida en PHPDoc causaba confusión y posibles imprecisiones en el código.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38961>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problema] Se ha corregido el diseño de páginas de productos del paquete dañado y descargable en Magento >= 2.4.7
   * _Nota de corrección_: se ha corregido el diseño de las páginas de productos agrupadas y descargables, lo que garantiza una visualización coherente y correcta en todos los dispositivos. Anteriormente, estas páginas experimentaban problemas de diseño debido a una reorganización del bloque multimedia de información del producto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39403>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_: [Nube] Productos en la categoría - Agregar productos - Asignar - Seleccionar todo
   * _Nota de corrección_: los usuarios ahora pueden seleccionar o anular la selección de productos mediante la opción.

### Promoción

* _ACP2E-3139_: La regla de ventas con el atributo Paso de cantidad de descuento (Comprar X) hace que no se apliquen otras reglas
   * _Nota de corrección_: la regla de precio del carro de compras no cancela las reglas aplicadas anteriormente si la cantidad del producto en el carro de compras no es suficiente para que se aplique la regla.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: Problema de rendimiento en la regla de precios del carro de compras - Módulo de regla de ventas avanzada
   * _Nota de corrección_: se agregaron los índices de BD que faltaban para los filtros AdvancedSalesRule
* _ACP2E-3332_: Emitir reglas de ventas con descuento de importe fijo y &quot;Se aplica descuento de cantidad máxima a&quot;
   * _Nota de corrección_: se ha corregido un problema con el descuento en las reglas del carro de compras cuando el descuento de cantidad fija está configurado para aplicarse a una cantidad limitada de productos que es el carro de compras. Anteriormente, el valor &quot;Descuento de cantidad máxima aplicado a&quot; se utilizaba para calcular el precio del artículo actual en el carro de compras, no solo para calcular el descuento de la regla.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: La actualización a [CLOUD] Magento hizo que los cupones hicieran distinción de mayúsculas y minúsculas
   * _Nota de corrección_: antes de la corrección, tenía que escribir el código de cupón exactamente como estaba configurado, teniendo en cuenta las mayúsculas y minúsculas. Ahora, el cupón se validará en el back-end independientemente de la configuración del código en mayúsculas o minúsculas.
* _ACP2E-3349_: Reglas de carro de compras &quot;Descuento de cantidad fija para todo el carro de compras&quot;  La acción aplica descuentos incorrectamente
   * _Nota de corrección_: los códigos de cupones se validarán correctamente, independientemente de las mayúsculas y minúsculas, cuando se utilicen para crear pedidos desde el área de administración. Antes, el código de cupón no se validaba si no coincidía con el caso de letra exacto del código de regla del carro de compras configurado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: En el servidor, los valores predeterminados de almacenamiento para los atributos de producto (en lugar de los valores de administración esperados)
   * _Nota de corrección_: ahora en el servidor se usan valores de administración en lugar de valores de almacén predeterminados para los atributos del producto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: La acción &quot;Descuento de cantidad fija para todo el carro de compras&quot; de las reglas del carro de compras aplica descuentos incorrectamente al agregar productos agrupados
   * _Nota de corrección_: las reglas del carro de compras de cantidad fija no se aplicaban correctamente a los productos agrupados. Ahora, al calcular la cantidad de descuento total, se tienen en cuenta los productos secundarios del paquete, lo que resulta en un cálculo de descuento adecuado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: Reglas de precios del carro de compras que calculan mal el descuento
   * _Nota de corrección_: los descuentos de cantidad fija ahora se calculan correctamente. Antes de la corrección, los descuentos de cantidad fija no se sumaban correctamente para los productos agrupados.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: No se muestran las categorías anidadas en las condiciones de regla
   * _Nota de corrección_: se corrigió un problema que se producía cuando las categorías anidadas de nivel 3 no se mostraban en las reglas de marketing para la condición de categoría
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit y uses_per_customer no se actualizan en la tabla salesrule_coupon
   * _Nota de corrección_: La actualización de los usuarios por cupón y los usuarios por cliente en la regla de precios del carro de compras ahora afectará los cupones generados automáticamente existentes. Anteriormente, los nuevos valores solo afectaban a los nuevos cupones
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: La regla de precio del carro de compras no considera la categoría principal cuando utiliza la condición &quot;es igual o mayor que&quot;.
   * _Nota de corrección_: Las reglas de precio del carro de compras ahora consideran correctamente la categoría principal cuando se utiliza en condiciones avanzadas
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: cálculo de descuento no válido con prioridad
   * _Nota de corrección_: en el caso de la cantidad fija aplicada para todo el tipo de descuento del carro de compras, la cantidad no se calculaba correctamente para los artículos del carro de compras que ya se habían descontado en una promoción anterior. Ahora, los descuentos están correctamente resumidos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3498_: Valor de descuento incorrecto cuando se aplican varias reglas de precios del carro de compras simultáneamente con productos con precios especiales o con descuento
   * _Nota de corrección_: antes de la corrección, la cantidad fija para las reglas completas del carro de compras no se aplicaba correctamente si se aplicaba más de una. Ahora, las reglas del carro de descuentos de cantidad fija se aplican correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Devuelve

* _ACP2E-3330_: [NUBE] Los usuarios administradores restringidos pueden ver el menú y los botones de retorno
   * _Nota de corrección_: Los usuarios administradores restringidos ahora no tienen acceso a los controles relacionados con RMA (menú y botones).
Los usuarios administradores anteriormente restringidos podían ver el menú y los botones de retorno.
* _ACP2E-3443_: La pantalla de retorno está dañada al actualizar la pantalla
   * _Nota de corrección_: el usuario puede actualizar la página sin experimentar distorsión de la pantalla.

### Ventas

* _AC-13750_: el total general y el total general base no coinciden con los pasos del resultado de la prueba
* _AC-13751_: La regla de precio del segundo carro de compras no se aplica si ya se ha aplicado la regla del primer carro de compras

### Buscar

* _AC-13053_: obteniendo &quot;Escribe un término de búsqueda y vuelve a intentarlo&quot;. error en la página de búsqueda avanzada de la tienda en 2.4.8-beta1
   * _Nota de corrección_: el sistema ahora muestra correctamente los resultados de búsqueda en la página Búsqueda avanzada cuando un atributo de producto está establecido en &quot;No&quot;. Anteriormente, si establecía un atributo de producto en &quot;No&quot; y realizaba una búsqueda, se mostraba un mensaje de error: &quot;Introduzca un término de búsqueda e inténtelo de nuevo&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-search depende de una rama opensearch-php inexistente
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: la tabla search_query cuando es de gran tamaño, tiene un gran impacto en el front-end del tiempo de carga
   * _Nota de corrección_: se ha mejorado el tiempo de carga de la página del listado de búsqueda. Antes de la corrección, la página de la lista de búsqueda se retrasaba debido a una consulta no optimizada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Seguridad

* _ACP2E-3273_: ReCaptcha V2 se muestra incorrectamente al pagar el idioma alemán
   * _Nota de corrección_: Anteriormente, el recaptcha de debajo de la dirección de correo electrónico de cierre de compra no tenía estilo para los idiomas con palabras largas, como el alemán. Después de esto, el recaptcha tiene el mismo aspecto que todos los elementos recaptcha del resto de las áreas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: El captcha al iniciar sesión como administrador no requiere interacción para algunos usuarios
   * _Nota de corrección_: ReCaptcha para el inicio de sesión del administrador se validó según lo esperado

### Envío

* _AC-12938_: actualizaciones de las instrucciones de configuración de UPS REST &quot;sandbox&quot; y &quot;prod&quot; en devdoc
* _ACP2E-3340_: la API de seguimiento de FedEx no funciona con las credenciales de REST
   * _Nota de corrección_: Anteriormente, la integración con FedEx no requería claves de API adicionales para la API de seguimiento. Ahora se ha añadido una nueva configuración para admitir el seguimiento de claves de API.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Las tarifas negociadas de FedEx de la nube] no se devuelven en REST
   * _Nota de corrección_: Antes de la corrección, las tasas específicas de la cuenta de FedEx no se enviaban en la respuesta, incluso a través de la documentación de FedEx que deberían haberse enviado. Después de la corrección, las tasas específicas de la cuenta se envían en la respuesta cambiando la solicitud por nuestra parte.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Ensayo y previsualización

* _ACP2E-3453_: No se puede actualizar la actualización programada al usar un atributo de categoría personalizado único
   * _Nota de corrección_: se corrigió un problema en el cual no era posible actualizar una actualización programada para una categoría si esta tenía un atributo único
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Impuestos

* _ACP2E-3193_: el impuesto sobre productos fijos (FPT) no funciona con productos configurables
   * _Nota de corrección_: FPT para las variaciones de productos configurables funciona correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Marco de prueba

* _AC-13362_: [Problema] ortografía de corrección de PHPDoc
   * _Nota de corrección_: el sistema ahora reconoce correctamente los métodos obsoletos en IDE debido a una corrección ortográfica en PHPDoc. Anteriormente, un error ortográfico en el PHPDoc provocaba que los IDE no reconocieran determinados métodos como obsoletos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/31399>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: comprobando el comportamiento con el carro de compras persistente después de que caduque la sesión
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: las pruebas de integración no se superaron Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Nota de corrección_: Mftfs fijos
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Marco de IU

* _AC-12432_: Campo De Archivo De Componente De Interfaz De Usuario
   * _Nota de corrección_: el sistema ahora valida correctamente el campo de archivo en un formulario de componente de interfaz de usuario, lo que permite enviar el formulario sin errores cuando se selecciona un archivo. Anteriormente, la validación fallaba incluso cuando se seleccionaba un archivo, lo que impedía el envío del formulario.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38908>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Problema] Se mejoró el formato de fecha en la consola js: cambia de 12 horas a 24 horas para...
   * _Nota de corrección_: Se ha mejorado el formato de fecha en la consola js: cambie de 12 horas a 24 horas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38983>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problema] al agregar la generación de sourceMap para menos archivos en modo de desarrollador
   * _Nota de corrección_: El sistema ahora genera asignaciones de origen para menos archivos cuando se encuentra en modo de desarrollador, lo que facilita la identificación del origen de un estilo. Anteriormente, la identificación del origen de un estilo era difícil al ejecutar el sistema en modo de desarrollador con menos compilación en el lado del servidor.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38982>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38977>
* _AC-13459_: comportamiento incoherente en la ordenación &quot;sin existencias&quot; con el umbral de existencias mínimo
   * _Nota de correcciones_: El sistema ahora ordena correctamente los productos del catálogo según los niveles de existencias, cumpliendo el umbral de existencias mínimo establecido y moviendo los artículos sin existencias al final de la lista de forma consistente. Anteriormente, el comportamiento de ordenación era incoherente, ya que los elementos no siempre aparecían en el orden correcto según sus niveles de stock, y los cambios en la ordenación podían producirse de forma impredecible después de guardar, actualizar o modificar la jerarquía de categorías.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Sugerencia para mejorar los informes de errores en los problemas de carga de require.js
   * _Nota de corrección_: esta PR mejora el mensaje de error cuando requireJs no puede cargar un componente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36761>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [Problema] Eliminar resumen de revisión de scripts innecesarios
   * _Nota de corrección_: El sistema ahora optimiza el tiempo de carga de la página eliminando los scripts de JavaScript innecesarios de la sección de clasificación, en lugar de utilizar estilos CSS en línea para lograr un código más eficiente y legible. Anteriormente, el uso de scripts de JavaScript para la sección de clasificación podía ralentizar el tiempo de carga de la página.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37776>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: Encabezado del sitio | Caracteres especiales que rompen la sección de Bienvenida al cliente
   * _Nota de corrección_: después de la corrección, los caracteres especiales se muestran correctamente en la sección de bienvenida del cliente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
