---
title: Servidor de aplicaciones para API de GraphQL
description: Siga estas instrucciones para habilitar el servidor de aplicaciones para las API de GraphQL en la implementación de Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta1" type="informative"
source-git-commit: 28bfc54e0f15ba4f4f941acc7d1fb4825702cdf3
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Servidor de aplicaciones para API de GraphQL

Commerce Application Server para las API de GraphQL permite a Adobe Commerce mantener el estado entre las solicitudes de la API de Commerce GraphQL y reducir el tiempo de arranque de cada solicitud. Al compartir el estado de la aplicación entre los procesos, las solicitudes de API se vuelven considerablemente más eficientes.

Esta versión beta de Application Server está disponible únicamente para implementaciones locales que ejecuten PHP 8.1 u 8.2. No admite implementaciones basadas en la nube. Todavía no admite la funcionalidad de GraphQL B2B. Es posible que las solicitudes de GraphQL no funcionen según lo esperado en implementaciones locales cuando se configura esta versión del servidor de aplicaciones PHP.

## ¿Quién puede utilizar Application Server?

Application Server solo está disponible para implementaciones locales de Commerce.

## Habilitar Application Server para las API de GraphQL

El `ApplicationServer` módulo (`Magento/ApplicationServer/`) habilita Application Server para las API de GraphQL.

La ejecución de Application Server requiere la instalación de la extensión Open Swoole y un cambio menor en el archivo de configuración Nginx de la implementación para ejecutar este servidor de aplicaciones localmente.

### Antes de empezar

Complete estas dos tareas antes de habilitar la variable `ApplicationServer` módulo:

* Configuración De Nginx

* Instale y configure la extensión Open Swoole v22

### Configuración De Nginx

Su implementación específica de Commerce determina cómo configurar Nginx. En general, el nombre predeterminado del archivo de configuración de Nginx es `nginx.conf` y se coloca en uno de estos directorios: `/usr/local/nginx/conf`, `/etc/nginx`, o `/usr/local/etc/nginx`. Consulte [Guía para principiantes](http://nginx.org/en/docs/beginners_guide.html) para obtener más información sobre la configuración de Nginx.

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

Puede instalar tanto la extensión Open Swoole para PHP (v22) como los paquetes Composer que requiere esta extensión con un solo comando.

### Instale la ranura abierta

Introduzca:

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Durante la instalación, Adobe Commerce muestra mensajes para habilitar la compatibilidad con `openssl`, `mysqlnd`, `sockets`, `http2`, y `postgres`. Entrar `yes` para todas las opciones excepto `postgres`.

### Confirme la instalación de la ranura abierta.

Ejecutar `php -m | grep openswoole` para confirmar que la extensión se ha habilitado correctamente.

### Errores comunes con la instalación de Open Swoole

Cualquier error que se produzca durante la instalación del Open Single suele ocurrir durante el `pecl` fase de instalación. Los errores habituales incluyen la falta de `openssl.h` y `pcre2.h` archivos. Para resolver estos errores, asegúrese de que estos dos paquetes estén instalados en el sistema local.

* Comprobar la ubicación de `openssl` ejecutando:

```bash
openssl version -d
```

Este comando muestra la ruta donde `openssl` está instalado.

* Comprobar la ubicación de `pcre2` ejecutando:

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

