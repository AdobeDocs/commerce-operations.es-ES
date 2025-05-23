---
title: Software Recommendations
description: Revise la lista de software recomendado relacionado con el rendimiento óptimo de las implementaciones de Adobe Commerce.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Recomendaciones de software

Se necesita el siguiente software para las instancias de producción de [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx y [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] o OpenSearch](../installation/prerequisites/search-engine/overview.md)

Para implementaciones de varios servidores o para comerciantes que planeen ampliar su negocio, le recomendamos lo siguiente:

* [Caché de [!DNL Varnish]](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) para sesiones (de la versión 2.0.6 o posterior)
* Una instancia de Redis independiente como su [caché predeterminada](../configuration/cache/redis-pg-cache.md) (no use esta instancia para la caché de la página)

Consulte [requisitos del sistema](../installation/system-requirements.md) para obtener información sobre las versiones compatibles de cada tipo de software.

## Sistema operativo

Las configuraciones y optimizaciones del sistema operativo son similares para [!DNL Commerce] en comparación con otras aplicaciones web de carga alta. A medida que aumenta el número de conexiones simultáneas gestionadas por el servidor, el número de sockets disponibles puede asignarse por completo. El núcleo Linux soporta un mecanismo para &quot;reutilizar&quot; conexiones TCP. Para habilitar este mecanismo, establezca el siguiente valor en `/etc/sysctl.conf`:

>[!INFO]
>
>Habilitar net.ipv4.tcp_tw_reuse no tiene ningún efecto en las conexiones entrantes.

```text
net.ipv4.tcp_tw_reuse = 1
```

