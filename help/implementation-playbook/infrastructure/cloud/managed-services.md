---
title: Managed Services
description: Revise las responsabilidades de Adobe Managed Services, los clientes y los proveedores de servicios en la nube para su Adobe Commerce en la implementación de la infraestructura de la nube.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Servicios administrados

Adobe Commerce en los servicios administrados por la infraestructura de la nube son seguros de forma predeterminada.

![Diagrama que muestra los servicios administrados de Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilidad compartida

Los planes de Adobe Commerce Pro dependen de un modelo de seguridad de responsabilidad compartida. En este modelo, las diferentes partes tienen diferentes ámbitos de responsabilidad en el mantenimiento de la seguridad del sistema. Este enfoque permite la flexibilidad y el uso de las mejores tecnologías de nube.

![Diagrama que muestra el modelo de responsabilidad compartida de Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilidades de los servicios administrados de Adobe

Adobe Managed Services es responsable de la seguridad y disponibilidad del entorno de nube de Adobe Commerce Pro, el código de aplicación principal de Adobe Commerce Pro y los sistemas de comercio internos. Esto incluye, entre otras cosas:

- Parches a nivel de servidor
- Funcionamiento de los servicios necesarios para ofrecer planes de Adobe Commerce Pro
- Prueba de vulnerabilidad
- Registro y monitorización de eventos de seguridad
- Gestión de incidentes
- Supervisión operativa
- Asistencia las 24 horas del día, los 7 días de la semana
- Garantizar que la infraestructura del cliente esté disponible de acuerdo con los SLAs

Adobe Managed Services también se encarga de administrar las configuraciones del cortafuegos del servidor (iptables) y las configuraciones del cortafuegos del perímetro (grupos de seguridad). El Adobe también puede publicar periódicamente actualizaciones de seguridad en la aplicación principal. Es responsabilidad de los clientes aplicar estos parches. Todas estas áreas están cubiertas por la certificación PCI de Adobe Commerce en el sistema de infraestructura en la nube.

### Responsabilidades de AWS

Adobe Managed Services utiliza Amazon Web Services (AWS) para la infraestructura de servidores en la nube. AWS es responsable de la seguridad de la red, incluyendo enrutamiento, conmutación y seguridad de la red perimetral a través de sistemas de firewall y sistemas de detección de intrusiones (IDS). AWS es responsable de la seguridad física de los centros de datos que administran los entornos de la nube de comercio de Adobe, así como de la seguridad ambiental para garantizar que se implementen los controles adecuados de alimentación, refrigeración y mecanismos.

Adobe Commerce Pro planea utilizar:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Equilibrador de carga elástica de Amazon (ELB)
- Servicios de rastreo de Amazon Cloud.

Amazon tiene un amplio programa de cumplimiento de normas, que incluye certificaciones PCI DSS, SOC 2 e ISO 27001.

### Responsabilidades de socios y clientes de la solución

El cliente es el principal responsable de la seguridad de su implementación personalizada de la aplicación de comercio de Adobe que se ejecuta en el entorno de nube de plan de Adobe Commerce Pro. Esto incluye:

- Garantizar una configuración y codificación seguras de las actividades de supervisión de aplicaciones y seguridad, incluidas las pruebas de penetración y los análisis regulares de vulnerabilidades.

- La seguridad de cualquier personalización, extensión, otras aplicaciones o integraciones utilizadas en su sistema.

- La seguridad de sus usuarios y la concesión de acceso a su configuración y aplicación.

- El cliente controla todas las implementaciones de código en los entornos que no sean de producción. Este control también incluye la responsabilidad de aplicar parches de seguridad de aplicaciones a la aplicación principal de Adobe Commerce, a las extensiones o a cualquier código personalizado.

- El cliente debe realizar pruebas de penetración de su aplicación personalizada. Estas responsabilidades se pueden abordar mediante recursos técnicos del cliente, socios de implementación o servicios profesionales de Adobe Commerce.

- Los clientes son responsables de los requerimientos de PCI de su aplicación personalizada y de sus propios procesos. El cumplimiento de PCI del cliente se basa en las certificaciones PCI de AWS y Adobe Commerce para minimizar las áreas que deben revisarse.
