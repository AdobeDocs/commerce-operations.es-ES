---
source-git-commit: a6086afc0a1f099b62014ad61098a5a1dc9d4675
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Documentación técnica de Adobe Commerce

Agradecemos las contribuciones de la comunidad, así como de los empleados de Adobe ajenos a los equipos de documentación.

## Adobe Abrir código de conducta de Source

Este proyecto ha adoptado el [Código de conducta de código abierto de Adobe](code-of-conduct.md) o el [Código de conducta de la Fundación .NET](https://dotnetfoundation.org/code-of-conduct). Para obtener más información, consulte el artículo [Colaboración](contributing.md).

## Acerca de sus contribuciones al contenido del Adobe

Consulte la [Guía del colaborador de Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=es).

La forma en que contribuya depende de quién sea y del tipo de cambios con los que desee contribuir:

### Cambios menores

Si va a contribuir con actualizaciones menores, visite el artículo y haga clic en el área de comentarios que aparece en la parte inferior del artículo, haga clic en **Opciones de comentarios detalladas** y, a continuación, haga clic en **Sugerir una edición** para ir al archivo de código fuente Markdown en GitHub. Utilice la interfaz de usuario de GitHub para realizar las actualizaciones. Para obtener más información, consulte la [guía para colaboradores de Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=es).

Las correcciones o aclaraciones menores que envíe para la documentación y los ejemplos de código en este repositorio están sujetos a las condiciones de uso del Adobe.

### Cambios importantes o nuevos artículos de los miembros de la comunidad

Si forma parte de la comunidad de Adobe y desea crear un artículo nuevo o enviar cambios importantes, utilice la pestaña Problemas del repositorio Git para enviar un problema e iniciar una conversación con el equipo de documentación. Una vez que haya aceptado un plan, deberá trabajar con un empleado para ayudar a incorporar ese nuevo contenido a través de una combinación de trabajo en los repositorios públicos y privados.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Cambios importantes de los empleados del Adobe

Si es redactor técnico, administrador de programa o desarrollador del equipo de producto para una solución de Adobe Experience Cloud y debe contribuir o crear artículos técnicos, debe utilizar el repositorio privado en `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Herramientas y configuración

Los colaboradores de la comunidad pueden utilizar la interfaz de usuario de GitHub para la edición básica o bifurcar el repositorio para realizar contribuciones importantes.

Consulte la [Guía del colaborador de Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=es) para obtener más información.

## Utilizar Markdown para dar formato al tema

Todos los artículos de este repositorio utilizan GitHub Flavored Markdown. Si no está familiarizado con el uso de markdown, consulte:

* [Conceptos básicos de Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Hoja de trucos de markdown imprimible](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Plantillas

Para algunos temas, utilizamos archivos de datos y plantillas para generar contenido publicado. Los casos de uso de este enfoque incluyen:

* Publicación de grandes conjuntos de contenido generado mediante programación
* Proporciona una única fuente fiable para los clientes de varios sistemas que requieren formatos de archivo legibles por máquina, como YAML, para la integración (por ejemplo, Site-Wide Analysis Tool)

Algunos ejemplos de contenido con plantillas son, entre otros, los siguientes:

* [Referencia de herramientas CLI](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [Tablas de disponibilidad de productos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=es)
* [Tablas de requisitos del sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=es)

### Generación de contenido con plantilla

En general, la mayoría de los redactores solo necesitan añadir una versión de lanzamiento a las tablas de disponibilidad del producto y requisitos del sistema. El mantenimiento del resto del contenido con plantillas se automatiza o se administra mediante un miembro del equipo dedicado. Estas instrucciones están destinadas a la mayoría de los escritores.

>**NOTA:**
>
>* La generación de contenido con plantillas requiere trabajar en la línea de comandos de un terminal.
>* Debe tener instalado Ruby para ejecutar el script de procesamiento. Consulte [_jekyll/.ruby-version] (_jekyll/.ruby-version) para obtener la versión requerida.

Consulte lo siguiente para obtener una descripción de la estructura de archivos del contenido con plantillas:

* `_jekyll`: contiene temas con plantillas y recursos necesarios
* `_jekyll/_data`: contiene los formatos de archivo legibles por el equipo utilizados para procesar plantillas
* `_jekyll/templated`: contiene archivos de plantilla basados en HTML que utilizan el lenguaje de plantilla Liquid
* `help/_includes/templated`: contiene la salida generada para el contenido con plantilla en formato de archivo `.md` para que se pueda publicar en temas de Experience League; el script de procesamiento escribe automáticamente la salida generada en este directorio

Para actualizar el contenido con plantillas:

1. En el editor de texto, abra un archivo de datos en el directorio `/jekyll/_data`. Por ejemplo:

   * [Tablas de disponibilidad de productos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=es): `/jekyll/_data/product-availability.yml`
   * [Tablas de requisitos del sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=es): `/jekyll/_data/system-requirements.yml`

1. Utilice la estructura YAML existente para crear entradas.

   Por ejemplo, para agregar una versión de Adobe Commerce a las tablas de disponibilidad del producto, agregue lo siguiente a cada entrada en las secciones `extensions` y `services` del archivo `/jekyll/_data/product-availability.yml` (modifique los números de versión según sea necesario):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Vaya al directorio `_jekyll`.

   ```
   cd _jekyll
   ```

1. Genere contenido con plantilla y escriba el resultado en el directorio `help/_includes/templated`.

   ```
   rake render
   ```

   >**NOTA:** Debe ejecutar el script desde el directorio `_jekyll`. Si es la primera vez que ejecuta el script, debe instalar primero las dependencias de Ruby con el comando `bundle install`.

1. Vuelva al directorio `root`.

   ```
   cd ..
   ```

1. Compruebe que se hayan modificado los `help/_includes/templated` archivos esperados.

   ```
   git status
   ```

   Debería ver un resultado similar al siguiente:

   ```
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Presione los cambios.

   ```
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Consulte la documentación de Jekyll para obtener más información sobre [Archivos de datos](https://jekyllrb.com/docs/datafiles), [Filtros líquidos](https://jekyllrb.com/docs/liquid/filters/) y otras características.
