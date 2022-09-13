---
title: Implementación de actualización
description: Obtenga información sobre las distintas fases de implementación de la actualización para proyectos de Adobe Commerce y Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 1%

---


# Implementación de actualización

La implementación de la actualización consta de cinco fases:

- Análisis de actualización
- Desarrollo y garantía de calidad
- Pruebas de aceptación del usuario (UAT) y preparación para el inicio
- Launch
- Posterior al lanzamiento

## Análisis de actualización

Podría decirse que el análisis es la parte más importante del proceso de actualización. Un análisis bien ejecutado le ahorra tiempo y limita las sorpresas futuras. El resultado de esta fase debe ser una lista de comprobación de actualización detallada y un documento con todas las dependencias.

Los siguientes son elementos que puede que desee incluir en un análisis exhaustivo:

- **Alcance de la versión de target**—Documentación sobre [Documentos de desarrollo comercial](https://devdocs.magento.com) y la información de los seminarios web de la versión del socio le proporcionan todos los detalles que debe conocer sobre su actualización de destino.

- **[!DNL Upgrade Compatibility Tool]resultados**: esta herramienta facilita y agiliza cualquier actualización comparando el código actual con el código de la versión de destino y produciendo un informe de todos los problemas que deben solucionarse. Consulte la [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md). Los detalles clave del informe incluyen:

   - Versión instalada actual
   - Actualizar la versión de destino
   - Número y detalles de errores críticos encontrados

- Actualización de servicios para admitir la versión de destino. Utilice la siguiente plantilla de tabla para asignar los servicios que debe actualizar. Utilice la variable [requisitos del sistema](../../installation/system-requirements.md) para determinar qué añadir a la variable _Actualizar a_ para abrir el Navegador.


   | Servicio | Versión actual | Actualizar a | Notas |
   |-----------------|-----------------|------------|----------------------------------------------------------|
   | PHP | 7,2,33 | 8,1 |  |
   | Redis | 5,05 | 6,0 |  |
   | RabbitMQ | 3,7 | 3,8 | No se está utilizando actualmente, pero debemos considerar su uso |
   | MariaDB (Cloud) | 10.2.33 | 10,4 |  |
   | MySQL | 8,0 |  |  |
   | Compositor | 1.9.2 | 2,0 |  |
   | Elasticsearch | 7,7 | 7,10 |  |

- **Extensiones y módulos de terceros**: utilice esta plantilla de tabla para comprender el estado de sus extensiones y personalizaciones, de modo que pueda tomar decisiones estratégicas y definir acciones. Esta es una oportunidad para reemplazar cualquier extensión que pueda ser nativa de Adobe Commerce o Magento Open Source para minimizar la complejidad del proyecto. Utilice la variable `bin/magento module:status` para ver una lista de módulos y extensiones.

   | # | Extensión/<br>nombre del módulo | Paquete de compositor | Proveedor | Versión actual | Funcionalidad | Compatible con la última versión<br>Versión comercial? | Problemas | ¿Nativo en comercio? | Acción | Notas |
   |---|-----------------------------|------------------------------------|-------------|-------------------|-----------------------|---------------------------------------------|--------------------------------------------------|---------------------|-------------------------|-------|
   | 1 | Nombre y vínculo de la extensión | extension/<br>extensionx-magento-2 | Nombre del proveedor | Versión instalada | Requisitos empresariales | Sí/No | Lista de problemas identificados con esta extensión | Sí/No | Mantener/Reemplazar/<br>Eliminar |  |

- **Módulos personalizados**: similar a la tabla de módulos de terceros, esta plantilla le ayuda a realizar un seguimiento y comprender el estado y las acciones necesarias para actualizar los módulos personalizados.

   | # | Nombre del módulo | Funcionalidad | ¿Requerido? | ¿Nativo en comercio? | Acción | Notas |
   |---|--------------|-----------------------|-----------|---------------------|---------------------|-------|
   | 1 | Nombre del módulo | Requisitos empresariales | Sí/No | Sí/No | Mantener/Reemplazar/Quitar |  |

- **Paquetes de compositor y dependencias en composer.json que requieren una actualización.**

Además, los socios pueden participar en la [Programa Beta de Adobe Commerce](https://devdocs.magento.com/release/beta-program.html) y utilice las oportunidades previas al lanzamiento para obtener acceso anticipado al código para una próxima versión. Obtener acceso al código antes de tiempo ayuda a los desarrolladores a prepararse con tiempo suficiente para completar la actualización antes de la fecha de disponibilidad general (GA). El código beta se suele publicar cinco semanas antes de la fecha de GA y los lanzamientos previos se lanzan con dos semanas de anticipación. Para la versión 2.4.4, Adobe comenzó a publicar código beta cinco meses antes de la fecha de disponibilidad general (8 de marzo de 2022), de modo que los socios puedan empezar a prepararse para esa actualización ya [registro para el programa](https://community.magento.com/t5/Magento-DevBlog/BREAKING-NEWS-2-4-4-beta-releases-are-coming-soon/ba-p/484310).

## Desarrollo y control de calidad

La prueba es la fase de una actualización que requiere la mayor cantidad de tiempo. Como resultado, este proceso debe ser lo más automatizado posible. La variable _[Guía de prueba de aplicaciones](https://developer.adobe.com/commerce/testing/guide/)_ proporciona detalles sobre cómo configurar y utilizar herramientas de prueba de sistemas y plataformas para un control de calidad más rápido. Utilice un entorno de ensayo para probar y validar la actualización antes de pasar a producción.

## UAT y preparación para el lanzamiento

UAT es una de las últimas etapas de la actualización que requiere revisar y validar el sitio. También debe decidir cuándo implementar y si necesita una página de mantenimiento. Planifique procesos cron y mensajes de terceros.

A medida que se acerca la fecha de despliegue, la comunicación es esencial. Si hay más personas que sepan del cambio en el horizonte, cómo les afecta y cómo deben abordarlo, entonces es más probable que tenga un lanzamiento exitoso. No tengas miedo de comunicar demasiado cada paso del camino, ¡aumenta la probabilidad de reseñas brillantes de todos los involucrados una vez que vayas en vivo!

## Launch

Complete la actualización implementando en las extensiones de producción y actualización. Asegúrese de probar los flujos de ruta críticos con pedidos simulados. Consulte estos [prácticas recomendadas](../prepare/best-practices.md) para obtener algunas sugerencias sobre el lanzamiento con problemas mínimos.

Siga su plan de comunicación y asegúrese de que todas las partes interesadas sean conscientes de la actualización y estén completamente entrenadas para apoyarla.

Por último, póngase en contacto con su equipo para determinar las lecciones aprendidas y los inconvenientes. Esta retrospectiva le ayuda a mejorar el proceso la próxima vez.

## Posterior al lanzamiento

Una vez que el sitio se inicie, asegúrese de comprobar los datos de análisis, la consola de búsqueda de Google y otros recursos para asegurarse de que no haya problemas inesperados y de que todo funcione según lo esperado.

Siempre es una buena idea vigilar el rendimiento mediante herramientas de monitorización bien diseñadas. Existen muchas herramientas y medios para monitorear el rendimiento del sitio, por lo que asegúrese de elegir uno que se empareje bien con su organización. Recomendamos que los clientes de Adobe Commerce que utilizan nuestro sistema de administración de infraestructuras de nube aprovechen servicios como [Nueva reliquia](https://devdocs.magento.com/cloud/project/new-relic.html) para supervisar el rendimiento del sitio.
