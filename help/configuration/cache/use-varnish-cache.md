---
title: Limpieza de caché con barniz
description: Aprenda cómo funciona la limpieza de caché con Varnish y cómo utilizarla como acelerador de almacenamiento en caché web para la aplicación de Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Limpieza de caché con barniz

En este tema se tratan los conceptos básicos del uso de Varnish como acelerador de almacenamiento en caché web para Adobe Commerce.

## Depuración de barniz

Según la [documentación de Varnish](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;Una *depuración* es lo que sucede cuando se elige un objeto de la caché y se descarta junto con sus variantes&quot;. Una depuración de barniz es similar a un comando de limpieza de caché (o hacer clic en **Vaciar caché de Magento** en el administrador).

De hecho, cuando se limpia, vacía o actualiza la caché de Commerce, Varnish también se depura.

Una vez instalado y configurado el barniz para que funcione con Commerce, las siguientes acciones pueden dar como resultado una depuración de barniz:

- Mantener un sitio web.

  Por ejemplo, cualquier cosa que haga en el Administrador de:

   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **General**
   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **Configuración de moneda**
   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **Almacenar direcciones de correo electrónico**

  Cuando Commerce detecta un cambio de este tipo, aparece un mensaje que le informa de que debe actualizar la caché.

- Mantener una tienda (por ejemplo, añadir o editar categorías, precios, productos y reglas de precios promocionales).

  El barniz se depura automáticamente cuando se realiza cualquiera de estas tareas.

- Mantener el código fuente.

  Debe actualizar la caché y también eliminar periódicamente todo lo que se encuentre en los directorios `generated/code` y `generated/metadata`. Para obtener información sobre cómo actualizar la caché, consulte la siguiente sección.

## Configuración de Commerce para depurar Barniz

Commerce purga los hosts de Varnish después de configurar los hosts de Varnish mediante el comando [`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset).

Puede usar el parámetro opcional `--http-cache-hosts` para especificar una lista separada por comas de hosts de Barnish y puertos de escucha. Configure todos los hosts de Varnish, independientemente de si tiene uno o varios. (No separe los hosts con caracteres de espacio.)

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

A continuación, puede purgar los hosts de Varnish cuando actualice la caché de Commerce (también conocida como *limpieza* de la caché) en Admin o mediante la línea de comandos.

Para actualizar la caché con el Administrador, haga clic en **[!UICONTROL SYSTEM]** > Herramientas > **Administración de caché** y, a continuación, haga clic en **Vaciar la caché de Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché mediante la línea de comandos, normalmente se usa el comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
