---
title: Notas de la versión de Adobe Commerce 2.4.7 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.7.
source-git-commit: 7705e750a466ab134ae2616a40a32880ee0c45de
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La versión de seguridad de Adobe Commerce 2.4.7-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

## Aspecto destacado de seguridad

Esta versión incluye una actualización de [configuración de contraseña de un solo uso (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para que Google Authenticator resuelva un error introducido por un [cambio incompatible con versiones anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) en 2.4.7. La descripción de la **[!UICONTROL OTP Window]** ahora proporciona una explicación precisa de la configuración y el valor predeterminado se ha cambiado de `1` hasta `29`.
