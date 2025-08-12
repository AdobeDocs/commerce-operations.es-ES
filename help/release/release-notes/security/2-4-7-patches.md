---
title: Notas de la versión de Adobe Commerce 2.4.7 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.7.
exl-id: 38e5632b-c795-47d8-89dd-26bbaeb34e67
source-git-commit: a5cdc9ee2d8c8632c40e0ced62182d5275b8b942
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.7

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.7-p7

La versión de seguridad de Adobe Commerce 2.4.7-p7 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.7-p6

La versión de seguridad de Adobe Commerce 2.4.7-p6 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-50](https://helpx.adobe.com/es/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Características destacadas

Esta versión incluye los siguientes aspectos destacados:

* **Compatibilidad con MariaDB**—Se ha agregado compatibilidad con MariaDB 10.11.

* **Mejora del rendimiento de la API**: resuelve la degradación del rendimiento en los extremos de API web asincrónicos masivos que se introdujeron después de la revisión de seguridad anterior.<!-- AC-14078 -->

* **Corrección de acceso de bloques de CMS**: resuelve un problema en el cual los usuarios administradores con permisos restringidos (como acceso de solo comercialización) no podían ver la página de listado [!UICONTROL CMS Blocks].

  Anteriormente, estos usuarios encontraban un error debido a la falta de parámetros de configuración después de instalar las revisiones de seguridad anteriores.<!-- AC-14087 -->

* **Compatibilidad con límites de cookies**: resuelve un cambio incompatible con versiones anteriores que implica la constante `MAX_NUM_COOKIES` en el marco de trabajo. Esta actualización restaura el comportamiento esperado y garantiza la compatibilidad de las extensiones o personalizaciones que interactúan con los límites de las cookies.<!-- AC-14475 -->

* **Operaciones asincrónicas**: operaciones asincrónicas restringidas para anular pedidos de clientes anteriores.<!-- AC-13917 -->

## 2.4.7-p5

La versión de seguridad de Adobe Commerce 2.4.7-p5 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-26](https://helpx.adobe.com/es/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

>[!BEGINSHADEBOX]

Esta versión también presenta compatibilidad con la [extensión compatible con HIPAA](https://experienceleague.adobe.com/es/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) de Adobe Commerce.

>[!ENDSHADEBOX]

### Problemas conocidos

**Problema**: al instalar 2.4.7-p5 con PHP 8.2 o superior, el sistema instala `paypal/module-braintree` versión 4.7.0, que está destinada a 2.4.8 y versiones posteriores. Para PHP 8.1, se utiliza la versión correcta de Braintree 4.6.1-p5. Esta discrepancia se debe a la dependencia holgada de `adobe-commerce/extensions-metapackage: ~2.0` en el metapaquete. Esto afecta a la compatibilidad y al conjunto de características compatibles para implementaciones de PHP 8.2+.<!-- ACPLTSRV-6276) -->

Además, para las versiones 2.4.7-p3, 2.4.7-p4 y 2.4.7-p5, puede estar instalada la extensión de Braintree versión 4.6.1-p5, mientras que algunos usuarios esperan 4.6.1-p3 o p4, debido a que las dependencias anteriores más estrictas se han relajado para permitir actualizaciones de extensión dentro de una línea de versión. <!-- AC-14430 -->

**Solución alternativa**: Para asegurarse de que dispone de la versión de Braintree correcta para su versión de PHP, ejecute `composer update` para instalar la versión adecuada según lo dictado por la dependencia `adobe-commerce/extensions-metapackage:2.0.0`.

## 2.4.7-p4

La versión de seguridad de Adobe Commerce 2.4.7-p4 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-08](https://helpx.adobe.com/es/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.7-p3

La versión de seguridad de Adobe Commerce 2.4.7-p3 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-73](https://helpx.adobe.com/es/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2,4,7-p2

La versión de seguridad de Adobe Commerce 2.4.7-p2 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-61](https://helpx.adobe.com/es/security/products/magento/apsb24-61.html).

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.7-p1

La versión de seguridad de Adobe Commerce 2.4.7-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.7.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-40](https://helpx.adobe.com/es/security/products/magento/apsb24-40.html).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Características destacadas

Esta versión incluye los siguientes aspectos destacados:

* **Actualizar la configuración de contraseña de un solo uso [OTP](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication#google) para Google Authenticator**: esta actualización es necesaria para resolver un error que se introdujo mediante un [cambio incompatible con versiones anteriores](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value) en 2.4.7. La descripción del campo **[!UICONTROL OTP Window]** ahora proporciona una explicación precisa de la configuración y el valor predeterminado se ha cambiado de `1` a `29`.

* **Compatibilidad de la versión B2B**: para la compatibilidad con Commerce versión 2.4.7-p1, los comerciantes que tengan la extensión Adobe Commerce B2B deben actualizar a [B2B versión 1.4.2-p1](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.7-p1 resuelve un problema introducido en el ámbito de la migración de la integración de UPS de SOAP a la API de REST. Este problema afectaba a los clientes que realizaban envíos fuera de los EE. UU. e impedía que utilizaran las mediciones del sistema métrico/SI de kilogramos y centímetros para los paquetes con el fin de crear envíos con UPS. Consulte el artículo de la base de conocimiento [Migración del método de envío UPS de SOAP a la API RESTful](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/ups-shipping-method-integration-migration-from-soap-to-restful-api) para obtener más detalles.
