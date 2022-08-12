---
title: '"El [!UICONTROL Security] tab"'
description: Obtenga información sobre [!UICONTROL Security] pestaña [!DNL Observation for Adobe Commerce].
source-git-commit: 5e4babd14bb918db7f894b7ca6a0344a4652704c
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# La variable [!UICONTROL Security] ficha

La variable **[!UICONTROL Security]** explica los problemas de seguridad y aísla sus posibles causas. Además, se describen los marcos de la pestaña .

## [!UICONTROL API calls by IP, details by URL]

La variable **[!UICONTROL API calls by IP, details by URL]** frame muestra un número de llamadas de API por IP en un intervalo de tiempo seleccionado. Este marco muestra la dirección IP y la dirección URL de API a la que accedió esa dirección IP.

![Llamadas de API por IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

La variable **[!UICONTROL Forgot Password]** el marco de acceso muestra el número de intentos de contraseña olvidados en un intervalo de tiempo seleccionado. Una actividad alta contra una dirección IP puede ser un ataque en el sitio.

![Contraseña olvidada](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

La variable **[!UICONTROL Create Account access]** frame muestra el número de actividades de cuenta nuevas en un intervalo de tiempo seleccionado. Una actividad alta desde una sola dirección IP puede indicar un ataque.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

La variable **[!UICONTROL POST activities]** frame muestra las actividades del POST para el sitio, incluidas en client_ip desde el [!DNL Fastly] registros. También muestra la dirección URL a la que se accede mediante la dirección IP.

![POST-actividades](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

La variable **Tabla de resumen de actividades del POST** frame muestra las actividades de POST resumidas para el sitio, incluidas en client_ip desde el [!DNL Fastly] registros. También muestra el recuento de la dirección URL a la que se accede mediante la dirección IP. El recuento es para el intervalo de tiempo seleccionado.

![POST-actividades-resumen](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

La variable **[!UICONTROL POST activities details table]** frame muestra las actividades de POST para el sitio desde el [!DNL Fastly] registros. También muestra todos los detalles de la [!DNL Fastly] para estas solicitudes. Está limitado a las últimas 2000 solicitudes.
![POST-actividades-detalles](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

La variable **[!UICONTROL Guest Carts activities]** frame muestra el número de actividades del carro de compras de invitados en un intervalo de tiempo seleccionado, faceteado por la dirección IP y la dirección URL a la que se accedió. Los carros de invitados pueden utilizarse en un ataque de cardado. Este marco muestra el número total de solicitudes en las que se accede a las URL de los carros de invitados.

![carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

La variable **[!UICONTROL API – forgot password, create account by Countries]** muestra el número de cuentas creadas y las solicitudes para restablecer una contraseña olvidada en un intervalo de tiempo seleccionado. Se trata de mostrar también el país de origen de la solicitud. Este marco se centra en el país de origen de la solicitud.

![api-olvidé-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

La variable **[!UICONTROL API - forgot password, create account by Countries and IP address]** muestra el número de cuentas creadas y las solicitudes para restablecer una contraseña olvidada en un intervalo de tiempo seleccionado. Se muestra en facetas la dirección IP, la dirección URL a la que se accede y el país de origen de la solicitud. Este fotograma se centra en el recuento de IP.

![api-olvid-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

La variable **[!UICONTROL Guest cart activities by IP]** frame muestra las actividades del carro de compras por IP en un intervalo de tiempo seleccionado.

![Guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

La variable **[!UICONTROL Guest cart activities by Countries]** frame muestra las actividades del carro de invitados por países en un intervalo de tiempo seleccionado.

![estados del carro de compras](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
