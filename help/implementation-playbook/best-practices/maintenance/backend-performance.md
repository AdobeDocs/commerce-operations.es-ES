---
title: Optimización del rendimiento back-end
description: Obtenga información sobre cómo optimizar el rendimiento back-end de los sitios de Adobe Commerce.
badge: label="Contribuido por objectsource" type="Informative" url="https://objectsource.co.uk/" tooltip="objectsource"
role: Admin, User, Developer
feature: Best Practices
exl-id: 18bc97a0-3d34-4d48-a3e2-84af2da7d0d3
source-git-commit: d884d434e696a911de626dc76983468556cf451f
workflow-type: tm+mt
source-wordcount: '977'
ht-degree: 0%

---

# Prácticas recomendadas para optimizar el rendimiento del servidor

En este tema se describen las prácticas recomendadas para investigar y optimizar el rendimiento back-end de los sitios de Adobe Commerce, centrándose en la optimización y las pruebas de bases de datos. Los desarrolladores pueden utilizar esta información para investigar el contexto único de cada proyecto de Commerce e identificar oportunidades para optimizar la configuración back-end y las operaciones para mejorar el rendimiento del sitio.

>[!NOTE]
>
>Las recomendaciones y los ejemplos se inspiran en los procesos que siguen los orígenes de objetos en las interacciones de clientes reales para ofrecer sitios Adobe Commerce de alto rendimiento a escala.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Optimización de la base de datos para un rendimiento mejorado

La optimización de bases de datos es una forma segura de mejorar la experiencia del usuario y aumentar las ventas. Al optimizar la base de datos, la columna vertebral de un sitio de Commerce, puede evitar el rendimiento lento del sitio web y eliminar los tiempos de carga prolongados que crean fricción para los clientes.

### Pruebas de estrés

Los períodos de alto tráfico, como el Black Friday, exigen que los sitios de Commerce gestionen volúmenes de tráfico masivos. Como preparación para estos eventos, las pruebas de esfuerzo son esenciales para comprender cómo funciona un sitio bajo aumentos exponenciales de carga.

Una herramienta que puede usar para las pruebas de esfuerzo es GTmetrix. Medir la preparación del sitio para la carga aumenta configurando GTmetrix para replicar y multiplicar el comportamiento y las acciones normales de los visitantes. A continuación, ejecute pruebas para identificar y resolver los problemas que puedan afectar al rendimiento y a la disponibilidad del sitio durante los principales eventos de compra.

Obtenga más información sobre la preparación de proyectos de Commerce para períodos de alto tráfico:

