---
title: Arquitectura de referencia empresarial
description: Aprenda a implementar Adobe Commerce utilizando la tecnología de comercio componible más reciente de Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 8eab688ed98eb1b9fcf4fc25f90fe2bbf99c02d6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Arquitectura de referencia empresarial de Adobe Commerce

Adobe Commerce es la plataforma basada en experiencias que combina de forma exclusiva la flexibilidad técnica con la facilidad de uso, todo al servicio de la creación de experiencias excepcionales que impulsen los resultados empresariales.

El comercio ha evolucionado para satisfacer los requisitos empresariales de rendimiento, escala y seguridad. La adopción de un enfoque de implementación moderno que utilice las últimas soluciones de comercio componible de Adobe es crítica para el éxito de los negocios empresariales. Esta página describe el enfoque moderno de implementación de Commerce con detalles técnicos.

El diagrama de arquitectura siguiente ilustra el flujo de datos entre Adobe Commerce y todas las soluciones de Adobe Experience Cloud.

![Diagrama arquitectónico que muestra cómo se conecta Adobe Commerce a las soluciones de Experience Cloud](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>Los flujos de datos de alto nivel que se muestran en el diagrama son coherentes en la mayoría de las implementaciones empresariales. El componente clave que puede hacer que las implementaciones sean únicas es la forma en que crea el catálogo (especialmente para B2B). Debe asignar cuidadosamente la arquitectura del catálogo a [API web de Commerce](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud foundation

[Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) es la base de su implementación de Commerce. Proporciona un [secure](../../security-and-compliance/shared-responsibility.md) plataforma de alojamiento automatizada con un enfoque de autoservicio para crear, implementar, monitorizar y administrar su aplicación de Commerce en un entorno nativo de la nube.

Consulte los siguientes detalles técnicos de Cloud Foundation:

- [**Arquitectura a escala**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture): capacidad ajustada automáticamente para mantener un rendimiento estable y predecible.
- [**Varios entornos**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—Preaprovisionado con PHP, MySQL (MariaDB), Redis, RabbitMQ y tecnologías de motores de búsqueda compatibles para desarrollar, probar e implementar su sitio
- [**Administración de configuración**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview): archivos de configuración de entorno personalizables e interfaz de línea de comandos (CLI) para administrar la configuración de la aplicación, las rutas, las acciones de generación e implementación y las notificaciones.
- [**Flujo de trabajo basado en Git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): cree e implemente automáticamente después de insertar los cambios del código para un desarrollo rápido y una implementación continua.
- [**Observabilidad integrada**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance): herramientas que combinan datos de registro de varias fuentes para ayudarle a administrar el rendimiento del sitio y diagnosticar problemas
- [**Cobertura completa de API**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) y [REST](https://developer.adobe.com/commerce/webapi/rest) API para integrar la aplicación principal de Commerce con sistemas de terceros y ampliar las capacidades de Commerce

## Integración con Experience Cloud

Adobe Commerce se integra con todas las soluciones de Experience Cloud para ofrecer [experiencias de comercio personalizadas a escala](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Conexión de datos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) desbloquea la información sobre el comportamiento de compra de sus compradores para que pueda crear experiencias de compra personalizadas en todos los canales con otros productos de Adobe Digital Experience.

>[!NOTE]
>
>Consulte [Modelos de experiencia digital](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) para obtener más información técnica.


## Integración con sistemas de terceros

Adobe proporciona a los desarrolladores puntos de extensión y herramientas completos para crear aplicaciones que amplíen las capacidades principales de Commerce e integren Commerce con sistemas de terceros (como CRM, ERPS y PIMS). Estas herramientas reducen el coste total de propiedad de la plataforma de las siguientes maneras:

- **Escalabilidad**: las aplicaciones se pueden escalar por separado del software principal, lo que permite una mayor eficiencia y actualizaciones simplificadas.
- **Aislamiento**-Un entorno aislado significa que los desarrolladores pueden actualizar o modificar sus extensiones a su discreción sin depender de una versión principal.
- **Independencia tecnológica**-Los desarrolladores pueden elegir cualquier pila de tecnología y lenguajes de codificación que se ajusten a sus necesidades.

Adobe proporciona las siguientes herramientas para desarrolladores para crear integraciones y personalizaciones:

- [**Malla de API para el Generador de aplicaciones de Adobe Developer**](https://developer.adobe.com/graphql-mesh-gateway/): coordine y combine varias fuentes de API, GraphQL, REST y otras en un único extremo de GraphQL consultable.
- [**Generador de aplicaciones**](https://developer.adobe.com/app-builder/docs/overview/): Cree e implemente aplicaciones web seguras y escalables que amplíen la funcionalidad de Commerce e integren soluciones de terceros.
- [**Eventos**](https://developer.adobe.com/commerce/extensibility/events/): utilice déclencheur de evento personalizados para interactuar con otras herramientas de desarrollo ampliables.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/): utilice los enlaces web para almacenar automáticamente en déclencheur las interacciones entre Commerce y sistemas de terceros.
- [**SDK de IU de administración**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/): personalice y mejore el administrador de Commerce con nuevas páginas y funciones para sus comerciantes.

## Servicios de tienda

Adobe proporciona un completo conjunto de servicios de comercialización inteligentes y componibles para ayudarle a respaldar sus objetivos comerciales clave. Estos servicios también proporcionan API esenciales para optimizar el rendimiento a escala.

- [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview): Ofrezca resultados más inteligentes, rápidos y relevantes a los compradores con esta herramienta de búsqueda con tecnología de IA.
- [Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview): agregue recomendaciones alimentadas por IA basadas en el comportamiento del comprador, las tendencias populares, la similitud del producto y mucho más.
- [Servicio de catálogo](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview): Ofrezca a sus clientes una experiencia de producto optimizada a la vez que aumenta el rendimiento, mejora la escalabilidad y aumenta las conversiones.
- [Servicios de pago](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview): aumente la satisfacción del cliente ofreciendo varios métodos de pago, incluidos plazos de pago sin intereses, y una única vista del procesamiento de pagos, pedidos y facturas.

## Tienda sin encabezado

El comercio sin encabezado es un comercio con prioridad de API. Adobe Commerce no tiene encabezado con una arquitectura disociada que proporciona todos los servicios y datos de comercio a través de una capa de API de GraphQL. Esta arquitectura permite a los equipos desarrollar sus front-end de forma independiente de la aplicación principal, lo que proporciona la agilidad para crear y probar rápidamente nuevos puntos de contacto con tecnologías emergentes.

Adobe proporciona una tecnología moderna de tienda sin encabezado que incluye las mismas ventajas y capacidades que ofrece [Edge Delivery Services](https://www.aem.live/home) con la creación basada en documentos, una arquitectura que da prioridad al rendimiento y la experimentación nativa predeterminada. Utiliza la escala y el rendimiento de Adobe Commerce [servicios de tienda](#storefront-services) y la flexibilidad y comodidad de [componentes integrados](https://experienceleague.adobe.com/developer/commerce/storefront/) para ofrecer funcionalidades de comercio.

