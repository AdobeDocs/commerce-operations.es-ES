---
source-git-commit: 2d46933005b9848fee526d0a9f96e2e5ff58cbb8
workflow-type: tm+mt
source-wordcount: '14732'
ht-degree: 0%

---
# Notas de la versión de Magento Open Source (versión 2.4.8-beta1)

## Características destacadas

Los 49 aspectos destacados siguientes se aplican a la versión de Magento Open Source 2.4.8.

### Marco

* _AC-10721_: actualice las dependencias del Compositor de sistemas de archivos/liga a la versión más reciente
   * _Nota de corrección_: Actualice las dependencias del Compositor de sistemas de archivo/liga 2.x a la última versión 3.x
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_: Actualización de componentes de plataforma 2.4.8-beta1
* _AC-11673_: Investigue las últimas versiones de php-amqplib/php-amqplib
   * _Nota de corrección_: Se ha actualizado la versión más reciente php-amqplib/php-amqplib :^3.x
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_: Refactorización del marco de prueba de integración para la compatibilidad con phpunit 10 - IntegrationTest.php no encontrado
   * _Nota de corrección_: PHPUnit 9 se ha actualizado a PHPUnit 10 con los cambios del módulo de pruebas de integración y WebAPI de Adobe Commerce. Los cambios de PHPUnit 10 son compatibles con versiones anteriores.
   * _Contribución de código de GitHub_: &lt;https://github.com/magento/magento2/ (interno, sin combinar)>
* _AC-11813_: Marco de prueba de WebApi para la compatibilidad con phpunit 10. Problema relacionado con la conectividad de RabbitMQ SOAP con módulos B2B y con los módulos B2B.
   * _Nota de corrección_: PHPUnit 9 se ha actualizado a PHPUnit 10 con los cambios del módulo de pruebas de integración y WebAPI de Adobe Commerce. Los cambios de PHPUnit 10 son compatibles con versiones anteriores.
   * _Contribución de código de GitHub_: &lt;https://github.com/magento/magento2/ (interno, sin combinar)>
* _AC-11816_: Agregar compatibilidad con MySQL 8.4 LTS
* _AC-11911_: limpieza de css de jQuery/fileuploader después de la migración a la biblioteca de carga
   * _Nota de corrección_: se quitó la biblioteca jQuery/fileUploader porque se migró a la biblioteca de actualización
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: Agregar compatibilidad con MySQL 8.4 LTS para Magento CE
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_: marcar el módulo elasticsearch 8 como obsoleto
* _AC-12015_: limpieza de la carpeta ExtJs después de la migración a la biblioteca jsTree
   * _Nota de corrección_: se ha eliminado la carpeta extJs porque la funcionalidad relacionada se ha migrado a jsTree
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: actualizar la dependencia del sistema monólogo/monólogo a la última versión principal
   * _Nota de corrección_: el sistema se ha actualizado para utilizar la última versión principal de la biblioteca &quot;monólogo/monólogo:^3.x&quot;, lo que garantiza la compatibilidad y mejora el rendimiento. Anteriormente, el sistema utilizaba una versión obsoleta de la biblioteca &quot;monólogo/monólogo&quot; que podría haber provocado posibles problemas y limitaciones.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: actualice la dependencia de wikimedia/less.php a la última versión principal
   * _Nota de corrección_: El sistema se ha actualizado para utilizar la última versión principal 5.x de la biblioteca &quot;wikimedia/less.php&quot;, lo que garantiza la compatibilidad y la funcionalidad actualizada. Anteriormente, el sistema utilizaba una versión obsoleta de la biblioteca que podría haber provocado problemas de seguridad.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: actualice la dependencia de biblioteca jquery/validate a la última versión secundaria
   * _Nota de corrección_: Actualice la dependencia de biblioteca jquery/validate a la última versión secundaria 1.20.0
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: actualice la dependencia del sistema moment.js a la última versión secundaria
   * _Nota de corrección_: Actualice la dependencia del sistema moment.js a la última versión secundaria 2.30.1
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: Agregar compatibilidad con MySQL 8.4 LTS para EE
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: Agregar compatibilidad con MySQL 8.4 LTS para B2B
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: Agregar compatibilidad con MySQL 8.4 LTS para extensiones de paquete
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: Agregar compatibilidad con MariaDB 11.4 LTS para CE
   * _Nota de corrección_: se ha agregado compatibilidad con MariaDB 11.4 con Adobe Commerce y extensiones
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: Optimización de suscriptores - PhpUnit10
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: admite reintentos de conexión para la sesión de Redis y compatible con colinmollenhour/php-redis-session-abstract v2.0.0
   * _Nota de corrección_: Se ha actualizado la última versión de colinmollenhour/php-redis-session-abstract v2.0.0 compatible con adobe commerce
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12268_: actualizar las dependencias del Compositor de sistemas de archivos/liga a la versión más reciente
   * _Nota de corrección_: Actualice las dependencias del Compositor de sistemas de archivo/liga 2.x a la última versión 3.x
* _AC-12576_: Investigue los errores de las pruebas de automatización con MySQL 8.4 LTS
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: Agregar compatibilidad con MariaDB 11.4 LTS For EE
   * _Nota de corrección_: se ha agregado compatibilidad con MariaDB 11.4 con Adobe Commerce y extensiones
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_: Investigue la herramienta de migración de datos (DMT) con MySQL 8.4 LTS
* _AC-12715_: actualizar las dependencias del Compositor de láminas a la versión más reciente
   * _Nota de corrección_: el sistema ahora admite las últimas versiones de las dependencias del compositor de láminas:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validador
garantizar la compatibilidad y la funcionalidad actualizada. Anteriormente, la actualización a las versiones más recientes de estas dependencias podría provocar problemas de incompatibilidad con versiones anteriores y errores de prueba.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_: Agregar compatibilidad con MariaDB 11.4 LTS para la herramienta de migración de datos
   * _Nota de corrección_: se ha agregado compatibilidad con MariaDB 11.4 con Adobe Commerce y extensiones
* _AC-12823_: Investigue el error de prueba de unidad debido a la actualización del parche de phpunit durante la actualización del componente
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_: compatibilidad de las herramientas SVC y EAT con MySQL 8.4
* _AC-12898_: compatibilidad de la herramienta UCT con MySQL 8.4
   * _Nota de corrección_: La herramienta de compatibilidad de actualización (UCT) ahora es compatible con MySQL 8.4, lo que garantiza un funcionamiento sin problemas y comprobaciones de compatibilidad para las instancias que se ejecutan en esta versión. Anteriormente, la herramienta UCT no se probaba y comprobaba para la compatibilidad con MySQL 8.4.
* _AC-9749_: actualización a PHPUnit 10
   * _Nota de corrección_: Se han actualizado las dependencias del compositor phpunit/phpunit a una versión compatible - &quot;phpunit/phpunit&quot;:&quot;10.x&quot;

### Instalar y administrar

* _AC-6819_: establezca los indizadores en &quot;Actualizar según lo programado&quot; de forma predeterminada

### Pedido

* _ACP2E-2709_: [Solicitud de característica] El cliente sugiere que el botón Enviar comentario en la página Detalles del pedido es confuso y debería cambiarse por otra cosa
   * _Nota de corrección_: para minimizar la confusión, la etiqueta del botón &quot;Enviar comentario&quot; cambió a &quot;Actualizar&quot; en la página de detalles del pedido.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/488c1034>

### Otros

