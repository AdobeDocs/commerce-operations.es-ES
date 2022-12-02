---
title: Administrar colas de mensajes
description: Obtenga información sobre cómo administrar las colas de mensajes desde la línea de comandos para Adobe Commerce.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Administrar colas de mensajes

Puede administrar las colas de mensajes desde la línea de comandos mediante trabajos cron o un administrador de procesos externo para asegurarse de que los consumidores estén recuperando mensajes.

## Administración de procesos

Los trabajos cron son el mecanismo predeterminado para reiniciar a los consumidores. Procesos iniciados por `cron` consuma el número especificado de mensajes y luego termine. Volver a ejecutar `cron` reinicia al consumidor.

El siguiente ejemplo muestra la variable `crontab` configuración para ejecutar consumidores:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>La frecuencia con la que comprueba las colas de mensajes depende de la lógica empresarial y de los recursos del sistema disponibles. En general, es posible que desee buscar nuevos clientes y enviar correos electrónicos de bienvenida con más frecuencia que con un proceso que consume más recursos, como actualizar el catálogo. Debe definir `cron` programaciones según sus necesidades comerciales.
>
>Se puede configurar en las opciones de configuración de Administración > Configuración > Avanzado > Sistema > Cron del grupo: consumidores.
>
>Consulte [Configuración y ejecución de cron](../cli/configure-cron-jobs.md) para obtener más información sobre el uso de `cron` con Commerce.

También puede utilizar un administrador de procesos como [Supervisor](http://supervisord.org/index.html) para controlar el estado de los procesos. El administrador puede utilizar la línea de comandos para reiniciar los procesos según sea necesario.

## Configuración

### Comportamiento de forma predeterminada

- Trabajo cron `consumers_runner` está habilitado
- Trabajo cron `consumers_runner` ejecuta todos los consumidores definidos
- Cada consumidor procesa 10000 mensajes y luego finaliza

>[!INFO]
>
>Si la tienda de Adobe Commerce está alojada en la plataforma de Cloud, use la variable [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) para configurar la variable `consumers_runner` trabajo de cron.

### Configuración específica

Edite el `/app/etc/env.php` para configurar el trabajo cron `consumers_runner`.

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Un valor booleano que habilita o deshabilita la variable `consumers_runner` trabajo cron (predeterminado = `true`).
- `max_messages` - El número máximo de mensajes que cada consumidor debe procesar antes de finalizar (predeterminado = `10000`). Aunque no se recomienda, puede utilizar 0 para evitar que el consumidor finalice. Consulte [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) para configurar el modo en que los consumidores procesan los mensajes desde la cola de mensajes.
- `consumers` : matriz de cadenas que especifican qué consumidores se van a ejecutar. Se ejecuta una matriz vacía *all* consumidores.
- `multiple_processes` : matriz de pares de clave-valor que especifica qué consumidor ejecutar en cuántos procesos.

   >[!INFO]
   >
   >No se recomienda ejecutar varios consumidores en una cola operada por MySQL. Consulte [Cambiar la cola de mensajes de MySQL a AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) para obtener más información.

   >[!INFO]
   >
   >Si la tienda de Adobe Commerce está alojada en la plataforma de Cloud, use la variable [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) para configurar el modo en que los consumidores procesan los mensajes desde la cola de mensajes.

Consulte [Iniciar consumidores de cola de mensajes](../cli/start-message-queues.md).
