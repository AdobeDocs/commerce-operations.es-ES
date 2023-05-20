---
title: Actualización de una instalación basada en Git
description: Actualice una instalación de Adobe Commerce o Magento Open Source que haya clonado desde un repositorio de Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Actualización de una instalación basada en Git

En este tema se explica cómo un desarrollador colaborador puede actualizar Adobe Commerce o Magento Open Source sin volver a instalarlo. Si no es un desarrollador colaborador, consulte [Realización de una actualización](../implementation/perform-upgrade.md).

Para actualizar si es un desarrollador colaborador:

{{$include /help/_includes/server-login.md}}

1. Guarde los cambios realizados en el `composer.json` porque los siguientes pasos lo sobrescriben.

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

1. Diferencia y fusión de su `composer.json.old` archivo con la variable `composer.json` archivo.

1. Resuelva dependencias y escriba versiones exactas en `composer.lock` archivo.

   ```bash
   composer update
   ```

1. Actualizar la base de datos:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpie la caché:

   ```bash
   bin/magento cache:clean
   ```
