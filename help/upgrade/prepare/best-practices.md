---
title: Prácticas recomendadas
description: Siga las prácticas recomendadas por Adobe para administrar el proceso de actualización de sus proyectos de Adobe Commerce.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 6b3afb93770c1d976dd975a484070e0aee730a98
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Prácticas recomendadas para la actualización

En este tema se enumeran las acciones que debe realizar para administrar la complejidad de actualizar proyectos de Adobe Commerce. Su equipo debe pensar en las actualizaciones desde el momento en que comience el desarrollo del proyecto y continuar con cada versión. Si sigue estas prácticas recomendadas, el proceso de actualización será mucho más fácil, rápido y barato.

>[!TIP]
>
>Estas recomendaciones se basan en las prácticas recomendadas y están respaldadas por pruebas de socios, comerciantes, expertos en Adobe y la comunidad que demuestran su impacto y efectividad.

## ¿Qué impacto tiene una actualización?

Es importante comprender las variables que determinan la complejidad de una actualización. Debe tener en cuenta estas variables al principio de cada proyecto, no solo cuando sea el momento de la actualización. El desarrollo de un proyecto es clave para garantizar que las futuras actualizaciones se realicen sin problemas y que pueda controlar los esfuerzos necesarios para completarlas.

El nivel de esfuerzo para actualizar la instancia de Adobe Commerce depende de estos factores:

- **¿Cómo creó el sitio?** La cantidad de trabajo personalizado y el número de módulos de terceros instalados afectan fuertemente la complejidad de una actualización. La calidad del trabajo personalizado y de los módulos puede determinar si una actualización se realiza sin problemas.

- **¿Se está saltando varias versiones?** Si se omiten las versiones, la siguiente actualización será más compleja; al actualizarla desde las versiones posteriores, el proceso será más fácil y barato.

- **¿Qué tipo de actualización está realizando?** Una actualización a una versión secundaria (de 2.3.x a 2.4.0, por ejemplo) es más extensa que una actualización entre versiones de parches (de 2.4.2 a 2.4.3, por ejemplo). Las actualizaciones de seguridad son el tipo más fácil de implementar.

## Prácticas recomendadas para planificar las actualizaciones

Si está trabajando en un proyecto que ya está en producción, las actualizaciones son una oportunidad para mejorar la calidad del código y las personalizaciones, así como para optimizar las futuras actualizaciones. El tiempo que invierte hoy es tiempo ahorrado a largo plazo.

Si administra varios sitios para diferentes comerciantes, el mejor enfoque es tener una instancia base con las funciones y personalizaciones principales que utiliza normalmente. Utilice esta instancia base como sitio de prueba para completar una actualización y, a continuación, hágalo en otros. Esta práctica le ofrece la flexibilidad de reutilizar módulos personalizados para distintos clientes y simplificar las actualizaciones entre proyectos.

Si el proyecto está activo, le sugerimos que realice una auditoría para determinar su calidad y comprender cómo puede mejorarlo para que las actualizaciones sean más eficientes.

### Desarrollo con actualizaciones en mente

Desde el momento en que empiece a trabajar en un proyecto, debe tener en cuenta cómo afectarán las futuras actualizaciones a su trabajo actual. Siga siempre las prácticas recomendadas de desarrollo de Adobe Commerce que se describen aquí:

