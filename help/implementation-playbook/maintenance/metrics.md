---
title: Métricas de asistencia
description: Supervise los esfuerzos de asistencia y mantenimiento para la implementación de Adobe Commerce con métricas comunes.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Métricas de asistencia

El diagrama siguiente muestra las métricas/KPI típicos recopilados e informados para las funciones L1:

![Diagrama que muestra métricas de SLA](../../assets/playbooks/sla-metrics.svg)

La medición y la elaboración de informes de los servicios L2 (mejoras y servicios opcionales) son similares a los proyectos de desarrollo. El rendimiento y el progreso de los equipos L2 se miden mediante métricas como velocidad, calidad del código, eficacia de las pruebas y productividad.

| Medición de rendimiento clave | Unidad de medida | Métricas de informes |
|------------------------------|---------------------|------------------------------------------------------------------------------------|
| Velocity | Número | No. de puntos de historia que el equipo pudo entregar para el sprint |
| Eficiencia de compromiso de Sprint | Porcentaje | Nº total de puntos de artículo comprometidos con respecto a entregados para una huella |
| Sprint Burn down | Número | Gráfico (Informe, hace un seguimiento de la finalización del trabajo a lo largo de todo el sprint) |
| Calidad de código | Números, Porcentaje | Complejidad, LoC, Violaciones, Cobertura de código para la huella digital |
| Volatilidad de los requisitos | Número | N.º de requisitos cambio/ total # requisitos para la sprint |
| Densidad de defecto | Porcentaje | [No. de defectos válidos encontrados/Número total de casos de prueba ejecutados]*100 para el sprint |
| Eficacia de las pruebas | Porcentaje | [Defectos válidos elevados/(Defectos válidos planteados+ defectos rechazados)]*100 para la velocidad |
| Productividad | Número (tendencia) | Puntos de artículo entregados por sprint/capacidad |