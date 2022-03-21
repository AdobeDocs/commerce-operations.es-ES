---
title: Principios del desarrollo de la plataforma
description: Conozca los principios fundamentales del desarrollo de plataformas al trabajar con Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Principios del desarrollo de plataformas

En este manual, profundizamos en algunos de los estándares principales de desarrollo de Adobe Commerce, entre los que se incluyen:

- Análisis funcional y técnico en línea con el proceso de desarrollo
- Prácticas recomendadas de desarrollo alineadas con la arquitectura de MVC
- Consideraciones arquitectónicas, incluida la GRA
- Normas de seguridad contra scripts y explotación
- Prácticas recomendadas para el desarrollo de extensiones
- Integraciones de API web con REST, SOAP y GraphQL
- Mejoras de rendimiento para la codificación y la infraestructura
- Herramientas, estrategias y metodologías de prueba

Aunque algunos implementadores de soluciones pueden tener sus propias preferencias cuando se trata de las metodologías, procesos y herramientas utilizadas a lo largo de un proyecto de implementación, este manual se centra en las mejores prácticas y metodologías generalmente aceptadas que se pueden compartir en la mayoría de las implementaciones.

Al igual que cualquier proyecto informático de gran tamaño, Adobe Commerce se basa en estándares de codificación que aprovechan las prácticas recomendadas y las estandarizaciones de las tecnologías subyacentes (por ejemplo, PHP/Zend, Symfony, JavaScript, jQuery y HTML), así como en estándares que se han establecido dentro de Adobe Commerce Coding Standard. Seguir estos estándares es absolutamente necesario para eliminar errores y mejorar la calidad y el mantenimiento del código personalizado.

## Adobe Commerce en infraestructura en la nube

Adobe Commerce en infraestructura de nube es una plataforma de alojamiento automatizada y gestionada para el software Adobe Commerce. Adobe Commerce en la infraestructura de nube incorpora una serie de funciones adicionales que la diferencian de las implementaciones locales de Adobe Commerce y Magento Open Source:

![infografías de componentes de Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce en infraestructura de nube proporciona una infraestructura preaprovisionada que incluye tecnologías PHP, MySQL, Redis, RabbitMQ y Elasticsearch; un flujo de trabajo basado en Git con operaciones automáticas de compilación e implementación para un desarrollo rápido y eficiente y una implementación continua cada vez que se inserten cambios en el código en un entorno de Platform as a Service (PaaS); herramientas y archivos de configuración de entorno altamente personalizables; y el alojamiento de AWS que ofrece un entorno escalable y seguro para ventas y comercio minorista en línea.

![infografías de componentes de Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
