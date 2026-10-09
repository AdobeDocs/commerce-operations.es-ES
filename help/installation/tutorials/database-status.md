---
title: Comprobar el estado de la base de datos
description: Siga estos pasos para comprobar el estado de la base de datos de Adobe Commerce.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
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
source-wordcount: '104'
ht-degree: 3%
---
# Comprobar el estado de la base de datos

Antes de ejecutar este comando, debe [crear o actualizar la configuración de implementación](deployment.md).

## Uso de comandos

Para comprobar el estado de la base de datos.

```shell
bin/magento setup:db:status
```

Este comando no tiene argumentos ni opciones.

Salida de ejemplo:

```text
All modules are up to date.
```

El comando devuelve uno de los siguientes códigos de salida:

| Código de salida | Descripción | Acción sugerida |
|--------------|--------------|---------------|
| 0 | Normal | Ninguno |
| 1 | Algunos módulos utilizan versiones de código más recientes o anteriores que la base de datos | Ejecute [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos y ejecute `composer update` desde el directorio raíz de la aplicación para actualizar las dependencias del componente |
| 2 | Se requiere `magento setup:upgrade`. | [`magento setup:upgrade`](database-upgrade.md) para actualizar el esquema de la base de datos |
