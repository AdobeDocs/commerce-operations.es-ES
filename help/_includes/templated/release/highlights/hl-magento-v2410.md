---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%
---
# Elementos destacados de Magento Open Source (v2.4.10)

## Características destacadas en la versión 2.4.10-alpha1

Los siguientes aspectos destacados se aplican a la versión Magento Open Source 2.4.10-alpha1.

### Braintree

#### Carril Rápido

Se ha agregado la compatibilidad de Fastlane by PayPal para una experiencia de pago más rápida y segura para los huéspedes.
Los clientes pueden optar por guardar los datos de pago y envío para realizar compras futuras más rápidas.
Los clientes de Fastlane que regresan pueden autenticarse con un código de una sola vez y recuperar la información guardada.
Los clientes también pueden agregar o cambiar sus tarjetas guardadas y direcciones de envío durante el cierre de compra.
También se admiten las opciones de configuración y estilo de carril rápido.

_PAQUETE-3521_

#### Braintree Insights

Se ha introducido Braintree Insights para proporcionar a los comerciantes informes centralizados de rendimiento de pagos en el administrador de Magento.
Proporciona visibilidad de los datos de transacciones, liquidaciones, rechazos de puertas de enlace y métodos de pago.
Admite el filtrado por sitio web, intervalo de fechas e intervalos diarios, semanales o mensuales.
Permite a los comerciantes importar hasta 13 meses de datos históricos de transacciones para la creación de informes.
Incluye retención de datos y limpieza automatizada para mantener hasta 3 años de datos de transacciones.

_PAQUETE-3522_

#### Swish - Método de pago local

Se ha introducido Swish como un nuevo método de pago local sueco en la extensión de Braintree Magento.
Swish está disponible cuando se cumplen las configuraciones requeridas de comerciante sueco, país, moneda y pago.
Los clientes con una dirección de envío o facturación sueca pueden completar los pagos usando Swish durante el pago.
Se ha agregado compatibilidad con flujos de pago Swish correctos, cancelados y fallidos con respuestas de cierre de compra adecuadas.
Swish solo se muestra cuando se cumplen todas las condiciones de configuración requeridas.

_PAQUETE-3523_

#### Versión actualizada a 4.9.0

Se ha actualizado el módulo Braintree de la versión 4.8.0 a la 4.9.0.
La actualización incluye los cambios y mejoras más recientes del módulo Braintree.
Se ha verificado que el proceso de pago y cierre de compra de Braintree sigue funcionando según lo esperado tras la actualización.
Los flujos de cierre de compra de clientes y creación de pedidos existentes siguen funcionando con el módulo actualizado.
Se realizaron pruebas de regresión básicas para garantizar que la actualización no introdujera ningún problema

_PAQUETE-3530_

### Marco

#### Actualizar dependencia de NPM: underscore.js (1.13.7 → 1.13.8)

Se ha actualizado underscore.js de 1.13.7 a 1.13.8 para incluir las últimas correcciones de flujo ascendente y mejoras de estabilidad.

_AC-17486 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualizar dependencia de NPM: imagemin-svgo (9.0.0 → 12.0.0)

Se ha actualizado imagemin-svgo de 9.0.0 a 12.0.0 para incluir las últimas correcciones del flujo ascendente, actualizaciones de seguridad y mejoras en la optimización de SVG.

_AC-17657 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualizar dependencia de NPM: eslint-formatter-junit (8.40.0 → 9.0.1)

Se ha actualizado eslint-formatter-junit de 8.40.0 a 9.0.1 para incluir las últimas correcciones del flujo ascendente y mejoras de compatibilidad para la creación de informes de ESLint.

_AC-17659 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualizar dependencia de NPM: glob (11.0.0 → 13.0.0)

Se ha actualizado glob de 11.0.0 a 13.0.0 para incluir las últimas correcciones del flujo ascendente, mejoras de rendimiento y mejoras de compatibilidad.

_AC-17660 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualizar dependencia de NPM: grunt-eslint (25.0.0 → 26.0.0)

Se ha actualizado grunt-eslint de 25.0.0 a 26.0.0 para incluir las últimas correcciones del flujo ascendente y mejoras de compatibilidad.

_AC-17661 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualizar dependencia de NPM: server-static (1.16.2 → 2.2.1)

Se ha actualizado serve-static de 1.16.2 a 2.2.1 para incluir las últimas correcciones del flujo ascendente, actualizaciones de seguridad y mejoras de compatibilidad.

_AC-17662 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualice las últimas dependencias de NPM para Grunt y Less

Se han actualizado Grunt y Less a las últimas versiones compatibles, lo que mejora la estabilidad y compatibilidad de la versión de front-end.

_AC-17663 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

#### Actualizar dependencias de anulación de NPM a las últimas versiones compatibles

Se han actualizado varias dependencias de anulación de NPM a las últimas versiones compatibles, lo que mejora la seguridad, la estabilidad de compilación y la compatibilidad.

_AC-17664 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c69ec9c5)_

### Otros

#### Actualización de predis/predis de 2.x a 3.x

La biblioteca de cliente Redis predis/predis se actualizó de la versión 2.x a la 3.x. Esta actualización de la versión principal se ajusta a los estándares de dependencia más recientes, mejora la compatibilidad y garantiza el mantenimiento a largo plazo.

_AC-17101 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Actualice knockout.js de la versión 3.5.1 a la 3.5.3.

Se ha actualizado la biblioteca knockout.js de la versión 3.5.1 a la 3.5.3. Esta actualización incluye correcciones de errores y mejoras de estabilidad para todos los componentes de la interfaz de usuario mediante enlaces de cobertura en tienda y administración.

_AC-17366 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/de7188da)_
