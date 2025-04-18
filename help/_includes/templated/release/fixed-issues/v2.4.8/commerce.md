---
source-git-commit: ae8701cf2486ef0a79c96bd264e16b0e7803a8f6
workflow-type: tm+mt
source-wordcount: '28386'
ht-degree: 0%

---
# Problemas corregidos de Adobe Commerce (v2.4.8)

## Se han corregido problemas en la versión 2.4.8

Hemos corregido 582 problemas en el código principal de Adobe Commerce 2.4.8. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

* _AC-10042_: la API de REST /V1/transactions devuelve un error cuando parent_txn_id = txn_id
   * _Nota de corrección_: El sistema ahora administra correctamente las transacciones de concepto principal y secundario donde el ID de transacción principal es el mismo que el ID de transacción, lo que evita un bucle infinito al consultar el extremo de la API REST /V1/transactions. Anteriormente, este escenario resultaba en un error grave debido a que se superaba el tiempo máximo de ejecución.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] Problema de tipo en 2.4.7
   * _Nota de corrección_: el sistema ahora administra correctamente los valores enteros en la función GetCustomSelectedOptionAttributes al ejecutar una consulta GraphQL, lo que evita cualquier error relacionado con el tipo. Anteriormente, al iniciar una consulta GraphQL que usaba GetCustomSelectedOptionAttributes con un argumento entero se producía un error de tipo.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38662>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: caracteres especiales en la categoría url_key (cuando se crea mediante la API de REST)
   * _Nota de corrección_: anteriormente, en category_url_key, el carácter especial no aparece después de la corrección, sino que muestra el carácter especial en category_url_key
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35577>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2703_: API REST que muestra pedidos de otro sitio web. 
   * _Nota de corrección_: el sistema ahora admite el acceso autorizado de ámbito para tokens de administrador de API de REST y extremos de Magento_Sales, lo que garantiza que la API de REST solo muestre los pedidos a los que el administrador tiene acceso. Anteriormente, la API de REST mostraba pedidos de todos los sitios web, independientemente del sitio web asignado al usuario administrador.
* _ACP2E-2755_: Problema con la API de REST después de habilitar el dúo 2FA
   * _Nota de corrección_: 2FA con opción de seguridad Duo ahora genera la firma correcta para la API de REST
   * _Contribución de código de GitHub_: <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_: [API REST]: Usar valor predeterminado en la vista de la tienda no permanece marcado después de agregar configuraciones para un producto configurable
   * _Nota de corrección_: el problema se ha corregido asegurando entradas de base de datos correctas para las opciones personalizables de un almacén no predeterminado. La casilla de verificación de la tienda personalizada en la sección &quot;admin > Catálogo > Edición de productos > Opciones personalizables&quot; se desmarcó anteriormente debido a entradas de base de datos inexactas, incluso si el título de la opción de la tienda personalizada seguía siendo el mismo que el almacén predeterminado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: la API de REST no puede realizar solicitudes con barra diagonal (/) en el SKU al usar Oauth1
   * _Nota de corrección_: antes de la corrección, no podía realizar una llamada de API correcta para un producto que tuviera &quot;/&quot; en su SKU. Ahora, puede realizar una solicitud de obtención de API correcta para obtener detalles del producto aunque su SKU tenga una barra diagonal.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: Error en la actualización de la dirección del cliente al actualizar mediante la API de REST si &quot;validateDefaultAddress&quot; está habilitado
   * _Nota de corrección_: El extremo de API ahora funciona como estaba previsto después de que se haya resuelto el problema con la clave de ID que falta en la carga útil de API.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Nube] al crear el grupo de clientes de precios de grupo de sitios web duplicado en la API de precios de nivel.
   * _Nota de corrección_: Ahora la Api REST de nivel de precio no permite crear el grupo de clientes de precios de grupo de sitios web Duplicado.
Anteriormente, era posible crear el grupo de clientes de precios de grupo de sitios web Duplicados en la Api de precios de nivel que no pasaba la validación en Administración durante el guardado del producto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: No se puede agregar el comentario de pedido con el estado mediante la API de REST
   * _Nota de corrección_: el problema se ha resuelto permitiendo el cambio en el estado del pedido si es solo del estado actual. Anteriormente, no respetaba el estado de la solicitud e impedía realizar cambios en cualquier estado de la solicitud, aunque fuera del mismo estado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_: La operación asincrónica falla cuando falta el SKU en la carga
   * _Nota de corrección_: las operaciones asíncronas y sincronizadas anteriormente fallaron debido a errores al guardar el producto si falta sku en la carga útil. Después de la corrección, las operaciones de API de rest de guardado de producto asincrónico y sincrónico fallan con un mensaje de excepción relevante.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [NUBE] No se pueden actualizar los precios base mediante la API de REST (el valor de &#39;value_id&#39; en &#39;catalog_product_entity_decimal&#39; no se incrementa correctamente).
   * _Nota de corrección_: Anteriormente a esta corrección, cuando se llamó a rest api /rest/default/V1/products/base-price, el id de incremento se aumentó erróneamente dejando un espacio entre los valores. Después de la corrección, el ID de incremento se incrementa según lo esperado. También se aumentó el rango del campo value_id.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: Los artículos de pedido no están visibles en los correos electrónicos de nota de abono para la API POST V1/order/:orderId/return
   * _Nota de corrección_: Anteriormente, antes de esta corrección, cuando un cliente crea un abono a partir de una solicitud de API que notifica a send_email, no contiene la cuadrícula de detalles del producto. Después de aplicar esta corrección, el cliente envía una solicitud de API de nota de crédito y encontrará los detalles del elemento de producto que aparecen en el correo electrónico.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
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

### API, GraphQL, Impuestos

* _AC-12060_: Luma (API de REST) y Graphql no calculan impuestos cuando solo se proporciona código postal.
   * _Nota de corrección_: El sistema ahora calcula correctamente los impuestos cuando solo se proporciona un código postal, lo que garantiza estimaciones de impuestos precisas tanto para Luma (API de REST) como para GraphQL. Anteriormente, solo se calculaban las estimaciones de envío y no se incluían los impuestos cuando solo se proporcionaba un código postal.

### Cuenta

* _AC-10782_: el formulario de dirección del cliente permite código aleatorio en los campos de nombre
   * _Nota de corrección_: el sistema ahora valida la entrada en los campos Nombre y Apellidos del formulario de dirección del cliente, lo que impide el uso de código aleatorio. Anteriormente, el sistema permitía el uso de código aleatorio en estos campos sin arrojar un error.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38331>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: actualización de contraseña de administrador.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38352>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: se bloqueó la dirección de adición de mi cuenta al guardar
   * _Nota de corrección_: El sistema ahora guarda correctamente las direcciones de los clientes incluso cuando no se muestra el campo de región, lo que evita un bloqueo durante el proceso de guardado. Anteriormente, si se intentaba agregar o editar una dirección sin un campo de región mostrado, se producía un error de excepción.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38406>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: bucle de redireccionamiento cuando la dirección URL está en mayúsculas
   * _Nota de corrección_: El sistema ahora convierte automáticamente los caracteres en mayúsculas de las direcciones URL en minúsculas, lo que evita un bucle de redireccionamiento al acceder a la página principal. Anteriormente, tener caracteres en mayúsculas en la URL de base segura provocaba un bucle de redirección continuo al intentar acceder a la página principal.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38538>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: los nombres intermedios no se guardaron para las cuentas de invitado
   * _Nota de corrección_: el sistema ahora guarda correctamente el segundo nombre de las cuentas de invitado durante el cierre de compra, por lo que es accesible en la plantilla de correo electrónico. Anteriormente, el segundo nombre no se guardaba en la tabla de comillas y no se podía acceder a él en la plantilla de correo electrónico de las cuentas de invitado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38593>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Administrador: Botones de acciones de página flotando a la izquierda en lugar de a la derecha
   * _Nota de corrección_: el sistema ahora alinea correctamente los botones de acción de página a la derecha del encabezado adhesivo en el panel de administración, lo que mejora la apariencia profesional. Anteriormente, estos botones flotaban incorrectamente en el lado izquierdo del encabezado adhesivo.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38701>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: error de `dev:di:info` en Magento 2.4.7
   * _Nota de corrección_: El sistema ahora muestra correctamente los parámetros del constructor al ejecutar el comando `dev:di:info`, lo que evita que se produzcan errores. Anteriormente, al ejecutar este comando, se producía un error debido a una discrepancia de tipos en el argumento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38740>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: la casilla de verificación de inclusión de Iniciar sesión como cliente no se puede traducir
   * _Nota de corrección_: el sistema ahora permite que los campos &quot;Casilla de verificación de inclusión de Iniciar sesión como cliente&quot; e &quot;Información de objeto de casilla de verificación de Iniciar sesión como cliente&quot; se establezcan en el ámbito &quot;Vista de tienda&quot;, lo que permite realizar traducciones para distintas vistas de tienda. Anteriormente, estos campos solo se establecían en el ámbito &quot;Sitio web&quot;, lo que impedía las traducciones para vistas de tiendas individuales.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32329>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32359>
* _AC-14299_: La página principal de la interfaz de usuario del front-end de mi perfil desplegable es que el botón no está ahí.(intermitentemente)
* _AC-6071_: el cliente ha iniciado sesión pero muestra un error 404 en front-end.
   * _Nota de corrección_: la página del panel del cliente de la tienda ahora se carga según lo esperado cuando un cliente inicia sesión. Anteriormente, los clientes podían iniciar sesión, pero esta página mostraba un error 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35838>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: no se puede guardar la información de atributos del cliente en la sección de administración Editar cliente;
   * _Nota de corrección_: El ID de tienda del cliente ahora se implementa correctamente por cada ámbito de sitio web para el formulario de edición de cliente de administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_: [Cloud] no puede crear clientes a través de API cuando las ventas privadas están habilitadas
   * _Nota de corrección_: Ahora el usuario administrador autenticado puede crear el cliente, así como con el token de integración autenticado a través de la API de REST, cuando la restricción del sitio web está habilitada.
* _ACP2E-3329_: Después de iniciar sesión, los productos agregados a la lista de comparación como usuarios invitados no son visibles.
   * _Nota de corrección_: los productos que se agregaron a la lista de comparación de productos antes de iniciar sesión como clientes ahora se conservan después de iniciar sesión.
Anteriormente, después de iniciar sesión, los productos agregados a la lista de comparación como usuarios invitados no eran visibles.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: La configuración de Permitir países causa problemas en las configuraciones de direcciones de clientes
   * _Nota de corrección_: al seleccionar Permitir países, la configuración no influye en los países mostrados fuera del ámbito determinado. Anteriormente, la configuración de Permitir países influía en el atributo de dirección del cliente fuera del ámbito determinado
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: Registro de regalos compartidos muestra la fecha del evento como 1 día antes
   * _Nota de corrección_: la fecha del registro de regalos se muestra correctamente ahora en Storefront
* _ACP2E-3501_: VAPT: Error de lógica empresarial: fecha futura como fecha de nacimiento del cliente
   * _Nota de corrección_: la fecha de nacimiento del cliente no se puede establecer después de hoy
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

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
* _AC-11427_: [Problema] Etiquetas incoherentes para atributos en reglas de marketing
   * _Nota de corrección_: el sistema ahora rellena correctamente las etiquetas de forma coherente para las opciones de categoría y atributo en la regla de precios del carro de compras
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/31232>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: la validación de datos es correcta y el botón Importar está presente durante Importar productos con el comportamiento Reemplazar
   * _Nota de corrección_: el sistema ahora valida correctamente los datos y oculta el botón &quot;Importar&quot; durante el proceso de importación del producto con el comportamiento &quot;Reemplazar&quot;, lo que evita cualquier reemplazo no deseado de los datos. Anteriormente, el sistema validaba los datos incorrectamente y mostraba el botón &quot;Importar&quot;, lo que producía posibles incoherencias en los datos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Error] Magento 2.4.7 no permite las fotos de productos con extensión de archivo en mayúsculas.
   * _Nota de corrección_: el sistema ahora acepta cargas de imágenes de productos con extensiones de archivo en mayúsculas, lo que garantiza un proceso de creación de productos sin problemas. Anteriormente, las cargas de imágenes con extensiones de archivo de mayúsculas se rechazaban, lo que obligaba a los usuarios a cambiar la extensión del archivo a minúsculas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38831>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: Menú desplegable oculto en las cuadrículas con una acción de selección (por ejemplo: Contenido > Elementos > Páginas)
   * _Nota de corrección_: Ahora el sistema se ha corregido en todos los menús desplegables similares para todas las cuadrículas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38891>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39371>
* _AC-13131_: [Advertencia de corrección de problema]: &quot;filtros&quot; de clave de matriz sin definir
   * _Nota de corrección_: el sistema ahora administra escenarios en los que un nuevo usuario aún no ha interactuado con marcadores, lo que impide que se registre una advertencia de &quot;filtros&quot; de clave de matriz no definida. Anteriormente, esta advertencia se registraba cuando un usuario nuevo no había interactuado con los marcadores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39013>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: el archivo csv de importación de productos con caracteres especiales falla debido a cambios de código en el archivo Validate.php
   * _Nota de corrección_: el sistema ahora valida e importa correctamente los archivos CSV del producto que contienen caracteres especiales, lo que permite la transferencia de datos correcta. Anteriormente, al intentar importar un archivo CSV de productos con caracteres especiales, se producía un error que impedía el proceso de importación.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: Cuando el número máximo de solicitudes de restablecimiento de contraseña&quot; está establecido en más de 0, p. ej.: 3 , &quot;Los mensajes de error que exceden el límite se envían antes de alcanzar el límite, es decir, desde la segunda vez
* _AC-13768_: aunque el número máximo de solicitudes de restablecimiento de contraseña&quot; está establecido en 0( deshabilitado) , &quot;Los mensajes de error que sobrepasan el límite se envían desde la segunda vez&quot;
* _AC-13850_: no hay asterisco rojo para el campo obligatorio de número de teléfono
   * _Nota de corrección_: el asterisco rojo anterior no se mostraba para el número de teléfono, pero  el número de teléfono era obligatorio. Que ahora es un asterisco rojo fijo se puede ver en el número de teléfono como un campo obligatorio.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c699c206>
* _AC-14300_: en el administrador, cuando intentamos reordenar el botón de envío del pedido, no se puede hacer clic en él. (intermitentemente)
* _AC-6975_: [Problema] Establecer el modo de indizador predeterminado en &#39;horario&#39;
   * _Nota de corrección_: todos los indizadores nuevos se encuentran de manera predeterminada en el modo **[!UICONTROL Update by Schedule]**.  Anteriormente, el modo predeterminado era **[!UICONTROL Update on Save]**. Los indexadores existentes no se ven afectados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36419>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problema] Eliminar tablas de registro de cambios del indizador al cancelar la suscripción de mview
   * _Nota de corrección_: El sistema ahora elimina automáticamente las tablas de registro de cambios no utilizadas cuando se cambia un índice de &#39;actualizar según lo programado&#39; a &#39;actualizar al guardar&#39;, marcando el índice como no válido para garantizar que no se pierdan entradas. Anteriormente, cambiar un índice a &quot;actualizar al guardar&quot; dejaba tablas de registro de cambios no utilizadas en el sistema y marcaba todos los índices cambiados como &quot;válidos&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/29789>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: no hay vínculo de envío en los pagos al pagar en la vista de teléfono móvil
   * _Nota de corrección_: El sistema ahora garantiza que los títulos/vínculos de pago y envío y &quot;Revisión y pagos&quot; estén siempre visibles en la parte superior de la página en la vista móvil, lo que permite a los usuarios navegar fácilmente entre los pasos y realizar las correcciones necesarias. Anteriormente, estos títulos o vínculos estaban ocultos en la vista móvil, lo que dificultaba a los usuarios conocer su paso actual o volver a pasos anteriores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36856>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: los comentarios de envío de consulta de pedidos de clientes created_at se devuelven en la zona horaria +0 que no está configurada en la tienda
   * _Nota de corrección_: el sistema ahora muestra correctamente el campo &quot;created_at&quot; de los comentarios de envío en la zona horaria configurada del cliente al utilizar la consulta de pedidos del cliente. Anteriormente, el campo &quot;created_at&quot; se mostraba en la zona horaria +0, independientemente de la configurada por el cliente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36947>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-phrases rompe la integridad de las traducciones
   * _Nota de corrección_: El comando `bin/magento i18n:collect-phrases -o` ahora recopila y agrega correctamente nuevas frases de archivos JavaScript y .phtml, lo que garantiza que las traducciones se reflejen con precisión en el archivo de traducción. Anteriormente, el sistema no incluía frases de traducción multilínea de archivos JavaScript ni frases de archivos .phtml en el archivo de traducción, lo que provocaba traducciones incompletas o incorrectas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2687_: Problema de permisos para acceder a Dynamic Block
   * _Nota de corrección_: Anteriormente, para el administrador restringido, al agregar un nuevo bloque dinámico, se produjo un error. Después de implementar esta corrección, el administrador restringido puede agregar correctamente el bloque dinámico y editar el bloque sin ningún error
* _ACP2E-2787_: el apóstrofo del nombre de la vista de la tienda se ha reemplazado por &#39;
   * _Nota de corrección_: los filtros de vista de almacén de la cuadrícula ahora muestran correctamente apóstrofos
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38395>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: La carga de Favicon no puede validar los archivos .ico
   * _Nota de corrección_: el error de validación del archivo se ha actualizado a &quot;Error de validación del archivo. Compruebe la configuración de procesamiento de imágenes en la configuración de la tienda&quot;. Anteriormente, era simplemente &quot;Error de validación de archivo&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: La galería en PageBuilder está mostrando una miniatura de imagen antigua en lugar de una imagen recién cargada
   * _Nota de corrección_: vuelva a generar vistas previas de imágenes para las imágenes eliminadas y cargadas de nuevo con el mismo nombre a través de la galería de medios en el contenido del generador de páginas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: al guardar el producto por un usuario administrador con un ámbito de función diferente, se sobrescribe o elimina la información de producto relacionada existente en el producto
   * _Nota de corrección_: anteriormente, antes de la corrección, los productos relacionados se restablecían y quedaban vacíos cuando el usuario administrador secundario hacía clic en el botón Guardar sin cambiar en el producto relacionado. Después de esta corrección, el usuario administrador secundario hace clic en el botón guardar y el producto no se restablece y se guarda correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: No se pueden exportar más de 200 pedidos
   * _Nota de corrección_: Los límites del servidor para el tamaño de solicitud de los ID seleccionados enviados anteriormente se han descuidado al modificar la solicitud HTTP de GET a POST para solucionar el problema. Anteriormente, debido a las limitaciones del servidor para el tamaño de la solicitud de GET, se encontraba el problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Mensaje de validación de página de cierre de compra incorrecto.
   * _Nota de corrección_: si se deja vacío algún campo obligatorio, como &quot;dirección&quot;, la validación del lado del servidor no mostrará el mensaje. La validación del lado del cliente garantizará que aparezca la notificación de error del campo requerido, que indica &quot;Este es un campo obligatorio&quot;. Anteriormente, aparecía el mensaje &quot;la dirección es obligatoria&quot; si se dejaba vacío cualquier campo requerido, además del mensaje de validación del lado del cliente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Problema de plantilla de restablecimiento de contraseña con el usuario administrador
   * _Nota de corrección_: el problema se resolvió usando la clave correcta, que ahora incluye el nombre de usuario del administrador en la plantilla de correo electrónico y completa correctamente el asunto. Anteriormente, el problema se debía a una clave obsoleta que se estaba utilizando.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: Barras dobles en la dirección URL del segmento del cliente
   * _Nota de corrección_: Las barras dobles no aparecen en la dirección URL cuando se hace clic en &#39;Restablecer filtro&#39; en la cuadrícula.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: COD no está disponible para países específicos permitidos
   * _Nota de corrección_: Ahora el Pago contra reembolso está disponible para países específicos permitidos siempre que sea necesario y   AC-3216 funciona según lo esperado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: No se puede actualizar el estado del pedido creado a medida
   * _Nota de corrección_: &#39;
