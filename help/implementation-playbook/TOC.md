---
user-guide-title: Guía de implementación
user-guide-description: Obtenga información acerca de las estrategias para planificar e implementar un sitio de Adobe Commerce con éxito.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 12%

---


# Guía de implementación {#implementation-playbook}

- [Información general](overview.md)
- Commerce {#intro}
   - [Acerca de Adobe Commerce](intro/about-commerce.md)
   - [Principios del desarrollo de plataformas](intro/platform-development.md)
- Ámbito del proyecto {#project-scope}
   - [El conocimiento es poder](project-scope/knowledge.md)
   - [Partes interesadas clave](project-scope/key-stakeholders.md)
   - [Proceso y cronología](project-scope/process-timeline.md)
   - [Entregables](project-scope/deliverables.md)
   - [Listas de comprobación de requisitos](project-scope/requirement-checklists.md)
- Desarrollo {#development}
   - [Herramientas de Platform](development/platform-tools.md)
   - [Herramientas de administración de proyectos](development/project-management-tools.md)
   - [Metodología de ejecución del proyecto](development/delivery.md)
   - [Control de calidad](development/quality-control.md)
- Planificación y administración {#planning}
   - [Enfoque de entrega y planificación](planning/delivery.md)
   - [Responsabilidad y propiedad](planning/ownership.md)
   - [Gobernanza del proyecto](planning/governance.md)
- Arquitectura e integraciones {#architecture}
   - [Referencia empresarial](architecture/enterprise-blueprint.md)
   - Arquitectura de referencia global {#global-reference-architecture}
      - [Información general](architecture/global-reference/overview.md)
      - [Ejemplos](architecture/global-reference/examples.md)
      - Desarrollo del compositor {#composer}
         - [Información general](architecture/global-reference/composer/overview.md)
         - [Estructura del proyecto](architecture/global-reference/composer/project-structure.md)
         - [Sugerencias y trucos](architecture/global-reference/composer/tips-and-tricks.md)
- Infraestructura e implementación {#infrastructure}
   - [Información general](infrastructure/overview.md)
   - Alojamiento propio {#self-hosting}
      - [Información general](infrastructure/self-hosting/overview.md)
      - [Infraestructura local](infrastructure/self-hosting/on-premises.md)
      - [Conceptos de seguridad](infrastructure/self-hosting/security-concepts.md)
      - [Monitorización de telemetría y herramientas](infrastructure/self-hosting/monitoring-tools.md)
      - [Ideas de recuperación ante desastres](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Sugerencias de rendimiento](infrastructure/self-hosting/performance-tips.md)
   - Infraestructura en la nube {#cloud}
      - [Información general](infrastructure/cloud/overview.md)
      - [Regiones](infrastructure/cloud/regions.md)
      - [Tecnologías](infrastructure/cloud/technology.md)
      - [Seguridad y cumplimiento](infrastructure/cloud/security.md)
   - Optimización de rendimiento {#performance}
      - [Problemas habituales](infrastructure/performance/optimization.md)
      - [Puntos de referencia](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Preparación para el inicio {#launch}
   - [Información general](launch/overview.md)
   - [Pasos previos al lanzamiento](launch/pre-launch-steps.md)
   - [Pasos del inicio](launch/launch-steps.md)
   - [Pasos del inicio de Post](launch/post-launch-steps.md)
- Mantenimiento y soporte técnico {#maintenance}
   - [Información general](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Prácticas recomendadas {#best-practices}
   - [Información general](best-practices/phases.md)
   - Planificando {#planning}
      - [Información general](best-practices/planning/overview.md)
      - [Administración de catálogos](best-practices/planning/catalog-management.md)
      - [Configuración de sitios, tiendas y vistas de tiendas](best-practices/planning/sites-stores-store-views.md)
      - [Configuración de informes](best-practices/planning/reporting-configuration.md)
      - [Configuración de bases de datos para implementaciones en la nube&#x200B;](best-practices/planning/database-on-cloud.md)
      - [Configuración de MySQL](best-practices/planning/mysql-configuration.md)
      - [Configuración del servicio Redis](best-practices/planning/redis-service-configuration.md)
      - [Tamaño de memoria de OPcache](best-practices/planning/opcache-memory-size.md)
      - [Tamaño de caché de RealPath](best-practices/planning/realpath-cache-size.md)
      - [Extensiones](best-practices/planning/extensions.md)
      - [Escalaciones de Partner](best-practices/planning/partner-escalation.md)
      - [Procesamiento de almacenamiento de pagos](best-practices/planning/payment-processing-storage.md)
   - Desarrollo {#development}
      - [Información general](best-practices/development/overview.md)
      - [Prácticas recomendadas generales](best-practices/development/general.md)
      - [Administración de código](best-practices/development/code-management.md)
      - [Revisión de código](best-practices/development/code-review.md)
      - [Depuración](best-practices/development/debugging.md)
      - [Control de excepciones](best-practices/development/exception-handling.md)
      - [Ramificación Git](best-practices/development/git-branching.md)
      - [Cambio de tamaño de imagen de catálogo](best-practices/development/catalog-image-resizing.md)
      - [Optimización de imagen](best-practices/development/image-optimization.md)
      - [Resolución de problemas](best-practices/development/troubleshooting.md)
      - [Optimización de archivos CSS y JS](best-practices/development/optimize-css-js-files.md)
      - [Bloques de contenido privado](best-practices/development/private-content-block-configuration.md)
      - [Implementación de contenido estático](best-practices/development/static-content-deployment.md)
      - [Modificación de tablas de base de datos](best-practices/development/modifying-core-and-third-party-tables.md)
      - [Modificar código principal y de terceros](best-practices/development/modifying-core-and-third-party-code.md)
   - Iniciar {#launch}
      - [Información general](best-practices/launch/overview.md)
      - [Configuración de rastreadores web](best-practices/launch/robots-txt.md)
      - [Proteja su sitio e infraestructura](best-practices/launch/security-best-practices.md)
   - Mantenimiento {#maintenance}
      - [Información general](best-practices/maintenance/overview.md)
      - [Auditar el rendimiento de front-end](best-practices/maintenance/frontend-performance.md)
      - [Optimización del rendimiento back-end](best-practices/maintenance/backend-performance.md)
      - [Configuración del indizador](best-practices/maintenance/indexer-configuration.md)
      - [Parches a escala](best-practices/maintenance/patching-at-scale.md)
      - [Procesamiento de pedidos](best-practices/maintenance/order-processing-configuration.md)
      - [Resolver problemas de rendimiento de base de datos](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Responder a incidentes de seguridad](best-practices/maintenance/respond-to-security-incident.md)
      - [Programación de actualizaciones de administración en sitios de producción](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Actualizar servicios](best-practices/maintenance/update-services.md)
      - [Lista de comprobación de actualización](best-practices/maintenance/upgrade-checklist.md)
      - [Actualizar los requisitos previos de MariaDB](best-practices/maintenance/mariadb-upgrade.md)
- [Volver a las guías operativas](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
