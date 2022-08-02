---
title: Interfaz de registrador
description: Introducción a la interfaz del registrador.
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Interfaz de registrador

Para empezar a trabajar con un registrador, debe crear una instancia de `\Psr\Log\LoggerInterface`. Con esta interfaz, puede llamar a las siguientes funciones para escribir datos en los archivos de registro:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Una forma de hacerlo se explica en la [Actividad de la base de datos de registro](../logs/database-activity.md) ejemplo.

A continuación se muestra otra manera:

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

El ejemplo anterior muestra que `SomeModel` recibe un `\Psr\Log\LoggerInterface` mediante inyección de constructor. En un método `doSomething`, si se ha producido algún error, se registra en un método `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) define ocho niveles de registro (depuración, información, aviso, advertencia, error, crítico, alerta y emergencia).
