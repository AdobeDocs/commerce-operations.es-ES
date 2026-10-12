---
title: Actualización de una instalación basada en Git
description: Actualice una instalación de Adobe Commerce que haya clonado desde un repositorio de Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
last-update: 2026-04-28
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
source-git-commit: a3c0eba7bdcd8017e88bdb4df1f45d77fe4bb351
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%
---
# Actualización de una instalación basada en Git

En este tema se explica cómo un desarrollador colaborador puede actualizar Adobe Commerce sin volver a instalarlo. Si no eres un desarrollador colaborador, consulta [Realizar una actualización](../implementation/perform-upgrade.md).

Para actualizar si es un desarrollador colaborador:

{{$include /help/_includes/server-login.md}}

1. Guarde los cambios que haya realizado en el archivo `composer.json` porque los siguientes pasos lo sobrescribirán.

1. Cree una copia de seguridad del archivo `composer.json`.

   ```shell
   cp composer.json composer.json.old
   ```

1. Actualice el repositorio local para obtener el código más reciente:

   ```shell
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Si `git pull origin develop` falla, consulte [solución de problemas](https://support.magento.com/hc/en-us/articles/360034229872).

1. Diferencia y combine el archivo de `composer.json.old` con el archivo de `composer.json`.

1. Resuelva dependencias y escriba versiones exactas en el archivo `composer.lock`.

   ```shell
   composer update
   ```

1. Actualizar la base de datos:

   ```shell
   bin/magento setup:upgrade
   ```

1. Limpie la caché:

   ```shell
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
