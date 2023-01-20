---
user-guide-title: Guía de implementación
user-guide-description: Obtenga información acerca de las estrategias para planificar e implementar un sitio de Adobe Commerce con éxito.
mini-toc-levels: 3
source-git-commit: 338a99f4f047640ac4bb944ac8599301cba5f646
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 6%

---


# Guía de implementación {#implementation-playbook}

- [Información general](overview.md)
- Comercio {#intro}
   - [Acerca de Adobe Commerce](intro/about-commerce.md)
   - [Principios del desarrollo de plataformas](intro/platform-development.md)
- Ámbito del proyecto {#project-scope}
   - [El conocimiento es poder](project-scope/knowledge.md)
   - [Principales partes interesadas](project-scope/key-stakeholders.md)
   - [Proceso y cronología](project-scope/process-timeline.md)
   - [Deliverables](project-scope/deliverables.md)
   - [Listas de comprobación de requisitos](project-scope/requirement-checklists.md)
- Desarrollo {#development}
   - [Herramientas de plataforma](development/platform-tools.md)
   - [Herramientas de administración de proyectos](development/project-management-tools.md)
   - [Metodología de implementación de proyectos](development/delivery.md)
   - [Control de calidad](development/quality-control.md)
- Planificación y gobernanza {#planning}
   - [Enfoque de ejecución y planificación](planning/delivery.md)
   - [Responsabilidad y titularidad](planning/ownership.md)
   - [Administración de proyectos](planning/governance.md)
- Arquitectura e integraciones {#architecture}
   - [Competencias](architecture/capabilities.md)
   - [Estrategia de integración](architecture/integration-strategy.md)
   - [Estrategia de extensibilidad](architecture/extensibility-strategy.md)
   - [Opciones de integración](architecture/integration-options.md)
   - [Arquitectura de referencia global](architecture/global-reference.md)
   - Comercio sin encabezado {#headless}
      - [Ventajas](architecture/headless/benefits.md)
      - [Recorrido a desatendido](architecture/headless/journey-to-headless.md)
      - [Microservicios](architecture/headless/microservices.md)
      - [Evolución de la cabeza](architecture/headless/evolution.md)
      - [Arquitectura de tienda acoplada](architecture/headless/legacy-storefront.md)
      - [Arquitectura sin encabezado](architecture/headless/adobe-commerce.md)
- Infraestructura e implementación {#infrastructure}
   - [Información general](infrastructure/overview.md)
   - [Infraestructura local](infrastructure/on-premises.md)
   - Infraestructura de nube {#cloud}
      - [Información general](infrastructure/cloud/overview.md)
      - [Regiones](infrastructure/cloud/regions.md)
      - [Tecnologías](infrastructure/cloud/technology.md)
      - [Entornos](infrastructure/cloud/environments.md)
      - [Servicios administrados](infrastructure/cloud/managed-services.md)
      - [Seguridad y cumplimiento](infrastructure/cloud/security.md)
   - Optimización del rendimiento {#performance}
      - [Problemas habituales](infrastructure/performance/optimization.md)
      - [Prueba comparativa](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Preparación para el lanzamiento {#launch}
   - [Información general](launch/overview.md)
   - [Pasos previos al lanzamiento](launch/pre-launch-steps.md)
   - [Pasos de Launch](launch/launch-steps.md)
   - [Pasos posteriores al lanzamiento](launch/post-launch-steps.md)
- Mantenimiento y asistencia {#maintenance}
   - [Información general](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Prácticas recomendadas {#best-practices}
   - [Información general](best-practices/phases.md)
   - Planificación {#planning}
      - [Información general](best-practices/planning/overview.md)
      - [Sitios, tiendas y configuración de vista de tienda](best-practices/planning/sites-stores-store-views.md)
      - [Configuración de informes](best-practices/planning/reporting-configuration.md)
      - [Configuración de la base de datos para implementaciones en la nube &#x200B;](best-practices/planning/database-on-cloud.md)
      - [Configuración de conexión esclava de MySQL &#x200B;](best-practices/planning/configure-mysql-slave-connection-on-cloud.md)
      - [Uso de déclencheur MySQL](best-practices/planning/mysql-triggers-usage.md)
      - [Configuración del servicio Redis](best-practices/planning/redis-service-configuration.md)
      - [Tamaño de memoria OPcache](best-practices/planning/opcache-memory-size.md)
      - [Tamaño de caché de la ruta de acceso real](best-practices/planning/realpath-cache-size.md)
      - [Categorías](best-practices/planning/category-limits.md)
      - [Product](best-practices/planning/product-sku-limits.md)
      - [Variaciones de productos](best-practices/planning/product-variations.md)
      - [Opciones de producto](best-practices/planning/product-options.md)
      - [Atributos del producto](best-practices/planning/product-attributes-and-options.md)
      - [Paginación de la lista de productos](best-practices/planning/product-listing-pagination.md)
      - [Límite del carro de productos](best-practices/planning/product-cart.md)
      - [Promociones](best-practices/planning/product-cart-promotions.md)
      - [Extensiones](best-practices/planning/extensions.md)
      - [Escalaciones de socios](best-practices/planning/partner-escalation.md)
      - [Procesamiento de almacenamiento de pagos](best-practices/planning/payment-processing-storage.md)
   - Desarrollo {#development}
      - [Información general](best-practices/development/overview.md)
      - [Optimización de imágenes](best-practices/development/image-optimization.md)
      - [Resolución de problemas](best-practices/development/troubleshooting.md)
      - [Optimización de archivos CSS y JS](best-practices/development/optimize-css-js-files.md)
      - [Bloques de contenido privado](best-practices/development/private-content-block-configuration.md)
      - [Implementación de contenido estático](best-practices/development/static-content-deployment.md)
      - [Modificación de tablas de base de datos](best-practices/development/modifying-core-and-third-party-tables.md)
   - Launch {#launch}
      - [Información general](best-practices/launch/overview.md)
      - [Servicio de notificaciones de seguridad de Adobe](best-practices/launch/security-notification-service.md)
      - [Configuración del archivo robots.txt](best-practices/launch/robots-txt.md)
      - [Prevención y respuesta de incidentes de seguridad](best-practices/launch/prevent-respond-security-incident.md)
   - Mantenimiento {#maintenance}
      - [Información general](best-practices/maintenance/overview.md)
      - [Rendimiento del front-end de auditoría](best-practices/maintenance/frontend-performance.md)
      - [Configuración del indexador](best-practices/maintenance/indexer-configuration.md)
      - [Procesamiento de pedidos](best-practices/maintenance/order-processing-configuration.md)
      - [Programación de actualizaciones de administración en sitios de producción](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Actualizar servicios](best-practices/maintenance/update-services.md)
      - [Actualizar lista de comprobación](best-practices/maintenance/upgrade-checklist.md)
      - [Resolver problemas de rendimiento de la base de datos &#x200B;](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Requisitos previos de actualización de Adobe Commerce 2.3.5 para &#x200B; de MariaDB](best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Volver a las guías operativas](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
