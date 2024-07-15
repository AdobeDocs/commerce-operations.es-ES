---
title: Herramientas de monitorización de Adobe Commerce con alojamiento propio
description: Obtenga información acerca de las herramientas de monitorización de alojamiento propio, las ideas y los conceptos, y las prácticas recomendadas que debe tener en cuenta.
landing-page-description: Conozca algunos conceptos y cosas de las herramientas de monitorización que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos de herramientas de monitorización para alojar Adobe Commerce usted mismo.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 5aa03f91-1240-47f6-8d06-b06e64973266
feature: Install, Logs, Observability
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# Herramientas y telemetría de monitorización de Adobe Commerce con alojamiento propio

El uso de herramientas de monitorización ofrece la oportunidad de detectar cambios sin tener que pagar a alguien para que vea todo el tiempo. Con la mayoría de las herramientas, puede agregar alertas y notificaciones si se alcanza un umbral, como cuando un disco duro se queda sin espacio. Algunas herramientas proporcionan resultados que se deben rastrear y calcular, como los resultados de las pruebas de carga. Independientemente de la herramienta, cada herramienta tiene un propósito y, cuando se utiliza de forma coherente, pueden ayudarle a administrar su aplicación. Hay opciones gratuitas para cada herramienta, pero recuerde que pagar por un servicio a menudo garantiza un soporte más rápido y confiable y puede valer la pena la inversión. New Relic es un ejemplo de una herramienta que ofrece un nivel gratuito y una versión de pago que desbloquea mucha más potencia y capacidades. Hay otros como DataDog o Dynatrace. Encuentre una buena opción y úsela de manera consistente.

## Monitorización de infraestructura

El término infraestructura se utiliza de forma bastante flexible para este contexto. Para este tema, esto significa cualquier servidor, proceso o dispositivo que se utilice para hacer funcionar el sitio. Por ejemplo:

* Discos duros
* uso de CPU
* Uso de RAM
* Redis
* Carga media por servidor
* tráfico de red

Umbrales de investigación para crear alertas efectivas. No asigne una para las cosas importantes, como la capacidad del disco duro. Configure algunas para notificar a diferentes grupos a medida que las cosas empeoren. Por ejemplo, aquí hay un conjunto de reglas cuando un disco duro se está llenando.

* Notificación del Slack del 70 % al canal DevOps
* 80% Notificar al canal DevOps de la sala de Slack y una lista de distribución por correo electrónico de compañeros de equipo de DevOps
* 90% Notificar al Slack del canal DevOps y al canal del Slack de soporte de producción, al grupo de distribución de DevOps por correo electrónico y al administrador de ingeniería
* 95% Notificar al Slack DevOps y canales de Slack de soporte de producción, lista de distribución por correo electrónico de todos los ingenieros y Director de ingeniería
* 98% Notificar a cualquier canal de Slack P1 y DevOps y canales de Slack de soporte de producción, lista de distribución por correo electrónico de ingenieros y Director de ingeniería y vicepresidente de tecnología

Hay muchas maneras de notificar a un equipo, así que asegúrese de elegir uno que sea confiable y no se inunde con demasiadas alertas. Es importante reservar las alertas para cuando importen; de lo contrario, corre el riesgo de saturarse y empezar a ignorar las alertas.

A menudo, hay buenas plantillas que seguir para la mayoría de las herramientas, como New Relic, DataDog y Dynatrace. Tómese un tiempo para encontrar buenas ideas que tengan más sentido para su aplicación. Con Adobe Commerce en la infraestructura en la nube, existen alertas y déclencheur cuando se aprovisiona el proyecto. Esto permite al equipo de soporte de producción de Adobe aplicar sus herramientas para el tiempo de actividad y la monitorización de alta disponibilidad.

