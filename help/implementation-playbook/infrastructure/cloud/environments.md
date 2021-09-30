---
title: Entornos de infraestructura de nube
description: Utilice los entornos adecuados para los casos de uso adecuados.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Entornos

Adobe Commerce en la infraestructura de la nube La arquitectura Pro admite entornos que puede utilizar para desarrollar, probar e iniciar su tienda. Cada entorno contiene una base de datos y un servidor web. Los cuatro entornos aprovechados por Adobe Commerce son:

- **Integración**: proporciona una sola rama de entorno y puede crear hasta cuatro ramas de entorno adicionales. Esto permite un máximo de cinco ramas activas implementadas en contenedores de Platform as a Service (PaaS).

- **Ensayo**: Proporciona una rama de entorno única implementada en contenedores de infraestructura como servicio (IaaS) dedicados.

- **Producción**: Proporciona una rama de entorno única implementada en contenedores dedicados de Infraestructura como un servicio (IaaS).

- **Global Master**: Proporciona una rama maestra implementada en contenedores de Platform as a Service (PaaS).

![Diagrama de la relación entre los entornos de la nube de comercio de Adobe](../../../assets/playbooks/environment-diagram.svg)

## Ramas de Git

El entorno de integración proporciona una sola rama de integración base que contiene el código de comercio de Adobe implementado en los contenedores de Platform como a-Service (PaaS).

El Adobe Commerce en entornos de infraestructura en la nube soporta un proceso de integración flexible y continuo. Comience clonando la rama de integración en la carpeta local del proyecto. Cree una rama nueva o varias ramas para desarrollar nuevas funciones, configurar cambios y agregar extensiones. Con una rama de código desarrollada y los archivos de configuración correspondientes, los cambios de código están listos para combinarse con la rama de integración para realizar pruebas más exhaustivas.

![Diagrama que muestra la estrategia de ramificación basada en Git para los entornos de la nube de Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
