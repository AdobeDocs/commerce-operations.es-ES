---
title: Notas de la versión de Adobe Commerce 2.4.7 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: e5f659cc3bee2d116222c15549fb3d6094644531
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.7

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.7-p1

La versión de seguridad de Adobe Commerce 2.4.7-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aspectos destacados de seguridad

* **Actualizar [configuración de contraseña de un solo uso (OTP)](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para Google Authenticator**-Esta actualización es necesaria para resolver un error introducido por un [cambio incompatible con versiones anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) en 2.4.7. La descripción de la **[!UICONTROL OTP Window]** ahora proporciona una explicación precisa de la configuración y el valor predeterminado se ha cambiado de `1` hasta `29`.

* **Compatibilidad de la versión B2B**—Para la compatibilidad con la versión 2.4.7-p1 de Commerce, los comerciantes que tengan la extensión Adobe Commerce B2B deben actualizar a [Versión 1.4.2-p1 de B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes#b2b-v142p1.html).

### Revisiones incluidas en esta versión

Adobe Commerce SOAP 2.4.7-p1 resuelve un problema que se introdujo en el ámbito de la migración de la integración de UPS de la API de REST a la API de. Este problema afectaba a los clientes que realizaban envíos fuera de los EE. UU. e impedía que utilizaran las mediciones del sistema métrico/SI de kilogramos y centímetros para los paquetes con el fin de crear envíos con UPS. Consulte la [SOAP Migración de la integración del método de envío UPS de la API de a la API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) artículo de la base de conocimientos para obtener más información.
