---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Aspectos destacados de Magento Open Source (versión 2.4.9-beta1)

## Aspectos destacados en la versión 2.4.9-beta1

Los siguientes aspectos destacados se aplican a la versión Magento Open Source 2.4.9-beta1.

### API

#### Agregar la posibilidad de mantener la herencia de la galería de productos en la API de REST al actualizar un producto en el nivel de vista de tienda

La actualización de un producto mediante la API de REST en un ámbito de tienda ya no impide que las imágenes y los vídeos de producto hereden cambios del ámbito global si media_gallery_entries se omite en la carga útil o se establece en NULL para evitar cualquier cambio en la galería de productos en ese ámbito. Además, ahora es posible restaurar la herencia de ámbito para imágenes y vídeo de productos mediante la API de REST estableciendo el campo correspondiente en NULL

_ACP2E-4358 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Marco

#### Investigue la última versión principal de web-token/jwt-framework

Como parte del proceso continuo de revisión de la seguridad, evaluamos la última versión del marco JWT para garantizar la futura compatibilidad y mantener estándares de seguridad sólidos. Esta versión no afecta a la funcionalidad existente.

_AC-13209 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/2bac8114) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/09b36ebb) - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/33b81f28)_

#### Reemplace carlos-mg89/oauth con funciones nativas de PHP

Se ha reemplazado la biblioteca carlos-mg89/oauth de terceros con funciones OAuth de PHP nativas para mejorar la seguridad, reducir las dependencias externas y mejorar la estabilidad de la plataforma.

_AC-14075 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/7b8064f7)_

#### Investigue la versión más reciente de chart.js

Se ha actualizado la biblioteca de gráficos JavaScript de Chart.js a la versión más reciente (4.4.8) para mejorar el rendimiento de procesamiento de gráficos, mejorar las capacidades visuales y abordar las vulnerabilidades de seguridad en el tablero de administración y en los módulos de informes.

_AC-14304 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/768b4442)_

#### Investigue la última versión de jquery/uppy y uppy

Se ha actualizado la biblioteca de carga de archivos de Uppy a la versión 4.13.4 para mejorar las capacidades de carga de archivos, mejorar la experiencia del usuario y resolver las vulnerabilidades de seguridad en la administración de archivos en la interfaz de administración de Adobe Commerce y en los componentes de front-end.

_AC-14307 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/eb491c05)_

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

#### Actualice allure-framework/allure-phpunit versión a 3 y elimine la dependencia nativa en 2.4.9-alpha1

En Adobe Commerce 2.4.9, la dependencia allure-framework/allure-phpunit se ha actualizado a la versión principal 3, que agrega compatibilidad con PHP 8.4, PHP 8.5 y moderniza nuestro grupo de informes de pruebas basado en Allure. La dependencia nativa que anteriormente requerían las versiones anteriores de Allure PHPUnit se ha eliminado cuando corresponde, lo que simplifica la configuración y el mantenimiento.

_AC-14548 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/87b8b34e)_

#### Actualice la dependencia de chart.js a la versión más reciente

La dependencia de chart.js se ha actualizado a la versión 4.5.0 más reciente

_AC-15133 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Añade soporte oficial para Symfony 7.4 LTS y PHP 8.5 en Adobe Commerce 2.4.9

Como parte de las actualizaciones de la plataforma Adobe Commerce 2.4.9, todas las dependencias de Symfony utilizadas por el paquete magento/composer se han actualizado a las últimas versiones de Symfony LTS 7.4. Esto alinea las herramientas de Compositor de Commerce con la línea actual de Symfony LTS y elimina las restricciones de dependencia anteriores relacionadas con versiones de Symfony anteriores. Además, todas las clases personalizadas que amplían las clases principales de Symfony han actualizado las declaraciones de tipos y las firmas de métodos alineadas con los requisitos más recientes de Symfony antes de actualizar a Adobe Commerce 2.4.9. Esto evitará problemas de compatibilidad y garantizará una transición sin problemas a los componentes del marco actualizado.

_AC-15170 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/c127d10b)_

### Otros

#### Captcha/reCaptha no funciona para API/GraphQl

En Adobe Commerce 2.4.9, cuando CAPTCHA (o reCAPTCHA) está habilitado para el formulario Crear cuenta, ahora se aplica la misma validación CAPTCHA para la creación de cuentas de cliente mediante las API de REST y GraphQL.

_AC-16245 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/fd7f30ee)_

### Seguridad

#### Mejora del rendimiento de las solicitudes asíncronas/masivas

Corrija la degradación del rendimiento en los extremos web asincrónicos masivos introducidos después del parche de seguridad APSB25-08, lo que da como resultado un aumento de los tiempos de ejecución.

_AC-14078 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/9a7352b7)_

#### Solo es necesario habilitar un proveedor 2FA para cada usuario

Ahora, los usuarios administradores solo tienen que configurar uno de los proveedores 2FA habilitados del comerciante (por ejemplo, Google Authenticator o U2F) para acceder al panel Administración. Se pueden configurar proveedores habilitados adicionales más adelante según sea necesario. Anteriormente, cuando se habilitaban varios proveedores de 2FA (por ejemplo, Google Authenticator y U2F), todos los usuarios administradores tenían que configurar todos los proveedores habilitados para poder iniciar sesión. Esto creó fricción para los usuarios que no tenían acceso a todos los factores (como una clave de hardware para U2F).

_AC-8253 - [Contribución de código de GitHub](https://github.com/magento/security-package/commit/71e7936b)_

### Ensayo y previsualización

#### [Solicitud de característica] Vista previa de ensayo de contenido en la vista móvil

La función de vista previa de ensayo del panel de administración ahora permite que las vistas previas de dispositivos móviles simulados por el explorador se representen con precisión, lo que proporciona una representación visual de cómo aparecerá la actualización de ensayo en un dispositivo móvil.

_ACP2E-3397 - [Contribución de código de GitHub](https://github.com/magento/magento2/commit/520f9e30)_
