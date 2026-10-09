---
title: .gitignore reference
description: Obtenga información sobre cómo agregar archivos a la lista .gitignore para proyectos de Adobe Commerce. Descubra las prácticas recomendadas de administración del control de versiones y exclusión de archivos.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
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
source-wordcount: '65'
ht-degree: 0%
---
# .gitignore reference

Magento Open Source incluye un archivo base `.gitignore`. Ver [el archivo `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) más reciente de Commerce. Si debe agregar un archivo que se encuentra en la lista `.gitignore`, puede utilizar la opción `-f` (forzar) al almacenar en zona intermedia una confirmación:

```shell
git add <path/filename> -f
```
