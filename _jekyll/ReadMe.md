---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%
---

# Información general

Este proyecto utiliza las tareas de Rake para automatizar partes del flujo de trabajo de documentación. La mayoría de las tareas se comparten entre repositorios de documentos de ExL Commerce y provienen de la joya [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks). A continuación se indican algunas tareas específicas de este repositorio.

**Para tareas comunes (procesar plantillas, administrar inclusiones, optimizar/auditar imágenes y generar el resumen de novedades), consulte el archivo LÉAME [adobe-comdox-exl-rake-tasks](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md).**

> Todos los comandos de `bundle exec rake` que se muestran a continuación deben ejecutarse desde el directorio `_jekyll/`, ya que ahí es donde se encuentran Gemfile y Rakefile.

## Tareas de seguimiento específicas de repositorios

### `whatsnew_bp`

Genera datos para un compendio de noticias en Prácticas recomendadas. El periodo de tiempo predeterminado es desde la última actualización. Puede especificar un período diferente utilizando el argumento `since`.

**Uso:**

```sh
bundle exec rake whatsnew_bp
```

**Con `since` argumento:**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `whatsnew_consolidated`

Consolida los proyectos de documentación publicados de Novedades de los proyectos configurados de Commerce en `help/_includes/automated/whatsnew/consolidated.md`.

```sh
bundle exec rake whatsnew_consolidated
```

Configurar proyectos en `whatsnew_consolidated.projects` en [`_config.yml`](_config.yml). Cada entrada requiere un nombre de repositorio, un título de proyecto y una dirección URL del sitio web HTTP(S) absoluta:

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/es/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/es/docs/commerce
```

Mover entradas para cambiar el orden de la sección. Puede entrelazar libremente proyectos de ambas plataformas. Los nombres de repositorio que terminan con `.en` utilizan la ruta de origen ExL, `help/_includes/templated/whats-new.md`. Todos los demás repositorios utilizan la ruta de origen DevSite `src/pages/_includes/templated/whats-new.md`.

La tarea recupera `main` archivos públicos de la organización GitHub `AdobeDocs`. Muestra el título de cada proyecto como un encabezado de texto sin formato e introduce cada tabla con una frase que vincula el título del proyecto con la página principal de la documentación configurada en `website` como origen de las actualizaciones de novedades. Utiliza `Description | Type | Date/source` encabezados de tabla en todo. Solo para proyectos DevSite, las etiquetas de escape `\<br/\>` se convierten en `<br/>`. De lo contrario, las filas del cuerpo, los duplicados, los vínculos y el orden de las filas de origen permanecen inalterados. Cada origen define su propio período de tiempo.

Se omiten los proyectos con un mensaje reconocido de no actualizaciones. Si cada proyecto no tiene entradas, la inclusión contiene un mensaje general de no actualizaciones. Los errores de configuración, captura, análisis o escritura fallan en la tarea sin reemplazar una inclusión existente.

La tarea no programa la generación ni actualiza las páginas consumidoras.

El grupo de pruebas centrado incluye pruebas de punto de entrada de Rake que cargan el archivo de clasificación `_jekyll` y se ejecutan a través de Bundler. Instale primero el paquete `_jekyll` y el paquete:

```sh
cd _jekyll && bundle install
```

A continuación, ejecute las pruebas desde la raíz del repositorio:

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

Crea `help/_includes/automated/whatsnew/consolidated-feedback.md` filtrando la inclusión `help/_includes/automated/whatsnew/consolidated.md` local existente.

```sh
bundle exec rake whatsnew_feedback
```

La tarea coincide con `Feedback` como un valor Type completo separado por comas, omitiendo mayúsculas y minúsculas y espacios en blanco adyacentes. Se incluyen los tipos combinados como `Feedback, technical`. Las menciones en descripciones, vínculos de origen o nombres de tipo parciales no cumplen los requisitos.

Las filas, duplicados, encabezados de proyecto de texto sin formato, frases de origen cuando están presentes y el orden de proyecto y fila no cambiarán. Se omiten los proyectos sin entradas coincidentes. Si nada coincide, la salida contiene un mensaje general sin comentarios.

La entrada ya debe existir. Ejecute `bundle exec rake whatsnew_consolidated` por separado cuando desee actualizarlo. La tarea de comentarios no obtiene contenido remoto, lee la configuración del proyecto ni regenera su entrada.

La entrada faltante o mal formada falla en la tarea sin reemplazar una inclusión filtrada existente. El archivo de entrada nunca se modifica y la salida filtrada se publica automáticamente.

### `get_released_versions`

Obtiene las últimas 10 versiones publicadas del repositorio `magento/magento2`. Requiere que [GitHub CLI](https://cli.github.com/) se instale y autentique.

**Uso:**

```sh
bundle exec rake get_released_versions
```

**Salida:** genera `tmp/core-release.txt` con nombres y fechas de etiquetas de versión.

### `first_merge_date`

Obtiene la fecha de la primera combinación en una rama especificada. Requiere que [GitHub CLI](https://cli.github.com/) se instale y autentique.

**Uso:**

```sh
bundle exec rake first_merge_date base=develop
```

**Argumentos:**

- `base` (obligatorio): El nombre de la rama de destino para buscar combinaciones.

## Enumeración de tareas disponibles

Para ver todas las tareas de rastrillo disponibles con sus descripciones, utilice:

```sh
bundle exec rake --tasks
```

Para obtener información más detallada sobre una tarea específica, utilice:

```sh
bundle exec rake -T [task_name]
```

## Incluir formato de archivo de relaciones

El archivo `include-relationships.yml` realiza un seguimiento de las relaciones entre los archivos de contenido principal y sus archivos incluidos. Este archivo lo mantiene automáticamente la tarea `includes:maintain_relationships` (consulte el archivo LÉAME [adobe-comdox-exl-rake-tasks](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) para el uso de tareas), que detecta relaciones al leer archivos include existentes y encontrar archivos principales que hacen referencia a ellos.

**Estructura de archivos:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Campos:**
- `metadata.last_updated`: marca de tiempo de la última actualización
- `metadata.total_relationships`: número total de archivos principales con inclusiones
- `metadata.auto_discovered`: indica que el archivo se generó automáticamente
- `metadata.discovery_date`: fecha en la que se descubrieron las relaciones por primera vez
- `relationships`: asignación de archivos principales a los archivos incluidos

**Incluir formato de instrucción:**
Los archivos de contenido principal utilizan la siguiente sintaxis para incluir otros archivos:

```markdown
{{$include /help/_includes/filename.md}}
```

## Requisitos previos

- Ruby y Bundler instalados.
- Se especificaron las gemas necesarias en el archivo Gemfile (las tareas comunes las proporciona `adobe-comdox-exl-rake-tasks`; la tarea `whatsnew` requiere además `whatsup_github`).
- [CLI de GitHub](https://cli.github.com/) para las tareas `get_released_versions` y `first_merge_date`.

## Configurar

Instale las gemas necesarias:

```sh
bundle install
```
