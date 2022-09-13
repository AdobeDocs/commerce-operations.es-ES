---
title: Crear el esquema de la base de datos
description: Siga estos pasos para crear una base de datos para su Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Crear el esquema de la base de datos

Antes de ejecutar este comando, debe [Crear o actualizar la configuración de implementación](deployment.md).

## Configuración de la base de datos y adición de datos

Uso de comandos:

```bash
bin/magento setup:db-schema:upgrade
```

Para ver el estado de la base de datos, introduzca

```bash
bin/magento setup:db:status
```
