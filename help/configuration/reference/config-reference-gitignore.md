---
title: .gitignore reference
description: Obtenga información sobre cómo agregar archivos a la lista .gitignore para proyectos de Adobe Commerce. Descubra las prácticas recomendadas de administración del control de versiones y exclusión de archivos.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# .gitignore reference

Magento Open Source incluye un archivo base `.gitignore`. Ver [el archivo `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) más reciente de Commerce. Si debe agregar un archivo que se encuentra en la lista `.gitignore`, puede utilizar la opción `-f` (forzar) al almacenar en zona intermedia una confirmación:

```shell
git add <path/filename> -f
```