Ahora podemos actualizar los estados de los pedidos creados a medida, mientras que anteriormente el estado solo se podía cambiar si el estado actual era &quot;Procesando&quot; o &quot;Fraude&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38659>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: El estado de la dirección de envío no se actualiza automáticamente
   * _Nota de corrección_: antes de la corrección, la región de dirección de envío (o id de región) no estaba sincronizada con la información de facturación de direcciones. Ahora, tanto la región de la dirección de envío como el ID de región se actualizan correctamente cuando se cambia la información de la dirección de facturación.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: El botón Restablecer no funciona en Agregar/Editar usuario administrador
   * _Nota de corrección_: anteriormente, el botón Restablecer no funcionaba en la página Agregar o editar usuario administrador. Ahora, en el panel Administración en Sistema -> Permisos -> Todos los usuarios, el botón Restablecer funcionará correctamente en la página Agregar/Editar usuario administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: detección incorrecta de enrutamiento de URL de administración de Magento y errores CORS
   * _Nota de corrección_: después de la corrección, si el dominio de administración personalizado es un subdominio del dominio principal, el administrador solo es accesible desde el subdominio configurado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37663>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: validación dañada para &#39;Cantidad máxima permitida en el carro de compras&#39;
   * _Nota de corrección_: anteriormente, cuando dejamos `Maximum Qty Allowed in Shopping Cart` vacío, no arrojó ninguna excepción, aunque no se acepta un valor vacío aquí. Una vez aplicada esta corrección, al colocar una cadena vacía se producirán excepciones y no se permitirá guardar el producto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problema de IU de vista previa de Pagebuilder] Los botones de la columna Page Builder no se alinean correctamente
   * _Nota de corrección_: los botones de las columnas de Page Builder ahora están correctamente alineados. Anteriormente, se desalineaban dentro de las columnas de Page Builder.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: el informe de productos pedidos no se está exportando. Error 404 en su lugar.
   * _Nota de corrección_: la exportación de informes de productos ordenados a CSV y XML ahora funciona según lo esperado
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: Error de TinyMCE JS en la consola tras habilitar la minificación de Js con el modo de producción
   * _Nota de corrección_: Anteriormente, al habilitar la minificación de JavaScript en el modo de producción dentro del panel de administración, aparecían errores de JavaScript relacionados con TinyMCE 6 en la consola del explorador, lo que afectaba a la funcionalidad y a la experiencia del usuario. Ahora, este problema se ha resuelto, lo que garantiza que TinyMCE 6 funcione sin problemas sin generar errores, incluso cuando la minificación JS esté habilitada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Solicitud de cambios adicionales para completar completamente la corrección de ACP2E-3375
   * _Nota de corrección_: &#39;-
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: Habilitación automática de nuevos permisos ACL
   * _Nota de corrección_: los nuevos permisos agregados a los módulos personalizados ya no concederán acceso automáticamente a todas las funciones de usuario existentes a menos que se configuren explícitamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: El informe de usuario del registro de acciones de administración no muestra detalles de adminhtml_user_delete
   * _Nota de corrección_: el adminhtml_user_delete ahora registra correctamente los detalles importantes. Anteriormente, no se generaban registros para las eliminaciones de usuarios.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: Regla de carro de compras con condición de envío que no se aplica al realizar un pedido del administrador
   * _Nota de corrección_: anteriormente, si la regla de precio del carro de compras tiene un descuento en el método de envío con el cupón, no se puede aplicar a través de la IU de administración. Después de aplicar esta corrección, la IU de administración aplica correctamente el descuento de la regla de precio del carro de compras con un cupón para un método de envío específico.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [El código HEX ]FRESH no se actualiza correctamente en SWATCH
   * _Nota de corrección_: el sistema ya no altera el código HEX que el usuario introduce manualmente en el selector de color de la muestra visual. Anteriormente, algunos códigos HEX experimentaban ligeros ajustes debido a errores de conversión entre modelos de color.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### IU de administración, B2B

* _AC-13628_: el inicio de sesión B2B como encabezado de cliente sigue teniendo la marca Magento
   * _Nota de corrección_: anteriormente, el encabezado de la tienda muestra &quot;Ahora está conectado como &lt;nombre de cliente> en &lt;nombre de tienda>&quot; con la marca Magento. Que ahora es fijo y el encabezado se muestra con la marca ADOBE.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/96dec499>

### IU de administración, catálogo

* _ACP2E-2708_: No se pueden cambiar las posiciones de los productos de categoría en el sitio web permitido como usuario administrador restringido
   * _Nota de corrección_: permita que un usuario administrador restringido agregue y ordene productos en una categoría incluida en la categoría raíz asignada en el sitio web restringido.

### IU de administración, métodos de pago/pago, pedido

* _AC-13520_: la autorización de transacción no se muestra en la ficha Transacción después de que se haya realizado el pedido del botón inteligente de PayPal
   * _Nota de corrección_: El sistema ahora muestra correctamente la autorización de transacción en la ficha Transacción después de realizar un pedido mediante el botón Smart Button de PayPal. Anteriormente, la transacción de autorización no aparecía en la pestaña Transacción después de hacer clic en el botón &quot;Autorizar&quot; y no se creaba ninguna nueva transacción de tipo &quot;Autorización&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### IU de administración, rendimiento

* _ACP2E-3169_: Después de la actualización a 2.4.5-p8 se producen 500 errores al crear el pedido del administrador
   * _Nota de corrección_: Anteriormente, al habilitar la minificación de HTML, no se podía realizar un pedido del administrador. Ahora, con la minificación de HTML habilitada, el pedido del administrador se puede realizar correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### IU de administración, envío

* _ACP2E-2519_: El recuento de código de cupón no se actualiza en   Columna &quot;Tiempo utilizado&quot; en la pestaña Administrar códigos de cupón si se realiza un pedido con varios envíos.
   * _Nota de corrección_: anteriormente, cuando se realizaba un pedido con varios envíos, el recuento de código de cupón no se actualizaba en la columna &quot;Tiempo utilizado&quot; de la ficha Administrar códigos de cupón. Ahora, el recuento correcto se muestra tanto en el &quot;Tiempo utilizado&quot;, que refleja los valores deseados con envío múltiple.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/4745100c>

### IU de administración, ensayo y vista previa

* _ACP2E-3424_: [Nube] Al eliminar la plantilla con imágenes que faltan, se eliminan los medios/pub
   * _Nota de corrección_: Anteriormente a esta corrección, si faltaba el nombre de la imagen de vista previa para una plantilla de pagebuilder, se eliminaba la carpeta pub/media. Después de la corrección, solo se eliminará la plantilla y la imagen de vista previa si se encuentra.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Análisis / Informes

* _AC-9922_: error de CSP de Google Analytics https://region1.analytics.google.com
   * _Nota de corrección_: El sistema ahora permite correctamente las conexiones a &#39;https://region1.analytics.google.com&#39; cuando Google Analytics está habilitado, lo que evita errores de la Política de seguridad de contenido (CSP). Anteriormente, habilitar Google Analytics y ver el sitio web desde la UE resultaba en errores de la consola CSP debido a la negativa a conectarse a &quot;https://region1.analytics.google.com&#39;&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37750>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: El informe avanzado no funciona
   * _Nota de corrección_: el sistema ahora admite la generación de archivos de datos de informes avanzados para conjuntos de datos extra grandes cargando y escribiendo informes en lotes de 10 000. Anteriormente, el módulo de informes avanzados no podía generar archivos de datos para conjuntos de datos extragrandes, lo que provocaba errores &quot;MySQL server has gone away&quot; durante la ejecución del trabajo cron analytics_collect_data.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Problema de visibilidad del intervalo de fechas de los productos ordenados por el administrador.
   * _Nota de corrección_: el usuario podrá seleccionar cualquier fecha del informe de productos solicitados. Anteriormente, después de actualizar la tabla, al seleccionar la fecha &quot;DESDE&quot; se restablecía la fecha &quot;HASTA&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Encabezados curl incorrectos que hacen que `newrelic:create:deploy-marker` no funcione
   * _Nota de corrección_: El sistema ahora da formato correctamente a los encabezados curl, lo que permite que el comando `newrelic:create:deploy-marker` cree correctamente un marcador de implementación en New Relic. Anteriormente, unos encabezados curl incorrectos impedían la creación de un marcador de implementación en New Relic.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37641>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
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

### Análisis / Informes, B2B

* _ACP2E-2300_: B2B - el mapa del sitio incluye productos/categorías no asignados a un catálogo compartido
   * _Nota de corrección_: Restrinja las categorías y productos generados por el mapa del sitio a las categorías y productos asignados únicamente al catálogo compartido público y/o a la configuración de permisos de categoría del catálogo.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics / Creación de informes, Cloud

* _ACP2E-3067_: Magento descarta la mayoría de las transacciones cron de New Relic #34108
   * _Nota de corrección_: AC informa correctamente de las transacciones relacionadas con trabajos cron a NewRelic. Anteriormente, algunas transacciones relacionadas con trabajos de cron se mostraban como &quot;OtherTransaction/Action/unknown&quot; en NR
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: La métrica en NR puede ser engañosa para transacciones en segundo plano- Seguimiento de ACP2E-3067
   * _Nota de corrección_: las transacciones en segundo plano (cron) utilizarán el nombre de aplicación de New Relic definido en la configuración
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: el paquete Enterprise Edition 2.4.8-beta102 está fallando con excepciones de aplicación
* _ACP2E-2139_: Los productos asignados al catálogo compartido no se reflejan en el front-end cuando se ejecuta el índice parcial
   * _Nota de corrección_: los productos asignados al catálogo compartido mediante la API de REST ahora están visibles inmediatamente en la tienda una vez completada la indexación parcial. Anteriormente, los productos solo eran visibles después de una reindexación completa.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-2873_: [Nube] El precio mostrado en la versión móvil y de escritorio no es el mismo en &quot;Mis presupuestos&quot;
   * _Nota de corrección_: ya no se muestra la línea Incluir impuestos innecesaria en la oferta negociable cuando se gasta la sección de precio total del catálogo.
* _ACP2E-3044_: Bordes innecesarios en la sección Mis pedidos
   * _Nota de corrección_: Anteriormente se creaba un contenedor adicional (referencias de pedidos) que aplicaba clases CSS adicionales, lo que provocaba que aparecieran líneas de borde innecesarias debajo del número de pedido dentro de la sección Mis pedidos, que ahora no está visible.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quote cron elimina las ofertas de los pedidos de compra aún aprobados
   * _Nota de corrección_: el trabajo cron sales_clean_quote no eliminará las ofertas usadas en los pedidos de compra ahora
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: El botón Realizar pedido desaparece en los detalles del pedido de compra
   * _Nota de corrección_: se corrigió un problema por el que el botón Realizar pedido estaba oculto para pedidos de compra aprobados cuando una variación de producto tenía un número mínimo en la tarjeta especificada
* _ACP2E-3474_: [NUBE] No existe esa entidad con id = 0 con módulo b2b
   * _Nota de corrección_: el usuario que ha iniciado sesión puede agregar un producto al carro de compras cuando las características de Catálogo compartido están habilitadas.
Si se agregaba anteriormente un producto al carro, se producía el error &quot;no existe esa entidad con ID = 0&quot;
* _ACP2E-3562_: No se muestra ningún mensaje de error para nuestra lista de productos de stock al agregar por lotes desde la lista de solicitudes
   * _Nota de corrección_: antes de la corrección se mostraba un mensaje de éxito independientemente del número de productos que no se pudieron agregar al carro de compras. Ahora se muestran mensajes independientes para los productos que se agregaron correctamente al carro de compras y para los productos que fallaron.
* _ACP2E-3628_: Problema con las actualizaciones de SKU después de actualizaciones programadas que causan permisos de producto incorrectos (-2 denegar)
   * _Nota de corrección_: al modificar la SKU de un producto con actualizaciones programadas anteriores, ya no es posible el acceso al producto para los clientes del catálogo compartido que tienen derecho a verlo.

### B2B, catálogo

* _ACP2E-2860_: productos/categorías visibles durante la reindexación al usar los permisos NoDDL y de categoría
   * _Nota de corrección_: evite mostrar en categorías restringidas de tienda y su contenido mientras se realiza la indexación de permisos de catálogo.

### B2B, marco

* _AC-9607_: Filtrar la cuadrícula de la empresa y luego intentar exportar el CSV de la cuadrícula fallará y generará una excepción
   * _Nota de corrección_: el sistema ahora permite exportar correctamente a CSV los datos de la cuadrícula Compañías en el panel de administración, incluso cuando se aplican filtros como &quot;Saldo pendiente&quot; y &quot;Tipo de compañía&quot;. Anteriormente, si se aplicaban ciertos filtros y se intentaba exportar los datos de la cuadrícula, se producía un error y se producía una excepción.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>

### B2B, GraphQL

* _ACP2E-3391_: [Nube] No se pueden establecer custom_attributes al crear la compañía a través de la llamada de graphql
   * _Nota de corrección_: después de la corrección, es posible establecer el atributo &quot;custom_attributes&quot; para el administrador de la compañía durante la creación de la compañía mediante una solicitud de graphql.

### Braintree

* _AC-14293_: el botón de desprotección de Admin Express está deshabilitado.
* _PAQUETE-3367_: Paga a través de LPM
   * _Nota de corrección_: El sistema ahora procesa correctamente los Métodos de pago locales (LPM) en la carga inicial, incluso cuando las direcciones de envío y facturación de un cliente que inició sesión no coinciden, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, una discrepancia entre las direcciones de envío y facturación de un cliente impedía que LPM se representara, lo que causaba posibles interrupciones durante el cierre de compra.
* _PAQUETE-3368_: configurable con producto virtual como secundario
   * _Nota de corrección_: El sistema ahora permite métodos de pago exprés para productos configurables que tienen un producto secundario virtual, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, los métodos de pago exprés no estaban disponibles cuando se agregaba al carro de compras un producto configurable con un producto secundario virtual.
* _PAQUETE-3369_: Error de comprobación de CSV
* _PAQUETE-3370_: problemas en el área de la cuenta para el almacenamiento en bóveda 247
   * _Nota de corrección_: el sistema ahora permite a los clientes guardar información de nuevas tarjetas o cuentas de PayPal en varios sitios web sin encontrar errores de autorización. Anteriormente, los clientes no podían guardar nuevos métodos de pago en diferentes sitios web y se les presentaba un mensaje de error de autorización.
* _PAQUETE-3371_: Enviar a una dirección de un país diferente
   * _Nota de corrección_: el sistema ahora permite que las transacciones se procesen sin errores al realizar envíos a una dirección de un país diferente, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, intentar enviar a una dirección de un país diferente resultaba en errores de consola, a pesar de que no había errores visibles en el front-end.
* _PAQUETE-3372_: Tarjeta de crédito - Función de desmontaje
   * _Nota de corrección_: El sistema ahora gestiona correctamente el desmontaje de los componentes de Braintree PayPal cuando un cliente vuelve de la página de pago a la página de envío, lo que evita cualquier error y garantiza que los botones de PayPal Express se muestren correctamente. Anteriormente, al volver a la página de envío desde la página de pago, a veces se producía un error al intentar desmontar los componentes de Braintree PayPal.
* _PAQUETE-3373_: devolución de llamada de envío para PayPal Express
   * _Nota de corrección_: el sistema ahora muestra correctamente los métodos de envío disponibles en el modal PayPal Express, lo que permite a los clientes seleccionar el método de envío preferido antes de pasar a la página de revisión o completar su transacción. Anteriormente, no había métodos de envío disponibles para seleccionar en el modal PayPal Express, lo que requería que los clientes seleccionaran un método de envío en una página de revisión independiente antes de poder completar su transacción.

### Paquete

* _AC-10826_: validación de casilla de verificación de paquete de tienda Error de recuento de mensajes de más de 1
   * _Nota de corrección_: el sistema ahora muestra un solo mensaje de error de validación cuando se hace clic en el botón &#39;Agregar al carro de compras&#39; sin seleccionar ninguna opción de casilla de verificación para un producto agrupado. Anteriormente, el sistema mostraba varios mensajes de error de validación para cada casilla de verificación no seleccionada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: se produjo una excepción de Magento en algunos casos de prueba relacionados con pedidos
   * _Nota de corrección_: el sistema ahora administra correctamente el paso &#39;sendGuestPaymentInformation&#39; en varios casos de prueba, lo que impide que se produzcan excepciones de Magento. Anteriormente, estas excepciones se producían debido a un método de pago nulo, lo que provocaba errores en varios casos de prueba.

### Carro y cierre de compra

* _AC-10660_: la excepción no se controla correctamente al agregar un producto al carro de compras en la página de comparación de productos
   * _Nota de corrección_: el sistema ahora administra correctamente las excepciones al agregar un producto al carro de compras desde la página de productos de comparación, mostrando un mensaje del administrador de mensajes en el controlador. Anteriormente, una excepción provocaba que se devolviera una página con codificación JSON en lugar de capturarse y gestionarse correctamente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38200>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag no envía los precios y totales de transacción.
   * _Nota de corrección_: El sistema ahora envía correctamente los precios y totales de transacción a Google Tag cuando GTag está habilitado, lo que garantiza un seguimiento preciso de los datos de comercio electrónico. Anteriormente, la moneda se enviaba incorrectamente como parte de los pedidos &quot;todos&quot;, en lugar de asociarse con el pedido individual.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37348>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Problema] [Cierre de compra] Se han actualizado las directivas dependientes en la plantilla de correo electrónico de pago con errores
   * _Nota de corrección_: el sistema ahora omite correctamente la dirección de envío y el método de envío de la plantilla de correo electrónico de pago errónea para los productos virtuales, lo que garantiza que solo se incluya información relevante en el correo electrónico. Anteriormente, el correo electrónico de pago erróneo para productos virtuales incluía incorrectamente la dirección de envío y el método de envío.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32781>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: el inicio de sesión de Magento 2 dentro del cierre de compra con un error de la consola de cliente existente en el navegador Firefox
   * _Nota de corrección_: el sistema ahora permite a los usuarios iniciar sesión durante el proceso de cierre de compra sin encontrar errores de consola en el explorador Firefox. Anteriormente, si se intentaba iniciar sesión como un cliente existente durante el cierre de compra, se producía un error de consola en Firefox.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38557>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [Problema] Regresión de reglas de ventas en 2.4.7
   * _Nota de corrección_: El sistema ahora valida correctamente las reglas de ventas, lo que impide la aplicación de un código de cupón a un carro de compras cuando la condición del producto no coincide con ningún nombre de producto. Anteriormente, se podía aplicar una regla de ventas y aplicar un descuento en el importe de envío incluso cuando la condición del producto no coincidía con ningún nombre de producto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38671>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Problema] Cálculo del carro de compras de la regla de ventasCálculo corregido : cantidad de descuento incorrecta
   * _Nota de corrección_: El sistema ahora calcula correctamente el importe de descuento de las reglas de ventas con importes fijos del carro de compras, lo que garantiza que se apliquen descuentos precisos independientemente de los cambios en los elementos del carro de compras. Anteriormente, la cantidad de descuento podía variar incorrectamente cuando cambiaban los artículos del carro de compras, lo que a veces resultaba en descuentos significativamente mayores de lo esperado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38694>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Problema] El cargador bloquea los métodos de envío después de que se cambie el código postal y las reglas de validación de tarifas de envío
   * _Nota de corrección_: el sistema ahora administra correctamente los métodos de envío personalizados sin reglas de validación de tarifas de envío, lo que garantiza que el cargador no bloquee los métodos de envío después de que se cambie el código postal en la dirección de envío durante el cierre de compra. Anteriormente, si se cambiaba el código postal en la dirección de envío durante la desprotección, el cargador bloqueaba los métodos de envío y no desaparecía cuando se utilizaban métodos de envío personalizados sin reglas de validación de tarifas de envío.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38742>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: La característica de código de cupón no funciona correctamente en la página de pago en Magento 2.4.7
   * _Nota de corrección_: el sistema ahora habilita el campo de entrada de código de descuento/cupón en la página de cierre de compra para productos virtuales y descargables, lo que permite a los usuarios aplicar códigos de descuento según lo esperado. Anteriormente, la entrada del código/cupón de descuento estaba desactivada y el texto del título del botón se mostraba como &quot;Cancelar cupón&quot;, lo que impedía a los usuarios aplicar códigos de descuento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38826>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
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
* _AC-13797_: el producto del registro de regalos no se muestra correctamente
* _AC-13841_: el producto del registro de regalos no se muestra correctamente
* _AC-8103_: IVA de traducción en el procesador de direcciones
   * _Nota de corrección_: El sistema permite ahora la traducción del texto &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; en los procesadores de direcciones, lo que permite a los usuarios traducir estos términos al idioma específico de la tienda. Anteriormente, estos términos no se podían traducir, lo que obligaba a los usuarios a emplear una solución alternativa.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36942>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: duplicar pedidos con el mismo id. de presupuesto al mismo tiempo y con pocas diferencias horarias
   * _Nota de corrección_: se corrigió el problema cuando los clientes de Adobe Commerce encontraban pedidos duplicados realizados con el mismo QuoteID
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Se borró el carro de compras persistente durante el paso de cierre de compra
   * _Nota de corrección_: después de la corrección, al seleccionar el método de pago durante el cierre de compra sin haber iniciado sesión, no se finaliza la sesión persistente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: al reordenar se agrega un producto no asignado al carro de compras
   * _Nota de corrección_: anteriormente, para las diferentes tiendas, los productos se pueden reordenar desde la otra tienda. Después de aplicar esta corrección solo en el mismo almacén , se puede reordenar el mismo producto de ámbito cuando se habilita el recurso compartido de cuenta de cliente
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: En administración, el &quot;Carro de compras&quot; de la izquierda no se actualiza al seleccionar los artículos y &quot;Mover al carro de compras&quot; de la derecha
   * _Nota de corrección_: El &quot;carro de compras&quot; del lado izquierdo se actualiza al seleccionar los elementos y &quot;Mover al carro de compras&quot; del lado derecho en el lado del administrador. Anteriormente, esta funcionalidad no funcionaba porque los elementos del carro de compras transformados no se estaban vaciando de la sesión.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: La regla de ventas de [Cloud] no se aplica al primer pedido de Multi Shipping
   * _Nota de corrección_: después de la corrección, el descuento se muestra correctamente para cada pedido de la misma oferta de envío múltiple.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: Las solicitudes paralelas de producción de [Cloud] para agregar el mismo producto al carro de compras resultan en dos elementos separados en la API REST del carro de compras
   * _Nota de corrección_: el sistema ahora procesa correctamente varias solicitudes paralelas para agregar el mismo producto al carro de compras en un solo elemento de línea, lo que impide la creación de elementos de línea independientes para el mismo SKU. Anteriormente, realizar solicitudes paralelas para añadir el mismo producto al carro de compras mediante la API de REST resultaba en varios elementos de línea para el mismo SKU.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_: Problema con el pedido desde el registro de regalos Magento 2.4.4 Enterprise/Commerce
   * _Nota de corrección_: se ha resuelto el problema que impedía la compra correcta de un producto de un registro de regalos, lo que permite realizar pedidos y actualizar correctamente el registro de regalos. Anteriormente, se producía un error al intentar realizar un pedido desde un registro de regalos, lo que impedía la finalización de la compra.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_: No se puede enviar la cookie. Tamaño de los &quot;mensajes de imagen&quot; al intentar reordenar
   * _Nota de corrección_: el proceso de reordenación no generará sus propios errores en este momento. Se basará en las comprobaciones de artículos integrados del anuncio del carro de compras.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: La dirección de envío predeterminada no está seleccionada al cerrar la compra
   * _Nota de corrección_: la dirección de envío predeterminada se está seleccionando ahora como evento en el contexto de la búsqueda de direcciones habilitada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [NUBE] problema de API addProductsToCart de graphql con opción personalizada
   * _Nota de corrección_: GraphQL agrega al carro de compras correctamente el mismo producto con diferentes opciones personalizadas
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2917_: Las reglas de productos relacionados de [Cloud] no funcionan al cambiar la vista de la tienda
   * _Nota de corrección_: el problema se ha corregido al confirmar que el valor de la propiedad personalizada se recibió correctamente en la página del carro de compras. Anteriormente, no se recuperaba correctamente al cambiar entre tiendas en la página del carro de compras de la tienda.
