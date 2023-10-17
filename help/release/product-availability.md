---
title: Disponibilidad del producto
description: Obtenga información sobre las funciones de Adobe Commerce que se admiten actualmente y compruebe su compatibilidad con versiones específicas de Adobe Commerce.
exl-id: 7e8e8ac2-a0b9-4023-a813-c0f1293e54c2
source-git-commit: df4a4b419fbd5780a98e062a12cb22c3bc9913a0
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 13%

---

# Disponibilidad del producto

En la tabla siguiente se describe el estado de disponibilidad del software de Adobe Commerce y dónde obtenerlo, especialmente para el software disponible fuera del paquete convencional de Adobe Commerce Composer.

Los servicios y las extensiones se prueban en la última versión de Commerce en el momento del lanzamiento de los productos.

El Adobe ha probado completamente las versiones compatibles. La asistencia para las versiones compatibles está disponible en Asistencia al cliente de Adobe. Las versiones anteriores pueden funcionar correctamente, pero no son compatibles oficialmente.

>[!NOTE]
>
>La compatibilidad con versiones de Adobe Commerce también incluye compatibilidad con [parches de seguridad disponibles](versions.md).

## Extensiones creadas por Adobe

Estas extensiones de Adobe Commerce están disociadas del código base principal de Adobe Commerce. Esto permite al Adobe lanzar iteraciones de estas extensiones en un periodo de tiempo más flexible y proporcionar a los clientes un acceso más rápido a las nuevas funciones.


En la tabla siguiente se muestra la compatibilidad con las versiones de cada extensión en relación con la versión de Adobe Commerce.

| **Versiones de Adobe Commerce** | 2.4.7-beta2 | 2.4.6 | 2.4.5 | 2.4.4 |                                                                                                                                                                                                                                          |
|---------------------------------------|-------------|--------|--------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Eventos de Adobe I/O para Adobe Commerce_ | 1.3.0 | 1.3.0 | 1.3.0 | 1.3.0 | [Compositor](https://developer.adobe.com/commerce/extensibility/events/installation/) <br/>[Notas de versión](https://developer.adobe.com/commerce/extensibility/events/release-notes/) |
| _B2B_ | 1.4.2 | 1.3.5+ | 1.3.4 | 1.3.3 | [Compositor](https://experienceleague.adobe.com/docs/commerce-admin/b2b/install.html) <br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html) |
| _Conector del Experience Platform_ | 3.0.0-beta1 | 1.0.0+ | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)<br/>[Notas de versión](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/release-notes.html) |
| _Page Builder_ | - | 1.7.3 | 1.7.2 | 1.7.1 | [Guía del usuario](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/guide-overview.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/release-notes.html) |

## Servicios de Commerce

[Servicios de Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) son un conjunto de funciones alojadas en el Adobe que proporcionan una funcionalidad sólida y tiempos de respuesta rápidos, junto con su instancia de Commerce.

Se recomienda que los comerciantes utilicen la versión más reciente de un servicio para garantizar la máxima estabilidad y funcionalidad. La documentación describe la versión lanzada actualmente.

* Actualmente, los servicios de Adobe Commerce son compatibles con Commerce 2.4.4 y versiones posteriores. Se recomienda que los comerciantes utilicen la última versión del servicio.
* Los servicios se consideran compatibles con versiones anteriores de Commerce 2.4.x, pero no son compatibles oficialmente.
* Los servicios no son compatibles con Commerce 2.3.x, excepto con Product Recommendations 3.3.7 y versiones anteriores.

La siguiente tabla muestra la compatibilidad con la versión de cada servicio en relación con la versión de Adobe Commerce.

| **Versiones de Adobe Commerce** | 2.4.7-beta2 | 2.4.6 | 2.4.5 | 2.4.4 |                                                                                                                                                                                                                                                |
|----------------------------------------|-------------|--------|-----------------|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| _Sales Channel de Amazon_ | - | 4.4.0+ | 4.3.0+ | 4.3.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-module-amazon.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-channels/amazon/release-notes.html) |
| _Servicio de catálogo para Adobe Commerce_ | 1.13 | 1.13 | 1.13 | 1.13 | [Información general](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/guide-overview.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-merchant-services/catalog-service/release-notes.html) |
| _Administrador de canales_ | 2.1.0 | 2.0.0 | 1.0.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-channel-manager.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/release-notes.html) |
| _Live Search_ | 3.1.1 | 3.1.1 | 3.1.1 | 3.1.1 | [Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)<br/>[Notas de versión](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html) |
| _Servicios de pago_ | 2.2.0 | 2.2.0 | 2.2.0 (PHP 8.1) | 2.2.0 (PHP 8.1) | [Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html)<br/> [Notas de la versión](https://commercemarketplace.adobe.com/magento-payment-services.html) |
| _Product Recommendations_ | 5.0.1 | 5.0.1 | 5.0 .1 | 5.0.1 | [Marketplace](https://commercemarketplace.adobe.com/magento-product-recommendations.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Cierre de compra rápido_ | - | 1.0.0+ | 1.2.0+ | 1.0.0+ | [Marketplace](https://commercemarketplace.adobe.com/magento-quick-checkout.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/release-notes.html) |
| _Gestión de tienda para Adobe Commerce_ | - | 1.5.0 | 1.2.0+ | 1.2.0+ | [Marketplace](https://commercemarketplace.adobe.com/store-fulfillment-magento-walmart.html)<br/> [Notas de la versión](https://experienceleague.adobe.com/docs/commerce-merchant-services/store-fulfillment/release-notes.html) |
