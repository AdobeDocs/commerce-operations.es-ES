---
title: Opciones de integración de Adobe Commerce
description: Explore sus opciones para integrar otros sistemas con la implementación de Adobe Commerce.
exl-id: 10de70d2-ff3b-4f10-b370-01d805b745dc
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Puntos de integración y flujos de datos habituales

Existen dos enfoques principales para las integraciones y los flujos de datos, que son muy similares, pero tienen una diferencia clave.

## Monolítico

En el diagrama siguiente se describe un enfoque monolítico que utiliza Adobe Commerce como sistema back-end y como aplicación de tienda:

![Diagrama del monolito de Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Headless

En el diagrama siguiente se describe un enfoque sin encabezado que utiliza Adobe Commerce como sistema back-end integrado con una aplicación DXP/CMS/personalizada como aplicación de tienda:

![Diagrama sin encabezado de Adobe Commerce](../../assets/playbooks/integration-headless.svg)

La única diferencia entre el enfoque monolítico y el sin encabezado es la integración de tiendas, que afecta la experiencia del usuario para los clientes. Monolithic utiliza la tienda de Adobe Commerce directamente para integrarse con servicios de terceros, mientras que sin encabezado depende de su propia tienda para personalizar e integrar con los mismos servicios. Algunos servicios, como el pago y el inicio de sesión único (SSO), necesitan personalización tanto de tienda como de Adobe Commerce para finalizar el flujo de integración.

## Sistemas de terceros

Algunos servicios populares ya tienen buenas extensiones para admitir Adobe Commerce o soluciones de tienda populares, como PWA Studio, Adobe Experience Manager y Vue Storefront, que se pueden encontrar desde su mercado de extensiones o desde sitios web de terceros relacionados. Incluso si no hay ninguna extensión existente, el esfuerzo por implementar la integración entre Adobe Commerce y otras tiendas sin encabezado es similar. Todos los servicios de terceros suelen tener documentos que explican cómo integrarse con ellos. Esos servicios son solo algunos ejemplos; varios países y mercados pueden tener diferentes opciones.

## Integraciones empresariales

En el caso de las integraciones de sistemas empresariales, que también se suelen denominar integraciones back-end, hay un impacto en el flujo de datos empresariales. En función de los distintos tipos de negocio y necesidades, puede utilizar tres opciones de integración diferentes, que ya hemos introducido.

Los datos obligatorios del producto, como SKU, inventario y precios base, generalmente provienen de ERP, mientras que los precios de venta suelen ser administrados por cada canal de ventas (por ejemplo, Adobe Commerce) o CPQ (ventas B2B o privadas). Dado que los datos obligatorios del producto (excepto el inventario) no cambian con mucha frecuencia, la práctica recomendada es utilizar actualizaciones programadas por lotes a través de la API de REST o la importación masiva de archivos. Para el inventario, la práctica recomendada es tener una actualización completa diariamente del inventario de productos que se comparte con diferentes canales de ventas para evitar un exceso de ventas. Además, programe cambios incrementales desde su ERP en un plazo de 24 horas.

El contenido de marketing, los metadatos y el catálogo de productos se pueden administrar por separado en cada canal de ventas (por ejemplo, Adobe Commerce) o desde un PIM central. Como los metadatos tampoco cambian con frecuencia, la práctica recomendada es utilizar actualizaciones programadas por lotes a través de la API de REST o la importación masiva de archivos.

Los datos de pedidos incluyen datos de pedidos, ofertas (B2B), envíos, devoluciones e intercambios que normalmente se gestionan desde un sistema OMS y WMS centralizado. Los datos de los pedidos deben sincronizarse lo antes posible, por lo que la API de REST suele ser la mejor opción. Para obtener un mejor rendimiento, considere reducir el número de llamadas a la API. Para el estado del pedido, los envíos, la devolución y los datos de intercambio, considere la posibilidad de programar las API de actualización por lotes REST en horas o minutos.

Los datos B2B generalmente se administran desde un CRM centralizado. Se utiliza una API en tiempo real para verificar los clientes existentes y crear nuevos clientes. Para B2B, puede requerir la introducción de más API para sincronizar diferentes empleados de la compañía, grupos y listas de precios entre Adobe Commerce y su CRM o CPQ.

Hay otras integraciones del sistema, como eDM para marketing por correo electrónico e inteligencia empresarial para el análisis de datos empresariales, que generalmente se realizan mediante la API de REST o la exportación/importación de archivos, que generalmente son compatibles con las extensiones existentes.
