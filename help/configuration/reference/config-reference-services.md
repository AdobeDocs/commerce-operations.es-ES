---
title: Referencia de rutas de configuración de servicios
description: Consulte una lista de valores de configuración de servicios.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Referencia de rutas de configuración de servicios

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones de Administración en **Almacenes** > Configuración > **Configuración** > **Servicios**.

La variable [`magento app:config:dump` command](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartido, `app/etc/config.php`, que debería estar en el control de código fuente. Para anular, opcionalmente, cualquier configuración o definir ajustes confidenciales, consulte [Usar variables de entorno para anular los ajustes de configuración](override-config-settings.md#environment-variables). Este tema sí _not_ list [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de API web de comercio

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Servicios** > **API web**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Conjunto de caracteres de respuesta predeterminado | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir acceso de invitado anónimo | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Rutas OAuth

Estos valores de configuración están disponibles en Administración en **Almacenes** > Configuración > **Configuración** > **Servicios** > **OAuth**.

| Nombre | Ruta de configuración | ¿Sólo comercio? |
|--------------|--------------|--------------|
| Duración del token del cliente (horas) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del token de administrador (horas) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilidad de limpieza | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credenciales de consumidor de OAuth Máximos redireccionamientos HTTP Post | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credenciales de consumidor de OAuth Tiempo de espera de HTTP Post | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
