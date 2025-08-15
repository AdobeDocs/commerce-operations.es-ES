---
title: Prácticas recomendadas de depuración
description: Conozca las técnicas para resolver los problemas comunes de desarrollo de Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Prácticas recomendadas de depuración para Adobe Commerce

En este tema se explican las formas de depurar de forma sistemática y eficaz el marco de trabajo de Adobe Commerce. El objetivo es ayudarle a llegar a la raíz de un problema rápidamente y minimizar el tiempo de investigación.

## Solución de problemas: sospechosos habituales

En esta sección se describen los problemas más comunes que pueden producirse durante el desarrollo.

### Caché

- Vaciar la caché antes de continuar con la investigación
- Considere la caché de APC, CDN, Varnish, el código generado y los directorios `var/view_preprocessed` y `pub/static/`
- Detener y reiniciar los controladores de cola después de vaciar la caché o modificar el código

El siguiente ejemplo de código proporciona comandos útiles relacionados con la administración de la caché (no se ejecute en entornos de producción):

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### Datos indexados

Reindexe todo si el problema puede estar relacionado con el índice. La depuración de datos indexados suele ocurrir en entornos que no son de producción. En entornos de producción, es posible que desee investigar el origen de la desalineación del índice antes de reindexar. Las características del estado defectuoso pueden indicarle algo sobre el origen del problema.

### Compositor

Es posible que el código esté obsoleto debido a un cambio de rama o a que los archivos principales se editaron en un esfuerzo de depuración anterior. Para eliminar posibles problemas, ejecute los siguientes comandos:

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Contenido generado

Vuelva a compilar los archivos de front-end antes de depurar el contenido generado en JS, CSS, imágenes, traducciones y otros archivos.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Modo de desarrollador

Asegúrese de que la instalación local esté en modo `developer`.

### Nuevo módulo

Si ha creado un módulo, compruebe los siguientes problemas:

- ¿Está activado el módulo?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Compruebe el archivo `app/etc/config.php` para su nuevo módulo.

- Compruebe el anidamiento de la estructura de archivos y directorios. Por ejemplo, ¿los archivos de diseño se encuentran en el directorio `view/layout/` en lugar del directorio `view/frontend/layout`? ¿Se encuentran las plantillas en el directorio `view/frontend/template` en lugar del directorio `view/frontend/templates`?

## Solución de problemas: división a medias

Si los sospechosos habituales no ofrecen una solución al problema, la forma más rápida de proceder es dividir a medias (o dividir en dos) el problema. Con este método, se eliminan los fragmentos grandes y se divide lo que queda para localizar la causa raíz en lugar de pasar por el código de forma lineal.

Consulte los siguientes diagramas:

![Diagrama de bisecto](../../../assets/playbooks/bisect.png)

![Diagrama de bisecto](../../../assets/playbooks/bisect2.png)

Existen varios métodos para dividir en dos partes, pero Adobe recomienda seguir este orden:

- Bisectar por tema
- Bisect por confirmaciones
- Bisectar por archivos

### Paso 1: Bisectar por tema

Si el problema no está relacionado con el código, elimine primero los fragmentos grandes. Algunos de los grandes trozos a pensar incluyen:

- **Adobe Commerce framework**: ¿el problema está relacionado con Adobe Commerce o podría estar relacionado con otro sistema conectado?
- **Servidor y cliente**: borre la memoria caché y el almacenamiento del explorador. ¿Se ha resuelto el problema? Eso podría descartar una causa relacionada con el servidor. ¿Persiste el problema? No es necesario perder más tiempo en la depuración del explorador.
- **Sesión**: ¿Ocurre el problema con cada usuario? Si no es así, es posible que el problema se limite a temas relacionados con la sesión o el explorador.
- **Caché**: ¿La deshabilitación de todas las cachés cambia algo? Si es así, puede centrarse en los temas relacionados con la caché.
- **Base de datos**: ¿Ocurre el problema en todos los entornos que ejecutan el mismo código? Si no es así, busque problemas en la configuración y otros temas relacionados con la base de datos.
- **Código**: busque problemas de código si ninguno de los anteriores ha resuelto el problema.

### Paso 2: Bisectar por confirmaciones

