---
title: Interfaz de registrador
description: Aprenda a utilizar la interfaz del registrador en Adobe Commerce para el registro personalizado. Descubra la implementación de PSR-3 y las funciones de registro.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Interfaz de registrador

Para comenzar a trabajar con un registrador, debe crear una instancia de `\Psr\Log\LoggerInterface`. Con esta interfaz, puede llamar a las siguientes funciones para escribir datos en los archivos de registro:

- [alerta()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [crítico()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergencia()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [información()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [aviso()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [advertencia()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Una forma de hacerlo se explica en el ejemplo [Registrar actividad de base de datos](../logs/database-activity.md).

Otra manera sigue:

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

El ejemplo anterior muestra que `SomeModel` recibe un objeto `\Psr\Log\LoggerInterface` mediante inyección de constructor. En un método `doSomething`, si se produjo algún error, se registra en un método `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) define ocho niveles de registro (depurar, información, aviso, advertencia, error, crítico, alerta y emergencia).
