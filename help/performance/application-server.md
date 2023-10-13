---
title: Servidor de aplicaciones para API de GraphQL
description: Siga estas instrucciones para habilitar el servidor de aplicaciones para las API de GraphQL en la implementación de Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b7639e8830b2cab971e3e22285d91105b64e9a6e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# Servidor de aplicaciones para API de GraphQL

Commerce Application Server para las API de GraphQL permite a Adobe Commerce mantener el estado entre las solicitudes de la API de Commerce GraphQL. El servidor de aplicaciones, que se crea en la extensión Open Swoole, funciona como un proceso con subprocesos de trabajo que administran el procesamiento de solicitudes. Al preservar un estado de aplicación de arranque entre las solicitudes de API de GraphQL, Application Server mejora la gestión de solicitudes y el rendimiento general del producto. Las solicitudes de API son mucho más eficientes.

Application Server solo es compatible con Cloud Starter e implementaciones locales. No está disponible para instancias de Cloud Pro durante la versión beta. No está disponible para implementaciones de Magento Open Source.

## Información general sobre la arquitectura de Application Server

Application Server mantiene el estado entre las solicitudes de la API de Commerce GraphQL y elimina la necesidad del arranque. Al compartir el estado de la aplicación entre procesos, las solicitudes de GraphQL se vuelven considerablemente más eficientes, lo que reduce los tiempos de respuesta en hasta un 30 %.

El modelo de ejecución de PHP que no comparte nada proporciona un desafío desde la perspectiva de la latencia porque cada solicitud requiere el arranque del marco de trabajo. Este proceso de arranque incluye tareas que llevan mucho tiempo, como leer la configuración, configurar el proceso de arranque y crear objetos de clase de servicio.

La transición de la lógica de gestión de solicitudes a un bucle de eventos de nivel de aplicación parece abordar el desafío de racionalizar el procesamiento de solicitudes a nivel empresarial. Este método elimina la necesidad del arranque durante el ciclo de vida de la ejecución de la solicitud.

## Ventajas de utilizar Application Server

Application Server permite a Adobe Commerce mantener el estado entre solicitudes consecutivas de la API de Commerce GraphQL. Compartir el estado de la aplicación entre solicitudes mejora la eficacia de las solicitudes de API al minimizar la sobrecarga de procesamiento y optimizar la administración de solicitudes. Como resultado, el tiempo de respuesta de las solicitudes de GraphQL se puede reducir hasta un 30 %.

## Requisitos del sistema

La ejecución del servidor de aplicaciones requiere lo siguiente:

* PHP 8.2 o superior
* Abrir extensión Swoole PHP v22+ instalada
* RAM y CPU adecuadas en función de la carga esperada

## Habilitar Application Server para Cloud Starter

El `ApplicationServer` módulo (`Magento/ApplicationServer/`) habilita Application Server para las API de GraphQL. Application Server solo es compatible con implementaciones locales y de Cloud Starter. No está disponible para instancias de Cloud Pro durante la versión beta.

### Antes de comenzar una implementación de Cloud Starter

Complete las tareas siguientes antes de desplegar Application Server:

