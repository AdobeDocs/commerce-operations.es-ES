---
title: Configuración de Apache para el motor de búsqueda
description: Siga estos pasos para configurar un motor de búsqueda con el servidor web Apache para instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: d3cfd97450164d38fd340b538099739601573d64
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Configuración de Apache para el motor de búsqueda

{{$include /help/_includes/web-server-communication.md}}

## Configuración de un proxy

>[!NOTE]
>
>Se ha añadido compatibilidad con OpenSearch en 2.4.4. OpenSearch es una ramificación compatible de Elasticsearch. Consulte [Migrar Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obtener más información.

En esta sección se explica cómo configurar Apache como un *inseguro* para que Adobe Commerce pueda utilizar un motor de búsqueda que se ejecute en este servidor. Esta sección no trata sobre la configuración de la autenticación HTTP Basic; se trata en [Comunicación segura con Apache](#secure-communication-with-apache).

>[!NOTE]
>
>La razón por la que el proxy no está protegido en este ejemplo es que es más fácil de configurar y verificar. Puede utilizar TLS con este proxy. Si desea hacerlo, asegúrese de añadir la información del proxy a la configuración de su host virtual seguro.

### Configuración de un proxy para Apache 2.4

En esta sección se explica cómo configurar un proxy mediante un host virtual.

1. Activar `mod_proxy` como sigue:

   ```bash
   a2enmod proxy_http
   ```

1. Use un editor de texto para abrir `/etc/apache2/sites-available/000-default.conf`
1. Agregue la siguiente directiva en la parte superior del archivo:

   ```conf
   Listen 8080
   ```

1. Agregue lo siguiente en la parte inferior del archivo:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Reinicie Apache:

   ```bash
   service apache2 restart
   ```

1. Compruebe que el proxy funciona introduciendo el siguiente comando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Por ejemplo, si utiliza Elasticsearch y el proxy utiliza el puerto 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Se muestran mensajes similares a los siguientes para indicar que se ha realizado correctamente:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicación segura con Apache

En esta sección se explica cómo proteger la comunicación entre Apache y el motor de búsqueda mediante [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) autenticación con Apache. Para obtener más opciones, consulte uno de los siguientes recursos:

* [Tutorial de autenticación y autorización de Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Consulte una de las siguientes secciones:

* [Crear un archivo de contraseña](#create-a-password)
* [Configure su host virtual seguro](#secure-communication-with-apache)

### Crear una contraseña

Por motivos de seguridad, puede localizar el archivo de contraseña en cualquier lugar excepto en el servidor web docroot. En este ejemplo, se muestra cómo almacenar el archivo de contraseña en un nuevo directorio.

#### Instale htpasswd si es necesario

Primero, compruebe si tiene el Apache `htpasswd` se instala de la siguiente manera:

1. Introduzca el siguiente comando para determinar si `htpasswd` ya está instalado:

   ```bash
   which htpasswd
   ```

   Si se muestra una ruta, se instala; si el comando no devuelve ninguna salida, `htpasswd` no está instalado.

1. Si es necesario, instale `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Crear un archivo de contraseña

Introduzca los siguientes comandos como usuario con `root` privilegios:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Donde

* `<username>` puede ser:

   * Configuración de cron: el usuario del servidor web u otro usuario.

   En este ejemplo, utilizamos el usuario del servidor web, pero la elección del usuario depende de usted.

   * Configuración del Elasticsearch: el nombre del usuario es `magento_elasticsearch` en este ejemplo


* `<password file name>` debe ser un archivo oculto (comienza por `.`) y deben reflejar el nombre del usuario. Consulte los ejemplos que aparecen más adelante en esta sección para obtener más información.

Siga las indicaciones de la pantalla para crear una contraseña de usuario.

#### Ejemplos

**Ejemplo 1: cron**
Debe configurar la autenticación solo para un usuario para cron; en este ejemplo, utilizamos el usuario del servidor web. Para crear un archivo de contraseña para el usuario del servidor web, introduzca los siguientes comandos:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Ejemplo 2: Elasticsearch**
Debe configurar la autenticación para dos usuarios: uno con acceso a nginx y otro con acceso a Elasticsearch. Para crear archivos de contraseña para estos usuarios, introduzca los siguientes comandos:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Añadir usuarios adicionales

Para agregar otro usuario al archivo de contraseñas, escriba el siguiente comando como usuario con `root` privilegios:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Comunicación segura con Apache

En esta sección se explica cómo configurar [Autenticación HTTP básica](https://httpd.apache.org/docs/2.2/howto/auth.html). El uso conjunto de autenticación TLS y HTTP Basic evita que cualquier persona intercepte la comunicación con Elasticsearch o OpenSearch, o con su servidor de aplicaciones.

En esta sección se explica cómo especificar quién puede acceder al servidor Apache.

1. Utilice un editor de texto para añadir el siguiente contenido a su host virtual seguro.

   * Apache 2.4: Editar `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Si agregó el anterior a su host virtual seguro, quite `Listen 8080` y el `<VirtualHost *:8080>` directivas que agregó anteriormente a su host virtual no seguro.

1. Guarde los cambios, salga del editor de texto y reinicie Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Verificar

{{$include /help/_includes/verify-secure-communication.md}}
