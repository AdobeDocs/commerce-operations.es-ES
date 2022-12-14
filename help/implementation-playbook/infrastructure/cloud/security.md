---
title: Seguridad de la infraestructura de nube
description: Obtenga información sobre cómo mantener Adobe Commerce seguro en la infraestructura de la nube.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
source-git-commit: 50882bebb4712e6cf095a81297684f37e15b1a6b
workflow-type: tm+mt
source-wordcount: '1644'
ht-degree: 0%

---

# Seguridad

La arquitectura del plan Adobe Commerce Pro está diseñada para proporcionar un entorno altamente seguro. Cada cliente se implementa en su propio entorno de servidor aislado, separado de otros clientes. A continuación se describen los detalles de seguridad del entorno de producción.

## Navegadores web

La mayor parte del tráfico que entra y sale del entorno de la nube proviene de los navegadores web de los consumidores. El tráfico de los consumidores se puede asegurar mediante HTTPS para todas las páginas del sitio web (mediante una certificación SSL compartida o el certificado SSL propio del cliente por un cargo adicional). Las páginas de cierre de compra y cuenta siempre se sirven mediante HTTPS. La práctica recomendada es servir todas las páginas en HTTPS.

## Red de distribución de contenido (CDN)

Finfinitamente proporciona una CDN y protección de denegación de servicio distribuida (DDoS). La CDN de FIENTE ayuda a aislar el acceso directo a los servidores de origen. El DNS público solo señala a la Red rápida. La solución de DDoS FIENTE protege contra ataques de Capa 3 y Capa 4 altamente disruptivos, así como ataques de Capa 7 más complejos. Los ataques de la capa 7 se pueden bloquear mediante reglas personalizadas basadas en todas las solicitudes HTTP/HTTPS y basadas en criterios de cliente y solicitud, incluidos encabezados, cookies, ruta de solicitud e IP del cliente, o indicadores como la geolocalización.

## firewall de aplicaciones web (WAF)

El Cortafuegos de la aplicación web de Flash (WAF) se utiliza para proporcionar protección adicional. El WAF basado en la nube de Finfinito utiliza reglas de terceros de fuentes comerciales y de código abierto como el conjunto de reglas principales OWASP. Además, se utilizan reglas específicas de Adobe Commerce. Los clientes están protegidos frente a ataques clave en la capa de aplicación, incluidos ataques de inyección e entradas malintencionadas, scripts en sitios cruzados, exfiltración de datos, violaciones del protocolo HTTP y otras amenazas de OWASP Top 10.

Adobe Commerce actualiza las reglas WAF si se detectan nuevas vulnerabilidades que permitan a Managed Services &quot;solucionar virtualmente&quot; los problemas de seguridad antes de los parches de software. El Ffinity WAF no proporciona servicios de limitación de velocidad ni de detección de bots. Si lo desea, los clientes pueden obtener una licencia de un servicio de detección de bots de terceros compatible con FIENTE.

## Nube privada virtual (VPC)

El entorno de producción del plan Adobe Commerce Pro está configurado como una nube privada virtual (VPC), de modo que los servidores de producción están aislados y tienen una capacidad limitada para conectarse dentro y fuera del entorno de la nube. Solo se permiten conexiones seguras con los servidores de nube. Los protocolos seguros como SFTP o rsync pueden utilizarse para transferencias de archivos.

Los clientes pueden utilizar túneles SSH para proteger las comunicaciones con la aplicación. El acceso a AWS PrivateLink se puede proporcionar por un suplemento. Todas las conexiones a estos servidores se controlan mediante AWS Security Groups, un firewall virtual que limita las conexiones al entorno. Los recursos técnicos de los clientes pueden acceder a estos servidores mediante SSH.

## Cifrado

Amazon Elastic Block Store (EBS) se utiliza para el almacenamiento. Todos los volúmenes de EBS se cifran con el algoritmo AES-265. Esto significa que los datos se cifrarán en reposo. El sistema también cifra los datos en tránsito entre la CDN y el origen, y entre los servidores de origen. Las contraseñas de los clientes se almacenan como hashes. Las credenciales confidenciales, incluidas las de la puerta de enlace de pago, se cifran mediante el algoritmo SHA-256.

