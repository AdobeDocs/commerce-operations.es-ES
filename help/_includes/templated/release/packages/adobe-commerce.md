---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '1996'
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

Adobe Commerce usa Composer para administrar paquetes PHP.

El archivo `composer.json` declara la lista de paquetes, mientras que el archivo `composer.lock` almacena una lista completa de los paquetes (una versión completa de cada paquete y sus dependencias) utilizados para generar una instalación de Adobe Commerce.

La siguiente documentación de referencia se genera a partir del archivo `composer.lock` y cubre los paquetes necesarios incluidos en Adobe Commerce 2.4.7-p1.

## Dependencias

`magento/product-enterprise-edition 2.4.7-p1` tiene las dependencias siguientes:

```config
adobe-commerce/extensions-metapackage: ~2.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ~1.5.3
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
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
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.17
laminas/laminas-code: ^4.13
laminas/laminas-db: ^2.19
laminas/laminas-di: ^3.13
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-file: ^2.13
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-oauth: ^2.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.16
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.10.0-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework-foreign-key: 100.4.6
magento/magento-composer-installer: >=0.4.0
magento/magento2-ee-base: 2.4.7-p1
magento/module-admin-gws: 100.4.7
magento/module-admin-gws-configurable-product: 100.4.4
magento/module-admin-gws-staging: 100.4.4
magento/module-advanced-catalog: 100.4.4
magento/module-advanced-checkout: 100.4.7
magento/module-advanced-rule: 100.4.4
magento/module-advanced-sales-rule: 100.4.4
magento/module-application-server: 100.4.0
magento/module-application-server-new-relic: 100.4.0
magento/module-application-server-performance-monitor: 100.4.0
magento/module-application-server-state-monitor: 100.4.0
magento/module-application-server-state-monitor-graph-ql: 100.4.0
magento/module-async-order: 100.4.3
magento/module-async-order-graph-ql: 100.4.2
magento/module-aws-s3-customer-custom-attributes: 100.4.4
magento/module-aws-s3-gift-card-import-export: 100.4.4
magento/module-aws-s3-scheduled-import-export: 100.4.4
magento/module-banner: 101.2.7
magento/module-banner-customer-segment: 100.4.5
magento/module-banner-graph-ql: 100.4.3
magento/module-banner-staging: 100.4.1
magento/module-bundle-import-export-staging: 100.4.4
magento/module-bundle-staging: 100.4.7
magento/module-catalog-event: 101.1.6
magento/module-catalog-import-export-staging: 100.4.4
magento/module-catalog-inventory-staging: 100.4.5
magento/module-catalog-permissions: 100.4.7
magento/module-catalog-permissions-graph-ql: 100.4.5
magento/module-catalog-rule-staging: 100.4.7
magento/module-catalog-staging: 100.4.7
magento/module-catalog-staging-graph-ql: 100.4.6
magento/module-catalog-url-rewrite-staging: 100.4.6-p1
magento/module-checkout-address-search: 100.4.6
magento/module-checkout-address-search-gift-registry: 100.4.3
magento/module-checkout-staging: 100.4.6
magento/module-cms-staging: 100.4.7
magento/module-configurable-product-staging: 100.4.6
magento/module-custom-attribute-management: 100.4.6
magento/module-customer-balance: 100.4.7
magento/module-customer-balance-graph-ql: 100.4.4
magento/module-customer-custom-attributes: 100.4.7
magento/module-customer-custom-attributes-graph-ql: 100.4.0
magento/module-customer-finance: 100.4.4
magento/module-customer-segment: 102.1.7
magento/module-customer-segment-graph-ql: 100.4.0
magento/module-deferred-total-calculating: 100.4.2
magento/module-downloadable-staging: 100.4.6
magento/module-elasticsearch-catalog-permissions: 100.4.3
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.2
magento/module-enterprise: 100.4.5
magento/module-gift-card: 101.3.7
magento/module-gift-card-account: 101.2.7
magento/module-gift-card-account-graph-ql: 100.4.5
magento/module-gift-card-graph-ql: 100.4.7
magento/module-gift-card-import-export: 100.4.4
magento/module-gift-card-staging: 100.4.4
magento/module-gift-message-staging: 100.4.4
magento/module-gift-registry: 101.2.7
magento/module-gift-registry-graph-ql: 100.4.3
magento/module-gift-wrapping: 101.2.6
magento/module-gift-wrapping-graph-ql: 100.4.4
magento/module-gift-wrapping-staging: 100.4.4
magento/module-google-optimizer-staging: 100.4.4
magento/module-google-tag-manager: 100.4.7
magento/module-grouped-product-staging: 100.4.5
magento/module-import-csv: 100.4.1
magento/module-import-csv-api: 100.4.1
magento/module-import-json: 100.4.0
magento/module-import-json-api: 100.4.0
magento/module-invitation: 100.4.6
magento/module-layered-navigation-staging: 100.4.4
magento/module-logging: 101.2.7
magento/module-login-as-customer-logging: 100.4.7
magento/module-login-as-customer-website-restriction: 100.4.5
magento/module-media-content-catalog-staging: 100.4.4
magento/module-msrp-staging: 100.4.5
magento/module-multicoupon: 100.4.0
magento/module-multicoupon-graph-ql: 100.4.0
magento/module-multicoupon-ui: 100.4.0
magento/module-multiple-wishlist: 100.4.7
magento/module-multiple-wishlist-graph-ql: 100.4.3
magento/module-payment-staging: 100.4.4
magento/module-persistent-history: 100.4.4
magento/module-price-permissions: 100.4.3
magento/module-product-video-staging: 100.4.4
magento/module-promotion-permissions: 100.4.4
magento/module-quote-commerce-graph-ql: 100.4.0
magento/module-quote-gift-card-options: 100.4.4
magento/module-quote-staging: 100.4.4
magento/module-reminder: 101.2.6
magento/module-remote-storage-commerce: 100.4.3
magento/module-resource-connections: 100.4.4
magento/module-review-staging: 100.4.4
magento/module-reward: 101.2.7
magento/module-reward-graph-ql: 100.4.6
magento/module-reward-staging: 100.4.4
magento/module-rma: 101.2.7
magento/module-rma-graph-ql: 100.4.6-p1
magento/module-rma-staging: 100.4.4
magento/module-sales-archive: 101.0.5
magento/module-sales-rule-staging: 100.4.6
magento/module-scalable-checkout: 100.4.6
magento/module-scalable-inventory: 100.4.5
magento/module-scalable-oms: 100.4.5
magento/module-scheduled-import-export: 101.2.7
magento/module-search-staging: 100.4.5
magento/module-staging: 101.2.7
magento/module-staging-graph-ql: 100.4.4
magento/module-support: 101.2.6
magento/module-swat: 100.4.5
magento/module-target-rule: 101.2.7
magento/module-target-rule-graph-ql: 100.4.4
magento/module-versions-cms: 101.2.7
magento/module-versions-cms-page-cache: 100.4.3
magento/module-versions-cms-url-rewrite: 100.4.5
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.3
magento/module-visual-merchandiser: 100.4.7
magento/module-website-restriction: 100.4.6
magento/module-weee-staging: 100.4.4
magento/module-wishlist-gift-card: 100.4.3
magento/module-wishlist-gift-card-graph-ql: 100.4.3
magento/page-builder-commerce: 1.7.4-p1
magento/product-community-edition: 2.4.7-p1
magento/security-package-ee: 1.0.2-p1
magento/theme-adminhtml-spectrum: 100.4.2
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0||~8.3.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
```

