---
title: Sugerencias de rendimiento de Adobe Commerce con alojamiento propio
description: Obtenga información sobre sugerencias, conceptos y prácticas recomendadas de rendimiento de alojamiento propio que debe tener en cuenta.
landing-page-description: Conozca algunos conceptos y cosas que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Conozca las estrategias y los conceptos de sugerencias de rendimiento para alojar Adobe Commerce usted mismo.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Consejos de rendimiento de Adobe Commerce con alojamiento propio

El uso de una plataforma de comercio electrónico flexible y potente no significa que tenga que sacrificar el rendimiento. Se han realizado numerosas mejoras en la aplicación principal desde el inicio de Adobe Commerce. En la versión 2.5.4, el equipo de ingeniería de Adobe Commerce realizó una prueba de conjunto para comparar la aplicación. Los resultados de la prueba demostraron que Adobe Commerce es capaz de gestionar un gran catálogo de más de 240 millones de SKU, los tiempos de solicitud de API son excepcionales promediando 300 ms, y el número de vistas de página y pedidos realizados por hora es fenomenal, llegando a los 2 millones de vistas de página y 208.000 pedidos por hora.

Consulte los últimos resultados de referencia dirigiéndose a [Experience League - Adobe Commerce - Guía de implementación - Puntos de referencia](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Para mantener las cosas lo más óptimas posible, siga estos estándares al agregar personalizaciones y complejidad adicional al proyecto.

Las secciones siguientes tratan temas que deben tenerse en cuenta y consejos para optimizar la implementación de alojamiento propio.

## Barniz

El barniz es un proxy inverso HTTP con caché. Por complicado que pueda parecer, el resultado son respuestas rápidas para ayudar a garantizar que las solicitudes se devuelvan más rápido que si tuviera que recuperar el elemento del origen. La ejecución de un sitio de Adobe Commerce sin alguna versión de Barniz hará que las cargas de página sean más lentas y que se utilicen otras métricas clave. Barniz puede ser un poco difícil de configurar y administrar por sí mismo, sin embargo, tenemos este tema en Experience League [Configurar barniz](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} para comprender mejor su uso con Adobe Commerce. Una alternativa es utilizar una solución basada en la nube. Aunque hay muchos que considerar, Fastly se eligió como solución para Adobe Commerce en la nube. Es una versión de Fastly, basada en la nube, que utiliza VCLs y muchas facetas de barniz.

Es difícil encontrar una solución que se adapte mejor a su aplicación, configuración, presupuesto y capacidades técnicas. El uso de una opción basada en la nube hace que todas las partes duras desaparezcan en la medida en que se consideren los componentes de administración, configuración, servidores y otros componentes de infraestructura. El equipo de Adobe Commerce en la nube lo eligió como solución debido a su rendimiento, escalabilidad, rendimiento y muchas otras métricas clave.

Al elegir una buena solución para su proyecto con respecto a Varnish, se está configurando para el mejor rendimiento para sus clientes y ahorrando que la aplicación de comercio trabaje más de lo que debe.

## CDN

Además de ser un valioso activo para su proyecto de Adobe Commerce, lo siguiente en la línea es una CDN. Junto con su Barniz, una CDN puede proporcionar instancias en caché para su CSS, recursos de página como imágenes para ayudar a reducir el ancho de banda que llega a su aplicación de Adobe Commerce. Puede almacenar en caché las respuestas de GraphQL y aumentar las ventajas de un sitio de Adobe Commerce sin encabezado. Algunas CDN proporcionan optimización de imágenes, un cortafuegos de aplicaciones web y otras funciones.

Adobe Commerce en la nube eligió usar Fastly para su caché de Varnish, pero también como su CDN. Esta solución única proporciona una gran variedad de funciones para proporcionar una buena experiencia a Adobe Commerce en los clientes de la nube. Puede leer la información general de los servicios de Fastly en Experience League [Resumen de servicios rápidos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Una CDN proporciona contenido de envío optimizado y seguro para el proyecto de Adobe Commerce. Si este puede no ser un componente necesario para el proyecto, debe considerarse a medida que el sitio madura y aumenta la cantidad de visitantes. Al proporcionar una CDN, puede retrasar la adición de hardware adicional a la infraestructura o ampliar la infraestructura existente debido a la carga eliminada de cada solicitud.

## Deshabilitar módulos

La desactivación de un módulo que no se utilice debe considerarse, pero no tomarse a la ligera. Esta técnica reduce algunos gastos generales y el tiempo de procesamiento de algunas solicitudes, pero hay efectos secundarios que deben tenerse en cuenta. A menudo, hay ocasiones en que un desarrollador supone que hay un módulo disponible al crear funcionalidades. Esto suele ser seguro, a menos que elijan usar algunas clases que se encuentran en un módulo que estaba deshabilitado.

Deshabilitar un módulo como el &quot;boletín informativo&quot; nativo es un evento bastante común. Esto es cierto especialmente cuando el propietario de la tienda tiene una empresa de terceros que administra su boletín informativo. Esto puede suponer un problema si se instala un módulo de terceros y, por alguna razón, se decide utilizar una clase del boletín informativo. Es probable que esta dependencia accidental se vea afectada durante alguna instalación y prueba iniciales, pero entonces se ve obligado a decidir si desea mantener este módulo de terceros, habilitar la newsletter y luego la regresión de probar el sitio en busca de cualquier comportamiento extraño que se introduce. O encuentra un reemplazo para ese módulo de terceros. Ambas decisiones conllevan riesgos, tiempo y posiblemente errores.

Antes de deshabilitar los módulos no utilizados, asegúrese de que no tiene ninguna prueba, como la unidad, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} pruebas de carga o solicitudes de API que puedan verse afectadas.

## Requerir que se sigan los estándares de codificación Adobe Commerce y PHP para cada solicitud de extracción

Adobe Commerce tiene un conjunto de [Estándares de codificación](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Esto ayuda a garantizar que se siga un patrón, un estilo y un diseño similares independientemente del tipo de desarrollo de software. Esto es un requisito al contribuir al código base de Adobe Commerce. Sin embargo, si decide seguir esta metodología, el desarrollo personalizado establece una base sólida para todos los desarrolladores, tanto actuales como futuros. Cuando se requiere que todas las solicitudes de extracción pasen un estándar de código, se garantiza que todos puedan comprender y esperar los mismos patrones de desarrollo coherentes.

Para acompañar los estándares de codificación de Adobe Commerce, la otra base utilizada son los estándares de codificación básicos de PHP. Se debe definir claramente en las guías del desarrollador qué estándares se deben seguir y las desviaciones que sean aceptables. Sin embargo, se debe hacer una reserva a la guía de mantenimiento público que se encuentra en [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Una postura firme en el seguimiento de PSR-1 y PSR-12. Garantizar que los desarrolladores que contribuyen al proyecto sigan estos pasos ayuda a garantizar que no haya archivos y patrones extrañamente estructurados. Esto también ayuda a garantizar que los futuros desarrolladores puedan leer y comprender rápidamente el código que están revisando. Cuanto más se sigan estos patrones y estándares de codificación, más fácil será leer y aplicar los esfuerzos de desarrollo futuros.

## Ejecutar pruebas de carga después de cada implementación

Realizar una prueba de carga después de cada implementación puede parecer excesivo. Sin embargo, si se sigue esta metodología, se puede hacer un seguimiento y mitigar la oportunidad de que las nuevas funciones que causan una disminución en el rendimiento se introduzcan.

Además de detectar una degradación en el rendimiento a partir del nuevo código, tener una referencia histórica de métricas clave de su sitio puede ayudar a proporcionar perspectiva sobre cuándo se habilita una nueva herramienta o una infraestructura de cambios. Por ejemplo, antes de pagar a la empresa de alojamiento para que amplíe su entorno y espere que obtenga el aumento de rendimiento que espera, puede configurar un entorno de ensayo con las nuevas configuraciones y ejecutar una prueba de carga para ver cuál sería el resultado real.

Estas pruebas pueden automatizarse y formar parte de la canalización de CI/CD. Debido a esto, también puede tener reglas que tomen los resultados y que potencialmente bloqueen la combinación de características si se produce demasiada desviación de la norma. El número de casos de uso de estos datos es ilimitado, pero sin iniciar este proceso es posible que nunca se dé cuenta de su potencial.

Adobe Commerce tiene una buena revisión de este tema que se encuentra en Experience League [Consejos de prueba de rendimiento](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
