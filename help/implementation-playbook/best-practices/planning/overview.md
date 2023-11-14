---
title: Fase de planificación de implementación
description: Conozca las prácticas recomendadas de implementación para la fase de planificación de los proyectos de Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# Fase de planificación

La fase de planificación incluye las siguientes actividades:

- Diseño arquitectónico
- Diseño de catálogo
- Adquisición de extensiones
- Ámbito del proyecto
- Recopilación de requisitos
- Ventas y marketing

Las secciones siguientes incluyen información sobre las prácticas recomendadas para la fase de planificación.

## Recopilación de requisitos

<table>
<thead>
  <tr>
    <th>Práctica recomendada</th>
    <th>Descripción</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Configuración de aplicación</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Configurar sitios, tiendas y vistas de tiendas</a></td>
    <td>Configure sitios, tiendas y vistas de tiendas para maximizar el rendimiento del sitio.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Problemas comunes de configuración</a></td>
    <td>Corrija y evite los cinco problemas de configuración más comunes para los sitios de Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Almacenamiento en caché</a></td>
    <td>Utilice las herramientas de administración de caché para mejorar el rendimiento del sitio.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Almacenamiento en caché de página completa</a></td>
    <td>Obtenga información sobre cómo trabajar con datos públicos al implementar el almacenamiento en caché en la extensión de Adobe Commerce o Magento Open Source.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">Tamaño de memoria de OPcache</a></td>
    <td>Evite la degradación del rendimiento con configuraciones específicas del consumo de memoria de la caché de OP.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Configuración de informes</a></td>
    <td>Optimice el rendimiento del sitio eliminando el módulo de creación de informes si no lo está utilizando.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuración de base de datos</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Configurar la base de datos para implementaciones en la nube</a></td>
    <td>Configure las opciones de la base de datos y la aplicación para mejorar el rendimiento al implementar Adobe Commerce en proyectos de infraestructura en la nube.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Configurar MySQL</a></td>
    <td>Aprenda cómo los déclencheur MySQL y las conexiones esclavas afectan el rendimiento del sitio y cómo utilizarlos de forma eficaz.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configuración de servicios</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Configuración rápida</a></td>
    <td>Configure los servicios de Fastly para su proyecto de Adobe Commerce en la nube.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Configuración de canales de notificación para New Relic</a></td>
    <td>Acceda a su tablero de New Relic y analice los datos de su proyecto de Adobe Commerce en la nube.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Configurar Redis</a></td>
    <td>Mejore el rendimiento del almacenamiento en caché utilizando la implementación de caché de Redis extendida para Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Tamaño de caché de RealPath</a></td>
    <td>Optimice el rendimiento actualizando la configuración de caché "readlpath" de PHP para usar la configuración recomendada.</td>
  </tr>
</tbody>
</table>

## Diseño arquitectónico

| Práctica recomendada | Descripción |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [Arquitectura de referencia global (GRA)](../../architecture/global-reference/examples.md) | Comprender los métodos comunes para organizar una base de código GRA. |

## Diseño de catálogo

| Práctica recomendada | Descripción |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Configuración de categoría](catalog-management.md#category-limits) | Configure categorías de productos para obtener un rendimiento óptimo. |
| [Configuración del producto&#x200B;](catalog-management.md#product-sku-limits) | Configure las SKU de los productos para obtener un rendimiento óptimo. |
| [Configuración de variación del producto](catalog-management.md#product-variations) | Configure las variaciones de productos para obtener un rendimiento óptimo. |
| [Configuración de opciones de producto](catalog-management.md#product-options) | Configure las opciones del producto para obtener un rendimiento óptimo. |
| [Configuración de atributos del producto&#x200B;](catalog-management.md#product-attributes) | Configure los atributos del producto para obtener un rendimiento óptimo. |
| [Configuración de paginación para listados de productos](catalog-management.md#product-listing-pagination) | Configure la paginación de la lista de productos para obtener un rendimiento óptimo. |

## Extensiones

| Práctica recomendada | Descripción |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Uso de extensiones de terceros en Adobe Commerce](extensions.md) | Obtenga información sobre cómo evitar problemas de rendimiento causados por extensiones de Adobe Commerce de terceros. |

## Ámbito del proyecto

| Práctica recomendada | Descripción |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Escalaciones de Partner](partner-escalation.md) | Prepárese para escalar un problema con un socio con un equipo de cuenta de Adobe o aprenda a evitar una escalación. |
| [Procesamiento de almacenamiento de pagos](payment-processing-storage.md) | Procese y almacene los datos de pago de forma segura. |

## Ventas y marketing

| Práctica recomendada | Descripción |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Límites del carro de productos](catalog-management.md#cart-limits) | Administre los límites del carro de compras para obtener un rendimiento óptimo. |
| [Configuración de promociones](catalog-management.md#promotions) | Configurar ventas y promociones de artículos en un carro de compras. |