- [Prácticas recomendadas de desarrollo](https://developer.adobe.com/commerce/php/best-practices/)
- [Estándares de codificación](https://developer.adobe.com/commerce/php/coding-standards/)

Empiece a adoptar la plataforma de extensibilidad de Adobe Commerce, si aún no lo ha hecho. La plataforma le permite personalizar procesos de forma eficaz, integrar sistemas e implementar nuevas funcionalidades al tiempo que mantiene la capacidad de actualización similar a SaaS. Sus características incluyen:

- **Extensibilidad de la IU**. Amplíe y desarrolle su tienda independientemente de su servidor y middleware con [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **Extensibilidad de API**. Use [GraphQL](https://developer.adobe.com/commerce/webapi/graphql/index.html) para ampliar el nivel de API web mediante la evolución del modelo de datos de gráficos y la ejecución de funciones lambda directamente desde el nivel de gráficos.

- **Servicios y middleware de Adobe I/O**. Conecte sus sistemas con Adobe Commerce mediante el middleware de Adobe y un conjunto de conexiones de aplicaciones basadas en [Adobe I/O](https://www.adobe.io/). Además, puede ampliar las funcionalidades básicas de la plataforma sobrescribiendo el comportamiento predeterminado con su propia lógica empresarial que se ejecuta en Adobe I/O.

### Planificación de actualizaciones

A medida que ampliamos continuamente las capacidades de Adobe Commerce, es fundamental que desarrolle en función de la versión disponible más reciente y defina una estrategia de actualización en sus planes de proyecto. Al hacerlo, se mantiene seguro, conforme y actualizado con las últimas mejoras, que le permiten aumentar las ventas más rápido, operar de forma más eficaz y adelantarse a la competencia ahora y en el futuro.

Para ayudarle a planificar y presupuestar las actualizaciones, debe supervisar nuestra [programación de versiones](https://experienceleague.adobe.com/es/docs/commerce-operations/release/planning/schedule). Planifique con antelación las tareas de actualización dentro del registro de pendientes de su equipo. Objetivo: completar este trabajo con GA.

- Utilice la versión preliminar para obtener más información sobre cada nueva versión. El prelanzamiento es el código de disponibilidad general que está disponible para los comerciantes de Adobe Commerce y todos los socios dos semanas antes de la disponibilidad general. Si tiene varias tiendas, utilice el prelanzamiento en su tienda base y compruebe que sus módulos y temáticas personalizados son compatibles con él.

- Revise la [lista de comprobación del plan de actualización](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/maintenance/upgrade-checklist) para Adobe Commerce para ayudarle a planificar su actualización.

- Planifique las actualizaciones a principios de año. Debe reservar un presupuesto y recursos para completar cada actualización. Recuerde, el esfuerzo de actualización puede variar significativamente de un proyecto a otro. Use sus experiencias y conocimientos para hacer un plan lo más preciso posible.

- Si las actualizaciones requieren más esfuerzo del que describimos aquí, le recomendamos que audite su proyecto y realice ajustes en su entorno para reducir el mantenimiento a largo plazo.

### Realización de actualizaciones

Las actualizaciones deben realizarse de forma regular y con un presupuesto predefinido. Recomendamos programar las actualizaciones aprobadas previamente a principios de año para garantizar que las actualizaciones se planifiquen y completen a tiempo.

Evalúe el trabajo que se debe realizar para la actualización:

- Revise las [notas de la versión](https://experienceleague.adobe.com/es/docs/commerce-operations/release/notes/overview) para comprender el ámbito y el impacto de la nueva versión.

- Use [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) para identificar posibles problemas que deben solucionarse en el código personalizado antes de intentar actualizar a una versión más reciente.

- Si utiliza extensiones de terceros, valide su compatibilidad con la versión de destino a la que planea actualizar.

### Pruebas posteriores a la actualización

Las pruebas son la fase de una actualización que requiere más tiempo. Como resultado, este proceso debe ser lo más automatizado posible. Puede beneficiarse del uso de las herramientas de prueba principales. La [Guía de prueba de aplicaciones](https://developer.adobe.com/commerce/testing/guide/) proporciona detalles.

Utilice un entorno de ensayo para probar y validar la actualización antes de pasar a producción.

Usar una **página de mantenimiento**. La preparación de esta página por adelantado le permite comunicarse con sus clientes y notificarles que el trabajo se está realizando en segundo plano. Esta página debería estar visible durante unos minutos, pero si hay algún problema, es posible que tenga que usarla más tiempo. Tener el contenido y el diseño adecuados para su página de mantenimiento ofrece a sus usuarios una buena experiencia incluso cuando su tienda no está disponible.
