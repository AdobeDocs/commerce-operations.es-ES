---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Información general

Este proyecto incluye varias tareas de Rake para automatizar varios aspectos del flujo de trabajo, como la generación de datos para resúmenes de noticias, el procesamiento de archivos con plantilla, la optimización de imágenes y la generación de mapas. A continuación se describen las descripciones y directrices de uso de cada tarea de rastrillo definida en el archivo de rastrillo.

## Rastrear tareas

### `render`

Procesa los archivos con plantillas en el directorio `_jekyll/templates` con datos de `_jekyll/_data/`. El resultado se encontrará en el directorio `help/includes/templated`.

**Uso:**

```sh
rake render
```

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
