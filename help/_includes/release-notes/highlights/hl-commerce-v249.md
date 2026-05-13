---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Elementos destacados de Adobe Commerce (v2.4.9)

## Aspectos destacados en la versión 2.4.9

En la versión de Adobe Commerce 2.4.9 se aplican los siguientes aspectos destacados.

### Cambios de API de REST

#### Control de herencia de la galería de productos API REST en el nivel de vista de tienda

La actualización de un producto mediante la API de REST en un ámbito de almacén ya no hace que las imágenes y los vídeos de productos hereden los cambios del ámbito global cuando `media_gallery_entries` se omite en la carga útil o se establece en `NULL`. Ahora también es posible restaurar la herencia de ámbito para imágenes y vídeos de productos mediante la API de REST estableciendo el campo correspondiente en `NULL`.

Al actualizar productos mediante la API de REST en el nivel de vista de tienda:

- Omitir `media_gallery_entries` o establecerlo en NULL ahora conservará la herencia de la galería predeterminada/global.
- Para restaurar la herencia para atributos específicos de la galería (como `label`, `position`, `disabled`, `video_title`, `video_description`), establezca esos campos en NULL dentro de la matriz `media_gallery_entries`.

Este cambio garantiza que las vistas de la tienda puedan mantener o restaurar fácilmente los valores predeterminados de la galería, reduciendo la confusión y haciendo que la administración de la galería sea más coherente.

_ACP2E-4358 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Cambios en la API de GraphQL

#### La mutación de GraphQL `clearCart` ya está disponible en Magento Open Source

La mutación de GraphQL [clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) ya está disponible para todos los usuarios de Magento Open Source. Anteriormente, solo se podía acceder a esta mutación en Adobe Commerce.

_AC-16683 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### Errores más descriptivos de la mutación de GraphQL `applyGiftCardToCart`

Tratamiento de errores mejorado para la mutación `applyGiftCardToCart`. La mutación ahora devuelve mensajes de error específicos para casos como tarjetas regalo caducadas o de saldo cero, lo que mejora la experiencia del comprador. Además, el servidor evita la aplicación de tarjetas de regalo adicionales a pedidos que ya son gratuitos.

_LYNX-787_

#### La nueva mutación de GraphQL `clearWishlist` elimina todos los elementos de la lista de deseos a la vez

Se agregó una mutación `clearWishlist` que elimina todos los elementos de una lista de deseos en una sola llamada.

_LYNX-790_

#### Nueva mutación de GraphQL `exchangeExternalCustomerToken` para la autenticación basada en la integración

Se ha introducido una nueva mutación de GraphQL `exchangeExternalCustomerToken` que autentica a los usuarios mediante un token de integración y devuelve tanto el token del cliente como los datos de clientes asociados.

_LYNX-815_


#### Las nuevas consultas de GraphQL devuelven grupos de clientes, segmentos e ID de reglas del carro de compras aplicados

Las nuevas consultas de GraphQL devuelven el `uid` codificado del grupo de clientes, los segmentos de clientes y las reglas del carro de compras aplicados.

_LYNX-867_

#### Las opciones de regalo se borran automáticamente cuando se vacía el carro de compras

Se ha corregido un problema por el cual las opciones de regalo persistían en un carro de compras vacío después de eliminar todos los elementos. Las opciones de regalo ahora se borran automáticamente cuando se vacía el carro de compras, coincidiendo con el comportamiento existente para los cupones.

_LYNX-786_

#### Las opciones de regalo se fusionan de manera consistente cuando se combinan los carros de compras para invitados y clientes

Administración mejorada de las opciones de regalo durante las combinaciones del carro de compras para garantizar una experiencia de usuario más coherente. Las opciones de regalo ahora siguen una lógica de combinación priorizada, que evita invalidaciones no deseadas cuando un usuario invitado inicia sesión y su carro de compras se combina con un carro de compras de clientes existente.

_LYNX-788_

#### Nuevo campo `grand_total_excl_tax` en la respuesta de GraphQL `OrderTotal`

Se ha agregado un nuevo campo, `OrderTotal.grand_total_excl_tax`, a la respuesta de pedido de GraphQL. Este campo proporciona el total general excluido de impuestos del pedido, lo que facilita el acceso a los totales exclusivos de impuestos directamente desde la API.

