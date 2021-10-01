---
title: Planificación de caché eficaz
description: Consulte los puntos de referencia recomendados para el almacenamiento en caché con el fin de garantizar el éxito del sitio bajo carga.
source-git-commit: 41c0ba17b3d731a82ad6ecd8b16fac151a597e75
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Planificación del almacenamiento en caché efectivo para el éxito del comercio electrónico bajo carga

La entrega de una experiencia de compra bajo carga requiere una estrategia de almacenamiento en caché bien planificada. Aunque inicialmente la solicitud de las partes interesadas del negocio puede ser presentar siempre datos de productos en tiempo real a los clientes, no se trata de un uso óptimo de los recursos del sistema, y el impacto del rendimiento del sitio del usuario final superaría en gran medida los beneficios de mostrar la información en tiempo real de forma coherente.

Por lo tanto, el paso inicial en la estrategia de almacenamiento en caché debería ser definir con las partes interesadas una matriz de tiempos de almacenamiento en caché aceptables para las diferentes áreas del sitio, por ejemplo:

| Área de almacenamiento en caché | ¿Con qué frecuencia cambian? | Impacto si el contenido obsoleto se sirve desde la caché | ¿Tiempo de vida (TTL) aceptable en caché? |
|---------------------------------------------------------------|--------------------|-------------------------------------------|-----------------------------------------------------|
| Páginas HTML de contenido de sitio actualizadas mediante CMS | Poco frecuentes | Bajo | 1 día |
| Recursos/medios de plantilla de contenido del sitio: logotipo, diseño de CSS, imágenes | Poco frecuentes | Bajo | 1 semana |
| Páginas de listas de productos (PLP) | Poco frecuentes | Medio | 1 día |
| Página de detalles del producto (PDP) | A veces | Medio | 1 hora |
| Categorías de productos | Poco frecuentes | Medio | 1 día |
| Precios | Frecuentes | Alto | Sin caché |
| Inventario/stock | Frecuentes | Alto | Sin caché |
| Búsqueda del sitio | La mayoría de los usuarios únicos | Medio | Resultados de caché de las 100 primeras frases de búsqueda durante 1 día |
| Cierre de compra | Cada usuario único | Muy alto | Sin caché |
| Carro de compras | Cada usuario único | Muy alto | Sin caché |
| Páginas de pago | Cada usuario único | Muy alto | Sin caché |

Con esta planificación inicial finalizada, se puede empezar a establecer la configuración técnica para configurar las cachés según estos requisitos.

Incluso si el contenido se actualiza y necesita activarse dentro del TTL de almacenamiento en caché, en la mayoría de los casos es posible borrar manualmente las cachés del despachante de AEM y la caché de Adobe Commerce de forma selectiva para ese contenido, lo que significa que los cambios urgentes se reflejarán inmediatamente. El proceso en torno a la limpieza manual de la caché también debe planificarse y probarse con antelación para que si hay necesidad de forzar manualmente una actualización de algún contenido, entonces se documenta en un runbook de operaciones del sitio y se borre cómo y quién debe estar involucrado para actuar en esto. Aquí se muestra un ejemplo de operación de borrado manual de caché para AEM y comercio de Adobe.
