---
source-git-commit: 62b6501fc2ba595146bf7f38a7d3352ef02be1a0
workflow-type: tm+mt
source-wordcount: '26051'
ht-degree: 0%

---
# Magento Open Source Notas de la versión (v2.4.8)

## Resúmenes

Los siguientes 31 puntos destacados se aplican a la versión 2.4.8 de Magento Open Source.

### Marco de referencia

* _AC-10721_: Actualización de las dependencias del Compositor de liga/flysystem Actualización a la última versión
   * _Nota_ de corrección: Actualizar las dependencias del Compositor 2.x league/flysystem a la versión más reciente 3.x
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11673_: Investigar las últimas versiones de php-amqplib/php-amqplib
   * _Nota_ de corrección: actualizada la última versión php-amqplib/php-amqplib :^3.x
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11911_: limpieza de css jQuery/fileuploader después de la migración a uppy biblioteca
   * _Nota_ de corrección: Se ha eliminado el biblioteca jQuery/fileUploader porque se ha migrado a Uppy biblioteca
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: compatibilidad añadir con MySQL 8.4 LTS para Magento CE
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12015_: Limpieza de la carpeta ExtJs después de la migración a jsTree biblioteca
   * _Nota_ de corrección: Se ha eliminado la carpeta extJs porque el funcionalidad relacionado se ha migrado a jsTree
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: Actualizar la dependencia del sistema monólogo/monólogo a la última versión principal
   * _Nota_ de corrección: El sistema se ha actualizado para utilizar la última versión principal de la biblioteca &quot;monolog:^3.x&quot;, lo que garantiza la compatibilidad y un rendimiento mejorado. Anteriormente, el sistema utilizaba una versión obsoleta del biblioteca &quot;monólogo/monólogo&quot;, lo que podría haber dado lugar a posibles problemas y limitaciones.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: Actualizar la dependencia wikimedia/less.php a la última versión principal
   * _Nota_ de corrección: El sistema ha sido actualizado para utilizar la última versión principal 5.x del biblioteca &quot;wikimedia/less.php&quot;, lo que garantiza la compatibilidad y la funcionalidad actualizada. Anteriormente, el sistema utilizaba una versión obsoleta del biblioteca lo que podría haber provocado problemas de seguridad.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: Actualización: jquery/validate biblioteca dependencia a la última versión secundaria
   * _Nota_ de corrección: Actualice jquery/validate biblioteca dependencia a la última versión secundaria 1.20.0
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: Actualización moment.js dependencia del sistema a la última versión secundaria
   * _Nota_ de corrección: Actualizar moment.js dependencia del sistema a la última versión secundaria 2.30.1
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: compatibilidad añadir con MySQL 8.4 LTS para EE
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: compatibilidad añadir con MySQL 8.4 LTS para B2B
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: compatibilidad añadir con MySQL 8.4 LTS para extensiones paquete
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: compatibilidad añadir con MariaDB 11.4 LTS For CE
   * _Nota_ de corrección: Se ha agregado compatibilidad con MariaDB 11.4 con Adobe Systems Commerce y extensiones
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: Optimización de suscriptores - phpUnit10
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: Soporte de conexión reintentos para sesión de Redis y compatible con colinmollenhour/php-redis-session-abstract v2.0.0
   * _Nota_ de corrección: actualizada la última versión de colinmollenhour/php-redis-session-abstract v2.0.0 compatible con Adobe Commerce
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12576_: Investigar los fallos de las pruebas de automatización con MySQL 8.4 LTS
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: compatibilidad añadir con MariaDB 11.4 LTS For EE
   * _Nota_ de corrección: Se ha agregado compatibilidad con MariaDB 11.4 con Adobe Systems Commerce y extensiones
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12715_: Actualizar las dependencias del compositor de laminas actualizando a la última versión
   * _Nota_ de corrección: El sistema ahora es compatible con las últimas versiones de las dependencias del compositor de laminas:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
Validador de láminas/láminas
garantizar la compatibilidad y la funcionalidad actualizada. Anteriormente, la actualización a las versiones más recientes de estas dependencias podía causar problemas de incompatibilidad con versiones anteriores y errores de prueba.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12823_: Investigación de la falla del prueba de la unidad debido a la actualización del parche phpunit durante la actualización del componente
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-13076_: [Parte 1] : Actualizar todo dependencia de js biblioteca y npm con la última versión disponible
   * _Nota_ de corrección: la compatibilidad con la versión del compositor solo era hasta la versión 2.2.x del compositor. Ahora el soporte se extendió a la versión 2.4.x también.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/19844aa0>

### Orden

* _ACP2E-2709_: [Solicitud de característica] El cliente sugiere que el botón Enviar Comentario en el Página de detalles del pedido sea confuso y se cambie por otra otra cosa.
   * _Nota_ de corrección: Para minimizar la confusión, la etiqueta &quot;Enviar Comentario&quot; botón cambió a &quot;Actualizar&quot; en el Página de detalles del pedido.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/488c1034>

### Otro

* _AC-11420_: Los indexadores establecidos aparecen en el estado Listo de forma predeterminada cuando se instala la nueva versión de Adobe Systems Commerce
   * _Nota_ de corrección: Después de la instalación Magento, la Estado del indizador debe estar en *estado Listo* de forma predeterminada.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: En la instalación de Magento existente al instalar el indexador de terceros módulo establecer indexadores en actualización según la programación de forma predeterminada.
   * _Nota_ de corrección: Todos los nuevos indexadores están por defecto en [modo Actualizar por programación] . Anteriormente, el modo predeterminado era [Actualizar en Guardar]. Lo mismo ocurre con los indexadores personalizados.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: Elasticsearch opciones 7 y 8 deben venir con Deprecated en la configuración de administración.
   * _Nota_ de corrección: Elasticsearch opción 8 en la opción Configuración del administrador se mostrará con texto obsoleto para informar a los usuarios que Elasticsearch opción 8 ya no se recomienda usar.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: añadir nota de texto cuando Elasticsearch opción está seleccionada en la configuración del administrador
   * _Nota_ de corrección: Se agrega una nota de texto para que los usuarios administradores de Adobe Systems de Commerce sepan que Elasticsearch ya no es compatible con Adobe Systems y que está en desuso.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0611e750>
* _AC-13448_: Ofrezca parche de mejora del rendimiento de las operaciones a precios nivelados en 2.4.8
   * _Nota de corrección_: El sistema ahora permite actualizaciones masivas más eficientes de los precios de nivel sin causar problemas de rendimiento o falta de respuesta del sitio cuando se utiliza el punto final de API de REST &quot;/V1/products/tier-prices&quot;. Anteriormente, la actualización de una gran cantidad de precios con este punto de conexión podía provocar problemas de rendimiento y falta de respuesta del sitio.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_: Quitar todos los avisos de derechos de autor Adobe Systems confidenciales de los repositorios de Magento Open Source
   * _Nota_ de corrección: Todos Adobe Systems avisos confidenciales de derechos de autor se han eliminado de los repositorios de código abierto, lo que garantiza que solo se utilice la forma reducida de Adobe Systems derechos de autor. Anteriormente, algunos archivos en los repositorios públicos contenían Adobe Systems avisos confidenciales de derechos de autor, lo que llevó a escaladas desde el comunidad.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39493>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/4bca5dfe>

### Marco IU

* _AC-12726_: [2.4.8-beta1] Migración de TinyMCE 5 a TinyMCE 7
   * _Nota_ de corrección: Se migró TinyMCE 5 a TinyMCE 7.3.0 para ser una versión compatible con Adobe Systems Commerce, anteriormente el sistema usaba 5.10.2, que estaba desactualizado e informaba de vulnerabilidad de seguridad
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [migración 2.4.8-beta1] de TinyMCE 5 a TinyMCE 7 Page Builder
   * _Nota_ de corrección: Se migró TinyMCE 5 a TinyMCE 7.3.0 para ser una versión compatible con Adobe Systems Commerce, anteriormente el sistema usaba 5.10.2, que estaba desactualizado e informaba de vulnerabilidad de seguridad
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [2.4.8-beta1] Migración de TinyMCE 5 a TinyMCE 7 - Magento2-infra - palabras prohibidas
   * _Nota_ de corrección: Se migró TinyMCE 5 a TinyMCE 7.3.0 para ser una versión compatible con Adobe Systems Commerce, anteriormente el sistema usaba 5.10.2, que estaba desactualizado e informaba de vulnerabilidad de seguridad
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Require.js actualizar a la versión más reciente 2.3.7 (vulnerabilidad de seguridad CVE-2024-38999)
   * _Nota_ de corrección: Se ha actualizado require.js a la versión más reciente 2.3.7. En la versión anterior se ha informado de una vulnerabilidad de seguridad
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b34c0a75>

## Problemas solucionados

Hemos corregido 497 problemas en el código central de Magento Open Source 2.4.8. A continuación se describe un subconjunto de los problemas corregidos incluidos en esta versión.

### Apis

* _AC-10042_: /V1/transactions La API de REST devuelve un error cuando parent_txn_id = txn_id
   * _Nota_ de corrección: El sistema ahora maneja correctamente las transacciones de concepto padre y secundario donde el ID de transacción principal es el mismo que el ID de transacción, evitando un bucle infinito al consultar el punto final de la API REST /V1/transactions. Anteriormente, este escenario daba como resultado un error fatal debido a que se excedía el tiempo máximo de ejecución.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Problema con el tipo Graphql] en 2.4.7
   * _Nota de corrección_: el sistema ahora controla correctamente los valores enteros en la función GetCustomSelectedOptionAttributes al ejecutar un consulta GraphQL, evitando cualquier error relacionado con el tipo. Anteriormente, el lanzamiento de un consulta GraphQL que usaba GetCustomSelectedOptionAttributes con un argumento entero daba como resultado un error de tipo.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38662>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: Caracteres especiales en categoría url_key (cuando se crean mediante API de REST)
   * _Nota_ de corrección: anteriormente en categoría_url_key el carácter especial no está allí después de la corrección muestra un carácter especial en categoría_url_key
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/35577>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2755_: Problema con la API REST después de habilitar 2FA Duo
   * _Nota_ de corrección: 2FA con la opción de seguridad Duo ahora genera la firma correcta para la API de REST
   * _Contribución_ de código de GitHub: <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_: [API de REST:] Utilizar valor predeterminado en tienda vista no permanece marcado después de agregar configuraciones para un producto configurable
   * _Nota_ de corrección: El problema se ha solucionado asegurándose de que las entradas correctas de la base de datos para las opciones personalizables para un tienda no predeterminado. La casilla de verificación para el tienda personalizado en la sección &quot;admin > Catalogue > Product Editar > Customizable Opciones&quot; no estaba marcada anteriormente debido a entradas inexactas en la base de datos, igualado si el título de la opción para el tienda personalizado seguía siendo el mismo que el tienda predeterminado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: API de REST no se pueden realizar solicitudes con barra diagonal (/) en unidad de almacén cuando se utiliza Oauth1
   * _Nota_ de corrección: Antes de la corrección, no se podía realizar una llamada API correcta para un producto que tenía &quot;/&quot; en su unidad de almacén. Ahora, puede emitir un solicitud de obtención de API exitoso para los detalles del producto igualado aunque su unidad de almacén tenga una barra diagonal.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: Error en la actualización de la dirección del cliente al actualizar mediante la API de REST si &quot;validateDefaultAddress&quot; está habilitado
   * _Nota de corrección_: El extremo de API ahora funciona como estaba previsto después de que se haya resuelto el problema con la clave de ID que falta en la carga útil de API.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [Creación] del sitio web duplicado grupo precio del cliente grupo en la API de precios de nivel.
   * _Nota_ de corrección: Ahora la API de resto de precios por niveles no permite crear el sitio web duplicado grupo el precio del cliente grupo.
Anteriormente, era posible crear el sitio web duplicado grupo el precio del cliente grupo en la API de precios de nivel que no pasaría validación en Administración durante el guardado del producto.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: No se puede añadir un comentario de pedido con estado a través de la API de REST
   * _Nota_ de corrección: El problema se ha resuelto al permitir el cambio en el estado del pedido si solo es del estado actual. Anteriormente, no estaba honrando el estado de orden y evitando cambios en cualquier estado de orden, igualado si era del mismo estado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3236_: Error en la operación asíncrona cuando falta el unidad de almacén de la carga útil
   * _Nota_ de corrección: Anteriormente, las operaciones asíncronas y sincronizar fallaban debido a errores de guardado del producto si faltaba SKU en la carga útil. Después de la corrección, las operaciones de API de guardar REST del producto asíncrono y sincronizar fallan con el mensaje de excepción correspondiente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [NUBE] No se pueden actualizar los precios base mediante la API de REST (El valor de &#39;value_id&#39; en &#39;catalog_product_entity_decimal&#39; no se incrementa correctamente).
   * _Nota_ de corrección: Antes de esta corrección, cuando se llamaba a rest api /rest/default/V1/products/base-prices, el ID de incremento aumentaba erróneamente dejando un espacio entre valores. Después de la corrección, el ID de incremento aumenta como se esperaba, gradualmente. También se aumentó el rango de campo de value_id.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: los artículos del pedido no son visibles en los correos electrónicos de notas de crédito para la API POST V1/order/:orderId/refund
   * _Nota_ de corrección: Anteriormente, antes de esta corrección, cuando un cliente crea una nota de crédito desde una API solicitud notifica a send_correo electrónico, no contiene la cuadrícula de detalles del producto. Después de aplicar esta corrección, el cliente envía una nota de crédito API solicitud y encontrará los detalles del artículo del producto que aparecen en el correo electrónico.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_: No se han establecido valores predeterminados para los atributos de fecha y hora con productos RestAPI
   * _Nota de corrección_: Los valores predeterminados ahora se establecen correctamente para los atributos de fecha y hora mediante RestAPI
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>

### API, carro y cierre de compra

* _ACP2E-3343_: Error crítico 500: Magento\Framework\Webapi\Exception Relacionado con aceptar encabezado HTTP
   * _Nota_ de corrección: Después de la corrección, no hay ningún problema con la especificación del encabezado &quot;Aceptar&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>

### Cuenta

* _AC-10782_: El formulario de dirección del cliente permite código aleatorio en los campos de nombre
   * _Nota_ de corrección: El sistema ahora valida la entrada en los campos Nombre y Apellido en el formulario de dirección del cliente, evitando el uso de código aleatorio. Anteriormente, el sistema permitía el uso de código aleatorio en estos campos sin arrojar un error.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38331>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: actualización del Contraseña del administrador.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38352>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: mi cuenta añadir dirección se bloquea al guardar
   * _Nota_ de corrección: El sistema ahora guarda correctamente las direcciones de los clientes igualado cuando el campo área geográfica no se muestra, evitando que se produzca un bloqueo durante el proceso de guardado. Anteriormente, intentar agregar o editar una dirección sin el campo área geográfica que se mostraba daba como resultado un error de excepción.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38406>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: Bucle de redirección cuando URL mayúsculas
   * _Nota_ de corrección: El sistema ahora convierte automáticamente los caracteres en mayúsculas en las URL a minúsculas, evitando un bucle de redirección al acceder a la página de inicio. Anteriormente, tener caracteres en mayúsculas en la URL base segura provocaba un bucle de redirección continuo al intentar acceder a la página de inicio.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38538>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: segundo nombre no guardado para cuentas de invitado
   * _Nota_ de corrección: El sistema ahora guarda correctamente el segundo nombre de las cuentas de invitado durante el pago, haciéndolo accesible en el correo electrónico plantilla. Anteriormente, el segundo nombre no se guardaba en la tabla de cotizaciones y no se podía acceder a él en la plantilla de correo electrónico para cuentas de invitado.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38593>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Administrador: Página botones de acciones flotando a la izquierda en lugar de a la derecha
   * _Nota_ de corrección: El sistema ahora alinea correctamente los botones de acciones de Página al lado derecho del encabezado adhesivo en el panel de administración, mejorando la apariencia profesional. Anteriormente, estos botones flotaban incorrectamente hacia el lado izquierdo del encabezado adhesivo.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38701>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: error de información de desarrollo:di:en magento 2.4.7
   * _Nota de corrección_: el sistema ahora muestra correctamente los parámetros del constructor al ejecutar el comando dev:di:info, evitando que se produzcan errores. Anteriormente, la ejecución de este comando provocaba un error debido a una falta de coincidencia de tipos en el argumento.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38740>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: Casilla de verificación no traducible como cliente inclusión
   * _Nota_ de corrección: El sistema ahora permite que los campos &quot;Iniciar sesión como cliente inclusión casilla de verificación&quot; e &quot;Iniciar sesión como cliente información de la casilla de verificación&quot; se establezcan en el ámbito &quot;Almacenar vista&quot;, lo que permite traducciones para diferentes vistas de tienda. Anteriormente, estos campos solo se establecían en la ámbito &quot;Sitio web&quot;, lo que impedía las traducciones de vistas de tienda individuales.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/32329>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/32359>
* _AC-6071_: el cliente ha iniciado sesión pero muestra el error 404 en la interfaz.
   * _Nota de corrección: La panel_ del cliente del escaparate ahora Página carga según lo esperado cuando un cliente inicia sesión. Anteriormente, los clientes podían iniciar sesión, pero este Página mostraba un error 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/35838>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: No se puede Guardar la información de atributos del cliente en la sección Administrador Editar cliente;
   * _Nota_ de corrección: El ID de tienda del cliente ahora se implementa correctamente por sitio web ámbito para el formulario de edición del cliente administrador.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3329_: después de registro entrada, los productos agregados al lista de comparación como usuario invitados no son visibles.
   * _Nota_ de corrección: Los productos que se añadieron a la lista de comparación de productos antes de registro como cliente ahora se conservan después de registro entrada.
Anteriormente, después de registro entrada, los productos agregados al lista de comparación como usuario invitado no eran visibles.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: La configuración de Permitir países causa problemas en las configuraciones de direcciones de clientes
   * _Nota_ de la corrección: Ahora, seleccionar la configuración de Permitir países no influye en los países que se muestran fuera del ámbito determinado. Anteriormente, la configuración de Permitir países influía en el atributo de dirección del cliente fuera de ámbito
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3501_: VAPT: Error lógico de Empresa - fecha futura como fecha de nacimiento del cliente
   * _Nota_ de corrección: La fecha de nacimiento del cliente no se puede establecer después de hoy
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>

### Cuenta, API, GraphQL

* _ACP2E-3246_: API del cliente: número de errores de inicio de sesión que no se puede Restablecer a 0 después de un inicio de sesión correcto
   * _Nota_ de corrección: Ahora el número de error se restablece a cero en la tabla de entidades del cliente después de que el cliente haya inicio de sesión con éxito a través de los puntos finales de API.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>

### Cuenta, IU de administración B2B

* _ACP2E-3038_: Los usuarios administradores restringidos no siempre pueden ver catálogos compartidos personalizados
   * _Nota de la_ corrección: Los usuarios administradores restringidos ahora pueden vista y administrar clientes de manera consistente y todos los catálogos compartidos a los que se asignan los productos, siempre que tengan acceso al tienda específico. Anteriormente, un administrador restringido usuario con acceso a un tienda en particular no siempre podía ver todos los catálogos compartidos a los que se asignaban los productos o podía ver a los clientes que no podían guardar, lo que provocaba inconsistencias en el sistema.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7377de59>

### Cuenta, carrito y cierre de compra

* _AC-2341_: el atributo &quot;select&quot; custom customer address no se muestra para la nueva dirección de cliente
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/34950>

### Administrador IU

* _AC-10705_: [Problema] de adición permiso verificación de datos de &quot;datos recargar&quot; botón
   * _Nota_ de corrección: El sistema ahora incluye una verificación de permiso para el botón &quot;Recargar datos&quot;, lo que garantiza que solo se muestren y sean accesibles para los usuarios con los permisos apropiados. Anteriormente, el botón &quot;Volver a cargar datos&quot; era visible y se puede hacer clic para todos los usuarios, lo que provocaba un Página &quot;no permitido&quot; cuando los usuarios sin los permisos necesarios hacían clic en ellos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38283>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38279>
* _AC-11427_: [Problema] de etiquetas incoherentes para atributos en reglas de marketing
   * _Nota_ de corrección: El sistema ahora rellena correctamente las etiquetas de forma coherente para las opciones de categoría y atributos en carro de compras regla de precios
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/31232>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/31231>
* _AC-11588:_ La validación de datos es exitosa y Importar botón está presente durante Importar productos con Reemplazar comportamiento
   * _Nota_ de corrección: El sistema ahora valida correctamente los datos y oculta el botón &quot;Importar&quot; durante el proceso de importación del producto con el comportamiento &quot;Reemplazar&quot;, evitando cualquier reemplazo de datos no deseado. Anteriormente, el sistema validaba incorrectamente los datos y mostraba el botón &quot;Importar&quot;, lo que provocaba posibles incoherencias en los datos.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Error] Magento 2.4.7 no permite fotos de productos con extensión de archivo en mayúsculas.
   * _Nota_ de corrección: El sistema ahora acepta cargas de imágenes de productos con extensiones de archivo en mayúsculas, lo que garantiza un proceso de creación de productos sin problemas. Anteriormente, se rechazaban las cargas de imágenes con extensiones de archivo con mayúsculas, lo que obligaba a los usuarios a cambiar la extensión del archivo a minúsculas.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38831>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: Desplegable oculto en cuadrículas con acción de selección (por ejemplo, contenido > elementos > páginas)
   * _Nota_ de corrección: Ahora el sistema se ha corregido todo el desplegable similar para todas las cuadrículas.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38891>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39371>
* _AC-13131_: [Corrección de problemas] Advertencia: clave de matriz &quot;filtros&quot; no definida
   * _Nota_ de corrección: El sistema ahora maneja escenarios en los que un nuevo usuario aún no ha interactuado con los marcadores, evitando que se registre una advertencia de clave de matriz &quot;filtros&quot; no definida. Anteriormente, esta advertencia se registraba cuando un usuario nuevo no había interactuado con los marcadores.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39013>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: El archivo CSV de importación de productos con caracteres especiales falla debido a cambios en el código Validate.php archivo
   * _Nota_ de corrección: El sistema ahora valida e importa correctamente los archivos de CSV del producto que contienen caracteres especiales, lo que permite una transferencia de datos correcta. Anteriormente, al intentar importar un producto CSV archivo con caracteres especiales, se producía un error que impedía el proceso de importación.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13850_: No hay asterisco rojo para el campo obligatorio de número de teléfono
   * _Nota_ de corrección: El asterisco rojo anterior no se mostraba para el número de teléfono, pero el número de teléfono era obligatorio. Lo que ahora se fija el asterisco rojo se puede ver en el número de teléfono como un archivo obligatorio.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c699c206>
* _AC-6975_: [Problema] Establezca el modo de indexador predeterminado en &#39;programación&#39;
   * _Nota_ de corrección: Todos los nuevos indexadores están en **[!UICONTROL Update by Schedule]** modo predeterminado.  Anteriormente, el modo predeterminado era **[!UICONTROL Update on Save]**. Los indexadores existentes no se ven afectados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36419>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problema] Eliminar tablas de registro de cambios del indexador en mview cancelar la suscripción
   * _Nota_ de corrección: El sistema ahora elimina automáticamente las tablas de registro de cambios no utilizadas cuando se cambia un índice de &quot;actualización según lo programado&quot; a &quot;actualización al guardar&quot;, marcando el índice como no válido para garantizar que no se pierdan entradas. Anteriormente, cambiar un índice a &quot;actualizar al guardar&quot; dejaba tablas de registro de cambios sin usar en el sistema y marcaba todos los índices modificados como &quot;válidos&quot;.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/29789>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: No hay vincular al envío cuando se realizan pagos en el proceso de pago en el vista del teléfono móvil
   * _Nota_ de corrección: El sistema ahora garantiza que los títulos / enlaces de pago &quot;Envío&quot; y &quot;Revisión y pagos&quot; estén siempre visibles en la parte superior del Página en vista móvil, lo que permite a los usuarios navegar fácilmente entre los pasos y realizar las correcciones necesarias. Anteriormente, estos títulos / enlaces se oculta en vista móvil, lo que dificultaba que los usuarios conocieran su paso actual o volvieran a los pasos anteriores.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36856>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: pedidos de clientes consulta envío comentarios created_at se devuelve en la zona horaria +0, no en tienda zona horaria configurada
   * _Nota de corrección_: El sistema ahora muestra correctamente el campo &quot;created_at&quot; del comentarios de envío en la zona horaria configurada del cliente cuando se utiliza el consulta de pedidos del cliente. Anteriormente, el campo &quot;created_at&quot; se mostraba en la zona horaria +0, independientemente de la zona horaria configurada por el cliente.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36947>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-phrases rompe la integridad de las traducciones
   * _Nota_ de corrección: El `bin/magento i18n:collect-phrases -o` comando ahora recopila y agrega correctamente nuevas frases de los archivos JavaScript y .phtml, lo que garantiza que las traducciones se reflejen correctamente en el archivo de traducción. Anteriormente, el sistema no incluía frases de traducción multilínea de archivos de JavaScript y frases de archivos .phtml en el archivo de traducción, lo que provocaba traducciones incompletas o incorrectas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: Apóstrofe en tienda vista nombre se sustituye por &#39;
   * _Nota_ de corrección: el tienda de la cuadrícula vista ahora filtros mostrar correctamente los apóstrofos
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38395>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Favicon cargar no puede validar los archivos .ico
   * _Nota_ de corrección: El error de validación de archivo se ha actualizado a &quot;Error validación de Archivo. Verifique el Configuración de procesamiento de Imagen en la configuración de la tienda&quot;. Anteriormente, era simplemente &quot;Archivo validación falló&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: la galería en PageBuilder muestra la miniatura de la imagen antigua en lugar de la imagen recién cargada
   * _Nota_ de corrección: Regenerar vistas previas de imágenes para imágenes eliminadas y cargadas de nuevo con el mismo nombre a través de medios galería en Página contenido del generador.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: Guardar el producto por usuario de administración con diferentes función ámbito sobrescribe o elimina la información del producto relacionada existente en el producto
   * _Nota_ de corrección: Anteriormente, antes de la corrección, los productos relacionados se restablecían y quedaban vacíos cuando el administrador secundario usuario hacía clic en el botón de guardar sin cambiar en el producto relacionado. Después de esta corrección, el administrador secundario usuario hace clic en el botón de guardado y el producto no se restablece y se guarda correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: No se pueden exportar más de 200 pedidos
   * _Nota_ de corrección: Se han descuidado los límites del servidor para el tamaño de solicitud de los ID seleccionados enviados anteriormente al alterar el petición HTTP de GET a POST para solucionar el problema. Anteriormente, debido a las limitaciones del servidor para el tamaño petición GET, se encontraba el problema.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: El mensaje de cierre de compra Página validación es incorrecto.
   * _Nota_ de corrección: Si algún campo obligatorio se deja vacío, como &quot;dirección&quot;, el validación del lado del servidor no mostrará el mensaje. El lado del cliente validación se asegurará de que aparezca el notificación de error del campo requerido, indicando &quot;Este es un campo obligatorio&quot;. Anteriormente, el mensaje &quot;se requiere dirección&quot; aparecía si se dejaba en blanco cualquier campo obligatorio, además del mensaje validación lado del cliente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: Contraseña restablecer plantilla problema con el usuario de administración
   * _Nota_ de corrección: El problema se ha resuelto utilizando la clave correcta, que ahora incluye el nombre de usuario del administrador en el plantilla de correo electrónico y completa correctamente el asunto. Anteriormente, el problema se debía a una clave obsoleta que se estaba utilizando.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: Barras dobles en el segmento del cliente URL
   * _Nota_ de corrección: Las barras dobles no aparecen en la URL cuando se hace clic en &quot;Filtrar Restablecer&quot; en la cuadrícula.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: COD no está disponible para países específicos permitidos
   * _Nota_ de corrección: Ahora Cash on envío está disponible para países específicos permitidos siempre que sea necesario y AC-3216 está funcionando como se esperaba.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: No se puede actualizar el estado del pedido creado de forma personalizada
   * _Nota_ de corrección: &#39;
Ahora podemos actualizar estados de pedidos creados a medida, mientras que antes, el estado solo se podía cambiar si el estado actual era &quot;procesando&quot; o &quot;fraude&quot;.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38659>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: El estado de la dirección de envío no se actualiza automáticamente
   * _Nota de corrección_: antes de la corrección, la región de dirección de envío (o id de región) no estaba sincronizada con la información de facturación de direcciones. Ahora, tanto la región de la dirección de envío como el ID de región se actualizan correctamente cuando se cambia la información de la dirección de facturación.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: Restablecer botón no funciona en añadir/Editar administración usuario
   * _Nota_ de corrección: Anteriormente, el botón Restablecer no funcionaba en el Página de usuarios administradores de añadir/Editar. Ahora, en el panel Administración en Sistema -> Permisos -> Todos los usuarios, el botón Restablecer funcionará correctamente en la página Agregar/Editar usuario administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: detección incorrecta de enrutamiento de URL de administración de Magento y errores CORS
   * _Nota de corrección_: después de la corrección, si el dominio de administración personalizado es un subdominio del dominio principal, el administrador solo es accesible desde el subdominio configurado.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37663>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: roto validación para &quot;Cantidad máxima permitida en el carro de compras&quot;
   * _Nota_ de corrección: Anteriormente, cuando poníamos `Maximum Qty Allowed in Shopping Cart` vacío, no arrojaba ninguna excepción, aunque aquí no se acepta un valor vacío. Después de que se aplique esta corrección, poner una cadena vacía generará excepciones y no permitirá guardar el producto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Problema de IU de vista previa de Pagebuilder] Los botones de la columna Page Builder no se alinean correctamente
   * _Nota de corrección_: los botones de las columnas de Page Builder ahora están correctamente alineados. Anteriormente, se desalineaban dentro de las columnas de Page Builder.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: El informe Productos pedidos no se exporta. Error 404 en su lugar.
   * _Nota de corrección_: El informe de productos pedidos se excport a CSV y XML ahora funciona como se esperaba
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: Error de TinyMCE JS en la consola tras habilitar la minificación de Js con el modo de producción
   * _Nota de corrección_: Anteriormente, al habilitar la minificación de JavaScript en el modo de producción dentro del panel de administración, aparecían errores de JavaScript relacionados con TinyMCE 6 en la consola del explorador, lo que afectaba a la funcionalidad y a la experiencia del usuario. Ahora, este problema se ha resuelto, lo que garantiza que TinyMCE 6 funcione sin problemas sin generar errores, incluso cuando la minificación JS esté habilitada.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Solicitud de cambios adicionales para completar completamente la corrección ACP2E-3375
   * _Nota_ de corrección: &#39;-
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: Activación automática de nuevos permisos de ACL
   * _Nota_ de corrección: Nuevo permisos agregados a los módulos personalizados ya no concederán acceso automáticamente a todos los roles de usuario existentes a menos que se configuren explícitamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: Registro de acciones de administración El informe de usuario no muestra detalles para adminhtml_usuario_delete
   * _Nota_ de corrección: adminhtml_usuario_delete ahora registra correctamente los detalles importantes. Anteriormente, no se generaban registros para eliminaciones usuario.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: La regla del carro de compras con condición de envío no se aplica al realizar un pedido desde el administrador
   * _Nota_ de corrección: Anteriormente, si el regla de precio de carro de compras tiene un descuento de método de envío con el cupón, no se puede aplicar a través del Administrador IU. Después de aplicar esta corrección, el carro de compras precio regla descuento con un cupón para un método de envío específico se aplicará desde Admin IU correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [El código FRESH] HEX no se actualiza correctamente en SWATCH
   * _Nota_ de corrección: el código HEX introducido manualmente por usuario en el selector de color de muestra visual ya no es alterado por el sistema. Anteriormente, ciertos códigos HEX experimentaban ligeros ajustes debido a errores de Conversión entre los modelos de color.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Administrador IU, B2B

* _AC-13628_: B2B encabezado Iniciar sesión como cliente todavía tiene Magento promoción de la marca
   * _Nota_ de corrección: Anteriormente, el encabezado del escaparate muestra &quot;Ahora está conectado como &lt;customer name=&quot;&quot;> en &lt;store name=&quot;&quot;>&quot; con Magento promoción de la marca. &lt;/store>&lt;/customer> Que ahora está arreglado y el encabezado se muestra con ADOBE promoción de la marca.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/96dec499>

### Administración IU, Formas de pago / Pago, Pedido

* _AC-13520_: La autorización de transacción no se muestra en la pestaña de transacciones después de PayPal pedido de botón inteligente
   * _Nota_ de corrección: El sistema ahora muestra correctamente la autorización de transacción en el pestaña de transacciones después de realizar un pedido utilizando el botón inteligente PayPal. Anteriormente, la transacción de autorización no aparecía en el pestaña de transacciones después de hacer clic en el botón &quot;Autorizar&quot; y no se creaba ninguna transacción nueva de tipo &quot;Autorización&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Administración IU, rendimiento

* _ACP2E-3169_: Después de actualizar a 2.4.5-p8 se producen 500 errores al crear el pedido desde el administrador
   * _Nota_ de corrección: Anteriormente, al habilitar la minificación de HTML, no se podía realizar un pedido del administrador. Ahora, con la minimización de HTML habilitada, el pedido del administrador se puede realizar con éxito.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b21e5d91>

### Administración IU, Envío

* _ACP2E-2519_: El recuento de códigos de cupón no se actualiza en la columna &quot;Tiempo empleado&quot; en la pestaña Administrar códigos de cupón si un pedido se realiza con envío múltiple.
   * _Nota_ de corrección: Anteriormente, cuando se realizaba un pedido con envío múltiple, el recuento de códigos de cupón no se actualizaba en la columna &quot;Tiempo empleado&quot; del pestaña Administrar códigos de cupón. Ahora, el recuento correcto se muestra en &quot;Tiempo empleado&quot; reflejando los valores deseados con envío múltiple.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/4745100c>

### Administración IU, Puesta en escena y Vista previa

* _ACP2E-3424_: [Eliminación de plantilla en la nube] con imágenes faltantes hace que se elimine pub/medios
   * _Nota_ de corrección: Antes de esta corrección, si faltaba el nombre de la imagen previsualización para un plantilla de creación de páginas, se eliminaba la carpeta pub/medios. Después de la corrección, solo se eliminará el plantilla y se encontrará la imagen previsualización si se encuentra.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analytics / Informes

* _AC-9922_: error de CSP de Google Analytics https://region1.analytics.google.com
   * _Nota_ de corrección: El sistema ahora permite correctamente que las conexiones se &#39;https://region1.analytics.google.com&#39; cuando Google Analytics está habilitado, evitando errores de política de seguridad de contenido (CSP). Anteriormente, habilitar el Google Analytics y ver el sitio web desde la UE provocaba errores en la consola del CSP debido a la negativa a conectarse a &quot;https://region1.analytics.google.com&quot;.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37750>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: El informe avanzado no funciona
   * _Nota_ de corrección: El sistema ahora admite la generación de archivos de datos de informes avanzados para conjuntos de datos extra grandes cargando y escribiendo informes en lotes de 10.000. Anteriormente, el módulo de informes avanzados no podía generar archivos de datos para conjuntos de datos extra grandes, lo que provocaba errores de &quot;el servidor MySQL ha desaparecido&quot; durante la ejecución del trabajo cron análisis_collect_data.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Informe de productos pedidos por el administrador intervalo de fecha problema de visibilidad.
   * _Nota_ de corrección: El usuario podrá seleccionar cualquier fecha en el informe de productos pedidos. Anteriormente, después de actualizar la tabla, al seleccionar la fecha &#39;DESDE&#39; se restablecerá la fecha &#39;Hasta&#39;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Los cabezales de curl incorrectos hacen que el marcador de implementar newrelic:create:no funcione
   * _Nota_ de corrección: El sistema ahora formatea correctamente los encabezados de curl, lo que permite que el comando newrelic:create:implementar-marker cree con éxito un marcador de implementación en Nuevo Relic. Anteriormente, los encabezados de curl incorrectos impedían la creación de un marcador de implementación en Nuevo Relic.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37641>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3183_: El script NewRelic explorador monitoring inlineJS provoca errores de CSP
   * _Nota_ de corrección: Los scripts de NewRelic Browser Monitoring ahora los inyecta el aplicación en lugar del agente APM para el cumplimiento de CSP (Política de seguridad de contenido). Anteriormente, los scripts de NewRelic Browser Monitoring inyectados por el agente APM no eran compatibles con CSP y provocaban que los scripts no se ejecutaran.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: INSERTAR consultas en la tabla sales_bestsellers_aggregated_daily se vuelve lento en el proyecto con un gran volumen de pedidos de ventas
   * _Nota_ de corrección: Anteriormente, el informe diario agregado de bestsellers tardaba mucho tiempo en generarse para un gran volumen de pedidos realizados. Ahora el informe se genera de manera oportuna.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: Informes de pedidos que muestran el símbolo de moneda incorrecto
   * _Nota_ de corrección: El símbolo de moneda para los importes de los pedidos en el informe de pedidos se ha tomado incorrectamente de currency/options/base. Ahora se ha corregido para usar moneda / opciones / predeterminado para una sistema de informes precisa.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Nube] de cálculos incorrectos en el informe de uso de cupones
   * _Nota_ de corrección: El total de ventas en la cuadrícula del informe cupón ahora se calcula con precisión incorporando tanto el &quot;Monto de compensación de impuestos de descuento&quot; como el &quot;Monto de compensación de impuestos de descuento de envío&quot;. Anteriormente, estas cantidades faltaban en el cálculo, lo que daba lugar a discrepancias entre el total de ventas y los datos del pedido de ventas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: Problemas con el &quot;&lt;project_id>/var/tmp&quot;&lt;/project_id> compartido
   * _Nota_ de corrección: Analytics archivos temporales de DataExport utilizarán el directorio sys tmp, que es más adecuado para el acceso frecuente y los cambios. Para evitar colisiones en caso de que se ejecuten varias instancias en el mismo servidor, la ruta de TMP se actualizó para utilizar un ID único de instancia
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics / Informes, B2B

* _ACP2E-2300_: B2B incluye mapa del sitio productos o categorías no asignados al catálogo compartido
   * _Nota_ de corrección: Restrinja las categorías y productos generados por mapa del sitio a las categorías y productos asignados solo al catálogo compartido público y / o al catálogo categoría permiso configuración.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics / Informes, Nube

* _ACP2E-3067_: Magento descarta la mayoría de las transacciones cron de reliquias Nuevo #34108
   * _Nota_ de corrección: AC está sistema de informes correctamente las transacciones relacionadas con el trabajo cron a NewRelic. Anteriormente, algunas transacciones relacionadas con el trabajo cron se mostraban como &quot;OtraTransacción/Acción/desconocido&quot; en NR
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: La métrica en NR podría ser engañosa para transacciones en segundo plano- Seguimiento de ACP2E-3067
   * _Nota_ de corrección: Fondo transacciones (cron) usarán Nuevo nombre de aplicación Relic definido en la configuración
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_: Los productos asignados al catálogo compartido no se reflejan en el front-end cuando se ejecuta el índice parcial
   * _Nota_ de corrección: Los productos asignados al catálogo compartido a través de la API de REST ahora son visibles inmediatamente en el escaparate después de que se complete la indexación parcial. Anteriormente, los productos solo eran visibles después de una reindexación completa.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3044_: Bordes innecesarios en la sección Mis pedidos
   * _Nota_ de corrección: Anteriormente se creaba un contenedor adicional (referencias de pedidos) que aplicaba clases CSS adicionales, lo que provocaba que aparecieran líneas de borde innecesarias debajo del número de pedido dentro de la sección Mis pedidos, que ahora no es visible.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quotes cron elimina las cotizaciones de las órdenes de compra aún aprobadas
   * _Nota_ de corrección: Las cotizaciones utilizadas en las órdenes de compra ahora no serán eliminadas por sales_clean_quotes trabajo cron
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>

### B2B, Marco

* _AC-9607_: Filtrar la cuadrícula de la empresa y luego intentar la exportación de la CSV de la cuadrícula fallará y arrojará una excepción
   * _Nota_ de corrección: El sistema ahora permite CSV exportación exitosa de los datos de la cuadrícula Empresas en el panel de administración, igualado cuando se aplican filtros como &#39;Saldo pendiente&#39; y &#39;Tipo de empresa&#39;. Anteriormente, la aplicación de ciertos filtros e intentar exportar los datos de la cuadrícula provocaba un error y se producía una excepción.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/44cef3a9>

### Haz

* _AC-10826_: Validación de casilla de verificación del paquete de escaparate Error recuento de mensajes más de 1
   * _Nota_ de corrección: El sistema ahora solo muestra un mensaje de error de validación cuando se hace clic en el botón &quot;añadir al carro&quot; sin seleccionar ninguna opción de casilla de verificación para un producto agrupado. Anteriormente, el sistema mostraba varios mensajes de error de validación por cada casilla de verificación no seleccionada.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3ea26621>

### Carro y cierre de compra

* _AC-10660_: La excepción es no gestionarse correctamente al agregar un producto a carro de compras en la página de producto de comparación
   * _Nota_ de corrección: El sistema ahora maneja correctamente las excepciones al agregar un producto al carro de compras desde el página de producto de comparación, mostrando un mensaje del administrador de mensajes en el controlador. Anteriormente, una excepción daba como resultado que se devolviera un Página codificado JSON en lugar de capturarse y manipularse adecuadamente.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38200>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag no envía precios y totales de transacciones.
   * _Nota_ de corrección: El sistema ahora envía correctamente los precios y totales de las transacciones a Google Tag cuando GTag está habilitado, lo que garantiza un seguimiento preciso de los datos de comercio electrónico. Anteriormente, la moneda se enviaba incorrectamente como parte de &quot;todos&quot; los pedidos, en lugar de asociarse con el pedido individual.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37348>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Emitir] [directivas de dependencia de cierre de] compra actualizadas en Pago fallido correo electrónico plantilla
   * _Nota_ de corrección: El sistema ahora omite correctamente la dirección de envío y el método de envío del plantilla de correo electrónico de pago fallido para productos virtuales, asegurando que solo se incluya información relevante en el correo electrónico. Anteriormente, el correo electrónico de pago fallido para productos virtuales incluía incorrectamente la dirección de envío y el método de envío.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/32781>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: Magento 2 inicio de sesión dentro del cierre de compra con cliente existente dar error de consola en Firefox explorador
   * _Nota_ de corrección: El sistema ahora permite a los usuarios iniciar sesión durante el proceso de cierre de compra sin encontrar ningún error de consola en el explorador de Firefox. Anteriormente, intentar iniciar sesión como cliente existente durante el cierre de compra, se producía un error de consola en Firefox.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38557>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [Regresión de reglas de venta de problemas] en 2.4.7
   * _Nota_ de corrección: El sistema ahora valida correctamente las reglas de ventas, evitando la aplicación de un código de cupón a un carro de compras cuando la condición del producto no coincide con ningún nombre de producto. Anteriormente, se podía aplicar un regla de ventas y se podía dar un descuento en el importe del envío igualado cuando la condición del producto no coincidía con ningún nombre de producto.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38671>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Problema] de ventas regla cálculo de CartFixed : importe de descuento incorrecto
   * _Nota_ de corrección: El sistema ahora calcula correctamente el monto del descuento para las reglas de ventas con carro de compras montos fijos, asegurando que se apliquen descuentos precisos independientemente de los cambios en carro de compras artículos. Anteriormente, el monto del descuento podía variar incorrectamente cuando carro de compras artículos cambiaban, lo que a veces resultaba en descuentos significativamente mayores de lo esperado.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38694>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Problema] El cargador bloquea los métodos de envío después de cambiar el código postal, las tarifas de envío validación las reglas
   * _Nota_ de corrección: El sistema ahora maneja correctamente los métodos de envío personalizados sin tarifas validación reglas de envío, asegurando que el cargador no bloquee los métodos de envío después de cambiar el código postal en la dirección de envío durante el pago. Anteriormente, cambiar el código postal en la dirección de envío durante el pago hacía que el cargador bloqueara los métodos de envío y no desapareciera cuando se utilizaban métodos de envío personalizados sin tarifas de envío validación reglas.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38742>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: La función de código de cupón no funciona correctamente en el Página de pago en Magento 2.4.7
   * _Nota_ de corrección: El sistema ahora habilita el código de descuento / cupón campo de entrada en el Página de pago para productos virtuales y descargables, lo que permite a los usuarios aplicar códigos de descuento como se espera. Anteriormente, la entrada del código/cupón de descuento estaba deshabilitada y el texto del título del botón se mostraba como &quot;Cancelar cupón&quot;, lo que impedía a los usuarios aplicar códigos de descuento.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38826>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_: La casilla de verificación Términos y condiciones no permite HTML en la tienda
   * _Nota_ de corrección: El sistema ahora admite el formato HTML en el texto de la casilla de verificación &quot;Términos y condiciones&quot; en el escaparate, lo que permite una mayor personalización y legibilidad. Anteriormente, el texto de la casilla de verificación se mostraba en texto sin formato formato, sin tener en cuenta las etiquetas HTML utilizadas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-12541_: El precio del carro de compras regla creado para el usuario iniciado sesión se aplica incorrectamente para el usuario no iniciado sesión
   * _Nota_ de corrección: El sistema ahora elimina correctamente la regla de precio carro de compras para los usuarios conectados cuando se cierra automáticamente debido a la caducidad de cookie, lo que garantiza que el descuento no se aplique a los usuarios que no han iniciado sesión. Anteriormente, el regla de precio carro de compras todavía se aplicaba igualado cuando se cerraba la sesión del usuario, lo que provocaba que se aplicara un descuento incorrecto a los usuarios que no habían iniciado sesión.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38944>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [Emitir] [FUNCIÓN Optimización] del rendimiento de carritos de compras grandes mediante la prevención...
   * _Nota_ de corrección: El sistema ahora optimiza el rendimiento para carros de compras grandes al evitar duplicado llamadas getActions, mejorando la velocidad y la eficiencia de las operaciones de carro de compras. Anteriormente, para un carro de compras con varios elementos, se llamaba a la función getActions varias veces, lo que ralentizaba el rendimiento del sistema.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39292>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39290>