La aplicación Adobe Commerce no admite cifrado o cifrado de nivel de columna o fila cuando los datos no están en reposo o no transitan entre servidores. El cliente puede administrar claves de cifrado desde la aplicación. Las claves que utiliza el sistema se almacenan en AWS Key Management System y deben ser administradas por Managed Services para proporcionar partes del servicio.

## Pruebas de penetración

Managed Services realiza pruebas de penetración regulares en el sistema de nube de Adobe Commerce con la aplicación predeterminada. Los clientes son responsables de cualquier prueba de penetración de su aplicación personalizada.

## Puerta de enlace de pago

Adobe Commerce requiere integraciones de pasarela de pago en las que los datos de tarjetas de crédito se pasan directamente desde el explorador del consumidor a la puerta de enlace de pago. Los datos de tarjeta nunca están disponibles en ninguno de los entornos Managed Services de Adobe Commerce Pro. Las acciones en las transacciones por parte de la aplicación de comercio electrónico se completan utilizando una referencia a la transacción desde la puerta de enlace.

## aplicación Adobe Commerce

Adobe prueba regularmente el código de la aplicación principal para detectar vulnerabilidades de seguridad. Se proporcionan a los clientes parches para detectar defectos y problemas de seguridad. El equipo de seguridad del producto valida los productos de Adobe Commerce siguiendo las directrices de seguridad de la aplicación OWASP. Se utilizan varias herramientas de evaluación de vulnerabilidades de seguridad y proveedores externos para probar y verificar el cumplimiento. Las herramientas de seguridad incluyen:

- Veracode Escaneo estático y dinámico
- Análisis del código fuente RIPS
- Servicios de análisis de vulnerabilidades de Trustwave y Alert Logic
- Burp Suite Pro
- OWASPZAP
- ySqlMap

