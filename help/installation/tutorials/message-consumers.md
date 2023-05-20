---
title: Configuración de consumidores de mensajes
description: Siga estos pasos para configurar el comportamiento de Adobe Commerce o de los consumidores de cola de mensajes del Magento Open Source.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Configuración de consumidores de mensajes

Antes de ejecutar este comando, debe hacer lo siguiente *o* usted debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Creación del esquema de base de datos](database.md)

## Configuración del comportamiento de los consumidores

La configuración del comportamiento del consumidor se realiza enviando pares de clave/valor dentro de la función de configuración:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

{{$include /help/_includes/cli-consumers.md}}
