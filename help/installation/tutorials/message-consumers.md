---
title: Configuración de consumidores de mensajes
description: Siga estos pasos para configurar el comportamiento de los consumidores de colas de mensajes de Adobe Commerce.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
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

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descripciones de parámetros

{{$include /help/_includes/cli-consumers.md}}
