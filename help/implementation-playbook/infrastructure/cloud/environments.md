---
title: Entornos de infraestructura de nube
description: Utilice los entornos adecuados para los casos de uso adecuados.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Entornos

La arquitectura Pro de Adobe Commerce en la infraestructura en la nube admite entornos que puede utilizar para desarrollar, probar e iniciar su tienda. Cada entorno contiene una base de datos y un servidor web. Los cuatro entornos que aprovecha Adobe Commerce son los siguientes:

- **Integración**: proporciona una sola rama de entorno y se pueden crear hasta cuatro ramas de entorno adicionales. Esto permite un máximo de cinco ramas activas implementadas en contenedores de plataforma como servicio (PaaS).

- **Ensayo**: proporciona una sola rama de entorno implementada en contenedores de infraestructura como servicio (IaaS) dedicados.

- **Producción**: proporciona una sola rama de entorno implementada en contenedores de infraestructura como servicio (IaaS) dedicados.

- **Principal global**: proporciona una rama maestra implementada en contenedores de plataforma como servicio (PaaS).

![Diagrama que muestra la relación entre los entornos de nube de Adobe Commerce](../../../assets/playbooks/environment-diagram.svg)

## Ramas de Git

El entorno de integración proporciona una sola rama de integración base que contiene el código Adobe Commerce implementado en contenedores de plataforma como servicio (PaaS).

Adobe Commerce en entornos de infraestructura en la nube admite un proceso de integración flexible y continuo. Comience por clonar la rama de integración en la carpeta local del proyecto. Cree una o varias ramas nuevas para desarrollar nuevas funciones, configurar cambios y agregar extensiones. Con una rama de código desarrollada y los archivos de configuración correspondientes, los cambios de código están listos para combinarse con la rama de integración para realizar pruebas más completas.

![Diagrama que muestra la estrategia de ramificación basada en Git para entornos de nube de Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
