---
title: Usar Redis para almacenamiento de sesión
description: Aprenda a configurar Redis para el almacenamiento de sesión.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---


# Usar Redis para almacenamiento de sesión

>[!IMPORTANT]
>
>Debe [instalar Redis](config-redis.md#install-redis) antes de continuar.


Commerce ahora proporciona opciones de línea de comandos para configurar el almacenamiento de sesión de Redis. En versiones anteriores, se editaba el `<Commerce install dir>app/etc/env.php` archivo. La línea de comandos proporciona validación y es el método de configuración recomendado, pero aún puede editar el `env.php` archivo.

Ejecute el `setup:config:set` y especifique los parámetros específicos de Redis.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

donde

`--session-save=redis` habilita el almacenamiento de sesión de Redis. Si esta función ya se ha habilitado, omita este parámetro.

`--session-save-redis-<parameter_name>=<parameter_value>` es una lista de pares de parámetros/valores que configuran el almacenamiento de sesión:

| Parámetro de línea de comandos | Nombre del parámetro | Significado | Valor predeterminado |
|--- |--- |--- |--- |
| session-save-redis-host | host | Nombre de host completo, dirección IP o ruta absoluta si se usan sockets UNIX. | localhost |
| session-save-redis-port | puerto | Puerto de escucha del servidor de Redis. | 6379 |
| session-save-redis-password | password | Especifica una contraseña si el servidor de Redis requiere autenticación. | empty |
| session-save-redis-timeout | timeout | Tiempo de espera de conexión, en segundos. | 2,5 |
| session-save-redis-persistent-id | persistent_identifier | Cadena única para habilitar conexiones persistentes (por ejemplo, sess-db0).<br>[Problemas conocidos con phpredis y php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | base de datos | Número de base de datos de Redis únicos, que se recomienda proteger contra la pérdida de datos.<br><br>**Importante**: Si utiliza Redis para más de un tipo de almacenamiento en caché, los números de la base de datos deben ser diferentes. Se recomienda asignar el número predeterminado de base de datos de almacenamiento en caché a 0, el número de base de datos de almacenamiento en caché de páginas a 1 y el número de base de datos de almacenamiento de sesión a 2. | 0 |
| session-save-redis-compression-threshold | compression_threshold | Establézcalo en 0 para desactivar la compresión (recomendado cuando `suhosin.session.encrypt = On`).<br>[Problema conocido con cadenas de más de 64 KB](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | Opciones: gzip, lzf, lz4 o snpy. | gzip |
| session-save-redis-log-level | log_level | Establézcalo en cualquiera de los siguientes, enumerados en orden de menos detalle a más detallado:<ul><li>0 (emergencia: solo los errores más graves)<li>1 (alerta: acción inmediata requerida)<li>2 (crítico: componente de aplicación no disponible)<li>3 (error: errores de tiempo de ejecución, no críticos, pero deben monitorizarse)<li>4 (advertencia: información adicional, recomendado)<li>5 (aviso: condición normal pero significativa)<li>6 (información: mensajes informativos)<li>7 (depuración: la información más completa para desarrollo o pruebas únicamente)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | Número máximo de procesos que pueden esperar un bloqueo en una sesión. Para clústeres de producción grandes, establezca esto en al menos el 10% del número de procesos PHP. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | Número de segundos que hay que esperar antes de intentar romper el bloqueo de la sesión de front-end (es decir, tienda). | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Número de segundos que hay que esperar antes de intentar romper el bloqueo de una sesión de administrador (es decir, administrador). | 30 |
| session-save-redis-first-lifetime | first_lifetime | Duración, en segundos, de la sesión para los usuarios que no sean bots en la primera escritura, o utilice 0 para desactivarla. | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | Duración, en segundos, de la sesión para bots en la primera escritura, o utilice 0 para desactivar. | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | Duración, en segundos, de la sesión para bots en escrituras posteriores o utilice 0 para desactivarlos. | 7200 |
| session-save-redis-disable-locking | disable_locking | Deshabilite el bloqueo de sesión por completo. | 0 (falso) |
| session-save-redis-min-lifetime | min_lifetime | Duración mínima de la sesión, en segundos. | 60 |
| session-save-redis-max-lifetime | max_lifetime | Duración máxima de la sesión, en segundos. | 2592000 (720 horas) |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel nombre maestro | empty |
| session-save-redis-sentinel-servers | sentinel_servers | Lista de servidores Sentinel Redis separados por comas | empty |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Comprobar el indicador de estado maestro de frase de lectura | 0 (falso) |
| session-save-redis-sentinel-connect-retry | sentinel_connect_retries | Reintentos de conexión para centinelas | 5 |

## Ejemplo

El ejemplo siguiente establece Redis como almacén de datos de sesión y establece el host como `127.0.0.1`, establece el nivel de registro en 4 y el número de base de datos en 2. Todos los demás parámetros se establecen en el valor predeterminado.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Resultado

Commerce agrega líneas similares a las siguientes a `<magento_root>app/etc/env.php`:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>El TTL para registros de sesión utiliza el valor de Duración de la cookie , que se configura en el Administrador. Si Duración de la cookie está configurada en 0 (el valor predeterminado es 3600), las sesiones de Redis caducan en el número de segundos especificado en min_lifetime (el valor predeterminado es 60). Esta discrepancia se debe a diferencias en la forma en que Redis y las cookies de sesión interpretan un valor de duración de 0. Si no desea ese comportamiento, aumente el valor de min_lifetime.

## Comprobar conexión Redis

Para verificar que Redis y Commerce están trabajando juntos, inicie sesión en el servidor que ejecuta Redis, abra un terminal y utilice el comando Redis monitor o el comando ping.

### Redis monitor, comando

```bash
redis-cli monitor
```

Salida de almacenamiento de sesión de muestra:

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis ping, comando

```bash
redis-cli ping
```

`PONG` debe ser la respuesta.

Si ambos comandos se ejecutaron correctamente, Redis está configurado correctamente.

### Inspección de datos comprimidos

Para inspeccionar los datos de sesión comprimidos y la caché de página, la variable [RESP.app](https://flathub.org/apps/details/app.resp.RESP) admite la descompresión automática de la caché de páginas y sesiones de Commerce 2 y muestra los datos de sesión de PHP de forma legible.