Ventajas:

- Recupere fácilmente el total general sin impuestos para cualquier pedido a través de GraphQL.
- Simplifica la integración con sistemas externos que requieren totales exclusivos de impuestos.
- Reduce la necesidad de realizar cálculos personalizados en el lado del cliente.

_LYNX-892_

#### Los pedidos históricos muestran detalles de los productos que ya no están disponibles

Los pedidos históricos ahora muestran detalles completos del producto para los artículos de línea incluso después de que el producto se haya agotado, de modo que los clientes y comerciantes conservan un registro completo de lo que se compró.

_LYNX-913_

#### Se agregó la validación de reCAPTCHA a las mutaciones de GraphQL `updateCustomer`, `updateCustomerV2` y `contactUs`

Cuando reCAPTCHA está habilitado para los formularios de tienda correspondientes, las mutaciones de GraphQL `updateCustomer`, `updateCustomerV2` y `contactUs` ahora aplican la misma validación, lo que ayuda a evitar el abuso automatizado a través de la API.

_LYNX-941_

#### Validación de reCAPTCHA agregada a la mutación de GraphQL `applyCouponsToCart`

Cuando reCAPTCHA está habilitado para el formulario de cupones, la mutación de GraphQL `applyCouponsToCart` ahora aplica la misma validación, lo que ayuda a evitar la enumeración de código de cupones a través de la API.

_LYNX-942_

#### Campo `customer_id` de la API de GraphQL B2B restaurado y totalmente compatible

El campo `customer_id` en la API de GraphQL B2B se ha restaurado y ahora devuelve el valor correcto en las consultas y mutaciones de administración de la empresa. Anteriormente, el campo estaba obsoleto y devolvía `null`, lo que limitaba su utilidad para las integraciones B2B.

_LYNX-955_

### IU de administración

#### Menú Acciones para la cuadrícula de reglas de precios del catálogo

La cuadrícula **Reglas de precio de catálogo** en el administrador de Commerce ahora incluye un menú de **Acciones**, que permite a los comerciantes activar, desactivar o eliminar varias reglas a la vez. Esto hace que la administración de reglas de precios de catálogo esté en armonía con las acciones masivas existentes disponibles para **Reglas de precios del carro de compras**, lo que reduce significativamente el tiempo necesario para administrar grandes conjuntos de reglas.

_AC-13916_

#### Vista previa de Mobile para ensayo de contenido

La función de vista previa de ensayo del administrador ahora procesa las vistas previas de dispositivos móviles simulados por el explorador con precisión, de modo que los comerciantes pueden ver cómo aparecerá una actualización ensayada en un dispositivo móvil antes de que se active.

_ACP2E-3397 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

#### La nueva configuración de administración controla el comportamiento de combinación del carro de compras de invitados y clientes al iniciar sesión

Los comerciantes ahora pueden elegir cómo se combinan los artículos del carro de compras cuando un invitado inicia sesión y ya tiene un carro de compras de cliente:

- **Prioridad de invitado** — Usar la cantidad del carro de compras de invitado.
- **Prioridad del cliente**: use la cantidad del carro de compras del cliente.
- **Combinar cantidades** (predeterminado): suma ambas cantidades.

Configure este comportamiento en **Tiendas** > **Configuración** > **Ventas** > **Cierre de compra**, en **Preferencia de combinación de carritos**. La configuración se aplica a todos los tipos de productos, lo que proporciona a los comerciantes control total sobre cómo se combinan los carros de los clientes y los invitados al iniciar sesión.

_LYNX-889_

### Braintree

#### Pago y envío exprés

- **Ofertas promocionales en la hoja de pago rápido de Google Pay**

  La hoja de pago rápido de Google Pay ahora admite códigos de promoción y oferta. Los compradores pueden aplicar, ver y eliminar promociones del carro de compras de Commerce directamente dentro de la hoja de pago de Google, de modo que los clientes del proceso de pago rápido reciben los mismos descuentos e incentivos que los flujos de pago estándar.

  _PAQUETE-3476_

