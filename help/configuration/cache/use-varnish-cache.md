---
title: Vaciado de caché con barniz
description: Aprenda cómo funciona la limpieza de caché con Varnish y cómo utilizarla como acelerador de almacenamiento en caché web para la aplicación de Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Limpieza de caché con barniz

En este tema se describen las bases para utilizar Varnish como acelerador de almacenamiento en caché web para Adobe Systems Commerce.

## Purga de barniz

Según la [documentación](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html) de Varnish, &quot;Una *purga* es lo que sucede cuando seleccionas un objeto de la caché y lo descartas junto con sus variantes&quot;. Una purga de barniz es similar a un comando de limpieza de caché (o a hacer clic **en Vaciar caché Magento** en el administrador).

De hecho, cuando limpia, limpia o actualiza la caché de Commerce, Varnish también se purga.

Después de haber instalado y configurado Varnish para trabajar con Commerce, las siguientes acciones pueden resultar en una purga de Barnish:

- Mantenimiento de un sitio web.

  Por ejemplo, todo lo que haga en la administración en:

   - **ALMACENA** > **Configuración** > **Configuración** > GENERAL > **General**
   - **STORES** > **Configuración** > **Configuración** > GENERAL > **Configuración de moneda**
   - **TIENDAS** > **Configuración** > **Configuración** > GENERAL > **Almacenar direcciones de correo electrónico**

  Cuando Comercio detecta un cambio de este tipo, se muestra un mensaje que informa que actualice la caché.

- Mantener un tienda (por ejemplo, agregar o editar categorías, precios, productos y reglas de precios promocionales).

  El barniz se purga automáticamente cuando se realiza cualquiera de estas tareas.

- Mantenimiento del código fuente.

  Debe actualizar la caché y también eliminar periódicamente todo en los `generated/code` directorios and `generated/metadata` . Para obtener información sobre cómo actualizar la memoria caché, consulte la siguiente sección.

## Configuración de comercio para depurar el barniz

Commerce purga los hosts de barniz después de configurar los hosts de barniz mediante el [`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset) comando.

Puede utilizar el parámetro opcional `--http-cache-hosts` para especificar una lista separada por comas de hosts y puertos de escucha de Varnish. Configure todos los hosts de Varnish, tanto si tiene uno como varios. (No separe los hosts con caracteres de espacio.)

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

A continuación, puede purgar los hosts de Barnish actualizando la caché de Commerce (también denominada *limpieza* de la caché) en el Administrador o mediante la línea de comandos.

Para actualizar la caché con el administrador, haga clic en **[!UICONTROL SYSTEM]** > Herramientas > **Administración** de caché y, a continuación, haga clic en **Vaciar caché Magento** en la parte superior del Página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché mediante la línea de comandos, normalmente se utiliza el [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando como propietario[&#128279;](../../installation/prerequisites/file-system/overview.md) el sistema de archivos.