* _ACP2E-2923_: Se agregaron varias direcciones a la cuenta al cerrar la compra como cliente nuevo
   * _Nota de corrección_: El sistema guarda ahora una nueva dirección de cliente solo una vez si no se ha podido crear el pedido, lo que impide la creación de varias direcciones idénticas en caso de errores de colocación del pedido. Anteriormente, el sistema guardaba una nueva dirección cada vez que se realizaba un intento de realización de un pedido, independientemente de si el pedido se había creado correctamente o no.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Reordenar el pedido del cliente a través del formulario de pedido de invitado genera un carro vacío
   * _Nota de corrección_: Anteriormente, al realizar un repedido a través de la página Pedidos y devoluciones, se redirigía al cliente a la página de inicio de sesión. Después de aplicar esta corrección, el cliente registrado se redirige correctamente a la página Ver carro de compras al realizar un repedido. El flujo funciona igual que como los clientes invitados.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: el usuario administrador con recursos de rol limitados no puede ver los carros de compras
   * _Nota de corrección_: anteriormente, el administrador restringido no podía ver el carro de compras abandonado del panel de administración de un sitio web asociado. Después de aplicar esta corrección, el administrador restringido puede ver el carro de compras abandonado en el panel de administración.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
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
* _ACP2E-3415_: No se respeta la persistencia del carro de compras al cerrar la sesión
   * _Nota de corrección_: funcionalidad agregada que falta Recordarme desde el inicio de sesión del cliente hasta la ventana emergente de autenticación y los inicios de sesión de cierre de compra.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: Los datos de comillas existentes no se actualizan o no son visibles; en su lugar, cree un nuevo registro de comillas cuando déclencheur_recollect = 1
   * _Nota de corrección_: los elementos del carro de compras del cliente ya no desaparecen como resultado de la eliminación de un producto después de agregarlo al carro de compras.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3495_: Cuando se compra un artículo del Registro de regalos, el cliente ve artículos que no están en su Registro
   * _Nota de corrección_: la actualización del registro de regalos ya no incluye elementos que no pertenecen al registro de regalos.
* _ACP2E-3510_: [Nube] Problema con la ventana emergente de confirmación &quot;Quitar todo&quot; Quitando elementos del carro de compras sin confirmación
   * _Nota de corrección_: Ahora, al hacer clic en el botón &quot;Quitar todo&quot; para los productos que requieren atención, aparece una ventana emergente de confirmación para asegurarse de que los elementos solo se quitan con la confirmación. Anteriormente, los elementos se eliminaban inmediatamente sin ninguna confirmación
* _ACP2E-3618_: [NUBE] Función de botón de reordenar
   * _Nota de corrección_: al reordenar un pedido desde el área de administración, ahora se agregarán productos con existencias a la oferta aunque haya algunos productos en el pedido original que ya no tengan existencias. Antes de la corrección, no se añadían productos a la nueva oferta si los productos sin existencias estaban en el pedido original.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: Las tiendas de búsqueda no funcionan por código postal
   * _Nota de corrección_: La búsqueda de ubicaciones de recogida por código postal no funcionaba correctamente en las localizaciones en neerlandés. Después de la corrección, la búsqueda de la ubicación de recogida proporcionará resultados basados en el código postal.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/344fce23>

### Carro y cierre de compra, cierre de compra/cierre de compra de una página

* _AC-9386_: [Error aleatorio] El campo de correo electrónico no se ha procesado o tarda mucho tiempo en aparecer en la página de pago o envío
   * _Nota de corrección_: Commerce ahora procesa el campo **[!UICONTROL Email]** en las páginas de envío y pago del cierre de compra según lo esperado. Anteriormente, este campo estaba ausente o se procesaba lentamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/e1babcfd>

### Carro de compras y cierre de compra, pedido

* _ACP2E-3097_: El selector de fecha para el producto con varias opciones personalizables con campos de fecha no funciona al realizar un pedido del administrador
   * _Nota de corrección_: el sistema ahora muestra correctamente el selector de fechas para todos los campos de fecha al configurar un producto con varias opciones de fecha personalizables en el proceso de creación de órdenes de administración. Anteriormente, el selector de fechas solo se mostraba para el primer campo de fecha, lo que dejaba los campos restantes sin selector de fechas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Carro y Pago, Envío

* _AC-12119_: compra instantánea de &quot;envío más barato&quot; interrumpida para productos configurables
   * _Nota de corrección_: La función de compra instantánea seleccionó incorrectamente la opción de entrega en tienda, más cara, para los productos configurables en lugar del método de tarifa plana más barato. Esta corrección garantiza que se elija el método de envío correcto en función del precio real&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38811>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catálogo

* _AC-10910_: la limpieza de la tabla de base de datos cron_schedule no limpia los trabajos no existentes
   * _Nota de corrección_: el sistema ahora limpia automáticamente la tabla de base de datos cron_schedule, eliminando las entradas de los trabajos que ya no existen en el sistema. Esto garantiza un rendimiento óptimo al mantener un número mínimo de filas en la tabla. Anteriormente, las entradas para trabajos de módulos inactivos o eliminados no se limpiaban, lo que producía una acumulación de datos innecesaria en la tabla cron_schedule.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38217>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: el precio de nivel no se está eliminando del producto configurable
   * _Nota de corrección_: el sistema elimina ahora correctamente el precio de nivel de un producto cuando se convierte de un producto simple a un producto configurable, lo que garantiza una visualización precisa del precio en el front-end. Anteriormente, el precio de nivel de un producto configurable no se eliminaba cuando un producto se convertía de un producto simple a un producto configurable, lo que provocaba un desajuste en el precio mostrado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38390>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: WYSIWYG de descripción de categoría está vacío en una vista de tienda no predeterminada
   * _Nota de corrección_: ahora el sistema guarda y muestra correctamente la descripción de la categoría en el editor de WYSIWYG al editar una categoría en el nivel de vista de tienda. Anteriormente, el editor de WYSIWYG aparecía vacío después de guardar una descripción de categoría en el nivel de vista de tienda.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38622>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38623>
* _AC-11970_: no se pueden reordenar los productos configurables con una casilla de verificación seleccionada como opción personalizada
   * _Nota de corrección_: El sistema ahora procesa correctamente la reordenación de los productos configurables con una sola opción personalizada de casilla de verificación seleccionada, lo que permite crear correctamente la cesta. Anteriormente, al intentar reordenar estos productos, se producía un error e impedía que se agregaran elementos al carro de compras.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38736>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-12076_: [Problema] Se corrigió la redacción del elemento de filtro en la navegación con capas
   * _Nota de corrección_: el sistema ahora utiliza correctamente las palabras &quot;item&quot; y &quot;items&quot; en el elemento de filtro de navegación por capas, lo que mejora la claridad y precisión de las descripciones de los filtros. Anteriormente, estas palabras se utilizaban incorrectamente, lo que producía una posible confusión para los usuarios que navegaban por las opciones de filtro.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38789>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: el formato de fecha y hora de la opción personalizada no funciona
   * _Nota de corrección_: el sistema ahora aplica correctamente el formato de fecha configurado a las opciones personalizadas del producto de tipo Fecha, asegurándose de que el formato de fecha se muestre correctamente en el front-end. Anteriormente, los cambios en la configuración del formato de fecha no se reflejaban en el front-end para las opciones personalizadas de producto de tipo Fecha.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32990>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38925>
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
* _AC-13622_: [Problema] Diseño de producto basado en attribute_set
   * _Nota de corrección_: el sistema ahora permite ajustar el diseño del producto en función del conjunto de atributos, lo que proporciona una forma más práctica y eficaz de administrar la visualización del producto en la tienda de front-end. Anteriormente, el diseño solo se podía ajustar por SKU o por tipos de producto, lo que no siempre era práctico para muchos productos o artículos específicos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38790>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: falta una clave única en la tabla eav_attribute_option_value
   * _Nota de corrección_: El sistema ahora incluye una clave única en las columnas &quot;option_id&quot; y &quot;store_id&quot; en la tabla &quot;eav_attribute_option_value&quot;, lo que evita la posibilidad de que una opción tenga varios valores para la misma vista de almacén. Anteriormente, un código defectuoso podía hacer que una opción tuviera varios valores para la misma vista de tienda, lo que provocaba problemas al editar productos o atributos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/24718>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Problema] Use la clase de visibilidad para el indizador de productos de categoría, en lugar de valores codificados
   * _Nota de corrección_: El sistema ahora utiliza la clase de visibilidad para el indizador de productos de categoría en lugar de valores codificados, lo que mejora la modularidad. Anteriormente, los valores codificados se utilizaban en el indexador de productos de categoría, lo que limitaba la flexibilidad y la adaptabilidad.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37200>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: el código de moneda no cambia en el widget Nuevo producto
   * _Nota de corrección_: el sistema ahora actualiza correctamente el código de moneda en el widget Nuevo producto cuando se cambia la moneda en el front-end, lo que garantiza la coherencia en la visualización de la moneda en todo el sitio. Anteriormente, el cambio de moneda en el front-end no afectaba al código de moneda mostrado en el widget Nuevo producto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37898>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: El precio normal no aparece en el PLP para productos configurables
   * _Nota de corrección_: ahora se muestra el precio normal en las páginas de lista de productos para los productos configurables que tienen productos secundarios con precio especial.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: La información de stock no se muestra correctamente en la cuadrícula de comercialización visual
   * _Nota de corrección_: ahora el inventario se muestra según el almacén seleccionado.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: el contenido del widget no se actualiza en la página de cms
   * _Nota de corrección_: el sistema ahora actualiza el contenido del widget en una página de CMS cuando un producto se establece como nuevo y se guarda, asegurándose de que la página muestre la colección de productos actualizada. Anteriormente, la página no se actualizaba para mostrar el nuevo producto debido a las identidades de caché incorrectas utilizadas para el widget en la caché.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: Problemas al guardar precios avanzados en productos agrupados
   * _Nota de corrección_: mejora del rendimiento al guardar el paquete.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [El proceso de reindexación local] es ineficiente al crear reglas de precios de catálogo
   * _Nota de corrección_: al guardar la regla de precio del catálogo, no se invalidarán los indizadores, sino que solo se reindexarán los productos afectados
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Actualizando la hora de los atributos de producto de tipo Fecha y Hora a través de la importación CSV
   * _Nota de corrección_: Ahora los atributos datetime tendrán parte de tiempo en los datos exportados. También será posible actualizar la hora de dichos atributos mediante la importación. Además, si &quot;Campos Enclosure&quot; está habilitado, los valores de atributo de la columna &quot;additional_attributes&quot; se escribirán entre comillas dobles.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38306>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: No hay un mensaje de error apropiado cuando el identificador del sitio web es incorrecto en la solicitud
   * _Nota de corrección_: Ahora se agregó el mensaje de error apropiado para mostrarlo cuando el id. del sitio web es incorrecto en la solicitud. Anteriormente, no había ninguna validación cuando el ID del sitio web era incorrecto en la solicitud.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: La imagen del producto se pierde después de eliminar una actualización programada existente que no afecta a la imagen
   * _Nota de corrección_: las imágenes de producto no se quitan al eliminar la actualización de ensayo.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Nube] Precio de paquete de producto incorrecto cuando se usa con precios de nivel
   * _Nota de corrección_: Anteriormente, al calcular ciertos descuentos porcentuales redondeados a 2 puntos decimales, se generarán precios finales diferentes para el carro de compras y la página de detalles de lista de productos/página de detalles del producto. Después de aplicar esta corrección, el precio final del producto del paquete es el mismo que en la página de detalles del producto, la página de lista de productos y la página del minicarrito.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38091>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: La regla de promociones de catálogo no funciona con el atributo quantity_and_stock_status
   * _Nota de corrección_: El atributo quantity_and_stock_status ahora será tenido en cuenta por la regla de promoción del catálogo, la cual no se había tenido en cuenta anteriormente al generar un nuevo producto desde el lado del administrador.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35627>
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: La entidad de producto updated_at no actualiza los valores de columna al actualizar el precio mediante la API de REST
   * _Nota de corrección_: la columna de producto &#39;actualizado por última vez el&#39; del administrador se actualiza en la fecha y hora adecuadas al actualizar los productos existentes mediante la API de REST. Anteriormente, la columna &quot;Última actualización en&quot; no se actualizaba correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Es posible establecer valores no únicos mediante la importación de productos
   * _Nota de corrección_: el sistema ahora aplica correctamente la restricción de valor único para los atributos de producto únicos durante la importación del producto, lo que impide que haya valores duplicados para ese atributo. Anteriormente, era posible establecer valores no únicos para atributos de producto configurados para tener valores únicos mediante la importación de productos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38445>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: Los productos del front-end usan datos específicos del almacén cuando el modo de almacén único está habilitado
   * _Nota de corrección_: anteriormente, cuando habilitábamos el modo de almacén único para la vista de almacén predeterminada, los cambios no se migraban al ámbito de nivel de sitio web. Después de aplicar esta corrección, cuando habilitamos el modo de tienda única, los datos predeterminados específicos de la vista de la tienda se sincronizarán con los datos específicos del nivel de sitio web y resolverán los posibles conflictos para productos y categorías.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: No se puede establecer &quot;Orden predeterminado por&quot; en una categoría mediante la API de REST
   * _Nota de corrección_: actualice correctamente default_sort_by en una categoría mediante una solicitud de API de REST/SOAP
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Nube] El comerciante enfrenta problemas con el recuento de listas de deseos
   * _Nota de corrección_: al agregar un producto a la lista de deseos en una tienda, ya no se incrementa el recuento de listas de deseos en otras tiendas abiertas en el mismo explorador. Anteriormente, si ambas tiendas se cargaban en el mismo explorador, el recuento de listas de deseos también aumentaba en la otra tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: La página Categoría en el front-end muestra espacios vacíos al usar el producto del paquete
   * _Nota de corrección_: los productos del paquete que no se pueden vender en el contexto actual de la tienda ya no se indizan.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2888_: [ACLARACIÓN] Problemas en la tabla de secuencia de productos del paquete
   * _Nota de corrección_: Los registros de las tablas de secuencia de productos del paquete (sequence_product_bundle_option, sequence_product_bundle_selection) ahora se eliminan cuando se elimina el producto del paquete o se eliminan las opciones de producto del paquete.
Anteriormente, los registros de las tablas de secuencia de productos del paquete no se eliminaban.
* _ACP2E-2905_: [Nube] Problema de cotización en la arquitectura de varios sitios web
   * _Nota de corrección_: anteriormente, la arquitectura de varios sitios web con distintas monedas y grupos de clientes no podía aplicar correctamente los descuentos a la tienda. Una vez implementada esta corrección, la arquitectura de varios sitios web con diferentes descuentos de precio de grupo de clientes se aplicará correctamente a las diferentes tiendas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38506>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 TypeError no capturado: dataRecord.slice al editar productos del paquete
   * _Nota de corrección_: no hay ningún error de JavaScript en la consola del explorador al eliminar la opción del producto del paquete.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38505>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: Paquete de [Nube] Precio incorrecto del producto en la confirmación del pedido
   * _Nota de corrección_: se muestra la cantidad correcta para las opciones de paquete en orden en Storefront cuando se utilizó una moneda distinta a la base uno.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Error al añadir vídeo de YouTube
   * _Nota de corrección_: las imágenes y los vídeos del producto están configurados en el ámbito global. Dado que no puede tener un vídeo de producto en un ámbito y no en otro, la configuración de clave de la API de YouTube se ha establecido en ámbito global.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [Actualización de URL de la nube] solo para store_id=0
   * _Nota de corrección_: La &quot;Ruta de URL&quot; ahora se almacena con el identificador de almacén correcto. Anteriormente, el ID de tienda era incorrecto, lo que provocaba que permanecieran rutas URL incorrectas en la base de datos al mover categorías.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all ejecutado y creado un error.
   * _Nota de corrección_: los datos de vínculos de productos incorrectos en las llamadas a la API de REST ya no causan errores críticos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Problema de nube] del dispositivo móvil No se pudo pellizcar la imagen PDP
   * _Nota de corrección_: El sistema ahora admite la funcionalidad de pellizco a zoom en las imágenes de la página de detalles del producto en la vista móvil en Chrome, lo que mejora la experiencia del usuario móvil. Anteriormente, al tocar dos veces la imagen en la vista móvil en Chrome, no se acercaba la imagen como se esperaba.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Falta la etiqueta en LayeredNavigation con el nombre de opción 0
   * _Nota de corrección_: el problema se ha resuelto omitiendo un comprobador de valores vacío para el valor de atributo 0. Anteriormente, se consideraba vacío y era la causa del problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: Los clientes ven precios de otros grupos de clientes
   * _Nota de corrección_: se ha corregido un problema por el que la información relacionada con el grupo de clientes se guardaba en un segmento incorrecto debido al valor antiguo de X-Magento-Vary en la solicitud
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Error al eliminar las opciones de paquete
   * _Nota de corrección_: el sistema ahora elimina correctamente las opciones de paquete sin activar un error ni hacer que la página no responda. Anteriormente, al intentar eliminar las opciones de paquete, se producía el error &quot;La página no responde&quot; y se impedía guardar el producto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_: Problema de permisos de categoría del explorador sin memoria
   * _Nota de corrección_: la interfaz de usuario de permisos de categoría se rediseñó para permitir la representación de una gran cantidad de permisos mediante la paginación y el componente de la interfaz de usuario listos para usar. Anteriormente, los permisos de categoría provocaban que el explorador se bloqueara con una gran cantidad de permisos asignados a la categoría.
* _ACP2E-3100_: El archivo de imagen [Cloud] no existe en el registro de errores de New Relic
   * _Nota de corrección_: El sistema ahora sincroniza las imágenes de marcador de posición personalizadas con el almacenamiento local, asegurándose de que se representen correctamente al utilizar el almacenamiento remoto como AWS S3. Anteriormente, las imágenes de marcador de posición personalizadas no se representaban al utilizar el almacenamiento remoto, lo que provocaba una visualización de imágenes rotas y registros de errores.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_: la fuente RSS de nuevos productos no se actualiza con nuevos productos debido a la caché
   * _Nota de corrección_: la fuente Rss para nuevos productos ahora se actualiza cuando un producto se establece como nuevo y se guarda
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: La respuesta de GQL de la Galería multimedia de productos de [Cloud] no está ordenada por la posición de la imagen
   * _Nota de corrección_: El sistema ahora ordena correctamente los elementos de la galería de medios por su posición en la respuesta de GraphQL, lo que garantiza un orden de visualización preciso. Anteriormente, los elementos de la galería de medios no se ordenaban por posición, lo que provocaba un orden de visualización incorrecto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37671>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Los elementos de subcategoría de la nube] no se muestran en la edición de widgets en el servidor de administración
   * _Nota de corrección_: el árbol de categorías de la nueva página del widget ya no debería tener problemas para cargar categorías de nivel 5+. Anteriormente, faltaban algunas categorías al cargar las tres últimas categorías de Nivel 5.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
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
* _ACP2E-3513_: [NUBE] No se muestra el precio especial en el producto configurable
   * _Nota de corrección_: después de la corrección, cambiar el valor &quot;Utilizado en el listado de productos&quot; para el atributo de precio especial no afectará a la presentación del precio especial de los productos configurables.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: los indizadores Las tablas temporales no se limpian si el proceso finaliza
   * _Nota de corrección_: las tablas temporales del indizador CatalogRule ahora se limpian si ha finalizado el proceso del indizador
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [QUANS] errores de prueba de unidad principal en 2.4.7-p3
   * _Nota de corrección_: no se necesitan notas de la versión para esta prueba porque es una mejora de prueba unitaria.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: Problema de rendimiento en la recuperación de cantidad de existencias para productos agrupados con varios orígenes
   * _Nota de corrección_: la página de edición de productos agrupados y agrupados ahora está optimizada cuando los productos asignados tienen un gran número de orígenes de inventario.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Refijar https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Nota de corrección_: se mejoró el rendimiento de la página de categoría de administrador en el caso de un gran número de categorías de anclaje
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

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

### Catálogo, marco

* _AC-9111_: pedido get(Shipments|Creditmemos|Invoice)Collection: la colección no se debe cargar
   * _Nota de corrección_: El sistema ahora garantiza que las colecciones de los envíos y los abonos no se precarguen cuando se recuperen de un pedido, lo que permite aplicar filtros o pedidos adicionales a estas colecciones. Anteriormente, estas colecciones se cargaban automáticamente, lo que impedía realizar más modificaciones.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37561>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: [Nube]Seguimiento: No coinciden en la comparación de datos al comprobar si los datos tienen cambios
   * _Nota de corrección_: anteriormente, se llamaba al objeto save cada vez sin ningún cambio de datos (para cualquier campo de datos numéricos, como int/float/double). Déclencheur el indicador _hasDataChanges para que sea true y llama a la función de guardado. Tampoco comprueba los números flotantes encapsulados por string. Después de aplicar esta corrección, la función de guardado solo llamará si se cambian los datos. El valor de datos para int/float/double-check con el valor que pasa a la función y hace una coincidencia de tipo estricta
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8931218>

### Catálogo, GraphQL

