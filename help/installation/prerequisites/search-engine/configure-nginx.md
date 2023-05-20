---
title: Configure Nginx para su motor de búsqueda
description: Siga estos pasos para configurar un motor de búsqueda con el servidor web Nginx para instalaciones locales de Adobe Commerce y Magento Open Source.
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# Configure Nginx para su motor de búsqueda

{{$include /help/_includes/web-server-communication.md}}

## Configuración de un proxy

>[!NOTE]
>
>Se ha añadido compatibilidad con OpenSearch en 2.4.4. OpenSearch es una ramificación compatible de Elasticsearch. Consulte [Migrar Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) para obtener más información.

En esta sección se explica cómo configurar nginx como un *inseguro* para que Adobe Commerce pueda utilizar un motor de búsqueda que se ejecute en este servidor. Esta sección no trata sobre la configuración de la autenticación HTTP Basic; se trata en [Comunicación segura con nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>La razón por la que el proxy no está protegido en este ejemplo es que es más fácil de configurar y verificar. Puede utilizar TLS con este proxy si lo desea; para ello, asegúrese de añadir la información del proxy a la configuración del bloque de servidor seguro.

### Especificar archivos de configuración adicionales en la configuración global

Asegúrese de que su `/etc/nginx/nginx.conf` contiene la siguiente línea, de modo que carga los demás archivos de configuración mencionados en las secciones siguientes:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configuración de nginx como proxy

En esta sección se explica cómo especificar quién puede acceder al servidor de nginx.

1. Uso de un editor de texto para crear un archivo `/etc/nginx/conf.d/magento_es_auth.conf` con los siguientes contenidos:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Reiniciar nginx:

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

   Se muestran mensajes similares a los siguientes para indicar que se ha realizado correctamente:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicación segura con nginx

En esta sección se explica cómo configurar [Autenticación HTTP básica](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) con su proxy seguro. El uso conjunto de autenticación TLS y HTTP Basic evita que cualquier persona intercepte la comunicación con Elasticsearch o OpenSearch, o con su servidor de aplicaciones.

Dado que nginx admite de forma nativa la autenticación HTTP Basic, se recomienda realizar esta operación, por ejemplo, [Autenticación implícita](https://www.nginx.com/resources/wiki/modules/auth_digest/), que no se recomienda en producción.

Recursos adicionales:

* [Cómo configurar la autenticación de contraseña con Nginx en Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Autenticación HTTP básica con Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Ejemplo de configuraciones de Nginx para el Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Consulte las secciones siguientes para obtener más información:

* [Crear contraseñas](#create-a-password)
* [Configuración del acceso a nginx](#set-up-access-to-nginx)
* [Configuración de un contexto restringido para el motor de búsqueda](#set-up-a-restricted-context-for-the-search-engine)
* [Compruebe que la comunicación es segura](#secure-communication-with-nginx)

### Crear una contraseña

Le recomendamos que utilice Apache `htpasswd` para codificar las contraseñas de un usuario con acceso a Elasticsearch u OpenSearch (denominado `magento_elasticsearch` en este ejemplo).

Para crear una contraseña:

1. Introduzca el siguiente comando para determinar si `htpasswd` ya está instalado:

   ```bash
   which htpasswd
   ```

   Si se muestra una ruta, se instala; si el comando no devuelve ninguna salida, `htpasswd` no está instalado.

1. Si es necesario, instale `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Crear un `/etc/nginx/passwd` directorio para almacenar contraseñas:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Por motivos de seguridad, `<filename>` debe estar oculta; es decir, debe comenzar con un punto.

1. *(Opcional).* Para agregar otro usuario al archivo de contraseñas, escriba el mismo comando sin el `-c` Opción (crear):

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Compruebe que el contenido de `/etc/nginx/passwd` es correcto.

### Configuración del acceso a nginx

En esta sección se explica cómo especificar quién puede acceder al servidor de nginx.

>[!WARNING]
>
>El ejemplo mostrado es para un *inseguro* proxy. Para utilizar un proxy seguro, agregue el siguiente contenido (excepto el puerto de escucha) al bloque de servidor seguro.

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
>El puerto de escucha del motor de búsqueda que se muestra en el ejemplo anterior solo son ejemplos. Por motivos de seguridad, le recomendamos que utilice un puerto de escucha no predeterminado.

### Configuración de un contexto restringido para el motor de búsqueda

En esta sección se explica cómo especificar quién puede acceder al servidor del motor de búsqueda.

1. Introduzca el siguiente comando para crear un directorio donde almacenar la configuración de autenticación:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Uso de un editor de texto para crear un archivo `/etc/nginx/auth/magento_elasticsearch.conf` con los siguientes contenidos:

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
