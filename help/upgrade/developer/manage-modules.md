---
title: Administración de módulos y extensiones (desarrollador)
description: Administre módulos y extensiones de Adobe Commerce mediante la interfaz de línea de comandos y el administrador de paquetes del Compositor.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
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

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
