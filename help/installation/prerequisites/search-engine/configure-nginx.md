---
title: Configure Nginx para su motor de búsqueda
description: Siga estos pasos para configurar un motor de búsqueda con el servidor web Nginx para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: a0f2c6480edcda5540ca83835580d18f401de72f
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Configure Nginx para su motor de búsqueda

{{$include /help/_includes/web-server-communication.md}}

## Configuración de un proxy

>[!NOTE]
>
>La compatibilidad con OpenSearch se ha agregado en la versión 2.4.4. OpenSearch es una ramificación de Elasticsearch compatible. Todas las instrucciones para configurar el Elasticsearch 7 se aplican a OpenSearch. Consulte [Migrar Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obtener más información.

Esta sección explica cómo configurar nginx como un *unsecure* para que Adobe Commerce o el Magento Open Source puedan utilizar un motor de búsqueda que se ejecute en este servidor. En esta sección no se analiza la configuración de la autenticación básica HTTP; que se analiza en [Comunicación segura con nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>La razón por la que el proxy no está protegido en este ejemplo es que es más fácil configurarlo y verificarlo. Puede utilizar TLS con este proxy si lo desea; para ello, asegúrese de añadir la información del proxy a la configuración de bloque del servidor seguro.

### Especifique archivos de configuración adicionales en la configuración global

Asegúrese de que su `/etc/nginx/nginx.conf` contiene la línea siguiente para que cargue los demás archivos de configuración que se tratan en las secciones siguientes:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configuración de nginx como proxy

En esta sección se explica cómo especificar quién puede acceder a la variable [nginx](https://glossary.magento.com/nginx) servidor.

1. Uso de un editor de texto para crear un archivo `/etc/nginx/conf.d/magento_es_auth.conf` con el siguiente contenido:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Reinicie nginx:

   ```bash
   service nginx restart
   ```

1. Compruebe que el proxy funciona introduciendo el siguiente comando:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Por ejemplo, si el proxy utiliza el puerto 8080:

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

## Comunicación segura con nginx

Esta sección describe cómo configurar [Autenticación HTTP básica](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) con su proxy seguro. El uso conjunto de autenticación TLS y HTTP Basic evita que cualquier persona intercepte comunicaciones con el Elasticsearch o con el servidor Adobe Commerce o del Magento Open Source.

Como nginx admite de forma nativa la autenticación HTTP Basic, recomendamos volver a hacerlo, por ejemplo [Autenticación implícita](https://www.nginx.com/resources/wiki/modules/auth_digest/), que no se recomienda en la producción.

Recursos adicionales:

* [Cómo configurar la autenticación de contraseña con Nginx en Ubuntu 14.04 (océano digital)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Autenticación HTTP básica con Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Ejemplo de configuraciones de Nginx para Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Consulte las secciones siguientes para obtener más información:

* [Crear contraseñas](#create-a-password)
* [Configuración del acceso a nginx](#set-up-access-to-nginx)
* [Configurar un contexto restringido para el motor de búsqueda](#set-up-a-restricted-context-for-the-search-engine)
* [Compruebe que la comunicación es segura](#secure-communication-with-nginx)

### Crear una contraseña

Le recomendamos que utilice el Apache `htpasswd` para codificar las contraseñas de un usuario con acceso al Elasticsearch o a OpenSearch (denominado `magento_elasticsearch` en este ejemplo).

Para crear una contraseña:

1. Introduzca el siguiente comando para determinar si `htpasswd` ya está instalado:

   ```bash
   which htpasswd
   ```

   Si se muestra una ruta, se instala; si el comando no devuelve ningún resultado, `htpasswd` no está instalado.

1. Si es necesario, instale `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Cree un `/etc/nginx/passwd` para almacenar contraseñas:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Por razones de seguridad, `<filename>` debe estar oculto; es decir, debe comenzar con un punto.

1. *(Opcional).* Para agregar otro usuario al archivo de contraseña, introduzca el mismo comando sin la variable `-c` (crear) opción:

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Compruebe que el contenido de `/etc/nginx/passwd` es correcto.

### Configuración del acceso a nginx

En esta sección se explica cómo especificar quién puede acceder al servidor nginx.

>[!WARNING]
>
>El ejemplo mostrado es para un *unsecure* proxy. Para utilizar un proxy seguro, añada los siguientes contenidos (excepto el puerto de escucha) al bloque de servidor seguro.

Utilice un editor de texto para modificar `/etc/nginx/conf.d/magento_es_auth.conf` (no seguro) o su bloque de servidor seguro con el siguiente contenido:

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>El puerto de escucha del motor de búsqueda que se muestra en el ejemplo anterior son solo ejemplos. Por motivos de seguridad, le recomendamos que utilice un puerto de escucha no predeterminado.

### Configurar un contexto restringido para el motor de búsqueda

En esta sección se explica cómo especificar quién puede acceder al servidor del motor de búsqueda.

1. Introduzca el siguiente comando para crear un directorio que almacene la configuración de autenticación:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Uso de un editor de texto para crear un archivo `/etc/nginx/auth/magento_elasticsearch.conf` con el siguiente contenido:

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Si configura un proxy seguro, elimine `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Reinicie nginx y continúe con la siguiente sección:

   ```bash
   service nginx restart
   ```

#### Verificar

{{$include /help/_includes/verify-secure-communication.md}}