* _ACP2E-3090_: Gestión de filtros de categoría en GraphQL: includeDirectChildrenOnly y category_uid
   * _Nota de corrección_: solo se recuperan las categorías secundarias directas al filtrar por category_uid.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: La ordenación de productos de [Cloud] Graphql no funciona
   * _Nota de corrección_: La ordenación del producto GraphQl por varios campos cuando los campos se pasan en variables ahora funciona según lo esperado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: Los precios de nivel devuelven un valor incorrecto en los productos GraphQL (en comparación con Storefront)
   * _Nota de corrección_: después de la corrección, los precios de nivel del producto devueltos para las solicitudes de graphql tienen un precio por elemento.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [NUBE] B2B: problema de categoría a través de GraphQL
   * _Nota de corrección_: después de la corrección, la consulta de categorías de graphql devuelve categorías con permiso de permiso aunque la categoría raíz no tenga permiso de permiso.

### Catálogo, precios, ensayo y previsualización

* _ACP2E-2672_: [La nube] El punto final de la API de precio especial devuelve un error al actualizar grandes cantidades de productos simultáneamente
   * _Nota de corrección_: Ahora la API de actualización masiva de precios especiales creará una sola campaña para cada intervalo de fechas en lugar de varias actualizaciones programadas para cada producto e intervalo de fechas. Además, admitirá solicitudes de API simultáneas para un procesamiento más rápido de un gran número de SKU.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>

### Catálogo, Producto

* _AC-7050_: el árbol de selección de categorías en el producto de edición no está en el mismo orden establecido en Catálogo->Categorías
   * _Nota de corrección_: el sistema ahora muestra correctamente el árbol de selección de categorías en la sección de edición de productos en el mismo orden establecido en Catálogo->Categorías, lo que facilita la administración de productos en catálogos grandes. Anteriormente, el árbol de categorías de la sección de edición de productos se mostraba en el orden de creación de categorías, independientemente del orden de visualización establecido en Catálogo->Categorías.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36101>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36104>

### Catálogo, SEO

* _ACP2E-3653_: URL canónica incorrecta para la categoría cuando la página es > 1
   * _Nota de corrección_: anteriormente, la URL canónica para el contenido de varias páginas no funcionaba correctamente, mostrando de forma coherente la URL base. Sin embargo, una vez implementada la corrección, la URL canónica para el contenido de varias páginas ahora muestra correctamente la URL con el ID de página.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Catálogo, Buscar

* _ACP2E-2757_: los productos que no se muestran en la categoría y la búsqueda, pero los vínculos directos, funcionan
   * _Nota de corrección_: Anteriormente, el atributo personalizado Sí/No con price_* attribute_code no funciona con la indización. Después de esta corrección, el atributo personalizado Sí/No funciona según lo esperado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Nube] Error de búsqueda elástico en ciertas páginas de la categoría
   * _Nota de corrección_: Anteriormente, con el vale de configuración mencionado, cuando ponemos el precio 0 para varios productos, se producirá una excepción en la página de categoría de front-end. Después de esta corrección se aplica cuando se carga múltiples precios de producto 0 y cargamos la página de categoría en front-end, no se producirá ninguna excepción y se cargará la página de categoría correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: Error de tipo al crear el objeto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Nota de corrección_: después de la corrección, se puede crear una instancia de la clase Magento\CatalogSearch\Model\Indexer\Fulltext sin especificar $data.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [NUBE] El problema con los productos no es visible en Frontend después de guardarlo en Magento Admin
   * _Nota de corrección_: después de la corrección, los productos configurables que tengan productos secundarios con nombres largos no se perderán en la tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Catálogo, Envío

* _ACP2E-3195_: Dirección de envío vacía al realizar un pedido de un artículo del registro de regalos
   * _Nota de corrección_: anteriormente, para los elementos del registro de regalos de usuario invitado, cuando se devolvían desde la función de correo electrónico, generaba una dirección vacía en blanco, que es incorrecta para realizar un pedido. Después de aplicar esta corrección, el Registro de regalos comprueba los usuarios que han iniciado sesión o los usuarios invitados y las direcciones asignadas si existen.

### Nube

* _ACP2E-3010_: [Cloud] PHPSESSID está cambiando cada petición POST
   * _Nota de corrección_: PHPSESSID ya no se regenera en las solicitudes POST en el área de front-end para un cliente que ha iniciado sesión si la caché de L2 Redis está habilitada y el cliente se actualizó desde el back-end
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: Advertencias de generación de mapas de sitios
   * _Nota de corrección_: después de la corrección, el mapa del sitio se genera en el directorio tmp del sistema y se copia en el destino final.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

### Contenido

* _AC-10539_: [Problema] con la visualización del precio en el widget visualizado recientemente
   * _Nota de corrección_: el sistema ahora muestra correctamente el precio de los productos simples sin existencias en el widget &quot;Productos vistos recientemente&quot;, lo que garantiza la coherencia en todos los widgets y páginas de listas de productos. Anteriormente, el precio de los productos simples sin existencias no se mostraba en el widget &quot;Producto visualizado recientemente&quot; debido a una condición en las plantillas de carga de precios.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38167>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problema] Corrección tipográfica y gramatical en el archivo acl.xsd
   * _Nota de corrección_: el sistema corrige ahora un error tipográfico y gramatical en el archivo acl.xsd, lo que mejora la claridad y precisión de la documentación. Anteriormente, el archivo acl.xsd contenía un error tipográfico y una gramática incorrecta que podría causar confusión.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38061>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: la imagen del titular de Pagebuilder no es visible en la galería
   * _Nota de corrección_: el sistema ahora muestra correctamente las imágenes de banner cargadas en carpetas recién creadas en la galería de Pagebuilder, con lo que se eliminan los errores anteriores de la consola. Antes de esta corrección, las imágenes de los titulares no eran visibles en la galería si se cargaban en una carpeta nueva, lo que provocaba un error de la consola.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;No se estableció el código de área&quot; tras actualizar a 2.4.5-p8
   * _Nota de corrección_: El sistema ahora completa correctamente el proceso de implementación de contenido estático cuando el módulo Magento_CSP está habilitado y &quot;dev/js/translate_strategy&quot; está establecido en &quot;embedded&quot;, sin activar el error &quot;Código de área no establecido&quot;. Anteriormente, en estas condiciones, el proceso de implementación del contenido estático fallaba con un error de &quot;Código de área no establecido&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38845>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38922>
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
* _AC-9638_: [Problema] de carga de archivos en el editor de WYSIWYG en la página del producto
   * _Nota de corrección_: el sistema ahora muestra correctamente el árbol de carpetas y permite las cargas de imágenes en el editor de WYSIWYG en la página del producto, incluso después de expandir primero la pestaña &quot;Imagen y vídeos&quot;. Anteriormente, al expandir la pestaña &quot;Imagen y vídeos&quot; por primera vez, el árbol de carpetas no se mostraba y aparecía un mensaje de error al intentar cargar una imagen en el editor de WYSIWYG.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38026>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-PREM] Problema de bloque dinámico
   * _Nota de corrección_: los widgets se están representando correctamente en bloques dinámicos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_: La URL nocookie de YouTube no funciona en Page Builder
   * _Nota de corrección_: Ahora el generador de páginas permite la URL sin cookies de YouTube en la configuración del elemento de formulario de las reglas de validación. Anteriormente, la URL sin cookies de YouTube no funcionaba en pagebuilder.
* _ACP2E-2693_: [El front-end ] de la nube no se carga debido a un problema en la plantilla de la newsletter
   * _Nota de corrección_: agregar bloques a través de la sección de contenido de la página CMS ya no genera excepciones
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [Nube] Se encontró una excepción de investigación en el registro: InvalidArgumentException: La clase no existe en vendor/magento/module-rule/Model/ConditionFactory.php
   * _Nota de corrección_: al eliminar una condición en la configuración de contenido de los productos de PageBuilder, ya no se registrará una excepción en los archivos de registro. Anteriormente, si se eliminaba una condición en la configuración de contenido de los productos de PageBuilder, se registraba una excepción crítica en los registros, a pesar de no causar ningún problema en el front-end.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: cambiando al modo de tienda única: el contenido global ya no aparece
   * _Nota de corrección_: El sistema ahora sincroniza las configuraciones de diseño de vista de tienda con las configuraciones de diseño de sitio web al habilitar el modo de tienda única, asegurándose de que las actualizaciones de contenido sean visibles en el front-end. Anteriormente, cambiar al modo de tienda única evitaba que las actualizaciones de contenido se reflejaran en la tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: Page Builder reemplaza la imagen al intentar agregar un vínculo y otros problemas de uso.
   * _Nota de corrección_: Ahora al hacer clic en una imagen, los vínculos del editor wysiwyg del elemento de texto Page Builder cargarán los datos adecuados en la imagen y el cuadro de diálogo de configuración del vínculo. También la adición de un vínculo a una imagen en el editor ahora funciona correctamente. Anteriormente, la imagen se sustituía por un vínculo.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: La galería de medios antigua no puede procesar imágenes cuando se coloca una imagen de 0 bytes en el directorio
   * _Nota de corrección_: el sistema ahora administra imágenes de 0 bytes en la galería de medios sin interrumpir la funcionalidad, lo que permite que otras imágenes del directorio se muestren y seleccionen según lo esperado. Anteriormente, la presencia de una imagen de 0 bytes en la galería de medios impedía que se mostraran o seleccionaran todas las imágenes del directorio.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Error en el Page Builder al editar el bloque de CMS
   * _Nota de corrección_: El sistema ahora guarda correctamente los cambios realizados en el área de administración mediante Page Builder, sin arrojar el error &quot;Page Builder se estaba representando durante 5 segundos sin liberar bloqueos&quot;. en la consola del explorador. Anteriormente, este error se producía al intentar guardar los cambios, lo que impedía que el contenido se actualizara correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [NUBE] No hay botones de cierre de compra o editar el carro de compras en la sección del carro de compras
   * _Nota de corrección_: el producto del paquete ahora se agrega al carro de compras mediante widgets sin errores.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_: la vista previa de ensayo de contenido en páginas de categoría no muestra widgets de producto
   * _Nota de corrección_: el problema se ha corregido asegurándose de que las entradas de producto para la categoría adicional vinculada al bloque de CMS se hayan registrado con precisión en la base de datos. Anteriormente, devolvía un conjunto de resultados vacío cuando se solicitaba la página de vista previa de la categoría.
* _ACP2E-3122_: [NUBE] El botón Cargar imagen no funciona
   * _Nota de corrección_: Antes el botón Cargar imagen para Banner y Slider de PageBuilder no funcionaba como se esperaba y ahora al pulsarlo se abre el administrador de archivos local para seleccionar la imagen que se desea cargar.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor(): El argumento #2 ($height) debe ser mayor que 0. No se puede cargar una imagen específica
   * _Nota de corrección_: se ha resuelto el problema que provocaba errores en el administrador al cargar imágenes con una altura de 0 a través de la galería de medios y se ha realizado correctamente la sincronización de recursos mediante el comando sync. Anteriormente, no se puede cargar la imagen a través de la galería de medios y el comando de sincronización también falla cuando una imagen específica está en la galería.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from está en conflicto con la API de Google Maps
   * _Nota de corrección_: Google Maps ahora se procesa correctamente en el editor de PageBuilder. Anteriormente, un error de JavaScript impedía que Google Maps se representara correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [Nube] - El control deslizante de CMS no refleja los cambios más recientes
   * _Nota de corrección_: el problema se ha corregido asegurándose de que la lista del control deslizante se actualice mientras se activa el evento de guardado en la pantalla de edición de diapositivas. Anteriormente, se activaba y causaba el problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Se produce un error en la página CSM cuando se insertan bloques de CMS usando el generador de páginas en un orden determinado
   * _Nota de corrección_: Anteriormente en algunas versiones de PHP y OS (Linux), la representación de bloques que hacían referencia a otros bloques cms a través de PageBuilder habría fallado con un &quot;Error desconocido&quot;. Inténtelo de nuevo&quot;. Ahora el contenido de los bloques cms se representa correctamente dentro de un contenido controlado por PageBuilder.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [Los bloques dinámicos de la nube] no funcionarán correctamente
   * _Nota de corrección_: los segmentos de clientes que iniciaron sesión ahora se borran tras cerrar la sesión, lo que impide que la sesión de invitado herede los segmentos que iniciaron sesión anteriormente
* _ACP2E-3428_: Error en la vista previa de plantilla de Pagebuilder para contenido grande
   * _Nota de corrección_: el contenido grande provocaba que un elemento de lienzo desbordara los límites del explorador y devolviera un valor incorrecto, lo que rompía el código back-end (no se puede descodificar correctamente la imagen). Se corrigió al limitar el tamaño del lienzo al límite del explorador universal.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: Faltan las últimas actualizaciones de seguridad con TinyMCE 7
   * _Nota de corrección_: Los selectores de tamaño de fuente y familia de fuentes ya están disponibles en el editor de WYSIWYG. Antes de esta corrección, con TinyMCE 7 estos no estaban disponibles en la interfaz del editor.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: TinyMCE 7 editor tamaño de fuente en el administrador en PT y no PX por favor aclarar
   * _Nota de corrección_: antes de la corrección, no se podía especificar el tamaño de fuente en píxeles en las áreas de WYSIWYG. Ahora puede establecer el tamaño de fuente en píxeles en lugar de pt.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: El tipo de contenido de producto en Page Builder se contrae sin mensajes correctos
   * _Nota de corrección_: antes de la corrección, el HTML de vista previa no se generaba correctamente cuando no había productos en el widget. Ahora, la respuesta vacía se genera correctamente y el widget de productos se muestra bien en la vista previa.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [generador de páginas]Agregar una lista de productos para bloquear da como resultado errores
   * _Nota de corrección_: ahora, agregar la lista de productos agrupados al bloque a través del generador de páginas no genera errores
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/344fce23>

### Contenido, SEO

* _ACP2E-2870_: La jerarquía de páginas de CMS puede causar problemas de reescritura de URL
   * _Nota de corrección_: Anteriormente, para la reescritura de URL permanente personalizada para páginas raíz que no son de sitios web, se redireccionaba infinitamente y la página nunca se cargaba. Después de aplicar esta corrección, la reescritura de URL personalizada para la página raíz que no es de sitio web funciona según lo esperado y no se produce ningún bucle de redirección.

### Contenido, ensayo y vista previa

* _ACP2E-2979_: La regla de precio de catálogo no se muestra cuando está configurada para programarse con bloques dinámicos
   * _Nota de corrección_: el sistema ahora muestra correctamente el contenido dinámico asociado con las reglas de precios de catálogo programadas en la página de detalles del producto. Anteriormente, el contenido dinámico no se cargaba cuando se programaban las reglas de precios de catálogo.

### Cliente/ Clientes

* _AC-12162_: front-end: la validación de la fecha de nacimiento está fallando en la página de creación del cliente
   * _Nota de corrección_: Asegúrese de que toda la validación funcione después de actualizar la dependencia del sistema moment.js a la última versión secundaria
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-13060_: Segmento del cliente > Condición > Historial del producto* > &quot;El producto se ha visto&quot; no funciona
   * _Nota de corrección_: el sistema ahora muestra correctamente los clientes registrados coincidentes en la condición &quot;Se vio el producto&quot; en Segmentos de clientes, cuando se cumple la condición. Anteriormente, incluso cuando se cumplía la condición, el recuento de clientes registrados coincidentes permanecía en cero.
* _AC-8499_: el campo de texto de región no se restablece cuando se cambia la lista desplegable de países
   * _Nota de corrección_: El sistema ahora restablece el campo de texto de región cuando se cambia el país en el menú desplegable, asegurándose de que los valores anteriores no persistan. Anteriormente, al cambiar el país de la lista desplegable, no se restablecía el campo de región, lo que provocaba que se conservara el último valor guardado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: al eliminar el cliente, no se limpian todos los datos de sesión del explorador en Storefront para el cliente que inició sesión y lo eliminó
   * _Nota de corrección_: al eliminar un cliente, ahora se limpian todos los datos de sesión del explorador de la tienda para los clientes que iniciaron sesión y se eliminaron según lo esperado. El comprador puede seguir comprando y su navegador trata su sesión como una sesión de invitado. Anteriormente, cuando la cuenta de cliente de un comprador que iniciaba sesión se eliminaba del administrador, el explorador del comprador arrojaba errores de JavaScript.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>

### Marco

* _AC-10037_: [Pregunta]Configuración de tipo sin usar en `app/code/Magento/Translation/etc/di.xml`
   * _Nota de corrección_: el sistema ahora elimina las dependencias que no se usan en la configuración, lo que mejora la limpieza y eficacia general del código. Anteriormente, había dependencias no utilizadas en la configuración de que no contribuían a ninguna funcionalidad.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38030>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: pregunta/problema de extremo V1/customers/password
   * _Nota de corrección_: El sistema ahora se adhiere a las restricciones establecidas dentro de la GUI de administración al procesar solicitudes de cambio de contraseña a través de la API, lo que evita posibles abusos de la función de restablecimiento de contraseña. Anteriormente, la API podía procesar solicitudes de cambio de contraseña fuera de las reglas definidas en la GUI de administración, lo que permitía un flujo constante de correos electrónicos restablecidos si se conocían correos electrónicos válidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38238>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: la configuración del barniz no excluye todos los parámetros de marketing
   * _Nota de corrección_: el sistema ahora excluye correctamente todos los parámetros de marketing comunes en la configuración de Barniz, lo que garantiza un seguimiento y análisis precisos. Anteriormente, no se excluían ciertos parámetros de marketing como gad_source, srsltid y msclkid, lo que producía posibles imprecisiones en la recopilación de datos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38298>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: proceso de indexación de error del índice de búsqueda del catálogo
   * _Nota de corrección_: El sistema ahora completa correctamente el comando de reindexación sin encontrar ningún error, independientemente de la versión de libxml compilada con PHP. Anteriormente, la ejecución del comando re-index resultaba en un error &quot;Error del proceso de índice de búsqueda en el catálogo durante el proceso de indexación&quot; cuando PHP se compilaba con ciertas versiones de libxml.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38254>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: se agregaron los filtros created_at, status y grand_total a la consulta de pedidos de clientes y se corrigió un error de varios filtros
   * _Nota de corrección_: el sistema ahora admite el uso de los filtros created_at, status y grand_total en las consultas de pedidos de clientes y ha resuelto un problema en el cual no se aplicaban correctamente varios filtros. Anteriormente, el sistema no admitía estos filtros y no podía aplicar todos los filtros cuando se utilizaba más de uno en una consulta.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38392>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: se inunda aleatoriamente con consultas de bloques relacionados/de ampliación de venta/venta cruzada e indexación de precios
   * _Nota de corrección_: El sistema ahora optimiza las consultas de bloques relacionados, de ventas adicionales y de ventas cruzadas, lo que mejora el rendimiento y evita que el sitio se cierre debido a consultas excesivas. Anteriormente, el sistema podía sobrecargarse con consultas de estos bloques, lo que provocaba ralentizaciones significativas y la posibilidad de derribar el sitio.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36667>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Excepción: Advertencia: Intentando obtener acceso al desplazamiento de la matriz en... -> Calendar.php desde la actualización a ICU 74.1 (PHP Intl)
   * _Nota de corrección_: Commerce ya no registra la siguiente excepción en exception.log cada vez que un comprador o comerciante visita la tienda o el administrador: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38214>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problema] Solucionar problemas con los datos del cliente cuando el formulario contiene un elemento con el nombre `method`
   * _Nota de corrección_: El sistema ahora identifica correctamente el atributo &quot;method&quot; en los envíos de formularios, incluso cuando haya un elemento llamado &quot;method&quot; presente en el formulario. Esto garantiza un procesamiento preciso de los datos del cliente. Anteriormente, si un elemento de formulario se denominaba &quot;método&quot;, interfería con la identificación del atributo &quot;método&quot; en los envíos de formularios, lo que producía posibles problemas con la administración de datos de los clientes.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38484>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Problema] que corrige PHPDocs para \Magento\Framework\Data\Collection::getItemById
   * _Nota de corrección_: Los PHPDocs del método \Magento\Framework\Data\Collection::getItemById se han actualizado para incluir null como posible tipo de valor devuelto, solucionando los problemas con las herramientas de análisis estático. Anteriormente, los PHPDocs del método no especificaban null como posible tipo de valor devuelto, lo que daba lugar a advertencias o errores en el análisis estático cuando el método se utilizaba en afirmaciones condicionales.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38485>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38439>
* _AC-11592_: [Problema] Permitir solo las preferencias válidas durante la instalación:di:compilación
   * _Nota de corrección_: El sistema genera un error durante el comando setup:di:compile si se crea una preferencia para una clase que no existe o se excluye específicamente, asegurándose de que solo se permiten preferencias válidas. Anteriormente, estos escenarios fallaban de forma silenciosa, lo que podía inutilizar cualquier complemento asociado con las clases originales.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38517>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento está intentando modificar la propiedad de solo lectura en __ método wakeup de LoggerProxy
   * _Nota de corrección_: El sistema ahora permite la modificación de propiedades de sólo lectura anteriores en el método __wakeup de LoggerProxy, lo que garantiza un funcionamiento sin problemas sin forzar a los usuarios a emplear una solución. Anteriormente, un intento de reasignar el valor de una propiedad de solo lectura en el método __wakeup de LoggerProxy causaba problemas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38526>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_: [Problema] Referencia de TinyMCE de actualización AC-2039 AC-1667
   * _Nota de corrección_: Se ha actualizado la última versión de tinymce en composer.json.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38533>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker no funciona en varios subprocesos
   * _Nota de corrección_: el sistema ahora admite la bifurcación de procesos para la indexación MView, lo que evita errores durante la ejecución del indizador cuando se opera en varios subprocesos. Anteriormente, si se ejecutaba ChangelogBatchWalker en varios subprocesos, se eliminaban las tablas utilizadas por otros subprocesos, lo que provocaba un error durante la ejecución del indizador.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38246>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Problema] Cambiar nombre de variable con nombre incorrecto
   * _Nota de corrección_: El sistema ahora asigna un nombre correcto a la variable que contiene la cantidad de dinero que aún se puede reembolsar, lo que evita confusiones durante la depuración. Anteriormente, esta variable se denominaba incorrectamente como totalRefund, lo que podría provocar malentendidos para los desarrolladores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38609>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [Problema] Pasar atributos personalizados al vínculo actual a través de XML
   * _Nota de corrección_: el sistema ahora permite que los atributos personalizados se pasen al vínculo actual a través de XML, asegurándose de que estos atributos se muestren correctamente incluso cuando el vínculo sea la página actual. Anteriormente, los atributos personalizados no se mostraban para el vínculo de página actual debido a que el método getAttributesHtml() no se utilizaba para el vínculo actual.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38500>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/30070>
