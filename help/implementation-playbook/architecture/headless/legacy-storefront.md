---
title: Arquitectura de tienda asociada
description: Obtenga información sobre lo que significa una tienda acoplada en el contexto de arquitecturas de comercio de Adobe sin objetivos.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Arquitectura asociada (heredada) de tienda de Adobe Commerce

La opción de implementación predeterminada actual para la mayoría de los clientes comerciales incluye:

- 100% de compatibilidad con características en B2B y B2C
- Tema de referencia maduro (Luma) que se puede implementar rápidamente o personalizar
- Experiencia en la implementación de socios de TI
- Completamente compatible con capacidades de comercio como Page Builder o Staging &amp; Preview
- Amplia compatibilidad con extensiones en el Commerce Marketplace de Adobe

![Diagrama de una arquitectura de tienda de comercio de Adobe emparejada](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Toneladas de tienda heredada

- **No sin cabeza**: todo es parte de la aplicación monolítica de comercio de Adobe. No hay separación de lógica y procesos empresariales entre el front-end y el backend.

- **No es PWA**: aunque el tema es interactivo, el rendimiento del sitio está muy por detrás del mejor PWA de su clase.

- **Arquitectura front-end (componentes de interfaz de usuario de comercio de Adobe)**: especialistas en comercio de Adobe/PHP para aprovechar las tiendas heredadas.

Antes de entrar en opciones sin objetivos, empecemos con la arquitectura de tienda más familiar. Si se desvincula la cabeza, esta sería la arquitectura de tienda acoplada, más comúnmente vista con nuestras demostraciones de Luma.

Aquí es donde las capacidades de tienda están estrechamente integradas con los servicios comerciales principales, no separadas por esa capa de API de GraphQL. Así que hay mucha lógica empresarial unida a ese tema. Este enfoque no es remoto y no es PWA.

Actualmente, esta es la opción más común que utilizan los comerciantes, ya que cuenta con un 100% de compatibilidad con las funciones de comercio B2B y B2C. La comunidad está familiarizada con ella, hay un ecosistema maduro de experiencia a su alrededor, y tiene una amplia compatibilidad con las extensiones de Commerce Marketplace de Adobe.

Sin embargo, carece de los beneficios de los que hablamos antes. Sin separación de capas, hay muchas dependencias y posibles puntos de fallo cuando se realizan cambios. No es tan eficaz como un PWA bien implementado y si un comerciante no tiene experiencia en comercio de Adobe o desarrollo de PHP, tendrán que ir a buscar esos recursos.
