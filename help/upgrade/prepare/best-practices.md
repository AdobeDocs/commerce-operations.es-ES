---
title: Prácticas recomendadas
description: Utilice las prácticas recomendadas por el Adobe para administrar el proceso de actualización de sus proyectos de Adobe Commerce y Magento Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# Prácticas recomendadas para la actualización

En este tema se enumeran las acciones que debe realizar para administrar la complejidad de actualizar proyectos de Adobe Commerce y Magento Open Source. Su equipo debe pensar en las actualizaciones desde el momento en que comience el desarrollo del proyecto y continúe con cada versión. Al seguir estas prácticas recomendadas, el proceso de actualización será mucho más fácil, rápido y más barato.

>[!TIP]
>
>Estas recomendaciones se basan en las mejores prácticas, respaldadas por pruebas de su impacto y eficacia por parte de asociados, comerciantes, expertos en Adobe y la comunidad.

## ¿Qué afecta a una actualización?

Es importante comprender las variables que determinan la complejidad de una actualización. Debe tener en cuenta estas variables al principio de cada proyecto, no solo cuando es el momento de actualizarlo. El desarrollo de un proyecto es clave para garantizar que las futuras actualizaciones sean fluidas y que pueda controlar el esfuerzo necesario para completarlas.

El nivel de esfuerzo para actualizar la instancia de Adobe Commerce depende de estos factores:

- **¿Cómo construyó el sitio?** La cantidad de trabajo personalizado y el número de módulos de terceros instalados afectan en gran medida a la complejidad de una actualización. La calidad del trabajo personalizado y los módulos puede determinar si una actualización se realiza sin problemas.

- **¿Está omitiendo varias versiones?** Omitir versiones hace que la siguiente actualización sea más compleja, la actualización de las versiones posteriores facilita y hace más barato el proceso.

- **¿Qué tipo de actualización está realizando?** Una actualización a una versión menor (de 2.3.x a 2.4.0, por ejemplo) es más extensa que una actualización entre versiones de parches (como de 2.4.2 a 2.4.3). Las actualizaciones de seguridad son el tipo más fácil de implementar.

## Prácticas recomendadas para la planificación de actualizaciones

Si está trabajando en un proyecto que ya está en producción, las actualizaciones son una oportunidad para mejorar la calidad del código y las personalizaciones, y para optimizar para futuras actualizaciones. El tiempo que invierte hoy es tiempo ahorrado a largo plazo.

Si administra varios sitios para diferentes comerciantes, el mejor enfoque es tener una instancia base con las principales características y personalizaciones que utiliza normalmente. Utilice esta instancia base como sitio de prueba para completar una actualización y luego hacerlo en otros. Esta práctica le ofrece la flexibilidad de reutilizar módulos personalizados para diferentes clientes y simplificar las actualizaciones entre proyectos.

Si el proyecto está activo, le sugerimos que realice una auditoría para determinar su calidad y que comprenda cómo puede mejorarlo para que las actualizaciones sean más eficientes.

### Desarrollo con actualizaciones en mente

Desde el momento en que empiece a trabajar en un proyecto, debe considerar cómo se verán afectadas las futuras actualizaciones por su trabajo actual. Siga siempre las prácticas recomendadas de desarrollo de Adobe Commerce que se describen aquí:

