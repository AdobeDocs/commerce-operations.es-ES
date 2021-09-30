---
title: Optimización del rendimiento
description: Obtenga información sobre la optimización del rendimiento y los pasos que debe seguir para revisar el rendimiento de la implementación de Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Optimización del rendimiento

El rendimiento es un tema importante. Cuando los usuarios experimentan un sitio lento o no interactivo, esto afecta a la conversión. Recomendamos seguir estos pasos para optimizar el rendimiento de Adobe Commerce en la implementación de la infraestructura de nube:

- Evaluar el problema
- Medir el rendimiento
- Identificar parte del sistema crítica para la mejora del rendimiento
- Modificar parte del sistema para quitar el cuello de botella
- Mida el rendimiento después de la modificación
- Si es mejor, adoptarlo o revertirlo

## Problemas habituales de rendimiento

El impacto de una experiencia lenta suele definirse mediante dos indicadores, y cada factor puede ser causado por toneladas de razones.

El tiempo de respuesta alto al primer byte (TTFB) se suele considerar como un indicador que define la velocidad de respuesta del servidor. El tiempo no solo proviene de la ejecución del código fuente para gestionar la solicitud, sino que también puede verse afectado por los siguientes factores:

- Búsqueda DNS
- Consultas lentas de la capa de base de datos
- Tiempo de CPU de cada capa de aplicación
- Limitación de memoria
- La espera de E/S puede afectar desde la lectura y escritura de archivos, conectar el servicio a través del socket
- Configuración de software (nginx, PHP, MySQL, Redis, Varnish)
- Ancho de banda de la red
- Almacenamiento en caché incorrecto
- Código incorrecto
- Enfoque de integración incorrecto
- Dependencia de la respuesta lenta del servicio de terceros
- Arquitectura sin escalabilidad

Los recursos de carga lenta generalmente se consideran un indicador que define el recurso estático (CSS, JavaScript, imágenes, vídeos, respuesta de llamada de Ajax de terceros).

Adobe Commerce puede escalar con su empresa a través de sus capacidades:

![Diagrama de las capacidades ampliables de Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

También hay factores clave que impulsan la escala del comercio, que también afectan el rendimiento general.

- Catálogo de productos complejo y grande
- Gran número de administradores
- Tiendas globales
- Tráfico de alta variable
- Expansión de puntos de contacto
- Transacciones de gran volumen

Para arquitecturas en capas y almacenables en caché creadas para escala, puede utilizar este gráfico como referencia.

![Diagrama que muestra cómo utilizar la API de Adobe Commerce GraphQL en una arquitectura almacenable en caché](../../../assets/playbooks/cacheable-architecture.svg)