- **Ofertas promocionales en la hoja de pago rápido de Apple Pay**

  La hoja de pago rápido de Apple Pay ahora admite códigos de promoción y oferta. Los compradores pueden aplicar un cupón directamente dentro de la hoja de Apple Pay, por lo que los usuarios del proceso de pago rápido se benefician de los mismos descuentos y campañas que los flujos de pago estándar.

  _PAQUETE-3477_

- **Apple Pay en Chrome y Firefox**

  Apple Pay ahora se puede usar en Chrome y Firefox, no solo en Safari. Cuando Apple Pay Express está habilitado, los botones de Apple Pay están disponibles en las páginas de PDP, minicarrito, carrito y cierre de compra, y los clientes completan el pago escaneando un código con su iPhone.

  _PAQUETE-3478_

- **Devolución de llamada de envío del lado del servidor para PayPal Express**

  La llamada de retorno de envío de PayPal Express se ha movido del lado del cliente al lado del servidor. Esto proporciona métodos de envío dinámicos, cálculos de costos en tiempo real y detalles precisos a nivel de carro de compras directamente en el modal de PayPal, mejorando la confiabilidad y sentando las bases para funciones futuras como soporte al Módulo de Contacto, flujos de app-switch y Venmo Express.

  _PAQUETE-3479_

- **Módulo de contacto de PayPal para el pago y envío exprés de comerciantes de EE. UU.**

  Se ha introducido un nuevo módulo de contacto de PayPal para los comerciantes de EE. UU. Cuando se activa, los compradores que utilizan PayPal Express pueden ver y actualizar la dirección de correo electrónico y el número de teléfono compartidos con el comerciante directamente dentro del modal de PayPal durante los flujos exprés (PDP, minicarrito, carrito, pago exprés). Los datos de contacto seleccionados se almacenan en el pedido de Commerce.

  _PAQUETE-3480_

#### Métodos de pago

- **Compatibilidad con tipo de tarjeta ELO para pagos Braintree**

  Compatibilidad añadida para el tipo de tarjeta ELO en Braintree Payments. Los administradores pueden habilitar ELO en la configuración de la tarjeta de crédito, y los clientes pueden pagar con tarjetas ELO al pagar.

  _PAQUETE-3464_

- **Método de pago local BLIK para compradores polacos**

  Se ha añadido BLIK como un nuevo método de pago local para los compradores polacos. Esto permite realizar pagos BLIK seguros y basados en el banco dentro del flujo existente de métodos de pago locales (LPM) de Braintree, lo que mejora la comodidad del proceso de pago y la conversión para los clientes en Polonia.

  _PAQUETE-3481_

- **Pagar tras factura — nuevo método de pago BNPL para Alemania**

  Se agregó [!DNL Pay Upon Invoice] como un nuevo método de pago local para compradores alemanes. [!DNL Pay Upon Invoice] es una opción Comprar ahora, pagar más tarde (BNPL) con tecnología PayPal y Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) que permite a los clientes recibir productos primero y pagar la factura en un plazo de 30 días sin necesidad de una cuenta PayPal. Como no es un pago instantáneo, la finalización del pedido se realiza mediante un webhook de PayPal en el lado del servidor.

  _PAQUETE-3475_

#### Bóveda de tarjetas

- **Abonando Google Pay a través del área de la cuenta**

  Los clientes ahora pueden depositar sus tarjetas de Google Pay a través del área de cuenta cuando Google Pay Vault está activado en Braintree. Las tarjetas abovedadas aparecen en los métodos de pago almacenados, se pueden utilizar para compras futuras al cierre de compra y el cliente puede eliminarlas. Esto extiende el soporte de bóvedas más allá de Tarjetas y PayPal a Google Pay.

  _PAQUETE-3459_

- **Actualizador de cuentas en tiempo real (RTAU) para tarjetas abovedadas de Braintree**

  La función Real-Time Account Updater (RTAU) agregada a Braintree garantiza que los detalles de las tarjetas Visa, Mastercard y Discover abovedadas se actualicen automáticamente cuando las tarjetas caduquen o se reemplacen. Esto minimiza los pagos fallidos, mantiene Commerce Vault actualizado y omite los tipos no admitidos (prepago, Apple Pay, Google Pay) sin errores.

  _PAQUETE-3462_

#### Herramientas de administración

