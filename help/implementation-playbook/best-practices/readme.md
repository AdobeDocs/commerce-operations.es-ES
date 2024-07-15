---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# Prácticas recomendadas: Flujo de trabajo de creación de contenido

En este documento se describe el flujo de trabajo del usuario para solicitar cambios o adiciones al contenido de *[Prácticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* en el *Libro de estrategias de implementación de Adobe Commerce*.

## ¿Quién puede crear una solicitud de?

El Adobe acepta solicitudes de partes interesadas internas y externas, incluidas, entre otras, las personas de los siguientes grupos:

- Socios de Adobe
- Adobe CTAG (Customer Technical Advisory Group), Asistencia al cliente, Éxito del cliente, Equipos de ingeniería

## ¿Cómo se crea una solicitud?

**Interesados internos** pueden enviar solicitudes abriendo un problema con Jira en el proyecto COMDOX. **Las partes interesadas externas** pueden enviar solicitudes abriendo un [problema de GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) en este repositorio.

Puede enviar los siguientes tipos de solicitudes:

- Ideas para contenido nuevo
- Actualizaciones de contenido que ya se ha publicado
- Publish: nuevo contenido proporcionado por la parte interesada o la comunidad

## ¿Cuál es el proceso general?


**Crear un ticket Jira o un problema**—Las partes interesadas internas crean un ticket Jira en el proyecto COMDOX. Las partes interesadas externas envían un problema de GitHub. Incluya detalles completos en el [problema de Jira o GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) para ayudar al equipo a comprender el contexto y priorizar la solicitud.

**El equipo del proyecto de Adobe evalúa y da prioridad a la solicitud**—El equipo supervisa con regularidad las solicitudes para determinar la prioridad y evaluar los cambios solicitados para su inclusión en las Prácticas recomendadas del libro de estrategias de implementación. Por ejemplo, el equipo de podría determinar que, en lugar de crear un nuevo tema de prácticas recomendadas, el contenido solicitado debería agregarse a la documentación del producto existente en Experience League o en el sitio de Adobe Developer.

Si no se proporciona suficiente información en una solicitud, el equipo solicita información adicional al solicitante. Si el solicitante no responde en un plazo de 14 días, el equipo cierra la solicitud.

**Crear o actualizar contenido**: el trabajo de creación de contenido se ha completado siguiendo el proceso documentado en [Guía del colaborador de Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Según la solicitud, el trabajo puede incluir la conversión del contenido nuevo a Markdown, la creación de un tema o la actualización de un tema existente.

**Revisión, aprobación y publicación de contenido**: el contenido se revisa y edita durante la creación o actualización del tema mediante [solicitudes de extracción de GitHub](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Todo el contenido debe pasar por una revisión editorial. La revisión técnica es opcional y depende del contenido. Si no se requiere una revisión técnica, el proceso continúa con una revisión editorial solamente. Este proceso puede tardar varias iteraciones hasta que se apruebe el contenido.

Una vez aprobado un artículo, la solicitud de extracción se puede combinar con la rama de producción. La combinación debe realizarla el autor. Después de combinar un tema, se puede publicar en producción inmediatamente mediante un proceso manual o automáticamente la próxima vez que se ejecute el trabajo de publicación. Los trabajos de publicación suelen ejecutarse cada dos horas.

El Adobe **Nueva notificación de contenido** proporcionará una sección *Novedades* en el tema de la [descripción general de las prácticas recomendadas](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) para mantener informados a los usuarios sobre los temas publicados recientemente o actualizados. El Adobe también promocionará contenido de prácticas recomendadas nuevas mediante los canales existentes, como el marketing y las comunicaciones internas.

## Registro de pendientes y Panel Kanban

Para evitar duplicaciones, las solicitudes que se hayan creado y priorizado se podrán ver en el registro de pendientes Jira del proyecto COMDOX y en el [proyecto de problemas de GitHub](https://github.com/orgs/AdobeDocs/projects/6/views/1). Se alienta a las partes interesadas internas a que participen en el sistema de votación de Jira para atender las solicitudes que consideren necesarias o pertinentes. La votación también ayuda al equipo del proyecto de Prácticas recomendadas a comprender el tipo de contenido que las partes interesadas esperan y valoran. Las solicitudes que están pendientes de priorización y revisión se muestran en el registro de pendientes hasta que se mueven a las rutas activas del panel Kanban.

Los usuarios internos pueden acceder al panel Kanban para ver (o monitorizar) en qué contenido se está trabajando y el progreso realizado. En este tablero solo se mostrarán las solicitudes activas.
