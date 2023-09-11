---
title: Estrategia de extensibilidad de Adobe Commerce
description: Descubra cómo el modelo de extensibilidad de Adobe Commerce le permite personalizar su implementación.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Estrategia de extensibilidad

La plataforma de extensibilidad de Adobe Commerce permite que las marcas personalicen de forma eficaz los procesos, integren sistemas e implementen nuevas funcionalidades a la vez que mantienen la capacidad de actualización.

## Información general sobre las estrategias de extensión de Commerce

Ampliar las capacidades de la plataforma de Commerce incluye los siguientes enfoques de alto nivel:

* Ampliación de las capacidades nativas de la plataforma de Commerce. Por ejemplo, los comerciantes pueden instalar aplicaciones de Marketplace (a menudo creadas por terceros) que amplíen y perfeccionen las capacidades nativas de la plataforma; por ejemplo, una extensión que puede validar las direcciones de envío durante el cierre de compra y facilitar la integración rápida con las API de direcciones de operadores de UPS.

* Integración de aplicaciones/extensiones de terceros con la plataforma de Commerce. Los desarrolladores pueden utilizar las API de REST y GraphQL completas de Commerce para integrar directamente Commerce con soluciones de terceros.

Sin embargo, la arquitectura de la plataforma determina las mejores estrategias para ampliar una plataforma. Commerce proporciona una amplia cobertura de API de GQL y REST para una implementación sin encabezado. La base del código principal de Commerce sigue evolucionando hacia una arquitectura más modular y una sola capa de integración, que proporciona nuevas herramientas de personalización mejoradas:

* [Generador de aplicaciones para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) es un marco de desarrollo y un conjunto de herramientas creados en una infraestructura de Adobe. Los desarrolladores pueden utilizarlo para crear extensiones de Commerce que van desde personalizaciones de experiencias del usuario/tiendas hasta extensiones de middleware y lógica empresarial.

* [Malla de API para el Generador de aplicaciones de Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/) permite a los desarrolladores combinar varias fuentes de datos en un único extremo de API. Esto admite la organización o integración de API de API privadas y de terceros, así como otras interfaces de software con API de Adobe Commerce y otros productos de Adobe mediante Adobe I/O.

* [Eventos de Adobe I/O para Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) pone los datos transaccionales a disposición de las aplicaciones desarrolladas con App Builder y los enlaces web de terceros, lo que permite la creación de aplicaciones impulsadas por eventos.

Estas herramientas proporcionan acceso a la consola de Adobe Developer y a las herramientas para desarrolladores de Adobe para crear API e integrar complementos e integraciones personalizados.

En el diagrama siguiente se destacan los componentes principales de la estrategia de extensibilidad de Commerce.

![Diagrama de estrategia de extensibilidad de Adobe Commerce](../../assets/playbooks/extensibility-strategy-overview.png)
