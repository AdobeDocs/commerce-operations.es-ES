---
title: Convertir archivos de diseño
description: Obtenga información sobre cómo convertir archivos de diseño XML mediante las herramientas de línea de comandos de Adobe Commerce. Descubra actualizaciones de hojas de estilo XSLT y procesos de conversión de archivos.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
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
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# Convertir archivos de diseño XML

{{file-system-owner}}

Utilice este comando para actualizar los archivos XML de diseño si actualiza la hoja de estilo XSLT (Extensible Stylesheet Language Transformations) correspondiente.

- [Instrucciones de diseño](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions)
- [Tipos de archivo de diseño](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-files-types-and-conventions)

Opciones de comando:

```shell
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Donde:

- `{xml file}`: es la ruta de acceso completa y el nombre de archivo de un archivo XML de diseño que se va a convertir (obligatorio).
- `{xslt stylesheet}`: es la ruta de acceso completa y el nombre de archivo de un archivo de hoja de estilos XSLT que se utilizará para la conversión (obligatorio)
- `-o|--overwrite`: incluya esta opción para sobrescribir el archivo XML existente
