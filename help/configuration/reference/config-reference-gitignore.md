---
title: .gitignore reference
description: Consulte cómo añadir un archivo incluido en la lista de omisión.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# .gitignore reference

El Magento Open Source incluye un archivo base `.gitignore`. Ver [el archivo `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) más reciente de Commerce. Si debe agregar un archivo que se encuentra en la lista `.gitignore`, puede utilizar la opción `-f` (forzar) al almacenar en zona intermedia una confirmación:

```bash
git add <path/filename> -f
```
