---
title: Seguridad de infraestructura en nube
description: Obtenga información sobre cómo mantenemos seguro Adobe Commerce en la infraestructura en la nube.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
source-git-commit: 50882bebb4712e6cf095a81297684f37e15b1a6b
workflow-type: tm+mt
source-wordcount: '1644'
ht-degree: 0%

---

# Seguridad

La arquitectura del plan Adobe Commerce Pro está diseñada para proporcionar un entorno altamente seguro. Cada cliente se implementa en su propio entorno de servidor aislado, separado de otros clientes. A continuación se describen los detalles de seguridad del entorno de producción.

## Exploradores web

La mayor parte del tráfico que entra y sale del entorno de la nube proviene de los navegadores web de los consumidores. El tráfico de consumidores puede protegerse mediante HTTPS en todas las páginas del sitio web (mediante una certificación SSL compartida o el certificado SSL propio del cliente, por un cargo adicional). Las páginas de cierre de compra y de cuenta siempre se proporcionan mediante HTTPS. La práctica recomendada es utilizar HTTPS en todas las páginas.

## Red de entrega de contenido (CDN)

Proporciona rápidamente una protección de CDN y denegación de servicio distribuido (DDoS). Fastly CDN ayuda a aislar el acceso directo a los servidores de origen. El DNS público solo apunta a la red de Fastly. La solución Fastly DDoS protege contra ataques de capa 3 y capa 4 altamente disruptivos, así como ataques de capa 7 más complejos. Los ataques de nivel 7 se pueden bloquear mediante reglas personalizadas basadas en todas las solicitudes HTTP/HTTPS y en criterios de cliente y solicitud, incluidos encabezados, cookies, ruta de solicitud e IP de cliente, o indicadores como la geolocalización.

## Firewall de aplicaciones web (WAF)

El firewall de aplicaciones web de Fastly (WAF) se utiliza para proporcionar protección adicional. El WAF basado en la nube de Fastly utiliza reglas de terceros de fuentes comerciales y de código abierto como el conjunto de reglas principal de OWASP. Además, se emplean reglas específicas de Adobe Commerce. Los clientes están protegidos de ataques clave en la capa de aplicación, incluidos ataques de inyección e entradas malintencionadas, scripts entre sitios, exfiltración de datos, violaciones del protocolo HTTP y otras amenazas del Top 10 de OWASP.

Adobe Commerce actualiza las reglas WAF en caso de que se detecten nuevas vulnerabilidades que permitan a Managed Services &quot;aplicar parches virtuales&quot; a los problemas de seguridad antes de aplicar los parches de software. Fastly WAF no proporciona servicios de limitación de velocidad o detección de bots. Si lo desea, los clientes pueden obtener una licencia de un servicio de detección de bots de terceros compatible con Fastly.

## Virtual Private Cloud (VPC)

El entorno de producción del plan Adobe Commerce Pro está configurado como una nube privada virtual (VPC) para que los servidores de producción estén aislados y tengan una capacidad limitada para conectarse dentro y fuera del entorno de la nube. Solo se permiten conexiones seguras a los servidores en la nube. Se pueden utilizar protocolos seguros como SFTP o rsync para transferencias de archivos.

Los clientes pueden utilizar túneles SSH para asegurar las comunicaciones con la aplicación. El acceso a AWS PrivateLink puede proporcionarse por un suplemento. Todas las conexiones a estos servidores se controlan mediante Grupos de seguridad de AWS, un cortafuegos virtual que limita las conexiones al entorno. Los recursos técnicos de los clientes pueden acceder a estos servidores mediante SSH.

## Cifrado

Almacén de bloques elásticos de Amazon (EBS) se utiliza para el almacenamiento. Todos los volúmenes EBS se cifran con el algoritmo AES-265. Esto significa que los datos se cifran en reposo. El sistema también cifra los datos en tránsito entre la CDN y el origen, y entre los servidores de origen. Las contraseñas de los clientes se almacenan como hashes. Las credenciales confidenciales, incluidas las de la puerta de enlace de pago, se cifran mediante el algoritmo SHA-256.