* _AC-11420_: los indizadores establecidos aparecen en el estado Listo de forma predeterminada cuando se instala una nueva versión de Adobe Commerce
   * Magento _Nota de corrección_: después de la instalación, el estado del indizador debe estar en el estado *Listo* de forma predeterminada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: en la instalación de Magento existente al instalar un módulo de indizador de terceros, los indizadores se actualizan de forma predeterminada según lo programado.
   * _Nota de corrección_: todos los indizadores nuevos se encuentran de forma predeterminada en el modo [Actualizar mediante programación]. Anteriormente, el modo predeterminado era [Actualizar al guardar]. Lo mismo ocurre con los indexadores personalizados.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: las opciones de Elasticsearch 7 y 8 deben incluir opciones obsoletas en la configuración del administrador.
   * _Nota de corrección_: la opción Elasticsearch 8 de la Configuración de administración se mostrará con texto obsoleto para informar a los usuarios de que ya no se recomienda utilizar la opción Elasticsearch 8.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: agregar nota de texto cuando la opción Elasticsearch está seleccionada en Configuración de administración
   * _Nota de corrección_: Se agrega una nota de texto para informar a los usuarios administradores de Adobe Commerce que elasticsearch ya no es compatible con el Adobe y que está obsoleto.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_: compatibilidad de las herramientas SVC y EAT con MariaDB 11.4
   * _Nota de corrección_: compatibilidad de las herramientas SVC y EAT con MariaDB 11.4
* _AC-12876_: compatibilidad de la herramienta UCT con MariaDB 11.4
* _LYNX-374_: documente la confirmación por correo electrónico mediante GraphQL
* _LYNX-376_: documento que obtiene configuraciones para reCAPTCHA en GraphQL
* _LYNX-409_: optimizaciones de consulta de base de datos para la mutación de elementos del carro de compras de actualización

### Seguridad

* _AC-11041_: mejoras de seguridad para 2.4.8-beta1 a partir de la versión de junio de 2024
* _AC-11864_: mejoras de seguridad para 2.4.8-beta1 a partir de la versión de agosto de 2024
* _AC-12346_: mejoras de seguridad para 2.4.8-beta1 a partir de la versión de octubre de 2024
* _AC-12691_: [2.4.8-beta1] El extremo de la API de REST de actualización del cliente no funciona
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4102373>, <https://github.com/magento/magento2/commit/a4102373>

### Marco de IU

* _AC-12726_: [2.4.8-beta1] TinyMCE 5 migración a TinyMCE 7
   * _Nota de corrección_: Se migró TinyMCE 5 a TinyMCE 7.3.0 para que fuera una versión compatible con Adobe Commerce; anteriormente el sistema utilizaba 5.10.2, que estaba obsoleto y notificó una vulnerabilidad de seguridad
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [2.4.8-beta1] Migración de TinyMCE 5 a Page Builder de TinyMCE 7
   * _Nota de corrección_: Se migró TinyMCE 5 a TinyMCE 7.3.0 para que fuera una versión compatible con Adobe Commerce; anteriormente el sistema utilizaba 5.10.2, que estaba obsoleto y notificó una vulnerabilidad de seguridad
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [2.4.8-beta1] TinyMCE 5 migración a TinyMCE 7 - Magento 2-infra - palabras prohibidas
   * _Nota de corrección_: Se migró TinyMCE 5 a TinyMCE 7.3.0 para que fuera una versión compatible con Adobe Commerce; anteriormente el sistema utilizaba 5.10.2, que estaba obsoleto y notificó una vulnerabilidad de seguridad
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Requiere la actualización de .js a la versión 2.3.7 más reciente (vulnerabilidad de seguridad CVE-2024-38999)
   * _Nota de corrección_: Se ha actualizado require.js a la versión más reciente 2.3.7. En la versión anterior, se notificó vulnerabilidad de seguridad
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b34c0a75>

## Problemas solucionados

Hemos corregido 253 problemas en el código principal de Magento Open Source 2.4.8. A continuación, se describe un subconjunto de los problemas corregidos que se incluyen en esta versión.

### API

* _AC-10042_: la API de REST /V1/transactions devuelve un error cuando parent_txn_id = txn_id
   * _Nota de corrección_: El sistema ahora administra correctamente las transacciones de concepto principal y secundario donde el ID de transacción principal es el mismo que el ID de transacción, lo que evita un bucle infinito al consultar el extremo de la API REST /V1/transactions. Anteriormente, este escenario resultaba en un error grave debido a que se superaba el tiempo máximo de ejecución.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] Problema de tipo en 2.4.7
   * _Nota de corrección_: el sistema ahora administra correctamente los valores enteros en la función GetCustomSelectedOptionAttributes al ejecutar una consulta GraphQL, lo que evita cualquier error relacionado con el tipo. Anteriormente, al iniciar una consulta GraphQL que usaba GetCustomSelectedOptionAttributes con un argumento entero se producía un error de tipo.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38662>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38663>
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

### Cuenta

* _AC-10782_: el formulario de dirección del cliente permite código aleatorio en los campos de nombre
   * _Nota de corrección_: el sistema ahora valida la entrada en los campos Nombre y Apellidos del formulario de dirección del cliente, lo que impide el uso de código aleatorio. Anteriormente, el sistema permitía el uso de código aleatorio en estos campos sin arrojar un error.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38331>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38345>
* _AC-10990_: se bloqueó la dirección de adición de mi cuenta al guardar
   * _Nota de corrección_: El sistema ahora guarda correctamente las direcciones de los clientes incluso cuando no se muestra el campo de región, lo que evita un bloqueo durante el proceso de guardado. Anteriormente, si se intentaba agregar o editar una dirección sin un campo de región mostrado, se producía un error de excepción.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38406>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38407>
