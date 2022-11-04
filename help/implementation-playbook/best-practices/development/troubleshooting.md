---
title: Prácticas recomendadas para la resolución de problemas
description: Obtenga información sobre cómo solucionar problemas de implementación de Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 754051c98d2c5265398f1f0806cb34128fe03c36
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Prácticas recomendadas para la resolución de problemas

Siga estas prácticas recomendadas para solucionar problemas eficaces de Adobe Commerce en problemas de infraestructura en la nube.

## Productos y versiones afectados

Adobe Commerce en infraestructura en la nube

## Prácticas recomendadas

| Tipo de problema | Prácticas recomendadas | Recurso |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemas de implementación | **Siga las prácticas recomendadas de implementación.** El 13 % de los tickets de asistencia implican problemas de implementación. Se han actualizado las prácticas recomendadas para incluir formas de prevenir muchas de estas causas. | [Prácticas recomendadas para compilaciones e implementación](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) en nuestra documentación para desarrolladores. |
| Problemas de acceso al sitio | **Utilice el Solucionador de problemas de visitas en el sitio.** Los crones pueden durar mucho tiempo y pueden desbordarse entre sí. Son la fuente de muchas interrupciones del servicio y problemas de rendimiento. | [Solucionador de problemas de visitas en el sitio](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) y [Restablecer trabajos cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) en nuestra base de conocimientos de soporte. |
| Problemas de rendimiento | **Si no utiliza un banner de Adobe Commerce, desactívelo.** Cuando el banner está habilitado pero no se utiliza, los recursos se utilizan para realizar búsquedas en la base de datos cuando no son necesarios y esto provocará problemas de rendimiento. | [Desactivar la salida de Adobe Commerce Banner para mejorar el rendimiento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) en nuestra base de conocimientos de soporte. |
| Problemas de búsqueda | **El motor de búsqueda del catálogo MySQL se eliminó en Adobe Commerce 2.4.0.** Debe tener configurado el host de Elasticsearch y configurado antes de instalar la versión 2.4.0. Consulte Instalar y configurar el Elasticsearch en nuestra documentación para desarrolladores. | [Configuración del servicio Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) en nuestra documentación para desarrolladores. |
| Errores personalizados | **No implemente durante las horas punta.** Añadir y eliminar usuarios supondrá un déclencheur para una implementación. | [Implementación sin downtime](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) en nuestra documentación para desarrolladores. |
| Errores y problemas en la base de datos | **Los problemas con la base de datos causan la implementación (problemas con los vínculos posteriores), rendimiento y situaciones de inactividad del sitio.** Muchos implican errores o una asignación insuficiente del espacio de la base de datos. | [Códigos de error de MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Administrar espacio de almacenamiento](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (incluida la base de datos) en nuestra documentación para desarrolladores. |
| Problemas de configuración | **Índice por programa en lugar de Índice en Guardar.** Esta es la configuración de indexación más eficiente. El índice de Guardar provocará una reindexación completa. | [Configuración de indexadores](../../../configuration/cli/manage-indexers.md#configure-indexers) en nuestra documentación para desarrolladores. |
| Problemas con el código personalizado | **Compruebe los registros de consulta lentos para obtener oportunidades de identificar y posiblemente matar procesos que tardan demasiado en completarse.** Las consultas lentas pueden causar interbloqueos de la base de datos, lo que provoca problemas de rendimiento y bajas del sitio. | [Comprobación de consultas y procesos lentos que tardan demasiado en MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemas de extensión | **Utilice únicamente extensiones verificadas actualmente en el Commerce Marketplace.** | [Extensiones para Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problemas de recursos | **Monitorice la memoria y el espacio disponibles y optimice el almacenamiento.** Es posible que tenga espacio disponible antes de una acción que consuma recursos importantes (implementación, por ejemplo). La mala optimización del almacenamiento de archivos (demasiadas imágenes enriquecidas y grandes, por ejemplo) también puede contribuir a que el espacio sea insuficiente. Los recursos bajos causan problemas de rendimiento, visitas en el sitio, implementaciones atascadas y errores de implementación. | [Administrar espacio en disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) en nuestra documentación para desarrolladores; [Almacenamiento de archivos bajo/agotado, cargas de página específicas son lentas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) en nuestra base de conocimientos de soporte. |
