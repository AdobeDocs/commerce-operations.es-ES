---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# Prácticas recomendadas: Flujo de trabajo de creación de contenido

Este documento describe el flujo de trabajo del usuario para solicitar cambios o adiciones al *[Prácticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html)* contenido en la variable *Manual de implementación de Adobe Commerce*.

## ¿Quién puede crear una solicitud?

Adobe acepta solicitudes de partes interesadas internas y externas, incluidas, entre otras, las personas de los siguientes grupos:

- Socios de Adobe
- Adobe CTAG (Grupo de Asesoramiento Técnico del Cliente), Asistencia al Cliente, Éxito del Cliente, Equipos de Ingeniería

## ¿Cómo se crea una solicitud?

**Interesados internos** puede enviar solicitudes abriendo un problema de Jira en el proyecto COMDOX. **Partes interesadas externas** puede enviar solicitudes abriendo una [Problema de GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) en este repositorio.

Puede enviar los siguientes tipos de solicitudes:

- Ideas para contenido nuevo
- Actualizaciones de contenido que ya se han publicado
- Publicar nuevo contenido proporcionado por el interesado o la comunidad

## ¿Cuál es el proceso general?


**Crear un ticket o problema de Jira**: los interesados internos crean un ticket de Jira en el proyecto COMDOX. Las partes interesadas externas envían un problema de GitHub. Incluir detalles completos en el Jira o [Problema de GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) para ayudar al equipo a comprender el contexto y priorizar la solicitud.

**El equipo del proyecto de Adobe evalúa y prioriza la solicitud**: el equipo supervisa regularmente las solicitudes para determinar la prioridad y evaluar los cambios solicitados para incluirlos en las prácticas recomendadas del libro de implementación. Por ejemplo, el equipo podría determinar que en lugar de crear un nuevo tema de Prácticas recomendadas, el contenido solicitado debe agregarse a la documentación de producto existente en el Experience League o en el sitio de Adobe Developer.

Si no se proporciona suficiente información en una solicitud, el equipo solicita información adicional al solicitante. Si el solicitante no responde en un plazo de 14 días, el equipo cerrará la solicitud.

**Crear o actualizar contenido**-El trabajo de creación de contenido se completa siguiendo el proceso documentado en el [Guía del colaborador de Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). En función de la solicitud, el trabajo puede incluir la conversión de nuevo contenido a markdown, la creación de un tema o la actualización de un tema existente.

**Revisión, aprobación y publicación de contenido**-El contenido se revisa y edita durante la creación o actualización de temas mediante [Solicitudes de extracción de GitHub](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Todo el contenido debe pasar por una revisión editorial. La revisión técnica es opcional y depende del contenido. Si no es necesario un examen técnico, el proceso continúa con una revisión editorial solamente. Este proceso puede tardar varias iteraciones hasta que se apruebe el contenido.

Una vez aprobado un artículo, la solicitud de extracción se puede fusionar con la rama de producción. La fusión debe realizarla el autor. Una vez combinado un tema, puede publicarse en producción inmediatamente mediante un proceso manual o automáticamente la próxima vez que se ejecute el trabajo de publicación. Los trabajos de publicación suelen ejecutarse cada dos horas.

**Notificación de contenido nuevo**-El Adobe proporcionará un *Novedades* en la sección [Información general sobre prácticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) para mantener informados a los usuarios sobre los temas publicados o actualizados recientemente. Adobe también promocionará el nuevo contenido de las prácticas recomendadas utilizando los canales existentes, como marketing y comunicaciones internas.

## Tablero Kanban y atrasos

Para evitar la duplicación, las solicitudes que se hayan creado y priorizado serán visibles en el atraso Jira del proyecto COMDOX y [Proyecto de problemas de GitHub](https://github.com/orgs/AdobeDocs/projects/6/views/1). Se alienta a los interesados internos a que colaboren con el sistema de votación de Jira para apoyar las solicitudes que consideren necesarias o pertinentes. La votación también ayuda al equipo del proyecto Prácticas recomendadas a comprender el tipo de contenido que los interesados esperan y valoran. Las solicitudes pendientes de priorización y revisión se muestran en el atraso hasta que se mueven a las rutas activas en la junta de Kanban.

Los usuarios internos pueden acceder al tablero Kanban para ver (y/o monitorear) en qué contenido se está trabajando y el progreso realizado. En este tablero solo se mostrarán las solicitudes activas.