La aplicación Adobe Commerce no admite el cifrado o cifrado de nivel de columna o fila cuando los datos no están en reposo o no están en tránsito entre los servidores. El cliente puede administrar las claves de cifrado desde la aplicación. Las claves utilizadas por el sistema se almacenan en el sistema de administración de claves de AWS y Managed Services debe administrarlas para proporcionar partes del servicio.

## Pruebas de penetración

Managed Services realiza pruebas de penetración regulares del sistema en la nube de Adobe Commerce con la aplicación predeterminada. Los clientes son responsables de cualquier prueba de penetración de su aplicación personalizada.

## Pasarela de pago

Adobe Commerce requiere integraciones de puerta de enlace de pago en las que los datos de la tarjeta de crédito se pasan directamente del explorador del consumidor a la puerta de enlace de pago. Los datos de la tarjeta nunca están disponibles en ninguno de los entornos Managed Services del plan Adobe Commerce Pro. Las acciones de las transacciones realizadas por la aplicación de comercio electrónico se completan mediante una referencia a la transacción desde la puerta de enlace.

## aplicación de Adobe Commerce

El Adobe prueba regularmente el código de la aplicación principal para detectar vulnerabilidades de seguridad. Los parches para defectos y problemas de seguridad se proporcionan a los clientes. El equipo de seguridad del producto valida los productos de Adobe Commerce siguiendo las directrices de seguridad de la aplicación OWASP. Para probar y verificar el cumplimiento se utilizan varias herramientas de evaluación de vulnerabilidades de seguridad y proveedores externos. Las herramientas de seguridad incluyen:

- Escaneado estático y dinámico de Veracode
- Análisis del código fuente RIPS
- Servicios de análisis de vulnerabilidades de Trustwave y Alert Logic
- Burp Suite Pro
- OWASPZAP
- andSqlMap

