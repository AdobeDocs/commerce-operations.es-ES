---
title: Notas de la versión de Adobe Commerce 2.4.7 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.7.
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La versión de seguridad de Adobe Commerce 2.4.7-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aspecto destacado de seguridad

Esta versión incluye una actualización de [configuración de contraseña de un solo uso (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para que Google Authenticator resuelva un error introducido por un [cambio incompatible con versiones anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) en 2.4.7. La descripción de la **[!UICONTROL OTP Window]** ahora proporciona una explicación precisa de la configuración y el valor predeterminado se ha cambiado de `1` hasta `29`.

### Mejoras de seguridad adicionales

{{$include /help/_includes/release-notes/2-4-7-security.md}}

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.7-p1 resuelve un problema introducido en el ámbito de la migración de la integración de UPS de SOAP a la API de REST. Este problema afectaba a los clientes que realizaban envíos fuera de los EE. UU. e impedía que utilizaran las mediciones del sistema métrico/SI de kilogramos y centímetros para los paquetes con el fin de crear envíos con UPS. Consulte la [Migración de la integración del método de envío UPS de SOAP a la API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) artículo de la base de conocimientos para obtener más información.
