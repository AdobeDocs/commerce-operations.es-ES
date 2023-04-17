---
title: Herramientas de supervisión de Adobe Commerce de alojamiento propio
description: Obtenga información sobre las herramientas de monitorización de alojamiento propio, ideas, conceptos y prácticas recomendadas que debe tener en cuenta.
landing-page-description: Aprenda algunos conceptos y cosas que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Conozca las estrategias y los conceptos de las herramientas de monitorización para alojarse usted mismo en Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 63fddb20673399bae397238a8dda866e1d740e6f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Herramientas y telemetría de monitorización de Adobe Commerce de alojamiento propio

El uso de herramientas de monitorización permite detectar cambios sin tener que pagar a alguien para que los vea todo el tiempo. Con la mayoría de las herramientas, puede agregar alertas y notificaciones si se alcanza un umbral, como una unidad de disco duro que se queda sin espacio. Algunas herramientas proporcionan resultados que se deben rastrear y calcular, como los resultados de las pruebas de carga. Independientemente de la herramienta, todas tienen un propósito y, cuando se utilizan de forma consistente, pueden ayudarle a administrar su aplicación. Hay opciones gratuitas para cada herramienta, pero recuerde pagar por un servicio a menudo garantiza un soporte más rápido y confiable y puede valer la pena la inversión. New Relic es un ejemplo de una herramienta que ofrece un nivel gratuito y una versión de pago que desbloquea mucha más potencia y capacidades. Hay otros como DataDog o Dynatrace. Encuentre una buena opción y utilícela de forma consistente.

## Supervisión de la infraestructura

El término infraestructura se utiliza de forma bastante flexible para este contexto. Para este tema, se refiere a cualquier servidor, proceso o dispositivo que se utilice para hacer que el sitio funcione. Por ejemplo:

* Discos duros
* Uso de CPU
* Uso de RAM
* Redis
* Carga promedio por servidor
* tráfico de red

Umbrales de investigación para crear alertas efectivas. No asigne una para cosas importantes como la capacidad del disco duro. Configure algunos para notificar a diferentes grupos a medida que las cosas empeoran. Por ejemplo, aquí hay un conjunto de reglas cuando una unidad de disco duro se está llenando.

* Notificación del 70% de Slack al canal DevOps
* 80% Notificar al Slack del canal DevOps y una lista de distribución por correo electrónico de los compañeros de equipo de DevOps
* 90% Notificar al Slack DevOps canal y al Slack de soporte de producción, al grupo de distribución DevOps de correo electrónico y al administrador de ingeniería
* 95% Notificar al Slack DevOps y a los canales del Slack de soporte de producción, lista de distribución por correo electrónico de todos los ingenieros y Director de ingeniería
* 98% Notificar a cualquier canal Slack P1 y canales de Slack de DevOps y soporte de producción, lista de distribución de correo electrónico de ingenieros y Director de ingeniería y VP de tecnología

Hay muchas formas de notificar a un equipo, así que asegúrese de elegir una que sea fiable y no se vea inundada con demasiadas alertas. Es importante reservar alertas para cuando esto importe, de lo contrario se corre el riesgo de quedar abrumado y comenzar a ignorar las alertas.

A menudo hay buenas plantillas que seguir para la mayoría de las herramientas, como New Relic, DataDog y Dynatrace. Tómese un tiempo para encontrar buenas ideas que tengan más sentido para su aplicación. Con Adobe Commerce en la infraestructura de nube, hay alertas y déclencheur cuando se aprovisiona el proyecto. Esto permite que el equipo de soporte de producción de Adobe aplique sus herramientas para la monitorización de tiempo activo y alta disponibilidad.

