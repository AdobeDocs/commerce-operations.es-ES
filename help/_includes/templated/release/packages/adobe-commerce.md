---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '2906'
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

La siguiente documentación de referencia se genera a partir del archivo `composer.lock` y abarca los paquetes necesarios incluidos en Adobe Commerce 2.4.8.

## Dependencias

`magento/product-enterprise-edition 2.4.8` tiene las dependencias siguientes:

- adobe-commerce/extensions-metapackage: 2.0.1
- colinmollenhour/cache-backend-file: ^1.4
- colinmollenhour/cache-backend-redis: ^1.16
- colinmollenhour/credis: ^1.15
- colinmollenhour/php-redis-session-abstract: ^2.0
- compositor/compositor: ^2.0, !=2,2,16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_universal_php: ^1.0
- elasticsearch/elasticsearch: ^8.15
- ext-bcmath: *
- ext-ctype: *
- ext-curl: *
- ext-dom: *
- ext-ftp: *
- ext-gd: *
- ext-hash: *
- ext-iconv: *
- ext-intl: *
- ext-mbstring: *
- ext-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- ext-soap: *
- ext-sodio: *
- ext-spl: *
- ext-xsl: *
- ext-zip: *
- ezyang/htmlpurifier: ^4.17
- guzzlehttp/guzzle: ^7.5
- laminas/laminas-captcha: ^2.18
- laminas/laminas-código: ^4.13
- laminas/laminas-di: ^3.15
- laminas/laminas-escaper: ^2.13
- laminas/laminas-eventmanager: ^3.11
- laminas/laminas-feed: ^2.22
- laminas/laminas-filter: ^2.33
- laminas/laminas-http: ^2.15
- laminas/laminas-i18n: ^2.17
- laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3.6
- laminas/laminas-permissions-acl: ^2.10
- laminas/laminas-servicemanager: ^3.16
- laminas/jabón laminas: ^2.10
- laminas/laminas-stdlib: ^3.11
- laminas/laminas-uri: ^2,9
- laminas/laminas-validador: ^2.23
- liga/sistema de archivos: ^3.0
- league/flysystem-aws-s3-v3: ^3.0
- lib-libxml: *
- magento/composer: ^1.10.1-beta1
- magento/composer-dependencies-version-audit-plugin: ^0.1
- magento/framework-external-key: 100.4.7
- magento/magento-composer-installer: >=0.4.0
- magento/magento-zf-db: ^3.21
- magento/magento2-ee-base: 2.4.8
- [magento/module-admin-gws](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws/): 100.4.8
- [magento/module-admin-gws-configurable-product](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-configurable-product/): 100.4.5
- [magento/module-admin-gws-staging](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-staging/): 100.4.5
- [magento/module-advanced-catalog](https://developer.adobe.com/commerce/php/module-reference/module-advanced-catalog/): 100.4.5
- [magento/module-advanced-checkout](https://developer.adobe.com/commerce/php/module-reference/module-advanced-checkout/): 100.4.8
- [magento/module-advanced-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-rule/): 100.4.5
- [magento/module-advanced-sales-rule](https://developer.adobe.com/commerce/php/module-reference/module-advanced-sales-rule/): 100.4.5
- [magento/module-application-server](https://developer.adobe.com/commerce/php/module-reference/module-application-server/): 100.4.1
- [magento/module-application-server-new-relic](https://developer.adobe.com/commerce/php/module-reference/module-application-server-new-relic/): 100.4.1
- [magento/module-application-server-performance-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-performance-monitor/): 100.4.1
- [magento/module-application-server-state-monitor](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor/): 100.4.1
- [magento/module-application-server-state-monitor-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor-graph-ql/): 100.4.1
- [magento/module-async-order](https://developer.adobe.com/commerce/php/module-reference/module-async-order/): 100.4.4
- [magento/module-async-order-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-async-order-graph-ql/): 100.4.3
- [magento/module-aws-s3-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-customer-custom-attributes/): 100.4.5
- [magento/module-aws-s3-gif-card-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-gift-card-import-export/): 100.4.5
- [magento/module-aws-s3-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-scheduled-import-export/): 100.4.5
- [magento/module-banner](https://developer.adobe.com/commerce/php/module-reference/module-banner/): 101.2.8
- [magento/module-banner-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-banner-customer-segment/): 100.4.6
- [magento/module-banner-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-banner-graph-ql/): 100.4.4
- [magento/module-banner-staging](https://developer.adobe.com/commerce/php/module-reference/module-banner-staging/): 100.4.2
- [magento/module-bundle-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export-staging/): 100.4.5
- [magento/module-bundle-staging](https://developer.adobe.com/commerce/php/module-reference/module-bundle-staging/): 100.4.8
- [magento/module-catalog-event](https://developer.adobe.com/commerce/php/module-reference/module-catalog-event/): 101.1.7
- [magento/module-catalog-import-export-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export-staging/): 100.4.5
- [magento/module-catalog-inventory-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-staging/): 100.4.6
- [magento/module-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions/): 100.4.8
- [magento/module-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions-graph-ql/): 100.4.6
- [magento/module-catalog-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-staging/): 100.4.8
- [magento/module-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging/): 100.4.8
- [magento/module-catalog-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging-graph-ql/): 100.4.7
- [magento/module-catalog-url-rewrite-staging](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-staging/): 100.4.7
- [magento/module-checkout-address-search](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search/): 100.4.7
- [magento/module-checkout-address-search-gif-registry](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search-gift-registry/): 100.4.4
- [magento/module-checkout-staging](https://developer.adobe.com/commerce/php/module-reference/module-checkout-staging/): 100.4.7
- [magento/module-cms-staging](https://developer.adobe.com/commerce/php/module-reference/module-cms-staging/): 100.4.8
- [magento/module-configurable-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-staging/): 100.4.7
- [magento/module-custom-attribute-management](https://developer.adobe.com/commerce/php/module-reference/module-custom-attribute-management/): 100.4.7
- [magento/module-customer-balance](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance/): 100.4.8
- [magento/module-customer-balance-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance-graph-ql/): 100.4.5
- [magento/module-customer-custom-attributes](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes/): 100.4.8
- [magento/module-customer-custom-attributes-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes-graph-ql/): 100.4.1
- [magento/module-customer-finance](https://developer.adobe.com/commerce/php/module-reference/module-customer-finance/): 100.4.5
- [magento/module-customer-segment](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment/): 102.1.8
- [magento/module-customer-segment-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment-graph-ql/): 100.4.1
- [cálculo total aplazado de magento/módulo](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/): 100.4.3
- [magento/module-downloadable-staging](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-staging/): 100.4.7
- [magento/module-elasticsearch-catalog-permissions](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions/): 100.4.4
- [magento/module-elasticsearch-catalog-permissions-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions-graph-ql/): 100.4.3
- [magento/module-enterprise](https://developer.adobe.com/commerce/php/module-reference/module-enterprise/): 100.4.6
- [tarjeta regalo de módulo/magento](https://developer.adobe.com/commerce/php/module-reference/module-gift-card/): 101.3.8
- [cuenta-tarjeta-regalo-módulo/magento](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account/): 101.2.8
- [magento/module-gif-card-account-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account-graph-ql/): 100.4.6
- [magento/module-gif-card-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-graph-ql/): 100.4.8
- [magento/module-gif-card-import-export](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-import-export/): 100.4.5
- [magento/module-gif-card-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-staging/): 100.4.5
- [magento/module-gif-message-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-staging/): 100.4.5
- [magento/module-gif-register](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry/): 101.2.8
- [magento/module-gif-register-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry-graph-ql/): 100.4.4
- [envoltorio para regalos de magento/módulo](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping/): 101.2.7
- [magento/module-gif-wrapping-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-graph-ql/): 100.4.5
- [magento/module-gif-wrapping-staging](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-staging/): 100.4.5
- [magento/module-google-optimizer-staging](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer-staging/): 100.4.5
- [magento/module-google-tag-manager](https://developer.adobe.com/commerce/php/module-reference/module-google-tag-manager/): 100.4.8
- [magento/module-agruped-product-staging](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-staging/): 100.4.6
- [magento/module-import-csv](https://developer.adobe.com/commerce/php/module-reference/module-import-csv/): 100.4.2
- [magento/module-import-csv-api](https://developer.adobe.com/commerce/php/module-reference/module-import-csv-api/): 100.4.2
- [magento/module-import-json](https://developer.adobe.com/commerce/php/module-reference/module-import-json/): 100.4.1
- [magento/module-import-json-api](https://developer.adobe.com/commerce/php/module-reference/module-import-json-api/): 100.4.1
- [magento/module-invite](https://developer.adobe.com/commerce/php/module-reference/module-invitation/): 100.4.7
- [magento/module-layered-navigation-staging](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation-staging/): 100.4.5
- [magento/module-logging](https://developer.adobe.com/commerce/php/module-reference/module-logging/): 101.2.8
- [magento/module-login-as-customer-logging](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-logging/): 100.4.8
- [magento/module-login-as-customer-website-constraint](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-website-restriction/): 100.4.6
- [magento/module-media-content-catalog-staging](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog-staging/): 100.4.5
- [magento/module-msrp-staging](https://developer.adobe.com/commerce/php/module-reference/module-msrp-staging/): 100.4.6
- [magento/module-multicoupon](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon/): 100.4.1
- [magento/module-multicast-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-graph-ql/): 100.4.1
- [magento/module-multicoupon-ui](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-ui/): 100.4.1
- [magento/module-multiple-wishlist](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist/): 100.4.8
- [magento/module-multiple-wishlist-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist-graph-ql/): 100.4.4
- [magento/module-payment-staging](https://developer.adobe.com/commerce/php/module-reference/module-payment-staging/): 100.4.5
- [magento/module-persistent-history](https://developer.adobe.com/commerce/php/module-reference/module-persistent-history/): 100.4.5
- [magento/module-price-permissions](https://developer.adobe.com/commerce/php/module-reference/module-price-permissions/): 100.4.4
- [magento/module-product-video-staging](https://developer.adobe.com/commerce/php/module-reference/module-product-video-staging/): 100.4.5
- [magento/module-promotion-permissions](https://developer.adobe.com/commerce/php/module-reference/module-promotion-permissions/): 100.4.5
- [magento/module-quote-commerce-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-quote-commerce-graph-ql/): 100.4.1
- [magento/module-quote-gif-card-options](https://developer.adobe.com/commerce/php/module-reference/module-quote-gift-card-options/): 100.4.5
- [magento/module-quote-staging](https://developer.adobe.com/commerce/php/module-reference/module-quote-staging/): 100.4.5
- [magento/module-reminder](https://developer.adobe.com/commerce/php/module-reference/module-reminder/): 101.2.7
- [magento/module-remote-storage-commerce](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage-commerce/): 100.4.4
- [magento/module-resource-connections](https://developer.adobe.com/commerce/php/module-reference/module-resource-connections/): 100.4.5
- [magento/module-review-staging](https://developer.adobe.com/commerce/php/module-reference/module-review-staging/): 100.4.5
- [magento/module-premio](https://developer.adobe.com/commerce/php/module-reference/module-reward/): 101.2.8
- [magento/module-premio-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-reward-graph-ql/): 100.4.7
- [magento/module-recompensa-staging](https://developer.adobe.com/commerce/php/module-reference/module-reward-staging/): 100.4.5
- [magento/module-rma](https://developer.adobe.com/commerce/php/module-reference/module-rma/): 101.2.8
- [magento/module-rma-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-rma-graph-ql/): 100.4.7
- [magento/module-rma-staging](https://developer.adobe.com/commerce/php/module-reference/module-rma-staging/): 100.4.5
- [magento/module-sales-archive](https://developer.adobe.com/commerce/php/module-reference/module-sales-archive/): 101.0.6
- [magento/module-sales-rule-staging](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-staging/): 100.4.7
- [magento/module-scale-checkout](https://developer.adobe.com/commerce/php/module-reference/module-scalable-checkout/): 100.4.7
- [magento/module-scale-inventory](https://developer.adobe.com/commerce/php/module-reference/module-scalable-inventory/): 100.4.6
- [magento/module-scale-oms](https://developer.adobe.com/commerce/php/module-reference/module-scalable-oms/): 100.4.6
- [magento/module-scheduled-import-export](https://developer.adobe.com/commerce/php/module-reference/module-scheduled-import-export/): 101.2.8
- [magento/module-search-staging](https://developer.adobe.com/commerce/php/module-reference/module-search-staging/): 100.4.6
- [magento/module-staging](https://developer.adobe.com/commerce/php/module-reference/module-staging/): 101.2.8
- [magento/module-staging-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-staging-graph-ql/): 100.4.5
- [magento/module-support](https://developer.adobe.com/commerce/php/module-reference/module-support/): 101.2.7
- [magento/module-swat](https://developer.adobe.com/commerce/php/module-reference/module-swat/): 100.4.6
- [magento/module-target-rule](https://developer.adobe.com/commerce/php/module-reference/module-target-rule/): 101.2.8
- [magento/module-target-rule-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-target-rule-graph-ql/): 100.4.5
- [magento/module-versions-cms](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms/): 101.2.8
- [magento/module-versions-cms-page-cache](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-page-cache/): 100.4.4
- [magento/module-versions-cms-url-rewrite](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite/): 100.4.6
- [magento/module-versions-cms-url-rewrite-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite-graph-ql/): 100.4.4
- [magento/module-visual-merchandiser](https://developer.adobe.com/commerce/php/module-reference/module-visual-merchandiser/): 100.4.8
- [magento/module-webapi-rest-gws](https://developer.adobe.com/commerce/php/module-reference/module-webapi-rest-gws/): 100.4.0
- [magento/module-website-constraint](https://developer.adobe.com/commerce/php/module-reference/module-website-restriction/): 100.4.7
- [magento/module-weee-staging](https://developer.adobe.com/commerce/php/module-reference/module-weee-staging/): 100.4.5
- [magento/module-wishlist-gif-card](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card/): 100.4.4
- [magento/module-wishlist-gif-graph-ql](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card-graph-ql/): 100.4.4
- magento/page-builder-commerce: 1.7.5
- magento/product-community-edition: 2.4.8
- magento/security-package-ee: 1.0.3
- magento/theme-adminhtml-spectrum: 100.4.3
- magento/zend-cache: ^1.16
- magento/zend-db: ^1.16
- magento/zend-pdf: ^1.16
- monólogo/monólogo: ^3.6
- opensearch-project/opensearch-php: ^2.3
- pelago/emogrificador: ^7.0
- php: ~8.2.0||~8.3.0||~8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4.2
- symfony/console: ^6.4
- symfony/intl: ^6.4
- symfony/mailer: ^6.4
- symfony/mime: ^6.4
- symfony/process: ^6.4
- symfony/string: ^6.4
- tedivm/jshrink: ^1.4
- tubalmartin/cssmin: ^4.1
- web-token/jwt-framework: ^3.4
- webonyx/graphql-php: ^15.0
- wikimedia/less.php: ^5.0

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
      <a href="https://github.com/opensearch-project/opensearch-php">opensearch-project/opensearch-php</a>
    </td>
    <td>Biblioteca</td>
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
      <a href="https://github.com/adobe/stock-api-libphp">astock/stock-api-libphp</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de API de Adobe Stock</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php">aws/aws-crt-php</a>
    </td>
    <td>Biblioteca</td>
    <td>Common Runtime de AWS para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php">aws/aws-sdk-php</a>
    </td>
    <td>Biblioteca</td>
    <td>AWS SDK para PHP: Utilice Amazon Web Service en su proyecto PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api">telemetría abierta/api</a>
    </td>
    <td>Biblioteca</td>
    <td>API para OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context">telemetría abierta/contexto</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementación de contexto para OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree
    </td>
    <td>Metapaquete</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php">wikimedia/less.php</a>
    </td>
    <td>Biblioteca</td>
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
      <a href="https://github.com/Bacon/BaconQrCode">bacon/bacon-qr-code</a>
    </td>
    <td>Biblioteca</td>
    <td>BaconQrCode es un generador de código QR para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum">dasprid/enum</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementación de enumeración en PHP 7.1</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer">webimpress/safe-writer</a>
    </td>
    <td>Biblioteca</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File">colinmollenhour/cache-backend-file</a>
    </td>
    <td>Magento-module</td>
    <td>El back-end Zend_Cache_Backend_File de stock tiene un rendimiento extremadamente bajo para la limpieza por etiquetas, lo que hace que no se pueda utilizar a medida que aumenta el número de elementos en caché. Este servidor realiza muchos cambios que mejoran enormemente el rendimiento, especialmente en la limpieza de etiquetas.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract">colinmollenhour/php-redis-session-abstract</a>
    </td>
    <td>Biblioteca</td>
    <td>Controlador de sesión basado en Redis con bloqueo optimista</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php">duosecurity/duo_universal_php</a>
    </td>
    <td>Biblioteca</td>
    <td>Una implementación PHP del Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt">firebase/php-jwt</a>
    </td>
    <td>Biblioteca</td>
    <td>Una sencilla biblioteca para codificar y descodificar tokens web JSON (JWT) en PHP. Debe ajustarse a la especificación actual.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha">laminas/laminas-captcha</a>
    </td>
    <td>Biblioteca</td>
    <td>Genere y valide CAPTCHA con miniprogramas, imágenes, ReCaptcha y más</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code">código laminas/laminas</a>
    </td>
    <td>Biblioteca</td>
    <td>Extensiones a la API de PHP Reflection, escaneo de código estático y generación de código</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config">laminas/laminas-config</a>
    </td>
    <td>Biblioteca</td>
    <td>proporciona una interfaz de usuario basada en la propiedad de objeto anidada para acceder a estos datos de configuración dentro del código de la aplicación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di">laminas/laminas-di</a>
    </td>
    <td>Biblioteca</td>
    <td>Inyección de dependencia automatizada para contenedores de PSR-11</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper">laminas/laminas-escaper</a>
    </td>
    <td>Biblioteca</td>
    <td>Escape de forma segura de HTML, atributos de HTML, JavaScript, CSS y direcciones URL</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager">laminas/laminas-eventmanager</a>
    </td>
    <td>Biblioteca</td>
    <td>Déclencheur y escucha de eventos dentro de una aplicación PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed">laminas/laminas-feed</a>
    </td>
    <td>Biblioteca</td>
    <td>proporciona funcionalidad para crear y consumir fuentes RSS y Atom</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter">filtro laminas/laminas</a>
    </td>
    <td>Biblioteca</td>
    <td>Filtrar y normalizar datos y archivos mediante programación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http">laminas/laminas-http</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona una interfaz sencilla para realizar solicitudes HTTP (Protocolo de transferencia de hipertexto)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n">laminas/laminas-i18n</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporcione traducciones para la aplicación y filtre y valide valores internacionalizados</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json">laminas/laminas-json</a>
    </td>
    <td>Biblioteca</td>
    <td>proporciona métodos de conveniencia para serializar PHP nativo en JSON y descodificar JSON en PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader">laminas/laminas-loader</a>
    </td>
    <td>Biblioteca</td>
    <td>Estrategias de carga automática y de complementos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager">laminas/laminas-modulemanager</a>
    </td>
    <td>Biblioteca</td>
    <td>Sistema de aplicación modular para aplicaciones laminas-mvc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc">laminas/laminas-mvc</a>
    </td>
    <td>Biblioteca</td>
    <td>Capa de MVC impulsada por eventos de Laminas, que incluye aplicaciones, controladores y complementos de MVC</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl">laminas/laminas-permissions-acl</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona una implementación de lista de control de acceso (ACL) ligera y flexible para la administración de privilegios</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha">laminas/laminas-recaptcha</a>
    </td>
    <td>Biblioteca</td>
    <td>Envoltorio OOP para el servicio web ReCaptcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router">laminas/laminas-router</a>
    </td>
    <td>Biblioteca</td>
    <td>Sistema de enrutamiento flexible para aplicaciones HTTP y de consola</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server">servidor laminas/laminas</a>
    </td>
    <td>Biblioteca</td>
    <td>Crear servidores RPC basados en reflexión</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager">laminas/laminas-servicemanager</a>
    </td>
    <td>Biblioteca</td>
    <td>Contenedor de inyección de dependencia de fábrica</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session">laminas/laminas-session</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz orientada a objetos para sesiones y almacenamiento de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap">jabón laminas/laminas</a>
    </td>
    <td>Biblioteca</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib">laminas/laminas-stdlib</a>
    </td>
    <td>Biblioteca</td>
    <td>Extensiones SPL, utilidades de matriz, controladores de errores y más</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text">laminas/laminas-text</a>
    </td>
    <td>Biblioteca</td>
    <td>Crear FIGlets y tablas basadas en texto</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator">laminas/laminas-translator</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaces para el componente Translator de laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri">laminas/laminas-uri</a>
    </td>
    <td>Biblioteca</td>
    <td>Componente que ayuda a manipular y validar los identificadores uniformes de recursos (URI)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator">laminas/laminas-validator</a>
    </td>
    <td>Biblioteca</td>
    <td>Clases de validación para una amplia gama de dominios y la capacidad de encadenar validadores para crear criterios de validación complejos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view">laminas/laminas-view</a>
    </td>
    <td>Biblioteca</td>
    <td>Capa de vista flexible que admite y proporciona varias capas de vista, ayuda, etc</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum">marc-mabe/php-enum</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementación sencilla y rápida de enumeraciones con PHP nativo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser">nikic/php-parser</a>
    </td>
    <td>Biblioteca</td>
    <td>Un analizador de PHP escrito en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha">phpfui/recaptcha</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de cliente para reCAPTCHA de Google para PHP 8.4 y superior</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink">tedivm/jshrink</a>
    </td>
    <td>Biblioteca</td>
    <td>Minifier Javascript integrado en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port">tubalmartin/cssmin</a>
    </td>
    <td>Biblioteca</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis">colinmollenhour/cache-backend-redis</a>
    </td>
    <td>Magento-module</td>
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
      <a href="https://github.com/paragonie/sodium_compat">paragonie/sodio_compat</a>
    </td>
    <td>Biblioteca</td>
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
      <a href="https://github.com/ezyang/htmlpurifier">ezyang/htmlpurifier</a>
    </td>
    <td>Biblioteca</td>
    <td>Filtro HTML compatible con estándares escrito en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib">php-amqplib/php-amqplib</a>
    </td>
    <td>Biblioteca</td>
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
      <a href="https://github.com/braintree/braintree_php">braintree/braintree_php</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de cliente de Braintree PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math">brick/math</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca aritmética de precisión arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter">brick/varexporter</a>
    </td>
    <td>Biblioteca</td>
    <td>Una alternativa potente a var_export(), que puede exportar cierres y objetos sin __set_state()</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32">christian-riesen/base32</a>
    </td>
    <td>Biblioteca</td>
    <td>Codificador/decodificador Base32 según RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis">colinmollenhour/credis</a>
    </td>
    <td>Biblioteca</td>
    <td>Credis es una interfaz ligera para el almacén de valor clave de Redis que ajusta la biblioteca phpredis cuando está disponible para obtener un mejor rendimiento.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle">compositor/ca-paquete</a>
    </td>
    <td>Biblioteca</td>
    <td>Le permite encontrar una ruta al paquete de CA del sistema e incluye una alternativa al paquete de CA de Mozilla.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator">compositor/generador de mapas de clase</a>
    </td>
    <td>Biblioteca</td>
    <td>Utilidades para escanear código PHP y generar mapas de clase.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer">compositor/compositor</a>
    </td>
    <td>Biblioteca</td>
    <td>Composer le ayuda a declarar, administrar e instalar dependencias de proyectos PHP. Garantiza que tenga la pila correcta en todas partes.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier">compositor/minificador de metadatos</a>
    </td>
    <td>Biblioteca</td>
    <td>Pequeña biblioteca de utilidades que gestiona la minificación y expansión de metadatos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre">compositor/pcre</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de envoltorio PCRE que ofrece reemplazos preg_* seguros para tipos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver">compositor/servidor</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de servidor que ofrece utilidades, análisis de restricción de versión y validación.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses">licencias de composición/spdx</a>
    </td>
    <td>Biblioteca</td>
    <td>Lista de licencias SPDX y biblioteca de validación.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler">composer/xdebug-handler</a>
    </td>
    <td>Biblioteca</td>
    <td>Reinicia un proceso sin Xdebug.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer">doctrina/lexer</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca del analizador de PHP Doctrine Lexer que se puede utilizar en analizadores descendentes recursivos descendentes verticales.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator">egulias/email-validator</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca para validar correos electrónicos con varios RFC</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php">elástico/transporte</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca PHP de transporte HTTP para productos elásticos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php">elasticsearch/elasticsearch</a>
    </td>
    <td>Biblioteca</td>
    <td>Cliente PHP para Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code">endroid/qr-code</a>
    </td>
    <td>Biblioteca</td>
    <td>Código QR de Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams">ezimuel/guzzlestreams</a>
    </td>
    <td>Biblioteca</td>
    <td>Bifurcación de guzzle/arroyos (abandonada) para usar con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp">ezimuel/ringphp</a>
    </td>
    <td>Biblioteca</td>
    <td>Tenedor de guzzle/RingPHP (abandonado) para usar con elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle">guzzlehttp/guzzle</a>
    </td>
    <td>Biblioteca</td>
    <td>Guzzle es una biblioteca de cliente HTTP PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises">guzzlehttp/promise</a>
    </td>
    <td>Biblioteca</td>
    <td>Guzzle promete biblioteca</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7">guzzlehttp/psr7</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementación de mensaje PSR-7 que también proporciona métodos de utilidad comunes</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema">justinrainbow/json-schema</a>
    </td>
    <td>Biblioteca</td>
    <td>Una biblioteca para validar un esquema json.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem">liga/sistema de archivos</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstracción de almacenamiento de archivos para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3">league/flysystem-aws-s3-v3</a>
    </td>
    <td>Biblioteca</td>
    <td>Adaptador del sistema de archivos AWS S3 para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local">liga/flysystem-local</a>
    </td>
    <td>Biblioteca</td>
    <td>Adaptador del sistema de archivos local para Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection">league/mime-type-discovery</a>
    </td>
    <td>Biblioteca</td>
    <td>Detección de tipo MIME para Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog">monólogo/monólogo</a>
    </td>
    <td>Biblioteca</td>
    <td>Envía sus registros a archivos, sockets, bandejas de entrada, bases de datos y diversos servicios web</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php">mtdowling/jmespath.php</a>
    </td>
    <td>Biblioteca</td>
    <td>Especificar mediante declaración cómo extraer elementos de un documento JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding">paragonie/constant_time_encoding</a>
    </td>
    <td>Biblioteca</td>
    <td>Implementaciones en tiempo constante de la codificación RFC 4648 (Base-64, Base-32, Base-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat">paragonie/random_compat</a>
    </td>
    <td>Biblioteca</td>
    <td>PHP 5.x polyfill para random_bytes() y random_int() de PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier">pelago/emogrificador</a>
    </td>
    <td>Biblioteca</td>
    <td>Convierte los estilos CSS en atributos de estilo en línea en el código HTML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery">php-http/discovery</a>
    </td>
    <td>Composer-plugin</td>
    <td>Busca e instala las implementaciones de PSR-7, PSR-17, PSR-18 y HTTPlug</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug">php-http/httplug</a>
    </td>
    <td>Biblioteca</td>
    <td>HTTPlug, la abstracción de cliente HTTP para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise">php-http/promise</a>
    </td>
    <td>Biblioteca</td>
    <td>Promesa utilizada para solicitudes HTTP asincrónicas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath">phpgt/cssxpath</a>
    </td>
    <td>Biblioteca</td>
    <td>Convierta selectores CSS en consultas XPath.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom">phpgt/dom</a>
    </td>
    <td>Biblioteca</td>
    <td>API DOM moderna.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc">phpgt/propfunc</a>
    </td>
    <td>Biblioteca</td>
    <td>Funciones de modificador y descriptor de acceso de propiedad.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat">phpseclib/mcrypt_compat</a>
    </td>
    <td>Biblioteca</td>
    <td>PHP 5.x-8.x polyfill para extensión mcrypt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib">phpseclib/phpseclib</a>
    </td>
    <td>Biblioteca</td>
    <td>Biblioteca de comunicaciones seguras de PHP: implementaciones Pure-PHP de RSA, AES, SSH2, SFTP, X.509, etc.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache">psr/cache</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz común para bibliotecas de almacenamiento en caché</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock">psr/clock</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz común para leer el reloj.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container">psr/container</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz de contenedor común (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher">psr/event-dispatcher</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaces estándar para la gestión de eventos.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client">psr/http-client</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz común para clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory">psr/http-factory</a>
    </td>
    <td>Biblioteca</td>
    <td>PSR-17: Interfaces comunes para las fábricas de mensajes HTTP PSR-7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message">psr/http-message</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz común para mensajes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log">psr/log</a>
    </td>
    <td>Biblioteca</td>
    <td>Interfaz común para bibliotecas de registro</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders">ralouphie/getallheaders</a>
    </td>
    <td>Biblioteca</td>
    <td>Un polyfill para getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection">ramsey/collection</a>
    </td>
    <td>Biblioteca</td>
    <td>Una biblioteca PHP para representar y manipular colecciones.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid">ramsey/uuid</a>
    </td>
    <td>Biblioteca</td>
    <td>Una biblioteca PHP para generar y trabajar con identificadores únicos universales (UUID).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise">reaccionar/prometer</a>
    </td>
    <td>Biblioteca</td>
    <td>Una implementación ligera de CommonJS Promises/A para PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser">sabberworm/php-css-parser</a>
    </td>
    <td>Biblioteca</td>
    <td>Analizador de archivos CSS escritos en PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint">seld/jsonlint</a>
    </td>
    <td>Biblioteca</td>
    <td>Linter de JSON</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils">seld/phar-utils</a>
    </td>
    <td>Biblioteca</td>
    <td>Utilidades de formato de archivo PHAR, para cuando PHP te pone en marcha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler">seld/signal-handler</a>
    </td>
    <td>Biblioteca</td>
    <td>Controlador de señal Unix simple que falla silenciosamente cuando las señales no son compatibles para un desarrollo fácil entre plataformas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap">spomky-labs/aes-key-wrap</a>
    </td>
    <td>Biblioteca</td>
    <td>AES Key Wrap para PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp">spomky-labs/otphp</a>
    </td>
    <td>Biblioteca</td>
    <td>Una biblioteca PHP para generar contraseñas de una sola vez según RFC 4226 (HOTP Algorithm) y RFC 6238 (TOTP Algorithm) y compatible con Google Authenticator</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework">spomky-labs/pki-framework</a>
    </td>
    <td>Biblioteca</td>
    <td>Un marco de PHP para administrar la infraestructura de claves públicas. Incluye certificados de clave pública X.509, certificados de atributos, solicitudes de certificación y validación de rutas de certificación.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config">symfony/config</a>
    </td>
    <td>Biblioteca</td>
    <td>Ayuda a buscar, cargar, combinar, rellenar automáticamente y validar valores de configuración de cualquier tipo</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console">symfony/console</a>
    </td>
    <td>Biblioteca</td>
    <td>Facilita la creación de interfaces de línea de comandos hermosas y comprobables</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector">symfony/css-selector</a>
    </td>
    <td>Biblioteca</td>
    <td>Convierte selectores CSS en expresiones XPath</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection">symfony/dependencies-inject</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite estandarizar y centralizar la forma en que se construyen los objetos en la aplicación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts">contratos de Symfony/deprecation</a>
    </td>
    <td>Biblioteca</td>
    <td>Una función y convención genéricas para almacenar en déclencheur los avisos de desaprobación</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler">symfony/error-handler</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona herramientas para gestionar errores y facilitar la depuración de código PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher">symfony/event-dispatcher</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona herramientas que permiten a los componentes de la aplicación comunicarse entre sí mediante la distribución de eventos y su escucha</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts">contratos de Symfony/event-dispatcher</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstracciones genéricas relacionadas con el evento de envío</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem">symfony/filesystem</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona utilidades básicas para el sistema de archivos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder">symfony/finder</a>
    </td>
    <td>Biblioteca</td>
    <td>Busca archivos y directorios a través de una interfaz fluida e intuitiva</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client">symfony/http-client</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona métodos eficaces para recuperar recursos HTTP sincrónica o asincrónicamente</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts">contratos de cliente/Symfony/http</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstracciones genéricas relacionadas con clientes HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation">symfony/http-foundation</a>
    </td>
    <td>Biblioteca</td>
    <td>Define una capa orientada a objetos para la especificación HTTP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel">symfony/http-kernel</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona un proceso estructurado para convertir una solicitud en una respuesta</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl">symfony/intl</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona acceso a los datos de localización de la biblioteca de la UCI</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer">symfony/mailer</a>
    </td>
    <td>Biblioteca</td>
    <td>Ayuda a enviar correos electrónicos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime">symfony/mime</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite manipular mensajes MIME</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype">symfony/polyfill-ctype</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para funciones ctype</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para las funciones de grafeme_* de intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn">symfony/polyfill-intl-idn</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para las funciones idn_to_ascii e idn_to_utf8 de intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para la clase Normalizer de intl y funciones relacionadas</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring">symfony/polyfill-mbstring</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill para la extensión Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73">symfony/polyfill-php73</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 7.3+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80">symfony/polyfill-php80</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.0+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81">symfony/polyfill-php81</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.1+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82">symfony/polyfill-php82</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.2+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83">symfony/polyfill-php83</a>
    </td>
    <td>Biblioteca</td>
    <td>Symfony polyfill backporting algunas características de PHP 8.3+ a versiones más bajas de PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process">symfony/process</a>
    </td>
    <td>Biblioteca</td>
    <td>Ejecuta comandos en subprocesos</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts">contratos de servicio/symfony</a>
    </td>
    <td>Biblioteca</td>
    <td>Abstracciones genéricas relacionadas con los servicios de escritura</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string">symfony/string</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona una API orientada a objetos para cadenas y trata bytes, puntos de código UTF-8 y clústeres de grafemas de forma unificada</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper">symfony/var-dumper</a>
    </td>
    <td>Biblioteca</td>
    <td>Proporciona mecanismos para caminar a través de cualquier variable PHP arbitraria</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter">symfony/var-exporter</a>
    </td>
    <td>Biblioteca</td>
    <td>Permite exportar cualquier estructura de datos PHP serializable a código PHP simple</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml">symfony/yaml</a>
    </td>
    <td>Biblioteca</td>
    <td>Carga y descarga archivos YAML</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework">web-token/jwt-framework</a>
    </td>
    <td>Paquete Symfony</td>
    <td>Biblioteca de firma y cifrado de objetos JSON para el paquete PHP y Symfony.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php">webonyx/graphql-php</a>
    </td>
    <td>Biblioteca</td>
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
    <td>módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gif-card
    </td>
    <td>módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gif-card-account
    </td>
    <td>módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-wrapping-regalos
    </td>
    <td>módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>módulo Magento2</td>
    <td>N/D</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-premio
    </td>
    <td>módulo Magento2</td>
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
      <a href="https://github.com/2tvenom/CBOREncode">2tvenom/cborencode</a>
    </td>
    <td>Biblioteca</td>
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
    <td>módulo Magento2</td>
    <td>Bifurcación del módulo Magento Braintree 2.2.0 de Gene Commerce para PayPal.</td>
  </tr>
  </tbody>
</table>