- **Vincular pedido de Commerce al portal de Braintree**

  Ahora se agrega un vínculo del portal de Braintree a los detalles del pedido en el Administrador de Commerce. Al hacer clic en el vínculo, se abre la transacción relacionada en el portal de Braintree (en una nueva pestaña), con el ID de comerciante y el ID de transacción del pedido de Commerce. Esto permite hacer referencias cruzadas directas sin iniciar sesión en ambos sistemas por separado.

  _PAQUETE-3461_

#### Seguridad y compatibilidad

- **Actualización de la directiva de seguridad de contenido de integración cardinal para 3D Secure**

  La Política de seguridad de contenido (CSP) se ha actualizado para admitir los requisitos de integración Cardinal (3-D Secure) más recientes. Esto garantiza que todos los scripts alojados en Cardinal, los iFrames y los recursos relacionados utilizados durante los flujos 3D Secure sean permitidos por el CSP del explorador, lo que evita solicitudes bloqueadas y experiencias rotas de desafío o verificación.

  _PAQUETE-3485_

- **Compatibilidad con la extensión de pago Braintree PHP 8.5**

  La extensión de pago Braintree se ha actualizado para admitir el tiempo de ejecución de PHP 8.5, manteniendo al mismo tiempo la compatibilidad con PHP 8.4.

  _PAQUETE-3493_

### Plataforma e infraestructura

#### Cargas de página más rápidas en tiendas de varios temas y configuraciones regionales después del refactor de almacenamiento hash SRI

El almacenamiento hash SRI ahora genera archivos independientes por área, tema y configuración regional, en lugar de un solo archivo `sri-hashes.json` grande. Este cambio garantiza que solo se cargue el archivo hash correspondiente a cada página, lo que mejora los tiempos de carga de la página y reduce el uso de memoria en los almacenes con varias temáticas o configuraciones regionales.

_AC-16113 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

#### Agregar compatibilidad con PHPUnit 12

La dependencia del Compositor de Adobe Commerce se ha actualizado a `phpunit/phpunit` 12.x. Todas las pruebas se actualizan por compatibilidad, mejorando la seguridad y la alineación con las últimas funciones de PHPUnit. Esta actualización mantiene Adobe Commerce preparado para futuras versiones de PHP y PHPUnit.

_AC-14808_

#### Agregar compatibilidad con RabbitMQ 4.2

RabbitMQ 4.2 es ahora un broker de mensajes compatible. Esta actualización es una ruta de compatibilidad a corto plazo que permite a los comerciantes que dependen del protocolo AMQP seguir utilizando RabbitMQ antes del fin de soporte de RabbitMQ 4.1 en febrero de 2026, sin una migración inmediata a STOMP. Para implementaciones a largo plazo, use Apache ActiveMQ Artemis como reemplazo a largo plazo de RabbitMQ.

_AC-16117_

#### Apache ActiveMQ Artemis es el reemplazo a largo plazo de RabbitMQ

Apache ActiveMQ Artemis es el intermediario de mensajes a largo plazo recomendado para Adobe Commerce, impulsado por los riesgos de fin de soporte asociados con RabbitMQ 4.1. ActiveMQ Artemis es totalmente compatible con las líneas de versión de Commerce 2.4.6 a 2.4.9. En Adobe Commerce Cloud, se entrega como AWS ActiveMQ para implementaciones nativas de la nube. Tanto los consumidores en cola como los editores pueden configurarse para utilizar STOMP.


