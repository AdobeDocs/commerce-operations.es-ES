---
title: Creación del esquema de base de datos
description: Siga estos pasos para crear una base de datos para Adobe Commerce o Magento Open Source.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---

# Creación del esquema de base de datos

Antes de ejecutar este comando, debe [Crear o actualizar la configuración de implementación](deployment.md).

## Configurar la base de datos y añadir datos

Uso de comandos:

```bash
bin/magento setup:db-schema:upgrade
```

Para ver el estado de la base de datos, introduzca

```bash
bin/magento setup:db:status
```