* _AC-8103_: Traducción del IVA en el procesador de direcciones
   * _Nota_ de corrección: El sistema ahora permite la traducción del texto &quot;IVA&quot;, &quot;T&quot;, &quot;F&quot; en los renderizadores de direcciones, lo que permite a los usuarios traducir estos términos al idioma específico del tienda. Anteriormente, estos términos no eran traducibles, lo que obligaba a los usuarios a emplear una solución alternativa.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36942>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: Pedidos duplicados con el mismo ID de cotización al mismo tiempo con poca diferencia horaria
   * _Nota_ de corrección: se solucionó el problema cuando los clientes de Adobe Systems Commerce encontraron duplicado pedidos realizados con el mismo ID de cotización.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: el carro de compras persistente se borra durante el paso de cierre de compra
   * _Nota_ de corrección: Después de la corrección, seleccionar el método de pago durante el pago mientras no está conectado no finaliza la sesión persistente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: Reorder agrega productos no asignados a carro de compras
   * _Nota_ de corrección: Anteriormente, para las diferentes tiendas, los productos se pueden repedir desde el otro tienda. Después de aplicar esta corrección, solo se puede volver a pedir el mismo tienda del mismo producto ámbito cuando el cliente cuenta recurso compartido está habilitado
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: En administración, el &quot;Carro de compras&quot; en el lado izquierdo no se actualiza al seleccionar los artículos y &quot;Mover al carrito de compras&quot; en el lado derecho
   * _Nota_ de corrección: El &quot;carro de compras de compras&quot; en el lado izquierdo se actualiza al seleccionar los artículos y &quot;Mover a carro de compras&quot; del lado derecho en el lado del administrador. Anteriormente, este funcionalidad no funcionaba porque los elementos de carro de compras transformados no quedaban vacíos de la sesión.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [Regla de ventas en la nube] no aplicada al primer pedido de envío múltiple
   * _Nota_ de corrección: Después de la corrección, el descuento se muestra correctamente para cada pedido de la misma cotización de envío múltiple.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Producción en la nube] Las solicitudes paralelas para añadir mismo producto al carro de compras dan como resultado dos elementos separados en la API de descanso del carro
   * _Nota_ de corrección: El sistema ahora procesa correctamente varias solicitudes paralelas para agregar el mismo producto al carro de compras en un solo elemento de línea, evitando la creación de elementos de línea separados para el mismo unidad de almacén. Anteriormente, realizar solicitudes paralelas para agregar el mismo producto al carro de compras a través de la API de REST resultaba en varios elementos de línea para el mismo unidad de almacén.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: No se puede enviar el cookie. Tamaño de los &#39;mensajes de mago&#39; al intentar reordenar
   * _Nota_ de corrección: El proceso de reordenación no generará sus propios errores ahora. Se basará en carro de compras comprobaciones de elementos incorporadas en la lista.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: la dirección de envío predeterminada no está seleccionada al finalizar la compra
   * _Nota de corrección_: La dirección de envío predeterminada se está seleccionando evento en el contexto del búsqueda de direcciones habilitado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [NUBE Problema] de la API graphql addProductsToCart con la opción personalizada
   * _Nota_ de corrección: GraphQL agrega a carro de compras correctamente el mismo producto con diferentes opciones personalizadas
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Varias direcciones agregadas al cuenta al finalizar la compra como cliente nuevo
   * _Nota de corrección_: El sistema ahora guarda una nueva dirección de cliente solo una vez si no se pudo crear el pedido, evitando la creación de múltiples direcciones idénticas en el evento de errores de ubicación de pedido. Anteriormente, el sistema guardaba una nueva dirección cada vez que se realizaba un pedido ubicación intento, independientemente de si el pedido se había creado correctamente o no.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Reordenar el pedido del cliente a través del formulario de pedido de invitado da como resultado un carro de compras vacío
   * _Nota_ de corrección: Anteriormente, al realizar un repedido a través del Página de pedidos y devoluciones, se redirigía al cliente al Página de inicio de sesión. Después de aplicar esta corrección, el cliente registrado es redirigido correctamente al Página del carrito de Ver al realizar un nuevo pedido. El flujo funciona igual que gustar que los clientes invitados.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: Usuario administrador con recursos de rol limitados no puede vista carros de compras
   * _Nota_ de corrección: Anteriormente, el administrador restringido no podía ver el carro de compras abandonado desde el panel de administración de un sitio web asociado. Después de aplicar esta corrección, el administrador restringido puede ver el carro de compras abandonado desde el panel de administración.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_: [Pedido rápido en la nube] gran cantidad de rendimiento unidad de almacén
   * _Nota_ de corrección: El rendimiento del cierre de compra se ha mejorado cuando los atributos utilizados en carro de compras condiciones de reglas de precios no están presentes para todos los productos y cuando la función MAP (precio mínimo anunciado) está habilitada.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Elementos duplicados en carro de compras
   * _Nota_ de corrección: El sistema ahora procesa correctamente varias solicitudes paralelas para agregar el mismo producto al carro de compras en un solo elemento de línea, evitando la creación de elementos de línea separados para el mismo unidad de almacén. Anteriormente, realizar solicitudes paralelas para agregar el mismo producto al carro de compras en StoreFront resultaba en varios elementos de línea para el mismo unidad de almacén.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: se envía la confirmación del pedido correo electrónico de cierre de compra a los correos electrónicos introducidos en Nombre/Apellido
   * _Nota_ de corrección: Ya no se envía la confirmación del correo electrónico del pedido de cierre de compra, que anteriormente se enviaba cuando se introducía un patrón de correo electrónico gustar en los campos Nombre y Apellido.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: El formulario de dirección de envío de pago recibe actualización con la dirección incorrecta
   * _Nota_ de corrección: shippingAddressFromData ahora se guarda en la almacenamiento local por sitio web. Anteriormente, una dirección del sitio web incorrecto se podía completar automáticamente en el formulario de dirección de envío durante el pago si se usaba un código de tienda en el URL y el pago se iniciaba desde varios sitios web durante la misma sesión de invitado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_: Producto de tarjeta regalo | La combinación de carros de compras combina tarjetas regalo
   * _Nota_ de corrección: los productos de tarjetas regalo ahora se fusionaron correctamente en el carro de compras
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_: No se respeta la persistencia del carro de compras al cerrar la sesión
   * _Nota de corrección_: funcionalidad agregada que falta Recordarme desde el inicio de sesión del cliente hasta la ventana emergente de autenticación y los inicios de sesión de cierre de compra.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: Los datos de cotización existentes no se actualizan / no son visibles, sino que crean un nuevo registro de cotizaciones cuando trigger_recollect = 1
   * _Nota_ de corrección: Los artículos carro de compras del cliente ya no desaparecen como resultado de la eliminación de un producto después de haberlo agregado al carro de compras.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3618_: [NUBE] Reordenar botón funcionalidad
   * _Nota_ de corrección: Volver a ordenar un pedido desde el área del administrador ahora agregará productos con stock a la cotización igualado aunque hay algunos productos en el pedido original que ya no tienen stock. Antes de la corrección, no se agregaba ningún producto a la nueva cotización si el producto sin stock estaba en el pedido original.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: Search tiendas no funcionan por código postal
   * _Nota_ de corrección: La búsqueda de ubicaciones de recogida por código postal no funcionaba correctamente para Neerlandés localizaciones. Después de la corrección, la ubicación de recogida búsqueda proporcionará resultados basados en el código postal.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/344fce23>

### Carro y cierre de compra, Cierre de compra/ Un Página Cierre de compra

* _AC-9386_: [El campo de correo electrónico de BUG] aleatorio no se representa o tarda mucho tiempo en aparecer en el Página de pago o de envío de pago
   * _Nota_ de corrección: Comercio ahora procesa el **[!UICONTROL Email]** campo en las páginas de envío y pago de pago como se esperaba. Anteriormente, este campo estaba ausente o se procesaba lentamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/e1babcfd>

### Carro y cierre de compra, pedido

* _ACP2E-3097_: Selector de fecha para productos con varias Opciones personalizables con campos de fecha que no funcionan al realizar un pedido desde el administrador
   * _Nota de corrección_: El sistema ahora muestra correctamente el selector de fecha para todos los campos de fecha al configurar un producto con varias opciones de fecha personalizables en el proceso de creación de pedidos de administración. Anteriormente, el selector de fecha solo se mostraba para el primer campo de fecha, dejando los campos restantes sin selector de fecha.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### Carro y Pago, Envío

* _AC-12119_: compra instantánea de &quot;envío más barato&quot; interrumpida para productos configurables
   * _Nota_ de corrección: La función compra instantánea seleccionó incorrectamente la opción de entrega en tienda más cara para productos configurables en lugar del método de tarifa plana más barato. Esta solución garantiza que se elija el método de envío correcto en función del precio real&quot;.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38811>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catálogo

* _AC-10910_: la limpieza de la tabla de base de datos cron_schedule no limpia los trabajos no existentes
   * _Nota de corrección_: el sistema ahora limpia automáticamente la tabla de base de datos cron_schedule, eliminando las entradas de los trabajos que ya no existen en el sistema. Esto garantiza un rendimiento óptimo al mantener un número mínimo de filas en la tabla. Anteriormente, las entradas para trabajos de módulos inactivos o eliminados no se limpiaban, lo que producía una acumulación de datos innecesaria en la tabla cron_schedule.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38217>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: El precio de nivel no se elimina del producto configurable
   * _Nota_ de corrección: El sistema ahora elimina correctamente el precio de nivel de un producto cuando se convierte de un producto simple a un producto configurable, lo que garantiza una visualización precisa del precio en la interfaz. Anteriormente, el precio de nivel de un producto configurable no se eliminaba cuando un producto se convertía de un producto simple a un producto configurable, lo que provocaba un desajuste en el precio mostrado.
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
   * _Nota de corrección_: el sistema ahora utiliza correctamente las palabras &quot;item&quot; y &quot;items&quot; en el elemento de filtro de navegación por capas, lo que mejora la claridad y precisión de las descripciones de los filtros. Anteriormente, estas palabras se usaban incorrectamente, lo que generaba confusión potencial para los usuarios que navegaban por las opciones de filtro.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38789>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: El formato de fecha y hora para la opción personalizada no funciona
   * _Nota de corrección_: El sistema ahora aplica correctamente el formato de fecha configurado a las opciones personalizadas del producto de tipo Fecha, asegurándose de que la fecha formato se muestre correctamente en el front-end. Anteriormente, los cambios en la fecha formato la configuración no se reflejaban en el front-end para las opciones personalizadas de productos de tipo Fecha.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/32990>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38925>
* _AC-13068_: Faltan opciones desplegables
   * _Nota de corrección_: El sistema ahora muestra correctamente todos los valores de la lista desplegable al crear un nuevo atributo con más de 20 valores. Anteriormente, solo se mostraban los 20 primeros valores u otro valor de Página seleccionado, lo que hacía que faltaran los valores restantes.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [problema] Utilice el sore id actual para categoría caché en tiempo de ejecución
   * _Nota de corrección_: El sistema ahora utiliza correctamente el ID de tienda actual para categoría caché de tiempo de ejecución, evitando la anulación de datos cuando se utiliza la emulación o el código personalizado guarda el categoría en diferentes almacenes. Anteriormente, el objeto almacenado en tiempo de ejecución podría haber sido del tienda incorrecto, lo que provocaba la anulación de los datos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39310>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: bin/magento sampledata:implementar --no-update lanza una excepción
   * _Nota_ de corrección: El sistema ahora acepta correctamente un valor booleano cuando utiliza la opción --no-update en el comando sampledata:implementar, evitando cualquier error durante el implementación de datos de muestra. Anteriormente, se producía un error al utilizar este comando, ya que el sistema esperaba incorrectamente un valor entero.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39344>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39345>
* _AC-13355:_[ Problema] Solucionar el uso del tipo de caché EAV
   * _Nota_ de corrección: El sistema ahora utiliza correctamente el tipo de caché EAV en todos los lugares relevantes, lo que garantiza un almacenamiento en caché de datos coherente y eficiente. Anteriormente, el tipo de caché EAV no se usaba de forma coherente, lo que provocaba posibles ineficiencias e inconsistencias en la almacenamiento en caché de datos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/32322>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: el Search de Avanzadas de catálogo con datos vacíos va al resultado de búsqueda Página[2.4.dev Rama]
   * _Nota_ de corrección: El sistema ahora retiene correctamente a los usuarios en el Página de Search de Avanzadas y muestra un mensaje de error cuando intentan realizar un búsqueda sin introducir ningún dato. Anteriormente, cuando se realizaban búsqueda vacías, los usuarios redirección al Catálogo Avanzadas Search Página con un mensaje en el que se les pedía que modificaran su búsqueda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_: [problema Diseño] del producto basado en attribute_set
   * _Nota_ de corrección: El sistema ahora permite el ajuste del diseño del producto en función del conjunto de atributos, proporcionando una forma más práctica y eficiente de administrar la visualización del producto en el tienda front-end. Anteriormente, el diseño solo se podía ajustar por unidad de almacén o por tipos de productos, lo que no siempre era práctico para muchos productos o artículos específicos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38790>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: Falta la clave única en eav_attribute_option_value tabla
   * _Nota_ de corrección: El sistema ahora incluye una clave única en las columnas &#39;option_id&#39; y &#39;tienda_id&#39; de la tabla &#39;eav_attribute_option_value&#39;, evitando la posibilidad de que una opción tenga varios valores para el mismo tienda vista. Anteriormente, un código defectuoso podía dar lugar a que una opción tuviera varios valores para el mismo vista de tienda, lo que causaba problemas al editar productos o atributos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/24718>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [problema Utilice] la clase de visibilidad para categoría indizador de producto, en lugar de valores codificados de forma rígida.
   * _Nota de corrección_: El sistema ahora utiliza la clase de visibilidad para el indizador de producto categoría en lugar de valores codificados, lo que mejora la modularidad. Anteriormente, los valores codificados se utilizaban en el indizador de productos categoría, lo que limitaba la flexibilidad y la adaptabilidad.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37200>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: El código de moneda no cambia en Nuevo widget del producto
   * _Nota_ de corrección: El sistema ahora actualiza correctamente el código de moneda en el widget Producto de Nuevo cuando se cambia la moneda en el front-end, lo que garantiza la coherencia en la visualización de la moneda en todo el sitio. Anteriormente, cambiar la moneda en el front-end no afectaba al código de moneda mostrado en el widget Producto de Nuevo.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37898>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: El precio regular no se muestra en PLP para el producto configurable
   * _Nota de_ corrección: El precio regular ahora se muestra en las páginas de listado de productos para productos configurables que tienen productos secundarios con precio especial.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: Stock información no se muestra directamente en la cuadrícula de Visual Merchandising
   * _Nota de_ corrección: Stock ahora se muestra según el tienda seleccionado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: Widget contenido no se actualiza en cms Página
   * _Nota_ de corrección: El sistema ahora actualiza el contenido de widget en un Página CMS cuando un producto se establece como nuevo y se guarda, asegurando que el Página muestre el colección actualizado del producto. Anteriormente, la Página no se actualizaba para mostrar el nuevo producto debido a las identidades de caché incorrectas utilizadas para la utilidad en la caché.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: Problemas para ahorrar precios avanzados en productos paquete
   * _Nota_ de corrección: Mejora del rendimiento del ahorro de productos del paquete.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [On-Premise] proceso de reindexación es ineficaz al crear reglas de precios de catálogo
   * _Nota_ de corrección: Ahora, guardar el regla de precios del catálogo no invalidará a los indexadores, sino que solo reindexará los productos afectados
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Actualización de la hora de fecha y hora de los atributos del producto mediante la importación CSV
   * _Nota_ de corrección: Ahora los atributos de fecha y hora tendrán parte de tiempo en los datos exportados. También será posible actualizar la hora de dichos atributos mediante la importación. Además, si &quot;Recinto de campos&quot; está habilitado, los valores de atributo de doble la columna &quot;additional_attributes&quot; se incluirán entre comillas.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38306>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: No hay mensaje de error apropiado cuando el ID del sitio web es incorrecto en el solicitud
   * _Nota_ de corrección: Ahora se agregó el mensaje de error apropiado para que se muestre cuando el ID del sitio web sea incorrecto en el solicitud. Anteriormente, no había ningún validación cuando la identificación del sitio web era incorrecta en el solicitud.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: La imagen del producto se pierde después de eliminar una actualización programada existente que no afecta a la imagen
   * _Nota_ de corrección: Las imágenes del producto no se eliminan al eliminar la actualización del ensayo.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] Precio incorrecto del producto paquete cuando se utiliza con precios de nivel
   * _Nota de corrección_: Anteriormente, al calcular ciertos descuentos porcentuales, redondeados a 2 puntos decimales se generarán diferentes precios finales para el carro de compras y la lista de productos Página / detalles del producto Página. Después de aplicar esta corrección, el precio final del producto paquete es el mismo que en los detalles del producto Página, Página de listado de productos y mini carro de compras Página.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38091>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: La regla de promociones del catálogo no funciona con el atributo cantidad_and_stock_status
   * _Nota_ de corrección: El atributo cantidad_and_stock_status ahora será tomado en cuenta por el catálogo promoción regla, que anteriormente no se tenía en cuenta al generar un nuevo producto desde el lado del administrador.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/35627>
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: La entidad del producto updated_at los valores de columna no se actualizan mientras se actualiza el precio a través de la API de REST
   * _Nota_ de corrección: La columna &quot;Última actualización en&quot; del producto del administrador se actualiza con la fecha y hora adecuadas al actualizar los productos existentes a través de la API de REST. Anteriormente, la columna &quot;Última actualización en&quot; no se actualizaba correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Es posible establecer valores no únicos a través de la importación de productos
   * _Nota_ de corrección: El sistema ahora aplica correctamente la restricción de valor único para los atributos únicos del producto durante la importación del producto, evitando tener valores duplicado para dicho atributo. Anteriormente, era posible establecer valores no únicos para los atributos del producto que estaban configurados para tener valores únicos a través de la importación del producto.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38445>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: Los productos en el front-end utilizan datos tienda específicos cuando el modo de almacén único está habilitado
   * _Nota_ de corrección: Anteriormente, cuando habilitamos el modo tienda único para el vista de tienda predeterminado, los cambios no se migraban al ámbito de nivel de sitio web. Después de aplicar esta corrección, cuando habilitamos el modo de tienda único, el tienda predeterminado de datos específicos del vista se sincronizará con datos específicos del nivel de sitio web y resolverá los posibles conflictos de productos y categorías.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: No se puede establecer &quot;Ordenar por&quot; predeterminado en una categoría utilizando la API del resto
   * _Nota_ de corrección: Actualización correcta default_sort_by en un categoría a través de REST / SOAP APi solicitud
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Nube] El comerciante tiene problemas con el recuento de listas de deseos
   * _Nota_ de corrección: Agregar un producto a la lista de deseos de una tienda ya no aumenta el recuento de listas de deseos en otras tiendas abiertas en el mismo explorador. Anteriormente, si ambas tiendas se cargaban en la misma explorador, el recuento de la lista de deseos también aumentaría en las otras tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: Categoría Página en interfaz muestra ranuras vacías cuando se utiliza paquete producto
   * _Nota_ de corrección: Los paquetes de productos que no se pueden vender en el contexto del tienda actual ya no se indexan.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [Nube] Problema de cotización en la arquitectura de varios sitios web
   * _Nota_ de corrección: Anteriormente, la arquitectura de varios sitios web con diferentes monedas y grupos de clientes no podía aplicar correctamente descuentos al tienda. Después de implementar esta corrección, la arquitectura de varios sitios web con diferentes descuentos en el precio grupo del cliente se aplicará con éxito a diferentes tiendas.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38506>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice al editar paquete productos
   * _Nota_ de corrección: No hay ningún error de javascript en explorador consola al eliminar la opción de paquete producto.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38505>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Bundle Precio incorrecto del producto en la confirmación del pedido
   * _Nota_ de corrección: Se muestra la cantidad correcta para paquete opciones en orden en Storefront cuando se utiliza una moneda distinta a la base.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Error de adición de Vídeo YouTube
   * _Nota de_ corrección: Las imágenes y los vídeos de los productos se configuran en ámbito global. Dado que no puede tener un video de producto en una ámbito y no en otra, la configuración de la clave de API de Youtube se ha establecido en ámbito global.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [actualización de Cloud] URL solo para tienda_id=0
   * _Nota_ de corrección: La ruta de acceso URL ahora se almacena con el ID de tienda correcto. Anteriormente, el ID de tienda era incorrecto, por lo que quedaban rutas de URL incorrectas en la base de datos al mover categorías.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all se ejecutó y creó un error.
   * _Nota_ de corrección: Los datos de vincular incorrectos del producto en las llamadas a la API de REST ya no causan errores esencial.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [Problema de Cloud] Mobile solo no se puede pellizcar en la imagen de PDP
   * _Nota_ de corrección: El sistema ahora admite pellizcar para acercar funcionalidad en detalles del producto Página imágenes en vista móvil en Cromo, mejorando el experiencia del usuario móvil. Anteriormente, al tocar doble la imagen en móviles vista en Cromo no se acercaba la imagen como se esperaba.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Falta etiqueta en LayeredNavigation con nombre de opción 0
   * _Nota_ de corrección: El problema se ha resuelto omitiendo un verificador de valores vacío para el valor de atributo 0. Anteriormente, se consideraba vacío y estaba causando el problema.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: Los clientes ven los precios de otros grupos de clientes
   * _Nota_ de corrección: Se ha corregido un problema por el que la información relacionada con la grupo del cliente se guardaba en un segmento incorrecto debido al valor anterior de X-Magento-Vary en solicitud
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Error al eliminar opciones de paquete
   * _Nota_ de corrección: El sistema ahora elimina correctamente paquete opciones sin activar un error o hacer que el Página deje de responder. Anteriormente, intentar eliminar paquete opciones daba como resultado un error de &quot;Página no respondía&quot; y evitaba que el producto se guardara.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: [Cloud] Imagen Archivo no existe en Nuevo registro de Error de reliquias
   * _Nota de corrección_: El sistema ahora sincroniza las imágenes de marcador de posición personalizadas con los almacenamiento locales, lo que garantiza que se representen correctamente al usar almacenamiento remotos como AWS S3. Anteriormente, las imágenes de marcador de posición personalizado no se representaban al usar almacenamiento remoto, lo que provocaba una visualización de imagen rota y registros de errores.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3103_: Productos Nuevo fuente RSS no se actualiza con nuevos productos debido a la caché
   * _Nota_ de corrección: la fuente Rss para Nuevo productos ahora se actualiza cuando un producto se establece como nuevo y se guarda
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: [Galería multimedia del producto en la nube] La respuesta de GQL no está ordenada por posición de la imagen
   * _Nota_ de corrección: El sistema ahora ordena correctamente los elementos en la galería de medios por posición en la respuesta GraphQL, lo que garantiza un orden de visualización preciso. Anteriormente, los elementos de la galería de medios no se ordenaban por posición, lo que provocaba un orden de visualización incorrecto.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37671>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Los elementos de Categoría Cloud] Sub no se muestran en la edición de widgets en el backend de administración
   * _Nota_ de corrección: El árbol categoría del nuevo widget Página ya no debería tener problemas para cargar categorías de nivel 5+. Anteriormente, faltaban algunas categorías al cargar las tres últimas categorías de Nivel 5.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_: [nube] Problema de zoom y movimiento de dos dedos en el dispositivo móvil real
   * _Nota_ de corrección: El sistema ahora garantiza un funcionalidad de zoom de imagen consistente en dispositivos móviles, proporcionando una experiencia del usuario fluida y predecible. Anteriormente, la función de zoom de imagen era incoherente y, de repente, se alejaba después de un determinado punto cuando se visualizaba en un dispositivo móvil.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: Cuando anulamos la asignación de productos del catálogo compartido, los productos de la lista de deseos no se borran
   * _Nota de corrección_: Ahora no hay elementos visibles en la lista de deseos si un producto no está disponible en el catálogo compartido. Anteriormente, la página de lista de deseos mostraba incorrectamente un recuento de &quot;1 elemento&quot; incluso cuando en realidad no había elementos disponibles en la lista de deseos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: Productos relacionados Seleccionar todo/Anular selección de todos los problemas
   * _Nota_ de corrección: Anteriormente, los botones &quot;Seleccionar todo&quot;/&quot;Anular selección de todo&quot; para los productos relacionados no funcionaban correctamente si un producto se seleccionaba manualmente. Después de la corrección, estos botones ahora funcionan de manera consistente, igualado después de la selección manual, asegurando que todos los productos estén seleccionados correctamente o no seleccionados.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [Cloud] Stock alerta correo electrónico traducción al idioma equivocado
   * _Nota_ de corrección: Al enviar alertas de Stock/precios para un sitio web con varias vistas de tienda utilizando diferentes idiomas, el idioma de la tienda vista donde se creó la alerta se utilizará en el correo electrónico.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: Las categorías deshabilitadas ya no tienen sus nombres en gris en el árbol de categoría
   * _Nota_ de corrección: Anteriormente, las categorías deshabilitadas no estaban atenuadas en el árbol de categoría. Ahora, se muestran con un efecto de gris.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: La carga configurable del formulario de edición de productos causa tiempo de espera y agotamiento de la memoria
   * _Nota_ de corrección: Antes de la corrección, las variaciones de productos configurables se construían en función de todas las combinaciones posibles de opciones de atributos. En los casos en que los atributos tenían muchas opciones, esto resultaba en una operación larga y que consumía muchos recursos. Ahora, las variaciones de producto configurables se construyen en función de los atributos de productos secundarios existentes. Esto da como resultado muchos menos cálculos, por lo tanto, un mejor uso de los recursos.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama no carga el vídeo correctamente cuando se utiliza Muestras y la opción está preseleccionada mediante URL
   * _Nota_ de corrección: Los vídeos de productos ahora se representarán correctamente en los detalles del producto configurables Página, si el URL contiene las opciones seleccionadas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: el Widget de carrusel PageBuilder muestra los productos que no coinciden con las condiciones
   * _Nota_ de corrección: el lista del producto utilizado en widgets ahora respeta categoría condición
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: Error de validación activada para todos los productos del grupo cuando se tiene una cantidad no válida
   * _Nota de corrección_: Ahora, el error de validación se activa correctamente para todos los productos del grupo cuando un producto tiene una cantidad no válida, lo que no ocurría anteriormente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_: [CLOUD] El precio especial no se muestra en Producto configurable
   * _Nota_ de corrección: Después de la corrección, cambiar el valor &quot;Utilizado en la ficha de productos&quot; por el atributo de precio especial no afectará a mostrar el precio especial de los productos configurables.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: Indizadores Las tablas temporales no se limpian si finaliza el proceso
   * _Nota de corrección_: Las tablas temporales del indizador CatalogRule ahora se limpian si finaliza el proceso del indizador
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [Unidad central QUANS] prueba fallos en 2.4.7-p3
   * _Nota_ de corrección: No es necesario incluir notas de la versión para este prueba, ya que se trata de una mejora prueba unidad.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: Problema de rendimiento en Stock recuperación de cantidad para productos agrupados con múltiples fuentes
   * _Nota de corrección_: la página de edición de productos agrupados y agrupados ahora está optimizada cuando los productos asignados tienen un gran número de orígenes de inventario.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Refijar https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Nota_ de corrección: Se mejoró el rendimiento del Página de categoría de administrador en caso de un gran número de categorías de anclaje
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### Catálogo, contenido

