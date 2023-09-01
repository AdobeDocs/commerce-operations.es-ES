---
title: Resumen de infraestructura en nube
description: Obtenga información acerca de Adobe Commerce en la infraestructura en la nube.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Información general

Una de las opciones de alojamiento administrado más populares para Adobe Commerce en AWS la ofrece el propio Adobe Commerce. Adobe Commerce en la infraestructura en la nube es una plataforma de alojamiento automatizado y totalmente gestionada para el software Adobe Commerce.

Adobe Commerce en la infraestructura en la nube es una oferta de plataforma como servicio (PaaS) que permite una implementación rápida de tiendas web totalmente personalizables, seguras y escalables combinadas con una infraestructura de alojamiento y Managed Services líder. Ofrece dos planes con diferentes infraestructuras. Adobe Commerce [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) Los planes de son más adecuados para tiendas más pequeñas con menos complejidad y catálogos más pequeños. Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) los planes están diseñados para tiendas más grandes con más complejidad, catálogos de productos más grandes o tráfico que alcanza su punto máximo. El Adobe determina la arquitectura adecuada con la entrada de los socios.

Adobe Commerce está preparado para la nube con una infraestructura de alojamiento de varias nubes totalmente redundante que proporciona un rendimiento optimizado, resiliencia y escalabilidad elástica. Puede ejecutar de forma eficaz su plataforma de comercio en la red de distribución de contenido (CDN) de Fastly, y con New Relic para la monitorización y la administración, puede mantener el entorno de su tienda funcionando sin problemas.

Adobe Commerce ofrece todas las ventajas de la computación en la nube moderna que normalmente se asocian con las soluciones SaaS y, al mismo tiempo, mantiene la flexibilidad en la personalización del software:

- Adaptación elástica
- Alta resiliencia y disponibilidad
- Conformidad con PCI
- Disponibilidad global y aplicación automatizada de parches

![Diagrama que muestra los elementos arquitectónicos de Adobe Commerce en la infraestructura en la nube](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Ventajas

Otras ventajas de Adobe Commerce son:

- **Optimizado para Adobe Commerce**. Los scripts de compilación y la configuración de servicios desarrollados por Adobe Commerce garantizan que cada instancia esté correctamente ajustada y configurada para un rendimiento óptimo del comerciante.

- **Versiones coherentes y seguras**. Todas las implementaciones de código están basadas en Git para mantener la coherencia y la repetibilidad, con entornos de producción de solo lectura para reforzar la seguridad.

- **Flexibilidad para los socios**. Una API REST completa y una interfaz de línea de comandos mediante scripts garantizan la facilidad de integración con sistemas externos y la compatibilidad con los flujos de trabajo de administración de código existentes.

- **Conjunto de herramientas de implementación flexible**. Gire, fusione, clone y elimine rápidamente entornos ilimitados a voluntad para tareas de desarrollo, pruebas de control de calidad o diagnósticos de problemas de producción.

- **Entrega continua en la nube**. Cambie con confianza directamente del desarrollo a UAT y a la producción, de forma continua entre ramas de código y equipos de desarrollo.

## Servicios de terceros

Esta sección resume los servicios y las herramientas clave de terceros para Adobe Commerce en proyectos de infraestructura en la nube. Consulte [Pila de tecnología](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) en el _Guía de Cloud_ para obtener más información.

- **Fastly CDN**: A medida que los clientes acceden al sitio y a las tiendas, las solicitudes llegan rápidamente para cargar las páginas en caché más rápido. Fastly WAF también proporciona un servicio de protección DDoS.

- **New Relic**: proporciona una vista completa de las aplicaciones y del entorno operativo. New Relic le permite combinar métricas clave de aplicaciones móviles y de explorador con servicios de soporte, almacenes de datos y hosts de modo que pueda optimizar el rendimiento de forma integral y garantizar el éxito de cada iniciativa.

- **Compositor**: administra dependencias y actualizaciones en Adobe Commerce y proporciona contexto sobre los paquetes incluidos, qué hacen los paquetes y cómo encajan.

- **Git**: Proporciona administración del código fuente. Git permite la ramificación local, áreas de ensayo cómodas y varios flujos de trabajo con generación e implementación automáticas para un desarrollo rápido y eficiente y una implementación continua.

- **Plataforma como servicio (PaaS)**: Proporciona una infraestructura aprovisionada previamente que incluye PHP, MySQL, Redis, [!DNL RabbitMQ]y las tecnologías OpenSearch o Elasticsearch.

- **Alojamiento en la nube de AWS o Azure**: Impulsa la infraestructura como servicio (IaaS) subyacente, que ofrece un entorno escalable y seguro para las ventas y la venta minorista en línea.
