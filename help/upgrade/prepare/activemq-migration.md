---
title: Migrar de RabbitMQ a ActiveMQ
description: Obtenga información sobre cómo reemplazar el agente de cola de mensajes que se utiliza para las instalaciones locales de Adobe Commerce.
feature: Services, Configuration
source-git-commit: 8f57a4fa7744f4647ab96d0fcfae08b8eb4927c6
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# Migración a ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis) es un agente de mensajes multiprotocolo de alto rendimiento que proporciona una alternativa a RabbitMQ para gestionar colas de mensajes en Adobe Commerce.

A partir de las versiones 2.4.8-p3, 2.4.7-p8 y 2.4.6-p13, Adobe Commerce admite ActiveMQ como agente de cola de mensajes. Esto proporciona flexibilidad adicional para que las instalaciones locales puedan elegir entre RabbitMQ y ActiveMQ en función de sus requisitos de infraestructura y experiencia.

## Antes de empezar

Antes de iniciar la migración, asegúrese de lo siguiente:

1. Revise la configuración actual de RabbitMQ en `app/etc/env.php`.
1. Realice una copia de seguridad completa de la base de datos y del código base.
1. Asegúrese de que la instalación cumple los requisitos del sistema para ActiveMQ.
1. Planifique una ventana de mantenimiento para completar la migración.

## Ruta de migración

La migración a ActiveMQ es un proceso directo, pero es esencial asegurarse de que todos los mensajes pendientes se procesen antes de cambiar de agente.

Estas instrucciones de migración suponen que Adobe Commerce es la única aplicación que utiliza el agente de cola de mensajes.

### Paso 1: Coloque el sitio en modo de mantenimiento

1. Coloque el sitio en [Modo de mantenimiento](../../installation/tutorials/maintenance-mode.md):

   ```bash
   bin/magento maintenance:enable
   ```

1. Verificar que el modo de mantenimiento esté activado:

   ```bash
   bin/magento maintenance:status
   ```

### Paso 2: Comprobar los recuentos de mensajes de RabbitMQ

Antes de continuar, compruebe que todos los mensajes de RabbitMQ se hayan procesado. Utilice uno de los siguientes métodos:

#### Método A: Uso de RabbitMQ Management Dashboard

1. Acceder a la interfaz de usuario de administración de RabbitMQ en `http://<host>:15672`
1. Credenciales predeterminadas: `guest/guest`
1. Vaya a la ficha **Colas**
1. Comprobar que todas las colas muestran **0 mensajes**

   ![Panel de administración de RabbitMQ](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### Método B: Uso de la línea de comandos rabbitmqctl

1. Compruebe todas las colas y sus recuentos de mensajes:

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="Salida CLI de RabbitMQ" width="500" />

1. Comprobar información detallada de la cola:

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="Salida detallada de la CLI de RabbitMQ" width="500" />

### Paso 3: Procesar mensajes pendientes

Si los mensajes están pendientes en cualquier cola, procesarlos antes de continuar.

1. Obtenga la lista de consumidores disponibles:

   ```bash
   bin/magento queue:consumers:list
   ```

1. Procesar consumidores como grupo o por cola de mensajes individual:

   - **Procesar consumidores como grupo**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Si cron ya se está ejecutando en el sistema, no necesita ejecutar `bin/magento cron:run --group=consumers` manualmente. En su lugar, compruebe que los mensajes se están procesando comprobando el recuento de mensajes mediante los comandos del paso 2.

   - **Procesar una cola de mensajes específica**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     Por ejemplo, para procesar operaciones asincrónicas:

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >El parámetro `--max-messages` limita el número de mensajes que se deben procesar antes de que se detenga el consumidor. Ajuste este valor en función del tamaño de la cola.

   - **Supervisar el procesamiento de mensajes**

     Compruebe continuamente los recuentos de mensajes hasta que todas las colas estén vacías:

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### Paso 4: Verificar que se procesan todos los mensajes

Antes de continuar con el siguiente paso, asegúrese de que **todas las colas muestran 0 mensajes**. Ejecute de nuevo los comandos de verificación del paso 2.

>[!WARNING]
>
>No continúe con el siguiente paso si algún mensaje permanece sin procesar. Puede producirse una pérdida de datos si cambia de agente mientras los mensajes siguen pendientes.

### Paso 5: Detener a los consumidores y los trabajos crónicos

1. Detener todos los consumidores de colas de mensajes en ejecución:

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. Deshabilitar trabajos cron:

   ```bash
   bin/magento cron:remove
   ```

1. Verifique que se eliminen los trabajos cron:

   ```bash
   crontab -l
   ```

### Paso 6: Copia de seguridad de la configuración actual

Cree una copia de seguridad de la configuración actual:

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### Paso 7: Desinstalar RabbitMQ de forma opcional

Puede desinstalar RabbitMQ si ya no es necesario.

### Paso 8: Instalar y configurar ActiveMQ en Adobe Commerce

Para completar las tareas de instalación y configuración de ActiveMQ, como configurar el protocolo STOMP y comprobar la conexión, consulte la [Guía de instalación y configuración](../../installation/prerequisites/activemq.md).

### Paso 9: Reinstalar los trabajos de cron

1. Una vez finalizada correctamente la prueba, vuelva a instalar los trabajos cron:

   ```bash
   bin/magento cron:install
   ```

1. Compruebe que los trabajos cron estén programados:

   ```bash
   crontab -l
   ```

### Paso 10: Desactivar el modo de mantenimiento

1. Después de comprobar que todo funciona correctamente, desactive el modo de mantenimiento:

   ```bash
   bin/magento maintenance:disable
   ```

1. Compruebe que el modo de mantenimiento está desactivado:

   ```bash
   bin/magento maintenance:status
   ```

### Paso 11: Monitorización del sistema

Supervise el sistema durante 24 a 48 horas después de la migración para asegurarse de que todas las operaciones en cola funcionan correctamente:

- Consulte la consola web de ActiveMQ regularmente para ver el rendimiento de los mensajes
- Supervisar los registros de aplicaciones en busca de errores relacionados con las colas
- Compruebe que las operaciones asincrónicas (configuración, guardados, exportaciones, etc.) funcionan
- Compruebe los registros de cron para asegurarse de que los consumidores están ejecutando

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Reversión

Si se producen problemas durante o después de la migración, puede volver a RabbitMQ:

1. Activar modo de mantenimiento:

   ```bash
   bin/magento maintenance:enable
   ```

1. Detenga a todos los consumidores y deshabilite cron:

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. Restaure la configuración anterior:

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. Iniciar RabbitMQ (si está detenido):

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. Borrar caché:

   ```bash
   bin/magento cache:flush
   ```

1. Vuelva a instalar cron:

   ```bash
   bin/magento cron:install
   ```

1. Desactivar el modo de mantenimiento:

   ```bash
   bin/magento maintenance:disable
   ```

No es necesario realizar más cambios en el valor de configuración una vez completada la migración.

