---
title: Registro personalizado
description: Obtenga información sobre cómo investigar errores mediante el registro personalizado.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Información general de registro personalizado

Los registros dan visibilidad a los procesos del sistema; por ejemplo, información de depuración que le ayudará a comprender cuándo se produjo un error o qué provocó el error.

Este tema se centra en el registro basado en archivos, aunque Commerce proporciona la flexibilidad para almacenar registros también en la base de datos.

Adobe recomienda utilizar el registro centralizado de aplicaciones por los siguientes motivos:

- Permite el almacenamiento de registros en un servidor que no sea el servidor de aplicaciones y disminuye las operaciones de E/S de disco, lo que simplifica el soporte del servidor de aplicaciones.

- Hace que el procesamiento de los datos de registro sea más eficaz mediante el uso de herramientas especiales, como [Logstash], [Logplex]o [fluentd]: sin impacto en un servidor de producción.

   >[!INFO]
   >
   >Adobe no recomienda ni respalda ninguna solución de registro en particular.

## Compatibilidad con PSR-3

La variable [PSR-3 estándar][laminas] define una interfaz PHP común para el registro de bibliotecas. El objetivo principal de PSR-3 es permitir que las bibliotecas reciban un `Psr\Log\LoggerInterface` logs de objeto y escritura en él de una manera simple y universal.

Esto permite reemplazar la implementación fácilmente sin tener que preocuparse de que dicha sustitución pueda romper el código de la aplicación. También garantiza que un componente personalizado funcionará incluso cuando la implementación de registro se cambie en una versión futura del sistema.

## Monólogo

Commerce 2 cumple con el estándar PSR-3. De forma predeterminada, Commerce utiliza [Monólogo]. Monólogo implementado como preferencia para `Psr\Log\LoggerInterface` en la aplicación Commerce [`di.xml`][di].

Monolog es una popular solución de registro PHP con una amplia gama de controladores que le permiten crear estrategias de registro avanzadas. A continuación se muestra un resumen del funcionamiento de Monolog.

Un monólogo _logger_ es un canal que tiene su propio conjunto de _controladores_. Monolog tiene muchos controladores, entre ellos:

- Registro en archivos y syslog
- Enviar alertas y correos electrónicos
- Registros específicos de servidores y registro en red
- Inicio de sesión en desarrollo (integración con FireBug y Chrome Logger, entre otros)
- Iniciar sesión en la base de datos

Cada controlador puede procesar el mensaje de entrada y detener la propagación o pasar el control al siguiente controlador de una cadena.

Los mensajes de registro se pueden procesar de diferentes maneras. Por ejemplo, puede almacenar toda la información de depuración en un archivo en disco, colocar los mensajes con niveles de registro más altos en una base de datos y, finalmente, enviar mensajes con el nivel de registro &quot;crítico&quot; por correo electrónico.

Otros canales pueden tener un conjunto diferente de controladores y lógica.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluentd]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monólogo]: https://github.com/Seldaek/monolog
