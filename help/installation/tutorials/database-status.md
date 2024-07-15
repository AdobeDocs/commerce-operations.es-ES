---
title: Comprobar el estado de la base de datos
description: Siga estos pasos para comprobar el estado de la base de datos de Adobe Commerce.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 3%

---

# Comprobar el estado de la base de datos

Antes de ejecutar este comando, debe [crear o actualizar la configuración de implementación](deployment.md).

## Uso de comandos

Para comprobar el estado de la base de datos.

```bash
bin/magento setup:db:status
```

Este comando no tiene argumentos ni opciones.

Salida de ejemplo:

```terminal
All modules are up to date.
```

El comando devuelve uno de los siguientes códigos de salida:

| Código de salida | Descripción | Acción sugerida |
|--------------|--------------|---------------|
| 0 | Normal | Ninguno |
| 1 | Algunos módulos utilizan versiones de código más recientes o anteriores que la base de datos | Ejecute [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos y ejecute `composer update` desde el directorio raíz de la aplicación para actualizar las dependencias del componente |
| 2 | Se requiere `magento setup:upgrade`. | [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos |
