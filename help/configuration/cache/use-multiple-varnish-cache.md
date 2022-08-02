---
title: Borrado de caché con varias instancias de Varnish
description: Aprenda cómo funciona la limpieza de caché con varias instancias de Varnish.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Borrado de caché de varias instancias de Varnish

Adobe Commerce y Magento Open Source admiten varias instancias de Varnish listas para usar.

En este tema se muestran los conceptos básicos para configurar varias instancias de Varnish con Commerce.

## Configuración para purgar varias instancias de Varnish

El comercio purga los hosts de Varnish después de configurar los hosts de Varnish usando la variable [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) comando.

Debe usar la variable `--http-cache-hosts` para especificar una lista separada por comas de los hosts Varnish y puertos de escucha. (No separe los hosts con un carácter de espacio).

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

A continuación, puede purgar todos los hosts de Varnish cuando actualice la caché de comercio (también denominada _limpieza_ la caché) en Admin o utilizando la línea de comandos.

Para actualizar la caché mediante el administrador, haga clic en **SISTEMA** > Herramientas > **Administración de caché** y haga clic en **Vaciar caché del Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché de varias instancias de Varnish desde cli, use el [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
