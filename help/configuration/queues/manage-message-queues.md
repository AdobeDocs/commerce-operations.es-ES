---
title: Administrar colas de mensajes
description: Obtenga información sobre cómo administrar colas de mensajes desde la línea de comandos para Adobe Commerce.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 8dce1f1e961ec02d7783a7423a51a7d4567dce79
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Administrar colas de mensajes

Puede administrar las colas de mensajes desde la línea de comandos mediante trabajos cron o un administrador de procesos externo para garantizar que los consumidores estén recuperando mensajes.

## Administración de procesos

Los trabajos de Cron son el mecanismo predeterminado para reiniciar a los consumidores. Los procesos iniciados por `cron` consumen el número especificado de mensajes y, a continuación, finalizan. Volver a ejecutar `cron` reinicia el consumidor.

El siguiente ejemplo muestra la configuración de `crontab` para consumidores en ejecución:

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
>La frecuencia con la que se comprueban las colas de mensajes puede depender de la lógica empresarial y de los recursos del sistema disponibles. En general, es posible que desee comprobar si hay nuevos clientes y enviar correos electrónicos de bienvenida con más frecuencia que un proceso que requiera más recursos, como actualizar el catálogo. Debe definir los horarios de `cron` de acuerdo con sus necesidades comerciales.
>
>Se puede configurar en las opciones de configuración Admin Stores > Settings > Configuration > Advanced > System > Cron para el grupo: consumidores.
>
>Consulte [Configurar y ejecutar cron](../cli/configure-cron-jobs.md) para obtener más información sobre el uso de `cron` con Commerce.

También puede usar un administrador de procesos como [Supervisor](https://supervisord.readthedocs.io/en/latest/) para supervisar el estado de los procesos. El administrador puede utilizar la línea de comandos para reiniciar los procesos según sea necesario.

## Configuración

### Comportamiento predeterminado

- El trabajo cron `consumers_runner` está habilitado
- El trabajo cron `consumers_runner` ejecuta todos los consumidores definidos
- Cada consumidor procesa 10000 mensajes y, a continuación, finaliza

>[!INFO]
>
>Si su tienda Adobe Commerce está alojada en la plataforma Cloud, use [`CRON_CONSUMERS_RUNNER`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es#cron_consumers_runner) para configurar el trabajo cron de `consumers_runner`.

### Configuración específica

Edite el archivo `/app/etc/env.php` para configurar el trabajo cron `consumers_runner`.

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

- `cron_run`: valor booleano que habilita o deshabilita el trabajo cron de `consumers_runner` (predeterminado = `true`).
- `max_messages`: el número máximo de mensajes que cada consumidor debe procesar antes de finalizar (predeterminado = `10000`). Aunque no lo recomendamos, puede utilizar 0 para evitar que el consumidor finalice. Consulte [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) para configurar el modo en que los consumidores procesan los mensajes de la cola de mensajes.
- `consumers`: matriz de cadenas que especifica qué consumidores se van a ejecutar. Una matriz vacía ejecuta *todos* los consumidores.
- `multiple_processes`: matriz de pares de clave-valor que especifica el consumidor que se ejecutará en cuántos procesos. Compatible con Commerce 2.4.4 o superior.

  >[!INFO]
  >
  >No se recomienda ejecutar varios consumidores en una cola operada por MySQL. Consulte [Cambiar la cola de mensajes de MySQL a AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) para obtener más información.

  >[!INFO]
  >
  >Si su tienda Adobe Commerce está alojada en la plataforma Cloud, use [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es#consumers_wait_for_max_messages) para configurar cómo procesan los consumidores los mensajes de la cola de mensajes.

Consulte [Iniciar consumidores de cola de mensajes](../cli/start-message-queues.md).