Si el problema comenzó entre ahora y hace dos meses, vuelva a revertir el código a hace dos meses. Compruebe si el problema persiste. Avanza un mes. ¿Ocurre el problema allí? Si no, adelante dos semanas. ¿Ocurre ahora? Retroceda una semana. ¿Todavía estás ahí? Retroceda cuatro días. En algún momento, solo le queda una confirmación que es probable que contenga código relacionado con el problema. Es probable que su causa raíz ahora se limite a los archivos editados en esa confirmación.

Puede sustituir semanas y días por confirmaciones. Por ejemplo, revertir 100 confirmaciones, avanzar 50, avanzar 25, retroceder 12.

### Paso 3: Bisectar por archivos

- Divida Adobe Commerce por tipos de archivo (principal y no principal). En primer lugar, deshabilite todos los módulos de cliente y mercado. ¿Persiste el problema? Es muy probable que sea un problema no central.
- Vuelva a habilitar (aproximadamente) la mitad de los módulos en el archivo `app/etc/config.php`. Tenga en cuenta las dependencias. Es mejor habilitar clústeres de módulos con el mismo tema a la vez. ¿Persiste el problema?
- Habilite una cuarta parte de los módulos restantes. ¿Persiste el problema? Deshabilite la mitad de lo que ha habilitado. Este método puede ayudarle a aislar la causa raíz en un solo módulo.

## Ahorradores de tiempo

Además de las técnicas de solución de problemas, esta sección proporciona algunas reglas generales que pueden ayudarle a ahorrar tiempo durante la depuración.

### Limitar datos

Piense en si necesita el catálogo completo o todas las vistas de la tienda para replicar el problema. Puede depurar los problemas de indexación con un clon de base de datos en el que haya eliminado el 95 % del catálogo antes de iniciar la depuración. Este método ahorra un tiempo considerable durante los procesos de indexación. Cree un duplicado de la base de datos del cliente con menos recuento de tiendas y catálogo. Esto también puede aplicarse a otras entidades (como clientes) según el área que esté depurando.

### Pedir más información

A veces, un paso fácil de olvidar entre todo el código y el trabajo técnico: pedir más información. Capturas de pantalla completa, un vídeo, un chat de videoconferencia con la persona que identificó el problema, pasos de replicación, preguntas sobre si sucedieron otras cosas aparentemente sin importancia en torno al evento problemático. Pregúntale lo que alguien esperaba que pasara. ¿Es esto realmente un error o tal vez solo un malentendido de la forma en que funciona el código?

### Lenguaje e interpretación

¿Está clara la descripción del problema? ¿Está seguro de que no hay términos ni descripciones que se puedan interpretar de varias formas? Si es así, asegúrese de que está hablando de lo mismo.

### búsqueda en Internet

Realice una búsqueda en Internet con términos relacionados con el problema. Es probable que alguien más ya haya encontrado el mismo problema. Busque [problemas de GitHub en Adobe Commerce](https://github.com/magento/magento2/issues).

### Tómese un descanso

Si está viendo un problema durante demasiado tiempo, puede ser difícil encontrar una solución. Deja tu trabajo y recoge otra tarea o da un paseo. La respuesta podría llegar a usted cuando se olvide del problema por un tiempo.

## Herramientas

Las herramientas de CLI de magerun n98 ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) proporcionan capacidades útiles para trabajar con Adobe Commerce desde la línea de comandos. Especialmente estos comandos:

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Fragmentos de código

En los temas siguientes se proporcionan fragmentos de código que pueden utilizarse para registrar o identificar problemas en proyectos de Commerce.

### Comprobar si Commerce utiliza un archivo XML

Agregue un error de sintaxis obvio en un archivo XML para ver si se utiliza. Abra una etiqueta y no la cierre, por ejemplo:

```xml
<?xml version="1.0"?>
<test
```

Si se utiliza este archivo, se genera un error. Si no es así, es posible que el módulo no se utilice o no esté habilitado, por ejemplo, o que el archivo XML esté en una ubicación incorrecta.

### Registro

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monólogo]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### Registro de bajo nivel

Dos ejemplos que siempre funcionan en cualquier archivo PHP:

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

Y para un seguimiento de pila:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
