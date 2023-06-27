---
title: Puertas de pago
description: Elija un proveedor de pasarela de pago para su proyecto de comercio electrónico en función de las necesidades de su empresa.
exl-id: eab50191-0744-41da-99ba-2e06ea61da27
feature: Best Practices, Payments
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Puertas de pago

Hubo un tiempo en que el efectivo era la principal fuente de transacciones, pero el mundo en línea se ha hecho cargo y los métodos de pago en línea están reemplazando a los antiguos métodos de pago. Todo está ahora en línea, lo que hace que las cosas sean más fáciles y accesibles, incluyendo tarjetas de crédito, billeteras electrónicas y transferencias bancarias.

![Logotipos de proveedor de pasarela de pago](../../assets/playbooks/payment-gateways.png)

Una pasarela de pago es un proveedor de servicios que conecta y procesa pagos para sitios web de comercio electrónico. Desempeñan un papel vital en la experiencia de compra de los clientes y en las tasas de conversión. Los sistemas de pago complicados tienden a hacer que los clientes abandonen sus carros de compras. Es importante proporcionar a los clientes un sistema de pago fácil de usar, donde incluso si un método de pago falla, tienen un método alternativo para motivarlos a completar la compra.

## Revisar requisitos

Los minoristas necesitan seleccionar la mejor pasarela de pago que cumpla con sus requisitos. Hay muchas puertas de enlace de pago en el mercado, como Braintree y Stripe, pero antes de decidir sobre una puerta de enlace de pago, pregúntese lo siguiente:

- ¿Cuál es mi requisito empresarial?
- ¿Está dentro de mi presupuesto?
- ¿Qué tan fuerte es la seguridad en la pasarela de pago?
- ¿Habrá algún impacto en mi UX/IU de la tienda?
- ¿Qué tan bien funciona la pasarela de pago?
- ¿Cómo es el servicio de soporte de la pasarela de pago después de la compra?
- ¿Qué proveedor de pasarela de pago me queda mejor?
- ¿Ofrece la pasarela de pago otras funciones, como el cálculo de impuestos, el uso de geolocalizaciones y el cálculo de la tarifa de servicio?

Existen algunas limitaciones de las puertas de enlace de pago que debe tener en cuenta, como las siguientes:

- No todos los tipos de tarjetas son aceptadas por las puertas de enlace de pago.
- Es posible que algunas opciones de pago no estén disponibles para los compradores internacionales.
- Resquicios de seguridad en la pasarela de pago. Los clientes tienden a dudar en realizar pedidos en línea por motivos de seguridad.

Cuando una empresa decide integrar una pasarela de pago con su plataforma siempre es mejor ver cómo aparece en la tienda, qué tipo de experiencia ofrece a los clientes y si es fácil de usar. Además, asegúrese de que la seguridad del pago no se vea comprometida. Una pasarela de pago de trabajo buena y segura proporciona una mejor experiencia al cliente.

## Consideraciones B2B y B2C

Las empresas B2B y B2C tienen sistemas de pago similares, pero las empresas B2B tienen más reglas, regulaciones y procesos. Las empresas B2B tienden a operar en mayores volúmenes en comparación con las empresas B2C.

Los clientes de B2C compran productos o servicios para uso individual. Los clientes suelen pagar el mismo precio que otros clientes y no hay negociación implicada. Los clientes B2B incluyen varias partes interesadas, lo que hace que la aprobación sea más compleja y costosa.

Los clientes B2B tienen diferentes pedidos y requisitos que deben ser procesados y aprobados por el representante de ventas o un representante de ventas debe participar cuando un cliente compra en línea utilizando una solicitud de propuesta (RFP) o una orden de compra (PO).

Los pagos B2C pueden ser únicos y de menor valor. Los clientes añaden productos al carro de compras y realizan el cierre de compra mediante un pago seguro con tarjeta de crédito o billetera electrónica.

Debido al alto valor de compra de las transacciones B2B, las empresas B2B ofrecen más opciones de pago además de las opciones estándar, incluidos cheques, transferencias bancarias y órdenes de compra.

La implementación de las opciones de pago adecuadas se basa en el tipo de negocio y los requisitos del negocio.
