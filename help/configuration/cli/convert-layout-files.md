---
title: Convertir archivos de diseño
description: Obtenga información sobre cómo convertir archivos de diseño XML mediante las herramientas de línea de comandos de Adobe Commerce. Descubra actualizaciones de hojas de estilo XSLT y procesos de conversión de archivos.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Convertir archivos de diseño XML

{{file-system-owner}}

Utilice este comando para actualizar los archivos XML de diseño si actualiza la hoja de estilo XSLT (Extensible Stylesheet Language Transformations) correspondiente.

- [Instrucciones de diseño](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Tipos de archivo de diseño](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opciones de comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Donde:

- `{xml file}`: es la ruta de acceso completa y el nombre de archivo de un archivo XML de diseño que se va a convertir (obligatorio).
- `{xslt stylesheet}`: es la ruta de acceso completa y el nombre de archivo de un archivo de hoja de estilos XSLT que se utilizará para la conversión (obligatorio)
- `-o|--overwrite`: incluya esta opción para sobrescribir el archivo XML existente
