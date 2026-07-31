---
title: Configuración de consumidores de mensajes
description: Siga estos pasos para configurar el comportamiento de los consumidores de colas de mensajes de Adobe Commerce.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28T00:00:00Z
source-git-commit: 1166b8fbfeef21a51ad6e4e695aed2b25006230e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Configuración de consumidores de mensajes

Antes de ejecutar este comando, debe hacer lo siguiente *o* y debe [instalar la aplicación](../advanced.md):

* [Crear o actualizar la configuración de implementación](deployment.md)
* [Creación del esquema de base de datos](database.md)

## Configuración del comportamiento de los consumidores

La configuración del comportamiento del consumidor se realiza enviando pares de clave/valor dentro de la función de configuración:

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
