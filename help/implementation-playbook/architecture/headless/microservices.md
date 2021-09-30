---
title: Microservicios de Adobe Commerce
description: Poder diferenciar entre sanidad y microservicios en lo que se refiere al comercio de Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Sin cabeza y microservicios

Es importante no confundir los microservicios sin cabeza. Muchas veces, escuchamos conversaciones sobre microservicios en la misma frase sin cabeza. Son cosas completamente diferentes. Pueden utilizarse juntos, pero son conceptos completamente diferentes.

La arquitectura de los microservicios es un término utilizado para describir la práctica de dividir una aplicación en una colección de servicios más pequeños y con poca acoplamiento. Los microservicios permiten que los servicios backend individuales sean:

- **Aislado entre sí**: por ejemplo, el servicio de precios no depende del servicio de catálogo.

- **Implementado a la carta**: los clientes implementan solo las partes de la aplicación que necesitan.

- **Escalar de forma independiente**: los recursos se pueden asignar a servicios de alta demanda, como la búsqueda de inventario.

- **Desarrollado** de forma autónoma: se puede desarrollar e implementar de forma independiente entre sí.

Los microservicios no tienen nada que ver con cortar la cabeza de la pila de comercio o las API. Cuando pensamos en esos servicios comerciales en el código central que están en la oficina de Adobe de Comercio, se trata de aislar esos servicios entre sí. Por lo tanto, una arquitectura de microservicios está dividiendo, en términos generales, todos esos servicios, como los servicios de precios, el servicio de catálogo y el servicio de inventario, y aislando cada uno de ellos de otro. Esto garantiza que sean un carrito para que no necesite comprar e implementar todo el Adobe Commerce de una sola vez.

Los microservicios pueden escalarse de forma independiente y desarrollarse de forma autónoma. Los microservicios son similares a un proceso de desarrollo SaaS de varios arrendatarios. Muchos de los modernos productos SaaS multiinquilinos se desarrollan con un enfoque multiservicio. Incluso los propios productos SaaS de Adobe, como Order Management, la nueva herramienta de Recommendations de productos impulsada por AI y otros componentes SaaS del Comercio de Adobe se están desarrollando con un enfoque de microservicios. Para ser claros, Adobe Commerce 2.4.x no es una arquitectura de microservicios, sino una arquitectura sin objetivos.
