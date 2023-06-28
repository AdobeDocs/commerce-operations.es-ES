---
title: Prácticas recomendadas de solución de problemas
description: Obtenga información sobre cómo solucionar problemas de implementación de Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Prácticas recomendadas de solución de problemas

Siga estas prácticas recomendadas para una solución de problemas eficaz de Adobe Commerce en problemas de infraestructura en la nube.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube

## Prácticas recomendadas

| Tipo de problema | Prácticas recomendadas | Recurso |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemas de implementación | **Siga las prácticas recomendadas de implementación.** El 13 % de los tickets de asistencia implican problemas de implementación. Se han actualizado las prácticas recomendadas para incluir formas de prevenir muchas de estas causas. | [Prácticas recomendadas para compilaciones e implementación](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) en nuestra documentación para desarrolladores. |
| Problemas de cierre del sitio | **Utilice el Solucionador de problemas de caída del sitio.** Los crones pueden ser de larga duración y pueden saturarse entre sí. Son la fuente de muchas interrupciones del servicio y problemas de rendimiento. | [Solucionador de problemas de Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) y [Cómo restablecer los trabajos de cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) en nuestra base de conocimiento de soporte. |
| Problemas de rendimiento | **Si no utiliza el banner de Adobe Commerce, desactívelo.** Cuando el banner está habilitado pero no se utiliza, los recursos se utilizan para realizar búsquedas en la base de datos cuando no son necesarias y provocarán problemas de rendimiento. | [Deshabilitar la salida del titular de Adobe Commerce para mejorar el rendimiento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) en nuestra base de conocimiento de soporte. |
| Buscar problemas | **El motor de búsqueda del catálogo MySQL se ha eliminado en Adobe Commerce 2.4.0.** Debe tener el host de Elasticsearch configurado antes de instalar la versión 2.4.0. Consulte Instalar y configurar Elasticsearch en la documentación para desarrolladores. | [Configuración del servicio de Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) en nuestra documentación para desarrolladores. |
| Errores personalizados | **No implementar durante las horas de mayor actividad.** Agregar y eliminar usuarios almacenará en déclencheur una implementación. | [Implementación sin tiempo de inactividad](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) en nuestra documentación para desarrolladores. |
| Errores y problemas de base de datos | **Los problemas de base de datos causan situaciones de implementación (problemas posteriores al enlace), rendimiento y cierre del sitio.** Muchos implican errores o una asignación insuficiente del espacio de la base de datos. | [Códigos de error de MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Administrar espacio de almacenamiento](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (incluida la base de datos) en nuestra documentación para desarrolladores. |
| Problemas de configuración | **Indexar por programación en lugar de Indexar al guardar.** Esta es la configuración de indexación más eficaz. Indexar al guardar provocará una reindexación completa. | [Configuración de indexadores](../../../configuration/cli/manage-indexers.md#configure-indexers) en nuestra documentación para desarrolladores. |
| Problemas de código personalizado | **Compruebe los registros de consultas lentas para ver las oportunidades de identificar y posiblemente eliminar procesos que tardan demasiado en completarse.** Las consultas lentas pueden provocar interbloqueos en la base de datos, lo que provoca caídas del sitio y problemas de rendimiento. | [Comprobación de consultas y procesos lentos que tardan demasiado en MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemas de extensión | **Utilice únicamente extensiones comprobadas que estén actualmente en el Commerce Marketplace.** | [Extensiones para Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problemas de recursos | **Supervise la memoria y el espacio disponibles y optimice el almacenamiento.** Es posible que tenga espacio disponible antes de una acción que consume recursos significativos (por ejemplo, en la implementación). Una optimización deficiente del almacenamiento de archivos (demasiadas imágenes grandes y enriquecidas, por ejemplo) también puede contribuir a que el espacio sea insuficiente. Los recursos bajos causan problemas de rendimiento, caída del sitio, implementaciones atascadas y errores de implementación. | [Administrar espacio en disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) en nuestra documentación para desarrolladores; [Almacenamiento de archivos bajo/agotado, cargas de página específicas lentas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) en nuestra base de conocimiento de soporte. |
