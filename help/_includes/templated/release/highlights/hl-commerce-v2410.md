---
source-git-commit: 78a34dc069a30b72a1e0baff36085a2458a05983
workflow-type: tm+mt
source-wordcount: '1349'
ht-degree: 0%
---
# Elementos destacados de Adobe Commerce (v2.4.10)

## Características destacadas en la versión 2.4.10-alpha1

Los siguientes aspectos destacados se aplican a la versión Adobe Commerce 2.4.10-alpha1.

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

#### Actualización del componente de plataforma [2.4.10-alpha1]

Adobe Commerce 2.4.10-alpha1 incluye un conjunto de actualizaciones de dependencia de la plataforma, mejoras de compatibilidad, actualizaciones de la biblioteca de front-end y correcciones de estabilidad. En esta versión se incluyen los siguientes cambios completados:

- Predis: se actualizó `predis/predis` de 2.x a 3.x, lo que mejora la compatibilidad con los entornos Redis y Valkey y mantiene al cliente Redis alineado con las últimas versiones de dependencia admitidas.
- Instalador del Compositor de Magento: se ha corregido un problema por el que `magento-composer-installer` podía salir de forma silenciosa sin completar el proceso de instalación, lo que mejoraba la fiabilidad de las instalaciones basadas en el Compositor.
- Knockout.js: se ha actualizado Knockout.js de la versión 3.5.1 a la 3.5.3, junto con las actualizaciones de validación y compatibilidad necesarias.
- Chart.js: se ha actualizado Chart.js de la versión 4.5.0 a la 4.5.1, incluidas las actualizaciones de validación y compatibilidad necesarias.
- Less.js: se ha actualizado Less.js de la versión 4.2.2 a la 4.6.4, con las actualizaciones de validación y compatibilidad asociadas.
- Actualización: se ha actualizado la actualización de 5.0.0 a 5.2.0, incluidos los cambios necesarios de validación y compatibilidad.
- Interfaz de usuario de jQuery: se ha actualizado la interfaz de usuario de jQuery de 1.14.1 a 1.14.2, con las actualizaciones de validación y compatibilidad asociadas.
- Compatibilidad con PHP 8.5: Se ha solucionado un problema de obsolescencia de PHP 8.5 relacionado con `chr()`, que garantizaba que la función proporcionaba valores de bytes válidos y mejoraba la compatibilidad con PHP 8.5.
- Búsqueda en el catálogo: se ha corregido un problema por el que la reindexación de `catalogsearch_fulltext` podía detenerse durante el procesamiento, lo que mejoraba la fiabilidad de la indexación de la búsqueda en el catálogo.
- js-cookie: se ha actualizado js-cookie de 3.0.5 a 3.0.7 o la versión compatible aplicable, para satisfacer los requisitos de dependencia y compatibilidad.

_AC-17061_

#### Garantizar la compatibilidad de B2B 1.5.3-p1/1.5.4-alpha1 con 2.4.10-alpha1, 2.4.9-p1, 2.4.8-p6, 2.4.7-p11 y 2.4.6-p16

B2B 1.5.4-alpha1 es compatible con las siguientes líneas de versión de Adobe Commerce: 2.4.9, 2.4.8, 2.4.7 y 2.4.6.

_AC-17100_

#### Actualización y modernización de dependencias NPM

Se han actualizado las siguientes dependencias npm a sus últimas versiones seguras para abordar vulnerabilidades de seguridad conocidas:

- subrayar
- imagemin-svgo
- globo
- server-static
- gruñir
- menos
- uglify-js
- marcado
- clean-css
- minimizar
- trim-newlines
- terser
- css-select
- nth-check
- semver-regex
- http-cache-semantics
- js-yaml
- package-json

Estas actualizaciones de dependencias mitigan las vulnerabilidades de seguridad identificadas al tiempo que mantienen la funcionalidad de la aplicación existente.

_AC-17372_

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

#### [B2B] Los pedidos de compra no se convierten automáticamente en pedidos de venta con ActiveMQ

Se corrigió un problema en el cual los pedidos de compra realizados a través de la tienda con la aprobación automática habilitada no se convertían automáticamente en pedidos de venta al usar ActiveMQ y al ejecutar consumidores a través de cron (bin/magento cron:run). Anteriormente, los mensajes se agregaban a la cola de ActiveMQ pero no se procesaban a menos que el consumidor se iniciara manualmente mediante CLI. Con esta corrección, el consumidor ahora procesa los mensajes como se espera después de que se ejecute cron, lo que garantiza una conversión de pedidos perfecta para los comerciantes B2B que utilizan ActiveMQ.

_AC-17679_

#### Optimización de caché Symfony L2 y compatibilidad con versiones anteriores de caché

Adobe Commerce 2.4.10 ahora proporciona compatibilidad optimizada con la caché Symfony L2 mientras mantiene la implementación existente de caché basada en Zend como predeterminada.

Los comerciantes que deseen utilizar Symfony Cache deben habilitarlo explícitamente y actualizar la configuración de caché requerida específica para la implementación de Symfony L1/L2. Los comerciantes existentes que continúan usando la caché basada en Zend no necesitan hacer ningún cambio en la configuración.

Este enfoque de caché dual proporciona a los comerciantes la flexibilidad de adoptar Symfony Cache en función de sus requisitos, al mismo tiempo que garantiza la compatibilidad con versiones anteriores con configuraciones e implementaciones de caché existentes.

_AC-17865_

### Otros

#### Administración de las subregiones de los países (Estados y provincias)

Los comerciantes ahora pueden administrar las subregiones de país (como estados y provincias) directamente desde la interfaz de administración. Esta nueva función permite a los comerciantes:

- Ver, agregar, editar, desactivar o quitar regiones de cualquier país.
- Haga que las nuevas regiones estén disponibles al instante como opciones desplegables en el cierre de compra, en los formularios de direcciones de clientes y durante la creación de la orden de administración: no se requieren cambios de código.
- Editar nombres para mostrar de la región (incluidos los nombres localizados) y códigos ISO.
- Desactive las regiones a las que hacen referencia los pedidos, las direcciones o las reglas fiscales existentes (lo que garantiza que los datos históricos sigan siendo precisos), al tiempo que evita la eliminación completa de dichas regiones.
- Todas las regiones predefinidas permanecen sin cambios y ahora son visibles y manejables en la nueva interfaz.

Esta función es totalmente compatible con versiones anteriores y garantiza que el comportamiento de las direcciones API y de cara al cliente siga siendo coherente.

_AC-16192_

#### Actualización de predis/predis de 2.x a 3.x

La biblioteca de cliente Redis predis/predis se actualizó de la versión 2.x a la 3.x. Esta actualización de la versión principal se ajusta a los estándares de dependencia más recientes, mejora la compatibilidad y garantiza el mantenimiento a largo plazo.

_AC-17101 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Actualice knockout.js de la versión 3.5.1 a la 3.5.3.

Se ha actualizado la biblioteca knockout.js de la versión 3.5.1 a la 3.5.3. Esta actualización incluye correcciones de errores y mejoras de estabilidad para todos los componentes de la interfaz de usuario mediante enlaces de cobertura en tienda y administración.

_AC-17366 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/de7188da)_

#### Actualizar Varnish a la versión 9 para 2.4.10-alpha1

Adobe Commerce 2.4.10 es compatible con la versión 9.0 de Varnish.

_AC-17972_
