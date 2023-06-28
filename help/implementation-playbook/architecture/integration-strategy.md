---
title: Estrategia de integración de Adobe Commerce
description: Revise las estrategias y opciones de integración de su implementación de Adobe Commerce.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Estrategia de integración de Adobe Commerce

La capacidad de integrar su plataforma es &quot;no negociable&quot;. Las empresas quieren que sus plataformas de comercio electrónico sean accesibles desde una variedad de puntos de contacto e integradas sin problemas en sus sistemas tecnológicos, especialmente su ERP. La personalización, la escalabilidad global y la asequibilidad también desempeñan un papel en la compra de la plataforma final.

Un enfoque de integración integral para los sistemas de tienda y back-end es compatible con las API de GraphQL de rendimiento, las API de REST completas y la importación de archivos por lotes entre Adobe Commerce y otros sistemas o servicios.

La API de Adobe Commerce GraphQL proporciona una cobertura completa de la tienda que puede utilizar para integrar con otras tiendas, como:

- Plataformas de experiencia digital (DXP) como Adobe Experience Manager y Bloomreach
- Sistemas de gestión de contenido (CMS) como Drupal y WordPress
- Aplicación de tienda personalizada moderna como Adobe Commerce, PWA Studio y Vue Storefront

GraphQL proporciona una respuesta eficiente y específica del canal, no sobrecarga de datos y una implementación ágil de nuevas funciones de puntos de contacto. También se elige a menudo para integrarse con canales de ventas como aplicaciones nativas móviles, POS, IoT, canales sociales y canales de comercio en directo como Facebook, Google, Instagram, WeChat y TikTok.

La API de REST de Adobe Commerce proporciona cobertura completa de configuración del sistema y funciones de administración de datos, incluidos producto y catálogo; carro de compras, presupuesto y cierre de compra; clientes, cuenta y empresas; y pedidos y devoluciones. Las API de REST admiten operaciones por lotes, varios modos de autenticación y autorización granular, por lo que las API de REST suelen elegirse para integrarse con sistemas empresariales, lo que incluye:

- Sistemas de planificación de recursos empresariales (ERP) como SAP
- Sistemas de gestión de información de productos (PIM) como Akeneo
- Sistemas de administración de la relación con los clientes (CRM) como Salesforce
- Sistemas de gestión de pedidos (OMS) como MOM, Manhattan y SAP
- Warehouse Management System (WMS) o logística de terceros (3PL) como Oracle, NetSuite y SAP WM
- Configurar, precio, presupuesto (CPQ) como SalesforceCPQ
- Administración de activos digitales (DAM) como DAM de Adobe.

Las importaciones de archivos por lotes también se consideran una buena opción para integrar sistemas empresariales como ERP y PIM, ya que esos datos no cambian con mucha frecuencia y a menudo se obtiene un mejor rendimiento con las importaciones de archivos programados. Por lo tanto, las importaciones de archivos por lotes generalmente se eligen para la sincronización de datos por lotes diaria/semanal y las sincronizaciones de datos completas mensuales, mientras que las API de REST se eligen para la sincronización de cambios de datos incrementales, para un mejor rendimiento. Esto también se considera solo un trabajo programado, pero se puede hacer con frecuencia (potencialmente cada 15 minutos a 1 hora), según las necesidades comerciales.

## Opciones de integración

Adobe Commerce ofrece tres opciones de integración flexibles:

- Integración directa de sistema a sistema con conectores pregenerados. Es posible que algunos sistemas ya tengan extensiones de Adobe Commerce en Adobe Commerce Marketplace o en su propio sitio web.

- Integración de sistema a sistema mediante middleware personalizado. La solución de middleware personalizada implementada se utilizará para la asignación, traducción y administración de datos de procesos.

- Integración de sistema a sistema mediante iPaaS (Plataforma de integración como servicio), también denominada EAI (Enterprise Application Integration Platform), como Mulesoft, Boomi y Software AG.

![Opciones de integración de Adobe Commerce](../../assets/playbooks/integration-options.svg)

A pesar de que las integraciones en tiempo real suelen ser deseables, no es necesario en algunos casos. Adobe Commerce admite de forma nativa [!DNL RabbitMQ] como el bus de mensajes para habilitar procesos asincrónicos, que se recomienda para algunos datos que no son necesarios para intercambiar en tiempo real, sino para actualizar con intercambio de archivos por lotes o la API de procesamiento de datos por lotes REST para procesar asincrónicamente.
