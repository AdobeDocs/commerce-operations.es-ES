---
title: Prácticas recomendadas de la lista de comprobación de actualización
description: Aprenda a crear y utilizar una lista de comprobación de actualización para planificar su estrategia de actualización de Adobe Commerce y Magento Open Source.
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 644970b350c7591896f7c00d4c94661c76495c73
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Prácticas recomendadas de la lista de comprobación de actualización

Utilice esta lista de comprobación durante las conversaciones anuales y trimestrales con su equipo de comercio electrónico. Muchas empresas trabajan con presupuestos anuales y hojas de ruta. Es imperativo, durante estas discusiones anuales, que hable de la estrategia de salud, dirección y actualización de su plataforma para el año, junto con cómo encaja en los objetivos generales y los KPI del negocio. Durante las conversaciones trimestrales, asegúrese de que el plan anual que ha creado sigue estando alineado con su situación actual o pivotado si no lo está. El objetivo de esta lista de comprobación del plan de actualización es ayudarlo a planificar y programar actualizaciones de Adobe Commerce para garantizar un proceso de actualización exitoso durante el año. Esta lista de comprobación debe ser utilizada por las siguientes audiencias para la planificación anual y la revisión trimestral:

- Director / Gestionar TI
- Administrador de comercio electrónico
- Socio/Consultor de soluciones

>[!NOTE]
>
>Para obtener una descripción detallada de los pasos técnicos para actualizar correctamente, consulte [Requisitos previos de actualización completos](../../../upgrade/prepare/prerequisites.md) en nuestra documentación de usuario.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Objetivos

▢ Revise los KPI actuales y ajuste según sea necesario.

## Extensiones y personalizaciones

▢ Revise todas las extensiones y personalizaciones actuales y asegúrese de que siguen siendo necesarias en función de los requisitos del negocio.

▢ la opción de reemplazar cualquier extensión que no tenga un buen registro de seguimiento para mantenerse al día con las versiones de Adobe Commerce.

## Equipo

▢ asegúrese de que dispone del equipo adecuado con las certificaciones y los conjuntos de habilidades de Adobe Commerce adecuados.

## Presupuesto y temporización

▢ usar Adobe Commerce [programación de versiones](../../../release/schedule.md) para planificar la próxima actualización y prepararse con antelación.

▢ Analice qué versión cree que adoptará (completa o solo de seguridad) según las necesidades previstas.

▢ Guarde un presupuesto y una capacidad de equipo para la actualización.

## Integraciones de terceros

▢ Revise las integraciones de terceros de Adobe Commerce actuales y sus ventanas de mantenimiento para el año, y considere la posibilidad de alinear el trabajo de actualización con su programa de mantenimiento.

## Planificación de ámbito e implementación

▢ Actividades de acceso anticipado

- Los socios participan en [Beta](../../../release/beta-program.md)
- Revisión de notas de la versión beta.

▢ de acuerdo sobre presupuesto, cronología y alcance.

▢ ejecutar el [Herramienta de compatibilidad de actualización](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ considerar el uso de la actualización para abordar los problemas identificados por el [Herramienta de análisis de todo el sitio](../../../tools/site-wide-analysis-tool/intro.md).

▢ Dependencias de documentos y cualquier cambio técnico de pila requerido, como las versiones PHP o Elastic Search.

▢ el equipo del proyecto Recopile con certificaciones de Adobe Commerce.

▢ Crear un plan de comunicación con las partes interesadas.

▢ Planificar período de mantenimiento si se prevé tiempo de inactividad.

▢ Revisar y aprobar la estrategia de ensayo; considere la posibilidad de utilizar Adobe Commerce [marco de pruebas](https://developer.adobe.com/commerce/testing/) o un grupo de automatización de terceros.

▢ Confirme que todas las extensiones y personalizaciones son compatibles.

▢ Revisar y actualizar el manual posterior al lanzamiento; que se utilizará si se descubren problemas durante o después de la actualización.

## Implementación posterior

▢ Supervisar el sitio para ver los problemas: rendimiento, procesamiento de pedidos, análisis y otros.

▢ realizar una Adobe Commerce [análisis de seguridad](https://account.magento.com/scanner/dashboard/) u otros análisis de terceros y revisión de posibles vulnerabilidades de seguridad.

▢ realizar una retrospectiva con todas las partes interesadas y documentar qué fue bien y qué no y cómo mejorar.

▢ Modifique su plan para la próxima actualización con las lecciones aprendidas.
