---
title: Comprobar el estado de la base de datos
description: Siga estos pasos para comprobar el estado de la base de datos de Adobe Commerce o de Magento Open Source.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---

# Comprobar el estado de la base de datos

Antes de ejecutar este comando, debe [Crear o actualizar la configuración de implementación](deployment.md).

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
| 1 | Algunos módulos utilizan versiones de código más recientes o anteriores que la base de datos | Ejecutar [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos y ejecutar `composer update` del directorio raíz de la aplicación para actualizar las dependencias del componente |
| 2 | `magento setup:upgrade` es obligatorio | [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos |
