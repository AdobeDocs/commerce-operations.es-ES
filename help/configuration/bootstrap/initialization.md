---
title: Inicialización y arranque de la aplicación
description: Obtenga información sobre la inicialización y la lógica de arranque para la aplicación Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Descripción general de la inicialización y el arranque

Para ejecutar la aplicación Commerce, se implementan las siguientes acciones en [pub/index.php][index]:

- Incluir [app/bootstrap.php][bootinitial], que realiza rutinas de inicialización esenciales, como la gestión de errores, la inicialización del cargador automático, la configuración de opciones de creación de perfiles y la configuración de la zona horaria predeterminada.
- Cree una instancia de [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Cree una instancia de aplicación de comercio: [\Magento\Framework\AppInterface][app-face]
- Ejecutar comercio

## lógica de ejecución del Bootstrap

[El objeto bootstrap][bootinitial] utiliza el siguiente algoritmo para ejecutar la aplicación Commerce:

1. Inicializa el controlador de error.
1. Crea el [administrador de objetos][object] y servicios compartidos básicos que se utilizan en todas partes y que se ven afectados por el medio ambiente. Los parámetros de entorno se insertan correctamente en estos objetos.
1. Afirma que el modo de mantenimiento es _not_ activado; de lo contrario, finaliza.
1. Afirma que la aplicación Commerce está instalada; de lo contrario, finaliza.
1. Inicia la aplicación Commerce.

   Cualquier excepción no detectada durante el inicio de la aplicación se devuelve automáticamente a Commerce en la `catchException()` método que puede utilizar para gestionar la excepción. Este último debe devolver: `true` o `false`:

   - If `true`: El comercio gestionó la excepción correctamente. No hay necesidad de hacer otra cosa.
   - If `false`: (o cualquier otro resultado vacío) Commerce no gestionó la excepción. El objeto bootstrap realiza la subrutina predeterminada de control de excepciones.

1. Envía la respuesta proporcionada por el objeto de aplicación.

   >[!INFO]
   >
   >Las afirmaciones de que la aplicación Commerce está instalada y no en modo de mantenimiento son el comportamiento predeterminado del `\Magento\Framework\App\Bootstrap` Clase . Puede modificarla con una secuencia de comandos de punto de entrada al crear el objeto bootstrap.

   Ejemplo de secuencia de comandos de punto de entrada que modifica el objeto bootstrap:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Gestión de excepciones predeterminada

El objeto bootstrap especifica cómo la aplicación Commerce gestiona las excepciones no capturadas de la siguiente manera:

- En [modo de desarrollador](../bootstrap/application-modes.md#developer-mode), muestra la excepción tal cual.
- En cualquier otro modo, intenta registrar la excepción y mostrar un mensaje de error genérico.
- Finaliza Commerce con código de error `1`

## Aplicaciones de punto de entrada

Tenemos las siguientes aplicaciones de puntos de entrada (es decir, aplicaciones definidas por Commerce que el servidor web utiliza como índice de directorio):

### Punto de entrada HTTP

[\Magento\Framework\App\Http][http] funciona de la siguiente manera:

1. Determina la variable [área de aplicación](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Inicia el controlador frontal y los sistemas de enrutamiento para encontrar y ejecutar una acción de controlador.
1. Utiliza un objeto de respuesta HTTP para devolver el resultado obtenido de la acción del controlador.
1. Gestión de errores (en el siguiente orden de prioridad):

   1. Si está utilizando [modo de desarrollador](../bootstrap/application-modes.md#developer-mode):
      - Si la aplicación Commerce no está instalada, redirija al Asistente para configuración.
      - Si la aplicación Commerce está instalada, muestre un error y el código de estado HTTP 500 (error interno del servidor).
   1. Si la aplicación Commerce está en modo de mantenimiento, muestre una página de aterrizaje &quot;Servicio no disponible&quot; descriptiva con el código de estado HTTP 503 (Servicio no disponible).
   1. Si la aplicación Commerce es _not_ instalado, redirija al Asistente de configuración.
   1. Si la sesión no es válida, redirija a la página principal.
   1. Si hay algún otro error de inicialización de la aplicación, muestre una página &quot;Página no encontrada&quot; fácil de usar con el código de estado HTTP 404 (No encontrada).
   1. En cualquier otro error, muestre una página &quot;Servicio no disponible&quot; descriptiva con la respuesta HTTP 503, genere un informe de error y muestre su ID en la página.

### Punto de entrada de recurso estático

[\Magento\Framework\App\StaticResource][static-resource] es una aplicación para recuperar recursos estáticos (por ejemplo, CSS, JavaScript e imágenes). Pospone cualquier acción con un recurso estático hasta que se solicita el recurso.

>[!INFO]
>
>El punto de entrada para los archivos de vista estáticos no se utiliza en [modo de producción](application-modes.md#production-mode) para evitar posibles vulnerabilidades en el servidor. En el modo de producción, la aplicación Commerce espera que existan todos los recursos necesarios en la variable `<your Commerce install dir>/pub/static` directorio.

En el modo predeterminado o de desarrollador, una solicitud de un recurso estático inexistente se redirige al punto de entrada estático según las reglas de reescritura especificadas por las correspondientes `.htaccess`.
Cuando se redirige la solicitud al punto de entrada, la aplicación Commerce analiza la dirección URL solicitada en función de los parámetros recuperados y busca el recurso solicitado.

- En [desarrollador](application-modes.md#developer-mode) , el contenido del archivo se devuelve para que cada vez que se solicita el recurso, el contenido devuelto esté actualizado.
- En [default](application-modes.md#default-mode) , el recurso recuperado se publica para que la dirección URL solicitada anteriormente pueda acceder a él.

   El servidor procesa todas las solicitudes futuras del recurso estático del mismo modo que los archivos estáticos; es decir, sin implicar el punto de entrada. Si es necesario sincronizar los archivos publicados con los originales, la variable `pub/static` se debe eliminar el directorio; como resultado, los archivos se vuelven a publicar automáticamente con la siguiente solicitud.

### Punto de entrada de recursos multimedia

[Magento\MediaStorage\App\Media][media] recupera los recursos de medios (es decir, cualquier archivo cargado en el almacenamiento de medios) de la base de datos. Se utiliza siempre que la base de datos esté configurada como almacenamiento de medios.

`\Magento\Core\App\Media` intenta encontrar el archivo multimedia en el almacenamiento de base de datos configurado y escribirlo en la `pub/static` y devuelva su contenido. Por error, devuelve un código de estado HTTP 404 (no encontrado) en el encabezado sin contenido.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
