---
title: Administración de módulos y extensiones (desarrollador)
description: Administre módulos y extensiones de Adobe Commerce mediante la interfaz de línea de comandos y el administrador de paquetes del Compositor.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Administración de módulos y extensiones

Los desarrolladores que contribuyen actualizan módulos y extensiones especificando sus versiones en el archivo de Adobe Commerce `composer.json`. Si no eres un desarrollador colaborador, consulta [Realizar una actualización](../implementation/perform-upgrade.md).

Puede agregar una sección `require` al archivo `composer.json` o usar el comando `composer require` de la siguiente manera:

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

## Usar el comando `composer require`

Uso de comandos:

```bash
composer require <vendor>/<name>:<version>
```

Por ejemplo:

```bash
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

   ```bash
   composer update
   ```
