---
title: Comprobar el estado de la base de datos
description: Siga estos pasos para comprobar el estado de la base de datos de Adobe Commerce o Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 2%

---


# Comprobar el estado de la base de datos

Antes de ejecutar este comando, debe [Crear o actualizar la configuración de implementación](deployment.md).

## Uso del comando

Para comprobar el estado de la base de datos.

```bash
bin/magento setup:db:status
```

Este comando no tiene argumentos ni opciones.

El resultado de muestra es el siguiente:

```terminal
All modules are up to date.
```

El comando devuelve uno de los siguientes códigos de salida:

| Código de salida | Descripción | Acción sugerida |
|--------------|--------------|---------------|
| 0 | Normal | Ninguna |
| 1 | Algunos módulos utilizan versiones de código más recientes o anteriores a la base de datos | Ejecutar [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de base de datos y ejecutar `composer update` desde el directorio raíz de la aplicación para actualizar las dependencias de los componentes |
| 2 | `magento setup:upgrade` es obligatorio | [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos |
