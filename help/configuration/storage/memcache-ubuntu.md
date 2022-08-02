---
title: Configurar memorias en Ubuntu
description: Instale y configure memcached en Ubuntu.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Configurar memorias en Ubuntu

Esta sección proporciona instrucciones para instalar memcached en Ubuntu.

>[!INFO]
>
>Adobe recomienda utilizar la versión 3.0.5 o posterior almacenada en caché.

Como PHP no tiene soporte nativo para memcache, debe instalar una extensión para PHP para usarla. Hay dos extensiones PHP disponibles y es importante descodificar qué utilizar:

- `memcache` (_no d_): una extensión antigua, pero popular, que no se mantiene con regularidad.
La variable `memcache` Extensión actual _no_ trabajar con PHP 7. Consulte [Documentación de PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

   El nombre exacto es `php5-memcache` para Ubuntu.

- `memcached` (_con un`d`_): una extensión más reciente y mantenida compatible con PHP 7. Consulte [Documentación de PHP para memoria en caché](https://www.php.net/manual/en/book.memcached.php).

   El nombre exacto es `php5-memcached` para Ubuntu.

## Instalar y configurar memcached en Ubuntu

**Para instalar y configurar memcached en Ubuntu**:

1. Como usuario con `root` privilegios, introduzca el siguiente comando:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Cambie la configuración almacenada en caché para `CACHESIZE` y `-l`:

   1. Apertura `/etc/memcached.conf` en un editor de texto.
   1. Busque la variable `-m` parámetro.
   1. Cambiar su valor a al menos `1GB`
   1. Busque la variable `-l` parámetro.
   1. Cambie su valor a `127.0.0.1` o `localhost`
   1. Guarde los cambios en `memcached.conf` y salga del editor de texto.
   1. Reinicie la memoria en caché.

      ```bash
      service memcached restart
      ```

1. Reinicie el servidor web.

   Para Apache, `service apache2 restart`

1. Continúe con la siguiente sección.

## Verifique que funcione la memoria caché antes de instalar el Magento

Adobe recomienda realizar pruebas en la caché para asegurarse de que funcionen antes de instalar Commerce. Esto solo tarda unos minutos y puede simplificar la resolución de problemas más tarde.

### Verifique que el servidor web reconozca la memoria caché

Para verificar que el servidor web reconoce la memoria almacenada en caché:

1. Cree un `phpinfo.php` en el docroot del servidor web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vaya a esa página en el explorador web. Por ejemplo:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Asegúrese de que la memoria caché se muestra de la siguiente manera:

   ![Confirmar que el servidor web reconoce la memoria caché](../../assets/configuration/memcache.png)

   Compruebe que está utilizando la versión almacenada en caché 3.0.5 o posterior.

   Si la memoria en caché no se muestra, reinicie el servidor web y actualice la página del explorador. Si sigue sin mostrarse, compruebe que ha instalado el `php-pecl-memcached` extensión.

### Verificar que los datos se puedan almacenar en caché

Esta prueba utiliza un script PHP para verificar que la memoria en caché puede almacenar y recuperar [cache](https://glossary.magento.com/cache) datos.

Para obtener más información sobre esta prueba, consulte [Tutorial sobre cómo instalar y utilizar Memcache en Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Crear `cache-test.php` en el docroot del servidor web con el siguiente contenido:

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Donde `<memcached hostname or ip>` es `localhost`, `127.0.0.1`o el nombre de host o la dirección IP de la memoria caché. La variable `<memcached port>` es el puerto de escucha; de forma predeterminada, `11211`.

Vaya a esa página en un explorador web. Por ejemplo

```http
http://192.0.2.1/cache-test.php
```

La primera vez que acceda a la página, se muestra lo siguiente: `No matching key found. Refresh the browser to add it!`

Actualice el explorador. El mensaje cambia a `Successfully retrieved the data!`

Por último, puede ver las claves de memcache mediante Telnet:

```bash
telnet localhost <memcache port>
```

En el símbolo del sistema, introduzca

```shell
stats items
```

El resultado es similar al siguiente:

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Vaciar el almacenamiento en caché y salir de Telnet:

```shell
flush_all
```

```shell
quit
```

[Información adicional sobre la prueba Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
