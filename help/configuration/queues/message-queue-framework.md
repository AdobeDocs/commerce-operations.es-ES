---
title: Resumen de colas de mensajes
description: Obtenga información sobre el marco de trabajo de la cola de mensajes y cómo funciona con la aplicación Adobe Commerce y Magento Open Source.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Resumen de colas de mensajes

Message Queue Framework (MQF) es un sistema que permite a un módulo publicar mensajes en colas. También define el [consumidores](consumers.md) que recibirá los mensajes de forma asíncrona. El MQF utiliza [[!DNL RabbitMQ]](https://www.rabbitmq.com) como agente de mensajería, que proporciona una plataforma escalable para enviar y recibir mensajes. También incluye un mecanismo para almacenar mensajes no enviados. [!DNL RabbitMQ] se basa en la especificación 0.9.1 del Protocolo avanzado de Message Queue Server (AMQP).

El diagrama siguiente ilustra el marco de trabajo de Message Queue:

![Marco de cola de mensajes](../../assets/configuration/mq-framework.png)

- Un publicador es un componente que envía mensajes a un intercambio. Sabe a qué intercambio publicar y el formato de los mensajes que envía.

- Un intercambio recibe mensajes de los editores y los envía a las colas. Aunque [!DNL RabbitMQ] admite varios tipos de intercambios, Commerce solo utiliza intercambios de temas. Un tema incluye una clave de enrutamiento, que contiene cadenas de texto separadas por puntos. El formato del nombre de un tema es `string1.string2`: por ejemplo, `customer.created` o `customer.sent.email`.

   El agente de permite utilizar caracteres comodín al establecer reglas para reenviar mensajes. Puede utilizar un asterisco (`*`) para reemplazar _uno_ cadena o signo de almohadilla (`#`) para reemplazar 0 o más cadenas. Por ejemplo, `customer.*` filtraría por `customer.create` y `customer.delete`, pero no `customer.sent.email`. Sin embargo `customer.#` filtraría por `customer.create`,  `customer.delete`, y `customer.sent.email`.

- Una cola es un búfer que almacena mensajes.

- Un consumidor recibe mensajes. Sabe qué cola consumir. Puede asignar procesadores del mensaje a una cola específica.

También se puede configurar un sistema básico de cola de mensajes sin utilizar [!DNL RabbitMQ]. En este sistema, un adaptador MySQL almacena mensajes en la base de datos. Tres tablas de base de datos (`queue`, `queue_message`, y `queue_message_status`) administrar la carga de trabajo de la cola de mensajes. Los trabajos de Cron garantizan que los consumidores puedan recibir mensajes. Esta solución no es muy escalable. [!DNL RabbitMQ] debe utilizarse siempre que sea posible.