* _AC-11919_: Administrador: Botones de acciones de página flotando a la izquierda en lugar de a la derecha
   * _Nota de corrección_: el sistema ahora alinea correctamente los botones de acción de página a la derecha del encabezado adhesivo en el panel de administración, lo que mejora la apariencia profesional. Anteriormente, estos botones flotaban incorrectamente en el lado izquierdo del encabezado adhesivo.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38701>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev:di:error de información en magento 2.4.7
   * _Nota de corrección_: El sistema ahora muestra correctamente los parámetros del constructor al ejecutar el comando dev:di:info, lo que evita que se produzcan errores. Anteriormente, al ejecutar este comando, se producía un error debido a una discrepancia de tipos en el argumento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38740>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: el cliente ha iniciado sesión pero muestra un error 404 en front-end.
   * _Nota de corrección_: la página del panel del cliente de la tienda ahora se carga según lo esperado cuando un cliente inicia sesión. Anteriormente, los clientes podían iniciar sesión, pero esta página mostraba un error 404. [GitHub-35838](https://github.com/magento/magento2/issues/35838)
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35838>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: no se puede guardar la información de atributos del cliente en la sección de administración Editar cliente;
   * _Nota de corrección_: El ID de tienda del cliente ahora se implementa correctamente por cada ámbito de sitio web para el formulario de edición de cliente de administrador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/488c1034>

### IU de administración

* _AC-11588_: la validación de datos es correcta y el botón Importar está presente durante Importar productos con el comportamiento Reemplazar
   * _Nota de corrección_: el sistema ahora valida correctamente los datos y oculta el botón &quot;Importar&quot; durante el proceso de importación del producto con el comportamiento &quot;Reemplazar&quot;, lo que evita cualquier reemplazo no deseado de los datos. Anteriormente, el sistema validaba los datos incorrectamente y mostraba el botón &quot;Importar&quot;, lo que producía posibles incoherencias en los datos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Error] El Magento 2.4.7 no permite las fotos de productos con la extensión de archivo de mayúsculas.
   * _Nota de corrección_: el sistema ahora acepta cargas de imágenes de productos con extensiones de archivo en mayúsculas, lo que garantiza un proceso de creación de productos sin problemas. Anteriormente, las cargas de imágenes con extensiones de archivo de mayúsculas se rechazaban, lo que obligaba a los usuarios a cambiar la extensión del archivo a minúsculas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38831>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-6975_: [Problema] Establecer el modo de indizador predeterminado en &#39;horario&#39;
   * _Nota de corrección_: todos los indizadores nuevos se encuentran de manera predeterminada en el modo **[!UICONTROL Update by Schedule]**.  Anteriormente, el modo predeterminado era **[!UICONTROL Update on Save]**. Los indexadores existentes no se ven afectados. [GitHub-36419](https://github.com/magento/magento2/issues/36419)
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36419>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0b410856>
* _AC-7700_: [Problema] Eliminar tablas de registro de cambios del indizador al cancelar la suscripción de mview
   * _Nota de corrección_: El sistema ahora elimina automáticamente las tablas de registro de cambios no utilizadas cuando se cambia un índice de &#39;actualizar según lo programado&#39; a &#39;actualizar al guardar&#39;, marcando el índice como no válido para garantizar que no se pierdan entradas. Anteriormente, cambiar un índice a &quot;actualizar al guardar&quot; dejaba tablas de registro de cambios no utilizadas en el sistema y marcaba todos los índices cambiados como &quot;válidos&quot;.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/29789>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:collect-phrases rompe la integridad de las traducciones
   * _Nota de corrección_: El comando `bin/magento i18n:collect-phrases -o` ahora recopila y agrega correctamente nuevas frases de archivos JavaScript y .phtml, lo que garantiza que las traducciones se reflejen con precisión en el archivo de traducción. Anteriormente, el sistema no incluía frases de traducción multilínea de archivos JavaScript ni frases de archivos .phtml en el archivo de traducción, lo que provocaba traducciones incompletas o incorrectas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: el apóstrofo del nombre de la vista de la tienda se ha reemplazado por &#39;
   * _Nota de corrección_: los filtros de vista de almacén de la cuadrícula ahora muestran correctamente apóstrofos
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38395>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: La carga de Favicon no puede validar los archivos .ico
   * _Nota de corrección_: el error de validación del archivo se ha actualizado a &quot;Error de validación del archivo. Compruebe la configuración de procesamiento de imágenes en la configuración de la tienda&quot;. Anteriormente, era simplemente &quot;Error de validación de archivo&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: La galería en PageBuilder está mostrando una miniatura de imagen antigua en lugar de una imagen recién cargada
   * _Nota de corrección_: vuelva a generar vistas previas de imágenes para las imágenes eliminadas y cargadas de nuevo con el mismo nombre a través de la galería de medios en el contenido del generador de páginas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_: al guardar el producto por un usuario administrador con un ámbito de función diferente, se sobrescribe o elimina la información de producto relacionada existente en el producto
   * _Nota de corrección_: anteriormente, antes de la corrección, los productos relacionados se restablecían y quedaban vacíos cuando el usuario administrador secundario hacía clic en el botón Guardar sin cambiar en el producto relacionado. Después de esta corrección, el usuario administrador secundario hace clic en el botón guardar y el producto no se restablece y se guarda correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: No se pueden exportar más de 200 pedidos
   * _Nota de corrección_: Los límites del servidor para el tamaño de solicitud de los identificadores seleccionados enviados anteriormente se han descuidado al alterar la solicitud HTTP de GET a POST para solucionar el problema. Anteriormente, debido a las limitaciones del servidor para el tamaño de la solicitud de GET, se encontraba el problema.
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

### IU de administración, rendimiento

* _ACP2E-3169_: Después de la actualización a 2.4.5-p8 se producen 500 errores al crear el pedido del administrador
   * _Nota de corrección_: Anteriormente, al habilitar la minificación de HTML, no se podía realizar un pedido del administrador. Ahora, con la minificación de HTML habilitada, el pedido del administrador se puede realizar correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>

### IU de administración, envío

* _ACP2E-2519_: El recuento de código de cupón no se actualiza en   Columna &quot;Tiempo utilizado&quot; en la pestaña Administrar códigos de cupón si se realiza un pedido con varios envíos.
   * _Nota de corrección_: anteriormente, cuando se realizaba un pedido con varios envíos, el recuento de código de cupón no se actualizaba en la columna &quot;Tiempo utilizado&quot; de la ficha Administrar códigos de cupón. Ahora, el recuento correcto se muestra tanto en el &quot;Tiempo utilizado&quot;, que refleja los valores deseados con envío múltiple.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/4745100c>

### Análisis / Informes

* _ACP2E-2570_: El informe avanzado no funciona
   * _Nota de corrección_: el sistema ahora admite la generación de archivos de datos de informes avanzados para conjuntos de datos extra grandes cargando y escribiendo informes en lotes de 10 000. Anteriormente, el módulo de informes avanzados no podía generar archivos de datos para conjuntos de datos extragrandes, lo que provocaba errores &quot;MySQL server has gone away&quot; durante la ejecución del trabajo cron analytics_collect_data.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Problema de visibilidad del intervalo de fechas de los productos ordenados por el administrador.
   * _Nota de corrección_: el usuario podrá seleccionar cualquier fecha del informe de productos solicitados. Anteriormente, después de actualizar la tabla, al seleccionar la fecha &quot;DESDE&quot; se restablecía la fecha &quot;HASTA&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Encabezados curl incorrectos que hacen que newrelic:create:deploy-marker no funcione
   * _Nota de corrección_: El sistema ahora da formato correctamente a los encabezados curl, lo que permite que el comando newrelic:create:deploy-marker cree correctamente un marcador de implementación en New Relic. Anteriormente, unos encabezados curl incorrectos impedían la creación de un marcador de implementación en New Relic.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37641>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Análisis / Informes, B2B

* _ACP2E-2300_: B2B - el mapa del sitio incluye productos/categorías no asignados a un catálogo compartido
   * _Nota de corrección_: Restrinja las categorías y productos generados por el mapa del sitio a las categorías y productos asignados únicamente al catálogo compartido público y/o a la configuración de permisos de categoría del catálogo.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analytics / Creación de informes, Cloud

* _ACP2E-3067_: el Magento descarta la mayoría de las transacciones cron de New Relic #34108
   * _Nota de corrección_: AC informa correctamente de las transacciones relacionadas con trabajos cron a NewRelic. Anteriormente, algunas transacciones relacionadas con trabajos de cron se mostraban como &quot;OtherTransaction/Action/unknown&quot; en NR
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_: Bordes innecesarios en la sección Mis pedidos
   * _Nota de corrección_: Anteriormente se creaba un contenedor adicional (referencias de pedidos) que aplicaba clases CSS adicionales, lo que provocaba que aparecieran líneas de borde innecesarias debajo del número de pedido dentro de la sección Mis pedidos, que ahora no está visible.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, marco

* _AC-9607_: Filtrar la cuadrícula de la empresa y luego intentar exportar el CSV de la cuadrícula fallará y generará una excepción
   * _Nota de corrección_: el sistema ahora permite exportar correctamente a CSV los datos de la cuadrícula Compañías en el panel de administración, incluso cuando se aplican filtros como &quot;Saldo pendiente&quot; y &quot;Tipo de compañía&quot;. Anteriormente, si se aplicaban ciertos filtros y se intentaba exportar los datos de la cuadrícula, se producía un error y se producía una excepción.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _PAQUETE-3367_: Paga a través de LPM
   * _Nota de corrección_: El sistema ahora procesa correctamente los Métodos de pago locales (LPM) en la carga inicial, incluso cuando las direcciones de envío y facturación de un cliente que inició sesión no coinciden, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, una discrepancia entre las direcciones de envío y facturación de un cliente impedía que LPM se representara, lo que causaba posibles interrupciones durante el cierre de compra.
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PAQUETE-3368_: configurable con producto virtual como secundario
   * _Nota de corrección_: El sistema ahora permite métodos de pago exprés para productos configurables que tienen un producto secundario virtual, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, los métodos de pago exprés no estaban disponibles cuando se agregaba al carro de compras un producto configurable con un producto secundario virtual.
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PAQUETE-3369_: Error de comprobación de CSV
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PAQUETE-3370_: problemas en el área de la cuenta para el almacenamiento en bóveda 247
   * _Nota de corrección_: el sistema ahora permite a los clientes guardar información de nuevas tarjetas o cuentas de PayPal en varios sitios web sin encontrar errores de autorización. Anteriormente, los clientes no podían guardar nuevos métodos de pago en diferentes sitios web y se les presentaba un mensaje de error de autorización.
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PAQUETE-3371_: Enviar a una dirección de un país diferente
   * _Nota de corrección_: el sistema ahora permite que las transacciones se procesen sin errores al realizar envíos a una dirección de un país diferente, lo que garantiza un proceso de cierre de compra sin problemas. Anteriormente, intentar enviar a una dirección de un país diferente resultaba en errores de consola, a pesar de que no había errores visibles en el front-end.
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PAQUETE-3372_: Tarjeta de crédito - Función de desmontaje
   * _Nota de corrección_: El sistema ahora gestiona correctamente el desmontaje de los componentes de PayPal del Braintree cuando un cliente vuelve de la página de pago a la página de envío, lo que evita cualquier error y garantiza que los botones de PayPal Express se muestren correctamente. Anteriormente, al volver a la página de envío desde la página de pago, a veces se producía un error al intentar desmontar los componentes de PayPal del Braintree.
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>
* _PAQUETE-3373_: devolución de llamada de envío para PayPal Express
   * _Nota de corrección_: el sistema ahora muestra correctamente los métodos de envío disponibles en el modal PayPal Express, lo que permite a los clientes seleccionar el método de envío preferido antes de pasar a la página de revisión o completar su transacción. Anteriormente, no había métodos de envío disponibles para seleccionar en el modal PayPal Express, lo que requería que los clientes seleccionaran un método de envío en una página de revisión independiente antes de poder completar su transacción.
   * _Contribución de código de GitHub_: <https://github.com/magento/ext-braintree/pull/204>

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
* _AC-11876_: [Problema] Regresión de reglas de ventas en 2.4.7
   * _Nota de corrección_: El sistema ahora valida correctamente las reglas de ventas, lo que impide la aplicación de un código de cupón a un carro de compras cuando la condición del producto no coincide con ningún nombre de producto. Anteriormente, se podía aplicar una regla de ventas y aplicar un descuento en el importe de envío incluso cuando la condición del producto no coincidía con ningún nombre de producto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38671>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11993_: [Problema] El cargador bloquea los métodos de envío después de que se cambie el código postal y las reglas de validación de tarifas de envío
   * _Nota de corrección_: el sistema ahora administra correctamente los métodos de envío personalizados sin reglas de validación de tarifas de envío, lo que garantiza que el cargador no bloquee los métodos de envío después de que se cambie el código postal en la dirección de envío durante el cierre de compra. Anteriormente, si se cambiaba el código postal en la dirección de envío durante la desprotección, el cargador bloqueaba los métodos de envío y no desaparecía cuando se utilizaban métodos de envío personalizados sin reglas de validación de tarifas de envío.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38742>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: La característica de código de cupón no funciona correctamente en la página de pago del Magento 2.4.7
   * _Nota de corrección_: el sistema ahora habilita el campo de entrada de código de descuento/cupón en la página de cierre de compra para productos virtuales y descargables, lo que permite a los usuarios aplicar códigos de descuento según lo esperado. Anteriormente, la entrada del código/cupón de descuento estaba desactivada y el texto del título del botón se mostraba como &quot;Cancelar cupón&quot;, lo que impedía a los usuarios aplicar códigos de descuento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38826>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/1bafc571>
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
* _ACP2E-2704_: No se puede enviar la cookie. Tamaño de los &quot;mensajes de imagen&quot; al intentar reordenar
   * _Nota de corrección_: el proceso de reordenación no generará sus propios errores en este momento. Se basará en las comprobaciones de artículos integrados del anuncio del carro de compras.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: La dirección de envío predeterminada no está seleccionada al cerrar la compra
   * _Nota de corrección_: la dirección de envío predeterminada se está seleccionando ahora como evento en el contexto de la búsqueda de direcciones habilitada.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [NUBE] problema de API addProductsToCart de graphql con opción personalizada
   * _Nota de corrección_: GraphQL agrega al carro de compras correctamente el mismo producto con diferentes opciones personalizadas
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Se agregaron varias direcciones a la cuenta al cerrar la compra como cliente nuevo
   * _Nota de corrección_: El sistema guarda ahora una nueva dirección de cliente solo una vez si no se ha podido crear el pedido, lo que impide la creación de varias direcciones idénticas en caso de errores de colocación del pedido. Anteriormente, el sistema guardaba una nueva dirección cada vez que se realizaba un intento de realización de un pedido, independientemente de si el pedido se había creado correctamente o no.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Reordenar el pedido del cliente a través del formulario de pedido de invitado genera un carro vacío
   * _Nota de corrección_: Anteriormente, al realizar un repedido a través de la página Pedidos y devoluciones, se redirigía al cliente a la página de inicio de sesión. Después de aplicar esta corrección, el cliente registrado se redirige correctamente a la página Ver carro de compras al realizar un repedido. El flujo funciona igual que como los clientes invitados.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: el usuario administrador con recursos de rol limitados no puede ver los carros de compras
   * _Nota de corrección_: anteriormente, el administrador restringido no podía ver el carro de compras abandonado del panel de administración de un sitio web asociado. Después de aplicar esta corrección, el administrador restringido puede ver el carro de compras abandonado en el panel de administración.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>

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
* _AC-12076_: [Problema] Se corrigió la redacción del elemento de filtro en la navegación con capas
   * _Nota de corrección_: el sistema ahora utiliza correctamente las palabras &quot;item&quot; y &quot;items&quot; en el elemento de filtro de navegación por capas, lo que mejora la claridad y precisión de las descripciones de los filtros. Anteriormente, estas palabras se utilizaban incorrectamente, lo que producía una posible confusión para los usuarios que navegaban por las opciones de filtro.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38789>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: el formato de fecha y hora de la opción personalizada no funciona
   * _Nota de corrección_: el sistema ahora aplica correctamente el formato de fecha configurado a las opciones personalizadas del producto de tipo Fecha, asegurándose de que el formato de fecha se muestre correctamente en el front-end. Anteriormente, los cambios en la configuración del formato de fecha no se reflejaban en el front-end para las opciones personalizadas de producto de tipo Fecha.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32990>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38925>
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
   * SOAP _Nota de corrección_: Actualice correctamente default_sort_by en una categoría mediante una solicitud REST/API de
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Nube] El comerciante enfrenta problemas con el recuento de listas de deseos
   * _Nota de corrección_: al agregar un producto a la lista de deseos en una tienda, ya no se incrementa el recuento de listas de deseos en otras tiendas abiertas en el mismo explorador. Anteriormente, si ambas tiendas se cargaban en el mismo explorador, el recuento de listas de deseos también aumentaba en la otra tienda.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: La página Categoría en el front-end muestra espacios vacíos al usar el producto del paquete
   * _Nota de corrección_: los productos del paquete que no se pueden vender en el contexto actual de la tienda ya no se indizan.
   * _Contribución de código de GitHub_: <https://github.com/magento/inventory/commit/bc37ec76>
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
* _ACP2E-3100_: El archivo de imagen [Cloud] no existe en el registro de errores de New Relic
   * _Nota de corrección_: El sistema ahora sincroniza las imágenes de marcador de posición personalizadas con el almacenamiento local, asegurándose de que se representen correctamente al utilizar el almacenamiento remoto como AWS S3. Anteriormente, las imágenes de marcador de posición personalizadas no se representaban al utilizar el almacenamiento remoto, lo que provocaba una visualización de imágenes rotas y registros de errores.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: La respuesta de GQL de la Galería multimedia de productos de [Cloud] no está ordenada por la posición de la imagen
   * _Nota de corrección_: El sistema ahora ordena correctamente los elementos de la galería de medios por su posición en la respuesta de GraphQL, lo que garantiza un orden de visualización preciso. Anteriormente, los elementos de la galería de medios no se ordenaban por posición, lo que provocaba un orden de visualización incorrecto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37671>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [Los elementos de subcategoría de la nube] no se muestran en la edición de widgets en el servidor de administración
   * _Nota de corrección_: el árbol de categorías de la nueva página del widget ya no debería tener problemas para cargar categorías de nivel 5+. Anteriormente, faltaban algunas categorías al cargar las tres últimas categorías de Nivel 5.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>