* _AC-11819_: la caché FPC integrada está dañada en la versión 2.4.7 para algunas configuraciones
   * _Nota de corrección_: El sistema ahora almacena correctamente en caché las páginas cuando se establece el parámetro MAGE_RUN_CODE, lo que garantiza un rendimiento óptimo. Anteriormente, las páginas no se almacenaban en caché en estas condiciones, lo que producía posibles problemas de rendimiento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38626>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problema] Corrija la incoherencia en la administración de excepciones entre los modos de desarrollo y producción
   * _Nota de corrección_: el sistema ahora administra de forma consistente las excepciones entre los modos de desarrollo y producción, lo que evita una redirección inesperada a la página de inicio de sesión cuando se produce una excepción. Anteriormente, una incoherencia en la gestión de excepciones podía provocar una redirección a la página de inicio de sesión en el modo de producción en lugar de mostrar el mensaje de excepción.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38639>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: reemplazar la traducción &#39;Cuenta PayPal&#39; en token_list.phtml
   * _Nota de corrección_: El sistema ahora etiqueta la sección de métodos de pago de cuentas con tokenización como &quot;Cuenta&quot; en lugar de &quot;Cuenta PayPal&quot; en la página Métodos de pago almacenados, lo que la hace más representativa de su función. Anteriormente, esta sección estaba etiquetada específicamente como &quot;Cuenta PayPal&quot;, lo que era engañoso cuando se añadían otros métodos de pago de cuentas tokenizables.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35622>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37959>
* _AC-11874_: se ha perdido la compatibilidad con versiones anteriores en la clase Magento\Catalog\Model\ProductRepository
   * _Nota de corrección_: La clase ProductRepository mantiene ahora la compatibilidad con versiones anteriores al restaurar la clase de ayuda de inicialización como el segundo parámetro, asegurándose de que los módulos que se extienden desde esta clase funcionan según lo esperado. Anteriormente, la eliminación del Asistente para la inicialización del constructor en la clase ProductRepository provocaba una pérdida de compatibilidad con versiones anteriores, lo que obligaba a los usuarios a utilizar una solución.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [Problema] Implementación de contenido estático: error de tipo
   * _Nota de corrección_: el sistema ahora gestiona correctamente los archivos LESS vacíos durante la implementación de contenido estático y muestra el mensaje de error &quot;El archivo LESS está vacío&quot;. Anteriormente, se producía un error de tipo incorrecto al encontrar un archivo LESS vacío durante la implementación.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38682>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [Problema] [Vista] eliminó espacio adicional en el vínculo y la etiqueta de script
   * _Nota de corrección_: El sistema ahora garantiza que no haya espacios adicionales en las etiquetas de vínculo y script, lo que proporciona un código más limpio y eficiente. Anteriormente, se podían encontrar espacios dobles entre atributos en las etiquetas de vínculo y script.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32920>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32919>
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
* _AC-12594_: [Problema] Use la configuración compilada para los datos generados en lugar de la configuración general
   * _Nota de corrección_: El sistema utiliza ahora la configuración compilada para los datos generados en lugar de la configuración general, lo que reduce la transferencia de red y la sobrecarga de datos que dependen de una determinada versión de código. Este cambio evita la anulación de caché en instancias compartidas durante el intercambio de contenedores, lo que conduce a una mejor estabilidad y a una reducción del tiempo de inactividad. Anteriormente, ciertas clases principales utilizaban el tipo de configuración compartida, que podía provocar la anulación de la caché o el tiempo de inactividad de la aplicación debido a diferencias en las versiones de código en varios servidores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38785>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Elimina las referencias a los archivos de extjs que se eliminaron en e1ccdb...
   * _Nota de corrección_: el sistema ahora quita las referencias a archivos de extjs que se quitaron anteriormente, lo que elimina los errores en la consola del explorador y en el archivo de registro del sistema. Anteriormente, estas referencias causaban errores debido a la ausencia de los archivos a los que se hace referencia.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38960>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [Problema] Limpieza menor: se corrigió el uso incorrecto de sprintf, solo se necesitan 2 marcadores de posición aquí y w...
   * _Nota de corrección_: el sistema ahora utiliza correctamente la función sprintf con el número adecuado de marcadores de posición, lo que mejora la limpieza y coherencia del código. Anteriormente, la función sprintf se utilizaba incorrectamente con un argumento adicional, que no causaba ningún problema importante, pero no era el uso correcto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39062>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 eliminó la extensión FTP
   * _Nota de corrección_: El sistema ahora incluye la extensión FTP como dependencia en el archivo composer.json, lo que garantiza la correcta configuración de las importaciones CSV a través de FTP. Anteriormente, se producía un error al intentar configurar las importaciones de CSV a través de FTP debido a que la extensión FTP no estaba presente en el paquete PHP.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39083>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_: [Problema] Corrige las clases incorrectas a las que se hace referencia en los módulos de Magento.
   * _Nota de corrección_: El sistema ahora hace referencia correctamente a las clases en módulos, lo que garantiza un funcionamiento más suave y evita bloqueos debido a clases no existentes. Esto incluye una corrección de errores en los módulos Indexer y CreditMemo, y la implementación de HttpGetActionInterface en la clase PrintAction. Anteriormente, las referencias de clase incorrectas provocaban errores y posibles bloqueos del sistema, y algunas funcionalidades, como el nombre de archivo de los archivos PDF de memo de crédito y la reindexación de existencias, no funcionaban según lo esperado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39126>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: capacidad para definir el área para el comando CLI `dev:di:info`
   * _Nota de corrección_: El sistema ahora permite a los desarrolladores definir un área para el comando CLI `dev:di:info`, lo que mejora el proceso de desarrollo y depuración. Anteriormente, este comando solo podía mostrar información del área GLOBAL.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38758>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [Problema] agrega la propiedad isMultipleFiles a la plantilla de elemento del formulario de imagen
   * _Nota de corrección_: esta corrección evita que el botón &quot;Buscar o arrastrar imagen aquí&quot; desaparezca cuando se agrega una imagen en un elemento de formulario de imagen de varios archivos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39219>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36325>
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
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http depende de la frase de motivo OK
   * _Nota de corrección_: se quitó la comprobación de frase &quot;OK&quot; de Magento\Framework\Filesystem\Driver\Http::isExists
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39546>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: el indizador de cuadrícula del cliente no funciona correctamente en el modo Actualizar por programación
   * _Nota de corrección_: la cuadrícula anterior del cliente se actualizó instantáneamente, pero después de la corrección, la cuadrícula del cliente se actualiza después de la ejecución de cron, pero no se refleja instantáneamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: error tipográfico en un archivo js.
   * _Nota de corrección_: El sistema ahora utiliza correctamente el término &quot;suscriptores&quot; en el archivo JavaScript, lo que garantiza la funcionalidad adecuada de las características relacionadas. Anteriormente, un error tipográfico en el archivo JavaScript provocaba el uso incorrecto del término &quot;suscriptores&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36163>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Problema] Quitar etiqueta `@author` prohibida
   * _Nota de corrección_: El sistema ahora se adhiere a los estándares de codificación al eliminar la etiqueta `@author` prohibida de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, la etiqueta `@author` estaba presente en algunos módulos, lo cual era contrario a los estándares de codificación establecidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37253>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Problema] Quitar la etiqueta `@author` prohibida de `Magento_Customer` (parte 2)
   * _Nota de corrección_: El sistema ahora se adhiere al estándar de codificación eliminando la etiqueta `@author` prohibida de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, la etiqueta `@author` estaba presente en algunos módulos, lo cual era contrario a los estándares de codificación establecidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37250>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: espacio en la sintaxis de editorconfig rompe la regla para [{composer,auth}.json]
   * _Nota de corrección_: El sistema ahora aplica correctamente una sangría de 4 espacios a los archivos composer y auth.json, después de corregir un error de sintaxis en la configuración del editor. Anteriormente, debido a un espacio en la sintaxis del editor de configuración, estos archivos tenían un formato incorrecto con una sangría de 2 espacios.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37394>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37395>
* _AC-8662_: [Problema] Mejora el registro de errores cron
   * _Nota de corrección_: El sistema ahora captura y registra tanto STDERR como STDOUT para los procesos cron, proporcionando información de diagnóstico valiosa en escenarios donde los procesos cron fallan. Anteriormente, no se registraba ningún mensaje de error en los procesos cron y se perdían STDERR y STDOUT para los grupos cron que se ejecutaban en procesos independientes.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37453>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32690>
* _AC-8984_: [Problema] Agrega más colores a la salida de ciertos comandos cli de instalación
   * _Nota de corrección_: El sistema ahora agrega más colores a la salida de ciertos comandos de la interfaz de línea de comandos (CLI) de configuración, lo que mejora la legibilidad y la experiencia del usuario. Anteriormente, el resultado de estos comandos era más difícil de leer debido a la falta de diferenciación de color.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/29335>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: la actualización de Magento restablece general/region/state_required cuando se agrega un nuevo país con el estado o la región requeridos.
   * _Nota de corrección_: El sistema ahora solo agrega el país modificado a la configuración &#39;general/region/state_required&#39; cuando se agrega un nuevo país con estados requeridos, lo que evita cualquier interrupción en el código personalizado que supone que la región está deshabilitada. Anteriormente, si se agregaba un nuevo país con estados requeridos, se restablecía la configuración &quot;general/region/state_required&quot; a los países predeterminados con un estado requerido, lo que podría romper la tienda.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37796>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Diferencia en menos compilación entre php y nodejs library (grunt) con expresiones `calc` complicadas
   * _Nota de corrección_: Corrija la diferencia en menos compilación entre la biblioteca php y nodejs (grunt) después de la actualización wikimedia/less.php:^5.x
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37841>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Error &quot;No se encontró la tabla o vista base&quot; al ejecutar la indexación parcial
   * _Nota de corrección_: el reíndice parcial ahora funciona correctamente con el registro de cambios grande en caso de conexión de base de datos secundaria
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: Problemas después de actualizar MariaDB a 10.5.1 o superior
   * _Nota de corrección_: se corrigió el problema en el que los valores datetime de una base de datos se convertirían en 0000-00-00 00:00:00 después de la actualización de Mysql
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: No coinciden los tipos en Comparación de datos al comprobar si los datos tienen cambios
   * _Nota de corrección_: anteriormente, se llamaba al objeto save cada vez sin ningún cambio de datos (para cualquier campo de datos numéricos, como int/float/double). Déclencheur el indicador _hasDataChanges para que sea true y llama a la función de guardado. Después de aplicar esta corrección, la función de guardado solo llamará si se cambian los datos. El valor de datos para int/float/double-check con el valor pasando a la función y hace una estricta coincidencia de tipos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: La importación de [Cloud] no se puede usar con la variable de directorio
   * _Nota de corrección_: el producto se puede importar correctamente independientemente del nombre de archivo.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: En ipad mini, el menú y el encabezado se cargan como móviles; en su lugar, deberían cargarse como escritorio.
   * _Nota de corrección_: El sistema ahora trata los dispositivos con una anchura de 768 píxeles como escritorio, asegurándose de que el menú y el encabezado se carguen correctamente. Anteriormente, los dispositivos con una anchura de 768 píxeles se trataban como móviles, lo que provocaba que el menú y el encabezado se cargaran en una vista móvil.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_: Error de tabla base o vista no encontrada al ejecutar mview cron mientras se tenía una operación DDL
   * _Nota de corrección_: el sistema ahora administra correctamente las operaciones de actualización de la base de datos mientras la actualización de mview se ejecuta en segundo plano, lo que evita que se produzcan errores de &#39;Tabla base o vista no encontrada&#39;. Anteriormente, algunas operaciones de actualización de la base de datos podían provocar el error &quot;Tabla base o vista no encontrada&quot; si la actualización de mview se ejecutaba al mismo tiempo.
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
* _ACP2E-3537_: Las entradas de clave de caché correspondientes no están disponibles en las etiquetas de caché, por lo que la limpieza de caché no funciona correctamente
   * _Nota de corrección_: el modo LUA ahora está habilitado de forma predeterminada para el recolector de elementos no utilizados de caché de Redis para evitar condiciones de carrera
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: Se omite el valor MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK
   * _Nota de corrección_: después de la corrección, una variable ENV establecida en &quot;false&quot; se tratará como bool false, no como cadena &#39;false&#39;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Marco de trabajo, GraphQL

* _AC-7976_: [Problema] introdujo la compatibilidad con tipos escalares personalizados para el esquema de GraphQL
   * _Nota de corrección_: el sistema ahora admite tipos escalares personalizados para el esquema de GraphQL, lo que permite a los desarrolladores definir tipos escalares personalizados e implementaciones. Esta función puede resultar especialmente útil para expresar valores que pueden requerir validación, como HTML, correos electrónicos, URL, fechas, etc., y para casos más avanzados como atributos EAV. Anteriormente, el sistema no admitía el procesamiento de tipos escalares personalizados en GraphQL.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36877>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Marco, producto

* _AC-13011_: 2.4.8-beta1 EE Los informes no se están generando debido a una excepción de Magento

### Marco, marco de IU

* _ACP2E-3324_: Posibilidad de sobrescribir el valor de configuración aunque esté bloqueado
   * _Nota de la corrección_: Anteriormente a esta corrección, la configuración del diseño no se podía establecer mediante el comando bin/magento config:set y los valores bloqueados se podían cambiar manipulando el formulario que los mostraba. Después de la corrección, los valores bloqueados establecidos desde cli con —lock-env o —lock-conf ya no se pueden actualizar.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_: Magento_GraphQl ejecuta el procesamiento de encabezados aunque el valor del encabezado no pase la validación
   * _Nota de corrección_: El sistema ahora garantiza que el procesamiento del encabezado se ejecute solo una vez y solo si el valor del encabezado pasa la validación, lo que mejora la seguridad y evita posibles vulnerabilidades. Anteriormente, el procesamiento del encabezado se ejecutaba incluso si el valor del encabezado no pasaba la validación, lo que producía posibles vulnerabilidades y comportamientos inesperados debido al doble procesamiento de los valores del encabezado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: las opciones de la tarjeta regalo física no tienen el orden de clasificación correcto
   * _Nota de corrección_: El sistema ahora ordena correctamente las opciones de los productos de tarjetas de regalo físicos cuando se consultan a través de GraphQL, lo que garantiza una representación coherente con el tema de Luma. Anteriormente, el criterio de ordenación era incorrecto según la temática de luma, lo que provocaba una visualización y un orden incorrectos de opciones como el nombre del remitente, el nombre del destinatario y la cantidad.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: La caché de resolución de [GraphQL] se invalida al crear, editar, mover o eliminar una actualización de ensayo
   * _Nota de corrección_: El sistema ahora garantiza que la caché de resolución no se invalidará al crear, editar, mover o eliminar una actualización de ensayo, sino únicamente cuando la actualización de ensayo se aplique a la entidad. Anteriormente, la caché del solucionador se invalidaba prematuramente, incluso antes de que se aplicara la actualización de ensayo, lo que provocaba invalidaciones de caché innecesarias.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: La caché de Fastly no se ha borrado para la actualización del ensayo de contenido
   * _Nota de corrección_: Ahora GraphQL con la memoria caché de respuestas de contenido de PageBuilder se invalida cuando se actualizan las entidades relacionadas con contenido de PageBuilder.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Desactivación del desplazamiento por capas - No se elimina la agregación de Graphql
   * _Nota de corrección_: el problema se ha corregido después de aplicar la comprobación al solicitar una búsqueda de productos con agregaciones de categorías a través de una consulta de GraphQL cuando la configuración de administración establece &quot;Catálogo > Navegación por capas > Mostrar filtro de categorías&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: La llamada de productos GraphQL que contiene el filtro de precios {from:&quot;0&quot;} no devuelve ningún resultado
   * _Nota de corrección_: Anteriormente, la búsqueda de productos de graphql con el filtro de precios cero no arrojaba ningún resultado debido a una excepción generada. Ahora la búsqueda devuelve los resultados según lo esperado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: las traducciones de los atributos devueltos por el cliente no se reflejan en la API de GraphQL para el StoreView correspondiente
   * _Nota de corrección_: las traducciones para atributos de devolución del cliente se reflejan en la API de GraphQL para el StoreView correspondiente.
Anteriormente, los atributos de retorno de los clientes para las respectivas vistas de tienda no se reflejaban en la API de GraphQL.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [La nube] ha interrumpido la llamada de GraphQL para getPurchaseOrder con el presupuesto del nodo
   * _Nota de corrección_: La llamada de GraphQL de la orden de compra podrá ejecutar la tarea sin encontrar errores internos del servidor.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Los productos configurables de la nube] no se muestran en el sitio de producción si el producto no está habilitado en &quot;Todas las vistas de la tienda&quot;
   * _Nota de corrección_: el sistema ahora muestra correctamente los productos configurables en el sitio aunque el producto no esté habilitado en &quot;Todas las vistas de tienda&quot;, pero esté habilitado en ámbitos específicos de las vistas de tienda.
Anteriormente, si un producto estaba deshabilitado en &quot;Todas las vistas de tienda&quot; y habilitado solo en ámbitos específicos de vista de tienda, los atributos del producto no se mostraban correctamente en la respuesta de GraphQL, lo que provocaba que el producto no se mostrara correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [Cloud] productos graphql con error cuando el mismo producto simple se ha asignado a varios productos configurables
   * _Nota de corrección_: Anteriormente, con productos configurables independientes con el mismo producto simple, GraphQL devuelve un error. Después de aplicar esta corrección, diferentes productos configurables con el mismo producto simple, grapQL devuelve el resultado sin ningún error.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [Nube] problema con autenticación de usuarios y acceso de tokens entre sitios en la configuración de varios sitios
   * _Nota de corrección_: Las consultas de Información del cliente y del carro de compras de GraphQl en la configuración de varios sitios comprueban si existe el cliente en un sitio web no predeterminado.
Anteriormente, la consulta funcionaba sin asegurarse de que el cliente existe en un sitio web no predeterminado en la configuración de varios sitios.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: la paginación de elementos V2 del carro de compras de GraphQL no funciona correctamente
   * _Nota de corrección_: el problema se ha corregido pasando el valor correcto para el argumento de la página actual en la consulta de colección. Anteriormente, se pasaba un valor incorrecto para establecer la página actual, lo que provocaba el problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
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
* _ACP2E-3492_: [Nube] Problemas con la API de Graphql
   * _Nota de corrección_: antes de la corrección mediante el servidor de aplicaciones Graphql, la solicitud de dirección del cliente no devolvía los datos más recientes.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: El producto deshabilitado sigue apareciendo en los elementos relacionados, de ampliación de venta y de venta cruzada en la consulta de GraphQL
   * _Nota de corrección_: Graphql ahora proporciona una respuesta correcta para los productos relacionados, ampliados y vendidos cruzados deshabilitados
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [NUBE]: Error de GraphQl Error interno del servidor placeOrder mutation
   * _Nota de corrección_: La mutación &quot;placeOrder&quot; con información de código de cupón en la solicitud ya no produce una excepción de error interno; el pedido se realizó correctamente. Anteriormente, fallaba con &quot;Error interno del servidor&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: el porcentaje de descuento no se calcula para los productos agrupados con precio dinámico
   * _Nota de corrección_: La corrección agregada para el argumento de porcentaje de descuento de product.price_details no muestra el valor correcto para los productos agrupados con el precio dinámico habilitado y el cupón de descuento aplicado.
* _LYNX-485_: el paquete de productos todavía muestra &quot;IN_STOCK&quot; cuando uno de sus paquetes está agotado
   * _Nota de corrección_: se ha resuelto el problema por el que los productos agrupados seguían mostrando &quot;IN_STOCK&quot; incluso cuando uno de sus productos agrupados estaba agotado.
* _LYNX-486_: not_available_message y only_x_left_in_stock no muestra el mismo stock disponible
   * _Nota de corrección_: se ha resuelto el problema por el que not_available_message y only_x_left_in_stock mostraban una disponibilidad de existencias incoherente
* _LYNX-488_: el campo original_row_total devuelve un valor incorrecto
   * _Nota de corrección_: se ha resuelto el problema con el campo original_row_total, que devolvía valores incorrectos cuando se seleccionaron las opciones personalizadas
* _LYNX-503_: la miniatura del producto agrupado debe mostrarse según la configuración     .
   * _Nota de corrección_: se ha resuelto el problema para garantizar que la miniatura del producto agrupado se muestre según los valores de configuración
* _LYNX-510_: error al consultar selected_options en OrderAddress
   * _Nota de corrección_: se ha actualizado AttributeSelectedOptions a custom_attributesV2 en la respuesta de GraphQL de la dirección de pedido.
* _LYNX-512_: original_item_price no incluye descuentos
   * _Nota de corrección_: se ha actualizado original_item_price para incluir descuentos.
* _LYNX-530_: el mensaje no disponible no muestra la cantidad de inventario disponible
   * _Nota de corrección_: se ha resuelto el mensaje de error y el código de error de la mutación AddProductsToCart para alinearlos con la configuración del mensaje &quot;no disponible&quot;
* _LYNX-532_: el estado &quot;OUT_OF_STOCK&quot; vuelve a aparecer en Simple con productos de opciones personalizadas con opciones de selección múltiple
   * _Nota de corrección_: se ha actualizado el solucionador StockStatusProvider en el paquete de inventario para corregir stock_status de productos simples con opciones personalizadas.
