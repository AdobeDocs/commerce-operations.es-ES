---
title: Infraestructura local
description: Obtenga información sobre la infraestructura local de Adobe Commerce y los servicios en la nube de terceros.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Adobe Comercio local

Las motivaciones para iniciar una nueva implementación de Adobe Commerce o trasladar una implementación existente de Adobe Commerce local a la nube son numerosas, pero los factores estratégicos más comunes son la reducción del gasto de capital, la disminución de los costos continuos, la mejora de la escalabilidad y la elasticidad, la mejora del tiempo de salida al mercado y el logro de mejoras en la seguridad y el cumplimiento de las normas.

El diagrama siguiente muestra la arquitectura de referencia para la implementación de Adobe Commerce local en la infraestructura de AWS. Otros proveedores de nube como Azure, Google Cloud y Alibaba Cloud comparten un diseño de infraestructura y servicios homólogas similares.

![Diagrama de la infraestructura de comercio de Adobe autoalojada en servicios en la nube de terceros](../../assets/playbooks/on-premises-infrastructure.svg)

Vamos a profundizar en las funciones y funciones de cada aspecto de la infraestructura que se muestra arriba:

1. La ruta de Amazon 53 proporciona configuración DNS.

1. AWS WAF es un firewall de aplicaciones web que protege Adobe Commerce de vulnerabilidades web comunes.

1. Amazon CloudFront es una red de entrega de contenido (CDN) rápida que acelera la distribución de contenido web estático y dinámico.

1. El primer equilibrador de carga de aplicación de equilibrio de carga elástica distribuye el tráfico entre instancias de Varnish en un grupo de escalado automático de AWS en varias zonas de disponibilidad.

1. Varnish Cache es un acelerador de aplicaciones web que almacena en caché el proxy inverso HTTP. Se recomienda la versión empresarial, disponible a través del mercado de AWS, ya que cuenta con mejores funciones para admitir los backends de la nube y la depuración de caché en los hosts dinámicos.

1. El segundo equilibrador de carga de aplicación de equilibrio de carga elástica distribuye el tráfico desde la caché de Varnish a través del grupo de escalado automático de AWS de instancias de comercio de Adobe en varias zonas de disponibilidad.

1. Instale la versión más reciente de Magento Open Source o Adobe Commerce en instancias de Amazon EC2. La instalación consiste en la aplicación Adobe Commerce, Nginx webserver y PHP. Cree la imagen del equipo de Amazon (AMI) para iniciar nuevas instancias en un grupo de escalado automático.

1. Amazon Elasticsearch Service es un servicio de Elasticsearch administrado para la búsqueda de catálogo de Adobe Commerce.

1. Amazon ElastiCache para Redis proporciona una capa de almacenamiento en caché para la base de datos.

1. Utilice Amazon Aurora o AmazonRDS para simplificar la administración de la base de datos (incluida la alta disponibilidad y la configuración de varios maestros).

1. EFSMount Target facilita la asignación del sistema de archivos elásticos de Amazon (AmazonEFS) a instancias de comercio de Adobe y Varnish.

1. Utilice Amazon EFS para acceder a la configuración compartida entre recursos de medios compartidos y de Varnish en todas las instancias de Adobe Commerce.

## Servicios de nube

Además de proporcionar una plataforma tecnológica de soporte para la habilitación de procesos DevOps en AWS alrededor de su entorno de comercio de Adobe, AWS proporciona una colección de servicios que pueden proporcionar (en ausencia de) o aumentar sus soluciones existentes de administración de configuración de software (SCM). Esto incluye AWSCodeCommit, AWSCodeBuild, AWSCodePipeline y AWSCodeDeploy, que permite un control de código fuente administrado, la compilación, la integración continua/implementación continua (CI/CD) y los servicios de implementación.

## Migración en la nube

La propuesta de valor para migrar el comercio de Adobe a AWS se ve aún más mejorada por la disponibilidad de varios servicios que proporcionan una perspectiva y agilidad operativas. Lo que queremos decir es información operacional sobre la plataforma no sólo desde una perspectiva técnica (por ejemplo, solicitudes por hora) sino también desde una perspectiva operacional del negocio (por ejemplo, pedidos por hora), particularmente cuando los dos conjuntos de datos se pueden casar. Esto proporciona una perspectiva casi en tiempo real del rendimiento de la campaña, los costos de las operaciones de la plataforma y un número casi infinito de otros indicadores.

La configuración de Adobe Commerce para AWS puede reemplazar dependencias específicas de aplicaciones con alternativas completamente administradas disponibles en la nube. Por ejemplo, en lugar de alojar directamente una base de datos relacional en instancias de EC2, la base de datos de muchas aplicaciones se puede reemplazar fácilmente con el servicio de base de datos relacional de Amazon (AmazonRDS). El beneficio de esta estrategia es que la responsabilidad operativa de los componentes no diferenciados puede descargarse a AWS sin que sea necesario realizar cambios significativos en la aplicación principal.

Hay varias opciones de implementación disponibles para ejecutar Adobe Commerce (tanto Magento Open Source como Adobe Commerce) en AWS. La elección más adecuada depende de sus necesidades de coste, escala, disponibilidad y flexibilidad, así como de las capacidades de AWS y Adobe Commerce de su organización.
