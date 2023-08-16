---
title: referencia env.php
description: Vea una lista de valores para el archivo env.php.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# referencia env.php

El `env.php` contiene las secciones siguientes:

| Nombre | Descripción |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Configuración del área de administración |
| `cache` | Configurar la página de reds y la caché predeterminada |
| `cache_types` | Configuración de almacenamiento en caché |
| `consumers_wait_for_messages` | Configurar cómo procesan los consumidores los mensajes de la cola de mensajes |
| `cron` | Habilitar o deshabilitar los trabajos cron |
| `crypt` | Clave de cifrado para funciones criptográficas |
| `db` | Configuración de conexión a base de datos |
| `default_connection` | Conexión predeterminada de colas de mensajes |
| `directories` | Configuración de asignación de directorios de Commerce |
| `downloadable_domains` | Lista de dominios descargables |
| `install` | La fecha de instalación |
| `lock` | Bloquear configuración del proveedor |
| `MAGE_MODE` | El [modo de aplicación](../bootstrap/application-modes.md) |
| `queue` | [Colas de mensajes](../queues/manage-message-queues.md) configuración |
| `resource` | Asignación del nombre del recurso a una conexión |
| `session` | Datos de almacenamiento de sesión |
| `system` | Deshabilita el campo para editarlo en el administrador |
| `x-frame-options` | Configuración para [x-frame-options][x-frame-options] |

## servidor

Configure las variables **frontName** para la URL de administración de Commerce mediante `backend` nodo en env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## escondrijo

Configurar el almacenamiento en caché predeterminado y de la página de redis mediante `cache` nodo en el `env.php` archivo.

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

Todas las configuraciones de tipos de caché están disponibles en este nodo.

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

Más información sobre las distintas [Tipos de caché](../cli/manage-cache.md).

## consumer_wait_for_messages

Especifique si los consumidores deben seguir encuestando mensajes si el número de mensajes procesados es menor que el `max_messages` valor. El valor predeterminado es `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Estas son las opciones disponibles:

- `1`: los consumidores continúan procesando mensajes de la cola de mensajes hasta alcanzar la `max_messages` valor especificado en `env.php` antes de cerrar la conexión TCP y finalizar el proceso de consumidor. Si la cola se vacía antes de alcanzar el `max_messages` , el consumidor espera a que lleguen más mensajes.

  Recomendamos esta configuración para los grandes comerciantes porque se espera un flujo de mensaje constante y los retrasos en el procesamiento no son deseables.

- `0`: los consumidores procesan los mensajes disponibles en la cola, cierran la conexión TCP y finalizan. Los consumidores no esperan a que los mensajes adicionales entren en la cola, aunque el número de mensajes procesados sea menor que el `max_messages` valor especificado en `env.php` archivo. Esto puede ayudar a evitar problemas con los trabajos cron causados por largos retrasos en el procesamiento de colas de mensajes.

  Recomendamos esta configuración para los comerciantes más pequeños que no esperan un flujo de mensajes constante y prefieren conservar los recursos informáticos a cambio de pequeños retrasos de procesamiento cuando no puede haber mensajes durante días.

## cron

Habilite o deshabilite los trabajos cron para la aplicación Commerce. De forma predeterminada, los trabajos cron están habilitados. Para deshabilitarlos, agregue la variable `cron` configuración de a la `env.php` y establezca el valor en `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Tenga cuidado al deshabilitar los trabajos cron. Cuando están desactivados, no se ejecutarán los procesos esenciales requeridos por la aplicación Commerce.

Más información sobre [Crons](../cli/configure-cron-jobs.md).

## cripta

Commerce utiliza una clave de cifrado para proteger las contraseñas y otros datos confidenciales. Esta clave se genera durante el proceso de instalación.

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

Define la conexión predeterminada para colas de mensajes. El valor puede ser `db`, `amqp`o un sistema de colas personalizado como `redismq`. Si especifica cualquier valor distinto de `db`, el software de cola de mensajes debe instalarse y configurarse primero. De lo contrario, los mensajes no se procesarán correctamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

If `queue/default_connection` se especifica en el sistema `env.php` , esta conexión se utiliza para todas las colas de mensajes a través del sistema, a menos que se defina una conexión específica en un `queue_topology.xml`, `queue_publisher.xml` o `queue_consumer.xml` archivo.
Por ejemplo, si `queue/default_connection` es `amqp` in `env.php` pero un `db` La conexión se especifica en los archivos XML de configuración de cola de un módulo, el módulo utilizará MySQL como intermediario de mensajes.

## directorios

Opciones opcionales de asignación de directorios que deben establecerse cuando el servidor web está configurado para ofrecer la aplicación de comercio desde el `/pub` directorio para [seguridad mejorada](../../installation/tutorials/docroot.md).

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

La configuración del proveedor de bloqueos se establece utilizando `lock` nodo.

Más información sobre [Bloquear configuración de proveedor](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

El modo de implementación se puede configurar en este nodo.

```conf
'MAGE_MODE' => 'developer'
```

Más información sobre [Modos de aplicación](../cli/set-mode.md).

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

## resource

Las opciones de configuración de recursos están disponibles en este nodo.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## sesión

Las configuraciones de sesión se almacenan en `session` nodo.

```conf
'session' => [
  'save' => 'files'
],
```

Más información sobre [Session](../storage/sessions.md).

## x-frame-options

El encabezado x-frame-options se puede configurar mediante este nodo.

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
