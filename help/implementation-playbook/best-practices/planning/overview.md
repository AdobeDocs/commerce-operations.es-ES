---
title: Fase de planificación de implementación
description: Conozca las prácticas recomendadas de implementación para la fase de planificación de los proyectos de Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Fase de planificación

La fase de planificación incluye las siguientes actividades:

- Recopilación de requisitos
- Diseño arquitectónico
- Diseño de catálogo
- Ámbito del proyecto
- Aprovisionamiento de cuentas
- Acceso de usuario
- Adquisición de extensiones

Las secciones siguientes incluyen información sobre las prácticas recomendadas para la fase de planificación.

## Recopilación de requisitos

- **Configuración de aplicación**
   - [Prácticas recomendadas para configurar sitios, tiendas y vistas de tiendas (infraestructura en la nube)](sites-stores-store-views.md)
   - [Cómo evitar y corregir los cinco problemas de configuración más comunes para los sitios de Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Prácticas recomendadas para el almacenamiento en caché](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Almacenamiento en caché de página completa](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Tamaño de memoria de OPcache](opcache-memory-size.md)
   - [Configuración de informes](reporting-configuration.md)

- **Configuración de base de datos**
   - [Prácticas recomendadas de configuración de bases de datos para implementaciones en la nube&#x200B;](database-on-cloud.md)
   - [Configuración de MySQL&#x200B;](mysql-configuration.md)

- **Configuración de servicios**
   - [Configuración rápida](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic: Configuración de canales de notificación](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Prácticas recomendadas para la configuración del servicio Redis&#x200B;](redis-service-configuration.md)
   - [Práctica recomendada de tamaño de caché de Realpath](realpath-cache-size.md)

## **Diseño arquitectónico**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Explicación de la arquitectura de referencia global](../../../implementation-playbook/architecture/global-reference/overview.md)

## **Diseño de catálogo**

En los siguientes temas se describen las prácticas recomendadas de optimización del rendimiento para configurar su catálogo de Adobe Commerce, incluidos los máximos recomendados para el número de categorías, SKU efectivas del producto, variaciones de productos, atributos y opciones del producto, etc.

- [Configuración de categoría](catalog-management.md#category-limits)
- [Configuración del producto&#x200B;](catalog-management.md#product-sku-limits)
- [Configuración de variación del producto](catalog-management.md#product-variations)
- [Configuración de opciones de producto](catalog-management.md#product-options)
- [Configuración de atributos del producto&#x200B;](catalog-management.md#product-attributes)
- [Configuración de paginación para listados de productos](catalog-management.md#product-listing-pagination)

## **Ventas y marketing**

- [Prácticas recomendadas para límite del carro de productos](catalog-management.md#cart-limits)
- [Prácticas recomendadas para configurar promociones](catalog-management.md#promotions)

## **Ámbito del proyecto**

- [Escalaciones de Partner](partner-escalation.md)
- [Procesamiento de almacenamiento de pagos](payment-processing-storage.md)

## **Extensiones de compra**

- [Prácticas recomendadas para usar extensiones de terceros en Adobe Commerce](extensions.md)
