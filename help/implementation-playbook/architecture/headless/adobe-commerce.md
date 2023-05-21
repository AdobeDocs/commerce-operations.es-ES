---
title: Arquitectura de Adobe Commerce sin encabezado
description: Descubra qué hace que el enfoque de arquitectura sin encabezado de Adobe Commerce sea único.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Arquitectura de Adobe Commerce sin encabezado

La ventaja de la arquitectura de Adobe Commerce es que no es una propuesta de todo o nada, y un comerciante puede encontrar la combinación adecuada de soluciones para su negocio. Pueden crear un PWA con tecnología de PWA Studio para su experiencia principal en el sitio o usar Adobe Experience Manager como el nivel en recorridos de clientes complejos, todo mientras crean un front-end personalizado para experimentar con nuevos puntos de contacto. Ninguna otra plataforma puede igualar el tiempo para comercializar los beneficios y la flexibilidad que ofrece Adobe Commerce con su arquitectura sin encabezado.

![Diagrama que muestra la arquitectura de tienda de Adobe Commerce sin encabezado](../../../assets/playbooks/headless-storefront-architecture.svg)

Cada enfoque no es mutuamente excluyente. Los clientes pueden crear su propio front-end (principal), utilizar PWA Studio para experiencias web/móviles o utilizar Adobe Experience Manager para el vidrio (en una implementación completa o híbrida).

Adobe Commerce siempre ha permitido implementaciones sin encabezado con API de REST. Aunque REST es potente, especialmente para el procesamiento masivo, cuando se trata de sin encabezado, las API de GraphQL permiten un desarrollo más rápido a través de una experiencia de desarrollador intuitiva, la buena flexibilidad al permitir cambios que no afectan a las API existentes y un mejor rendimiento al minimizar la cantidad de datos recuperados a solo lo que se necesita exactamente.

GraphQL es un estándar del sector para las API con rendimiento, que utilizan muchas de las principales plataformas de comercio electrónico. Eso es bueno ya que esto significa que es una solución probada y la experiencia existe en el mercado.

Aunque Adobe Commerce tiene una tienda emparejada como opción, no es necesario que un comerciante utilice esa interfaz heredada de Adobe Commerce. Un comerciante puede aprovechar los mejores servicios de comercio de Adobe Commerce para gestionar los procesos empresariales back-end y, mediante nuestras API de tienda, integrar su propia tienda disociada para impulsar la experiencia de front-end.

Ahora, echemos un vistazo a las distintas opciones sin encabezado.

## PWA Studio

La primera es una aplicación web progresiva creada con PWA Studio. Parte de esto se habilita por el hecho de que un PWA es una tienda sin encabezado disociada del back-end comercial. Con PWA Studio, los comerciantes pueden crear PWA de alto rendimiento, fiables y rentables además de Adobe Commerce para ofrecer las mejores experiencias web de su clase, tanto en dispositivos móviles como de escritorio. A medida que pase el tiempo, esta superará a la tienda emparejada como opción predeterminada.

La mayoría de los comerciantes entienden la dirección hacia la que se dirige la industria con respecto a los PWA y muchos bloqueadores potenciales se están eliminando rápidamente.

Semana tras semana, el número de socios que crean experiencia en PWA Studio aumenta y tenemos un número cada vez mayor de lanzamientos de clientes. La actualización más reciente de PWA Studio incluyó extensibilidad que ayudará a realizar un progreso significativo en la compatibilidad con las extensiones de Adobe Commerce Marketplace.

Muchos comerciantes pueden sentir que no están listos para trabajar sin encabezado y con PWA porque requieren una fuerte dependencia de los desarrolladores. Una de las grandes ventajas de tener la aplicación de comercio y el encabezado desarrollados por Adobe Commerce es que ayuda a garantizar la compatibilidad entre las capacidades de comercio.

Para que los PWA sean más accesibles y fáciles de administrar para nuestros comerciantes, facultamos a los usuarios empresariales para que administren los cambios diarios de contenido, creen nuevas páginas de aterrizaje y mucho más mediante Page Builder. Estas dos potentes funciones juntas permiten que la velocidad se comercialice en todos los dispositivos y experiencias.

## Adobe Experience Manager

Adobe Experience Manager, una potente combinación para sus necesidades de administración de contenido y recursos digitales, ayuda a los comerciantes a introducir más rápido en el mercado experiencias personalizadas basadas en contenido, combinando la administración de recursos digitales con la potencia del aprendizaje automático, el contenido con tecnología Adobe Sensei y la administración del recorrido del cliente.

Adobe Commerce más Adobe Experience Manager es una historia potente en la que el motor de comercio permite a las empresas activar el comercio a través de interfaces de cliente impulsadas por Adobe Experience Manager.

## Cabezales personalizados

La opción final que se debe discutir aquí es la opción de crear un front-end personalizado. Esta opción es para empresas que tienen experiencia existente y desarrolladores internos capacitados en una pila de front-end en particular, como React. Si no tienen habilidades en el desarrollo de front-end tradicional de Adobe Commerce, pueden decidir que es más rentable crear su propio front-end React personalizado.

Naturalmente, este modelo requiere habilidades y recursos sólidos de desarrollo de front-end para la integración de clientes o sistemas, y no se obtiene el beneficio de la compatibilidad nativa con elementos como Page Builder que se obtiene con PWA Studio. Cada vez que un comerciante está construyendo algo completamente personalizado, puede perder ventajas de tiempo de salida al mercado.

Los front-end personalizados también permiten innovaciones y experimentación. Se habla mucho sobre RA/VR o comercio de voz, y una arquitectura como la de Adobe Commerce permite a los comerciantes explorar estas opciones sin afectar a sus tiendas web existentes.
