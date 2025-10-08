---
title: Descripción general del proceso de actualización
description: Descubra cómo actualizar su proyecto de Adobe Commerce mantiene su tienda segura y eficiente. Descubra las prácticas recomendadas para planificar y ejecutar actualizaciones exitosas.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Descripción general del proceso de actualización

La actualización de su proyecto de Adobe Commerce es fundamental para garantizar que su tienda esté segura, sea compatible con PCI y funcione con la máxima eficiencia. Esta guía le explica las consideraciones clave al prepararse para una actualización.

La guía proporciona información general sobre el recorrido de actualización típico de Adobe Commerce y las prácticas recomendadas que deben seguirse a lo largo de ese recorrido. También se describen detalles técnicos del proceso de actualización con un ejemplo oportuno e instrucciones paso a paso para actualizar a la versión más reciente de Adobe Commerce. Es importante revisar la [programación de versiones](../release/schedule.md) de Adobe Commerce y comenzar a prepararse para las actualizaciones tempranas. Adobe publica la programación de versiones anualmente para facilitar el proceso de planificación de los comerciantes y recomienda actualizar cada ciclo de lanzamiento de parches. Para seguir siendo compatible con PCI, los comerciantes deben estar en el último parche o parche de seguridad.

## ¿Para quién es esta guía?

La audiencia de destino de esta guía incluye:

- **Administradores de comercio electrónico y directores técnicos**: comprenda el recorrido de la actualización, la importancia de actualizarla regularmente y cómo planificarla y prepararla mejor para una actualización.
- **Equipos de operaciones y desarrollo**: Conozca los pasos técnicos necesarios para actualizar a la versión más reciente de Adobe Commerce y las herramientas disponibles que hacen que el proceso sea más fácil, rápido y asequible.

## Proceso de actualización explicado

Es probable que una de las razones por las que eligió Adobe Commerce sea:

- Amplio conjunto de funciones listo para usar
- Funciones de SaaS ofrecidas por separado del código principal
- Oferta sólida de extensiones de Marketplace
- Capacidad única para permitir una flexibilidad infinita para que pueda personalizar su sitio para satisfacer mejor las necesidades de su negocio y de los clientes

Sin embargo, la ventaja de ser un producto altamente ampliable y personalizable puede estimular posibles problemas de actualización cuando las personalizaciones no están codificadas según las prácticas recomendadas, lo que provoca costes de actualización superiores a los esperados.

_Entonces... ¿por qué actualizar?_

La actualización permite a su empresa mantenerse ágil en el acelerado y cambiante sector del comercio electrónico y permite que su plataforma sea compatible con las últimas funciones de Adobe Commerce que maximizan las ventas y las conversiones. La inclusión de actualizaciones en sus planes de mantenimiento habituales es fundamental para garantizar que su tienda esté segura, sea compatible con PCI y funcione con la máxima eficiencia.

### Seguridad

La seguridad es una de las principales razones para la actualización, ya que el 83 % de los incidentes de seguridad se producen en software obsoleto. Según [IBM](https://www.ibm.com/reports/data-breach), el costo promedio de una violación de datos es de 3,86 millones de dólares, mucho más de lo que cuesta mitigar este riesgo mediante la actualización. Adobe ofrece dos formas de mantener la seguridad de su tienda durante todo el año:

- **Versiones de parches**: incluye correcciones de errores de alta prioridad, de seguridad, de rendimiento y de calidad.
- **Versiones de parches de seguridad**: incluye correcciones y mejoras para mantener el sitio seguro y son más fáciles de implementar.

### Rendimiento

El rendimiento es otro de los principales motivos para la actualización. Según [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), los primeros cinco segundos de tiempo de carga tienen un efecto significativo en las tasas de conversión y cada segundo de latencia a partir de entonces tiene un impacto de -4.4%. Esto, junto con el hecho de que la velocidad de la página es un factor de clasificación SEO líder, demuestra por qué el rendimiento del sitio es un elemento crítico de su sitio para mantener y mejorar regularmente. Cada versión del parche incluye mejoras de rendimiento, por lo que aprovechar las nuevas versiones es compatible con sus planes de crecimiento y mantiene a su empresa competitiva.

### Coste del retraso

El motivo para retrasar o aplazar las actualizaciones de la plataforma a menudo se reduce al coste inmediato. Sin embargo, el coste real de ejecutar una versión obsoleta de cualquier software es mucho mayor y puede tener un impacto duradero en una empresa.

Puede parecer ilógico, pero realizar actualizaciones regulares de la plataforma requiere menos esfuerzo general que realizar actualizaciones poco frecuentes debido a la cantidad de deuda técnica acumulada que resulta del retraso. Adobe ha trabajado recientemente con un socio que tiene un comerciante minorista que solía realizar actualizaciones de forma poco frecuente e incoherente (una vez al año o durante más tiempo). Al transformar la forma en que se abordan las actualizaciones y seguir una ruta de actualización regular recomendada por Adobe a lo largo de 12 meses, el socio pudo ahorrar al cliente cuatro semanas de tiempo de desarrollo acumulado, esfuerzo y costes asociados. Estos costes podrían entonces redirigirse a iniciativas para impulsar el crecimiento del negocio.

Cuando las actualizaciones se realizan regularmente, los cambios son incrementales y el esfuerzo de actualización correspondiente lo refleja. Cuando las actualizaciones de la plataforma se aplazan durante un periodo prolongado, pueden convertirse en un proceso mucho más involucrado. Además, las extensiones que utilice de [Adobe Commerce Marketplace](https://marketplace.magento.com/) y otras integraciones de terceros también pueden verse afectadas. Por último, el tiempo que se tarda en investigar, planificar y realizar una actualización retrasada se amplía, lo que añade esfuerzo y costes que se pueden evitar.

Algunos de los factores generales que afectan el nivel de esfuerzo para actualizar su proyecto incluyen, entre otros:

| Complejidad técnica | Planificación y estrategia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Alcance de las personalizaciones | Claridad de los requisitos, decisiones dudosas y alcance lento |
| Número de extensiones | Su frecuencia de actualización |
| Número de integraciones con terceros (OMS, ERP) | Su estrategia de prueba |
| Codificación según las prácticas recomendadas |                                                              |

El crecimiento continuo en el espacio del comercio digital ha ejercido una mayor presión sobre las empresas para que evolucionen más rápido, con más frecuencia y de formas impredecibles. El no mantenerse al día y anticipar el comportamiento de compra de los clientes ha nivelado el campo de juego incluso para las marcas más grandes y establecidas. Debe poder proporcionar experiencias personalizadas y sólidas en todos los puntos de contacto, sin interrupciones en el rendimiento y el tiempo de actividad. Debe ser capaz de innovar más rápido, sin límites, para mantenerse por delante de los competidores globales. Al actualizar, está afianzando su empresa en el futuro y configurándose para atender mejor las necesidades dinámicas de los clientes.
