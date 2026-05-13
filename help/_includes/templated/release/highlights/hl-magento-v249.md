---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Elementos destacados de Magento Open Source (v2.4.9)

## Aspectos destacados en la versión 2.4.9

En la versión de Magento Open Source 2.4.9 se aplican los siguientes aspectos destacados.

### API

#### Agregar la posibilidad de mantener la herencia de la galería de productos en la API de REST al actualizar un producto en el nivel de vista de tienda

La actualización de un producto mediante la API de REST en un ámbito de tienda ya no impide que las imágenes y los vídeos de producto hereden cambios del ámbito global si media_gallery_entries se omite en la carga útil o se establece en NULL para evitar cualquier cambio en la galería de productos en ese ámbito. Además, ahora es posible restaurar la herencia de ámbito para imágenes de productos y vídeo a través de la API de REST estableciendo el campo correspondiente en NULL.

_ACP2E-4358 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### Abonos de Google Pay a través del área de cuenta

En Adobe Commerce 2.4.9, los clientes ahora pueden Vault sus tarjetas de pago Google a través del área de cuenta cuando Google Pay Vault está habilitado en Braintree. Las tarjetas abovedadas aparecen en los métodos de pago almacenados, se pueden utilizar para compras futuras al cierre de compra y el cliente puede eliminarlas. Esto extiende el soporte de bóvedas más allá de Tarjetas y PayPal a Google Pay.

_PAQUETE-3459_

#### Actualizador de cuentas en tiempo real (RTAU)

La función Real Time Account Updater (RTAU) de Adobe Commerce 2.4.9 para Braintree garantiza que los detalles de las tarjetas Visa, Mastercard y Discover abovedadas se actualicen automáticamente cuando las tarjetas caduquen o se reemplacen. Esto minimiza los pagos fallidos, mantiene Magento Vault actualizado y omite los tipos no admitidos (prepago, Apple Pay, Google Pay) sin errores.

_PAQUETE-3462_

#### Soporte de tipo tarjeta ELO para Braintree Card Payments

En Adobe Commerce 2.4.9, se ha añadido compatibilidad con el tipo de tarjeta ELO a Braintree Payments. Los administradores ahora pueden habilitar ELO en la configuración de la tarjeta de crédito, y los clientes pueden realizar pedidos con éxito utilizando tarjetas ELO al cierre de compra, lo que garantiza transacciones sin problemas a través de Braintree.

_PAQUETE-3464_

#### Pagar tras factura

Para Adobe Commerce 2.4.9 (extensión de Braintree), se ha añadido un nuevo método de pago local &quot;Pagar tras factura&quot; para compradores alemanes. Pagar tras la factura es una opción Comprar ahora, pagar más tarde (BNPL) con tecnología PayPal + Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) que permite a los clientes recibir productos primero y pagar la factura en un plazo de 30 días, sin necesidad de una cuenta PayPal. Como no se trata de un pago instantáneo, la finalización del pedido se realiza mediante un webhook de PayPal en el servidor.

_PAQUETE-3475_

#### Añadir ofertas a la hoja de pago de Google Pay Express

Para la extensión de Braintree en Adobe Commerce 2.4.9, la hoja de Google Pay Express Pay ahora admite códigos de promoción/oferta. Los compradores pueden aplicar, ver y eliminar promociones del carro de compras de Magento directamente dentro de la hoja de pago de Google, lo que garantiza que los clientes del proceso de pago rápido reciban los mismos descuentos e incentivos que los flujos de pago estándar.

_PAQUETE-3476_

#### Añadir ofertas a la hoja de pago de Apple Pay Express

Para la extensión de Braintree en Adobe Commerce 2.4.9, la hoja de Apple Pay Express Pay ahora admite códigos de promoción/oferta. Los compradores pueden aplicar un cupón directamente dentro de la hoja de Apple Pay, por lo que los usuarios del proceso de pago rápido se benefician de los mismos descuentos y campañas que los flujos de pago estándar.

_PAQUETE-3477_

#### Paga con Apple Pay en Chrome y Firefox

