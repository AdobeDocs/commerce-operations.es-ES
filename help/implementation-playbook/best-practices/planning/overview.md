---
title: Fase de planificación de la implementación
description: Obtenga información sobre las prácticas recomendadas de implementación para la fase de planificación de proyectos de Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Fase de planificación

La fase de planificación incluye las siguientes actividades:

- Recopilación de requisitos
- Diseño arquitectónico
- Diseño del catálogo
- Creación de ámbitos del proyecto
- Aprovisionamiento de cuentas
- Acceso de usuario
- Compra de extensiones

Las secciones siguientes incluyen información sobre las prácticas recomendadas para la fase de planificación.

## Recopilación de requisitos

- **Configuración de la aplicación**
   - [Prácticas recomendadas para configurar sitios, tiendas y vistas de tiendas (infraestructura de nube)](sites-stores-store-views.md)
   - [Cómo evitar (y corregir) los cinco problemas de configuración más comunes para los sitios de Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Prácticas recomendadas para el almacenamiento en caché](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Almacenamiento en caché de página completa](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Tamaño de memoria OPcache](opcache-memory-size.md)
   - [Configuración de informes](reporting-configuration.md)

- **Configuración de la base de datos**
   - [Prácticas recomendadas en la configuración de bases de datos para implementaciones en la nube &#x200B;](database-on-cloud.md)
   - [Configuración de conexión esclava de MySQL &#x200B;](configure-mysql-slave-connection-on-cloud.md)
   - [Uso de déclencheur MySQL](mysql-triggers-usage.md)

- **Configuración de servicios**
   - [Configuración rápida](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [Nueva relación: Configurar canales de notificación](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Prácticas recomendadas para la configuración de servicios de Redis &#x200B;](redis-service-configuration.md)
   - [Práctica recomendada de tamaño de caché de Realpath](realpath-cache-size.md)

## **Diseño arquitectónico**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Explicación de la arquitectura de referencia global](../../../implementation-playbook/architecture/global-reference.md)

## **Diseño del catálogo**

Los siguientes temas describen las prácticas recomendadas de optimización del rendimiento para configurar su catálogo de Adobe Commerce, incluidos los máximos recomendados para el número de categorías, los SKU efectivos del producto, las variaciones de productos, los atributos y las opciones de productos, etc.

- [Configuración de categoría](category-limits.md)
- [&#x200B; de configuración del producto](product-sku-limits.md)
- [Configuración de la variación del producto](product-variations.md)
- [Configuración de opciones de producto](product-options.md)
- [&#x200B; de configuración de atributos de producto](product-attributes-and-options.md)
- [Configuración de paginación para listas de productos](product-listing-pagination.md)

## **Ventas y mercadotecnia**

- [Prácticas recomendadas para limitar el carro de &#x200B;](product-cart.md)
- [Prácticas recomendadas para configurar promociones](product-cart-promotions.md)

## **Creación de ámbitos del proyecto**

- [Escalaciones de socios](partner-escalation.md)

## **Extensiones de compra**

- [Prácticas recomendadas para usar extensiones de terceros en Adobe Commerce &#x200B;](extensions.md)
