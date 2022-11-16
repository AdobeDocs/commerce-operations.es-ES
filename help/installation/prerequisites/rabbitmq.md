---
title: Agente de mensajes
description: Siga estos pasos para instalar y configurar el software de broker de mensajes necesario (por ejemplo, [!DNL RabbitMQ]) para instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 1233d2e1d80a3228626be3e20f1bd826b1283523
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Agente de mensajes

Adobe Commerce utiliza la variable [!DNL RabbitMQ] broker de mensajes de código abierto. Ofrece un sistema de mensajería fiable, altamente disponible, escalable y portátil.

Las colas de mensajes proporcionan un mecanismo de comunicaciones asincrónico en el que el remitente y el receptor de un mensaje no se comunican entre sí. Tampoco necesitan comunicarse con la cola de mensajes al mismo tiempo. Cuando un remitente coloca un mensaje en cola, se almacena hasta que el destinatario lo recibe.

El sistema de cola de mensajes debe establecerse antes de instalar Adobe Commerce o Magento Open Source. La secuencia básica es:

1. Instalar [!DNL RabbitMQ] y cualquier requisito previo.
1. Connect [!DNL RabbitMQ] a Adobe Commerce o Magento Open Source.

>[!NOTE]
>
>Puede usar MySQL o [!DNL RabbitMQ] para el procesamiento de la cola de mensajes. Para obtener más información sobre la configuración del sistema de colas de mensajes, consulte [Resumen de las colas de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si utiliza la API masiva con Adobe Commerce, la configuración del sistema de la cola de mensajes toma como valor predeterminado el uso de [!DNL RabbitMQ] como agente de mensajes. Consulte [Iniciar consumidores de cola de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.

## Instalar [!DNL RabbitMQ] en Ubuntu

Para instalar [!DNL RabbitMQ] en Ubuntu 16, introduzca el siguiente comando:

```bash
sudo apt install -y rabbitmq-server
```

Este comando también instala los paquetes Erlang necesarios.

Si tiene una versión anterior de Ubuntu, [!DNL RabbitMQ] recomienda instalar el paquete desde su sitio web.

1. Descargue el paquete .deb desde [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Instale el paquete con `dpkg`.

Consulte [Instalación en Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) para obtener más información.

## Instalar [!DNL RabbitMQ] en CentOS

### Instalar Erlang

[!DNL RabbitMQ] se escribió utilizando el lenguaje de programación Erlang, que debe estar instalado en el mismo sistema que [!DNL RabbitMQ].

Consulte [Instalación manual](https://www.erlang-solutions.com/downloads/) para obtener más información.

Consulte la [[!DNL RabbitMQ]/Erlang matriz de versiones](https://www.rabbitmq.com/which-erlang.html) para instalar la versión correcta.

### Instalar [!DNL RabbitMQ]

La variable [!DNL RabbitMQ] El servidor está incluido en CentOS, pero la versión suele ser antigua. [!DNL RabbitMQ] recomienda instalar el paquete desde su sitio web.

Consulte la [!DNL RabbitMQ] instale la página para obtener la última versión compatible. Compatibilidad con Adobe Commerce y Magento Open Source 2.3 y 2.4 [!DNL RabbitMQ] 3.8.x.

Consulte [Instalación en Linux basado en RPM](https://www.rabbitmq.com/install-rpm.html) para obtener más información.

## Configurar [!DNL RabbitMQ]

Revise el [!DNL RabbitMQ] documentación para configurar y administrar [!DNL RabbitMQ]. Preste atención a los siguientes elementos:

* Variables de entorno
* Acceso a puertos
* Cuentas de usuario predeterminadas
* Inicio y parada del agente
* Límites del sistema

## Instale con [!DNL RabbitMQ] y conectar

Si instala Adobe Commerce o Magento Open Source _after_ instalación [!DNL RabbitMQ], agregue los siguientes parámetros de línea de comandos durante la instalación:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Donde:

| Parámetro | Descripción |
|--- |--- |
| `--amqp-host` | El nombre de host donde [!DNL RabbitMQ] está instalado. |
| `--amqp-port` | El puerto a utilizar para conectarse a [!DNL RabbitMQ]. El valor predeterminado es `5672`. |
| `--amqp-user` | El nombre de usuario para conectarse a [!DNL RabbitMQ]. No utilizar el usuario predeterminado `guest`. |
| `--amqp-password` | La contraseña para conectarse a [!DNL RabbitMQ]. No use la contraseña predeterminada `guest`. |
| `--amqp-virtualhost` | El host virtual para conectarse a [!DNL RabbitMQ]. El valor predeterminado es `/`. |
| `--amqp-ssl` | Indica si se conecta a [!DNL RabbitMQ]. El valor predeterminado es `false`. Si establece el valor en true, consulte Configuración de SSL para obtener más información. |

## Connect [!DNL RabbitMQ]

Si ya tiene instalado Adobe Commerce o Magento Open Source y desea conectarlo a [!DNL RabbitMQ], agregue un `queue` en la sección `<install_directory>/app/etc/env.php` para que sea similar al siguiente:

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

También puede establecer [!DNL RabbitMQ] los valores de configuración que usan la variable `bin/magento setup:config:set` comando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Después de ejecutar el comando o actualizar el `<install_directory>/app/etc/env.php` archivo con valores de configuración AMQP, ejecute `bin/magento setup:upgrade` para aplicar los cambios y crear las colas e intercambios necesarios en [!DNL RabbitMQ].

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

Después de haber conectado Adobe Commerce y [!DNL RabbitMQ], debe iniciar los consumidores de la cola de mensajes. Consulte [Configuración de colas de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.
