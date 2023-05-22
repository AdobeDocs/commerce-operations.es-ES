---
title: Interfaz de registrador
description: Introducción a la interfaz del registrador.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Interfaz de registrador

Para comenzar a trabajar con un registrador, debe crear una instancia de `\Psr\Log\LoggerInterface`. Con esta interfaz, puede llamar a las siguientes funciones para escribir datos en los archivos de registro:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notify()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Una forma de hacerlo se explica en la sección [Registrar actividad de base de datos](../logs/database-activity.md) ejemplo.

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

El ejemplo anterior muestra que `SomeModel` recibe un `\Psr\Log\LoggerInterface` objeto mediante inyección de constructor. En un método `doSomething`, si se produce algún error, se registra en un método `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) define ocho niveles de registro (depurar, información, aviso, advertencia, error, crítico, alerta y emergencia).
