---
title: referencia env.php
description: Vea una lista de valores para el archivo env.php.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 26fac37405ad635f297b65415517451d5149e50f
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 0%

---

# referencia env.php

El archivo `env.php` contiene las siguientes secciones:

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
| `directories` | configuración de asignación de directorios de Commerce |
| `downloadable_domains` | Lista de dominios descargables |
| `install` | La fecha de instalación |
| `lock` | Bloquear configuración del proveedor |
| `MAGE_MODE` | El [modo de aplicación](../bootstrap/application-modes.md) |
| `queue` | Configuración de [colas de mensajes](../queues/manage-message-queues.md) |
| `resource` | Asignación del nombre del recurso a una conexión |
| `session` | Datos de almacenamiento de sesión |
| `system` | Deshabilita el campo para editarlo en el administrador |
| `x-frame-options` | Estableciendo para [x-frame-options][x-frame-options] |

## servidor

Configure **frontName** para la URL de administración de Commerce usando el nodo `backend` en env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## escondrijo

Configure la página redis y el almacenamiento en caché predeterminado mediante el nodo `cache` en el archivo `env.php`.

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

Más información sobre los [tipos de caché](../cli/manage-cache.md).

## consumer_wait_for_messages

Especifique si los consumidores deben continuar encuestando los mensajes si el número de mensajes procesados es menor que el valor `max_messages`. El valor predeterminado es `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Estas son las opciones disponibles:

- `1`: los consumidores continúan procesando mensajes de la cola de mensajes hasta alcanzar el valor `max_messages` especificado en el archivo `env.php` antes de cerrar la conexión TCP y finalizar el proceso de consumo. Si la cola se vacía antes de alcanzar el valor `max_messages`, el consumidor espera a que lleguen más mensajes.

  Recomendamos esta configuración para los grandes comerciantes porque se espera un flujo de mensaje constante y los retrasos en el procesamiento no son deseables.

- `0`: los consumidores procesan los mensajes disponibles en la cola, cierran la conexión TCP y finalizan. Los consumidores no esperan a que otros mensajes entren en la cola, aunque el número de mensajes procesados sea menor que el valor `max_messages` especificado en el archivo `env.php`. Esto puede ayudar a evitar problemas con los trabajos cron causados por largos retrasos en el procesamiento de colas de mensajes.

  Recomendamos esta configuración para los comerciantes más pequeños que no esperan un flujo de mensajes constante y prefieren conservar los recursos informáticos a cambio de pequeños retrasos de procesamiento cuando no puede haber mensajes durante días.

## cron

Habilite o deshabilite los trabajos cron para la aplicación de Commerce. De forma predeterminada, los trabajos cron están habilitados. Para deshabilitarlos, agregue la configuración de `cron` al archivo `env.php` y establezca el valor en `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Tenga cuidado al deshabilitar los trabajos cron. Cuando están desactivados, no se ejecutarán los procesos esenciales requeridos por la aplicación de Commerce.

Más información sobre [Crons](../cli/configure-cron-jobs.md).

## cripta

Commerce utiliza una clave de cifrado para proteger contraseñas y otros datos confidenciales. Esta clave se genera durante el proceso de instalación.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Obtenga más información acerca de la [clave de cifrado](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/security/encryption-key) en la _guía del usuario de Commerce_.

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

Define la conexión predeterminada para colas de mensajes. El valor puede ser `db`, `amqp` o un sistema de colas personalizado como `redismq`. Si especifica cualquier valor distinto de `db`, primero debe instalar y configurar el software de cola de mensajes. De lo contrario, los mensajes no se procesarán correctamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Si se especifica `queue/default_connection` en el archivo del sistema `env.php`, esta conexión se utiliza para todas las colas de mensajes a través del sistema, a menos que se defina una conexión específica en un archivo de `queue_topology.xml`, `queue_publisher.xml` o `queue_consumer.xml`.
Por ejemplo, si `queue/default_connection` es `amqp` en `env.php` pero se especifica una conexión `db` en los archivos XML de configuración de cola de un módulo, el módulo utilizará MySQL como agente de mensajes.

