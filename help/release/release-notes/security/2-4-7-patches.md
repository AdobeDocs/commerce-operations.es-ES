---
title: Notas de la versión de Adobe Commerce 2.4.7 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p5

La versión de seguridad de Adobe Systems Commerce 2.4.7-p5 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Características destacadas

Esta versión incorpora compatibilidad con la [extensión compatible con HIPAA](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) de Adobe Commerce.

## 2.4.7-p4

La versión de seguridad de Adobe Commerce 2.4.7-p4 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

La versión de seguridad de Adobe Commerce 2.4.7-p3 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Resúmenes

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Correcciones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2,4,7-p2

La versión de seguridad de Adobe Commerce 2.4.7-p2 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

La versión de seguridad de Adobe Commerce 2.4.7-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.7.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Resúmenes

Esta versión incluye los siguientes elementos destacados:

* **Actualizar la configuración de contraseña de un solo uso [OTP](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para Google Authenticator**: esta actualización es necesaria para resolver un error que se introdujo mediante un [cambio incompatible con versiones anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) en 2.4.7. La descripción del campo **[!UICONTROL OTP Window]** ahora proporciona una explicación precisa de la configuración y el valor predeterminado se ha cambiado de `1` a `29`.

* **Compatibilidad de la versión B2B**: para la compatibilidad con Commerce versión 2.4.7-p1, los comerciantes que tengan la extensión Adobe Commerce B2B deben actualizar a [B2B versión 1.4.2-p1](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.7-p1 resuelve un problema introducido en el ámbito de la migración de la integración de UPS de SOAP a la API de REST. Este problema afectaba a los clientes que realizaban envíos fuera de los EE. UU. e impedía que utilizaran las mediciones del sistema métrico/SI de kilogramos y centímetros para los paquetes con el fin de crear envíos con UPS. Consulte el artículo de la base de conocimiento [Migración del método de envío UPS de SOAP a la API RESTful](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) para obtener más detalles.
