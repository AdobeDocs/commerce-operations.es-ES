---
title: Metodología de implementación del proyecto
description: Familiarícese con el funcionamiento de la entrega de software de Adobe Commerce.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
feature: Build, Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Metodología de ejecución del proyecto

Ahora que tiene una mejor idea de las herramientas implicadas, vamos a desglosar nuestros procesos de entrega y prueba.

## Integración continua (CI)

Los trabajos de integración continua realizan automáticamente las siguientes acciones:

- Genere el código fuente para comprobar los errores de compilación.
- Ejecutar pruebas cuando se cree o actualice una solicitud de extracción. Actualmente, se ejecutan pruebas unitarias de PHP.

El trabajo publica su estado de ejecución en la solicitud de extracción. Los desarrolladores pueden ver los detalles de la ejecución del trabajo para que puedan corregir o mejorar el código existente.

## Entrega continua (CD)

Entrega continua (CD) implementa inmediatamente el código fuente en el servidor después de que todas las pruebas se hayan realizado correctamente. Los desarrolladores pueden comprobar sus funciones rápidamente y luego asignar la tarea al equipo de control de calidad para que la revise.

A medida que la compilación se ejecuta en el sistema de compilación, no solo minimiza el tiempo de inactividad de la implementación, sino que también reduce la carga en el servidor. Como resultado, las actividades de control de calidad, que se producen en el servidor, se ven menos afectadas.

![Infografía de envío continuo](../../assets/playbooks/cicd.svg)

El proceso de CI/CD del diagrama anterior puede describirse brevemente de la siguiente manera:

- Bitbucket aloja el repositorio Git.
- Las imágenes Docker se replican desde las configuraciones de pila de la tecnología de producción.
- Los contenedores Docker se utilizan en todos los entornos de desarrollo y prueba. Otros entornos pueden aprovechar estas configuraciones si es necesario.
- Los desarrolladores realizan una comprobación de la rama de código correspondiente para cada nueva tarea o ticket.
- Para todas las ramas de compromiso, automáticamente:
   - Ejecute un análisis de código estándar.
   - Ejecute una prueba de compilación de código.
   - Ejecute un análisis de código estático (por ejemplo, SonarQube).
- Todas las confirmaciones de análisis que aprueban se combinan con la rama de destino.
- Se inserta una nueva etiqueta lanzada en AWS S3 para el paquete de preparación de la implementación.
- El equipo de ingeniería de implementación activa la nueva implementación.
   - Un trabajo de implementación implementa el nuevo paquete en el entorno de destino.
   - Las actualizaciones de la estructura de la base de datos requieren una pausa para aceptar nuevas solicitudes del cliente.
- El proceso de implementación termina con una notificación por correo electrónico, Slack o equipos, que el servidor envía automáticamente al equipo de ingeniería de implementación.