1. Confirme que Adobe Commerce está instalado en el Commerce Cloud.
1. Confirme que la variable `CRYPT_KEY` La variable de entorno está configurada para su instancia. Puede comprobar el estado de esta variable en el portal del proyecto en la nube (interfaz de usuario de incorporación).
1. Clone el proyecto de Commerce Cloud.
1. Crear un `graphql` carpeta en su `project_root` carpeta.
1. Añadir el personalizado adicional `.magento.app.yaml` archivo incluido en el [contenido del archivo magento.app.yaml](#magento.app.yaml-file-content) tema en su `project_root/graphql` carpeta.
1. Edite el `project_root/.magento/routes.yaml` para incluir estas directivas:

   ```yaml
   # The routes of the project.
   #
   # Each route describes how an incoming URL is going to be processed.
   
   "http://{default}/":
     type: upstream
     upstream: "mymagento:http"
   
   "http://{default}/graphql":
     type: upstream
     upstream: "graphql:http"
   ```

1. Añada archivos actualizados al índice de Git con este comando:

   ```bash
   git add -f php.ini graphql/.magento.app.yaml .magento/routes.yaml swoole.so
   ```

1. Confirme los cambios con este comando:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Implementar Application Server en Cloud Starter

Después de realizar las tareas previas necesarias, implemente Application Server con este comando:

```bash
git push
```

### Verificar la activación del servidor de aplicaciones en Cloud Starter

1. Abra la interfaz de usuario del proyecto en la nube. Debería ver un punto de acceso SSH adicional para `graphql` aplicación.

1. Utilice SSH para acceder a la instancia de Cloud mediante el punto de acceso de la aplicación graphql y, a continuación, ejecute el siguiente comando:

   ```bash
   ps aux|grep php
   ```

1. Realice una consulta o mutación de GraphQL en la instancia para confirmar que la variable `graphql` el punto de conexión es accesible. Por ejemplo:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La respuesta esperada debe ser similar a este ejemplo:

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Utilice SSH para acceder a su instancia de Cloud a través del punto de acceso de la aplicación GraphQL. El `project_root/var/log/magento-server.log` debe contener un nuevo registro para cada solicitud de GraphQL.

Si estos pasos de verificación son correctos, puede continuar con la ejecución del ciclo de prueba.


## Habilitar Application Server en implementaciones locales

El `ApplicationServer` módulo (`Magento/ApplicationServer/`) habilita Application Server para las API de GraphQL.

La ejecución de Application Server requiere la instalación de la extensión Open Swoole y un cambio menor en el archivo de configuración Nginx de la implementación para ejecutar este servidor de aplicaciones localmente.

### Antes de comenzar una implementación local

Complete estas dos tareas antes de habilitar la variable `ApplicationServer` módulo:

* Configuración De Nginx

* Instale y configure la extensión Open Swoole v22

### Configuración De Nginx

Su implementación específica de Commerce determina cómo configurar Nginx. En general, el nombre predeterminado del archivo de configuración de Nginx es `nginx.conf` y se coloca en uno de estos directorios: `/usr/local/nginx/conf`, `/etc/nginx`, o `/usr/local/etc/nginx`. Consulte [Guía para principiantes](https://nginx.org/en/docs/beginners_guide.html) para obtener más información sobre la configuración de Nginx.

Ejemplo de configuración de Nginx:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Instalar y configurar Open Swoole

Para ejecutar Application Server localmente, instale la extensión Open Swoole v22. Existen varias formas de instalar esta extensión.

## Ejecutar servidor de aplicaciones

Inicie el servidor de aplicaciones:

```bash
bin/magento server:run
```

Este comando inicia un puerto HTTP en 9501. Una vez que Application Server se inicia, el puerto 9501 se convierte en un servidor proxy HTTP para todas las consultas de GraphQL.

## Ejemplo: Instalación de una ranura abierta (OSX)

Este procedimiento ilustra cómo instalar la extensión Open Swoole en PHP 8.2 para sistemas OSX. Es una de las varias formas de instalar la extensión Open Swoole.

### Instale la ranura abierta

Introduzca:

```bash
pecl install openswoole-22.0.0
composer require openswoole/core:22.1.1
```

Durante la instalación, Adobe Commerce muestra mensajes para habilitar la compatibilidad con `openssl`, `mysqlnd`, `sockets`, `http2`, y `postgres`. Entrar `yes` para todas las opciones excepto `postgres`.

### Confirme la instalación de la ranura abierta.

Ejecutar `php -m | grep openswoole` para confirmar que la extensión se ha habilitado correctamente.

### Errores comunes con la instalación de Open Swoole

Cualquier error que se produzca durante la instalación del Open Single suele ocurrir durante el `pecl` fase de instalación. Los errores habituales incluyen la falta de `openssl.h` y `pcre2.h` archivos. Para resolver estos errores, asegúrese de que estos dos paquetes estén instalados en el sistema local.

* Compruebe la ubicación de `openssl` ejecutando:

```bash
openssl version -d
```

Este comando muestra la ruta donde `openssl` está instalado.

* Compruebe la ubicación de `pcre2` ejecutando:

```bash
pcre2-config --prefix 
```

Utilice Homebrew para instalar los paquetes que faltan si la salida del comando indica que faltan archivos:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Resolver problemas con openssl

Para resolver problemas relacionados con `openssl`, ejecute:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Confirme que está utilizando la ruta de su `dev` entorno.

#### Confirmar la resolución de los problemas relacionados con openssl

Puede ejecutar de nuevo el siguiente comando para comprobar si se han resuelto los problemas relacionados con openssl:

```bash
pecl install openswoole-22.0.0
```

#### Solución de problemas con pcre2.h

Para resolver problemas relacionados con `pcre2.h`, enlace simbólico `pcre2.h` ruta al directorio de extensiones PHP instalado. Su versión instalada específica de PHP y `pcr2.h` determina la versión concreta del comando que debe utilizar.

### Confirme que el servidor de aplicaciones se está ejecutando.

Para confirmar que Application Server se está ejecutando en la implementación, ejecute este comando:

```bash
ps aux | grep php
```

Formas adicionales de confirmar que Application Server se está ejecutando incluyen:

* Compruebe la `/var/log/magento-server.log` para entradas relacionadas con solicitudes de GraphQL procesadas.
* Intente conectarse al puerto HTTP en el que se ejecuta Application Server. Por ejemplo: `curl -g 'http://localhost:9501/graph`.

### Confirme que Application Server está procesando las solicitudes de GraphQL.

Application Server agrega `X-Backend` encabezado de respuesta con el valor `graphql_server` a cada solicitud que procesa. Para comprobar si el servidor de aplicaciones ha gestionado una solicitud, compruebe este encabezado de respuesta.

### Confirmar la compatibilidad de extensión y personalización con el servidor de aplicaciones

Los desarrolladores y comerciantes de extensiones deben comprobar primero que su código de extensión y personalización cumple las directrices técnicas descritas en [Directrices técnicas](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Tenga en cuenta estas directrices durante la evaluación del código:

* Clases de servicio (es decir, clases que proporcionan comportamiento pero no datos, como `EventManager`) no debería tener un estado mutable.
* Evite el acoplamiento temporal.

## Deshabilitar servidor de aplicaciones

Los procedimientos para desactivar Application Server varían en función de si el servidor se está ejecutando en una implementación local o en la nube.

### Deshabilitar Application Server en Cloud Starter

1. Elimine los nuevos archivos y cualquier otro cambio de código que se haya incluido en la `AppServer Enabled` confirme durante los preparativos para la implementación.

1. Confirme los cambios con este comando:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Implemente estos cambios con este comando:

   ```bash
   git push
   ```

### Deshabilitar servidor de aplicaciones

1. Comente el `/graphql` sección de `nginx.conf` que agregó al habilitar el servidor de aplicaciones.
1. Reinicie nginx.

Este método de deshabilitar Application Server puede resultar útil para probar o comparar rápidamente el rendimiento.

### Confirme que Servidor de aplicaciones está deshabilitado.

Para confirmar que procesa las solicitudes de GraphQL `php-fpm` en lugar de Servidor de aplicaciones, introduzca este comando: `ps aux | grep php`.

Después de deshabilitar Application Server:

* `bin/magento server:run` está inactivo.
* `var/log/magento-server.log` no contiene entradas después de las solicitudes de GraphQL.

## Pruebas funcionales e integraciones para el servidor de aplicaciones PHP

Los desarrolladores de extensiones pueden ejecutar dos pruebas de integración para comprobar la compatibilidad de la extensión con el servidor de aplicaciones: `GraphQlStateTest` y `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` detecta el estado en objetos compartidos que no deben reutilizarse en varias solicitudes.

Esta prueba está diseñada para detectar cambios de estado en los objetos de servicio producidos por el `ObjectManager`. La prueba ejecuta consultas de GraphQL idénticas dos veces y compara el estado del objeto de servicio antes y después de la segunda consulta. 

#### Errores de GraphQlStateTest y posible corrección

* **No se puede agregar, omitir ni filtrar una lista**. Si se produce un error que sugiere que no es seguro agregar, omitir o filtrar una lista, considere si la clase se puede refactorizar de una manera compatible con versiones anteriores para utilizar las fábricas de las clases de servicio que tienen estado mutable.

* **La clase muestra un estado mutable**. Si la propia clase muestra un estado mutable, intente reescribir el código para evitar este estado. Si el estado mutable es necesario por motivos de rendimiento, implemente `ResetAfterRequestInterface` y utilice `_resetState()` para restablecer el objeto a su estado construido inicial.

* **No se debe acceder a la propiedad escrita $x antes del mensaje de inicialización**. Los errores con este tipo de mensaje sugieren que el constructor no ha inicializado la propiedad especificada. Se trata de una forma de acoplamiento temporal que se produce porque el objeto no se puede utilizar después de construirse inicialmente. Este acoplamiento se produce incluso si la propiedad es privada porque el recolector que recupera los datos de las propiedades está utilizando la función de reflexión PHP. En este caso, intente refactorizar la clase para evitar el acoplamiento temporal y el estado mutable. Si esa refactorización no resuelve el error, puede cambiar el tipo de propiedad a un tipo que admita valores NULL para que se pueda inicializar en NULL.  Si la propiedad es una matriz, intente inicializar la propiedad como una matriz vacía.

Ejecutar `GraphQlStateTest` ejecutando `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` busca todas las clases que implementan `ResetAfterRequestInterface` y comprueba que la variable `_resetState()` devuelve el estado de un objeto al mismo estado que tenía después de ser construido por `ObjectManager`.  Esta prueba crea un objeto de servicio con `ObjectManager`, luego clona ese objeto, llama a `_resetState()`y, a continuación, compara ambos objetos. La prueba no llama a ningún método entre la creación de instancias de objeto y `_resetState()`, de modo que no se confirma el restablecimiento de ningún estado mutable. Encuentra problemas donde aparece un error o error tipográfico `_resetState()` puede establecer el estado en algo diferente de lo que era originalmente.

#### Errores de ResetAfterRequestTest y posibles correcciones

* **La clase tiene valores de propiedad incoherentes**. Si esta prueba falla, compruebe si una clase ha cambiado con el resultado de que el objeto después de la construcción tiene valores de propiedad diferentes de los que tiene después de la `_resetState()` método se llama. Si la clase en la que está trabajando no contiene `_resetState()` y, a continuación, compruebe la jerarquía de clases de una superclase que la implemente.

* **No se debe acceder a la propiedad escrita $x antes del mensaje de inicialización**. Este problema también se produce con `GraphQlStateTest`.
 
Ejecutar `ResetAfterRequestTest` ejecutando: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Pruebas funcionales

Los desarrolladores de extensiones deben ejecutar pruebas funcionales de WebAPI para GraphQL, así como cualquier prueba funcional automática o manual personalizada para GraphQL, mientras implementan el servidor de aplicaciones. Estas pruebas funcionales ayudan a los desarrolladores a identificar posibles errores o problemas de compatibilidad.

## contenido del archivo magento.app.yaml

Consulte [Antes de comenzar una implementación de Cloud Starter](#Before-you-begin-a-Cloud-Starter-deployment) para obtener instrucciones sobre cómo agregar el siguiente código a su `project_root/graphql` carpeta.

```yaml
name: graphql
# The toolstack used to build the application.
type: php:8.2
build:
    flavor: none
 
source:
    root: /
dependencies:
    php:
        composer/composer: '2.5.5'
 
# Enable extensions required by Magento 2
runtime:
    extensions:
        - xsl
        - sodium
 
# The relationships of the application with services or other applications.
# The left-hand side is the name of the relationship as it will be exposed
# to the application in the environment variable. The right-hand
# side is in the form `<service name>:<endpoint name>`.
relationships:
    database: "mysql:mysql"
    redis: "redis:redis"
    opensearch: "opensearch:opensearch"
 
# The configuration of app when it is exposed to the web.
web:
    commands:
        start: "php -dopcache.enable_cli=1 -dopcache.validate_timestamps=0 bin/magento server:run -vvv  --port=${PORT:-80} > ${MAGENTO_CLOUD_APP_DIR}/var/log/magento-server.log 2>&1"
    upstream:
        socket_family: tcp
        protocol: http
    locations:
        '/':
            root: "pub"
            passthru: true
 
# The size of the persistent disk of the application (in MB).
disk: 5120
 
# The mounts that will be performed when the package is deployed.
mounts:
    "var": "shared:files/var"
    "app/etc": "shared:files/etc"
    "pub/media": "shared:files/media"
    "pub/static": "shared:files/static"
 
hooks:
    # We run build hooks before your application has been packaged.
    build: |
        set -e
        composer install
        php ./vendor/bin/ece-tools run scenario/build/generate.xml
        php ./vendor/bin/ece-tools run scenario/build/transfer.xml
    # We run deploy hook after your application has been deployed and started.
    deploy: |
        php ./vendor/bin/ece-tools run scenario/deploy.xml
    # We run post deploy hook to clean and warm the cache. Available with ECE-Tools 2002.0.10.
    post_deploy: |
        php ./vendor/bin/ece-tools run scenario/post-deploy.xml
```
