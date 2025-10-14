---
title: Agente de mensajes (RabbitMQ)
description: Siga estos pasos para instalar y configurar el software de Agente de mensajes necesario (como  [!DNL RabbitMQ]) para las instalaciones locales de Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 73faaa2a3b9ce773e9a381d103735403966f568b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Agente de mensajes (RabbitMQ)

Adobe Commerce usa el agente de mensajes de código abierto [!DNL RabbitMQ]. Ofrece un sistema de mensajería fiable, de alta disponibilidad, escalable y portátil.

Las colas de mensajes proporcionan un mecanismo de comunicaciones asincrónico en el que el remitente y el receptor de un mensaje no se ponen en contacto entre sí. Tampoco necesitan comunicarse con la cola de mensajes al mismo tiempo. Cuando un remitente coloca un mensaje en cola, se almacena hasta que el destinatario lo recibe.

Debe establecerse el sistema de cola de mensajes antes de instalar Adobe Commerce. La secuencia básica es:

1. Instale [!DNL RabbitMQ] y todos los requisitos previos.
1. Conectar [!DNL RabbitMQ] a Adobe Commerce.

>[!NOTE]
>
>Puede utilizar MySQL o [!DNL RabbitMQ] para el procesamiento de colas de mensajes. Para obtener más información sobre la configuración del sistema de colas de mensajes, consulte [Resumen de colas de mensajes](https://developer.adobe.com/commerce/php/development/components/message-queues/). Si utiliza la API en bloque con Adobe Commerce, la configuración predeterminada del sistema de colas de mensajes será el uso de [!DNL RabbitMQ] como intermediario de mensajes. Consulte [Iniciar consumidores de cola de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.

## Instalar [!DNL RabbitMQ] en Ubuntu

Para instalar [!DNL RabbitMQ] en Ubuntu 16, ingrese el siguiente comando:

```bash
sudo apt install -y rabbitmq-server
```

Este comando también instala los paquetes de Erlang necesarios.

Si tiene una versión anterior de Ubuntu, [!DNL RabbitMQ] recomienda instalar el paquete desde su sitio web.

1. Descargue el paquete .deb desde [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Instale el paquete con `dpkg`.

Consulte [Instalar en Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) para obtener más información.

## Instalar [!DNL RabbitMQ] en CentOS

### Instalar Erlang

[!DNL RabbitMQ] se escribió con el lenguaje de programación Erlang, que debe instalarse en el mismo sistema que [!DNL RabbitMQ].

Consulte [Instalación manual](https://www.erlang-solutions.com/downloads/) para obtener más información.

Consulte [[!DNL RabbitMQ]/Erlang version matrix](https://www.rabbitmq.com/which-erlang.html) para instalar la versión correcta.

### Instalar [!DNL RabbitMQ]

El servidor [!DNL RabbitMQ] está incluido en CentOS, pero la versión suele ser antigua. [!DNL RabbitMQ] recomienda instalar el paquete desde su sitio web.

Consulte la página de instalación de [!DNL RabbitMQ] para obtener la última versión compatible. Adobe Commerce 2.3 y 2.4 admiten [!DNL RabbitMQ] 3.8.x.

Consulte [Instalación en Linux basado en RPM](https://www.rabbitmq.com/install-rpm.html) para obtener más información.

## Configurar [!DNL RabbitMQ]

Revise la documentación oficial de [!DNL RabbitMQ] para configurar y administrar [!DNL RabbitMQ]. Preste atención a los siguientes elementos:

* Variables de entorno
* Acceso al puerto
* Cuentas de usuario predeterminadas
* Inicio y detención del agente
* Límites del sistema

## Instalar con [!DNL RabbitMQ] y conectar

Si instala Adobe Commerce _después de_, instale [!DNL RabbitMQ] y agregue los siguientes parámetros de línea de comandos durante la instalación:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Donde:

| Parámetro | Descripción |
|--- |--- |
| `--amqp-host` | Nombre de host donde está instalado [!DNL RabbitMQ]. |
| `--amqp-port` | El puerto que se va a usar para conectarse a [!DNL RabbitMQ]. El valor predeterminado es `5672`. |
| `--amqp-user` | Nombre de usuario para conectarse a [!DNL RabbitMQ]. No use el usuario predeterminado `guest`. |
| `--amqp-password` | Contraseña para conectarse a [!DNL RabbitMQ]. No use la contraseña predeterminada `guest`. |
| `--amqp-virtualhost` | Host virtual para conectarse a [!DNL RabbitMQ]. El valor predeterminado es `/`. |
| `--amqp-ssl` | Indica si se debe conectar con [!DNL RabbitMQ]. El valor predeterminado es `false`. Si establece el valor en true, consulte Configuración de SSL para obtener más información. |

## Conectar [!DNL RabbitMQ]

Si ya tiene Adobe Commerce instalado y desea conectarlo a [!DNL RabbitMQ], agregue una sección `queue` en el archivo `<install_directory>/app/etc/env.php` para que sea similar a lo siguiente:

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

También puede establecer los valores de configuración de [!DNL RabbitMQ] mediante el comando `bin/magento setup:config:set`:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Después de ejecutar el comando o actualizar el archivo `<install_directory>/app/etc/env.php` con valores de configuración de AMQP, ejecute `bin/magento setup:upgrade` para aplicar los cambios y crear las colas e intercambios necesarios en [!DNL RabbitMQ].

## Configurar SSL

Para configurar la compatibilidad con SSL, edite los parámetros `ssl` y `ssl_options` en el archivo `<install_directory>/app/etc/env.php` de modo que sean similares a los siguientes:

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

Una vez que haya conectado Adobe Commerce y [!DNL RabbitMQ], debe iniciar los consumidores de cola de mensajes. Consulte [Configurar colas de mensajes](../../configuration/cli/start-message-queues.md) para obtener más información.
