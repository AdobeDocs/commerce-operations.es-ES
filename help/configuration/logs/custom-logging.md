---
title: Registro personalizado
description: Obtenga información sobre cómo investigar errores mediante el registro personalizado basado en archivos en Adobe Commerce, incluida la conformidad con PSR-3 y las consideraciones de registro centralizado.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%
---
# Resumen del registro personalizado

Los registros proporcionan visibilidad de los procesos del sistema; por ejemplo, la información de depuración que le ayuda a comprender cuándo se produjo un error o qué provocó el error.

Este tema se centra en el registro basado en archivos, aunque Commerce proporciona la flexibilidad para almacenar registros también en la base de datos.

Adobe recomienda utilizar el registro centralizado de aplicaciones por los siguientes motivos:

- Permite el almacenamiento de registros en un servidor distinto del servidor de aplicaciones y disminuye las operaciones de E/S del disco, lo que simplifica la compatibilidad con el servidor de aplicaciones.

- Hace que el procesamiento de los datos de registros sea más eficaz mediante herramientas especiales, como [Logstash](https://www.elastic.co/products/logstash), [Logplex](https://devcenter.heroku.com/articles/logplex) o [fluentd](https://www.fluentd.org/), sin afectar a un servidor de producción.

  >[!INFO]
  >
  >Adobe no recomienda ni respalda ninguna solución de registro en particular.

## Compatibilidad con PSR-3

El [estándar PSR-3](https://docs.laminas.dev/laminas-log/) define una interfaz PHP común para las bibliotecas de registro. El objetivo principal de PSR-3 es permitir que las bibliotecas reciban un objeto `Psr\Log\LoggerInterface` y escriban registros en él de una manera simple y universal.

Esto permite reemplazar la implementación fácilmente sin tener que preocuparse de que dicha sustitución pueda dañar el código de la aplicación. También garantiza que un componente personalizado funcionará incluso cuando la implementación de registro se cambie en una versión futura del sistema.

## Monólogo

Commerce 2 cumple con el estándar PSR-3. De manera predeterminada, Commerce usa [Monólogo](https://github.com/Seldaek/monolog). Monólogo implementado como preferencia para `Psr\Log\LoggerInterface` en la aplicación de Commerce [`di.xml`](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9).

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

