---
title: La ficha [!UICONTROL [!DNL RabbitMQ]
description: Obtenga información acerca de la ficha [!UICONTROL [!DNL RabbitMQ] de  [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# La ficha [!UICONTROL [!DNL RabbitMQ]]

La ficha **[!UICONTROL [!DNL RabbitMQ]]** tiene información que se centra en [!DNL RabbitMQ] señales.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] eventos de infraestructura](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

El fotograma **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** muestra eventos de infraestructura que involucran [!DNL RabbitMQ] que ocurrieron en el periodo de tiempo seleccionado:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) como `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) como `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) como `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) como `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) como `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) como `node2_timeout_exceeded`
* `%401 Unauthorized%`) como `401_unauth`
* `%401 Unauthorized%`) como `401_unauth`
* `%Service restarted: rabbitmq-server%`) como `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) como `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) como `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) como `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) como `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) como `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) como `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) como `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) como `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) como `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) como `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] señales de inicio/parada del servicio](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Este fotograma muestra [!DNL RabbitMQ] señales de inicio/detención del servicio que ocurrieron durante el intervalo de tiempo seleccionado:

* `%RabbitMQ is asked to stop...%`) como `rabbitmq_stop`
* `%Starting RabbitMQ%`) como `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errores](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Este fotograma muestra [!DNL RabbitMQ] errores que se produjeron durante el intervalo de tiempo seleccionado:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` como `exit_timeout`
* `%client unexpectedly closed TCP connection%`) como `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) como `undef_exit`
* `%Connection attempt from disallowed node%`) como `disallowed_node`
* `%closing AMQP connection%`) como `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] estado de nodo](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) como `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) como `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) como `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) como `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) como `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) como `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] estado de resumen de alto nivel de mensaje por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

El gráfico **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** muestra el número de mensajes publicados por la cola [!DNL RabbitMQ] para el periodo de tiempo seleccionado.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] resumen de detalles de mensaje](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) como `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) como `queue_err`
* `%authenticated and granted access to vhost%`) como `auth`
* `%closing AMQP connection%`) como `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg) de consumo de cola

El gráfico **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** muestra el número de bytes consumidos por cada cola [!DNL RabbitMQ] durante el periodo de tiempo seleccionado.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] mensajes publicados por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

El gráfico **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** muestra el número de bytes consumidos por cada cola [!DNL RabbitMQ] durante el periodo de tiempo seleccionado.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Rendimiento de mensajes publicados por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

El gráfico **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** muestra el número promedio de mensajes publicados por segundo por cada cola [!DNL RabbitMQ] durante el intervalo de tiempo seleccionado.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Rendimiento total del mensaje por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

El gráfico **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** muestra el número total promedio de mensajes por segundo en cada cola [!DNL RabbitMQ] durante el intervalo de tiempo seleccionado.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] consumidores por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

El gráfico **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** muestra el número total promedio de consumidores por cada cola [!DNL RabbitMQ] durante el periodo de tiempo seleccionado.
