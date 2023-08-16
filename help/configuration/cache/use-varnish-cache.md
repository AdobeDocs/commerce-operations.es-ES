---
title: Limpieza de caché con barniz
description: Aprenda cómo funciona la limpieza de caché con Varnish y cómo utilizarla como acelerador de almacenamiento en caché web para la aplicación de Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Limpieza de caché con barniz

En este tema se tratan los conceptos básicos del uso de Varnish como acelerador de almacenamiento en caché web para Adobe Commerce y Magento Open Source.

## Depuración de barniz

Según [Documentación de barniz](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *purgar* Esto es lo que sucede cuando se elige un objeto de la caché y se descarta junto con sus variantes&quot;. Una depuración de barniz es similar a un comando de limpieza de caché (o hacer clic en **Vaciar caché del Magento** en el Administrador).

De hecho, cuando se limpia, vacía o actualiza la caché de Commerce, Varnish también se depura.

Después de instalar y configurar Varnish para trabajar con Commerce, las siguientes acciones pueden resultar en una depuración de Varnish:

- Mantener un sitio web.

  Por ejemplo, cualquier cosa que haga en el Administrador de:

   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **General**
   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **Configuración de moneda**
   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **Almacenar direcciones de correo electrónico**

  Cuando Commerce detecta un cambio de este tipo, aparece un mensaje que le informa de que debe actualizar la caché.

- Mantener una tienda (por ejemplo, añadir o editar categorías, precios, productos y reglas de precios promocionales).

  El barniz se depura automáticamente cuando se realiza cualquiera de estas tareas.

- Mantener el código fuente.

  Debe actualizar la caché y también eliminar periódicamente todo lo que hay en la `generated/code` y `generated/metadata` directorios. Para obtener información sobre cómo actualizar la caché, consulte la siguiente sección.

## Configurar Commerce para depurar Varnish

Commerce purga los hosts de Varnish después de configurar los hosts de Varnish mediante el [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) comando.

Puede utilizar el parámetro opcional `--http-cache-hosts` para especificar una lista separada por comas de hosts de barniz y puertos de escucha. Configure todos los hosts de Varnish, independientemente de si tiene uno o varios. (No separe los hosts con caracteres de espacio.)

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

A continuación, puede purgar los hosts de Varnish al actualizar la caché de Commerce (también denominada *limpieza* la caché) en Admin o mediante la línea de comandos.

Para actualizar la caché con el administrador, haga clic en **[!UICONTROL SYSTEM]** > Herramientas > **Administración de caché**, luego haga clic en **Vaciar caché del Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché mediante la línea de comandos, normalmente se utiliza la variable [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como el [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
