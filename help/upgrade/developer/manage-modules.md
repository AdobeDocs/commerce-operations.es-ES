---
title: Administrar módulos y extensiones
description: Administre módulos y extensiones de Adobe Commerce y Magento Open Source mediante la interfaz de línea de comandos y el administrador de paquetes del Composer.
source-git-commit: 7bcfbc4483f4b6d4c1a5e852adbd1cd81bc136b7
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Administración de módulos y extensiones

Los desarrolladores que contribuyen a la actualización de módulos y extensiones especificando sus versiones en Adobe Commerce o en el Magento Open Source `composer.json` archivo. Si no es desarrollador colaborador, consulte [Realizar una actualización](../implementation/perform-upgrade.md).

Puede agregar una `require` para `composer.json` o puede usar la variable `composer require` como se indica a continuación:

{{$include /help/_includes/server-login.md}}

Tiene las siguientes opciones:

## Obtener versiones de módulos disponibles

Uso de comandos:

```bash
composer show --all <vendor>/<name>
```

Por ejemplo:

```bash
composer show --all example/module
```

## Utilice la variable `composer require` command

Uso de comandos:

```bash
composer require <vendor>/<name>:<version>
```

Por ejemplo:

```bash
composer require example/module:1.0.0
```

Espere mientras el Compositor actualiza las dependencias e instala el módulo.

## Agregue un `require` al archivo composer.json

1. Abra el `composer.json` en un editor de texto.

1. Agregue un `require` para obtener más información.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Guarde los cambios en la `composer.json` y salga del editor de texto.

1. Resuelva dependencias y escriba versiones exactas en el `composer.lock` archivo.

   ```bash
   composer update
   ```
