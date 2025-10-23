---
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---
# Notas de la versión de Adobe Commerce (v2.4.9-alpha2)

## Características destacadas en la versión 2.4.9-alpha2

Los siguientes aspectos destacados se aplican a la versión Adobe Commerce 2.4.9-alpha2.

### Marco

#### Agregar compatibilidad con OpenSearch 3

Adobe Commerce 2.4.9 ahora es totalmente compatible con OpenSearch 3.x. Esta actualización permite a los comerciantes beneficiarse de un rendimiento mejorado, seguridad y soporte a largo plazo, manteniendo al mismo tiempo la compatibilidad con versiones anteriores de OpenSearch 2.x.

_AC-11846_

#### Actualización de la versión de Nginx de 1.26 a 1.28

La versión de Nginx utilizada en los entornos de desarrollo y prueba en todas las versiones de Adobe Commerce admitidas actualmente se actualiza de 1.26 a 1.28, alineándose con la última versión estable de Nginx disponible.
Las pruebas de nivel PR ahora se ejecutan con Nginx 1.28, lo que confirma la compatibilidad total y la compatibilidad con todas las versiones de Adobe Commerce.

_AC-14104_

#### Investigue la última versión de jquery-validate

Se ha actualizado la biblioteca de validación de jQuery a la versión 1.21.0 para mejorar las capacidades de validación de formularios, mejorar la experiencia del usuario y garantizar la compatibilidad del explorador moderno en todos los formularios Adobe Commerce en las interfaces de administración y de front-end.

_AC-14403 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Investigue la última versión de jquery-ui

Se ha actualizado la biblioteca de la interfaz de usuario de jQuery a la versión 1.14.1 para mejorar los widgets de la interfaz de usuario, mejorar la accesibilidad y garantizar la compatibilidad moderna del explorador en todos los componentes de la interfaz de administración y front-end de Adobe Commerce.

_AC-14417 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/77c589a6)_

#### Investigue la última versión de less.js

Se ha actualizado el preprocesador CSS Less.js a la versión 4.2.2 para mejorar el rendimiento de la compilación CSS, mejorar la compatibilidad con la sintaxis y modernizar el proceso de compilación de temas en todos los temas de front-end y administración de Adobe Commerce.

_AC-14418 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Investigue la última versión de moment-timezone-with-data.js

Se ha actualizado la biblioteca de zona horaria Moment a la versión 0.5.43 para mejorar las capacidades de administración de zonas horarias, actualizar los datos de zona horaria con los últimos cambios en la base de datos de zonas horarias de IANA y mejorar la precisión del procesamiento de fecha y hora en todas las operaciones internacionales y de zonas horarias múltiples de Adobe Commerce.

_AC-14419 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Investigue la versión más reciente underscore.js

Se ha actualizado la biblioteca de utilidades Underscore.js a la versión 1.13.7 para mejorar las capacidades de programación funcional de JavaScript, mejorar el rendimiento de manipulación de datos y garantizar la compatibilidad moderna del explorador en todos los componentes de interfaz de administración y front-end de Adobe Commerce.

_AC-14420 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/98b2848a)_

#### Migrar de TinyMCE a Hugerte.org

Debido al fin de la compatibilidad con TinyMCE 5 y 6 y a las incompatibilidades de licencia con TinyMCE 7, la implementación actual del editor WYSIWYG de Adobe Commerce se migra de TinyMCE al editor HugeRTE de código abierto (https://hugerte.org/).
Esta migración garantiza que Adobe Commerce siga siendo compatible con las licencias de código abierto, evita las vulnerabilidades conocidas de TinyMCE 6 y ofrece una experiencia de edición moderna y compatible para comerciantes y desarrolladores.

_AC-14568_

#### Agregar compatibilidad total con Valkey 8.x para 2.4.9-alpha2

Adobe Commerce 2.4.9 tiene compatibilidad total con comandos CLI para Valkey, lo que refleja la funcionalidad de Redis existente actualmente. Se ha actualizado la configuración de administración y nube para permitir una configuración de Valkey sin problemas.
Esta actualización garantiza que Adobe Commerce esté preparado para el futuro y tenga un buen rendimiento al admitir Valkey 8.x, lo que ofrece a los comerciantes y desarrolladores una alternativa fiable a Redis a medida que se acerca al final de su vida útil.

_AC-14604_

### Otros

#### Actualizar el servicio de AWS Valkey 8.x para la compilación y prueba de CNS

Actualización del servicio AWS Valkey 8.x para la compilación de CNS

_AC-14470_

#### 2.4.9-alpha2: Mejoras de calidad de los componentes principales de agosto

_AC-14700_

### Seguridad

#### Mejoras de seguridad para 2.4.9-alpha2

_AC-14610_

### Envío

#### Migrar la integración de USPS de las API de Web Tools obsoletas a las nuevas API de RESTful USPS

Para cumplir con el anuncio de USPS de la retirada de las API de herramientas web heredadas antes del 25 de enero de 2026, la integración de Adobe Commerce USPS se migra a las nuevas API de RESTful USPS.

Mejoras clave:

* Compatibilidad con API dual: Los usuarios administradores ahora pueden elegir entre la API heredada de Web Tools y la nueva API de RESTful USPS a través de los ajustes de configuración.
* Actualización de autenticación: se ha implementado OAuth 2.0 para el acceso seguro a la API.
* Formato de datos mejorado: Se ha realizado la transición de XML a JSON para una comunicación más limpia y eficaz.
* Nuevos campos de administración:
   * URL de REST de puerta de enlace (según el modo: Desarrollo o Activo)
   * ID de cliente &amp;amp; Secret
   * Tipo de cuenta, Número de cuenta
   * CRID, MID, código de identificación de Mailer
   * AES/ITN para envíos internacionales
   * Métodos de envío permitidos específicos de REST

Esta migración garantiza que Adobe Commerce siga cumpliendo con los estándares de USPS, mejore la fiabilidad del sistema y las integraciones de envíos futuras para los comerciantes.

_AC-13257_