## Licencias de terceros

### Solo Apache-2.0, LGPL-2.1

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
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">opensearch-project/opensearch-php</a>
    </td>
    <td>biblioteca</td>
    <td>Cliente PHP para OpenSearch</td>
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
    <td>Common Runtime de AWS para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>biblioteca</td>
    <td>AWS SDK para PHP: Utilice Amazon Web Service en su proyecto PHP</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>metapaquete</td>
    <td>Magento Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>biblioteca</td>
    <td>Puerto PHP del procesador LESS</td>
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
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>biblioteca</td>
    <td>Implementación de enumeración en PHP 7.1</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmollenhour/cache-backend-file</a>
    </td>
    <td>magento-module</td>
    <td>El back-end Zend_Cache_Backend_File de stock tiene un rendimiento extremadamente bajo para la limpieza por etiquetas, lo que hace que no se pueda utilizar a medida que aumenta el número de elementos en caché. Este servidor realiza muchos cambios que mejoran enormemente el rendimiento, especialmente en la limpieza de etiquetas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>biblioteca</td>
    <td>Controlador de sesión basado en Redis con bloqueo optimista</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">firebase/php-jwt</a>
    </td>
    <td>biblioteca</td>
    <td>Una sencilla biblioteca para codificar y descodificar tokens web JSON (JWT) en PHP. Debe ajustarse a la especificación actual.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de cliente para reCAPTCHA, un servicio gratuito que protege los sitios web del correo no deseado y del uso indebido.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>biblioteca</td>
    <td>Genere y valide CAPTCHA con miniprogramas, imágenes, ReCaptcha y más</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">código laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Extensiones a la API de PHP Reflection, escaneo de código estático y generación de código</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>biblioteca</td>
    <td>proporciona una interfaz de usuario basada en la propiedad de objeto anidada para acceder a estos datos de configuración dentro del código de la aplicación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>biblioteca</td>
    <td>Herramientas criptográficas sólidas y hash de contraseñas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>biblioteca</td>
    <td>Capa de abstracción de base de datos, abstracción de SQL, abstracción de conjunto de resultados e implementaciones RowDataGateway y TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>biblioteca</td>
    <td>Inyección de dependencia automatizada para contenedores de PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escaper</a>
    </td>
    <td>biblioteca</td>
    <td>Escape de forma segura del HTML, los atributos del HTML, JavaScript, CSS y direcciones URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>biblioteca</td>
    <td>Déclencheur y escucha de eventos dentro de una aplicación PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/laminas-feed</a>
    </td>
    <td>biblioteca</td>
    <td>proporciona funcionalidad para crear y consumir fuentes RSS y Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">archivo laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Localizar archivos de clase PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">filtro laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Filtrar y normalizar datos y archivos mediante programación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona una interfaz sencilla para realizar solicitudes HTTP (Protocolo de transferencia de hipertexto)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>biblioteca</td>
    <td>Proporcione traducciones para la aplicación y filtre y valide valores internacionalizados</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>biblioteca</td>
    <td>proporciona métodos de conveniencia para serializar PHP nativo en JSON y descodificar JSON en PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminas/laminas-loader</a>
    </td>
    <td>biblioteca</td>
    <td>Estrategias de carga automática y de complementos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona funcionalidad generalizada para componer y enviar mensajes de correo electrónico de varias partes compatibles con MIME y texto</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>biblioteca</td>
    <td>Cree números pseudoaleatorios criptográficamente seguros y administre números enteros grandes</td>
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
    <td>Capa de MVC impulsada por eventos de Laminas, que incluye aplicaciones, controladores y complementos de MVC</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>biblioteca</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona una implementación de lista de control de acceso (ACL) ligera y flexible para la administración de privilegios</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>biblioteca</td>
    <td>Envoltorio OOP para el servicio web ReCaptcha</td>
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
      <a href="https://github.com/laminas/laminas-server.git">servidor laminas/laminas</a>
    </td>
    <td>biblioteca</td>
    <td>Crear servidores RPC basados en reflexión</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>biblioteca</td>
    <td>Contenedor de inyección de dependencia de fábrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-session</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz orientada a objetos para sesiones y almacenamiento de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">jabón laminas/laminas</a>
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
    <td>Componente que ayuda a manipular y validar los identificadores uniformes de recursos (URI)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>biblioteca</td>
    <td>Clases de validación para una amplia gama de dominios y la capacidad de encadenar validadores para crear criterios de validación complejos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminas-view</a>
    </td>
    <td>biblioteca</td>
    <td>Capa de vista flexible que admite y proporciona varias capas de vista, ayuda, etc</td>
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
      <a href="https://github.com/tedious/JShrink.git">tedivm/jshrink</a>
    </td>
    <td>biblioteca</td>
    <td>Minifier Javascript integrado en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>biblioteca</td>
    <td>Un puerto PHP del compresor CSS YUI</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause-Modification

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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>Backend_Cache usando Redis con soporte total para etiquetas.</td>
  </tr>
  </tbody>