### Catálogo, marco

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

### Catálogo, precios, ensayo y previsualización

* _ACP2E-2672_: [La nube] El punto final de la API de precio especial devuelve un error al actualizar grandes cantidades de productos simultáneamente
   * _Nota de corrección_: Ahora la API de actualización masiva de precios especiales creará una sola campaña para cada intervalo de fechas en lugar de varias actualizaciones programadas para cada producto e intervalo de fechas. Además, admitirá solicitudes de API simultáneas para un procesamiento más rápido de un gran número de SKU.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/f89a447e>

### Catálogo, Producto

* _AC-7050_: el árbol de selección de categorías en el producto de edición no está en el mismo orden establecido en Catálogo->Categorías
   * _Nota de corrección_: el sistema ahora muestra correctamente el árbol de selección de categorías en la sección de edición de productos en el mismo orden establecido en Catálogo->Categorías, lo que facilita la administración de productos en catálogos grandes. Anteriormente, el árbol de categorías de la sección de edición de productos se mostraba en el orden de creación de categorías, independientemente del orden de visualización establecido en Catálogo->Categorías.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36101>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36104>

### Catálogo, Buscar

* _ACP2E-2757_: los productos que no se muestran en la categoría y la búsqueda, pero los vínculos directos, funcionan
   * _Nota de corrección_: Anteriormente, el atributo personalizado Sí/No con price_* attribute_code no funciona con la indización. Después de esta corrección, el atributo personalizado Sí/No funciona según lo esperado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [Nube] Error de búsqueda elástico en ciertas páginas de la categoría
   * _Nota de corrección_: Anteriormente, con el vale de configuración mencionado, cuando ponemos el precio 0 para varios productos, se producirá una excepción en la página de categoría de front-end. Después de esta corrección se aplica cuando se carga múltiples precios de producto 0 y cargamos la página de categoría en front-end, no se producirá ninguna excepción y se cargará la página de categoría correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8931218>

