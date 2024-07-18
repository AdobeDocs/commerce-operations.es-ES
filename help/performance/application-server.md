---
title: GraphQL Application Server
description: Siga estas instrucciones para activar GraphQL Application Server en la implementación de Adobe Commerce.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: f9f8aea1a77ef062d7076a61bbafd12433f15edf
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 0%

---


# GraphQL Application Server

Commerce GraphQL Application Server permite a Adobe Commerce mantener el estado entre las solicitudes de API de Commerce GraphQL. GraphQL Application Server, que se basa en la extensión Swoole, funciona como un proceso con subprocesos de trabajo que administran el procesamiento de solicitudes. Al preservar un estado de aplicación de arranque entre las solicitudes de API de GraphQL, GraphQL Application Server mejora la gestión de solicitudes y el rendimiento general del producto. Las solicitudes de API son mucho más eficientes.

GraphQL Application Server solo está disponible para Adobe Commerce. No está disponible para el Magento Open Source. Debe [enviar un ticket de asistencia de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para habilitar GraphQL Application Server en proyectos Pro.

>[!NOTE]
>
>GraphQL Application Server no es compatible actualmente con [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Los clientes de Adobe Commerce en la infraestructura en la nube que actualmente usan [!DNL AWS S3] para [almacenamiento remoto](../configuration/remote-storage/cloud-support.md) no pueden usar GraphQL Application Server hasta que Adobe publique una revisión más adelante en 2024.

## Arquitectura

El servidor de aplicaciones de GraphQL mantiene el estado entre las solicitudes de API de GraphQL de Commerce y elimina la necesidad del arranque. Al compartir el estado de la aplicación entre procesos, las solicitudes de GraphQL se vuelven considerablemente más eficientes, lo que reduce los tiempos de respuesta en hasta un 30 %.

El modelo de ejecución de PHP que no comparte nada proporciona un desafío desde la perspectiva de la latencia porque cada solicitud requiere el arranque del marco de trabajo. Este proceso de arranque incluye tareas que llevan mucho tiempo, como leer la configuración, configurar el proceso de arranque y crear objetos de clase de servicio.

La transición de la lógica de gestión de solicitudes a un bucle de eventos de nivel de aplicación parece abordar el desafío de racionalizar el procesamiento de solicitudes a nivel empresarial. Este método elimina la necesidad del arranque durante el ciclo de vida de la ejecución de la solicitud.

## Ventajas

El servidor de aplicaciones de GraphQL permite que Adobe Commerce mantenga el estado entre solicitudes consecutivas de la API de Commerce GraphQL. Compartir el estado de la aplicación entre solicitudes mejora la eficacia de las solicitudes de API al minimizar la sobrecarga de procesamiento y optimizar la administración de solicitudes. Como resultado, el tiempo de respuesta de las solicitudes de GraphQL se puede reducir hasta un 30 %.

## Requisitos del sistema

La ejecución de GraphQL Application Server requiere lo siguiente:

* PHP 8.2 o superior
* Instalación de la extensión PHP v5+
* RAM y CPU adecuadas en función de la carga esperada

## Habilitar e implementar en la infraestructura en la nube

El módulo `ApplicationServer` (`Magento/ApplicationServer/`) habilita GraphQL Application Server.

### Activar proyectos Pro

>[!NOTE]
>
>El servidor de aplicaciones es una función de inclusión en instancias de Cloud Pro. Para habilitarlo, envíe una solicitud de asistencia.

Una vez habilitada la función Servidor de aplicaciones en el proyecto Pro, complete los siguientes pasos antes de implementar GraphQL Application Server:

1. Implemente Adobe Commerce en la infraestructura de la nube mediante la plantilla de la nube desde la rama [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Asegúrese de que todas las personalizaciones y extensiones de Commerce sean [compatibles](https://developer.adobe.com/commerce/php/development/components/app-server/) con GraphQL Application Server.
1. Clone el proyecto de Commerce Cloud.
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
1. Confirme que la variable de entorno `CRYPT_KEY` esté configurada para su instancia. Puede comprobar el estado de esta variable en el portal del proyecto en la nube (interfaz de usuario de incorporación).
1. Clone el proyecto de Commerce Cloud.
1. Cambie el nombre de `application-server/.magento/.magento.app.yaml.sample` a `application-server/.magento/.magento.app.yaml` y ajuste la configuración en .magento.app.yaml si es necesario.
1. Elimine los comentarios de la configuración de la siguiente ruta en el archivo `project_root/.magento/routes.yaml` para redirigir el tráfico de `/graphql` a GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Añada archivos actualizados al índice de Git:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Confirme los cambios:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Asegúrese de que todas las configuraciones personalizadas del archivo raíz `.magento.app.yaml` se migren correctamente al archivo `application-server/.magento/.magento.app.yaml`. Una vez agregado el archivo `application-server/.magento/.magento.app.yaml` al proyecto, debe mantenerlo además del archivo raíz `.magento.app.yaml`. Por ejemplo, si necesita [configurar rabbitmq](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) o [administrar propiedades web](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property), también debe agregar la misma configuración a `application-server/.magento/.magento.app.yaml`.

### Implementar proyectos iniciales

Después de completar los [pasos](#before-you-begin-a-cloud-starter-deployment) de habilitación, inserte los cambios en el repositorio de Git para implementar GraphQL Application Server:

```bash
git push
```

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

Su implementación específica de Commerce determina cómo configurar Nginx. En general, el archivo de configuración Nginx se denomina de forma predeterminada `nginx.conf` y se coloca en uno de estos directorios: `/usr/local/nginx/conf`, `/etc/nginx` o `/usr/local/etc/nginx`. Consulte [Guía para principiantes](https://nginx.org/en/docs/beginners_guide.html) para obtener más información sobre cómo configurar Nginx.

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

Los desarrolladores y comerciantes de extensiones deben comprobar primero que su código de extensión y personalización cumple las directrices técnicas descritas en [Directrices técnicas](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

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

Este método de deshabilitar GraphQL Application Server puede resultar útil para probar o comparar rápidamente el rendimiento.

### Confirme que GraphQL Application Server está desactivado.

Para confirmar que `php-fpm` está procesando las solicitudes de GraphQL en lugar de GraphQL Application Server, escriba este comando: `ps aux | grep php`.

Después de deshabilitar GraphQL Application Server:

* `bin/magento server:run` está inactivo.
* `var/log/application-server.log` no contiene entradas después de las solicitudes de GraphQL.

## Pruebas funcionales e integraciones para GraphQL Application Server

Los desarrolladores de extensiones pueden ejecutar dos pruebas de integración para comprobar la compatibilidad de la extensión con GraphQL Application Server: `GraphQlStateTest` y `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` detecta el estado en objetos compartidos que no deben reutilizarse para varias solicitudes.

Esta prueba está diseñada para detectar cambios de estado en los objetos de servicio producidos por `ObjectManager`. La prueba ejecuta consultas de GraphQL idénticas dos veces y compara el estado del objeto de servicio antes y después de la segunda consulta.

#### Errores de GraphQlStateTest y posible corrección

* **No se puede agregar, omitir ni filtrar una lista**. Si se produce un error que sugiere que no es seguro agregar, omitir o filtrar una lista, considere si la clase se puede refactorizar de una manera compatible con versiones anteriores para utilizar las fábricas de las clases de servicio que tienen estado mutable.

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

Los desarrolladores de extensiones deben ejecutar pruebas funcionales de WebAPI para GraphQL, así como cualquier prueba funcional automática o manual personalizada para GraphQL, al implementar GraphQL Application Server. Estas pruebas funcionales ayudan a los desarrolladores a identificar posibles errores o problemas de compatibilidad.

#### Modo de monitor de estado

Al ejecutar pruebas funcionales (o pruebas manuales), el servidor de aplicaciones puede ejecutarse con `--state-monitor mode` habilitado para ayudar a encontrar clases en las que el estado se esté reutilizando de forma involuntaria. Inicie Application Server normalmente, excepto si agrega el parámetro `--state-monitor`.

```
bin/magento server:run --state-monitor
```

Después de procesar cada solicitud, se agrega un nuevo archivo al directorio `tmp`, por ejemplo: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Una vez finalizada la prueba, estos archivos se pueden combinar con el comando `bin/magento server:state-monitor:aggregate-output`, que crea dos archivos combinados, uno en `XML` y uno en `JSON`.

Ejemplos:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Estos archivos se pueden inspeccionar con cualquier herramienta que utilice para ver XML o JSON, que mostrarán las propiedades modificadas de los objetos de servicio como lo hace GraphQlStateTest. El modo `--state-monitor` utiliza la misma lista de omisión y lista de filtros que GraphQlStateTest.

>[!NOTE]
>
>No utilice el modo `--state-monitor` en la producción. Solo está diseñado para desarrollo y pruebas. Crea muchos archivos de salida y se ejecuta más lentamente de lo normal.

>[!NOTE]
>
>`--state-monitor` no es compatible con las versiones de PHP `8.3.0` - `8.3.4` debido a un error en el recolector de elementos no utilizados de PHP. Si usa PHP 8.3, debe actualizar a `8.3.5` o posterior para poder usar esta característica.
