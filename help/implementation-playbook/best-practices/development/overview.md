---
title: Fase de desarrollo de implementación
description: Obtenga información acerca de las prácticas recomendadas de implementación para la fase de desarrollo de proyectos de Adobe Commerce.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: ce386611834c4199e34b5d95ce76254957821f46
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 2%

---


# Fase de desarrollo

La fase de desarrollo incluye las siguientes actividades:

- Configuración del entorno local y de ensayo
- Planificación de sprint
- Ejecución de tickets
- Resolución de problemas
- Revisión, combinación y prueba del código
- Revisión de Sprint
- Cierre de sesión del cliente

>[!TIP]
>
>Consulte [prácticas recomendadas generales](general.md) para obtener recomendaciones de alto nivel sobre la gestión general del proceso de desarrollo.

Las secciones siguientes incluyen información sobre las prácticas recomendadas para la fase de desarrollo.

## Administración de código

| Práctica recomendada | Descripción |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [Revisión de código](code-review.md) | Proceso de validación recomendado para garantizar que la funcionalidad implementada cumpla los requisitos |
| [Compositor frente a Git](code-management.md) | Determine cómo distribuir código personalizado teniendo en cuenta la administración de versiones, la complejidad del código y la administración de dependencias |
| [Estrategia de ramas](git-branching.md) | Administrar código fuente en repositorios Git |
| [Ejemplos de GRA](../../architecture/global-reference/examples.md) | Comprender los métodos comunes para organizar una [arquitectura de referencia global](../../architecture/global-reference/overview.md) código base |

## Base de datos

| Práctica recomendada | Descripción |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [Modificación de tabla](modifying-core-and-third-party-tables.md) | Determine cómo y cuándo modificar las tablas de bases de datos de Adobe Commerce y de terceros |

## Optimización de archivos

| Práctica recomendada | Descripción |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [Cambio de tamaño de imagen de catálogo](catalog-image-resizing.md) | Proporciona instrucciones sobre el cambio de tamaño de las imágenes antes de que una tienda entre en producción para garantizar un rendimiento óptimo |
| [CSS y JS](optimize-css-js-files.md) | Combine y minifique archivos de hoja de estilos en cascada (CSS) y JavaScript (JS) desde el administrador o la línea de comandos |
| [Imágenes](image-optimization.md) | Optimizar imágenes y utilizar Fastly para optimizar el tiempo de respuesta |

## Desarrollo de front-end

| Práctica recomendada | Descripción |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [Desarrollo del tema](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Describe los patrones de desarrollo para garantizar la compatibilidad entre el tema, las versiones futuras de Adobe Commerce y las extensiones personalizadas |

## Desarrollo de PHP

| Práctica recomendada | Descripción |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [Control de excepciones](exception-handling.md) | Describe los métodos recomendados para registrar excepciones |
| [Extensiones](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Describe los patrones de desarrollo para garantizar la compatibilidad entre su extensión, las versiones futuras de Adobe Commerce y otras extensiones personalizadas |
| [Bloques de contenido privado](private-content-block-configuration.md) | Configurar bloques de contenido privado para optimizar el rendimiento de la tienda |
| [Modificar código PHP principal y de terceros](modifying-core-and-third-party-code.md) | Modifique la funcionalidad, el resultado o la entrada de cualquier código que no haya creado o que no controle directamente |

## Plataforma y servicios

| Práctica recomendada | Descripción |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [Compilaciones e implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html){target="_blank"} | Describe las prácticas recomendadas para las fases de compilación e implementación de Adobe Commerce en proyectos de infraestructura en la nube |
| Depuración | Depurar el marco de trabajo de Adobe Commerce de forma sistemática y eficaz |
| [Implementación de contenido estático](static-content-deployment.md) | Evite los problemas con el contenido estático que no aparezca en la tienda |
| [Solución de problemas](troubleshooting.md) | Solución de problemas comunes de implementación de Adobe Commerce |
