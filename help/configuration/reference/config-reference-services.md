---
title: Referencia de rutas de configuración de servicios
description: Obtenga información sobre las rutas y los valores de configuración de servicios en la configuración de administración de Adobe Commerce. Descubra las opciones de configuración de API web, OAuth e integración de servicios.
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
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
source-wordcount: '171'
ht-degree: 1%
---
# Referencia de rutas de configuración de servicios

Esta sección enumera los nombres de las variables y las rutas de configuración disponibles para las opciones del Administrador en **Tiendas** > Configuración > **Configuración** > **Servicios**.

El comando [`magento app:config:dump` &#x200B;](../cli/export-configuration.md) escribe estos valores en el archivo de configuración compartida, `app/etc/config.php`, que debe estar en el control de código fuente. Para anular opcionalmente las opciones de configuración o establecer opciones confidenciales, vea [Usar variables de entorno para anular las opciones de configuración](override-config-settings.md#environment-variables). Este tema _no_ enumera [valores confidenciales y específicos del sistema](config-reference-sens.md).

## Rutas de API web de Commerce

Estos valores de configuración están disponibles en el Administrador de **Tiendas** > Configuración > **Configuración** > **Servicios** > **API web**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Conjunto de caracteres de respuesta predeterminado | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permitir acceso anónimo a invitados | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Rutas de OAuth

Estos valores de configuración están disponibles en el Administrador en **Tiendas** > Configuración > **Configuración** > **Servicios** > **OAuth**.

| Nombre | Ruta de configuración | ¿Solo Commerce? |
|--------------|--------------|--------------|
| Duración del token del cliente (horas) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Duración del token de administrador (horas) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilidad de limpieza | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Período de caducidad | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| credenciales de consumidor de OAuth HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tiempo de espera de publicación HTTP de credenciales de consumidor de OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