* _ACP2E-3063_: [la caché de nube] no se invalida.
   * _Nota_ de corrección: Anteriormente, al guardar un Página CMS con un diseño de diseño actualizado, no se reflejaba adecuadamente en el front-end. Después de aplicar esta corrección, el diseño de diseño apropiado será visible en la parte delantera cuando cambiemos el diseño y guardemos el Página CMS.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Categorías Anclaje/no Anclaje en la nube] invertidas en el contenido Widget
   * _Nota_ de corrección: Anteriormente, cuando seleccionábamos Mostrar en -> Anclaje categorías, se mostraban todas las categorías que no reflejaban la relación padre-hijo entre el anclaje y el no anclaje. Una vez aplicada esta corrección, Mostrar en -> Anclaje categorías solo muestra Anclaje categorías (seleccionables) y Mostrar en -> categorías no Anclaje muestra Categorías no Anclaje (seleccionables)
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Las categorías no funcionan con widgets
   * _Nota_ de corrección: Anteriormente, si guardábamos el bloque CMS para diferentes categorías anclaje/no anclaje, no funcionaba para las categorías secundarias cuando se mostraba en el front-end. Después de aplicar esta corrección, el bloque se muestra en la parte delantera para diferentes categorías.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d01ee51e>

### catálogo, marco

* _AC-9111_: Obtención de pedidos(Envíos|Notas de crédito|Factura)Cobranza: la colección no debe cargarse
   * _Nota_ de corrección: El sistema ahora garantiza que los cobros de envíos y notas de crédito no estén precargados cuando se recuperan de un pedido, lo que permite aplicar filtros o pedidos adicionales a estos cobros. Anteriormente, estas colecciones se cargaban automáticamente, lo que impedía futuras modificaciones.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37561>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: []Cloud Follow-up: Falta de coincidencia en la comparación de datos cuando se comprueba si los datos tienen cambios
   * _Nota_ de corrección: Anteriormente, se llamaba al objeto guardar cada vez sin ningún cambio de datos (para cualquier campo de datos numérica, gustar int/float/doble). Activa la _hasDataChanges de indicador para que sea verdadera y llama a la función de guardado. Tampoco comprueba los números flotantes encapsulados por cadena. Después de que se aplique esta corrección, la función de guardar llamará solo si los datos se modifican. El valor de datos para int/float/doble-check con el valor que pasa a la función y hace una coincidencia de tipos estricta
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8931218>

### Catálogo, GraphQL

* _ACP2E-3090_: Control de filtros de Categoría en GraphQL: includeDirectChildrenOnly y categoría_uid
   * _Nota_ de corrección: solo se recuperan las categorías secundarias directas mientras se filtra por categoría_uid.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [Cloud] Graphql La clasificación de productos no funciona
   * _Nota_ de corrección: La clasificación de productos GraphQl por varios campos cuando se pasan los campos en las variables ahora funciona como se espera.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: Los precios de nivel devuelven un valor incorrecto en los productos GraphQL (en comparación con Storefront)
   * _Nota_ de corrección: Después de la corrección, los precios de nivel del producto devueltos para las solicitudes de graphql tienen precio por artículo.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>

### Catálogo, precios, puesta en escena y Vista previa

* _ACP2E-2672_: [El punto final de la API de precio especial en la nube] devuelve un error al actualizar un gran número de productos simultáneamente
   * _Nota_ de corrección: Ahora la API de actualización masiva de precio especial creará una sola campaña para cada intervalo de fecha en lugar de varias actualizaciones programadas para cada producto y intervalo de fecha. Además, admitirá solicitudes de API simultáneas para un procesamiento más rápido de una gran cantidad de SKU.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/f89a447e>

### catálogo, producto

* _AC-7050_: Categoría árbol de selección en editar producto no está en el mismo orden que el establecido en Catálogo->Categorías
   * _Nota_ de corrección: El sistema ahora muestra correctamente el árbol de selección de categoría en la sección de edición de productos en el mismo orden que se establece en Catálogo->Categorías, lo que facilita la administración del producto en catálogos grandes. Anteriormente, el árbol de categoría en la sección de edición de productos se mostraba en el orden de creación de categoría, independientemente del orden de visualización establecido en Catálogo->Categorías.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36101>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36104>

### catálogo, Optimización de los motores de búsqueda

* _ACP2E-3653_: URL canónico incorrecto para categoría cuando Página > 1
   * _Nota_ de corrección: Anteriormente, el URL canónico para contenido multi Página no funcionaba correctamente, mostrando consistentemente el URL base. Sin embargo, después de implementar la corrección, el URL canónico para contenido multi Página ahora muestra correctamente el URL con el ID de Página.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### catálogo, Search

* _ACP2E-2757_: Los productos no se muestran en categoría y búsqueda pero los enlaces directos funcionan
   * _Nota_ de corrección: Anteriormente, el atributo personalizado Sí/No con price_* attrbute_code no funcionaba con la indexación. Después de esta corrección, el atributo personalizado Sí/No funciona como se esperaba.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Error de búsqueda elástico en la nube] en determinadas páginas de categoría
   * _Nota_ de corrección: Anteriormente, con el ticket de configuración mencionado, cuando poníamos precio 0 para varios productos, se lanzaba una excepción en el frontend categoría Página. Después de que esta corrección se aplique cuando el precio de varios productos es 0 y cargamos categoría Página en frontend, no arrojará ninguna excepción y cargará categoría Página correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: Tipo Error ocurrido al crear el objeto: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Nota_ de corrección: Después de la corrección, se puede crear un instancia de Magento\CatalogSearch\Model\Indexer\Fulltext sin especificar $data.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [Problema de CLOUD] con productos no son visibles en frontend después de guardar en Magento admin
   * _Nota_ de la corrección: Después de la corrección, los productos configurables que tienen productos secundarios con nombres largos no faltarán en la tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>

### Nube

* _ACP2E-3010_: [Cloud] PHPSESSID está cambiando cada solicitud POST
   * _Nota_ de corrección: PHPSESSID ya no se regenera en las solicitudes de POST en el área front-end para un cliente conectado si la caché de L2 Redis está habilitada y el cliente se actualizó desde el back-end
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: Advertencias de generación de mapa del sitio
   * _Nota_ de corrección: Después de la corrección, la mapa del sitio se genera en el directorio tmp del sistema y se copia en el destino final.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>

### Contenido

* _AC-10539_: [problema]  con la visualización de precios en el widget Vistos recientemente
   * _Nota_ de corrección: El sistema ahora muestra correctamente el precio de los productos simples agotados en el widget &quot;Producto visto recientemente&quot;, lo que garantiza la coherencia en todas las utilidades y páginas de lista de productos. Anteriormente, el precio de los productos simples agotados no se mostraba en el widget &quot;Producto visto recientemente&quot; debido a una condición en las plantillas de carga de precios.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38167>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [Problema Corrección] de errores tipográficos y gramaticales en el archivo acl.xsd
   * _Nota_ de corrección: El sistema ahora corrige un error tipográfico y gramatical en el archivo acl.xsd, mejorando la claridad y precisión de la documentación. Anteriormente, el archivo acl.xsd contenía un error tipográfico y una gramática incorrecta que podría causar confusión.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38061>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: Pagebuilder banner imagen no visible en la galería
   * _Nota_ de corrección: El sistema ahora muestra correctamente banner imágenes cargadas en carpetas recién creadas en la galería del generador de páginas, eliminando los errores de consola anteriores. Antes de esta corrección, banner imágenes no eran visibles en la galería si se cargaban en una carpeta nueva, lo que provocaba un error de consola.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;Código de área no establecido&quot; después de la actualización a 2.4.5-p8
   * _Nota_ de corrección: El sistema ahora completa con éxito el proceso de implementación de contenido estático cuando el módulo Magento_CSP está habilitado y &quot;dev/js/translate_strategy&quot; está configurado como &quot;incrustado&quot;, sin activar el error &quot;Código de área no establecido&quot;. Anteriormente, en estas condiciones, el proceso de implementación de contenido estática fallaba con un error de &quot;Código de área no establecido&quot;.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38845>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38922>
