---
title: Prácticas recomendadas para modificar código PHP principal y de terceros
description: Aprenda cómo y cuándo modificar el código principal de Adobe Commerce y PHP de terceros.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Prácticas recomendadas para modificar o anular el código PHP principal y de terceros

Este documento describe las prácticas recomendadas cuando surge la necesidad de modificar la funcionalidad, el resultado o la entrada de cualquier código que no haya creado o que no controle directamente. En otras palabras, código principal y código de terceros. Este documento se centra principalmente en el código PHP back-end.

## Métodos de modificación del código

Al modificar el código, es importante tener en cuenta el ámbito de los cambios. El &quot;alcance&quot; de los cambios se refiere a la magnitud de los efectos de los cambios en el código. Como práctica recomendada, base la decisión sobre cómo se completa la implementación final en la opción que tenga el menor espacio y el menor uso de recursos. Cuanto más amplias sean las anulaciones de código, más se desviará un equipo de desarrollo de la funcionalidad principal de Adobe Commerce, lo que aumentará la probabilidad de que se produzcan errores y mayores esfuerzos por mantener la base de código en el futuro.

### Parche

Un parche es un archivo que contiene instrucciones para cambiar directamente el código en un archivo que no está bajo el control directo del equipo de desarrollo. Esta es una opción que generalmente debe considerarse como un último recurso cuando no existen otras opciones. Los parches están pensados para ser una solución temporal. Si tiene que crear un parche, como práctica recomendada general, quítelo en favor de una solución más permanente en las siguientes 2-4 semanas. 

Los parches se rompen fácilmente. Si se actualizan los archivos a los que se dirige el parche, a menudo el parche deja de funcionar. Esto se debe a que un archivo de parche contiene números de línea y números de columna que indican específicamente lo que debe cambiar el parche. Si algo no coincide con lo que esperaba el parche, deja de aplicarse y rompe el código.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### Qué se puede cambiar con un parche

Cualquier cosa. Literalmente, cualquier carácter dentro de cualquier archivo de destino puede cambiarse. Los parches no se limitan a ningún tipo de archivo o lenguaje de código en particular. Normalmente, utilizaría un parche para los archivos de destino dentro del directorio `vendor`. 

#### Cuándo usar un parche

Si te das cuenta de que no existe otra opción. Por ejemplo, cuando el proveedor aún no ha publicado una corrección para el código, puede utilizar un parche para solucionar temporalmente el problema mientras espera una solución permanente.

#### Inconvenientes

Los parches se rompen fácilmente. En el momento en que el código objetivo cambia, el parche deja de funcionar. Están pensados para ser una solución a corto plazo solamente.

### Preferencia

Una preferencia es un concepto diseñado en la plataforma de Adobe Commerce. Es esencialmente un &quot;reemplazo de clase PHP&quot;.

La plataforma Adobe Commerce usa un &quot;gestor de objetos&quot; para crear instancias de clases PHP porque no crea instancias de clases PHP con la nueva palabra clave como se hace en las aplicaciones PHP tradicionales. En su lugar, el administrador de objetos hace referencias cruzadas al nombre de la clase PHP que se va a crear con una configuración compilada para determinar si algún módulo ha declarado una preferencia para la clase original. Si se encuentra una preferencia para la clase PHP, el administrador de objetos crea una instancia de la clase especificada en su lugar.

Cabe señalar que (por lo general) la nueva clase PHP que reemplaza la clase PHP original se extiende/hereda de la clase PHP original. Esto se hace por un par de razones:

- Para garantizar que se cumple la inyección de dependencia/sugerencia de tipo. De lo contrario, se produce un error grave y la aplicación se interrumpe.
- Para permitir una escritura mínima del código. Si la clase PHP original contiene diez métodos pero sólo necesita anular uno, normalmente puede cambiar un método y dejar intactos los otros nueve. Esto es importante para asegurarse de que no está bloqueando las actualizaciones de la funcionalidad principal a medida que la plataforma se actualiza a nuevas versiones.

#### Declarar una preferencia

