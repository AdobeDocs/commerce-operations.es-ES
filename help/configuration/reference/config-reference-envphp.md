---
title: referencia env.php
description: Consulte una lista de valores para el archivo env.php .
source-git-commit: fe5e16d44213d1864a62230029e9e206eecd1717
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# referencia env.php

La variable `env.php` contiene las siguientes secciones:

| Nombre | Descripción |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Configuración del área de administración |
| `cache` | Configurar la página de redireccionamiento y la caché predeterminada |
| `cache_types` | Configuración de almacenamiento en caché |
| `consumers_wait_for_messages` | Configurar el modo en que los consumidores procesan los mensajes desde la cola de mensajes |
| `cron` | Habilitar o deshabilitar los trabajos cron |
| `crypt` | La clave de cifrado para las funciones criptográficas |
| `db` | Configuración de conexión de base de datos |
| `default_connection` | Conexión predeterminada de colas de mensajes |
| `directories` | Configuración de asignación de directorios de comercio |
| `downloadable_domains` | Lista de dominios descargables |
| `install` | La fecha de instalación |
| `lock` | Bloquear configuración del proveedor |
| `MAGE_MODE` | La variable [modo de aplicación](../bootstrap/application-modes.md) |
| `queue` | [Cola de mensajes](../queues/manage-message-queues.md) configuración |
| `resource` | Asignación del nombre del recurso a una conexión |
| `session` | Datos de almacenamiento de sesión |
| `system` | Desactiva el campo para editarlo en el administrador |
| `x-frame-options` | Configuración para [x-frame-options][x-frame-options] |

## backend

Configure las variables **frontName** para la URL de administración de comercio usando la variable `backend` en env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configurar la página de redireccionamiento y el almacenamiento en caché predeterminado mediante `cache` en el `env.php` archivo.

```conf
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
]
```

Obtenga más información en [Configuración de Redis](../cache/redis-pg-cache.md).

## cache_types

Todas las configuraciones de tipos de caché están disponibles desde este nodo.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

Más información sobre diferentes [Tipos de caché](../cli/manage-cache.md).

## customer_wait_for_messages

Especifique si los consumidores deben continuar sondeando los mensajes si el número de mensajes procesados es menor que el `max_messages` valor. El valor predeterminado es `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Estas son las opciones disponibles:

- `1`: los consumidores siguen procesando mensajes desde la cola de mensajes hasta que llegan al `max_messages` valor especificado en la variable `env.php` antes de cerrar la conexión TCP y finalizar el proceso de consumidor. Si la cola se vacía antes de alcanzar la variable `max_messages` , el consumidor espera a que lleguen más mensajes.

   Recomendamos esta configuración para los grandes comerciantes porque se espera un flujo de mensajes constante y no es deseable que haya retrasos en el procesamiento.

- `0`: los consumidores procesan los mensajes disponibles en la cola, cierran la conexión TCP y finalizan. Los consumidores no esperan a que se introduzcan mensajes adicionales en la cola, aunque el número de mensajes procesados sea menor que el `max_messages` valor especificado en la variable `env.php` archivo. Esto puede ayudar a evitar problemas con los trabajos cron causados por retrasos largos en el procesamiento de la cola de mensajes.

   Recomendamos esta configuración para los comerciantes más pequeños que no esperan un flujo de mensajes constante y prefieren conservar los recursos informáticos a cambio de retrasos menores en el procesamiento cuando no podría haber mensajes durante días.

## cron

Habilite o deshabilite los trabajos cron para la aplicación Commerce. De forma predeterminada, los trabajos cron están habilitados. Para deshabilitarlos, agregue la variable `cron` para `env.php` y establezca el valor en `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Tenga cuidado cuando deshabilite los trabajos cron. Cuando están desactivados, los procesos esenciales requeridos por la aplicación Commerce no se ejecutarán.

Más información sobre [Crones](../cli/configure-cron-jobs.md).

## crypt

Commerce utiliza una clave de cifrado para proteger contraseñas y otros datos confidenciales. Esta clave se genera durante el proceso de instalación.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Más información sobre [Clave de cifrado](https://docs.magento.com/user-guide/system/encryption-key.html) en el _Guía del usuario de Commerce_.

## db

Todas las configuraciones de base de datos están disponibles en este nodo.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Define la conexión predeterminada para las colas de mensajes. El valor puede ser `db`, `amqp`o un sistema de cola personalizado como `redismq`. Si especifica cualquier valor que no sea `db`, el software de la cola de mensajes debe instalarse y configurarse primero. De lo contrario, los mensajes no se procesarán correctamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

If `queue/default_connection` se especifica en el sistema `env.php` , esta conexión se utiliza para todas las colas de mensajes a través del sistema, a menos que una conexión específica esté definida en un `queue_topology.xml`, `queue_publisher.xml` o `queue_consumer.xml` archivo.
Por ejemplo, si `queue/default_connection` es `amqp` en `env.php` pero `db` La conexión se especifica en los archivos XML de configuración de cola de un módulo, el módulo utilizará MySQL como agente de mensajes.

## directorios

Opciones opcionales de asignación de directorios que deben establecerse cuando el servidor web está configurado para servir la aplicación Commerce desde la `/pub` para [seguridad mejorada](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domains

Una lista de dominios descargables disponibles en este nodo. Se pueden agregar, eliminar o enumerar dominios adicionales mediante comandos CLI.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Más información sobre [Dominios descargables](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## instalar

La fecha de instalación de la aplicación Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## bloquear

La configuración del proveedor de bloqueo se configura con la variable `lock` nodo .

Más información sobre [Bloquear configuración del proveedor](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

El modo de implementación se puede configurar en este nodo.

```conf
'MAGE_MODE' => 'developer'
```

Más información sobre [modos de aplicación](../cli/set-mode.md).

## cola

Las configuraciones de cola de mensajes están disponibles en este nodo.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

Más información sobre [Cola de mensajes][message-queue].

## recurso

Los ajustes de configuración de recursos están disponibles en este nodo.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## session

Las configuraciones de sesión se almacenan en la variable `session` nodo .

```conf
'session' => [
  'save' => 'files'
],
```

Más información sobre [Sesión](../storage/sessions.md).

## x-frame-options

el encabezado x-frame-options se puede configurar usando este nodo.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Más información sobre [x-frame-options](../security/xframe-options.md).

## sistema

Con este nodo, Commerce bloquea los valores de configuración en la variable `env.php` y, a continuación, deshabilita el campo en el administrador.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

Obtenga más información en [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