Para la extensión de Braintree en Adobe Commerce 2.4.9, Apple Pay ahora se puede utilizar en Chrome y Firefox, no solo en Safari. Cuando Apple Pay Express está activado, los botones de Apple Pay están disponibles en todas las ubicaciones de tiendas admitidas y los clientes completan el pago escaneando un código con su iPhone.

_PAQUETE-3478_

#### Devolución de llamada de envío del servidor

Para la extensión de Braintree en Adobe Commerce 2.4.9, la llamada de retorno de envío de PayPal Express se ha movido del lado del cliente al lado del servidor. Esto proporciona métodos de envío dinámicos, cálculos de costos en tiempo real y detalles precisos a nivel de carro de compras directamente en el modal de PayPal, mejorando la confiabilidad y sentando las bases para funciones futuras como soporte al Módulo de Contacto, flujos de app-switch y Venmo Express.

_PAQUETE-3479_

#### Módulo de contacto de PayPal

Para la extensión de Braintree en Adobe Commerce 2.4.9, se presenta un nuevo módulo de contacto de PayPal para los comerciantes de EE. UU. Cuando se activa, los compradores que utilizan PayPal Express pueden ver y actualizar la dirección de correo electrónico y el número de teléfono compartidos con el comerciante directamente dentro del modal de PayPal durante los flujos exprés (PDP, minicarrito, carrito, pago exprés). Los datos de contacto seleccionados se almacenan en el pedido de Adobe Commerce.

_PAQUETE-3480_

#### BLIK (Método de pago local)

Para la extensión Braintree en Adobe Commerce 2.4.9, se ha añadido BLIK como un nuevo método de pago local para los compradores polacos. Esto permite realizar pagos BLIK seguros y basados en el banco dentro del flujo existente de métodos de pago locales (LPM) de Braintree, lo que mejora la comodidad del proceso de pago y la conversión para los clientes en Polonia.

_PAQUETE-3481_

#### Política del CSP de actualización de integración cardinal

Para la extensión de Braintree en Adobe Commerce 2.4.9, la Política de seguridad de contenido (CSP) se ha actualizado para admitir los requisitos de integración Cardinal (3-D Secure) más recientes. Esto garantiza que todos los scripts alojados en Cardinal, los iFrames y los recursos relacionados utilizados durante los flujos 3D Secure sean permitidos por el CSP del explorador, lo que evita solicitudes bloqueadas y experiencias de desafío/verificación rotas.

_PAQUETE-3485_

### Marco

#### Se ha actualizado la biblioteca web-token/jwt-framework a la última versión principal

Como parte del proceso continuo de revisión de la seguridad, evaluamos la última versión del marco JWT para garantizar la futura compatibilidad y mantener estándares de seguridad sólidos. Esta versión no afecta a la funcionalidad existente.

_AC-13209 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### [Parte 2]: Actualice toda la biblioteca js y la dependencia npm con la última versión disponible

la compatibilidad con la versión del compositor estaba hasta la versión del compositor 2.2.x solamente. Ahora, la compatibilidad también se ha ampliado a la versión 2.4.x.

_AC-13792 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/19844aa0)_

#### Reemplace carlos-mg89/oauth con funciones nativas de PHP

Se ha reemplazado la biblioteca carlos-mg89/oauth de terceros con funciones OAuth de PHP nativas para mejorar la seguridad, reducir las dependencias externas y mejorar la estabilidad de la plataforma.

_AC-14075 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Actualice las bibliotecas de jquery/uppy y uppy con la última versión

Se ha actualizado la biblioteca de carga de archivos de Uppy a la versión 4.13.4 para mejorar las capacidades de carga de archivos, mejorar la experiencia del usuario y resolver las vulnerabilidades de seguridad en la administración de archivos en la interfaz de administración de Adobe Commerce y en los componentes de front-end.

_AC-14307 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/eb491c05)_

#### Actualice la biblioteca jquery-validate a la versión más reciente

Se ha actualizado la biblioteca de validación de jQuery a la versión 1.21.0 para mejorar las capacidades de validación de formularios, mejorar la experiencia del usuario y garantizar la compatibilidad del explorador moderno en todos los formularios Adobe Commerce en las interfaces de administración y de front-end.

_AC-14403 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Actualice la biblioteca jquery-ui a la versión más reciente

