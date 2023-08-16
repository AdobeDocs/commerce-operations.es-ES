---
title: Configuración avanzada de barniz
description: Configure las funciones avanzadas de Barniz, incluidos los modos de comprobación de estado, gracia y santo.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---

# Configuración avanzada de barniz

El barniz proporciona varias funciones que impiden que los clientes experimenten largos retrasos y tiempos de espera cuando el servidor de Commerce no funciona correctamente. Estas funciones se pueden configurar en la variable `default.vcl` archivo. En este tema se describen las adiciones que proporciona Commerce en el archivo VCL (Varnish Configuration Language) que descarga del administrador.

Consulte la [Manual de referencia del barniz](https://varnish-cache.org/docs/6.3/reference/index.html) para obtener más información sobre el uso del lenguaje de configuración de barniz.

## Comprobación de estado

La función de comprobación de estado de Varnish sondea el servidor de Commerce para determinar si responde a tiempo. Si responde con normalidad, el contenido nuevo se regenera después de que caduque el período de tiempo de vida (TTL). Si no es así, Varnish siempre ofrece contenido anticuado.

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

Cada 5 segundos, esta comprobación de estado llama a la función `pub/health_check.php` script. Este script comprueba la disponibilidad del servidor, cada base de datos y Redis (si están instalados). La secuencia de comandos debe devolver una respuesta en 2 segundos. Si la secuencia de comandos determina que cualquiera de estos recursos está inactivo, devuelve un código de error HTTP 500. Si este código de error se recibe en seis de cada diez intentos, el backend se considera no saludable.

El `health_check.php` El script se encuentra en `pub` directorio. Si el directorio raíz de Commerce es `pub`, luego asegúrese de cambiar la ruta en el `url` parámetro de `/pub/health_check.php` hasta `health_check.php`.

Para obtener más información, consulte la [Barniz de controles de estado](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) documentación.

## Modo de gracia

El modo de gracia permite a Varnish mantener un objeto en caché más allá de su valor TTL. A continuación, el barniz puede servir el contenido caducado (obsoleto) mientras obtiene una nueva versión. Esto mejora el flujo de tráfico y disminuye los tiempos de carga. Se utiliza en las siguientes situaciones:

- Cuando el back-end de Commerce está en buen estado, pero una solicitud está tardando más de lo normal
- Cuando el servidor de Commerce no está en buen estado.

El `vcl_hit` La subrutina define cómo Varnish responde a una solicitud de objetos que se han almacenado en caché.

### Cuando el back-end de Commerce está en buen estado

Cuando las comprobaciones de estado determinan que el back-end de Commerce está en buen estado, Varnish comprueba si el tiempo permanece en el período de gracia. El período de gracia predeterminado es de 300 segundos, pero un comerciante puede establecer el valor desde el administrador, tal como se describe en [Configuración de Commerce para utilizar Barniz](configure-varnish-commerce.md). Si el período de gracia no ha caducado, Varnish envía el contenido obsoleto y actualiza asincrónicamente el objeto desde el servidor de Commerce. Si el periodo de gracia ha caducado, Varnish proporciona el contenido obsoleto y actualiza sincrónicamente el objeto desde el servidor de Commerce.

La cantidad máxima de tiempo que Varnish proporciona un objeto obsoleto es la suma del período de gracia (300 segundos de forma predeterminada) y el valor TTL (86400 segundos de forma predeterminada).

Para cambiar el período de gracia predeterminado desde dentro de `default.vcl` , edite la línea siguiente en la `vcl_hit` subrutina:

```conf
if (obj.ttl + 300s > 0s) {
```

### Cuando el back-end de Commerce no está en buen estado

Si el servidor de Commerce no responde, Varnish proporciona contenido obsoleto desde la caché durante tres días (o como se define en `beresp.grace`) más el TTL restante (que de forma predeterminada es un día), a menos que el contenido almacenado en caché se purgue manualmente.

## Modo Saint

El modo Saint excluye los backends no saludables durante una cantidad de tiempo configurable. Como resultado, los backends no saludables no pueden servir tráfico cuando se usa Barnish como equilibrador de carga. El modo Saint se puede utilizar con el modo de gracia para permitir una gestión compleja de servidores back-end en mal estado. Por ejemplo, si un servidor back-end no está en buen estado, los reintentos se pueden redirigir a otro servidor. Si todos los demás servidores están inactivos, proporcione objetos en caché obsoletos. Los hosts del backend y los períodos de interrupción del modo Saint se definen en la variable `default.vcl` archivo.

El modo Saint también se puede utilizar cuando las instancias de Commerce se desconectan individualmente para realizar tareas de mantenimiento y actualización sin afectar a la disponibilidad del sitio de Commerce.

### Requisitos previos del modo Saint

Designar un equipo como instalación principal. En este equipo, instale la instancia principal de Commerce, la base de datos mySQL y Varnish.

En todos los demás equipos, la instancia de Commerce debe tener acceso a la base de datos mySQL del equipo principal. Los equipos secundarios también deben tener acceso a los archivos de la instancia principal de Commerce.

Como alternativa, el control de versiones de archivos estáticos se puede desactivar en todos los equipos. Se puede acceder a desde el administrador en **Tiendas** > Configuración > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de archivos estáticos** > **Firmar archivos estáticos** = **No**.

Finalmente, todas las instancias de Commerce deben estar en modo de producción. Antes de iniciar Varnish, borre la caché en cada instancia. En el Administrador, vaya a **Sistema** > Herramientas > **Administración de caché** y haga clic en **Vaciar caché del Magento**. También puede ejecutar el siguiente comando para borrar la caché:

```bash
bin/magento cache:flush
```

### Instalación

El modo Saint no forma parte del paquete principal de barniz. Es una versión separada `vmod` que deben descargarse e instalarse. Como resultado, debe volver a compilar Varnish desde el origen, tal como se describe en los siguientes artículos:

- [Instalación de Varnish 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Instalación de Varnish 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

Después de volver a compilar, puede instalar el módulo del modo Saint. En general, siga estos pasos:

1. Obtener el código fuente de [Módulos de barniz](https://github.com/varnish/varnish-modules). Clone la versión de Git (versión maestra) ya que las versiones 0.9.x contienen un error de código fuente.
1. Genere el código fuente con autotools:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Consulte [Colección del módulo de barniz](https://github.com/varnish/varnish-modules) para obtener información sobre la instalación del módulo de modo Saint.

### Archivo VCL de muestra

En el ejemplo de código siguiente se muestra el código que debe añadirse al fichero VCL para activar el modo san. Coloque el `import` extractos y `backend` definiciones en la parte superior del archivo.

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