### Nube

* _ACP2E-3010_: [Cloud] PHPSESSID está cambiando cada solicitud de POST
   * _Nota de corrección_: PHPSESSID ya no se regenera en solicitudes de POST en el área de front-end para un cliente que ha iniciado sesión si la caché de L2 Redis está habilitada y el cliente se actualizó desde el back-end
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>

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
* _AC-9638_: [Problema] de carga de archivos en el editor de WYSIWYG en la página del producto
   * _Nota de corrección_: el sistema ahora muestra correctamente el árbol de carpetas y permite las cargas de imágenes en el editor de WYSIWYG en la página del producto, incluso después de expandir primero la pestaña &quot;Imagen y vídeos&quot;. Anteriormente, al expandir la pestaña &quot;Imagen y vídeos&quot; por primera vez, el árbol de carpetas no se mostraba y aparecía un mensaje de error al intentar cargar una imagen en el editor de WYSIWYG.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38026>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [On-PREM] Problema de bloque dinámico
   * _Nota de corrección_: los widgets se están representando correctamente en bloques dinámicos.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a12063bd>
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
* _ACP2E-3127_: imagecreatetruecolor(): El argumento #2 ($height) debe ser mayor que 0. No se puede cargar una imagen específica
   * _Nota de corrección_: se ha resuelto el problema que provocaba errores en el administrador al cargar imágenes con una altura de 0 a través de la galería de medios y se ha realizado correctamente la sincronización de recursos mediante el comando sync. Anteriormente, no se puede cargar la imagen a través de la galería de medios y el comando de sincronización también falla cuando una imagen específica está en la galería.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from está en conflicto con la API de Google Maps
   * _Nota de corrección_: Google Maps ahora se procesa correctamente en el editor de PageBuilder. Anteriormente, un error de JavaScript impedía que Google Maps se representara correctamente.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/148c3ead>

### Cliente/ Clientes

* _AC-12162_: front-end: la validación de la fecha de nacimiento está fallando en la página de creación del cliente
   * _Nota de corrección_: Asegúrese de que toda la validación funcione después de actualizar la dependencia del sistema moment.js a la última versión secundaria
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Marco

* _AC-10654_: pregunta/problema de extremo V1/customers/password
   * _Nota de corrección_: El sistema ahora se adhiere a las restricciones establecidas dentro de la GUI de administración al procesar solicitudes de cambio de contraseña a través de la API, lo que evita posibles abusos de la función de restablecimiento de contraseña. Anteriormente, la API podía procesar solicitudes de cambio de contraseña fuera de las reglas definidas en la GUI de administración, lo que permitía un flujo constante de correos electrónicos restablecidos si se conocían correos electrónicos válidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38238>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _Nota de corrección_: Actualice las dependencias del Compositor de sistemas de archivo/liga actualizando a la versión más reciente
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _Contribución de código de GitHub_: actualice las dependencias del Compositor de sistemas de archivos/liga 2.x a la última versión 3.x.
* _AC-10838_: proceso de indexación de error del índice de búsqueda del catálogo
   * _Nota de corrección_: El sistema ahora completa correctamente el comando de reindexación sin encontrar ningún error, independientemente de la versión de libxml compilada con PHP. Anteriormente, la ejecución del comando re-index resultaba en un error &quot;Error del proceso de índice de búsqueda en el catálogo durante el proceso de indexación&quot; cuando PHP se compilaba con ciertas versiones de libxml.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38254>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _AC-10941_: se agregaron los filtros created_at, status y grand_total a la consulta de pedidos de clientes y se corrigió un error de varios filtros
   * _Nota de corrección_: el sistema ahora admite el uso de los filtros created_at, status y grand_total en las consultas de pedidos de clientes y ha resuelto un problema en el cual no se aplicaban correctamente varios filtros. Anteriormente, el sistema no admitía estos filtros y no podía aplicar todos los filtros cuando se utilizaba más de uno en una consulta.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38392>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36949>
* _AC-10971_: https://github.com/magento/magento2/issues/38415
   * _Nota de corrección_: PHP 8.2/8.3, solo una dependencia falla en el filtro php en este momento: league/flysystem
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribución de código de GitHub_: El sistema ahora es compatible con PHP 8.2/8.3 al actualizar el paquete league/flysystem a la versión 3.0.20, lo que garantiza que no se produzcan errores de identificación de PHP. Anteriormente, ejecutar archivos PHP a través del linter PHP con PHP 8.3 resultaba en errores de linting en el paquete league/flysystem.
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
* _AC-11651_: el Magento está intentando modificar la propiedad de solo lectura en __ método de reactivación de LoggerProxy
   * _Nota de corrección_: El sistema ahora permite la modificación de propiedades de sólo lectura anteriores en el método __wakeup de LoggerProxy, lo que garantiza un funcionamiento sin problemas sin forzar a los usuarios a emplear una solución. Anteriormente, un intento de reasignar el valor de una propiedad de solo lectura en el método __wakeup de LoggerProxy causaba problemas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38526>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _Nota de corrección_: Investigue las últimas versiones de php-amqplib/php-amqplib
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribución de código de GitHub_: Se ha actualizado la versión más reciente php-amqplib/php-amqplib :^3.x
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
* _AC-11808_:
   * _Nota de corrección_: Investigue y actualice la lista de dependencias principales de Adobe Commerce
   * _Contribución de código de GitHub_: Se necesita actualizar la lista de dependencias principales de Adobe Commerce 
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
* _AC-11905_: [Problema] Implementación de contenido estático: error de tipo
   * _Nota de corrección_: el sistema ahora gestiona correctamente los archivos LESS vacíos durante la implementación de contenido estático y muestra el mensaje de error &quot;El archivo LESS está vacío&quot;. Anteriormente, se producía un error de tipo incorrecto al encontrar un archivo LESS vacío durante la implementación.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38682>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _Nota de corrección_: limpieza de css de jQuery/fileuploader después de la migración a la biblioteca de carga
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribución de código de GitHub_: se eliminó la biblioteca jQuery/fileUploader porque se migró a la biblioteca de carga
* _AC-12002_: [Problema] [Vista] eliminó espacio adicional en el vínculo y la etiqueta de script
   * _Nota de corrección_: El sistema ahora garantiza que no haya espacios adicionales en las etiquetas de vínculo y script, lo que proporciona un código más limpio y eficiente. Anteriormente, se podían encontrar espacios dobles entre atributos en las etiquetas de vínculo y script.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/32920>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _Nota de corrección_: Limpieza de la carpeta ExtJs después de la migración a la biblioteca jsTree
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _Contribución de código de GitHub_: se eliminó la carpeta extJs porque la funcionalidad relacionada se migró a jsTree
* _AC-12022_:
   * _Nota de corrección_: actualice la dependencia del sistema monólogo/monólogo a la última versión principal
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribución de código de GitHub_: el sistema se ha actualizado para utilizar la última versión principal de la biblioteca &quot;monólogo/monólogo:^3.x&quot;, lo que garantiza la compatibilidad y mejora el rendimiento. Anteriormente, el sistema utilizaba una versión obsoleta de la biblioteca &quot;monólogo/monólogo&quot; que podría haber provocado posibles problemas y limitaciones.
* _AC-12023_:
   * _Nota de corrección_: Actualice la dependencia de wikimedia/less.php a la última versión principal
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribución de código de GitHub_: El sistema se ha actualizado para utilizar la última versión principal 5.x de la biblioteca &quot;wikimedia/less.php&quot;, lo que garantiza la compatibilidad y la funcionalidad actualizada. Anteriormente, el sistema utilizaba una versión obsoleta de la biblioteca que podría haber provocado problemas de seguridad.
* _AC-12024_:
   * _Nota de corrección_: Actualice la dependencia de biblioteca jquery/validate a la última versión secundaria
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribución de código de GitHub_: actualice la dependencia de biblioteca jquery/validate a la última versión menor 1.20.0
* _AC-12025_:
   * _Nota de corrección_: Actualice la dependencia del sistema moment.js a la última versión secundaria
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _Contribución de código de GitHub_: actualice la dependencia del sistema moment.js a la última versión secundaria 2.30.1.
* _AC-12267_:
   * _Nota de corrección_: admite reintentos de conexión para la sesión de Redis y compatible con colinmollenhour/php-redis-session-abstract v2.0.0
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _Contribución de código de GitHub_: Se ha actualizado la última versión de colinmollenhour/php-redis-session-abstract v2.0.0 compatible con adobe commerce
* _AC-12268_:
   * _Nota de corrección_: actualice las dependencias del Compositor de sistemas de archivos/liga a la versión más reciente.
   * _Contribución de código de GitHub_: actualice las dependencias del Compositor de sistemas de archivos/liga 2.x a la última versión 3.x.