* _AC-12692_: Widget árbol de categoría no se representa correctamente
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39008>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: No se puede ver el mensaje &quot;Utilizando valor predeterminado&quot; al cambiar el tema en la configuración del diseño Página
   * _Nota_ de corrección: El sistema ahora incluye una columna separada para mostrar el mensaje &quot;Utilizando valor predeterminado&quot; dependiendo del tema seleccionado en el Página de configuración de diseño. Esto garantiza claridad y visibilidad del estado del valor predeterminado. Anteriormente, no se mostraba el mensaje &quot;Utilizando valor predeterminado&quot;, lo que generaba confusión sobre el estado del tema seleccionado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13569_: [Problema] Restaura la compatibilidad con los complementos de TinyMCE de nuevo (después de...
   * _Nota_ de corrección: El sistema ahora restaura la compatibilidad con los complementos de TinyMCE, lo que permite llamar a las funciones definidas dentro del plug-in cuando se usa el widget desde otra ubicación. Anteriormente, debido a un cambio en la versión de TinyMCE, los complementos no devolvían los widgets como un objeto, lo que resultaba en un error al intentar llamar a ciertas funciones en el instancia del widget.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39262>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39258>
* _AC-9638_: [Archivo de emisión] cargar problema en WYSIWYG editor en página de producto
   * _Nota_ de corrección: El sistema ahora muestra correctamente el árbol de carpetas y permite la carga de imágenes en el editor WYSIWYG en el página de producto, igualado primero después de expandir el pestaña &#39;Imagen y Videos&#39;. Anteriormente, la expansión de la pestaña &quot;Imagen y vídeos&quot; provocaba que no se mostrara el árbol de carpetas y se mostrara un mensaje de error al intentar cargar una imagen en el editor WYSIWYG.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38026>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [Problema de bloqueo dinámico en PREM]
   * _Nota_ de corrección: Los Wdigets ahora se están procesando correctamente dentro de bloques dinámicos.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [Cloud] Frontend no se carga debido a un problema en la newsletter plantilla
   * _Nota_ de corrección: Agregar bloques a través de CMS Página contenido sección ya no posible cliente a excepción
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [excepción] de Cloud Investigate encontrada en el registro: InvalidArgumentException: La clase no existe en vendor/magento/módulo-regla/Model/ConditionFactory.php
   * _Nota_ de corrección: La eliminación de una condición en la configuración de contenido de los productos PageBuilder ya no hace que se registre una excepción en los archivos de registro. Anteriormente, la eliminación de una condición en la configuración contenido de los productos de PageBuilder provocaba que se registrara una excepción esencial en los registros, a pesar de no causar ningún problema en el frontend.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Cambio al modo de tienda único: contenido global ya no aparece
   * _Nota_ de corrección: El sistema ahora sincroniza tienda configuraciones de diseño vista con las configuraciones de diseño del sitio web al habilitar el modo de tienda único, asegurando que las actualizaciones de contenido sean visibles en el frontend. Anteriormente, cambiar al modo de tienda única evitaba que las actualizaciones de contenido se reflejaran en la tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: Page Builder reemplaza a la imagen cuando se intenta agregar vincular y otros fallos de usabilidad.
   * _Nota_ de corrección: Ahora haciendo clic en una imagen, los enlaces en wysiwyg editor en Page Builder elemento de texto cargarán los datos adecuados en la imagen vincular cuadro de diálogo de configuración. Además, agregar un vincular a una imagen en el editor ahora funciona correctamente. Anteriormente, la imagen se reemplazaba por un vincular.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: La galería de medios antigua no puede procesar imágenes cuando se coloca una imagen de 0 bytes en el directorio
   * _Nota_ de corrección: El sistema ahora maneja imágenes de 0 bytes en la galería de medios sin interrumpir funcionalidad, lo que permite que otras imágenes en el directorio se muestren y seleccionen como se espera. Anteriormente, la presencia de una imagen de 0 bytes en la galería de medios impedía que se mostraran o seleccionaran todas las imágenes del directorio.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Error Page Builder al editar el bloque CMS
   * _Nota_ de corrección: El sistema ahora guarda correctamente los cambios realizados en el área de administración usando Page Builder, sin lanzar el error &quot;Page Builder estaba renderizando durante 5 segundos sin liberar bloqueos&quot;. en la consola explorador. Anteriormente, este error se producía al intentar guardar los cambios, lo que impedía la actualización correcta de contenido.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [NUBE] No hay botones de cierre de compra o editar carro de compras en la sección carro de compras
   * _Nota_ de corrección: El paquete de productos ahora se añade al carro de compras mediante widgets sin errores.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3122_: [CLOUD] Cargar imágenes botón no funciona
   * _Nota_ de corrección: Antes de que el botón de Imagen de carga para Banner y Slider de PageBuilder no funcionara como se esperaba, y ahora al presionarlo se abre el administrador de archivos local para seleccionar la imagen deseada para cargar.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor(): El argumento #2 ($height) debe ser mayor que 0. No se puede cargar imagen específica
   * _Nota_ de corrección: Se ha resuelto el problema que causaba errores en el administrador al cargar imágenes con una altura de 0 a través de la galería de medios y se ha realizado una sincronización de activos con el comando sincronizar. Anteriormente no se puede cargar la imagen a través de la galería de medios y el comando sincronizar también falla cuando hay una imagen específica en la galería.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Array.from Prototipo.js en conflicto con la API de Google Maps
   * _Nota_ de corrección: Google Maps ahora se procesa correctamente en PageBuilder editor. Anteriormente, un error de JavaScript impedía que Google Maps se renderizara correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [Cloud] - CMS Slider no refleja los últimos cambios
   * _Nota_ de corrección: El problema se ha solucionado asegurándose de que el lista de regulador se actualiza mientras se activa el evento de guardado en la pantalla de diapositiva edición. Anteriormente, desencadenaba y causaba el problema.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Se produce un error en la Página CSM cuando los bloques CMS se insertan utilizando Página generador en cierto orden
   * _Nota_ de corrección: Anteriormente, en algunas versiones de PHP y OS (Linux), la representación de bloques que hacían referencia a otros bloques cms a través de PageBuilder habría fallado con un &quot;Se produjo un error desconocido. Inténtelo de nuevo&quot;. Ahora el contenido de los bloques cms se representa correctamente dentro de un contenido controlado por PageBuilder.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3428_: Error de previsualización de plantilla del constructor de páginas para grandes contenido
   * _Nota_ de corrección: Un contenido grande provocaba que el elemento de lienzo desbordara los límites del explorador y devolviera un valor incorrecto que rompía el código del servidor (no se puede descodificar correctamente la imagen). Se corrigió con la limitación del tamaño del lienzo al límite del explorador universal.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: Últimas actualizaciones de seguridad con TinyMCE 7 sin tamaño fuente
   * _Nota_ de corrección: Los selectores de tamaño de fuente y fuente familia ahora están disponibles en WYSIWYG editor. Antes de esta corrección, con TinyMCE 7 no estaban disponibles en la interfaz editor.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: TinyMCE 7 editor tamaño fuente en el admin en PT y no en PX por favor aclare
   * _Nota_ de corrección: Antes de la corrección, no se podía especificar el tamaño de fuente en píxeles en las áreas WYSIWYG. Ahora puede establecer el tamaño fuente en píxeles en lugar de pt.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: Tipo de contenido de producto en Page Builder se contrae sin mensajes correctos
   * _Nota_ de corrección: Antes de la corrección, el previsualización html no se generaba correctamente cuando no había productos en el widget. Ahora, la respuesta vacía se genera correctamente y el widget de productos se muestra correctamente en previsualización.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [Generador]de Página Agregar una lista de productos al bloque produce errores
   * _Nota_ de corrección: Ahora agregar Bundle Product Listing para bloquear a través Página builder no genera errores
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/344fce23>

### Cliente/ Clientes

* _AC-12162_: Front-end - Fecha de nacimiento validación está fallando en la creación del cliente Página
   * _Nota_ de corrección: Asegúrese de que todos los validación funcionen después de actualizar moment.js dependencia del sistema a la última versión secundaria
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-8499_: El campo de texto de región no se restablece al cambiar la lista desplegable de países
   * _Nota_ de corrección: El sistema ahora restablece el campo de texto de área geográfica cuando se cambia el país en el menú desplegable, asegurando que los valores anteriores no persistan. Anteriormente, al cambiar el país desde el lista desplegable no se restablecía el campo área geográfica, lo que hacía que se conservara el último valor guardado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: La eliminación del cliente no limpia todos los datos de sesión del navegador en Storefront para clientes registrados y eliminados
   * _Nota_ de corrección: Al eliminar un cliente, ahora se limpian todos los datos de explorador sesión del escaparate para los clientes que han iniciado sesión y eliminado, según lo esperado. El comprador puede continuar comprando y su explorador trata su sesión como una sesión de invitados. Anteriormente, cuando el cuenta del cliente para una comprador iniciada se eliminaba del administrador, el explorador del comprador arrojaba JavaScript errores.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7d5e3906>

### Marco de referencia

* _AC-10037_: [Configuración de tipo de pregunta]no utilizada en `app/code/Magento/Translation/etc/di.xml`
   * _Nota de corrección_: el sistema ahora elimina las dependencias que no se usan en la configuración, lo que mejora la limpieza y eficacia general del código. Anteriormente, había dependencias no utilizadas en la configuración de que no contribuían a ninguna funcionalidad.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38030>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: pregunta/problema de extremo V1/customers/password
   * _Nota_ de corrección: El sistema ahora se adhiere a las restricciones establecidas dentro de la GUI de administración al procesar solicitudes de cambio contraseña a través de la API, evitando posibles abusos de la función de restablecimiento de contraseña. Anteriormente, la API podía procesar solicitudes de cambio de contraseña fuera de las reglas definidas en la GUI de administración, lo que potencialmente permitía un flujo constante de correos electrónicos de restablecimiento si se conocían correos electrónicos válidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38238>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: la configuración del barniz no excluye todos los parámetros de marketing
   * _Nota de corrección_: el sistema ahora excluye correctamente todos los parámetros de marketing comunes en la configuración de Barniz, lo que garantiza un seguimiento y análisis precisos. Anteriormente, no se excluían ciertos parámetros de marketing como gad_source, srsltid y msclkid, lo que producía posibles imprecisiones en la recopilación de datos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38298>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: Proceso de indexación de errores del proceso de índice búsqueda catálogo
   * _Nota_ de corrección: El sistema ahora completa con éxito el comando re-index sin encontrar ningún error, independientemente de la versión libxml compilada con PHP. Anteriormente, ejecutar el comando re-index daba como resultado un error de &quot;Error de proceso de índice de Search catálogo durante el proceso de indexación&quot; cuando PHP se compilaba con ciertas versiones de libxml.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38254>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: se agregaron los filtros created_at, status y grand_total a la consulta de pedidos de clientes y se corrigió un error de varios filtros
   * _Nota de corrección_: el sistema ahora admite el uso de los filtros created_at, status y grand_total en las consultas de pedidos de clientes y ha resuelto un problema en el cual no se aplicaban correctamente varios filtros. Anteriormente, el sistema no admitía estos filtros y no podía aplicar todos los filtros cuando se utilizaba más de uno en una consulta.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38392>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: Ser inundado aleatoriamente con consultas de bloques relacionados / impulsar ventas / venta cruzada e indexación de precios
   * _Nota de corrección_: El sistema ahora optimiza las consultas de bloques relacionados, de ventas adicionales y de ventas cruzadas, lo que mejora el rendimiento y evita que el sitio se cierre debido a consultas excesivas. Anteriormente, el sistema podía sobrecargarse con consultas de estos bloques, causando ralentizaciones significativas y potencialmente derribando el sitio.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36667>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Excepción: Advertencia: Intentando obtener acceso al desplazamiento de la matriz en... -> Calendar.php desde la actualización a ICU 74.1 (PHP Intl)
   * _Nota de corrección_: Commerce ya no registra la siguiente excepción en exception.log cada vez que un comprador o comerciante visita la tienda o el administrador: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [GitHub-38214](https://github.com/magento/magento2/issues/38214)
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38214>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Problema] Solucionar problemas con los datos del cliente cuando el formulario contiene un elemento con el nombre `method`
   * _Nota de corrección_: El sistema ahora identifica correctamente el atributo &#39;method&#39; en los envíos de formularios igualado cuando un elemento llamado &#39;method&#39; está presente en el formulario. Esto garantiza un procesamiento preciso de los datos de los clientes. Anteriormente, si un elemento de formulario se denominaba &quot;método&quot;, interfería con la identificación del atributo &quot;método&quot; en los envíos de formularios, lo que provocaba posibles problemas con la gestión de datos del cliente.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38484>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38449>
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
   * _Nota de corrección_: El sistema ahora asigna un nombre correcto a la variable que contiene la cantidad de dinero que aún se puede reembolsar, lo que evita confusiones durante la depuración. Anteriormente, este variable se llamaba incorrectamente como totalRefund, lo que podría posible cliente a malentendidos para los desarrolladores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38609>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [Problema] Pasar atributos personalizados al vínculo actual a través de XML
   * _Nota de corrección_: el sistema ahora permite que los atributos personalizados se pasen al vínculo actual a través de XML, asegurándose de que estos atributos se muestren correctamente incluso cuando el vínculo sea la página actual. Anteriormente, los atributos personalizados no se mostraban para el vínculo de página actual debido a que el método getAttributesHtml() no se utilizaba para el vínculo actual.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38500>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/30070>
* _AC-11819_: La caché FPC incorporada se rompe en 2.4.7 para algunas configuraciones
   * _Nota_ de corrección: El sistema ahora almacena correctamente las páginas en caché cuando se establece el parámetro MAGE_RUN_CODE, lo que garantiza un rendimiento óptimo. Anteriormente, las páginas no se almacenaban en caché en estas condiciones, lo que provocaba posibles problemas de rendimiento.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38626>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [Problema] Corrija la incoherencia en la administración de excepciones entre los modos de desarrollo y producción
   * _Nota de corrección_: el sistema ahora administra de forma consistente las excepciones entre los modos de desarrollo y producción, lo que evita una redirección inesperada a la página de inicio de sesión cuando se produce una excepción. Anteriormente, una incoherencia en la gestión de excepciones podía provocar una redirección a la página de inicio de sesión en el modo de producción en lugar de mostrar el mensaje de excepción.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38639>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: Reemplazar traducción de &#39;PayPal Account&#39; en token_lista.phtml
   * _Nota_ de corrección: El sistema ahora etiqueta la sección de métodos de pago cuenta tokenizables como &quot;Cuenta&quot; en lugar de &quot;Cuenta PayPal&quot; en el Página Métodos de pago almacenados, lo que la hace más representativa de su función. Anteriormente, esta sección estaba etiquetada específicamente como &quot;Cuenta PayPal&quot;, lo que era engañoso cuando se agregaban otros métodos de pago cuenta tokenizables.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/35622>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37959>
* _AC-11874_: Se ha perdido la compatibilidad con versiones anteriores en Magento\Catalog\Model\ProductRepository clase
   * _Nota_ de corrección: La clase ProductRepository ahora mantiene la compatibilidad con versiones anteriores restaurando la clase Asistente de inicialización como segundo parámetro, lo que garantiza que los módulos que se extienden desde esta clase funcionen como se espera. Anteriormente, la eliminación del asistente de inicialización del constructor de la clase ProductRepository provocaba una pérdida de compatibilidad con versiones anteriores, lo que obligaba a los usuarios a utilizar una solución provisional.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [Problema] de implementar de contenido estática - Error de tipo
   * _Nota_ de corrección: El sistema ahora maneja correctamente los archivos LESS vacíos durante la implementación de contenido estática, mostrando un mensaje de error &quot;El archivo LESS está vacío&quot;. Anteriormente, se producía un error de tipo incorrecto al encontrar un archivo LESS vacío durante implementación.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38682>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [Problema] [Ver] Se ha eliminado el espacio adicional en vincular y etiqueta de secuencias de comandos
   * _Nota_ de corrección: El sistema ahora garantiza que no haya espacios adicionales en las etiquetas vincular y script, proporcionando un código más limpio y eficiente. Anteriormente, se podían encontrar espacios doble entre los atributos de las etiquetas vincular y script.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/32920>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/32919>
* _AC-12127_: [Problema] para evitar una mala configuración Bucle infinito
   * _Nota_ de corrección: El sistema ahora evita un bucle infinito al evitar la asignación autorreferencial en configuraciones de tipo virtual. Esto asegura que el aplicación no se quede atascado en un bucle sin fin cuando se intenta desreferenciar un nodo autorreferencial. Anteriormente, si una configuración de tipo virtual era autorreferencial, hacía que el aplicación se giro indefinidamente.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38822>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: El Administrador de objetos no se utiliza para Magento\Csp\Model\Mode\Data\ModeConfigured
   * _Nota_ de corrección: El sistema ahora utiliza correctamente el Administrador de objetos al crear el objeto ModeConfigurated, lo que permite utilizar complementos en este objeto. Anteriormente, el Administrador de objetos no se utilizaba, lo que impedía que los complementos se aplicaran al objeto ModeConfigurated.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38875>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: Comentario de bloque de documentos inexacto en Stock de productos y alertas de precios
   * _Nota_ de corrección: El comentario del bloque de documentos para el método deleteCustomer en el Stock del producto y las alertas de precios se ha corregido para reflejar con precisión que el método elimina todas las alertas de productos o precios de stock asociadas con un cliente y sitio web determinados, no con el cliente del sitio web. Anteriormente, el comentario indicaba incorrectamente que el método era para eliminar a un cliente del sitio web.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38939>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39001>
* _AC-12594_: [problema] Utilice la configuración compilada para los datos generados en lugar de la configuración general
   * _Nota_ de corrección: El sistema ahora utiliza la configuración compilada para los datos generados en lugar de la configuración general, lo que reduce la transferencia de red y la sobrecarga de datos que depende de una determinada versión del código. Este cambio evita que se anule la caché en las instancias compartidas durante el intercambio de contenedor, lo que mejora la estabilidad y reduce el tiempo de inactividad. Anteriormente, ciertas clases principales utilizaban el tipo de configuración compartida, que podía posible cliente para anular en caché o aplicación el tiempo de inactividad debido a las diferencias en las versiones de código entre varios servidores.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38785>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Quitar referencias a archivos de extjs que se eliminaron en e1ccdb...
   * _Nota_ de corrección: El sistema ahora elimina las referencias a archivos de extjs que se eliminaron anteriormente, eliminando errores en la consola del explorador y el sistema archivo de registro. Anteriormente, estas referencias causaban errores debido a la ausencia de los archivos a los que se hace referencia.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38960>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [Problema] Limpieza menor: se corrigió el uso incorrecto de sprintf, solo se necesitan 2 marcadores de posición aquí y ...
   * _Nota_ de corrección: El sistema ahora utiliza correctamente la función sprintf con el número apropiado de marcadores de posición, mejorando la limpieza y consistencia del código. Anteriormente, la función sprintf se usaba incorrectamente con un argumento adicional, que no causaba ningún problema importante, pero no era el uso correcto.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39062>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 eliminó la extensión FTP
   * _Nota de corrección_: El sistema ahora incluye la extensión FTP como una dependencia en el archivo composer.json, lo que garantiza la configuración correcta de las importaciones de CSV a través de FTP. Anteriormente, se producía un error al intentar configurar CSV importaciones a través de FTP debido a que la extensión FTP faltaba en el paquete PHP.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39083>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12869_: [Correcciones de problemas] Se hace referencia a clases incorrectas en Magento módulos.
   * _Nota_ de corrección: El sistema ahora hace referencia correctamente a las clases en los módulos, lo que garantiza un funcionamiento más suave y evita bloqueos debido a clases no existentes. Esto incluye una corrección de errores en los módulos Indexer y Creditmemo, y el implementación de HttpGetActionInterface en la clase PrintAction. Anteriormente, las referencias de clase incorrectas provocaban errores y posibles bloqueos del sistema, y ciertas funcionalidades, como el nombre del archivo para los archivos PDF creditmemo y la reindexación de acciones, no funcionaban como se esperaba.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39126>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: Capacidad de definir un área para el comando dev:di:info CLI
   * _Nota_ de la corrección: El sistema ahora permite a los desarrolladores definir un área para el comando dev:di:info CLI, mejorando el proceso de desarrollo y depuración. Anteriormente, este comando solo podía mostrar información del área GLOBAL.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38758>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [Problema] para agregar isMultipleFiles Propiedad al elemento de formulario de imagen plantilla
   * _Nota_ de corrección: Esta corrección evita que el botón &quot;Examinar buscar o arrastrar una imagen aquí&quot; desaparezca cuando se agrega una imagen en un elemento de formulario de imagen de varios archivos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39219>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36325>
* _AC-13279_: [Problema] Quitar todos los marketing obtener parámetros para minimizar la caché
   * _Nota_ de corrección: El sistema ahora elimina todos los parámetros marketing get para optimizar la utilización de la caché, reflejando la lógica utilizada cuando Varnish está en uso. Anteriormente, estos parámetros podían posible cliente para almacenar en caché la hinchazón y reducir el rendimiento.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39266>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [Problema] [PHPDOC] Corregir phpdoc incorrecto Magento\Directory\Model\AllowedCountries::getAllowedCountries()
   * _Nota_ de corrección: El PHPDoc para el método AllowedCountries::getAllowedCountries() se ha corregido para proporcionar información precisa, mejorando la claridad y utilidad de la documentación. Anteriormente, el PHPDoc para este método contenía información incorrecta, que podría posible cliente a confusión o mal uso del método.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39246>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [problema Elimina parte del] código de las versiones de PHP que ya no admitimos.
   * _Nota_ de corrección: Eliminación de código para versiones de PHP que ya no son compatibles con Magento
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39361>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Problema Hacer] que el adaptador de ImageMagick sea compatible con php8 (Conversión implícita de float a int)
   * _Nota_ de corrección: El sistema ahora garantiza la compatibilidad con PHP8 al manejar correctamente los números flotantes al calcular las dimensiones de la imagen, evitando cualquier error debido a la Conversión implícita de float a int. Anteriormente, el cálculo de las dimensiones de la imagen podía dar como resultado números flotantes, que cuando se redondeaban implícitamente, causaban un error.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39402>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [Problema] [PHPDOC] Corregir mal phpdoc Magento\Framework\aplicación\Config\ScopeConfigInterface
   * _Nota_ de corrección: esta actualización corrige las anotaciones de PHPDoc en Magento\Framework\aplicación\Config\ScopeConfigInterface para reflejar con precisión el tipo del argumento $scopeCode para los métodos getValue e isSetFlag.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39492>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39199>
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http depende de la frase de razón OK
   * _Nota_ de corrección: se ha eliminado la comprobación de frase &quot;OK&quot; de Magento\Framework\Filesystem\Driver\Http::isExists
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39546>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: El indexador de red de clientes no funciona correctamente en modo de actualización por programación
   * _Nota_ de corrección: Anteriormente, la cuadrícula del cliente se actualizaba instantáneamente, pero después de la corrección, la cuadrícula del cliente se actualiza después de la ejecución cron, pero no se refleja al instante.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: error tipográfico en un archivo js.
   * _Nota_ de corrección: El sistema ahora utiliza correctamente el término &quot;suscriptores&quot; en el archivo de JavaScript, asegurando el funcionalidad adecuado de las características relacionadas. Anteriormente, un error tipográfico en el archivo JavaScript resultaba en el uso incorrecto del término &quot;subsctibers&quot;.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36163>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [Emisión] Quitar prohibida `@author` etiqueta
   * _Nota_ de corrección: El sistema ahora se adhiere a los estándares de codificación al eliminar el etiqueta prohibido `@author` de ciertos módulos, lo que garantiza un código más limpio y estandarizado. Anteriormente, el `@author` etiqueta estaba presente en algunos módulos, lo que iba en contra de los estándares de codificación establecidos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37253>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [Emisión] Quitar etiqueta prohibida `@author` de `Magento_Customer` (parte 2)
   * _Nota_ de corrección: El sistema ahora se adhiere al estándar de codificación al eliminar el etiqueta prohibido `@author` de ciertos módulos, asegurando un código más limpio y estandarizado. Anteriormente, el `@author` etiqueta estaba presente en algunos módulos, lo que iba en contra de los estándares de codificación establecidos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37250>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: El espacio en la sintaxis de editorconfig se rompe regla para [{composer,auth}.json]
   * _Nota de corrección_: El sistema ahora aplica correctamente una sangría de 4 espacios al compositor y auth.json archivos, siguiendo una corrección a un error de sintaxis en editorconfig. Anteriormente, debido a un espacio en la sintaxis de editorconfig, estos archivos tenían un formato incorrecto con una sangría de 2 espacios.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37394>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37395>
* _AC-8662_: [problema] Mejora el error cron registro
   * _Nota_ de corrección: El sistema ahora captura y registra tanto STDERR como STDOUT para los procesos cron, proporcionando información de diagnóstico valiosa en escenarios donde los procesos cron fallan. Anteriormente, no se registraban los mensajes de error dentro de los procesos cron, y STDERR y STDOUT para grupos cron que se ejecutaban en procesos separados se perdían.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37453>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/32690>
* _AC-8984_: [Problema] Agrega algunos colores más a la salida de ciertos comandos cli de instalación
   * _Nota_ de corrección: El sistema ahora agrega más colores a la salida de ciertos comandos de la interfaz de línea de comandos (CLI) de configuración, mejorando la legibilidad y la experiencia del usuario. Anteriormente, el resultado de estos comandos era más difícil de leer debido a la falta de diferenciación de color.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/29335>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: La actualización Magento restablece general/área geográfica/state_required cuando se agrega un nuevo país con el estado/área geográfica requerido.
   * _Nota_ de corrección: El sistema ahora solo agrega el país modificado a la configuración &#39;general/área geográfica/state_required&#39; cuando se agrega un nuevo país con estados requeridos, evitando cualquier interrupción en el código personalizado que asume que el área geográfica está deshabilitado. Anteriormente, agregar un nuevo país con estados requeridos restablecía la configuración &#39;general/área geográfica/state_required&#39; a los países predeterminados con un estado requerido, lo que podría dañar la tienda.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37796>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Diferencia en menos compilación entre php &amp; nodejs biblioteca (gruñido) con expresiones complicadas `calc`
   * _Nota_ de corrección: Corregir la diferencia en menos compilación entre php y nodejs biblioteca (grunt) después de actualizar wikimedia/less.php:^5.x
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37841>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Error &quot;Tabla base o vista no encontrado&quot; se produce cuando se ejecuta la indexación parcial
   * _Nota_ de corrección: El reindexado parcial ahora funciona correctamente con el registro de cambios grande en caso de conexión de base de datos secundaria
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: Problemas después de actualizar MariaDB a 10.5.1 o superior
   * _Nota_ de corrección: Se corrigió el problema cuando los valores de fecha y hora en una base de datos se convertían en 0000-00-00 00:00:00 después de la actualización de Mysql
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Discrepancia de tipos en la comparación de datos cuando se comprueba si los datos tienen cambios
   * _Nota_ de corrección: Anteriormente, se llamaba al objeto guardar cada vez sin ningún cambio de datos (para cualquier campo de datos numérica, gustar int/float/doble). Activa la _hasDataChanges de indicador para que sea verdadera y llama a la función de guardado. Después de que se aplique esta corrección, la función de guardar llamará solo si los datos se modifican. El valor de datos para int/float/doble-check con el valor que pasa a la función y hace una coincidencia estricta de tipos.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [La importación en la nube] no se puede utilizar con el directorio var
   * _Nota_ de corrección: el producto se puede importar con éxito independientemente del nombre del archivo.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: En el iPad mini el menú y la cabecera se cargan como móviles, en su lugar deberían cargarse como escritorio.
   * _Nota_ de corrección: El sistema ahora trata dispositivos con un ancho de 768px como escritorio, asegurando que el menú y el encabezado se carguen correctamente. Anteriormente, los dispositivos con un ancho de 768px se trataban como móviles, lo que provocaba que el menú y el encabezado se cargaran en un vista móvil.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3230_: Modificar la longitud de la columna a través de db_esquema.xml no funciona en caso de claves externas
   * _Nota_ de corrección: modificar la columna con clave externa a través de esquema declarativo ahora no aumenta los errores con MariaDB
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: algunos registros de relaciones se guardan en la base de datos cuando se guarda el registro de pedidos
   * _Nota_ de la corrección: Antes de la corrección, se activaban consultas de UPDATE innecesarias que pueden tener un impacto en el rendimiento. Después de la corrección, se eliminaron las consultas UPDATE innecesarias.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [NUBE] En admin hay muchos errores de javascript en la consola
   * _Nota_ de corrección: Anteriormente, en el panel de administración hay muchos errores de javascript en la consola. Ahora, en el panel de administración, no habrá errores de JavaScript en la consola, y todas las funciones de JavaScript predeterminadas se ejecutarán con éxito sin ningún problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Nube] Magento: se eliminó el mensaje en cola
   * _Nota_ de corrección: Los mensajes en cola ahora se están borrando correctamente. Antes de la corrección, dado que se estaba utilizando el sistema SQL cola, se podrían haber eliminado nuevos mensajes si el mensaje de cola de limpieza se estaba ejecutando al mismo tiempo.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3537_: Las entradas de clave de caché correspondientes no están disponibles en las etiquetas de caché, por lo tanto, la limpieza de caché no funciona correctamente
   * _Nota_ de corrección: El modo LUA ahora está habilitado de forma predeterminada para el recolector de basura de caché de Redis para evitar condiciones de carrera
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: se ignora MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK valor
   * _Nota_ de corrección: Después de la corrección, un variable ENV establecido en &quot;false&quot; se tratará como bool false, no como cadena &#39;false&#39;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### Marco de trabajo, GraphQL

* _AC-7976_: [Se ha introducido la] compatibilidad con tipos escalares personalizados para GraphQL esquema
   * _Nota de corrección_: el sistema ahora admite tipos escalares personalizados para el esquema de GraphQL, lo que permite a los desarrolladores definir tipos escalares personalizados e implementaciones. Esta función puede resultar especialmente útil para expresar valores que pueden requerir validación, como HTML, correos electrónicos, URL, fechas, etc., y para casos más avanzados como atributos EAV. Anteriormente, el sistema no admitía el procesamiento de tipos escalares personalizados en GraphQL.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36877>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Marco, IU Framework

* _ACP2E-3324_: Posibilidad de sobrescribir el valor de configuración igualado si está bloqueado
   * _Nota_ de corrección: Antes de esta corrección, la configuración de diseño no se podía establecer a través del comando bin/magento config:set y los valores bloqueados se podían cambiar manipulando el formulario que los muestra. Después de la corrección, los valores bloqueados establecidos desde cli con --lock-env o --lock-conf ya no se pueden actualizar.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _AC-11729_: Magento_GraphQl ejecuta el procesamiento de encabezados igualado si el valor del encabezado no pasa validación
   * _Nota_ de corrección: El sistema ahora garantiza que el procesamiento del encabezado solo se ejecute una vez y solo si el valor del encabezado pasa validación, lo que mejora la seguridad y evita posibles vulnerabilidades. Anteriormente, el procesamiento del encabezado se ejecutaba igualado si el valor del encabezado no pasaba validación, lo que provocaba posibles vulnerabilidades y un comportamiento inesperado debido al procesamiento doble de los valores del encabezado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: Las opciones de tarjetas de regalo físicas no tienen el orden de clasificación correcto
   * _Nota_ de corrección: El sistema ahora ordena correctamente las opciones de regalos físicos tarjeta productos cuando se consultan a través de GraphQL, lo que garantiza una representación coherente con el tema Luma. Anteriormente, el orden de clasificación era incorrecto según el tema luma, lo que provocaba una visualización y ordenación incorrectas de opciones como el nombre del remitente, el nombre del destinatario y la cantidad.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [La caché de resolución de GraphQL] se invalida al crear/editar/mover/eliminar una actualización de ensayo
   * _Nota de corrección_: El sistema ahora garantiza que la caché de resolución no se invalide al crear, editar, mover o eliminar una actualización de ensayo, sino solo cuando la actualización de ensayo se aplique a la entidad. Anteriormente, la caché del solucionador se invalidaba prematuramente, igualado antes de que se aplicara la actualización de ensayo, lo que provocaba invalidaciones innecesarias de la caché.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: caché de Fastly no borrada para la actualización de ensayo de contenido
   * _Nota_ de corrección: Ahora GraphQL con la caché de respuestas de contenido de PageBuilder se invalida cuando se actualizan PageBuilder contenido entidades relacionadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Desactivación del desplazamiento por capas - No se elimina la agregación de Graphql
   * _Nota_ de corrección: El problema se ha solucionado después de aplicar la comprobación al solicitar un búsqueda de producto con categoría agregaciones a través de un consulta GraphQL cuando la configuración de administración de &quot;Catálogo > navegación por capas > mostrar Categoría Filtrar&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: La llamada a los productos GraphQL que contiene el filtro de precios {from:&quot;0&quot;} no devuelve ningún resultado
   * _Nota de corrección_: Anteriormente, la búsqueda de productos de graphql con el filtro de precios cero no arrojaba ningún resultado debido a una excepción generada. Ahora la búsqueda devuelve los resultados según lo esperado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: las traducciones de los atributos devueltos por el cliente no se reflejan en la API de GraphQL para el StoreView correspondiente
   * _Nota de corrección_: las traducciones para atributos de devolución del cliente se reflejan en la API de GraphQL para el StoreView correspondiente.
