---
title: Sugerencias de rendimiento de Adobe Commerce para alojamiento propio
description: Obtenga información sobre sugerencias de rendimiento para alojamiento propio, ideas, conceptos y prácticas recomendadas a tener en cuenta.
landing-page-description: Conozca algunos conceptos y cosas que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Conozca las estrategias y los conceptos de consejos de rendimiento para hospedarse usted mismo en Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 66abe9f234aa44f7e07cc024607eeb6591a99d07
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---


# Consejos de rendimiento de Adobe Commerce de alojamiento propio

Usar una plataforma de comercio electrónico flexible y potente no significa que tenga que sacrificar el rendimiento. Desde el inicio de Adobe Commerce, se han realizado numerosas mejoras en la aplicación principal. En la versión 2.5.4, el equipo de ingeniería de Adobe Commerce realizó una prueba de conjunto para comparar la aplicación. Los resultados de la prueba demostraron que Adobe Commerce es capaz de gestionar un amplio catálogo de más de 240 millones de SKU, que los tiempos de solicitud de la API son un promedio excepcional de 300 ms y que el número de vistas de página y pedidos realizados por hora es fenomenal, ya que llegan a 2 millones de vistas de página y 208.000 pedidos por hora.

Consulte los últimos resultados de referencia pasando a [Experience League - Adobe Commerce - Manual de implementación - Puntos de referencia](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Para mantener las cosas lo más óptimas posible, siga estos estándares al agregar personalizaciones y complejidad adicional al proyecto.

Las siguientes secciones tratan sobre temas a considerar y consejos para optimizar la implementación de alojamiento propio.

## Varniz

Varnish es un proxy inverso HTTP con caché. Por más complicado que parezca, el resultado son respuestas rápidas para garantizar que las solicitudes se devuelvan más rápido que si tuviera que recuperar el elemento del origen. Si ejecuta un sitio de Adobe Commerce sin alguna versión de Varnish, la carga de las páginas será más lenta y se utilizarán otras métricas clave. Varnish puede ser un poco difícil de configurar y administrar usted mismo, sin embargo tenemos este tema en Experience League [Configuración de barniz](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} para comprender mejor su uso con Adobe Commerce. Una alternativa es usar una solución basada en la nube. Aunque hay muchos que considerar, Finfinito fue elegido como la solución para Adobe Commerce en la nube. Es una versión de Finfinito, basada en la nube, que utiliza VCLs y muchas facetas de barniz.

Encontrar una solución que se adapte mejor a sus capacidades técnicas, presupuestarias, de configuración y de aplicación es difícil de lograr. El uso de una opción basada en la nube hace que todas las partes duras desaparezcan en la medida en que se tengan en cuenta los componentes de administración, configuración, servidores y otras infraestructuras. El equipo de Adobe Commerce en la nube lo eligió como solución debido a su rendimiento, escalabilidad, rendimiento y muchas otras métricas clave.

Al elegir una buena solución para su proyecto con respecto a Varnish, se está configurando para obtener el mejor rendimiento para sus clientes y para evitar que la aplicación de comercio trabaje más duro de lo que debe.

## CDN

Junto con Varnish como un recurso valioso para su proyecto de Adobe Commerce, la siguiente línea es una CDN. Junto con su Varnish, una CDN puede proporcionar instancias en caché para su CSS, recursos de página como imágenes para ayudar a reducir el ancho de banda que llega a su aplicación Adobe Commerce. Puede almacenar en caché las respuestas de GraphQL que aumentan las ventajas de un sitio Adobe Commerce sin objetivos. Algunas CDN proporcionan optimización de imágenes, un cortafuegos de aplicaciones web y otras funciones.

Adobe Commerce on cloud eligió usar Finfinito para su caché de Varnish pero también como su CDN. Esta única solución ofrece una gran cantidad de funciones para ofrecer una buena experiencia para Adobe Commerce en los clientes de la nube. Puede leer la descripción general de los servicios de FAdministración en Experience League [Información general sobre servicios rápidos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Una CDN proporciona contenido de entrega optimizado y seguro para el proyecto Adobe Commerce. Cuando este componente puede no ser obligatorio para su proyecto, debe considerarse a medida que el sitio madure y aumente la cantidad de visitantes. Al proporcionar una CDN, puede retrasar la adición de hardware adicional a la infraestructura o la ampliación de la infraestructura existente debido a la carga eliminada de cada solicitud.

## Deshabilitar módulos

Se debe considerar la desactivación de un módulo que no esté en uso, pero no tomarlo a la ligera. Esta técnica reduce la sobrecarga y el tiempo de procesamiento de algunas solicitudes, pero hay efectos secundarios que deben tenerse en cuenta. A menudo hay ocasiones en que un desarrollador asume que un módulo está disponible al crear funcionalidad. Esto suele ser seguro, a menos que opten por utilizar algunas clases que se encuentran en un módulo que está deshabilitado.

Desactivar un módulo como el &quot;boletín&quot; nativo es un evento bastante común. Esto ocurre especialmente cuando el propietario de la tienda tiene una empresa de terceros que administra la newsletter. Donde esto puede ser un problema es cuando se instala un módulo de terceros y por alguna razón decidieron usar una clase del boletín informativo. Es probable que esta dependencia accidental se capture durante alguna instalación inicial y prueba, pero entonces se verá obligado a decidir si desea mantener este módulo de terceros, habilitar el boletín y, a continuación, probar la regresión en el sitio buscando cualquier comportamiento extraño que se introduzca. O encuentra un reemplazo para ese módulo de terceros. Ambas decisiones vienen con riesgo, tiempo y posiblemente errores.

Antes de desactivar los módulos no utilizados, asegúrese de que no dispone de pruebas como la unidad, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} pruebas de carga o solicitudes de API que pueden verse afectadas.

## Requerir que se sigan los estándares de codificación Adobe Commerce y PHP para cada solicitud de extracción

Adobe Commerce tiene un conjunto de [Normas de codificación](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Ayudan a garantizar que se siga un patrón, estilo y diseño esperado similares independientemente del tipo de desarrollo de software. Lo que es un requisito de absolución a seguir es cuando contribuye al código base de Adobe Commerce. Sin embargo, seguir esta metodología para el desarrollo personalizado también constituye un pilar sólido para todos los desarrolladores, actuales y futuros, que pueden esperar. Cuando se requiere que todas las solicitudes de extracción pasen un código estándar, se garantiza que todos entiendan y esperen los mismos patrones de desarrollo coherentes.

Para acompañar a los estándares de codificación de Adobe Commerce, la otra base utilizada son los estándares básicos de codificación de PHP. Debe estar claramente definido en las guías del desarrollador qué estándares debe seguir y cualquier desviación que sea aceptable. Sin embargo, una alternativa debería ser la guía que se mantiene públicamente en [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Una postura firme sobre el seguimiento de PSR-1 y PSR-12. Asegurarse de que los desarrolladores que contribuyen al proyecto sigan estos pasos ayuda a garantizar que no haya archivos y patrones extrañamente estructurados. Esto también ayuda a garantizar que los futuros desarrolladores puedan leer y comprender rápidamente el código que están revisando. Cuanto más se sigan estos patrones y estándares de codificación, más fácil será leer y más rápido implementar los futuros esfuerzos de desarrollo.

## Ejecutar pruebas de carga después de cada implementación

Puede parecer excesivo realizar una prueba de carga después de cada implementación. Sin embargo, si se sigue esta metodología, se puede hacer un seguimiento y mitigar la oportunidad de que las funciones recién introducidas causen una disminución del rendimiento.

Además de detectar la degradación en el rendimiento a partir del nuevo código, tener una referencia histórica de las métricas clave de su sitio puede ayudar a proporcionar información sobre cuándo se habilita una nueva herramienta o una infraestructura de cambio. Por ejemplo, antes de pagar a la empresa de alojamiento para que aumente el tamaño del entorno y esperar que obtenga el aumento de rendimiento esperado, puede configurar un entorno de ensayo con las nuevas configuraciones y ejecutar una prueba de carga para ver cuál sería el resultado real.

Estas pruebas pueden automatizarse y formar parte de la canalización de CI/CD. Debido a esto, también puede tener reglas en su lugar que tomen los resultados y posiblemente bloqueen la combinación de características si se produce demasiada desviación de la norma. El número de casos de uso de estos datos es ilimitado, pero sin iniciar este proceso es posible que nunca se dé cuenta de su potencial.

Adobe Commerce tiene una buena escritura sobre este tema que se encuentra en el Experience League [Consejos de pruebas de rendimiento](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
