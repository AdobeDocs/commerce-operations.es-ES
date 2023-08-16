---
title: Configuración de memcached en Ubuntu
description: Instale y configure memcached en Ubuntu.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Configuración de memcached en Ubuntu

Esta sección proporciona instrucciones para instalar memcached en Ubuntu.

>[!INFO]
>
>Adobe recomienda utilizar memcached versión 3.0.5 o posterior.

Debido a que PHP no tiene soporte nativo para memcache, debe instalar una extensión para que PHP la use. Hay dos extensiones PHP disponibles y es importante descodificar cuál utilizar:

- `memcache` (_sin d_): una extensión antigua pero popular que no se mantiene con regularidad.
El `memcache` extensión actualmente _no tiene_ trabajar con PHP 7. Consulte [Documentación de PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

  El nombre exacto es `php5-memcache` para Ubuntu.

- `memcached` (_con un`d`_): una extensión más reciente y mantenida que es compatible con PHP 7. Consulte [Documentación de PHP para memcached](https://www.php.net/manual/en/book.memcached.php).

  El nombre exacto es `php5-memcached` para Ubuntu.

## Instale y configure memcached en Ubuntu

**Para instalar y configurar memcached en Ubuntu**:

1. Como usuario con `root` privilegios, introduzca el siguiente comando:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Cambiar la configuración de memcached para `CACHESIZE` y `-l`:

   1. Abrir `/etc/memcached.conf` en un editor de texto.
   1. Busque el `-m` parámetro.
   1. Cambie su valor por lo menos `1GB`
   1. Busque el `-l` parámetro.
   1. Cambie su valor a `127.0.0.1` o `localhost`
   1. Guardar los cambios en `memcached.conf` y salga del editor de texto.
   1. Reinicie memcached.

      ```bash
      service memcached restart
      ```

1. Reinicie el servidor web.

   Para Apache, `service apache2 restart`

1. Continúe con la siguiente sección.

## Verificar que memcached funcione antes de instalar Magento

Adobe recomienda probar memcached para asegurarse de que funciona antes de instalar Commerce. Hacerlo solo lleva unos minutos y puede simplificar la resolución de problemas más adelante.

### Verificar que el servidor web reconozca memcached

Para comprobar que el servidor web reconoce memcached:

1. Crear un `phpinfo.php` en el docroot del servidor web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vaya a esa página en el explorador web. Por ejemplo:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Asegúrese de que memcached se muestre de la siguiente manera:

   ![Confirme que el servidor web reconoce memcached](../../assets/configuration/memcache.png)

   Compruebe que está utilizando memcached versión 3.0.5 o posterior.

   Si no se muestra memcached, reinicie el servidor web y actualice la página del explorador. Si sigue sin mostrarse, compruebe que ha instalado el `php-pecl-memcached` extensión.

### Verificar que memcached pueda almacenar datos en caché

Esta prueba utiliza un script PHP para verificar que memcached puede almacenar y recuperar datos de caché.

Para obtener más información sobre esta prueba, consulte [Cómo instalar y utilizar Memcache en Ubuntu tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

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

Donde `<memcached hostname or ip>` es o bien `localhost`, `127.0.0.1`o el nombre de host o la dirección IP memcache. El `<memcached port>` es el puerto de escucha; de forma predeterminada, `11211`.

Vaya a esa página en un explorador web. Por ejemplo

```http
http://192.0.2.1/cache-test.php
```

La primera vez que vaya a la página, se mostrará lo siguiente: `No matching key found. Refresh the browser to add it!`

Actualice el explorador. El mensaje cambia a `Successfully retrieved the data!`

Finalmente, puede ver las claves memcache usando Telnet:

```bash
telnet localhost <memcache port>
```

En el mensaje, escriba

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

Vaciar el almacenamiento en memoria caché y salir de Telnet:

```shell
flush_all
```

```shell
quit
```

[Información adicional sobre la prueba Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