Anteriormente, los atributos de retorno de los clientes para las respectivas vistas de tienda no se reflejaban en la API de GraphQL.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [Llamada GraphQL con la nube] rota para getPurchaseOrder con cotización nodo
   * _Nota_ de corrección: La llamada GraphQL de la orden de compra podrá ejecutar el tarea sin encontrar ningún error interno del servidor.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [Los productos configurables en la nube] no se muestran en el sitio de producción si el producto no está habilitado en &quot;Todas las vistas de la tienda&quot;
   * _Nota de corrección_: El sistema ahora muestra correctamente los productos configurables en el sitio igualado si el producto no está habilitado en &quot;Todas las vistas de la tienda&quot;, pero está habilitado en tienda específicos vista ámbitos.
Anteriormente, si un producto se deshabilitaba en &quot;Todas las vistas de la tienda&quot; y se habilitaba solo en ámbitos de vista tienda específicos, los atributos del producto no se mostraban correctamente en la respuesta de GraphQL, lo que provocaba que el producto no se mostrara correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [Productos de nube] GraphQL tiene error cuando el mismo producto simple se ha asignado a varios productos configurables
   * _Nota_ de corrección: Anteriormente, con productos configurables separados con el mismo producto simple, grapQL devuelve un error. Después de aplicar esta corrección, diferentes productos configurables con el mismo producto simple, grapQL devuelve el resultado sin ningún error.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [Problema de nube] con la Authentication de usuario y el acceso a tokens entre sitios en la configuración de varios sitios
   * _Nota_ de corrección: Las consultas de información del cliente y carrito de GraphQl en la configuración de sitios múltiples verifican si existe el cliente en un sitio web no predeterminado.
Anteriormente consulta funcionaba sin asegurarse de que el cliente existiera en un sitio web no predeterminado en la configuración de varios sitios.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: La paginación de GraphQL carro de compras itemsV2 no funciona correctamente
   * _Nota_ de corrección: el problema se ha solucionado pasando el valor correcto para el argumento Página actual en el consulta colección. Anteriormente, se pasaba el valor incorrecto para establecer el Página actual, lo que causaba el problema.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3255_: [se debe especificar el valor del modelo GRAPHQL] al obtener customerCart
   * _Nota_ de corrección: La consulta &#39;customerCart&#39; de GraphQL ahora puede crear un carro de compras vacío igualado cuando la cotización no está disponible en la base de datos. Anteriormente, esta operación fallaba debido a problemas de validación país al crear el carro de compras vacío.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [Los artículos de la lista de artículos deseados de GraphQl] son visibles a través de GraphQl pero no visibles en la tienda
   * _Nota_ de corrección: Los productos de la lista de deseos no se enumeraban correctamente cuando se solicitaban a través de GraphQL. Ahora, los productos de la lista de deseos se filtran en función del contexto tienda proporcionado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] Restablecer contraseña correo electrónico inconsistencia entre contenido y sujeto/vincular
   * _Nota_ de corrección: El problema se ha resuelto simulando la tienda correcta en la que está registrada la cuenta del cliente al enviar el contraseña restablecimiento solicitud, independientemente del sitio web tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Productos en la nube] GraphQL consulta devuelve productos relacionados no asignados al sitio web actual
   * _Nota de_ corrección: Anteriormente, para los consulta de graphQL, los productos relacionados con varias tienda no se mostraban correctamente para la consulta del producto. Después de aplicar esta corrección, para los productos, graphQL consulta productos relacionados con tienda se muestran en consecuencia.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: El uso incorrecto de ID de tienda en el encabezado GraphQL causa un error de memoria fatal
   * _Nota_ de corrección: El envío de código de tienda incorrecto en GraphQL ya no solicitud produce un consumo excesivo de memoria.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [respuesta de Cloud] 500 a la respuesta vacía de Graphql en 2.4.7
   * _Nota_ de corrección: Después de la corrección, no válido solicitudes graphql no se registrarán en exception.archivo de registro.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_: [Problemas de nube] con la API de Graphql
   * _Nota_ de corrección: Antes de la corrección mediante el uso de Graphql aplicación servidor, la dirección del cliente solicitud no devolvía los datos más recientes.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: El producto deshabilitado sigue apareciendo en artículos relacionados, impulsar ventas y de venta cruzada en grpahQL consulta
   * _Nota_ de corrección: Graphql ahora proporciona una respuesta correcta para productos de realizar venta cruzada, impulsar ventas y relatado deshabilitados
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [CLOUD:] Error GraphQl Error interno del servidor Mutación placeOrder
   * _Nota_ de corrección: La mutación &quot;placeOrder&quot; con información de código cupón en el solicitud ya no genera una excepción de error interno, el pedido se realizó correctamente. Anteriormente, fallaba con &quot;Error interno del servidor&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: El discount_percentage no se calcula para productos paquete con precio dinámico
   * _Nota_ de corrección: Se ha añadido una corrección para discount_percentage de product.price_details que no mostraban el valor correcto para paquete productos con precio dinámico habilitado y cupón de descuento aplicado.
* _LYNX-485_: El paquete de productos todavía muestra &quot;IN_STOCK&quot; cuando uno de sus productos empaquetados se agota
   * _Nota_ de corrección: se ha resuelto el problema por el que paquete productos seguían mostrando el igualado &quot;IN_STOCK&quot; cuando uno de los productos incluidos estaba agotado.
* _LYNX-486_: not_available_message y only_x_left_in_stock no muestran el mismo stock disponible
   * _Nota_ de corrección: se ha resuelto el problema por el que el not_available_message y el only_x_left_in_stock mostraban una disponibilidad de existencias incoherente.
* _LYNX-488:_ campo original_row_total devuelve un valor incorrecto
   * _Nota_ de corrección: se ha resuelto el problema con el campo original_row_total, que devolvía valores incorrectos al seleccionar opciones personalizadas
* _LYNX-503_: La miniatura del producto agrupada debe mostrarse según la configuración.
   * _Nota_ de corrección: se ha resuelto el problema para garantizar que la miniatura del producto agrupada se muestre de acuerdo con los ajustes de configuración.
* _LYNX-512_: original_item_price no incluye descuentos
   * _Nota_ de corrección: Se ha actualizado la original_item_price para incluir descuentos.
* _LYNX-530_: El mensaje no disponible no muestra el inventario disponible cantidad
   * _Nota_ de corrección: Se han resuelto el mensaje de error y el código de error de la mutación AddProductsToCart para alinearlos con la configuración del mensaje &quot;no disponible&quot;
* _LYNX-532_: El estado &quot;OUT_OF_STOCK&quot; regresa el Simple con opciones personalizadas productos con opciones de selección múltiple
   * _Nota_ de corrección: Se actualizó el solucionador StockStatusProvider en el paquete inventario para corregir el stock_status de productos simples con opciones personalizadas.
* _LYNX-533_: Error (GQL): carro de compras.itemsV2.items.product.custom_attributesV2 devuelve un error de servidor
   * _Nota_ de corrección: Se ha resuelto el error de servidor que se producía cuando una consulta de carro de compras incluía los atributos personalizados de un producto al agregar un producto sin atributos personalizados.
* _LYNX-536_: pedidos/date_of_first_order siempre devuelven nulos
   * _Nota_ de corrección: se ha resuelto el problema por el que los pedidos > date_of_first_order siempre devolvían nulos.
* _LYNX-544_: El cliente no debe poder cancelar un pedido enviado parcialmente
   * _Nota_ de corrección: Se ha añadido la validación para impedir que los clientes cancelen un pedido enviado parcialmente.
* _LYNX-548_: Error códigos para la cancelación de pedidos basados en el mensaje de error
   * _Nota_ de corrección: Los códigos de error para la cancelación de pedidos ahora se basan en el mensaje de error específico.
* _LYNX-581_: Retroceder las propiedades relacionadas con el cookie de privadas a protegidas
   * _Nota_ de corrección: revierte la visibilidad de las propiedades del constructor de clase Magento\Framework\aplicación\PageCache\Versión de privado a protegido
* _LYNX-600_: Aumente la complejidad máxima del consulta predeterminado de GraphQL a 1000
   * _Nota_ de corrección: Se ha aumentado la complejidad máxima predeterminada del consulta GraphQL de 300 a 1000.
* _LYNX-620_: GQL - itemsV2 > El total de la fila original, los precios del rango de precios se devuelven como $ 0.00 para el producto descargable con opciones de archivo que tiene precios separados.
   * _Nota_ de corrección: se ha resuelto un problema por el que los productos descargables con opciones de compra de vincular separadas habilitadas devolvían $0 por artículosV2 > total de la fila original, el rango de precios devuelto como $0,00 para productos con opciones de archivo con precios separados.
* _LYNX-772_: GraphQl Compatibilidad para PHP-8.4 Versión
   * _Nota_ de corrección: Se corrigieron problemas de compatibilidad de GraphQL con PHP 8.4 en múltiples resolvers, lo que garantiza un funcionalidad sin problemas. Se han actualizado los archivos afectados en los módulos CatalogRule, Customer, GiftMessage, GiftCard y GiftWrapping.

### GraphQL, Inventario / MSI

* _ACP2E-2607_: La mutación MergeCart produce una excepción cuando los carros de origen y destino tienen el mismo paquete elementos
   * _Nota_ de corrección: &#39;-
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventario / MSI, Rendimiento

* _ACP2E-1716_: Sitio caído después de la actualización
   * _Nota_ de corrección: Se ha mejorado el rendimiento de la recuperación de productos de paquete a través de GraphQl.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, rendimiento

* _AC-9569_: [Los datos de resolución de clientes de GraphQL Resolver] no se invalidan desde Importar
   * _Nota de corrección_: La caché de resolución de clientes de GraphQL ahora se invalida como se espera cuando se edita o elimina un cliente mediante importaciones. Anteriormente, la memoria caché no se invalidaba y los datos del cliente podían editarse o eliminarse durante la importación.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, Buscar

* _ACP2E-2809_: El ordenamiento de lista de productos GraphQL por varios parámetros no funciona
   * _Nota_ de corrección: La ordenación de productos por varios campos en GraphQl ahora funciona como se describe en la documentación
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_: Lista de productos GraphQL consulta limitada a total_count solo 10.000 productos
   * _Nota_ de corrección: Después de la corrección, el resultado de búsqueda no se limita a 10000 productos, es posible obtener todos los productos que coincidan con los criterios de búsqueda igualado si el recuento es más de 10000.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, marco de trabajo de prueba

* _ACP2E-3363_: Error en la prueba de integración de Magento\GraphQl\aplicación\GraphQlCustomerMutationsTest.php
   * _Nota_ de corrección: &#39;-
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importar / exportación

* _AC-12172_: Problema en la importación del producto cuando se proporciona el tipo de opciones personalizado: archivo (el producto creado no contiene el precio de la opción personalizada y muestra solo la primera extensión de tipo de archivo proporcionada)
   * _Nota de corrección_: El sistema ahora importa correctamente los datos del producto con opciones personalizadas de tipo &#39;archivo&#39;, asegurando que se muestren todas las extensiones de archivo proporcionadas y se incluya el precio de la opción personalizada. Anteriormente, durante la importación del producto, si se proporcionaba una opción personalizada de tipo &quot;archivo&quot; con más de una extensión de archivo, solo se mostraba la primera extensión y faltaba el precio de la opción personalizada.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38805>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Tiempo de ejecución incorrecto para la operación de importación en la cuadrícula del historial de Importar
   * _Nota_ de corrección: Importar tiempo de ejecución del informe se muestra correctamente independientemente de la configuración regional del administrador.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Se crean clientes duplicados con la misma dirección correo electrónico mediante la importación
   * _Nota de corrección_: Importar el cliente mientras se establece Uso compartido de cuenta en Global, se actualiza el cliente importado que existe en el sistema.
Se ha duplicado el cliente importado anteriormente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Importar añadir/Update sobre productos que duplican Opciones personalizables
   * _Nota_ de corrección: El problema se ha resuelto asignando el tienda correcto a las opciones de producto durante las opciones de producto CSV las importaciones.
Anteriormente, se asignaba al tienda de administración en lugar de a su respectivo tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: fecha &quot;created_at&quot; del cliente no convertida a tienda zona horaria en el momento de la exportación
   * _Nota_ de corrección: Un valor de fecha de columna &#39;created_at&#39; se convierte a la fecha adecuada formato en función de la zona horaria tienda en la sección CSV de exportación del cliente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [Error de obtención de nube] al comprobar los datos de importación mediante CSV
   * _Nota_ de corrección: No hay ningún error al verificar los datos durante CSV importación. Anteriormente, el mensaje de error que se mostraba era: &quot;No podemos encontrar un cliente que coincida con este código de correo electrónico y sitio web en la fila (s): 1&quot; al verificar los datos en la sección de importación usando CSV del administrador.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3172_: falta botón Importar
   * _Nota_ de corrección: Resuelva el problema de falta de botón Importar después de las comprobaciones de datos con registros correctos e incorrectos en el CSV. Anteriormente, el botón de importación no se mostraba después de la comprobación de datos con registros correctos e incorrectos en el CSV.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: No se puede importar la dirección de cliente exportada
   * _Nota_ de corrección: La importación de la dirección del cliente se realizará según lo esperado. Anteriormente, un archivo de importación de dirección de cliente no pasaba validación si Compartir cuentas de cliente = Global, y hay dos sitios web donde el sitio web predeterminado tiene un lista de país restringido, y la dirección que se está importando es para otro sitio web donde los países permitidos son diferentes
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [La nube] incorrecta cantidad en CSV archivo no dio error
   * _Nota_ de corrección: Ahora la importación de fuentes de stock arrojará validación error para los valores no numérica en la columna cantidad. Anteriormente, la importación de orígenes de stock con un valor no numérica en la columna cantidad provocaba que el cantidad se estableciera en 0.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: Clave de URL duplicada El mensaje de error generado al importar un producto no es correcto cuando la clave de URL ya pertenece a un categoría
   * _Nota_ de corrección: mostrar el mensaje de error correcto durante la verificación de importación del producto, cuando el cliente intentó importar un producto cuando la clave URL del producto ya pertenece a un categoría.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: La exportación de productos causa OOM igualado con límite de memoria 4G
   * _Nota_ de corrección: Anterior a esta corrección, la exportación del producto falló si los atributos del producto tenían miles de valores de opción igualado con memoria disponible 4G. Después de esta corrección, la exportación del producto debería terminar de exportar el archivo csv.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [Los procesos de Importar nube] interfieren entre sí
   * _Nota_ de corrección: Los mensajes correctos se muestran si el mismo administrador usuario realiza dos o más operaciones de importación utilizando la misma sesión de usuario.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>

### Importar / exportación, rendimiento

* _ACP2E-3476_: [El tiempo de importación de productos en la nube] ha aumentado significativamente
   * _Nota_ de la corrección: Anterior a la corrección, la importación de productos de catálogo con más de 10K entradas tuvo una degradación de tiempo significativa. Después de la corrección, la importación del producto de catálogo se ejecuta a tiempo.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/87d012e5>

### Instalar y administrar

* _AC-13242_: Magento actualización falla en MariaDB 11.4 + 2.4.8-beta1
   * _Nota_ de la corrección: La actualización debería realizarse sin ningún error.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: No hay exportación de VCL para el botón Barniz 7 en el panel de administración
   * _Nota de corrección_: Se agregó el botón &quot;Exportar VCL para Barniz 7&quot; al Panel de administración.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventario / MSI

* _AC-10750_: La actualización de inventario del producto configurable falla cuando la base de datos utiliza prefijos
   * _Nota de corrección_: El sistema actualiza correctamente el inventario de productos configurables cuando la base de datos utiliza prefijos, lo que evita mensajes de error y garantiza que se guarde la cantidad correcta. Anteriormente, se producía un error al intentar guardar la cantidad de inventario para productos simples dentro de un producto configurable si la base de datos utilizaba prefijos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: la clave de la API de Google de Google no funciona al agregar un mapa con atributos
   * _Nota_ de corrección: El sistema ahora es compatible con la última versión 3.56 de la API de Google Maps, lo que permite a los usuarios agregar con éxito un bloque de contenido de mapas desde el menú PageBuilder al fase sin encontrar ningún error. Anteriormente, los usuarios no podían agregar un bloque de contenido Map debido a problemas de compatibilidad con la versión de la API de Google Maps, lo que generaba el mensaje de error &quot;algo salió mal&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: No se puede crear un envío para un elemento de pedido con múltiples fuentes y unidad de almacén dañada
   * _Nota_ de corrección: Anteriormente, cuando se agregaron espacios por error en sku a través de la base de datos, se produce un error en el envío, Página que ahora está solucionado y el ajuste automático se considera un error amigable para los humanos y no se encontró ningún impacto. Por lo tanto, el envío se ha creado correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [Prueba] Paquete de productos con 0 inventario en la tienda
   * _Nota de corrección_: el producto del paquete no se muestra en los sitios web adicionales que usan existencias adicionales.
* _ACP2E-2794_: [Nube] problema crítico con la lista de productos con espacios vacíos
   * _Nota de corrección_: el sistema ahora muestra correctamente las listas de productos sin espacios vacíos cuando los productos están configurados en &#39;Agotado&#39;, lo que garantiza una presentación coherente y precisa de los productos disponibles. Anteriormente, si se establecía un producto en &quot;Agotado&quot;, aparecía un espacio vacío en la lista de productos, lo que afectaba al diseño y podía confundir a los clientes.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: No se puede enviar el pedido cuando el almacén de recogida MSI está habilitado
   * _Nota_ de corrección: Rendimiento inventario mejorado de crear envío en caso de muchas fuentes con recogida en tienda
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: el reíndice de Cron no puede actualizar la disponibilidad del producto en el front-end
   * _Nota_ de corrección: Anteriormente, los Productos permanecían agotados en el frontend después de actualizar el estado del pedido pendiente a través de la API de REST. Ahora, después de actualizar el estado del pedido pendiente a través de la API de REST, los productos se muestran como en stock.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Agregar imágenes a configurable no funciona cuando MSI está habilitado.
   * _Nota_ de corrección: Imagen cargar para un producto configurable ahora funcionará como se espera cuando se utilice inventario módulo. Anteriormente, el cargar de imágenes no funcionaba
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: Problema con el paquete Product + MSI en Clean M2.4.7-p3
   * _Nota_ de corrección: Anteriormente, para inventario paquete productos después de la duplicación con el mismo producto simple, el producto simple no se puede guardar. Después de aplicar esta corrección, el producto simple se puede guardar correctamente sin excepciones.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39358>
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/0208e433>

### Inventario / MSI, Search

* _ACP2E-3413_: Todos los productos se indexan con [is_out_of_stock] = 1 cuando el unidad de almacén no se ha establecido como atributo de búsqueda
   * _Nota_ de corrección: Después de la corrección, el &quot;is_out_of_stock&quot; en el catálogo búsqueda índice es correcto, igualado cuando no se puede buscar en sku.
   * _Contribución_ de código de GitHub: <https://github.com/magento/inventory/commit/5b21b7af>

### Orden

* _AC-10828_: Pantalla de descripción general del pedido back-end: El pedido pendiente no cantidad visible en el nivel de elemento del pedido
   * _Nota_ de corrección: El sistema ahora muestra el número de elementos pendientes en la columna cantidad de la pantalla de información general del pedido back-end. Esto garantiza que los usuarios puedan realizar un seguimiento preciso del estado de todos los elementos de un pedido. Anteriormente, la columna cantidad solo mostraba el número de artículos pedidos, facturados y enviados, pero no mostraba el número de artículos pendientes.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38252>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] se usó un identificador de almacén incorrecto en el procesador de direcciones de pedidos
   * _Nota_ de corrección: El sistema ahora utiliza correctamente el ID de tienda asociado con un pedido al representar la dirección del pedido, asegurando que las direcciones tengan el formato correcto de acuerdo con su respectivo ID de tienda. Anteriormente, el sistema utilizaba incorrectamente el ID de tienda actual, que podía posible cliente a un formato de dirección incorrecto en los casos en que era necesario enviar varios correos electrónicos de pedidos de diferentes tiendas.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38412>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: Problema con la almacenamiento en caché JoinProcessor
   * _Nota_ de corrección: El sistema ahora aplica correctamente el JoinProcessor para cada iteración, igualado con llamadas consecutivas, lo que garantiza una recuperación precisa de los datos. Anteriormente, JoinProcessor se marcaba incorrectamente como ya aplicado en iteraciones consecutivas, lo que provocaba errores en la recuperación de datos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/27504>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Emitir] precio de envío mostrando diferente en pdf impreso
   * _Nota_ de corrección: El sistema ahora muestra correctamente los precios de envío en PDF impresos de acuerdo con los ajustes de configuración de impuestos, lo que garantiza la coherencia entre la factura del pedido de cliente vista Página y la factura impresa. Anteriormente, el precio de envío mostrado en el PDF impreso no incluía impuestos, independientemente de los ajustes de configuración de impuestos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38608>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _AC-13839_: Reordenar con un producto principal configurable eliminado
   * _Nota_ de corrección: Ahora, al reordenar con el producto eliminado, el sistema no mostrará el botón de repedido para reordenar
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39568>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Corrección de problemas] \Magento\Sales\Model\Order\Email\Container\Template::$id Propiedad
   * _Nota_ de corrección: Esto corrige el mal phpdoc para \Magento\Sales\Model\Order\Email\Container\Template::$id, en realidad $id es type int pero en realidad es cadena.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39151>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: No se pueden guardar los cambios en el número de teléfono en detalles del pedido existente
   * _Nota_ de corrección: Ahora el usuario puede agregar el prefijo internacional 00 en el campo telefónico de la dirección del pedido
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38201>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: Los correos electrónicos no se pueden enviar
   * _Nota de corrección_: El sistema ahora incluye una opción de configuración async_sending_attempts especificar el número de intentos de enviar un correo electrónico antes de detenerse, mejorando el manejo de los envíos de correo electrónico fallidos cuando &quot;Envío asíncrono&quot; está habilitado. Anteriormente, si una correo electrónico no se enviaba, el sistema intentaba reenviarla continuamente, lo que provocaba un bucle interminable de mensajes de error en el registro del sistema.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [El pedido en la nube] Estado cambia para completarse cuando se reembolsa parcialmente un pedido enviado parcialmente
   * _Nota_ de corrección: Al emitir una nota de crédito, el estado del pedido ya no cambia a &quot;completado&quot; si hay artículos que aún no se han enviado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [CLOUD] no puede deshabilitar el envío de correos electrónicos desde el administrador IU como muestra Dev Docs
   * _Nota_ de corrección: El sistema ahora evita correctamente que se envíen correos electrónicos de ventas cuando correo electrónico comunicación está desactivada. Estos correos electrónicos ya no se enviarán cuando se vuelva a habilitar correo electrónico comunicación. Anteriormente, los correos electrónicos de ventas iniciados mientras correo electrónico comunicación estaba deshabilitada se enviaban una vez que se volvía a habilitar correo electrónico comunicación.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Pedido cerrado sin reembolso total
   * _Nota_ de corrección: El sistema ahora mantiene correctamente el estado del pedido como &#39;Procesando&#39; y el estado de la factura como &#39;Pendiente&#39; cuando un pedido con un pago no capturado tiene un envío creado. Esto garantiza que los pedidos solo se marquen como &quot;Cerrados&quot; después de recibir el reembolso completo. Anteriormente, crear un envío para un pedido con una factura pendiente cambiaba incorrectamente el estado del pedido a &quot;Cerrado&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Cloud] No se puede crear un pedido en la administración de un tienda si no se ha configurado la dirección de facturación predeterminada
   * _Nota_ de corrección: ahora es el mensaje de error relevante &quot;Ya existe un cliente con la misma dirección de correo electrónico en un sitio web asociado&quot;. se muestra si un cliente no tiene una dirección de facturación predeterminada e intenta crear un pedido en otro tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Solicitud de pedido duplicado por el administrador enviada
   * _Nota_ de corrección: Anteriormente, el botón &quot;Enviar pedido&quot; en el panel de administración se podía hacer clic varias veces o activarse presionando repetidamente la tecla &quot;Enter&quot;, lo que provocaba envíos de duplicado o pedidos con errores. Ahora, se evitan acciones adicionales hasta que el pedido se haya procesado por completo, lo que garantiza que solo se envíe un pedido.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: el administrador aún puede realizar pedidos igualado sin método de pago
   * _Nota_ de la corrección: El método de pago seleccionado anteriormente ahora se conserva cuando el método de pago vuelve a aparecer en la lista de pagos disponibles.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d50f6b5d>

