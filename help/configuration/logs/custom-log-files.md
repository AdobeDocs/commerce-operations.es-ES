---
title: Escribir en archivo de registro personalizado
description: Obtenga información sobre cómo crear y configurar archivos de registro personalizados en Adobe Commerce. Descubra los controladores de registro y la implementación de registro personalizada.
feature: Configuration, Logs
badge: label="Gentileza de Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Escribir en un archivo de registro personalizado

El módulo `Magento\Framework\Logger` contiene las siguientes clases de controladores:

| Clase | Archivo de registro |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php) | - |
| [Magento\Framework\Logger\Handler\Debug](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php) | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php) | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php) | - |
| [Magento\Framework\Logger\Handler\System](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php) | `/var/log/system.log` |

Puede encontrarlos en el directorio `lib/internal/Magento/Framework/Logger/Handler`.

Puede utilizar uno de los siguientes métodos para iniciar sesión en un archivo personalizado:

- Configurar un archivo de registro personalizado en `di.xml`
- Configurar un archivo personalizado en la clase de controlador de registrador personalizado

## Configurar un archivo de registro personalizado en `di.xml`

Este ejemplo muestra cómo usar [tipos virtuales](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) para registrar `debug` mensajes en un archivo de registro personalizado en lugar de un `/var/log/debug.log` estándar.

1. En el archivo `di.xml` de su módulo, defina un archivo de registro personalizado como [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   El valor `name` de `Magento\Payment\Model\Method\MyCustomDebug` debe ser único.

1. Defina el controlador en otro [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) con un `name` único:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Inyecte el `MyCustomLogger` [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) en el objeto `Magento\Payment\Model\Method\Logger`:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. La clase virtual `Magento\Payment\Model\Method\MyCustomDebug` se inserta en el controlador `debug` de la propiedad `$logger` en la clase `Magento\Payment\Model\Method\Logger`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Los mensajes de excepción se han registrado en el archivo `/var/log/payment.log`.

## Configurar un archivo de registro personalizado en la clase de controlador del registrador

Este ejemplo muestra cómo utilizar una clase de controlador de registrador personalizada para registrar `error` mensajes en un archivo de registro específico.

1. Cree una clase que registre datos. En este ejemplo, la clase se define en `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Defina el controlador para esta clase como un [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) en el archivo `di.xml` del módulo.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` es un identificador único.

1. En la definición `type`, especifique el nombre de clase donde se inserta el controlador de registrador personalizado. Utilice el nombre de tipo virtual del paso anterior como argumento para este tipo.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Código Source de la clase `Vendor\ModuleName\Observer\MyObserver`:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. La clase `Vendor\ModuleName\Logger\Handler\ErrorHandler` se inserta en el controlador `error` de la propiedad `$logger` en `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Los mensajes de excepción se registran en el archivo `/var/log/my_custom_logger/error.log`.

