---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
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
