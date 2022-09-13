---
title: Instalación local avanzada
description: Obtenga información sobre escenarios de instalación avanzados para Adobe Commerce o Magento Open Source en la infraestructura que posee.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '2339'
ht-degree: 0%

---


# Instalación local avanzada

>[!TIP]
>
>¿Perdido? ¿Necesita una mano de ayuda? Pruebe nuestra [Instalación rápida](composer.md) o [Instalación del colaborador](https://developer.adobe.com/commerce/contributor/guides/install/) guías.

>[!NOTE]
>
>Si eligió habilitar SELinux, consulte [SELinux e iptables](prerequisites/security.md).

## Interfaz de línea de comandos (CLI)

Adobe Commerce y el Magento Open Source tienen una interfaz de línea de comandos única para las tareas de instalación y configuración: `<magento_root>/bin/magento`. La interfaz realiza varias tareas, entre ellas:

* Instalación (y tareas relacionadas como crear o actualizar el esquema de base de datos, crear la configuración de implementación).
* Borrado de la caché.
* Administración de índices, incluida la reindexación.
* Creación de diccionarios de traducción y paquetes de traducción.
* Generando clases inexistentes como fábricas e interceptores para complementos, generando la configuración de inyección de dependencias para el administrador de objetos.
* Implementación de archivos de vista estáticos.
* Crear CSS a partir de Menos.

Otras ventajas:

* Un solo comando (`<magento_root>/bin/magento list`) enumera todos los comandos de instalación y configuración disponibles.
* Interfaz de usuario coherente basada en Symfony.
* La CLI es extensible, por lo que los desarrolladores de terceros pueden &quot;conectarla&quot; a ella. Esto tiene la ventaja adicional de eliminar la curva de aprendizaje de los usuarios.
* Los comandos para los módulos desactivados no se muestran.

Este tema trata sobre la instalación del software Adobe Commerce o Magento Open Source mediante la CLI. Para obtener información sobre la configuración, consulte la [Guía de configuración](../configuration/overview.md).

El instalador se puede ejecutar varias veces si es necesario para que pueda:

* Proporcionar valores diferentes

   Por ejemplo, después de configurar el servidor web para Secure Sockets Layer (SSL), puede ejecutar el instalador para establecer las opciones de SSL.

* Corrección de errores en instalaciones anteriores
* Instalar Adobe Commerce o Magento Open Source en una instancia de base de datos diferente

## Antes de iniciar la instalación

Antes de comenzar, complete los siguientes pasos:

* Verifique que su sistema cumpla los requisitos descritos en [requisitos del sistema](system-requirements.md).

* Completar todo [requisito previo](prerequisites/overview.md) tareas.

* Complete los primeros pasos de instalación. Consulte [su ruta de instalación o actualización](overview.md).

* Después de iniciar sesión en el servidor de aplicaciones, [cambie al propietario del sistema de archivos](prerequisites/file-system/overview.md).

* Consulte la [inicio rápido de instalación](composer.md) información general.

>[!NOTE]
>
>Debe instalar Adobe Commerce o el Magento Open Source desde el `bin` subdirectorio.

Puede ejecutar el instalador varias veces con diferentes opciones para completar tareas de instalación como las siguientes:

* Instalar en fases: por ejemplo, después de configurar el servidor web para Secure Sockets Layer (SSL), puede volver a ejecutar el instalador para establecer las opciones de SSL.

* Corrija errores en instalaciones anteriores.

* Instale Adobe Commerce o Magento Open Source en una instancia de base de datos diferente.

>[!NOTE]
>
>De forma predeterminada, el instalador no sobrescribe la base de datos si instala el software en la misma instancia de base de datos. Puede utilizar la opción `cleanup-database` para cambiar este comportamiento.

Consulte también [Actualizar, volver a instalar, desinstalar](tutorials/uninstall.md).

### Instalación segura

{{$include /help/_includes/secure-install.md}}

## Comandos de ayuda del instalador

Puede ejecutar los siguientes comandos para buscar valores para algunos argumentos necesarios:

| Argumento del instalador | Comando |
| ------------------ | ------------------------------- |
| Idioma | información de bin/magento:language:list |
| Moneda | información de bin/magento:currency:list |
| Zona horaria | información de bin/magento:timezone:list |

>[!NOTE]
>
>Si aparece un error al ejecutar estos comandos, compruebe que ha actualizado las dependencias de instalación tal como se describe en [Actualización de dependencias de instalación](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Instalar desde la línea de comandos

El comando install utiliza el siguiente formato:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

Las siguientes tablas describen los nombres y valores de las opciones de instalación. Por ejemplo, comandos de instalación, consulte [Instalaciones de host local de muestra](#sample-localhost-installations).

>[!NOTE]
>
>Todas las opciones que contengan espacios o caracteres especiales deben estar incluidas entre comillas simples o dobles.

**Credenciales de administrador:**

Las siguientes opciones especifican la información de usuario y las credenciales del usuario administrador.

Puede crear el usuario administrador durante o después de la instalación. Si crea el usuario durante la instalación, se requieren todas las variables de credenciales de administrador. Consulte [Instalaciones de host local de muestra](#sample-localhost-installations).

Las siguientes tablas proporcionan muchos, pero no todos los parámetros de instalación disponibles. Para obtener una lista completa, consulte la [Referencia de herramientas de la línea de comandos](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--admin-firstname` | Nombre del usuario administrador. | Sí |
| `--admin-lastname` | Apellido del usuario administrador. | Sí |
| `--admin-email` | Dirección de correo electrónico del usuario administrador. | Sí |
| `--admin-user` | Nombre de usuario del administrador. | Sí |
| `--admin-password` | Contraseña de usuario administrador. La contraseña debe tener al menos 7 caracteres de longitud y debe incluir al menos un carácter alfabético y al menos un carácter numérico. Recomendamos una contraseña más larga y compleja. Escriba toda la cadena de contraseña entre comillas simples. Por ejemplo, `--admin-password='A0b9%t3g'` | Sí |

**Opciones de configuración de sitio y base de datos:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--base-url` | Dirección URL básica que se utilizará para acceder a su administrador y tienda en cualquiera de los formatos siguientes:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Nota:** Tanto el esquema (http:// o https://) como una barra diagonal son obligatorios.<br><br>`<your install dir>` es la ruta relativa a docroot en la que se instala el software de Adobe Commerce o Magento Open Source. Según la configuración del servidor web y los hosts virtuales, la ruta puede ser magento2 o estar en blanco.<br><br>Para acceder a Adobe Commerce o al Magento Open Source en localhost, puede utilizar `http://127.0.0.1/<your install dir>/` o `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` que representa una URL base definida por una configuración de host virtual o por un entorno de virtualización como Docker. Por ejemplo, si configura un host virtual con el nombre de host `magento.example.com`, puede instalar el software con `--base-url={{base_url}}` y acceda al administrador con una URL como `http://magento.example.com/admin`. | Sí |
| `--backend-frontname` | Identificador uniforme de recursos (URI) para acceder al administrador. Puede omitir este parámetro para permitir que la aplicación genere un URI aleatorio por usted con el siguiente patrón admin_jkhgdfq</code>.<br><br>Recomendamos un URI aleatorio para fines de seguridad. Un URI aleatorio es más difícil de explotar para hackers o software malintencionado.<br><br>El URI se muestra al final de la instalación. Puede mostrarlo más tarde en cualquier momento utilizando la variable `bin/magento info:adminuri` comando.<br><br>Si decide introducir un valor, le recomendamos que no utilice una palabra común como admin, backend. El URI de administración puede contener valores alfanuméricos y el carácter de subrayado (`_`) solamente. | No |
| `--db-host` | Utilice cualquiera de las siguientes opciones:<br><br>- El nombre de host o la dirección IP completa del servidor de base de datos.<br><br>- `localhost` (predeterminado) o `127.0.0.1` si su servidor de base de datos está en el mismo host que su servidor web.localhost significa que la biblioteca de cliente MySQL utiliza sockets UNIX para conectarse a la base de datos. `127.0.0.1` hace que la biblioteca cliente utilice el protocolo TCP. Para obtener más información sobre los sockets, consulte la [Documentación PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Si lo desea, puede especificar el puerto del servidor de la base de datos en su nombre de host como www.example.com:9000 | Sí |
| `--db-name` | Nombre de la instancia de base de datos en la que desea instalar las tablas de base de datos.<br><br>El valor predeterminado es `magento2`. | Sí |
| `--db-user` | Nombre de usuario del propietario de la instancia de base de datos.<br><br>El valor predeterminado es `root`. | Sí |
| `--db-password` | Contraseña del propietario de la instancia de base de datos. | Sí |
| `--db-prefix` | Utilícelo solo si está instalando las tablas de base de datos en una instancia de base de datos que ya tiene tablas Adobe Commerce o Magento Open Source.<br><br>En ese caso, utilice un prefijo para identificar las tablas de esta instalación. Algunos clientes tienen más de una instancia de Adobe Commerce o Magento Open Source ejecutándose en un servidor con todas las tablas de la misma base de datos.<br><br>El prefijo puede tener un máximo de cinco caracteres de longitud. Debe comenzar con una letra y solo puede incluir letras, números y caracteres de subrayado.<br><br>Esta opción permite a esos clientes compartir el servidor de base de datos con más de una instalación de Adobe Commerce o Magento Open Source. | No |
| `--db-ssl-key` | Ruta a la clave del cliente. | No |
| `--db-ssl-cert` | Ruta al certificado de cliente. | No |
| `--db-ssl-ca` | Ruta al certificado del servidor. | No |
| `--language` | Código de idioma para usar en Admin y tienda. (Si aún no lo ha hecho, puede ver la lista de códigos de idioma introduciendo `bin/magento info:language:list` del directorio bin.) | No |
| `--currency` | Moneda predeterminada para usar en la tienda. (Si aún no lo ha hecho, puede ver la lista de monedas introduciendo `bin/magento info:currency:list` del directorio bin.) | No |
| `--timezone` | Zona horaria predeterminada para usar en Admin y tienda. (Si aún no lo ha hecho, puede ver la lista de zonas horarias introduciendo `bin/magento info:timezone:list` de la variable `bin/` ). | No |
| `--use-rewrites` | `1` significa que utiliza las reescrituras del servidor web para los vínculos generados en la tienda y en el administrador.<br><br>`0` deshabilita el uso de las reescrituras del servidor web. Este es el valor predeterminado. | No |
| `--use-secure` | `1` habilita el uso de Secure Sockets Layer (SSL) en las URL de tienda. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` deshabilita el uso de SSL. En este caso, se supone que todas las demás opciones de URL seguras también son 0. Este es el valor predeterminado. | No |
| `--base-url-secure` | URL base segura que se utilizará para acceder a su administrador y tienda en el siguiente formato: `http[s]://<host or ip>/<your install dir>/` | No |
| `--use-secure-admin` | `1` significa que utiliza SSL para acceder al administrador. Asegúrese de que el servidor web admita SSL antes de seleccionar esta opción.<br><br>`0` significa que no utiliza SSL con el administrador. Este es el valor predeterminado. | No |
| `--admin-use-security-key` | 1 hace que la aplicación utilice un valor de clave generado aleatoriamente para acceder a las páginas en el Administrador y en los formularios. Estos valores clave ayudan a evitar ataques de falsificación de scripts en sitios múltiples. Este es el valor predeterminado.<br><br>`0` desactiva el uso de la clave. | No |
| `--session-save` | Utilice cualquiera de las siguientes opciones:<br><br>- `db` para almacenar datos de sesión en la base de datos. Elija el almacenamiento de la base de datos si tiene una base de datos en clúster; de lo contrario, es posible que no haya muchos beneficios con respecto al almacenamiento de información basado en archivos.<br><br>- `files` para almacenar datos de sesión en el sistema de archivos. El almacenamiento de sesión basado en archivos es adecuado a menos que el acceso al sistema de archivos sea lento, que tenga una base de datos agrupada o que desee almacenar datos de sesión en Redis.<br><br>- `redis` para almacenar datos de sesión en Redis. Si utiliza Redis para el almacenamiento en caché predeterminado o de página, Redis debe estar ya instalado. Consulte Usar Redis para el almacenamiento de sesión para obtener información adicional sobre cómo configurar la compatibilidad con Redis. | No |
| `--key` | Si tiene una, especifique una clave para cifrar datos confidenciales en la base de datos. Si no tiene uno, la aplicación genera uno para usted. | Sí |
| `--cleanup-database` | Para soltar tablas de base de datos antes de instalar Adobe Commerce o Magento Open Source, especifique este parámetro sin un valor. De lo contrario, la base de datos se mantiene intacta. | No |
| `--db-init-statements` | Parámetro de configuración avanzado de MySQL. Utiliza instrucciones de inicialización de base de datos para ejecutarse al conectarse a la base de datos MySQL. Consulte una referencia similar a esta antes de establecer cualquier valor.<br><br>El valor predeterminado es `SET NAMES utf8;`. | No |
| `--sales-order-increment-prefix` | Especifique un valor de cadena para usar como prefijo para los pedidos de venta. Normalmente, se utiliza para garantizar números de pedido únicos para los procesadores de pagos. | No |

**Opciones de configuración del motor de búsqueda:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--search-engine` | Versión de Elasticsearch o OpenSearch que se utilizará como motor de búsqueda. Los valores posibles son `elasticsearch7`, `elasticsearch6`y `elasticsearch5`. El valor predeterminado es `elasticsearch7`. Para utilizar OpenSearch, especifique `elasticsearch7`. El Elasticsearch 5 ha quedado obsoleto y no se recomienda. | No |
| `--elasticsearch-host` | El nombre de host o la dirección IP donde se está ejecutando el motor de búsqueda. El valor predeterminado es `localhost`. | No |
| `--elasticsearch-port` | El puerto para las solicitudes HTTP entrantes. El valor predeterminado es `9200`. | No |
| `--elasticsearch-index-prefix` | Prefijo que identifica el índice del motor de búsqueda. El valor predeterminado es `magento2`. | No |
| `--elasticsearch-timeout` | Número de segundos antes de que se agote el tiempo de espera del sistema. El valor predeterminado es `15`. | No |
| `--elasticsearch-enable-auth` | Habilita la autenticación en el servidor de motor de búsqueda. El valor predeterminado es `false`. | No |
| `--elasticsearch-username` | El ID de usuario para autenticar el motor de búsqueda | No, a menos que la autenticación esté habilitada |
| `--elasticsearch-password` | La contraseña para autenticar el motor de búsqueda | No, a menos que la autenticación esté habilitada |

**Opciones de configuración de RabbitMQ:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--amqp-host` | No use el `--amqp` a menos que ya haya configurado una instalación de RabbitMQ. Consulte Instalación de RabbitMQ para obtener más información sobre cómo instalar y configurar RabbitMQ.<br><br>Nombre de host donde está instalado RabbitMQ. | No |
| `--amqp-port` | Puerto que se utilizará para conectar con RabbitMQ. El valor predeterminado es 5672. | No |
| `--amqp-user` | El nombre de usuario para conectarse a RabbitMQ. No utilizar el usuario predeterminado `guest`. | No |
| `--amqp-password` | La contraseña para conectarse a RabbitMQ. No use la contraseña predeterminada `guest`. | No |
| `--amqp-virtualhost` | El host virtual para conectarse a RabbitMQ. El valor predeterminado es `/`. | No |
| `--amqp-ssl` | Indica si se conecta a RabbitMQ. El valor predeterminado es `false`. Consulte RabbitMQ para obtener información sobre la configuración de SSL para RabbitMQ. | No |
| `--consumers-wait-for-messages` | ¿Deben los consumidores esperar un mensaje de la cola? 1 - Sí, 0 - No | No |

**Bloquear opciones de configuración:**

| Nombre | Valor | ¿Requerido? |
|--- |--- |--- |
| `--lock-provider` | Bloquear nombre del proveedor.<br><br>Proveedores de bloqueo disponibles: `db`, `zookeeper`, `file`.<br><br>El proveedor de bloqueo predeterminado: `db` | No |
| `--lock-db-prefix` | El prefijo db específico para evitar conflictos de bloqueo al utilizar `db` bloquear proveedor.<br><br>El valor predeterminado: `NULL` | No |
| `--lock-zookeeper-host` | Host y puerto para conectarse al clúster de Zookeeper cuando utiliza `zookeeper` bloquear proveedor.<br><br>Por ejemplo: `127.0.0.1:2181` | Sí, si establece `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Ruta donde Zookeeper guarda los bloqueos.<br><br>La ruta predeterminada es: `/magento/locks` | No |
| `--lock-file-path` | Ruta donde se guardan los bloqueos de archivo. | Sí, si establece `--lock-provider=file` |

**Opciones de configuración de consumidores:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Para habilitar o deshabilitar módulos después de instalar Adobe Commerce o Magento Open Source, consulte [Habilitar y deshabilitar módulos](tutorials/manage-modules.md).

**Datos confidenciales:**

{{$include /help/_includes/sensitive-data.md}}

### Instalaciones de host local de muestra

Los siguientes ejemplos muestran los comandos para instalar Adobe Commerce localmente con varias opciones.

#### Ejemplo 1: Instalación básica con cuenta de usuario administrador

El siguiente ejemplo instala Adobe Commerce o Magento Open Source con las siguientes opciones:

* La aplicación está instalada en el `magento2` directorio relativo al servidor web docroot en `localhost` y la ruta al administrador es `admin`; por lo tanto:

   La dirección URL de tu tienda es `http://127.0.0.1`

* El servidor de base de datos está en el mismo host que el servidor web.

   El nombre de la base de datos es `magento`, y el nombre de usuario y la contraseña son ambos `magento`

* Utiliza reescrituras del servidor

* El administrador tiene las siguientes propiedades:

   * El nombre y los apellidos son `Magento User`
   * El nombre de usuario es `admin` y la contraseña es `admin123`
   * La dirección de correo electrónico es `user@example.com`

* El idioma predeterminado es `en_US` (inglés de EE. UU.)
* La moneda predeterminada es dólares estadounidenses
* La zona horaria predeterminada es EE. UU. Central (América/Chicago)
* OpenSearch 1.2 está instalado en `es-host.example.com` y se conecta al puerto 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Mensajes similares a los que se muestran a continuación para indicar que la instalación se ha realizado correctamente:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Ejemplo 2: Instalación básica sin cuenta de usuario administrador

Puede instalar Adobe Commerce o Magento Open Source sin crear el usuario administrador, como se muestra en el siguiente ejemplo.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

Si la instalación se realiza correctamente, aparecen mensajes como los siguientes:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Después de la instalación, puede crear un usuario administrador utilizando la variable `admin:user:create` comando:
[Crear o editar un administrador](tutorials/admin.md#create-or-edit-an-administrator)

#### Ejemplo 3: Instalar con opciones adicionales

El siguiente ejemplo instala Adobe Commerce o Magento Open Source con las siguientes opciones:

* La aplicación está instalada en el `magento2` directorio relativo al servidor web docroot en `localhost` y la ruta al administrador es `admin`; por lo tanto:

   La dirección URL de tu tienda es `http://127.0.0.1`

* El servidor de base de datos está en el mismo host que el servidor web.

   El nombre de la base de datos es `magento`, y el nombre de usuario y la contraseña son ambos `magento`

* El administrador tiene las siguientes propiedades:

   * El nombre y los apellidos son `Magento User`
   * El nombre de usuario es `admin` y la contraseña es `admin123`
   * La dirección de correo electrónico es `user@example.com`

* El idioma predeterminado es `en_US` (inglés de EE. UU.)
* La moneda predeterminada es dólares estadounidenses
* La zona horaria predeterminada es EE. UU. Central (América/Chicago)
* El instalador limpia primero la base de datos antes de instalar las tablas y el esquema
* Puede utilizar el prefijo de incremento de pedido de ventas `ORD$` (ya que contiene un carácter especial [`$`], el valor debe estar entre comillas dobles)
* Los datos de sesión se guardan en la base de datos
* Utiliza reescrituras del servidor
* El Elasticsearch 7 está instalado en `es-host.example.com` y se conecta al puerto 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=elasticsearch7 --elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200
```

>[!NOTE]
>
>Debe introducir el comando en una sola línea o, como en el ejemplo anterior, con una `\` al final de cada línea.

Si la instalación se realiza correctamente, aparecen mensajes como los siguientes:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
