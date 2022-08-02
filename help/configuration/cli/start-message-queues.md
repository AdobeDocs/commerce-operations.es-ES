---
title: Iniciar consumidores de cola de mensajes
description: Obtenga información sobre cómo iniciar un consumidor de cola de mensajes.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Iniciar consumidores de cola de mensajes

{{file-system-owner}}

Debe iniciar un consumidor de cola de mensajes para habilitar operaciones asincrónicas como acciones masivas de Inventory management y extremos masivos y asíncronos de REST. Para habilitar la funcionalidad B2B, debe iniciar varios consumidores. Los módulos de terceros también pueden requerir el inicio de un consumidor personalizado.

Para ver una lista de todos los consumidores:

```bash
bin/magento queue:consumers:list
```

Para iniciar los consumidores de cola de mensajes:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Después de consumir todos los mensajes disponibles, el comando finaliza. Puede ejecutar el comando de nuevo manualmente o con un trabajo cron. También puede ejecutar varias instancias del `magento queue:consumers:start` para procesar colas de mensajes grandes. Por ejemplo, puede anexar `&` al comando para ejecutarlo en segundo plano, vuelva a un símbolo del sistema y continúe ejecutando comandos:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Consulte [cola:consumers:start](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#queueconsumersstart) en la sección Comercio de _Referencia de herramientas de la línea de comandos_ para obtener más información sobre las opciones, los parámetros y los valores de los comandos.

>[!INFO]
>
>La variable `--multi-process` está presente en la variable `queue:consumers:start` pero para ejecutar consumidores con procesos paralelos, configure la variable [`multiple_processes`](../queues/manage-message-queues.md#configuration) en `/app/etc/env.php`. De lo contrario, si `queue:consumers:start` se llama con la función `--multi-process` , solo funciona en un solo subproceso.
