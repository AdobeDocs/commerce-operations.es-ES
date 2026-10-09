---
title: Evitar el envenenamiento de caché
description: Aprenda a evitar el envenenamiento de la caché de la página para su tienda de Commerce.
feature: Configuration, Cache, Security
exl-id: 947024dd-d59d-480d-bb6c-8e0065054bb6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
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
