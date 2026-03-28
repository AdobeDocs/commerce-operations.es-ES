---
source-git-commit: adda02b9d05b66ab066f110e877584bc1c77515d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Aspectos destacados de Adobe Commerce (versión 2.4.9-beta1)

## Aspectos destacados en la versión 2.4.9-beta1

Los siguientes aspectos destacados se aplican a la versión Adobe Commerce 2.4.9-beta1.

### API

#### Control de herencia de la galería de productos API REST en el nivel de vista de tienda

La actualización de un producto mediante la API de REST en un ámbito de almacén ya no hace que las imágenes y los vídeos de productos hereden los cambios del ámbito global cuando `media_gallery_entries` se omite en la carga útil o se establece en `NULL`. Ahora también es posible restaurar la herencia de ámbito para imágenes y vídeos de productos mediante la API de REST estableciendo el campo correspondiente en `NULL`.

_ACP2E-4358 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### IU de administración

#### Menú Acciones para la cuadrícula de reglas de precios del catálogo

La cuadrícula Reglas de precio de catálogo del Administrador de Commerce ahora incluye un menú Acciones, que permite a los comerciantes activar, desactivar o eliminar varias reglas de precio de catálogo a la vez. Esto hace que la administración de reglas de precios de catálogo esté en armonía con las acciones masivas existentes disponibles para las reglas de precios del carro de compras, lo que reduce considerablemente el tiempo necesario para administrar grandes conjuntos de reglas.

_AC-13916_

#### Vista previa de Mobile para ensayo de contenido

La función de vista previa de ensayo del administrador ahora permite que las vistas previas de dispositivos móviles simulados por el explorador se representen con precisión, lo que proporciona una representación visual de cómo aparecerá una actualización de ensayo en un dispositivo móvil.

_ACP2E-3397 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### Pago y envío exprés

- **Ofertas promocionales en la hoja de pago rápido de Google Pay**

  La hoja de pago Google Pay Express ahora admite códigos de promoción y oferta. Los compradores pueden aplicar, ver y eliminar promociones del carro de compras de Commerce directamente dentro de la hoja de pago de Google, lo que garantiza que los clientes del proceso de pago rápido reciban los mismos descuentos e incentivos que los flujos de pago estándar.

  _PAQUETE-3476_

- **Ofertas promocionales en la hoja de pago rápido de Apple Pay**

  La hoja de pago Apple Pay Express ahora admite códigos de promoción y oferta. Los compradores pueden aplicar un cupón directamente dentro de la hoja de Apple Pay, por lo que los usuarios del proceso de pago rápido se benefician de los mismos descuentos y campañas que los flujos de pago estándar.

  _PAQUETE-3477_

- **Apple Pay en Chrome y Firefox**

  Apple Pay ahora se puede usar en Chrome y Firefox, no solo en Safari. Cuando Apple Pay Express está activado, los botones de Apple Pay están disponibles en todas las ubicaciones de tiendas admitidas y los clientes completan el pago escaneando un código con su iPhone.

  _PAQUETE-3478_

- **Devolución de llamada de envío del lado del servidor para PayPal Express**

  La llamada de retorno de envío de PayPal Express se ha movido del lado del cliente al lado del servidor. Esto proporciona métodos de envío dinámicos, cálculos de costos en tiempo real y detalles precisos a nivel de carro de compras directamente en el modal de PayPal, mejorando la confiabilidad y sentando las bases para funciones futuras como soporte al Módulo de Contacto, flujos de app-switch y Venmo Express.

  _PAQUETE-3479_

- **Módulo de contacto de PayPal para el pago y envío exprés de comerciantes de EE. UU.**

  Se ha introducido un nuevo módulo de contacto de PayPal para los comerciantes de EE. UU. Cuando se activa, los compradores que utilizan PayPal Express pueden ver y actualizar la dirección de correo electrónico y el número de teléfono compartidos con el comerciante directamente dentro del modal de PayPal durante los flujos exprés (PDP, minicarrito, carrito, pago exprés). Los datos de contacto seleccionados se almacenan en el pedido de Commerce.

  _PAQUETE-3480_

#### Métodos de pago

- **Compatibilidad con tipo de tarjeta ELO para pagos Braintree**

  Compatibilidad añadida para el tipo de tarjeta ELO en Braintree Payments. Los administradores ahora pueden habilitar ELO en la configuración de la tarjeta de crédito, y los clientes pueden realizar pedidos con éxito utilizando tarjetas ELO al cierre de compra, lo que garantiza transacciones sin problemas a través de Braintree.

  _PAQUETE-3464_

- **Método de pago local BLIK para compradores polacos**

  Se ha añadido BLIK como un nuevo método de pago local para los compradores polacos. Esto permite realizar pagos BLIK seguros y basados en el banco dentro del flujo existente de métodos de pago locales (LPM) de Braintree, lo que mejora la comodidad del proceso de pago y la conversión para los clientes en Polonia.

  _PAQUETE-3481_

- **Pagar tras factura — nuevo método de pago BNPL para Alemania**

  Se ha añadido una nueva forma de pago local, Pago tras factura para compradores alemanes. Pagar tras la factura es una opción Comprar ahora, pagar más tarde (BNPL) con tecnología PayPal y Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) que permite a los clientes recibir productos primero y pagar la factura en un plazo de 30 días, sin necesidad de una cuenta PayPal. Como no es un pago instantáneo, la finalización del pedido se realiza mediante un webhook de PayPal en el lado del servidor.

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

#### Compatibilidad con OpenSearch 3.x

Adobe Commerce 2.4.9-beta1 es totalmente compatible con OpenSearch 3.x. Esta actualización permite a los comerciantes beneficiarse de un rendimiento mejorado, seguridad y soporte a largo plazo, manteniendo al mismo tiempo la compatibilidad con versiones anteriores de OpenSearch 2.x.

_AC-11846_

#### Compatibilidad total con Valkey 8.x

Adobe Commerce 2.4.9-beta1 agrega compatibilidad completa con Valkey 8.x como back-end de caché compatible con Redis, incluida la paridad de comandos CLI completa con Redis. Se han actualizado las opciones de configuración de administración y nube para una configuración de Valkey perfecta. Esta compatibilidad está impulsada por los cambios de fin de soporte y licencia de Redis 7.2, lo que proporciona a los comerciantes una alternativa fiable y totalmente compatible a Redis en las líneas de versión 2.4.5 a 2.4.9-beta1 de Commerce.

_AC-14103, AC-14604_

#### La compatibilidad con Apache ActiveMQ Artemis reemplaza a RabbitMQ

Se ha agregado compatibilidad con Apache ActiveMQ Artemis como alternativa estratégica a RabbitMQ, impulsada por riesgos de fin de soporte asociados con RabbitMQ 4. ActiveMQ Artemis ahora es totalmente compatible con todas las líneas de versión de Commerce 2.4.6 a 2.4.9-beta1, incluido Adobe Commerce Cloud con AWS ActiveMQ para implementaciones nativas en la nube, y admite la configuración STOMP para consumidores y editores en cola. Las instalaciones existentes de RabbitMQ 4 siguen siendo compatibles con los comerciantes que prefieren seguir utilizando su servicio actual de cola de mensajes.

_AC-14558_

### PHP y Composer

#### Compatibilidad con PHP 8.5

A partir de Adobe Commerce 2.4.9-beta1, la plataforma es totalmente compatible con PHP 8.5, al tiempo que mantiene la compatibilidad con PHP 8.4 y permite PHP 8.3 para escenarios de solo actualización. Este trabajo moderniza el código principal, las dependencias y las herramientas para que los comerciantes puedan pasar con seguridad a las versiones más nuevas de PHP antes del fin de la compatibilidad con PHP 8.4, manteniendo el cumplimiento con PCI y el estado de la plataforma a largo plazo.

_AC-15615_

#### Compatibilidad con PHP 8.2 eliminada

A partir de Adobe Commerce 2.4.9-beta1, PHP 8.2 ya no es compatible. La plataforma ahora se dirige a PHP 8.3 y versiones posteriores, con código principal, dependencias y herramientas actualizadas para ejecutarse de forma limpia y fiable en PHP 8.4 y 8.5.

_AC-15758_

#### Compatibilidad verificada con Composer 2.9

Adobe Commerce 2.4.9-beta1 es totalmente compatible con Composer 2.x, incluido Composer 2.9. Esta alineación preserva la compatibilidad con versiones anteriores y garantiza una experiencia de compilación e implementación estable para los comerciantes y desarrolladores que utilizan las últimas versiones de Composer.

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

A partir de Adobe Commerce 2.4.9-beta1, el componente obsoleto Zend_Cache se ha sustituido por el componente Symfony Cache. Esta actualización mejora el rendimiento de la caché y la capacidad de mantenimiento, y garantiza la compatibilidad a largo plazo con PHP 8.x y futuras actualizaciones de la plataforma. Los back-ends de caché y los comandos de administración de caché existentes siguen siendo totalmente compatibles, y no se requieren cambios para las integraciones actuales.

_AC-15823_

#### El editor de WYSIWYG migró de TinyMCE a HugeRTE

Debido al fin de la compatibilidad con TinyMCE 5 y 6 y a las incompatibilidades de licencia con TinyMCE 7, el editor WYSIWYG de Adobe Commerce se ha migrado al editor de código abierto [HugeRTE](https://hugerte.org/). Esta migración garantiza que Adobe Commerce siga siendo compatible con las licencias de código abierto, evita las vulnerabilidades conocidas de TinyMCE 6 y ofrece una experiencia de edición moderna y compatible para comerciantes y desarrolladores.

_AC-14568_

#### La implementación nativa de MVC reemplaza a Laminas MVC

Adobe Commerce ha introducido una implementación nativa de MVC, reemplazando a la heredada Laminas MVC, para garantizar la compatibilidad y estabilidad a largo plazo más allá de PHP 8.5. Este cambio refuerza el rendimiento, reduce las dependencias externas y proporciona una base más preparada para el futuro para Commerce.

_AC-15160_

#### Soporte oficial de Symfony 7.4 LTS

Como parte de las actualizaciones de la plataforma Adobe Commerce 2.4.9-beta1, todas las dependencias de Symfony se han actualizado a las últimas versiones de Symfony LTS 7.4. Todas las clases personalizadas que amplían las clases principales de Symfony tienen declaraciones de tipos actualizadas y firmas de métodos alineadas con los requisitos más recientes de Symfony, lo que evita problemas de compatibilidad y garantiza una transición sin problemas a los componentes del marco de trabajo actualizados.

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

Ahora, los usuarios administradores solo tienen que configurar uno de los proveedores 2FA habilitados del comerciante (por ejemplo, Google Authenticator o U2F) para acceder al panel Administración. Se pueden configurar proveedores habilitados adicionales más adelante según sea necesario. Anteriormente, cuando se habilitaban varios proveedores de 2FA, todos los usuarios administradores tenían que configurar todos los proveedores habilitados para poder iniciar sesión, lo que creaba fricciones para los usuarios que no tenían acceso a todos los factores.

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
