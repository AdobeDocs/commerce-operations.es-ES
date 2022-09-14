---
source-git-commit: 5a950079e8b445ef363217c085da92f0991a3a7f
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 5%

---
# Documentación del usuario de Adobe Commerce

Agradecemos las contribuciones de nuestra comunidad, así como de los empleados de Adobe de fuera de los equipos de documentación.

## Código de conducta de código abierto de Adobe

Este proyecto ha adoptado el [Código de conducta de código abierto de Adobe](code-of-conduct.md) o el [Código de conducta de la Fundación .NET](https://dotnetfoundation.org/code-of-conduct). Para obtener más información, consulte el artículo [Colaboración](contributing.md).

## Acerca de sus contribuciones al contenido de Adobe

Consulte la [Guía del colaborador de Adobe Docs](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html).

La forma en que contribuya depende de quién sea y del tipo de cambios que desee aportar:

### Cambios menores

Si aporta actualizaciones menores de la bondad de su corazón, visite el artículo y haga clic en el botón **Editar** vínculo en el artículo que va al origen de GitHub para el artículo. A continuación, utilice la interfaz de usuario de GitHub para realizar sus actualizaciones. Consulte la [Guía del colaborador de Adobe Docs](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html) para obtener más información.

Las correcciones o aclaraciones menores que envíe para la documentación y los ejemplos de código de esta cesión temporal están cubiertas por las condiciones de uso del Adobe.

### Principales cambios o nuevos artículos de los miembros de la comunidad

Si forma parte de la comunidad de Adobe y desea crear un artículo nuevo o enviar cambios importantes, utilice la pestaña Problemas del repositorio de Git para enviar un problema e iniciar una conversación con el equipo de documentación. Una vez que haya aceptado un plan, deberá trabajar con un empleado para ayudar a traer ese nuevo contenido a través de una combinación de trabajo en los repositorios públicos y privados.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Principales cambios de los empleados de Adobe

Si es redactor técnico, administrador de programa o desarrollador del equipo de producto para una solución de Adobe Experience Cloud y su trabajo consiste en contribuir a artículos técnicos o crearlos, debe utilizar el repositorio privado que hay en `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Herramientas y configuración

Los colaboradores de la comunidad pueden usar la interfaz de usuario de GitHub para la edición básica o bifurcar la repo para realizar contribuciones importantes.

Consulte la [Guía del colaborador de Adobe Docs](https://docs.adobe.com/content/help/en/contributor/contributor-guide/introduction.html) para obtener más información.

## Cómo utilizar markdown para dar formato al tema

Todos los artículos de este repositorio utilizan el Markdown con sabor a GitHub. Si no está familiarizado con el uso de markdown, consulte:

* [Conceptos básicos de Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Hoja de referencia de markdown para imprimir](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Etiquetas

En el repositorio público, se asignan etiquetas automatizadas a las solicitudes de extracción para que nos ayuden a administrar el flujo de trabajo de las solicitudes de extracción y para que sepan lo que sucede con la solicitud de extracción:

* **Cambio enviado al autor**: Se ha notificado al autor de la solicitud de extracción pendiente.
* **listo para combinar**: Listo para su revisión por nuestro equipo de revisión de solicitudes de extracción.

## Plantillas

La variable `_jekyll` contiene temas con plantillas y recursos necesarios.
Las plantillas que utilizan el lenguaje de plantilla Líquido residen en la variable `_jekyll` como archivos HTML.
La variable `_jekyll/_data` contiene archivos con los datos que se utilizan para procesar las plantillas.

Para procesar todas las plantillas:

1. Vaya a la `_jekyll` directorio.

   cd_jekyll

1. Ejecute el script de renderización.

```
_scripts/render
```

> **NOTA:** Debe ejecutar la secuencia de comandos desde el `_jekyll` directorio.
> **NOTA:** Debe tener Ruby instalado para ejecutar este script.

La secuencia de comandos ejecuta la renderización y escribe los archivos procesados en la variable `_jekyll/_rendered` como archivos HTML y los copia en el `help/_includes` como `.md` archivos.


Consulte la documentación de Jekyll para obtener más información sobre [Archivos de datos](https://jekyllrb.com/docs/datafiles, [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/), y otras funciones.