Los tableros proporcionan acceso rápido a los aspectos frecuentes o importantes del sitio. Los elementos de tablero pueden consistir en vistas de página, uso de CPU por host, lista de todos los servidores, tiempos de carga de página, duraciones de transacción e incluso resultados de pruebas de monitorización sintética durante los últimos días. Estos tableros deben crearse para permitir un aprendizaje rápido si algo está mal o si se han configurado distintos tableros para distintas experiencias de usuario. Con suerte, puede diseñar varios tableros y disfrutar de ver la supervisión de su aplicación en tiempo real. Es muy satisfactorio, especialmente cuando el propietario del proyecto o un gerente le preguntan cómo funciona el sitio, y usted puede encontrar la respuesta en segundos, no en horas.

## Agregación y rotación de registros

Los archivos de registro se encuentran en servidores de aplicaciones que procesan solicitudes o registros MySQL cuando las cosas tardan demasiado en ejecutarse. Lo difícil de los registros es que están separados unos de otros y los encuentran todos, analizar la información de cada registro puede ser engorroso. Hace muchos años, este problema se resolvió usando una técnica llamada _agregación de registros_. Esto toma los archivos de registro de todas sus ubicaciones de registro y los lleva a una ubicación centralizada. Una vez que se mueven, un software puede leerlos y proporcionar formas de buscar, filtrar y revisar la información. Este puede ser un proceso difícil para acercarse. Hay muchas opciones, pero si tiene suerte, las herramientas de monitoreo pueden leer y agregar sus archivos de registro, como New Relic. Al encontrar una buena herramienta, puede ahorrarse una cantidad incalculable de tiempo en el futuro. A menos que tenga un solo servidor que haga todo lo posible para que su sitio funcione, es esencial tener agregación de registros. Esto resulta especialmente útil cuando se intenta averiguar si se encuentra bajo un ataque DDoS o si se está experimentando un pico de tráfico legítimo, o cuando se investiga por qué una solicitud determinada está fallando.

Otra pieza clave para los registros es garantizar que se produzca la rotación. Históricamente, esto pertenece a `run-away logs` que puede llenar accidentalmente su disco duro y hacer que el sitio se vaya. Se puede producir una versión de rotación de registros cuando un archivo de registro alcanza un tamaño determinado, como 1 GB. Existen herramientas de nivel de servidor como `logrotate` que pueden eliminarlos automáticamente. Por ejemplo, puede eliminar archivos de registro demasiado grandes una vez que llegan a ser buenos de 1 GB o eliminar archivos de registro de más de 90 días. Puede definir una directiva de registro, por lo que es importante comprender las limitaciones de recursos.

## Análisis de malware

