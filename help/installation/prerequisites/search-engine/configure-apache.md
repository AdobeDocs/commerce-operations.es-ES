---
title: Configurar Apache para su motor de búsqueda
description: Siga estos pasos para configurar un motor de búsqueda con el servidor web Apache para instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '662'
ht-degree: 0%

---


# Configurar Apache para su motor de búsqueda

{{$include /help/_includes/web-server-communication.md}}

## Configuración de un proxy

>[!NOTE]
>
>La compatibilidad con OpenSearch se ha agregado en la versión 2.4.4. OpenSearch es una ramificación de Elasticsearch compatible. Todas las instrucciones para configurar el Elasticsearch 7 se aplican a OpenSearch. Consulte [Migrar Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obtener más información.

Esta sección trata sobre cómo configurar Apache como un *unsecure* para que Adobe Commerce o el Magento Open Source puedan utilizar un motor de búsqueda que se ejecute en este servidor. En esta sección no se analiza la configuración de la autenticación básica HTTP; que se analiza en [Comunicación segura con Apache](#secure-communication-with-apache).

>[!NOTE]
>
>La razón por la que el proxy no está protegido en este ejemplo es que es más fácil configurarlo y verificarlo. Puede utilizar TLS con este proxy. Si desea hacerlo, asegúrese de agregar la información del proxy a la configuración segura del host virtual.

### Configuración de un proxy para Apache 2.4

En esta sección se explica cómo configurar un proxy mediante un host virtual.

1. Habilitar `mod_proxy` de la siguiente manera:

   ```bash
   a2enmod proxy_http
   ```

1. Usar un editor de texto para abrir `/etc/apache2/sites-available/000-default.conf`
1. Agregue la siguiente directiva en la parte superior del archivo:

   ```conf
   Listen 8080
   ```

1. Añada lo siguiente en la parte inferior del archivo :

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

   Por ejemplo, si está utilizando Elasticsearch y su proxy utiliza el puerto 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Los mensajes similares a los que se muestran a continuación indican que se ha realizado correctamente:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicación segura con Apache

Esta sección trata sobre cómo proteger la comunicación entre Apache y el motor de búsqueda mediante [HTTP básico](https://datatracker.ietf.org/doc/html/rfc2617) autenticación con Apache. Para obtener más opciones, consulte uno de los siguientes recursos:

* [Tutorial de autenticación y autorización de Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Consulte una de las siguientes secciones:

* [Crear un archivo de contraseña](#create-a-password)
* [Configurar el host virtual seguro](#secure-communication-with-apache)

### Crear una contraseña

Por motivos de seguridad, puede localizar el archivo de contraseña en cualquier lugar excepto en el docroot de su servidor web. En este ejemplo, se muestra cómo almacenar el archivo de contraseña en un nuevo directorio.

#### Instale htpasswd si es necesario

Primero, compruebe si tiene el Apache `htpasswd` se instala de la siguiente manera:

1. Introduzca el siguiente comando para determinar si `htpasswd` ya está instalado:

   ```bash
   which htpasswd
   ```

   Si se muestra una ruta, se instala; si el comando no devuelve ningún resultado, `htpasswd` no está instalado.

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

   * Configuración del Elasticsearch: el nombre del usuario `magento_elasticsearch` en este ejemplo


* `<password file name>` debe ser un archivo oculto (comienza con `.`) y debe reflejar el nombre del usuario. Consulte los ejemplos que aparecen más adelante en esta sección para obtener más información.

Siga las indicaciones de la pantalla para crear una contraseña para el usuario.

#### Ejemplos

**Ejemplo 1: cron**
Debe configurar la autenticación de solo un usuario para cron; en este ejemplo, utilizamos el usuario del servidor web. Para crear un archivo de contraseña para el usuario del servidor web, introduzca los siguientes comandos:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Ejemplo 2: Elasticsearch**
Debe configurar la autenticación para dos usuarios: una con acceso a nginx y otra con acceso a Elasticsearch. Para crear archivos de contraseña para estos usuarios, introduzca los siguientes comandos:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Agregar usuarios adicionales

Para agregar otro usuario al archivo de contraseña, introduzca el siguiente comando como usuario con `root` privilegios:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Comunicación segura con Apache

Esta sección describe cómo configurar [Autenticación HTTP básica](https://httpd.apache.org/docs/2.2/howto/auth.html). El uso conjunto de autenticación TLS y HTTP Basic evita que cualquier persona intercepte comunicaciones con el Elasticsearch o con el servidor de aplicaciones.

Esta sección explica cómo especificar quién puede acceder al servidor Apache.

1. Utilice un editor de texto para agregar el siguiente contenido a su host virtual seguro.

   * Apache 2.4: Editar `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elastic Server"
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Si agregó el anterior al host virtual seguro, elimine `Listen 8080` y `<VirtualHost *:8080>` directivas agregadas anteriormente al host virtual no seguro.

1. Guarde los cambios, salga del editor de texto y reinicie Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Verificar

{{$include /help/_includes/verify-secure-communication.md}}
