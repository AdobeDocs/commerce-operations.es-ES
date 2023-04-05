---
title: Instalación local de inicio rápido
description: Siga estos pasos para instalar Adobe Commerce o Magento Open Source en la infraestructura que posea.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---


# Instalación local de inicio rápido

Usamos [Compositor](https://getcomposer.org/) para administrar los componentes de Adobe Commerce y Magento Open Source y sus dependencias. El uso del Compositor para obtener el metapaquete Adobe Commerce y Magento Open Source ofrece las siguientes ventajas:

- Reutilizar bibliotecas de terceros sin empaquetarlas con código fuente
- Reduzca los conflictos de las extensiones y los problemas de compatibilidad mediante el uso de una arquitectura basada en componentes con una sólida administración de dependencias
- Adherirse a [Grupo de Interoperabilidad de PHP-Framework (FIG)](https://www.php-fig.org/) estándares
- Volver a empaquetar el Magento Open Source con otros componentes
- Uso del software Adobe Commerce o Magento Open Source en un entorno de producción

>[!NOTE]
>
>Los desarrolladores que contribuyan al Magento Open Source deben utilizar la variable [basado en Git](https://developer.adobe.com/commerce/contributor/guides/install/) método de instalación.

## Requisitos previos

Antes de continuar, debe hacer lo siguiente:

- Completar todo [tareas previas](system-requirements.md).
- [Instalar Compositor](https://getcomposer.org/download/).
- Get [claves de autenticación](prerequisites/authentication-keys.md) al repositorio de Adobe Commerce y del Compositor de Magento Open Source.

## Iniciar sesión como propietario del sistema de archivos

Obtenga información sobre la propiedad, los permisos y el propietario del sistema de archivos en nuestra [Resumen del tema de propiedad y permisos](prerequisites/file-system/overview.md).

Para cambiar al propietario del sistema de archivos:

1. Inicie sesión en el servidor de aplicaciones como usuario con permisos para escribir en el sistema de archivos o cambie a.

   Si utiliza el shell de bash, puede utilizar la siguiente sintaxis para cambiar al propietario del sistema de archivos e introducir el comando al mismo tiempo:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Si el propietario del sistema de archivos no permite inicios de sesión, puede hacer lo siguiente:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Para ejecutar comandos CLI desde cualquier directorio, agregue `<app_root>/bin` al sistema `PATH`.

   Dado que los contenedores tienen una sintaxis diferente, consulte una referencia como [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Ejemplo de shell bash para CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   De forma opcional, puede ejecutar los comandos de las siguientes maneras:

   - `cd <app_root>/bin` y ejecútelos como `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` es un subdirectorio de su servidor web docroot

## Obtener el metapackage

Para obtener el metapaquete Adobe Commerce o Magento Open Source:

1. Inicie sesión en el servidor de aplicaciones como, o cambie a [propietario del sistema de archivos](prerequisites/file-system/overview.md).
1. Cambie al directorio docroot del servidor web o a un directorio que haya configurado como docroot de host virtual.
1. Cree un proyecto de Compositor con el metapaquete Adobe Commerce o Magento Open Source.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Cuando se le pida, introduzca las claves de autenticación. Las claves pública y privada se crean y configuran en su [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   Si se producen errores, como `Could not find package...` o `...no matching package found`, asegúrese de que no haya errores tipográficos en el comando. Si sigue encontrando errores, es posible que no esté autorizado a descargar Adobe Commerce. Contacto [Asistencia de Adobe Commerce](https://support.magento.com/hc/en-us) para obtener ayuda.

   Consulte [Resolución de problemas](https://support.magento.com/hc/en-us/articles/360033818091) para obtener ayuda con más errores.

   >[!NOTE]
   >
   >Los clientes de Adobe Commerce pueden acceder a parches dos semanas antes de la fecha de disponibilidad general (GA). Los paquetes de versiones anteriores solo están disponibles a través del Compositor. No puede acceder a las versiones anteriores en Developer Portal o GitHub hasta que se disponga de asistencia técnica. Si no encuentra estos paquetes en el Compositor, póngase en contacto con el servicio de asistencia técnica de Adobe Commerce.

### Ejemplo: versión menor

Las versiones menores contienen nuevas funciones, correcciones de calidad y correcciones de seguridad. Use el Compositor para especificar una versión secundaria. Por ejemplo, para especificar el metapaquete de Adobe Commerce 2.4.5:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Ejemplo: parche de calidad

Los parches de calidad funcionan principalmente _y_ correcciones de seguridad. Sin embargo, a veces también pueden contener nuevas funciones compatibles con versiones anteriores. Use Composer para descargar un parche de calidad. Por ejemplo, para especificar el metapaquete de Adobe Commerce 2.4.5:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5 <install-directory-name>
```

### Ejemplo: parche de seguridad

Los parches de seguridad solo contienen correcciones de seguridad. Están diseñadas para que el proceso de actualización sea más rápido y fácil.

Los parches de seguridad utilizan la convención de nomenclatura del Compositor `2.4.5-px`. Use el Compositor para especificar un parche. Por ejemplo, para descargar el metapaquete Adobe Commerce 2.4.5-p1:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.5-p1 <install-directory-name>
```

## Definir permisos de archivo

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

Este ejemplo asume que el directorio de instalación tiene el nombre `magento2ee`, el `db-host` está en la misma máquina (`localhost`) y que la variable `db-name`, `db-user`y `db-password` son todos `magento`:

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
>Puede personalizar el URI de administración con la variable `--backend-frontname` . Sin embargo, recomendamos omitir esta opción y permitir que el comando de instalación genere automáticamente un URI aleatorio. Un URI aleatorio es más difícil de explotar para hackers o software malintencionado. El URI se muestra en la consola cuando se completa la instalación.

>[!TIP]
>
>Para obtener una descripción completa de las opciones de instalación de CLI, consulte [Instale la aplicación desde la línea de comandos](advanced.md).

## Resumen de comandos

Para mostrar una lista completa de comandos, escriba:

```bash
bin/magento list
```

Para obtener ayuda para un comando en particular, introduzca:

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

La siguiente tabla resume los comandos disponibles. Los comandos se muestran únicamente en forma de resumen. Para obtener más información sobre un comando, haga clic en el vínculo de la columna Comando .

| Comando | Descripción | Requisitos previos |
|--- |--- |--- |
| `magento setup:install` | Instala la aplicación | Ninguna |
| `magento setup:uninstall` | Quita la aplicación. | Aplicación instalada |
| `magento setup:upgrade` | Actualiza la aplicación. | Configuración de implementación |
| `magento maintenance:{enable/disable}` | Habilita o deshabilita el modo de mantenimiento (en el modo de mantenimiento, solo las direcciones IP exentas pueden acceder al Administrador o tienda). | Aplicación instalada |
| `magento setup:config:set` | Crea o actualiza la configuración de implementación. | Ninguna |
| `magento module:{enable/disable}` | Habilite o deshabilite los módulos. | Ninguna |
| `magento setup:store-config:set` | Establece las opciones relacionadas con la tienda, como la URL base, el idioma o la zona horaria. | Configuración de implementación |
| `magento setup:db-schema:upgrade` | Actualiza el esquema de la base de datos. | Configuración de implementación |
| `magento setup:db-data:upgrade` | Actualiza los datos de la base de datos. | Configuración de implementación |
| `magento setup:db:status` | Comprueba si la base de datos está actualizada con el código. | Configuración de implementación |
| `magento admin:user:create` | Crea un usuario administrador. | Puede crear usuarios para lo siguiente:<br><br>Configuración de implementación<br><br>Active como mínimo la variable `Magento_User` y `Magento_Authorization` módulos<br><br>Base de datos (la forma más sencilla es utilizar `bin/magento setup:upgrade`) |
| `magento list` | Enumera todos los comandos disponibles. | Ninguna |
| `magento help` | Proporciona ayuda para el comando especificado. | Ninguna |

### Argumentos comunes

Los siguientes argumentos son comunes a todos los comandos. Estos comandos se pueden ejecutar antes o después de instalar la aplicación:

| Versión larga | Versión corta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtenga ayuda para cualquier comando. Por ejemplo, `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sin salida. |
| `--no-interaction` | `-n` | No hay preguntas interactivas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nivel de detalle. Por ejemplo, `--verbose=3` o `-vvv` muestra debug verbosity, que es el resultado más detallado. El valor predeterminado es `--verbose=1` o `-v`. |
| `--version` | `-V` | Mostrar esta versión de la aplicación |
| `--ansi` | n.a | Forzar salida ANSI |
| `--no-ansi` | n.a | Deshabilitar salida ANSI |

>[!NOTE]
>
>¡Felicidades! Ha completado la instalación rápida. ¿Necesita más ayuda avanzada? Consulte nuestra [Instalación avanzada](advanced.md) guía.
