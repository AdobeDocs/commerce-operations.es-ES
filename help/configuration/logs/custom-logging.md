---
title: Registro personalizado
description: Obtenga información sobre cómo investigar errores mediante el registro personalizado.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Resumen del registro personalizado

Los registros proporcionan visibilidad de los procesos del sistema; por ejemplo, la información de depuración que le ayuda a comprender cuándo se produjo un error o qué provocó el error.

Este tema se centra en el registro basado en archivos, aunque Commerce proporciona la flexibilidad para almacenar registros también en la base de datos.

Adobe recomienda utilizar el registro centralizado de aplicaciones por los siguientes motivos:

- Permite el almacenamiento de registros en un servidor distinto del servidor de aplicaciones y disminuye las operaciones de E/S del disco, lo que simplifica la compatibilidad con el servidor de aplicaciones.

- Hace que el procesamiento de los datos de registros sea más eficaz mediante herramientas especiales, como [Logstash], [Logplex] o [fluentd], sin afectar a un servidor de producción.

  >[!INFO]
  >
  >Adobe no recomienda ni respalda ninguna solución de registro en particular.

## Compatibilidad con PSR-3

El [estándar PSR-3][laminas] define una interfaz PHP común para las bibliotecas de registro. El objetivo principal de PSR-3 es permitir que las bibliotecas reciban un objeto `Psr\Log\LoggerInterface` y escriban registros en él de una manera simple y universal.

Esto permite reemplazar la implementación fácilmente sin tener que preocuparse de que dicha sustitución pueda dañar el código de la aplicación. También garantiza que un componente personalizado funcionará incluso cuando la implementación de registro se cambie en una versión futura del sistema.

## Monólogo

Commerce 2 cumple con el estándar PSR-3. De manera predeterminada, Commerce usa [Monólogo]. Monólogo implementado como preferencia para `Psr\Log\LoggerInterface` en la aplicación de Commerce [`di.xml`][di].

Monolog es una popular solución de registro de PHP con una amplia gama de controladores que le permiten construir estrategias de registro avanzadas. A continuación se muestra un resumen del funcionamiento de Monolog.

Un registrador _logger_ en monólogo es un canal que tiene su propio conjunto de _controladores_. Monólogo tiene muchos controladores, incluidos:

- Registro en archivos y syslog
- Envío de alertas y correos electrónicos
- Registrar servidores específicos y registros en red
- Inicio de sesión en desarrollo (integración con FireBug y Chrome Logger, entre otros)
- Registro en la base de datos

Cada controlador puede procesar el mensaje de entrada y detener la propagación o pasar el control al siguiente controlador de una cadena.

Los mensajes de registro se pueden procesar de muchas maneras diferentes. Por ejemplo, puede almacenar toda la información de depuración en un archivo del disco, colocar los mensajes con niveles de registro más altos en una base de datos y, finalmente, enviar mensajes con el nivel de registro &quot;crítico&quot; por correo electrónico.

Otros canales pueden tener un conjunto diferente de controladores y lógica.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluido]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monólogo]: https://github.com/Seldaek/monolog
