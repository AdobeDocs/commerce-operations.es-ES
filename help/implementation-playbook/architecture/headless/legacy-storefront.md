---
title: Arquitectura de tienda emparejada
description: Obtenga información sobre lo que significa una tienda emparejada en el contexto de las arquitecturas de Adobe Commerce sin encabezado.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Arquitectura de tienda de Adobe Commerce asociada (heredada)

La opción de implementación predeterminada actual para la mayoría de los clientes comerciales incluye:

- Compatibilidad de funciones al 100 % en B2B y B2C
- Tema de referencia maduro (Luma) que se puede implementar/personalizar rápidamente
- Experiencia en implementación de socios de SI maduros
- Totalmente compatible con las funcionalidades de comercio como Page Builder o Ensayo y previsualización
- Amplia compatibilidad con las extensiones en Adobe Commerce Marketplace

![Diagrama que muestra una arquitectura de tienda de Adobe Commerce emparejada](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Contras de tienda heredada

- **Sin encabezado**: todos forman parte de la aplicación monolítica de Adobe Commerce. No hay separación de lógica y procesos empresariales entre el front-end y el back-end.

- **No es PWA**: Aunque la temática es adaptable, el rendimiento del sitio está muy por detrás del mejor PWA de su clase.

- **Arquitectura front-end (componentes de la interfaz de usuario de Adobe Commerce)**—Especialistas de Adobe Commerce/PHP para construir sobre tienda heredada.

Antes de entrar en las opciones sin encabezado, vamos a empezar con la arquitectura de tienda más familiar. Si sin encabezado está disociado, esta sería la arquitectura de tienda emparejada, más comúnmente vista con nuestras demostraciones de Luma.

Aquí es donde las funcionalidades de la tienda están estrechamente integradas con los servicios principales de comercio, no separados por esa capa de API de GraphQL. Por lo tanto, hay mucha lógica empresarial asociada a ese tema. Este enfoque no es sin encabezado y no es PWA.

Actualmente, esta es la opción más común que utilizan los comerciantes porque tiene una compatibilidad de funciones del 100 % con las capacidades de comercio B2B y B2C. La comunidad está familiarizada con él, existe un ecosistema de experiencia maduro a su alrededor y tiene una amplia compatibilidad con las extensiones de Adobe Commerce Marketplace.

Sin embargo, carece de los beneficios de los que hablamos anteriormente. Sin la separación de las capas, cuando se realizan cambios hay muchas dependencias y posibles puntos de error. No tiene el mismo rendimiento que un PWA bien implementado y si un comerciante no tiene experiencia en desarrollo de Adobe Commerce o PHP, tendrá que ir a buscar esos recursos.
