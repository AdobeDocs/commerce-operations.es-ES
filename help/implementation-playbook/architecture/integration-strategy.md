---
title: Estrategia de integración del comercio de Adobe
description: Revise las estrategias y opciones de integración para su implementación de Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Estrategia de integración de Adobe Commerce

La capacidad de integrar su plataforma es &quot;no negociable&quot;. Las empresas desean que sus plataformas de comercio electrónico sean accesibles desde una variedad de puntos de contacto y estén perfectamente integradas en sus sistemas tecnológicos, especialmente su ERP. La personalización, la escalabilidad global y la asequibilidad también desempeñan un papel en la compra final de la plataforma.

Las API de GraphQL, las API completas de REST y la importación por lotes de archivos entre Adobe Commerce y otros sistemas o servicios admiten un enfoque de integración holístico tanto para los sistemas de tienda como para los sistemas de back-end.

La API de Adobe Commerce GraphQL proporciona una cobertura completa de tienda que puede utilizar para integrarla con otras tiendas, como:

- Plataformas de experiencia digital (DXP) como Adobe Experience Manager y Bloomscope
- Sistemas de administración de contenido (CMS) como Drupal y WordPress
- Moderna aplicación de tienda personalizada, como Adobe Commerce, PWA Studio y Tienda de valores

GraphQL proporciona una respuesta eficiente y específica del canal, no sobrecarga de datos y una implementación ágil de nuevas funciones de touchpoint. También suele elegirse para integrarse con canales de ventas como aplicaciones nativas para móviles, POS, IoT, canales sociales y canales comerciales de transmisión en directo como Facebook, Google, Instagram, WeChat y TikTok.

La API de REST de Adobe Commerce proporciona una amplia cobertura de configuración del sistema y funciones de administración de datos, incluidos el producto y el catálogo; carro, presupuesto y cierre de compra; clientes, cuentas y empresas; y pedidos y devoluciones. Las API de REST admiten operaciones masivas, varios modos de autenticación y autorización granular, por lo que las API de REST suelen elegirse para integrarse con sistemas empresariales, incluidos:

- Sistemas de planificación de recursos empresariales (ERP) como SAP
- Sistemas de administración de la información del producto (PIM) como Akeneo
- Sistemas de administración de la relación con los clientes (CRM) como Salesforce
- Sistemas de administración de pedidos (OMS) como MOM, Manhattan y SAP
- Sistema de administración de almacenes (WMS) o logística de terceros (3PL) como Oracle, NetSuite y SAP WM
- Configure, Price, Quote (CPQ) como SalesforceCPQ
- Administración de activos digitales (DAM) como DAM de Adobe.

Las importaciones de archivos por lotes también se consideran una buena opción para integrar sistemas empresariales como ERPs y PIMs, ya que esos datos no cambian muy a menudo, y a menudo tiene un mejor rendimiento con las importaciones de archivos programadas. Por lo tanto, las importaciones de archivos por lotes generalmente se eligen para la sincronización de datos por lotes diaria/semanal y para la sincronización mensual completa de los datos, mientras que las API de REST se eligen para la sincronización de cambios de datos incrementales, para un mejor rendimiento. Esto también se considera un trabajo programado, pero se puede realizar con frecuencia (potencialmente cada 15 minutos a 1 hora) dependiendo de las necesidades del negocio.

## Opciones de integración

Adobe Commerce ofrece tres opciones de integración flexibles:

- Integración directa de sistema a sistema con conectores pregenerados. Es posible que algunos sistemas ya tengan extensiones de Adobe Commerce en el Commerce Marketplace de Adobe o en su propio sitio web.

- Integración de sistema a sistema a través de middleware personalizado. La solución de middleware personalizada implementada se utilizará para la asignación, traducción y administración de datos de procesos.

- Integración de sistema a sistema mediante iPaaS (Integration Platform-as-a-Service), también conocido como EAI (Enterprise Application Integration Platform), como Mulesoft, Boomi y Software AG.

![Opciones de integración de Adobe Commerce](../../assets/playbooks/integration-options.svg)

Aunque normalmente se desean integraciones en tiempo real, no es necesario para algunos escenarios. Adobe Commerce es compatible de forma nativa con RabbitMQ como el bus de mensajes para habilitar procesos asincrónicos, lo que se recomienda para algunos datos que no son necesarios para intercambiarlos en tiempo real, sino que se actualizan con el intercambio de archivos por lotes o la API de procesamiento de datos por lotes REST para procesarlos asincrónicamente.
