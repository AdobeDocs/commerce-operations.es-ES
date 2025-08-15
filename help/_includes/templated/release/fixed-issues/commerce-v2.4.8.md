---
source-git-commit: 1f377ab6e4dcdd2d350366f3889b8befd233474b
workflow-type: tm+mt
source-wordcount: '27924'
ht-degree: 0%

---
# Problemas corregidos de Adobe Commerce (v2.4.8)

## Se han corregido problemas en la versión 2.4.8

Hemos corregido 581 problemas en el código principal de Adobe Commerce 2.4.8. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

#### La API de REST /V1/transactions devuelve un error cuando parent_txn_id = txn_id

El sistema ahora gestiona correctamente las transacciones de concepto principal y secundario donde el ID de transacción principal es el mismo que el ID de transacción, lo que evita un bucle infinito al consultar el punto final de la API REST /V1/transactions. Anteriormente, este escenario resultaba en un error grave debido a que se superaba el tiempo máximo de ejecución.

_AC-10042 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### [Graphql] problema de tipo en 2.4.7

El sistema ahora administra correctamente los valores enteros en la función GetCustomSelectedOptionAttributes al ejecutar una consulta GraphQL, lo que evita errores relacionados con el tipo. Anteriormente, al iniciar una consulta GraphQL que usaba GetCustomSelectedOptionAttributes con un argumento entero se producía un error de tipo.

