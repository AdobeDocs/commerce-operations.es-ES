---
title: Principios de desarrollo de plataformas
description: Comprender los principios fundamentales del desarrollo de plataformas al trabajar con Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Principios del desarrollo de plataformas

En este manual, profundizamos en algunos de los principales estándares de desarrollo de Adobe Commerce, como:

- Alcance funcional y técnico en línea con el proceso de desarrollo
- Prácticas recomendadas de desarrollo alineadas con la arquitectura de MVC
- Consideraciones arquitectónicas, incluyendo GRA
- Estándares de seguridad contra scripts y exploits
- Prácticas recomendadas de desarrollo de extensiones
- Integraciones de API web con REST, SOAP y GraphQL
- Mejoras de rendimiento para codificación e infraestructura
- Herramientas, estrategias y metodologías de prueba

Aunque algunos implementadores de soluciones pueden tener sus propias preferencias en cuanto a las metodologías, los procesos y las herramientas utilizadas en un proyecto de implementación, este manual se centra en las prácticas recomendadas y las metodologías generalmente aceptadas que se pueden compartir en la mayoría de las implementaciones.

Al igual que cualquier proyecto de TI de gran tamaño, Adobe Commerce se basa en estándares de codificación que aprovechan las prácticas recomendadas y las estandarizaciones de las tecnologías subyacentes (por ejemplo, PHP/Zend, Symfony, JavaScript, jQuery y HTML), así como en estándares creados dentro del estándar de codificación de Adobe Commerce. Seguir estos estándares es una necesidad absoluta para eliminar errores y mejorar la calidad y mantenimiento del código creado a medida.

## Adobe Commerce en la infraestructura en la nube

Adobe Commerce en la infraestructura en la nube es una plataforma de alojamiento automatizada y administrada para el software de Adobe Commerce. Adobe Commerce en la infraestructura en la nube incluye una variedad de funciones adicionales que lo diferencian de las implementaciones locales de Adobe Commerce y Magento Open Source:

![infografías de componentes de Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce en la nube proporciona una infraestructura aprovisionada previamente que incluye PHP, MySQL, Redis, [!DNL RabbitMQ], y tecnologías Elasticsearch; un flujo de trabajo basado en Git con operaciones de creación e implementación automáticas para un desarrollo rápido y eficaz y una implementación continua cada vez que se insertan cambios de código en un entorno de Platform as a Service (PaaS); archivos y herramientas de configuración de entorno altamente personalizables; y alojamiento de AWS que ofrece un entorno escalable y seguro para ventas y venta minorista en línea.

![infografías de componentes de Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
