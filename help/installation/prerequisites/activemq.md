---
title: Agente de mensajes (ActiveMQ Artemis)
description: Siga estos pasos para instalar y configurar Apache ActiveMQ Artemis message broker para instalaciones locales de Adobe Commerce.
source-git-commit: 46816b42ea30cb6c5f5ce59752cc00c38d221610
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Agente de mensajes (ActiveMQ Artemis)

Adobe Commerce también es compatible con el agente de mensajes de código abierto ActiveMQ Artemis a través del Protocolo simple de mensajería orientada a texto (STOMP). Ofrece un sistema de mensajería fiable y escalable, que ofrece flexibilidad para integraciones basadas en STOMP.


>[!NOTE]
>
>ActiveMQ Artemis se introdujo en Adobe Commerce 2.4.6 y versiones posteriores. Para obtener más información sobre la instalación de ActiveMQ Artemis en Adobe Commerce en proyectos de infraestructura en la nube, consulte [Configurar el servicio ActiveMQ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemqsee) en la *Guía de Commerce en la nube*.

Las colas de mensajes proporcionan un mecanismo de comunicaciones asincrónico en el que el remitente y el receptor de un mensaje no se ponen en contacto entre sí. Tampoco necesitan comunicarse con la cola de mensajes al mismo tiempo. Cuando un remitente coloca un mensaje en cola, se almacena hasta que el destinatario lo recibe.

Debe establecerse el sistema de cola de mensajes antes de instalar Adobe Commerce. La secuencia básica es:

1. Instale Apache ActiveMQ Artemis y cualquier requisito previo.
1. Conecte ActiveMQ a Adobe Commerce.

