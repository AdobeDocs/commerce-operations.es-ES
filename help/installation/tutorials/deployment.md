---
title: Crear o actualizar la configuración de implementación
description: Siga estos pasos para administrar la configuración de implementación de Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# Crear o actualizar la configuración de implementación

No hay requisitos previos para utilizar este comando.

## Crear o actualizar la configuración de implementación

[Configuración de implementación](../../configuration/reference/deployment-files.md) proporciona la información que la aplicación necesita inicializar y arrancar.

Puede utilizar este comando si:

* Previamente ha instalado la aplicación y desea modificar la configuración de implementación
* Desea crear solo la configuración de implementación y continuar con la instalación de otra manera
* Para actualizar la configuración de implementación sin afectar a nada más

Opciones de comando:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

La siguiente tabla analiza el significado de los parámetros y valores de instalación.

| Parámetro | Valor | ¿Requerido? |
|--- |--- |--- |
| `--backend-frontname` | Identificador uniforme de recurso ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) para acceder al administrador.<br><br>Para evitar vulnerabilidades, le recomendamos que no utilice una palabra común como admin, backend. El URI de administración puede contener valores alfanuméricos y el carácter de subrayado (`_`) solamente. | No |
| `--db-host` | Utilice cualquiera de las siguientes opciones:<br><br>- El nombre de host o la dirección IP completa del servidor de base de datos.<br><br>- `localhost` (predeterminado) o `127.0.0.1` si el servidor de la base de datos está en el mismo host que el servidor web. localhost significa que la biblioteca de cliente MySQL utiliza sockets UNIX para conectarse a la base de datos. `127.0.0.1` hace que la biblioteca cliente utilice el protocolo TCP. Para obtener más información sobre los sockets, consulte la [Documentación PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Si lo desea, puede especificar el puerto del servidor de la base de datos en su nombre de host como `www.example.com:9000` | No |
| `--db-name` | Nombre de la instancia de base de datos en la que desea instalar las tablas de base de datos.<br><br>El valor predeterminado es `magento2`. | No |
| `--db-user` | Nombre de usuario del propietario de la instancia de base de datos.<br><br>El valor predeterminado es `root`. | No |
| `--db-password` | Contraseña del propietario de la instancia de base de datos. | No |
| `--db-prefix` | Utilícelo solo si está instalando las tablas de base de datos en una instancia de base de datos que ya tiene tablas Adobe Commerce y Magento Open Source.<br><br>En ese caso, utilice un prefijo para identificar las tablas de esta instalación. Algunos clientes tienen más de una instancia de Adobe Commerce o Magento Open Source ejecutándose en un servidor con todas las tablas de la misma base de datos.<br><br>El prefijo puede tener un máximo de cinco caracteres de longitud. Debe comenzar con una letra y solo puede incluir letras, números y caracteres de subrayado.<br><br>Esta opción permite a esos clientes compartir el servidor de base de datos con más de una instalación de Adobe Commerce o Magento Open Source. | No |
| `--session-save` | Utilice cualquiera de las siguientes opciones:<br><br>- `db` para almacenar datos de sesión en la variable [base de datos](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Elija el almacenamiento de la base de datos si tiene una base de datos en clúster; de lo contrario, es posible que no haya muchos beneficios con respecto al almacenamiento de información basado en archivos.<br><br>- `files` para almacenar datos de sesión en el sistema de archivos. El almacenamiento de sesión basado en archivos es adecuado a menos que el acceso al sistema de archivos sea lento, que tenga una base de datos agrupada o que desee almacenar datos de sesión en Redis.<br><br>- `redis` para almacenar datos de sesión en [Usar Redis para almacenamiento de sesión](../../configuration/cache/config-redis.md). Si utiliza Redis para el almacenamiento en caché predeterminado o de página, Redis debe estar ya instalado. | No |
| `--key` | Si tiene una, especifique una clave para cifrar [datos confidenciales](#sensitive-data) en la base de datos. Si no tiene uno, la aplicación genera uno para usted. | No |
| `--db-init-statements` | Parámetro de configuración avanzado de MySQL. Utiliza instrucciones de inicialización de base de datos para ejecutarse al conectarse a la base de datos MySQL.<br><br>El valor predeterminado es `SET NAMES utf8;`.<br><br>Consulte una referencia similar a [este](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) antes de establecer cualquier valor. | No |
| `--http-cache-hosts` | Lista separada por comas de los hosts de la puerta de enlace de la caché HTTP a los que enviar solicitudes de depuración. (Por ejemplo, servidores Varnish). Utilice este parámetro para especificar el host o los hosts que se purgarán en la misma solicitud. (No importa si solo tiene uno o varios hosts).<br><br>El formato debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80. Por ejemplo, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. No separe los hosts con un carácter de espacio. | No |

## Importar datos de configuración

Al configurar un sistema de producción, se recomienda importar los ajustes de configuración de `config.php` y `env.php` en la base de datos.
Estos ajustes incluyen rutas y valores de configuración, sitios web, tiendas, vistas de tiendas y temas.

Después de importar sitios web, tiendas, vistas de tiendas y temas, puede crear atributos de producto y aplicarlos a sitios web, tiendas y vistas de tiendas, en el sistema de producción.

En el sistema de producción, ejecute el siguiente comando para importar datos de los archivos de configuración (`config.php` y `env.php`) a la base de datos:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

La opción `[-n, --no-interaction]` El indicador permite que el comando se ejecute sin confirmaciones adicionales.

Para obtener más información, consulte la [Importar datos de archivos de configuración](../../configuration/cli/import-configuration.md)

### Datos confidenciales

{{$include /help/_includes/sensitive-data.md}}
