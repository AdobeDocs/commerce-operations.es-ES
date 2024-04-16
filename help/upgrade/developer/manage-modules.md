---
title: Administración de módulos y extensiones (desarrollador)
description: Administre módulos y extensiones de Adobe Commerce mediante la interfaz de línea de comandos y el administrador de paquetes del Compositor.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# Administración de módulos y extensiones

Contribuir a que los desarrolladores actualicen los módulos y las extensiones especificando sus versiones en Adobe Commerce o Magento Open Source `composer.json` archivo. Si no es un desarrollador colaborador, consulte [Realización de una actualización](../implementation/perform-upgrade.md).

Puede añadir una variable `require` a la sección `composer.json` o puede utilizar el archivo `composer require` como se indica a continuación:

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

## Utilice el `composer require` mando

Uso de comandos:

```bash
composer require <vendor>/<name>:<version>
```

Por ejemplo:

```bash
composer require example/module:1.0.0
```

Espere mientras Composer actualiza las dependencias e instala el módulo.

## Añadir un `require` al archivo composer.json

1. Abra el `composer.json` en un editor de texto.

1. Añadir un `require` sección.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Guarde los cambios en `composer.json` y salga del editor de texto.

1. Resuelva dependencias y escriba versiones exactas en `composer.lock` archivo.

   ```bash
   composer update
   ```