- [Preparación para las vacaciones](https://experienceleague.adobe.com/docs/events/commerce-intelligence-webinar-recordings/2021/holiday-readiness.html)
- [Análisis de compras de vacaciones](https://experienceleague.adobe.com/docs/commerce-business-intelligence/mbi/analyze/performance/holiday-season-perf.html)
- [Aumento de capacidad de sobretensión](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/2021-holiday-surge-capacity-requests-for-magento-commerce-cloud.html)

### Prueba de carga

También puede utilizar GTmetrix o una herramienta similar para cargar proyectos de Commerce de prueba. Como precursor de las pruebas de esfuerzo, las pruebas de carga son una práctica esencial para sitios de alto tráfico y a gran escala. Evite las interrupciones inesperadas del sitio, los clientes frustrados y las pérdidas financieras anticipando y mitigando los problemas que afectan el rendimiento del sitio bajo cargas máximas.

Utilice GTmetrix para simular el tráfico pesado y analizar el rendimiento del sitio para obtener información clara sobre la capacidad del sitio. Este análisis ayuda a identificar y abordar los cuellos de botella e identificar las oportunidades de optimización, lo que garantiza que los sitios de Commerce puedan funcionar de forma eficaz con una mayor carga.

Obtenga más información sobre la prueba de proyectos de Adobe Commerce:

- [Guía de pruebas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html) (infraestructura en la nube)
- [Pruebas de aplicación](https://developer.adobe.com/commerce/testing/guide/)

### Identificar y resolver problemas de rendimiento

Aborde los problemas de rendimiento utilizando varias herramientas como New Relic y Observación para Adobe Commerce para detectar cuellos de botella y optimizar los sitios de Commerce de forma eficaz. [New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html) se incluye con Adobe Commerce en la infraestructura en la nube, y [Observación para Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md) se incluye tanto para implementaciones locales como en la nube.

Utilice estas herramientas para analizar el rendimiento del sitio e identificar los problemas de rendimiento relacionados con lo siguiente:

- Funciones de uso intensivo de CPU
- Configuración de administración de caché para consultas y operaciones back-end
- Llamadas de API de terceros
- Programación de Cron

Por ejemplo, puede examinar minuciosamente las transacciones centrándose en las páginas de categorías y detalles del producto. Identifique los procesos que requieren mucho tiempo y que se pueden optimizar para mejorar el rendimiento. En una participación del cliente, el origen de objetos observó un problema de rendimiento en una página de detalles del producto y encontró una llamada de API que consumía el 3,5 % del tiempo de rendimiento. En función de este resultado, examinaron la jerarquía de ejecución del código para localizar y corregir el problema que causaba el cuello de botella.

Más información sobre la administración del rendimiento del sitio:

- [Supervisión del rendimiento](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/performance.html) (infraestructura en la nube)
- [Prácticas recomendadas de configuración](/help/performance/configuration.md)
- [Observación para Adobe Commerce](/help/tools/observation-for-adobe-commerce/intro.md)

### Optimizar el rendimiento de MySQL

Abordar los problemas de rendimiento de MySQL mediante la implementación de clústeres de bases de datos y la optimización de consultas es un enfoque eficaz para mejorar el rendimiento antes y durante períodos de alto tráfico como el Black Friday.

#### Implementar clústeres de base de datos

Los sitios web de alto tráfico a menudo se enfrentan a cuellos de botella en la base de datos, principalmente causados por la dependencia en un solo servidor MySQL. Puede solucionar estos cuellos de botella implementando la agrupación en clúster de bases de datos, una arquitectura distribuida que mejora el rendimiento y garantiza una alta disponibilidad.

La agrupación en clúster de bases de datos minimiza el impacto de los problemas relacionados con las bases de datos durante los períodos de tráfico máximo, ya que permite que varios nodos web se conecten a varios servidores MySQL. Utilice herramientas como Cluster de Galera para configurar clústeres de base de datos para sitios de Commerce. El clúster Galera se incluye con [proyectos Adobe Commerce implementados en la infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture).

#### Optimización de consultas MySQL

Normalmente, la infraestructura de la mayoría de los sitios de Adobe Commerce consiste en varios nodos web conectados a un único servidor MySQL.

En esta configuración, cada nodo web front-end se conecta al clúster de Galera, que permite varios servidores MySQL. El aumento del número de nodos web front-end puede mejorar el rendimiento de la aplicación, pero el único servidor MySQL sigue siendo un cuello de botella.

Para optimizar el rendimiento del servidor MySQL y minimizar los cuellos de botella, es esencial identificar y reducir las consultas innecesarias. Por ejemplo, si envía 1000 consultas por segundo pero solo son necesarias 200, optimizar y reducir el recuento de consultas puede mejorar significativamente el rendimiento.

Obtenga más información sobre la configuración y optimización de MySQL:

- [Prácticas recomendadas para la configuración de bases de datos](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
- [Replicación lenta para la replicación de Galera DB](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/galera-db-slow-replication.html)
- [Directrices generales de MySQL](/help/installation/prerequisites/database/mysql.md)
- [Almacenamiento en caché de consultas MySQL](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/mysql-query-cache.html)

## Administrar los trabajos de cron de forma eficaz: rendimiento y tiempo

Los trabajos de Cron desempeñan un papel vital en las tareas en segundo plano del sitio de procesamiento, como la generación de informes y la indexación de productos. Sin embargo, la optimización del trabajo de cron requiere considerar cuidadosamente su impacto en el rendimiento general. Los desarrolladores deben evaluar la frecuencia de programación y determinar el tiempo óptimo en función de requisitos específicos.

Equilibrando el rendimiento y la comodidad, a menudo es aconsejable programar trabajos cron durante períodos de poco tráfico. Sin embargo, tratar con clientes en diferentes zonas horarias puede presentar desafíos, lo que exige un enfoque reflexivo para garantizar una experiencia armoniosa en múltiples regiones geográficas.

Si usted es el responsable de optimizar el rendimiento y el tiempo de cron, revise la configuración actual de cron desde el Administrador de Commerce, y aprenda a configurar los trabajos de cron para proyectos de Commerce.

Además, puede utilizar Observación para Adobe Commerce para ver indicadores de rendimiento relacionados con Cron. Esta herramienta combina datos de registro de varias fuentes para ayudarle a administrar mejor el rendimiento del sitio de Adobe Commerce y diagnosticar problemas.

Obtenga más información acerca de la implementación de Adobe Commerce cron:

- [Cron (tareas programadas)](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) en la _Guía del usuario de Commerce Admin Systems_
- [Configuración de la aplicación - propiedad de crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (infraestructura en la nube)
- [Configurar y ejecutar crons](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html) (local)
- [Observación para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html) (vea las fichas [!UICONTROL Cron] y [!UICONTROL MySQL]).
