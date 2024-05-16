---
title: Notas de la versión de Adobe Commerce 2.4.2 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.2.
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Notas de la versión de los parches de seguridad de Adobe Commerce 2.4.2

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.2-p2

La versión de seguridad de Adobe Commerce 2.4.2-p2 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en la versión trimestral anterior, Adobe Commerce 2.4.2 y Magento Open Source 2.4.2.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html).

## Aplicar `AC-3022.patch` para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte la [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Artículo de Knowledge Base para obtener información sobre cómo descargar e instalar el parche.