Las instalaciones existentes de RabbitMQ 4 siguen siendo compatibles con los comerciantes que prefieren seguir usando su servicio actual de cola de mensajes a corto plazo; consulte [Agregar compatibilidad con RabbitMQ 4.2](#add-compatibility-with-rabbitmq-42) más arriba. Planifique una migración a ActiveMQ Artemis para soporte a largo plazo.

_AC-14558_

#### Añadir compatibilidad con Valkey 9.x

Adobe Commerce 2.4.9 amplía la compatibilidad con Valkey como back-end de caché compatible con Redis:

- **Valkey 9.x**: soporte completo incluido en Adobe Commerce 2.4.9, que incluye paridad de comandos CLI completa con Redis y opciones de configuración actualizadas de administración y nube para una instalación perfecta. Este trabajo se basa en los cambios de fin de soporte y licencia de Redis 7.2, lo que ofrece a los comerciantes una alternativa fiable y totalmente compatible a Redis.

_AC-14103, AC-14604, AC-16122_

#### Agregar compatibilidad con OpenSearch 3.x

Adobe Commerce 2.4.9 es totalmente compatible con OpenSearch 3.x, con la última versión menor ahora el motor de búsqueda recomendado. Los comerciantes se benefician de un mejor rendimiento, seguridad y soporte a largo plazo, mientras que la compatibilidad con versiones anteriores de OpenSearch 2.x se mantiene.

_AC-11846, AC-16403_

#### Agregar compatibilidad con MariaDB 11.8 y 12.x

MariaDB 11.8 y 12.x son ahora versiones de base de datos compatibles, lo que permite a los comerciantes adoptar las últimas versiones para mejorar el rendimiento de SQL y la estabilidad de la plataforma a largo plazo.

_AC-16533_

### PHP y Composer

#### Compatibilidad con PHP 8.5

Adobe Commerce 2.4.9 ahora es compatible con PHP 8.5 y PHP 8.4, lo que le permite ejecutar su tienda en las últimas versiones seguras y compatibles de PHP. Todas las funciones principales, extensiones agrupadas (incluidos Page Builder, B2B, Braintree y más) y servicios SaaS de Adobe son compatibles con PHP 8.5.

- PHP 8.5 y 8.4 son totalmente compatibles.
- PHP 8.3 se permite solo con fines de actualización (no recomendado para producción).
- Garantiza la conformidad con PCI y asegura la futura instalación de Adobe Commerce.

_AC-15615_

#### Compatibilidad con PHP 8.2 eliminada

A partir de Adobe Commerce 2.4.9, PHP 8.2 ya no es compatible. La plataforma ahora se dirige a PHP 8.3 y versiones posteriores, con código principal, dependencias y herramientas actualizadas para ejecutarse de forma limpia y fiable en PHP 8.4 y 8.5.

_AC-15758_

#### Compatibilidad verificada con Composer 2.9

Adobe Commerce 2.4.9 es totalmente compatible con Composer 2.x, incluido Composer 2.9. Se conserva la compatibilidad con versiones anteriores de Composer 2.x, lo que garantiza una experiencia de compilación e implementación estable para comerciantes y desarrolladores que utilizan las últimas versiones de Composer.

_AC-14481_

### Marco

#### Actualización de seguridad y compatibilidad del marco JWT

Como parte de la revisión continua de la seguridad de la plataforma, la dependencia del marco JWT de token web se ha evaluado y actualizado a la última versión principal, lo que garantiza la compatibilidad futura y estándares de seguridad sólidos para la autenticación basada en tokens en todas las integraciones de Commerce. La funcionalidad existente se ha conservado por completo.

_AC-13209 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### El marco de pruebas funcionales de Adobe Commerce se ha actualizado a las dependencias de Symfony LTS

El Marco de prueba funcional de Adobe Commerce (MFTF) se ha actualizado para utilizar las dependencias más recientes de Symfony LTS, incluida symfony/config, según lo requerido por la actualización del marco web-token/jwt-framework. Esto resuelve los conflictos de dependencias anteriores y garantiza una pila estable y compatible para las pruebas funcionales.

_AC-13244_

#### Las funciones OAuth de PHP nativas reemplazan la biblioteca de terceros

La biblioteca `carlos-mg89/oauth` de terceros se ha reemplazado con funciones OAuth de PHP nativas, lo que mejora la seguridad, reduce las dependencias externas y mejora la estabilidad de la plataforma.

_AC-14075 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### El componente Caché Symfony reemplaza a Zend_Cache

A partir de Adobe Commerce 2.4.9, el componente obsoleto Zend_Cache se ha sustituido por el componente Symfony Cache. Esta actualización mejora el rendimiento de la caché y la capacidad de mantenimiento, y garantiza la compatibilidad a largo plazo con PHP 8.x y futuras actualizaciones de la plataforma. Los back-ends de caché y los comandos de administración de caché existentes siguen siendo totalmente compatibles, y no se requieren cambios para las integraciones actuales.

_AC-15823_

#### El editor de WYSIWYG migró de TinyMCE a HugeRTE

Debido al fin de la compatibilidad con TinyMCE 5 y 6 y a las incompatibilidades de licencia con TinyMCE 7, el editor WYSIWYG de Adobe Commerce se ha migrado al editor de código abierto [HugeRTE](https://hugerte.org/). Esta migración garantiza que Adobe Commerce siga siendo compatible con las licencias de código abierto, evita las vulnerabilidades conocidas de TinyMCE 6 y ofrece una experiencia de edición moderna y compatible para comerciantes y desarrolladores.

_AC-14568_

#### La implementación nativa de MVC reemplaza a Laminas MVC

Adobe Commerce ha introducido una implementación nativa de MVC, reemplazando a la heredada Laminas MVC, para garantizar la compatibilidad y estabilidad a largo plazo más allá de PHP 8.5. Este cambio refuerza el rendimiento, reduce las dependencias externas y proporciona una base más preparada para el futuro para Commerce.

_AC-15160_

#### Soporte oficial de Symfony 7.4 LTS

Como parte de las actualizaciones de la plataforma Adobe Commerce 2.4.9, todas las dependencias de Symfony se han actualizado a las últimas versiones de Symfony LTS 7.4. Todas las clases personalizadas que amplían las clases principales de Symfony tienen declaraciones de tipos actualizadas y firmas de métodos alineadas con los requisitos más recientes de Symfony, lo que evita problemas de compatibilidad y garantiza una transición sin problemas a los componentes del marco de trabajo actualizados.

_AC-15170 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c127d10b)_

#### Dependencia de la unidad PHPUnit de Allure actualizada a la versión 3

La dependencia `allure-framework/allure-phpunit` se ha actualizado a la versión principal 3, que agrega compatibilidad con PHP 8.4 y PHP 8.5 y moderniza la pila de informes de pruebas basadas en Allure. Se ha eliminado la dependencia nativa que anteriormente requerían las versiones anteriores de Allure PHPUnit, lo que simplifica la configuración y el mantenimiento.

_AC-14548 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Informes de New Relic actualizados a la API de NerdGraph

El módulo de informes de New Relic se ha actualizado para admitir la API de seguimiento de cambios de NerdGraph (GraphQL) de New Relic, al tiempo que se conserva completamente la integración del marcador de implementación de REST v2 existente. El cambio ofrece metadatos de implementación más completos, compatibilidad con puntos de conexión regionales (EE. UU. y UE) y capacidad de configuración a través de la configuración de administración sin romper las configuraciones existentes.

_AC-15461_

#### Actualizaciones de biblioteca de JavaScript

- **Chart.js se ha actualizado a la versión 4.5.0**

  Se ha actualizado la biblioteca de gráficos JavaScript de Chart.js a la versión 4.5.0 para mejorar el rendimiento de procesamiento de gráficos, mejorar las capacidades visuales y abordar las vulnerabilidades de seguridad en el tablero de administración y en los módulos de creación de informes.

  _AC-14304, AC-15133: [contribución de código de GitHub](https://github.com/magento/magento2/commit/768b4442), [contribución de código de GitHub](https://github.com/magento/magento2/commit/657f983e)_

- **Biblioteca de carga de archivos actualizada a la versión 4.13.4**

  Se ha actualizado la biblioteca de carga de archivos de Uppy a la versión 4.13.4 para mejorar las capacidades de carga de archivos, mejorar la experiencia del usuario y resolver las vulnerabilidades de seguridad en la administración de archivos en la interfaz de administración de Adobe Commerce y en los componentes de front-end.

  _AC-14307 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/eb491c05)_

- **biblioteca jQuery Validate actualizada a la versión 1.21.0**

  Se ha actualizado la biblioteca de validación de jQuery a la versión 1.21.0 para mejorar las capacidades de validación de formularios, mejorar la experiencia del usuario y garantizar la compatibilidad del explorador moderno en todos los formularios Adobe Commerce en las interfaces de administración y de front-end.

  _AC-14403 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Biblioteca de IU de jQuery actualizada a la versión 1.14.1**

  Se ha actualizado la biblioteca de la interfaz de usuario de jQuery a la versión 1.14.1 para mejorar los widgets de la interfaz de usuario, mejorar la accesibilidad y garantizar la compatibilidad moderna del explorador en todos los componentes de la interfaz de administración y front-end de Adobe Commerce.

  _AC-14417 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/77c589a6)_