</table>

### ISC

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
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/sodio_compat</a>
    </td>
    <td>biblioteca</td>
    <td>Implementación Pure PHP de libsodio; utiliza la extensión PHP si existe</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1 o posterior

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
    <td>Filtro de HTML compatible con estándares escrito en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>biblioteca</td>
    <td>Anteriormente videlalvaro/php-amqplib.  Esta biblioteca es una implementación PHP pura del protocolo AMQP. Ha sido probado contra RabbitMQ.</td>
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
    <td>Biblioteca de cliente de Braintree PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">brick/math</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca aritmética de precisión arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">brick/varexporter</a>
    </td>
    <td>biblioteca</td>
    <td>Una alternativa potente a var_export(), que puede exportar cierres y objetos sin __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>biblioteca</td>
    <td>Codificador/decodificador Base32 según RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmollenhour/credis</a>
    </td>
    <td>biblioteca</td>
    <td>Credis es una interfaz ligera para el almacén de valor clave de Redis que ajusta la biblioteca phpredis cuando está disponible para obtener un mejor rendimiento.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">compositor/ca-paquete</a>
    </td>
    <td>biblioteca</td>
    <td>Le permite encontrar una ruta al paquete de CA del sistema e incluye una alternativa al paquete de CA de Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">compositor/generador de mapas de clase</a>
    </td>
    <td>biblioteca</td>
    <td>Utilidades para escanear código PHP y generar mapas de clase.</td>
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
    <td>Pequeña biblioteca de utilidades que gestiona la minificación y expansión de metadatos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">compositor/pcre</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de envoltorio PCRE que ofrece reemplazos preg_* seguros para tipos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">compositor/servidor</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de servidor que ofrece utilidades, análisis de restricción de versión y validación.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">licencias de composición/spdx</a>
    </td>
    <td>biblioteca</td>
    <td>Lista de licencias SPDX y biblioteca de validación.</td>
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
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>biblioteca</td>
    <td>Bifurcación de guzzle/arroyos (abandonada) para usar con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>biblioteca</td>
    <td>Tenedor de guzzle/RingPHP (abandonado) para usar con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp/guzzle</a>
    </td>
    <td>biblioteca</td>
    <td>Guzzle es una biblioteca de cliente HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp/promise</a>
    </td>
    <td>biblioteca</td>
    <td>Guzzle promete biblioteca</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>biblioteca</td>
    <td>Implementación de mensaje PSR-7 que también proporciona métodos de utilidad comunes</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>biblioteca</td>
    <td>Una biblioteca para validar un esquema json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">liga/sistema de archivos</a>
    </td>
    <td>biblioteca</td>
    <td>Abstracción de almacenamiento de archivos para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">league/flysystem-aws-s3-v3</a>
    </td>
    <td>biblioteca</td>
    <td>Adaptador del sistema de archivos AWS S3 para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">league/mime-type-discovery</a>
    </td>
    <td>biblioteca</td>
    <td>Detección de tipo MIME para Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monólogo/monólogo</a>
    </td>
    <td>biblioteca</td>
    <td>Envía sus registros a archivos, sockets, bandejas de entrada, bases de datos y diversos servicios web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>biblioteca</td>
    <td>Especificar mediante declaración cómo extraer elementos de un documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constant_time_encoding</a>
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
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrificador</a>
    </td>
    <td>biblioteca</td>
    <td>Convierte estilos CSS en atributos de estilo en línea en el código del HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>biblioteca</td>
    <td>Convierta selectores CSS en consultas XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>biblioteca</td>
    <td>API DOM moderna.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>biblioteca</td>
    <td>Funciones de modificador y descriptor de acceso de propiedad.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>biblioteca</td>
    <td>PHP 5.x-8.x polyfill para extensión mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>biblioteca</td>
    <td>Biblioteca de comunicaciones seguras de PHP: implementaciones Pure-PHP de RSA, AES, SSH2, SFTP, X.509, etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git">psr/cache</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para bibliotecas de almacenamiento en caché</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/clock</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para leer el reloj.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
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
    <td>PSR-17: Interfaces comunes para las fábricas de mensajes HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para mensajes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>biblioteca</td>
    <td>Interfaz común para bibliotecas de registro</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>biblioteca</td>
    <td>Un polyfill para getallheaders.</td>
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
      <a href="https://github.com/reactphp/promise.git">reaccionar/prometer</a>
    </td>
    <td>biblioteca</td>
    <td>Una implementación ligera de CommonJS Promises/A para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>biblioteca</td>
    <td>Analizador de archivos CSS escritos en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>biblioteca</td>
    <td>Linter de JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phar-utils</a>
    </td>
    <td>biblioteca</td>
    <td>Utilidades de formato de archivo PHAR, para cuando PHP te pone en marcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signal-handler</a>
    </td>
    <td>biblioteca</td>
    <td>Controlador de señal Unix simple que falla silenciosamente cuando las señales no son compatibles para un desarrollo fácil entre plataformas</td>
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
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>biblioteca</td>
    <td>Una biblioteca PHP para generar contraseñas de una sola vez según RFC 4226 (HOTP Algorithm) y RFC 6238 (TOTP Algorithm) y compatible con Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>biblioteca</td>
    <td>Un marco de PHP para administrar la infraestructura de claves públicas. Incluye certificados de clave pública X.509, certificados de atributos, solicitudes de certificación y validación de rutas de certificación.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>biblioteca</td>
    <td>Ayuda a buscar, cargar, combinar, rellenar automáticamente y validar valores de configuración de cualquier tipo</td>
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
    <td>Convierte selectores CSS en expresiones XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/dependencies-inject</a>
    </td>
    <td>biblioteca</td>
    <td>Permite estandarizar y centralizar la forma en que se construyen los objetos en la aplicación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">contratos de Symfony/deprecation</a>
    </td>
    <td>biblioteca</td>
    <td>Una función y convención genéricas para almacenar en déclencheur los avisos de desaprobación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona herramientas para gestionar errores y facilitar la depuración de código PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona herramientas que permiten a los componentes de la aplicación comunicarse entre sí mediante la distribución de eventos y su escucha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">contratos de Symfony/event-dispatcher</a>
    </td>
    <td>biblioteca</td>
    <td>Abstracciones genéricas relacionadas con el evento de envío</td>
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
    <td>Busca archivos y directorios a través de una interfaz fluida e intuitiva</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona métodos eficaces para recuperar recursos HTTP sincrónica o asincrónicamente</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">contratos de cliente/Symfony/http</a>
    </td>
    <td>biblioteca</td>
    <td>Abstracciones genéricas relacionadas con clientes HTTP</td>
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
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona acceso a los datos de localización de la biblioteca de la UCI</td>
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
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill para las funciones de grafeme_* de intl</td>
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
    <td>Symfony polyfill backporting algunas características de PHP 7.2+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 7.3+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.0+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.1+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.3+ a versiones más bajas de PHP</td>
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
      <a href="https://github.com/symfony/service-contracts.git">contratos de servicio/symfony</a>
    </td>
    <td>biblioteca</td>
    <td>Abstracciones genéricas relacionadas con los servicios de escritura</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/string</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona una API orientada a objetos para cadenas y trata bytes, puntos de código UTF-8 y clústeres de grafemas de forma unificada</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>biblioteca</td>
    <td>Proporciona mecanismos para caminar a través de cualquier variable PHP arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>biblioteca</td>
    <td>Permite exportar cualquier estructura de datos PHP serializable a código PHP simple</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>paquete Symfony</td>
    <td>Biblioteca de firma y cifrado de objetos JSON para el paquete PHP y Symfony.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>biblioteca</td>
    <td>Afirmaciones para validar la entrada/salida del método con mensajes de error correctos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>biblioteca</td>
    <td>Implementación de referencia de un puerto PHP de GraphQL</td>
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
      paypal/module-braintree-customer-balance
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gif-card-account
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-wrapping-regalos
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>N/D</td>
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

### Propietario

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
    <td>Bifurcación del módulo Magento Braintree 2.2.0 de Gene Commerce para PayPal.</td>
  </tr>
  </tbody>
</table>
