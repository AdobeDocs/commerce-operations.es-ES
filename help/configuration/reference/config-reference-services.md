---
title: Referencia de rutas de configuración de servicios
description: Consulte una lista de valores de configuración de servicios.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Referencia de rutas de configuración de servicios

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Admin en **Tiendas** > Configuración > **Configuración** > **Servicios**.

El [`magento app:config:dump` mando](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente. Para anular cualquier configuración de configuración o definir configuraciones confidenciales, consulte [Utilice variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables). Este tema sí _no_ lista [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de API web de Commerce

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Servicios** > **API web**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Conjunto de caracteres de respuesta predeterminado | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir acceso anónimo a invitados | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de OAuth

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Servicios** > **OAuth**.

| Nombre | Ruta de configuración | ¿Solo comercio? |
|--------------|--------------|--------------|
| Duración del token del cliente (horas) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del token de administrador (horas) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilidad de limpieza | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| credenciales de consumidor de OAuth HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de publicación HTTP de credenciales de consumidor de OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
