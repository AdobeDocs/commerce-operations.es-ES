---
title: Inicialización de aplicaciones y bootstrap
description: Obtenga información sobre la inicialización y la lógica de arranque de la aplicación Commerce.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Información general sobre inicialización y bootstrap

Para ejecutar la aplicación Commerce, se han implementado las siguientes acciones en [pub/index.php][index]:

- Incluya [app/bootstrap.php][bootinitial], que realiza rutinas de inicialización esenciales como la gestión de errores, la inicialización del cargador automático, la configuración de opciones de generación de perfiles y la configuración de la zona horaria predeterminada.
- Crear una instancia de [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Crear una instancia de aplicación de Commerce: [\Magento\Framework\AppInterface][app-face]
- Ejecutar Commerce

## Lógica de ejecución de Bootstrap

[El objeto de arranque][bootinitial] usa el siguiente algoritmo para ejecutar la aplicación Commerce:

1. Inicializa el controlador de errores.
1. Crea el [administrador de objetos][object] y los servicios compartidos básicos que se usan en todas partes y se ven afectados por el entorno. Los parámetros de entorno se insertan correctamente en estos objetos.
1. Afirma que el modo de mantenimiento está habilitado para _not_; de lo contrario, finaliza.
1. Afirma que la aplicación de Commerce está instalada; de lo contrario, finaliza.
1. Inicia la aplicación de Commerce.

   Cualquier excepción no detectada durante el inicio de la aplicación se vuelve a pasar automáticamente a Commerce en el método `catchException()`, que puede utilizar para controlar la excepción. Este último debe devolver `true` o `false`:

   - Si `true`: Commerce administró la excepción correctamente. No hay necesidad de hacer nada más.
   - Si `false`: (o cualquier otro resultado vacío) Commerce no controló la excepción. El objeto de bootstrap realiza la subrutina predeterminada de control de excepciones.

1. Envía la respuesta proporcionada por el objeto de aplicación.

   >[!INFO]
   >
   >Las afirmaciones de que la aplicación de Commerce está instalada y no está en modo de mantenimiento son el comportamiento predeterminado de la clase `\Magento\Framework\App\Bootstrap`. Puede modificarlo con un script de punto de entrada al crear el objeto de bootstrap.

   Ejemplo de script de punto de entrada que modifica el objeto de bootstrap:

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

## Tratamiento de excepciones predeterminado

El objeto de bootstrap especifica cómo gestiona la aplicación Commerce las excepciones no detectadas de la siguiente manera:

- En [modo de desarrollador](../bootstrap/application-modes.md#developer-mode), muestra la excepción tal cual.
- En cualquier otro modo, intenta registrar la excepción y mostrar un mensaje de error genérico.
- Termina Commerce con código de error `1`

## Aplicaciones de punto de entrada

Tenemos las siguientes aplicaciones de punto de entrada (es decir, aplicaciones definidas por Commerce que el servidor web utiliza como índice de directorio):

### Punto de entrada HTTP

[\Magento\Framework\App\Http][http] funciona de la siguiente manera:

1. Determina el [área de aplicación](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Inicia el controlador delantero y los sistemas de enrutamiento para buscar y ejecutar una acción del controlador.
1. Utiliza un objeto de respuesta HTTP para devolver el resultado obtenido de la acción del controlador.
1. Tratamiento de errores (en el siguiente orden de prioridad):

   1. Si está usando [modo de desarrollador](../bootstrap/application-modes.md#developer-mode):
      - Si la aplicación Commerce no está instalada, redirija al Asistente para la instalación.
      - Si la aplicación de Commerce está instalada, mostrar un error y el código de estado HTTP 500 (Error interno del servidor).
   1. Si la aplicación de Commerce está en modo de mantenimiento, muestre una página de aterrizaje &quot;Servicio no disponible&quot; de fácil manejo con el código de estado HTTP 503 (Servicio no disponible).
   1. Si la aplicación Commerce está _no_ instalada, redirija al Asistente para la instalación.
   1. Si la sesión no es válida, redirija a la página principal.
   1. Si hay algún otro error de inicialización de la aplicación, muestre una página &quot;Página no encontrada&quot; fácil de usar con el código de estado HTTP 404 (No encontrada).
   1. En cualquier otro error, muestre una página &quot;Servicio no disponible&quot; fácil de usar con la respuesta HTTP 503 y genere un informe de errores y muestre su ID en la página.

### Punto de entrada de recurso estático

[\Magento\Framework\App\StaticResource][static-resource] es una aplicación para recuperar recursos estáticos (por ejemplo, CSS, JavaScript e imágenes). Pospone cualquier acción con un recurso estático hasta que se solicita el recurso.

>[!INFO]
>
>El punto de entrada de los archivos de vista estática no se usa en [modo de producción](application-modes.md#production-mode) para evitar posibles ataques en el servidor. En el modo de producción, la aplicación de Commerce espera que existan todos los recursos necesarios en el directorio `<your Commerce install dir>/pub/static`.

En modo predeterminado o de desarrollador, una solicitud para un recurso estático inexistente se redirige al punto de entrada estático según las reglas de reescritura especificadas por el `.htaccess` apropiado.
Cuando se redirige la solicitud al punto de entrada, la aplicación de Commerce analiza la dirección URL solicitada en función de los parámetros recuperados y encuentra el recurso solicitado.

- En el modo [developer](application-modes.md#developer-mode), se devuelve el contenido del archivo para que el contenido devuelto esté actualizado cada vez que se solicite el recurso.
- En el modo [default](application-modes.md#default-mode), el recurso recuperado se publica para que la dirección URL solicitada anteriormente pueda obtener acceso a él.

  El servidor procesa todas las solicitudes futuras del recurso estático de la misma manera que los archivos estáticos; es decir, sin involucrar el punto de entrada. Si es necesario sincronizar los archivos publicados con los originales, se debe quitar el directorio `pub/static`; como resultado, los archivos se vuelven a publicar automáticamente con la siguiente solicitud.

### Punto de entrada de medios

[Magento\MediaStorage\App\Media][media] recupera recursos multimedia (es decir, cualquier archivo cargado en el almacenamiento multimedia) de la base de datos. Se utiliza siempre que la base de datos está configurada como almacenamiento de medios.

`\Magento\Core\App\Media` intenta encontrar el archivo multimedia en el almacenamiento de base de datos configurado, escribirlo en el directorio `pub/static` y devolver su contenido. Si se produce un error, devuelve un código de estado HTTP 404 (no encontrado) en el encabezado sin contenido.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