>[!NOTE]
>
>Puede utilizar MySQL, ActiveMQ o [!DNL RabbitMQ] para el procesamiento de colas de mensajes. Para obtener más información sobre la configuración del sistema de colas de mensajes, consulte [Resumen de colas de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si utiliza la API en bloque con Adobe Commerce, la configuración predeterminada del sistema de colas de mensajes será el uso de [!DNL RabbitMQ] como intermediario de mensajes. Consulte [Iniciar consumidores de cola de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.

>[!TIP]
>
>Compruebe siempre la [página de descarga de Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/download/) para obtener la última versión estable antes de la instalación. Los ejemplos de este documento utilizan la versión 2.42.0, que fue la última versión estable a partir de septiembre de 2025.


## Instalar Apache ActiveMQ Artemis

Puede instalar ActiveMQ Artemis mediante Docker (recomendado para desarrollo) o instalación manual (recomendado para producción).

### Opción 1: instalación de Docker (recomendada para desarrollo)

#### Requisitos previos

Asegúrese de que Docker esté instalado y en ejecución en el sistema.

>[!TIP]
>
>Para obtener más información sobre la imagen oficial de ActiveMQ Artemis Docker, consulte la [página del Apache ActiveMQ Artemis Docker Hub](https://hub.docker.com/r/apache/activemq-artemis).

#### Pasos de instalación

1. Ejecute ActiveMQ Artemis utilizando la imagen oficial de Docker:

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Ejecutar con credenciales personalizadas:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Comandos de administración de Docker

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Acceso a servicios

Una vez que se esté ejecutando el contenedor Docker, puede acceder a:

- **Consola web**: http://localhost:8161/console (credenciales predeterminadas: artemis/artemis)
- **Puerto STOMP**: localhost:61613 (para conexión Adobe Commerce)

>[!NOTE]
>
>Se recomienda la instalación de Docker para fines de desarrollo y pruebas. Para la producción, considere la posibilidad de utilizar la instalación manual con las configuraciones de seguridad adecuadas.

### Opción 2: Instalación manual en Ubuntu/CentOS

#### Requisitos previos

Asegúrese de que Java 17 o superior esté instalado (requerido para ActiveMQ Artemis 2.42.0 o posterior).

### Pasos de instalación

1. Descargue e instale la versión más reciente del [sitio web Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/download/). A partir de septiembre de 2025, la última versión estable es 2.42.0:

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Crear el usuario `artemis` y establecer la propiedad:

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Cree una instancia de broker:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Inicie el agente:

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## Configurar elementos de ActiveMQ

Revise la documentación oficial de ActiveMQ Artemis para configurar y administrar el agente. Preste atención a los siguientes elementos:

- Variables de entorno
- Acceso al puerto (protocolo STOMP)
- Credenciales y cuentas de usuario predeterminadas
- Inicio y detención del agente
- Límites del sistema y ajuste de recursos

### Archivos de configuración clave

- `/var/lib/artemis-instance/etc/broker.xml`: configuración de agente principal
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Autenticación de usuario
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Funciones de usuario
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Configuración de Bootstrap

### Habilitar el protocolo STOMP

Compruebe `/var/lib/artemis-instance/etc/broker.xml` para asegurarse de que el aceptador STOMP está configurado:

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Para habilitar SSL en STOMP, debe agregar el aceptador `stomp-ssl` explícitamente.

## Instale con ActiveMQ Artemis y conecte

Si instala Adobe Commerce _después de_ de instalar ActiveMQ Artemis, agregue los siguientes parámetros de línea de comandos durante la instalación:

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Donde:

| Parámetro | Descripción |
|--- |--- |
| `--stomp-host` | Nombre de host donde está instalado ActiveMQ. |
| `--stomp-port` | Puerto que se utilizará para conectar con ActiveMQ. El valor predeterminado es `61613`. |
| `--stomp-user` | Nombre de usuario para conectarse a ActiveMQ. No use el usuario predeterminado `artemis`. |
| `--stomp-password` | Contraseña para conectarse a ActiveMQ. No use la contraseña predeterminada `artemis`. |
| `--stomp-ssl` | Indica si se debe conectar con ActiveMQ. El valor predeterminado es `false`. Si establece el valor en true, consulte Configuración de SSL para obtener más información. |

## Conectar ActiveMQ Artemis

Si ya tiene una instancia de Adobe Commerce con la configuración de RabbitMQ (AMQP) en el archivo `<install_directory>/app/etc/env.php` y desea conectarla a ActiveMQ, reemplace la sección `queue` por la sección STOMP para que sea similar a la siguiente:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

También puede establecer los valores de configuración de ActiveMQ mediante el comando `bin/magento setup:config:set` (quite la configuración de AMQP si existe en el archivo `app/etc/env.php`):

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

Después de ejecutar el comando o actualizar el archivo `<install_directory>/app/etc/env.php` con valores de configuración STOMP, ejecute `bin/magento setup:upgrade` para aplicar los cambios y crear las colas necesarias en ActiveMQ.

## Configurar SSL

Para configurar la compatibilidad con SSL, edite los parámetros `ssl` y `ssl_options` en el archivo `<install_directory>/app/etc/env.php` de modo que sean similares a los siguientes:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### Opciones de configuración SSL

| Opción | Descripción | Predeterminado |
|--- |--- |--- |
| `verify_peer` | Verificar el certificado SSL del corredor | `true` |
| `verify_peer_name` | Compruebe que el nombre de host del agente coincide con el certificado | `true` |
| `allow_self_signed` | Permitir certificados autofirmados | `false` |
| `cafile` | Ruta al archivo de certificado de CA para la verificación del agente | Necesario para SSL |
| `certfile` | Ruta al archivo de certificado de cliente (para SSL mutuo) | Opcional |
| `keyfile` | Ruta al archivo de clave privada del cliente (para SSL mutuo) | Opcional |
| `passphrase` | Frase de contraseña para la clave privada del cliente | Opcional |

### Configuración SSL de desarrollo

Para entornos de desarrollo, puede utilizar una configuración SSL relajada:

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Ajuste del rendimiento

ActiveMQ Artemis ofrece varias opciones de ajuste de rendimiento:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Monitorización y administración

### consola web

ActiveMQ Artemis proporciona una consola de administración basada en web accesible en:
- URL: `http://localhost:8161/console`
- Credenciales predeterminadas: `artemis/artemis`

## Resolución de problemas

### Problemas comunes

1. **Conexión rechazada**: Asegúrese de que ActiveMQ Artemis se está ejecutando y de que el aceptador STOMP está configurado.
1. **Error de autenticación**: compruebe el nombre de usuario y la contraseña en la configuración de Broker y en el archivo `env.php`.
1. **Error del protocolo de enlace SSL**: compruebe los certificados SSL y la configuración.




### Verificar conexión STOMP

Probar la conexión STOMP con telnet:

```bash
telnet localhost 61613
```

Debería ver una conexión establecida. Para probar con un comando STOMP:

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

La salida esperada debe mostrar la conexión establecida y la respuesta del protocolo STOMP.

## Iniciar los consumidores de cola de mensajes

Después de conectar Adobe Commerce y ActiveMQ Artemis, debe iniciar los consumidores de cola de mensajes. Consulte [Configurar colas de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.