Los paneles proporcionan un acceso rápido a los aspectos frecuentes o importantes del sitio. Los elementos de panel pueden consistir en vistas de página, uso de CPU por host, lista de todos los servidores, tiempos de carga de las páginas, duraciones de las transacciones e incluso resultados de pruebas de monitorización sintéticas de los últimos días. Estos paneles deben crearse para permitir una clasificación rápida en caso de que algo esté mal o deben configurarse diferentes paneles para diferentes experiencias de usuario. Esperamos que pueda diseñar varios paneles y disfrutar de la monitorización de su aplicación en tiempo real. Es muy satisfactorio, especialmente cuando el propietario del proyecto o un gerente le pregunta cómo funciona el sitio, y usted puede encontrar la respuesta en segundos, no en horas.

## Agregación y rotación de registros

Los archivos de registro se encuentran en servidores de aplicaciones que procesan solicitudes o registros MySQL cuando las cosas tardan demasiado en ejecutarse. Lo difícil de los registros es que están separados entre sí y encontrarlos todos, analizar la información de cada registro puede ser engorroso. Hace muchos años, este problema se resolvió mediante una técnica llamada _agregación de registros_. Esto toma archivos de registro de todas las ubicaciones de registro y los lleva a una ubicación centralizada. Una vez que se mueven los datos, un programa puede leerlos y proporcionar formas de buscar, filtrar y revisar la información. Esto puede ser un proceso difícil para hacer las cosas bien. Hay muchas opciones, pero si tiene suerte, las herramientas de monitorización pueden leer y agregar sus archivos de registro, como New Relic. Al encontrar una buena herramienta, puede ahorrarse una cantidad de tiempo inmensurable en el futuro. A menos que tenga un solo servidor que haga todo lo posible para que el sitio funcione y funcione, es esencial disponer de agregación de registros. Esto es especialmente útil cuando intenta averiguar si está bajo un ataque DDoS o experimentando un pico de tráfico legítimo, o cuando investiga por qué una determinada solicitud está fallando.

Otra pieza clave para los registros es garantizar que la rotación se produzca. Históricamente, esto pertenece a `run-away logs`, que puede rellenar accidentalmente el disco duro y provocar que el sitio se cierre. Se puede producir una versión de rotación del registro cuando un archivo de registro alcanza un tamaño determinado, como 1 GB. Hay herramientas de nivel de servidor como `logrotate` que pueden eliminarlas automáticamente. Por ejemplo, puede eliminar archivos de registro excesivamente grandes una vez que superen los 1 GB o archivos de registro anteriores a 90 días. Define una directiva de registro, por lo que es importante comprender sus limitaciones de recursos.

## Análisis de malware

