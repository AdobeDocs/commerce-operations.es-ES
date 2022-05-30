---
title: Actualizar una instalación basada en Git
description: Actualice una instalación de Adobe Commerce o Magento Open Source que haya clonado desde un repositorio de Git.
source-git-commit: 7bcfbc4483f4b6d4c1a5e852adbd1cd81bc136b7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Actualizar una instalación basada en Git

En este tema se explica cómo un desarrollador colaborador puede actualizar Adobe Commerce o Magento Open Source sin necesidad de reinstalarlo. Si no es desarrollador colaborador, consulte [Realizar una actualización](../implementation/perform-upgrade.md).

Para actualizar si es un desarrollador colaborador:

{{$include /help/_includes/server-login.md}}

1. Guarde los cambios realizados en la variable `composer.json` porque los siguientes pasos lo sobrescriben.

1. Cree una copia de seguridad de su `composer.json` archivo.

   ```bash
   cp composer.json composer.json.old
   ```

1. Actualice el repositorio local para obtener el código más reciente:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >If `git pull origin develop` falla, consulte [solución de problemas](https://support.magento.com/hc/en-us/articles/360034229872).

1. Difiera y fusione su `composer.json.old` con el `composer.json` archivo.

1. Resuelva dependencias y escriba versiones exactas en el `composer.lock` archivo.

   ```bash
   composer update
   ```

1. Actualice la base de datos:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```
