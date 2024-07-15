---
title: Borrado de caché con varias instancias de barniz
description: Descubra cómo funciona la limpieza de caché con varias instancias de Barniz.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Caché que borra varias instancias de Varnish

Adobe Commerce admite varias instancias de Barniz de forma predeterminada.

En este tema se muestran los conceptos básicos para configurar varias instancias de Varnish con Commerce.

## Configuración para depurar varias instancias de Barniz

Commerce purga los hosts de Varnish después de configurar los hosts de Varnish mediante el comando [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Debe usar el parámetro `--http-cache-hosts` para especificar una lista separada por comas de hosts de Varnish y puertos de escucha. (No separe los hosts con caracteres de espacio.)

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

A continuación, puede purgar todos los hosts de Varnish cuando actualice la caché de Commerce (también conocida como _limpieza_ de la caché) en Admin o mediante la línea de comandos.

Para actualizar la caché con el administrador, haga clic en **SISTEMA** > Herramientas > **Administración de caché** y, a continuación, haga clic en **Vaciar caché del Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché de varias instancias de Varnish desde cli, use el comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