_AC-11878 - [Problema de GitHub](https://github.com/magento/magento2/issues/38662) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38663)_

#### Caracteres especiales de la categoría url_key (cuando se crea mediante la API de REST)

Anteriormente, en category_url_key, el carácter especial no está allí después de la corrección, sino que muestra un carácter especial en category_url_key

_AC-3223 - [Problema de GitHub](https://github.com/magento/magento2/issues/35577) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### API de REST que muestra pedidos de otro sitio web. 

El sistema ahora admite el acceso autorizado de ámbito para tokens de administrador de API de REST y puntos finales de Magento_Sales, lo que garantiza que la API de REST solo muestre los pedidos a los que el administrador tiene acceso. Anteriormente, la API de REST mostraba pedidos de todos los sitios web, independientemente del sitio web asignado al usuario administrador.

_ACP2E-2703_

#### Problema con la API de REST después de habilitar el dúo 2FA

La opción de seguridad 2FA con Duo ahora genera la firma correcta para la API de REST

_ACP2E-2755 - [Contribución de código de GitHub](https://github.com/magento/security-package/commit/412fa642)_

#### [API REST]: Usar valor predeterminado en la vista de tienda no permanece marcado después de agregar configuraciones para un producto configurable

El problema se ha corregido asegurando entradas de base de datos correctas para las opciones personalizables de un almacén no predeterminado. La casilla de verificación de la tienda personalizada en la sección &quot;admin > Catálogo > Edición de productos > Opciones personalizables&quot; se desmarcó anteriormente debido a entradas de base de datos inexactas, incluso si el título de la opción de la tienda personalizada seguía siendo el mismo que el almacén predeterminado.

_ACP2E-2927 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### La API de REST no puede realizar solicitudes con una barra (/) en el SKU al usar Oauth1

Antes de la corrección, no podía realizar una llamada de API correcta para un producto que tuviera &quot;/&quot; en su SKU. Ahora, puede realizar una solicitud de obtención de API correcta para obtener detalles del producto aunque su SKU tenga una barra diagonal.

_ACP2E-2969 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### Error al actualizar la dirección del cliente al actualizar mediante la API de REST si &quot;validateDefaultAddress&quot; está habilitado

El extremo de la API ahora funciona como estaba previsto después de que se haya resuelto el problema con la clave de ID que falta en la carga útil de la API.

_ACP2E-3079 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### [Cloud] creando el grupo de clientes de precios de grupo de sitios web duplicado en la API de precios de nivel.

Ahora, la API de REST de precios de nivel no permite crear el grupo de clientes de precios de grupo de sitios web Duplicado.
Anteriormente, era posible crear el grupo de clientes de precios de grupo de sitios web Duplicados en la Api de precios de nivel que no pasaba la validación en Administración durante el guardado del producto.

_ACP2E-3091 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### No se puede agregar un comentario de pedido con el estado mediante la API de REST

El problema se ha resuelto permitiendo el cambio en el estado del pedido si solo es del estado actual. Anteriormente, no respetaba el estado de la solicitud e impedía realizar cambios en cualquier estado de la solicitud, aunque fuera del mismo estado.

_ACP2E-3130 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### La operación asincrónica falla cuando falta el SKU en la carga útil

Anteriormente, las operaciones asincrónicas y de sincronización no se ejecutaban debido a errores al guardar el producto si faltaba el SKU en la carga útil. Después de la corrección, las operaciones de API de rest de guardado de producto asincrónico y sincrónico fallan con un mensaje de excepción relevante.

_ACP2E-3236 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### [CLOUD] No se pueden actualizar los precios base mediante la API de REST (el valor de &#39;value_id&#39; en &#39;catalog_product_entity_decimal&#39; no se incrementa correctamente).

Anteriormente, cuando se llamaba a rest api /rest/default/V1/products/base-price, el ID de incremento aumentaba incorrectamente, lo que dejaba un espacio entre los valores. Después de la corrección, el ID de incremento se incrementa según lo esperado. También se aumentó el rango del campo value_id.

_ACP2E-3376 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Los elementos de pedido no están visibles en los correos electrónicos de nota de crédito para la API POST V1/order/:orderId/return

Anteriormente, antes de esta corrección, cuando un cliente crea un abono a partir de una solicitud de API que notifica a send_email, no contiene la cuadrícula de detalles del producto. Después de aplicar esta corrección, el cliente envía una solicitud de API de nota de crédito y encontrará los detalles del elemento de producto que aparecen en el correo electrónico.

_ACP2E-3460 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### No se establecen valores predeterminados para los atributos de fecha y hora con productos RestAPI

Los valores predeterminados ahora se establecen correctamente para los atributos de fecha y hora a través de RestAPI

_ACP2E-3486 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### API, carro y cierre de compra

#### Error crítico 500: Magento\Framework\Webapi\Exception Relacionado con Aceptar encabezado HTTP

Después de la corrección, no hay problema con especificar el encabezado &quot;Accept&quot;.

_ACP2E-3343 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

### API, GraphQL

#### no hay ningún graphQl disponible para suscribirse a las actualizaciones de puntos de recompensa para el cliente

Antes de la corrección, el atributo de cliente premio_advertencia_notificación no se podía actualizar mediante la mutación de GraphQL y la llamada a la API de REST. Ahora se puede actualizar de la misma forma que el atributo de cliente premio_actualizar_notificación.

_ACP2E-3348_

### API, GraphQL, Impuestos

#### Luma (API de REST) y Graphql no calculan los impuestos cuando solo se proporciona código postal.

El sistema ahora calcula correctamente los impuestos cuando solo se proporciona un código postal, lo que garantiza estimaciones fiscales precisas tanto para Luma (API de REST) como para GraphQL. Anteriormente, solo se calculaban las estimaciones de envío y no se incluían los impuestos cuando solo se proporcionaba un código postal.

_AC-12060_

### Cuenta

#### El formulario de dirección del cliente permite código aleatorio en los campos de nombre

El sistema ahora valida la entrada en los campos Nombre y Apellidos del formulario de dirección del cliente, lo que impide el uso de código aleatorio. Anteriormente, el sistema permitía el uso de código aleatorio en estos campos sin arrojar un error.

_AC-10782 - [Problema de GitHub](https://github.com/magento/magento2/issues/38331) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38345)_

#### admin Actualización de contraseña.

_AC-10886 - [Problema de GitHub](https://github.com/magento/magento2/issues/38352) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4bca5dfe)_

#### bloqueo de añadir dirección de mi cuenta al guardar

El sistema ahora guarda correctamente las direcciones de los clientes incluso cuando no se muestra el campo de región, lo que evita un bloqueo durante el proceso de guardado. Anteriormente, si se intentaba agregar o editar una dirección sin un campo de región mostrado, se producía un error de excepción.

_AC-10990 - [Problema de GitHub](https://github.com/magento/magento2/issues/38406) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38407)_

#### Redirigir el bucle cuando las direcciones URL estén en mayúsculas

El sistema ahora convierte automáticamente los caracteres en mayúsculas en las direcciones URL a minúsculas, lo que evita un bucle de redireccionamiento al acceder a la página principal. Anteriormente, tener caracteres en mayúsculas en la URL de base segura provocaba un bucle de redirección continuo al intentar acceder a la página principal.

_AC-11718 - [Problema de GitHub](https://github.com/magento/magento2/issues/38538) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38539)_

#### los nombres intermedios no se han guardado para las cuentas de invitado

El sistema ahora guarda correctamente el segundo nombre de las cuentas de invitado durante el cierre de compra, lo que hace que sea accesible en la plantilla de correo electrónico. Anteriormente, el segundo nombre no se guardaba en la tabla de comillas y no se podía acceder a él en la plantilla de correo electrónico de las cuentas de invitado.

_AC-11755 - [Problema de GitHub](https://github.com/magento/magento2/issues/38593) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39067)_

#### Administración: botones de acciones de página flotantes a la izquierda en lugar de a la derecha

El sistema ahora alinea correctamente los botones de acción de página a la derecha del encabezado adhesivo en el panel de administración, lo que mejora el aspecto profesional. Anteriormente, estos botones flotaban incorrectamente en el lado izquierdo del encabezado adhesivo.

_AC-11919 - [Problema de GitHub](https://github.com/magento/magento2/issues/38701) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### `dev:di:info` error en magento 2.4.7

El sistema ahora muestra correctamente los parámetros del constructor al ejecutar el comando `dev:di:info`, lo que evita que se produzcan errores. Anteriormente, al ejecutar este comando, se producía un error debido a una discrepancia de tipos en el argumento.

_AC-11999 - [Problema de GitHub](https://github.com/magento/magento2/issues/38740) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### La casilla de verificación de inclusión Iniciar sesión como cliente no se puede traducir

El sistema ahora permite establecer los campos &quot;Iniciar sesión como cliente: casilla de verificación de inclusión&quot; e &quot;Iniciar sesión como cliente: información de objeto&quot; en el ámbito &quot;Vista de tienda&quot;, lo que permite realizar traducciones para distintas vistas de tienda. Anteriormente, estos campos solo se establecían en el ámbito &quot;Sitio web&quot;, lo que impedía las traducciones para vistas de tiendas individuales.

_AC-13000 - [Problema de GitHub](https://github.com/magento/magento2/issues/32329) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32359)_

#### La página principal de la interfaz de usuario del front-end de mi perfil desplegable es que el botón no está allí.(intermitentemente)

_AC-14299_

#### El cliente ha iniciado sesión, pero muestra el error 404 en front-end.

La página del panel del cliente de la tienda ahora se carga como se espera cuando un cliente inicia sesión. Anteriormente, los clientes podían iniciar sesión, pero esta página mostraba un error 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)

_AC-6071 - [Problema de GitHub](https://github.com/magento/magento2/issues/35838) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36263)_

#### No se puede guardar la información de atributos del cliente en la sección de administración Editar cliente;

El ID de tienda del cliente ahora se implementa correctamente por ámbito de sitio web para el formulario de edición del cliente de administración.

_ACP2E-2791 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/488c1034)_

#### [Cloud] no puede crear clientes a través de la API cuando las ventas privadas están habilitadas

Ahora, el usuario administrador autenticado puede crear el cliente, así como con el token de integración autenticado a través de la API de REST cuando la restricción del sitio web está habilitada.

_ACP2E-3115_

#### Después de iniciar sesión, los productos agregados a la lista de comparación como usuarios invitados no son visibles.

Los productos que se añadieron a la lista de comparación de productos antes de iniciar sesión como clientes ahora se conservan después de iniciar sesión.
Anteriormente, después de iniciar sesión, los productos agregados a la lista de comparación como usuarios invitados no eran visibles.

_ACP2E-3329 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Permitir configuración de países causa problemas en las configuraciones de direcciones de clientes

Ahora, seleccionar Permitir configuración de países no influye en los países que se muestran fuera del ámbito determinado. Anteriormente, la configuración de Permitir países influía en el atributo de dirección del cliente fuera del ámbito determinado

_ACP2E-3433 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Shared Gift Registry muestra la fecha del evento 1 día antes

La fecha del registro de regalos se muestra correctamente ahora en Storefront

_ACP2E-3445_

#### VAPT: Error de lógica empresarial, fecha futura como fecha de nacimiento del cliente

La fecha de nacimiento del cliente no se puede establecer después de hoy

_ACP2E-3501 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Cuenta, API, GraphQL

#### API De Cliente: Número De Errores De Inicio De Sesión Que No Se Pueden Restablecer A 0 Tras Un Inicio De Sesión Correcto

Ahora el número de error se restablece a cero en la tabla de entidades del cliente después del inicio de sesión correcto del cliente mediante los extremos de la API.

_ACP2E-3246 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Cuenta, IU de administración, B2B

#### Los usuarios administradores restringidos no siempre pueden ver los catálogos compartidos personalizados

Los usuarios administradores restringidos ahora pueden ver y administrar de forma coherente los clientes y todos los catálogos compartidos a los que están asignados los productos, siempre que tengan acceso al almacén específico. Anteriormente, un usuario administrador restringido con acceso a un almacén determinado no siempre podía ver todos los catálogos compartidos a los que se asignaban los productos o podía ver clientes que no se podían guardar, lo que producía incoherencias en el sistema.

_ACP2E-3038 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7377de59)_

### Cuenta, carro y cierre de compra

#### El atributo de dirección de cliente personalizada &quot;select&quot; no se representa para la nueva dirección de cliente

_AC-2341 - [Problema de GitHub](https://github.com/magento/magento2/issues/34950)_

### IU de administración

#### [Problema]: agregar comprobación de permiso para el botón de datos &quot;recargar datos&quot;

El sistema ahora incluye una comprobación de permisos para el botón &quot;Recargar datos&quot;, lo que garantiza que solo se muestre y sea accesible a los usuarios con los permisos adecuados. Anteriormente, el botón &quot;Recargar datos&quot; era visible y se podía hacer clic en él para todos los usuarios, lo que conducía a una página &quot;no permitida&quot; cuando los usuarios hacían clic sin los permisos necesarios.

_AC-10705 - [Problema de GitHub](https://github.com/magento/magento2/issues/38283) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38279)_

#### [Problema] Etiquetas incoherentes para atributos en reglas de marketing

El sistema ahora rellena correctamente las etiquetas de forma coherente para las opciones de categoría y atributo en la regla de precios del carro de compras

_AC-11427 - [Problema de GitHub](https://github.com/magento/magento2/issues/31232) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31231)_

#### La validación de datos es correcta y el botón Importar está presente durante Importar productos con el comportamiento Reemplazar

El sistema ahora valida correctamente los datos y oculta el botón &quot;Importar&quot; durante el proceso de importación del producto con el comportamiento &quot;Reemplazar&quot;, lo que evita cualquier reemplazo no intencionado de los datos. Anteriormente, el sistema validaba los datos incorrectamente y mostraba el botón &quot;Importar&quot;, lo que producía posibles incoherencias en los datos.

_AC-11588 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Error]: Magento 2.4.7 no permite fotos de productos con extensión de archivo de mayúsculas.

El sistema ahora acepta cargas de imágenes de productos con extensiones de archivo en mayúsculas, lo que garantiza un proceso de creación de productos sin problemas. Anteriormente, las cargas de imágenes con extensiones de archivo de mayúsculas se rechazaban, lo que obligaba a los usuarios a cambiar la extensión del archivo a minúsculas.

_AC-12167 - [Problema de GitHub](https://github.com/magento/magento2/issues/38831) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Menú desplegable oculto en las cuadrículas con acción de selección (por ejemplo, Contenido > Elementos > Páginas)

Ahora el sistema ha sido arreglado todo el menú desplegable similar para todas las cuadrículas.

_AC-12319 - [Problema de GitHub](https://github.com/magento/magento2/issues/38891) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39371)_

#### [Problema] Advertencia de corrección: &quot;filtros&quot; de clave de matriz sin definir

El sistema ahora gestiona escenarios en los que un nuevo usuario aún no ha interactuado con marcadores, lo que evita que se registre una advertencia de &quot;filtros&quot; de clave de matriz indefinida. Anteriormente, esta advertencia se registraba cuando un usuario nuevo no había interactuado con los marcadores.

_AC-13131 - [Problema de GitHub](https://github.com/magento/magento2/issues/39013) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38996)_

#### El archivo csv de importación de productos con caracteres especiales falla debido a cambios en el código en el archivo Validate.php

El sistema ahora valida e importa correctamente los archivos CSV del producto que contienen caracteres especiales, lo que permite la transferencia de datos correcta. Anteriormente, al intentar importar un archivo CSV de productos con caracteres especiales, se producía un error que impedía el proceso de importación.

_AC-13529 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### Cuando el número máximo de solicitudes de restablecimiento de contraseña&quot; está establecido en más de 0, p. ej.: 3 , &quot;Los mensajes de error que exceden el límite se envían antes de alcanzar el límite, es decir, desde la segunda vez

_AC-13767_

#### Aunque &quot;Número máximo de solicitudes de restablecimiento de contraseña&quot; está establecido en 0 ( deshabilitado) , &quot;Los mensajes de error que exceden el límite se envían desde la segunda vez&quot;

_AC-13768_

#### No hay ningún asterisco rojo para el campo obligatorio de número de teléfono

Anteriormente, el asterisco rojo no se mostraba para el número de teléfono, pero  el número de teléfono era obligatorio. Que ahora es un asterisco rojo fijo se puede ver en el número de teléfono como un campo obligatorio.

_AC-13850 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c699c206)_

#### En Administración Cuando intentamos Reordenar el botón de envío del pedido no se puede hacer clic en. (intermitentemente)

_AC-14300_

#### [Problema]: establezca el modo de indizador predeterminado en &#39;programar&#39;.

Todos los indizadores nuevos se encuentran de manera predeterminada en el modo **[!UICONTROL Update by Schedule]**.  Anteriormente, el modo predeterminado era **[!UICONTROL Update on Save]**. Los indexadores existentes no se ven afectados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)

_AC-6975 - [Problema de GitHub](https://github.com/magento/magento2/issues/36419) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0b410856)_

#### [Problema] al eliminar las tablas de registro de cambios del indizador al cancelar la suscripción a mview

El sistema ahora elimina automáticamente las tablas de registro de cambios no utilizadas cuando se cambia un índice de &quot;actualizar según lo programado&quot; a &quot;actualizar al guardar&quot;, marcando el índice como no válido para garantizar que no se pierdan entradas. Anteriormente, cambiar un índice a &quot;actualizar al guardar&quot; dejaba tablas de registro de cambios no utilizadas en el sistema y marcaba todos los índices cambiados como &quot;válidos&quot;.

_AC-7700 - [Problema de GitHub](https://github.com/magento/magento2/issues/29789) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/25859)_

#### Sin vínculo a envío en pagos en la vista de pago en el teléfono móvil

El sistema ahora garantiza que los títulos/vínculos de cierre de compra &quot;Envío&quot; y &quot;Revisión y pagos&quot; estén siempre visibles en la parte superior de la página en la vista móvil, lo que permite a los usuarios navegar fácilmente entre los pasos y realizar las correcciones necesarias. Anteriormente, estos títulos o vínculos estaban ocultos en la vista móvil, lo que dificultaba a los usuarios conocer su paso actual o volver a pasos anteriores.

_AC-7962 - [Problema de GitHub](https://github.com/magento/magento2/issues/36856) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36982)_

#### cliente Los comentarios de envío de consulta de pedidos created_at se devuelven en una zona horaria +0 que no está configurada en la tienda

El sistema ahora muestra correctamente el campo &quot;created_at&quot; de los comentarios de envío en la zona horaria configurada del cliente al utilizar la consulta Pedidos del cliente. Anteriormente, el campo &quot;created_at&quot; se mostraba en la zona horaria +0, independientemente de la configurada por el cliente.

_AC-8109 - [Problema de GitHub](https://github.com/magento/magento2/issues/36947) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37642)_

#### i18n:collect-phrases rompe la integridad de las traducciones

El comando `bin/magento i18n:collect-phrases -o` ahora recopila y agrega correctamente nuevas frases de archivos JavaScript y .phtml, lo que garantiza que las traducciones se reflejen con precisión en el archivo de traducción. Anteriormente, el sistema no incluía frases de traducción multilínea de archivos JavaScript ni frases de archivos .phtml en el archivo de traducción, lo que provocaba traducciones incompletas o incorrectas.

_AC-9843 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Problema de permisos para acceder a Dynamic Block

Anteriormente, para el administrador restringido, al agregar un nuevo bloque dinámico, se producía un error. Después de implementar esta corrección, el administrador restringido puede agregar correctamente el bloque dinámico y editar el bloque sin ningún error

_ACP2E-2687_

#### El nombre de apóstrofo en la vista de tienda se reemplaza por &#039;

Los filtros de vista de tienda de la cuadrícula ahora muestran correctamente los apóstrofos

_ACP2E-2787 - [Problema de GitHub](https://github.com/magento/magento2/issues/38395) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### La carga de Favicon no valida los archivos .ico

El error de validación del archivo se ha actualizado a &quot;Error de validación de archivo. Compruebe la configuración de procesamiento de imágenes en la configuración de la tienda&quot;. Anteriormente, era simplemente &quot;Error de validación de archivo&quot;.

_ACP2E-2847 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### La galería de PageBuilder muestra la miniatura de la imagen antigua en lugar de la imagen recién cargada

Regenerar vistas previas de imágenes para imágenes eliminadas y recargadas con el mismo nombre mediante la galería de medios en el contenido del generador de páginas.

_ACP2E-2957 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/001e5188)_

#### Al guardar el producto por un usuario administrador con un ámbito de función diferente, se sobrescribe o elimina la información de producto relacionada existente en el producto

Anteriormente, antes de la corrección, los productos relacionados se restablecían y se volvían vacíos cuando el usuario administrador secundario hacía clic en el botón Guardar sin cambiar en el producto relacionado. Después de esta corrección, el usuario administrador secundario hace clic en el botón guardar y el producto no se restablece y se guarda correctamente.

_ACP2E-2978 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### No se pueden exportar más de 200 pedidos

Los límites del servidor para el tamaño de la solicitud de los ID seleccionados enviados anteriormente se han descuidado al modificar la solicitud HTTP de GET a POST para solucionar el problema. Anteriormente, debido a las limitaciones del servidor para el tamaño de la solicitud de GET, se encontraba el problema.

_ACP2E-3033 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Mensaje de validación de página de cierre incorrecto.

Si se deja vacío cualquier campo requerido, como &quot;dirección&quot;, la validación del lado del servidor no mostrará el mensaje. La validación del lado del cliente garantizará que aparezca la notificación de error del campo requerido, que indica &quot;Este es un campo obligatorio&quot;. Anteriormente, aparecía el mensaje &quot;la dirección es obligatoria&quot; si se dejaba vacío cualquier campo requerido, además del mensaje de validación del lado del cliente.

_ACP2E-3037 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### Problema de plantilla de restablecimiento de contraseña con usuario administrador

El problema se ha resuelto mediante la clave correcta, que ahora incluye el nombre de usuario del administrador en la plantilla de correo electrónico y completa correctamente el asunto. Anteriormente, el problema se debía a una clave obsoleta que se estaba utilizando.

_ACP2E-3125 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Barras dobles en la URL del segmento del cliente

Las barras dobles no aparecen en la dirección URL cuando se hace clic en &#39;Restablecer filtro&#39; en la cuadrícula.

_ACP2E-3149 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### La DQO no está disponible para países específicos permitidos

Ahora, el Pago contra reembolso está disponible para países específicos permitidos siempre que sea necesario y   AC-3216 funciona según lo esperado.

_ACP2E-3171 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### No se puede actualizar el estado del pedido creado personalizado

&#39;Ahora podemos actualizar los estados de pedidos creados a medida, mientras que anteriormente el estado solo se podía cambiar si el estado actual era &quot;Procesando&quot; o &quot;Fraude&quot;.

_ACP2E-3178 - [Problema de GitHub](https://github.com/magento/magento2/issues/38659) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### El estado de la dirección de envío no se actualiza automáticamente

Antes de la corrección, la región de la dirección de envío (o el ID de región) no estaba sincronizada con la información de facturación de la dirección. Ahora, tanto la región de la dirección de envío como el ID de región se actualizan correctamente cuando se cambia la información de la dirección de facturación.

_ACP2E-3294 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### El botón Restablecer no funciona en Añadir/Editar usuario administrador

Anteriormente, el botón Restablecer no funcionaba en la página Agregar/Editar usuario administrador. Ahora, en el panel Administración en Sistema -> Permisos -> Todos los usuarios, el botón Restablecer funcionará correctamente en la página Agregar/Editar usuario administrador.

_ACP2E-3364 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Detección de errores de enrutamiento de URL de administración de Magento y errores CORS

Después de la corrección, si el dominio de administración personalizado es un subdominio del dominio principal, el administrador solo es accesible desde el subdominio configurado.

_ACP2E-3373 - [Problema de GitHub](https://github.com/magento/magento2/issues/37663) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Validación interrumpida para &quot;Cantidad máxima permitida en el carro de compras&quot;

Anteriormente, cuando se ponía `Maximum Qty Allowed in Shopping Cart` empty, no se producía ninguna excepción, aunque no se acepta un valor vacío aquí. Una vez aplicada esta corrección, al colocar una cadena vacía se producirán excepciones y no se permitirá guardar el producto.

_ACP2E-3392 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Problema de interfaz de usuario de vista previa de Page Builder] Los botones de la columna Page Builder no se alinean correctamente

Los botones de las columnas de Page Builder ahora están correctamente alineados. Anteriormente, se desalineaban dentro de las columnas de Page Builder.

_ACP2E-3408 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_

#### El informe Productos pedidos no se está exportando. Error 404 en su lugar.

La exportación de informes ordenada de productos a CSV y XML ahora funciona según lo esperado

_ACP2E-3431 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### Error de TinyMCE JS en la consola después de habilitar la minificación Js con el modo de producción

Anteriormente, al habilitar la minificación de JavaScript en el modo de producción dentro del panel de administración, aparecían errores de JavaScript relacionados con TinyMCE 6 en la consola del explorador, lo que afectaba a la funcionalidad y la experiencia del usuario. Ahora, este problema se ha resuelto, lo que garantiza que TinyMCE 6 funcione sin problemas sin generar errores, incluso cuando la minificación JS esté habilitada.

_ACP2E-3457 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### Solicitud de cambios adicionales para completar completamente la corrección de ACP2E-3375

&#39;-

_ACP2E-3459 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Habilitación automática de nuevos permisos ACL

Los nuevos permisos añadidos a los módulos personalizados ya no otorgarán acceso automáticamente a todas las funciones de usuario existentes a menos que se configuren explícitamente.

_ACP2E-3503 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### El informe de usuario de registro de acciones de administración no muestra detalles de admin_user_delete

El adminhtml_user_delete ahora registra correctamente detalles importantes. Anteriormente, no se generaban registros para las eliminaciones de usuarios.

_ACP2E-3509 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4de008a9)_

#### Regla de carro de compras con condición de envío que no se aplica al realizar un pedido del administrador

Anteriormente, si la regla de precio del carro de compras tenía un descuento en el método de envío con el cupón, no se podía aplicar a través de la IU de administración. Después de aplicar esta corrección, la IU de administración aplica correctamente el descuento de la regla de precio del carro de compras con un cupón para un método de envío específico.

_ACP2E-3536 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a52ff98f) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/11ce816b)_

#### El código HEX [FRESH] no se actualiza correctamente en la MUESTRA

El sistema ya no modifica el código HEX que el usuario introduce manualmente en el selector de color de la muestra visual. Anteriormente, algunos códigos HEX experimentaban ligeros ajustes debido a errores de conversión entre modelos de color.

_ACP2E-3559 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/344fce23) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/1ef984c0)_

### IU de administración, B2B

#### El inicio de sesión B2B como encabezado de cliente sigue teniendo la marca Magento

Anteriormente, el encabezado de la tienda muestra &quot;Ahora está conectado como &lt;nombre del cliente> en &lt;nombre de la tienda>&quot; con la marca Magento. Que ahora es fijo y el encabezado se muestra con la marca ADOBE.

_AC-13628 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/96dec499)_

### IU de administración, catálogo

#### No se pueden cambiar las posiciones de los productos de la categoría en el sitio web permitido como usuario administrador restringido

Permitir que un usuario administrador restringido añada y ordene productos en una categoría contenida en la categoría raíz asignada en el sitio web restringido.

_ACP2E-2708_

### IU de administración, métodos de pago/pago, pedido

#### Autorización de transacción no mostrada en la pestaña Transacción después de realizar el pedido del botón inteligente de PayPal

El sistema ahora muestra correctamente la autorización de la transacción en la pestaña Transacción después de realizar un pedido con el botón inteligente de PayPal. Anteriormente, la transacción de autorización no aparecía en la pestaña Transacción después de hacer clic en el botón &quot;Autorizar&quot; y no se creaba ninguna nueva transacción de tipo &quot;Autorización&quot;.

_AC-13520 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

### IU de administración, rendimiento

#### Después de la actualización a 2.4.5-p8 se producen errores de 500 al crear el pedido del administrador

Anteriormente, al habilitar la minificación de HTML, no se podía realizar un pedido del administrador. Ahora, con la minificación de HTML habilitada, el pedido del administrador se puede realizar correctamente.

_ACP2E-3169 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### IU de administración, envío

#### El recuento de código de cupón no se actualiza en la   Columna &quot;Tiempo utilizado&quot; en la pestaña Administrar códigos de cupón si se realiza un pedido con varios envíos.

Anteriormente, cuando se realizaba un pedido con varios envíos, el recuento de códigos de cupones no se actualizaba en la columna &quot;Tiempo utilizado&quot; de la pestaña Administrar códigos de cupones. Ahora, el recuento correcto se muestra tanto en el &quot;Tiempo utilizado&quot;, que refleja los valores deseados con envío múltiple.

_ACP2E-2519 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4745100c)_

### IU de administración, ensayo y vista previa

#### [Nube] Al eliminar la plantilla con imágenes faltantes, se eliminan los medios/pub

Anteriormente, si faltaba el nombre de la imagen de vista previa para una plantilla de pagebuilder, se eliminaba la carpeta pub/media. Después de la corrección, solo se eliminará la plantilla y la imagen de vista previa si se encuentra.

_ACP2E-3424 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Análisis / Informes

#### Error de CSP de Google Analytics https://region1.analytics.google.com

El sistema ahora permite correctamente conexiones a &quot;https://region1.analytics.google.com&#39;&quot; cuando Google Analytics está habilitado, lo que evita errores de la Política de seguridad de contenido (CSP). Anteriormente, habilitar Google Analytics y ver el sitio web desde la UE resultaba en errores de la consola CSP debido a la negativa a conectarse a &quot;https://region1.analytics.google.com&#39;&quot;.

_AC-9922 - [Problema de GitHub](https://github.com/magento/magento2/issues/37750) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38991)_

#### El informe avanzado no funciona

El sistema ahora admite la generación de archivos de datos de informes avanzados para conjuntos de datos extragrandes cargando y escribiendo informes en lotes de 10 000. Anteriormente, el módulo de informes avanzados no podía generar archivos de datos para conjuntos de datos extragrandes, lo que provocaba errores &quot;MySQL server has gone away&quot; durante la ejecución del trabajo cron analytics_collect_data.

_ACP2E-2570 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Problema de visibilidad del intervalo de fechas del informe de productos ordenados por el administrador.

El usuario puede seleccionar cualquier fecha del informe de productos solicitados. Anteriormente, después de actualizar la tabla, al seleccionar la fecha &quot;DESDE&quot; se restablecía la fecha &quot;HASTA&quot;.

_ACP2E-3080 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Encabezados curl incorrectos que hacen que `newrelic:create:deploy-marker` no funcione

El sistema ahora da formato correctamente a los encabezados curl, lo que permite que el comando `newrelic:create:deploy-marker` cree correctamente un marcador de implementación en New Relic. Anteriormente, unos encabezados curl incorrectos impedían la creación de un marcador de implementación en New Relic.

_ACP2E-3096 - [Problema de GitHub](https://github.com/magento/magento2/issues/37641) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Falta el evento addToCart de GTM en dataLayer para un producto configurable con opción personalizada

Anteriormente, el evento addToCart no se activaba para los productos configurables. Ahora, el evento se agrega correctamente a la variable dataLayer de GTM.

_ACP2E-3146_

#### La monitorización del explorador NewRelic mediante scripts inlineJS provoca errores CSP

Los scripts de monitorización del explorador de NewRelic ahora los inserta la aplicación en lugar del agente de APM para el cumplimiento con la CSP (Política de seguridad de contenido). Anteriormente, los scripts de monitorización del explorador de NewRelic insertados por el agente de APM no eran compatibles con el CSP y provocaban que los scripts no se ejecutaran.

_ACP2E-3183 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Las consultas INSERT a la tabla sales_bestsellers_aggregated_daily se ralentizan en un proyecto con un gran volumen de pedidos de ventas

Anteriormente, el informe diario agregado de superventas tardaba mucho tiempo en generarse para un gran volumen de pedidos realizados. Ahora el informe se genera de manera oportuna.

_ACP2E-3189 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Informes de pedidos que muestran el símbolo de moneda incorrecto

El símbolo de divisa de los importes de pedido del informe de pedidos se ha tomado incorrectamente de la divisa, las opciones o la base. Ahora se ha corregido para utilizar moneda/opciones/predeterminado para un sistema de informes preciso.

_ACP2E-3276 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Nube] cálculos incorrectos en informe de uso de cupones

El total de ventas en la cuadrícula del informe de cupones ahora se calcula con precisión incorporando tanto el &quot;Importe de compensación fiscal de descuento&quot; como el &quot;Importe de compensación fiscal de descuento de envío&quot;. Anteriormente, estas cantidades no aparecían en el cálculo, lo que producía discrepancias entre el total de ventas y los datos del pedido de ventas.

_ACP2E-3302 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Problemas con el &quot;&lt;project_id>/var/tmp&quot; compartido

Los archivos temporales de exportación de datos de Analytics utilizarán el directorio sys tmp, que es más adecuado para accesos y cambios frecuentes. Para evitar conflictos en caso de que se ejecuten varias instancias en el mismo servidor, la ruta tmp se actualizó para utilizar un ID único de instancia

_ACP2E-3339 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Análisis / Informes, B2B

#### B2B: el mapa del sitio incluye productos/categorías no asignados al catálogo compartido

Restrinja las categorías y productos generados por el mapa del sitio a las categorías y productos asignados únicamente al catálogo compartido público y/o a la configuración de permisos de categoría del catálogo.

_ACP2E-2300 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analytics / Creación de informes, Cloud

#### Magento descarta la mayoría de las transacciones cron de New Relic #34108

AC informa correctamente de las transacciones relacionadas con trabajos de cron a NewRelic. Anteriormente, algunas transacciones relacionadas con trabajos de cron se mostraban como &quot;OtherTransaction/Action/unknown&quot; en NR

_ACP2E-3067 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### La métrica en NR puede ser engañosa para transacciones en segundo plano- Seguimiento de ACP2E-3067

Las transacciones en segundo plano (cron) utilizarán el nombre de la aplicación de New Relic definido en la configuración

_ACP2E-3187 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

#### Paquete 2.4.8-beta102 Enterprise Edition falla con excepciones de aplicación

_AC-13501_

#### Los productos asignados al catálogo compartido no se reflejan en el front-end cuando se ejecuta el índice parcial

Los productos asignados al catálogo compartido mediante la API de REST ahora son visibles inmediatamente en la tienda una vez completada la indexación parcial. Anteriormente, los productos solo eran visibles después de una reindexación completa.

_ACP2E-2139 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### [Nube] El precio mostrado en la versión para móviles y equipos de escritorio no es el mismo en &quot;Mis presupuestos&quot;

La línea de impuestos de inclusión innecesaria ya no se muestra en la oferta negociable cuando se gasta la sección de precio total del catálogo.

_ACP2E-2873_

#### Bordes innecesarios en la sección Mis pedidos

Anteriormente se creaba un contenedor adicional (referencias de pedidos) que aplicaba clases CSS adicionales, lo que provocaba que aparecieran líneas de borde innecesarias debajo del número de pedido dentro de la sección Mis pedidos, que ahora no es visible.

_ACP2E-3044 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### sales_clean_quote cron elimina las ofertas de los pedidos de compra aún aprobados

El trabajo cron sales_clean_quote no eliminará las ofertas utilizadas en los pedidos de compra ahora

_ACP2E-3247 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### El botón Realizar pedido desaparece en Detalles del pedido de compra

Se ha corregido un problema por el cual el botón Realizar pedido se ocultaba para pedidos de compra aprobados cuando una variación de producto tenía un número mínimo en la tarjeta especificada

_ACP2E-3465_

#### [NUBE] No existe esa entidad con id = 0 con módulo b2b

El usuario que ha iniciado sesión puede añadir un producto al carro de compras cuando las funciones de catálogo compartido están habilitadas.
Si se agregaba anteriormente un producto al carro, se producía el error &quot;no existe esa entidad con ID = 0&quot;

_ACP2E-3474_

#### No se muestra ningún mensaje de error para nuestra lista de productos de stock al añadir masivamente desde la lista de solicitudes

Antes de la corrección, se mostraba un mensaje de éxito independientemente del número de productos que no se añadían al carro de compras. Ahora se muestran mensajes independientes para los productos que se agregaron correctamente al carro de compras y para los productos que fallaron.

_ACP2E-3562_

#### Problema con las actualizaciones de SKU después de actualizaciones programadas que causan permisos de producto incorrectos (-2 denegar)

La modificación del SKU de un producto con actualizaciones programadas anteriores ya no hace que el producto sea inaccesible para los clientes del catálogo compartido con derecho a ver el producto.

_ACP2E-3628_

### B2B, catálogo

#### Productos/categorías visibles durante la reindexación al utilizar los permisos NoDDL y de Categoría

Evite mostrar en la tienda categorías restringidas y su contenido mientras se realiza la indexación de permisos de catálogo.

_ACP2E-2860_

### B2B, marco

#### Filtrar la cuadrícula de la empresa y, a continuación, intentar exportar el CSV de la cuadrícula producirá un error y generará una excepción

El sistema ahora permite la exportación correcta de CSV de los datos de cuadrícula de Compañías en el panel de administración, incluso cuando se aplican filtros como &quot;Saldo pendiente&quot; y &quot;Tipo de compañía&quot;. Anteriormente, si se aplicaban ciertos filtros y se intentaba exportar los datos de la cuadrícula, se producía un error y se producía una excepción.

_AC-9607 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B, GraphQL

#### [Cloud] no puede establecer custom_attributes mientras la compañía crea la llamada de graphql

Después de la corrección, es posible establecer el atributo &quot;custom_attributes&quot; para el administrador de la empresa durante la creación de la empresa mediante una solicitud de graphql.

_ACP2E-3391_

### Braintree

#### El botón de cierre de compra rápido del administrador está desactivado.

_AC-14293_

#### Pagar a través de LPM

El sistema ahora procesa correctamente los métodos de pago locales (LPM) en la carga inicial, incluso cuando las direcciones de envío y facturación de un cliente que ha iniciado sesión no coinciden, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, una discrepancia entre las direcciones de envío y facturación de un cliente impedía que LPM se representara, lo que causaba posibles interrupciones durante el cierre de compra.

_PAQUETE-3367_

#### Configurable con producto virtual como secundario

El sistema ahora permite métodos de pago exprés para productos configurables que tienen un producto secundario virtual, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, los métodos de pago exprés no estaban disponibles cuando se agregaba al carro de compras un producto configurable con un producto secundario virtual.

_PAQUETE-3368_

#### Error de comprobación de CVV

_PAQUETE-3369_

#### Problemas de área de la cuenta 247

El sistema ahora permite a los clientes guardar la nueva información de la tarjeta o de la cuenta PayPal en varios sitios web sin encontrar errores de autorización. Anteriormente, los clientes no podían guardar nuevos métodos de pago en diferentes sitios web y se les presentaba un mensaje de error de autorización.

_PAQUETE-3370_

#### Enviar a una dirección de un país diferente

El sistema ahora permite que las transacciones se procesen sin errores cuando se envían a una dirección de un país diferente, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, intentar enviar a una dirección de un país diferente resultaba en errores de consola, a pesar de que no había errores visibles en el front-end.

_PAQUETE-3371_

#### Tarjeta de crédito: función de desmontaje

El sistema gestiona ahora correctamente el desmontaje de los componentes de Braintree PayPal cuando un cliente regresa de la página de pago a la página de envío, lo que evita cualquier error y garantiza que los botones de PayPal Express se representen correctamente. Anteriormente, al volver a la página de envío desde la página de pago, a veces se producía un error al intentar desmontar los componentes de Braintree PayPal.

_PAQUETE-3372_

#### Devolución de llamada de envío para PayPal Express

El sistema ahora muestra correctamente los métodos de envío disponibles en el modal PayPal Express, lo que permite a los clientes seleccionar su método de envío preferido antes de pasar a la página de revisión o completar su transacción. Anteriormente, no había métodos de envío disponibles para seleccionar en el modal PayPal Express, lo que requería que los clientes seleccionaran un método de envío en una página de revisión independiente antes de poder completar su transacción.

_PAQUETE-3373_

### Paquete

#### Validación de casilla de verificación del paquete de tienda Recuento de mensajes de error más de 1

El sistema ahora solo muestra un mensaje de error de validación cuando se hace clic en el botón &quot;Agregar al carro de compras&quot; sin seleccionar ninguna opción de casilla de verificación para un producto agrupado. Anteriormente, el sistema mostraba varios mensajes de error de validación para cada casilla de verificación no seleccionada.

_AC-10826 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### Se produjo una excepción de Magento en algunos casos de prueba relacionados con pedidos

El sistema ahora administra correctamente el paso &#39;sendGuestPaymentInformation&#39; en varios casos de prueba, lo que evita que se produzcan excepciones de Magento. Anteriormente, estas excepciones se producían debido a un método de pago nulo, lo que provocaba errores en varios casos de prueba.

_AC-13321_

### Carro y cierre de compra

#### La excepción no se gestiona correctamente al añadir un producto al carro de compras en la página de comparación de productos

El sistema ahora gestiona correctamente las excepciones al añadir un producto al carro de compras desde la página de comparación de productos, mostrando un mensaje del gestor de mensajes en el controlador. Anteriormente, una excepción provocaba que se devolviera una página con codificación JSON en lugar de capturarse y gestionarse correctamente.

_AC-10660 - [Problema de GitHub](https://github.com/magento/magento2/issues/38200) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38257) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### GTag no envía los precios ni los totales de las transacciones.

El sistema ahora envía correctamente los precios y totales de las transacciones a Google Tag cuando GTag está habilitado, lo que garantiza un seguimiento preciso de los datos de comercio electrónico. Anteriormente, la moneda se enviaba incorrectamente como parte de los pedidos &quot;todos&quot;, en lugar de asociarse con el pedido individual.

_AC-10698 - [Problema de GitHub](https://github.com/magento/magento2/issues/37348) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37504) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37349)_

#### [Problema] [Cierre de compra] Directivas dependientes actualizadas en la plantilla de correo electrónico de pago con errores

El sistema ahora omite correctamente la dirección de envío y el método de envío de la plantilla de correo electrónico de pago fallido para productos virtuales, lo que garantiza que solo se incluya información relevante en el correo electrónico. Anteriormente, el correo electrónico de pago erróneo para productos virtuales incluía incorrectamente la dirección de envío y el método de envío.

_AC-11641 - [Problema de GitHub](https://github.com/magento/magento2/issues/32781) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32511)_

#### Error de inicio de sesión de Magento 2 dentro del cierre de compra con el cliente existente en el navegador Firefox.

El sistema ahora permite a los usuarios iniciar sesión durante el proceso de cierre de compra sin encontrar errores de consola en el navegador Firefox. Anteriormente, si se intentaba iniciar sesión como un cliente existente durante el cierre de compra, se producía un error de consola en Firefox.

_AC-11717 - [Problema de GitHub](https://github.com/magento/magento2/issues/38557) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39509)_

#### [Problema]: regresión de reglas de ventas en 2.4.7

El sistema ahora valida correctamente las reglas de ventas, lo que impide la aplicación de un código de cupón a un carro de compras cuando la condición del producto no coincide con ningún nombre de producto. Anteriormente, se podía aplicar una regla de ventas y aplicar un descuento en el importe de envío incluso cuando la condición del producto no coincidía con ningún nombre de producto.

_AC-11876 - [Problema de GitHub](https://github.com/magento/magento2/issues/38671) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### [Problema] Cálculo CartFixed de regla de ventas: cantidad de descuento incorrecta

El sistema ahora calcula correctamente el importe de descuento de las reglas de ventas con importes fijos del carro de compras, lo que garantiza que se apliquen descuentos precisos independientemente de los cambios en los elementos del carro de compras. Anteriormente, la cantidad de descuento podía variar incorrectamente cuando cambiaban los artículos del carro de compras, lo que a veces resultaba en descuentos significativamente mayores de lo esperado.

_AC-11914 - [Problema de GitHub](https://github.com/magento/magento2/issues/38694) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### [Problema]: el cargador bloquea los métodos de envío después de que se cambie el código postal y las reglas de validación de tarifas de envío

El sistema ahora gestiona correctamente los métodos de envío personalizados sin reglas de validación de tarifas de envío, lo que garantiza que el cargador no bloquee los métodos de envío después de que se cambie el código postal en la dirección de envío durante el cierre de compra. Anteriormente, si se cambiaba el código postal en la dirección de envío durante la desprotección, el cargador bloqueaba los métodos de envío y no desaparecía cuando se utilizaban métodos de envío personalizados sin reglas de validación de tarifas de envío.

_AC-11993 - [Problema de GitHub](https://github.com/magento/magento2/issues/38742) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La función de código de cupón no funciona correctamente en la página de pago en Magento 2.4.7

El sistema ahora habilita el campo de entrada de código de descuento/cupón en la página de pago para productos virtuales y descargables, lo que permite a los usuarios aplicar códigos de descuento según lo esperado. Anteriormente, la entrada del código/cupón de descuento estaba desactivada y el texto del título del botón se mostraba como &quot;Cancelar cupón&quot;, lo que impedía a los usuarios aplicar códigos de descuento.

_AC-12170 - [Problema de GitHub](https://github.com/magento/magento2/issues/38826) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La casilla de verificación de Términos y condiciones no permite HTML en la tienda

El sistema ahora admite el formato HTML en el texto de la casilla &quot;Términos y condiciones&quot; de la tienda, lo que permite una mayor personalización y legibilidad. Anteriormente, el texto de la casilla de verificación se mostraba en formato de texto sin formato, ignorando las etiquetas de HTML utilizadas.

_AC-12479 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### La regla de precio de carro de compras creada para el usuario que ha iniciado sesión incorrectamente se aplica para el usuario que no ha iniciado sesión

El sistema ahora elimina correctamente la regla de precio del carro de compras para los usuarios que iniciaron sesión cuando cierran sesión automáticamente debido a la caducidad de la cookie, lo que garantiza que el descuento no se aplique a los usuarios que no iniciaron sesión. Anteriormente, la regla de precio del carro de compras se seguía aplicando incluso cuando se cerraba la sesión del usuario, lo que provocaba que se aplicara un descuento incorrecto a los usuarios que no iniciaban sesión.

_AC-12541 - [Problema de GitHub](https://github.com/magento/magento2/issues/38944) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problema] [CARACTERÍSTICA] Optimización del rendimiento para carros de compras grandes al evitar...

El sistema ahora optimiza el rendimiento de los carros de compras grandes al evitar llamadas getActions duplicadas, lo que mejora la velocidad y la eficacia de las operaciones del carro de compras. Anteriormente, para un carro de compras con varios elementos, se llamaba varias veces a la función getActions, lo que ralentizaba el rendimiento del sistema.

_AC-13302 - [Problema de GitHub](https://github.com/magento/magento2/issues/39292) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39290)_

#### Registro de regalos El producto no se muestra correctamente

_AC-13797_

#### Registro de regalos El producto no se muestra correctamente

_AC-13841_

#### IVA de traducción en el procesador de direcciones

El sistema permite ahora la traducción del texto &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; en los procesadores de direcciones, lo que permite a los usuarios traducir estos términos al idioma específico de la tienda. Anteriormente, estos términos no se podían traducir, lo que obligaba a los usuarios a emplear una solución alternativa.

_AC-8103 - [Problema de GitHub](https://github.com/magento/magento2/issues/36942) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36943)_

#### Duplicar pedidos con el mismo ID de presupuesto al mismo tiempo con pocas diferencias horarias

Se ha corregido el problema que se producía cuando los clientes de Adobe Commerce encontraban pedidos duplicados colocados con el mismo QuoteID

_ACP2E-2055 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Carro de compras persistente borrado durante el paso de cierre de compra

Después de la corrección, seleccionar el método de pago durante el cierre de compra sin haber iniciado sesión no finaliza la sesión persistente.

_ACP2E-2470 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Reordenar agrega un producto no asignado al carro de compras

Anteriormente, para las diferentes tiendas, los productos se podían reordenar desde la otra tienda. Después de aplicar esta corrección solo en el mismo almacén , se puede reordenar el mismo producto de ámbito cuando se habilita el recurso compartido de cuenta de cliente

_ACP2E-2518 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### En administración, el &quot;Carro de compras&quot; de la izquierda no se actualiza al seleccionar los artículos y &quot;Mover al carro de compras&quot; de la derecha

El &quot;Carro de compras&quot; de la izquierda se actualiza al seleccionar los artículos y el &quot;Mover al carro de compras&quot; de la derecha en el lado del administrador. Anteriormente, esta funcionalidad no funcionaba porque los elementos del carro de compras transformados no se estaban vaciando de la sesión.

_ACP2E-2620 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### La regla de ventas [Cloud] no se ha aplicado al primer pedido de Multi Shipping

Después de la corrección, el descuento se muestra correctamente para cada pedido de la misma oferta de envío múltiple.

_ACP2E-2646 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### [Cloud] Solicitudes en paralelo de producción para agregar el mismo producto al carro de compras resultan en dos elementos separados en la API de resto del carro de compras

El sistema ahora procesa correctamente varias solicitudes paralelas para agregar el mismo producto al carro de compras en un solo elemento de línea, lo que impide la creación de elementos de línea independientes para el mismo SKU. Anteriormente, realizar solicitudes paralelas para añadir el mismo producto al carro de compras mediante la API de REST resultaba en varios elementos de línea para el mismo SKU.

_ACP2E-2664 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problema con el pedido desde el registro de regalos Magento 2.4.4 Enterprise/Commerce

Se ha resuelto el problema que impedía la compra exitosa de un producto de un registro de regalos, permitiendo que los pedidos se hicieran y que el registro de regalos se actualizara apropiadamente. Anteriormente, se producía un error al intentar realizar un pedido desde un registro de regalos, lo que impedía la finalización de la compra.

_ACP2E-2676 - [Problema de GitHub](https://github.com/magento/magento2/issues/35432)_

#### Obteniendo No se puede enviar la cookie. Tamaño de los &quot;mensajes de imagen&quot; al intentar reordenar

El proceso de reordenación no generará sus propios errores en este momento. Se basará en las comprobaciones de artículos integrados del anuncio del carro de compras.

_ACP2E-2704 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### La dirección de envío predeterminada no está seleccionada al cerrar la compra

La dirección de envío predeterminada ahora se selecciona como evento en el contexto de la búsqueda de direcciones habilitada.

_ACP2E-2798 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### [NUBE] problema de API addProductsToCart de graphql con opción personalizada

GraphQL agrega correctamente al carro el mismo producto con diferentes opciones personalizadas

_ACP2E-2897 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Las reglas de productos relacionados de [Cloud] no funcionan al cambiar la vista de la tienda

El problema se ha corregido confirmando que el valor de la propiedad personalizada se recibe correctamente en la página del carro de compras. Anteriormente, no se recuperaba correctamente al cambiar entre tiendas en la página del carro de compras de la tienda.

_ACP2E-2917_

#### Varias direcciones agregadas a la cuenta al cerrar la compra como cliente nuevo

El sistema guarda ahora una nueva dirección de cliente solo una vez si no se ha podido crear el pedido, lo que impide la creación de varias direcciones idénticas en caso de errores de colocación de pedidos. Anteriormente, el sistema guardaba una nueva dirección cada vez que se realizaba un intento de realización de un pedido, independientemente de si el pedido se había creado correctamente o no.

_ACP2E-2923 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/001e5188) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/2ebcef39)_

#### Reordenar el pedido del cliente mediante el formulario de pedido de invitado genera un carro de compras vacío

Anteriormente, al realizar un repedido a través de la página Pedidos y devoluciones, se redirigía al cliente a la página de inicio de sesión. Después de aplicar esta corrección, el cliente registrado se redirige correctamente a la página Ver carro de compras al realizar un repedido. El flujo funciona igual que como los clientes invitados.

_ACP2E-3004 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### El usuario administrador con recursos de función limitados no puede ver los carros de compras

Anteriormente, el administrador restringido no podía ver el carro de compras abandonado del panel de administración para un sitio web asociado. Después de aplicar esta corrección, el administrador restringido puede ver el carro de compras abandonado en el panel de administración.

_ACP2E-3025 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### La nube [Cloud] realiza pedidos rápidos con una gran cantidad de rendimiento de SKU

El rendimiento del cierre de compra se ha mejorado cuando los atributos utilizados en las reglas de precios del carro de compras no están presentes en todas las condiciones de los productos y cuando la función MAP (Precio mínimo anunciado) está habilitada.

_ACP2E-3176 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Elementos duplicados en el carro

El sistema ahora procesa correctamente varias solicitudes paralelas para agregar el mismo producto al carro de compras en un solo elemento de línea, lo que impide la creación de elementos de línea independientes para el mismo SKU. Anteriormente, realizar solicitudes paralelas para agregar el mismo producto al carro de compras en Storefront resultaba en varios elementos de línea para el mismo SKU.

_ACP2E-3211 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### La confirmación por correo electrónico del pedido de cierre de compra se envía a los correos electrónicos introducidos en Nombre/Apellido

La confirmación de correo electrónico del pedido de cierre de compra, que se envió anteriormente cuando se introdujo un patrón de correo electrónico en los campos Nombre y Apellido, ya no se envía.

_ACP2E-3296 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Formulario de dirección de envío de pago y envío obtener actualización con dirección incorrecta

shippingAddressFromData ahora se guarda en el almacenamiento local por sitio web. Anteriormente, una dirección del sitio web incorrecto se podía rellenar automáticamente en el formulario de dirección de envío durante el cierre de compra si se utilizaba un código de tienda en la dirección URL y el cierre de compra se iniciaba desde varios sitios web durante la misma sesión de invitado.

_ACP2E-3402 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### La desprotección de [CLOUD] no conserva la dirección de facturación seleccionada cuando la búsqueda de direcciones está habilitada

La página Pago y envío ahora conservará la dirección de facturación seleccionada cuando la búsqueda de direcciones esté habilitada. Anteriormente, si &quot;Límite de número de direcciones del cliente&quot; está configurado en 1 y el cliente tiene más de una dirección, la dirección de facturación seleccionada desaparecería después de volver a cargar la página.

_ACP2E-3405_

#### Producto de tarjeta regalo | Combinar carrito es combinar tarjetas de regalo

Los productos de tarjeta de regalo ahora se combinan correctamente en el carro de compras

_ACP2E-3407 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### No se respeta la persistencia del carro de compras al cerrar la sesión

Se ha agregado la funcionalidad que falta Recordarme desde el inicio de sesión del cliente hasta la ventana emergente de autenticación y los inicios de sesión de cierre de compra.

_ACP2E-3415 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/344fce23)_

#### Los datos de comillas existentes no se actualizan o no están visibles; en su lugar, cree un nuevo registro de comillas cuando déclencheur_recollect = 1

Los artículos del carro de compras del cliente ya no desaparecen como resultado de la eliminación de un producto después de agregarlo al carro de compras.

_ACP2E-3488 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Cuando se compra un artículo del registro de regalos, el cliente ve artículos que no están en su registro

La actualización del registro de regalos ya no incluye elementos que no pertenecen al registro de regalos.

_ACP2E-3495_

#### [Nube] Problema Con La Ventana Emergente De Confirmación &quot;Quitar Todo&quot; Eliminando Elementos Del Carro De Compras Sin Confirmación

Ahora, al hacer clic en el botón &quot;Eliminar todo&quot; para los productos que requieren atención, aparece una ventana emergente de confirmación para garantizar que los artículos solo se eliminen con la confirmación. Anteriormente, los elementos se eliminaban inmediatamente sin ninguna confirmación

_ACP2E-3510_

#### [NUBE] Funcionalidad del botón Reordenar

Volver a pedir un pedido desde el área de administración ahora agregará productos con existencias a la oferta aunque haya algunos productos en el pedido original que ya no tengan existencias. Antes de la corrección, no se añadían productos a la nueva oferta si los productos sin existencias estaban en el pedido original.

_ACP2E-3618 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### Las tiendas de búsqueda no funcionan por código postal

La búsqueda de ubicaciones de recogida por código postal no funcionaba correctamente en las localizaciones holandesas. Después de la corrección, la búsqueda de la ubicación de recogida proporcionará resultados basados en el código postal.

_ACP2E-3622 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Carro y cierre de compra, cierre de compra/cierre de compra de una página

#### [Error aleatorio] El campo de correo electrónico no se ha procesado o tarda mucho tiempo en aparecer en la página Pago y envío o en la página de pago

Commerce ahora procesa el campo **[!UICONTROL Email]** en las páginas de envío y pago del cierre de compra según lo esperado. Anteriormente, este campo estaba ausente o se procesaba lentamente.

_AC-9386 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/e1babcfd)_

### Carro de compras y cierre de compra, pedido

#### Selector de fecha para el producto con varias opciones personalizables con campos de fecha que no funcionan al realizar un pedido del administrador

El sistema ahora muestra correctamente el selector de fechas para todos los campos de fecha al configurar un producto con varias opciones de fecha personalizables en el proceso de creación de solicitudes de administración. Anteriormente, el selector de fechas solo se mostraba para el primer campo de fecha, lo que dejaba los campos restantes sin selector de fechas.

_ACP2E-3097 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

### Carro y Pago, Envío

#### Compra instantánea &quot;envío más barato&quot; roto para productos configurables

La función de compra instantánea seleccionaba incorrectamente la opción de entrega en tienda, más cara, para productos configurables en lugar del método de tarifa plana más barato. Esta corrección garantiza que se elija el método de envío correcto en función del precio real&quot;.

_AC-12119 - [Problema de GitHub](https://github.com/magento/magento2/issues/38811) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38819) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/29fe9097)_

### Catálogo

#### La limpieza de la tabla de base de datos cron_schedule no limpia los trabajos no existentes

El sistema ahora limpia automáticamente la tabla de base de datos cron_schedule, eliminando las entradas para los trabajos que ya no existen en el sistema. Esto garantiza un rendimiento óptimo al mantener un número mínimo de filas en la tabla. Anteriormente, las entradas para trabajos de módulos inactivos o eliminados no se limpiaban, lo que producía una acumulación de datos innecesaria en la tabla cron_schedule.

_AC-10910 - [Problema de GitHub](https://github.com/magento/magento2/issues/38217) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38693)_

#### El precio de nivel no se elimina del producto configurable

El sistema ahora elimina correctamente el precio de nivel de un producto cuando se convierte de un producto simple a un producto configurable, lo que garantiza una visualización precisa del precio en la front-end. Anteriormente, el precio de nivel de un producto configurable no se eliminaba cuando un producto se convertía de un producto simple a un producto configurable, lo que provocaba un desajuste en el precio mostrado.

_AC-10953 - [Problema de GitHub](https://github.com/magento/magento2/issues/38390) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38427)_

#### Descripción de categoría WYSIWYG está vacío en una vista de tienda no predeterminada

El sistema ahora guarda y muestra correctamente la descripción de la categoría en el editor de WYSIWYG al editar una categoría en el nivel de vista de tienda. Anteriormente, el editor de WYSIWYG aparecía vacío después de guardar una descripción de categoría en el nivel de vista de tienda.

_AC-11804 - [Problema de GitHub](https://github.com/magento/magento2/issues/38622) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38623)_

#### No se pueden reordenar los productos configurables con una casilla de verificación seleccionada como opción personalizada

El sistema ahora procesa correctamente la reordenación de los productos configurables con una única opción personalizada de casilla de verificación seleccionada, lo que permite crear con éxito la cesta. Anteriormente, al intentar reordenar estos productos, se producía un error e impedía que se agregaran elementos al carro de compras.

_AC-11970 - [Problema de GitHub](https://github.com/magento/magento2/issues/38736) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1d144bce)_

#### [Problema]: se corrigió la redacción del elemento de filtro en la navegación por capas

El sistema utiliza ahora correctamente las palabras &quot;item&quot; y &quot;items&quot; en el elemento de filtro de navegación por capas, lo que mejora la claridad y precisión de las descripciones de los filtros. Anteriormente, estas palabras se utilizaban incorrectamente, lo que producía una posible confusión para los usuarios que navegaban por las opciones de filtro.

_AC-12076 - [Problema de GitHub](https://github.com/magento/magento2/issues/38789) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37852)_

#### El formato de fecha y hora de la opción personalizada no funciona

El sistema ahora aplica correctamente el formato de fecha configurado a las opciones personalizadas del producto de tipo Fecha, lo que garantiza que el formato de fecha se muestre correctamente en el front-end. Anteriormente, los cambios en la configuración del formato de fecha no se reflejaban en el front-end para las opciones personalizadas de producto de tipo Fecha.

_AC-12164 - [Problema de GitHub](https://github.com/magento/magento2/issues/32990) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38925)_

#### Faltan opciones desplegables

El sistema ahora muestra correctamente todos los valores de la lista desplegable al crear un nuevo atributo con más de 20 valores. Anteriormente, solo se mostraban los 20 primeros valores u otros valores de página seleccionados, lo que provocaba que faltaran los valores restantes.

_AC-13068 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Use el ID de almacén actual para la caché de tiempo de ejecución de categoría

El sistema ahora utiliza correctamente el ID de almacén actual para la caché de tiempo de ejecución de categoría, lo que evita la anulación de datos cuando se utiliza la emulación o el código personalizado guarda la categoría en diferentes almacenes. Anteriormente, el objeto almacenado en tiempo de ejecución podría haber sido del almacén incorrecto, lo que provocaba la anulación de datos.

_AC-13296 - [Problema de GitHub](https://github.com/magento/magento2/issues/39310) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36394)_

#### bin/magento sampledata:deploy —no-update genera una excepción

El sistema ahora acepta correctamente un valor booleano al utilizar la opción —no-update en el comando sampledata:deploy, lo que evita cualquier error durante la implementación de los datos de ejemplo. Anteriormente, se producía un error al utilizar este comando, ya que el sistema esperaba incorrectamente un valor entero.

_AC-13324 - [Problema de GitHub](https://github.com/magento/magento2/issues/39344) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39345)_

#### [Problema]: corrige el uso del tipo de caché EAV

El sistema ahora utiliza correctamente el tipo de caché EAV en todos los lugares relevantes, lo que garantiza un almacenamiento en caché de datos coherente y eficiente. Anteriormente, el tipo de caché de EAV no se utilizaba de forma coherente, lo que producía posibles ineficiencias e incoherencias en el almacenamiento en caché de datos.

_AC-13355 - [Problema de GitHub](https://github.com/magento/magento2/issues/32322) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31264)_

#### La búsqueda avanzada en el catálogo con datos vacíos se dirigirá a la página de resultados de búsqueda [2.4.dev branch]

El sistema ahora retiene correctamente a los usuarios en la página Búsqueda avanzada y muestra un mensaje de error cuando intentan realizar una búsqueda sin introducir ningún dato. Anteriormente, realizar una búsqueda vacía redirigía a los usuarios a la página Búsqueda avanzada en el catálogo con un mensaje que les solicitaba que modificaran su búsqueda.

_AC-13596 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### [Problema] Diseño de producto basado en attribute_set

El sistema ahora permite ajustar el diseño del producto en función del conjunto de atributos, lo que proporciona una forma más práctica y eficaz de administrar la visualización del producto en la tienda de front-end. Anteriormente, el diseño solo se podía ajustar por SKU o por tipos de producto, lo que no siempre era práctico para muchos productos o artículos específicos.

_AC-13622 - [Problema de GitHub](https://github.com/magento/magento2/issues/38790) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36244)_

#### Falta la clave única en la tabla eav_attribute_option_value

El sistema ahora incluye una clave única en las columnas &quot;option_id&quot; y &quot;store_id&quot; en la tabla &quot;eav_attribute_option_value&quot;, lo que evita la posibilidad de que una opción tenga varios valores para la misma vista de tienda. Anteriormente, un código defectuoso podía hacer que una opción tuviera varios valores para la misma vista de tienda, lo que provocaba problemas al editar productos o atributos.

_AC-6738 - [Problema de GitHub](https://github.com/magento/magento2/issues/24718) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/28796)_

#### [Problema] Use la clase de visibilidad para el indizador de productos de categoría, en lugar de valores codificados

El sistema ahora utiliza la clase de visibilidad para el indexador de productos de categoría en lugar de valores codificados, lo que mejora la modularidad. Anteriormente, los valores codificados se utilizaban en el indexador de productos de categoría, lo que limitaba la flexibilidad y la adaptabilidad.

_AC-8297 - [Problema de GitHub](https://github.com/magento/magento2/issues/37200) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37199)_

#### El código de moneda no cambia en el widget Nuevo producto

El sistema ahora actualiza correctamente el código de moneda en el widget Nuevo producto cuando la moneda se cambia en el front-end, lo que garantiza la coherencia en la visualización de la moneda en todo el sitio. Anteriormente, el cambio de moneda en el front-end no afectaba al código de moneda mostrado en el widget Nuevo producto.

_AC-9375 - [Problema de GitHub](https://github.com/magento/magento2/issues/37898) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37899)_

#### El precio normal no aparece en PLP para productos configurables

Ahora se muestra el precio normal en las páginas de lista de productos para productos configurables que tienen productos secundarios con precio especial.

_ACP2E-2224 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### La información de stock no se muestra correctamente en la cuadrícula de Visual Merchandising

Ahora, las existencias se muestran según la tienda seleccionada.

_ACP2E-2478 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

#### El contenido del widget no se actualiza en la página de cms

El sistema actualiza ahora el contenido del widget en una página de CMS cuando un producto se establece como nuevo y se guarda, lo que garantiza que la página muestre la colección de productos actualizada. Anteriormente, la página no se actualizaba para mostrar el nuevo producto debido a las identidades de caché incorrectas utilizadas para el widget en la caché.

_ACP2E-2621 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Problemas al guardar precios avanzados en productos agrupados

Mejora del rendimiento del ahorro de productos del paquete.

_ACP2E-2630 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### El proceso de reindexación de [On-Premise] no es eficiente al crear reglas de precios de catálogo

Al guardar la regla de precio del catálogo, no se invalidarán los indexadores, sino que solo se reindexarán los productos afectados

_ACP2E-2652 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

#### Actualización de la hora de los atributos de producto del tipo Fecha y Hora mediante la importación CSV

Ahora los atributos datetime tendrán parte de tiempo en los datos exportados. También será posible actualizar la hora de dichos atributos mediante la importación. Además, si &quot;Campos Enclosure&quot; está habilitado, los valores de atributo de la columna &quot;additional_attributes&quot; se escribirán entre comillas dobles.

_ACP2E-2679 - [Problema de GitHub](https://github.com/magento/magento2/issues/38306) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### No hay un mensaje de error apropiado cuando el ID del sitio web es incorrecto en la solicitud

Ahora se ha agregado el mensaje de error correspondiente para que se muestre cuando el ID del sitio web sea incorrecto en la solicitud. Anteriormente, no había ninguna validación cuando el ID del sitio web era incorrecto en la solicitud.

_ACP2E-2689 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### La imagen del producto se pierde después de eliminar una actualización programada existente que no afecta a la imagen

Las imágenes de producto no se eliminan al eliminar la actualización de ensayo.

_ACP2E-2785 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### [Nube] Precio de paquete de producto incorrecto al usarlo con precios de nivel

Anteriormente, al calcular ciertos descuentos porcentuales redondeados a 2 puntos decimales, se generaban precios finales diferentes para la página de lista de productos y la página de detalles del carro de compras. Después de aplicar esta corrección, el precio final del producto del paquete es el mismo que en la página de detalles del producto, la página de lista de productos y la página del minicarrito.

_ACP2E-2799 - [Problema de GitHub](https://github.com/magento/magento2/issues/38091) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### La regla de promociones de catálogo no funciona con el atributo quantity_and_stock_status

El atributo quantity_and_stock_status ahora se tiene en cuenta en la regla de promoción del catálogo, que anteriormente no se tenía en cuenta al generar un nuevo producto desde el administrador.

_ACP2E-2805 - [Problema de GitHub](https://github.com/magento/magento2/issues/35627) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/cf34971d)_

#### La entidad del producto updated_at no actualiza los valores de columna al actualizar el precio mediante la API de REST

La columna del producto &quot;Última actualización en&quot; del administrador se actualiza en la fecha y hora adecuadas mientras se actualizan los productos existentes mediante la API de REST. Anteriormente, la columna &quot;Última actualización en&quot; no se actualizaba correctamente.

_ACP2E-2837 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### Es posible establecer valores no únicos mediante la importación de productos

El sistema ahora aplica correctamente la restricción de valor único para los atributos de producto únicos durante la importación del producto, lo que impide que haya valores duplicados para ese atributo. Anteriormente, era posible establecer valores no únicos para atributos de producto configurados para tener valores únicos mediante la importación de productos.

_ACP2E-2840 - [Problema de GitHub](https://github.com/magento/magento2/issues/38445) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Los productos del front-end utilizan datos específicos cuando el modo de tienda única está habilitado

Anteriormente, cuando se habilitaba el modo de almacén único para la vista de almacén predeterminada, los cambios no se migraban al ámbito de nivel de sitio web. Después de aplicar esta corrección, cuando habilitamos el modo de tienda única, los datos predeterminados específicos de la vista de la tienda se sincronizarán con los datos específicos del nivel de sitio web y resolverán los posibles conflictos para productos y categorías.

_ACP2E-2843 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### No se puede establecer &quot;Orden predeterminado por&quot; en una categoría mediante la API REST

Actualizar correctamente default_sort_by en una categoría mediante una solicitud de API de REST/SOAP

_ACP2E-2857 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Nube] El comerciante tiene problemas con el recuento de listas de deseos

Añadir un producto a la lista de deseos en una tienda ya no aumenta la cantidad de listas de deseos en otras tiendas abiertas en el mismo navegador. Anteriormente, si ambas tiendas se cargaban en el mismo explorador, el recuento de listas de deseos también aumentaba en la otra tienda.

_ACP2E-2871 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### La página Categoría en el front-end muestra ranuras vacías al utilizar el producto del paquete

Los productos agrupados que no se pueden vender en el contexto de tienda actual ya no se indexan.

_ACP2E-2874 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/bc37ec76)_

#### [ACLARACIÓN] problemas de tabla de secuencia de productos del paquete

Los registros de las tablas de secuencia de productos del paquete (sequence_product_bundle_option, sequence_product_bundle_selection) ahora se eliminan cuando se elimina el producto del paquete o se eliminan las opciones de producto del paquete.
Anteriormente, los registros de las tablas de secuencia de productos del paquete no se eliminaban.

_ACP2E-2888_

#### [Nube] problema de cotización en la arquitectura de varios sitios web

Anteriormente, la arquitectura de varios sitios web con diferentes monedas y grupos de clientes no podía aplicar correctamente descuentos a la tienda. Una vez implementada esta corrección, la arquitectura de varios sitios web con diferentes descuentos de precio de grupo de clientes se aplicará correctamente a las diferentes tiendas.

_ACP2E-2905 - [Problema de GitHub](https://github.com/magento/magento2/issues/38506) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### dynamic-rows.js:658 TypeError no detectado: dataRecord.slice al editar productos del paquete

No hay ningún error de javascript en la consola del explorador al eliminar la opción del producto del paquete.

_ACP2E-2909 - [Problema de GitHub](https://github.com/magento/magento2/issues/38505) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### Paquete de [Cloud] con precios incorrectos en la confirmación del pedido

Se muestra la cantidad correcta para las opciones de paquete en orden en Storefront cuando se utilizó una moneda distinta a la base uno.

_ACP2E-2950 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### Error al añadir vídeo de YouTube

Las imágenes y los vídeos del producto se configuran en el ámbito global. Dado que no puede tener un vídeo de producto en un ámbito y no en otro, la configuración de clave de la API de YouTube se ha establecido en ámbito global.

_ACP2E-2956 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Actualización de URL de la nube] solo para store_id=0

La &quot;Ruta de URL&quot; ahora se almacena con el ID de almacén correcto. Anteriormente, el ID de tienda era incorrecto, lo que provocaba que permanecieran rutas URL incorrectas en la base de datos al mover categorías.

_ACP2E-2964 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9af794a4)_

#### async.operations.all ejecutó y creó un error.

Los datos incorrectos del vínculo del producto en las llamadas a la API de REST ya no causan errores críticos.

_ACP2E-3009 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

#### [Nube] problema del dispositivo móvil: no se pudo bloquear la imagen PDP

El sistema ahora admite la funcionalidad de pellizco y zoom en las imágenes de la página de detalles del producto en la vista móvil en Chrome, lo que mejora la experiencia del usuario móvil. Anteriormente, al tocar dos veces la imagen en la vista móvil en Chrome, no se acercaba la imagen como se esperaba.

_ACP2E-3029 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### Falta la etiqueta en la navegación por capas con el nombre de opción 0

El problema se ha resuelto omitiendo un verificador de valores vacío para el valor de atributo 0. Anteriormente, se consideraba vacío y era la causa del problema.

_ACP2E-3058 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Los clientes ven precios de otros grupos de clientes

Se ha corregido un problema por el cual la información relacionada con el grupo de clientes se guardaba en un segmento incorrecto debido al valor antiguo de X-Magento-Vary en la solicitud

_ACP2E-3069 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### Error al eliminar las opciones de paquete

El sistema ahora elimina correctamente las opciones de paquete sin activar un error o hacer que la página no responda. Anteriormente, al intentar eliminar las opciones de paquete, se producía el error &quot;La página no responde&quot; y se impedía guardar el producto.

_ACP2E-3076 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Problema de explorador de Permisos sin memoria de categoría

La interfaz de usuario de permisos de categoría se ha rediseñado para permitir el procesamiento de una gran cantidad de permisos mediante la paginación y el componente de la interfaz de usuario predeterminados. Anteriormente, los permisos de categoría provocaban que el explorador se bloqueara con una gran cantidad de permisos asignados a la categoría.

_ACP2E-3094_

#### El archivo de imagen [Cloud] no existe en el registro de errores de New Relic

El sistema ahora sincroniza las imágenes de marcador de posición personalizadas con el almacenamiento local, asegurándose de que se representen correctamente al utilizar el almacenamiento remoto como AWS S3. Anteriormente, las imágenes de marcador de posición personalizadas no se representaban al utilizar el almacenamiento remoto, lo que provocaba una visualización de imágenes rotas y registros de errores.

_ACP2E-3100 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d1f7dc95)_

#### La fuente RSS de Nuevos productos no se actualiza con nuevos productos debido a la caché

La fuente RSS para nuevos productos ahora se actualiza cuando un producto se establece como nuevo y se guarda

_ACP2E-3103 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### La respuesta de GQL de la Galería multimedia de productos [Cloud] no está ordenada por la posición de la imagen

El sistema ahora ordena correctamente los elementos de la galería de medios por su posición en la respuesta de GraphQL, lo que garantiza un orden de visualización preciso. Anteriormente, los elementos de la galería de medios no se ordenaban por posición, lo que provocaba un orden de visualización incorrecto.

_ACP2E-3126 - [Problema de GitHub](https://github.com/magento/magento2/issues/37671) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b21e5d91)_

#### [Los elementos de la subcategoría Cloud] no se muestran en la edición de widgets del servidor de administración

El árbol de categorías de la nueva página del widget ya no debería tener problemas para cargar categorías de Nivel 5+. Anteriormente, faltaban algunas categorías al cargar las tres últimas categorías de Nivel 5.

_ACP2E-3136 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [cloud]: problema de movimiento y zoom con dos dedos en el dispositivo móvil real

El sistema ahora garantiza una funcionalidad de zoom de imagen consistente en dispositivos móviles, proporcionando una experiencia de usuario fluida y predecible. Anteriormente, la función de zoom de imagen era incoherente y, de repente, se alejaba después de un determinado punto cuando se visualizaba en un dispositivo móvil.

_ACP2E-3198 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Cuando anulamos la asignación de productos del catálogo compartido, los productos de la lista de deseos no se borran

Ahora, no hay elementos visibles en la lista de deseos si un producto no está disponible en el catálogo compartido. Anteriormente, la página de lista de deseos mostraba incorrectamente un recuento de &quot;1 elemento&quot; incluso cuando en realidad no había elementos disponibles en la lista de deseos.

_ACP2E-3282 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### Productos relacionados Seleccionar todo/Anular selección de todos los problemas

Anteriormente, los botones &quot;Seleccionar todo&quot;/&quot;Anular la selección de todo&quot; de los productos relacionados no funcionaban correctamente si se seleccionaba un producto manualmente. Después de la corrección, estos botones ahora funcionan de forma coherente, incluso después de la selección manual, lo que garantiza que todos los productos estén seleccionados correctamente o no.

_ACP2E-3286 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [Nube]: la traducción por correo electrónico de la alerta de stock al idioma incorrecto

Al enviar alertas de cotizaciones/precios para un sitio web con varias vistas de tiendas en distintos idiomas, se utilizará en el correo electrónico el idioma de la vista de tienda en la que se creó la alerta.

_ACP2E-3336 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4cf5e62) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### Las categorías deshabilitadas ya no aparecen atenuadas en el árbol de categorías

Anteriormente, las categorías deshabilitadas no aparecían atenuadas en el árbol de categorías. Ahora, se muestran con un efecto gris.

_ACP2E-3350 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### La carga del formulario de edición de productos configurables provoca tiempo de espera y agotamiento de memoria

Antes de la corrección, se construían variaciones de productos configurables en función de todas las combinaciones de opciones de atributos posibles. En los casos en los que los atributos tenían muchas opciones, esto resultaba en una operación larga y que consumía recursos. Ahora, las variaciones de producto configurables se construyen en función de los atributos de producto secundarios existentes. Esto da como resultado muchos menos cálculos, lo que mejora el uso de los recursos.

_ACP2E-3410 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Fotorama no carga el vídeo correctamente al usar Muestras y la opción está preseleccionada mediante una URL

Los vídeos del producto ahora se representarán correctamente en la página de detalles del producto configurable, si la dirección URL contiene opciones seleccionadas.

_ACP2E-3454 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### El widget de carrusel de PageBuilder muestra productos que no coinciden con las condiciones

La lista de productos utilizada en los widgets ahora respeta la condición de categoría

_ACP2E-3461 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### Error de validación activado para todos los productos del grupo cuando uno tiene una cantidad no válida

Ahora, el error de validación se activa correctamente para todos los productos del grupo cuando un producto tiene una cantidad no válida, lo que no ocurría anteriormente.

_ACP2E-3469 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/56463d5e)_

#### [NUBE] El precio especial no se muestra en el producto configurable

Después de la corrección, cambiar el valor &quot;Utilizado en la lista de productos&quot; para el atributo de precio especial no afectará a la visualización del precio especial de los productos configurables.

_ACP2E-3513 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### Indexadores Las tablas temporales no se limpian si el proceso finaliza

Las tablas temporales del indexador CatalogRule ahora se limpian si el proceso del indexador ha finalizado

_ACP2E-3516 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [QUANS] errores de prueba de unidad principal en 2.4.7-p3

No es necesario incluir notas de la versión para esta prueba, ya que es una mejora de Prueba unitaria.

_ACP2E-3520 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Problema de rendimiento en la recuperación de cantidad de stock para productos agrupados con varios orígenes

La página de edición de productos agrupados y agrupados ahora se optimiza cuando los productos asignados tienen un gran número de fuentes de inventario.

_ACP2E-3533 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/0208e433)_

#### Refijo ACP2E-3389

Se ha mejorado el rendimiento de la página de categoría de administrador en el caso de un gran número de categorías de anclaje

_ACP2E-3641 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catálogo, Contenido

#### La caché [Cloud] no se está invalidando.

Anteriormente, al guardar una página de CMS con un diseño actualizado, no se reflejaba correctamente en el front-end. Después de aplicar esta corrección, el diseño de diseño adecuado será visible en el front-end cuando cambiemos el diseño y guardemos la página de CMS.

_ACP2E-3063 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/66dea0de)_

#### Categorías de anclaje/no anclaje [Cloud] invertidas en el widget de contenido

Anteriormente, al seleccionar Mostrar activado -> Categorías de anclaje, se mostraban todas las categorías que no reflejaban la relación principal-secundario entre el anclaje y el no anclaje. Después de aplicar esta corrección, la opción Mostrar activado -> Categorías de anclaje solo muestra Categorías de anclaje (seleccionable) y Mostrar activado -> Categorías de no anclaje muestra Categorías de no anclaje (seleccionable)

_ACP2E-3131 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### Las categorías no funcionan con widgets

Anteriormente, si guardábamos el bloque de CMS para diferentes categorías de anclaje/no anclaje, no funcionaba para las categorías secundarias cuando se mostraba en el front-end. Después de aplicar esta corrección, el bloque se muestra en el front-end para diferentes categorías.

_ACP2E-3152 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

### Catálogo, marco

#### Obtención de pedido(Envíos|Abonos|Factura)Cobro: no se debe cargar el cobro

El sistema ahora garantiza que los cobros para envíos y notas de abono no se precarguen cuando se recuperen de un pedido, lo que permite aplicar filtros o pedidos adicionales a estos cobros. Anteriormente, estas colecciones se cargaban automáticamente, lo que impedía realizar más modificaciones.

_AC-9111 - [Problema de GitHub](https://github.com/magento/magento2/issues/37561) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37562)_

#### [Seguimiento de la nube]No coinciden en la comparación de datos al comprobar si los datos tienen cambios

Anteriormente, se llamaba cada vez al objeto de guardado sin ningún cambio de datos (para cualquier campo de datos numéricos, como int/float/double). Déclencheur el indicador _hasDataChanges para que sea true y llama a la función de guardado. Tampoco comprueba los números flotantes encapsulados por string. Después de aplicar esta corrección, la función de guardado solo llamará si se cambian los datos. El valor de datos para int/float/double-check con el valor que pasa a la función y hace una coincidencia de tipo estricta

_ACP2E-2949 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8931218)_

### Catálogo, GraphQL

#### Gestión de filtros de categoría en GraphQL: includeDirectChildrenOnly y category_uid

Solo se recuperan las categorías secundarias directas al filtrar por category_uid.

_ACP2E-3090 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/93d50f8d)_

#### La ordenación de productos de [Cloud] Graphql no funciona

GraphQl La ordenación de productos por varios campos cuando los campos se pasan en variables ahora funciona según lo esperado.

_ACP2E-3166 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Los precios de nivel devuelven un valor incorrecto en los productos GraphQL (en comparación con Storefront)

Después de la corrección, los precios de nivel del producto devueltos para las solicitudes de graphql tienen un precio por cada elemento.

_ACP2E-3312 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [CLOUD] B2B: problema de categoría a través de GraphQL

Después de la corrección, la consulta de categorías de graphql devuelve categorías con permiso de permiso incluso si la categoría raíz no tiene permiso de permiso.

_ACP2E-3385_

### Catálogo, precios, ensayo y previsualización

#### [Nube] El punto de conexión de API de precio especial devuelve un error al actualizar grandes cantidades de productos simultáneamente

Ahora, la API de actualización masiva de precios especiales creará una sola campaña para cada intervalo de fechas en lugar de varias actualizaciones programadas para cada producto e intervalo de fechas. Además, admitirá solicitudes de API simultáneas para un procesamiento más rápido de un gran número de SKU.

_ACP2E-2672 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f89a447e)_

### Catálogo, Producto

#### El árbol de selección de categorías del producto de edición no está en el mismo orden que el establecido en Catálogo->Categorías

El sistema ahora muestra correctamente el árbol de selección de categorías en la sección de edición del producto en el mismo orden establecido en Catálogo->Categorías, lo que facilita la administración del producto en catálogos grandes. Anteriormente, el árbol de categorías de la sección de edición de productos se mostraba en el orden de creación de categorías, independientemente del orden de visualización establecido en Catálogo->Categorías.

_AC-7050 - [Problema de GitHub](https://github.com/magento/magento2/issues/36101) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36104)_

### Catálogo, SEO

#### URL canónica incorrecta para la categoría cuando la página es > 1

Anteriormente, la URL canónica para el contenido de varias páginas no funcionaba correctamente, lo que mostraba la URL base de forma coherente. Sin embargo, una vez implementada la corrección, la URL canónica para el contenido de varias páginas ahora muestra correctamente la URL con el ID de página.

_ACP2E-3653 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Catálogo, Buscar

#### Los productos que no se muestran en la categoría y la búsqueda, pero los vínculos directos, funcionan

Anteriormente, el atributo personalizado Sí/No con price_* attribute_code no funciona con la indexación. Después de esta corrección, el atributo personalizado Sí/No funciona según lo esperado.

_ACP2E-2757 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### [Nube] Error de búsqueda elástico en ciertas páginas de la categoría

Anteriormente, con el ticket de configuración mencionado, cuando ponemos el precio 0 para varios productos, se genera una excepción en la página de categoría de front-end. Después de esta corrección se aplica cuando se carga múltiples precios de producto 0 y cargamos la página de categoría en front-end, no se producirá ninguna excepción y se cargará la página de categoría correctamente.

_ACP2E-3053 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Error de tipo al crear el objeto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception

Después de la corrección, se puede crear una instancia de la clase Magento\CatalogSearch\Model\Indexer\Fulltext sin especificar $data.

_ACP2E-3345 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [NUBE] problema con productos no visible en FrontEnd después de guardar en el administrador de Magento

Después de la corrección, los productos configurables que tienen productos secundarios con nombres largos no se perderán en la tienda.

_ACP2E-3521 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Catálogo, Envío

#### Dirección de envío vacía al realizar un pedido de un artículo del registro de regalos

Anteriormente, para los artículos de registro de regalos de usuario invitado, cuando se devolvían desde la función de correo electrónico, generaba una dirección en blanco vacía, que es incorrecta para realizar un pedido. Después de aplicar esta corrección, el Registro de regalos comprueba los usuarios que han iniciado sesión o los usuarios invitados y las direcciones asignadas si existen.

_ACP2E-3195_

### Nube

#### [Cloud] PHPSESSID está cambiando cada petición POST

PHPSESSID ya no se regenera en solicitudes POST en el área de front-end para un cliente que ha iniciado sesión si la caché de L2 Redis está habilitada y el cliente se actualizó desde el back-end

_ACP2E-3010 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### Advertencias de generación de mapa

Después de la corrección, el mapa del sitio se genera en el directorio tmp del sistema y se copia en el destino final.

_ACP2E-3532 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Contenido

#### [Problema] con la visualización del precio en el widget visualizado recientemente

El sistema ahora muestra correctamente el precio de los productos simples sin existencias en el widget &quot;Productos vistos recientemente&quot;, lo que garantiza la coherencia en todos los widgets y páginas de listas de productos. Anteriormente, el precio de los productos simples sin existencias no se mostraba en el widget &quot;Producto visualizado recientemente&quot; debido a una condición en las plantillas de carga de precios.

_AC-10539 - [Problema de GitHub](https://github.com/magento/magento2/issues/38167) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38159)_

#### [Problema]: error tipográfico y gramática correctos en el archivo acl.xsd

El sistema corrige ahora un error tipográfico y gramatical en el archivo acl.xsd, lo que mejora la claridad y precisión de la documentación. Anteriormente, el archivo acl.xsd contenía un error tipográfico y una gramática incorrecta que podría causar confusión.

_AC-10596 - [Problema de GitHub](https://github.com/magento/magento2/issues/38061) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38046)_

#### La imagen del titular de Pagebuilder no es visible en la galería

El sistema ahora muestra correctamente las imágenes de banner cargadas en las carpetas recién creadas en la galería de Pagebuilder, lo que elimina los errores de consola anteriores. Antes de esta corrección, las imágenes de los titulares no eran visibles en la galería si se cargaban en una carpeta nueva, lo que provocaba un error de la consola.

_AC-10845 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### &quot;Código de área no establecido&quot; después de actualizar a 2.4.5-p8

El sistema ahora completa correctamente el proceso de implementación de contenido estático cuando el módulo Magento_CSP está habilitado y &quot;dev/js/translate_strategy&quot; está configurado como &quot;incrustado&quot;, sin activar el error &quot;Código de área no establecido&quot;. Anteriormente, en estas condiciones, el proceso de implementación del contenido estático fallaba con un error de &quot;Código de área no establecido&quot;.

_AC-12283 - [Problema de GitHub](https://github.com/magento/magento2/issues/38845) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38922)_

#### El árbol de categorías del widget no se representa correctamente

_AC-12692 - [Problema de GitHub](https://github.com/magento/magento2/issues/39008) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/58e40ceb)_

#### No se puede ver el mensaje &quot;Using Default value&quot; al cambiar el tema en la página de configuración de diseño

El sistema ahora incluye una columna independiente para mostrar el mensaje &quot;Uso del valor predeterminado&quot; en función del tema seleccionado en la página de configuración de diseño. Esto garantiza la claridad y visibilidad del estado del valor predeterminado. Anteriormente, no se mostraba el mensaje &quot;Using Default value&quot;, lo que producía confusión sobre el estado de la temática seleccionada.

_AC-13054 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] restaura de nuevo la compatibilidad con los complementos TinyMCE (una vez...

El sistema ahora restaura la compatibilidad con versiones anteriores de los complementos TinyMCE, lo que permite llamar a las funciones definidas dentro del complemento cuando se utiliza el widget desde otra ubicación. Anteriormente, debido a un cambio en la versión de TinyMCE, los complementos no devolvían los widgets como un objeto, lo que provocaba un error al intentar llamar a ciertas funciones en la instancia del widget.

_AC-13569 - [Problema de GitHub](https://github.com/magento/magento2/issues/39262) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39258)_

#### [Problema] problema de carga de archivo en el editor de WYSIWYG en la página del producto

El sistema ahora muestra correctamente el árbol de carpetas y permite cargar imágenes en el editor de WYSIWYG en la página del producto, incluso después de expandir primero la pestaña Imagen y vídeos. Anteriormente, al expandir la pestaña &quot;Imagen y vídeos&quot; por primera vez, el árbol de carpetas no se mostraba y aparecía un mensaje de error al intentar cargar una imagen en el editor de WYSIWYG.

_AC-9638 - [Problema de GitHub](https://github.com/magento/magento2/issues/38026) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38025)_

#### [Problema de bloque dinámico On-PREM]

Los widgets ahora se representan correctamente dentro de bloques dinámicos.

_ACP2E-2392 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### La URL nocookie de YouTube no funciona en Page Builder

Ahora, pagebuilder permite la URL sin cookies de YouTube en la configuración del elemento de formulario de las reglas de validación. Anteriormente, la URL sin cookies de YouTube no funcionaba en pagebuilder.

_ACP2E-2606_

#### [Nube] de front-end no se está cargando debido a un problema en la plantilla del boletín informativo

Añadir bloques a través de la sección de contenido de la página de CMS ya no provoca excepciones

_ACP2E-2693 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### ACP2E-2836: [Nube] Investigue la excepción encontrada en el registro: InvalidArgumentException: La clase no existe en vendor/magento/module-rule/Model/ConditionFactory.php

La eliminación de una condición en la configuración de contenido de los productos de PageBuilder ya no provoca que se registre una excepción en los archivos de registro. Anteriormente, si se eliminaba una condición en la configuración de contenido de los productos de PageBuilder, se registraba una excepción crítica en los registros, a pesar de no causar ningún problema en el front-end.

_ACP2E-2836 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_

#### Cambio al modo de tienda única: el contenido global ya no aparece

El sistema ahora sincroniza las configuraciones de diseño de vista de tienda con las configuraciones de diseño de sitio web al habilitar el modo de tienda única, lo que garantiza que las actualizaciones de contenido sean visibles en el front-end. Anteriormente, cambiar al modo de tienda única evitaba que las actualizaciones de contenido se reflejaran en la tienda.

_ACP2E-2842 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### Page Builder reemplaza la imagen al intentar agregar un vínculo y otros problemas de uso.

Ahora, al hacer clic en una imagen, los vínculos del editor wysiwyg en el elemento de texto Page Builder cargarán los datos adecuados en la imagen y el cuadro de diálogo de configuración del vínculo. También la adición de un vínculo a una imagen en el editor ahora funciona correctamente. Anteriormente, la imagen se sustituía por un vínculo.

_ACP2E-2903 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### La galería de medios antigua no puede procesar imágenes cuando se coloca una imagen de 0 bytes en el directorio

El sistema ahora gestiona imágenes de 0 bytes en la galería de medios sin interrumpir la funcionalidad, lo que permite mostrar y seleccionar otras imágenes del directorio según lo esperado. Anteriormente, la presencia de una imagen de 0 bytes en la galería de medios impedía que se mostraran o seleccionaran todas las imágenes del directorio.

_ACP2E-2970 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Error del Page Builder al editar el bloque de CMS

El sistema ahora guarda correctamente los cambios realizados en el área de administración con Page Builder, sin arrojar el error &quot;Page Builder estaba procesando durante 5 segundos sin liberar bloqueos&quot;. en la consola del explorador. Anteriormente, este error se producía al intentar guardar los cambios, lo que impedía que el contenido se actualizara correctamente.

_ACP2E-3064 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### [NUBE]: no hay botones de cierre de compra ni de editar el carro de compras en la sección del carro de compras

El producto del paquete ahora se agrega al carro de compras mediante widgets sin errores.

_ACP2E-3092 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b21e5d91) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_

#### La vista previa de ensayo de contenido en páginas de categoría no muestra widgets de producto

El problema se ha corregido asegurando que las entradas de producto para la categoría adicional vinculada al bloque de CMS se hayan registrado con precisión en la base de datos. Anteriormente, devolvía un conjunto de resultados vacío cuando se solicitaba la página de vista previa de la categoría.

_ACP2E-3113_

#### [NUBE] El botón Cargar imagen no funciona

Antes, el botón Cargar imagen para titular y deslizador de PageBuilder no funcionaba según lo esperado y ahora, al pulsarlo, se abre el administrador de archivos local para seleccionar la imagen que se desea cargar.

_ACP2E-3122 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_

#### imagecreatetruecolor(): El argumento #2 ($height) debe ser mayor que 0. No se puede cargar una imagen específica

Se ha resuelto el problema que provocaba errores en el administrador al cargar imágenes con una altura de 0 a través de la galería de medios y la sincronización de recursos correctamente mediante el comando sync. Anteriormente, no se puede cargar la imagen a través de la galería de medios y el comando de sincronización también falla cuando una imagen específica está en la galería.

_ACP2E-3127 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### Prototype.js.Array.from está en conflicto con la API de Google Maps

Los mapas de Google ahora se representan correctamente en el editor de PageBuilder. Anteriormente, un error de JavaScript impedía que Google Maps se representara correctamente.

_ACP2E-3154 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Nube]: El deslizador de CMS no refleja los cambios más recientes

El problema se ha solucionado asegurándose de que la lista del control deslizante se actualice mientras el evento de guardado se activa en la pantalla de edición de la diapositiva. Anteriormente, se activaba y causaba el problema.

_ACP2E-3275 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### Se produce un error en la página CSM cuando los bloques de CMS se insertan mediante el generador de páginas en un orden determinado

Anteriormente en algunas versiones de PHP y OS (Linux), el procesamiento de bloques que hacían referencia a otros bloques de cms a través de PageBuilder habría fallado con un &quot;Se produjo un error desconocido. Inténtelo de nuevo&quot;. Ahora el contenido de los bloques cms se representa correctamente dentro de un contenido controlado por PageBuilder.

_ACP2E-3326 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_

#### [Nube] Los bloques dinámicos no funcionarán correctamente

Los segmentos de clientes que iniciaron sesión ahora se borran tras cerrar la sesión, lo que impide que la sesión de invitado herede segmentos que iniciaron sesión anteriormente

_ACP2E-3388_

#### Error en la previsualización de plantilla de Pagebuilder para contenido grande

El contenido grande provocaba que un elemento de lienzo desbordara los límites del explorador y devolviera un valor incorrecto, que rompía el código back-end (no se puede descodificar correctamente la imagen). Se corrigió al limitar el tamaño del lienzo al límite del explorador universal.

_ACP2E-3428 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/adfb1747)_

#### Últimas actualizaciones de seguridad con TinyMCE 7 tamaño de fuente faltante

Los selectores de tamaño de fuente y familia de fuentes ya están disponibles en el editor de WYSIWYG. Antes de esta corrección, con TinyMCE 7 estos no estaban disponibles en la interfaz del editor.

_ACP2E-3430 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_

#### TinyMCE 7 editor tamaño de fuente en el administrador en PT y no PX por favor aclarar

Antes de la corrección, no se podía especificar el tamaño de fuente en píxeles en las áreas de WYSIWYG. Ahora puede establecer el tamaño de fuente en píxeles en lugar de pt.

_ACP2E-3483 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### El tipo de contenido de producto en Page Builder se contrae sin mensajes correctos

Antes de la corrección, el HTML de previsualización no se generaba correctamente cuando no había productos en el widget. Ahora, la respuesta vacía se genera correctamente y el widget de productos se muestra bien en la vista previa.

_ACP2E-3490 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_

#### [generador de páginas]Agregar una lista de productos para bloquear da como resultado errores

Ahora, agregar la lista de productos agrupados al bloque a través del generador de páginas no provoca errores

_ACP2E-3534 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/344fce23)_

### Contenido, SEO

#### La jerarquía de páginas de CMS puede causar problemas de reescritura de URL

Anteriormente, para la reescritura de URL permanentes personalizadas para páginas raíz que no son de sitios web, se redireccionaba infinitamente y la página nunca se cargaba. Después de aplicar esta corrección, la reescritura de URL personalizada para la página raíz que no es de sitio web funciona según lo esperado y no se produce ningún bucle de redirección.

_ACP2E-2870_

### Contenido, ensayo y vista previa

#### La regla de precio de catálogo no se muestra cuando está configurada para programarse con bloques dinámicos

El sistema ahora muestra correctamente el contenido dinámico asociado con las reglas de precios de catálogo programadas en la página de detalles del producto. Anteriormente, el contenido dinámico no se cargaba cuando se programaban las reglas de precios de catálogo.

_ACP2E-2979_

### Cliente/ Clientes

#### Front-end: la validación de la fecha de nacimiento falla en la página de creación del cliente

Asegúrese de que toda la validación funcione después de actualizar la dependencia del sistema moment.js a la última versión secundaria

_AC-12162 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Segmento de cliente > Condición > Historial del producto* > &quot;Se ha visto el producto&quot; no funciona

El sistema ahora muestra correctamente los clientes registrados coincidentes en la condición &quot;El producto se ha visto&quot; en Segmentos de clientes, cuando se cumple la condición. Anteriormente, incluso cuando se cumplía la condición, el recuento de clientes registrados coincidentes permanecía en cero.

_AC-13060_

#### El campo de texto de región no se restablece cuando se cambia la lista desplegable de países

El sistema ahora restablece el campo de texto de región cuando se cambia el país en el menú desplegable, asegurándose de que los valores anteriores no persistan. Anteriormente, al cambiar el país de la lista desplegable, no se restablecía el campo de región, lo que provocaba que se conservara el último valor guardado.

_AC-8499 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### Al eliminar el cliente, no se limpian todos los datos de sesión del explorador en Storefront para el cliente que ha iniciado sesión y que ha eliminado

Al eliminar un cliente, ahora se limpian todos los datos de sesión del explorador de la tienda para los clientes que han iniciado sesión y los que se han eliminado según lo esperado. El comprador puede seguir comprando y su navegador trata su sesión como una sesión de invitado. Anteriormente, cuando la cuenta de cliente de un comprador que iniciaba sesión se eliminaba del administrador, el explorador del comprador arrojaba errores de JavaScript.

_AC-9240 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

### Marco

#### [Pregunta]Configuración de tipo sin usar en `app/code/Magento/Translation/etc/di.xml`

El sistema ahora elimina las dependencias no utilizadas en la configuración, lo que mejora la limpieza y eficacia general del código. Anteriormente, había dependencias no utilizadas en la configuración de que no contribuían a ninguna funcionalidad.

_AC-10037 - [Problema de GitHub](https://github.com/magento/magento2/issues/38030) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38064)_

#### Pregunta/problema de extremo de V1/customers/password

El sistema ahora se adhiere a las restricciones establecidas dentro de la GUI de administración al procesar solicitudes de cambio de contraseña a través de la API, lo que evita el posible uso indebido de la función de restablecimiento de contraseña. Anteriormente, la API podía procesar solicitudes de cambio de contraseña fuera de las reglas definidas en la GUI de administración, lo que permitía un flujo constante de correos electrónicos restablecidos si se conocían correos electrónicos válidos.

_AC-10654 - [Problema de GitHub](https://github.com/magento/magento2/issues/38238) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### La configuración del barniz no excluye todos los parámetros de marketing

El sistema ahora excluye correctamente todos los parámetros de marketing comunes en la configuración de Barniz, lo que garantiza un seguimiento y análisis precisos. Anteriormente, no se excluían ciertos parámetros de marketing como gad_source, srsltid y msclkid, lo que producía posibles imprecisiones en la recopilación de datos.

_AC-10738 - [Problema de GitHub](https://github.com/magento/magento2/issues/38298) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39188)_

#### Proceso de indexación de error del proceso del índice de búsqueda del catálogo

El sistema ahora completa con éxito el comando re-index sin encontrar ningún error, independientemente de la versión de libxml compilada con PHP. Anteriormente, la ejecución del comando re-index resultaba en un error &quot;Error del proceso de índice de búsqueda en el catálogo durante el proceso de indexación&quot; cuando PHP se compilaba con ciertas versiones de libxml.

_AC-10838 - [Problema de GitHub](https://github.com/magento/magento2/issues/38254) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38553) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### Se han agregado los filtros created_at, status y grand_total a la consulta Pedidos del cliente y se ha corregido un error de varios filtros

El sistema admite ahora el uso de filtros created_at, status y grand_total en consultas de pedidos de clientes y ha resuelto un problema en el que no se aplicaban correctamente varios filtros. Anteriormente, el sistema no admitía estos filtros y no podía aplicar todos los filtros cuando se utilizaba más de uno en una consulta.

_AC-10941 - [Problema de GitHub](https://github.com/magento/magento2/issues/38392) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36949)_

#### Inundación aleatoria de consultas de bloques relacionados/de ampliación de venta/venta cruzada e indexación de precios

El sistema ahora optimiza las consultas de bloques relacionados, de ampliación de venta y de venta cruzada, lo que mejora el rendimiento y evita que el sitio caiga debido a consultas excesivas. Anteriormente, el sistema podía sobrecargarse con consultas de estos bloques, lo que provocaba ralentizaciones significativas y la posibilidad de derribar el sitio.

_AC-10991 - [Problema de GitHub](https://github.com/magento/magento2/issues/36667) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38050)_

#### Excepción: Advertencia: Intentando acceder al desplazamiento de la matriz en... -> Calendar.php desde la actualización a ICU 74.1 (PHP Intl)

Commerce ya no registra la siguiente excepción en exception.log cada vez que un comprador o comerciante visita la tienda o el administrador: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)

_AC-11423 - [Problema de GitHub](https://github.com/magento/magento2/issues/38214) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38364)_

#### [Problema]: se corrigieron problemas con los datos del cliente cuando el formulario contiene un elemento con el nombre `method`

El sistema ahora identifica correctamente el atributo &quot;method&quot; en los envíos de formularios, incluso cuando un elemento llamado &quot;method&quot; esté presente en el formulario. Esto garantiza un procesamiento preciso de los datos del cliente. Anteriormente, si un elemento de formulario se denominaba &quot;método&quot;, interfería con la identificación del atributo &quot;método&quot; en los envíos de formularios, lo que producía posibles problemas con la administración de datos de los clientes.

_AC-11476 - [Problema de GitHub](https://github.com/magento/magento2/issues/38484) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38449)_

#### [Problema] corrige PHPDocs para \Magento\Framework\Data\Collection::getItemById

Se han actualizado los PHPDocs del método \Magento\Framework\Data\Collection::getItemById para incluir null como posible tipo de valor devuelto y solucionar problemas con las herramientas de análisis estático. Anteriormente, los PHPDocs del método no especificaban null como posible tipo de valor devuelto, lo que daba lugar a advertencias o errores en el análisis estático cuando el método se utilizaba en afirmaciones condicionales.

_AC-11489 - [Problema de GitHub](https://github.com/magento/magento2/issues/38485) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38439)_

#### [Problema] Permitir solo las preferencias válidas durante `setup:di:compile`

El sistema genera ahora un error durante el comando `setup:di:compile` si se crea una preferencia para una clase que no existe o que se excluye específicamente, lo que garantiza que solo se permitan las preferencias válidas. Anteriormente, estos escenarios fallaban de forma silenciosa, lo que podía inutilizar cualquier complemento asociado con las clases originales.

_AC-11592 - [Problema de GitHub](https://github.com/magento/magento2/issues/38517) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33161)_

#### Magento está intentando modificar la propiedad de solo lectura en __ método de activación de LoggerProxy

El sistema ahora permite la modificación de propiedades de solo lectura anteriores en el método __wakeup de LoggerProxy, lo que garantiza un funcionamiento sin problemas sin obligar a los usuarios a emplear una solución alternativa. Anteriormente, un intento de reasignar el valor de una propiedad de solo lectura en el método __wakeup de LoggerProxy causaba problemas.

_AC-11651 - [Problema de GitHub](https://github.com/magento/magento2/issues/38526) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### [Problema] AC-2039 AC-1667 actualizar referencias TinyMCE

Se ha actualizado la última versión de tinymce en composer.json

_AC-11681 - [Problema de GitHub](https://github.com/magento/magento2/issues/38533) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36543) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### ChangelogBatchWalker no funciona en varios subprocesos

El sistema ahora admite la bifurcación de procesos para la indexación de MView, lo que evita errores durante la ejecución del indexador cuando se opera en varios subprocesos. Anteriormente, si se ejecutaba ChangelogBatchWalker en varios subprocesos, se eliminaban las tablas utilizadas por otros subprocesos, lo que provocaba un error durante la ejecución del indizador.

_AC-11696 - [Problema de GitHub](https://github.com/magento/magento2/issues/38246) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38248)_

#### [Problema] Cambiar nombre de variable con nombre incorrecto

El sistema ahora asigna un nombre correcto a la variable que contiene la cantidad de dinero que aún se puede reembolsar, lo que evita confusiones durante la depuración. Anteriormente, esta variable se denominaba incorrectamente como totalRefund, lo que podría provocar malentendidos para los desarrolladores.

_AC-11781 - [Problema de GitHub](https://github.com/magento/magento2/issues/38609) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36205)_

#### [Problema]: pasar atributos personalizados al vínculo actual mediante XML

El sistema ahora permite que se pasen atributos personalizados al vínculo actual mediante XML, lo que garantiza que estos atributos se muestren correctamente incluso cuando el vínculo es la página actual. Anteriormente, los atributos personalizados no se mostraban para el vínculo de página actual debido a que el método getAttributesHtml() no se utilizaba para el vínculo actual.

_AC-11809 - [Problema de GitHub](https://github.com/magento/magento2/issues/38500) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30070)_

#### La caché FPC integrada está dañada en la versión 2.4.7 para algunas configuraciones

El sistema ahora almacena en caché correctamente las páginas cuando se establece el parámetro MAGE_RUN_CODE, lo que garantiza un rendimiento óptimo. Anteriormente, las páginas no se almacenaban en caché en estas condiciones, lo que producía posibles problemas de rendimiento.

_AC-11819 - [Problema de GitHub](https://github.com/magento/magento2/issues/38626) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38646) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### [Problema] Corrija la incoherencia en la administración de excepciones entre los modos de desarrollo y producción

El sistema ahora gestiona de forma coherente las excepciones entre los modos de desarrollo y producción, lo que evita una redirección inesperada a la página de inicio de sesión cuando se produce una excepción. Anteriormente, una incoherencia en la gestión de excepciones podía provocar una redirección a la página de inicio de sesión en el modo de producción en lugar de mostrar el mensaje de excepción.

_AC-11829 - [Problema de GitHub](https://github.com/magento/magento2/issues/38639) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37712)_

#### Reemplazar la traducción &quot;Cuenta PayPal&quot; en token_list.phtml

El sistema ahora etiqueta la sección de métodos de pago de cuentas con token como &quot;Cuenta&quot; en lugar de &quot;Cuenta PayPal&quot; en la página Métodos de pago almacenados, lo que la hace más representativa de su función. Anteriormente, esta sección estaba etiquetada específicamente como &quot;Cuenta PayPal&quot;, lo que era engañoso cuando se añadían otros métodos de pago de cuentas tokenizables.

_AC-11852 - [Problema de GitHub](https://github.com/magento/magento2/issues/35622) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37959)_

#### Se ha perdido la compatibilidad con versiones anteriores en la clase Magento\Catalog\Model\ProductRepository

La clase ProductRepository mantiene ahora la compatibilidad con versiones anteriores al restaurar la clase de ayuda de inicialización como segundo parámetro, lo que garantiza que los módulos que se extienden desde esta clase funcionen según lo esperado. Anteriormente, la eliminación del Asistente para la inicialización del constructor en la clase ProductRepository provocaba una pérdida de compatibilidad con versiones anteriores, lo que obligaba a los usuarios a utilizar una solución.

_AC-11874: [problema de GitHub](https://github.com/magento/magento2/issues/38669)_

#### [Problema]: implementación de contenido estático. Error de tipo

El sistema ahora gestiona correctamente los archivos LESS vacíos durante la implementación de contenido estático, mostrando un mensaje de error &quot;El archivo LESS está vacío&quot;. Anteriormente, se producía un error de tipo incorrecto al encontrar un archivo LESS vacío durante la implementación.

_AC-11905 - [Problema de GitHub](https://github.com/magento/magento2/issues/38682) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38683)_

#### [Problema] [Vista] eliminó espacio adicional en el vínculo y la etiqueta de script

El sistema ahora garantiza que no haya espacios adicionales en las etiquetas de vínculo y script, lo que proporciona un código más limpio y eficiente. Anteriormente, se podían encontrar espacios dobles entre atributos en las etiquetas de vínculo y script.

_AC-12002 - [Problema de GitHub](https://github.com/magento/magento2/issues/32920) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32919)_

#### [Problema] evita un bucle infinito de configuración incorrecta

El sistema ahora evita un bucle infinito al impedir la asignación de autorreferencia en configuraciones de tipo virtual. Esto garantiza que la aplicación no se quede atascada en un bucle interminable al intentar anular la referencia a un nodo de referencia automática. Anteriormente, si una configuración de tipo virtual era de referencia propia, la aplicación giraba indefinidamente.

_AC-12127 - [Problema de GitHub](https://github.com/magento/magento2/issues/38822) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38794)_

#### Administrador de objetos no utilizado para Magento\Csp\Model\Mode\Data\ModeConfigured

El sistema ahora utiliza correctamente el Administrador de objetos al crear el objeto ModeConficonfigured, lo que permite utilizar complementos en este objeto. Anteriormente, no se utilizaba el Administrador de objetos, lo que impedía que se aplicaran complementos al objeto ModeConficonfigured.

_AC-12299 - [Problema de GitHub](https://github.com/magento/magento2/issues/38875) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38886)_

#### Comentario de bloque de documentación incorrecto en las alertas de precio y existencias de productos

El comentario del bloque de documentación para el método deleteCustomer en las alertas de precios y existencias de productos se ha corregido para reflejar con precisión que el método elimina todas las alertas de precios o productos de existencias asociadas a un cliente y sitio web determinados, no al cliente del sitio web. Anteriormente, el comentario indicaba de forma incorrecta que el método era para eliminar un cliente del sitio web.

_AC-12540 - [Problema de GitHub](https://github.com/magento/magento2/issues/38939) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39001)_

#### [Problema] Use la configuración compilada para los datos generados en lugar de la configuración general

El sistema utiliza ahora la configuración compilada para los datos generados en lugar de la configuración general, lo que reduce la transferencia de red y la sobrecarga de datos que dependen de una determinada versión del código. Este cambio evita la anulación de caché en instancias compartidas durante el intercambio de contenedores, lo que conduce a una mejor estabilidad y a una reducción del tiempo de inactividad. Anteriormente, ciertas clases principales utilizaban el tipo de configuración compartida, que podía provocar la anulación de la caché o el tiempo de inactividad de la aplicación debido a diferencias en las versiones de código en varios servidores.

_AC-12594 - [Problema de GitHub](https://github.com/magento/magento2/issues/38785) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/29954)_

#### [Problema] Elimina las referencias a los archivos de extjs que se eliminaron en e1ccdb...

El sistema ahora elimina las referencias a archivos de extjs que se eliminaron anteriormente, lo que elimina los errores en la consola del explorador y en el archivo de registro del sistema. Anteriormente, estas referencias causaban errores debido a la ausencia de los archivos a los que se hace referencia.

_AC-12597 - [Problema de GitHub](https://github.com/magento/magento2/issues/38960) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38951)_

#### [Problema] Limpieza menor: se corrigió el uso incorrecto de sprintf, solo se necesitan 2 marcadores de posición aquí y...

El sistema ahora utiliza correctamente la función sprintf con el número adecuado de marcadores de posición, lo que mejora la limpieza y coherencia del código. Anteriormente, la función sprintf se utilizaba incorrectamente con un argumento adicional, que no causaba ningún problema importante, pero no era el uso correcto.

_AC-12778 - [Problema de GitHub](https://github.com/magento/magento2/issues/39062) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38628)_

#### PHP 8.2.15 eliminó la extensión FTP

El sistema ahora incluye la extensión FTP como dependencia en el archivo composer.json, lo que garantiza la correcta configuración de las importaciones de CSV a través de FTP. Anteriormente, se producía un error al intentar configurar las importaciones de CSV a través de FTP debido a que la extensión FTP no estaba presente en el paquete PHP.

_AC-12857 - [Problema de GitHub](https://github.com/magento/magento2/issues/39083) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### [Problema] Corrige las clases incorrectas a las que se hace referencia en los módulos Magento.

El sistema ahora hace referencia correctamente a las clases en los módulos, lo que garantiza un funcionamiento más suave y evita bloqueos debido a clases no existentes. Esto incluye una corrección de errores en los módulos Indexer y CreditMemo, y la implementación de HttpGetActionInterface en la clase PrintAction. Anteriormente, las referencias de clase incorrectas provocaban errores y posibles bloqueos del sistema, y algunas funcionalidades, como el nombre de archivo de los archivos PDF de memo de crédito y la reindexación de existencias, no funcionaban según lo esperado.

_AC-12869 - [Problema de GitHub](https://github.com/magento/magento2/issues/39126) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37784)_

#### Capacidad para definir el área para el comando CLI `dev:di:info`

El sistema ahora permite a los desarrolladores definir un área para el comando CLI `dev:di:info`, lo que mejora el proceso de desarrollo y depuración. Anteriormente, este comando solo podía mostrar información del área GLOBAL.

_AC-12964 - [Problema de GitHub](https://github.com/magento/magento2/issues/38758) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38759)_

#### [Problema]: agregue la propiedad isMultipleFiles a la plantilla de elemento de formulario de imagen

Esta corrección evita que el botón &quot;Buscar o arrastrar imagen aquí&quot; desaparezca cuando se agrega una imagen en un elemento de formulario de imagen de varios archivos.

_AC-13149 - [Problema de GitHub](https://github.com/magento/magento2/issues/39219) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36325)_

#### La instalación :upgrade está fallando con la versión MariaDB 11.4 debido a cambios en el conjunto de caracteres y la intercalación

_AC-13247_

#### [Problema] Elimine todos los parámetros de obtención de marketing para minimizar la caché

El sistema ahora elimina todos los parámetros de obtención de marketing para optimizar la utilización de la caché, reflejando la lógica utilizada cuando Varnish está en uso. Anteriormente, estos parámetros podían provocar una hinchazón de la caché y reducir el rendimiento.

_AC-13279 - [Problema de GitHub](https://github.com/magento/magento2/issues/39266) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39099)_

#### [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Directory\Model\AllowedCountries::getAllowedCountries()

El método PHPDoc para AllowedCountries::getAllowedCountries() se ha corregido para proporcionar información precisa, lo que mejora la claridad y utilidad de la documentación. Anteriormente, el PHPDoc de este método contenía información incorrecta, lo que podría llevar a confusión o uso indebido del método.

_AC-13345 - [Problema de GitHub](https://github.com/magento/magento2/issues/39246) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39241)_

#### [Problema] elimina código de versiones de PHP que ya no se admiten.

Eliminación de código para versiones de PHP que ya no son compatibles con Magento

_AC-13348 - [Problema de GitHub](https://github.com/magento/magento2/issues/39361) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39202)_

#### [Problema] hace que el adaptador ImageMagick sea compatible con php8 (conversión implícita de flotante a int)

El sistema ahora garantiza la compatibilidad con PHP8 manejando correctamente los números flotantes al calcular las dimensiones de la imagen, evitando cualquier error debido a la conversión implícita de flotante a int. Anteriormente, el cálculo de las dimensiones de imagen podía dar como resultado números flotantes, que cuando se redondeaban implícitamente, provocaban un error.

_AC-13417 - [Problema de GitHub](https://github.com/magento/magento2/issues/39402) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37362)_

#### [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Framework\App\Config\ScopeConfigInterface

Esta actualización corrige las anotaciones PHPDoc en Magento\Framework\App\Config\ScopeConfigInterface para reflejar con precisión el tipo del argumento $scopeCode para los métodos getValue e isSetFlag.

_AC-13537 - [Problema de GitHub](https://github.com/magento/magento2/issues/39492) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39199)_

#### Magento\Framework\Filesystem\Driver\Http depende de la frase de razón OK

Se ha eliminado la comprobación de frase &quot;OK&quot; de Magento\Framework\Filesystem\Driver\Http::isExists

_AC-13725 - [Problema de GitHub](https://github.com/magento/magento2/issues/39546) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39558)_

#### El indexador de cuadrícula de cliente no funciona correctamente en el modo Actualizar por programación

Anteriormente, la cuadrícula del cliente se actualizaba instantáneamente, pero después de corregir, la cuadrícula del cliente se actualiza después de la ejecución de cron, pero no se refleja instantáneamente.

_AC-13810 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### error tipográfico en un archivo js.

El sistema utiliza ahora correctamente el término &quot;suscriptores&quot; en el archivo JavaScript, lo que garantiza la correcta funcionalidad de las funciones relacionadas. Anteriormente, un error tipográfico en el archivo JavaScript provocaba el uso incorrecto del término &quot;suscriptores&quot;.

_AC-6754 - [Problema de GitHub](https://github.com/magento/magento2/issues/36163) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36171)_

#### [Problema] Elimina la etiqueta `@author` prohibida

El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, la etiqueta `@author` estaba presente en algunos módulos, lo cual era contrario a los estándares de codificación establecidos.

_AC-8353 - [Problema de GitHub](https://github.com/magento/magento2/issues/37253) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37003)_

#### [Problema] Quitar la etiqueta `@author` prohibida de `Magento_Customer` (parte 2)

El sistema ahora se adhiere al estándar de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, la etiqueta `@author` estaba presente en algunos módulos, lo cual era contrario a los estándares de codificación establecidos.

_AC-8356 - [Problema de GitHub](https://github.com/magento/magento2/issues/37250) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37000)_

#### Espacio en la regla de saltos de sintaxis del editor para `[&lbrace;composer,auth&rbrace;.json]`

El sistema ahora aplica correctamente una sangría de 4 espacios a los archivos composer y auth.json, siguiendo una corrección de un error de sintaxis en la configuración del editor. Anteriormente, debido a un espacio en la sintaxis del editor de configuración, estos archivos tenían un formato incorrecto con una sangría de 2 espacios.

_AC-8659 - [Problema de GitHub](https://github.com/magento/magento2/issues/37394) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37395)_

#### [Problema] mejora el registro de errores cron

El sistema ahora captura y registra tanto STDERR como STDOUT para los procesos cron, proporcionando información de diagnóstico valiosa en escenarios donde los procesos cron fallan. Anteriormente, no se registraba ningún mensaje de error en los procesos cron y se perdían STDERR y STDOUT para los grupos cron que se ejecutaban en procesos independientes.

_AC-8662 - [Problema de GitHub](https://github.com/magento/magento2/issues/37453) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32690)_

#### [Problema] Agrega más colores a la salida de ciertos comandos cli de instalación

El sistema ahora agrega más colores a la salida de ciertos comandos de la interfaz de línea de comandos (CLI) de configuración, lo que mejora la legibilidad y la experiencia del usuario. Anteriormente, el resultado de estos comandos era más difícil de leer debido a la falta de diferenciación de color.

_AC-8984 - [Problema de GitHub](https://github.com/magento/magento2/issues/29335) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/29298)_

#### La actualización de Magento restablece general/region/state_required cuando se añade un nuevo país con el estado o la región requeridos.

El sistema ahora solo agrega el país modificado a la configuración &quot;general/region/state_required&quot; cuando se agrega un nuevo país con estados requeridos, lo que evita cualquier interrupción en el código personalizado que supone que la región está deshabilitada. Anteriormente, si se agregaba un nuevo país con estados requeridos, se restablecía la configuración &quot;general/region/state_required&quot; a los países predeterminados con un estado requerido, lo que podría romper la tienda.

_AC-9630 - [Problema de GitHub](https://github.com/magento/magento2/issues/37796) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38076)_

#### Diferencia en menos compilación entre php y nodejs library (grunt) con expresiones `calc` complicadas

Corregir la diferencia en menos compilación entre php y nodejs biblioteca (grunt) después de la actualización wikimedia/less.php:^5.x

_AC-9712 - [Problema de GitHub](https://github.com/magento/magento2/issues/37841) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b34c0a75)_

#### El error &quot;Tabla base o vista no encontrada&quot; se produce cuando se ejecuta la indexación parcial

La reindexación parcial ahora funciona correctamente con grandes registros de cambios en caso de conexión de base de datos secundaria

_ACP2E-2692 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Problemas después de actualizar MariaDB a 10.5.1 o superior

Se corrigió el problema en el cual los valores de fecha y hora de una base de datos se convertirían en 0000-00-00 00:00:00 después de la actualización de Mysql

_ACP2E-2844 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a12063bd)_

#### Discordancia de tipos en Comparación de datos al comprobar si los datos tienen cambios

Anteriormente, se llamaba cada vez al objeto de guardado sin ningún cambio de datos (para cualquier campo de datos numéricos, como int/float/double). Déclencheur el indicador _hasDataChanges para que sea true y llama a la función de guardado. Después de aplicar esta corrección, la función de guardado solo llamará si se cambian los datos. El valor de datos para int/float/double-check con el valor pasando a la función y hace una estricta coincidencia de tipos.

_ACP2E-2855 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### La importación [Cloud] no se puede usar con la variable de directorio

El producto se puede importar correctamente independientemente del nombre del archivo.

_ACP2E-2959 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### En ipad mini, el menú y el encabezado se cargan como móviles; en su lugar, deben cargarse como de escritorio.

El sistema ahora trata los dispositivos con una anchura de 768 píxeles como escritorio, lo que garantiza que el menú y el encabezado se carguen correctamente. Anteriormente, los dispositivos con una anchura de 768 píxeles se trataban como móviles, lo que provocaba que el menú y el encabezado se cargaran en una vista móvil.

_ACP2E-2966 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/35b1b1da) - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_

#### Error de tabla base o vista no encontrada al ejecutar mview cron mientras se tenía una operación DDL

El sistema ahora gestiona correctamente las operaciones de actualización de la base de datos mientras la actualización de mview se ejecuta en segundo plano, lo que evita la aparición de errores de &quot;Tabla base o vista no encontrada&quot;. Anteriormente, algunas operaciones de actualización de la base de datos podían provocar el error &quot;Tabla base o vista no encontrada&quot; si la actualización de mview se ejecutaba al mismo tiempo.

_ACP2E-3046_

#### La modificación de la longitud de la columna a través de db_schema.xml no funciona en el caso de claves externas

La modificación de la columna con clave externa mediante el esquema declarativo ahora no genera errores con MariaDB

_ACP2E-3230 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### Algunos de los registros de relaciones se guardan en la base de datos cuando se guarda el registro del pedido

Antes de la corrección, se activaban consultas UPDATE innecesarias que pueden afectar al rendimiento. Después de la corrección, se eliminaron las consultas UPDATE innecesarias.

_ACP2E-3361 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### [NUBE] En la administración hay muchos errores de JavaScript en la consola

Anteriormente, en el panel de administración hay muchos errores de JavaScript en la consola. Ahora, en el panel de administración, no habrá errores de JavaScript en la consola y todas las funciones predeterminadas de JavaScript se ejecutarán correctamente sin ningún problema.

_ACP2E-3375 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### [Cloud] Magento: se eliminó el mensaje en cola

Los mensajes en cola se están borrando correctamente. Antes de la corrección, dado que se estaba utilizando el sistema de cola SQL, se podían haber eliminado nuevos mensajes si el mensaje de la cola de limpieza se estaba ejecutando al mismo tiempo.

_ACP2E-3387 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Las entradas de clave de caché correspondientes no están disponibles en las etiquetas de caché, por lo que la limpieza de la caché no funciona correctamente

El modo LUA está ahora habilitado de forma predeterminada para el recolector de elementos no utilizados de caché de Redis para evitar condiciones de carrera

_ACP2E-3537 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a52ff98f)_

#### El valor Magento_DC_INDEXER__USE_APPLICATION_LOCK se omite

Después de la corrección, una variable ENV establecida en &quot;false&quot; se tratará como bool false, no como cadena &#39;false&#39;.

_ACP2E-3681 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Marco de trabajo, GraphQL

#### [Problema] introdujo la compatibilidad con los tipos escalares personalizados para el esquema de GraphQL

El sistema ahora admite tipos escalares personalizados para el esquema de GraphQL, lo que permite a los desarrolladores definir tipos escalares personalizados e implementaciones. Esta función puede resultar especialmente útil para expresar valores que pueden requerir validación, como HTML, correos electrónicos, URL, fechas, etc., y para casos más avanzados como atributos EAV. Anteriormente, el sistema no admitía el procesamiento de tipos escalares personalizados en GraphQL.

_AC-7976 - [Problema de GitHub](https://github.com/magento/magento2/issues/36877) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/34651) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### Marco, producto

#### Los informes 2.4.8-beta1 EE no se generan debido a la excepción de Magento

_AC-13011_

### Marco, marco de IU

#### Posibilidad de sobrescribir el valor de configuración incluso si está bloqueado

Antes de esta corrección, la configuración de diseño no se podía establecer mediante el comando bin/magento config:set y los valores bloqueados se podían cambiar manipulando el formulario que los mostraba. Después de la corrección, los valores bloqueados establecidos desde cli con —lock-env o —lock-conf ya no se pueden actualizar.

_ACP2E-3324 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

#### Magento_GraphQl ejecuta el procesamiento de encabezados incluso si el valor del encabezado no pasa la validación

El sistema ahora garantiza que el procesamiento del encabezado solo se ejecute una vez y solo si el valor del encabezado pasa la validación, lo que mejora la seguridad y evita posibles vulnerabilidades. Anteriormente, el procesamiento del encabezado se ejecutaba incluso si el valor del encabezado no pasaba la validación, lo que producía posibles vulnerabilidades y comportamientos inesperados debido al doble procesamiento de los valores del encabezado.

_AC-11729 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8f87c25)_

#### Las opciones de la tarjeta regalo física no tienen el orden de clasificación correcto

El sistema ahora ordena correctamente las opciones de los productos de tarjetas de regalo físicos cuando se consultan a través de GraphQL, lo que garantiza una representación coherente con la temática de Luma. Anteriormente, el criterio de ordenación era incorrecto según la temática de luma, lo que provocaba una visualización y un orden incorrectos de opciones como el nombre del remitente, el nombre del destinatario y la cantidad.

_AC-8951 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### La caché de resolución [GraphQL] se ha invalidado al crear, editar, mover o eliminar una actualización de ensayo

El sistema ahora garantiza que la caché de resolución no se invalide al crear, editar, mover o eliminar una actualización de ensayo, sino solo cuando la actualización de ensayo se aplique a la entidad. Anteriormente, la caché del solucionador se invalidaba prematuramente, incluso antes de que se aplicara la actualización de ensayo, lo que provocaba invalidaciones de caché innecesarias.

_AC-9157 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0c53bbf7)_

#### Caché de Fastly no borrada para la actualización del ensayo de contenido

Ahora, GraphQL con la caché de respuestas de contenido de PageBuilder se invalida cuando se actualizan las entidades relacionadas con el contenido de PageBuilder.

_ACP2E-2642 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Desactivación de la navegación por capas: no se elimina la agregación de Graphql

El problema se ha corregido después de aplicar la comprobación al solicitar una búsqueda de productos con agregaciones de categorías a través de una consulta de GraphQL al configurar la administración de Catálogo > Navegación por capas > Mostrar filtro de categorías.

_ACP2E-2653 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### La llamada de productos GraphQL que contiene el filtro de precios `&lbrace;from:&quot;0&quot;&rbrace;` no devuelve ningún resultado

Anteriormente, la búsqueda de productos de graphql con filtro para precios cero no arrojaba ningún resultado debido a una excepción generada. Ahora la búsqueda devuelve los resultados según lo esperado.

_ACP2E-2928 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Las traducciones de los atributos de devolución del cliente no se reflejan en la API de GraphQL para el StoreView correspondiente.

Las traducciones para atributos de devolución del cliente se reflejan en la API de GraphQL para el StoreView correspondiente.
Anteriormente, los atributos de retorno de los clientes para las respectivas vistas de tienda no se reflejaban en la API de GraphQL.

_ACP2E-2974 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### Llamada de GraphQL [Cloud] interrumpida para getPurchaseOrder con presupuesto de nodo

La llamada de GraphQL de orden de compra podrá ejecutar la tarea sin encontrar errores internos del servidor.

_ACP2E-3128 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6f4805f8)_

#### [Productos configurables en la nube] no se muestran en el sitio de producción si el producto no está habilitado en &quot;Todas las vistas de la tienda&quot;

El sistema ahora muestra correctamente los productos configurables en el sitio aunque el producto no esté habilitado en &quot;Todas las vistas de tienda&quot;, pero esté habilitado en ámbitos específicos de la vista de tienda.
Anteriormente, si un producto estaba deshabilitado en &quot;Todas las vistas de tienda&quot; y habilitado solo en ámbitos específicos de vista de tienda, los atributos del producto no se mostraban correctamente en la respuesta de GraphQL, lo que provocaba que el producto no se mostrara correctamente.

_ACP2E-3184 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/3f300077)_

#### Error de [Cloud] Products.graphql cuando el mismo producto simple se ha asignado a varios productos configurables

Anteriormente, con productos configurables independientes con el mismo producto simple, GraphQL devuelve un error. Después de aplicar esta corrección, diferentes productos configurables con el mismo producto simple, grapQL devuelve el resultado sin ningún error.

_ACP2E-3190 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/148c3ead)_

#### [Nube] problema con la autenticación de usuarios y el acceso de tokens entre sitios en la configuración de varios sitios

Las consultas de Información del cliente y Carro de GraphQL de la configuración de varios sitios comprueban si existe el cliente en un sitio web no predeterminado.
Anteriormente, la consulta funcionaba sin asegurarse de que el cliente existe en un sitio web no predeterminado en la configuración de varios sitios.

_ACP2E-3215 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### La paginación de elementos V2 del carro de compras de GraphQL no funciona correctamente

El problema se ha corregido pasando el valor correcto para el argumento de la página actual en la consulta de colección. Anteriormente, se pasaba un valor incorrecto para establecer la página actual, lo que provocaba el problema.

_ACP2E-3253 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Se debe especificar el valor del modelo [GRAPHQL] al obtener customerCart

La consulta &quot;customerCart&quot; de GraphQL ahora puede crear un carro vacío incluso cuando el presupuesto no está disponible en la base de datos. Anteriormente, esta operación fallaba debido a problemas de validación de país al crear el carro de compras vacío.

_ACP2E-3255 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

#### [GraphQl] Los elementos de la lista de deseos son visibles a través de GraphQl, pero no en la tienda

Productos de la lista de deseos donde no se enumeran correctamente cuando se solicita mediante GraphQL. Ahora, los productos de la lista de deseos se filtran según el contexto de tienda proporcionado.

_ACP2E-3380 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/55615e61)_

#### [GraphQL] Restablecer incoherencia de correo electrónico de contraseña entre contenido y asunto/vínculo

El problema se ha resuelto simulando el almacén correcto en el que la cuenta del cliente está registrada al enviar la solicitud de restablecimiento de contraseña, independientemente del almacén del sitio web.

_ACP2E-3404 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### La consulta de GraphQL de [Cloud] productos devuelve productos relacionados no asignados al sitio web actual

Anteriormente, para la consulta de graphQL, los productos relacionados con varias tiendas no se mostraban correctamente para la consulta de productos. Después de aplicar esta corrección, para los productos de, graphQL consulta los productos relacionados con varias tiendas que se muestran en consecuencia.

_ACP2E-3419 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### El uso del ID de tienda incorrecto en el encabezado de GraphQL provoca un error grave de memoria

Enviar un código de almacén incorrecto en una solicitud de GraphQL ya no provoca un consumo de memoria excesivo.

_ACP2E-3447 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### [Nube] respuesta de 500 a la respuesta vacía de Graphql en 2.4.7

Después de la corrección, las solicitudes de graphql no válidas no se registrarán en el archivo exception.log.

_ACP2E-3467 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### [Problemas de nube] con la API de Graphql

Antes de la corrección mediante el servidor de aplicaciones Graphql, la solicitud de dirección del cliente no devolvía los datos más recientes.

_ACP2E-3492 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### El producto deshabilitado sigue apareciendo en los elementos relacionados, de venta adicional y de venta cruzada en la consulta de GraphQL

Graphql ahora proporciona una respuesta correcta para los productos relacionados, de ampliación de venta y de venta cruzada desactivados

_ACP2E-3505 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [CLOUD]: error de GraphQl Error interno del servidor: mutación placeOrder

La mutación &quot;placeOrder&quot; con información del código de cupón en la solicitud ya no produce una excepción de error interno; el pedido se realizó correctamente. Anteriormente, fallaba con &quot;Error interno del servidor&quot;.

_ACP2E-3647 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/982b1c42)_

#### El porcentaje de descuento no se calcula para los productos agrupados con precio dinámico

Se ha agregado una corrección para el porcentaje de descuento de product.price_details que no muestra el valor correcto para los productos agrupados con el precio dinámico habilitado y el cupón de descuento aplicado.

_LYNX-426_

#### Los productos agrupados siguen mostrando &quot;IN_STOCK&quot; cuando uno de sus productos agrupados está agotado

Se ha resuelto el problema de que los productos agrupados seguían mostrando &quot;IN_STOCK&quot; incluso cuando uno de sus productos agrupados estaba agotado.

_LYNX-485_

#### not_available_message y only_x_left_in_stock no muestran el mismo stock disponible

Se ha resuelto el problema en el que los argumentos not_available_message y only_x_left_in_stock mostraban una disponibilidad de existencias incoherente

_LYNX-486_

#### el campo original_row_total devuelve un valor incorrecto

Se ha resuelto el problema con el campo original_row_total, que devolvía valores incorrectos cuando se seleccionaban opciones personalizadas

_LYNX-488_

#### La miniatura del producto agrupado debe mostrarse según la configuración     .

Se ha resuelto el problema para garantizar que la miniatura del producto agrupado se muestre según los ajustes de configuración

_LYNX-503_

#### Error al consultar selected_options en OrderAddress

Se ha actualizado AttributeSelectedOptions a custom_attributesV2 en la respuesta de GraphQL de la dirección de pedido.

_LYNX-510_

#### original_item_price no incluye descuentos

Se ha actualizado original_item_price para incluir descuentos.

_LYNX-512_

#### El mensaje No disponible no muestra la cantidad de inventario disponible

Se ha resuelto el mensaje de error y el código de error de la mutación AddProductsToCart para alinearlos con la configuración del mensaje &quot;no disponible&quot;

_LYNX-530_

#### El estado &quot;OUT_OF_STOCK&quot; vuelve sobre Simple con opciones personalizadas productos con opciones de selección múltiple

Se ha actualizado la resolución StockStatusProvider en el paquete de inventario para corregir stock_status para productos simples con opciones personalizadas.

_LYNX-532_

#### Error (GQL): cart.itemsV2.items.product.custom_attributesV2 devuelve un error de servidor

Se ha resuelto el error del servidor que se producía cuando una consulta del carro de compras incluía los atributos personalizados de un producto al agregar un producto sin atributos personalizados.

_LYNX-533_

#### orders/date_of_first_order siempre devuelve nulo

Se ha resuelto el problema en el que pedidos > date_of_first_order siempre devolvía nulo.

_LYNX-536_

#### El cliente no debe poder cancelar un pedido enviado parcialmente

Se ha añadido validación para restringir la cancelación de un pedido enviado parcialmente por parte de los clientes.

_LYNX-544_

#### Códigos de error para la cancelación de pedidos basados en el mensaje de error

Los códigos de error para la cancelación de pedidos ahora se basan en el mensaje de error específico.

_LYNX-548_

#### Retroceder de propiedades relacionadas con cookies de privadas a protegidas

Revierte la visibilidad de las propiedades del constructor de clases Magento\Framework\App\PageCache\Version de privada a protegida

_LYNX-581_

#### Aumentar la complejidad máxima de las consultas de GraphQL predeterminadas a 1000

Se ha aumentado la complejidad máxima predeterminada de las consultas de GraphQL de 300 a 1000.

_LYNX-600_

#### GQL: itemsV2 > Total de fila original, los precios de rango de precios se devuelven como 0,00 $ para el producto descargable con opciones de archivo que tiene precios independientes.

Se ha resuelto un problema en el cual los productos descargables con las opciones de compra de vínculos independientes activadas devolvían 0 $ para itemsV2 > Total de fila original, el rango de precios devuelto como 0,00 $ para los productos con opciones de archivo con precios independientes.

_LYNX-620_

#### El esquema de una tabla cuando se crea una marca nueva es diferente al de al actualizar

Se ha resuelto un problema en el cual, al agregar una nueva columna VARCHAR a una tabla existente, se producían errores de prueba debido a diferencias de esquema entre instalaciones nuevas y actualizaciones. El método modifyColumn() ahora gestiona correctamente las columnas VARCHAR al establecer el conjunto de caracteres y la intercalación predeterminados.

_LYNX-711_

#### Compatibilidad de GraphQl para la versión PHP-8.4

Se corrigieron problemas de compatibilidad de GraphQL con PHP 8.4 en varios solucionadores, lo que garantiza una funcionalidad sin problemas. Se han actualizado los archivos afectados en los módulos CatalogRule, Customer, GiftMessage, GiftCard y GiftWrapping.

_LYNX-772_

### GraphQL, inventario/MSI

#### La mutación MergeCart genera una excepción cuando los carros de compras de origen y destino tienen los mismos elementos de paquete

&#39;-

_ACP2E-2607 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c971859e) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, inventario/MSI, rendimiento

#### Sitio caído después de la actualización

Se mejora el rendimiento de recuperar productos agrupados mediante GraphQl.

_ACP2E-1716 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, Rendimiento

#### [GraphQL Resolver] Los datos de Customer Resolver no se han invalidado en la importación

La caché de GraphQL customer resolver ahora se invalida como se espera cuando se edita o elimina un cliente mediante importaciones. Anteriormente, la caché no se invalidaba y los datos del cliente se podían editar o eliminar durante la importación.

_AC-9569 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, Buscar

#### La ordenación de la lista de productos de GraphQL por varios parámetros no funciona

La ordenación de productos por varios campos en GraphQl ahora funciona como se describe en la documentación

_ACP2E-2809 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Lista de productos GraphQL query limited to total_count 10.000 productos solamente

Después de la corrección, el resultado de la búsqueda no se limita a 10000 productos, sino que es posible obtener todos los productos que coinciden con los criterios de búsqueda incluso si el recuento es superior a 10000.

_ACP2E-948 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, marco de prueba

#### Error de prueba de integración de Magento\GraphQl\App\GraphQlCustomerMutationsTest.php

&#39;-

_ACP2E-3363 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importación/exportación

#### Problema en la importación del producto cuando se proporciona con opciones personalizadas-tipo: archivo (el producto creado no contiene precio para la opción personalizada y muestra solo la primera extensión de tipo de archivo proporcionada)

El sistema ahora importa correctamente los datos del producto con opciones personalizadas del tipo &quot;archivo&quot;, asegurándose de que se muestren todas las extensiones de archivo proporcionadas y se incluya el precio de la opción personalizada. Anteriormente, durante la importación del producto, si se proporcionaba una opción personalizada de tipo &quot;archivo&quot; con más de una extensión de archivo, solo se mostraba la primera extensión y faltaba el precio de la opción personalizada.

_AC-12172 - [Problema de GitHub](https://github.com/magento/magento2/issues/38805) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38926)_

#### Tiempo de ejecución incorrecto para la operación de importación en la cuadrícula Historial de importación

El tiempo de ejecución del informe de importación se muestra correctamente independiente de la configuración regional del administrador.

_ACP2E-2710 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Se están creando clientes duplicados con la misma dirección de correo electrónico mediante la importación

Se actualiza la importación del cliente mientras el uso compartido de cuentas está establecido en Global, el cliente importado que existe en el sistema.
Se ha duplicado el cliente importado anteriormente.

_ACP2E-2737 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### Agregar/actualizar importación en productos duplicando opciones personalizables

El problema se ha resuelto asignando el almacén correcto a las opciones de producto durante las importaciones de CSV de opciones de producto.
Anteriormente, se asignaba al almacén de administración en lugar de a su respectivo almacén.

_ACP2E-2902 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### Fecha &quot;created_at&quot; del cliente no convertida a la zona horaria del almacén tras la exportación

Un valor de fecha &quot;created_at&quot; de columna se convierte al formato de fecha adecuado en función de la zona horaria de tienda en la sección CSV de exportación del cliente.

_ACP2E-2990 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3056e9cb)_

#### [Cloud]: error al comprobar los datos en la importación de datos con CSV

No se produce ningún error al comprobar los datos durante la importación de CSV. Anteriormente, se mostraba el mensaje de error: &quot;No podemos encontrar un cliente que coincida con este correo electrónico y código de sitio web en la fila o filas: 1&quot; al comprobar los datos en la sección de importación con CSV del administrador.

_ACP2E-3165 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/8459b17d)_

#### Falta el botón Importar

Resuelva el problema del botón Importar que falta después de las comprobaciones de datos con registros correctos e incorrectos en el CSV. Anteriormente, el botón de importación no se muestra después de la comprobación de datos con registros correctos e incorrectos en el CSV.

_ACP2E-3172 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1819fe73)_

#### No se puede importar la dirección del cliente exportado

La importación de direcciones de clientes se realizará según lo esperado. Anteriormente, un archivo de importación de direcciones de clientes no pasaba la validación si Compartir cuentas de clientes = Global y hay dos sitios web en los que el sitio web predeterminado tiene una lista de países restringidos y la dirección que se importa es para otro sitio web en el que los países permitidos son diferentes

_ACP2E-3382 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Nube]: La cantidad errónea en el archivo CSV no generó error

Ahora la importación de fuentes de stock generará un error de validación para valores no numéricos en la columna de cantidad. Anteriormente, al importar orígenes de stock con valores no numéricos en la columna de cantidad, la cantidad se establecía en 0.

_ACP2E-3448 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

#### El mensaje de error de clave URL duplicado generado al importar un producto no es correcto cuando la clave URL ya pertenece a una categoría

Mostrar el mensaje de error correcto durante la comprobación de importación de productos, cuando el cliente intentó importar el producto cuando la clave URL del producto ya pertenece a una categoría.

_ACP2E-3455 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### La exportación de productos causa OOM incluso con límite de memoria 4G

Antes de esta corrección, la exportación del producto fallaba si los atributos del producto tenían miles de valores de opción incluso con memoria disponible 4G. Después de esta corrección, la exportación del producto debe terminar de exportar el archivo CSV.

_ACP2E-3475 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

#### Procesos de importación de [Cloud] que interfieren entre sí

Los mensajes correctos se muestran si el mismo usuario administrador realiza dos o más operaciones de importación utilizando la misma sesión de usuario.

_ACP2E-3527 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

### Importación/exportación, Rendimiento

#### El tiempo de importación del producto [Cloud] ha aumentado significativamente

Antes de la corrección, la importación de productos de catálogo con más de 10 000 entradas tenía una degradación del tiempo significativa. Después de la corrección, la importación del producto del catálogo se ejecuta de manera oportuna.

_ACP2E-3476 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/87d012e5)_

### Instalar y administrar

#### La actualización a Magento falla en MariaDB 11.4 + 2.4.8-beta1

La actualización debería producirse sin errores.

_AC-13242 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7b336d0a)_

#### No se ha agregado ningún VCL de exportación para el botón Barniz 7 en el panel de administración

Se ha añadido el botón Exportar VCL para Barniz 7 al panel de administración.

_ACP2E-2102 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventario/MSI

#### La actualización de inventario del producto configurable falla cuando la base de datos utiliza prefijos

El sistema actualiza ahora correctamente el inventario de productos configurables cuando la base de datos utiliza prefijos, lo que evita cualquier mensaje de error y garantiza que se guarde la cantidad correcta. Anteriormente, se producía un error al intentar guardar la cantidad de inventario para productos simples dentro de un producto configurable si la base de datos utilizaba prefijos.

_AC-10750: [problema de GitHub](https://github.com/magento/magento2/issues/38045)_

#### La clave de la API de Google de Google no funciona al agregar un mapa con atributos

El sistema ahora es compatible con la última versión 3.56 de la API de Google Maps, lo que permite a los usuarios añadir correctamente un bloque de contenido de mapa del menú PageBuilder al escenario sin encontrar ningún error. Anteriormente, los usuarios no podían agregar un bloque de contenido de mapa debido a problemas de compatibilidad con la versión de la API de Google Maps, lo que provocaba un mensaje de error &quot;Se ha producido un error&quot;.

_AC-11593 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### No se puede crear el envío para el artículo de pedido con varios orígenes y SKU dañados

Anteriormente, cuando los espacios se añadió por error en el SKU a través de la base de datos conduce a un error en la página de envío que ahora es fijo y el recorte automático se considera como error humano y no se encontró ningún impacto. Por lo tanto, el envío se creó correctamente.

_AC-13922 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/c18eb5fa)_

#### [Probar] productos en paquete con 0 inventario visible en la tienda

El producto del paquete no se muestra en los sitios web adicionales que utilizan stock adicional.

_ACP2E-1411_

#### [Nube] problema crítico con la lista de productos con espacios vacíos

El sistema ahora muestra correctamente las listas de productos sin espacios vacíos cuando los productos están configurados en &quot;Agotado&quot;, lo que garantiza una visualización coherente y precisa de los productos disponibles. Anteriormente, si se establecía un producto en &quot;Agotado&quot;, aparecía un espacio vacío en la lista de productos, lo que afectaba al diseño y podía confundir a los clientes.

_ACP2E-2794 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/b59e48ca)_

#### No se puede enviar el pedido cuando el almacén de recogida MSI está habilitado

Se ha mejorado el rendimiento de inventario al crear el envío en caso de que haya muchas fuentes con recogida en la tienda

_ACP2E-3335 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/9f3e63d1)_

#### El reíndice de Cron no puede actualizar la disponibilidad del producto en el front-end

Anteriormente, los productos permanecían sin existencias en el front-end después de actualizar el estado del pedido pendiente mediante la API de REST. Ahora, después de actualizar el estado del pedido pendiente mediante la API de REST, los productos se muestran como en stock.

_ACP2E-3355 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/e6fe0aa7)_

#### Agregar imágenes a objetos configurables no funciona cuando MSI está habilitado.

La carga de imágenes para el producto configurable ahora funcionará como se espera cuando se utilice el módulo de inventario. Anteriormente, la carga de imagen no funcionaba

_ACP2E-3357 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/fdf409aa)_

#### Problema con el paquete de producto + MSI en Clean M2.4.7-p3

Anteriormente, para los productos de paquete de inventario después de la duplicación con el mismo producto simple, el producto simple no se puede guardar. Después de aplicar esta corrección, el producto simple se puede guardar correctamente sin excepciones.

_ACP2E-3470 - [Problema de GitHub](https://github.com/magento/magento2/issues/39358) - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/0208e433)_

### Inventario / MSI, búsqueda

#### Todos los productos están indexados con [is_out_of_stock] = 1 cuando el SKU no está establecido como atributo en el que se puede buscar

Después de la corrección, el &quot;is_out_of_stock&quot; del índice de búsqueda en el catálogo es correcto, incluso cuando no se puede buscar en el SKU.

_ACP2E-3413 - [Contribución de código de GitHub](https://github.com/magento/inventory/commit/5b21b7af)_

### Pedido

#### Pantalla de resumen de pedidos back-end: Cantidad no satisfecha no visible en el nivel de artículo de pedido

El sistema ahora muestra el número de artículos no pedidos en la columna de cantidad en la pantalla de información general de pedidos backend. Esto garantiza que los usuarios puedan realizar un seguimiento preciso del estado de todos los elementos de un pedido. Anteriormente, la columna de cantidad solo mostraba el número de artículos pedidos, facturados y enviados, pero no mostraba el número de artículos no pedidos.

_AC-10828 - [Problema de GitHub](https://github.com/magento/magento2/issues/38252) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38320)_

#### [Problema] Se usó un ID de almacén incorrecto en el Procesador de direcciones de pedidos

El sistema ahora utiliza correctamente el ID de tienda asociado a un pedido al procesar la dirección del pedido, lo que garantiza que las direcciones tengan el formato correcto según su ID de tienda respectivo. Anteriormente, el sistema utilizaba incorrectamente el ID de tienda actual, lo que podía provocar un formato de dirección incorrecto en los casos en que era necesario enviar varios correos electrónicos de pedidos de diferentes tiendas.

_AC-10994 - [Problema de GitHub](https://github.com/magento/magento2/issues/38412) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37932)_

#### Problema de almacenamiento en caché JoinProcessor

El sistema ahora aplica correctamente JoinProcessor para cada iteración, incluso con llamadas consecutivas, lo que garantiza una recuperación de datos precisa. Anteriormente, JoinProcessor se marcaba incorrectamente como ya aplicado en iteraciones consecutivas, lo que producía errores en la recuperación de datos.

_AC-11690 - [Problema de GitHub](https://github.com/magento/magento2/issues/27504) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37550)_

#### [Problema] Precio de envío que se muestra diferente en el PDF impreso

El sistema ahora muestra correctamente los precios de envío en PDF impresos según la configuración de impuestos, lo que garantiza la coherencia entre la página de vista de facturas de pedidos de venta y la factura impresa. Anteriormente, el precio de envío mostrado en el PDF impreso excluía impuestos, independientemente de la configuración de impuestos.

_AC-11798 - [Problema de GitHub](https://github.com/magento/magento2/issues/38608) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38595) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1bafc571)_

#### Reordenar con un producto configurable principal eliminado

Ahora, al reordenar con el producto eliminado, el sistema no mostrará el botón de reordenar para reordenar

_AC-13839 - [Problema de GitHub](https://github.com/magento/magento2/issues/39568) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39601)_

#### [Problema] Corrección incorrecta \Magento\Sales\Model\Order\Email\Container\Template::$id propiedad

Esto corrige el phpdoc incorrecto para \Magento\Sales\Model\Order\Email\Container\Template::$id, en realidad $id es type int pero en realidad es string.

_AC-13924 - [Problema de GitHub](https://github.com/magento/magento2/issues/39151) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39150)_

#### No se pueden guardar los cambios del número de teléfono en los detalles del pedido existente

Ahora el usuario puede añadir el prefijo internacional 00 en el campo telefónico de la dirección de pedido

_ACP2E-2622 - [Problema de GitHub](https://github.com/magento/magento2/issues/38201) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/12e071c3)_

#### No se pueden enviar los correos electrónicos

El sistema ahora incluye una opción de configuración async_sending_tries para especificar el número de intentos de enviar un correo electrónico antes de detenerse, lo que mejora la administración de los envíos de correo electrónico fallidos cuando se habilita &quot;Envío asincrónico&quot;. Anteriormente, si un correo electrónico no se enviaba, el sistema intentaba reenviarlo continuamente, lo que daba como resultado un bucle interminable de mensajes de error en el registro del sistema.

_ACP2E-2734 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Se cambió el estado del pedido de [Cloud] a completo cuando se reembolsa parcialmente un pedido enviado parcialmente

Al emitir una nota de abono, el estado del pedido ya no cambia a &quot;completado&quot; si hay artículos que aún no se han enviado.

_ACP2E-2756 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7e0e5582)_

#### [CLOUD] no puede deshabilitar el envío de correos electrónicos desde la IU de administración como muestran los documentos de desarrollo

El sistema evita ahora correctamente que se envíen correos electrónicos de ventas cuando se desactiva la comunicación por correo electrónico. Estos correos electrónicos ya no se enviarán cuando se vuelva a habilitar la comunicación por correo electrónico. Anteriormente, los correos electrónicos de ventas iniciados mientras la comunicación por correo electrónico estaba desactivada se enviaban una vez que se volvía a habilitar.

_ACP2E-3002 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c8931218)_

#### Pedido cerrado sin reembolso completo

El sistema mantiene ahora correctamente el estado del pedido como &quot;Procesando&quot; y el estado de la factura como &quot;Pendiente&quot; cuando se crea un envío en un pedido con un pago no capturado. Esto garantiza que los pedidos solo se marquen como &quot;Cerrados&quot; después de ser reembolsados por completo. Anteriormente, si se creaba un envío para un pedido con una factura pendiente, el estado del pedido se cambiaba incorrectamente a &#39;Cerrado&#39;.

_ACP2E-3045 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### [Nube] No se puede crear el pedido en administración en una tienda si solamente no se configuró la Dirección de facturación predeterminada

Ahora aparece el mensaje de error &quot;Ya existe un cliente con la misma dirección de correo electrónico en un sitio web asociado&quot;. se muestra si un cliente no tiene una dirección de facturación predeterminada e intenta crear un pedido en otra tienda.

_ACP2E-3311 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d75cff27)_

#### Solicitudes de pedido de lugares duplicadas por el administrador enviadas

Anteriormente, se podía hacer clic en el botón &quot;Enviar pedido&quot; del panel de administración varias veces o activarlo pulsando repetidamente la tecla &quot;Intro&quot;, lo que provocaba envíos duplicados o de pedidos con errores. Ahora, evita acciones adicionales hasta que la solicitud se procese por completo, lo que garantiza que solo se envíe una solicitud.

_ACP2E-3416 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### El administrador puede realizar el pedido incluso sin forma de pago

El método de pago seleccionado anteriormente ahora se conserva cuando el método de pago vuelve a aparecer en la lista de pagos disponibles.

_ACP2E-3425 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d50f6b5d)_

#### Los elementos se duplican después de crear un pedido desde el administrador en - Mozilla Firefox navegador

Los productos añadidos mediante &quot;Añadir productos por SKU&quot; ya no se duplican en Firefox al crear un pedido en el administrador.

_ACP2E-3518_

### Pedido, Pagos

#### El administrador puede realizar el pedido incluso sin forma de pago

Anteriormente, el comerciante podía realizar pedidos desde el panel de administración sin seleccionar un método de pago. Ahora, el comerciante necesita un método de pago para proceder a realizar un pedido.

_ACP2E-3233 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fd5cf3af)_

### Pedido, Devoluciones

#### El reembolso del pedido genera un abono duplicado

Emitir el reembolso a través de la API de REST cuando se ejecutaron dos solicitudes idénticas simultáneamente ya no creará notas de abono duplicadas.

_ACP2E-2982 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a4fbf702)_

### Pedido, Impuesto

#### [NUBE] Base_row_total incorrecto en la API de pedido RESTFUL al habilitar transacciones internacionales y aplicar descuentos de cupones

Ahora se devuelve el base_row_total correcto desde la API de pedidos RESTFUL cuando se habilita la transacción internacional y se aplica el descuento de cupón.

_ACP2E-3003 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9af794a4)_

### Otros

#### [Braintree] reembolsa la transacción de almacenamiento en línea como transactionid-return

_PAQUETE-3394_

#### [Braintree] + [CLOUD] Braintree (tarjeta de crédito) no puede dividir los cargos

_PAQUETE-3421_

#### El certificado SSL de [Braintree] [Cloud]Braintree caduca el 30 de junio

_PAQUETE-3422_

#### cookie private_content_version devuelta en consultas GQL

Se ha corregido un problema por el cual la cookie private_content_version se devolvía en consultas de GraphQL, incluso cuando la cookie de sesión estaba deshabilitada. La cookie ya no se incluye en las respuestas de GraphQL cuando la sesión está desactivada, como se espera.

_LYNX-339_

#### Error del servidor en las props de correo electrónico en consultas de tarjetas regalo físicas

Se ha corregido un problema en el cual las consultas para sender_email y recipient_email en tarjetas de regalo físicas provocaban un error del servidor. Estas props ahora se devuelven correctamente para las tarjetas de regalo virtuales y el comportamiento de la consulta es coherente.

_LYNX-366_

#### El atributo is_available en CartItemInterface siempre devuelve el valor &quot;false&quot; para los productos configurables

Se ha corregido un problema en el cual el atributo is_available de CartItemInterface siempre devolvía false para productos configurables en stock. Ahora, refleja correctamente la disponibilidad como verdadera cuando corresponde.

_LYNX-380_

#### El atributo is_available de CartItemInterface devuelve el valor &quot;True&quot; incluso cuando el stock comercializable es inferior a la cantidad del producto

Se ha corregido un problema por el cual el atributo is_available de CartItemInterface devolvía incorrectamente el valor true incluso cuando la cantidad del artículo del carro de compras superaba el stock vendible.

_LYNX-382_

#### El atributo only_x_left_in_stock de ProductInterface no es preciso en productos configurables

Se ha corregido un problema en el cual el atributo only_x_left_in_stock de ProductInterface no reflejaba con precisión el stock disponible para variantes de productos configurables en el carro de compras. Ahora, el valor only_x_left_in_stock corresponde correctamente a los niveles de stock de variante reales, lo que garantiza que se devuelvan datos de inventario precisos en la consulta GQL del carro de compras.

_LYNX-395_

#### La miniatura del marcador de posición devuelve cuando un producto simple se agrega al carro de compras dentro de un producto agrupado

Se ha corregido un problema por el cual al agregar un producto simple (parte de un producto agrupado) al carro de compras se devolvía una imagen en miniatura de marcador de posición, incluso cuando el producto tenía una imagen asignada.
Detalles de la corrección:
- La miniatura del producto ahora muestra correctamente la imagen asignada si está disponible.
- La selección de miniaturas respeta la configuración de administración en:
Tiendas > Configuración > Ventas > Cierre de compra > Carro de compra > Imagen de producto agrupada.
Esto garantiza un comportamiento de miniaturas coherente para los productos agrupados en función de la configuración de la tienda.

_LYNX-399_

#### Los atributos de opción personalizados del cliente no funcionan con valores enteros

Se ha corregido un problema en el cual los atributos de opción personalizados del cliente no funcionaban cuando el valor devuelto era un número entero. Las opciones personalizadas ahora administran correctamente y devuelven valores enteros como se espera.

_LYNX-400_

#### Error interno del servidor al intentar obtener priceDetails para productos en paquete con precio dinámico

Se ha resuelto un problema en el cual la consulta de price_details para paquetes de productos con precios dinámicos a través de GraphQL provocaba un error interno del servidor. Esta mejora garantiza consultas de carro estables al trabajar con productos de paquete configurados con precios dinámicos.

_LYNX-402_

#### only_x_left_in_stock siempre devuelve 0 para los productos configurables

Se ha resuelto un problema en el cual el atributo only_x_left_in_stock siempre devolvía 0 para los productos configurables cuando se añadía utilizando el SKU principal con opciones.
Detalles de la corrección:
- El valor only_x_left_in_stock ahora refleja con precisión el stock de la variante secundaria seleccionada en lugar del SKU principal.
- Esto garantiza que los niveles de stock se muestren correctamente para las variaciones de productos configurables en el carro de compras y las páginas de productos.

_LYNX-403_

#### Error de GraphQL: tipo de &quot;archivo&quot; no admitido en la consulta de opciones personalizables

Se ha corregido un problema en el cual GraphQL devolvía un error para las opciones personalizables del tipo &quot;archivo&quot; en los elementos del carro de compras. La consulta ahora devuelve correctamente los detalles de todos los tipos de opciones personalizables, incluidas las opciones basadas en archivos, sin causar errores.

_LYNX-405_

#### La consulta de GraphQL no devuelve el precio normal calculado correcto para los productos personalizables

Se ha corregido un problema en el cual GraphQL no devolvía el precio normal calculado correcto para los productos personalizables. La consulta ahora incluye correctamente el precio normal calculado con valores personalizables aplicados (por ejemplo, 125 $) en la propiedad precios, lo que refleja tanto el precio base como cualquier coste de personalización adicional.

_LYNX-411_

#### AppliedTaxes mediante EstimatedTotals persiste con mutaciones actualizadas

Se ha corregido un problema con la mutación Totales estimados en el cual los impuestos aplicados persistían en un carro de compras incluso después de actualizar la región o el código postal. La mutación ahora actualiza correctamente los impuestos aplicados al cambiar entre los valores de región y código postal, asegurándose de que solo se aplique la regla fiscal correcta en función de los datos del carro de compras actual.

_LYNX-412_

#### El atributo is_available de CartItemInterface devuelve el valor &quot;True&quot; incluso cuando el stock comercializable es inferior a la cantidad del producto

Se ha corregido un problema por el cual el atributo is_available de CartItemInterface devolvía incorrectamente el valor true incluso cuando el stock comercializable era inferior a la cantidad de producto solicitada. El campo is_available ahora devuelve correctamente el valor false cuando la cantidad del producto supera el stock disponible.

_LYNX-420_

#### No se puede añadir un cupón al carro de compras solo para envíos con descuento

Se ha corregido un problema en el cual no se podía aplicar un cupón a un carro de compras para descuentos solo de envío. El cupón ahora se aplica correctamente al importe de envío cuando se utiliza una regla de ventas sin condiciones de producto, lo que garantiza que se aplique el descuento esperado al coste de envío.

_LYNX-421_

#### Precio normal del producto con 12 decimales y valor incorrecto

Se ha corregido un problema por el cual el valor regular_price de las rutas GraphQL product.price_range.maximum_price y minimum_price no coincidía con el precio de catálogo cuando se aplicaban varios tipos impositivos. Ahora, el valor regular_price refleja de forma coherente el precio de catálogo en todas las configuraciones de impuestos, lo que garantiza una precisión en los precios unitarios, los cálculos de coste total de las filas y las comprobaciones de descuentos en el Resumen del carro de compras.

_LYNX-425_

#### Error del servidor de GraphQL en el carro con el producto agrupado agotado

Se ha corregido un problema en el cual GraphQL devolvía un error interno del servidor al recuperar un carro de compras que contenía un producto agrupado con un elemento sin existencias, específicamente cuando la consulta incluía la propiedad itemsV2. GraphQL ahora devuelve correctamente una lista de elementos con mensajes de error relevantes adjuntos a la entrada del elemento de producto agrupado, según lo esperado.

_LYNX-430_

#### No es posible crear una dirección con atributos personalizados

Se ha corregido un problema con la mutación createCustomerAddress que impedía la creación de direcciones con atributos personalizados requeridos. La mutación ahora gestiona correctamente los atributos de dirección personalizados cuando se proporciona la carga útil adecuada.

_LYNX-441_

#### Error del servidor de GraphQL en el carro de compras con only_x_left_in_stock en el producto agrupado

Se ha corregido un problema en el cual al recuperar un carro de compras que contenía un producto agrupado con el campo only_x_left_in_stock en la consulta de GraphQL, se producía un error interno del servidor. GraphQL ahora devuelve correctamente un valor flotante o nulo para el campo only_x_left_in_stock sin errores.

_LYNX-447_

#### Error de GraphQL al eliminar otros productos con un producto configurable insuficiente en el carro de compras

Se ha corregido un problema por el cual al intentar eliminar productos en stock del carro de compras se producía un error de GraphQL &quot;La cantidad solicitada no está disponible&quot; si el carro de compras también contenía productos configurables con existencias insuficientes. La eliminación ahora funciona según lo esperado sin activar errores.

_LYNX-464_

#### No se pueden añadir productos porque el SKU de la mutación distingue entre mayúsculas y minúsculas

Se ha resuelto un problema en el que la mutación addProductsToCart devolvía un error &quot;PRODUCT_NOT_FOUND&quot; al utilizar SKU con mayúsculas y minúsculas diferentes. La mutación ahora gestiona los SKU sin distinción de mayúsculas y minúsculas, lo que garantiza la coherencia con las consultas del servicio de catálogo y el comportamiento de PDP.

_LYNX-469_

#### Atributo del producto > marca comercial abreviada &trade; se devuelve como &trade;

Se ha resuelto un problema de codificación de caracteres con el nombre del producto para la API de GraphQL

_LYNX-603_

#### problema de mutación de updateCustomerEmail

Se ha resuelto un problema con la mutación updateCustomerEmail en el que los clientes sin los atributos personalizados necesarios (añadidos después de la creación de la cuenta) no podían actualizar su correo electrónico.

_LYNX-619_

#### La mutación setShippingAddressesOnCart genera un error al usar pickup_location_code

Se ha corregido un problema en el cual la mutación setShippingAddressesOnCart devolvía un error al utilizar pickup_location_code sin especificar customer_address_id o address. La mutación ahora permite correctamente configurar una dirección de envío con solo el pickup_location_code.

_LYNX-626_

#### La lista CustomerOrder.items_eligibility_for_return debe ser coherente con los artículos del pedido

Incoherencias resueltas con la idoneidad para la devolución en pedidos:
1. La lista CustomerOrder.items_eligibility_for_return es ahora coherente con los artículos de pedido reales.
2. El campo OrderItemInterface.eligibility_for_return devuelve correctamente el valor &quot;false&quot; cuando ya se ha devuelto la cantidad completa.
3. CustomerOrder.items_eligibility_for_return ahora incluye solo los artículos que aún no se encuentran en proceso de devolución.

_LYNX-627_

#### Agregar campo quantity_return_requested

Se ha agregado el campo quantity_return_requested a OrderItemInterface, lo que permite identificar la cantidad de artículos para los que se ha enviado una devolución. Esto mejora el seguimiento de devoluciones junto con el campo quantity_returned existente.

_LYNX-628_

#### Las acciones disponibles en el pedido no deben contener DEVOLUCIÓN después de crear devoluciones para todos los artículos en cantidad completa

Se ha corregido un problema por el cual el campo available_actions de la consulta customer.orders de GraphQL incluía incorrectamente RETURN después de crear una devolución completa para todos los elementos. La acción RETURN ahora se elimina correctamente una vez completado el proceso de devolución.

_LYNX-634_

#### Compatibilidad de tienda: actualice la lógica para obtener el nombre de la tabla con el prefijo y otras mejoras menores

Se ha actualizado la lógica para recuperar el nombre de tabla con el prefijo (relacionado con los cambios de SCP).

_LYNX-637_

#### guardar en la libreta de direcciones no funciona al utilizar el campo same_as_shipping de setBillingAddressOnCart GQL

Se ha corregido un problema en el cual la dirección de envío no se guardaba en la libreta de direcciones del cliente al utilizar la mutación de GraphQL setBillingAddressOnCart con el campo same_as_shipping establecido en true. Ahora, la dirección de envío se almacena correctamente según lo esperado.

_LYNX-643_

#### Estandarizar order_id en mutaciones

Se ha estandarizado la entrada order_id en mutaciones y se ha actualizado la plantilla de correo electrónico de confirmación de cancelación de pedidos para exponer el ID de incremento en lugar del ID de pedido.

_LYNX-650_

#### CustomerOrder no muestra los comentarios del pedido

Se ha resuelto un problema con CustomerOrder para incluir comentarios de pedidos en las consultas de GraphQL de pedidos de clientes y de clientes.

_LYNX-651_

#### original_item_price no debe incluir ningún descuento

Se ha actualizado la lógica de original_item_price en GraphQL Cart Precios de artículos para excluir descuentos.

_LYNX-652_

#### Los productos agrupados siguen mostrando &quot;IN_STOCK&quot; cuando uno de sus productos agrupados está agotado

Se ha resuelto un problema en el cual product.stock_status para productos agrupados seguía mostrando &quot;IN_STOCK&quot; incluso cuando uno de los elementos agrupados estaba agotado.

_LYNX-681_

#### La consulta del cliente devuelve un error de servidor interno si existe un valor para el atributo personalizado eliminado para un cliente

Se ha corregido el problema en el cual la consulta del cliente devolvía un error interno del servidor cuando un atributo personalizado eliminado aún tenía un valor almacenado. Ahora, se devuelve un mensaje de error adecuado si se solicita un atributo no existente. La caché necesaria se invalida al eliminar el atributo personalizado del cliente.

_LYNX-686_

#### Parámetro de acción para los vínculos de confirmación de devolución y cancelación

Se ha añadido un parámetro de acción para los vínculos relacionados con la devolución y cancelación del correo electrónico de confirmación

_LYNX-687_

#### La URL de confirmación de usuario invitado se redirige a la página de estado del pedido, ya que falta orderRef (para GuestRMA)

Se ha añadido el parámetro orderRef al vínculo en el correo electrónico de confirmación de RMA de invitado

_LYNX-688_

#### La URL de confirmación de usuario invitado se redirige a la página de estado del pedido, ya que falta orderRef

Se ha añadido el parámetro orderRef al vínculo en el correo electrónico de confirmación de cancelación de pedidos de invitado

_LYNX-689_

#### Problemas con la consulta del cliente cuando RMA está desactivado

Se ha actualizado la lógica de GraphQL para garantizar que los retornos creados anteriormente siguen siendo accesibles incluso cuando RMA está desactivado globalmente. El mensaje de error se ha eliminado para mejorar la experiencia de usuario de la tienda, lo que garantiza que los clientes puedan seguir viendo sus devoluciones pasadas.

_LYNX-690_

#### GraphQL no devuelve datos actualizados del carro de compras cuando se aplican cupones en conflicto

Se ha corregido un problema que causaba que, al aplicar un cupón en conflicto con una prioridad mayor, se mostrara un mensaje de error sin devolver los datos actualizados del carro de compras. Ahora, cuando un nuevo cupón invalida el existente, la mutación devuelve correctamente el carro de compras con el cupón válido aplicado.

_LYNX-696_

#### No se puede devolver nulo para el campo que no admite valores NULL &quot;TaxItem.title&quot; en placeOrder GQL

Se ha corregido un problema en el cual la mutación placeOrder fallaba con un error interno del servidor debido a un valor nulo para el campo que no admite valores NULL TaxItem.title. Ahora, el campo siempre devuelve un valor válido, lo que garantiza una colocación correcta del pedido.

_LYNX-699_

#### EstimateTotals: los descuentos son nulos para tipos de productos virtuales

Se ha resuelto el problema con la mutación estimatedTotals, que devolvía nulo para los descuentos cuando se aplicaba un código de descuento a un carro de compras que contenía productos virtuales.

_LYNX-702_

#### El producto agrupado no devuelve el porcentaje y el importe de descuento correctos

Se han introducido nuevas propiedades &quot;catalog_discount&quot; y &quot;row_catalog_discount&quot; para que los precios de los artículos del catálogo muestren los importes y porcentajes de descuento correctos en los niveles de fila y artículo único.

_LYNX-703_

#### Configuración de mensaje de regalo en el nivel de producto

Se ha corregido un problema en el cual los mensajes de regalo no se aplicaban en el nivel de producto cuando se deshabilitaban globalmente. Ahora, si los mensajes de regalo están habilitados para un producto específico, se pueden agregar correctamente utilizando la mutación updateCartItems y se guardarán y reflejarán correctamente.

_LYNX-714_

#### Problema con la eliminación del envoltorio para regalos del artículo del carro de compras

Se ha corregido un problema que causaba que la eliminación del envoltorio para regalos de un elemento del carro de compras mediante la mutación updateCartItems no funcionara según lo esperado. Ahora, tanto aplicar como eliminar el envoltorio para regalos funcionan correctamente sin errores.

_LYNX-717_

#### La función de cliente registrado coincidente no funciona en Boilerplate, y la mutación trackViewedProduct debe habilitarse para los invitados.

Mutación trackViewedProduct expuesta para rastrear el evento de vistas de productos para clientes e invitados

_LYNX-751_

#### error de devolución de consulta cart.rules en lugar de matriz vacía en caso de que no se apliquen reglas de carro de compras activas

Se ha corregido la consulta cart.rules para devolver una matriz vacía en lugar de un error cuando no se aplican reglas de carro de compras activas.

_LYNX-757_

#### Problema al recuperar los envoltorios para regalos para artículos del carro

Se ha actualizado la lógica de recuperación para devolver las opciones de envoltorio para regalos para artículos del carro de compras cuando está globalmente deshabilitada pero habilitada en el nivel de producto

_LYNX-758_

#### Las llamadas de GraphQL con el método OPTIONS devuelven un código de respuesta 500 cuando se instala el paquete de compatibilidad con adobe-commerce/storefront

Se ha corregido un problema en el cual las llamadas de GraphQL que usaban el método OPTIONS devolvían un error de servidor interno 500 cuando se instalaba el paquete de compatibilidad de adobe-commerce/storefront. El extremo ahora devuelve correctamente una respuesta 200/204 según lo esperado.

_LYNX-778_

### Otras herramientas para desarrolladores

#### [Problema]: corrija el error de sintaxis de HTML en visual.phtml.

El sistema ahora cierra correctamente la etiqueta de inicio en el archivo visual.phtml, lo que garantiza una sintaxis de HTML adecuada. Anteriormente, la etiqueta de inicio no se cerraba correctamente, lo que provocaba un error de sintaxis de HTML.

_AC-10658 - [Problema de GitHub](https://github.com/magento/magento2/issues/38247) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37457)_

#### [Problema] cambió &quot;activo&quot; a &quot;habilitado&quot; en el comando bin/magento maintenance:status

El sistema ahora proporciona mensajes de estado más precisos para el comando del modo de mantenimiento, cambiando el estado de &quot;activo&quot; a &quot;habilitado&quot; y de &quot;no activo&quot; a &quot;deshabilitado&quot;. Anteriormente, el mensaje de estado del comando de modo de mantenimiento se mostraba como &quot;activo&quot; o &quot;no activo&quot;, lo que podía generar confusión.

_AC-11474 - [Problema de GitHub](https://github.com/magento/magento2/issues/38486) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38410)_

#### La navegación en el árbol de categorías provoca errores en Redis: &quot;La sesión de Redis ha superado las conexiones simultáneas&quot;

_AC-12571 - [Problema de GitHub](https://github.com/magento/magento2/issues/38851) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0611e750)_

#### Problemas de CSP combinados con dev/css/use_css_critical_path

El sistema ahora carga correctamente los archivos CSS de forma asíncrona en las páginas de cierre de compra, incluso cuando la configuración &quot;dev/css/use_css_critical_path&quot; está habilitada, lo que garantiza que estas páginas se representen con los estilos CSS adecuados. Anteriormente, una directiva de seguridad de contenido (CSP) restringida impedía la ejecución de JavaScript en línea, lo que provocaba que los archivos CSS no se cargaran según lo esperado.

_AC-12731 - [Problema de GitHub](https://github.com/magento/magento2/issues/39020) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39040)_

#### Si se usa el tipo virtual para configurar el complemento, el método interceptor no se puede generar correctamente en el comando `setup:di:compile`

El sistema ahora genera correctamente métodos interceptores cuando se utiliza un tipo virtual para configurar un complemento, lo que garantiza resultados coherentes, ya sean precompilados o compilados en tiempo de ejecución. Anteriormente, el sistema generaba resultados incorrectos cuando se precompilaba en comparación con la compilación en tiempo de ejecución.

_AC-13398 - [Problema de GitHub](https://github.com/magento/magento2/issues/33980) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38141)_

#### Las pruebas unitarias de Adobe Commerce 2.4.7-p3 dan error

No se requieren notas de la versión.

_ACP2E-3631 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/982b1c42)_

### Pago / Métodos de pago, Pedido

#### Los datos de la tarjeta de crédito guardada para su uso posterior no se muestran en la página del método de pago almacenado

Los datos de la tarjeta de crédito guardada para su uso posterior no se mostraban en la página del método de pago almacenado, que ahora es información de la tarjeta de crédito fija que se muestra en la página del método de pago almacenado.

_AC-13699 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/96dec499)_

### Pagos

#### El pago con tarjeta de crédito (enlace de flujo de pago) no funciona

Error de obtención anterior (el pago se rechazó) al realizar el pedido con la tarjeta de crédito después de que el pedido corregido se haya realizado correctamente.

_AC-13414 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a68324bc)_

#### El flujo de trabajo crea una nueva transacción cada vez que hacemos clic en el botón Recuperar en la pantalla Ver transacción

El sistema obtiene ahora correctamente la información de la transacción sin crear una nueva transacción de pago cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción. Anteriormente, hacer clic en el botón Recuperar creaba incorrectamente una nueva transacción de pago para un pedido que ya se había pagado.

_ACP2E-2841 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### El mensaje de Paylater no se muestra en PDP para la cuenta de comerciante de PayPal canadiense

El sistema ahora muestra correctamente el mensaje PayAfter para las cuentas de comerciante de PayPal canadiense en la página de detalles del producto (PDP) cuando se puede determinar el país del comprador a partir de la dirección de facturación o el envío de la cuenta. Anteriormente, no se mostraba el mensaje Paylater debido a la falta de un parámetro, lo que daba como resultado un error en la consola del explorador.

_ACP2E-3028 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6a185204)_

#### El reembolso del pedido de PayPal genera un abono duplicado

Se ha corregido el problema de concurrencia de los abonos creados por IPN para el servicio de pago de PayPal.

_ACP2E-3143 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### La regla de precio del carrito no funciona para Paypal

El importe correcto se muestra en el lado de PayPal cuando se aplica el descuento por forma de pago

_ACP2E-3163 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### [Nube] Los usuarios con un rol específico no pueden iniciar sesión

El usuario administrador con una función que solo contenga acceso a la sección de PayPal ahora puede iniciar sesión sin errores

_ACP2E-3208 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/66dea0de)_

### Rendimiento

#### Problema de configuración de atributos de producto predeterminados

El sistema ahora permite a los usuarios deseleccionar una opción predeterminada para un atributo de producto, lo que garantiza que el atributo no siempre tenga un conjunto predeterminado. Anteriormente, una vez que se establecía un valor predeterminado para un atributo de producto, no había forma de anular la selección, lo que provocaba que el atributo siempre tuviera un valor predeterminado establecido.

_AC-11932 - [Problema de GitHub](https://github.com/magento/magento2/issues/38703) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### [Problema] de limpieza de código y adición de nuevo bloque de encabezado crítico y movimiento de css crítico antes de los recursos

El sistema ahora incluye un nuevo bloque de encabezado crítico y mueve el CSS crítico antes que los recursos, lo que permite una mayor personalización y optimización del rendimiento en el front-end. Anteriormente, el CSS crítico no se colocaba antes de los recursos, lo que limitaba las oportunidades de personalización y optimización.

_AC-12000 - [Problema de GitHub](https://github.com/magento/magento2/issues/38748) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/35580)_

#### La compilación del tema se interrumpe cuando el host mysql contiene información del puerto

El sistema ahora gestiona correctamente la configuración del host MySQL que incluye información de puerto, lo que garantiza una compilación correcta del tema. Anteriormente, la compilación del tema fallaba si la configuración del host MySQL en la conexión de base de datos incluía información de puerto.

_AC-12176 - [Problema de GitHub](https://github.com/magento/magento2/issues/38799) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38842)_

#### Compatibilidad con CommandLoaderInterface de Symfony en Magento CLI

Este cambio reduce el tiempo de inicialización de la aplicación CLI de Magento al permitir la inicialización diferida de comandos hasta que se necesitan.

_AC-13471 - [Problema de GitHub](https://github.com/magento/magento2/issues/29266) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/29355)_

#### Problema de rendimiento al cargar atributos de producto en reglas de carro de compras

Se ha mejorado el rendimiento de las consultas para reglas de ventas: de unos 150 ms a ms de un solo dígito.

_ACP2E-2494 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### Rendimiento de indexación parcial de precios

El rendimiento de indexación parcial de precios se ha mejorado optimizando algunas de las consultas de eliminación utilizadas dentro del proceso de indexación.

_ACP2E-2673 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ba25af8a)_

#### El pedido se rechaza en la configuración de varias tiendas al utilizar el procesamiento asincrónico de pedidos + Términos y condiciones

Ahora se procesan los pedidos realizados desde sitios web no predeterminados con los términos y condiciones habilitados.
Antes de que se rechazaran automáticamente.

_ACP2E-2850 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### La llamada a la API de REST de pedidos está tardando mucho tiempo en ejecutarse

El sistema ahora ejecuta la llamada a la API Order Rest en un periodo de tiempo razonable, lo que mejora el rendimiento al recuperar un gran número de pedidos. Anteriormente, la llamada a la API de Order Rest tardaba mucho tiempo en ejecutarse, lo que provocaba retrasos al recuperar un gran número de pedidos.

_ACP2E-2910 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/001e5188)_

### Rendimiento, promoción

#### El indexador de reglas de ventas dejó de ejecutarse

El sistema ahora completa correctamente el indexador de reglas de ventas incluso con un gran número de grupos de filtros combinados, lo que garantiza que las condiciones de las reglas del carro de compras se apliquen al carro de compras según lo esperado. Anteriormente, el indizador de reglas de ventas no se completaba cuando había un gran número de grupos de filtros combinados, lo que producía un mensaje de error e impedía la aplicación de condiciones de reglas de carro de compras.

_ACP2E-2617_

### Precio

#### Magento2.4.6-p4 Pedido API Simple Artículo precio perdido

El sistema ahora muestra correctamente el precio de los productos simples cuando se consultan a través de la API de pedidos, lo que garantiza una representación de datos precisa. Anteriormente, el precio de los productos simples se mostraba incorrectamente como cero en la respuesta de la API.

_AC-11810: [problema de GitHub](https://github.com/magento/magento2/issues/38603)_

#### Error de redondeo de céntimos en la regla de catálogo

_AC-13855 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/276e0acd)_

### Product

#### Los caracteres especiales del nombre de producto asociado configurable se están convirtiendo en entidades de HTML.

El sistema ahora conserva correctamente caracteres especiales en los nombres de los productos asociados al editar un producto configurable, lo que impide que se conviertan en entidades de HTML. Anteriormente, los caracteres especiales de los nombres de producto asociados se convertían en entidades de HTML cuando se editaba el producto configurable.

_AC-10535 - [Problema de GitHub](https://github.com/magento/magento2/issues/38146) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38447)_

#### La función GetById del ProductRepository no crea la clave de caché correcta

El sistema ahora crea correctamente una clave de caché en la función GetById del ProductRepository, independientemente de si el ID de almacén se pasa como una cadena o como un entero. Esto garantiza que el producto se recupere de la memoria en llamadas posteriores, lo que mejora el rendimiento. Anteriormente, el sistema recuperaba el producto de la base de datos cada vez que se llamaba a la función, incluso con los mismos parámetros, debido a la creación incorrecta de la clave de caché.

_AC-10947 - [Problema de GitHub](https://github.com/magento/magento2/issues/38384) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38433)_

#### [Problema] [MFTF] agregó AdminClickAddOptionForBundleItemsActionGroup

El sistema ahora incluye AdminClickAddOptionForBundleItemsActionGroup, lo que mejora la funcionalidad del panel de administración. Anteriormente, este grupo de acción no estaba disponible.

_AC-11992 - [Problema de GitHub](https://github.com/magento/magento2/issues/30857) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30838)_

#### [Problema] Corregir error tipográfico en el bloque PHPDoc

El sistema ahora elimina correctamente una variable de referencia desconocida en PHPDoc para la declaración de la variable $helper, lo que mejora la claridad y precisión del código. Anteriormente, esta variable de referencia desconocida en PHPDoc causaba confusión y posibles imprecisiones en el código.

_AC-13173 - [Problema de GitHub](https://github.com/magento/magento2/issues/38961) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38940)_

#### [Problema] Se ha corregido el diseño de páginas de productos descargables y paquetes rotos en Magento >= 2.4.7

Se ha corregido el diseño de las páginas de productos agrupadas y descargables, lo que garantiza una visualización coherente y correcta en todos los dispositivos. Anteriormente, estas páginas experimentaban problemas de diseño debido a una reorganización del bloque multimedia de información del producto.

_AC-13423 - [Problema de GitHub](https://github.com/magento/magento2/issues/39403) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/6cfb9b6b)_

#### AlertProcessor - El argumento #2 ($storeId) debe ser del tipo int, se ha proporcionado una cadena

El sistema ahora almacena correctamente en déclencheur los correos electrónicos de alerta de producto asegurándose de que el identificador de tienda sea del tipo de datos correcto. Anteriormente, los correos electrónicos de alerta de producto no se enviaban debido a una discrepancia de tipos en el identificador de tienda.

_AC-5969 - [Problema de GitHub](https://github.com/magento/magento2/issues/35602) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0574ac23)_

#### La función [Cloud] addFilterToMap no funciona para ciertas columnas

Ahora, el módulo personalizado se puede utilizar en la cuadrícula de pedidos. Anteriormente, se producían errores al utilizar un módulo personalizado.

_ACP2E-2944 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3a7c4d17)_

#### [Nube] productos en la categoría - Agregar productos - Asignar - Seleccionar todo

Los usuarios ahora pueden seleccionar o deseleccionar productos mediante la opción.

_ACP2E-3471_

### Promoción

#### El atributo del cliente no está visible al crear la cuenta a partir de la invitación

Los atributos del cliente están disponibles al crear una cuenta a partir de una invitación.

_ACP2E-2602 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/39d54c2d)_

#### El código de cupón con el límite de usuarios por cupón no se libera para el pago si se produce un error al cancelar el pedido

El sistema ahora actualiza inmediatamente los usos de cupones cuando se crea o cancela un pedido, y añade usos de reglas a una cola para evitar posibles interbloqueos. Esto garantiza que se libere un código de cupón con un límite de &quot;Usos por cupón&quot; y que pueda reutilizarse si se cancela un pedido debido a un pago fallido. Anteriormente, el sistema no liberaba el código de cupón para reutilizarlo en estos casos, lo que daba como resultado un mensaje de error que indicaba que el código de cupón no era válido.

_ACP2E-2627 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c971859e)_

#### El indizador de productos de reglas de catálogo de reindexación [Cloud] lanza SQLSTATE[HY000]: Error general: El servidor MySQL de 2006 ha desaparecido.

El sistema ahora gestiona correctamente el valor &quot;batchCount&quot; personalizado en el archivo di.xml para &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, lo que evita errores de SQL como &quot;Error general: 2006 MySQL server has gone away&quot; durante la reindexación del indexador de productos de reglas de catálogo debido al tamaño incorrecto del lote en catálogos grandes

_ACP2E-2811 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### [NUBE]Regla de precio del carro de compras para visitantes. El segmento de cliente no aplica descuento en el carro de compras

El sistema ahora aplica correctamente las reglas de precios del carro de compras para los segmentos de clientes visitantes, incluso si la regla no utiliza un cupón, lo que garantiza que se apliquen los descuentos adecuados al carro de compras. Anteriormente, los descuentos no se aplicaban al carro de compras para segmentos de clientes de visitantes a menos que la regla de precio del carro de compras usara un cupón.

_ACP2E-2926_

#### Falta el atributo &quot;Type&quot; en la pestaña &quot;Products to Match&quot; de las reglas de producto relacionadas

El atributo &quot;Type&quot; está ahora disponible como opción de filtro en la pestaña &quot;Products to Match&quot; del módulo &quot;Related Product Rules&quot;, lo que permite una definición de regla más precisa. Anteriormente, este atributo no aparecía en la pestaña &quot;Productos para combinar&quot;, lo que limitaba la capacidad de crear criterios de coincidencia precisos.

_ACP2E-3024_

#### La regla de ventas con el atributo Paso de cantidad de descuento (Comprar X) provoca que no se apliquen otras reglas

La regla de precio del carro de compras no cancela las reglas aplicadas anteriormente si la cantidad del producto en el carro de compras no es suficiente para que se aplique la regla.

_ACP2E-3139 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d01ee51e)_

#### Problema de rendimiento en la regla de precios del carro de compras: módulo Regla de ventas avanzada

Se agregaron índices de BD faltantes para los filtros AdvancedSalesRule

_ACP2E-3331_

#### Emitir reglas de ventas con descuento de importe fijo y &quot;Descuento de cantidad máxima aplicado a&quot;

Se ha corregido un problema con el descuento de reglas del carro de compras cuando el descuento de cantidad fija está configurado para aplicarse a una cantidad limitada de productos y es el carro de compras. Anteriormente, el valor &quot;Descuento de cantidad máxima aplicado a&quot; se utilizaba para calcular el precio del artículo actual en el carro de compras, no solo para calcular el descuento de la regla.

_ACP2E-3332 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### La actualización a [CLOUD] Magento hizo que los cupones hicieran distinción entre mayúsculas y minúsculas

Antes de la corrección, tenía que escribir el código de cupón exactamente como estaba configurado, teniendo en cuenta las mayúsculas y minúsculas. Ahora, el cupón se validará en el back-end independientemente de la configuración del código en mayúsculas o minúsculas.

_ACP2E-3342_

#### Reglas de carro de compras &quot;Descuento de cantidad fija para todo el carro de compras&quot;  La acción aplica descuentos incorrectamente

Los códigos de cupones se validarán correctamente, independientemente de las mayúsculas o minúsculas, cuando se utilicen para la creación de pedidos desde el área de administración. Antes, el código de cupón no se validaba si no coincidía con el caso de letra exacto del código de regla del carro de compras configurado.

_ACP2E-3349 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/581b7ef1)_

#### En el servidor, almacene valores predeterminados para los atributos del producto (en lugar de los valores de administración esperados)

Ahora, en el back-end de, se utilizan valores de administración en lugar de valores de almacén predeterminados para los atributos de producto.

_ACP2E-3374 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/5184c067)_

#### La acción &quot;Descuento de cantidad fija para todo el carro de compras&quot; de las reglas del carro de compras aplica descuentos incorrectamente al agregar productos agrupados

Las reglas del carro de compras de cantidad fija no se aplicaban correctamente a los productos agrupados. Ahora, al calcular la cantidad de descuento total, se tienen en cuenta los productos secundarios del paquete, lo que resulta en un cálculo de descuento adecuado.

_ACP2E-3377 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### Reglas de precio de carro calculando mal descuento

Los descuentos de cantidad fija ahora se calculan correctamente. Antes de la corrección, los descuentos de cantidad fija no se sumaban correctamente para los productos agrupados.

_ACP2E-3403 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/0b488dd1)_

#### No se muestran las categorías anidadas en las condiciones de regla

Se ha corregido un problema que se producía cuando las categorías anidadas en la categoría de nivel 3 no se mostraban en las reglas de marketing de la condición de categoría

_ACP2E-3406 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### usage_limit y uses_per_customer no se actualizan en la tabla salesrule_coupon

La actualización de los usos por cupón y los usos por cliente en la regla de precios del carro de compras ahora afectará los cupones autogenerados existentes. Anteriormente, los nuevos valores solo afectaban a los nuevos cupones

_ACP2E-3432 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/88660e79)_

#### La regla de precio del carro de compras no considera la categoría principal cuando utiliza la condición &quot;es igual o mayor que&quot;.

Las reglas de precios del carro de compras ahora consideran correctamente la categoría principal cuando se utiliza en condiciones avanzadas

_ACP2E-3456 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/93359343)_

#### Cálculo de descuento no válido con prioridad

En el caso de un importe fijo aplicado para todo el tipo de descuento del carro de compras, el importe no se calculaba correctamente para los artículos del carro de compras que ya se habían descontado en una promoción anterior. Ahora, los descuentos están correctamente resumidos.

_ACP2E-3463 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

#### [NUBE] El cálculo del envío no tiene en cuenta la regla del carro de compras

Antes de la corrección, una regla de carro de compras con la condición de región no se aplicaba de forma coherente. Después de la corrección, las reglas de carro de compras con condiciones de región se aplican correctamente.

_ACP2E-3472 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### La condición de SKU de regla de carro de compras falla en la factura.

El descuento en el paquete de productos con precio dinámico ahora se refleja correctamente en la factura. Anteriormente, el descuento no se reflejaba en la factura.

_ACP2E-3491 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3f12d152)_

#### Valor de descuento incorrecto cuando se aplican varias reglas de precio del carro de compras simultáneamente con productos con precio especial o descuento

Antes de la corrección, la cantidad fija para reglas de carro de compras completas no se aplicaba correctamente si se aplicaba más de una. Ahora, las reglas del carro de descuentos de cantidad fija se aplican correctamente.

_ACP2E-3498 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1984c61c)_

### Devuelve

#### [NUBE] Los usuarios administradores restringidos pueden ver el menú y los botones de retorno

Los usuarios administradores restringidos ahora no tienen acceso a los controles relacionados con RMA (menú y botones).
Los usuarios administradores anteriormente restringidos podían ver el menú y los botones de retorno.

_ACP2E-3330_

#### La pantalla de retorno está dañada al actualizar la pantalla

El usuario puede actualizar la página sin experimentar distorsión de la pantalla.

_ACP2E-3443_

### SEO

#### Añadir reescrituras de URL con acento provoca una carga infinita

El sistema ahora crea y funciona correctamente las reescrituras de URL con acentos, lo que evita la carga infinita durante el proceso de guardado. Anteriormente, al añadir una reescritura de URL con un acento, se producía un problema de carga infinita.

_AC-11907 - [Problema de GitHub](https://github.com/magento/magento2/issues/38692) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/44cef3a9)_

#### Reescritura de URL de categoría incorrecta de varias tiendas para la categoría de tercer nivel

Genere las reescrituras de URL correctas para los elementos secundarios con clave de URL principal con ámbito personalizado

_ACP2E-2641 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### Los caracteres de doble byte (caracteres especiales) del campo Nombre del producto bloquean la creación del producto en el backend

Se ha añadido una nueva configuración que le permite aplicar transliteraciones a la URL del producto o no. La configuración está disponible aquí: Tiendas > Configuración > Catálogo > Catálogo > Optimización del motor de búsqueda: &quot;Aplicar transliteración para la URL del producto&quot;

_ACP2E-2770 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Creación de entradas url_rewrite incorrecta con varios almacenes en un grupo de tiendas

Antes de la corrección, solo podía generar reescrituras de URL en un nivel de sitio web al editar un producto. Con la corrección, se introdujo una nueva configuración (Tiendas > Configuración > Catálogo > Optimización del motor de búsqueda, &quot;Ámbito de reescritura de URL del producto&quot; con opciones &quot;Vista de tienda&quot;, &quot;Sitio web&quot;) que le permite generar reescrituras de URL en el nivel de vista de tienda o sitio web.

_ACP2E-3383 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2d627301)_

### Ventas

#### La regla de precio del segundo carro de compras no se aplica si ya se ha aplicado la regla del primer carro de compras

_AC-13751_

### Buscar

#### Obteniendo &quot;Introduzca un término de búsqueda e inténtelo de nuevo&quot;. error en la página de búsqueda avanzada de la tienda en 2.4.8-beta1

El sistema ahora muestra correctamente los resultados de búsqueda en la página Búsqueda avanzada cuando un atributo de producto está definido como &quot;No&quot;. Anteriormente, si establecía un atributo de producto en &quot;No&quot; y realizaba una búsqueda, se mostraba un mensaje de error: &quot;Introduzca un término de búsqueda e inténtelo de nuevo&quot;.

_AC-13053 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/3ea26621)_

#### magento/module-open-search depende de una rama opensearch-php inexistente

_AC-13721 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/05dc0bbf)_

#### tabla search_query cuando es de gran tamaño, tiene un gran impacto en el tiempo de carga de front-end

Se ha mejorado el tiempo de carga de página del listado de búsqueda. Antes de la corrección, la página de la lista de búsqueda se retrasaba debido a una consulta no optimizada.

_ACP2E-3362 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Seguridad

#### [Problema] Falta fuente en el elemento emergente Paylater de CSP

El sistema ahora permite la carga de la fuente &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sin violar la directiva de Política de seguridad de contenido, lo que garantiza la correcta visualización de la ventana emergente de Paylater. Anteriormente, la fuente se rechazaba cargar debido a una infracción de la directiva de la política de seguridad de contenido, lo que causaba problemas de visualización con la ventana emergente de Paylater.

_AC-11855 - [Problema de GitHub](https://github.com/magento/magento2/issues/38624) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/37401)_

#### [Problema]: actualice el texto del DOM js.js reinterpretado como HTML.

Al utilizar innerText, se evitará el riesgo de la inyección de HTML, ya que estas propiedades escapan automáticamente a cualquier carácter especial de HTML en el texto proporcionado. Esta corrección ayuda a evitar vulnerabilidades de scripts entre sitios (XSS) al tratar la entrada como texto sin formato en lugar de HTML interpretado.

_AC-12035: [problema de GitHub](https://github.com/magento/magento2/issues/38767)_

#### ReCaptcha V2 se muestra incorrectamente al cerrar la compra para el idioma alemán

Anteriormente, la dirección de correo electrónico de recaptcha de debajo del cierre de compra no tenía estilo para los idiomas con palabras largas, como el alemán. Después de esto, el recaptcha tiene el mismo aspecto que todos los elementos recaptcha del resto de las áreas.

_ACP2E-3273 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7377de59)_

#### El captcha al iniciar sesión como administrador no requiere interacción para algunos usuarios

ReCaptcha para el inicio de sesión del administrador se valida según lo esperado

_ACP2E-3300 - [Contribución de código de GitHub](https://github.com/magento/security-package/commit/8f64ab3c)_

### Envío

#### [Problema] Se corrigió un error tipográfico en tracking.phtml - se cambió el nombre de las funciones JS &quot;currier&quot; a &quot;carrier&quot;

El sistema ahora utiliza correctamente el término &quot;carrier&quot; en lugar del mal escrito &quot;currier&quot; en las funciones de controlador de JavaScript utilizadas en la plantilla de seguimiento de pedidos, lo que garantiza una nomenclatura de funciones y una claridad de código adecuadas. Anteriormente, se utilizaba el término mal escrito &quot;currier&quot;, lo que producía una posible confusión e incoherencia en la base del código.

_AC-10757 - [Problema de GitHub](https://github.com/magento/magento2/issues/34523) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/33414)_

#### UPS REST &quot;Un envío no puede tener un KGS/IN o LBS/CM u OZS/CM como unidad de medida&quot;

Asegúrese de que las tarifas de UPS sean visibles en el pago y en el carro de compras.

_AC-11938 - [Problema de GitHub](https://github.com/magento/magento2/issues/38618) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/493e01f5)_

#### Actualizaciones de las instrucciones de configuración de &quot;sandbox&quot; y &quot;prod&quot; de UPS REST en devdoc

_AC-12938_

#### [Problema] Corrección ortográfica de las variables de la dirección del cliente

El sistema ahora escribe correctamente las variables para las direcciones de los clientes, lo que garantiza una visualización precisa en el área de cuenta del front-end. Anteriormente, la ortografía incorrecta de estas variables podía provocar errores durante las revisiones de código local.

_AC-13172 - [Problema de GitHub](https://github.com/magento/magento2/issues/32817) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32815)_

#### Ventana de seguimiento que muestra una fecha de envío esperada incorrecta

Mostrar la fecha de entrega correcta para el operador de Fedex.

_ACP2E-2738 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### Las Tarifas De Tabla Siguen Mostrándose Aunque Se Aplique El Envío Gratuito

Tabla El método de envío de tarifa ahora se muestra incluso si el envío gratuito está disponible después de aplicar el cupón

_ACP2E-2763 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/b2286ecf)_

#### Error en la prueba MFTF AdminCreatingShippingLabelTest debido a credenciales no añadidas en el entorno Jenkins

corrección de la prueba mftf

_ACP2E-2765 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ea79f7dd)_

#### La API de seguimiento de FedEx no funciona con las credenciales de REST

Anteriormente, la integración con FedEx no requería claves de API adicionales para la API de seguimiento. Ahora se ha añadido una nueva configuración para admitir el seguimiento de claves de API.

_ACP2E-3340 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

#### [Las tarifas negociadas por FedEx de la nube] no se devuelven en REST

Antes de la corrección, las tasas específicas de la cuenta de FedEx no se enviaban en la respuesta, incluso a través de la documentación de FedEx que deberían haberse enviado. Después de la corrección, las tasas específicas de la cuenta se envían en la respuesta cambiando la solicitud por nuestra parte.

_ACP2E-3354 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/55615e61)_

### Ensayo y previsualización

#### La configuración de la actualización programada no se guarda si se agregó originalmente ejecutando la actualización

El sistema ahora borra correctamente los valores de atributos de producto en las actualizaciones programadas posteriores cuando dichos atributos se modifican en la actualización que se está ejecutando. Anteriormente, cuando una actualización programada en ejecución modificaba un atributo de producto, era imposible borrar dichos valores de atributos al crear una nueva actualización programada, lo que requería que el usuario los reeditara después de la creación.

_ACP2E-2901_

#### Regla de precio de carro de compras desde la fecha y hasta la fecha Problema no sincronizado con actualización de ensayo

Las fechas se guardan según las actualizaciones para Ensayo de Regla de Precio de Carro.

_ACP2E-2999_

#### Error de JS en vista previa de ensayo

Ahora el archivo form-mini-stub.js se está cargando correctamente sin ningún error de sintaxis Js en las herramientas para desarrolladores.

_ACP2E-3104_

#### No se puede actualizar el contenido clasificado con precio especial del producto

El sistema ahora permite editar la fecha final de una campaña de actualización de precios una vez iniciada, lo que garantiza que los usuarios puedan realizar los ajustes necesarios en sus campañas. Anteriormente, se producía un error al intentar actualizar la fecha de finalización de una campaña activa, lo que impedía a los usuarios realizar cambios.

_ACP2E-3162_

#### No se puede actualizar la actualización programada al usar un atributo de categoría personalizado único

Se ha corregido un problema que impedía actualizar una actualización programada para una categoría si esta tenía un atributo único

_ACP2E-3453 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Direccionamiento

#### [Problema] Permite el uso de rangos CIDR en la lista de permitidos de mantenimiento

El sistema ahora admite el uso de rangos CIDR en la lista de IP permitidas del modo de mantenimiento, lo que permite que un rango de direcciones IP omita el modo de mantenimiento. Anteriormente, el modo de mantenimiento permitía que la lista de direcciones IP solo permitiera a direcciones IP individuales omitir el modo de mantenimiento.

_AC-9432 - [Problema de GitHub](https://github.com/magento/magento2/issues/37943) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/30699)_

### Impuestos

#### [Problema] Feature/php8.1 constructor property promotion wee graph ql

Reemplace casi todas las propiedades con la promoción de propiedades de constructor en el gráfico web del módulo ql:

_AC-13295 - [Problema de GitHub](https://github.com/magento/magento2/issues/39309) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36975)_

#### El impuesto sobre productos fijos (FPT) no funciona con productos configurables

FPT para las variaciones de productos configurables que funcionan correctamente.

_ACP2E-3193 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ec7e32a9)_

### Marco de prueba

#### Prueba de integración que falla testDbSchemaUpToDate debido al tipo de columna JSON

El sistema ahora reconoce correctamente los tipos de columnas JSON en el esquema de la base de datos durante las pruebas de integración, lo que evita errores de prueba debido a una discrepancia entre el esquema de la base de datos y el esquema declarativo. Anteriormente, el sistema identificaba incorrectamente los tipos de columnas JSON como LONGTEXT en MariaDB, lo que provocaba que las pruebas de integración fallaran.

_AC-11654 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/ef81f5a2)_

#### [Problema] ortografía de corrección de PHPDoc

El sistema ahora reconoce correctamente los métodos obsoletos en los IDE debido a una corrección ortográfica en el PHPDoc. Anteriormente, un error ortográfico en el PHPDoc provocaba que los IDE no reconocieran determinados métodos como obsoletos.

_AC-13362 - [Problema de GitHub](https://github.com/magento/magento2/issues/31399) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/31398)_

#### MAGETWO-95118: Comprobación del comportamiento con el carro de compras persistente después de que caduque la sesión

_AC-13478 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7d5e3906)_

#### Las pruebas de integración dan error Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission

_AC-13716_

#### [Comparación de base de datos] Error irrecuperable si la base de datos contiene registros sobre la regla de destino sin condiciones

Anteriormente, si la base de datos contenía un registro sobre la regla de destino sin ninguna condición, se obtenían errores irrecuperables, pero después de que la herramienta de comparación de bases de datos de corrección pasara correctamente sin errores irrecuperables.

_AC-13722_

#### Corregir pruebas estáticas para habilitar el uso por extensiones de terceros

_AC-13848 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9e383b4d)_

#### [Error interno] en la aplicación de correcciones no se muestra durante la ejecución ni en los registros

&#39;-

_ACP2E-3334 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/d4de4726)_

#### [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest

Mftfs fijos

_ACP2E-3458 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/078c387e)_

### Marco de IU

#### Corrección de vulnerabilidad de seguridad Prototype.js en CVE-2020-27511

El sistema se ha actualizado para hacer frente a la vulnerabilidad de seguridad CVE-2020-27511 en Prototype.js 1.7.3, lo que mejora la seguridad general del sistema. Antes de esta actualización, el sistema era susceptible a una Denegación de servicio de expresión regular (ReDOS) mediante la eliminación de etiquetas HTML creadas.

_AC-12128 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/de4dfb8e)_

#### Grunt Less utiliza pub/ prefix para los mapas de origen

El sistema ahora genera mapas de origen de less/css sin el prefijo /pub para las rutas al utilizar grunt, lo que elimina la necesidad de una solución alternativa en la configuración del servidor web. Anteriormente, el uso del prefijo /pub en las rutas de mapas de origen requería una configuración específica en el servidor web para funcionar correctamente.

_AC-12189 - [Problema de GitHub](https://github.com/magento/magento2/issues/38837) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38840)_

#### Campo De Archivo De Componente De Iu

El sistema ahora valida correctamente el campo de archivo en un formulario de componente de la interfaz de usuario, lo que permite enviar el formulario sin errores cuando se selecciona un archivo. Anteriormente, la validación fallaba incluso cuando se seleccionaba un archivo, lo que impedía el envío del formulario.

_AC-12432 - [Problema de GitHub](https://github.com/magento/magento2/issues/38908) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/39004)_

#### [Problema] Se mejoró el formato de fecha en la consola js: cambie de 12 horas a 24 horas para...

Se ha mejorado el formato de fecha en la consola js: cambiar de 12 horas a 24 horas

_AC-12645 - [Problema de GitHub](https://github.com/magento/magento2/issues/38983) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38972)_

#### [Problema] al agregar la generación de sourceMap para menos archivos en modo de desarrollador

El sistema ahora genera mapas de origen para menos archivos cuando se encuentra en modo de desarrollador, lo que facilita la identificación del origen de un estilo. Anteriormente, la identificación del origen de un estilo era difícil al ejecutar el sistema en modo de desarrollador con menos compilación en el lado del servidor.

_AC-12650 - [Problema de GitHub](https://github.com/magento/magento2/issues/38982) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38977)_

#### Se está implementando el contenido estático para los módulos desactivados

El sistema ahora excluye CSS relacionado con módulos desactivados de los archivos de salida CSS finales, lo que garantiza que no se carguen estilos innecesarios. Anteriormente, el CSS relacionado con los módulos desactivados se incluía en los archivos de salida CSS finales, lo que provocaba la carga de estilos adicionales e innecesarios.

_AC-1306 - [Problema de GitHub](https://github.com/magento/magento2/issues/24666) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/32922)_

#### Comportamiento incoherente en la clasificación &quot;Sin existencias&quot; con el umbral mínimo de existencias

El sistema ahora ordena correctamente los productos del catálogo en función de los niveles de stock, cumpliendo el umbral mínimo de stock establecido y moviendo los artículos sin existencias al final de la lista de forma coherente. Anteriormente, el comportamiento de ordenación era incoherente, ya que los elementos no siempre aparecían en el orden correcto según sus niveles de stock, y los cambios en la ordenación podían producirse de forma impredecible después de guardar, actualizar o modificar la jerarquía de categorías.

_AC-13459 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/47b448e2)_

#### Sugerencia para mejorar los informes de errores con problemas de carga de require.js

Esta PR mejora el mensaje de error cuando requireJs no puede cargar un componente.

_AC-13472 - [Problema de GitHub](https://github.com/magento/magento2/issues/36761) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/38971)_

#### Errores de obsolescencia de PHP 8.4 que causan errores de compilación en 2.4-development

_AC-14004 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1da9ba6f)_

#### [Problema] No cargar contexto de bloque de servidor en front-end

El sistema ahora garantiza que el contexto del bloque back-end no se cargue en el front-end, lo que evita la creación de sesiones back-end innecesarias y posibles bloqueos de sesión. Anteriormente, el sistema cargaba incorrectamente el contexto de bloque back-end en el front-end, lo que provocaba la creación de sesiones back-end y posibles bloqueos de sesión.

_AC-9007 - [Problema de GitHub](https://github.com/magento/magento2/issues/37617) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/36368)_

#### [Problema] Eliminar resumen de revisión de scripts innecesarios

El sistema ahora optimiza el tiempo de carga de la página al eliminar los scripts de JavaScript innecesarios de la sección de clasificación, en lugar de utilizar estilos CSS en línea para un código más eficiente y legible. Anteriormente, el uso de scripts de JavaScript para la sección de clasificación podía ralentizar el tiempo de carga de la página.

_AC-9168 - [Problema de GitHub](https://github.com/magento/magento2/issues/37776) - [Contribución de código de GitHub](https://github.com/magento/magento2/pull/34643)_

#### Excepción al comprobar el saldo de una tarjeta regalo cuando Recaptcha está habilitado

Los usuarios podrán recuperar el saldo de la tarjeta regalo en la pantalla de vista y edición del carro de compras. Anteriormente, estos detalles no se mostraban cuando reCAPTCHA estaba habilitado.

_ACP2E-2529 - [Contribución de código de GitHub](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_

#### [ACLARACIÓN] Cumplimiento de ADA de solicitud de característica

El sistema ahora garantiza el cumplimiento de ADA eliminando las propiedades CSS no admitidas y reemplazándolas por otras admitidas en el archivo print.css. Anteriormente, el uso de propiedades CSS no admitidas producía problemas de compatibilidad con el explorador.

_ACP2E-2729 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/57a32313)_

#### [Código de biblioteca de confusión de Cloud] en effect-drop.js de AC 2.4.4-p8

El sistema ahora implementa correctamente la biblioteca effect-drop.js, lo que garantiza el funcionamiento adecuado de los efectos de la interfaz de usuario de jQuery. Anteriormente, la biblioteca effect-drop.js se sobrescribía por error con la biblioteca effect-clip.js, lo que causaba posibles problemas con los efectos de la interfaz de usuario de jQuery.

_ACP2E-3061 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/35b1b1da)_

#### Encabezado del sitio | Caracteres especiales que rompen la sección de Bienvenida al cliente

Después de la corrección, los caracteres especiales se muestran correctamente en la sección de bienvenida del cliente.

_ACP2E-3367 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/1366ae5e)_

#### La edición del segmento del cliente falla con daterange

Es posible guardar el segmento del cliente con la condición de intervalo de fechas, cuando solo se editó una de las fechas.

_ACP2E-3561 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/a52ff98f)_
