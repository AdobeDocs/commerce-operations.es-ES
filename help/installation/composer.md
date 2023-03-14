---
title: Instalación local de inicio rápido
description: Siga estos pasos para instalar Adobe Commerce o Magento Open Source en la infraestructura de su propiedad.
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 0%

---


# Instalación local de inicio rápido

Utilizamos [Compositor](https://getcomposer.org/) para administrar los componentes de Adobe Commerce y Magento Open Source y sus dependencias. Usar Composer para obtener Adobe Commerce y Magento Open Source [metapaquete](https://glossary.magento.com/metapackage) ofrece las siguientes ventajas:

- Reutilice bibliotecas de terceros sin agruparlas con el código fuente
- Reduzca los conflictos de extensiones y los problemas de compatibilidad utilizando una arquitectura basada en componentes con una sólida administración de dependencias
- Adherirse a [Grupo de Interoperabilidad PHP-Framework (FIG)](https://www.php-fig.org/) normas
- Volver a empaquetar el Magento Open Source con otros componentes
- Uso del software Adobe Commerce o de Magento Open Source en un entorno de producción

>[!NOTE]
>
>Los desarrolladores que colaboren con Magento Open Source deben utilizar [basado en Git](https://developer.adobe.com/commerce/contributor/guides/install/) método de instalación.

## Requisitos previos

Antes de continuar, debe hacer lo siguiente:

- Completar todo [tareas previas](system-requirements.md).
- [Instalar Compositor](https://getcomposer.org/download/).
- Obtener [claves de autenticación](prerequisites/authentication-keys.md) al repositorio de Adobe Commerce y Compositor de Magento Open Source.

## Iniciar sesión como propietario del sistema de archivos

Obtenga información acerca de la propiedad, los permisos y el propietario del sistema de archivos en nuestra [Tema de información general sobre propiedad y permisos](prerequisites/file-system/overview.md).

Para cambiar al propietario del sistema de archivos:

1. Inicie sesión en el servidor de aplicaciones como un usuario con permisos para escribir en el sistema de archivos o cambie a.

   Si utiliza el shell de bash, puede utilizar la siguiente sintaxis para cambiar al propietario del sistema de archivos e introducir el comando al mismo tiempo:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si el propietario del sistema de archivos no permite inicios de sesión, puede hacer lo siguiente:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Para ejecutar comandos CLI desde cualquier directorio, agregue `<app_root>/bin` a su sistema `PATH`.

   Dado que los shells tienen una sintaxis diferente, consulte una referencia como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Ejemplo de shell de bash para CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Opcionalmente, puede ejecutar los comandos de las siguientes maneras:

   - `cd <app_root>/bin` y ejecútelas como `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` es un subdirectorio del servidor web docroot

## Obtenga el metapaquete

Para obtener el metapaquete de Adobe Commerce o Magento Open Source:

1. Inicie sesión en el servidor de aplicaciones como, o cambie a, [propietario del sistema de archivos](prerequisites/file-system/overview.md).
1. Cambie al directorio docroot del servidor web o a un directorio que haya configurado como docroot del host virtual.
1. Cree un proyecto de Composer utilizando el metapaquete Adobe Commerce o Magento Open Source.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Cuando se le solicite, introduzca sus claves de autenticación. Las claves pública y privada se crean y configuran en su [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   Si se producen errores, como `Could not find package...` o `...no matching package found`, asegúrese de que no haya errores tipográficos en el comando. Si sigue encontrando errores, es posible que no tenga autorización para descargar Adobe Commerce. Contacto [Asistencia de Adobe Commerce](https://support.magento.com/hc/en-us) para obtener ayuda.

   Consulte [Solución de problemas](https://support.magento.com/hc/en-us/articles/360033818091) para obtener ayuda con más errores.

   >[!NOTE]
   >
   >Los clientes de Adobe Commerce pueden acceder a los parches dos semanas antes de la fecha de disponibilidad general (GA). Los paquetes previos al lanzamiento solo están disponibles mediante Composer. No puede acceder a las versiones previas en el portal del desarrollador o GitHub hasta GA. Si no encuentra estos paquetes en Composer, póngase en contacto con el Soporte técnico de Adobe Commerce.

### Ejemplo: versión menor

Las versiones menores contienen nuevas funciones, correcciones de calidad y correcciones de seguridad. Use Compositor para especificar una versión secundaria. Por ejemplo, para especificar el metapaquete de Adobe Commerce 2.4.5:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Ejemplo: parche de calidad

Los parches de calidad contienen principalmente parches funcionales _y_ correcciones de seguridad. Sin embargo, a veces también pueden contener nuevas funciones compatibles con versiones anteriores. Use Composer para descargar un parche de calidad. Por ejemplo, para especificar el metapaquete de Adobe Commerce 2.4.5:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Ejemplo: parche de seguridad

Los parches de seguridad solo contienen correcciones de seguridad. Están diseñadas para que el proceso de actualización sea más rápido y sencillo.

Los parches de seguridad utilizan la convención de nombres del Compositor `2.4.5-px`. Use el Compositor para especificar un parche. Por ejemplo, para descargar el metapaquete Adobe Commerce 2.4.5-p1:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## Definición de permisos de archivo

Debe establecer permisos de lectura y escritura para el grupo de servidores web antes de instalar Adobe Commerce o Magento Open Source. Esto es necesario para que la línea de comandos pueda escribir archivos en el sistema de archivos.

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Instalación de la aplicación

Debe utilizar la línea de comandos para instalar Adobe Commerce o Magento Open Source.

En este ejemplo se supone que el nombre del directorio de instalación es `magento2ee`, el `db-host` está en el mismo equipo (`localhost`), y que la variable `db-name`, `db-user`, y `db-password` son todos `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>Puede personalizar el URI de administrador con la variable `--backend-frontname` opción. Sin embargo, se recomienda omitir esta opción y permitir que el comando de instalación genere automáticamente un URI aleatorio. Un URI aleatorio es más difícil de explotar para los piratas informáticos o para el software malintencionado. El URI se muestra en la consola cuando se completa la instalación.

>[!TIP]
>
>Para obtener una descripción completa de las opciones de instalación de CLI, consulte [Instale la aplicación desde la línea de comandos](advanced.md).

## Resumen de comandos

Para mostrar una lista completa de comandos, escriba:

```bash
bin/magento list
```

Para obtener ayuda acerca de un comando concreto, escriba:

```bash
bin/magento help <command>
```

Por ejemplo:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

En la tabla siguiente se resumen los comandos disponibles. Los comandos sólo se muestran en forma de resumen. Para obtener más información acerca de un comando, haga clic en el vínculo en la columna Comando.

| Comando | Descripción | Requisitos previos |
|--- |--- |--- |
| `magento setup:install` | Instala la aplicación | Ninguno |
| `magento setup:uninstall` | Quita la aplicación. | Aplicación instalada |
| `magento setup:upgrade` | Actualiza la aplicación. | Configuración de implementación |
| `magento maintenance:{enable/disable}` | Activa o desactiva el modo de mantenimiento (en este modo, solo las direcciones IP exentas pueden acceder al administrador o a la tienda). | Aplicación instalada |
| `magento setup:config:set` | Crea o actualiza la configuración de implementación. | Ninguno |
| `magento module:{enable/disable}` | Habilitar o deshabilitar módulos. | Ninguno |
| `magento setup:store-config:set` | Establece opciones relacionadas con la tienda, como la dirección URL base, el idioma y la zona horaria. | Configuración de implementación |
| `magento setup:db-schema:upgrade` | Actualiza el esquema de la base de datos. | Configuración de implementación |
| `magento setup:db-data:upgrade` | Actualiza los datos de la base de datos. | Configuración de implementación |
| `magento setup:db:status` | Comprueba si la base de datos está actualizada con el código. | Configuración de implementación |
| `magento admin:user:create` | Crea un usuario administrador. | Puede crear usuarios para lo siguiente:<br><br>Configuración de implementación<br><br>Habilite como mínimo la `Magento_User` y `Magento_Authorization` módulos<br><br>Base de datos (la forma más sencilla es usar `bin/magento setup:upgrade`) |
| `magento list` | Muestra todos los comandos disponibles. | Ninguno |
| `magento help` | Proporciona ayuda para el comando especificado. | Ninguno |

### Argumentos comunes

Los siguientes argumentos son comunes a todos los comandos. Estos comandos se pueden ejecutar antes o después de instalar la aplicación:

| Versión larga | Versión corta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtener ayuda para cualquier comando. Por ejemplo, `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sin salida. |
| `--no-interaction` | `-n` | No hay preguntas interactivas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nivel de detalle. Por ejemplo, `--verbose=3` o `-vvv` muestra el nivel de detalle de la depuración, que es el resultado más detallado. El valor predeterminado es `--verbose=1` o `-v`. |
| `--version` | `-V` | Mostrar esta versión de la aplicación |
| `--ansi` | n/a | Forzar salida ANSI |
| `--no-ansi` | n/a | Deshabilitar salida ANSI |

>[!NOTE]
>
>¡Felicitaciones! Ha completado la instalación rápida. ¿Necesita ayuda más avanzada? Consulte nuestra [Instalación avanzada](advanced.md) guía.