Muchas empresas de alojamiento web dedicadas a Adobe Commerce tendrían una biblioteca de vulnerabilidades y malware conocidos. Deben ofrecer un análisis automáticamente o bajo petición. Cuando estos son efectivos, son reaccionarios y solo funcionan cuando se detecta nuevo malware. Puede ser una buena idea tener una herramienta proactiva que pueda buscar en el código y la base de datos malware conocido. Hay algunas opciones disponibles, como [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"} o [analizador de malware para Magento](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Pueden realizar un análisis remoto desde el exterior o instalarse y actualizar/analizar/monitorizar de forma proactiva después de configurarse en los servidores. Estas pueden ser una gran opción, ya que su biblioteca se actualiza constantemente, ya que se instalan y monitorizan miles de sitios si elige una solución proporcionada, como Sansec. A medida que se detecta un nuevo malware, cada proyecto que monitorizan se beneficia de la información y ahora son alertados si se detecta.

Hay algunas versiones gratuitas a tener en cuenta, pero para el malware, realmente debe considerar una solución de pago. Esta puede ser la diferencia entre que su sitio esté infectado durante unos minutos y que haya estado infectado durante unos pocos meses. Tener una explotación en su sitio causa enormes dolores de cabeza, esta es una área que debe considerar pagar por un servicio.

## Adobe de la herramienta de análisis de todo el sitio

La herramienta de análisis de todo el sitio es una herramienta de autoservicio proactiva y un repositorio central que incluye información detallada del sistema y recomendaciones para garantizar la seguridad y la operabilidad de la instalación de Adobe Commerce. Proporciona monitorización del rendimiento, informes y consejos en tiempo real las 24 horas del día, los 7 días de la semana para identificar posibles problemas y una mejor visibilidad de las configuraciones de salud, seguridad y aplicaciones del sitio. Ayuda a reducir el tiempo de resolución y a mejorar la estabilidad y el rendimiento del sitio.

La página de Recommendations de la herramienta de análisis de todo el sitio enumera recomendaciones basadas en prácticas recomendadas para abordar los problemas detectados en el sitio. Las recomendaciones se ordenan por prioridad PO a P4, donde PO es crítico y P4 es bajo. Los resultados incluyen descripción, recomendación, impacto del sitio, causa raíz, escenarios/condiciones previas, resultado esperado y herramientas utilizadas.

Conozca las prácticas recomendadas para mejorar el rendimiento del sitio. Rastree e implemente las recomendaciones enumeradas según su prioridad.

Para obtener más información sobre cómo instalar esto en su proyecto, visite [Guía de instalación de la herramienta de análisis de todo el sitio](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Supervisión SSL

Uno de los elementos más olvidados de un proyecto es el certificado SSL. Solo necesitan atención una vez al año, así que olvidarlas es muy fácil. La caducidad del certificado de seguridad podría provocar que los exploradores modernos adviertan o rechacen mostrar las páginas del sitio. Los clientes pueden empezar a enviar correos electrónicos o llamar al servicio de asistencia si experimentan un problema de este tipo, y es posible que no pueda operar hasta que se resuelva. Cada minuto cuenta, por lo que reconocer la caducidad es adelantarse a tiempo y asegurarse de que las cosas se renueven es primordial para mantener el sitio en funcionamiento. Existen muchas maneras de realizar la monitorización SSL. Considere la posibilidad de utilizar herramientas de monitorización sintéticas para su sitio, utilizando herramientas gratuitas o de bajo coste como PKingdom, Keybox o Sucuri e incluso suscribirse a un servicio que ofrezca alertas de caducidad de certificados SSL. Estas sencillas herramientas pueden garantizar que los certificados del sitio sean válidos y reducir el riesgo de tiempo de inactividad para los clientes.

## Pruebas automatizadas

Realizar pruebas automatizadas, como pruebas funcionales o pruebas unitarias, suele ayudar a detectar problemas en el código recién introducido. Es posible que estas pruebas no lo capten todo, ya que las pruebas unitarias y de Adobe Commerce suelen tener una cobertura inferior al 50 %. Esto no significa que deba evitar escribirlos y probarlos. Estas herramientas están aquí para agregar otra capa de seguridad y que todo lo que se compromete no afecte negativamente a las pruebas predeterminadas y a las personalizadas que cree su equipo de desarrollo. Al ejecutar estas pruebas en cada implementación, los problemas principales se detectan antes de tiempo y evitan que las cosas pasen a la producción.

Las pruebas de carga pueden ser difíciles de hacer correctamente. Gran parte de la complejidad se debe al uso y la implementación del front-end. Si su sitio tiene un front-end sin encabezado, es posible que desee cargar y probar las API de GraphQL y REST. La forma en que termine la prueba de carga depende de usted y del equipo de DevOps. Tenga en cuenta que cada prueba de carga, realizada lo antes posible, proporciona una perspectiva del estado del proyecto. También proporciona puntos de referencia para pruebas futuras a fin de ver si hay algún cambio drástico en los resultados de las pruebas de carga. Si es así y son negativos, esta es una buena oportunidad para revisar los cambios de código más recientes y buscar secciones que afectan al rendimiento para mejorar.

Adobe Commerce ofrece instrucciones útiles para comprender cómo ejecutar pruebas unitarias. Consulte [Pruebas unitarias de PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} en la _Guía de pruebas de aplicaciones_ en el sitio de documentación de Adobe Developer.

Para obtener más información acerca de las pruebas funcionales, visite [Introducción al marco de pruebas funcionales](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