Declarar una preferencia es un proceso bastante sencillo. Una sola línea de código necesitaría ser agregada a un archivo `di.xml` dentro de un módulo. Esto se puede hacer de forma global o en cualquier &quot;área&quot; de Adobe Commerce, como `frontend`, `adminhtml`, `graphql`, `webapi_rest` y `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### Qué se puede cambiar con una preferencia

Solo las clases PHP pueden ser anuladas con una preferencia. Dentro de la clase PHP, puede modificar métodos y propiedades públicos y protegidos. En el caso de los métodos públicos y protegidos, puede anular completamente el método o modificar los argumentos que entran en el método principal original (o el resultado que sale de él).

Técnicamente, los métodos privados no se pueden anular. Sin embargo, puede crear su propio reemplazo para el método privado original. Incluso puede darle un nombre arbitrario, también puede utilizar el nombre original. No importa porque un método privado sólo existe dentro del archivo real que lo contiene. Para reemplazar un método privado, debe reemplazar o modificar el método público o protegido que llama al método privado original y debe sustituir la funcionalidad por la suya propia.

#### Cuándo usar una preferencia

Una vez más, debe usar las preferencias cuando no exista otra opción y cuando no pueda lograr su objetivo con la inyección de dependencia, un complemento u observador. A veces, es posible que necesite una preferencia si necesita modificar o anular métodos o propiedades privados o protegidos. Cabe señalar que las preferencias deben utilizarse con moderación. Son un método bastante &quot;codicioso&quot; de cambiar la aplicación y usted efectivamente toma posesión de la clase PHP. Esto puede provocar conflictos con módulos de terceros, bloquear las actualizaciones de la clase principal y provocar errores difíciles de diagnosticar. La plataforma de Adobe Commerce se ha diseñado para incluir otras vías mediante las cuales se pueden realizar cambios en el código subyacente con un espacio menor.

#### Inconvenientes

Las preferencias son una forma voraz de modificar el código y solo deben utilizarse cuando no existen otras opciones. Las preferencias a menudo pueden provocar conflictos dentro de la base de código y, peor aún, pueden bloquear las actualizaciones principales que se producen con las actualizaciones de la plataforma. 

### Observador

Un observador es el concepto de oyente de eventos, tal como se encuentra en muchas aplicaciones, plataformas, bibliotecas y lenguajes de codificación. El concepto no es exclusivo de la plataforma Adobe Commerce. Los observadores han estado en la plataforma desde los días del Magento 1 y se consideran una opción principal de cómo modificar el código principal y el código de terceros. 

El código base principal y cualquier módulo de terceros pueden distribuir un evento en un lugar elegido del código. El observador, que está declarado en un archivo `events.xml` y escucha el evento enviado por su nombre, puede trabajar a nivel global o estar restringido a cualquier &quot;área&quot; de Adobe Commerce, como `frontend`, `adminhtml`, `graphql`, `webapi_rest` y `crontab`.

#### Cómo declarar un observador

Los observadores se pueden configurar en un archivo `events.xml` global o de área específica.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### Qué se puede cambiar con un observador

Los observadores solo se aplican al código PHP dentro de la plataforma Adobe Commerce. Sólo se pueden modificar los datos y objetos específicos que se pasan con el envío de eventos.

#### Cuándo usar un observador

Siempre que esté disponible Si los observadores estuvieran más disponibles y fueran más flexibles, entonces los observadores ocuparían el segundo lugar en esta lista. Los observadores tienen menos sobrecarga de procesamiento que los complementos, están menos disponibles y son menos flexibles.

#### Inconvenientes

Aunque los observadores son una excelente manera de interceptar y modificar el código, el envío de los eventos debe agregarse al código principal o de terceros para que esté disponible para que el código lo escuche. Esto hace que el concepto de usar observadores sea un poco limitado. Se limita a los eventos que un desarrollador tuvo la previsión de incluir en el código.

Además, otro factor limitante de los observadores es que el evento enviado solo proporciona acceso a los datos y objetos específicos que el desarrollador decidió pasar junto con el evento.

### Complemento

Un complemento es un concepto flexible introducido en la plataforma de Adobe Commerce. Le permite interceptar, reemplazar y modificar cualquier método PHP público. Los complementos le permiten modificar los argumentos que van a un método antes de que se ejecute el método de destino, modificar el resultado después de ejecutar el método de destino o reemplazar completamente el método de destino. Puede modificar muchos métodos de una clase PHP dirigida dentro de un solo archivo de plugin. Además, puede utilizar el argumento `$subject` para ejecutar cualquier método público que exista en la clase PHP de destino.

#### Cómo declarar un complemento

Los complementos se pueden configurar en un archivo `di.xml` global o de área específica.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### Qué se puede cambiar con un complemento

Esta funcionalidad solo está disponible para las clases de PHP de destino. Puede cambiar la entrada o salida de un método público y puede utilizar un complemento para almacenar en déclencheur otras funcionalidades. Si varios plugins se dirigen a la misma clase PHP, se puede establecer un orden para la ejecución de plugins para permitir que su plugin se ejecute antes o después de otros plugins.

#### Cuándo utilizar un complemento

Cuando el reemplazo de dependencia no está disponible. Los complementos se utilizan normalmente en la base de código principal y en el código de terceros, y se pueden utilizar comúnmente en su propio código personalizado. Normalmente, cuando debe modificar una funcionalidad que no es propiedad del código personalizado o que no está controlada por él, la mejor opción es utilizar un complemento.

#### Inconvenientes

No se pueden modificar los métodos o propiedades protegidos. La sobrecarga de procesamiento es mayor que la de un observador. Eso no es realmente un argumento para no usar complementos, la diferencia es trivial. Sin embargo, esto es algo bueno para tener en cuenta.

### Sustitución de dependencias

La inyección de dependencias es un concepto de codificación estándar orientado a objetos en el que se pasan las dependencias necesarias a una clase con el constructor. Sin embargo, la plataforma Adobe Commerce va un paso más allá al proporcionar varias formas de sustituir dependencias con XML. Básicamente, sustitución de dependencias. El reemplazo de dependencias no es adecuado para todas las situaciones, pero permite escribir código mínimo, reducir la sobrecarga y puede segmentar únicamente fragmentos de código exactos. Puede modificar los métodos privados y protegidos con reemplazo de dependencia.

#### Cómo utilizar el reemplazo de dependencia

La sustitución de dependencias se puede realizar a nivel global o por áreas específicas.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

Después de seguir estos pasos, habrá modificado correctamente el comportamiento de un método privado.

#### Qué se puede cambiar con la sustitución de dependencias

Los métodos public, protected y private se pueden cambiar con el reemplazo de dependencias. Al igual que con un complemento, puede modificar los argumentos que se utilizan, reemplazar completamente la función o modificar la salida de la función.

#### Cuándo usar el reemplazo de dependencia

Esta es una buena primera opción cuando realmente lograría el objetivo deseado, suponiendo que no se tiene que hacer nada demasiado complejo para implementarlo.

#### Inconvenientes

No muchos. No se puede utilizar en todas las situaciones. El principal inconveniente es que debe ampliar la clase original que contiene la funcionalidad que desea modificar. Eso va en contra del principio de &quot;Composición sobre Herencia&quot;.
