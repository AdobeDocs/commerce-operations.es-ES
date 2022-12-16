---
title: Información general sobre las colas de mensajes
description: Obtenga información sobre el marco de la cola de mensajes y cómo funciona con la aplicación Adobe Commerce y Magento Open Source.
source-git-commit: 78ad565f051f254229424ddcdb8ce633d3a78ec6
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Resumen de las colas de mensajes

El marco de cola de mensajes (MQF) es un sistema que permite un [módulo](https://glossary.magento.com/module) para publicar mensajes en las colas. También define el [consumidores](consumers.md) que recibirá los mensajes de forma asíncrona. El MQF utiliza [[!DNL RabbitMQ]](https://www.rabbitmq.com) como agente de mensajería, que proporciona una plataforma escalable para enviar y recibir mensajes. También incluye un mecanismo para almacenar los mensajes no enviados. [!DNL RabbitMQ] se basa en la especificación del Protocolo avanzado de Message Queue Server (AMQP) 0.9.1.

El diagrama siguiente ilustra el marco de cola de mensajes:

![Marco de cola de mensajes](../../assets/configuration/mq-framework.png)

- A [publisher](https://glossary.magento.com/publisher-subscriber-pattern) es un componente que envía mensajes a un intercambio. Sabe a qué intercambio se debe publicar y el formato de los mensajes que envía.

- Un intercambio recibe mensajes de editores y los envía a colas. Aunque [!DNL RabbitMQ] admite varios tipos de intercambios, Commerce solo utiliza intercambios de temas. Un tema incluye una clave de enrutamiento, que contiene cadenas de texto separadas por puntos. El formato del nombre de un tema es `string1.string2`: por ejemplo, `customer.created` o `customer.sent.email`.

   El agente de bolsa le permite utilizar caracteres comodín al configurar reglas para el reenvío de mensajes. Puede usar un asterisco (`*`) para reemplazar _one_ cadena o signo de almohadilla (`#`) para reemplazar 0 o más cadenas. Por ejemplo, `customer.*` filtrar por `customer.create` y `customer.delete`, pero no `customer.sent.email`. Sin embargo `customer.#` filtrar por `customer.create`,  `customer.delete`y `customer.sent.email`.

- Una cola es un búfer que almacena mensajes.

- Un consumidor recibe mensajes. Sabe qué cola consumir. Puede asignar procesadores del mensaje a una cola específica.

También se puede configurar un sistema de cola de mensajes básico sin usar [!DNL RabbitMQ]. En este sistema, un MySQL [adaptador](https://glossary.magento.com/adapter) almacena mensajes en la base de datos. Tres tablas de base de datos (`queue`, `queue_message`y `queue_message_status`) administre la carga de trabajo de la cola de mensajes. Los trabajos cron garantizan que los consumidores puedan recibir mensajes. Esta solución no es muy escalable. [!DNL RabbitMQ] debe utilizarse siempre que sea posible.
