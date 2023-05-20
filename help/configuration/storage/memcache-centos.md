---
title: Configuración de memcached en CentOS
description: Instale y configure memcached en CentOS.
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# Configuración de memcached en CentOS

Esta sección proporciona instrucciones para instalar memcached en CentOS. Para obtener más información, consulte la [wiki memcached](https://github.com/memcached/old-wiki).

>[!INFO]
>
>El Adobe recomienda utilizar la última versión estable de memcached (actualmente 3.1.3 para memcached).

Debido a que PHP no tiene soporte nativo para memcache, debe instalar una extensión para que PHP la use. Hay dos extensiones PHP disponibles y es importante descodificar cuál utilizar:

- `memcache` (_sin d_): una extensión antigua pero popular que no se mantiene con regularidad.
El `memcache` extensión actualmente _no tiene_ trabajar con PHP 7. Consulte [Documentación de PHP para memcache](https://www.php.net/manual/en/book.memcache.php).

   El nombre exacto es `php-pecl-memcache` para CentOS.

- `memcached` (_con un`d`_): una extensión más reciente y mantenida que es compatible con PHP 7. Consulte [Documentación de PHP para memcached](https://www.php.net/manual/en/book.memcached.php).

   El nombre exacto es `php-pecl-memcached` para CentOS.

## Instalación y configuración de memcached en CentOS

Para instalar memcached en CentOS, realice las siguientes tareas como usuario con `root` privilegios:

1. Instale memcached y sus dependencias:

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >La sintaxis de los comandos anteriores puede depender de los repositorios de paquetes que utilice. Por ejemplo, si utiliza webtatic y PHP 5.6, introduzca `yum install -y php56w-pecl-memcache`. Uso `yum search memcache|grep php` para encontrar el nombre de paquete apropiado.


1. Cambiar la configuración de memcached para `CACHESIZE` y `OPTIONS`:

   1. Abrir `/etc/sysconfig/memcached` en un editor de texto.
   1. Busque el valor de `CACHESIZE` y cámbielo por lo menos a 1 GB. Por ejemplo:

      ```config
      CACHESIZE="1GB"
      ```

   1. Busque el valor de `OPTIONS` y cámbielo por `localhost` o `127.0.0.1`

1. Guardar los cambios en `memcached` y salga del editor de texto.
1. Reinicie memcached.

   ```bash
   service memcached restart
   ```

1. Reinicie el servidor web.

   Para Apache:

   ```bash
   service httpd restart
   ```

1. Continúe con la siguiente sección.

## Verificar que memcached funcione antes de instalar Commerce

Adobe recomienda probar memcached para asegurarse de que funciona antes de instalar Commerce. Hacerlo solo lleva unos minutos y puede simplificar la resolución de problemas más adelante.

### Verificar que el servidor web reconozca memcached

Para comprobar que el servidor web reconoce memcached:

1. Crear un `phpinfo.php` en el docroot del servidor web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vaya a esa página en el explorador web.

   Por ejemplo, `http://192.0.2.1/phpinfo.php`

1. Asegúrese de que memcache se muestre de la siguiente manera:

![Confirme que el servidor web reconoce memcache.](../../assets/configuration/memcache.png)

Compruebe que está utilizando memcached versión 3.0.5 o posterior.

Si no se muestra memcache, reinicie el servidor web y actualice la página del navegador. Si sigue sin mostrarse, compruebe que ha instalado el `php-pecl-memcache` extensión.

### Cree una prueba memcache que consista en una base de datos MySQL y un script PHP

La prueba utiliza una base de datos, tabla y datos MySQL para comprobar que puede recuperar los datos de la base de datos y almacenarlos en memcache. Un script PHP busca primero en la caché. Si el resultado no existe, el script consulta la base de datos. Una vez que la base de datos original ha completado la consulta, la secuencia de comandos almacena el resultado en memcache, utilizando `set` comando.

[Más detalles acerca de esta prueba](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Cree la base de datos MySQL:

```bash
mysql -u root -p
```

En el `mysql` , introduzca los siguientes comandos:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Crear `cache-test.php` en el docroot del servidor web:

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Donde `<memcached hostname or ip>` es o bien `localhost`, `127.0.0.1`o el nombre de host o la dirección IP memcache. El `<memcached port>` es el puerto de escucha; de forma predeterminada, `11211`.

Ejecute la secuencia de comandos desde la línea de comandos.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

El primer resultado es `got result from mysql`. Esto significa que la clave no existía en memcached pero se recuperó de MySQL.

El segundo resultado es `got result from memcached`, que comprueba que el valor se almacena correctamente en memcached.

Finalmente, puede ver las claves memcache usando Telnet:

```bash
telnet localhost <memcache port>
```

En el mensaje, escriba

```bash
stats items
```

El resultado es similar al siguiente:

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Vaciar el almacenamiento de memcache y salir de Telnet:

```bash
flush_all
```

```bash
quit
```

[Información adicional sobre la prueba Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
