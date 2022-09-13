---
title: Configurar consumidores de mensajes
description: Siga estos pasos para configurar el comportamiento de los consumidores de cola de mensajes de Adobe Commerce o de Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# Configurar consumidores de mensajes

Antes de ejecutar este comando, debe hacer lo siguiente *o* debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Crear el esquema de la base de datos](database.md)

## Configurar el comportamiento de los consumidores

La configuración del comportamiento del consumidor se realiza enviando pares de clave/valor dentro de la función de configuración:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

{{$include /help/_includes/cli-consumers.md}}