El parámetro del núcleo `net.core.somaxconn` controla el número máximo de sockets abiertos que esperan conexiones. Este valor puede aumentarse de forma segura a 1024, pero debe correlacionarse con la capacidad del servidor para gestionar esta cantidad. Para habilitar este parámetro del núcleo, establezca el siguiente valor en `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

El Magento es totalmente compatible con PHP 7.3 y 7.4. Hay varios factores a tener en cuenta al configurar PHP para obtener la máxima velocidad y eficiencia en el procesamiento de solicitudes.

### Extensiones de PHP

Se recomienda limitar la lista de extensiones de PHP activas a las necesarias para la funcionalidad de [!DNL Commerce].

Magento Open Source y Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-sodio
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Además, Adobe Commerce requiere:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-sodio
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Añadir más extensiones aumenta los tiempos de carga de la biblioteca.

>[!INFO]
>
>`php-mcrypt` ha sido eliminado de PHP 7.2 y reemplazado por la biblioteca [`sodium`](https://www.php.net/manual/en/book.sodium.php). Asegúrese de que [sodio](https://www.php.net/manual/en/sodium.installation.php) esté habilitado correctamente al actualizar PHP.

>[!INFO]
>
>La presencia de cualquier extensión de generación de perfiles y depuración puede afectar negativamente al tiempo de respuesta de las páginas. Por ejemplo, un módulo xDebug activo sin ninguna sesión de depuración puede aumentar el tiempo de respuesta de la página hasta en un 30 %.

### Configuración de PHP

Para garantizar la ejecución correcta de todas las instancias de [!DNL Commerce] sin volcar datos o código en el disco, establezca el límite de memoria de la siguiente manera:

```text
memory_limit=1G
```

Para la depuración, aumente este valor a 2G.

#### Configuración de Realpath_cache

Para mejorar el rendimiento de [!DNL Commerce], agregue o actualice la siguiente configuración `realpath_cache` recomendada en el archivo `php.ini`. Esta configuración permite a los procesos de PHP almacenar en caché las rutas a los archivos en lugar de buscarlos cada vez que se carga una página. Consulte [Ajuste del rendimiento](https://www.php.net/manual/en/ini.core.php) en la documentación de PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Para obtener la máxima velocidad de [!DNL Commerce] en PHP 7, debe activar el módulo OpCache y configurarlo correctamente. Se recomiendan estas configuraciones para el módulo:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Al ajustar la asignación de memoria para opcache, tenga en cuenta el tamaño del código base de Magento y todas las extensiones. El equipo de rendimiento de Magento utiliza los valores del ejemplo anterior para realizar pruebas, ya que proporciona suficiente espacio en opcache para el promedio de extensiones instaladas.

Si tiene un equipo con poca memoria y no tiene instaladas muchas extensiones o personalizaciones, utilice la siguiente configuración para obtener un resultado similar:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Se recomienda habilitar la extensión [PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) y [configurar `composer` para admitirla](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) a fin de optimizar el rendimiento máximo. Esta extensión almacena en caché las ubicaciones de los archivos abiertos, lo que aumenta el rendimiento de las llamadas al servidor [!DNL Commerce], incluidas las páginas, las llamadas Ajax y los extremos.

Edite el archivo `apcu.ini` para incluir lo siguiente:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Servidor web

Magento es totalmente compatible con los servidores web Nginx y Apache. [!DNL Commerce] proporciona archivos de configuración recomendados de ejemplo en los archivos `<magento_home>/nginx.conf.sample` (Nginx) y `<magento_home>.htaccess.sample` (Apache).  La muestra Nginx contiene ajustes para un mejor rendimiento y está diseñada para que se requiera poca reconfiguración. Algunas de las prácticas recomendadas de configuración principales definidas en el archivo de muestra son las siguientes:

* Configuración para almacenar en caché contenido estático en un explorador
* Ajustes de memoria y tiempo de ejecución para PHP
* Configuración de compresión de contenido

También debe configurar el número de hilos para el procesamiento de solicitudes de entrada, como se muestra a continuación:

| Servidor web | Nombre de atributo | Ubicación | Información relacionada |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Ajuste de NGINX para el rendimiento](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Ajuste de rendimiento de Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Directivas comunes de Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Este documento no proporciona instrucciones detalladas de ajuste de [!DNL MySQL] porque cada tienda y entorno son diferentes, pero podemos hacer algunas recomendaciones generales.

Se han realizado muchas mejoras en [!DNL MySQL] 5.7.9 Confiamos en que [!DNL MySQL] se distribuya con una buena configuración predeterminada. Las configuraciones más críticas son:

| Parámetro | Predeterminado | Descripción |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | El valor predeterminado se establece en 8 para evitar problemas con varios subprocesos que intentan acceder a la misma instancia. |
| `innodb_buffer_pool_size` | 128 MB | En combinación con las instancias de grupo múltiples descritas anteriormente, esto significa una asignación de memoria predeterminada de 1024 MB. El tamaño total se divide entre todos los grupos de búferes. Para obtener la máxima eficacia, especifique una combinación de `innodb_buffer_pool_instances` y `innodb_buffer_pool_size` de modo que cada instancia de grupo de búferes tenga al menos 1 GB. |
| `max_connections` | 150 | El valor del parámetro `max_connections` debe correlacionarse con el número total de subprocesos PHP configurados en el servidor de aplicaciones. Una recomendación general sería 300 para un entorno pequeño y 1.000 para un medio ambiente mediano. |
| `innodb_thread_concurrency` | 0 | El mejor valor para esta configuración se debe calcular mediante la fórmula: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

El Magento recomienda encarecidamente usar [!DNL Varnish] como servidor de caché de página completa para su tienda. El módulo PageCache sigue presente en la base de código, pero debe usarse únicamente con fines de desarrollo. No se debe usar junto con [!DNL Varnish] ni en su lugar.

Instale [!DNL Varnish] en un servidor independiente delante del nivel web. Debe aceptar todas las solicitudes entrantes y proporcionar copias de las páginas en caché. Para permitir que [!DNL Varnish] funcione correctamente con páginas seguras, se puede colocar un proxy de terminación SSL delante de [!DNL Varnish]. Nginx se puede utilizar para este fin.

[!DNL Commerce] distribuye un archivo de configuración de ejemplo para [!DNL Varnish] (versiones 4 y 5) que contiene todas las opciones recomendadas para el rendimiento. Entre ellos, los más críticos en términos de rendimiento son:

* **Comprobación de estado back-end** sondea el servidor [!DNL Commerce] para determinar si responde a tiempo.
* **El modo de gracia** le permite indicar a [!DNL Varnish] que mantenga un objeto en la caché más allá de su período de tiempo de vida (TTL) y que sirva este contenido obsoleto si [!DNL Commerce] no está en buen estado o si aún no se ha recuperado contenido nuevo.
* **Modo Saint** pone en lista negra servidores [!DNL Commerce] que no están en buen estado durante un período de tiempo configurable. Como resultado, los backends que no están en buen estado no pueden servir tráfico al usar [!DNL Varnish] como equilibrador de carga.

Consulte [Configuración avanzada [!DNL Varnish] 2&rbrace; para obtener más información sobre cómo implementar estas características.](../configuration/cache/config-varnish-advanced.md)

### Optimizar el rendimiento del recurso

En general, recomendamos almacenar los recursos (imágenes, JS, CSS, etc.) en una CDN para obtener un rendimiento óptimo.

Si su sitio no requiere la implementación de un gran número de configuraciones regionales y los servidores se encuentran en la misma región que la mayoría de sus clientes, puede encontrar mejoras de rendimiento significativas a un costo menor almacenando los recursos en [!DNL Varnish] en lugar de usar una CDN.

Para almacenar los recursos en [!DNL Varnish], agregue las siguientes entradas VCL al archivo `default.vcl` generado por [!DNL Commerce] para [!DNL Varnish] 5.

Al final de la instrucción `if` para las solicitudes PURGE en la subrutina `vcl_recv`, agregue:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

En la subrutina `vcl_backend_response`, busque la instrucción `if` que anula la configuración de la cookie para las solicitudes `GET` o `HEAD`.
El bloque `if` actualizado debe tener el siguiente aspecto:

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Reinicie el servidor [!DNL Varnish] para vaciar los recursos en caché cada vez que actualice el sitio o implemente o actualice los recursos.

## Servidores de almacenamiento en caché y sesión

Magento proporciona una serie de opciones para almacenar los datos de la sesión y la memoria caché, incluidos Redis, Memcache, el sistema de archivos y la base de datos. Algunas de estas opciones se analizan a continuación.

### Configuración de nodo web único

Si planea servir todo el tráfico con un solo nodo web, no tiene sentido colocar la caché en un servidor remoto de Redis. En su lugar, utilice el sistema de archivos o un servidor local de Redis. Si desea utilizar el sistema de archivos, coloque las carpetas de la caché en un volumen montado en un sistema de archivos RAM. Si desea utilizar un servidor Redis local, le recomendamos encarecidamente que configure Redis para que utilice sockets para conexiones directas, en lugar de intercambiar datos a través de HTTP.

### Configuración de varios nodos web

Para una configuración de varios nodos web, Redis es la mejor opción. Dado que [!DNL Commerce] almacena en caché activamente muchos datos para obtener un mejor rendimiento, preste atención al canal de red entre los nodos web y el servidor Redis. No desea que el canal se convierta en un cuello de botella para el procesamiento de solicitudes.

>[!INFO]
>
>Si necesita servir cientos y miles de solicitudes simultáneas, puede necesitar un canal de hasta 1 Gbit (o incluso más ancho) a su servidor Redis.