La base de código completa se analiza con estas herramientas cada dos semanas. Los parches de seguridad se notifican a los clientes por correo electrónico directo, en la aplicación y en el [Centro de seguridad](https://magento.com/security).

Los clientes deben asegurarse de que estos parches se aplican a su aplicación personalizada dentro de los 30 días posteriores al lanzamiento, según las directrices de PCI. El Adobe también proporciona un [Herramienta de exploración de seguridad](https://docs.magento.com/user-guide/magento/security-scan.html) que permite a los comerciantes supervisar con regularidad sus sitios y recibir actualizaciones sobre riesgos de seguridad conocidos, malware y acceso no autorizado. Security Scan Tool es un servicio gratuito que se puede ejecutar en cualquier versión de Adobe Commerce.

Para animar a los investigadores de seguridad a identificar y notificar vulnerabilidades, Adobe Commerce tiene un [programa de devolución de errores](https://hackerone.com/magento) además de las pruebas internas. Además, se proporciona al cliente el código fuente completo de la aplicación para su propia revisión si lo desea.

## Sistema de archivos de solo lectura

Todo el código ejecutable se implementa en una imagen de sistema de archivos de solo lectura, lo que reduce drásticamente las superficies disponibles para el ataque. El proceso de implementación crea una imagen Squash-FS. Este enfoque reduce drásticamente las oportunidades de insertar código PHP o JavaScript en el sistema o modificar los archivos de la aplicación Adobe Commerce.

## Implementación remota

La única manera de obtener código ejecutable en el entorno de producción de Managed Services es ejecutarlo a través de un proceso de aprovisionamiento. Esto implica insertar el código fuente del repositorio de origen en un repositorio remoto que inicie un proceso de implementación. El acceso a ese destino de implementación está controlado, por lo que tiene control total sobre quién puede acceder al destino de implementación. El cliente controla todas las implementaciones de código de aplicación en el entorno que no sea de producción.

## Registro

Todas las actividades de AWS están registradas en AWS CloudTrail. Los registros de Linux, del servidor de aplicaciones y de la base de datos se almacenan en los servidores de producción y en las copias de seguridad. Todos los cambios en el código fuente se registran en un repositorio Git. El historial de implementación está disponible en Adobe Commerce [Interfaz web de Project](https://devdocs.magento.com/cloud/project/projects.html#login). Todo el acceso de asistencia se registra y las sesiones de asistencia se registran.

## Datos confidenciales

Los datos confidenciales pueden incluir información personal de los consumidores o datos confidenciales de clientes de Managed Services. La protección de los datos confidenciales de clientes y consumidores es una obligación esencial para Adobe Commerce Managed Services. Tanto Managed Services como nuestros clientes tienen obligaciones legales en torno a la información personal. Además de las características de seguridad de la arquitectura, existen otros controles para limitar la distribución y el acceso a los datos confidenciales.

Los clientes son propietarios de sus datos y tienen control sobre dónde se ubicarán dichos datos. El cliente especifica la ubicación donde residen sus instancias de producción y desarrollo. También especifican qué ubicación se utilizará para el entorno de informes de Adobe Commerce junto con Commerce y si la aplicación de informes de Adobe Commerce tiene acceso a información personal o no. Las instancias de producción se pueden encontrar en la mayoría de las regiones de AWS, mientras que los entornos de desarrollo e informes de Adobe Commerce se pueden encontrar en Estados Unidos o en la Unión Europea en este momento.

Los datos confidenciales pueden pasar a través de la red del servidor de CDN de Fastly, pero no se almacenan en la red de Fastly. Todos los socios incluidos en la oferta de Adobe Commerce Managed Services tienen obligaciones contractuales para garantizar la protección de los datos confidenciales. Managed Services no moverá datos confidenciales de clientes o consumidores desde las ubicaciones especificadas por el cliente.

Como parte de la prestación de los servicios incluidos en la oferta de Adobe Commerce Managed Services, el personal de Managed Services necesita tener acceso a los sistemas de producción que contienen datos confidenciales. Estos empleados reciben formación sobre sus obligaciones de proteger los datos confidenciales de los clientes y los consumidores. El acceso a estos sistemas está limitado a los empleados que requieren acceso. Estos empleados solo tienen acceso durante el tiempo necesario para prestar estos servicios.

## Reglamento General de Protección de Datos (RGPD)

El RGPD es un marco legal que establece directrices para la recopilación y el procesamiento de información personal de personas en la Unión Europea (UE). Estas regulaciones se aplican independientemente de dónde se base el sitio y de si los visitantes de la UE tienen acceso a él.

Básicamente, se debe notificar a los visitantes los datos que el sitio recopila de ellos y dar su consentimiento explícito a la recopilación de información. Los sitios deben notificar a los visitantes si se infringen los datos personales que mantiene el sitio.

El comerciante o empresa que gestione el sitio también debe tener un responsable de protección de datos dedicado que supervise la seguridad de datos del sitio, y esta persona (o equipo de administración del sitio web) debe estar disponible para ponerse en contacto si un visitante solicita que se borren sus datos.

El RGPD también exige que cualquier información de identificación personal (como nombres, raza y fecha de nacimiento) recopilada sea anónima o seudónima.

>[!NOTE]
>
> Esta página es simplemente una descripción general de lo que hay que tener en cuenta para el RGPD. Para obtener más información, consulte con su asesor legal o consulte la[texto oficial](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Copias de seguridad

Las copias de seguridad se realizan cada hora durante las últimas 24 horas de funcionamiento. Después del período de 24 horas, las copias de seguridad se conservan según la siguiente programación mediante el servicio de instantáneas de AWS EBS:

| Período de tiempo | Política de retención de copias |
|----------------|-------------------------|
| Días 1 a 3 | Cada copia de seguridad |
| Días 4 a 6 | Una copia de seguridad al día |
| Semanas 2 a 6 | Una copia de seguridad por semana |
| Semanas 8 a 12 | Una copia de seguridad quincenal |
| Semanas 12 a 22 | Una copia de seguridad al mes |

Esto crea una copia de seguridad independiente en el almacenamiento redundante. Como los volúmenes EBS están cifrados, las copias de seguridad también están cifradas. Además, Managed Services realiza copias de seguridad bajo demanda según lo solicitado por el cliente.

Su enfoque de backup y recuperación de Adobe Commerce Managed Services utiliza una arquitectura de alta disponibilidad combinada con backups de todo el sistema. Cada proyecto se duplica (todos los datos, el código y los recursos) en tres zonas de disponibilidad de AWS independientes; cada zona tiene un centro de datos independiente.