* _AC-12594_: [Problema] Use la configuración compilada para los datos generados en lugar de la configuración general
   * _Nota de corrección_: El sistema utiliza ahora la configuración compilada para los datos generados en lugar de la configuración general, lo que reduce la transferencia de red y la sobrecarga de datos que dependen de una determinada versión de código. Este cambio evita la anulación de caché en instancias compartidas durante el intercambio de contenedores, lo que conduce a una mejor estabilidad y a una reducción del tiempo de inactividad. Anteriormente, ciertas clases principales utilizaban el tipo de configuración compartida, que podía provocar la anulación de la caché o el tiempo de inactividad de la aplicación debido a diferencias en las versiones de código en varios servidores.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38785>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Problema] Elimina las referencias a los archivos de extjs que se eliminaron en e1ccdb...
   * _Nota de corrección_: el sistema ahora quita las referencias a archivos de extjs que se quitaron anteriormente, lo que elimina los errores en la consola del explorador y en el archivo de registro del sistema. Anteriormente, estas referencias causaban errores debido a la ausencia de los archivos a los que se hace referencia.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38960>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _Nota de corrección_: actualice las dependencias del compositor de láminas a la versión más reciente
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contribución de código de GitHub_: El sistema ahora admite las versiones más recientes de las dependencias del compositor de láminas:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validador
garantizar la compatibilidad y la funcionalidad actualizada. Anteriormente, la actualización a las versiones más recientes de estas dependencias podría provocar problemas de incompatibilidad con versiones anteriores y errores de prueba.
* _AC-12778_: [Problema] Limpieza menor: se corrigió el uso incorrecto de sprintf, solo se necesitan 2 marcadores de posición aquí y w...
   * _Nota de corrección_: el sistema ahora utiliza correctamente la función sprintf con el número adecuado de marcadores de posición, lo que mejora la limpieza y coherencia del código. Anteriormente, la función sprintf se utilizaba incorrectamente con un argumento adicional, que no causaba ningún problema importante, pero no era el uso correcto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39062>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38628>
* _AC-12866_:
   * _Nota de corrección_: Eliminar obsolescencias - Pruebas de integración de PhpUnit10
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribución de código de GitHub_: resuelva los casos de obsolescencia de PHPUnit
* _AC-12868_:
   * _Nota de corrección_: Eliminar obsolescencias - Pruebas de WebApi de PhpUnit10
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _Contribución de código de GitHub_: resuelva los casos de obsolescencia de PHPUnit
* _AC-12869_: [Problema] Corrige las clases incorrectas a las que se hace referencia en los módulos de Magento.
   * _Nota de corrección_: El sistema ahora hace referencia correctamente a las clases en módulos, lo que garantiza un funcionamiento más suave y evita bloqueos debido a clases no existentes. Esto incluye una corrección de errores en los módulos Indexer y CreditMemo, y la implementación de HttpGetActionInterface en la clase PrintAction. Anteriormente, las referencias de clase incorrectas provocaban errores y posibles bloqueos del sistema, y algunas funcionalidades, como el nombre de archivo de los archivos del PDF creditmemo y la reindexación de existencias, no funcionaban según lo esperado.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/39126>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37784>
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
* _AC-8984_: [Problema] Agrega más colores a la salida de ciertos comandos cli de instalación
   * _Nota de corrección_: El sistema ahora agrega más colores a la salida de ciertos comandos de la interfaz de línea de comandos (CLI) de configuración, lo que mejora la legibilidad y la experiencia del usuario. Anteriormente, el resultado de estos comandos era más difícil de leer debido a la falta de diferenciación de color.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/29335>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: al actualizar el Magento, se restablece general/region/state_required cuando se agrega un nuevo país con el estado o la región requeridos.
   * _Nota de corrección_: El sistema ahora solo agrega el país modificado a la configuración &#39;general/region/state_required&#39; cuando se agrega un nuevo país con estados requeridos, lo que evita cualquier interrupción en el código personalizado que supone que la región está deshabilitada. Anteriormente, si se agregaba un nuevo país con estados requeridos, se restablecía la configuración &quot;general/region/state_required&quot; a los países predeterminados con un estado requerido, lo que podría romper la tienda.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37796>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: https://github.com/magento/magento2/issues/37841
   * _Nota de corrección_: Diferencia en menos compilación entre php y nodejs library (grunt) con expresiones `calc` complicadas
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _Contribución de código de GitHub_: Corrija la diferencia en menos compilación entre php y nodejs library (grunt) después de actualizar wikimedia/less.php:^5.x
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

### Marco de trabajo, GraphQL

* _AC-7976_: [Problema] introdujo la compatibilidad con tipos escalares personalizados para el esquema de GraphQL
   * _Nota de corrección_: el sistema ahora admite tipos escalares personalizados para el esquema de GraphQL, lo que permite a los desarrolladores definir tipos escalares personalizados e implementaciones. Esta función puede resultar especialmente útil para expresar valores que pueden requerir validación, como HTML, correos electrónicos, URL, fechas, etc., y para casos más avanzados como atributos EAV. Anteriormente, el sistema no admitía el procesamiento de tipos escalares personalizados en GraphQL.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/36877>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

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
* _ACP2E-3253_: la paginación de elementos V2 del carro de compras de GraphQL no funciona correctamente
   * _Nota de corrección_: el problema se ha corregido pasando el valor correcto para el argumento de la página actual en la consulta de colección. Anteriormente, se pasaba un valor incorrecto para establecer la página actual, lo que provocaba el problema.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/8459b17d>

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

### Instalar y administrar

* _ACP2E-2102_: No hay exportación de VCL para el botón Barniz 7 en el panel de administración
   * _Nota de corrección_: Se agregó el botón &quot;Exportar VCL para Barniz 7&quot; al Panel de administración.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventario/MSI

