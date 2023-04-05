---
title: Evitar la intoxicación de la caché
description: Obtenga información sobre cómo evitar la intoxicación en la caché de la página para su tienda de comercio.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Evitar la intoxicación de la caché

En este tema se explica cómo evitar la intoxicación de la caché si utiliza el servidor web de Microsoft Internet Information Server (IIS). _Intoxicación de caché_ es un método para cambiar el contenido de la caché para incluir diferentes páginas del mismo sitio. Por ejemplo, es posible insertar una página de error HTTP 404 (no encontrado) en lugar de una página benigna (por ejemplo, la página principal de la tienda), que puede provocar una posible denegación de servicio (DoS). Las direcciones URL de páginas malintencionadas las almacena en caché Varnish o Redis, de ahí el nombre _envenenamiento de caché de página_.

Estos tipos de ataques pueden ser difíciles de detectar porque no dan lugar a errores en los registros del servidor web.

Esta solución se aplica a las siguientes versiones de Commerce:

- 2.0.10 y posteriores
- 2.1.2 y posteriores

>[!INFO]
>
>Este tema está pensado para administradores de IIS experimentados.

## Descripción

El problema se produce si las reescrituras de URL están habilitadas en el servidor IIS y cualquiera de los siguientes encabezados HTTP se modifica antes de que la solicitud llegue al servicio de almacenamiento en caché de Varnish o Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Si se cambian estos encabezados, la dirección URL y el contenido resultantes se almacenan en caché, lo que provoca posibles vulnerabilidades.

## Solución

Proporcionamos la opción de eliminar los valores de todos los encabezados anteriores basados en la configuración del servidor IIS para `Enable_IIS_Rewrites`.

- If `Enable_IIS_Rewrites` está configurado como `0`, se eliminan los valores de los encabezados.
- If `Enable_IIS_Rewrites` está configurado como `1`, los valores de los encabezados se dejan intactos.

>[!WARNING]
>
>Si configura `Enable_IIS_Rewrites` a `1`, no debe permitir que los valores de los encabezados anteriores se modifiquen antes de que la solicitud llegue al servidor web IIS.
