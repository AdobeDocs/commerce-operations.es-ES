---
title: Notas de la versión de Adobe Commerce 2.4.8 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: c297996273c42481fe9d3ee20ec3b9256e27fb5f
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p4

La versión de seguridad de Adobe Commerce 2.4.8-p4 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.8.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB26-05](https://helpx.adobe.com/es/security/products/magento/apsb26-05.html).

{{b2b-patches}}

### Características destacadas

Esta versión incluye los siguientes aspectos destacados:

#### Compatibilidad con la API REST de MyDHL para la integración de envíos DHL

La integración de envíos de DHL ahora admite las API de REST de MyDHL además de la integración XML de DHL Express existente. Esta actualización se alinea con la pila actual de API de DHL y se prepara para la obsolescencia de las API XML más antiguas.

#### Añada compatibilidad con la última versión de Composer

Adobe Commerce 2.4.8 se ha actualizado para admitir Composer 2.9.x, pero seguirá siendo compatible con Composer 2.2 LTS.

## 2,4,8-p3

La versión de seguridad de Adobe Commerce 2.4.8-p3 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.8.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-94](https://helpx.adobe.com/es/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### Características destacadas

Esta versión incluye los siguientes aspectos destacados:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* Corrección para ACP2E-3874: La respuesta de la API de REST para los detalles del pedido ahora contiene valores correctos para los atributos `base_row_total` y `row_total` en caso de que se hayan pedido varios artículos iguales.

* Corrección para AC-15446: se corrigió un error en `Magento\Framework\Mail\EmailMessage` en el que `getBodyText()` intentó llamar a un método `getTextBody()` inexistente en `Symfony\Component\Mime\Message`, lo que garantiza la compatibilidad con Magento 2.4.8-p2 y `magento/framework` 103.0.8-p2.

{{oct-2025-backports}}

### Problemas conocidos

#### La página Checkout no puede cargar static.min.js y mixins.min.js

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2,4,8-p2

La versión de seguridad de Adobe Commerce 2.4.8-p2 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.8.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-71](https://helpx.adobe.com/es/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2,4,8-p1

La versión de seguridad de Adobe Commerce 2.4.8-p1 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.8.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-50](https://helpx.adobe.com/es/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Características destacadas

Esta versión incluye los siguientes aspectos destacados:

* **Mejora del rendimiento de la API**: resuelve la degradación del rendimiento en los extremos de API web asincrónicos masivos que se introdujeron después de la revisión de seguridad anterior.<!-- AC-14078 -->

* **Corrección de acceso de bloques de CMS**: resuelve un problema en el cual los usuarios administradores con permisos restringidos (como acceso de solo comercialización) no podían ver la página de listado [!UICONTROL CMS Blocks].

  Anteriormente, estos usuarios encontraban un error debido a la falta de parámetros de configuración después de instalar las revisiones de seguridad anteriores.<!-- AC-14087 -->

* **Compatibilidad con límites de cookies**: resuelve un cambio incompatible con versiones anteriores que implica la constante `MAX_NUM_COOKIES` en el marco de trabajo. Esta actualización restaura el comportamiento esperado y garantiza la compatibilidad de las extensiones o personalizaciones que interactúan con los límites de las cookies.<!-- AC-14475 -->

* **Operaciones asincrónicas**: operaciones asincrónicas restringidas para anular pedidos de clientes anteriores.<!-- AC-13917 -->

* **Corrección para CVE-2025-47110**: resuelve una vulnerabilidad de las plantillas de correo electrónico.<!-- AC-14695 -->

* **Corrección para VULN-31547**: resuelve una vulnerabilidad de vínculo canónico de categoría.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Las correcciones para CVE-2025-47110 y VULN-31547 también están disponibles como parche aislado. Consulte el [artículo de la Base de conocimiento](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) para obtener detalles.

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-02-20 15:30:03 -->
