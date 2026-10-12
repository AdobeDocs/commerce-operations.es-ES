---
title: Administración de módulos y extensiones (desarrollador)
description: Administre módulos y extensiones de Adobe Commerce mediante la interfaz de línea de comandos y el administrador de paquetes del Compositor.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%
---
# Administración de módulos y extensiones

Los desarrolladores que contribuyen actualizan módulos y extensiones especificando sus versiones en el archivo de Adobe Commerce `composer.json`. Si no eres un desarrollador colaborador, consulta [Realizar una actualización](../implementation/perform-upgrade.md).

Puede agregar una sección `require` al archivo `composer.json` o usar el comando `composer require` de la siguiente manera:

{{$include /help/_includes/server-login.md}}

Tiene las siguientes opciones:

## Obtener versiones de módulos disponibles

Uso de comandos:

```shell
composer show --all <vendor>/<name>
```

Por ejemplo:

```shell
composer show --all example/module
```

## Usar el comando `composer require`

Uso de comandos:

```shell
composer require <vendor>/<name>:<version>
```

Por ejemplo:

```shell
composer require example/module:1.0.0
```

Espere mientras Composer actualiza las dependencias e instala el módulo.

## Agregue una sección `require` al archivo composer.json

1. Abra `composer.json` en un editor de texto.

1. Agregar una sección `require`.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Guarde los cambios en el archivo `composer.json` y salga del editor de texto.

1. Resuelva dependencias y escriba versiones exactas en el archivo `composer.lock`.

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