Se ha actualizado la biblioteca de la interfaz de usuario de jQuery a la versión 1.14.1 para mejorar los widgets de la interfaz de usuario, mejorar la accesibilidad y garantizar la compatibilidad moderna del explorador en todos los componentes de la interfaz de administración y front-end de Adobe Commerce.

_AC-14417 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Actualice la biblioteca less.js a la versión más reciente

Se ha actualizado el preprocesador CSS Less.js a la versión 4.2.2 para mejorar el rendimiento de la compilación CSS, mejorar la compatibilidad con la sintaxis y modernizar el proceso de compilación de temas en todos los temas de front-end y administración de Adobe Commerce.

_AC-14418 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Actualice la biblioteca moment-timezone-with-data.js a la versión más reciente

Se ha actualizado la biblioteca de zona horaria Moment a la versión 0.5.43 para mejorar las capacidades de administración de zonas horarias, actualizar los datos de zona horaria con los últimos cambios en la base de datos de zonas horarias de IANA y mejorar la precisión del procesamiento de fecha y hora en todas las operaciones internacionales y de zonas horarias múltiples de Adobe Commerce.

_AC-14419 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Actualice la biblioteca underscore.js a la versión más reciente

Se ha actualizado la biblioteca de utilidades Underscore.js a la versión 1.13.7 para mejorar las capacidades de programación funcional de JavaScript, mejorar el rendimiento de manipulación de datos y garantizar la compatibilidad moderna del explorador en todos los componentes de interfaz de administración y front-end de Adobe Commerce.

_AC-14420 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Actualice allure-framework/allure-phpunit versión a 3 y elimine la dependencia nativa en 2.4.9-alpha1

En Adobe Commerce 2.4.9, la dependencia allure-framework/allure-phpunit se ha actualizado a la versión principal 3, que agrega compatibilidad con PHP 8.4, PHP 8.5 y moderniza nuestro grupo de informes de pruebas basado en Allure. La dependencia nativa que anteriormente requerían las versiones anteriores de Allure PHPUnit se ha eliminado cuando corresponde, lo que simplifica la configuración y el mantenimiento.

_AC-14548 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Actualice la dependencia de chart.js a la versión más reciente

La dependencia de chart.js se ha actualizado a la versión 4.5.0 más reciente.

_AC-15133 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Añade soporte oficial para Symfony 7.4 LTS y PHP 8.5 en Adobe Commerce 2.4.9

Como parte de las actualizaciones de la plataforma Adobe Commerce 2.4.9, todas las dependencias de Symfony utilizadas por el paquete magento/composer se han actualizado a las últimas versiones de Symfony LTS 7.4. Esto alinea la herramienta Compositor de Commerce con la línea actual de Symfony LTS y elimina las restricciones de dependencia anteriores relacionadas con versiones anteriores de Symfony. Además, todas las clases personalizadas que amplían las clases principales de Symfony han actualizado las declaraciones de tipos y las firmas de métodos alineadas con los requisitos más recientes de Symfony antes de actualizar a Adobe Commerce 2.4.9. Esto evitará problemas de compatibilidad y garantizará una transición sin problemas a los componentes del marco actualizado.

_AC-15170 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Asegúrese de que la mutación de GraphQL clearCart esté disponible en Open Source

Con Adobe Commerce 2.4.9, la mutación clearCart GraphQL ya está disponible para todos los usuarios de Open Source. Anteriormente, esta mutación solo era accesible en Adobe Commerce, pero ahora también forma parte de la funcionalidad estándar de carrito de GraphQL para Open Source.
La documentación de la mutación se ha actualizado para reflejar su disponibilidad en Open Source para la versión 2.4.9.
Consulte [documentación sobre la mutación de GraphQL clearCart](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/).

_AC-16683 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/4449d914)_

#### [AC-2.4.9]: combinando la lógica del carro de compras de clientes e invitados mediante la configuración de administración

Se ha introducido una nueva opción de configuración de administración para controlar cómo se combinan los carros de compras de invitados y clientes cuando un comprador inicia sesión. Esta mejora le proporciona flexibilidad para definir el comportamiento de combinación de carro de compras que mejor se adapte a sus necesidades comerciales.

