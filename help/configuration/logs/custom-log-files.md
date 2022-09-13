---
title: Escribir en un archivo de registro personalizado
description: Aprenda a configurar archivos de registro personalizados.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# Escribir en un archivo de registro personalizado

La variable `Magento\Framework\Logger` contiene las siguientes clases de controlador:

| Clase | Archivo de registro |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Puede encontrarlas en la `lib/internal/Magento/Framework/Logger/Handler` directorio.

Puede utilizar uno de los siguientes métodos para iniciar sesión en un archivo personalizado:

- Configure un archivo de registro personalizado en la variable `di.xml`
- Configuración de un archivo personalizado en la clase de controlador del registrador personalizado

## Configure un archivo de registro personalizado en la variable `di.xml`

Este ejemplo muestra cómo utilizar [tipos virtuales](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) para registrar `debug` en un archivo de registro personalizado en lugar de en un `/var/log/debug.log`.

1. En el `di.xml` del módulo, defina un archivo de registro personalizado como [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   La variable `name` valor de `Magento\Payment\Model\Method\MyCustomDebug` debe ser único.

1. Defina el controlador en otro [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) con un `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Inyecte el `MyCustomLogger` [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) en el `Magento\Payment\Model\Method\Logger` objeto:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. La clase virtual `Magento\Payment\Model\Method\MyCustomDebug` se inyecta en la variable `debug` del `$logger` en la variable `Magento\Payment\Model\Method\Logger` Clase .

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Los mensajes de excepción se registran en la `/var/log/payment.log` archivo.

## Configurar un archivo de registro personalizado en la clase del controlador del registrador

Este ejemplo muestra cómo utilizar una clase de controlador de registro personalizada para registrar `error` en un archivo de registro específico.

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

1. Defina el controlador de esta clase como un [tipo virtual](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) en el `di.xml` archivo.

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

1. En el `type` , especifique el nombre de clase donde se inserta el controlador de registro personalizado. Utilice el nombre de tipo virtual del paso anterior como argumento para este tipo.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Código fuente de `Vendor\ModuleName\Observer\MyObserver` Clase :

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

1. La clase `Vendor\ModuleName\Logger\Handler\ErrorHandler` se inyecta en la variable `error` del `$logger` en la variable `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Los mensajes de excepción se registran en la `/var/log/my_custom_logger/error.log` archivo.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
