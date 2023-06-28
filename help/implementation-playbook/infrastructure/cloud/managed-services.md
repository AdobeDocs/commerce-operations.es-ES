---
title: Managed Services
description: Revise las responsabilidades de Adobe Managed Services, los clientes y los proveedores de servicios en la nube para su Adobe Commerce en la implementación de la infraestructura en la nube.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed Services

Los servicios administrados de Adobe Commerce en la nube son seguros de forma predeterminada.

![Diagrama que muestra los servicios administrados de Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilidad compartida

Los planes de Adobe Commerce Pro dependen de un modelo de seguridad de responsabilidad compartida. En este modelo, las diferentes partes tienen diferentes áreas de responsabilidad para mantener la seguridad del sistema. Este enfoque permite la flexibilidad y el uso de las mejores tecnologías de nube.

![Diagrama que muestra el modelo de responsabilidad compartida de Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilidades de Adobe Managed Services

Adobe Managed Services es responsable de la seguridad y disponibilidad del entorno de nube de Adobe Commerce Pro, el código de aplicación principal de Adobe Commerce Pro y los sistemas de comercio interno. Esto incluye, entre otras cosas:

- Parches de nivel de servidor
- Funcionamiento de los servicios necesarios para ofrecer planes Adobe Commerce Pro
- Pruebas de vulnerabilidad
- Registro y monitorización de eventos de seguridad
- Administración de incidentes
- Monitorización operativa
- Asistencia 24/7
- Garantizar que la infraestructura del cliente esté disponible de acuerdo con los SLA

Adobe Managed Services también es responsable de administrar las configuraciones del firewall del servidor (iptables) y del firewall perimetral (grupos de seguridad). El Adobe también puede publicar actualizaciones de seguridad en la aplicación principal de forma periódica. Es responsabilidad del cliente aplicar estos parches. Todas estas áreas están cubiertas por la certificación PCI de Adobe Commerce en el sistema de infraestructura en la nube.

### Responsabilidades de AWS

Adobe Managed Services utiliza Amazon Web Service (AWS) para la infraestructura de servidores en la nube. AWS es responsable de la seguridad de la red, incluido el enrutamiento, la conmutación y la seguridad de la red perimetral a través de sistemas de cortafuegos y sistemas de detección de intrusiones (IDS). AWS es responsable de la seguridad física de los centros de datos que administran los entornos de nube de Adobe Commerce, así como de la seguridad medioambiental para garantizar que se establecen los controles adecuados de alimentación, refrigeración y mecanismos.

Los planes de Adobe Commerce Pro utilizan:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Tienda de bloques elásticos de Amazon (EBS)
- Amazon Virtual Private Cloud (VPC)
- Equilibrador de carga elástico de Amazon (ELB)
- Servicios de seguimiento de Amazon Cloud.

Amazon cuenta con un amplio programa de conformidad, que incluye las certificaciones PCI DSS, SOC 2 e ISO 27001.

### Responsabilidades del cliente/socio de soluciones

El cliente es el principal responsable de la seguridad de su implementación personalizada de la aplicación de Adobe Commerce que se ejecuta en el entorno de nube del plan Adobe Commerce Pro. Esto incluye:

- Garantizar una configuración y codificación seguras de la aplicación y las actividades de monitorización de seguridad, incluidas las pruebas de penetración y los análisis de vulnerabilidades regulares.

- La seguridad de cualquier personalización, extensión, otras aplicaciones o integraciones utilizadas en su sistema.

- La seguridad de sus usuarios y el acceso a su configuración y aplicación.

- El cliente controla todas las implementaciones de código en los entornos que no son de producción. Este control también incluye la responsabilidad de aplicar parches de seguridad de la aplicación a la aplicación principal de Adobe Commerce, las extensiones o cualquier código personalizado.

- El cliente debe realizar pruebas de penetración de su aplicación personalizada. El cliente, los socios de implementación o los servicios profesionales de Adobe Commerce pueden hacerse cargo de estas responsabilidades mediante recursos técnicos.

- Los clientes son responsables de los requisitos de PCI de su aplicación personalizada y de sus propios procesos. La conformidad con PCI del cliente se basa en las certificaciones PCI de AWS y Adobe Commerce para minimizar las áreas que deben revisarse.
