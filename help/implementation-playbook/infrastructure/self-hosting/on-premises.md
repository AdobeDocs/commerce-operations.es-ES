---
title: Infraestructura local
description: Obtenga información acerca de la infraestructura local de Adobe Commerce y los servicios en la nube de terceros.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# infraestructura local de Adobe Commerce

Las motivaciones para iniciar una nueva implementación de Adobe Commerce o mover una implementación de Adobe Commerce local existente a la nube son numerosas, pero los impulsores estratégicos más comunes son la reducción del gasto de capital, la disminución del coste actual, la mejora de la escalabilidad y la elasticidad, la mejora del tiempo de salida al mercado y la obtención de mejoras en la seguridad y el cumplimiento.

El diagrama siguiente muestra la arquitectura de referencia para implementar Adobe Commerce de forma local en la infraestructura de AWS. Otros proveedores de nube como Azure, Google Cloud y Alibaba Cloud comparten un diseño de infraestructura y servicios homólogos similares.

![Diagrama que muestra la infraestructura de Adobe Commerce de alojamiento propio en servicios en la nube de terceros](/help/assets/playbooks/on-premises-infrastructure.svg)

Vamos a profundizar en las funciones y los roles de cada aspecto de la infraestructura que se muestra arriba:

1. La Ruta 53 de Amazon proporciona la configuración DNS.

1. AWS WAF es un cortafuegos de aplicaciones web que protege Adobe Commerce de vulnerabilidades web comunes.

1. Amazon Cloud Front es una red de entrega de contenido (CDN) rápida que acelera la distribución de contenido web estático y dinámico.

1. El primer equilibrador de carga de la aplicación Elastic Load Balancing distribuye el tráfico entre las instancias de Varnish en un grupo de escalado automático de AWS en varias zonas de disponibilidad.

1. Varnish Cache es un acelerador de aplicaciones web que almacena en caché el proxy inverso HTTP. Se recomienda la versión empresarial, disponible a través de AWS Marketplace, ya que tiene mejores funciones para admitir backends de nube y depuración de caché en hosts dinámicos.

1. El segundo equilibrador de carga de la aplicación Elastic Load Balancing distribuye el tráfico de la caché de Barnish a través del grupo de escalado automático de AWS de instancias de Adobe Commerce en varias zonas de disponibilidad.

1. Instale la última versión de Adobe Commerce en instancias de Amazon EC2. La instalación consiste en la aplicación Adobe Commerce, el servidor web Nginx y PHP. Cree la imagen de equipo de Amazon (AMI) para iniciar nuevas instancias en un grupo de escalado automático.

1. El servicio de Elasticsearch de Amazon es un servicio de Elasticsearch administrado para la búsqueda en el catálogo de Adobe Commerce.

1. Amazon ElastiCache para Redis proporciona una capa de almacenamiento en caché para la base de datos.

1. Utilice Amazon Aurora o Amazon RDS para simplificar la administración de bases de datos (incluida la alta disponibilidad y la configuración de varios maestros).

1. EFSMount Target facilita la asignación del sistema de archivos elástico de Amazon (AmazonEFS) a las instancias de Barniz y Adobe Commerce.

1. Utilice Amazon EFS para acceder a la configuración compartida entre los recursos de barniz y medios compartidos en las instancias de Adobe Commerce.

## Cloud Services

Además de proporcionar una plataforma tecnológica de soporte para la activación de procesos de DevOps en AWS en su entorno de Adobe Commerce, AWS proporciona una colección de servicios que pueden proporcionar (en ausencia de) o aumentar sus soluciones de administración de configuración de software (SCM) existentes. Esto incluye AWSCodeCommit, AWSCodeBuild, AWSCodePipeline y AWSCodeDeploy, que permite un control de código fuente administrado, una compilación, una integración continua/implementación continua (CI/CD) y servicios de implementación.

## Migración de nube

La propuesta de valor para migrar Adobe Commerce a AWS se mejora aún más mediante la disponibilidad de varios servicios que proporcionan perspectiva operativa y agilidad. Lo que queremos decir es una perspectiva operativa de la plataforma no solo desde una perspectiva técnica (por ejemplo, solicitudes por hora), sino también desde una perspectiva operativa empresarial (por ejemplo, pedidos por hora), especialmente cuando los dos conjuntos de datos pueden estar casados. Esto proporciona una visión casi en tiempo real del rendimiento de la campaña, los costes de operaciones de la plataforma y un número casi infinito de otros indicadores.

La configuración de Adobe Commerce en AWS puede reemplazar dependencias específicas de la aplicación con alternativas totalmente administradas disponibles en la nube. Por ejemplo, en lugar de alojar directamente una base de datos relacional en instancias EC2, la base de datos de muchas aplicaciones se puede reemplazar fácilmente por el servicio de base de datos relacional de Amazon (AmazonRDS). La ventaja de esta estrategia es que la responsabilidad operativa de los componentes no diferenciados se puede descargar en AWS sin necesidad de realizar cambios significativos en la aplicación principal.

Hay varias opciones de implementación disponibles para ejecutar Adobe Commerce en AWS. La elección más adecuada depende de sus necesidades de coste, escala, disponibilidad y flexibilidad, así como de las habilidades de AWS y Adobe Commerce de su organización.

{{$include /help/_includes/hosting-related-links.md}}
