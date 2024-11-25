---
title: Arquitectura de referencia empresarial
description: Aprenda a implementar Adobe Commerce utilizando la tecnología de comercio componible más reciente de Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 581a7dbcc19c31df80e03cb9f321a6adb5fa1a73
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Arquitectura de referencia empresarial de Adobe Commerce

Adobe Commerce es la plataforma basada en experiencias que combina de forma exclusiva la flexibilidad técnica con la facilidad de uso, todo al servicio de la creación de experiencias excepcionales que impulsen los resultados empresariales.

Commerce ha evolucionado para satisfacer los requisitos empresariales de rendimiento, escala y seguridad. La adopción de un enfoque de implementación moderno que utilice las últimas soluciones de comercio componible de Adobe es crítica para el éxito de los negocios empresariales. En esta página se describe el método moderno de implementación de Commerce con detalles técnicos.

El diagrama de arquitectura siguiente ilustra el flujo de datos entre Adobe Commerce y todas las soluciones de Adobe Experience Cloud.

![Diagrama arquitectónico que muestra cómo se conecta Adobe Commerce a las soluciones de Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>Los flujos de datos de alto nivel que se muestran en el diagrama son coherentes en la mayoría de las implementaciones empresariales. El componente clave que puede hacer que las implementaciones sean únicas es la forma en que crea el catálogo (especialmente para B2B). Debe asignar cuidadosamente la arquitectura de catálogo a las [API web de Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud foundation

[Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) es la base de su implementación de Commerce. Proporciona una plataforma de alojamiento automatizada [secure](../../security-and-compliance/shared-responsibility.md) con un enfoque de autoservicio para crear, implementar, supervisar y administrar su aplicación de Commerce en un entorno nativo de la nube.

Consulte los siguientes detalles técnicos de Cloud Foundation:

- [**Arquitectura a escala**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture): capacidad ajustada automáticamente para mantener un rendimiento estable y predecible.
- [**Varios entornos**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture): preaprovisionados con PHP, MySQL (MariaDB), Redis, RabbitMQ y tecnologías de motores de búsqueda compatibles para desarrollar, probar e implementar su sitio
- [**Administración de configuración**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview): archivos de configuración de entorno personalizables e interfaz de línea de comandos (CLI) para administrar la configuración de la aplicación, las rutas, las acciones de generación e implementación y las notificaciones.
- [**Flujo de trabajo basado en Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): genérelo e impleméntelo automáticamente después de insertar los cambios del código para un desarrollo rápido y una implementación continua
- [**Observabilidad integrada**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance): herramientas que combinan datos de registro de varias fuentes para ayudarle a administrar el rendimiento del sitio y diagnosticar problemas
- [**Amplia cobertura de API**](https://developer.adobe.com/commerce/webapi/get-started/)—[API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) y [REST](https://developer.adobe.com/commerce/webapi/rest) para integrar la aplicación principal de Commerce con sistemas de terceros y ampliar las capacidades de Commerce

## Integración con Experience Cloud

Adobe Commerce se integra con todas las soluciones de Experience Cloud para ofrecer [experiencias de comercio personalizadas a escala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Conexión de datos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) desbloquea la información sobre el comportamiento de compra de tus compradores para que puedas crear experiencias de compra personalizadas en todos los canales con otros productos de Experiencia digital de Adobe.

>[!NOTE]
>
>Consulte los siguientes recursos para obtener más información:
>
>- [Modelos de experiencia digital](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) para obtener más detalles técnicos.
>- Ver [Personalización de la experiencia del cliente](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integración con sistemas de terceros

Adobe proporciona a los desarrolladores puntos de extensión y herramientas completos para crear aplicaciones que amplíen las capacidades principales de Commerce e integren Commerce con sistemas de terceros (como CRM, ERPS y PIMS). Estas herramientas reducen el coste total de propiedad de la plataforma de las siguientes maneras:

- **Escalabilidad**: las aplicaciones se pueden escalar por separado del software principal, lo que permite una mayor eficiencia y actualizaciones simplificadas.
- **Aislamiento**: un entorno aislado significa que los desarrolladores pueden actualizar o modificar sus extensiones a su discreción sin depender de una versión principal.
- **Independencia tecnológica**: los desarrolladores pueden elegir entre pilas de tecnología y lenguajes de codificación que se ajusten a sus necesidades.

Adobe proporciona las siguientes herramientas para desarrolladores para crear integraciones y personalizaciones:

- [**Mesh de API para Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/): coordina y combina varias fuentes de API, GraphQL, REST y otras en un único extremo de GraphQL consultable.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): cree e implemente aplicaciones web seguras y escalables que amplíen la funcionalidad de Commerce y se integren con soluciones de terceros.
- [**Eventos**](https://developer.adobe.com/commerce/extensibility/events/): utilice déclencheur de eventos personalizados para interactuar con otras herramientas de desarrollo ampliables.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/): utilice los webhooks para almacenar automáticamente en déclencheur las interacciones entre Commerce y sistemas de terceros.
- [**SDK de IU de administración**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/): personalice y mejore el administrador de Commerce con nuevas páginas y características para sus comerciantes.
- [**Kit de inicio de integración**](https://developer.adobe.com/commerce/extensibility/starter-kit/): acelere las integraciones de back-office con integraciones de referencia, scripts de incorporación y una arquitectura estandarizada.

>[!NOTE]
>
>Ver [El enfoque moderno: extensibilidad efectiva en Adobe Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Servicios de tienda

Adobe proporciona un completo conjunto de servicios de comercialización inteligentes y componibles para ayudarle a respaldar sus objetivos comerciales clave. Estos servicios también proporcionan API esenciales para optimizar el rendimiento a escala.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview): ofrece resultados más inteligentes, rápidos y relevantes a los compradores con esta herramienta de búsqueda con tecnología de IA.
- [Recommendations del producto](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview): agregue recomendaciones impulsadas por IA en función del comportamiento del comprador, las tendencias populares, la similitud del producto y mucho más.
- [Servicio de catálogo](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview): ofrezca a sus clientes una experiencia de producto optimizada a la vez que aumenta el rendimiento, mejora la escalabilidad y aumenta las conversiones.
- [Servicios de pago](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview): Mejore la satisfacción del cliente ofreciendo varios métodos de pago, incluidos pagos a plazos sin intereses, y una sola vista del procesamiento de pagos, pedidos y facturas.

## Tienda sin encabezado

El comercio sin encabezado es un comercio con prioridad de API. Adobe Commerce no tiene encabezado con una arquitectura disociada que proporciona todos los servicios y datos de comercio a través de una capa de API de GraphQL. Esta arquitectura permite a los equipos desarrollar sus front-end de forma independiente de la aplicación principal, lo que proporciona la agilidad para crear y probar rápidamente nuevos puntos de contacto con tecnologías emergentes.

El Adobe proporciona una tecnología moderna de tienda sin encabezado que incluye las mismas ventajas y capacidades que ofrecen [Edge Delivery Services](https://www.aem.live/home) con la creación basada en documentos, una arquitectura que da prioridad al rendimiento y experimentación nativa lista para usar. Utiliza la escala y el rendimiento de [servicios de tienda](#storefront-services) de Adobe Commerce y la flexibilidad y comodidad de [componentes integrados](https://experienceleague.adobe.com/developer/commerce/storefront/) para ofrecer funciones de comercio.

