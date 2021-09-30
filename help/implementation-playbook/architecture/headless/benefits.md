---
title: Comercio sin objetivos
description: Aprenda qué significa el comercio sin objetivos y cómo el comercio de Adobe admite arquitecturas sin objetivos.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# Comercio sin objetivos

## ¿Por qué sin cabeza?

Para empezar, el comercio empresarial heredado es costoso y difícil de escalar debido a los silos; las estructuras heredadas se refuerzan mediante limitaciones de plataforma; y la innovación se convierte en un desafío.

Los clientes esperan que una empresa interactúe con ellos y se involucre con ellos en todos los canales. Las organizaciones centradas en el cliente buscan crear plataformas a prueba del futuro que puedan adaptarse a las cambiantes expectativas de los clientes.

El comercio sin encabezado se basa en API. Desvincula la lógica empresarial, así como los aspectos de datos y transacciones del comercio, de la presentación. Sin encabezado es un marco integrado que proporciona flexibilidad completa para todos los canales y puntos de contacto, con una capa de experiencia de front-end que está separada de la propia plataforma. Esto permite a las marcas la agilidad de entregar contenido como productos, datos y pedidos a cualquier punto de contacto, tanto ahora como en el futuro, mientras pueden mostrarlo de la forma que deseen.

La arquitectura sin encabezado es la separación técnica del encabezado del resto de la aplicación de comercio. Adobe Commerce es totalmente independiente con una arquitectura disociada que proporciona todos los servicios de comercio y datos a través de una capa de API de GraphQL. Esta arquitectura permite a los equipos de front-end desarrollar sus frentes de forma independiente del comercio de Adobe, lo que proporciona la agilidad para crear y probar rápidamente nuevos puntos de contacto con tecnologías emergentes.

Las API de Adobe Commerce GraphQL también se pueden ampliar con microservicios implementados en I/O Runtime de Adobe. Esto proporciona una agilidad sin igual para integrar, ampliar y personalizar procesos empresariales omnicanal sin necesidad de personalizar el código en el backend, lo que garantiza que la plataforma principal se pueda actualizar fácilmente sin afectar a los puntos de contacto de front-end. Las API de Adobe Commerce GraphQL son de código abierto y forman parte de nuestro programa de ingeniería comunitaria, con importantes contribuciones y supervisión de nuestra comunidad de desarrolladores.

![Diagrama de arquitectura de comercio sin encabezado](../../../assets/playbooks/headless-diagram.svg)

![Ventajas del diagrama de arquitectura de comercio sin objetivos](../../../assets/playbooks/headless-benefits.svg)
