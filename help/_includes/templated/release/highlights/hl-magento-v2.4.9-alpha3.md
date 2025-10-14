---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Notas de la versión de Magento Open Source (v2.4.9-alpha3)

## Características destacadas en la versión 2.4.9-alpha3

Los siguientes aspectos destacados se aplican a la versión Magento Open Source 2.4.9-alpha3.

### Braintree

#### Abonos de Google Pay a través del área de cuenta

En Magento 2.4.9-alpha3, los clientes ahora pueden Vault sus tarjetas de pago de Google a través del área de cuenta cuando Google Pay Vault está habilitado en Braintree. Las tarjetas abovedadas aparecen en los métodos de pago almacenados, se pueden utilizar para compras futuras al cierre de compra y el cliente puede eliminarlas. Esto extiende el soporte de bóvedas más allá de Tarjetas y PayPal a Google Pay.

_PAQUETE-3459_

#### Vincular pedido de Magento al pedido de portal de Braintree

En Magento 2.4.9-alpha3, ahora se agrega un vínculo del portal de Braintree a los detalles del pedido en el Administrador de Magento. Al hacer clic en el vínculo, se abre la transacción relacionada en el portal de Braintree (en una nueva pestaña), con el ID de comerciante y el ID de transacción del pedido de Magento. Esto permite hacer referencias cruzadas directas sin iniciar sesión en ambos sistemas por separado.

_PAQUETE-3461_

#### Actualizador de cuentas en tiempo real (RTAU)

La función Real Time Account Updater (RTAU) de Magento 2.4.9-alpha3 para Braintree garantiza que los detalles de las tarjetas Visa, Mastercard y Discover abovedadas se actualicen automáticamente cuando las tarjetas caduquen o se reemplacen. Esto minimiza los pagos fallidos, mantiene Magento Vault actualizado y omite los tipos no admitidos (prepago, Apple Pay, Google Pay) sin errores.

_PAQUETE-3462_

#### Soporte de tipo tarjeta ELO para Braintree Card Payments

En Magento 2.4.9-alpha3, se ha añadido compatibilidad con el tipo de tarjeta ELO a Braintree Payments. Los administradores ahora pueden habilitar ELO en la configuración de la tarjeta de crédito, y los clientes pueden realizar pedidos con éxito utilizando tarjetas ELO al cierre de compra, lo que garantiza transacciones sin problemas a través de Braintree.

_PAQUETE-3464_

### Marco

#### Migración de RabbitMQ a Apache ActiveMQ

_AC-14558_

#### Actualice la dependencia de chart.js a la versión más reciente

La dependencia de chart.js se ha actualizado a la versión 4.5.0 más reciente

_AC-15133 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Migración desde Laminas MVC

Adobe Commerce ha introducido una implementación nativa de MVC, reemplazando a la heredada Laminas MVC, para garantizar la compatibilidad y estabilidad a largo plazo más allá de PHP 8.5. Este cambio refuerza el rendimiento, reduce las dependencias externas y proporciona una base más preparada para el futuro para Commerce

_AC-15160_