* _LYNX-533_: error (GQL): cart.itemsV2.items.product.custom_attributesV2 devuelve un error de servidor
   * _Nota de corrección_: se ha resuelto el error del servidor que se producía cuando una consulta del carro de compras incluía atributos personalizados de un producto al agregar un producto sin atributos personalizados.
* _LYNX-536_: pedidos/date_of_first_order siempre devuelven un valor nulo
   * _Nota de corrección_: se ha resuelto el problema por el que pedidos > date_of_first_order siempre devolvía un valor nulo.
* _LYNX-544_: el cliente no debe poder cancelar un pedido enviado parcialmente
   * _Nota de corrección_: se ha agregado validación para impedir que los clientes cancelen un pedido enviado parcialmente.
* _LYNX-548_: códigos de error para la cancelación de pedidos basados en el mensaje de error
   * _Nota de corrección_: Los códigos de error para la cancelación de pedidos ahora se basan en el mensaje de error específico.
* _LYNX-581_: retroceda las propiedades relacionadas con cookies de privadas a protegidas
   * _Nota de corrección_: revierte la visibilidad de las propiedades del constructor de clases de Magento\Framework\App\PageCache\Version de privada a protegida
* _LYNX-600_: aumente la complejidad máxima predeterminada de las consultas de GraphQL a 1000
   * _Nota de corrección_: se ha aumentado la complejidad máxima predeterminada de la consulta de GraphQL de 300 a 1000.
* _LYNX-620_: GQL - itemsV2 > Total de fila original, los precios del rango de precios se devuelven como $0.00 para el producto descargable con opciones de archivo que tiene precios separados.
   * _Nota de corrección_: se ha resuelto un problema en el que los productos descargables con las opciones de compra de vínculos independientes habilitadas devolvían 0 $ para itemsV2 > Total de fila original; el intervalo de precios devuelto era 0,00 $ para los productos con opciones de archivo con precios independientes.
* _LYNX-711_: el esquema de una tabla cuando se crea una nueva es diferente al actualizar
   * _Nota de corrección_: se ha resuelto un problema por el que al agregar una nueva columna VARCHAR a una tabla existente se producían errores de prueba debido a diferencias de esquema entre instalaciones nuevas y actualizaciones. El método modifyColumn() ahora gestiona correctamente las columnas VARCHAR al establecer el conjunto de caracteres y la intercalación predeterminados.
* _LYNX-772_: compatibilidad de GraphQl para la versión PHP-8.4
   * _Nota de corrección_: se corrigieron problemas de compatibilidad de GraphQL con PHP 8.4 en varios solucionadores, lo que garantiza una funcionalidad sin problemas. Se han actualizado los archivos afectados en los módulos CatalogRule, Customer, GiftMessage, GiftCard y GiftWrapping.

### GraphQL, inventario/MSI

* _ACP2E-2607_: La mutación MergeCart genera una excepción cuando los carros de compras de origen y destino tienen los mismos elementos de paquete
   * _Nota de corrección_: &#39;-
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, inventario/MSI, rendimiento

* _ACP2E-1716_: Sitio inactivo después de la actualización
   * _Nota de corrección_: se ha mejorado el rendimiento de recuperar productos agrupados mediante GraphQl.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, Rendimiento

* _AC-9569_: [GraphQL Resolver] Los datos de Customer Resolver no se han invalidado en la importación
   * _Nota de corrección_: la memoria caché de GraphQL Customer Resolver ahora se invalida como se espera cuando se edita o elimina un cliente mediante importaciones. Anteriormente, la caché no se invalidaba y los datos del cliente se podían editar o eliminar durante la importación.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Buscar

* _ACP2E-2809_: La ordenación de la lista de productos de GraphQL por varios parámetros no funciona
   * _Nota de corrección_: La ordenación de productos por varios campos en GraphQl ahora funciona como se describe en la documentación
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_: la consulta de GraphQL de listado de productos está limitada únicamente a total_count 10.000 productos
   * _Nota de corrección_: después de la corrección, el resultado de la búsqueda no se limita a 10000 productos, es posible obtener todos los productos que coincidan con los criterios de búsqueda aunque el recuento sea superior a 10000.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, marco de prueba

* _ACP2E-3363_: Error en la prueba de integración de Magento\GraphQl\App\GraphQlCustomerMutationsTest.php
   * _Nota de corrección_: &#39;-
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importación/exportación

* _AC-12172_: Problema en la importación del producto cuando se proporciona con opciones personalizadas-tipo: archivo (el producto creado no contiene precio para la opción personalizada y muestra solo la primera extensión de tipo de archivo proporcionada)
   * _Nota de corrección_: el sistema ahora importa correctamente los datos del producto con opciones personalizadas de tipo &#39;archivo&#39;, asegurándose de que se muestren todas las extensiones de archivo proporcionadas y de que se incluya el precio de la opción personalizada. Anteriormente, durante la importación del producto, si se proporcionaba una opción personalizada de tipo &quot;archivo&quot; con más de una extensión de archivo, solo se mostraba la primera extensión y faltaba el precio de la opción personalizada.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38805>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Tiempo de ejecución incorrecto para la operación de importación en la cuadrícula Historial de importación
   * _Nota de corrección_: el tiempo de ejecución del informe de importación se muestra correctamente independientemente de la configuración regional del administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Se están creando clientes duplicados con la misma dirección de correo electrónico mediante la importación
   * _Nota de corrección_: se actualiza la importación del cliente mientras la cuenta compartida está establecida en Global, el cliente importado que existe en el sistema.
Se ha duplicado el cliente importado anteriormente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Agregar/actualizar importación en productos duplicando opciones personalizables
   * _Nota de corrección_: el problema se ha resuelto asignando el almacén correcto a las opciones de productos durante las importaciones de CSV de opciones de productos.
Anteriormente, se asignaba al almacén de administración en lugar de a su respectivo almacén.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: Fecha &quot;created_at&quot; del cliente no convertida a la zona horaria de almacenamiento tras la exportación
   * _Nota de corrección_: Un valor de fecha &quot;created_at&quot; de columna se convierte al formato de fecha adecuado basado en la zona horaria de tienda en la sección CSV de exportación del cliente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Nube] Error al comprobar los datos de importación mediante CSV
   * _Nota de corrección_: no hay ningún error al comprobar los datos durante la importación de CSV. Anteriormente, se mostraba el mensaje de error: &quot;No podemos encontrar un cliente que coincida con este correo electrónico y código de sitio web en la fila o filas: 1&quot; al comprobar los datos en la sección de importación con CSV del administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_: Falta el botón Importar
   * _Nota de corrección_: resuelva el problema de falta del botón Importar después de comprobar los datos con registros correctos e incorrectos en el CSV. Anteriormente, el botón de importación no se muestra después de la comprobación de datos con registros correctos e incorrectos en el CSV.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: no se puede importar la dirección de cliente exportada
   * _Nota de corrección_: la importación de direcciones de clientes se realizará según lo esperado. Anteriormente, un archivo de importación de direcciones de clientes no pasaba la validación si Compartir cuentas de clientes = Global y hay dos sitios web en los que el sitio web predeterminado tiene una lista de países restringidos y la dirección que se importa es para otro sitio web en el que los países permitidos son diferentes
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [Nube] La cantidad incorrecta en el archivo CSV no produjo error
   * _Nota de corrección_: Ahora la importación de orígenes de existencias generará un error de validación para los valores no numéricos de la columna de cantidad. Anteriormente, al importar orígenes de stock con valores no numéricos en la columna de cantidad, la cantidad se establecía en 0.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: mensaje de error de clave URL duplicado generado al importar un producto no es correcto cuando la clave URL ya pertenece a una categoría
   * _Nota de corrección_: se muestra el mensaje de error correcto durante la comprobación de la importación del producto, cuando el cliente intentó importar el producto cuando la clave de dirección URL del producto ya pertenece a una categoría.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: La exportación de productos causa OOM incluso con límite de memoria 4G
   * _Nota de corrección_: antes de esta corrección, la exportación del producto fallaba si los atributos del producto tenían miles de valores de opción incluso con memoria disponible 4G. Después de esta corrección, la exportación del producto debe terminar de exportar el archivo CSV.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [Procesos de importación de la nube] que se interfieren entre sí
   * _Nota de corrección_: los mensajes correctos se muestran si el mismo usuario administrador realiza dos o más operaciones de importación utilizando la misma sesión de usuario.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>

### Importación/exportación, Rendimiento

* _ACP2E-3476_: El tiempo de importación del producto de [Cloud] ha aumentado significativamente
   * _Nota de corrección_: antes de la corrección, la importación de productos del catálogo con más de 10 000 entradas experimentaba una degradación del tiempo significativa. Después de la corrección, la importación del producto del catálogo se ejecuta de manera oportuna.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/87d012e5>

### Instalar y administrar

* _AC-13242_: la actualización de Magento falla en MariaDB 11.4 + 2.4.8-beta1
   * _Nota de corrección_: la actualización debe realizarse sin errores.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: No hay exportación de VCL para el botón Barniz 7 en el panel de administración
   * _Nota de corrección_: Se agregó el botón &quot;Exportar VCL para Barniz 7&quot; al Panel de administración.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventario/MSI

* _AC-10750_: Error en la actualización de inventario del producto configurable cuando la base de datos usa prefijos
   * _Nota de corrección_: El sistema actualiza correctamente el inventario de productos configurables cuando la base de datos utiliza prefijos, lo que evita mensajes de error y garantiza que se guarde la cantidad correcta. Anteriormente, se producía un error al intentar guardar la cantidad de inventario para productos simples dentro de un producto configurable si la base de datos utilizaba prefijos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: la clave de la API de Google de Google no funciona al agregar un mapa con atributos
   * _Nota de corrección_: el sistema ahora admite la última versión 3.56 de la API de Google Maps, lo que permite a los usuarios agregar correctamente un bloque de contenido de mapa del menú PageBuilder al escenario sin encontrar ningún error. Anteriormente, los usuarios no podían agregar un bloque de contenido de mapa debido a problemas de compatibilidad con la versión de la API de Google Maps, lo que provocaba un mensaje de error &quot;Se ha producido un error&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: no se puede crear el envío para el artículo de pedido con varios orígenes y SKU dañado
   * _Nota de corrección_: Anteriormente, cuando se agregaban espacios por error en el código de artículo a través de la base de datos, se producía un error en la página de envío que ahora está corregida y el recorte automático se considera un error descriptivo y no se encontró ningún impacto. Por lo tanto, el envío se creó correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [Prueba] Paquete de productos con 0 inventario en la tienda
   * _Nota de corrección_: el producto del paquete no se muestra en los sitios web adicionales que usan existencias adicionales.
* _ACP2E-2794_: [Nube] problema crítico con la lista de productos con espacios vacíos
   * _Nota de corrección_: el sistema ahora muestra correctamente las listas de productos sin espacios vacíos cuando los productos están configurados en &#39;Agotado&#39;, lo que garantiza una presentación coherente y precisa de los productos disponibles. Anteriormente, si se establecía un producto en &quot;Agotado&quot;, aparecía un espacio vacío en la lista de productos, lo que afectaba al diseño y podía confundir a los clientes.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: No se puede enviar el pedido cuando el almacén de recogida MSI está habilitado
   * _Nota de corrección_: se ha mejorado el rendimiento de inventario de la creación de envíos en caso de que haya muchas fuentes con recogida en la tienda
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: el reíndice de Cron no puede actualizar la disponibilidad del producto en el front-end
   * _Nota de corrección_: anteriormente, los productos permanecían sin existencias en el front-end después de actualizar el estado del pedido pendiente a través de la API de REST. Ahora, después de actualizar el estado del pedido pendiente mediante la API de REST, los productos se muestran como en stock.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: La adición de imágenes a configurables no funciona cuando MSI está habilitado.
   * _Nota de corrección_: la carga de imágenes para el producto configurable ahora funcionará como se espera cuando se utilice el módulo de inventario. Anteriormente, la carga de imagen no funcionaba
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: Problema con el producto del paquete + MSI en Clean M2.4.7-p3
   * _Nota de corrección_: anteriormente, para los productos del paquete de inventario después de la duplicación con el mismo producto simple, el producto simple no se puede guardar. Después de aplicar esta corrección, el producto simple se puede guardar correctamente sin excepciones.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39358>
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/0208e433>

### Inventario / MSI, búsqueda

* _ACP2E-3413_: Todos los productos están indexados con [is_out_of_stock] = 1 cuando el SKU no está establecido como atributo en el que se puede buscar
   * _Nota de corrección_: después de la corrección, el valor &quot;is_out_of_stock&quot; en el índice de búsqueda del catálogo es correcto, incluso cuando no se puede buscar en el SKU.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/5b21b7af>

### Pedido

* _AC-10828_: pantalla de información general del pedido back-end: la cantidad no satisfecha no es visible en el nivel de artículo de pedido
   * _Nota de corrección_: El sistema ahora muestra el número de artículos no pedidos en la columna de cantidad en la pantalla de información general del pedido back-end. Esto garantiza que los usuarios puedan realizar un seguimiento preciso del estado de todos los elementos de un pedido. Anteriormente, la columna de cantidad solo mostraba el número de artículos pedidos, facturados y enviados, pero no mostraba el número de artículos no pedidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38252>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] se usó un identificador de almacén incorrecto en el procesador de direcciones de pedidos
   * _Nota de corrección_: El sistema ahora utiliza correctamente el identificador de almacén asociado a un pedido al procesar la dirección del pedido, asegurándose de que las direcciones tengan el formato correcto de acuerdo con su respectivo identificador de almacén. Anteriormente, el sistema utilizaba incorrectamente el ID de tienda actual, lo que podía provocar un formato de dirección incorrecto en los casos en que era necesario enviar varios correos electrónicos de pedidos de diferentes tiendas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38412>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: problema de almacenamiento en caché JoinProcessor
   * _Nota de corrección_: El sistema ahora aplica correctamente JoinProcessor para cada iteración, incluso con llamadas consecutivas, lo que garantiza una recuperación de datos precisa. Anteriormente, JoinProcessor se marcaba incorrectamente como ya aplicado en iteraciones consecutivas, lo que producía errores en la recuperación de datos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/27504>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Problema] Precio de envío que se muestra diferente en el PDF impreso
   * _Nota de corrección_: el sistema ahora muestra correctamente los precios de envío en PDF impresos según la configuración de impuestos, lo que garantiza la coherencia entre la página de vista de facturas de pedidos de venta y la factura impresa. Anteriormente, el precio de envío mostrado en el PDF impreso excluía impuestos, independientemente de la configuración de impuestos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38608>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_: reordene con un producto configurable principal eliminado
   * _Nota de corrección_: ahora, al reordenar con el producto eliminado, el sistema no mostrará el botón de reordenar para reordenar
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39568>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Problema] Corrección incorrecta \Magento\Sales\Model\Order\Email\Container\Template::$id propiedad
   * _Nota de corrección_: Esto corrige el phpdoc incorrecto para \Magento\Sales\Model\Order\Email\Container\Template::$id, en realidad $id es type int pero en realidad es string.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39151>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: No se pueden guardar los cambios en el número de teléfono en los detalles de pedido existentes
   * _Nota de corrección_: Ahora el usuario puede agregar el prefijo internacional 00 en el campo de teléfono de la dirección de pedido
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38201>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: No se pueden enviar los correos electrónicos
   * _Nota de corrección_: El sistema ahora incluye una opción de configuración async_sending_tries para especificar el número de intentos de enviar un correo electrónico antes de detenerse, lo que mejora el manejo de los envíos de correo electrónico con errores cuando se habilita &quot;Envío asincrónico&quot;. Anteriormente, si un correo electrónico no se enviaba, el sistema intentaba reenviarlo continuamente, lo que daba como resultado un bucle interminable de mensajes de error en el registro del sistema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: El estado del pedido de [Cloud] cambió a completo cuando se reembolsa parcialmente un pedido enviado parcialmente
   * _Nota de corrección_: al emitir un abono, el estado del pedido ya no cambia a &quot;completado&quot; si hay artículos que aún no se han enviado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] no puede deshabilitar el envío de correos electrónicos desde la interfaz de usuario del administrador como muestran los documentos de desarrolladores
   * _Nota de corrección_: el sistema evita ahora correctamente que se envíen correos electrónicos de ventas cuando se deshabilita la comunicación por correo electrónico. Estos correos electrónicos ya no se enviarán cuando se vuelva a habilitar la comunicación por correo electrónico. Anteriormente, los correos electrónicos de ventas iniciados mientras la comunicación por correo electrónico estaba desactivada se enviaban una vez que se volvía a habilitar.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Pedido cerrado sin reembolso completo
   * _Nota de corrección_: El sistema ahora mantiene correctamente el estado del pedido como &#39;Procesando&#39; y el estado de la factura como &#39;Pendiente&#39; cuando un pedido con un pago no capturado tiene un envío creado. Esto garantiza que los pedidos solo se marquen como &quot;Cerrados&quot; después de ser reembolsados por completo. Anteriormente, si se creaba un envío para un pedido con una factura pendiente, el estado del pedido se cambiaba incorrectamente a &#39;Cerrado&#39;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Nube] No se puede crear un pedido en administración en un almacén si solamente no se configuró la dirección de facturación predeterminada
   * _Nota de corrección_: Ahora existe un mensaje de error relevante &quot;Ya existe un cliente con la misma dirección de correo electrónico en un sitio web asociado&quot;. se muestra si un cliente no tiene una dirección de facturación predeterminada e intenta crear un pedido en otra tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Se han enviado solicitudes de pedidos de lugares duplicadas por el administrador
   * _Nota de corrección_: anteriormente, se podía hacer clic en el botón &quot;Enviar pedido&quot; en el panel de administración varias veces o activarlo presionando repetidamente la tecla &quot;Intro&quot;, lo que provocaba envíos duplicados o de pedidos con errores. Ahora, evita acciones adicionales hasta que la solicitud se procese por completo, lo que garantiza que solo se envíe una solicitud.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: El administrador aún puede hacer el pedido incluso sin el método de pago
   * _Nota de corrección_: el método de pago seleccionado anteriormente ahora se conserva cuando el método de pago vuelve a aparecer en la lista de pagos disponibles.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3518_: Los elementos se duplican después de que creamos un pedido del administrador en - Mozilla Firefox navegador
   * _Nota de corrección_: los productos agregados mediante &quot;Agregar productos por SKU&quot; ya no se duplican en Firefox al crear un pedido en la administración.

### Pedido, Pagos

* _ACP2E-3233_: El administrador aún puede hacer el pedido incluso sin el método de pago
   * _Nota de corrección_: anteriormente, el comerciante podía realizar pedidos desde el panel de administración sin seleccionar un método de pago. Ahora, el comerciante necesita un método de pago para proceder a realizar un pedido.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Pedido, Devoluciones

* _ACP2E-2982_: El reembolso del pedido genera un abono duplicado
   * _Nota de corrección_: emitir el reembolso a través de la API de REST cuando se ejecutaron simultáneamente dos solicitudes idénticas dejará de crear notas de abono duplicadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Pedido, Impuesto

* _ACP2E-3003_: [NUBE] Base_row_total incorrecto en la API de pedido RESTFUL al habilitar transacciones internacionales y aplicar descuentos de cupones
   * _Nota de corrección_: Ahora se devuelve el total base_row_correcto desde la API de pedidos RESTFUL cuando se habilita la transacción internacional y se aplica el descuento de cupones.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### Otros

* _PAQUETE-3394_: [Braintree] reembolsa la transacción de almacenamiento en línea como transactionid-return
* _PAQUETE-3421_: pedidos de [Braintree] + [CLOUD] Braintree (tarjeta de crédito) no pueden dividir los cargos
* _BUNDLE-3422_: [Braintree] [Cloud]El certificado SSL de Braintree caduca el 30 de junio
* _LYNX-339_: se devolvió la cookie private_content_version en las consultas GQL
   * _Nota de corrección_: se ha corregido un problema por el que la cookie private_content_version se devolvía en consultas de GraphQL, incluso cuando la cookie de sesión estaba deshabilitada. La cookie ya no se incluye en las respuestas de GraphQL cuando la sesión está desactivada, como se espera.
* _LYNX-366_: error del servidor en props de correo electrónico en consultas de tarjetas de regalo físicas
   * _Nota de corrección_: se ha corregido un problema por el que las consultas de sender_email y recipient_email en tarjetas de regalo físicas generaban un error del servidor. Estas props ahora se devuelven correctamente para las tarjetas de regalo virtuales y el comportamiento de la consulta es coherente.
* _LYNX-380_: el atributo is_available en CartItemInterface siempre devuelve false para los productos configurables
   * _Nota de corrección_: se ha corregido un problema por el que el atributo is_available de CartItemInterface siempre devolvía false para los productos configurables en existencias. Ahora, refleja correctamente la disponibilidad como verdadera cuando corresponde.
* _LYNX-382_: el atributo is_available en CartItemInterface devuelve true incluso cuando el stock vendible es menor que la cantidad del producto
   * _Nota de corrección_: se corrigió un problema por el que el atributo is_available de CartItemInterface devolvía incorrectamente true incluso cuando la cantidad de artículos del carro de compras superaba el stock vendible.
* _LYNX-395_: el atributo only_x_left_in_stock de ProductInterface no es preciso en los productos configurables
   * _Nota de corrección_: se ha corregido un problema por el que el atributo only_x_left_in_stock de ProductInterface no reflejaba con precisión el stock disponible para las variantes de producto configurables en el carro de compras. Ahora, el valor only_x_left_in_stock corresponde correctamente a los niveles de stock de variante reales, lo que garantiza que se devuelvan datos de inventario precisos en la consulta GQL del carro de compras.
* _LYNX-399_: la miniatura del marcador de posición se devuelve cuando se agrega un producto simple al carro de compras dentro de un producto agrupado
   * _Nota de corrección_: se corrigió un problema por el que al agregar un producto simple (parte de un producto agrupado) al carro de compras se devolvía una imagen en miniatura de marcador de posición, incluso cuando el producto tenía una imagen asignada.
