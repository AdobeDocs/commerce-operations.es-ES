---
title: Opciones de integración de Adobe Commerce
description: Explore las opciones para integrar otros sistemas con su implementación de Adobe Commerce.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Puntos de integración típicos y flujos de datos

Existen dos enfoques principales para las integraciones y los flujos de datos, que son muy similares pero tienen una diferencia clave.

## Monolítico

En el diagrama siguiente se describe un enfoque monolítico que utiliza Adobe Commerce como sistema back-end y aplicación de tienda:

![Diagrama de monolito de Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Sin encabezado

En el diagrama siguiente se describe un método sin encabezado que utiliza Adobe Commerce como sistema back-end integrado con una aplicación DXP/CMS/custom como aplicación de tienda:

![Diagrama sin encabezado de Adobe Commerce](../../assets/playbooks/integration-headless.svg)

La única diferencia entre el enfoque monolítico y el enfoque remoto es la integración de tienda, que afecta a la experiencia del usuario para los clientes. Monolithic utiliza la tienda de Adobe Commerce directamente para integrarse con los servicios de terceros, mientras que headless depende de su propia tienda para personalizar e integrar con los mismos servicios. Algunos servicios, como el pago y el inicio de sesión único (SSO), necesitan personalización de tienda y Adobe Commerce para finalizar el flujo de integración.

## Sistemas de terceros

Algunos servicios populares ya tienen buenas extensiones para admitir Adobe Commerce o soluciones de tienda populares, como PWA Studio, Adobe Experience Manager y Tienda de valores, que se pueden encontrar desde su mercado de extensiones o desde sitios web de terceros relacionados. Incluso si no existe ninguna extensión, el esfuerzo para implementar la integración entre Adobe Commerce y otras tiendas sin periféricos es similar. Por lo general, todos los servicios de terceros tienen documentos que explican cómo integrarse con ellos. Esos servicios son sólo algunos ejemplos; diversos países y mercados pueden tener diferentes opciones.

## Integraciones empresariales

Para las integraciones de sistemas empresariales, que también se denominan integraciones back-end, existe un impacto en el flujo de datos del negocio. En función de diferentes tipos de negocio y necesidades, puede utilizar tres opciones de integración diferentes, que ya hemos introducido.

Los datos obligatorios para el producto, como SKU, inventario y precios básicos, normalmente provienen de ERP, mientras que los precios de venta normalmente son administrados por cada canal de ventas (por ejemplo, Adobe Commerce) o CPQ (B2B o ventas privadas). Debido a que los datos obligatorios del producto (excepto el inventario) no cambian muy a menudo, se recomienda utilizar actualizaciones por lotes programadas mediante la API de REST o la importación de archivos por lotes. En el caso de los inventarios, se recomienda disponer de una actualización completa diaria del inventario de productos que se comparte con distintos canales de ventas para evitar ventas excesivas. Además, tenga los cambios incrementales de su ERP programados en un plazo de 24 horas.

El catálogo de productos, los metadatos y el contenido de marketing se pueden administrar por separado en cada canal de ventas (por ejemplo, Adobe Commerce) o desde un PIM central. Como los metadatos tampoco cambian con frecuencia, se recomienda utilizar actualizaciones por lotes programadas mediante la API de REST o la importación de archivos por lotes.

Los datos de pedidos incluyen pedidos, presupuestos (B2B), envíos, devoluciones e intercambios de datos que normalmente se administran desde un sistema OMS y WMS centralizado. Los datos de pedido deben sincronizarse lo antes posible, por lo que la API de REST suele ser la mejor opción. Para obtener un mejor rendimiento, considere la posibilidad de reducir el número de llamadas de API. Para el estado del pedido, los envíos, la devolución y el intercambio de datos, considere la posibilidad de programar las API de actualización por lotes de REST en horas o minutos.

Los datos B2B generalmente se administran desde un CRM centralizado. Se utiliza una API en tiempo real para verificar clientes existentes y crear clientes nuevos. Para B2B, puede requerir la introducción de más API para sincronizar diferentes empleados, grupos y listas de precios de la empresa entre Adobe Commerce y su CRM o CPQ.

Existen otras integraciones de sistema, como eDM para marketing por correo electrónico e inteligencia empresarial para análisis de datos empresariales, que normalmente se realizan mediante la API de REST o exportación/importación de archivos, que normalmente son compatibles con las extensiones existentes.
