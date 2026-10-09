---
title: Seleccionar las [!UICONTROL focus] fichas
description: Obtenga información sobre cómo seleccionar las fichas [!UICONTROL focus] para observar las áreas que causan problemas.
exl-id: 6c0a7d81-09cf-49ce-888a-9ecaaad2b7ae
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%
---
# Seleccionar las [!UICONTROL focus] fichas

![Elija las fichas de enfoque](../../assets/tools/observation-for-adobe-commerce/choosing-the-focus-tabs-1.jpg)

La potencia de [!DNL Observation for Adobe Commerce] se debe a que se alinea un gran volumen de distintas vistas de datos en la misma cronología. [!DNL Observation for Adobe Commerce] puede presentar a los agentes [!DNL New Relic] una muestra de datos recopilados y una vista visual de los registros del sistema y de la aplicación. Si piensa en solucionar problemas complejos, siempre se trata de dividir a medias los datos. Cuando se analiza un problema en una cronología, la primera pregunta es: &quot;¿Cuándo se produjo esto?&quot; De preocupación inmediata es todo lo que sucedió antes de ese momento. Si conoce la hora exacta en la que se produjo el problema en la cronología, puede seleccionar una cronología inmediatamente antes del problema. Es posible que no sepa que los detalles del problema, aparte de su sitio, están inactivos o son lentos. Con Adobe Commerce, los posibles sospechosos incluyen servicios de componentes, niveles de recursos y el número de procesos en ejecución.

Las pestañas de **[!UICONTROL focus]** muestran información que puede ayudarle a centrarse en las áreas que causan el problema o que contribuyen a él. También puede agregar continuamente señales de datos a [!DNL Observation for Adobe Commerce]. Las señales de datos pueden ser [!DNL New Relic] datos recopilados o recuentos de fases críticas o mensajes de error de registros. A medida que los mensajes de error se identifican como relacionados con los problemas del sitio, se pueden agregar a las consultas [!DNL Observation for Adobe Commerce] para ayudar a mejorar la visualización de la información crítica.

![Elija las fichas de enfoque](../../assets/tools/observation-for-adobe-commerce/choosing-the-focus-tabs-2.jpeg)
