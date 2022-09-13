---
title: Agente de mensajes
description: Siga estos pasos para instalar y configurar el software de broker de mensajes necesario (como RabbitMQ) para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Agente de mensajes

Adobe Commerce utiliza el Agente de mensajes de código abierto RabbitMQ. Ofrece un sistema de mensajería fiable, altamente disponible, escalable y portátil.

Las colas de mensajes proporcionan un mecanismo de comunicaciones asincrónico en el que el remitente y el receptor de un mensaje no se comunican entre sí. Tampoco necesitan comunicarse con la cola de mensajes al mismo tiempo. Cuando un remitente coloca un mensaje en cola, se almacena hasta que el destinatario lo recibe.

El sistema de cola de mensajes debe establecerse antes de instalar Adobe Commerce o Magento Open Source. La secuencia básica es:

1. Instale RabbitMQ y cualquier requisito previo.
1. Conecte RabbitMQ a Adobe Commerce o Magento Open Source.

>[!NOTE]
>
>Puede utilizar MySQL o RabbitMQ para el procesamiento de la cola de mensajes. Para obtener más información sobre la configuración del sistema de colas de mensajes, consulte [Resumen de las colas de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si utiliza la API masiva con Adobe Commerce, la configuración predeterminada del sistema de cola de mensajes es usar RabbitMQ como agente de mensajería. Consulte [Iniciar consumidores de cola de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.

## Instalar RabbitMQ en Ubuntu

Para instalar RabbitMQ en Ubuntu 16, introduzca el siguiente comando:

```bash
sudo apt install -y rabbitmq-server
```

Este comando también instala los paquetes Erlang necesarios.

Si tiene una versión anterior de Ubuntu, RabbitMQ recomienda instalar el paquete desde su sitio web.

1. Descargue el paquete .deb desde [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Instale el paquete con `dpkg`.

Consulte [Instalación en Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) para obtener más información.

## Instalar RabbitMQ en CentOS

### Instalar Erlang

RabbitMQ fue escrito usando el lenguaje de programación Erlang, que debe ser instalado en el mismo sistema que RabbitMQ.

Consulte [Instalación manual](https://www.erlang-solutions.com/downloads/) para obtener más información.

Consulte la [Matriz de versiones de RabbitMQ/Erlang](https://www.rabbitmq.com/which-erlang.html) para instalar la versión correcta.

### Instalar RabbitMQ

El servidor RabbitMQ está incluido en CentOS, pero la versión es a menudo antigua. RabbitMQ recomienda instalar el paquete desde su sitio web.

Consulte la página de instalación de RabbitMQ para obtener la última versión compatible. Adobe Commerce y los Magento Open Source 2.3 y 2.4 admiten RabbitMQ 3.8.x.

Consulte [Instalación en Linux basado en RPM](https://www.rabbitmq.com/install-rpm.html) para obtener más información.

## Configurar RabbitMQ

Revise la documentación oficial de RabbitMQ para configurar y administrar RabbitMQ. Preste atención a los siguientes elementos:

* Variables de entorno
* Acceso a puertos
* Cuentas de usuario predeterminadas
* Inicio y parada del agente
* Límites del sistema

## Instale con RabbitMQ y conecte

Si instala Adobe Commerce o Magento Open Source _after_ Si instala RabbitMQ, agregue los siguientes parámetros de línea de comandos durante la instalación:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Donde:

| Parámetro | Descripción |
|--- |--- |
| `--amqp-host` | Nombre de host donde está instalado RabbitMQ. |
| `--amqp-port` | Puerto que se utilizará para conectar con RabbitMQ. El valor predeterminado es `5672`. |
| `--amqp-user` | El nombre de usuario para conectarse a RabbitMQ. No utilizar el usuario predeterminado `guest`. |
| `--amqp-password` | La contraseña para conectarse a RabbitMQ. No use la contraseña predeterminada `guest`. |
| `--amqp-virtualhost` | El host virtual para conectarse a RabbitMQ. El valor predeterminado es `/`. |
| `--amqp-ssl` | Indica si se conecta a RabbitMQ. El valor predeterminado es `false`. Si establece el valor en true, consulte Configuración de SSL para obtener más información. |

## Conectar RabbitMQ

Si ya tenía instalado Adobe Commerce o Magento Open Source y desea conectarlo a RabbitMQ, agregue un `queue` en la sección `<install_directory>/app/etc/env.php` para que sea similar al siguiente:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

También puede establecer los valores de configuración de RabbitMQ usando la variable `bin/magento setup:config:set` comando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Después de ejecutar el comando o actualizar el `<install_directory>/app/etc/env.php` archivo con valores de configuración AMQP, ejecute `bin/magento setup:upgrade` para aplicar los cambios y crear las colas e intercambios necesarios en RabbitMQ.

## Configuración de SSL

Para configurar la compatibilidad con SSL, edite la `ssl` y `ssl_options` en la variable `<install_directory>/app/etc/env.php` para que sean similares a los siguientes:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Iniciar los consumidores de la cola de mensajes

Una vez que haya conectado Adobe Commerce y RabbitMQ, debe iniciar los consumidores de la cola de mensajes. Consulte [Configuración de colas de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.
