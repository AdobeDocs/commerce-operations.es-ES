---
title: Microservicios de Adobe Commerce
description: Ser capaz de diferenciar entre microservicios y sin periféricos en lo que se refiere a Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Sin cabeza y microservicios

Es importante no confundir los microservicios sin cabeza. Muchas veces, escuchamos conversaciones sobre microservicios en la misma frase sin cabeza. Son cosas completamente diferentes. Pueden utilizarse juntos, pero son conceptos completamente diferentes.

La arquitectura de los microservicios es un término utilizado para describir la práctica de dividir una aplicación en una colección de servicios más pequeños y con poca acoplamiento. Los microservicios permiten que los servicios backend individuales sean:

- **Aislados unos de otros**: por ejemplo, el servicio de precios no depende del servicio de catálogo.

- **Implementado a la carta**: los clientes implementan solo las partes de la aplicación que necesitan.

- **Escalar de forma independiente**: los recursos se pueden asignar a servicios de alta demanda, como la búsqueda de inventario.

- **Desarrollo autónomo**: se puede desarrollar e implementar de forma independiente entre sí.

Los microservicios no tienen nada que ver con cortar la cabeza de la pila de comercio o las API. Cuando pensamos en esos servicios de comercio en el código principal que están en la oficina de administración de Adobe Commerce, se trata de aislar esos servicios entre sí. Por lo tanto, una arquitectura de microservicios está dividiendo, en términos generales, todos esos servicios, como los servicios de precios, el servicio de catálogo y el servicio de inventario, y aislando cada uno de ellos de otro.

Los microservicios pueden escalarse de forma independiente y desarrollarse de forma autónoma. Los microservicios son similares a un proceso de desarrollo SaaS de varios arrendatarios. Muchos de los modernos productos SaaS multiinquilinos se desarrollan con un enfoque multiservicio. Incluso los propios productos SaaS de Adobe, como Order Management, la nueva herramienta Recommendations de productos impulsada por AI y otros componentes SaaS de Adobe Commerce se están desarrollando con un enfoque de microservicios. Para ser claros, Adobe Commerce 2.4.x no es una arquitectura de microservicios, sino una arquitectura sin objetivos.
