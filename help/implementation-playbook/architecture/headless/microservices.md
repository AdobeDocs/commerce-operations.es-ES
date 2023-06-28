---
title: Adobe Commerce Microservices
description: Poder diferenciar entre sin encabezado y microservicios en lo que respecta a Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
feature: Integration, Services
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Sin encabezado y microservicios

Es importante no confundir sin encabezado con los microservicios. Muchas veces, oímos conversaciones sobre microservicios en la misma frase que sin encabezado. Son cosas completamente diferentes. Se pueden usar juntos, pero son conceptos completamente diferentes.

Una arquitectura de microservicios es un término que se utiliza para describir la práctica de dividir una aplicación en una colección de servicios más pequeños y de correspondencia imprecisa. Los microservicios permiten que los servicios back-end individuales sean:

- **Aislados unos de otros**: por ejemplo, el servicio de precios no depende del servicio de catálogo.

- **Implementado a la carta**: los clientes implementan solo las partes de la aplicación que necesitan.

- **Escalar de forma independiente**: los recursos se pueden asignar a servicios de alta demanda, como la búsqueda de inventario.

- **Desarrollado de forma autónoma**: se puede desarrollar e implementar de forma independiente entre sí.

Los microservicios no tienen nada que ver con cortar la cabeza de la pila de comercio o las API. Cuando pensamos en esos servicios de comercio en el código principal que están en el back office de Adobe Commerce, se trata de aislar esos servicios entre sí. Entonces, una arquitectura de microservicios está separando vagamente todos esos servicios como los servicios de precios, el servicio de catálogo y el servicio de inventario, y haciendo que cada uno esté aislado de otro.

Los microservicios pueden ampliarse de forma independiente y desarrollarse de forma autónoma. Los microservicios son similares a un proceso de desarrollo de SaaS de varios inquilinos. Muchos de los productos modernos de SaaS para varios inquilinos se desarrollan con un enfoque multiservicio. Incluso los productos de SaaS propios de Adobe, como Order Management, la nueva herramienta de Recommendations de productos impulsada por IA y otros componentes de SaaS de Adobe Commerce, se están desarrollando utilizando un enfoque de microservicios. Para ser muy claros, Adobe Commerce 2.4.x no es una arquitectura de microservicios, sino una arquitectura sin encabezado.
