---
title: Crear enlaces simbólicos a archivos LESS
description: Aprenda a crear enlaces simbólicos a archivos LESS.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Crear enlaces simbólicos a archivos LESS

{{file-system-owner}}

Para crear enlaces simbólicos a archivos LESS:

Opciones de comando:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Durante el desarrollo, este comando crea enlaces simbólicos para archivos LESS en la variable `var/view_preprocessed` y `pub/static` carpetas. Este proceso no compila archivos LESS en archivos CSS.

La siguiente tabla explica los parámetros y valores de este comando.

| Parámetro | Valor | ¿Requerido? |
| --------- | ----- | --------- |
| `--type` | Tipo de archivos de origen: [less] (predeterminado: &quot;less&quot;)<br>Actualmente, LESS es el único tipo de archivo admitido. | No |
| `--locale` | Código de configuración regional.<br>Para mostrar la lista de códigos de configuración regional, introduzca `bin/magento info:language:list` | No |
| `--area` | Área (`adminhtml` para el ámbito administrativo, `frontend` para la tienda). | No |
| `--theme` | Nombre del tema en `<VendorName>/<theme-name>` formato. Por ejemplo, `Magento/blank` o `Magento/backend`. | No |
| `<file>` | Lista de archivos CSS separados por espacios para convertir a LESS sin la extensión CSS. (El valor predeterminado es `css/styles-m css/styles-l`, para el tipo adminhtml `css/styles css/styles-old`) | No |

Por ejemplo, para crear archivos LESS para el tema de front-end denominado `VendorName/themeName` en el `en_US` configuración regional con un archivo CSS denominado `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, introduzca el siguiente comando:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Se muestran los siguientes mensajes para confirmar que el proceso ha sido satisfactorio:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Para crear archivos LESS para el adminhtml:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
