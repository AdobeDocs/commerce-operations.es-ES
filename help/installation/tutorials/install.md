---
title: Instalación de Adobe Commerce
description: Siga estos pasos para instalar Adobe Commerce en la infraestructura de su propiedad.
exl-id: 25f3c56e-0654-4f8b-a69d-f4152f68aca3
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2094'
ht-degree: 0%

---

# Instalación de Adobe Commerce

Antes de empezar, complete los siguientes pasos:

* Compruebe que su sistema cumple los requisitos mencionados en [requisitos del sistema](../system-requirements.md).

* Complete todas las [tareas previas](../prerequisites/overview.md).

* Complete los primeros pasos de instalación. Consulte [Su ruta de instalación o actualización](../overview.md).

* Después de iniciar sesión en el servidor de aplicaciones, [cambie al propietario del sistema de archivos](../prerequisites/file-system/overview.md).

* Revise la [introducción a la instalación desde la línea de comandos](../composer.md).

>[!NOTE]
>
>Debe instalar la aplicación desde su subdirectorio `bin`.

Puede ejecutar el instalador varias veces con diferentes opciones para completar tareas de instalación como las siguientes:

* Instalar por fases: por ejemplo, después de configurar el servidor web para Secure Sockets Layer (SSL), puede volver a ejecutar el instalador para definir las opciones de SSL.

* Corrija los errores en instalaciones anteriores.

* Instale la aplicación en una instancia de base de datos diferente.

>[!NOTE]
>
>De forma predeterminada, el instalador no sobrescribe la base de datos si instala el software de Commerce en la misma instancia de base de datos. Puede usar el parámetro `cleanup-database` opcional para cambiar este comportamiento.

Ver también [Actualizar, reinstalar, desinstalar](uninstall.md).

## Instalación segura

{{$include /help/_includes/secure-install.md}}

## Comandos de ayuda del instalador

Puede ejecutar los siguientes comandos para buscar los valores de algunos argumentos necesarios:

| Argumento del instalador | Comando |
| ------------------ | ------------------------------- |
| Idioma | `magento info:language:list` |
| Moneda | `magento info:currency:list` |
| Zona horaria | `magento info:timezone:list` |