- [Prácticas recomendadas de desarrollo](https://devdocs.magento.com/guides/v2.4/ext-best-practices/bk-ext-best-practices.html)
- [Normas de codificación](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)

Empiece a adoptar la plataforma de extensibilidad de Adobe Commerce, si aún no lo ha hecho. La plataforma le permite personalizar de forma eficiente los procesos, integrar los sistemas e implementar nuevas capacidades, al mismo tiempo que mantiene la capacidad de actualización similar a SaaS. Sus características incluyen:

- **Extensión de la interfaz de usuario**. Amplíe y desarrolle su tienda independientemente de su back-end y middleware usando [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **Extensión de API**. Uso [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) para ampliar la capa de API web mediante la evolución del modelo de datos de gráficos y la ejecución de funciones lambda directamente desde la capa de gráfico.

- **middleware y servicios de Adobe I/O**. Conecte sus sistemas con Adobe Commerce mediante el middleware de Adobe y un conjunto de conexiones de aplicaciones integradas [Adobe I/O](https://www.adobe.io/). Además, puede ampliar las funciones de la plataforma principal sobrescribiendo el comportamiento predeterminado con su propia lógica empresarial que se ejecuta en Adobe I/O.

### Planificación de actualizaciones

A medida que continuamos ampliando las capacidades de Adobe Commerce, es fundamental que desarrolle la última versión disponible y defina una estrategia de actualización en sus planes de proyecto. Esto le ayuda a mantenerse seguro, conforme y actualizado con las últimas mejoras que le permiten aumentar las ventas más rápido, operar con mayor eficacia y mantenerse a la vanguardia de su competencia ahora y en el futuro.

Para ayudarle a planificar y presupuestar las actualizaciones, debe supervisar nuestra [programación de versiones](https://devdocs.magento.com/release). Planifique las tareas de actualización dentro del tiempo acumulado de su equipo con antelación. Pretende completar este trabajo con la Asamblea General.

- Utilice la versión previa al lanzamiento para obtener más información sobre cada nueva versión. El prelanzamiento es un código de disponibilidad general disponible para los comerciantes de Adobe Commerce y todos los socios dos semanas antes de la disponibilidad general. Si tiene varias tiendas, utilice el lanzamiento previo de su tienda base y compruebe que sus módulos y temas personalizados son compatibles con él.

- Consulte la [Actualizar lista de comprobación del plan](https://support.magento.com/hc/en-us/articles/360057968951) para que Adobe Commerce le ayude a planificar su actualización.

- Planifique actualizaciones a principios de año. Debe reservar un presupuesto y recursos para completar cada actualización. Recuerde que el esfuerzo de actualización puede variar significativamente de un proyecto a otro. Use sus experiencias y conocimientos para hacer un plan lo más preciso posible.

- Si las actualizaciones están tomando más esfuerzo del que describimos aquí, le recomendamos que audite el proyecto y realice ajustes en su entorno para reducir el mantenimiento a largo plazo.

### Realización de actualizaciones

Las actualizaciones deben realizarse con regularidad y con un presupuesto predefinido. Se recomienda programar actualizaciones preaprobadas a principios de año para garantizar que las actualizaciones se planifiquen y completen a tiempo.

Evalúe el trabajo a realizar para la actualización:

- Consulte la [notas de la versión](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) para comprender el alcance y el impacto de la nueva versión.

- Utilice la variable [Herramienta de compatibilidad de actualización](../upgrade-compatibility-tool/overview.md) para identificar posibles problemas que deben solucionarse en el código personalizado antes de intentar actualizar a una versión más reciente.

- Si utiliza extensiones de terceros, valide su compatibilidad con la versión de destino a la que planea actualizar.

### Pruebas posteriores a la actualización

La prueba es la fase de una actualización que requiere la mayor cantidad de tiempo. Como resultado, este proceso debe ser lo más automatizado posible. Puede beneficiarse del uso de las herramientas de prueba principales. La variable [Guía de prueba de aplicaciones](https://devdocs.magento.com/guides/v2.4/test/testing.html) proporciona detalles.

Utilice un entorno de ensayo para probar y validar la actualización antes de pasar a producción.

Utilice un **página de mantenimiento**. Preparar esta página por adelantado le permite comunicarse con sus clientes, notificándoles que el trabajo se está realizando en segundo plano. Esta página debería estar visible durante unos minutos, pero si hay algún problema, es posible que tenga que usarla más tiempo. Tener el contenido y el diseño adecuados para su página de mantenimiento ofrece a los usuarios una buena experiencia incluso cuando la tienda no está disponible.
