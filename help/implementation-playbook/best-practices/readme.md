---
source-git-commit: aaf174e5d895ebc60d4937b0214e23a559532942
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---
# Prácticas recomendadas: Flujo de trabajo de creación de contenido

El propósito de este documento es detallar el flujo de trabajo que los usuarios deben seguir para solicitar el contenido de las prácticas recomendadas.

## ¿Quién puede crear una solicitud?

Hay dos grupos de partes interesadas que pueden presentar una solicitud, que incluyen, entre otros:

- Externo: Socios
- Interno: CTAG (grupo de asesoramiento técnico del cliente), Asistencia al cliente, Éxito del cliente, equipos de ingeniería

## ¿Cómo se crea una solicitud?

Las partes interesadas internas deben realizar solicitudes abriendo un problema de Jira en el proyecto COMDOX. Las partes interesadas externas deben realizar solicitudes abriendo un problema de GitHub en este repositorio. Las partes interesadas pueden realizar las siguientes solicitudes:

- Solicitar nuevo contenido para añadir
- Solicitar ediciones para contenido que ya se ha publicado
- Compartir su propio contenido para publicarlo

## ¿Cuál es el proceso general?

Las partes interesadas internas deben abrir un ticket de Jira en el proyecto de documentación comercial (COMDOX) y proporcionar detalles completos, incluida la finalización de una plantilla. Estos detalles ayudan al equipo a priorizar las solicitudes de contenido.

El equipo supervisa regularmente las solicitudes en el registro acumulado para determinar la prioridad y si el Manual de implementación es el mejor lugar para la solicitud. El equipo puede determinar que, en lugar de crear un tema nuevo, el contenido solicitado debe agregarse a la documentación de producto existente en el Experience League o en el sitio de Adobe Developer.

Si no hay suficiente información proporcionada en una solicitud, el equipo pedirá al solicitante que complete todos los campos correspondientes. Si el solicitante no responde dentro de X días, el equipo cierra la solicitud.
Una vez que el equipo valida y prioriza la solicitud, el siguiente paso es crear el tema. Esto puede significar adaptar el contenido al formato .md o crear el artículo desde cero.

El contenido se revisa y edita durante la creación del tema. El proceso de revisión se produce mediante solicitudes de extracción de GitHub. Todo el contenido debe pasar por una revisión editorial. La revisión técnica es opcional y depende del contenido. Si no es necesario un examen técnico, el proceso continúa con una revisión editorial solamente. Este proceso puede tardar varias iteraciones hasta que se apruebe el contenido.

Después de aprobar un artículo, el siguiente paso es combinarlo con la rama de producción. La fusión debe realizarla el autor. El tema se puede publicar inmediatamente o esperar a que se ejecute el siguiente trabajo de publicación, que publica todos los temas aprobados y fusionados.

Mostraremos una nueva sección en la página de inicio de Prácticas recomendadas en Experience League para ayudar a los usuarios a mantenerse actualizados con los temas publicados recientemente, de modo que no necesitan navegar por diferentes páginas y portales para encontrar información relevante de interés. También promoveremos contenido en canales existentes, como marketing y comunicaciones internas.

## Tablero Kanban y atrasos

Para evitar la duplicación, las solicitudes que se hayan creado y priorizado deben ser visibles en el atraso. Se anima a los usuarios a que colaboren con el sistema de votación en Jira para apoyar las solicitudes que consideren necesarias o pertinentes. Esto también será un buen indicador para el equipo de qué tipo de contenido se espera de los interesados. Las solicitudes pendientes de priorización y revisión se mostrarán en el atraso hasta que se trasladen a los carriles activos de la junta de Kanban.

Los usuarios internos pueden acceder al tablero Kanban para ver (y/o monitorear) en qué contenido se está trabajando y el progreso realizado. En este tablero solo se mostrarán las solicitudes activas.
