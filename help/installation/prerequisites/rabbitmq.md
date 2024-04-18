---
title: Agente de mensajes
description: Siga estos pasos para instalar y configurar el software de Agente de mensajes necesario (como [!DNL RabbitMQ]) para instalaciones locales de Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Agente de mensajes

Adobe Commerce utiliza el [!DNL RabbitMQ] agente de mensajes de código abierto. Ofrece un sistema de mensajería fiable, de alta disponibilidad, escalable y portátil.

Las colas de mensajes proporcionan un mecanismo de comunicaciones asincrónico en el que el remitente y el receptor de un mensaje no se ponen en contacto entre sí. Tampoco necesitan comunicarse con la cola de mensajes al mismo tiempo. Cuando un remitente coloca un mensaje en cola, se almacena hasta que el destinatario lo recibe.

Debe establecerse el sistema de cola de mensajes antes de instalar Adobe Commerce. La secuencia básica es:

1. Instalar [!DNL RabbitMQ] y cualquier requisito previo.
1. Connect [!DNL RabbitMQ] a Adobe Commerce.

>[!NOTE]
>
>Puede utilizar MySQL o [!DNL RabbitMQ] para el procesamiento de colas de mensajes. Para obtener más información sobre la configuración del sistema de colas de mensajes, consulte [Resumen de colas de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si utiliza la API por lotes con Adobe Commerce, la configuración predeterminada del sistema de colas de mensajes es utilizar [!DNL RabbitMQ] como intermediario de mensajes. Consulte [Iniciar consumidores de cola de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.

## Instalar [!DNL RabbitMQ] en Ubuntu

Para instalar [!DNL RabbitMQ] en Ubuntu 16, introduzca el siguiente comando:

```bash
sudo apt install -y rabbitmq-server
```

Este comando también instala los paquetes de Erlang necesarios.

Si tiene una versión anterior de Ubuntu, [!DNL RabbitMQ] recomienda instalar el paquete desde su sitio web.

1. Descargue el paquete .deb desde [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Instale el paquete con `dpkg`.

Consulte [Instalación en Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) para obtener más información.

## Instalar [!DNL RabbitMQ] en CentOS

### Instalar Erlang

[!DNL RabbitMQ] se ha escrito utilizando el lenguaje de programación Erlang, que debe instalarse en el mismo sistema que [!DNL RabbitMQ].

Consulte [Instalación manual](https://www.erlang-solutions.com/downloads/) para obtener más información.

Consulte la [[!DNL RabbitMQ]/Erlang matriz de versiones](https://www.rabbitmq.com/which-erlang.html) para instalar la versión correcta.

### Instalar [!DNL RabbitMQ]

El [!DNL RabbitMQ] El servidor de se incluye en CentOS, pero la versión suele ser antigua. [!DNL RabbitMQ] recomienda instalar el paquete desde su sitio web.

Consulte la [!DNL RabbitMQ] instale para obtener la última versión compatible. Compatibilidad con Adobe Commerce 2.3 y 2.4 [!DNL RabbitMQ] 3.8.x.

Consulte [Instalación en Linux basado en RPM](https://www.rabbitmq.com/install-rpm.html) para obtener más información.

## Configurar [!DNL RabbitMQ]

Revisar el funcionario [!DNL RabbitMQ] documentación para configurar y administrar [!DNL RabbitMQ]. Preste atención a los siguientes elementos:

* Variables de entorno
* Acceso al puerto
* Cuentas de usuario predeterminadas
* Inicio y detención del agente
* Límites del sistema

## Instalar con [!DNL RabbitMQ] y conectar

Si instala Adobe Commerce _después_ usted instala [!DNL RabbitMQ], agregue los siguientes parámetros de línea de comandos durante la instalación:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Donde:

| Parámetro | Descripción |
|--- |--- |
| `--amqp-host` | El nombre de host donde [!DNL RabbitMQ] está instalado. |
| `--amqp-port` | El puerto al que se conectará [!DNL RabbitMQ]. El valor predeterminado es `5672`. |
| `--amqp-user` | El nombre de usuario para conectarse a [!DNL RabbitMQ]. No utilizar el usuario predeterminado `guest`. |
| `--amqp-password` | La contraseña para conectarse a [!DNL RabbitMQ]. No utilice la contraseña predeterminada `guest`. |
| `--amqp-virtualhost` | El host virtual al que conectarse [!DNL RabbitMQ]. El valor predeterminado es `/`. |
| `--amqp-ssl` | Indica si se debe conectar a [!DNL RabbitMQ]. El valor predeterminado es `false`. Si establece el valor en true, consulte Configuración de SSL para obtener más información. |

## Connect [!DNL RabbitMQ]

Si ya tiene Adobe Commerce instalado y desea conectarlo a [!DNL RabbitMQ], añada un `queue` de la sección `<install_directory>/app/etc/env.php` de modo que sea similar a lo siguiente:

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

También puede establecer [!DNL RabbitMQ] valores de configuración utilizando `bin/magento setup:config:set` comando:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Después de ejecutar el comando o actualizar el `<install_directory>/app/etc/env.php` archivo con valores de configuración de AMQP, ejecutar `bin/magento setup:upgrade` para aplicar los cambios y crear las colas e intercambios necesarios en [!DNL RabbitMQ].

## Configurar SSL

Para configurar la compatibilidad con SSL, edite el `ssl` y `ssl_options` Parámetros de en `<install_directory>/app/etc/env.php` de modo que sean similares a los siguientes:

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

## Iniciar los consumidores de cola de mensajes

Después de conectar Adobe Commerce y [!DNL RabbitMQ], debe iniciar los consumidores de la cola de mensajes. Consulte [Configuración de colas de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.
