---
title: Configuración avanzada de barniz
description: Configure las funciones avanzadas de Barniz, incluidos los modos de comprobación de estado, gracia y santo.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Configuración avanzada de barniz

El barniz proporciona varias funciones que evitan que los clientes experimenten retrasos y tiempos de espera largos cuando el servidor de Commerce no funciona correctamente. Estas características se pueden configurar en el archivo `default.vcl`. En este tema se describen las adiciones que Commerce proporciona al archivo VCL (Varnish Configuration Language) que se descarga desde el administrador.

Consulte el [Manual de referencia de barniz](https://varnish-cache.org/docs/index.html) para obtener más información acerca del uso del lenguaje de configuración de barniz.

## Comprobación de estado

La función de comprobación de estado de Varnish sondea el servidor de Commerce para determinar si está respondiendo a tiempo. Si responde con normalidad, el contenido nuevo se regenera después de que caduque el período de tiempo de vida (TTL). Si no es así, Varnish siempre ofrece contenido anticuado.

Commerce define la siguiente comprobación de estado predeterminada:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Cada 5 segundos, esta comprobación de estado llama al script `pub/health_check.php`. Este script comprueba la disponibilidad del servidor, cada base de datos y Redis (si están instalados). La secuencia de comandos debe devolver una respuesta en 2 segundos. Si la secuencia de comandos determina que cualquiera de estos recursos está inactivo, devuelve un código de error HTTP 500. Si este código de error se recibe en seis de cada diez intentos, el backend se considera no saludable.

El script `health_check.php` se encuentra en el directorio `pub`. Si el directorio raíz de Commerce es `pub`, asegúrese de cambiar la ruta de acceso en el parámetro `url` de `/pub/health_check.php` a `health_check.php`.

Para obtener más información, consulte la [documentación de las comprobaciones de estado de Varnish](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks).

## Modo de gracia

El modo de gracia permite a Varnish mantener un objeto en caché más allá de su valor TTL. A continuación, el barniz puede servir el contenido caducado (obsoleto) mientras obtiene una nueva versión. Esto mejora el flujo de tráfico y disminuye los tiempos de carga. Se utiliza en las siguientes situaciones:

- Cuando el servidor de Commerce está en buen estado, pero una solicitud está tardando más de lo normal
- Cuando el servidor de Commerce no está en buen estado.

La subrutina `vcl_hit` define cómo Varnish responde a una solicitud de objetos que se han almacenado en caché.

### Cuando el servidor de Commerce está en buen estado

Cuando las comprobaciones de estado determinan que el back-end de Commerce está en buen estado, Varnish comprueba si el tiempo permanece en el período de gracia. El período de gracia predeterminado es de 300 segundos, pero un comerciante puede establecer el valor desde el administrador como se describe en [Configurar Commerce para que use Barnish](configure-varnish-commerce.md). Si el período de gracia no ha caducado, Varnish entrega el contenido obsoleto y actualiza asincrónicamente el objeto desde el servidor de Commerce. Si el período de gracia ha caducado, Varnish proporciona el contenido obsoleto y actualiza sincrónicamente el objeto desde el servidor de Commerce.

La cantidad máxima de tiempo que Varnish proporciona un objeto obsoleto es la suma del período de gracia (300 segundos de forma predeterminada) y el valor TTL (86400 segundos de forma predeterminada).

Para cambiar el período de gracia predeterminado desde el archivo `default.vcl`, edite la línea siguiente en la subrutina `vcl_hit`:

```conf
if (obj.ttl + 300s > 0s) {
```

### Cuando el servidor de Commerce no está en buen estado

Si el servidor de Commerce no responde, Varnish proporciona contenido obsoleto de la caché durante tres días (o como se define en `beresp.grace`) más el TTL restante (que de forma predeterminada es un día), a menos que el contenido almacenado en caché se purgue manualmente.

## Modo Saint

El modo Saint excluye los backends no saludables durante una cantidad de tiempo configurable. Como resultado, los backends no saludables no pueden servir tráfico cuando se usa Barnish como equilibrador de carga. El modo Saint se puede utilizar con el modo de gracia para permitir una gestión compleja de servidores back-end en mal estado. Por ejemplo, si un servidor back-end no está en buen estado, los reintentos se pueden redirigir a otro servidor. Si todos los demás servidores están inactivos, proporcione objetos en caché obsoletos. Los hosts back-end y los períodos de interrupción del modo Saint se definen en el archivo `default.vcl`.

El modo Saint también se puede utilizar cuando las instancias de Commerce se desconectan individualmente para realizar tareas de mantenimiento y actualización sin afectar a la disponibilidad del sitio de Commerce.

### Requisitos previos del modo Saint

Designar un equipo como instalación principal. En este equipo, instale la instancia principal de Commerce, la base de datos mySQL y Varnish.

En todos los demás equipos, la instancia de Commerce debe tener acceso a la base de datos mySQL del equipo principal. Los equipos secundarios también deben tener acceso a los archivos de la instancia principal de Commerce.

Como alternativa, el control de versiones de archivos estáticos se puede desactivar en todos los equipos. Se puede acceder a esta opción desde el administrador en **Tiendas** > Configuración > **Configuración** > **Avanzado** > **Desarrollador** > **Configuración de archivos estáticos** > **Firmar archivos estáticos** = **No**.

Finalmente, todas las instancias de Commerce deben estar en modo de producción. Antes de iniciar Varnish, borre la caché en cada instancia. En el Administrador, vaya a **Sistema** > Herramientas > **Administración de caché** y haga clic en **Vaciar caché de Magento**. También puede ejecutar el siguiente comando para borrar la caché:

```bash
bin/magento cache:flush
```

### Instalación

El modo Saint no forma parte del paquete principal de barniz. Es un(a) `vmod` con versiones por separado que debe descargarse e instalarse. Como resultado, debe volver a compilar Varnish desde el origen, tal como se describe en las [instrucciones de instalación](https://varnish-cache.org/docs/index.html) para su versión de Varnish.

Después de volver a compilar, puede instalar el módulo del modo Saint. En general, siga estos pasos:

1. Obtenga el código fuente de [módulos Varnish](https://github.com/varnish/varnish-modules). Clone la versión de Git (versión maestra) ya que las versiones 0.9.x contienen un error de código fuente.
1. Genere el código fuente con autotools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Consulte [Colección de módulos de barniz](https://github.com/varnish/varnish-modules) para obtener información sobre cómo instalar el módulo de modo Saint.

### Archivo VCL de muestra

En el ejemplo de código siguiente se muestra el código que debe añadirse al fichero VCL para activar el modo san. Coloque las instrucciones `import` y las definiciones `backend` en la parte superior del archivo.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
