---
title: Optimización del rendimiento
description: Obtenga información sobre la optimización del rendimiento y los pasos a seguir para revisar el rendimiento de su implementación de Adobe Commerce.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Optimización del rendimiento

El rendimiento es un gran tema. Cuando los usuarios experimentan un sitio lento o que no responde, afecta a la conversión. Recomendamos seguir estos pasos para optimizar el rendimiento de su Adobe Commerce en la implementación de la infraestructura en la nube:

- Evaluar el problema
- Rendimiento de medida
- Identificar parte del sistema esencial para la mejora del rendimiento
- Modificar parte del sistema para eliminar el cuello de botella
- Medir el rendimiento después de la modificación
- Si es mejor, adoptarlo o revertirlo

## Problemas habituales de rendimiento

El impacto de una experiencia lenta suele definirse por dos indicadores, y cada factor puede ser causado por toneladas de razones.

El tiempo de espera alto para el primer byte (TTFB) suele considerarse como un indicador que define la velocidad de respuesta del servidor. El tiempo no solo proviene de la ejecución del código fuente para administrar la solicitud, sino que también puede verse afectado por los siguientes factores:

- Búsqueda de DNS
- Consultas lentas desde la capa DB
- Tiempo de CPU de cada capa de aplicación
- Limitación de memoria
- La espera de E/S puede afectar a la lectura y escritura de archivos, conectar el servicio a través del socket
- Configuración de software (nginx, PHP, MySQL, Redis, Varnish)
- Ancho de banda de red
- Almacenamiento en caché incorrecto
- Código incorrecto
- Enfoque de integración incorrecto
- Dependencia de la respuesta lenta del servicio de terceros
- Arquitectura sin escalabilidad

Los recursos de carga lenta suelen considerarse como un indicador que define el recurso estático (CSS, JavaScript, imágenes, vídeos, respuesta de llamada Ajax de terceros).

Adobe Commerce se puede ampliar con su empresa a través de sus funciones:

![Diagrama que muestra las funciones escalables de Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

También hay factores clave que impulsan la escala en el comercio, que también afectan el rendimiento general.

- Catálogo de productos complejo y grande
- Gran cantidad de administradores
- Escaparates globales
- Tráfico de alta variable
- Expansión de puntos de contacto
- Transacciones de gran volumen

Para las arquitecturas por capas y almacenables en caché creadas para escalar, puede utilizar este gráfico como referencia.

![Diagrama que muestra cómo utilizar la API de GraphQL de Adobe Commerce en una arquitectura almacenable en caché](../../../assets/playbooks/cacheable-architecture.svg)
