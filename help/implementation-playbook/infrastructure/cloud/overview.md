---
title: Información general sobre la infraestructura de nube
description: Obtenga información sobre Adobe Commerce en infraestructura de nube.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Información general

Adobe Commerce ofrece una de las opciones de alojamiento administrado más populares para Adobe Commerce en AWS. Adobe Commerce en infraestructura en la nube es una plataforma de alojamiento automatizada completamente administrada para el software Adobe Commerce.

Adobe Commerce en infraestructura en la nube es una oferta de plataforma como servicio (PaaS) que permite una rápida implementación de tiendas web totalmente personalizables, seguras y escalables, combinadas con una infraestructura de servicios administrados y de alojamiento líder. Ofrece dos planos con diferentes infraestructuras. Adobe Commerce Starter es el más adecuado para tiendas más pequeñas con menos complejidad y catálogos más pequeños. Adobe Commerce Pro está diseñado para grandes tiendas con más complejidad, catálogos de productos más grandes o tráfico que alcanza su punto máximo. Adobe Commerce determinará la arquitectura adecuada con las aportaciones de los socios.

Adobe Commerce está listo para la nube con una infraestructura de alojamiento en varios niveles completamente redundante que proporciona rendimiento optimizado, flexibilidad y escalabilidad elástica. Puede ejecutar de forma eficaz su plataforma de comercio en la red de distribución de contenido (CDN) de Finfinidad y, con New Relic para la supervisión y administración, puede mantener el entorno de su tienda funcionando sin problemas.

Adobe Commerce ofrece todas las ventajas de la informática en la nube moderna que se asocian más comúnmente con las soluciones SaaS: escalabilidad elástica, alta resiliencia y disponibilidad, cumplimiento de PCI, disponibilidad global y parches automatizados, al tiempo que se mantiene la flexibilidad en la personalización de software que requieren nuestros comerciantes.

![Diagrama que muestra los elementos arquitectónicos de Adobe Commerce en la infraestructura de la nube](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Ventajas

Otras ventajas de Adobe Commerce son:

- **Optimizado para Adobe Commerce**. Los scripts de compilación y la configuración de servicio desarrollados por Adobe Commerce garantizan que todas las instancias estén correctamente ajustadas y configuradas para obtener un rendimiento de comerciante óptimo.

- **Versiones coherentes y seguras**. Todas las implementaciones de código se basan en Git para mantener la coherencia y la repetibilidad, con entornos de producción de solo lectura para reforzar la seguridad.

- **Flexibilidad para socios**. Una API de REST completa y una interfaz de línea de comandos con secuencias de comandos que permiten una integración sencilla con sistemas externos y la compatibilidad con flujos de trabajo de administración de código existentes.

- **Conjunto de herramientas de implementación flexible**. Invertir, combinar, clonar y eliminar rápidamente entornos ilimitados a su voluntad para tareas de desarrollo, pruebas de control de calidad o diagnóstico de problemas de producción.

- **Entrega continua en la nube**. Pásese con confianza directamente del desarrollo a la UAT a la producción, de forma continua entre las ramas de código y los equipos de desarrollo.

## Servicios de terceros

Echemos un vistazo al software que hace realidad los beneficios de Adobe Commerce.

![Diagrama que muestra Adobe Commerce en la pila de tecnología de infraestructura en la nube](../../../assets/playbooks/cloud-tech-stack.svg)

- CDN de tamaño más rápido: A medida que los clientes acceden al sitio y a las tiendas, las solicitudes llegan a Facebook para cargar las páginas en caché más rápido. Finfinito WAF también proporciona servicio de protección DDoS.

- New Relic le ofrece una vista completa de sus aplicaciones y entorno operativo. Le permite combinar métricas clave de aplicaciones móviles y de navegador con servicios de soporte, almacenes de datos y hosts para que pueda optimizar el rendimiento de forma integral y garantizar el éxito de cada iniciativa.

- Composer administra dependencias y actualizaciones en Adobe Commerce y proporciona contexto sobre los paquetes incluidos, lo que hacen los paquetes y cómo se ajustan juntos.

- Git es su código en repositorios. Permite ramificación local, áreas de ensayo prácticas y múltiples flujos de trabajo con compilación e implementación automáticas para un desarrollo rápido y eficiente y una implementación continua.

- Platform-as-a-Service (PaaS) proporciona una infraestructura preaprovisionada que incluye tecnologías PHP, MySQL, Redis, RabbitMQ y Elasticsearch.

- El alojamiento en la nube de AWS o Azure potencia la infraestructura como servicio (IaaS) subyacente, que ofrece un entorno escalable y seguro para ventas y ventas al por menor en línea.