Detalles de la corrección:
* La miniatura del producto ahora muestra correctamente la imagen asignada si está disponible.
* La selección de miniaturas respeta la configuración de administración en:
Tiendas > Configuración > Ventas > Cierre de compra > Carro de compra > Imagen de producto agrupada.
Esto garantiza un comportamiento de miniaturas coherente para los productos agrupados en función de la configuración de la tienda.
* _LYNX-400_: los atributos de opción personalizados del cliente no funcionan con valores enteros
   * _Nota de corrección_: se corrigió un problema en el que los atributos de opción personalizados del cliente no funcionaban cuando el valor devuelto era un número entero. Las opciones personalizadas ahora administran correctamente y devuelven valores enteros como se espera.
* _LYNX-402_: error interno del servidor al intentar obtener priceDetails para productos en paquete con precio dinámico
   * _Nota de corrección_: se ha resuelto un problema por el que al consultar price_details para productos agrupados con precios dinámicos a través de GraphQL se producía un error interno del servidor. Esta mejora garantiza consultas de carro estables al trabajar con productos de paquete configurados con precios dinámicos.
* _LYNX-403_: only_x_left_in_stock siempre devuelve 0 para los productos configurables
   * _Nota de corrección_: se ha resuelto un problema por el que el atributo only_x_left_in_stock siempre devolvía 0 para los productos configurables cuando se añadía usando el SKU principal con opciones.
Detalles de la corrección:
* El valor only_x_left_in_stock ahora refleja con precisión el stock de la variante secundaria seleccionada en lugar del SKU principal.
* Esto garantiza que los niveles de stock se muestren correctamente para las variaciones de productos configurables en el carro de compras y las páginas de productos.
* _LYNX-405_: error de GraphQL: tipo de &#39;archivo&#39; no admitido en la consulta de opciones personalizables
   * _Nota de corrección_: se ha corregido un problema por el que GraphQL devolvía un error para las opciones personalizables de tipo &quot;archivo&quot; en los elementos del carro de compras. La consulta ahora devuelve correctamente los detalles de todos los tipos de opciones personalizables, incluidas las opciones basadas en archivos, sin causar errores.
* _LYNX-411_: la consulta de GraphQL no devuelve el precio normal calculado correcto para los productos personalizables
   * _Nota de corrección_: se ha corregido un problema por el que GraphQL no devolvía el precio normal calculado correcto para los productos personalizables. La consulta ahora incluye correctamente el precio normal calculado con valores personalizables aplicados (por ejemplo, 125 $) en la propiedad precios, lo que refleja tanto el precio base como cualquier coste de personalización adicional.
* _LYNX-412_: AppliedTaxes vía EstimatedTotals persiste con mutaciones actualizadas
   * _Nota de corrección_: se ha corregido un problema con la mutación EstimatedTotals por el que los impuestos aplicados persistían en un carro de compras incluso después de actualizar la región o el código postal. La mutación ahora actualiza correctamente los impuestos aplicados al cambiar entre los valores de región y código postal, asegurándose de que solo se aplique la regla fiscal correcta en función de los datos del carro de compras actual.
* _LYNX-420_: el atributo is_available en CartItemInterface devuelve true incluso cuando el stock vendible es menor que la cantidad del producto
   * _Nota de corrección_: se ha corregido un problema por el que el atributo is_available de CartItemInterface devolvía incorrectamente true incluso cuando el stock vendible era inferior a la cantidad de producto solicitada. El campo is_available ahora devuelve correctamente el valor false cuando la cantidad del producto supera el stock disponible.
* _LYNX-421_: no se puede agregar un cupón al carro de compras por el descuento de envío solamente
   * _Nota de corrección_: se corrigió un problema en el cual no se podía aplicar un cupón a un carro de compras para descuentos de envío solamente. El cupón ahora se aplica correctamente al importe de envío cuando se utiliza una regla de ventas sin condiciones de producto, lo que garantiza que se aplique el descuento esperado al coste de envío.
* _LYNX-425_: precio normal del producto con 12 decimales y valor incorrecto
   * _Nota de corrección_: se ha corregido un problema por el que el valor regular_price de las rutas de GraphQL product.price_range.maximum_price y minimum_price no coincidían con el precio de catálogo cuando se aplicaban varios tipos impositivos. Ahora, el valor regular_price refleja de forma coherente el precio de catálogo en todas las configuraciones de impuestos, lo que garantiza una precisión en los precios unitarios, los cálculos de coste total de las filas y las comprobaciones de descuentos en el Resumen del carro de compras.
* _LYNX-430_: error del servidor de GraphQL en el carro de compras con un producto agrupado agotado
   * _Nota de corrección_: se ha corregido un problema por el que GraphQL devolvía un error interno del servidor al recuperar un carro de compras que contenía un producto agrupado con un producto sin existencias, específicamente cuando la consulta incluía la propiedad itemsV2. GraphQL ahora devuelve correctamente una lista de elementos con mensajes de error relevantes adjuntos a la entrada del elemento de producto agrupado, según lo esperado.
* _LYNX-441_: no es posible crear una dirección con atributos personalizados
   * _Nota de corrección_: se ha corregido un problema con la mutación createCustomerAddress que impedía la creación de direcciones con atributos personalizados requeridos. La mutación ahora gestiona correctamente los atributos de dirección personalizados cuando se proporciona la carga útil adecuada.
* _LYNX-447_: error del servidor de GraphQL en el carro de compras con only_x_left_in_stock en el producto agrupado
   * _Nota de corrección_: se corrigió un problema en el cual al recuperar un carro de compras que contenía un producto agrupado con el campo only_x_left_in_stock en la consulta de GraphQL, se producía un error interno del servidor. GraphQL ahora devuelve correctamente un valor flotante o nulo para el campo only_x_left_in_stock sin errores.
* _LYNX-464_: error de GraphQL al eliminar otros productos con un producto configurable insuficiente en el carro de compras
   * _Nota de corrección_: se corrigió un problema por el que al intentar eliminar los productos en existencias del carro de compras se producía un error de GraphQL &#39;La cantidad solicitada no está disponible&#39; si el carro de compras también contenía productos configurables con existencias insuficientes. La eliminación ahora funciona según lo esperado sin activar errores.
* _LYNX-469_: no se pueden agregar productos debido a SKU en una mutación que distingue entre mayúsculas y minúsculas
   * _Nota de corrección_: se ha resuelto un problema en el que la mutación addProductsToCart devolvía un error &#39;PRODUCT_NOT_FOUND&#39; al usar SKU con mayúsculas y minúsculas diferentes. La mutación ahora gestiona los SKU sin distinción de mayúsculas y minúsculas, lo que garantiza la coherencia con las consultas del servicio de catálogo y el comportamiento de PDP.
* _LYNX-603_: el atributo del producto > la ™ de forma corta de la marca comercial se devuelve como ™
   * _Nota de corrección_: se ha resuelto un problema de codificación de caracteres con el nombre del producto para la API de GraphQL
* _LYNX-619_: problema de mutación de updateCustomerEmail
   * _Nota de corrección_: se ha resuelto un problema con la mutación updateCustomerEmail en el que los clientes sin los atributos personalizados requeridos (añadidos después de la creación de la cuenta) no podían actualizar su correo electrónico.
* _LYNX-626_: la mutación setShippingAddressesOnCart genera un error al usar pickup_location_code
   * _Nota de corrección_: se ha corregido un problema por el que la mutación setShippingAddressesOnCart devolvía un error al usar pickup_location_code sin especificar customer_address_id o address. La mutación ahora permite correctamente configurar una dirección de envío con solo el pickup_location_code.
* _LYNX-627_: la lista CustomerOrder.items_eligibility_for_return debe ser coherente con los elementos del pedido
   * _Nota de corrección_: se han resuelto incoherencias con la idoneidad de devolución en los pedidos:
1. La lista CustomerOrder.items_eligibility_for_return es ahora coherente con los artículos de pedido reales.
2. El campo OrderItemInterface.eligibility_for_return devuelve correctamente el valor &quot;false&quot; cuando ya se ha devuelto la cantidad completa.
3. CustomerOrder.items_eligibility_for_return ahora incluye solo los artículos que aún no se encuentran en proceso de devolución.
* _LYNX-628_: agregue el campo quantity_return_requested
   * _Nota de corrección_: se agregó el campo quantity_return_requested a OrderItemInterface, lo que permite identificar la cantidad de artículos para los que se ha enviado una devolución. Esto mejora el seguimiento de devoluciones junto con el campo quantity_returned existente.
* _LYNX-634_: las acciones disponibles del pedido no deben contener RETURN después de las devoluciones creadas para todos los artículos en cantidad completa
   * _Nota de corrección_: se ha corregido un problema por el que el campo available_actions de la consulta customer.orders de GraphQL incluía incorrectamente RETURN después de crear una devolución completa para todos los elementos. La acción RETURN ahora se elimina correctamente una vez completado el proceso de devolución.
* _LYNX-637_: Compatibilidad de tienda - Actualice la lógica para obtener el nombre de la tabla con prefijo y otras mejoras menores
   * _Nota de corrección_: Se ha actualizado la lógica para recuperar el nombre de tabla con el prefijo (relacionado con los cambios de SCP).
* _LYNX-643_: guardar en la libreta de direcciones no funciona al usar el campo same_as_shipping de setBillingAddressOnCart GQL
   * _Nota de corrección_: se corrigió un problema en el cual la dirección de envío no se guardaba en la libreta de direcciones del cliente al usar la mutación de GraphQL setBillingAddressOnCart con el campo same_as_shipping establecido en true. Ahora, la dirección de envío se almacena correctamente según lo esperado.
* _LYNX-650_: Estandarizar order_id en mutaciones
   * _Nota de corrección_: estandarizó la entrada order_id en mutaciones y actualizó la plantilla de correo electrónico de confirmación de cancelación de pedido para exponer el id de incremento en lugar del id de pedido.
* _LYNX-651_: CustomerOrder no muestra los comentarios del pedido
   * _Nota de corrección_: se ha resuelto un problema con CustomerOrder para incluir comentarios de pedidos en las consultas de GraphQL de pedidos de clientes y de invitados.
* _LYNX-652_: original_item_price no debe incluir ningún descuento
   * _Nota de corrección_: se ha actualizado la lógica de original_item_price en GraphQL Cart Item precios para excluir descuentos.
* _LYNX-681_: el paquete de productos todavía muestra &quot;IN_STOCK&quot; cuando uno de sus paquetes está agotado
   * _Nota de corrección_: se ha resuelto un problema en el que product.stock_status de los productos agrupados seguía mostrando &quot;IN_STOCK&quot; incluso cuando uno de los elementos agrupados estaba agotado.
* _LYNX-686_: la consulta del cliente devuelve un error interno del servidor si existe un valor para el atributo personalizado eliminado para un cliente
   * _Nota de corrección_: se ha corregido el problema por el que la consulta del cliente devolvía un error interno del servidor cuando un atributo personalizado eliminado aún tenía un valor almacenado. Ahora, se devuelve un mensaje de error adecuado si se solicita un atributo no existente. La caché necesaria se invalida al eliminar el atributo personalizado del cliente.
* _LYNX-687_: parámetro de acción para los vínculos de confirmación de devolución y cancelación
   * _Nota de corrección_: parámetro de acción agregado para los vínculos relacionados con el correo electrónico de confirmación de devolución y cancelación
* _LYNX-688_: la URL de confirmación de usuario invitado se redirige a la página de estado del pedido, ya que falta orderRef (para GuestRMA)
   * _Nota de corrección_: se ha agregado el parámetro orderRef al vínculo en el correo electrónico de confirmación de RMA de invitado
* _LYNX-689_: la URL de confirmación de usuario invitado se redirige a la página de estado del pedido, ya que falta orderRef
   * _Nota de corrección_: se agregó el parámetro orderRef al vínculo en el correo electrónico de confirmación de cancelación de pedidos de invitado
* _LYNX-690_: problemas con la consulta del cliente cuando se deshabilitó RMA
   * _Nota de corrección_: Se ha actualizado la lógica de GraphQL para garantizar que los retornos creados anteriormente permanezcan accesibles incluso cuando RMA esté deshabilitado globalmente. El mensaje de error se ha eliminado para mejorar la experiencia de usuario de la tienda, lo que garantiza que los clientes puedan seguir viendo sus devoluciones pasadas.
* _LYNX-696_: GraphQL no devuelve datos actualizados del carro de compras cuando se aplican cupones conflictivos
   * _Nota de corrección_: se corrigió un problema por el cual al aplicar un cupón en conflicto con una prioridad mayor se producía un mensaje de error sin devolver los datos actualizados del carro de compras. Ahora, cuando un nuevo cupón invalida el existente, la mutación devuelve correctamente el carro de compras con el cupón válido aplicado.
* _LYNX-699_: no se puede devolver nulo para el campo que no admite valores NULL &quot;TaxItem.title&quot; en placeOrder GQL
   * _Nota de corrección_: se ha corregido un problema por el que la mutación placeOrder fallaba con un error interno del servidor debido a un valor nulo para el campo que no admite valores NULL TaxItem.title. Ahora, el campo siempre devuelve un valor válido, lo que garantiza una colocación correcta del pedido.
* _LYNX-702_: EstimateTotals: los descuentos son nulos para los tipos de productos virtuales
   * _Nota de corrección_: se ha resuelto el problema con la mutación estimateTotals, que devolvía null para los descuentos cuando se aplica un código de descuento a un carro de compras que contiene productos virtuales.
* _LYNX-703_: el paquete de productos no devuelve el porcentaje y la cantidad de descuento correctos
   * _Nota de corrección_: se han introducido nuevas propiedades &quot;catalog_discount&quot; y &quot;row_catalog_discount&quot; para los precios de los artículos del catálogo a fin de mostrar los importes y porcentajes de descuento correctos en los niveles de fila y de artículo único.
* _LYNX-714_: configuración de mensaje de regalo en el nivel de producto
   * _Nota de corrección_: se corrigió un problema en el cual los mensajes de regalo no se aplicaban en el nivel de producto cuando estaban deshabilitados globalmente. Ahora, si los mensajes de regalo están habilitados para un producto específico, se pueden agregar correctamente utilizando la mutación updateCartItems y se guardarán y reflejarán correctamente.
* _LYNX-717_: problema con la eliminación del envoltorio para regalos del artículo del carro de compras
   * _Nota de corrección_: se corrigió un problema por el cual la eliminación del envoltorio para regalos de un elemento del carro de compras mediante la mutación updateCartItems no funcionaba según lo esperado. Ahora, tanto aplicar como eliminar el envoltorio para regalos funcionan correctamente sin errores.
* _LYNX-751_: la característica de cliente registrado coincidente no funciona en Boilerplate, y es necesario habilitar la mutación trackViewedProduct para los invitados.
   * _Nota de corrección_: se expuso la mutación trackViewedProduct para rastrear el evento de vista de productos de clientes e invitados
* _LYNX-757_: error de devolución de consulta cart.rules en lugar de matriz vacía en caso de que no se apliquen reglas de carro de compras activas
   * _Nota de corrección_: se ha corregido la consulta cart.rules para devolver una matriz vacía en lugar de un error cuando no se aplican reglas de carro activas.
* _LYNX-758_: problema al recuperar los envoltorios para regalos para los artículos del carro de compras
   * _Nota de corrección_: se ha actualizado la lógica de recuperación para devolver opciones de envoltorio para regalos para artículos del carro de compras cuando está globalmente deshabilitada pero habilitada en el nivel de producto
* _LYNX-778_: las llamadas de GraphQL con el método OPTIONS devuelven un código de respuesta 500 cuando se instala el paquete de compatibilidad con adobe-commerce/storefront
   * _Nota de corrección_: se ha corregido un problema por el que las llamadas de GraphQL mediante el método OPTIONS devolvían un error de servidor interno 500 al instalar el paquete de compatibilidad de adobe-commerce/storefront. El extremo ahora devuelve correctamente una respuesta 200/204 según lo esperado.

### Otras herramientas para desarrolladores

* _AC-10658_: [Problema] Corrija el error de sintaxis de HTML en visual.phtml
   * _Nota de corrección_: El sistema cierra ahora correctamente la etiqueta de inicio en el archivo visual.phtml, lo que garantiza una sintaxis de HTML adecuada. Anteriormente, la etiqueta de inicio no se cerraba correctamente, lo que provocaba un error de sintaxis de HTML.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38247>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problema] cambió &quot;activo&quot; a &quot;habilitado&quot; en el comando bin/magento maintenance:status
   * _Nota de corrección_: El sistema ahora proporciona mensajes de estado más precisos para el comando de modo de mantenimiento, cambiando el estado de &quot;activo&quot; a &quot;habilitado&quot; y de &quot;no activo&quot; a &quot;deshabilitado&quot;. Anteriormente, el mensaje de estado del comando de modo de mantenimiento se mostraba como &quot;activo&quot; o &quot;no activo&quot;, lo que podía generar confusión.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38486>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: La navegación en el árbol de categorías genera errores en Redis: &quot;La sesión de Redis ha superado las conexiones simultáneas&quot;
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38851>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0611e750>
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
* _ACP2E-3631_: las pruebas unitarias de Adobe Commerce 2.4.7-p3 están fallando
   * _Nota de corrección_: no se requieren notas de la versión.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/982b1c42>

### Pago / Métodos de pago, Pedido

* _AC-13699_: los detalles de la tarjeta de crédito del flujo de pago papal guardada para su uso posterior no se muestran en la página de métodos de pago almacenados
   * _Nota de corrección_: los detalles de la tarjeta de crédito de flujo de pago papal anterior guardada para su uso posterior no se mostraban en la página de métodos de pago almacenados, que ahora son detalles fijos de la tarjeta de crédito que se muestran en la página de métodos de pago almacenados.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/96dec499>

### Pagos

* _AC-13414_: el pago con tarjeta de crédito (vínculo de flujo de pago) no funciona
   * _Nota de corrección_: error de obtención anterior (el pago se rechazó) al realizar el pedido con la tarjeta de crédito después de que el pedido de corrección se haya realizado correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: El flujo de trabajo crea una nueva transacción cada vez que hacemos clic en el botón de captura en la pantalla de visualización de transacción
   * _Nota de corrección_: El sistema ahora obtiene correctamente la información de transacción sin crear una nueva transacción de pago cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción. Anteriormente, hacer clic en el botón Recuperar creaba incorrectamente una nueva transacción de pago para un pedido que ya se había pagado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: No se muestra el mensaje de Paylater en PDP para la cuenta de PayPal Merchant de Canadá
   * _Nota de corrección_: el sistema ahora muestra correctamente el mensaje PayAfter para las cuentas de comerciante de PayPal canadiense en la página de detalles del producto (PDP) cuando se puede determinar el país del comprador a partir de la dirección de facturación o envío de la cuenta. Anteriormente, no se mostraba el mensaje Paylater debido a la falta de un parámetro, lo que daba como resultado un error en la consola del explorador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
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
* _AC-12000_: [Problema] Limpieza de código, adición de nuevo bloque de encabezado crítico y movimiento de css crítico antes de los recursos
   * _Nota de corrección_: el sistema ahora incluye un nuevo bloque de encabezado crítico y mueve CSS crítico antes que los recursos, lo que permite una mayor personalización y optimización del rendimiento en el front-end. Anteriormente, el CSS crítico no se colocaba antes de los recursos, lo que limitaba las oportunidades de personalización y optimización.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38748>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: La compilación del tema se interrumpe cuando el host mysql contiene información del puerto
   * _Nota de corrección_: El sistema ahora administra correctamente la configuración de host de MySQL que incluye información de puerto, lo que garantiza la compilación correcta del tema. Anteriormente, la compilación del tema fallaba si la configuración del host MySQL en la conexión de base de datos incluía información de puerto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38799>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: compatibilidad con CommandLoaderInterface de Symfony en Magento CLI
   * _Nota de corrección_: Este cambio reduce el tiempo de inicialización de la aplicación CLI de Magento al permitir la inicialización diferida de comandos hasta que se necesitan.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/29266>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: Problema de rendimiento al cargar atributos de producto en reglas de carro de compras
   * _Nota de corrección_: se ha mejorado el rendimiento de las consultas para las reglas de ventas, de unos 150 ms a un solo dígito ms.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Rendimiento de indexación parcial de precios
   * _Nota de corrección_: El rendimiento de indización parcial de precios se ha mejorado al optimizar algunas de las consultas de eliminación utilizadas en el proceso de indización.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: el pedido se rechaza en la configuración de varias tiendas al usar el procesamiento asincrónico de pedidos + Términos y condiciones
   * _Nota de corrección_: ahora se procesan los pedidos realizados desde sitios web no predeterminados con los términos y condiciones habilitados.
Antes de que se rechazaran automáticamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: La llamada a la API Rest de pedidos está tardando mucho tiempo en ejecutarse
   * _Nota de corrección_: El sistema ahora ejecuta la llamada a la API de Order Rest en un período de tiempo razonable, lo que mejora el rendimiento al recuperar un gran número de pedidos. Anteriormente, la llamada a la API de Order Rest tardaba mucho tiempo en ejecutarse, lo que provocaba retrasos al recuperar un gran número de pedidos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/001e5188>

### Rendimiento, promoción

* _ACP2E-2617_: el indizador de reglas de ventas dejó de ejecutarse
   * _Nota de corrección_: El sistema ahora completa correctamente el indizador de reglas de ventas incluso con un gran número de grupos de filtros combinados, asegurándose de que las condiciones de las reglas del carro de compras se apliquen al carro de compras según lo esperado. Anteriormente, el indizador de reglas de ventas no se completaba cuando había un gran número de grupos de filtros combinados, lo que producía un mensaje de error e impedía la aplicación de condiciones de reglas de carro de compras.

### Precio