- **El preprocesador CSS Less.js se actualizó a la versión 4.2.2**

  Se ha actualizado el preprocesador CSS Less.js a la versión 4.2.2 para mejorar el rendimiento de la compilación CSS, mejorar la compatibilidad con la sintaxis y modernizar el proceso de compilación de temas en todos los temas de front-end y administración de Adobe Commerce.

  _AC-14418 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Biblioteca de zona horaria en el momento actualizada a la versión 0.5.43**

  Se ha actualizado la biblioteca de zona horaria Moment (`moment-timezone-with-data.js`) a la versión 0.5.43 para mejorar las capacidades de administración de zona horaria, actualizar los datos de zona horaria con los cambios más recientes de la base de datos de zona horaria de IANA y mejorar la precisión del procesamiento de fecha y hora en todas las operaciones internacionales y de zona horaria múltiple de Adobe Commerce.

  _AC-14419 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

- **Biblioteca de utilidades Underscore.js actualizada a la versión 1.13.7**

  Se ha actualizado la biblioteca de utilidades Underscore.js a la versión 1.13.7 para mejorar las capacidades de programación funcional de JavaScript, mejorar el rendimiento de manipulación de datos y garantizar la compatibilidad moderna del explorador en todos los componentes de interfaz de administración y front-end de Adobe Commerce.

  _AC-14420 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

