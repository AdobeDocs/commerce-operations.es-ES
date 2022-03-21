---
title: Arquitectura Adobe Commerce sin objetivos
description: Obtenga información sobre lo que hace que el enfoque de arquitectura sin encabezado de Adobe Commerce sea único.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Arquitectura Adobe Commerce sin objetivos

La ventaja de la arquitectura de Adobe Commerce es que no es una propuesta de todo o nada y un comerciante puede encontrar la combinación correcta de soluciones para su negocio. Pueden crear un PWA con tecnología de PWA Studio para su experiencia principal en el sitio o utilizar Adobe Experience Manager como capa en recorridos de clientes complejos, todo ello mientras crean un front-end personalizado para experimentar con nuevos puntos de contacto. Ninguna otra plataforma puede igualar el tiempo a las ventajas del mercado y la flexibilidad que ofrece Adobe Commerce con su arquitectura sin objetivos.

![Diagrama de una arquitectura de tienda Adobe Commerce sin periféricos](../../../assets/playbooks/headless-storefront-architecture.svg)

Cada enfoque no se excluye mutuamente. Los clientes pueden crear su propio front-end (head), utilizar PWA Studio para experiencias web/móviles y/o utilizar Adobe Experience Manager para el vidrio (en una implementación completa o híbrida).

Adobe Commerce siempre ha permitido implementaciones sin periféricos con las API de REST. Aunque REST es potente, especialmente para el procesamiento masivo, cuando se trata de una API sin periféricos, las API de GraphQL permiten un desarrollo más rápido gracias a una experiencia intuitiva para desarrolladores, la buena flexibilidad al permitir cambios que no afectan a las API existentes y un mejor rendimiento al minimizar la cantidad de datos recuperados únicamente a lo que se necesita exactamente.

GraphQL es un estándar del sector para las API con rendimiento, que utilizan muchas de las plataformas de comercio electrónico más importantes. Eso es algo bueno ya que esto significa que es una solución comprobada y la experiencia existe en el mercado.

Aunque Adobe Commerce tiene una tienda acoplada como opción, de ninguna manera es necesario que un comerciante utilice esa interfaz heredada de Adobe Commerce. Un comerciante puede aprovechar los mejores servicios de comercio de Adobe Commerce para gestionar los procesos empresariales back-end y, mediante nuestras API de tienda, integrar su propia tienda disociada para impulsar la experiencia de front-end.

Ahora, echemos un vistazo a las diversas opciones sin objetivos.

## PWA Studio

La primera es una aplicación web progresiva creada con PWA Studio. Parte de esto se habilita por el hecho de que un PWA es una tienda sin periféricos disociada del servidor comercial. Con PWA Studio, los comerciantes pueden crear PWA de alto rendimiento, confiables y rentables además de Adobe Commerce para ofrecer las mejores experiencias web de su clase, tanto en dispositivos móviles como de escritorio. Con el tiempo, esto superará a la tienda asociada como opción predeterminada.

La mayoría de los comerciantes entienden la dirección hacia la que se dirige la industria con respecto a los PWA y muchos bloqueadores potenciales se están eliminando rápidamente.

Semana tras semana, el número de socios que adquieren experiencia en PWA Studio crece y tenemos un número cada vez mayor de lanzamientos de clientes. La actualización más reciente para PWA Studio incluye la extensibilidad que ayudará a lograr un progreso significativo en la compatibilidad con las extensiones de Adobe Commerce Marketplace.

Muchos comerciantes pueden sentir que no están listos para trabajar sin objetivos y PWA porque requieren una gran dependencia de los desarrolladores. Una de las grandes ventajas de tener tanto la aplicación comercial como el jefe desarrollados por Adobe Commerce es que ayuda a garantizar la compatibilidad entre las capacidades comerciales.

Con el fin de que los PWA sean más accesibles y fáciles de administrar para nuestros comerciantes, ofrecemos a los usuarios empresariales la posibilidad de administrar los cambios de contenido diarios, crear nuevas páginas de aterrizaje y mucho más mediante el Page Builder. Estas dos potentes capacidades juntas permiten la rápida comercialización en todos los dispositivos y experiencias.

## Adobe Experience Manager

Adobe Experience Manager, una combinación potente para sus necesidades de administración de recursos digitales y contenido, ayuda a los comerciantes a obtener experiencias personalizadas basadas en contenido en el mercado más rápido, combinando la administración de recursos digitales con la potencia del aprendizaje automático, el contenido con tecnología Adobe Sensei y la administración del recorrido de los clientes.

Adobe Commerce plus Adobe Experience Manager es una historia contundente en el sentido de que el motor de comercio permite a las empresas activar el comercio mediante interfaces de cliente con tecnología Adobe Experience Manager.

## Cabeceras personalizadas

La última opción para discutir aquí es la opción de crear un front-end personalizado. Esta opción es para empresas que tienen experiencia y desarrolladores internos cualificados en una pila de front-end determinada, como React. Si no tienen habilidades en el desarrollo de front-end tradicional de Adobe Commerce, pueden decidir que es más rentable construir su propio front-end React personalizado.

Naturalmente, este modelo requiere recursos y habilidades de desarrollo de front-end para la integración de sistemas o clientes sólidos, y no obtiene el beneficio de la compatibilidad nativa con cosas como Page Builder que obtiene con el PWA Studio. Cada vez que un comerciante está construyendo algo completamente personalizado, puede perder ventajas de tiempo de salida al mercado.

Los front-end personalizados también permiten innovaciones y experimentación. Se habla mucho de AR/VR o comercio de voz, y una arquitectura como la de Adobe Commerce permite a los comerciantes explorar estas opciones sin afectar a sus tiendas web existentes.
