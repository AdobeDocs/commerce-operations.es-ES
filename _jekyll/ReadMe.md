---
source-git-commit: 9994f486c38df4c0dc2ff477c48f3e8f3259aa9f
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---
# Información general

Este proyecto incluye varias tareas de Rake para automatizar varios aspectos del flujo de trabajo, como la generación de datos para resúmenes de noticias, el procesamiento de archivos con plantilla, la optimización de imágenes y la generación de mapas. A continuación se describen las descripciones y directrices de uso de cada tarea de rastrillo definida en el archivo de rastrillo.

## Rastrear tareas

### `render`

Procesa los archivos con plantillas en el directorio `_jekyll/templates` con datos de `_jekyll/_data/`. El resultado se encontrará en el directorio `help/includes/templated`. Esta tarea mantiene automáticamente las relaciones de inclusión y las marcas de tiempo después del procesamiento.

**Uso:**

```sh
rake render
```

**Qué hace:**
- Ejecuta el script de procesamiento para generar archivos con plantillas
- Ejecuta `includes:maintain_all` para actualizar las relaciones de inclusión y las marcas de tiempo
- Garantiza que todos los metadatos de inclusión estén actualizados después del procesamiento

### `image_optim`

Optimiza las imágenes en archivos no confirmados modificados. Para otras imágenes, utilice el argumento `path` para especificar el directorio o el archivo.

**Uso:**

```sh
rake image_optim
```

**Con `path` argumento:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Genera datos para un compendio de noticias. El periodo de tiempo predeterminado es desde la última actualización. Puede especificar un período diferente utilizando el argumento `since`.

**Uso:**

```sh
rake whatsnew
```

**Con `since` argumento:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Genera datos para un compendio de noticias en Prácticas recomendadas. El periodo de tiempo predeterminado es desde la última actualización. Puede especificar un período diferente utilizando el argumento `since`.

**Uso:**

```sh
rake whatsnew_bp
```

**Con `since` argumento:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Genera un mapa de regiones de Azure. El archivo de datos de entrada debe colocarse en `_jekyll/tmp/azure-regions.json`. El resultado se encontrará en `_jekyll/tmp/azure-regions.svg`. Tenga en cuenta que necesita instalar Python, [PyGMT](https://www.pygmt.org/latest/install.html) y [pdf2svg](https://formulae.brew.sh/formula/pdf2svg).

**Uso:**

```sh
rake azure_regions
```

### `includes:maintain_relationships`

Detecta y actualiza el archivo `include-relationships.yml` al analizar todos los archivos Markdown del directorio `help` para obtener instrucciones de inclusión mediante el patrón `{{$include /help/_includes/filename.md}}`. Esta tarea mantiene automáticamente las relaciones entre los archivos de contenido principales y sus archivos incluidos.

**Uso:**

```sh
rake includes:maintain_relationships
```

**Qué hace:**
- Lee la lista de archivos de inclusión existentes del directorio `help/_includes`
- Busca en todos los archivos de markdown principales para encontrar cuáles hacen referencia a cada uno de ellos
- Utiliza el patrón `{{$include /help/_includes/filename.md}}` para identificar referencias
- Actualiza el archivo `include-relationships.yml` con relaciones detectadas
- Proporciona un resumen de los cambios realizados e identifica las inclusiones sin referencia

### `includes:maintain_timestamps`

Mantiene las marcas de hora de inclusión agregando las marcas de hora de cambio de archivo de inclusión más recientes a los archivos principales. Esta tarea lee el archivo `include-relationships.yml`, comprueba el historial de Git de cada archivo de inclusión y agrega o actualiza marcas de tiempo al final de los archivos principales.

**Uso:**

```sh
rake includes:maintain_timestamps
```

**Qué hace:**
- Las cargas incluyen relaciones de `include-relationships.yml`
- Para cada archivo principal, encuentra la última fecha de confirmación de Git entre sus archivos de inclusión
- Agrega o actualiza comentarios de HTML con marcas de tiempo al final de los archivos principales
- Utiliza el formato: `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Proporciona resultados detallados que muestran qué archivos de inclusión se comprobaron y sus marcas de tiempo

**Ejemplo de salida:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

Una tarea de conveniencia que ejecuta `includes:maintain_relationships` y `includes:maintain_timestamps` en secuencia. Esta es la forma recomendada de mantener tanto las relaciones de inclusión como las marcas de tiempo.

**Uso:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Los búsquedas incluyen archivos en el directorio `help/_includes` a los que no hace referencia ningún archivo Markdown. Esto ayuda a identificar archivos de inclusión huérfanos que se pueden eliminar de forma segura.

**Uso:**

```sh
rake unused_includes
```

## Enumeración de tareas disponibles

Para ver todas las tareas de rastrillo disponibles con sus descripciones, utilice:

```sh
rake --tasks
```

Para obtener información más detallada sobre una tarea específica, utilice:

```sh
rake -T [task_name]
```

## Incluir tareas de administración

Todas las tareas relacionadas con la inclusión están organizadas en el área de nombres `includes` para mejorar la organización:

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Incluir formato de archivo de relaciones

El archivo `include-relationships.yml` realiza un seguimiento de las relaciones entre los archivos de contenido principal y sus archivos incluidos. Este archivo lo mantiene automáticamente la tarea de rastrillado `maintain_include_relationships`, que detecta las relaciones leyendo los archivos de inclusión existentes y buscando los archivos principales que hacen referencia a ellos.

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
- Se han especificado las gemas necesarias en Gemfile.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) y [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) para la tarea `azure_regions`.

## Configurar

1. Instale las gemas necesarias:

   ```sh
   bundle install
   ```

2. Asegúrese de que tiene Python, PyGMT y pdf2svg instalados para la tarea `azure_regions`. Para obtener más información sobre la configuración, consulte la documentación en los comentarios en [_scripts/azure_regions.py](_scripts/azure_regions.py).
