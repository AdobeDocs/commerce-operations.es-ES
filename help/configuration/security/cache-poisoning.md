---
title: Evitar el envenenamiento de caché
description: Aprenda a evitar el envenenamiento de la caché de la página para su tienda de Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Evitar el envenenamiento de caché

En este tema se explica cómo evitar el envenenamiento de caché si utiliza el servidor web de Microsoft Internet Information Server (IIS). _Intoxicación de caché_ es un método para cambiar el contenido de la caché con el fin de incluir páginas diferentes del mismo sitio. Por ejemplo, es posible insertar una página de error HTTP 404 (no encontrada) en lugar de alguna página benigna (por ejemplo, la página principal de la tienda), lo que puede provocar una posible denegación de servicio (DoS). Varnish o Redis almacenan en caché las direcciones URL de páginas malintencionadas; de ahí el nombre _envenenamiento de caché de páginas_.

Estos tipos de ataques pueden ser difíciles de detectar porque no producen errores en los registros del servidor web.

Esta solución se aplica a las siguientes versiones de Commerce:

- 2.0.10 y posterior
- 2.1.2 y posterior

>[!INFO]
>
>Este tema está dirigido a administradores de IIS con experiencia.

## Descripción

El problema se produce si las reescrituras de URL están habilitadas en el servidor IIS y cualquiera de los siguientes encabezados HTTP se modifica antes de que la solicitud llegue al servicio de almacenamiento en caché de Varnish o Redis:

- `X-Rewrite-Url`
- `X-Original-Url`
- `IIS-wasurlrewritten`
- `Unencoded-URL`
- `Orig-path-info`

Si se cambian estos encabezados, la dirección URL y el contenido resultantes se almacenan en caché, lo que provoca posibles vulnerabilidades.

## Solución

Proporcionamos la opción de quitar los valores de todos los encabezados anteriores en función de la configuración del servidor IIS para `Enable_IIS_Rewrites`.

- Si `Enable_IIS_Rewrites` se establece en `0`, se quitan los valores de los encabezados.
- Si `Enable_IIS_Rewrites` se establece en `1`, los valores de los encabezados permanecen intactos.

>[!WARNING]
>
>Si establece `Enable_IIS_Rewrites` en `1`, no debe permitir que los valores de los encabezados anteriores se modifiquen antes de que la solicitud llegue al servidor web de IIS.
