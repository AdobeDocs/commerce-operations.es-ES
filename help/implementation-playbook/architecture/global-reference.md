---
title: Arquitectura de referencia global de Adobe Commerce
description: Aproveche al máximo su implementación de Adobe Commerce con una arquitectura de referencia global.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: f713e07b57705e8720c773f9f762a357c173e29d
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Arquitectura de referencia global (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

Cuando se gestionan empresas que tienen varios sitios para varias marcas en varios mercados locales (con monedas, idiomas, medios, catálogos compartidos y carros de compras únicos localizados) y que desean evitar costes innecesarios para implementar las mismas funciones e integraciones, la arquitectura de referencia global (GRA) siempre es una buena opción.

![Tabla que explica el coste de la divergencia en la arquitectura](../../assets/playbooks/divergent-architecture.svg)

![Tabla que explica el coste de los archivos consolidados en arquitectura](../../assets/playbooks/consolidated-architecture.svg)

El GRA es:

- Un enfoque de implementación
- Una estrategia de implementación
- Un modelo de gobernanza de procesos

GRA no:

- Una &quot;función&quot; de producto
- Exclusivo para cualquier plataforma de comercio
- Solo para casos de uso empresariales globales

Impactos de GRA:

- Entrega del código

   - Se crean en torno a repositorios de código específicos para fines específicos, que ofrecen diferentes experiencias.

- Cómo se integran los sistemas empresariales

   - Consolida las conexiones a sistemas empresariales por marca o región.

- Desarrollo y mantenimiento de la personalización

   - Garantiza que las personalizaciones estén centralizadas y sean específicas del dominio, de modo que todo el esfuerzo de personalización se realice desde un punto de vista integral para la empresa.

- Cómo se habilitan los nuevos mercados

   - Simplifica el lanzamiento de múltiples canales y mercados que de otra manera costarían considerablemente más tiempo y dinero.
