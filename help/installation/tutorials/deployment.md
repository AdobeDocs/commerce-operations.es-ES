---
title: Crear o actualizar la configuración de implementación
description: Siga estos pasos para administrar la configuración de implementación de Adobe Commerce o Magento Open Source.
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Crear o actualizar la configuración de implementación

No hay requisitos previos para utilizar este comando.

## Crear o actualizar la configuración de implementación

[Configuración de implementación](../../configuration/reference/deployment-files.md) proporciona la información que la aplicación necesita para inicializar y arrancar.

Puede utilizar este comando si:

* Ha instalado previamente la aplicación y desea modificar la configuración de implementación
* Desea crear únicamente la configuración de implementación y continuar con la instalación de otra forma
* Para actualizar la configuración de implementación sin afectar a nada más

Opciones de comando:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

En la tabla siguiente se describen los significados de los parámetros y valores de instalación.

| Parámetro | Valor | ¿Requerido? |
|--- |--- |--- |
| `--backend-frontname` | Identificador uniforme de recursos ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) para acceder al administrador.<br><br>Para evitar vulnerabilidades, le recomendamos que no utilice una palabra común como administrador o backend. El URI de administrador puede contener valores alfanuméricos y el carácter de subrayado (`_`) únicamente. | No |
| `--db-host` | Utilice cualquiera de las siguientes opciones:<br><br>: Nombre de host o dirección IP completos del servidor de base de datos.<br><br>- `localhost` (predeterminado) o `127.0.0.1` si el servidor de la base de datos está en el mismo host que el servidor web. localhost significa que la biblioteca de cliente MySQL utiliza sockets UNIX para conectarse a la base de datos. `127.0.0.1` hace que la biblioteca cliente utilice el protocolo TCP. Para obtener más información sobre los sockets, consulte la [Documentación de PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Si lo desea, puede especificar el puerto del servidor de la base de datos en su nombre de host como `www.example.com:9000` | No |
| `--db-name` | Nombre de la instancia de base de datos en la que desea instalar las tablas de base de datos.<br><br>El valor predeterminado es `magento2`. | No |
| `--db-user` | Nombre de usuario del propietario de la instancia de base de datos.<br><br>El valor predeterminado es `root`. | No |
| `--db-password` | Contraseña del propietario de la instancia de base de datos. | No |
| `--db-prefix` | Utilícelo únicamente si va a instalar las tablas de base de datos en una instancia de base de datos que ya contiene tablas de Adobe Commerce y de Magento Open Source.<br><br>En ese caso, utilice un prefijo para identificar las tablas de esta instalación. Algunos clientes tienen más de una instancia de Adobe Commerce o de Magento Open Source ejecutándose en un servidor con todas las tablas de la misma base de datos.<br><br>El prefijo puede tener una longitud máxima de cinco caracteres. Debe comenzar por una letra y solo puede incluir letras, números y caracteres de subrayado.<br><br>Esta opción permite a estos clientes compartir el servidor de base de datos con más de una instalación de Adobe Commerce o de Magento Open Source. | No |
| `--session-save` | Utilice cualquiera de las siguientes opciones:<br><br>- `db` para almacenar datos de sesión en [database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Elija el almacenamiento de la base de datos si tiene una base de datos en clúster; de lo contrario, es posible que no haya muchas ventajas con respecto al almacenamiento basado en archivos.<br><br>- `files` para almacenar datos de sesión en el sistema de archivos. El almacenamiento de sesión basado en archivos es adecuado a menos que el acceso al sistema de archivos sea lento, tenga una base de datos en clúster o desee almacenar los datos de sesión en Redis.<br><br>- `redis` para almacenar datos de sesión en [Usar Redis para el almacenamiento de sesión](../../configuration/cache/config-redis.md). Si utiliza Redis para el almacenamiento en caché predeterminado o de página, debe estar instalado. | No |
| `--key` | Si tiene una, especifique la clave que desea cifrar [datos confidenciales](#sensitive-data) en la base de datos. Si no tiene ninguna, la aplicación generará una para usted. | No |
| `--db-init-statements` | Parámetro de configuración avanzado de MySQL. Utiliza sentencias de inicialización de base de datos para ejecutarse al conectarse a la base de datos MySQL.<br><br>El valor predeterminado es `SET NAMES utf8;`.<br><br>Consulte una referencia similar a [este](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) antes de establecer cualquier valor. | No |
| `--http-cache-hosts` | Lista separada por comas de los hosts de puerta de enlace de caché HTTP a los que enviar solicitudes de depuración. (Por ejemplo, servidores Varnish). Utilice este parámetro para especificar el host o hosts que se van a depurar en la misma solicitud. (No importa si solo tiene un host o varios).<br><br>El formato debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80. Por ejemplo, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. No separe los hosts con caracteres de espacio. | No |

## Importar datos de configuración

Al configurar un sistema de producción, se recomienda importar los ajustes de configuración de `config.php` y `env.php` en la base de datos.
Estas opciones incluyen rutas y valores de configuración, sitios web, tiendas, vistas de tiendas y temas.

Después de importar sitios web, tiendas, vistas de tiendas y temas, puede crear atributos de producto y aplicarlos a sitios web, tiendas y vistas de tiendas en el sistema de producción.

En el sistema de producción, ejecute el siguiente comando para importar datos de los archivos de configuración (`config.php` y `env.php`) a la base de datos:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

El opcional `[-n, --no-interaction]` El indicador permite ejecutar el comando sin confirmaciones adicionales.

Para obtener más información, consulte la [Importación de datos de archivos de configuración](../../configuration/cli/import-configuration.md)

### Datos confidenciales

{{$include /help/_includes/sensitive-data.md}}
