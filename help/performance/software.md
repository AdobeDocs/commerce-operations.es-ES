---
title: Software Recommendations
description: Revise una lista de software recomendado relacionado con el rendimiento óptimo de las implementaciones de Adobe Commerce y Magento Open Source.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '1476'
ht-degree: 0%

---


# Recomendaciones de software

Necesitamos el siguiente software para las instancias de producción de [!DNL Commerce]:

* [PHP](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html)
* Nginx y [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html)
* [[!DNL Elasticsearch] o OpenSearch](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html)

Para implementaciones de varios servidores o para comerciantes que planifiquen la ampliación de su negocio, se recomienda lo siguiente:

* [[!DNL Varnish] cache](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish.html)
* [Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-session.html) para sesiones (a partir de 2.0.6+)
* Una instancia de Redis independiente como su [caché predeterminada](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html) (no utilice esta instancia para la caché de página)

Consulte [requisitos del sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) para obtener información sobre las versiones compatibles de cada tipo de software.

## Sistema operativo

Las configuraciones y optimizaciones del sistema operativo son similares para [!DNL Commerce] en comparación con otras aplicaciones web de carga alta. A medida que aumenta el número de conexiones simultáneas gestionadas por el servidor, el número de sockets disponibles se puede asignar completamente. El núcleo Linux soporta un mecanismo para &quot;reutilizar&quot; conexiones TCP. Para habilitar este mecanismo, establezca el siguiente valor en `/etc/sysctl.conf`:

>[!INFO]
>
>Habilitar net.ipv4.tcp_tw_reuse no tiene ningún efecto en las conexiones entrantes.

```terminal
net.ipv4.tcp_tw_reuse = 1
```

El parámetro del núcleo `net.core.somaxconn` controla el número máximo de sockets abiertos que esperan conexiones. Este valor puede aumentarse de forma segura a 1024, pero debe correlacionarse con la capacidad del servidor para gestionar esta cantidad. Para habilitar este parámetro del núcleo, establezca el siguiente valor en `/etc/sysctl.conf`:

`net.core.somaxconn = 1024`

## PHP

Magento es totalmente compatible con PHP 7.3 y 7.4. Existen varios factores a tener en cuenta al configurar PHP para obtener la máxima velocidad y eficacia en el procesamiento de solicitudes.

### Extensiones PHP

Se recomienda limitar la lista de extensiones PHP activas a las que se requieren para [!DNL Commerce] funcionalidad.

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
* tomas de texto
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
* tomas de texto
* ext-sodio
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Añadir más extensiones aumenta los tiempos de carga de las bibliotecas.

