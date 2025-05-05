---
title: Arquitectura de referencia empresarial
description: Aprenda a implementar Adobe Systems Commerce utilizando la última tecnología de comercio componible de Adobe Systems.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Arquitectura de referencia empresarial de Adobe Systems Commerce

Adobe Systems Commerce es la plataforma liderada por experiencia que combina de manera única la flexibilidad técnica con la facilidad de uso, todo al servicio de crear experiencias excepcionales que dirigir resultados comerciales.

El comercio ha evolucionado para satisfacer los requisitos empresariales de rendimiento, escala y seguridad. La adopción de un enfoque de implementación moderno que utiliza las últimas soluciones de comercio componible de Adobe Systems es esencial para el éxito de las empresas empresariales. Este Página describe el enfoque moderno de implementación de comercio en detalle técnico.

En el diagrama de arquitectura siguiente se ilustra el flujo de datos entre Adobe Systems Commerce y todas las Adobe Experience Cloud soluciones.

![Diagrama arquitectónico que muestra cómo se conecta Adobe Systems Commerce con las soluciones de Experience Cloud](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"}

>[!NOTE]
>
>Los flujos de datos de alto nivel mostrados en el diagrama son coherentes en la mayoría de las implementaciones empresariales. El componente clave que puede hacer que las implementaciones sean únicas es la forma en que versión su catálogo (especialmente para B2B). Debe asignar cuidadosamente la arquitectura del catálogo a las API[&#128279;](https://developer.adobe.com/commerce/webapi/get-started/) web de comercio.

## Base de nube

[Adobe Systems Commerce on infraestructura en la nube](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/overview) es la base de su implementación de comercio. Proporciona una [plataforma de alojamiento automatizada segura](../../security-and-compliance/shared-responsibility.md) con un enfoque de autoservicio para crear, implementar, monitorear y administrar su aplicación de comercio en un entorno de nube nativa.

Consulte los siguientes detalles técnicos de la base nube:

- [**Arquitectura**](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) escalada: capacidad ajustada automáticamente para mantener un rendimiento constante y predecible.
- [**Múltiples entornos**](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/architecture/pro-architecture): preaprovisionados con PHP, MySQL (MariaDB), Redis, RabbitMQ y tecnologías motor de búsqueda compatibles para desarrollar, prueba y implementar su sitio
- [**Gestión de la**](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/overview) configuración: archivos de configuración de entorno personalizables e interfaz de línea de comandos (CLI) para administrar aplicación configuración, rutas, acciones de versión y implementar y notificaciones.
- [**flujo de trabajo**](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) basado en Git: versión y implementar automáticamente después de realizar cambios en el código para un desarrollo rápido y una implementación continua.
- [**Observabilidad**](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/monitor/performance) integrada: Herramientas que combinan datos de registro de múltiples fuentes para ayudarlo a administrar el rendimiento de su sitio y diagnosticar problemas
- [**Cobertura**](https://developer.adobe.com/commerce/webapi/get-started/) completa de API:[ API de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) y [REST](https://developer.adobe.com/commerce/webapi/rest) para integrar el aplicación de comercio central con los sistemas terceros y ampliar las capacidades de comercio

## Integración con Experience Cloud

Adobe Systems Commerce se integra con todas las soluciones de Experience Cloud para ofrecer [experiencias de comercio personalizadas a escala](https://experienceleague.adobe.com/es/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[La conexión](https://experienceleague.adobe.com/es/docs/commerce/data-connection/overview) de datos desbloquea información sobre el comportamiento de compra de sus compradores para que pueda crear experiencias de compra personalizadas en todos los canales con otros productos de Adobe Systems Digital Experience.

>[!NOTE]
>
>Si necesita más información, consulte las siguientes recomendaciones:
>
>- [Planos de](https://experienceleague.adobe.com/es/docs/blueprints-learn/architecture/overview) la experiencia digital para obtener más detalles técnicos.
>- Consulte [Personalización de la experiencia](https://experienceleague.adobe.com/es/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization) del cliente.


## Integración con sistemas terceros

Adobe Systems proporciona a los desarrolladores puntos de extensión completos y herramientas para versión aplicaciones que amplían las capacidades básicas de Commerce e integran Commerce con sistemas terceros (como CRM, ERP y PIMS). Estas herramientas reducen el coste total de propiedad de la plataforma de las siguientes maneras:

- **Escalabilidad**: las aplicaciones se pueden escalar por separado del software principal, lo que permite una mayor eficiencia y actualizaciones simplificadas.
- **Aislamiento**: una entorno aislada significa que los desarrolladores pueden actualizar o modificar sus extensiones a su discreción sin depender de una versión principal.
- **Independencia** tecnológica: los desarrolladores pueden elegir cualquier pila de tecnología y lenguajes de codificación que se ajusten a sus necesidades.

Adobe Systems proporciona las siguientes herramientas de desarrollo para crear integraciones y personalizaciones:

- [**API Mesh for Adobe Systems Developer aplicación Builder**](https://developer.adobe.com/graphql-mesh-gateway/): coordine y combine varias API, GraphQL, REST y otras fuentes en un único punto final de GraphQL consultable.
- [**aplicación Builder**](https://developer.adobe.com/app-builder/docs/overview/): cree y implementar aplicaciones web seguras y escalables que amplíen funcionalidad Commerce y integrar con soluciones terceros.
- [**Eventos**](https://developer.adobe.com/commerce/extensibility/events/): utilice activadores de Evento personalizado para interactuar con otras herramientas de desarrollo extensibles.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/): use webhooks para activar automáticamente las interacciones entre los sistemas Commerce y terceros.
- [**SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) de IU de administración: personalice y mejore el administrador de comercio con nuevas páginas y funciones para sus comerciantes.
- [**Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/) de inicio de integración: acelere sus integraciones de backoffice con integraciones de referencia, scripts de incorporación y una arquitectura estandarizada.

>[!NOTE]
>
>Véase [El enfoque moderno: extensibilidad efectiva en el comercio](https://experienceleague.adobe.com/es/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility) Adobe Systems.

## Servicios de escaparate

Adobe Systems proporciona un amplio conjunto de servicios de comercialización inteligentes y componibles para ayudarlo a respaldar sus objetivos comerciales clave. Estos servicios también proporcionan API que son esencial para optimizar el rendimiento a escala.

- [Live Search](https://experienceleague.adobe.com/es/docs/commerce/live-search/overview): ofrezca resultados más inteligentes, rápidos y relevantes para los compradores con este herramienta búsqueda impulsado por IA.
- [Recommendations](https://experienceleague.adobe.com/es/docs/commerce/product-recommendations/overview) del producto: añadir recomendaciones impulsadas por IA basadas en el comportamiento comprador, las tendencias populares, la similitud de productos y más.
- [Servicio](https://experienceleague.adobe.com/es/docs/commerce/catalog-service/guide-overview) de catálogo: ofrezca a sus clientes un experiencia de producto optimizado a la vez que aumenta el rendimiento, mejora escalabilidad y aumenta las conversiones.
- [Servicios](https://experienceleague.adobe.com/es/docs/commerce/payment-services/guide-overview) de pago: impulse la satisfacción del cliente ofreciendo varios métodos de pago, incluidas las cuotas de pago de interés gratuito y una sola vista en el procesamiento de pagos, pedidos y facturas.

## Escaparate sin cabeza

El comercio sin cabeza es el comercio con prioridad de API. Adobe Systems Commerce es totalmente headless con una arquitectura desacoplada que proporciona todos los servicios y datos de comercio a través de una capa API GraphQL. Esta arquitectura permite a los equipos desarrollar sus frontends independientemente del aplicación central, proporcionando la agilidad para versión rápidamente y prueba nuevos puntos de contacto con tecnologías emergentes.

Adobe Systems proporciona una moderna tecnología de escaparate sin cabeza que incluye los mismos beneficios y capacidades que ofrecen [los servicios](https://www.aem.live/home) de entrega perimetral con creación basada en documento, una arquitectura de rendimiento y experimentación nativa lista para usar. Aprovecha la escala y el rendimiento de los servicios[&#128279;](#storefront-services) de escaparate de Adobe Systems Commerce y la flexibilidad y conveniencia de [los componentes](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=es) directos para ofrecer capacidades comerciales.

