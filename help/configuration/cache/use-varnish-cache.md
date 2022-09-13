---
title: Borrado de caché con Varnish
description: Aprenda cómo funciona la limpieza de caché con Varnish y cómo utilizarla como acelerador de almacenamiento en caché web para la aplicación Adobe Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# Borrado de caché con Varnish

En este tema se tratan los conceptos básicos del uso de Varnish como acelerador de almacenamiento en caché web para Adobe Commerce y Magento Open Source.

## Purga de barniz

Según [Documentación de Varnish](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *purge* es lo que sucede cuando se elige un objeto de la variable [cache](https://glossary.magento.com/cache) y desecharlo junto con sus variantes&quot;. Una purga de barniz es similar a un comando de limpieza de caché (o hacer clic en **Vaciar caché del Magento** en el administrador).

De hecho, al limpiar, vaciar o actualizar la caché de comercio, también se depura Varnish.

Después de instalar y configurar Varnish para que funcione con Commerce, las siguientes acciones pueden resultar en una purga de Varnish:

- Mantenimiento de un [sitio web](https://glossary.magento.com/website).

   Por ejemplo, cualquier cosa que haga en el Administrador de :

   - **ALMACENES** > **Configuración** > **Configuración** > GENERAL > **General**
   - **ALMACENES** > **Configuración** > **Configuración** > GENERAL > **Configuración de moneda**
   - **ALMACENES** > **Configuración** > **Configuración** > GENERAL > **Almacenar direcciones de correo electrónico**

   Cuando Comercio detecta un cambio de este tipo, aparece un mensaje que le informa de que debe actualizar la caché.

- Mantenimiento de una tienda (por ejemplo, adición o edición de categorías, precios, productos y reglas de precios promocionales).

   Varnish se depura automáticamente cuando realiza cualquiera de estas tareas.

- Mantenimiento del código fuente.

   Debe actualizar la caché y también eliminar periódicamente todo en la `generated/code` y `generated/metadata` directorios. Para obtener información sobre cómo actualizar la caché, consulte la siguiente sección.

## Configurar Commerce para depurar Varnish

El comercio purga los hosts de Varnish después de configurar los hosts de Varnish usando la variable [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) comando.

Puede utilizar el parámetro opcional `--http-cache-hosts` para especificar una lista separada por comas de los hosts Varnish y puertos de escucha. Configure todos los hosts de Varnish, independientemente de que tenga uno o varios. (No separe los hosts con un carácter de espacio).

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

A continuación, puede purgar los hosts de Varnish cuando actualice la caché de comercio (también denominada *limpieza* la caché) en Admin o utilizando la línea de comandos.

Para actualizar la caché mediante el administrador, haga clic en **[!UICONTROL SYSTEM]** > Herramientas > **Administración de caché** y haga clic en **Vaciar caché del Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché utilizando la línea de comandos, normalmente utiliza la variable [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
