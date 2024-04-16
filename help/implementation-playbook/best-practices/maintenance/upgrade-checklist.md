---
title: Prácticas recomendadas de lista de comprobación de actualización
description: Obtenga información sobre cómo crear y utilizar una lista de comprobación de actualización para planificar su estrategia de actualización de Adobe Commerce.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Prácticas recomendadas de lista de comprobación de actualización

Utilice esta lista de comprobación durante sus conversaciones anuales y trimestrales con su equipo de comercio electrónico. Muchas empresas trabajan con presupuestos anuales y hojas de ruta. Es imperativo, durante estas discusiones anuales, que hable sobre la salud, la dirección y la estrategia de actualización de su plataforma para el año, junto con cómo encaja en los objetivos generales y los KPI del negocio. Durante las conversaciones trimestrales, asegúrese de que el plan anual que ha creado sigue estando alineado con su situación actual o pivote si no. El objetivo de esta lista de comprobación del plan de actualización es ayudarle a planificar y programar las actualizaciones de Adobe Commerce para garantizar un proceso de actualización correcto durante el año. Esta lista de comprobación está pensada para que la utilicen las siguientes audiencias para la planificación anual y la revisión trimestral:

- TI de Director/Manager
- Administrador de comercio electrónico
- Socio de soluciones / Consultor

>[!NOTE]
>
>Para obtener una descripción detallada de los pasos técnicos para una actualización correcta, consulte [Completar requisitos previos de actualización](../../../upgrade/prepare/prerequisites.md) en nuestra documentación de usuario.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Metas

▢ Revise los KPI actuales y ajústelos según sea necesario.

## Extensiones y personalizaciones

▢ Revise todas las extensiones y personalizaciones actuales y asegúrese de que siguen siendo necesarias según los requisitos empresariales.

▢ Considere la posibilidad de reemplazar cualquier extensión que no tenga un buen historial de mantenimiento actualizado con versiones de Adobe Commerce.

## Equipo

▢ Asegúrese de que dispone del equipo adecuado con las certificaciones y los conjuntos de aptitudes de Adobe Commerce adecuados.

## Presupuesto y calendario

▢ Uso de Adobe Commerce [programación de versiones](../../../release/schedule.md) para planificar su próxima actualización y prepararse con antelación.

▢ Analice qué versión cree que adoptará (completa o solo de seguridad) en función de las necesidades previstas.

▢ Reserve un presupuesto y capacidad de equipo para la actualización.

## Integraciones de terceros

▢ Revise las integraciones actuales de terceros de Adobe Commerce y sus ventanas de mantenimiento para el año, y considere la posibilidad de alinear el trabajo de actualización con su programa de mantenimiento.

## Ámbito y planificación de la implementación

▢ Actividades de acceso anticipado

- El socio participa en [Beta](../../../release/beta.md)
- Revisión de notas de la versión beta.

▢ Acordar el presupuesto, el calendario y el alcance.

▢ Ejecutar [Actualizar herramienta de compatibilidad](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Considere la posibilidad de utilizar la actualización para abordar los problemas identificados por el [Herramienta de análisis de todo el sitio](../../../tools/site-wide-analysis-tool/intro.md).

▢ Dependencias de documentos y cualquier cambio técnico de pila necesario, como versiones de PHP o Elastic Search.

▢ Reúna al equipo del proyecto con las certificaciones de Adobe Commerce.

▢ Cree un plan de comunicación con las partes interesadas.

▢ Período de mantenimiento del plan si se prevé tiempo de inactividad.

▢ Revise y apruebe la estrategia de prueba; considere la posibilidad de utilizar Adobe Commerce. [marco de prueba](https://developer.adobe.com/commerce/testing/) o un grupo de automatización de terceros.

▢ Confirme que todas las extensiones y personalizaciones son compatibles.

▢ Revise y actualice el manual posterior al inicio; se utilizará si se detectan problemas durante o después de la actualización.

## Después de la implementación

▢ Supervisar el sitio para ver si hay problemas de rendimiento, procesamiento de pedidos, análisis y otros.

▢ una Adobe Commerce [análisis de seguridad](https://account.magento.com/scanner/dashboard/) u otros exploradores de terceros y revisan posibles vulnerabilidades de seguridad.

▢ Realice una retrospectiva con todas las partes interesadas y documente lo que salió bien y lo que no y cómo mejorar.

▢ Modifique su plan para la próxima actualización con las lecciones aprendidas.
