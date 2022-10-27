---
source-git-commit: a3fa25993f365a85307db45ef16f68eeb12604bb
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---
# Paquetes de Adobe Commerce

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce utiliza Composer para administrar paquetes PHP.

La variable `composer.json` declara la lista de paquetes, mientras que la variable `composer.lock` almacena una lista completa de los paquetes (una versión completa de cada paquete y sus dependencias) utilizados para construir una instalación de Adobe Commerce o Magento Open Source.

La siguiente documentación de referencia se genera a partir de la variable `composer.lock` y cubre los paquetes requeridos incluidos en Adobe Commerce 2.4.5.

## Dependencias

`magento/product-enterprise-edition 2.4.5` tiene las siguientes dependencias:

```config
colinmollenhour/cache-backend-file: ~1.4.1
colinmollenhour/cache-backend-redis: 1.14.2
colinmollenhour/credis: 1.13.0
colinmollenhour/php-redis-session-abstract: ~1.4.5
composer/composer: ^1.9 || ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.14
guzzlehttp/guzzle: ^7.4.2
laminas/laminas-captcha: ^2.12
laminas/laminas-code: ~4.5.0
laminas/laminas-db: ^2.15.0
laminas/laminas-dependency-plugin: ^2.2.0
laminas/laminas-di: ^3.7.0
laminas/laminas-escaper: ~2.10.0
laminas/laminas-eventmanager: ^3.5.0
laminas/laminas-feed: ^2.17.0
laminas/laminas-http: ^2.15.0
laminas/laminas-json: ^3.3.0
laminas/laminas-mail: ^2.16.0
laminas/laminas-mime: ^2.9.1
laminas/laminas-modulemanager: ^2.11.0
laminas/laminas-mvc: ^3.3.3
laminas/laminas-server: ^2.11.1
laminas/laminas-servicemanager: ^3.11.0
laminas/laminas-soap: ^2.10.0
laminas/laminas-stdlib: ^3.7.1
laminas/laminas-uri: ^2.9.1
laminas/laminas-validator: ^2.17.0
league/flysystem: ~2.4.5
league/flysystem-aws-s3-v3: ^2.4.3
lib-libxml: *
magento/composer: ~1.8.0
magento/composer-dependency-version-audit-plugin: ~0.1
magento/framework-foreign-key: 100.4.4
magento/magento-composer-installer: >=0.3.0
magento/magento2-ee-base: 2.4.5
magento/module-admin-gws: 100.4.5
magento/module-admin-gws-configurable-product: 100.4.2
magento/module-admin-gws-staging: 100.4.2
magento/module-advanced-catalog: 100.4.2
magento/module-advanced-checkout: 100.4.5
magento/module-advanced-rule: 100.4.2
magento/module-advanced-sales-rule: 100.4.2
magento/module-async-order: 100.4.1
magento/module-async-order-graph-ql: 100.4.0
magento/module-aws-s3-customer-custom-attributes: 100.4.2
magento/module-aws-s3-gift-card-import-export: 100.4.2
magento/module-aws-s3-scheduled-import-export: 100.4.2
magento/module-banner: 101.2.5
magento/module-banner-customer-segment: 100.4.3
magento/module-banner-graph-ql: 100.4.1
magento/module-bundle-import-export-staging: 100.4.2
magento/module-bundle-staging: 100.4.5
magento/module-catalog-event: 101.1.4
magento/module-catalog-import-export-staging: 100.4.2
magento/module-catalog-inventory-staging: 100.4.3
magento/module-catalog-permissions: 100.4.5
magento/module-catalog-permissions-graph-ql: 100.4.3
magento/module-catalog-rule-staging: 100.4.5
magento/module-catalog-staging: 100.4.5
magento/module-catalog-staging-graph-ql: 100.4.4
magento/module-catalog-url-rewrite-staging: 100.4.4
magento/module-checkout-address-search: 100.4.4
magento/module-checkout-address-search-gift-registry: 100.4.1
magento/module-checkout-staging: 100.4.4
magento/module-cms-staging: 100.4.5
magento/module-configurable-product-staging: 100.4.4
magento/module-custom-attribute-management: 100.4.4
magento/module-customer-balance: 100.4.5
magento/module-customer-balance-graph-ql: 100.4.2
magento/module-customer-custom-attributes: 100.4.5
magento/module-customer-finance: 100.4.2
magento/module-customer-segment: 102.1.5
magento/module-deferred-total-calculating: 100.4.0
magento/module-downloadable-staging: 100.4.4
magento/module-elasticsearch-catalog-permissions: 100.4.1
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.0
magento/module-enterprise: 100.4.3
magento/module-gift-card: 101.3.5
magento/module-gift-card-account: 101.2.5
magento/module-gift-card-account-graph-ql: 100.4.3
magento/module-gift-card-graph-ql: 100.4.5
magento/module-gift-card-import-export: 100.4.2
magento/module-gift-card-staging: 100.4.2
magento/module-gift-message-staging: 100.4.2
magento/module-gift-registry: 101.2.5
magento/module-gift-registry-graph-ql: 100.4.1
magento/module-gift-wrapping: 101.2.4
magento/module-gift-wrapping-graph-ql: 100.4.2
magento/module-gift-wrapping-staging: 100.4.2
magento/module-google-optimizer-staging: 100.4.2
magento/module-google-tag-manager: 100.4.5
magento/module-grouped-product-staging: 100.4.3
magento/module-invitation: 100.4.4
magento/module-layered-navigation-staging: 100.4.2
magento/module-logging: 101.2.5
magento/module-login-as-customer-logging: 100.4.5
magento/module-login-as-customer-website-restriction: 100.4.3
magento/module-media-content-catalog-staging: 100.4.2
magento/module-msrp-staging: 100.4.3
magento/module-multiple-wishlist: 100.4.5
magento/module-multiple-wishlist-graph-ql: 100.4.1
magento/module-payment-staging: 100.4.2
magento/module-persistent-history: 100.4.2
magento/module-price-permissions: 100.4.1
magento/module-product-video-staging: 100.4.2
magento/module-promotion-permissions: 100.4.2
magento/module-quote-gift-card-options: 100.4.2
magento/module-quote-staging: 100.4.2
magento/module-reminder: 101.2.4
magento/module-remote-storage-commerce: 100.4.1
magento/module-resource-connections: 100.4.2
magento/module-review-staging: 100.4.2
magento/module-reward: 101.2.5
magento/module-reward-graph-ql: 100.4.4
magento/module-reward-staging: 100.4.2
magento/module-rma: 101.2.5
magento/module-rma-graph-ql: 100.4.4
magento/module-rma-staging: 100.4.2
magento/module-sales-archive: 101.0.3
magento/module-sales-rule-staging: 100.4.4
magento/module-scalable-checkout: 100.4.4
magento/module-scalable-inventory: 100.4.3
magento/module-scalable-oms: 100.4.3
magento/module-scheduled-import-export: 101.2.5
magento/module-search-staging: 100.4.3
magento/module-staging: 101.2.5
magento/module-staging-graph-ql: 100.4.2
magento/module-support: 101.2.4
magento/module-swat: 100.4.3
magento/module-target-rule: 101.2.5
magento/module-target-rule-graph-ql: 100.4.2
magento/module-versions-cms: 101.2.5
magento/module-versions-cms-page-cache: 100.4.1
magento/module-versions-cms-url-rewrite: 100.4.3
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.1
magento/module-visual-merchandiser: 100.4.5
magento/module-website-restriction: 100.4.4
magento/module-weee-staging: 100.4.2
magento/module-wishlist-gift-card: 100.4.1
magento/module-wishlist-gift-card-graph-ql: 100.4.1
magento/page-builder-commerce: 1.7.2
magento/product-community-edition: 2.4.5
magento/security-package-ee: 1.0.0
magento/theme-adminhtml-spectrum: 100.4.0
magento/zendframework1: ~1.15.0
monolog/monolog: ^2.7
pelago/emogrifier: ^6.0.0
php: ~7.4.0||~8.1.0
php-amqplib/php-amqplib: ~3.2.0
phpseclib/mcrypt_compat: ~2.0.2
phpseclib/phpseclib: ~3.0.13
ramsey/uuid: ~4.2.0
symfony/console: ~4.4.0
symfony/process: ~4.4.0
tedivm/jshrink: ~1.4.0
tubalmartin/cssmin: 4.1.1
web-token/jwt-framework: ^v2.2.7
webonyx/graphql-php: ~14.11.6
wikimedia/less.php: ^3.0.0
```