### Pedido, pagos

* _ACP2E-3233:_ el administrador todavía puede realizar pedidos igualado sin método de pago
   * _Nota_ de corrección: Anteriormente, el comerciante podía realizar pedidos desde el panel de administración sin seleccionar un método de pago. Ahora, el comerciante se requiere un método de pago para proceder con la realización de un pedido.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/fd5cf3af>

### pedido, devoluciones

* _ACP2E-2982_: El reembolso del pedido resulta en duplicado nota de crédito
   * _Nota_ de corrección: Emitir el reembolso a través de la API de REST cuando se ejecutaron dos solicitudes idénticas simultáneamente ya no creará duplicado notas de crédito.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a4fbf702>

### Orden, Impuestos

* _ACP2E-3003_: [NUBE] base_row_total incorrecta en la API de pedido RESTFUL al habilitar transacciones entre borde y aplicar descuentos cupón
   * _Nota_ de corrección: Ahora se devuelve la base_row_total correcta de la API de pedido RESTFUL cuando la transacción entre borde está habilitada y se aplica cupón descuento.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/9af794a4>

### Otro

* _LYNX-339_: private_contenido_version cookie devuelto en consultas GQL
   * _Nota_ de corrección: Se ha corregido un problema por el que se devolvía el cookie private_contenido_version en consultas de GraphQL igualado cuando se deshabilitaba el cookie de sesión. El cookie ya no se incluye en las respuestas de GraphQL cuando la sesión está deshabilitada, como se esperaba.
* _LYNX-380_: is_available atributo en CartItemInterface devuelve siempre false para productos configurables
   * _Nota_ de corrección: se ha corregido un problema por el que el atributo is_available de CartItemInterface siempre devolvía false para los productos configurables en stock. Ahora, refleja correctamente la disponibilidad como verdadera cuando corresponde.
* _LYNX-382_: is_available atributo en CartItemInterface devuelve igualado verdadero cuando el stock vendible es inferior al cantidad del producto
   * _Nota_ de corrección: se ha corregido el problema por el que el atributo is_available de CartItemInterface devolvía incorrectamente el valor verdadero igualado cuando el artículo carro de compras cantidad excedía el stock vendible.
* _LYNX-399_: la miniatura de marcador de posición regresa cuando un producto simple agregado a carro de compras dentro de un producto agrupado
   * _Nota_ de corrección: Se ha corregido un problema por el que al agregar un producto simple (parte de un producto agrupado) al carro de compras se devolvía una imagen en miniatura de marcador de posición, igualado cuando el producto tenía una imagen asignada.
Detalles de la corrección:
• La miniatura del producto ahora muestra correctamente la imagen asignada si está disponible.
• La selección de miniaturas respeta la configuración del administrador en:
Configuración de > de las tiendas > ventas > cierre de compra > carro de compras > Imagen de productos agrupados.
Esto garantiza un comportamiento coherente de las miniaturas para los productos agrupados en función de la configuración tienda.
* _LYNX-400_: Los atributos de opciones personalizados del cliente no funcionan con valores enteros
   * _Nota_ de corrección: Se ha corregido un problema por el que los atributos de opción personalizados del cliente no funcionaban cuando el valor devuelto era un número entero. Las opciones personalizadas ahora tratan y devuelven correctamente los valores enteros según lo esperado.
* _LYNX-402_: Error interno del servidor al intentar obtener priceDetails para productos de paquetes con precio dinámico
   * _Nota_ de corrección: Se ha resuelto un problema por el que al consultar price_details productos de paquete con precios dinámicos a través de GraphQL se producía un error interno del servidor. Esta mejora garantiza una carro de compras consultas estables cuando se trabaja con productos paquete configurados con precios dinámicos.
* _LYNX-403_: only_x_left_in_stock siempre devuelve 0 para productos configurables
   * _Nota_ de corrección: se ha resuelto un problema por el que el atributo only_x_left_in_stock siempre devolvía 0 para productos configurables cuando se agregaba mediante el unidad de almacén principal con opciones.
Detalles de la corrección:
• El valor only_x_left_in_stock ahora refleja con precisión el stock de la variante secundaria seleccionada en lugar de la unidad de almacén principal.
• Esto garantiza que los niveles de stock se muestren correctamente para las variaciones de producto configurables en las páginas de carro de compras y productos.
* _LYNX-411_: GraphQL no consulta devolviendo el precio regular calculado correcto para productos personalizables
   * _Nota_ de corrección: Se ha corregido un problema por el que GraphQL no devolvía el precio regular calculado correcto para los productos personalizables. El consulta ahora incluye correctamente el precio regular calculado con valores personalizables aplicados (por ejemplo, $ 125) en los precios Propiedad, reflejando tanto el precio base como cualquier costo de personalización adicional.
* _LYNX-412_: Los impuestos aplicados mediante EstimatedTotals persisten con mutaciones actualizadas
   * _Nota_ de corrección: Se ha corregido un problema con la mutación EstimatedTotals por el cual los impuestos aplicados persistían en un igualado de carro de compras después de actualizar el área geográfica o el código postal. La mutación ahora actualiza correctamente los impuestos aplicados al cambiar entre los valores de área geográfica y código postal, asegurando que solo se aplique el regla fiscal correcto en función de los datos carro de compras actuales.
* _LYNX-420_: is_available atributo en CartItemInterface devuelve igualado verdadero cuando el stock vendible es inferior al cantidad del producto
   * _Nota_ de corrección: se ha corregido un problema por el que el atributo is_available de CartItemInterface devolvía incorrectamente igualado verdadero cuando el stock vendible era inferior al cantidad de producto solicitado. El campo is_available ahora devuelve correctamente false cuando el cantidad del producto supera el stock disponible.
* _LYNX-425_: Precio regular del producto con 12 decimales y valor incorrecto
   * _Nota_ de corrección: Se ha corregido un problema por el que el valor regular_price de las rutas product.price_range.maximum_price y minimum_price GraphQL no coincidía con el precio del catálogo cuando se aplicaban varios tipos impositivos. El regular_price ahora refleja consistentemente el precio del catálogo en todas las configuraciones de impuestos, lo que garantiza precios unitarios precisos, cálculos de costos totales de filas y verificaciones de descuento en el Resumen del carrito.
* _LYNX-430_: Error del servidor GraphQL en carro de compras con productos empaquetados agotados
   * _Nota_ de corrección: Se ha corregido un problema por el que GraphQL devolvía un error interno del servidor al recuperar un carro de compras que contenía un producto empaquetado con un artículo agotado, específicamente cuando el consulta incluía el Propiedad itemsV2. GraphQL ahora devuelve correctamente una lista de artículos con mensajes de error relevantes adjuntos a la entrada de artículo de producto agrupado, como se esperaba.
* _LYNX-441_: No es posible crear una dirección con atributos personalizados
   * _Nota_ de corrección: Se ha corregido un problema con la mutación createCustomerAddress que impedía la creación de direcciones con los atributos personalizados necesarios. La mutación ahora gestiona correctamente los atributos de dirección personalizados cuando se proporciona la carga útil adecuada.
* _LYNX-447_: Error del servidor GraphQL en carro de compras con only_x_left_in_stock en el producto incluido
   * _Nota_ de corrección: Se ha corregido un problema por el que la recuperación de un carro de compras que contenía un producto empaquetado con el campo only_x_left_in_stock en el consulta GraphQL provocaba un error interno del servidor. GraphQL ahora devuelve correctamente un float o null para el campo only_x_left_in_stock sin errores.
* _LYNX-464_: Error de GraphQL al eliminar otros productos con un producto configurable insuficiente en carro de compras
   * _Nota_ de corrección: Se ha corregido un problema en el que al intentar eliminar productos en stock del carro de compras se producía el error GraphQL &quot;La cantidad solicitada no está disponible&quot; si el carro de compras también contenía productos configurables con existencias insuficientes. La eliminación ahora funciona como se esperaba sin activar errores.
* _LYNX-469_: No se pueden agregar productos debido a unidad de almacén mutación que se está con distinción de mayúsculas y minúsculas
   * _Nota_ de corrección: se ha resuelto un problema por el que la mutación addProductsToCart devolvía un error &quot;PRODUCT_NOT_FOUND&quot; al usar SKU con mayúsculas y minúsculas diferentes. La mutación ahora gestiona las SKU sin distinción de mayúsculas y minúsculas, lo que garantiza la coherencia con las consultas del servicio de catálogo y el comportamiento de PDP.
* _LYNX-603_: El atributo de producto > formulario abreviado ™ de marca comercial se devuelve como ™
   * _Nota_ de corrección: Se ha resuelto el problema de codificación de caracteres con el nombre del producto para la API de GraphQL
* _LYNX-619_: problema de mutación updateCustomerEmail
   * _Nota_ de corrección: se ha resuelto un problema con la mutación updateCustomerEmail por el que los clientes sin los atributos personalizados necesarios (añadidos después de cuenta creación) no podían actualizar su correo electrónico.
* _LYNX-626_: La mutación setShippingAddressesOnCart genera un error al usar pickup_location_code
   * _Nota_ de corrección: se ha corregido un problema por el que la mutación setShippingAddressesOnCart devolvía un error al usar pickup_location_code sin especificar customer_address_id o dirección. La mutación ahora permite configurar correctamente una dirección de envío con solo el pickup_location_code.
* _LYNX-637_: Storefront Compatibilidad - Actualice la lógica para obtener el nombre de la tabla con prefijo y otras mejoras menores
   * _Nota_ de corrección: Se ha actualizado la lógica para recuperar el nombre de la tabla con el prefijo (relacionado con los cambios de SCP).
* _LYNX-643_: guardar en la libreta de direcciones no funciona al utilizar setBillingAddressOnCart Campo de same_as_shipping de GQL
   * _Nota_ de corrección: se ha corregido un problema por el que la dirección de envío no se guardaba en la libreta de direcciones del cliente al utilizar la mutación GraphQL setBillingAddressOnCart con el campo same_as_shipping establecido en true. Ahora, la dirección de envío se almacena correctamente como se esperaba.
* _LYNX-650_: Estandarizar el order_id en mutaciones
   * _Nota_ de corrección: Se ha estandarizado la entrada de order_id en las mutaciones y se ha actualizado la correo electrónico plantilla de confirmación de cancelación de pedido para exponer el ID de incremento en lugar del ID de pedido.
* _LYNX-651_: CustomerOrder no muestra el pedido comentarios
   * _Nota_ de corrección: se ha resuelto un problema con CustomerOrder para incluir el comentarios de pedido en las consultas GraphQL de pedidos de invitados y clientes.
* _LYNX-652_: original_item_price no debe incluir ningún descuento
   * _Nota_ de corrección: Se ha actualizado la lógica para original_item_price en los precios de los artículos del carro de compras de GraphQL para excluir los descuentos.
* _LYNX-681_: Bundle products todavía muestra &quot;IN_STOCK&quot; cuando uno de sus productos incluidos se agota
   * _Nota_ de corrección: se ha resuelto un problema por el que los product.stock_status de paquete productos seguían mostrando &quot;IN_STOCK&quot; igualado cuando uno de los artículos incluidos estaba agotado.
* _LYNX-686_: el consulta del cliente devuelve el servidor interno Error si existe un valor para el atributo personalizado eliminado para un cliente
   * _Nota_ de corrección: Se ha corregido el problema por el que el cliente devolvía consulta un error de servidor interno cuando un atributo personalizado eliminado todavía tenía un valor almacenado. Ahora, se devuelve un mensaje de error adecuado si se solicita un atributo inexistente. La caché necesaria se invalida al eliminar el atributo personalizado del cliente.
* _LYNX-687_: Parámetro de acción para vínculos de confirmación de devolución y cancelación
   * _Nota_ de corrección: Se agregó el parámetro Action para la confirmación de devolución y cancelación correo electrónico vínculos relacionados
* _LYNX-689_: La URL de confirmación del usuario de invitado se redirige al Página de estado del pedido, ya que falta orderRef
   * _Nota_ de corrección: Se ha agregado el parámetro orderRef a la vincular en la correo electrónico de confirmación de cancelación del pedido del huésped
* _LYNX-699_: No se puede devolver nulo para el campo no anulable &quot;TaxItem.title&quot; en placeOrder GQL
   * _Nota_ de corrección: se ha corregido un problema por el que la mutación placeOrder fallaba con un error interno del servidor debido a un valor nulo para el campo no anulable TaxItem.title. Ahora, el campo siempre devuelve un valor válido, lo que garantiza una correcta ubicación del pedido.
* _LYNX-702_: EstimateTotals: Descuentos es nulo para tipos de productos virtuales
   * _Nota_ de corrección: se ha resuelto el problema con la mutación estimateTotals que devuelve null para descuentos cuando se aplica un código de descuento a una carro de compras que contiene productos virtuales.
* _LYNX-703_: El paquete de productos no devuelve el porcentaje y la cantidad de descuento correctos
   * _Nota_ de corrección: Nuevo propiedades &quot;catalog_discount&quot; y &quot;row_catalog_discount&quot; se han introducido para que los precios de los artículos del catálogo muestren los importes y porcentajes de descuento correctos tanto en el nivel de fila como en el de un solo artículo.
* _LYNX-714_: Configuración de mensajes de regalo a nivel de producto
   * _Nota_ de corrección: Se ha corregido un problema por el cual los mensajes regalo no se aplicaban a nivel de producto cuando se deshabilitaba globalmente. Ahora, si los mensajes de regalo están habilitados para un producto específico, se pueden agregar correctamente mediante la mutación updateCartItems y se guardarán y reflejarán correctamente.
* _LYNX-757_: carro de compras.rules consulta error de retorno en lugar de una matriz vacía en caso de que no se apliquen reglas de carro de compras activas
   * _Nota_ de corrección: Se ha corregido el consulta carro de compras.rules para que devolviera una matriz vacía en lugar de un error cuando no se aplicaban reglas carro de compras activas.
* _LYNX-778_: Las llamadas GraphQL con método OPTIONS devuelven código de respuesta 500 cuando se instala el paquete adobe-commerce/storefront-compatibility
   * _Nota_ de corrección: Se ha corregido un problema por el que las llamadas GraphQL con el método OPTIONS devolvían un Error de servidor interno 500 cuando se instalaba el paquete de compatibilidad adobe-commerce/storefront. El punto final ahora devuelve correctamente una respuesta 200/204 como se esperaba.

### Otros Herramientas de desarrolladores

* _AC-10658_: [Problema] Corrección de error de sintaxis HTML en visual.phtml
   * _Nota_ de corrección: El sistema ahora cierra correctamente el etiqueta de inicio en el archivo visual.phtml, lo que garantiza una sintaxis HTML adecuada. Anteriormente, el etiqueta inicio no se cerraba correctamente, lo que provocaba un error de sintaxis HTML.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38247>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Se ha cambiado el problema] &quot;activo&quot; a &quot;habilitado&quot; en bin/magento mantenimiento:comando status
   * _Nota_ de corrección: El sistema ahora proporciona mensajes de estado más precisos para el comando del modo de mantenimiento, cambiando el estado de &quot;activo&quot; a &quot;habilitado&quot; y de &quot;no activo&quot; a &quot;deshabilitado&quot;. Anteriormente, el mensaje de estado para el comando del modo de mantenimiento se mostraba como &quot;activo&quot; o &quot;no activo&quot;, lo que podía posible cliente a confusión.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38486>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: La navegación en el árbol de categorías produce errores en Redis: &quot;La sesión de Redis excedió las conexiones simultáneas&quot;
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38851>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_: Problemas de CSP combinados con dev/css/use_css_esencial_path
   * _Nota_ de corrección: El sistema ahora carga correctamente los archivos CSS de forma asíncrona en las páginas de pago, igualado cuando la configuración &#39;dev/css/use_css_esencial_path&#39; está habilitada, lo que garantiza que estas páginas se representen con los estilos CSS adecuados. Anteriormente, una política de seguridad de contenido (CSP) restringida impedía la ejecución de JavaScript en línea, lo que provocaba que los archivos CSS no se cargaran como se esperaba.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39020>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Usar tipo virtual para configurar plug-in, el método interceptor no se puede generar correctamente en el comando de compilación de instalación:di:
   * _Nota_ de corrección: El sistema ahora genera correctamente métodos interceptores cuando se utiliza un tipo virtual para configurar un plug-in, asegurando resultados consistentes ya sean precompilados o compilados en tiempo de ejecución. Anteriormente, el sistema generaba resultados incorrectos cuando se precompilaba en comparación con la compilación en tiempo de ejecución.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/33980>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3631_: Las pruebas unitarias de Adobe Systems Commerce 2.4.7-p3 están fallando
   * _Nota_ de corrección: No se requieren Notas de la versión.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/982b1c42>

### Pago / Métodos de pago, Pedido

* _AC-13699_: El crédito de flujo de pago papal tarjeta los detalles guardados para su uso posterior no aparecen en el método de pago almacenado Página
   * _Nota_ de corrección: Los detalles anteriores del tarjeta de crédito de flujo de pago papal guardados para su uso posterior no aparecían en el método de pago almacenado Página que ahora es crédito fijo tarjeta los detalles aparecen en el método de pago almacenado Página.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/96dec499>

### Pagos

* _AC-13414_: El pago con tarjeta de crédito (enlace de flujo de pago) no funciona
   * _Nota_ de corrección: Error de obtención anterior (el pago se rechazó) al realizar el pedido con tarjeta de crédito después de la corrección El pedido se realizó correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: Payflow crea una nueva transacción cada vez que hacemos clic en buscar botón en la pantalla de vista transacción
   * _Nota_ de corrección: El sistema ahora obtiene correctamente la información de la transacción sin crear una nueva transacción de pago cada vez que se hace clic en el botón de recuperación en la pantalla de transacción vista. Anteriormente, al hacer clic en el botón de recuperación se creaba incorrectamente una nueva transacción de pago para un pedido que ya se había pagado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: El mensaje de Paylater no se muestra en PDP para PayPal canadienses comerciante cuenta
   * _Nota_ de corrección: El sistema ahora muestra correctamente el mensaje PayLater para las cuentas de comerciante PayPal canadienses en el Página de detalles del producto (PDP) cuando el país del comprador se puede determinar a partir de la dirección facturación cuenta o el envío. Anteriormente, el mensaje PayLater no se mostraba debido a la falta de un parámetro, lo que provocaba un error en la consola de explorador.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_: PayPal reembolso del pedido resulta en duplicado nota de crédito
   * _Nota_ de corrección: Se corrigió el problema de simultaneidad de las notas de crédito creadas por IPN para PayPal servicio de pago.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: El precio del carro de regla no funciona durante PayPal
   * _Nota_ de corrección: La cantidad correcta se muestra en PayPal lateral cuando se aplica el descuento por método de pago
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [Los usuarios de nube] con un función específico no pueden inicio de sesión
   * _Nota_ de corrección: los usuario de administrador con función que contienen solo acceso a la sección PayPal ahora pueden inicio de sesión sin errores
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/66dea0de>

### Rendimiento

* _AC-11932_: Atributo de producto predeterminado Configuración problema
   * _Nota de corrección_: El sistema ahora permite a los usuarios anular la selección de una opción predeterminada para un atributo de producto, lo que garantiza que el atributo no siempre tenga un valor predeterminado. Anteriormente, una vez que se establecía un valor predeterminado para un atributo de producto, no había forma de anular su selección, lo que provocaba que el atributo siempre tuviera un valor predeterminado.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38703>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_: [Emitir] limpieza Code y agregar nuevo bloqueo esencial encabezado y mover esencial css antes de activos
   * _Nota_ de corrección: El sistema ahora incluye un nuevo bloque de cabeza de esencial y se mueve esencial CSS antes de activos, lo que permite una mayor personalización y optimización del rendimiento en el frontend. Anteriormente, el esencial CSS no estaba posicionado antes del activos, lo que limitaba las oportunidades de personalización y optimización.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38748>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: La compilación de temas se interrumpe cuando la host mysql contiene información puerto
   * _Nota_ de corrección: El sistema ahora maneja correctamente MySQL host configuración que incluye información puerto, asegurando una compilación exitosa del tema. Anteriormente, la compilación de temas fallaba si la configuración de host MySQL en la conexión de base de datos incluía información puerto.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38799>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: Soporte para CommandLoaderInterface de Symfony en Magento CLI
   * _Nota_ de corrección: Este cambio reduce el tiempo de inicialización de la aplicación Magento CLI al permitir la inicialización diferida de comandos hasta que sean necesarios.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/29266>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: Problema de rendimiento al cargar atributos de producto en reglas de carro de compras
   * _Nota_ de corrección: Rendimiento consulta mejorado para las reglas de ventas, de alrededor de 150 ms a un solo dígito ms.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: Rendimiento de indexación parcial de precio
   * _Nota de corrección_: El rendimiento de indización parcial de precios se ha mejorado al optimizar algunas de las consultas de eliminación utilizadas en el proceso de indización.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: El pedido se rechaza en la configuración multi tienda cuando se utiliza el procesamiento de pedidos asíncronos + Términos y condiciones
   * _Nota de corrección_: ahora se procesan los pedidos realizados desde sitios web no predeterminados con los términos y condiciones habilitados.
