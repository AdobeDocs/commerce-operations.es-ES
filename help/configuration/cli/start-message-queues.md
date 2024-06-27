---
title: Iniciar consumidores de cola de mensajes
description: Obtenga información sobre cómo iniciar un consumidor de cola de mensajes.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Iniciar consumidores de cola de mensajes

{{file-system-owner}}

Debe iniciar un [consumidor de cola de mensajes](../queues/consumers.md) para habilitar operaciones asincrónicas como acciones masivas de Inventory management y extremos masivos y asincrónicos de REST. Para habilitar la funcionalidad B2B, debe iniciar varios consumidores. Los módulos de terceros también pueden requerir que inicie un consumidor personalizado.

Para ver una lista de todos los consumidores:

```bash
bin/magento queue:consumers:list
```

Para iniciar consumidores de cola de mensajes:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Después de consumir todos los mensajes disponibles, el comando finaliza. Puede volver a ejecutar el comando manualmente o con un trabajo cron. También puede ejecutar varias instancias del `magento queue:consumers:start` para procesar colas de mensajes grandes. Por ejemplo, puede anexar `&` para ejecutar el comando en segundo plano, vuelva a un símbolo del sistema y continúe ejecutando los comandos:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Consulte [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) en la sección Commerce de _Referencia de herramientas de la línea de comandos_ para obtener más información acerca de las opciones, los parámetros y los valores de los comandos.

>[!INFO]
>
>El `--multi-process` está presente en el `queue:consumers:start` , pero para ejecutar consumidores con procesos paralelos, configure el [`multiple_processes`](../queues/manage-message-queues.md#configuration) opción en `/app/etc/env.php`. De lo contrario, si `queue:consumers:start` se llama con el `--multi-process` , solo funciona en un único subproceso.