La base de código completa se analiza con estas herramientas cada dos semanas. Se notifica a los clientes de los parches de seguridad mediante correos electrónicos directos, notificaciones en la aplicación y en la variable [Centro de seguridad](https://magento.com/security).

Los clientes deben asegurarse de que estos parches se apliquen a su aplicación personalizada en un plazo de 30 días a partir del lanzamiento, según las directrices de PCI. El Adobe también proporciona un [Herramienta de análisis de seguridad](https://docs.magento.com/user-guide/magento/security-scan.html) que permite a los comerciantes monitorear regularmente sus sitios y recibir actualizaciones sobre riesgos de seguridad conocidos, malware y acceso no autorizado. La herramienta de análisis de seguridad es un servicio gratuito y se puede ejecutar en cualquier versión de Adobe Commerce.

Para animar a los investigadores de seguridad a identificar y notificar vulnerabilidades, Adobe Commerce tiene un [programa de rechazo a errores](https://hackerone.com/magento) además de las pruebas internas. Además, se proporciona al cliente el código fuente completo de la aplicación para su propia revisión si lo desea.

## Sistema de archivos de sólo lectura

Todo el código ejecutable se implementa en una imagen de sistema de archivos de sólo lectura, lo que reduce drásticamente las superficies disponibles para ataque. El proceso de implementación crea una imagen Squash-FS. Este método reduce considerablemente las oportunidades de insertar código PHP o JavaScript en el sistema o modificar los archivos de la aplicación Adobe Commerce.

## Implementación remota

La única manera de obtener código ejecutable en el entorno de producción de Managed Services es ejecutarlo a través de un proceso de aprovisionamiento. Esto implica transferir el código fuente del repositorio de origen a un repositorio remoto que inicia un proceso de implementación. El acceso a ese destino de implementación está controlado, por lo que tiene control absoluto sobre quién puede acceder al destino de implementación. El cliente controla todas las implementaciones de código de aplicación en el entorno que no sea de producción.

## Registro

Todas las actividades de AWS se registran en AWS CloudTrack. Linux, el servidor de aplicaciones y los registros de bases de datos se almacenan en los servidores de producción y se almacenan en backups. Todos los cambios en el código fuente se registran en un repositorio de Git. El historial de implementación está disponible en Adobe Commerce [Interfaz web del proyecto](https://devdocs.magento.com/cloud/project/projects.html#login). Se registra todo el acceso de asistencia y se registran las sesiones de asistencia.

## Datos confidenciales

Los datos confidenciales pueden abarcar información personal de los consumidores o datos confidenciales de clientes de Managed Services. La protección de datos confidenciales de clientes y consumidores es una obligación fundamental para Adobe Commerce Managed Services. Tanto Managed Services como nuestros clientes tienen obligaciones legales en cuanto a la información de identificación personal. Además de las funciones de seguridad de la arquitectura, existen otros controles para limitar la distribución y el acceso a los datos confidenciales.

Los clientes son propietarios de sus datos y tienen control sobre dónde se ubicarán dichos datos. El cliente especifica la ubicación donde residen sus instancias de producción y desarrollo. También especifican qué ubicación se utilizará para el entorno de informes de Adobe Commerce junto con Comercio y si esa aplicación de informes de Adobe Commerce tiene acceso o no a información de identificación personal. Las instancias de producción se pueden encontrar en la mayoría de las regiones de AWS, mientras que los entornos de desarrollo e informes de Adobe Commerce se pueden encontrar en Estados Unidos o en la Unión Europea en este momento.

Los datos confidenciales pueden pasar a través de la red de servidores de CDN FIngente, pero no se almacenan en la red FIngente. Todos los socios incluidos en la oferta de Adobe Commerce Managed Services tienen obligaciones contractuales para garantizar la protección de datos confidenciales. Managed Services no moverá datos confidenciales de clientes o consumidores de las ubicaciones especificadas por el cliente.

Como parte del suministro de los servicios incluidos en la oferta de Adobe Commerce Managed Services, el personal de Managed Services necesita acceder a sistemas de producción que contengan datos confidenciales. Estos empleados reciben formación sobre sus obligaciones para proteger datos confidenciales de clientes y consumidores. El acceso a estos sistemas está limitado a los empleados que necesitan acceso. Estos empleados solo tienen acceso durante el tiempo necesario para prestar estos servicios.

## Reglamento general de protección de datos (RGPD)

El RGPD es un marco jurídico que establece directrices para la recopilación y el tratamiento de información personal de personas en la Unión Europea (UE). Estas regulaciones se aplican independientemente de la ubicación del sitio y los visitantes de la UE tienen acceso a él.

Esencialmente, se debe notificar a los visitantes de los datos que el sitio recopila de ellos y consentir explícitamente en la recopilación de información. Los sitios deben notificar a los visitantes si se infringen los datos personales del sitio.

El comerciante o la empresa que opera el sitio también deben tener un responsable de protección de datos que supervise la seguridad de los datos del sitio, y este individuo (o equipo de administración del sitio web) debe estar disponible para ponerse en contacto si un visitante solicita que se borren sus datos.

El RGPD también pide que cualquier información personal identificable (como nombres, raza y fecha de nacimiento) recopilada sea anonimizada o seudonizada.

>[!NOTE]
>
> Esta página es una descripción general de lo que hay que tener en cuenta para el RGPD. Para obtener más información, consulte con su asesor jurídico o consulte la[texto oficial](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Copias de seguridad

Las copias de seguridad se realizan cada hora durante las últimas 24 horas de funcionamiento. Después del período de 24 horas, las copias de seguridad se retienen según la siguiente programación, utilizando el servicio AWS EBS Snapshot:

| Período de tiempo | Política de retención de copia de seguridad |
|----------------|-------------------------|
| Días 1 a 3 | Cada copia de seguridad |
| Días 4 a 6 | Una copia de seguridad al día |
| Semanas 2 a 6 | Una copia de seguridad por semana |
| Semanas 8 a 12 | Una copia de seguridad bisemanal |
| Semanas 12 a 22 | Una copia de seguridad mensual |

Esto crea un backup independiente en almacenamiento de información redundante. Dado que los volúmenes EBS están cifrados, los backups también están cifrados. Además, Managed Services realiza backups bajo demanda según lo solicitado por el cliente.

Su enfoque de backup y recuperación de Adobe Commerce Managed Services usa una arquitectura de alta disponibilidad combinada con backups de todo el sistema. Cada proyecto se replica (todos los datos, código y recursos) en tres zonas de disponibilidad de AWS independientes. cada zona con un centro de datos independiente.
