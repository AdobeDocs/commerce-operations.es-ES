---
title: Implementación de actualización
description: Obtenga información acerca de las diferentes fases de la implementación de actualización para proyectos de Adobe Commerce.
exl-id: d64855a7-73ee-463f-a314-6a8d4ebe4726
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 1%

---

# Actualizar implementación

La implementación de la actualización consta de cinco fases:

- Análisis de actualización
- Desarrollo y control de calidad (QA)
- Pruebas de aceptación de usuarios (UAT) y preparación para el lanzamiento
- Launch
- Posterior al lanzamiento

## Análisis de actualización

El análisis es posiblemente la parte más importante del proceso de actualización. Un análisis bien ejecutado le ahorra tiempo y limita las sorpresas en el futuro. El resultado de esta fase debe ser una lista de comprobación de actualización detallada y un documento con todas las dependencias.

Los siguientes son elementos que puede que desee incluir en un análisis exhaustivo:

- **Ámbito de la versión de Target**: documentación sobre [Experience League](../../release/release-notes/overview.md) y la información de los seminarios web de versiones de socios proporcionan todos los detalles que debe conocer sobre la actualización de target.

- **[!DNL Upgrade Compatibility Tool]resultados**: esta herramienta hace que cualquier actualización sea más rápida y sencilla comparando el código actual con el código de la versión de destino y generando un informe de todos los problemas que deben solucionarse. Consulte la [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Los detalles clave del informe incluyen:

   - Versión instalada actual
   - Actualizar versión de destino
   - Número y detalles de errores críticos encontrados

- Actualización de servicios para admitir la versión de destino. Utilice la siguiente plantilla de tabla para asignar los servicios que debe actualizar. Utilice el [requisitos del sistema](../../installation/system-requirements.md) para determinar qué añadir al _Actualizar a_ columna.


   | Servicio | Versión actual | Actualizar a | Notas |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7.4 | 8.1 |  |
   | Redis | 6.0 | 6.2 |  |
   | [!DNL RabbitMQ] | 3.8 | 3.9 | No se está utilizando actualmente, pero deberíamos considerar su uso |
   | MariaDB (Cloud) | 10.4 | 10.6 |  |
   | MySQL | 8.0 | -/-/ |  |
   | Compositor | 1.9.2 | 2.2 |  |
   | Elasticsearch | 7.10 | 7.17 |  |

- **Extensiones y módulos de terceros**: utilice esta plantilla de tabla para comprender el estado de las extensiones y personalizaciones, de modo que pueda tomar decisiones estratégicas y definir acciones. Esta es una oportunidad para reemplazar cualquier extensión que pueda ser nativa de Adobe Commerce o Magento Open Source para minimizar la complejidad del proyecto. Utilice el `bin/magento module:status` para ver una lista de módulos y extensiones.

   | # | Extensión/<br>nombre del módulo | Paquete Composer | Proveedor | Versión actual | Funcionalidad | Compatible con lo último<br>¿Versión de Commerce? | Problemas | ¿Nativo de Commerce? | Acción | Notas |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Nombre de la extensión y vínculo | extension/<br>extensionx-magento-2 | Nombre del proveedor | Versión instalada | Requisitos empresariales | Sí/No | Enumerar los problemas identificados que enfrenta esta extensión | Sí/No | Conservar/Reemplazar/<br>Eliminar |  |

- **Módulos personalizados**: similar a la tabla de módulos de terceros, esta plantilla le ayuda a realizar un seguimiento y comprender el estado y las acciones necesarias para actualizar módulos personalizados.

   | # | Nombre de módulo | Funcionalidad | ¿Requerido? | ¿Nativo de Commerce? | Acción | Notas |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Nombre de módulo | Requisitos empresariales | Sí/No | Sí/No | Conservar/Reemplazar/Quitar |  |

- **Paquetes del compositor y dependencias en composer.json que requieren una actualización.**

Además, los socios pueden participar en [Versiones beta de Adobe Commerce](../../release/beta.md) y utilice las oportunidades previas al lanzamiento para obtener acceso anticipado al código de una próxima versión. El acceso anticipado al código ayuda a los desarrolladores a prepararse con tiempo suficiente para completar la actualización antes de la fecha de disponibilidad general (GA). El código beta se suele publicar cinco semanas antes de la fecha de GA y las versiones preliminares se publican dos semanas antes.

## Desarrollo y control de calidad

Las pruebas son la fase de una actualización que requiere más tiempo. Como resultado, este proceso debe ser lo más automatizado posible. El _[Guía de prueba de aplicaciones](https://developer.adobe.com/commerce/testing/guide/)_ proporciona detalles sobre cómo configurar y utilizar las herramientas de prueba de sistemas y plataformas para un control de calidad más rápido. Utilice un entorno de ensayo para probar y validar la actualización antes de pasar a producción.

## UAT y preparación para el lanzamiento

UAT es una de las últimas etapas de la actualización que requiere la revisión y validación del sitio. También debe decidir cuándo implementar y si necesita una página de mantenimiento. Planifique los procesos de cron y los mensajes de terceros.

A medida que se acerca la fecha de despliegue, la comunicación es esencial. Si más personas conocen el cambio en el horizonte, cómo les afecta y cómo deben abordarlo, entonces es más probable que su lanzamiento sea exitoso. No tenga miedo de comunicar en exceso cada paso del camino: aumenta la probabilidad de reseñas brillantes de todos los involucrados una vez que salga en vivo.

## Launch

Complete la actualización implementando en producción y actualizando las extensiones. Asegúrese de probar los flujos de ruta críticos con pedidos simulados. Consulte estos [prácticas recomendadas](../prepare/best-practices.md) para obtener algunas sugerencias sobre el inicio con problemas mínimos.

Siga su plan de comunicación y asegúrese de que todas las partes interesadas estén al tanto de la actualización y completamente formadas para apoyarla.

Por último, informe a su equipo para determinar las lecciones aprendidas y los inconvenientes. Esta retrospectiva le ayuda a mejorar el proceso la próxima vez.

## Posterior al lanzamiento

Una vez que se inicie el sitio, asegúrese de comprobar los datos de análisis, la consola de búsqueda de Google y otros recursos para garantizar que no haya problemas inesperados y que todo funcione según lo esperado.

Siempre es una buena idea vigilar el rendimiento con herramientas de monitorización bien diseñadas. Existen muchas herramientas y medios para monitorizar el rendimiento de su sitio, por lo que asegúrese de elegir uno que se adapte bien a su organización. Recomendamos que los clientes de Adobe Commerce que utilicen nuestro sistema de administración de la infraestructura en la nube aprovechen servicios como [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html) para supervisar el rendimiento del sitio.
