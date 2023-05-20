---
title: Configuración de la cola de mensajes de Amazon
description: Aprenda a configurar Commerce para que utilice el servicio AWS MQ.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Configuración de la cola de mensajes de Amazon

A partir de Commerce 2.4.3, Amazon Message Queue (MQ) está disponible como un reemplazo listo para la nube para instancias de cola de mensajes locales.

Para crear una cola de mensajes en AWS, consulte [Configuración de Amazon MQ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) en el _Documentación de AWS_.

## Configuración de Commerce para AWS MQ

Para conectarse al servicio AWS MQ, configure el `queue.amqp` objeto en el `env.php` archivo.
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

- `host`: URL del extremo AMQP; disponible haciendo clic en el nombre del agente en AWS (elimine &quot;https://&quot; y el número de puerto final).
- `user`: el valor de nombre de usuario introducido al crear AWS MQ Broker
- `password`: el valor de contraseña introducido al crear AWS MQ Broker

>[!INFO]
>
>Amazon MQ solo admite conexiones TLS. No se admite la verificación de igual a igual.

Después de editar el `env.php` , ejecute el siguiente comando para finalizar la instalación:

```bash
bin/magento setup:upgrade
```

## Cómo utiliza Commerce el servicio AWS MQ

El `async.operations.all` el consumidor de cola de mensajes utiliza la conexión AMQP.

Este consumidor enruta cualquier nombre de tema con el prefijo `async` a través de la conexión de AWS MQ.

Por ejemplo, en `InventoryCatalog` existen:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

La configuración predeterminada para `InventoryCatalog` no publica mensajes en [!DNL RabbitMQ]; el comportamiento predeterminado es realizar la acción en el mismo subproceso de usuario. Para saber `InventoryCatalog` para publicar mensajes, habilite `cataloginventory/bulk_operations/async`. Desde el administrador, vaya a **Tiendas** > Configuración > **Catálogo** > **Inventario** > Administración de operaciones masivas y configuración  `Run asynchronously`hasta **Sí**.

## Prueba de la cola de mensajes

Para probar el envío de mensajes de Commerce a [!DNL RabbitMQ]:

1. Inicie sesión en [!DNL RabbitMQ] consola web en AWS para monitorizar las colas.
1. En el Administrador, cree un producto.
1. Crear un origen de inventario.
1. Activar **Tiendas** > Configuración > **Catálogo** > **Inventario** > Operaciones masivas de administración > Ejecutar asincrónicamente.
1. Ir a **Catálogo** > Productos. En la cuadrícula, seleccione el producto creado anteriormente y haga clic en **Asignar origen de inventario**.
1. Clic **Guardar y cerrar** para completar el proceso.

   Ahora debería ver los mensajes que aparecen en la [!DNL RabbitMQ] consola web.

1. Inicie el `async.operations.all` consumidor de cola de mensajes.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Ahora debería ver que el mensaje en cola se procesa en la [!DNL RabbitMQ] consola web.
Compruebe que los orígenes de inventario hayan cambiado en el producto en el Administrador.
