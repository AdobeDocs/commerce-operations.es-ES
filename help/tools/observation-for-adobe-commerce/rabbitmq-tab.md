---
title: '"El [!UICONTROL RabbitMQ] tab"'
description: Obtenga información sobre [!UICONTROL RabbitMQ] pestaña [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# La variable [!UICONTROL RabbitMQ] ficha

La variable **[!UICONTROL RabbitMQ]** tiene información centrada en [!DNL RabbitMQ] señales.

## [!UICONTROL RabbitMQ Infrastructure events]

![Eventos de infraestructura de RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

La variable **[!UICONTROL RabbitMQ Infrastructure events]** frame muestra los eventos de infraestructura que implican [!DNL RabbitMQ] que se produjeron en el intervalo de tiempo seleccionado:

* %Response [error] para el nodo [rabbit@host1]: respuesta http inesperada de%) como &#39;inesperado_resp_node1&#39;
* &#39;%Respuesta [error] para el nodo [rabbit@host2]: respuesta http inesperada de%) como &#39;inesperado_resp_node2&#39;
* &#39;%Respuesta [error] para el nodo [rabbit@host3]: respuesta http inesperada de%) como &#39;inesperado_resp_node3&#39;
* &#39;%Respuesta [error] para el nodo [rabbit@host3]: Obtenga &quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot;: límite de contexto excedido%) como &#39;node3_timeout_expanded&#39;
* &#39;%Respuesta [error] para el nodo [rabbit@host1]: Obtenga &quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot;: límite de contexto excedido%) como &#39;node1_timeout_expanded&#39;
* &#39;%Respuesta [error] para el nodo [rabbit@host2]: Obtenga &quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot;: límite de contexto excedido%) como &#39;node2_timeout_expanded&#39;
* &#39;%401 (no autorizado%) como &#39;401_unauth&#39;
* &#39;%401 No autorizado%&#39;) como &#39;401_unauth&#39;
* %Service reiniciado: rabbitmq-server%&#39;) como &#39;rmq_service_restart&#39;
* &#39;%Respuesta [failed] para el nodo [rabbit@host1]: nodedown%&#39;) como &#39;rmq_node1_down&#39;
* &#39;%Respuesta [failed] para el nodo [rabbit@host2]: nodedown%&#39;) como &#39;rmq_node2_down&#39;
* &#39;%Respuesta [failed] para el nodo [rabbit@host2]: nodedown%&#39;) como &#39;rmq_node2_down&#39;
* &#39;%Entidad modificada: exchange/bindings.destination%&#39;) como &#39;rmq_entity_modified&#39;
* &#39;%Entidad modificada: exchange/bindings.destination%&#39;) como &#39;rmq_entity_modified&#39;
* &#39;%Entidad modificada: queue/exclusivo%&#39;) como &#39;rmq_entity_created_q_exclusivo&#39;&#39;%Entidad modificada: queue/auto_delete%&#39;) como &#39;rmq_entity_q_delete&#39;
* &#39;%Entidad modificada: queue/durable%&#39;) como &#39;rmq_entity_modified_q_durable&#39;
* &#39;%Entidad modificada: version/management%&#39;) como &#39;rmq_entity_modified_ver_mgt&#39;
* &#39;%Entidad modificada: version/management%&#39;) como &#39;rmq_entity_modified_ver_mgt&#39;

## [!UICONTROL RabbitMQ service start/stop signals]

![Señales de inicio/parada del servicio RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Este marco muestra [!DNL RabbitMQ] señales de inicio/parada del servicio que se produjeron durante el intervalo de tiempo seleccionado:

* Se pide que se detenga &#39;%RabbitMQ...%&#39;) como &#39;rabbitmq_stop&#39;
* &#39;%Iniciando RabbitMQ%&#39;) como &#39;rabbitmq_start&#39;

## [!UICONTROL RabbitMQ errors]

![Errores de RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Este marco muestra [!DNL RabbitMQ] errores que se produjeron durante el intervalo de tiempo seleccionado:

* &#39;%exit con el motivo {case_subscription,timeout} y stacktrace {rabbit_mgmt_wm_health_check%&#39;} como &#39;exit_timeout&#39;
* &#39;%client cerró inesperadamente la conexión TCP%&#39;) como &#39;client_closed_tcp_conn&#39;
* &#39;%at undefined exit with reason shutdown in context shutdown_error%&#39;) como &#39;undef_exit&#39;
* &#39;%Intento de conexión del nodo no permitido%&#39;) como &#39;disallowed_node&#39;
* &#39;%cerrando conexión AMQP%&#39;) como &#39;rmq_err_amqp_conn&#39;

## [!UICONTROL RabbitMQ node status]

![Estado del nodo RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* &#39;%rabbit en el nodo rabbit@host1 down%&#39;) como &#39;rmq_node1_down&#39;
* &#39;%rabbit en el nodo rabbit@host2 down%&#39;) como &#39;rmq_node2_down&#39;
* &#39;%rabbit en el nodo rabbit@host3 down%&#39;) como &#39;rmq_node3_down&#39;
* &#39;%rabbit en el nodo rabbit@host1 up%&#39;) como &#39;rmq_node1_up&#39;
* &#39;%rabbit en el nodo rabbit@host2 up%&#39;) como &#39;rmq_node2_up&#39;
* &#39;%rabbit en el nodo rabbit@host3 up%&#39;) como &#39;rmq_node3_up&#39;

## [!UICONTROL RabbitMQ Message High-Level Summary status by Queue]

![Estado de resumen de alto nivel del mensaje RabbitMQ por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

La variable **[!UICONTROL RabbitMQ Message High-Level Summary status by Queue]** El gráfico muestra el número de mensajes publicados por el [!DNL RabbitMQ] para el intervalo de tiempo seleccionado.

## [!UICONTROL RabbitMQ Message Detail Summary]

![Resumen de detalles de mensajes de RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* &#39;%report.ERROR: Cron Job Consumer_runner tiene un error: NOT_FOUND - sin queue%&#39;) como &#39;queue_err&#39;
* &#39;%report.ERROR: Cron Job Consumer_runner tiene un error: NOT_FOUND - sin queue%&#39;) como &#39;queue_err&#39;
* &#39;%autenticado y acceso concedido a vhost%&#39;) como &#39;auth&#39;
* &#39;%cerrando conexión AMQP%&#39;) como &#39;close_conn&#39;

## [!UICONTROL RabbitMQ Queue Consumption MB]

![Consumo de cola RabbitMQ MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

La variable **[!UICONTROL RabbitMQ Queue Consumption MB]** el gráfico muestra la cantidad de bytes consumidos por cada [!DNL RabbitMQ] en el intervalo de tiempo seleccionado.

## [!UICONTROL RabbitMQ Published Messages by Queue]

![Mensajes publicados de RabbitMQ por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

La variable **[!UICONTROL RabbitMQ Published Messages by Queue]** el gráfico muestra la cantidad de bytes consumidos por cada [!DNL RabbitMQ] en el intervalo de tiempo seleccionado.

## [!UICONTROL RabbitMQ Published Message Throughput by Queue]

![Rendimiento de mensajes publicados de RabbitMQ por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

La variable **[!UICONTROL RabbitMQ Published Message Throughput by Queue]** El gráfico muestra el número promedio de mensajes publicados por segundo por cada [!DNL RabbitMQ] en el intervalo de tiempo seleccionado.

## [!UICONTROL RabbitMQ Total Message Throughput by Queue]

![Rendimiento total del mensaje RabbitMQ por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

La variable **[!UICONTROL RabbitMQ Total Message Throughput by Queue]** el gráfico muestra el número total promedio de mensajes por segundo por cada [!DNL RabbitMQ] en el intervalo de tiempo seleccionado.

## [!UICONTROL RabbitMQ Consumers by Queue]

![Consumidores RabbitMQ por cola](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

La variable **[!UICONTROL RabbitMQ Consumers by Queue]** el gráfico muestra el número total promedio de consumidores por cada [!DNL RabbitMQ] en el intervalo de tiempo seleccionado.