* _AC-11810_: Magento2.4.6-p4 Pedido API Simple Artículo sin precio
   * _Nota de corrección_: El sistema ahora muestra correctamente el precio de los productos simples cuando se consultan a través de la API de pedidos, lo que garantiza una representación de datos precisa. Anteriormente, el precio de los productos simples se mostraba incorrectamente como cero en la respuesta de la API.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: error de redondeo de céntimos en la regla de catálogo
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/276e0acd>

### Product

* _AC-10535_: los caracteres especiales del nombre de producto asociado configurable se están convirtiendo en entidades de HTML.
   * _Nota de corrección_: El sistema ahora conserva correctamente caracteres especiales en los nombres de productos asociados al editar un producto configurable, lo que impide que se conviertan en entidades de HTML. Anteriormente, los caracteres especiales de los nombres de producto asociados se convertían en entidades de HTML cuando se editaba el producto configurable.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38146>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: la función GetById del ProductRepository no crea la clave de caché correcta
   * _Nota de corrección_: el sistema ahora crea correctamente una clave de caché en la función GetById del ProductRepository, independientemente de si el Id. de almacén se pasa como una cadena o como un entero. Esto garantiza que el producto se recupere de la memoria en llamadas posteriores, lo que mejora el rendimiento. Anteriormente, el sistema recuperaba el producto de la base de datos cada vez que se llamaba a la función, incluso con los mismos parámetros, debido a la creación incorrecta de la clave de caché.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38384>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [Problema] [MFTF] agregó AdminClickAddOptionForBundleItemsActionGroup
   * _Nota de corrección_: el sistema ahora incluye AdminClickAddOptionForBundleItemsActionGroup, lo que mejora la funcionalidad del panel de administración. Anteriormente, este grupo de acción no estaba disponible.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/30857>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/30838>
* _AC-13173_: [Problema] Se corrigió un error tipográfico en el bloque PHPDoc
   * _Nota de corrección_: El sistema ahora quita correctamente una variable de referencia desconocida en PHPDoc para la declaración de la variable $helper, lo que mejora la claridad y precisión del código. Anteriormente, esta variable de referencia desconocida en PHPDoc causaba confusión y posibles imprecisiones en el código.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38961>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Problema] Se ha corregido el diseño de páginas de productos del paquete dañado y descargable en Magento >= 2.4.7
   * _Nota de corrección_: se ha corregido el diseño de las páginas de productos agrupadas y descargables, lo que garantiza una visualización coherente y correcta en todos los dispositivos. Anteriormente, estas páginas experimentaban problemas de diseño debido a una reorganización del bloque multimedia de información del producto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39403>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) debe ser de tipo int, se ha proporcionado una cadena
   * _Nota de corrección_: el sistema ahora almacena correctamente en déclencheur los correos electrónicos de alertas de productos asegurándose de que el identificador del almacén sea del tipo de datos correcto. Anteriormente, los correos electrónicos de alerta de producto no se enviaban debido a una discrepancia de tipos en el identificador de tienda.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35602>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: La función [Cloud] addFilterToMap no funciona para ciertas columnas
   * _Nota de corrección_: Ahora, el módulo personalizado se puede usar en la cuadrícula de pedidos. Anteriormente, se producían errores al utilizar un módulo personalizado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3471_: [Nube] Productos en la categoría - Agregar productos - Asignar - Seleccionar todo
   * _Nota de corrección_: los usuarios ahora pueden seleccionar o anular la selección de productos mediante la opción.

### Promoción

* _ACP2E-2602_: el atributo del cliente no está visible al crear una cuenta a partir de una invitación
   * _Nota de corrección_: los atributos del cliente están disponibles al crear la cuenta a partir de la invitación.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: El código de cupón con el límite de usuarios por cupón no se libera para el pago si se cancela el pedido
   * _Nota de corrección_: El sistema ahora actualiza inmediatamente los usos de cupones cuando se crea o cancela un pedido y agrega los usos de reglas a una cola para evitar posibles interbloqueos. Esto garantiza que se libere un código de cupón con un límite de &quot;Usos por cupón&quot; y que pueda reutilizarse si se cancela un pedido debido a un pago fallido. Anteriormente, el sistema no liberaba el código de cupón para reutilizarlo en estos casos, lo que daba como resultado un mensaje de error que indicaba que el código de cupón no era válido.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: El indizador de productos de reglas de catálogo de reindexación de [Cloud] lanza SQLSTATE[HY000]: Error general: El servidor MySQL 2006 ha desaparecido.
   * _Nota de corrección_: El sistema ahora administra correctamente el valor &quot;batchCount&quot; personalizado en el archivo di.xml para el archivo &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, lo que evita errores de SQL como &quot;Error general: 2006 MySQL server has gone away&quot; durante la reindexación del indexador de productos de reglas de catálogo debido al tamaño incorrecto del lote en catálogos grandes
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2926_: [NUBE]Regla de precio del carro de compras para visitantes El segmento de cliente no aplica descuento en el carro de compras
   * _Nota de corrección_: El sistema ahora aplica correctamente las reglas de precios del carro de compras para los segmentos de clientes de visitantes, incluso si la regla no utiliza un cupón, lo que garantiza que se apliquen los descuentos adecuados al carro de compras. Anteriormente, los descuentos no se aplicaban al carro de compras para segmentos de clientes de visitantes a menos que la regla de precio del carro de compras usara un cupón.
* _ACP2E-3024_: Falta el atributo &quot;Type&quot; en la pestaña &quot;Products to Match&quot; de las reglas de producto relacionadas
   * _Nota de corrección_: El atributo &quot;Type&quot; está ahora disponible como opción de filtro en la ficha &quot;Products to Match&quot; del módulo &quot;Related Product Rules&quot;, lo que permite una definición de regla más precisa. Anteriormente, este atributo no aparecía en la pestaña &quot;Productos para combinar&quot;, lo que limitaba la capacidad de crear criterios de coincidencia precisos.
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
* _ACP2E-3472_: [NUBE] El cálculo del envío no tiene en cuenta la regla del carro de compras
   * _Nota de corrección_: antes de la corrección, una regla de carro de compras con la condición de región no se aplicaba de manera coherente. Después de la corrección, las reglas de carro de compras con condiciones de región se aplican correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_: La condición de SKU de la regla de carro de compras no se cumple para la factura.
   * _Nota de corrección_: el descuento en el paquete de productos con precio dinámico ahora se refleja correctamente en la factura. Anteriormente, el descuento no se reflejaba en la factura.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: Valor de descuento incorrecto cuando se aplican varias reglas de precios del carro de compras simultáneamente con productos con precios especiales o con descuento
   * _Nota de corrección_: antes de la corrección, la cantidad fija para las reglas completas del carro de compras no se aplicaba correctamente si se aplicaba más de una. Ahora, las reglas del carro de descuentos de cantidad fija se aplican correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1984c61c>

### Devuelve

* _ACP2E-3330_: [NUBE] Los usuarios administradores restringidos pueden ver el menú y los botones de retorno
   * _Nota de corrección_: Los usuarios administradores restringidos ahora no tienen acceso a los controles relacionados con RMA (menú y botones).
Los usuarios administradores anteriormente restringidos podían ver el menú y los botones de retorno.
* _ACP2E-3443_: La pantalla de retorno está dañada al actualizar la pantalla
   * _Nota de corrección_: el usuario puede actualizar la página sin experimentar distorsión de la pantalla.

### SEO

* _AC-11907_: agregar reescrituras de URL con acento provoca una carga infinita
   * _Nota de corrección_: el sistema ahora crea y funciona correctamente las reescrituras de URL con acentos, lo que evita la carga infinita durante el proceso de guardado. Anteriormente, al añadir una reescritura de URL con un acento, se producía un problema de carga infinita.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38692>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: la reescritura de URL de categoría incorrecta de varias tiendas para la categoría de tercer nivel
   * _Nota de corrección_: genere reescrituras de URL correctas para los elementos secundarios con clave de URL principal con ámbito personalizado
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: Los caracteres de doble byte (caracteres especiales) del campo Nombre de producto bloquean la creación de productos en el servidor
   * _Nota de corrección_: Se ha agregado una nueva configuración que le permite aplicar transliteraciones a la dirección URL del producto o no. La configuración está disponible aquí: Tiendas > Configuración > Catálogo > Catálogo > Optimización del motor de búsqueda: &quot;Aplicar transliteración para la URL del producto&quot;
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_: creación de entradas url_rewrite incorrecta con varios almacenes en un grupo de tiendas
   * _Nota de corrección_: antes de la corrección, solo podía generar reescrituras de URL en un sitio web al editar un producto. Con la corrección, se introdujo una nueva configuración (Tiendas > Configuración > Catálogo > Optimización del motor de búsqueda, &quot;Ámbito de reescritura de URL del producto&quot; con opciones &quot;Vista de tienda&quot;, &quot;Sitio web&quot;) que le permite generar reescrituras de URL en el nivel de vista de tienda o sitio web.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/2d627301>

### Ventas

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

* _AC-11855_: [Problema] Falta Fuente CSP Emergente Más Tarde
   * _Nota de corrección_: El sistema ahora permite cargar la fuente &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sin infringir la directiva de la directiva de la directiva de seguridad de contenido, lo que garantiza la correcta visualización de la ventana emergente de Paylater. Anteriormente, la fuente se rechazaba cargar debido a una infracción de la directiva de la política de seguridad de contenido, lo que causaba problemas de visualización con la ventana emergente de Paylater.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38624>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [Problema] Actualizar el texto DOM de js.js reinterpretado como HTML
   * _Nota de corrección_: al usar innerText, se evitará el riesgo de que se inyecte HTML, ya que estas propiedades omiten automáticamente cualquier carácter especial de HTML en el texto proporcionado. Esta corrección ayuda a evitar vulnerabilidades de scripts entre sitios (XSS) al tratar la entrada como texto sin formato en lugar de HTML interpretado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 se muestra incorrectamente al pagar el idioma alemán
   * _Nota de corrección_: Anteriormente, el recaptcha de debajo de la dirección de correo electrónico de cierre de compra no tenía estilo para los idiomas con palabras largas, como el alemán. Después de esto, el recaptcha tiene el mismo aspecto que todos los elementos recaptcha del resto de las áreas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: El captcha al iniciar sesión como administrador no requiere interacción para algunos usuarios
   * _Nota de corrección_: ReCaptcha para el inicio de sesión del administrador se validó según lo esperado
   * _Contribución de código de GitHub_: <https://github.com/magento/security-package/commit/8f64ab3c>

### Envío

* _AC-10757_: [Problema] Se corrigió un error tipográfico en tracking.phtml - se cambió el nombre de las funciones JS &quot;currier&quot; a &quot;carrier&quot;
   * _Nota de corrección_: El sistema ahora utiliza correctamente el término &quot;carrier&quot; en lugar del mal escrito &quot;currier&quot; en las funciones de controlador de JavaScript utilizadas en la plantilla de seguimiento de pedidos, lo que garantiza una nomenclatura de funciones y una claridad de código adecuadas. Anteriormente, se utilizaba el término mal escrito &quot;currier&quot;, lo que producía una posible confusión e incoherencia en la base del código.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/34523>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST &quot;Un envío no puede tener una unidad de medida KGS/IN o LBS/CM u OZS/CM&quot;
   * _Nota de corrección_: Asegúrese de que las tarifas de UPS sean visibles en el cierre de compra y el carro de compras.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38618>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-12938_: actualizaciones de las instrucciones de configuración de UPS REST &quot;sandbox&quot; y &quot;prod&quot; en devdoc
* _AC-13172_: [Problema] Corrección ortográfica de las variables de la dirección del cliente
   * _Nota de corrección_: el sistema ahora escribe correctamente las variables para las direcciones de los clientes, lo que garantiza una visualización precisa en el área de cuenta del front-end. Anteriormente, la ortografía incorrecta de estas variables podía provocar errores durante las revisiones de código local.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32817>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: La ventana de seguimiento muestra una fecha de entrega esperada incorrecta
   * _Nota de corrección_: muestra la fecha de entrega correcta para el operador de Fedex.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Se Siguen Mostrando Las Tarifas De Tabla Aunque Se Aplique El Envío Gratuito
   * _Nota de corrección_: el método de envío de tarifa de tabla ahora se muestra aunque el envío gratuito esté disponible después de aplicar el cupón
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: error de MFTF test AdminCreatingShippingLabelTest debido a credenciales no agregadas en el entorno Jenkins
   * _Nota de corrección_: corrección de la prueba mftf
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: la API de seguimiento de FedEx no funciona con las credenciales de REST
   * _Nota de corrección_: Anteriormente, la integración con FedEx no requería claves de API adicionales para la API de seguimiento. Ahora se ha añadido una nueva configuración para admitir el seguimiento de claves de API.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Las tarifas negociadas de FedEx de la nube] no se devuelven en REST
   * _Nota de corrección_: Antes de la corrección, las tasas específicas de la cuenta de FedEx no se enviaban en la respuesta, incluso a través de la documentación de FedEx que deberían haberse enviado. Después de la corrección, las tasas específicas de la cuenta se envían en la respuesta cambiando la solicitud por nuestra parte.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/55615e61>

### Ensayo y previsualización

* _ACP2E-2901_: La configuración de actualización programada no se guardó si se agregó originalmente al ejecutar la actualización
   * _Nota de corrección_: El sistema ahora borra correctamente los valores de atributos de productos en las actualizaciones programadas subsiguientes cuando se modifican dichos atributos en la actualización que se está ejecutando. Anteriormente, cuando una actualización programada en ejecución modificaba un atributo de producto, era imposible borrar dichos valores de atributos al crear una nueva actualización programada, lo que requería que el usuario los reeditara después de la creación.
* _ACP2E-2999_: La regla de precio del carro de compras desde la fecha y hasta la fecha no se sincronizó con la actualización de ensayo
   * _Nota de corrección_: las fechas se guardan según las actualizaciones para el ensayo de reglas de precios del carro de compras.
* _ACP2E-3104_: Error de JS en la vista previa de ensayo
   * _Nota de corrección_: Ahora el archivo form-mini-stub.js se está cargando correctamente sin ningún error de sintaxis Js en las herramientas para desarrolladores.
* _ACP2E-3162_: No se puede actualizar el contenido de ensayo del precio especial del producto
   * _Nota de corrección_: El sistema ahora permite editar la fecha de finalización de una campaña de actualización de precios una vez iniciada, lo que garantiza que los usuarios puedan realizar los ajustes necesarios en sus campañas. Anteriormente, se producía un error al intentar actualizar la fecha de finalización de una campaña activa, lo que impedía a los usuarios realizar cambios.
* _ACP2E-3453_: No se puede actualizar la actualización programada al usar un atributo de categoría personalizado único
   * _Nota de corrección_: se corrigió un problema en el cual no era posible actualizar una actualización programada para una categoría si esta tenía un atributo único
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Direccionamiento

* _AC-9432_: [Problema] Permitir el uso de intervalos CIDR en la lista de permitidos de mantenimiento
   * _Nota de corrección_: el sistema ahora admite el uso de intervalos CIDR en la lista de IP permitidas del modo de mantenimiento, lo que permite que un intervalo de direcciones IP omita el modo de mantenimiento. Anteriormente, el modo de mantenimiento permitía que la lista de direcciones IP solo permitiera a direcciones IP individuales omitir el modo de mantenimiento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37943>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/30699>

### Impuestos

* _AC-13295_: [Problema] Feature/php8.1 constructor property promotion wee graph ql
   * _Nota de corrección_: reemplace casi todas las propiedades con la promoción de propiedades de constructor en el módulo web graph ql:
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39309>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: el impuesto sobre productos fijos (FPT) no funciona con productos configurables
   * _Nota de corrección_: FPT para las variaciones de productos configurables funciona correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Marco de prueba

* _AC-11654_: prueba de integración con error testDbSchemaUpToDate debido a un tipo de columna JSON
   * _Nota de corrección_: El sistema ahora reconoce correctamente los tipos de columnas JSON en el esquema de la base de datos durante las pruebas de integración, lo que evita errores de prueba debido a una discrepancia entre el esquema de la base de datos y el esquema declarativo. Anteriormente, el sistema identificaba incorrectamente los tipos de columnas JSON como LONGTEXT en MariaDB, lo que provocaba que las pruebas de integración fallaran.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Problema] ortografía de corrección de PHPDoc
   * _Nota de corrección_: el sistema ahora reconoce correctamente los métodos obsoletos en IDE debido a una corrección ortográfica en PHPDoc. Anteriormente, un error ortográfico en el PHPDoc provocaba que los IDE no reconocieran determinados métodos como obsoletos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/31399>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: comprobando el comportamiento con el carro de compras persistente después de que caduque la sesión
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: las pruebas de integración no se superaron Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _AC-13722_: [Comparación de base de datos] Error irrecuperable si la base de datos contiene un registro sobre la regla de destino sin condiciones
   * _Nota de corrección_: Anteriormente, si la base de datos contiene un registro sobre la regla de destino sin ninguna condición, se obtenían errores irrecuperables, pero después de que la herramienta de comparación de bases de datos de corrección pase correctamente sin errores irrecuperables.
* _AC-13848_: corrija pruebas estáticas para habilitar el uso por extensiones de terceros
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [Error interno] en la aplicación de correcciones no se muestra durante la ejecución ni en los registros
   * _Nota de corrección_: &#39;-
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Nota de corrección_: Mftfs fijos
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/078c387e>

### Marco de IU

* _AC-12128_: corrección de la vulnerabilidad de seguridad Prototype.js CVE-2020-27511
   * _Nota de corrección_: el sistema se ha actualizado para solucionar la vulnerabilidad de seguridad CVE-2020-27511 en Prototype.js 1.7.3, lo que mejora la seguridad general del sistema. Antes de esta actualización, el sistema era susceptible a una Denegación de servicio de expresión regular (ReDOS) mediante la eliminación de etiquetas HTML creadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less usa pub/ prefix para los mapas de origen
   * _Nota de corrección_: El sistema ahora genera mapas de origen de less/css sin el prefijo /pub para las rutas al usar grunt, lo que elimina la necesidad de una solución alternativa en la configuración del servidor web. Anteriormente, el uso del prefijo /pub en las rutas de mapas de origen requería una configuración específica en el servidor web para funcionar correctamente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38837>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38840>
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
* _AC-1306_: el contenido estático se está implementando para los módulos deshabilitados
   * _Nota de corrección_: el sistema ahora excluye CSS relacionado con módulos deshabilitados de los archivos de salida CSS finales, lo que garantiza que no se carguen estilos innecesarios. Anteriormente, el CSS relacionado con los módulos desactivados se incluía en los archivos de salida CSS finales, lo que provocaba la carga de estilos adicionales e innecesarios.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/24666>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: comportamiento incoherente en la ordenación &quot;sin existencias&quot; con el umbral de existencias mínimo
   * _Nota de correcciones_: El sistema ahora ordena correctamente los productos del catálogo según los niveles de existencias, cumpliendo el umbral de existencias mínimo establecido y moviendo los artículos sin existencias al final de la lista de forma consistente. Anteriormente, el comportamiento de ordenación era incoherente, ya que los elementos no siempre aparecían en el orden correcto según sus niveles de stock, y los cambios en la ordenación podían producirse de forma impredecible después de guardar, actualizar o modificar la jerarquía de categorías.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Sugerencia para mejorar los informes de errores en los problemas de carga de require.js
   * _Nota de corrección_: esta PR mejora el mensaje de error cuando requireJs no puede cargar un componente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36761>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: Errores de obsolescencia de PHP 8.4 que causan errores de compilación en 2.4-development
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Problema] No cargar contexto de bloque de servidor en front-end
   * _Nota de corrección_: El sistema ahora garantiza que el contexto de bloque del servidor no se cargue en el front-end, lo que evita la creación de sesiones back-end innecesarias y posibles bloqueos de sesión. Anteriormente, el sistema cargaba incorrectamente el contexto de bloque back-end en el front-end, lo que provocaba la creación de sesiones back-end y posibles bloqueos de sesión.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37617>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [Problema] Eliminar resumen de revisión de scripts innecesarios
   * _Nota de corrección_: El sistema ahora optimiza el tiempo de carga de la página eliminando los scripts de JavaScript innecesarios de la sección de clasificación, en lugar de utilizar estilos CSS en línea para lograr un código más eficiente y legible. Anteriormente, el uso de scripts de JavaScript para la sección de clasificación podía ralentizar el tiempo de carga de la página.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37776>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: Excepción al comprobar el saldo de una tarjeta regalo cuando Recaptcha está habilitado
   * _Nota de corrección_: los usuarios podrán recuperar el saldo de la tarjeta regalo en la pantalla de vista y edición del carro de compras. Anteriormente, estos detalles no se mostraban cuando reCAPTCHA estaba habilitado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ACLARACIÓN] Cumplimiento de ADA de solicitud de característica
   * _Nota de corrección_: El sistema ahora garantiza el cumplimiento de ADA eliminando las propiedades CSS no admitidas y reemplazándolas por otras admitidas en el archivo print.css. Anteriormente, el uso de propiedades CSS no admitidas producía problemas de compatibilidad con el explorador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Nube] Código de biblioteca de confusión en effect-drop.js de AC 2.4.4-p8
   * _Nota de corrección_: El sistema ahora implementa correctamente la biblioteca effect-drop.js, lo que garantiza el funcionamiento adecuado de los efectos de la interfaz de usuario de jQuery. Anteriormente, la biblioteca effect-drop.js se sobrescribía por error con la biblioteca effect-clip.js, lo que causaba posibles problemas con los efectos de la interfaz de usuario de jQuery.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: Encabezado del sitio | Caracteres especiales que rompen la sección de Bienvenida al cliente
   * _Nota de corrección_: después de la corrección, los caracteres especiales se muestran correctamente en la sección de bienvenida del cliente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: Error en la edición de segmentos de clientes con el intervalo de fechas
   * _Nota de corrección_: es posible guardar el segmento del cliente con la condición de intervalo de fechas, cuando solo se editó una de las fechas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a52ff98f>
