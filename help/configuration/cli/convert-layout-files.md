---
title: Convertir archivos de diseño
description: Convertir archivos de diseño XML.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Convertir archivos de diseño XML

{{file-system-owner}}

Utilice este comando para actualizar los archivos XML de presentación si actualiza la hoja de estilo correspondiente Transformaciones de lenguaje de hoja de estilo extensible (XSLT).

- [Instrucciones de diseño](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Tipos de archivo de diseño](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Opciones de comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Donde:

- `{xml file}`: es la ruta completa y el nombre de archivo de un archivo XML de diseño que se va a convertir (requerido).
- `{xslt stylesheet}`: es la ruta completa y el nombre de archivo de un archivo de hoja de estilo XSLT que se utilizará para la conversión (requerido).
- `-o|--overwrite`—incluir esta opción para sobrescribir el archivo XML existente