Antes de que se rechazaran automáticamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: La llamada a la API Rest de pedidos está tardando mucho tiempo en ejecutarse
   * _Nota de corrección_: El sistema ahora ejecuta la llamada a la API de Order Rest en un período de tiempo razonable, lo que mejora el rendimiento al recuperar un gran número de pedidos. Anteriormente, la llamada a la API de Order Rest tardaba mucho tiempo en ejecutarse, lo que provocaba retrasos al recuperar un gran número de pedidos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/001e5188>

### Precio

* _AC-11810_: Magento2.4.6-p4 Pedido API Simple Artículo sin precio
   * _Nota_ de corrección: El sistema ahora muestra correctamente el precio de productos simples cuando se consulta a través de la API de pedidos, lo que garantiza una representación precisa de los datos. Anteriormente, el precio de los productos simples se mostraba incorrectamente como cero en la respuesta de la API.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: Error de redondeo de centavos en el catálogo regla
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
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - Argumento #2 ($storeId) debe ser de tipo int, cadena dada
   * _Nota_ de corrección: El sistema ahora activa correctamente los correos electrónicos de alerta de producto asegurándose de que el identificador de tienda sea del tipo de datos correcto. Anteriormente, los correos electrónicos de alerta de producto no se enviaban debido a una falta de coincidencia de tipos en el identificador tienda.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/35602>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [La función Cloud] addFilterToMap no funciona para ciertas columnas
   * _Nota_ de corrección: Ahora, la módulo personalizada se puede utilizar en la cuadrícula de pedidos. Anteriormente, se producían errores al utilizar un módulo personalizado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3a7c4d17>

### Promoción

* _ACP2E-2602_: Atributo del cliente no visible al crear cuenta desde la invitación
   * _Nota_ de la corrección: Los atributos del cliente están disponibles al crear cuenta desde la invitación.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: El código de cupón con límite de Usos por cupón no se libera para el error de pago con cancelación del pedido
   * _Nota de corrección_: El sistema ahora actualiza inmediatamente cupón usos cuando se crea o cancela un pedido, y agrega regla usos a un cola para evitar posibles interbloqueos. Esto garantiza que se libere un código cupón con un límite de &quot;Usos por cupón&quot; y se pueda reutilizar si se cancela un pedido debido a un pago fallido. Anteriormente, el sistema no liberaba el código de cupón para su reutilización en tales casos, lo que generaba un mensaje de error que indicaba que el código cupón no era válido.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [Regla de catálogo de reindexación en la nube] El indexador de productos lanza SQLSTATE[HY000]: Error general: 2006 El servidor MySQL ha desaparecido.
   * _Nota_ de corrección: El sistema ahora maneja correctamente el valor personalizado &quot;batchCount&quot; en el di.xml para el &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, evitando errores SQL como &quot;Error general: 2006 MySQL server has gone away&quot; durante la reindexación del Catalog Rule Product Indexer debido al tamaño incorrecto del lote en catálogos grandes
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3139_: La regla de ventas con el atributo Discount Qty Step (Buy X) hace que no se apliquen otras reglas
   * _Nota_ de corrección: El regla de precios del carrito no cancela las reglas aplicadas anteriormente si la cantidad del producto en el carro de compras no es suficiente para aplicar regla.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_: Emitir reglas de venta con descuento de cantidad fija y &quot;Se aplica el descuento por cantidad máxima&quot;
   * _Nota_ de corrección: Se corrigió un problema con el descuento de reglas de carro de compras, cuando el descuento de cantidad fija está configurado para aplicarse a una cantidad limitada de productos es el carro de compras. Anteriormente, el valor &quot;Se aplica el descuento por la cantidad máxima&quot; para calcular el precio del artículo actual en el carro de compras, no solo para calcular el descuento del regla.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_: Reglas del carro de compras La acción &quot;Descuento por importe fijo para todo el carro de compras&quot; aplica descuentos incorrectamente
   * _Nota_ de corrección: Los códigos de cupón se validarán correctamente independientemente de las mayúsculas o minúsculas, cuando se utilicen en la creación de pedidos desde el área de administración. Antes, el código cupón no se validaba si no coincidía con las letras mayúsculas y minúsculas exactas del código de regla carro de compras configurado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: en Backend, valores de tienda predeterminados para los atributos del producto (en lugar de los valores de administración esperados)
   * _Nota_ de la corrección: Ahora en Backend, se utilizan valores de administrador en lugar de valores de tienda predeterminados para los atributos del producto.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: Las reglas del carro de compras La acción &quot;Descuento por importe fijo para todo el carro de compras&quot; aplica descuentos incorrectamente al agregar productos paquete
   * _Nota_ de corrección: Las reglas de cantidad fija carro de compras no se aplicaban correctamente a paquete productos. Ahora, al calcular el monto total del descuento, paquete productos secundarios se toman en consideración, lo que resulta en un cálculo de descuento adecuado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: Reglas de precios del carro de compras que calculan mal el descuento
   * _Nota_ de corrección: Los descuentos por importe fijo ahora se están calculando correctamente. Antes de la corrección, los descuentos por importe fijo no se totalizaban correctamente para paquete productos.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: No se muestran las categorías anidadas en condiciones de regla
   * _Nota_ de corrección: Se ha corregido el problema cuando las categorías anidadas en categoría de nivel 3 no se mostraban en las reglas de marketing para categoría condición
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit y uses_per_customer no se actualizan en la tabla salesrule_cupón
   * _Nota_ de corrección: La actualización de Usos por cupón y Usos por cliente en carro de compras regla de precio afectará ahora a los cupones autogenerados existentes. Anteriormente, los nuevos valores solo afectaban a los nuevos cupones
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: regla de precio del carro de compras no tiene en cuenta la categoría principal cuando utiliza la condición &quot;igual o mayor que&quot;.
   * _Nota de corrección_: Las reglas de precios del carro de compras ahora consideran correctamente la categoría principal cuando se utiliza en condiciones avanzadas
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: Cálculo de descuento no válido con prioridad
   * _Nota_ de corrección: En el caso de la cantidad fija aplicada para todo el tipo de descuento carro de compras, la cantidad no se estaba calculando correctamente para carro de compras artículos que ya estaban descontados por un promoción anterior. Ahora, los descuentos se resumen correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_: [CLOUD] El cálculo del envío no tiene en cuenta el carro de compras regla
   * _Nota_ de corrección: Antes de la corrección, un regla carro de compras con área geográfica condición no se aplicaba de forma coherente. Después de la corrección, carro de compras reglas con área geográfica condiciones se aplican correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_: la condición de sku de regla carro de compras no funciona en la factura.
   * _Nota_ de corrección: El descuento en el producto Bundle con precio dinámico ahora se refleja correctamente en la factura. Anteriormente, el descuento no se reflejaba en la factura.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: Valor de descuento incorrecto cuando se aplican varias reglas de precios carro de compras simultáneamente con productos con descuento/precio especial
   * _Nota_ de corrección: Antes de la corrección, la cantidad fija para reglas de carro de compras completas no se aplicaba correctamente si se aplicaba más de una. Ahora, las reglas de descuento carro de compras de cantidad fija se están aplicando correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1984c61c>

### Optimización de los motores de búsqueda

* _AC-11907_: Agregar URL reescribir con acento causa una carga infinita
   * _Nota_ de corrección: El sistema ahora crea y funciona con éxito URL reescribe con acentos, evitando la carga infinita durante el proceso de guardado. Anteriormente, añadir un URL reescribir con acento causaba un problema de carga infinita.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38692>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: Multi Store Se ha categoría reescritura de url incorrecta para categoría de tercer nivel
   * _Nota de corrección_: Generar reescrituras de URL correctas para elementos secundarios con elemento principal con clave de URL definida personalizada
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: Caracteres de doble byte (caracteres especiales) en el campo Nombre del producto bloquea la creación de productos en el servidor
   * _Nota_ de corrección: Se ha añadido una nueva configuración que permite aplicar o no la transliteración a los URL del producto. La configuración está disponible aquí: Almacena > Configuración > Catálogo > Optimización del > del Search Engine de Aplicar: &quot;transliteración  para URL del producto&quot;
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_: Creación incorrecta de entradas de url_rewrite con varios almacenes en un tienda grupo
   * _Nota_ de corrección: Antes de la corrección, solo se podía generar URL reescrituras a nivel de sitio web al editar un producto. Con la corrección, se introdujo una nueva configuración (Configuración de > Tiendas > Catálogo > Catálogo > Optimización del motor de Search, &quot;Alcance de reescritura de URL de productos&quot; con opciones &quot;Tienda vista&quot;, &quot;Sitio web&quot;) que le permite generar URL reescrituras a nivel de vista o sitio web de tienda.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/2d627301>

### Buscar

* _AC-13053_: obtención de &quot;Ingrese un término búsqueda e inténtelo de nuevo&quot;. Error en el Página de búsqueda avanzado en StoreFront en 2.4.8-beta1
   * _Nota_ de corrección: El sistema ahora muestra correctamente búsqueda resultados en el Página de Search de Avanzadas cuando un atributo de producto se establece en &quot;No&quot;. Anteriormente, establecer un atributo de producto en &quot;No&quot; y realizar una búsqueda daba como resultado un mensaje de error &quot;Ingrese un término búsqueda e inténtelo de nuevo&quot;.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/módulo-open-búsqueda depende de un Rama opensearch-php inexistente
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: búsqueda_consulta tabla cuando es de gran tamaño, tiene un gran impacto en el frontend de tiempo de carga
   * _Nota_ de corrección: Se ha mejorado el tiempo de carga del Página del listado de búsqueda. Antes de la corrección, el Página de listado de búsqueda se retrasaba debido a un consulta no optimizado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/55615e61>

### Seguridad

* _AC-11855_: [Problema] que falta la fuente CSP Paylater Popup
   * _Nota_ de corrección: El sistema ahora permite la carga del fuente &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sin violar la directiva de Política de seguridad de contenido, asegurando la correcta visualización de la ventana emergente de Paylater. Anteriormente, el fuente se negaba a cargar debido a una infracción de la directiva Política de seguridad de contenido, lo que causaba problemas de visualización con la ventana emergente de Paylater.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38624>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [Actualización del problema] js.js texto DOM reinterpretado como HTML
   * _Nota_ de corrección: Al usar innerText, evitará el riesgo de inserción de HTML, ya que estas propiedades escapan automáticamente cualquier carácter especial HTML en el texto proporcionado. Esta corrección ayuda a prevenir vulnerabilidades ejecución de scripts en sitios múltiples (XSS) al tratar la entrada como texto sin formato en lugar de HTML interpretado.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 se muestra incorrectamente al finalizar la compra para Alemán idioma
   * _Nota_ de corrección: Anteriormente, el recaptcha de debajo de correo electrónico dirección del cierre de compra aparecía sin estilo para idiomas con palabras largas, gustar alemán. Después de esto, el recaptcha tiene el mismo aspecto que todos los elementos de recaptcha del resto de las áreas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha en el inicio de sesión de administración no requiere interacción para algunos usuarios
   * _Nota_ de corrección: ReCaptcha para inicio de sesión de administrador se valida según lo esperado
   * _Contribución_ de código de GitHub: <https://github.com/magento/security-package/commit/8f64ab3c>

### Naviero

* _AC-10757_: [Problema] Se ha corregido un error tipográfico en seguimiento.phtml - se cambió el nombre de las funciones JS &quot;currier&quot; a &quot;carrier&quot;
   * _Nota_ de corrección: El sistema ahora utiliza correctamente el término &quot;carrier&quot; en lugar del mal escrito &quot;currier&quot; en las funciones del controlador de JavaScript utilizadas en el orden seguimiento plantilla, lo que garantiza la nomenclatura adecuada de las funciones y la claridad del código. Anteriormente, se usaba el término mal escrito &quot;currier&quot;, lo que generaba confusión e inconsistencia en la base de código.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/34523>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST &quot;Un envío no puede tener un KGS/IN o LBS/CM u OZS/CM como unidad de medida&quot;
   * _Nota_ de corrección: Asegúrese de que las tarifas de UPS sean visibles en el proceso de pago y carro de compras.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38618>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-13172_: [Problema] Ortografía correcta de variables para la dirección del cliente
   * _Nota_ de corrección: El sistema ahora escribe correctamente las variables para las direcciones de los clientes, lo que garantiza una visualización precisa en el área cuenta del front-end. Anteriormente, la ortografía incorrecta de estas variables podía posible cliente a errores durante las revisiones de código local.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/32817>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: Ventana de seguimiento que muestra una fecha de entrega prevista incorrecta
   * _Nota_ de corrección: Muestra la fecha de entrega correcta para Fedex Carrier.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Las tarifas de la tabla siguen mostrando a pesar de que se aplica el envío gratuito
   * _Nota_ de corrección: El método de envío de tarifa de tabla ahora se muestra igualado si el Envío gratuito está disponible después de cupón aplicar
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF prueba AdminCreatingShippingLabelTest fallan debido a credenciales no agregadas en Jenkins entorno
   * _Nota_ de corrección: corrección de mftf prueba
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: FedEx Track API no funciona con credenciales REST
   * _Nota_ de corrección: Anteriormente, la integración de FedEx no requería claves de API adicionales para la API de seguimiento. Ahora se ha añadido una nueva configuración para admitir claves de API de seguimiento.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [Las tarifas negociadas de FedEx en la nube] no se devuelven en REST
   * _Nota_ de corrección: Anterior a la corrección, FedEx cuenta tarifas específicas no se enviaron en la respuesta, igualado de acuerdo con la documentación de FedEx deberían haberse enviado. Después de la corrección, las tasas cuenta específicas se envían en la respuesta cambiando la solicitud de nuestro lado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/55615e61>

### Puesta en escena y Vista previa

* _ACP2E-3453_: No se puede actualizar la actualización programada cuando se utiliza un atributo de Categoría personalizado único
   * _Nota_ de corrección: Se ha corregido un problema por el que no era posible actualizar una actualización programada para un categoría si el categoría tenía un atributo único
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>

### Direccionamiento

* _AC-9432_: [Problema] Permitir el uso de intervalos CIDR en mantenimiento Permitir lista
   * _Nota de corrección_: El sistema ahora admite el uso de rangos CIDR en el modo de mantenimiento permitir lista IP, lo que permite que un rango de direcciones IP omita el modo de mantenimiento. Anteriormente, el modo de mantenimiento permitía lista IP solo permitía que las direcciones IP individuales omitieran el modo de mantenimiento.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37943>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/30699>

### Impuesto

* _AC-13295_: [Problema] Feature/php8.1 constructor Propiedad promoción wee graph ql
   * _Nota_ de corrección: Reemplazar casi todas las propiedades con Propiedad constructor promoción en módulo pequeño grafo ql:
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/39309>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: El impuesto sobre el producto fijo (FPT) no funciona con productos configurables
   * _Nota_ de corrección: FPT para variaciones de producto configurables que funcionan correctamente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ec7e32a9>

### marco de trabajo de prueba

* _AC-11654_: Integración prueba falla testDbSchemaUpToDate debido al tipo de columna JSON
   * _Nota_ de corrección: El sistema ahora reconoce correctamente los tipos de columna JSON en el esquema de la base de datos durante las pruebas de integración, evitando errores de prueba debido a una falta de coincidencia entre el esquema de la base de datos y el esquema declarativo. Anteriormente, el sistema identificaba incorrectamente los tipos de columna JSON como LONGTEXT en MariaDB, lo que provocaba que las pruebas de integración fallaran.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Problema de] corrección ortográfica de PHPDoc
   * _Nota_ de corrección: El sistema ahora reconoce correctamente los métodos obsoletos en los IDE debido a una corrección ortográfica en PHPDoc. Anteriormente, un error ortográfico en PHPDoc causaba que los IDE no reconocieran ciertos métodos como obsoletos.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/31399>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Comprobación del comportamiento con el carro de compras persistente después de que expire la sesión
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13848_: Corregir pruebas estáticas para permitir el uso por parte de extensiones de terceros
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [El error de aplicación del accesorio interno] no se muestra durante la ejecución o en los registros
   * _Nota_ de corrección: &#39;-
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [MFTF] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Nota de corrección_: Mftfs fijos
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/078c387e>

### Marco IU

* _AC-12128_: corrección de vulnerabilidad de seguridad de Prototipo.js CVE-2020-27511
   * _Nota_ de corrección: El sistema se ha actualizado para corregir la vulnerabilidad de seguridad CVE-2020-27511 en Prototipo.js 1.7.3, lo que mejora la seguridad general del sistema. Antes de esta actualización, el sistema era susceptible a una denegación de servicio de expresión regular (ReDOS) mediante la eliminación de etiquetas HTML elaboradas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less usa el prefijo pub/ para los mapas de origen
   * _Nota_ de corrección: El sistema ahora genera mapas fuente less/css sin el prefijo /pub para las rutas cuando se utiliza grunt, eliminando la necesidad de una solución alternativa en la configuración del servidor web. Anteriormente, el uso del prefijo /pub en las rutas de sourcemaps requería una configuración específica en el servidor web para funcionar correctamente.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38837>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38840>
* _AC-12432_: Campo de Archivo Ui Componente
   * _Nota de corrección_: el sistema ahora valida correctamente el campo de archivo en un formulario de componente de interfaz de usuario, lo que permite enviar el formulario sin errores cuando se selecciona un archivo. Anteriormente, la validación fallaba incluso cuando se seleccionaba un archivo, lo que impedía el envío del formulario.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38908>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [Problema] Se mejoró el formato de fecha en la consola js: cambia de 12 horas a 24 horas para...
   * _Nota_ de corrección: formato de fecha mejorada en la consola js: cambiar de 12 horas a 24 horas
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38983>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [Problema] para agregar generación de SourceMap para menos archivos en modo de desarrollador
   * _Nota_ de corrección: El sistema ahora genera mapas de origen para menos archivos cuando está en modo de desarrollador, lo que facilita la identificación de la fuente de un estilo. Anteriormente, identificar la fuente de un estilo era un desafío cuando se ejecutaba el sistema en modo de desarrollador con del lado del servidor menos compilación.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/38982>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38977>
* _AC-1306_: Se está implementando un contenido estático para los módulos deshabilitados
   * _Nota_ de corrección: El sistema ahora excluye CSS relacionado con módulos deshabilitados de los archivos de salida CSS finales, asegurando que no se carguen estilos innecesarios. Anteriormente, CSS relacionado con los módulos deshabilitados se incluía en los archivos de salida CSS finales, lo que llevaba a la carga de estilos adicionales e innecesarios.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/24666>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: Comportamiento inconsistente en la ordenación &quot;Fuera de Stock&quot; con umbral de Stock mínimo
   * _Nota_ de corrección: El sistema ahora ordena correctamente los productos en el catálogo en función de los niveles de existencias, cumpliendo con el umbral de Stock mínimo establecido y moviendo los artículos agotados a la parte inferior del lista de manera consistente. Anteriormente, el comportamiento de clasificación era inconsistente, ya que los artículos no siempre aparecían en el orden correcto en función de sus niveles de existencias, y los cambios en la clasificación podían ocurrir de forma impredecible después de guardar, actualizar o modificar el jerarquía categoría.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Sugerencia para mejorar la sistema de informes de errores para problemas de carga de require.js
   * _Nota_ de corrección: Este PR mejora el mensaje de error cuando requirejs no puede cargar un componente.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/36761>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: Errores de obsolescencia de PHP 8.4 que causan errores de compilación en 2.4-develop
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Problema] No cargar el contexto del bloque del servidor en el front-end
   * _Nota_ de corrección: El sistema ahora garantiza que el contexto del bloque del backend no se cargue en el frontend, evitando la creación de sesiones de backend innecesarias y posibles bloqueos de sesión. Anteriormente, el sistema cargaba incorrectamente el contexto del bloque de backend en el frontend, lo que llevaba a la creación de sesiones de backend y posibles bloqueos de sesión.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37617>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [Problema] Quitar resumen de revisión de scripts innecesarios
   * _Nota_ de corrección: El sistema ahora optimiza el tiempo de carga de Página eliminando scripts de JavaScript innecesarios de la sección de calificación, en lugar de usar estilos CSS en línea para un código más eficiente y legible. Anteriormente, el uso de scripts de JavaScript para la sección de clasificación podía ralentizar Página tiempo de carga.
   * _Problema_ de GitHub: <https://github.com/magento/magento2/issues/37776>
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: Excepción al comprobar un regalo tarjeta saldo cuando Recaptcha está habilitado
   * _Nota_ de corrección: Los usuarios podrán obtener el saldo de tarjeta de regalo en la vista y editar carro de compras pantalla. Anteriormente, estos detalles no se mostraban mientras reCAPTCHA estaba habilitado.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [Solicitud de función de ACLARACIÓN] Cumplimiento de la ADA
   * _Nota_ de corrección: El sistema ahora garantiza el cumplimiento de la ADA eliminando las propiedades CSS no compatibles y reemplazándolas por otras compatibles en el archivo print.css. Anteriormente, el uso de propiedades CSS no admitidas provocaba problemas de compatibilidad explorador.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Cloud] Confusion código biblioteca en effect-drop.js de AC 2.4.4-p8
   * _Nota_ de corrección: El sistema ahora implementa correctamente el biblioteca de effect-drop.js, asegurando el correcto funcionamiento de los efectos de IU jQuery. Anteriormente, el biblioteca effect-drop.js se sobrescribía por error con el biblioteca effect-clip.js, lo que causaba posibles problemas con los efectos IU jQuery.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: Encabezado del sitio | Caracteres especiales Desglose de la sección Bienvenido del cliente
   * _Nota_ de corrección: Después de la corrección, los caracteres especiales se muestran correctamente en la sección de bienvenida al cliente.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: La edición del segmento de clientes falla con intervalo de fechas
   * _Nota_ de corrección: Es posible guardar las segmento del cliente con intervalo de fecha condición, cuando solo se editó una de las fechas.
   * _Contribución_ de código de GitHub: <https://github.com/magento/magento2/commit/a52ff98f>
