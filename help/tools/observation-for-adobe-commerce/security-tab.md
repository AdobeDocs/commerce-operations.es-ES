---
title: La ficha [!UICONTROL Security]
description: Obtenga información acerca de la ficha [!UICONTROL Security] de [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
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
source-wordcount: '403'
ht-degree: 0%
---
# La ficha [!UICONTROL Security]

La ficha **[!UICONTROL Security]** explica los problemas de seguridad y aísla sus posibles causas. Además, se describen los marcos de la pestaña.

## [!UICONTROL API calls by IP, details by URL]

El fotograma **[!UICONTROL API calls by IP, details by URL]** muestra un número de llamadas de API por dirección IP en un intervalo de tiempo seleccionado. Este marco muestra la dirección IP y la URL de API a la que accedió esa dirección IP.

![llamadas API por dirección IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

El marco de acceso **[!UICONTROL Forgot Password]** muestra el número de intentos de contraseña olvidada en un intervalo de tiempo seleccionado. Una actividad alta contra una dirección IP puede ser un ataque al sitio.

![Olvidé la contraseña](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

El marco **[!UICONTROL Create Account access]** muestra el número de nuevas actividades de cuenta en un intervalo de tiempo seleccionado. Una alta actividad desde una sola dirección IP puede indicar un ataque.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

El marco **[!UICONTROL POST activities]** muestra las actividades `POST` para el sitio, con facetas en `client_ip` de los registros [!DNL Fastly]. También muestra la dirección URL a la que accede la dirección IP.

![actividades POST](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

El marco **[!UICONTROL POST activities summary table]** muestra las actividades `POST` resumidas para el sitio, con facetas en `client_ip` de los registros [!DNL Fastly]. También muestra el recuento de la dirección URL a la que accede la dirección IP. El recuento es para el periodo de tiempo seleccionado.

![Resumen de actividades de PUBLICACIÓN](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

El marco **[!UICONTROL POST activities details table]** muestra las actividades `POST` para el sitio desde los registros [!DNL Fastly]. También muestra todos los detalles del registro [!DNL Fastly] para estas solicitudes. Se limita a las últimas 2000 solicitudes.
![detalles de actividades de PUBLICACIÓN](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

El fotograma **[!UICONTROL Guest Carts activities]** muestra el número de actividades del carro de compras de invitados en un intervalo de tiempo seleccionado, faceteadas por dirección IP y dirección URL a la que se accedió. Los carros de invitados se pueden usar en un ataque de carding. Este marco muestra el número total de solicitudes en las que se accede a las direcciones URL de los carros de invitados.

![actividades-carritos-invitados](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

El marco **[!UICONTROL API – forgot password, create account by Countries]** muestra el número de cuentas creadas y solicita restablecer una contraseña olvidada en un intervalo de tiempo seleccionado. Se incluye una faceta para mostrar también el país de origen de la solicitud. Este marco se centra en el país de origen de la solicitud.

![países-olvidados-api](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

El marco **[!UICONTROL API - forgot password, create account by Countries and IP address]** muestra el número de cuentas creadas y solicita restablecer una contraseña olvidada en un intervalo de tiempo seleccionado. Incluye una faceta para mostrar la dirección IP, la dirección URL a la que se accede y el país de origen de la solicitud. Este fotograma se centra en el recuento de direcciones IP.

![api-olvides-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

El fotograma **[!UICONTROL Guest cart activities by IP]** muestra las actividades del carro de compras de los invitados por dirección IP en un intervalo de tiempo seleccionado.

![ip-carro-de-invitados](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

El fotograma **[!UICONTROL Guest cart activities by Countries]** muestra las actividades del carro de compras de los invitados por países en un intervalo de tiempo seleccionado.

![país-carro-de-invitados](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