* _AC-11593_: la clave de la API de Google de Google no funciona al agregar un mapa con atributos
   * _Nota de corrección_: el sistema ahora admite la última versión 3.56 de la API de Google Maps, lo que permite a los usuarios agregar correctamente un bloque de contenido de mapa del menú PageBuilder al escenario sin encontrar ningún error. Anteriormente, los usuarios no podían agregar un bloque de contenido de mapa debido a problemas de compatibilidad con la versión de la API de Google Maps, lo que provocaba un mensaje de error &quot;Se ha producido un error&quot;.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_: [Nube] problema crítico con la lista de productos con espacios vacíos
   * _Nota de corrección_: el sistema ahora muestra correctamente las listas de productos sin espacios vacíos cuando los productos están configurados en &#39;Agotado&#39;, lo que garantiza una presentación coherente y precisa de los productos disponibles. Anteriormente, si se establecía un producto en &quot;Agotado&quot;, aparecía un espacio vacío en la lista de productos, lo que afectaba al diseño y podía confundir a los clientes.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Pedido

* _AC-10828_: pantalla de información general del pedido back-end: la cantidad no satisfecha no es visible en el nivel de artículo de pedido
   * _Nota de corrección_: El sistema ahora muestra el número de artículos no pedidos en la columna de cantidad en la pantalla de información general del pedido back-end. Esto garantiza que los usuarios puedan realizar un seguimiento preciso del estado de todos los elementos de un pedido. Anteriormente, la columna de cantidad solo mostraba el número de artículos pedidos, facturados y enviados, pero no mostraba el número de artículos no pedidos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38252>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Problema] se usó un identificador de almacén incorrecto en el procesador de direcciones de pedidos
   * _Nota de corrección_: El sistema ahora utiliza correctamente el identificador de almacén asociado a un pedido al procesar la dirección del pedido, asegurándose de que las direcciones tengan el formato correcto de acuerdo con su respectivo identificador de almacén. Anteriormente, el sistema utilizaba incorrectamente el ID de tienda actual, lo que podía provocar un formato de dirección incorrecto en los casos en que era necesario enviar varios correos electrónicos de pedidos de diferentes tiendas.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38412>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37932>
* _AC-11798_: [Problema] Precio de envío que se muestra diferente en el PDF impreso
   * _Nota de corrección_: el sistema ahora muestra correctamente los precios de envío en los PDF impresos según la configuración de impuestos, lo que garantiza la coherencia entre la página de vista de facturas de pedidos de venta y la factura impresa. Anteriormente, el precio de envío mostrado en el PDF impreso excluía impuestos, independientemente de la configuración de impuestos.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38608>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
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

### Pedido, Devoluciones

* _ACP2E-2982_: El reembolso del pedido genera un abono duplicado
   * _Nota de corrección_: emitir el reembolso a través de la API de REST cuando se ejecutaron simultáneamente dos solicitudes idénticas dejará de crear notas de abono duplicadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/a4fbf702>

### Pedido, Impuesto

* _ACP2E-3003_: [NUBE] Base_row_total incorrecto en la API de pedido RESTFUL al habilitar transacciones internacionales y aplicar descuentos de cupones
   * _Nota de corrección_: Ahora se devuelve el total base_row_correcto desde la API de pedidos RESTFUL cuando se habilita la transacción internacional y se aplica el descuento de cupones.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/9af794a4>

### Otras herramientas para desarrolladores

* _AC-10658_: [Problema] Corrija el error de sintaxis del HTML en visual.phtml
   * _Nota de corrección_: El sistema cierra ahora correctamente la etiqueta de inicio en el archivo visual.phtml, lo que garantiza una sintaxis de HTML adecuada. Anteriormente, la etiqueta de inicio no se cerraba correctamente, lo que provocaba un error de sintaxis del HTML.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38247>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [Problema] cambió &quot;activo&quot; a &quot;habilitado&quot; en el comando bin/magento maintenance:status
   * _Nota de corrección_: El sistema ahora proporciona mensajes de estado más precisos para el comando de modo de mantenimiento, cambiando el estado de &quot;activo&quot; a &quot;habilitado&quot; y de &quot;no activo&quot; a &quot;deshabilitado&quot;. Anteriormente, el mensaje de estado del comando de modo de mantenimiento se mostraba como &quot;activo&quot; o &quot;no activo&quot;, lo que podía generar confusión.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38486>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: La navegación en el árbol de categorías genera errores en Redis: &quot;La sesión de Redis ha superado las conexiones simultáneas&quot;
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38851>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0611e750>

### Pagos

* _ACP2E-2841_: El flujo de trabajo crea una nueva transacción cada vez que hacemos clic en el botón de captura en la pantalla de visualización de transacción
   * _Nota de corrección_: El sistema ahora obtiene correctamente la información de transacción sin crear una nueva transacción de pago cada vez que se hace clic en el botón de recuperación en la pantalla Ver transacción. Anteriormente, hacer clic en el botón Recuperar creaba incorrectamente una nueva transacción de pago para un pedido que ya se había pagado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: No se muestra el mensaje de Paylater en PDP para la cuenta de PayPal Merchant de Canadá
   * _Nota de corrección_: el sistema ahora muestra correctamente el mensaje PayAfter para las cuentas de comerciante de PayPal canadiense en la página de detalles del producto (PDP) cuando se puede determinar el país del comprador a partir de la dirección de facturación o envío de la cuenta. Anteriormente, no se mostraba el mensaje Paylater debido a la falta de un parámetro, lo que daba como resultado un error en la consola del explorador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/6a185204>

### Rendimiento

* _AC-12000_: [Problema] Limpieza de código, adición de nuevo bloque de encabezado crítico y movimiento de css crítico antes de los recursos
   * _Nota de corrección_: el sistema ahora incluye un nuevo bloque de encabezado crítico y mueve CSS crítico antes que los recursos, lo que permite una mayor personalización y optimización del rendimiento en el front-end. Anteriormente, el CSS crítico no se colocaba antes de los recursos, lo que limitaba las oportunidades de personalización y optimización.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38748>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: La compilación del tema se interrumpe cuando el host mysql contiene información del puerto
   * _Nota de corrección_: El sistema ahora administra correctamente la configuración de host de MySQL que incluye información de puerto, lo que garantiza la compilación correcta del tema. Anteriormente, la compilación del tema fallaba si la configuración del host MySQL en la conexión de base de datos incluía información de puerto.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38799>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38842>
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

### Product

* _AC-10535_: los caracteres especiales del nombre de producto asociado configurable se están convirtiendo en entidades HTML.
   * _Nota de corrección_: El sistema ahora conserva correctamente caracteres especiales en los nombres de productos asociados al editar un producto configurable, lo que impide que se conviertan en entidades HTML. Anteriormente, los caracteres especiales de los nombres de producto asociados se convertían en entidades de HTML cuando se editaba el producto configurable.
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
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) debe ser de tipo int, se ha proporcionado una cadena
   * _Nota de corrección_: el sistema ahora almacena correctamente en déclencheur los correos electrónicos de alertas de productos asegurándose de que el identificador del almacén sea del tipo de datos correcto. Anteriormente, los correos electrónicos de alerta de producto no se enviaban debido a una discrepancia de tipos en el identificador de tienda.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/35602>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: La función [Cloud] addFilterToMap no funciona para ciertas columnas
   * _Nota de corrección_: Ahora, el módulo personalizado se puede usar en la cuadrícula de pedidos. Anteriormente, se producían errores al utilizar un módulo personalizado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/3a7c4d17>

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

### Seguridad

* _AC-11762_:
   * _Nota de corrección_: actualice el campo de ventana OTP de 2FA con la descripción correcta y el valor predeterminado después de cambiar BiC
   * _Contribución de código de GitHub_: Se ha actualizado el comando para ver cómo se entrará el período otp_window desde ahora bin/magento config:set twofactorauth/google/otp_window VALUE
a bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-11855_: [Problema] Falta Fuente CSP Emergente Más Tarde
   * _Nota de corrección_: El sistema ahora permite cargar la fuente &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; sin infringir la directiva de la directiva de la directiva de seguridad de contenido, lo que garantiza la correcta visualización de la ventana emergente de Paylater. Anteriormente, la fuente se rechazaba cargar debido a una infracción de la directiva de la política de seguridad de contenido, lo que causaba problemas de visualización con la ventana emergente de Paylater.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38624>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _Nota de corrección_: actualice el campo de ventana OTP de 2FA con la descripción correcta y el valor predeterminado después de cambiar BiC
   * _Contribución de código de GitHub_: Se ha actualizado el comando para ver cómo se entrará el período otp_window desde ahora bin/magento config:set twofactorauth/google/otp_window VALUE
