---
title: Borrado de caché con varias instancias de barniz
description: Descubra cómo funciona la limpieza de caché con varias instancias de Barniz.
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Caché que borra varias instancias de Varnish

Adobe Commerce y Magento Open Source admiten varias instancias de Barniz listas para usarse.

Este tema muestra los conceptos básicos para configurar varias instancias de Varnish con Commerce.

## Configuración para depurar varias instancias de Barniz

Commerce purga los hosts de Varnish después de configurar los hosts de Varnish mediante el [`magento setup:config:set`](../../installation/tutorials/deployment.md) comando.

Debe usar el `--http-cache-hosts` para especificar una lista separada por comas de hosts de barniz y puertos de escucha. (No separe los hosts con caracteres de espacio.)

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

A continuación, puede purgar todos los hosts de Varnish al actualizar la caché de Commerce (también denominada _limpieza_ la caché) en Admin o mediante la línea de comandos.

Para actualizar la caché con el administrador, haga clic en **SISTEMA** > Herramientas > **Administración de caché**, luego haga clic en **Vaciar caché del Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché de varias instancias de Barniz desde cli, utilice el [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como el [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