_LYNX-889_

#### [AC-2.4.9] Obteniendo pedidos históricos con productos sin existencias

Los pedidos históricos ahora muestran detalles del producto incluso si ya no están disponibles.

_LYNX-913_

#### [AC-2.4.9] [CE] Implementar ReCaptcha para mutaciones de GraphQL que faltan

La validación de ReCaptcha se agrega a las mutaciones updateCustomer, updateCustomerV2 y contactUs.

_LYNX-941_

### Otros

#### Captcha/reCAPTCHA no funciona para API/GraphQL

En Adobe Commerce 2.4.9, cuando CAPTCHA (o reCAPTCHA) está habilitado para el formulario Crear cuenta, ahora se aplica la misma validación CAPTCHA para la creación de cuentas de cliente mediante las API de REST y GraphQL.

_AC-16245 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

#### La rama braintree debe actualizarse con soporte para PHP 8.5

La extensión de pago Braintree se ha actualizado para admitir el último tiempo de ejecución de PHP 8.5, manteniendo al mismo tiempo la compatibilidad con PHP 8.4.

_PAQUETE-3493_

#### Agregar operación de borrado de lista de deseos

Se ha añadido una nueva mutación clearWishlist para admitir operaciones masivas, lo que permite eliminar todos los elementos de una lista de deseos en una sola acción.

_LYNX-790_

#### Introducir la mutación exchangeExternalCustomerToken

Se ha introducido una nueva mutación de GraphQL exchangeExternalCustomerToken que autentica a los usuarios mediante un token de integración y devuelve tanto el token de cliente como los datos de cliente asociados

_LYNX-815_

#### [AC] introduce consultas de GraphQL que devuelven id de grupos, segmentos y reglas del carro de compras aplicados

las consultas de GraphQL expuestas a recuperar el uid codificado del grupo de clientes, los segmentos de clientes y las reglas del carro de compras aplicados.

_LYNX-867_

#### [AC-2.4.9] Introducir campo OrderTotal.grand_total_excl_tax

Se ha añadido un nuevo campo, OrderTotal.grand_total_excl_tax, a la respuesta de pedido de GraphQL. Este campo proporciona el total general excluido de impuestos del pedido, lo que facilita el acceso a los totales exclusivos de impuestos directamente desde la API.

Ventajas:

- Recupere fácilmente el total general sin impuestos para cualquier pedido a través de GraphQL.
- Simplifica la integración con sistemas externos que requieren totales exclusivos de impuestos.
- Reduce la necesidad de realizar cálculos personalizados en el lado del cliente.

_LYNX-892_

### PCI, seguridad

#### Refactorización del almacenamiento SRI para aumentar la eficiencia del rendimiento

El almacenamiento hash SRI ahora genera archivos independientes por área, tema y configuración regional, en lugar de un único archivo sri-hashes.json de gran tamaño. Este cambio garantiza que solo se cargue el archivo hash correspondiente a cada página, lo que mejora el rendimiento y reduce el uso de memoria en tiendas con varios temas o configuraciones regionales.

_AC-16113 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/bc83cd2c)_

### Seguridad

#### Mejora del rendimiento de las solicitudes asíncronas/masivas

Corrija la degradación del rendimiento en los extremos web asincrónicos masivos introducidos después del parche de seguridad APSB25-08, lo que da como resultado un aumento de los tiempos de ejecución.

_AC-14078 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Solo es necesario habilitar un proveedor 2FA para cada usuario

Ahora, los usuarios administradores solo tienen que configurar uno de los proveedores 2FA habilitados del comerciante (por ejemplo, Google Authenticator o U2F) para acceder al panel Administración. Se pueden configurar proveedores habilitados adicionales más adelante según sea necesario. Anteriormente, cuando se habilitaban varios proveedores de 2FA (por ejemplo, Google Authenticator y U2F), todos los usuarios administradores tenían que configurar todos los proveedores habilitados para poder iniciar sesión. Esto creó fricción para los usuarios que no tenían acceso a todos los factores (como una clave de hardware para U2F).

_AC-8253 - [Contribución de código de GitHub](https://github.com/magento/security-package/commit/71e7936b)_
