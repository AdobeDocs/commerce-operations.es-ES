---
title: Arquitectura de referencia global de Adobe Commerce
description: Saque el máximo partido a su implementación de Adobe Commerce aprovechando la arquitectura de referencia global.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: f713e07b57705e8720c773f9f762a357c173e29d
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Arquitectura de referencia global (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

Cuando se ejecutan negocios que tienen varios sitios para varias marcas en varios mercados locales (con monedas, idiomas, medios, catálogos compartidos y carros de compras únicos localizados) y que desean evitar costes innecesarios para implementar la misma función e integraciones: la arquitectura de referencia global (GRA) siempre es una buena opción.

![Tabla que explica el costo de la divergencia en la arquitectura](../../assets/playbooks/divergent-architecture.svg)

![Tabla que explica el coste de la consolidación en arquitectura](../../assets/playbooks/consolidated-architecture.svg)

GRA es:

- Un enfoque de implementación
- Una estrategia de implementación
- Un modelo de gobernanza de procesos

GRA no es:

- Una &quot;función&quot; de producto
- Único para cualquier plataforma de comercio
- Solo para casos de uso comercial global

Impacto de GRA:

- Envío del código

   - Se crea en torno a repositorios de código específicos, que ofrecen diferentes experiencias.

- Integración de los sistemas empresariales

   - Consolida las conexiones a los sistemas del negocio por marca o región.

- Desarrollo y mantenimiento de la personalización

   - Garantiza que las personalizaciones estén centralizadas y específicas del dominio, de modo que todo el esfuerzo de personalización se realice desde un punto de vista holístico para el negocio.

- Cómo activar los nuevos mercados

   - Simplifica el lanzamiento de múltiples canales y mercados que de otra manera costaría mucho más tiempo y dinero.