### Seguridad

#### La validación CAPTCHA ahora se impone para las API de REST y GraphQL

Cuando CAPTCHA (o reCAPTCHA) está habilitado para el formulario Crear cuenta, ahora se aplica la misma validación CAPTCHA para la creación de cuentas de cliente mediante las API de REST y GraphQL.

_AC-16245_

#### Rendimiento de solicitudes asincrónicas/masivas mejorado

Esta corrección aborda la degradación del rendimiento en los puntos finales asincrónicos de API web masivos introducidos después del parche de seguridad APSB25-08, restaurando los tiempos de ejecución esperados.

_AC-14078 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Configuración de autenticación de doble factor simplificada

Ahora, los usuarios administradores solo tienen que configurar uno de los proveedores 2FA habilitados del comerciante (por ejemplo, Google Authenticator o U2F) para acceder al panel Administración. Se pueden configurar proveedores habilitados adicionales más adelante según sea necesario. Anteriormente, cuando se habilitaban varios proveedores de 2FA, todos los usuarios administradores tenían que configurarlos para poder iniciar sesión, lo que creaba fricciones para los usuarios que no tenían acceso a todos los proveedores.

_AC-8253 - [Contribución de código de GitHub](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### Envío

#### Migración de la integración de USPS a las API de RESTful USPS

Para cumplir con la retirada anunciada por USPS de las API heredadas de herramientas web, Adobe Commerce ha migrado su integración USPS a las nuevas API RESTful USPS.

Mejoras clave:

- Compatibilidad con API dual: Los usuarios administradores ahora pueden elegir entre la API heredada de Web Tools y la nueva API de RESTful USPS a través de los ajustes de configuración.
- Actualización de autenticación: Utiliza OAuth 2.0 para obtener acceso seguro a la API.
- Formato de datos mejorado: Utiliza JSON en lugar de XML para una comunicación más limpia y eficiente.
- Nuevos campos de administración:
   - URL de REST de puerta de enlace (según el modo: Desarrollo o Activo)
   - Secreto e ID del cliente
   - Tipo de cuenta, Número de cuenta
   - CRID, MID, código de identificación de Mailer
   - AES/ITN para envíos internacionales
   - Métodos de envío permitidos específicos de REST

Esta migración garantiza que Adobe Commerce siga cumpliendo con los estándares de USPS, mejore la fiabilidad del sistema y las integraciones de envíos futuras para los comerciantes.

_AC-13257_

#### Migración de la integración de DHL a las API de MyDHL RESTful

La integración de envíos de DHL integrada ahora es compatible con las API MyDHL RESTful, al tiempo que conserva la compatibilidad con la API heredada de XML de DHL Express. Los comerciantes pueden elegir qué API de DHL utilizar en el administrador, beneficiándose de las capacidades modernas de REST sin romper las configuraciones existentes basadas en XML.

_AC-13258_