>[!NOTE]
>
>Si aparece un error al ejecutar estos comandos, compruebe que ha actualizado las dependencias de instalación tal como se describe en [Actualizar dependencias de instalación](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Instale desde la línea de comandos

El comando install utiliza el siguiente formato:

```bash
magento setup:install --<option>=<value> ... --<option>=<value>
```

En las tablas siguientes se describen los nombres y valores de las opciones de instalación, como los comandos de instalación. Consulte [Ejemplos de instalaciones de localhost](#sample-localhost-installations).

>[!NOTE]
>
>Cualquier opción que contenga espacios o caracteres especiales debe estar entre comillas simples o dobles.

**Credenciales de administrador:**

Las siguientes opciones especifican la información de usuario y las credenciales del usuario administrador.

En la versión 2.2.8 y posteriores de Adobe Commerce, puede crear el usuario administrador durante o después de la instalación. Si crea el usuario durante la instalación, se requieren todas las variables de credenciales de administrador. Consulte [Ejemplos de instalaciones de localhost](#sample-localhost-installations).

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--admin-firstname` | Nombre del usuario administrador. | Sí |
| `--admin-lastname` | Apellido del usuario administrador. | Sí |
| `--admin-email` | Dirección de correo electrónico del usuario administrador. | Sí |
| `--admin-user` | Nombre de usuario del administrador. | Sí |
| `--admin-password` | Contraseña de usuario del administrador. La contraseña debe tener al menos 7 caracteres de longitud e incluir al menos un carácter alfabético y al menos un carácter numérico. Se recomienda una contraseña más larga y compleja. Escriba toda la cadena de contraseña entre comillas simples. Por ejemplo, `--admin-password='A0b9%t3g'` | Sí |

**Opciones de configuración del sitio y la base de datos:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--base-url` | Dirección URL base que se utilizará para obtener acceso al administrador y a la tienda en cualquiera de los siguientes formatos: <br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** El esquema (http:// o https://) y una barra diagonal son obligatorios.<br><br>`<your install dir>` es la ruta de acceso relativa a docroot en la que se instala la aplicación. Según la configuración del servidor web y los hosts virtuales, la ruta puede ser magento2 o estar en blanco.<br><br>Para tener acceso a la aplicación en localhost, puede usar `http://127.0.0.1/<your install dir>/` o `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` que representa una URL base definida por una configuración de host virtual o por un entorno de virtualización como Docker. Por ejemplo, si configura un host virtual con el nombre de host commerce.example.com, puede instalar la aplicación con `--base-url={{base_url}}` y acceder al administrador con una dirección URL como `http://commerce.example.com/admin`. | Sí |
| `--backend-frontname` | Identificador uniforme de recursos (URI) para acceder al administrador. Puede omitir este parámetro para permitir que la aplicación genere un URI aleatorio con el siguiente patrón <code>admin_jkhgdfq</code>.<br><br>Recomendamos un URI aleatorio por motivos de seguridad. Un URI aleatorio es más difícil de explotar para los piratas informáticos o para el software malintencionado.<br><br>El URI se muestra al final de la instalación. Puede mostrarlo más adelante en cualquier momento mediante el comando `magento info:adminuri`.<br><br>Si elige introducir un valor, le recomendamos que no utilice una palabra común como admin, backend. El URI de administrador solo puede contener valores alfanuméricos y el carácter de subrayado (`_`). | No |
| `--db-host` | Use cualquiera de los siguientes:<br><br>- El nombre de host completo o la dirección IP del servidor de base de datos.<br><br>- `localhost` (predeterminado) o `127.0.0.1` si el servidor de la base de datos está en el mismo host que el servidor web.localhost significa que la biblioteca de cliente MySQL utiliza sockets UNIX para conectarse a la base de datos. `127.0.0.1` hace que la biblioteca de cliente use el protocolo TCP. Para obtener más información sobre sockets, consulte la [documentación PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Si lo desea, puede especificar el puerto del servidor de base de datos en su nombre de host como www.example.com:9000 | Sí |
| `--db-name` | Nombre de la instancia de base de datos en la que desea instalar las tablas de base de datos.<br><br>El valor predeterminado es `magento2`. | Sí |
| `--db-user` | Nombre de usuario del propietario de la instancia de base de datos.<br><br>El valor predeterminado es `root`. | Sí |
| `--db-password` | Contraseña del propietario de la instancia de base de datos. | Sí |
| `--db-prefix` | Utilícelo únicamente si va a instalar las tablas de base de datos en una instancia de base de datos que ya contiene tablas de Adobe Commerce.<br><br>En ese caso, use un prefijo para identificar las tablas de esta instalación. Algunos clientes tienen más de una instancia de Adobe Commerce ejecutándose en un servidor con todas las tablas de la misma base de datos.<br><br>El prefijo puede tener una longitud máxima de cinco caracteres. Debe comenzar por una letra y solo puede incluir letras, números y caracteres de subrayado.<br><br>Esta opción permite que esos clientes compartan el servidor de base de datos con más de una instalación. | No |
| `--db-ssl-key` | Ruta a la clave de cliente. | No |
| `--db-ssl-cert` | Ruta al certificado de cliente. | No |
| `--db-ssl-ca` | Ruta al certificado del servidor. | No |
| `--language` | Código de idioma que se utilizará en la administración y en la tienda. (Si aún no lo ha hecho, puede ver la lista de códigos de idioma al escribir `magento info:language:list` desde el directorio bin.) | No |
| `--currency` | Moneda predeterminada que se utilizará en la tienda. (Si aún no lo ha hecho, puede ver la lista de monedas especificando `magento info:currency:list` desde el directorio bin.) | No |
| `--timezone` | Zona horaria predeterminada que se utilizará en la administración y en la tienda. (Si aún no lo ha hecho, puede ver la lista de zonas horarias escribiendo `magento info:timezone:list` desde el directorio bin.) | No |
| `--use-rewrites` | `1` significa que utiliza las reescrituras de servidor web para los vínculos generados en la tienda y el administrador.<br><br>`0` deshabilita el uso de reescrituras de servidor web. Esta es la opción predeterminada. | No |
| `--use-secure` | `1` habilita el uso de Capa de sockets seguros (SSL) en las direcciones URL de las tiendas. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` deshabilita el uso de SSL. En este caso, todas las demás opciones de URL segura se suponen que también son 0. Esta es la opción predeterminada. | No |
| `--base-url-secure` | URL base segura que se usará para tener acceso a su administración y tienda en el siguiente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa que utiliza SSL para acceder al administrador. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` significa que no utiliza SSL con el administrador. Esta es la opción predeterminada. | No |
| `--admin-use-security-key` | 1 hace que la aplicación utilice un valor clave generado aleatoriamente para acceder a las páginas del administrador y a los formularios. Estos valores clave ayudan a evitar ataques de falsificación de scripts entre sitios. Esta es la opción predeterminada.<br><br>`0` deshabilita el uso de la clave. | No |
| `--session-save` | Use cualquiera de las siguientes opciones:<br><br>- `db` para almacenar datos de sesión en la base de datos. Elija el almacenamiento de la base de datos si tiene una base de datos en clúster; de lo contrario, es posible que no haya muchas ventajas con respecto al almacenamiento basado en archivos.<br><br>- `files` para almacenar datos de sesión en el sistema de archivos. El almacenamiento de sesión basado en archivos es adecuado a menos que el acceso al sistema de archivos sea lento, tenga una base de datos en clúster o desee almacenar los datos de sesión en Redis.<br><br>- `redis` para almacenar datos de sesión en Redis. Si utiliza Redis para el almacenamiento en caché predeterminado o de página, debe estar instalado. Consulte Uso de Redis para el almacenamiento de sesión para obtener información adicional sobre la configuración de la compatibilidad con Redis. | No |
| `--key` | Si tiene una, especifique una clave para cifrar datos confidenciales en la base de datos. Si no tiene ninguna, la aplicación generará una para usted. | Sí |
| `--cleanup-database` | Para borrar tablas de base de datos antes de instalar la aplicación, especifique este parámetro sin un valor. De lo contrario, la base de datos se deja intacta. | No |
| `--db-init-statements` | Parámetro de configuración avanzado de MySQL. Utiliza sentencias de inicialización de base de datos para ejecutarse al conectarse a la base de datos MySQL. Consulte una referencia similar a esta antes de establecer cualquier valor.<br><br>El valor predeterminado es `SET NAMES utf8;`. | No |
| `--sales-order-increment-prefix` | Especifique un valor de cadena para utilizarlo como prefijo de pedidos de venta. Normalmente, se utiliza para garantizar números de pedido únicos para los procesadores de pagos. | No |

>[!TIP]
>
>Para habilitar los servicios de almacenamiento remoto durante la instalación, consulte [Configurar almacenamiento remoto](../../configuration/remote-storage/remote-storage.md) en la _Guía de configuración_.

**Opciones de configuración del motor de búsqueda:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--search-engine` | La versión del motor de búsqueda. Los valores posibles son `elasticsearch7`, `elasticsearch6` y `elasticsearch5`. El valor predeterminado es `elasticsearch7`. Si ha instalado OpenSearch como motor de búsqueda, especifique el valor `elasticsearch7`. El Elasticsearch 5 se ha desaprobado y no se recomienda. | No |
| `--elasticsearch-host` | El nombre de host o la dirección IP donde se está ejecutando el motor de búsqueda. El valor predeterminado es `localhost`. | No |
| `--elasticsearch-port` | El puerto para las solicitudes HTTP entrantes. El valor predeterminado es `9200`. | No |
| `--elasticsearch-index-prefix` | Prefijo que identifica el índice de búsqueda. El valor predeterminado es `magento2`. | No |
| `--elasticsearch-timeout` | El número de segundos antes de que se agote el tiempo de espera del sistema. El valor predeterminado es `15`. | No |
| `--elasticsearch-enable-auth` | Habilita la autenticación en el servidor del motor de búsqueda. El valor predeterminado es `false`. | No |
| `--elasticsearch-username` | El ID de usuario para autenticar | No, a menos que la autenticación esté habilitada |
| `--elasticsearch-password` | La contraseña para autenticarse | No, a menos que la autenticación esté habilitada |

**[!DNL RabbitMQ]opciones de configuración:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--amqp-host` | No utilice las opciones `--amqp` a menos que ya haya configurado una instalación de [!DNL RabbitMQ]. Consulte la instalación de [!DNL RabbitMQ] para obtener más información sobre cómo instalar y configurar [!DNL RabbitMQ].<br><br>Nombre de host donde está instalado [!DNL RabbitMQ]. | No |
| `--amqp-port` | El puerto que se va a usar para conectarse a [!DNL RabbitMQ]. El valor predeterminado es 5672. | No |
| `--amqp-user` | Nombre de usuario para conectarse a [!DNL RabbitMQ]. No use el usuario predeterminado `guest`. | No |
| `--amqp-password` | Contraseña para conectarse a [!DNL RabbitMQ]. No use la contraseña predeterminada `guest`. | No |
| `--amqp-virtualhost` | Host virtual para conectarse a [!DNL RabbitMQ]. El valor predeterminado es `/`. | No |
| `--amqp-ssl` | Indica si se debe conectar con [!DNL RabbitMQ]. El valor predeterminado es `false`. Consulte [!DNL RabbitMQ] para obtener información sobre cómo configurar SSL para [!DNL RabbitMQ]. | No |
| `--consumers-wait-for-messages` | ¿Deben los consumidores esperar un mensaje de la cola? 1 - Sí, 0 - No | No |

**Opciones de almacenamiento remoto:**

| Nombre | Descripción | ¿Requerido? |
|--- |--- |--- |
| `remote-storage-driver` | Nombre del adaptador<br>Valores posibles:<br>**archivo**: Deshabilita el almacenamiento remoto y usa el sistema de archivos local <br>**aws-s3**: Use el [servicio Amazon Simple Storage (Amazon S3)](https://aws.amazon.com/s3/) | No |
| `remote-storage-bucket` | Almacenamiento de objetos o nombre de contenedor | No |
| `remote-storage-prefix` | Prefijo opcional (ubicación dentro del almacenamiento de objetos) | No |
| `remote-storage-region` | Nombre de región | No |
| `remote-storage-key` | Clave de acceso opcional | No |
| `remote-storage-secret` | Clave secreta opcional | No |

**Bloquear opciones de configuración:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--lock-provider` | Bloquear nombre de proveedor.<br><br>Proveedores de bloqueos disponibles: `db`, `zookeeper`, `file`.<br><br>El proveedor de bloqueo predeterminado: `db` | No |
| `--lock-db-prefix` | Prefijo de base de datos específico para evitar conflictos de bloqueo al utilizar el proveedor de bloqueo `db`.<br><br>El valor predeterminado: `NULL` | No |
| `--lock-zookeeper-host` | Host y puerto para conectarse al clúster de Zookeeper cuando se utiliza el proveedor de bloqueo `zookeeper`.<br><br>Por ejemplo: `127.0.0.1:2181` | Sí, si se establece `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | El camino donde Zookeeper guarda las cerraduras.<br><br>La ruta predeterminada es: `/magento/locks` | No |
| `--lock-file-path` | Ruta de acceso donde se guardan los bloqueos de archivo. | Sí, si se establece `--lock-provider=file` |

**Opciones de configuración de consumidores:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Para habilitar o deshabilitar módulos después de instalar la aplicación, vea [Habilitar y deshabilitar módulos](manage-modules.md).

**Datos confidenciales:**

{{$include /help/_includes/sensitive-data.md}}

### Ejemplos de instalaciones de localhost

Los siguientes ejemplos muestran los comandos para instalar Adobe Commerce localmente con varias opciones.

#### Ejemplo 1: instalación básica con cuenta de usuario de administrador

En el ejemplo siguiente se instala la aplicación con las opciones siguientes:

* La aplicación está instalada en el directorio `magento2` con relación al servidor web docroot en `localhost` y la ruta de acceso al administrador es `admin`; por lo tanto:

  La URL de tu tienda es `http://127.0.0.1`

* El servidor de base de datos está en el mismo host que el servidor web.

  El nombre de la base de datos es `magento`, y el nombre de usuario y la contraseña son `magento`

* Utiliza reescrituras del servidor

* El administrador tiene las siguientes propiedades:

   * El nombre y los apellidos son `Commerce User`
   * El nombre de usuario es `admin` y la contraseña es `admin123`
   * La dirección de correo electrónico es `user@example.com`

* El idioma predeterminado es `en_US` (inglés de EE. UU.)
* La moneda predeterminada es el dólar estadounidense
* La zona horaria predeterminada es Centro de Estados Unidos (América/Chicago)
* Elasticsearch 7 está instalado en `es-host.example.com` y se conecta al puerto 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Se muestran mensajes similares a los siguientes para indicar que la instalación se ha realizado correctamente:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Ejemplo 2: instalación básica sin cuenta de usuario de administrador

Puede instalar la aplicación sin crear el usuario administrador, como se muestra en el siguiente ejemplo.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Si la instalación se realiza correctamente, se muestran mensajes como el siguiente:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Después de la instalación, puede crear un usuario administrador mediante el comando `admin:user:create`:
[Crear o editar un administrador](admin.md#create-or-edit-an-administrator)

#### Ejemplo 3: Instalar con opciones adicionales

En el ejemplo siguiente se instala la aplicación con las opciones siguientes:

* La aplicación Magento está instalada en el directorio `magento2` con relación al servidor web docroot en `localhost` y la ruta de acceso al administrador es `admin`; por lo tanto:

  La URL de tu tienda es `http://127.0.0.1`

* El servidor de base de datos está en el mismo host que el servidor web.

  El nombre de la base de datos es `magento`, y el nombre de usuario y la contraseña son `magento`

* El administrador tiene las siguientes propiedades:

   * El nombre y los apellidos son `Commerce User`
   * El nombre de usuario es `admin` y la contraseña es `admin123`
   * La dirección de correo electrónico es `user@example.com`

* El idioma predeterminado es `en_US` (inglés de EE. UU.)
* La moneda predeterminada es el dólar estadounidense
* La zona horaria predeterminada es Centro de Estados Unidos (América/Chicago)
* El instalador primero limpia la base de datos antes de instalar las tablas y el esquema
* Utiliza un prefijo de incremento de pedido de ventas `ORD$` (dado que contiene un carácter especial [`$`], el valor debe escribirse entre comillas dobles)
* Los datos de la sesión se guardan en la base de datos
* Utiliza reescrituras del servidor
* Elasticsearch 7 está instalado en `es-host.example.com` y se conecta al puerto 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Commerce --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>Debe escribir el comando en una sola línea o, como en el ejemplo anterior, con un carácter `\` al final de cada línea.

Si la instalación se realiza correctamente, se muestran mensajes como el siguiente:

```
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

>[!TIP]
>
>Si tiene una cuenta de usuario para tener acceso al servidor de aplicaciones, vea [establecer una máscara de usuario](../next-steps/set-umask.md). Este tipo de configuración es típico del alojamiento compartido.
