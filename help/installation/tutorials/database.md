---
title: Creación del esquema de base de datos
description: Siga estos pasos para crear una base de datos para su proyecto de Adobe Commerce.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Creación del esquema de base de datos

Antes de ejecutar este comando, debe [crear o actualizar la configuración de implementación](deployment.md).

## Configurar la base de datos y añadir datos

Uso de comandos:

```shell
bin/magento setup:db-schema:upgrade
```

Para ver el estado de la base de datos, introduzca

```shell
bin/magento setup:db:status
```
