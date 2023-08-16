---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---
# Documentación técnica de Adobe Commerce

Agradecemos las contribuciones de nuestra comunidad, así como de los empleados de Adobe ajenos a los equipos de documentación.

## Código de conducta de código abierto de Adobe

Este proyecto ha adoptado el [Código de conducta de código abierto de Adobe](code-of-conduct.md) o el [Código de conducta de la Fundación .NET](https://dotnetfoundation.org/code-of-conduct). Para obtener más información, consulte el artículo [Colaboración](contributing.md).

## Acerca de sus contribuciones al contenido del Adobe

Consulte la [Guía del colaborador de Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

La forma en que contribuya depende de quién sea y del tipo de cambios con los que desee contribuir:

### Cambios menores

Si está aportando actualizaciones menores porque quiere hacerlo, visite el artículo y haga clic en **Editar** en el artículo que va al origen de GitHub del artículo. A continuación, utilice la interfaz de usuario de GitHub para realizar las actualizaciones. Consulte la información general [Guía del colaborador de Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) para obtener más información.

Las correcciones o aclaraciones menores que envíe para la documentación y los ejemplos de código en este repositorio están sujetos a las condiciones de uso del Adobe.

### Cambios importantes o nuevos artículos de los miembros de la comunidad

Si forma parte de la comunidad de Adobe y desea crear un artículo nuevo o enviar cambios importantes, utilice la pestaña Problemas del repositorio Git para enviar un problema e iniciar una conversación con el equipo de documentación. Una vez que haya aceptado un plan, deberá trabajar con un empleado para ayudar a incorporar ese nuevo contenido a través de una combinación de trabajo en los repositorios públicos y privados.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Cambios importantes de los empleados del Adobe

Si es redactor técnico, administrador de programa o desarrollador del equipo de producto para una solución de Adobe Experience Cloud y su trabajo consiste en colaborar en artículos técnicos o en crearlos, debe utilizar el repositorio privado que hay en `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Herramientas y configuración

Los colaboradores de la comunidad pueden utilizar la interfaz de usuario de GitHub para la edición básica o bifurcar el repositorio para realizar contribuciones importantes.

Consulte la [Guía del colaborador de Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) para obtener más información.

## Utilizar Markdown para dar formato al tema

Todos los artículos de este repositorio utilizan GitHub Flavored Markdown. Si no está familiarizado con el uso de markdown, consulte:

* [Fundamentos de marcado](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Hoja de trucos de markdown imprimible](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Plantillas

El `_jekyll` El directorio contiene temas con plantillas y recursos necesarios.
Las plantillas que utilizan el lenguaje de plantilla Liquid residen en la variable `_jekyll/templated` como archivos de HTML.
El `_jekyll/_data` contiene archivos con los datos que se utilizan para procesar las plantillas.

Para procesar todas las plantillas:

1. Vaya a `_jekyll` directorio.

   cd _jekyll

1. Ejecute el script de renderización.

```
_scripts/render
```

> **NOTA:** Debe ejecutar el script desde el `_jekyll` directorio.
> **NOTA:** Debe tener Ruby instalado para ejecutar este script.

El script ejecuta el procesamiento y escribe las plantillas procesadas en `help/_includes/templated` directorio.

Consulte la documentación de Jekyll para obtener más información sobre [Archivos de datos](https://jekyllrb.com/docs/datafiles), [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/)y otras funciones de.
