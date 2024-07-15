---
title: Prácticas recomendadas de ramificación Git
description: Obtenga información sobre las distintas estrategias de ramificación para la administración del código fuente.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Prácticas recomendadas de ramificación Git

El código Source pasa por varias fases de estabilidad durante el proceso de desarrollo:

- Desarrollo activo
- Integración de código inicial
- Integración de código para el control de calidad (QA)
- Integración de código para la prueba de aceptación final del usuario (UAT)
- Integración de código final para versiones de producción

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Administración de sucursales

Cada fase de desarrollo debe tener una rama correspondiente en Git para rastrear los cambios de código y facilitar el proceso de implementación:

- **Rama de tareas**: donde los desarrolladores confirman sus cambios de código individuales al implementar tareas específicas, como características y correcciones de errores.
- **Rama de desarrollo**: donde varios desarrolladores combinan cambios de sus ramas de tareas individuales en una sola rama de desarrollo para realizar pruebas de integración automatizadas. Esta rama se implementa en un entorno de desarrollo.
- **Rama de control de calidad**: donde los desarrolladores combinan los cambios una vez completado el desarrollo y el código ha pasado todas las pruebas de integración automatizada y la revisión de código. Esta rama se implementa en el entorno de control de calidad para realizar pruebas de control de calidad manuales.
- **Rama estable/UAT**: donde el código se combina después de pasar la prueba de control de calidad manual. Esta rama se implementa en un entorno UAT para las pruebas de aceptación de usuarios.
- **Rama de producción/liberación**: donde el código se combina después de pasar UAT. Esta rama se implementa en producción para una versión.

>[!TIP]
>
>Adobe Commerce en proyectos de infraestructura en la nube contiene ramas específicas que corresponden a entornos diferentes. Consulte [Flujo de trabajo del proyecto profesional](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) y [Flujo de trabajo del proyecto inicial](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) en la _Guía de Cloud_.

## Estrategias de rama

Existen varias estrategias de ramificación que puede utilizar. Elija la estrategia que mejor se adapte a su equipo de desarrollo y a la complejidad de su proyecto.

Para obtener más información, consulte los siguientes recursos externos:

- [Flujos de trabajo de ramificación](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Flujos de trabajo distribuidos](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Patrones para administrar ramas de código fuente](https://martinfowler.com/articles/branching-patterns.html)
- [Un modelo de bifurcación Git correcto](https://nvie.com/posts/a-successful-git-branching-model/)
- [Flujo de GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Flujo de GitLab](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