## Licencias de terceros

### Apache-2.0, LGPL-2.1-only

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>biblioteca</td>
    <td>Cliente PHP para Elasticsearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de API de Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>biblioteca</td>
    <td>Tiempo de ejecución común de AWS para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>biblioteca</td>
    <td>SDK de AWS para PHP: Utilice Amazon Web Service en su proyecto PHP</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>metapackage</td>
    <td>Magento del Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>biblioteca</td>
    <td>Puerto PHP de la versión Javascript de LESS http://lesscss.org (originalmente mantenido por Josh Schmidt)</td>
  </tr>
  </tbody>
</table>

### BSD-2-Clause

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>biblioteca</td>
    <td>BaconQrCode es un generador de código QR para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/beberlei/assert.git">beberlei/assert</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de aserciones delgada para la validación de entradas en modelos de negocio.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>biblioteca</td>
    <td>Implementación de enumeración de PHP 7.1</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>biblioteca</td>
    <td>Herramienta para escribir archivos de forma segura, para evitar condiciones de carrera</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend file</a>
    </td>
    <td>magento-module</td>
    <td>El back-end de archivo stock Zend_Cache_Backend_File tiene un rendimiento extremadamente pobre para la limpieza mediante etiquetas, lo que hace que sea inutilizable a medida que aumenta el número de elementos en caché. Este servidor hace muchos cambios, lo que resulta en un gran aumento del rendimiento, especialmente para la limpieza de etiquetas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>El back-end de Zend_Cache mediante Redis con compatibilidad total con etiquetas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>biblioteca</td>
    <td>Un controlador de sesión basado en Redis con bloqueo optimista</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de clientes para reCAPTCHA, un servicio gratuito que protege los sitios web de spam y abuso.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>biblioteca</td>
    <td>Genere y valide CAPTCHA utilizando filtros, imágenes, ReCaptcha y mucho más</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">código laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Extensiones a la API de reflejo de PHP, análisis de código estático y generación de código</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>biblioteca</td>
    <td>proporciona una interfaz de usuario basada en una propiedad de objeto anidada para acceder a estos datos de configuración dentro del código de la aplicación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>biblioteca</td>
    <td>Capas de abstracción de bases de datos, abstracción de SQL, abstracción de conjuntos de resultados e implementaciones RowDataGateway y TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-dependency-plugin.git">laminas/laminas-dependencia-plugin</a>
    </td>
    <td>composer-plugin</td>
    <td>Reemplace los paquetes zendframework y zfcampus con sus equivalentes del proyecto Laminas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>biblioteca</td>
    <td>Inyección automatizada de dependencias para contenedores PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escapador</a>
    </td>
    <td>biblioteca</td>
    <td>Escape segura y segura de HTML, atributos de HTML, JavaScript, CSS y direcciones URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>biblioteca</td>
    <td>Déclencheur y escucha eventos dentro de una aplicación PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-pienso</a>
    </td>
    <td>biblioteca</td>
    <td>proporciona funcionalidad para crear y consumir fuentes RSS y Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona una interfaz fácil para realizar solicitudes de protocolo de transferencia de hipertexto (HTTP)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>biblioteca</td>
    <td>proporciona métodos de conveniencia para serializar el PHP nativo a JSON y descodificar el JSON a PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">cargador laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Estrategias de carga automática y de complemento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona una funcionalidad generalizada para componer y enviar mensajes de correo electrónico de varias partes compatibles con el texto y MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>biblioteca</td>
    <td>Crear y analizar mensajes y partes MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>biblioteca</td>
    <td>Sistema de aplicación modular para aplicaciones laminas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>biblioteca</td>
    <td>Capa MVC impulsada por eventos de Laminas, incluyendo aplicaciones MVC, controladores y complementos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>biblioteca</td>
    <td>Ajuste OOP para el servicio web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>biblioteca</td>
    <td>Sistema de enrutamiento flexible para aplicaciones HTTP y de consola</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>biblioteca</td>
    <td>Crear servidores RPC basados en reflejo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>biblioteca</td>
    <td>Contenedor de inyección de dependencia impulsado por fábrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">sesiones laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz orientada a objetos para sesiones y almacenamiento PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminas/laminas-soap</a>
    </td>
    <td>biblioteca</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>biblioteca</td>
    <td>Extensiones SPL, utilidades de matriz, controladores de errores y más</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>biblioteca</td>
    <td>Crear FIGlets y tablas basadas en texto</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>biblioteca</td>
    <td>Un componente que ayuda a manipular y validar los identificadores uniformes de recursos (URI)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validador</a>
    </td>
    <td>biblioteca</td>
    <td>Clases de validación para una amplia gama de dominios y la capacidad de encadenar a los validadores para crear criterios de validación complejos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/vista laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Capa de vista flexible que admite y proporciona múltiples capas de vista, asistentes y mucho más</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-zendframework-bridge.git">laminas/laminas-zendframework-bridge</a>
    </td>
    <td>biblioteca</td>
    <td>Alias nombres de clase ZF heredados a equivalentes del proyecto Laminas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>biblioteca</td>
    <td>Un analizador de PHP escrito en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshink</a>
    </td>
    <td>biblioteca</td>
    <td>Minificador Javascript incorporado en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>biblioteca</td>
    <td>Puerto PHP del compresor YUI CSS</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1-o posterior

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>biblioteca</td>
    <td>Filtro HTML compatible con normas escrito en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>biblioteca</td>
    <td>Antes videlalvaro/php-amqplib.  Esta biblioteca es una implementación PHP pura del protocolo AMQP. Se ha probado contra RabbitMQ.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">braintree/braintree_php</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de cliente PHP del Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">ladrillo/matemáticas</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca aritmética de precisión arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>biblioteca</td>
    <td>Una poderosa alternativa a var_export(), que puede exportar cierres y objetos sin __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">quristian-riesen/base32</a>
    </td>
    <td>biblioteca</td>
    <td>Codificador/decodificador Base32 según RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>biblioteca</td>
    <td>Credis es una interfaz ligera al almacén de clave-valor de Redis que ajusta la biblioteca phpredis cuando está disponible para un mejor rendimiento.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">compositor/ca-bundle</a>
    </td>
    <td>biblioteca</td>
    <td>Permite encontrar una ruta al paquete de CA del sistema e incluye una alternativa al paquete de Mozilla CA.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">compositor/compositor</a>
    </td>
    <td>biblioteca</td>
    <td>Composer le ayuda a declarar, administrar e instalar dependencias de proyectos PHP. Garantiza que tenga la pila correcta en todas partes.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">compositor/minificador de metadatos</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de utilidades pequeña que gestiona la minificación y expansión de metadatos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">compositor/pcre</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de envoltura PCRE que ofrece reemplazos preg_* seguros para el tipo.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">compositor/semver</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de seminarios que ofrece utilidades, análisis y validación de restricciones de versión.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">compositor/spdx-license</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de validación y lista de licencias SPDX.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>biblioteca</td>
    <td>Reinicia un proceso sin Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>biblioteca</td>
    <td>Código QR de Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestrems</a>
    </td>
    <td>biblioteca</td>
    <td>Bifurcación de guzzle/streams (abandonados) que se utilizará con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>biblioteca</td>
    <td>Bifurcación de guzzle/RingPHP (abandonado) que se utilizará con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/fgrosse/PHPASN1.git">fgrosse/phpasn1</a>
    </td>
    <td>biblioteca</td>
    <td>Un marco de PHP que le permite codificar y descodificar estructuras ASN.1 arbitrarias usando las Reglas de Codificación ITU-T X.690.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>biblioteca</td>
    <td>Guzzle es una biblioteca cliente HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/rondas</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de promesas de Guzzle</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>biblioteca</td>
    <td>Implementación de mensajes PSR-7 que también proporciona métodos de utilidad comunes</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>biblioteca</td>
    <td>Una biblioteca para validar un esquema json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">liga/sistema aéreo</a>
    </td>
    <td>biblioteca</td>
    <td>Extracción de almacenamiento de archivos para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">liga/flysystem-aws-s3-v3</a>
    </td>
    <td>biblioteca</td>
    <td>Adaptador de sistema de archivos AWS S3 para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">detección de tipo liga/mime</a>
    </td>
    <td>biblioteca</td>
    <td>Detección de tipo mime para sistema volátil</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monólogo/monólogo</a>
    </td>
    <td>biblioteca</td>
    <td>Envía los registros a archivos, sockets, bandejas de entrada, bases de datos y diversos servicios web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>biblioteca</td>
    <td>Especificar declarativamente cómo extraer elementos de un documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constante_time_encoding</a>
    </td>
    <td>biblioteca</td>
    <td>Implementaciones en tiempo constante de la codificación RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>biblioteca</td>
    <td>PHP 5.x polyfill para random_bytes() y random_int() de PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>biblioteca</td>
    <td>Convierte los estilos CSS en atributos de estilo en línea en el código del HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>biblioteca</td>
    <td>Convertir selectores CSS en consultas XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>biblioteca</td>
    <td>La API DOM moderna para proyectos PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>biblioteca</td>
    <td>PHP 5.x-8.x polyfill para la extensión mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>biblioteca</td>
    <td>PHP Secure Communications Library: implementaciones Pure-PHP de RSA, AES, SSH2, SFTP, X.509, etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/contenedor</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz de contenedor común (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaces estándar para la gestión de eventos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaces comunes para las fábricas de mensajes HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http message</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para mensajes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para el registro de bibliotecas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>biblioteca</td>
    <td>Un polyfill para encabezados getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collection</a>
    </td>
    <td>biblioteca</td>
    <td>Una biblioteca PHP para representar y manipular colecciones.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>biblioteca</td>
    <td>Una biblioteca PHP para generar y trabajar con identificadores únicos universales (UUID).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">Reacción/promesa</a>
    </td>
    <td>biblioteca</td>
    <td>Una implementación ligera de CommonJS Promises/A para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/sabberworm/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>biblioteca</td>
    <td>Analizador para archivos CSS escritos en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>biblioteca</td>
    <td>Linter JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>biblioteca</td>
    <td>Utilidades de formato de archivo PHAR, para cuando PHP te carga</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>biblioteca</td>
    <td>AES Key Wrap para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/base64url.git">spomky-labs/base64url</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca PHP de codificación/descodificación segura de URL base 64</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>biblioteca</td>
    <td>Una biblioteca PHP para generar contraseñas únicas de acuerdo con RFC 4226 (Algoritmo HOTP) y RFC 6238 (Algoritmo TOTP) y compatible con Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>biblioteca</td>
    <td>Ayuda a encontrar, cargar, combinar, rellenar automáticamente y validar valores de configuración de cualquier tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>biblioteca</td>
    <td>Facilita la creación de interfaces de línea de comandos hermosas y comprobables</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>biblioteca</td>
    <td>Convierte los selectores CSS en expresiones XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/debug.git">symfony/debug</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona herramientas para facilitar la depuración del código PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependencia-inyectable</a>
    </td>
    <td>biblioteca</td>
    <td>Permite estandarizar y centralizar la forma en que se construyen los objetos en la aplicación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/deprecation-Contracts</a>
    </td>
    <td>biblioteca</td>
    <td>Una función genérica y una convención para almacenar en déclencheur los avisos de desaprobación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona herramientas para administrar errores y facilitar la depuración del código PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona herramientas que permiten a los componentes de la aplicación comunicarse entre sí al enviar eventos y escucharlos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-Contracts</a>
    </td>
    <td>biblioteca</td>
    <td>abstracciones genéricas relacionadas con el evento de envío</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona utilidades básicas para el sistema de archivos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>biblioteca</td>
    <td>Encuentra archivos y directorios a través de una interfaz intuitiva y fluida</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-Contracts</a>
    </td>
    <td>biblioteca</td>
    <td>abstracciones genéricas relacionadas con clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>biblioteca</td>
    <td>Define una capa orientada a objetos para la especificación HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona un proceso estructurado para convertir una solicitud en una respuesta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-ctype</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para funciones ctype</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para las funciones idn_to_ascii e idn_to_utf8 de intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para la clase Normalizer de intl y funciones relacionadas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para la extensión Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill que soporta algunas características de PHP 7.2+ para reducir las versiones de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill que soporta algunas características de PHP 7.3+ para reducir las versiones de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill que soporta algunas características de PHP 8.0+ para reducir las versiones de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill que soporta algunas características de PHP 8.1+ para reducir las versiones de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfony/process</a>
    </td>
    <td>biblioteca</td>
    <td>Ejecuta comandos en subprocesos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/service-Contracts</a>
    </td>
    <td>biblioteca</td>
    <td>abstracciones genéricas relacionadas con los servicios de escritura</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona mecanismos para recorrer cualquier variable PHP arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thecodingmachine/safe.git">máquina de documentos/caja fuerte</a>
    </td>
    <td>biblioteca</td>
    <td>Funciones principales de PHP que generan excepciones en lugar de devolver FALSE en caso de error</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundle</td>
    <td>Biblioteca de firma y cifrado de objetos JSON para PHP y Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>biblioteca</td>
    <td>Afirmaciones para validar la entrada/salida del método con mensajes de error agradables.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>biblioteca</td>
    <td>Puerto PHP de la implementación de referencia de GraphQL</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      temando/module-Shipping-remover
    </td>
    <td>magento2-module</td>
    <td>Elimina la extensión de envío multioperador de Temando del Magento 2</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      temando/module-Shipping
    </td>
    <td>metapackage</td>
    <td>Extensión de envío multioperador Temando para el Magento 2</td>
  </tr>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cborencode</a>
    </td>
    <td>biblioteca</td>
    <td>Codificador CBOR para PHP</td>
  </tr>
  </tbody>
</table>

### Titular

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### propietario

<table>
  <thead>
    <tr>
      <th>Nombre</th>
      <th>Tipo</th>
      <th>Descripción</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-braintree-core
    </td>
    <td>magento2-module</td>
    <td>Bifurcación del módulo Braintree Magento 2.2.0 de Gene Commerce para PayPal.</td>
  </tr>
  </tbody>
</table>
