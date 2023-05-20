---
title: Creación de enlaces simbólicos a archivos LESS
description: Aprenda a crear enlaces simbólicos a archivos LESS.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Creación de enlaces simbólicos a archivos LESS

{{file-system-owner}}

Para crear enlaces simbólicos a archivos LESS:

Opciones de comando:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Durante el desarrollo, este comando crea enlaces simbólicos para los archivos LESS en el `var/view_preprocessed` y `pub/static` carpetas. Este proceso no compila archivos LESS en archivos CSS.

En la tabla siguiente se explican los parámetros y valores de este comando.

| Parámetro | Valor | ¿Requerido? |
| --------- | ----- | --------- |
| `--type` | Tipo de archivos de origen: [menos] (valor predeterminado: &quot;less&quot;)<br>Actualmente, LESS es el único tipo de archivo compatible. | No |
| `--locale` | Código de configuración regional.<br>Para mostrar la lista de códigos de configuración regional, escriba `bin/magento info:language:list` | No |
| `--area` | Área (`adminhtml` para el área administrativa, `frontend` para la tienda). | No |
| `--theme` | Nombre del tema en `<VendorName>/<theme-name>` formato. Por ejemplo, `Magento/blank` o `Magento/backend`. | No |
| `<file>` | Lista separada por espacios de archivos CSS para convertirlos en LESS sin la extensión CSS. (El valor predeterminado es `css/styles-m css/styles-l`, para el tipo adminhtml `css/styles css/styles-old`) | No |

Por ejemplo, para crear archivos LESS para el tema de front-end denominado `VendorName/themeName` en el `en_US` configuración regional mediante un archivo CSS denominado `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, introduzca el siguiente comando:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Se muestran los siguientes mensajes para confirmar que se ha realizado correctamente:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Para crear archivos LESS para el adminhtml:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
