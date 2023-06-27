---
title: Planificación eficaz de caché
description: Consulte los puntos de referencia recomendados para el almacenamiento en caché a fin de garantizar el éxito de su sitio bajo carga.
exl-id: 275eb21d-fa52-4b97-9453-8f8553128b53
feature: Integration, Cache
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Planificación del almacenamiento en caché efectivo para el éxito del comercio electrónico bajo carga

Para ofrecer una experiencia de compra bajo carga, se necesita una estrategia de almacenamiento en caché bien planificada. Aunque inicialmente la solicitud de las partes interesadas de la empresa puede ser presentar siempre los datos de productos en tiempo real a los clientes, no se trata de un uso óptimo de los recursos del sistema y el impacto del rendimiento del sitio del usuario final superaría en gran medida los beneficios de mostrar la información en tiempo real de forma coherente.

Por lo tanto, el paso inicial en la estrategia de almacenamiento en caché debe ser definir con las partes interesadas relevantes una matriz de tiempos de almacenamiento en caché aceptables para las diferentes áreas del sitio, por ejemplo:

| Área de almacenamiento en caché | ¿Con qué frecuencia cambia? | Impacto si el contenido antiguo se suministra desde la caché | ¿Tiempo de vida (TTL) de almacenamiento en caché aceptable? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Páginas del HTML de contenido del sitio, actualizadas mediante CMS | Poco Frecuente | Baja | 1 día |
| Medios/activos de la plantilla de contenido del sitio: logotipo, diseño CSS, imágenes | Poco Frecuente | Baja | 1 semana |
| Páginas de lista de productos (PLP) | Poco Frecuente | Mediana | 1 día |
| Página de detalles del producto (PDP) | A veces | Mediana | 1 hora |
| Categorías de productos | Poco Frecuente | Mediana | 1 día |
| Precios | Frecuentemente | Alta | Sin caché |
| Inventario/existencias | Frecuentemente | Alta | Sin caché |
| Búsqueda del sitio | La mayoría de usuarios únicos | Mediana | Almacenar en caché los resultados de las 100 frases de búsqueda principales durante 1 día |
| Finalizar compra | Cada usuario único | Muy alto | Sin caché |
| Carro de compras | Cada usuario único | Muy alto | Sin caché |
| Páginas de pago | Cada usuario único | Muy alto | Sin caché |

Una vez finalizada esta planificación inicial, se puede empezar a establecer la configuración técnica para configurar las cachés según estos requisitos.

Incluso si el contenido se actualiza y debe activarse dentro del TTL de almacenamiento en caché, en la mayoría de los casos es posible borrar manualmente las cachés del [AEM dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=en) y [Adobe Commerce](../configuration//cli/manage-cache.md#clean-and-flush-cache-types) almacenar en caché de forma selectiva ese contenido, lo que significa que los cambios urgentes se reflejarán inmediatamente. El proceso de borrado manual de caché también debe planificarse y probarse de antemano para que si hay necesidad de forzar manualmente una actualización de algún contenido, se documente en un runbook de operaciones del sitio y se borre cómo y quién debe involucrarse para actuar en esto.
