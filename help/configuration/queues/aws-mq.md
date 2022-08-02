---
title: Configurar la cola de mensajes de Amazon
description: Aprenda a configurar Commerce para utilizar el servicio AWS MQ.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Configurar la cola de mensajes de Amazon

A partir de Commerce 2.4.3, la cola de mensajes de Amazon (MQ) está disponible como un reemplazo listo para la nube para las instancias de cola de mensajes locales.

Para crear una cola de mensajes en AWS, consulte [Configuración de Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) en el _Documentación de AWS_.

## Configuración de Commerce para AWS MQ

Para conectarse al servicio de AWS MQ, configure la variable `queue.amqp` en el `env.php` archivo.
La cola de mensajes de AWS requiere una conexión SSL/TLS.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Donde:

- `host`: la dirección URL del extremo AMQP; disponible haciendo clic en el nombre del agente en AWS (elimine &quot;https://&quot; y el número de puerto final)
- `user`: el valor de nombre de usuario introducido al crear AWS MQ Broker
- `password`: el valor de la contraseña introducido al crear el agente de AWS MQ.

>[!INFO]
>
>Amazon MQ solo admite conexiones TLS. No se admite la verificación por pares.

Después de editar la variable `env.php` ejecute el siguiente comando para finalizar la configuración:

```bash
bin/magento setup:upgrade
```

## Cómo utiliza Commerce el servicio AWS MQ

La variable `async.operations.all` el consumidor de cola de mensajes utiliza la conexión AMQP.

Este consumidor enruta cualquier nombre de tema con el prefijo `async` a través de la conexión de AWS MQ.

Por ejemplo, en `InventoryCatalog` hay:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

La configuración predeterminada para `InventoryCatalog` no publica mensajes en RabbitMQ; el comportamiento predeterminado es realizar la acción en el mismo subproceso de usuario. Para decir `InventoryCatalog` para publicar mensajes, habilite `cataloginventory/bulk_operations/async`. Desde el administrador, vaya a **Almacenes** > Configuración > **Catálogo** > **Inventario** > Administración de operaciones masivas y configuración  `Run asynchronously`a **Sí**.

## Prueba de la cola de mensajes

Para probar el envío de mensajes desde Commerce a RabbitMQ:

1. Inicie sesión en la consola web RabbitMQ en AWS para monitorizar las colas.
1. En Administración, cree un producto.
1. Crear un origen de inventario.
1. Habilitar **Almacenes** > Configuración > **Catálogo** > **Inventario** > Operaciones masivas de administración > Ejecutar asincrónicamente.
1. Vaya a **Catálogo** > Productos. En la cuadrícula, seleccione el producto creado anteriormente y haga clic en **Asignar origen de inventario**.
1. Haga clic en **Guardar y cerrar** para completar el proceso.

   Ahora debería ver los mensajes que aparecen en la consola web de RabbitMQ.

1. Inicie el `async.operations.all` consumidor de cola de mensajes.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Ahora debería ver que el mensaje en cola se procesa en la consola web de RabbitMQ.
Compruebe que las fuentes de inventario hayan cambiado en el producto en el Administrador.
