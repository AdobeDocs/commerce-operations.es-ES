---
title: Arquitectura de tienda asociada
description: Obtenga información sobre lo que significa una tienda acoplada en el contexto de arquitecturas Adobe Commerce sin periféricos.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Arquitectura de tienda Adobe Commerce combinada (heredada)

La opción de implementación predeterminada actual para la mayoría de los clientes comerciales incluye:

- 100% de compatibilidad con características en B2B y B2C
- Tema de referencia maduro (Luma) que se puede implementar rápidamente o personalizar
- Experiencia en la implementación de socios de TI
- Completamente compatible con capacidades de comercio como Page Builder o Staging &amp; Preview
- Amplia compatibilidad con extensiones en Adobe Commerce Marketplace

![Diagrama de una arquitectura de tienda Adobe Commerce acoplada](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Toneladas de tienda heredada

- **Sin encabezado**: todas las partes de la aplicación Adobe Commerce monolítica. No hay separación de lógica y procesos empresariales entre el front-end y el backend.

- **No es PWA**: aunque el tema es interactivo, el rendimiento del sitio está muy por detrás del mejor PWA de su clase.

- **Arquitectura front-end (componentes de interfaz de usuario de Adobe Commerce)**—Especialistas en Adobe Commerce/PHP para aprovechar las tiendas heredadas.

Antes de entrar en opciones sin objetivos, empecemos con la arquitectura de tienda más familiar. Si se desvincula la cabeza, esta sería la arquitectura de tienda acoplada, más comúnmente vista con nuestras demostraciones de Luma.

Aquí es donde las capacidades de tienda están estrechamente integradas con los servicios comerciales principales, no separadas por esa capa de API de GraphQL. Así que hay mucha lógica empresarial unida a ese tema. Este enfoque no es remoto y no es PWA.

Actualmente, esta es la opción más común que utilizan los comerciantes, ya que cuenta con un 100% de compatibilidad con las funciones de comercio B2B y B2C. La comunidad está familiarizada con ella, existe un ecosistema maduro de experiencia a su alrededor y tiene una amplia compatibilidad con las extensiones de Adobe Commerce Marketplace.

Sin embargo, carece de los beneficios de los que hablamos antes. Sin separación de capas, hay muchas dependencias y posibles puntos de fallo cuando se realizan cambios. No es tan eficaz como un PWA bien implementado y si un comerciante no tiene experiencia en el desarrollo de Adobe Commerce o PHP, tendrá que ir a buscar esos recursos.
