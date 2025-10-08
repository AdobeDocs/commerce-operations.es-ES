---
title: GraphQL Application Server
description: Obtenga información sobre el servidor de aplicaciones graphql en Adobe Commerce. Descubra estrategias de optimización y directrices de implementación.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '2212'
ht-degree: 0%

---


# GraphQL Application Server

Commerce GraphQL Application Server permite a Adobe Commerce mantener el estado entre las solicitudes de API de Commerce GraphQL. GraphQL Application Server, que se basa en la extensión Swoole, funciona como un proceso con subprocesos de trabajo que administran el procesamiento de solicitudes. Al preservar un estado de aplicación de arranque entre las solicitudes de API de GraphQL, GraphQL Application Server mejora la gestión de solicitudes y el rendimiento general del producto. Las solicitudes de API son mucho más eficientes.

GraphQL Application Server solo está disponible para Adobe Commerce. No está disponible para Magento Open Source. Para los proyectos de Cloud Pro, debe [enviar un vale de soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para habilitar el servidor de aplicaciones de GraphQL.

>[!NOTE]
>
>GraphQL Application Server no es compatible actualmente con [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Los clientes de Adobe Commerce en la infraestructura en la nube que actualmente usan [!DNL AWS S3] para [almacenamiento remoto](../configuration/remote-storage/cloud-support.md) no pueden usar GraphQL Application Server.

## Arquitectura

El servidor de aplicaciones de GraphQL mantiene el estado entre las solicitudes de API de GraphQL de Commerce y elimina la necesidad del arranque. Al compartir el estado de la aplicación entre procesos, las solicitudes de GraphQL se vuelven considerablemente más eficientes, lo que reduce los tiempos de respuesta en hasta un 30 %.

El modelo de ejecución de PHP que no comparte nada proporciona un desafío desde la perspectiva de la latencia porque cada solicitud requiere el arranque del marco de trabajo. Este proceso de arranque incluye tareas que llevan mucho tiempo, como leer la configuración, configurar el proceso de arranque y crear objetos de clase de servicio.

La transición de la lógica de gestión de solicitudes a un bucle de eventos de nivel de aplicación parece abordar el desafío de racionalizar el procesamiento de solicitudes a nivel empresarial. Este método elimina la necesidad del arranque durante el ciclo de vida de la ejecución de la solicitud.

## Ventajas

El servidor de aplicaciones de GraphQL permite que Adobe Commerce mantenga el estado entre solicitudes consecutivas de la API de Commerce GraphQL. Compartir el estado de la aplicación entre solicitudes mejora la eficacia de las solicitudes de API al minimizar la sobrecarga de procesamiento y optimizar la administración de solicitudes. Como resultado, puede reducir el tiempo de respuesta de las solicitudes de GraphQL hasta en un 30 %.

## Requisitos del sistema

La ejecución de GraphQL Application Server requiere lo siguiente:

* Commerce versión 2.4.7+
* PHP 8.2 o superior
* RAM y CPU adecuados en función de la carga esperada
* Extensión Swoole PHP v5+ (consulte los requisitos específicos del proyecto a continuación)

### Proyectos en la nube

Adobe Commerce en proyectos de infraestructura en la nube incluye la extensión Swoole de forma predeterminada. Puede [habilitarlo](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) en la propiedad `runtime` del archivo `.magento.app.yaml`. Por ejemplo:

```yaml
runtime:
    extensions:
        - swoole
```

### Proyectos locales

Debe [instalar y configurar](#install-and-configure-swoole) manualmente la extensión Swoole PHP para proyectos locales.

## Habilitar e implementar en la infraestructura en la nube

El módulo `ApplicationServer` (`Magento/ApplicationServer/`) habilita GraphQL Application Server.

### Activar proyectos Pro

>[!NOTE]
>
>El servidor de aplicaciones es una función de inclusión en instancias de Cloud Pro. Para habilitarlo, envíe una solicitud de asistencia.

Una vez habilitada la función Servidor de aplicaciones en el proyecto Pro, complete los siguientes pasos antes de implementar GraphQL Application Server:

1. Implemente Adobe Commerce en la infraestructura de la nube mediante la plantilla de la nube desde la rama [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Asegúrese de que todas las personalizaciones y extensiones de Commerce sean [compatibles](https://developer.adobe.com/commerce/php/development/components/app-server/) con GraphQL Application Server.
1. Clone su proyecto de Commerce Cloud.
1. Ajuste la configuración en el archivo &quot;application-server/nginx.conf.sample&quot; si es necesario.
1. Comente completamente la sección &quot;web&quot; activa en el archivo `project_root/.magento.app.yaml`.
1. Elimine los comentarios de la siguiente configuración de sección &quot;web&quot; en el archivo `project_root/.magento.app.yaml` que incluye el comando `start` del servidor de aplicaciones de GraphQL.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Asegúrese de que `/application-server/start.sh` sea ejecutable ejecutando el siguiente comando:

   ```bash
   chmod +x application-server/start.sh
   ```

1. Añada archivos actualizados al índice de Git con este comando:

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Confirme los cambios con este comando:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Implementación de proyectos Pro

Después de completar los pasos de activación, inserte los cambios en el repositorio de Git para implementar GraphQL Application Server:

```bash
git push
```

### Habilitar proyectos iniciales

Complete los siguientes pasos antes de implementar GraphQL Application Server en proyectos iniciales:

1. Implemente Adobe Commerce en la infraestructura de la nube mediante la plantilla de la nube desde la rama [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Asegúrese de que todas las personalizaciones y extensiones de Commerce sean compatibles con GraphQL Application Server.
1. Confirme que la variable de entorno `CRYPT_KEY` esté configurada para su instancia. Puede comprobar el estado de esta variable en la consola de Cloud.
1. Clone su proyecto de Commerce Cloud.
1. Cambie el nombre de `application-server/.magento/.magento.app.yaml.sample` a `application-server/.magento/.magento.app.yaml` y ajuste la configuración en .magento.app.yaml si es necesario.
1. Elimine los comentarios de la configuración de la siguiente ruta en el archivo `project_root/.magento/routes.yaml` para redirigir el tráfico de `/graphql` a GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Elimine los comentarios de la sección `files` en el archivo `.magento/services.yaml`.

   ```yaml
   files:
       type: network-storage:2.0
       disk: 5120
   ```

1. Elimine los comentarios de la parte `TEMPORARY SHARED MOUNTS` de la configuración de montajes en el archivo `.magento.app.yaml`.

   ```yaml
   "var_shared":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc_shared":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media_shared":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static_shared":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. Añada archivos actualizados al índice de Git:

   ```bash
   git add -f .magento.app.yaml .magento/routes.yaml .magento/services.yaml application-server/.magento/*
   ```

1. Confirme los cambios e instálelos para almacenar en déclencheur una implementación:

   ```bash
   git commit -m "Enabling AppServer: initial changes"
   git push
   ```

1. Use SSH para iniciar sesión en el entorno de nube remoto (_no_ en la aplicación `application-server`):

   ```bash
   magento-cloud ssh -p <project-ID> -e <environment-ID>
   ```

1. Sincronice los datos de los montajes locales con los montajes compartidos:

   ```bash
   rsync -avz var/* var_shared/
   rsync -avz app/etc/* app/etc_shared/
   rsync -avz pub/media/* pub/media_shared/
   rsync -avz pub/static/* pub/static_shared/
   ```

1. Comente las partes `DEFAULT MOUNTS` y `TEMPORARY SHARED MOUNTS` de la configuración de montajes en el archivo `.magento.app.yaml`.

   ```yaml
   #"var": "shared:files/var"
   #"app/etc": "shared:files/etc"
   #"pub/media": "shared:files/media"
   #"pub/static": "shared:files/static"
   
   #"var_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "var"
   #"app/etc_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "etc"
   #"pub/media_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "media"
   #"pub/static_shared":
   #    source: "service"
   #    service: "files"
   #    source_path: "static"
   ```

1. Elimine los comentarios de las partes `OLD LOCAL MOUNTS` y `SHARED MOUNTS` de la configuración de montajes en el archivo `.magento.app.yaml`.

   ```yaml
   "var_old": "shared:files/var"
   "app/etc_old": "shared:files/etc"
   "pub/media_old": "shared:files/media"
   "pub/static_old": "shared:files/static"
   
   "var":
       source: "service"
       service: "files"
       source_path: "var"
   "app/etc":
       source: "service"
       service: "files"
       source_path: "etc"
   "pub/media":
       source: "service"
       service: "files"
       source_path: "media"
   "pub/static":
       source: "service"
       service: "files"
       source_path: "static"
   ```

1. Agregue el archivo actualizado al índice de Git, confirme los cambios e inserte en el déclencheur una implementación:

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: switch mounts"
   git push
   ```

1. Asegúrese de que los archivos de los directorios `*_old` estén presentes en los directorios reales.

1. Limpieza de montajes locales antiguos:

   ```bash
   rm -rf var_old/*
   rm -rf app/etc_old/*
   rm -rf pub/media_old/*
   rm -rf pub/static_old/*
   ```

1. Comente la parte `OLD LOCAL MOUNTS` de la configuración de montajes en el archivo `.magento.app.yaml`.

   ```yaml
   #"var_old": "shared:files/var"
   #"app/etc_old": "shared:files/etc"
   #"pub/media_old": "shared:files/media"
   #"pub/static_old": "shared:files/static"
   ```

1. Agregue el archivo actualizado al índice de Git, confirme los cambios e inserte en el déclencheur una implementación:

   ```bash
   git add -f .magento.app.yaml
   git commit -m "Enabling AppServer: finish"
   git push
   ```

>[!NOTE]
>
>Asegúrese de que todas las configuraciones personalizadas del archivo raíz `.magento.app.yaml` se migren correctamente al archivo `application-server/.magento/.magento.app.yaml`. Una vez agregado el archivo `application-server/.magento/.magento.app.yaml` al proyecto, debe mantenerlo además del archivo raíz `.magento.app.yaml`. Por ejemplo, si necesita [configurar el servicio RabbitMQ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/rabbitmq) o [administrar propiedades web](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/app/properties/web-property), también debe agregar la misma configuración a `application-server/.magento/.magento.app.yaml`.

### Verificar la habilitación en proyectos en la nube

1. Realice una consulta o mutación de GraphQL en la instancia para confirmar que el extremo `graphql` es accesible. Por ejemplo:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La respuesta esperada debe ser similar a este ejemplo:

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Utilice SSH para acceder a su instancia de Cloud. `project_root/var/log/application-server.log` debe contener un nuevo registro para cada solicitud de GraphQL.

1. También puede comprobar si GraphQL Application Server se está ejecutando ejecutando el siguiente comando:

   ```bash
   ps aux|grep php
   ```

   Debería ver un proceso `bin/magento server:run` con varios subprocesos.

Si estos pasos de comprobación se realizan correctamente, GraphQL Application Server se está ejecutando y está sirviendo `/graphql` solicitudes.

## Habilitar proyectos locales

El módulo `ApplicationServer` (`Magento/ApplicationServer/`) habilita GraphQL Application Server para las API de GraphQL.

La ejecución de GraphQL Application Server localmente requiere la instalación de la extensión Swoole y un cambio menor en el archivo de configuración Nginx de la implementación.

### Requisitos previos

Complete los siguientes pasos antes de habilitar el módulo `ApplicationServer`:

* Configuración De Nginx
* Instale y configure la extensión de Swoole v5+

#### Configuración De Nginx

Su implementación específica de Commerce determina cómo configurar Nginx. En general, el archivo de configuración Nginx se denomina de forma predeterminada `nginx.conf` y se coloca en uno de estos directorios: `/usr/local/nginx/conf`, `/etc/nginx` o `/usr/local/etc/nginx`. Consulte la _[Guía para principiantes](https://nginx.org/en/docs/beginners_guide.html)_ para obtener más información sobre cómo configurar Nginx.

Ejemplo de configuración de Nginx:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Instalar y configurar Swoole

Para ejecutar GraphQL Application Server localmente, instale la extensión Swoole (v5.0 o superior). Existen varias formas de instalar esta extensión.

El siguiente procedimiento describe cómo instalar la extensión Swoole para PHP 8.2 en sistemas basados en OSX. Es una de las varias formas de instalar la extensión Swoole.

```bash
pecl install swoole
```

Durante la instalación, Adobe Commerce muestra mensajes para habilitar la compatibilidad con `openssl`, `mysqlnd`, `sockets`, `http2` y `postgres`. Escriba `yes` para todas las opciones excepto `postgres`.

### Verificar instalación de Swoole

Confirme que la extensión se ha habilitado correctamente:

```bash
php -m | grep swoole
```

### Errores comunes con la instalación de Swoole

Los errores que se producen durante la instalación de Swoole suelen producirse durante la fase de instalación de `pecl`. Los errores habituales incluyen la falta de `openssl.h` y `pcre2.h` archivos. Para resolver estos errores, asegúrese de que estos dos paquetes estén instalados en el sistema local.

* Compruebe la ubicación de `openssl` ejecutando:

```bash
openssl version -d
```

Este comando muestra la ruta de acceso donde está instalado `openssl`.

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

Confirme que está utilizando la ruta de acceso desde el entorno local `dev`.

#### Confirmar la resolución de los problemas relacionados con openssl

Puede ejecutar de nuevo el siguiente comando para comprobar si se han resuelto los problemas relacionados con openssl:

```bash
pecl install swoole
```

#### Solución de problemas con pcre2.h

Para resolver problemas relacionados con `pcre2.h`, vincule simbólicamente la ruta de acceso `pcre2.h` al directorio de extensión PHP instalado. Su versión instalada específica de PHP y `pcr2.h` determina la versión concreta del comando que debe utilizar.

### Ejecutar GraphQL Application Server

Inicie GraphQL Application Server:

```bash
bin/magento server:run
```

Este comando inicia un puerto HTTP en 9501. Una vez que se inicia GraphQL Application Server, el puerto 9501 se convierte en un servidor proxy HTTP para todas las consultas de GraphQL.

Para confirmar que GraphQL Application Server se está ejecutando en la implementación:

```bash
ps aux | grep php
```

Formas adicionales de confirmar que GraphQL Application Server se está ejecutando incluyen:

* Compruebe en el archivo `/var/log/application-server.log` las entradas que estén relacionadas con las solicitudes de GraphQL procesadas.
* Intente conectarse al puerto HTTP en el que se ejecuta GraphQL Application Server. Por ejemplo: `curl -g 'http://localhost:9501/graph`.

### Confirmar que se están procesando las solicitudes de GraphQL.

GraphQL Application Server agrega el encabezado de respuesta `X-Backend` con el valor `graphql_server` a cada solicitud que procesa. Para comprobar si GraphQL Application Server ha gestionado una solicitud, compruebe este encabezado de respuesta.

### Confirmar la compatibilidad de extensiones y personalizaciones

Los desarrolladores y comerciantes de extensiones deben comprobar primero que su código de personalización y extensión cumple las directrices descritas en _[Directrices técnicas](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_.

Tenga en cuenta estas directrices durante la evaluación del código:

* Las clases de servicio (es decir, las clases que proporcionan comportamiento pero no datos, como `EventManager`) no deben tener un estado mutable.
* Evite el acoplamiento temporal.

## Deshabilitar GraphQL Application Server

Los procedimientos para desactivar GraphQL Application Server varían en función de si el servidor se está ejecutando en una implementación local o en la nube.

### Deshabilitar GraphQL Application Server (nube)

1. Elimine los nuevos archivos y cualquier otro cambio de código que se haya incluido en la confirmación de `AppServer Enabled` durante los preparativos para la implementación.

1. Confirme los cambios con este comando:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Implemente estos cambios con este comando:

   ```bash
   git push
   ```

### Deshabilitar GraphQL Application Server (local)

1. Convierta en comentario la sección `/graphql` del archivo `nginx.conf` que agregó al habilitar GraphQL Application Server.
1. Reinicie nginx.

Este método de deshabilitar GraphQL Application Server puede resultar útil para probar o comparar el rendimiento rápidamente.

### Confirme que GraphQL Application Server está desactivado.

Para confirmar que `php-fpm` está procesando solicitudes de GraphQL en lugar de GraphQL Application Server, escriba este comando: `ps aux | grep php`.

Después de deshabilitar GraphQL Application Server:

* `bin/magento server:run` está inactivo.
* `var/log/application-server.log` no contiene entradas después de las solicitudes de GraphQL.

## Pruebas funcionales e integraciones para GraphQL Application Server

Los desarrolladores de extensiones pueden ejecutar dos pruebas de integración para comprobar la compatibilidad de la extensión con GraphQL Application Server: `GraphQlStateTest` y `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` detecta el estado en objetos compartidos que no deben reutilizarse para varias solicitudes.

Esta prueba está diseñada para detectar cambios de estado en los objetos de servicio que produce `ObjectManager`. La prueba ejecuta consultas de GraphQL idénticas dos veces y compara el estado del objeto de servicio antes y después de la segunda consulta.

#### Errores de GraphQlStateTest y posible corrección

* **No se puede agregar, omitir ni filtrar una lista**. Si aparece este error, intente refactorizar la clase para que utilice fábricas para clases de servicio con estado mutable.

* **La clase muestra un estado mutable**. Si la propia clase muestra un estado mutable, intente reescribir el código para evitar este estado. Si el estado mutable es necesario por motivos de rendimiento, implemente `ResetAfterRequestInterface` y use `_resetState()` para restablecer el objeto a su estado construido inicial.

* **No se debe tener acceso a la propiedad $x escrita antes del mensaje de inicialización**. Los errores con este tipo de mensaje sugieren que el constructor no ha inicializado la propiedad especificada. Se trata de una forma de acoplamiento temporal que se produce porque el objeto no se puede utilizar después de construirse inicialmente. Este acoplamiento se produce incluso si la propiedad es privada porque el recolector que recupera los datos de las propiedades está utilizando la función de reflexión PHP. En este caso, intente refactorizar la clase para evitar el acoplamiento temporal y el estado mutable. Si esa refactorización no resuelve el error, puede cambiar el tipo de propiedad a un tipo que admita valores NULL para que se pueda inicializar en NULL.  Si la propiedad es una matriz, intente inicializar la propiedad como una matriz vacía.

Ejecute `GraphQlStateTest` ejecutando `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` busca todas las clases que implementan `ResetAfterRequestInterface` y comprueba que el método `_resetState()` devuelve el estado de un objeto al mismo estado que tenía después de ser construido por `ObjectManager`.  Esta prueba crea un objeto de servicio con `ObjectManager`, después clona ese objeto, llama a `_resetState()` y, a continuación, compara ambos objetos. La prueba no llama a ningún método entre la creación de instancias del objeto y `_resetState()`, por lo que no confirma el restablecimiento de ningún estado mutable. Encuentra problemas en los que un error tipográfico o de error tipográfico en `_resetState()` puede establecer el estado en algo diferente de lo que era originalmente.

#### Errores de ResetAfterRequestTest y posibles correcciones

* **La clase tiene valores de propiedad incoherentes**. Si esta prueba falla, compruebe si una clase ha cambiado con el resultado de que el objeto después de la construcción tiene valores de propiedad diferentes de los que tiene después de llamar al método `_resetState()`. Si la clase en la que está trabajando no contiene el método `_resetState()` en sí, compruebe la jerarquía de clases de una superclase que lo implemente.

* **No se debe tener acceso a la propiedad $x escrita antes del mensaje de inicialización**. Este problema también ocurre con `GraphQlStateTest`.

  Ejecutar `ResetAfterRequestTest` ejecutando: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Pruebas funcionales

Al implementar GraphQL Application Server, los desarrolladores de extensiones deben ejecutar pruebas funcionales de WebAPI y cualquier prueba funcional automática o manual personalizada para GraphQL. Estas pruebas funcionales ayudan a los desarrolladores a identificar posibles errores o problemas de compatibilidad.

#### Modo de monitor de estado

Al ejecutar pruebas funcionales (o pruebas manuales), GraphQL Application Server puede ejecutarse con `--state-monitor mode` habilitado para ayudar a encontrar clases en las que el estado se esté reutilizando de forma involuntaria. Inicie Application Server normalmente, excepto si agrega el parámetro `--state-monitor`.

```
bin/magento server:run --state-monitor
```

Después de procesar cada solicitud, se agrega un nuevo archivo al directorio `tmp`, por ejemplo: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Una vez finalizada la prueba, estos archivos se pueden combinar con el comando `bin/magento server:state-monitor:aggregate-output`, que crea dos archivos combinados, uno en `XML` y uno en `JSON`.

Ejemplos:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Estos archivos se pueden inspeccionar con cualquier herramienta que utilice para ver XML o JSON que muestre las propiedades modificadas de los objetos de servicio, como hace `GraphQlStateTest`. El modo `--state-monitor` utiliza la misma lista de omisión y lista de filtros que GraphQlStateTest.

>[!NOTE]
>
>No utilice el modo `--state-monitor` en la producción. Solo está diseñado para desarrollo y pruebas. Crea muchos archivos de salida y se ejecuta más lentamente de lo normal.

>[!NOTE]
>
>`--state-monitor` no es compatible con las versiones de PHP `8.3.0` - `8.3.4` debido a un error en el recolector de elementos no utilizados de PHP. Si usa PHP 8.3, debe actualizar a `8.3.5` o posterior para usar esta característica.