Muchas empresas de alojamiento de sitios web dedicadas a Adobe Commerce tendrían una biblioteca de software malicioso y de explotación conocidos. Deben ofrecer un análisis de forma automática o previa solicitud. Cuando son eficaces, son reaccionarios y solo funcionan cuando se detecta un nuevo malware. Puede ser una buena idea tener una herramienta proactiva que pueda ver el código y la base de datos de malware conocido. Hay algunas opciones disponibles, como [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Pueden realizar un análisis remoto desde el exterior o instalarse y actualizar, analizar o monitorizar de forma proactiva después de configurarse en los servidores. Estas pueden ser una buena opción, ya que su biblioteca se actualiza constantemente porque se instalan y supervisan miles de sitios si elige una solución proporcionada como Sansec. A medida que se detecta un nuevo malware, cada proyecto que monitoree se beneficia de la información y ahora se le alertará si se detecta.

Hay algunas versiones libres que considerar, pero para malware, realmente debe considerar una solución de pago. Esta puede ser la diferencia entre que su sitio se haya infectado durante unos minutos, frente a los pocos meses. Tener una explotación en su sitio causa enormes dolores de cabeza, este es un área que debe considerar para pagar un servicio.

## Herramienta de análisis de todo el sitio de Adobe

La herramienta de análisis de todo el sitio es una herramienta de autoservicio proactiva y un repositorio central que incluye información detallada del sistema y recomendaciones para garantizar la seguridad y la operabilidad de su instalación de Adobe Commerce. Proporciona monitoreo del rendimiento en tiempo real las 24 horas del día, los 7 días de la semana, informes y asesoramiento para identificar posibles problemas y una mejor visibilidad de las configuraciones de aplicaciones, seguridad y salud del sitio. Ayuda a reducir el tiempo de resolución y a mejorar la estabilidad y el rendimiento del sitio.

La página Recommendations de la herramienta de análisis de todo el sitio enumera las recomendaciones basadas en las prácticas recomendadas para abordar los problemas detectados en el sitio. Las recomendaciones se clasifican por prioridad PO a P4, donde PO es crítico y P4 es bajo. Los resultados incluyen descripción, recomendación, impacto en el sitio, causa raíz, escenarios/condiciones previas, resultado esperado y herramientas utilizadas.

Conozca las prácticas recomendadas para mejorar el rendimiento del sitio. Rastree e implemente las recomendaciones enumeradas según la prioridad.

Para obtener más información sobre cómo instalar esto en su proyecto, visite [Guía de instalación de la herramienta de análisis de sitio](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Supervisión SSL

Uno de los elementos más olvidados de un proyecto es el certificado SSL. Solo necesitan atención una vez al año, así que olvidarlos es muy fácil. La caducidad del certificado de seguridad podría provocar que los navegadores modernos avisen o se nieguen a mostrar las páginas del sitio. Los clientes pueden empezar a enviar correos electrónicos o a llamar al servicio de asistencia si experimentan un problema de este tipo y es posible que no pueda operar hasta que se resuelva. Cada minuto cuenta, por lo que reconocer la caducidad viene antes de tiempo y asegurarse de que las cosas se renueven es primordial para mantener el sitio en funcionamiento. Existen muchas maneras de realizar la monitorización SSL. Considere la posibilidad de utilizar herramientas de monitorización sintéticas para su sitio, utilizando herramientas gratuitas o de bajo costo como PKingdom, Keyshop o Sucuri, e incluso suscribirse a un servicio que ofrezca alertas de caducidad de certificados SSL. Estas herramientas sencillas pueden garantizar que los certificados del sitio sean válidos y reducir el riesgo de downtime para los clientes.

## Pruebas automatizadas

Realizar pruebas automatizadas, como pruebas funcionales o pruebas unitarias, a menudo ayuda a detectar problemas a partir del código recién introducido. Es posible que estas pruebas no lo capten todo, ya que las pruebas Adobe Commerce y unitarias suelen tener una cobertura inferior al 50%. No significa que debería evitar escribirlas y probarlas. Estas herramientas están aquí para agregar otra capa de seguridad que todo lo que se está comprometiendo no afecta negativamente a los componentes listos para usar y cualquier prueba personalizada que cree su equipo de desarrollo. Al ejecutar estas pruebas en cada implementación, todos los problemas importantes se detectan antes de lo previsto y evitan que se produzcan.

Las pruebas de carga pueden ser un desafío para hacerlo bien. Gran parte de la complejidad proviene de cómo se utiliza e implementa el front-end. Si su sitio tiene un front-end sin encabezado, es posible que desee cargar las API de prueba de GraphQL y REST. La forma de terminar las pruebas de carga depende de usted y del equipo de DevOps. Tenga en cuenta que cada prueba de carga, realizada lo antes posible, proporciona una perspectiva del estado del proyecto. También proporciona puntos de referencia para pruebas futuras con el fin de comprobar si hay cambios drásticos en los resultados de las pruebas de carga. Si es así, y son negativos, esta es una buena oportunidad para revisar los cambios de código más recientes y buscar secciones que afecten al rendimiento para mejorar.

Adobe Commerce tiene buenas directrices para ayudarle a comprender cómo ejecutar pruebas unitarias, consulte [Prueba de unidades PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} en el _Guía de prueba de aplicaciones_ en el sitio de documentación de Adobe Developer.

Para obtener más información sobre las pruebas funcionales, visite [Introducción al marco de pruebas funcionales](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