>[!INFO]
>
>`php-mcrypt` se ha eliminado de PHP 7.2 y se ha sustituido por el [`sodium` biblioteca](https://www.php.net/manual/en/book.sodium.php). Asegúrese de que [sodio](https://www.php.net/manual/en/sodium.installation.php) se habilita correctamente al actualizar PHP.

>[!INFO]
>
>La presencia de cualquier extensión de creación de perfiles y depuración puede afectar negativamente al tiempo de respuesta de las páginas. Por ejemplo, un módulo xDebug activo sin ninguna sesión de depuración puede aumentar el tiempo de respuesta de la página hasta un 30%.

### Configuración de PHP

Para garantizar la ejecución correcta de todas las [!DNL Commerce] instancias sin transferir datos o código al disco, establezca el límite de memoria de la siguiente manera:

`memory_limit=1G`

Para la depuración, aumente este valor a 2G.

#### Configuración de Realpath_cache

Para mejorar [!DNL Commerce] rendimiento, añadir o actualizar lo siguiente recomendado `realpath_cache` en la `php.ini` archivo. Esta configuración permite que los procesos PHP almacenen en caché las rutas a los archivos en lugar de buscarlas cada vez que se carga una página. Consulte [Ajuste del rendimiento](https://www.php.net/manual/en/ini.core.php) en la documentación de PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Para obtener la máxima velocidad de [!DNL Commerce] en PHP 7, debe activar el módulo OpCache y configurarlo correctamente. Se recomiendan estas configuraciones para el módulo :

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Al ajustar la asignación de memoria para opcache, tenga en cuenta el tamaño de la base de código del Magento y todas las extensiones. El equipo de rendimiento del Magento utiliza los valores del ejemplo anterior para realizar pruebas, ya que proporciona suficiente espacio en opcache para el número promedio de extensiones instaladas.

Si tiene un equipo de memoria baja y no tiene muchas extensiones o personalizaciones instaladas, utilice la siguiente configuración para obtener un resultado similar:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Se recomienda habilitar la variable [Extensión PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) y [configurar `composer` para admitirlo](https://devdocs.magento.com/guides/v2.4/performance-best-practices/deployment-flow.html#preprocess-dependency-injection-instructions) para optimizar y obtener el máximo rendimiento. Esta extensión almacena en caché las ubicaciones de archivos para los archivos abiertos, lo que aumenta el rendimiento de [!DNL Commerce] llamadas al servidor, incluidas páginas, llamadas de Ajax y extremos.

Edite su `apcu.ini` para incluir lo siguiente:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Servidor web

Magento es totalmente compatible con los servidores web Nginx y Apache. [!DNL Commerce] proporciona archivos de configuración recomendados de ejemplo en la variable  `<magento_home>/nginx.conf.sample` (Nginx) y  `<magento_home>.htaccess.sample` (Apache).  El ejemplo de Nginx contiene ajustes para un mejor rendimiento y está diseñado para que se requiera poca reconfiguración. Algunas de las principales prácticas recomendadas de configuración definidas en el archivo de muestra son:

* Configuración para almacenar en caché contenido estático en un explorador
* Configuración de memoria y tiempo de ejecución para PHP
* Configuración de compresión de contenido

También debe configurar el número de subprocesos para el procesamiento de solicitudes de entrada, como se indica a continuación:

| Servidor web | Nombre del atributo | Ubicación | Información relacionada |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Ajuste de NGINX para el rendimiento](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Ajuste del rendimiento de Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Directivas comunes de Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Este documento no proporciona información detallada [!DNL MySQL] las instrucciones de ajuste, ya que cada tienda y entorno es diferente, pero podemos hacer algunas recomendaciones generales.

Se han realizado muchas mejoras en [!DNL MySQL] 5.7.9 Confiamos en que [!DNL MySQL] se distribuye con una buena configuración predeterminada. Los ajustes más importantes son:

| Parámetro | Predeterminado | Descripción |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | El valor predeterminado está establecido en 8 para evitar problemas con varios subprocesos que intentan acceder a la misma instancia. |
| `innodb_buffer_pool_size` | 128 MB | Combinado con las múltiples instancias de pool descritas anteriormente, esto significa una asignación de memoria predeterminada de 1024 MB. El tamaño total se divide entre todos los grupos de búfer. Para obtener la mejor eficiencia, especifique una combinación de `innodb_buffer_pool_instances` y `innodb_buffer_pool_size` de modo que cada instancia de pool de búferes sea de al menos 1 GB. |
| `max_connections` | 150 | El valor de la variable `max_connections` debe correlacionarse con el número total de subprocesos PHP configurados en el servidor de aplicaciones. Una recomendación general sería 300 para un entorno pequeño y 1.000 para un entorno mediano. |
| `innodb_thread_concurrency` | 0 | El mejor valor para esta configuración debe calcularse con la fórmula : `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento recomienda encarecidamente usar [!DNL Varnish] como servidor de caché de página completa para su tienda. El módulo PageCache sigue presente en la base de código, pero solo debe utilizarse para fines de desarrollo. No debe usarse junto con, o en lugar de, [!DNL Varnish].

Instalar [!DNL Varnish] en un servidor independiente delante del nivel web. Debe aceptar todas las solicitudes entrantes y proporcionar copias de páginas en caché. Para permitir [!DNL Varnish] para trabajar de forma eficaz con páginas seguras, se puede colocar un proxy de terminación SSL delante de [!DNL Varnish]. Nginx puede utilizarse para este fin.

[!DNL Commerce] distribuye un archivo de configuración de ejemplo para [!DNL Varnish] (versiones 4 y 5) que contiene todas las configuraciones recomendadas para el rendimiento. Entre ellos, los más críticos en términos de rendimiento son:

* **Comprobación de estado del back-end** sondeos [!DNL Commerce] para determinar si está respondiendo a tiempo.
* **Modo de gracia** permite instruir [!DNL Varnish] para mantener un objeto en la caché más allá del periodo de tiempo de vida (TTL) y servir este contenido obsoleto si [!DNL Commerce] no está en buen estado o si aún no se ha recuperado contenido nuevo.
* **Modo Saint** listas negras no saludables [!DNL Commerce] por una cantidad de tiempo configurable. Como resultado, los backends no sanos no pueden servir tráfico al usar [!DNL Varnish] como equilibrador de carga.

Consulte [Avanzadas [!DNL Varnish] configuración](https://devdocs.magento.com/guides/v2.4/config-guide/varnish/config-varnish-advanced.html) para obtener más información sobre la implementación de estas funciones.

### Optimizar el rendimiento de los recursos

En general, recomendamos almacenar sus recursos (imágenes, JS, CSS, etc.) en una CDN para obtener un rendimiento óptimo.

Si el sitio no requiere la implementación de un gran número de configuraciones regionales y los servidores se encuentran en la misma región que la mayoría de los clientes, es posible que se obtengan mejoras de rendimiento significativas a un costo menor al almacenar los recursos en [!DNL Varnish] en lugar de usar una CDN.

Para almacenar los recursos en [!DNL Varnish], añada las siguientes entradas de VCL en su `default.vcl` archivo generado por [!DNL Commerce] para [!DNL Varnish] 5.

Al final del `if` para solicitudes PURGE en el `vcl_recv` subrutina, agregue:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

En el `vcl_backend_response` subrutina, busque la `if` que desestablece la cookie para `GET` o `HEAD` solicitudes.
El `if` debe tener un aspecto similar al siguiente:

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

Reinicie el [!DNL Varnish] para vaciar recursos en caché cada vez que actualice su sitio o implemente/actualice recursos.

## Almacenamiento en caché y servidores de sesión

Magento proporciona una serie de opciones para almacenar su caché y sus datos de sesión, incluyendo Redis, Memcache, filesystem y base de datos. A continuación se examinan algunas de estas opciones.

### Configuración de nodo web único

Si planea servir todo su tráfico con un solo nodo web, no tiene sentido poner la caché en un servidor remoto de Redis. En su lugar, utilice el sistema de archivos o un servidor de Redis local. Si desea utilizar el sistema de archivos, coloque sus carpetas de caché en un volumen montado en un sistema de archivos RAM. Si desea utilizar un servidor de Redis local, le recomendamos encarecidamente que configure Redis para que utilice sockets para conexiones directas en lugar de intercambiar datos a través de HTTP.

### Configuración de varios nodos web

Para la configuración de varios nodos web, Redis es la mejor opción. Porque [!DNL Commerce] almacena en caché activamente muchos datos para un mejor rendimiento, preste atención al canal de red entre los nodos web y el servidor de Redis. No desea que el canal se convierta en un cuello de botella para el procesamiento de solicitudes.

>[!INFO]
>
>Si necesita servir cientos y miles de solicitudes simultáneas, puede que necesite un canal de hasta 1 Gbit (o incluso más amplio) a su servidor de Redis.