## directorios

Opciones de asignación de directorio opcionales que deben establecerse cuando el servidor web está configurado para servir la aplicación Commerce desde el directorio `/pub` para [seguridad mejorada](../../installation/tutorials/docroot.md).

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

Más información sobre [Dominios descargables](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## instalar

La fecha de instalación de la aplicación de Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## bloquear

La configuración del proveedor de bloqueos se establece mediante el nodo `lock`.

Más información sobre la [Configuración del proveedor de bloqueos](../../installation/tutorials/lock-provider.md).

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

Las configuraciones de sesión se almacenan en el nodo `session`.

```conf
'session' => [
  'save' => 'files'
],
```

Más información sobre [Sesión](../storage/sessions.md).

## x-frame-options

El encabezado x-frame-options se puede configurar mediante este nodo.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Más información sobre [x-frame-options](../security/xframe-options.md).

## sistema

Con este nodo, Commerce bloquea los valores de configuración en el archivo `env.php` y, a continuación, deshabilita el campo en el administrador.

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


## Agregar variables a la configuración de archivo

Puede establecer o anular todas las opciones de configuración (variables con valor) con variables de entorno del sistema operativo (SO).

La configuración de `env.php` se almacena en una matriz con niveles anidados. Para convertir una ruta de acceso de matriz anidada en una cadena para las variables de entorno del sistema operativo, concatene cada clave en la ruta con caracteres de subrayado dobles `__`, en mayúsculas y con el prefijo `MAGENTO_DC_`.

Por ejemplo, vamos a convertir el controlador de guardado de sesión de la configuración `env.php` en una variable de entorno del sistema operativo.

```conf
'session' => [
  'save' => 'files'
],
```

La concatenación de `__` y las claves en mayúsculas se convertirán en `SESSION__SAVE`.

A continuación, se agrega el prefijo `MAGENTO_DC_` para obtener el nombre de la variable de entorno `MAGENTO_DC_SESSION__SAVE` del sistema operativo resultante.

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

Otro ejemplo: vamos a convertir una ruta de opciones de configuración escalar `env.php`.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>Aunque el nombre de la variable debe estar en mayúsculas, el valor distingue entre mayúsculas y minúsculas y debe conservarse tal y como se documenta.

Simplemente lo ponemos en mayúsculas y agregamos el prefijo `MAGENTO_DC_` para recibir el nombre de la variable de entorno `MAGENTO_DC_X-FRAME-OPTIONS` del sistema operativo final.

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>Tenga en cuenta que el contenido de `env.php` tendrá prioridad sobre las variables de entorno del sistema operativo.

## Anular la configuración del archivo con variables

Para anular las opciones de configuración de `env.php` existentes con una variable de entorno de sistema operativo, el elemento de matriz de la configuración debe estar codificado en JSON y establecerse como un valor de la variable de sistema operativo `MAGENTO_DC__OVERRIDE`.

Cuando se establece `MAGENTO_DC__OVERRIDE`, el marco de trabajo de Commerce omite los valores correspondientes del archivo `env.php` y lee la configuración directamente desde la variable de entorno. Los valores del archivo `env.php` permanecen inalterados, pero se omiten para las secciones de configuración anuladas.

>[!IMPORTANT]
>
>La variable `MAGENTO_DC__OVERRIDE` omite completamente las secciones de configuración especificadas en el archivo `env.php`. Este comportamiento es diferente de las variables `MAGENTO_DC_` individuales, que tienen una prioridad menor que los valores del archivo `env.php`.

Si necesita anular varias opciones de configuración, asígnelas todas en una sola matriz antes de la codificación JSON.

Por ejemplo, vamos a anular las siguientes `env.php` configuraciones:

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

El texto con codificación JSON de la matriz anterior sería
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`.

A continuación, configúrelo como el valor de la variable del sistema operativo `MAGENTO_DC__OVERRIDE`.

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>Asegúrese de que la matriz codificada con JSON esté correctamente citada o se haya escapado si es necesario para evitar que el sistema operativo dañe la cadena codificada.