a bin/magento config:set twofactorauth/google/leeway VALUE
* _AC-12309_:
   * _Nota de corrección_: actualice la documentación de usuario para la autenticación de doble factor (2FA) para cambiar el comando otp_window
   * _Contribución de código de GitHub_: Actualice la documentación del usuario para la autenticación de doble factor (2FA) para cambiar el comando de configuración OTP_WINDOW según: https://jira.corp.adobe.com/browse/AC-11762

### Envío

* _AC-10757_: [Problema] Se corrigió un error tipográfico en tracking.phtml - se cambió el nombre de las funciones JS &quot;currier&quot; a &quot;carrier&quot;
   * _Nota de corrección_: El sistema ahora utiliza correctamente el término &quot;carrier&quot; en lugar del mal escrito &quot;currier&quot; en las funciones de controlador de JavaScript utilizadas en la plantilla de seguimiento de pedidos, lo que garantiza una nomenclatura de funciones y una claridad de código adecuadas. Anteriormente, se utilizaba el término mal escrito &quot;currier&quot;, lo que producía una posible confusión e incoherencia en la base del código.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/34523>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _Nota de corrección_: UPS REST &quot;Un envío no puede tener una unidad de medida KGS/IN o LBS/CM u OZS/CM&quot;
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _Contribución de código de GitHub_: Las tasas de UPS son visibles en el cierre de compra y el carro de compras.
* _AC-11916_:
   * _Nota de corrección_: [QPT] UPS REST &quot;Un envío no puede tener una unidad de medida KGS/IN o LBS/CM u OZS/CM&quot;
   * _Contribución de código de GitHub_: Las tasas de UPS son visibles en el cierre de compra y el carro de compras.
* _AC-11938_: UPS REST &quot;Un envío no puede tener una unidad de medida KGS/IN o LBS/CM u OZS/CM&quot;
   * _Nota de corrección_: Asegúrese de que las tarifas de UPS sean visibles en el cierre de compra y el carro de compras.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38618>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _Nota de corrección_: [QPT] UPS REST &quot;Un envío no puede tener una unidad de medida KGS/IN o LBS/CM u OZS/CM&quot;
   * _Contribución de código de GitHub_: Las tasas de UPS son visibles en el cierre de compra y el carro de compras.
* _AC-11984_:
   * _Nota de corrección_: [QPT] UPS REST &quot;Un envío no puede tener una unidad de medida KGS/IN o LBS/CM u OZS/CM&quot;
   * _Contribución de código de GitHub_: Las tasas de UPS son visibles en el cierre de compra y el carro de compras.
* _ACP2E-2738_: La ventana de seguimiento muestra una fecha de entrega esperada incorrecta
   * _Nota de corrección_: muestra la fecha de entrega correcta para el operador de Fedex.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Se Siguen Mostrando Las Tarifas De Tabla Aunque Se Aplique El Envío Gratuito
   * _Nota de corrección_: el método de envío de tarifa de tabla ahora se muestra aunque el envío gratuito esté disponible después de aplicar el cupón
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: error de MFTF test AdminCreatingShippingLabelTest debido a credenciales no agregadas en el entorno Jenkins
   * _Nota de corrección_: corrección de la prueba mftf
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Segmentación

* _AC-9432_: [Problema] Permitir el uso de intervalos CIDR en la lista de permitidos de mantenimiento
   * _Nota de corrección_: el sistema ahora admite el uso de intervalos CIDR en la lista de IP permitidas del modo de mantenimiento, lo que permite que un intervalo de direcciones IP omita el modo de mantenimiento. Anteriormente, el modo de mantenimiento permitía que la lista de direcciones IP solo permitiera a direcciones IP individuales omitir el modo de mantenimiento.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37943>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/30699>

### Marco de prueba

* _AC-11491_:
   * _Nota de corrección_: [Omitir] debe anular la omisión de nuevo Prueba de integración
   * _Problema de GitHub_: &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _Contribución de código de GitHub_: anule la omisión de todas las pruebas de integración que se omitan en esta PR - https://github.com/magento-commerce/magento2ce/pull/8811/
* _AC-11654_: prueba de integración con error testDbSchemaUpToDate debido a un tipo de columna JSON
   * _Nota de corrección_: El sistema ahora reconoce correctamente los tipos de columnas JSON en el esquema de la base de datos durante las pruebas de integración, lo que evita errores de prueba debido a una discrepancia entre el esquema de la base de datos y el esquema declarativo. Anteriormente, el sistema identificaba incorrectamente los tipos de columnas JSON como LONGTEXT en MariaDB, lo que provocaba que las pruebas de integración fallaran.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/ef81f5a2>

### Marco de IU

* _AC-12128_: corrección de la vulnerabilidad de seguridad Prototype.js CVE-2020-27511
   * _Nota de corrección_: el sistema se ha actualizado para solucionar la vulnerabilidad de seguridad CVE-2020-27511 en Prototype.js 1.7.3, lo que mejora la seguridad general del sistema. Antes de esta actualización, el sistema era susceptible a una Denegación de servicio de expresión regular (ReDOS) mediante la eliminación de etiquetas de HTML creadas.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt Less usa pub/ prefix para los mapas de origen
   * _Nota de corrección_: El sistema ahora genera mapas de origen de less/css sin el prefijo /pub para las rutas al usar grunt, lo que elimina la necesidad de una solución alternativa en la configuración del servidor web. Anteriormente, el uso del prefijo /pub en las rutas de mapas de origen requería una configuración específica en el servidor web para funcionar correctamente.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/38837>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/38840>
* _AC-1306_: el contenido estático se está implementando para los módulos deshabilitados
   * _Nota de corrección_: el sistema ahora excluye CSS relacionado con módulos deshabilitados de los archivos de salida CSS finales, lo que garantiza que no se carguen estilos innecesarios. Anteriormente, el CSS relacionado con los módulos desactivados se incluía en los archivos de salida CSS finales, lo que provocaba la carga de estilos adicionales e innecesarios.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/24666>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [Problema] No cargar contexto de bloque de servidor en front-end
   * _Nota de corrección_: El sistema ahora garantiza que el contexto de bloque del servidor no se cargue en el front-end, lo que evita la creación de sesiones back-end innecesarias y posibles bloqueos de sesión. Anteriormente, el sistema cargaba incorrectamente el contexto de bloque back-end en el front-end, lo que provocaba la creación de sesiones back-end y posibles bloqueos de sesión.
   * _Problema de GitHub_: <https://github.com/magento/magento2/issues/37617>
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_: Excepción al comprobar el saldo de una tarjeta regalo cuando Recaptcha está habilitado
   * _Nota de corrección_: los usuarios podrán recuperar el saldo de la tarjeta regalo en la pantalla de vista y edición del carro de compras. Anteriormente, estos detalles no se mostraban cuando reCAPTCHA estaba habilitado.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ACLARACIÓN] Cumplimiento de ADA de solicitud de característica
   * _Nota de corrección_: El sistema ahora garantiza el cumplimiento de ADA eliminando las propiedades CSS no admitidas y reemplazándolas por otras admitidas en el archivo print.css. Anteriormente, el uso de propiedades CSS no admitidas producía problemas de compatibilidad con el explorador.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [Nube] Código de biblioteca de confusión en effect-drop.js de AC 2.4.4-p8
   * _Nota de corrección_: El sistema ahora implementa correctamente la biblioteca effect-drop.js, lo que garantiza el funcionamiento adecuado de los efectos de la interfaz de usuario de jQuery. Anteriormente, la biblioteca effect-drop.js se sobrescribía por error con la biblioteca effect-clip.js, lo que causaba posibles problemas con los efectos de la interfaz de usuario de jQuery.
   * _Contribución de código de GitHub_: <https://github.com/magento/magento2/commit/35b1b1da>
